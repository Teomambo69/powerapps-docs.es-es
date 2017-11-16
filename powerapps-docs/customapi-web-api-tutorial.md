---
title: "Creación de un conector personalizado para una API web | Microsoft Docs"
description: "Aprenda a crear una instancia de ASP.NET Web API con autenticación de Azure Active Directory en PowerApps."
services: 
suite: powerapps
documentationcenter: 
author: mgblythe
manager: anneta
editor: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/26/2016
ms.author: mblythe
ms.openlocfilehash: 6ec78949915c8c82a88def492c249902afef6a88
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="build-a-custom-connector-for-a-web-api-in-powerapps"></a>Creación de un conector personalizado para una API web en PowerApps
En este tutorial se muestra cómo crear una instancia de ASP.NET Web API, hospedarla en Azure Web Apps, habilitar la autenticación de Azure Active Directory y registrar la instancia de ASP.NET Web API en PowerApps. Después de registrar la API, puede conectarse a ella y llamarla desde la aplicación.

## <a name="prerequisites"></a>Requisitos previos
* Una [suscripción de Azure](https://azure.microsoft.com/en-us/free/).
* Una [cuenta de PowerApps](https://powerapps.microsoft.com).
* [Visual Studio](https://www.visualstudio.com/vs/) 2013 o versiones posteriores.

## <a name="create-an-aspnet-web-api-and-deploy-it-to-azure"></a>Crear una instancia de ASP.NET Web API e implementarla en Azure
1. En Visual Studio, haga clic en **Archivo** > **Nuevo proyecto** para crear una aplicación web ASP.NET de C#.
   
    ![Nueva aplicación web](./media/customapi-web-api-tutorial/newwebapp.png)
2. Seleccione la plantilla **API web**.  Deje **Host en la nube** activada.  Haga clic en **Cambiar autenticación**.
   
    ![Plantilla de nuevo proyecto web](./media/customapi-web-api-tutorial/new-web-api.png)
3. Seleccione **Sin autenticación** y haga clic en **Aceptar**.
   
    ![Sin autenticación](./media/customapi-web-api-tutorial/noauth.png)
4. Haga clic en **Aceptar** en el cuadro de diálogo **Nuevo proyecto ASP.NET**.  Aparece el cuadro de diálogo Configurar aplicación web de Microsoft Azure.
   
    ![Configurar aplicación web de Microsoft Azure](./media/customapi-web-api-tutorial/azure-publishing.png)]
   
    Seleccione su cuenta de Azure, escriba un valor en **Nombre de la aplicación web** (o deje el predeterminado) y seleccione su **suscripción** de Azure.  Seleccione o cree un **plan de App Service** (una colección de Web Apps dentro de su suscripción).  Seleccione o cree un **grupo de recursos** (una agrupación de recursos de Azure dentro de su suscripción).  Seleccione la región donde se debe implementar la aplicación web.  Si es necesario para la API web, seleccione o cree un **servidor de bases de datos** de Azure.  Por último, haga clic en **Aceptar**.
5. Cree la API web.
   
    **Nota**: Si aún no tiene código preparado para una API web, consulte el tutorial [Introducción a ASP.NET Web API 2 (C#)](http://www.asp.net/web-api/overview/getting-started-with-aspnet-web-api/tutorial-your-first-web-api).
6. Para conectar la API web con PowerApps, será necesario un archivo de [OpenAPI](http://swagger.io/) que describa sus operaciones.  Podría escribir un archivo de OpenAPI propio con el [editor en línea](http://editor.swagger.io/) pero, en este tutorial, usará una herramienta de código abierto denominada [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle/blob/master/README.md).  Instale el paquete NuGet de Swashbuckle en el proyecto de Visual Studio; para ello, haga clic en **Herramientas** > **Administrador de paquetes NuGet** > **Consola del Administrador de paquetes** y, en la consola del Administrador de paquetes, escriba el comando `Install-Package Swashbuckle`.
   
    ![Install-Package Swashbuckle](./media/customapi-web-api-tutorial/swashbuckle-console.png)
   
    **Sugerencia**: Al ejecutar la aplicación de API web después de instalar Swashbuckle, se generará un archivo de OpenAPI en la dirección URL `http://<your root URL>/swagger/docs/v1`.  También hay disponible una interfaz de usuario generada en `http://<your root URL>/swagger`.
7. Cuando la API web esté lista, publíquela en Azure. Para publicarla desde Visual Studio, haga clic con el botón derecho en el proyecto web en el Explorador de soluciones, haga clic en **Publicar** y siga las indicaciones en el cuadro de diálogo Publicar.
8. Recupere el código JSON de OpenAPI en `https://<azure-webapp-url>/swagger/docs/v1`.  Guarde el contenido como archivo JSON.  Según el explorador, es posible que tenga que copiar y pegar el texto en un archivo de texto vacío.   
   
    **Importante**: Un documento de OpenAPI con identificadores de operación duplicados no es válido. Si usa la plantilla C# de ejemplo, el identificador de operación `Values_Get` se repite dos veces. Para corregirlo, cambie una instancia a `Value_Get` y vuelva a publicar. También puede descargar un [archivo de OpenAPI de ejemplo](http://pwrappssamples.blob.core.windows.net/samples/webAPI.json) desde este tutorial. Asegúrese de quitar los comentarios (a partir de `//`) antes de usarlo.

## <a name="set-up-azure-active-directory-authentication"></a>Configurar la autenticación de Azure Active Directory
Ahora creará dos aplicaciones de Azure Active Directory (AAD) en Azure.  Para ver un ejemplo de cómo hacerlo, consulte el [tutorial de Azure Resource Manager](customapi-azure-resource-manager-tutorial.md#enable-authentication-in-azure-active-directory).

**Importante** Ambas aplicaciones deben estar en el mismo directorio.

### <a name="first-aad-application-securing-the-web-api"></a>Primera aplicación de AAD: protección de la API web
La primera aplicación de AAD se usa para proteger la API web. Asígnele el nombre **webAPI**.  Siga los pasos del tutorial vinculados anteriores (solo la sección titulada "Habilitar la autenticación en Azure Active Directory") con los siguientes valores:

* Dirección URL de inicio de sesión: `https://login.windows.net`
* URL de respuesta: `https://<your-root-url>/.auth/login/aad/callback`
* No se necesita una clave de cliente.
* No es necesario delegar los permisos.
* **Importante**: Tome nota del identificador de aplicación.  Lo necesitará más adelante.

### <a name="second-aad-application-securing-the-custom-connector-and-delegated-access"></a>Segunda aplicación de AAD: protección del conector personalizado y acceso delegado
La segunda aplicación de AAD se usa para proteger el registro del conector personalizado y para obtener acceso delegado a la API web protegida por la primera aplicación. Asigne a esta el nombre **webAPI-customAPI**.

* Dirección URL de inicio de sesión: `https://login.windows.net`
* URL de respuesta: `https://msmanaged-na.consent.azure-apim.net/redirect`
* Agregue permisos para obtener acceso delegado a la API web.
* También necesitará el identificador de esta aplicación más adelante, así que anótelo.
* Genere una clave de cliente y almacénela en un lugar seguro. La necesitará más adelante.

## <a name="add-authentication-to-your-azure-web-app"></a>Agregar autenticación a la aplicación web de Azure
1. Inicie sesión en [Azure Portal](https://portal.azure.com) y busque la aplicación web que ha implementado en la primera sección.
2. Haga clic en **Configuración** y seleccione **Autenticación/autorización**.
3. Active **Autenticación de App Service** y seleccione **Azure Active Directory**.  En la siguiente hoja, seleccione **Rápido**.  
4. Haga clic en **Seleccionar aplicación de AD existente** y seleccione la aplicación de AAD **webAPI** que creó antes.

Ahora debería poder usar AAD para autenticar la aplicación web.

## <a name="add-the-custom-connector-to-powerapps"></a>Agregar el conector personalizado a PowerApps
1. Modifique el archivo de OpenAPI para agregar el objeto `securityDefintions` y la autenticación de AAD usada para la aplicación web. La sección de su archivo de OpenAPI con la propiedad **host** debería tener el siguiente aspecto:

```javascript
// File header should be above here...

"host": "<your-root-url>",
"schemes": [
    "https"         //Make sure this is https!
],
"securityDefinitions": {
    "AAD": {
        "type": "oauth2",
        "flow": "implicit",
        "authorizationUrl": "https://login.windows.net/common/oauth2/authorize",
        "scopes": {}
    }
},

// The rest of the OpenAPI document follows...
```

1. Vaya a [PowerApps](https://web.powerapps.com) y agregue un conector personalizado como se describe en [Registrar y usar conectores personalizados en PowerApps](register-custom-api.md).
2. Una vez que cargado el archivo de OpenAPI, el asistente detecta automáticamente que está usando la autenticación de AAD para la API web.
3. Configure la autenticación de AAD para el conector personalizado.  
   
   * **Client ID** (Id. de cliente): *identificador de cliente de webAPI-CustomAPI*
   * **Secret** (Secreto): *clave de cliente de webAPI-CustomAPI*
   * **Login URL** (Dirección URL de inicio de sesión): `https://login.windows.net`
   * **Resource URL** (URL de recursos): *identificador de cliente de webAPI*
4. Haga clic en **Crear** para crear una conexión al conector personalizado.

## <a name="next-steps"></a>Pasos siguientes
Realice el [tutorial de conectores personalizados en Azure Resource Manager](customapi-azure-resource-manager-tutorial.md).

