---
title: Uso de Azure Active Directory con un conector personalizado | Microsoft Docs
description: "Aprenda a crear un conector personalizado para Azure Resource Manager, con autenticación de Azure Active Directory."
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
ms.date: 05/03/2017
ms.author: mblythe
ms.openlocfilehash: b3df99a335947b0472b9230090e6a49fcea0f799
ms.sourcegitcommit: 68eee592c351688e5d0bd458f33a70be507fa53f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2018
---
# <a name="use-azure-active-directory-with-a-custom-connector-in-powerapps"></a>Uso de Azure Active Directory con un conector personalizado en PowerApps
Azure Resource Manager (ARM) permite administrar los componentes de una solución en Azure: componentes como las bases de datos, las máquinas virtuales y las aplicaciones web. En este tutorial se muestra cómo habilitar la autenticación en Azure Active Directory, registrar una de las API de ARM, como un conector personalizado, y conectarse a él en PowerApps. Esto resultara útil si desea administrar los recursos de Azure directamente desde una aplicación. Para más información sobre ARM, consulte [Introducción a Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).

## <a name="prerequisites"></a>Requisitos previos
* Una [suscripción de Azure](https://azure.microsoft.com/free/).
* Una [cuenta de PowerApps](https://powerapps.microsoft.com).
* El [archivo de OpenAPI de ejemplo](http://pwrappssamples.blob.core.windows.net/samples/AzureResourceManager.json) que se usa en este tutorial.

## <a name="enable-authentication-in-azure-active-directory"></a>Habilitar la autenticación en Azure Active Directory
En primer lugar, se debe crear una aplicación de Azure Active Directory (AAD) que llevará a cabo la autenticación al llamar al punto de conexión de API de ARM.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).  Si tiene más de un inquilino de Azure Active Directory, asegúrese de que ha iniciado sesión en el directorio correcto, como indica el nombre de usuario en la esquina superior derecha.
   
    ![Nombre de usuario](./media/customapi-azure-resource-manager-tutorial/current-user.png)
2. En el menú izquierdo, haga clic en **Más servicios**.  En el cuadro de texto **Filtro**, escriba **Azure Active Directory** y haga clic en **Azure Active Directory**.
   
    ![Azure Active Directory](./media/customapi-azure-resource-manager-tutorial/azureaad.png)
   
    Se abre la hoja Azure Active Directory.   
3. En el menú de la hoja Azure Active Directory, haga clic en **Registros de aplicaciones**.
   
    ![Registros de aplicaciones](./media/customapi-azure-resource-manager-tutorial/azureapplication.png)
4. En la lista de aplicaciones registradas, haga clic en **Agregar**.
   
    ![Botón Agregar](./media/customapi-azure-resource-manager-tutorial/add-app-btn.png)   
5. Escriba un nombre para la aplicación, deje **Aplicación web o API** seleccionado y, para **Dirección URL de inicio de sesión**, escriba `https://login.windows.net`.  Haga clic en **Crear**.  
   
    ![Formulario de nueva aplicación](./media/customapi-azure-resource-manager-tutorial/newapplication.png)
6. Haga clic en la nueva aplicación en la lista.
   
    ![Nueva aplicación en la lista](./media/customapi-azure-resource-manager-tutorial/newapplication2.png)
   
    Se abre la hoja Aplicación registrada.  Tome nota del valor en **Id. de la aplicación**.  Lo necesitará más adelante.
7. También se debería haber abierto la hoja Configuración.  De lo contrario, haga clic en el botón **Configuración**.
   
    ![Botón Configuración](./media/customapi-azure-resource-manager-tutorial/settings-btn.png)
8. En la hoja Configuración, haga clic en **Direcciones URL de respuesta**. En la lista de direcciones URL, agregue `https://msmanaged-na.consent.azure-apim.net/redirect` y haga clic en **Guardar**.
   
    ![Direcciones URL de respuesta](./media/customapi-azure-resource-manager-tutorial/reply-urls.png)
9. De nuevo en la hoja Configuración, haga clic en **Permisos necesarios**.  En la hoja Permisos necesarios, haga clic en **Agregar**.
   
    ![Permisos necesarios](./media/customapi-azure-resource-manager-tutorial/permissions.png)
   
    Se abre la hoja Agregar acceso de API.
10. Haga clic en **Seleccionar una API**. En la hoja que se abre, haga clic en la opción para Azure Service Management API y haga clic en **Seleccionar**.
    
    ![Seleccionar una API](./media/customapi-azure-resource-manager-tutorial/permissions2.png)
11. Haga clic en **Seleccionar permisos**.  En *Permisos delegados*, haga clic en **Access Azure Service Management as organization users** (Acceder a administración de servicios de Azure como usuarios de la organización) y haga clic en **Seleccionar**.
    
    ![Permisos delegados](./media/customapi-azure-resource-manager-tutorial/permissions3.png)
12. En la hoja Agregar acceso de API, haga clic en **Listo**.
13. De nuevo en la hoja Configuración, haga clic en **Claves**.  En la hoja Claves, escriba una descripción para la clave, seleccione un período de expiración y haga clic en **Guardar**.  Se mostrará la nueva clave.  Tome nota del valor de la clave, ya que también será necesario más adelante.  Ahora puede cerrar Azure Portal.
    
    ![Crear una clave](./media/customapi-azure-resource-manager-tutorial/configurekeys.png)

## <a name="add-the-connection-in-powerapps"></a>Agregar la conexión en PowerApps
Ahora que la aplicación de AAD está configurada, agreguemos el conector personalizado.

1. En [powerapps.com](https://web.powerapps.com), en el menú de la izquierda, seleccione **Conexiones**. Seleccione los puntos suspensivos (**...** ) y **Manage custom connectors** (Administrar conectores personalizados) en la esquina superior derecha.
   
     > [!TIP]
> Si no encuentra dónde se administran los conectores personalizados en el explorador de algún dispositivo móvil, podría estar en un menú de la esquina superior izquierda.
   
    ![Create custom connector (Crear conector personalizado)](./media/customapi-azure-resource-manager-tutorial/managecustomapi.png)  
2. Seleccione **Create custom connector** (Crear conector personalizado).
   
    ![Propiedades del conector personalizado](./media/customapi-azure-resource-manager-tutorial/newcustomapi.png)
3. Escriba un nombre para la conexión y cargue el [archivo de OpenAPI de ARM de ejemplo](http://pwrappssamples.blob.core.windows.net/samples/AzureResourceManager.json).  Haga clic en **Continuar**.  
   
    ![Conectarse a un nuevo punto de conexión de API](./media/customapi-azure-resource-manager-tutorial/createcustom.png)
4. En la siguiente pantalla, dado que el archivo de OpenAPI usa nuestra aplicación de AAD para la autenticación, es necesario proporcionar a PowerApps algo de información sobre nuestra aplicación.  En **Client id** (Id. de cliente), escriba el valor de **Id. de la aplicación** de AAD que anotó antes.  Como secreto del cliente, use la **clave**.  Y, por último, para **Resource URL** (URL de recursos), escriba `https://management.core.windows.net/`.
   
    > [!IMPORTANT]
> Asegúrese de escribir la dirección URL de recursos exactamente como se indica antes, incluida la barra diagonal final.
   
    ![Configuración de OAuth](./media/customapi-azure-resource-manager-tutorial/oauthsettings.png)
5. El conector personalizado ya está registrado y se puede consumir en PowerApps o Microsoft Flow.
   
    ![Conector personalizado agregado](./media/customapi-azure-resource-manager-tutorial/createdcustomapi.png)
   
    > [!NOTE]
> El archivo de OpenAPI de ejemplo no define el conjunto completo de operaciones de ARM y actualmente solo contiene la operación de [enumeración de todas las suscripciones](https://msdn.microsoft.com/library/azure/dn790531.aspx).  Puede editar este archivo de OpenAPI o crear otro con el [editor en línea de OpenAPI](http://editor.swagger.io/). Este proceso sirve para acceder a cualquier API de RESTful autenticada con AAD.

## <a name="next-steps"></a>Pasos siguientes
Para información más detallada sobre cómo crear una aplicación, consulte [Crear una aplicación a partir de datos](get-started-create-from-data.md).

Para información más detallada sobre cómo usar un flujo en una aplicación, consulte [Start a flow in an app](using-logic-flows.md) (Iniciar un flujo en una aplicación).

Para plantear preguntas o hacer comentarios acerca de los conectores personalizados, [únase a nuestra comunidad](https://aka.ms/powerapps-community).

