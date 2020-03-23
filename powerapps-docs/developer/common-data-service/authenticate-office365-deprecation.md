---
title: Uso de la autenticación de Office365 con el protocolo de seguridad WS-Trust (Common Data Service) | Microsoft Docs
description: Describe la obsolescencia del protocolo de seguridad WS-Trust y los cambios en el código de autenticación necesarios en las aplicaciones.
ms.custom: ''
ms.date: 02/05/2020
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: phecke
ms.author: pehecke
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 734d64fe24e7fbaec56109987fc8f0bb9163f5c8
ms.sourcegitcommit: 4f2e9e8f9bd3204ca9eee9e2a46f797c957c55ec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2020
ms.locfileid: "3029796"
---
# <a name="use-of-office365-authentication-with-the-ws-trust-security-protocol"></a>Uso de la autenticación de Office365 con el protocolo de seguridad WS-Trust

El uso del protocolo de seguridad de autenticación WS-Trust al conectarse a Common Data Service ya no se recomienda y ha quedado en desuso; consulte el [anuncio](/power-platform/important-changes-coming#deprecation-of-office365-authentication-type-and-organizationserviceproxy-class-for-connecting-to-common-data-service). 

Este cambio afecta a las aplicaciones cliente personalizadas que usan autenticación "Office365" y las clases [Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy](/dotnet/api/microsoft.xrm.sdk.client.organizationserviceproxy) o [Microsoft.Xrm.Tooling.Connector.CrmServiceClient](/dotnet/api/microsoft.xrm.tooling.connector.crmserviceclient). Si sus aplicaciones usan este tipo de protocolo de autenticación y API, continúe leyendo a continuación para obtener más información sobre los cambios de autenticación recomendados que se realizarán en el código de su aplicación.

## <a name="how-do-i-know-if-my-code-or-application-is-using-ws-trust"></a>¿Cómo sé si mi código o aplicación está usando WS-Trust?

Primero y más importante, este cambio **solamente** afecta las aplicaciones cliente que se conectan a Common Data Service. No afecta a los complementos personalizados, las actividades de flujo de trabajo o las conexiones de servicio locales/IFD.

- Si su código emplea credenciales de cuenta de usuario y contraseña para autenticación con Common Data Service o una aplicación, es probable que esté utilizando el protocolo de seguridad WS-Trust. Algunos ejemplos se muestran a continuación, aunque esta lista no es totalmente inclusiva.

  - Cuando use la clase [CrmServiceClient](/dotnet/api/microsoft.xrm.tooling.connector.crmserviceclient) con una cadena de conexión:

    `connectionString="AuthType=Office365; Username=jsmith\@contoso.onmicrosoft.com;Password=passcode;Url=https://contoso.crm.dynamics.com"`

  - Cuando use constructores de clase [OrganizationServiceProxy](/dotnet/api/microsoft.xrm.sdk.client.organizationserviceproxy):


```csharp
using (OrganizationServiceProxy organizationServiceProxy =
    new OrganizationServiceProxy(serviceManagement, clientCredentials)
{ ... }
```

- Si está utilizando la clase `OrganizationServiceProxy` en absoluto en su código, está utilizando WS-Trust.

- Si está usando [CrmServiceClient](/dotnet/api/microsoft.xrm.tooling.connector.crmserviceclient).`OrganizationServiceProxy` en su código, está utilizando WS-Trust.

## <a name="what-should-i-do-to-fix-my-application-code-if-affected"></a>¿Qué debo hacer para corregir el código de mi aplicación si está afectado?

Hay formas muy directas de modificar el código de su aplicación para usar la interfaz de conexión recomendada para autenticación con Common Data Service.

- Si su código usa una instancia [Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy](/dotnet/api/microsoft.xrm.sdk.client.organizationserviceproxy):

  Si está pasando la instancia `OrganizationServiceProxy` por varios métodos, o devolviendo la instancia de una función, reemplace todas las apariciones del tipo `OrganizationServiceProxy` con la interfaz [IOrganizationService](/dotnet/api/microsoft.xrm.sdk.iorganizationservice?view=dynamics-general-ce-9). Esta interfaz expone todos los métodos principales utilizados para comunicarse con Common Data Service.

  Al invocar al constructor, se recomienda agregar el paquete NuGet [Microsoft.CrmSdk.XrmTooling.CoreAssembly](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CoreAssembly/) a su proyecto y reemplazar todo uso de los constructores de clase `OrganizationServiceProxy` con los constructores de clase [CrmServiceClient](/dotnet/api/microsoft.xrm.tooling.connector.crmserviceclient). Sin embargo, deberá modificar su patrón de codificación aquí, por simplicidad `CrmServiceClient` admite cadenas de conexión además de constructores complejos y la capacidad de proporcionar controladores de autenticación externos. `CrmServiceClient` implementa `IOrganizationService`, por tanto, su nuevo código de autenticación será portátil para el resto del código de su aplicación. Puede encontrar ejemplos sobre el uso de `CrmServiceClient` en el repositorio [PowerApps-Samples](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23).

- Si su código está usando [CrmServiceClient](/dotnet/api/microsoft.xrm.tooling.connector.crmserviceclient) con el tipo de autenticación "Office365":

    Un ejemplo de esto es una cadena de conexiones que tiene este aspecto:

    `connectionString = "AuthType=Office365;Username=jsmith@contoso.onmicrosoft.com;Password=passcode;Url=https://contoso.crm.dynamics.com"`

    Del mismo modo, también podría usar un constructor `CrmServiceClient` y pasarlo en `AuthType.Office365`.

    Tienes dos opciones para tratar con esto.<p/>

    - Cambie a usar una cadena de conexión basada en Oauth. Dicha cadena de conexión tiene este aspecto:

        `connectionString = "AuthType=OAuth;Username=jsmith@contoso.onmicrosoft.com;
    Password=passcode;Url=https://contosotest.crm.dynamics.com;AppId=51f81489-12ee-4a9e-aaae-a2591f45987d;
    RedirectUri=app://58145B91-0C36-4500-8554-080854F2AC97;LoginPrompt=Auto"`

        Esta será su forma más rápida de actualizar el código. Tenga en cuenta que LoginPrompt se puede establecer en "nunca" para simular la forma en que funcionó el comportamiento de Office 365.

        AppId y RedirectUri proporcionados anteriormente son ejemplos de valores de registro de la aplicación en funcionamiento. Estos valores funcionan en todas partes donde se implementan nuestros servicios en línea. Sin embargo, se proporcionan aquí como ejemplo y le recomendamos que cree su propio registro de aplicación en Azure Active Directory (AAD) para aplicaciones que se ejecutan en su inquilino.<p/>

    - Cuando lo anunciemos, actualice al último paquete NuGet [Microsoft.CrmSdk.XrmTooling.CoreAssembly](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CoreAssembly/) que incluye soporte para redireccionamiento automático. Esta biblioteca redirigirá un tipo de autenticación de Office365 a Oauth y usará la URI de Id. de aplicación y redireccionamiento de ejemplo automáticamente. Esta capacidad está planeada para la versión 9.2.x del paquete Microsoft.CrmSdk.XrmTooling.CoreAssembly.

- Si está accediendo a la propiedad [CrmServiceClient](/dotnet/api/microsoft.xrm.tooling.connector.crmserviceclient).`OrganizationServiceProxy` :

     Elimine todo uso de esa propiedad en su código. `CrmServiceClient` implementas `IOrganizationService` y expone todo lo que se puede configurar para el proxy de servicio de la organización.

> [!IMPORTANT]
> Si no puede iniciar sesión con ID de usuario/Contraseña incluso usando Oauth, si su inquilino y usuario están configurados en Azure Active Directory para acceso condicional y/o autenticación multifactor es necesaria, no podrá utilizar los flujos de ID de usuario/contraseña en un formato no interactivo. Para esas situaciones, debe usar un usuario principal de servicio para autenticarse con Common Data Service.<p/>
Para ello, primero debe registrar el usuario de la aplicación (Principal de servicio) en Azure Active Directory. Puedes averigua cómo hacer esto [aquí](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal). Durante el registro de la aplicación, deberá crear ese usuario en Common Data Service y conceder permisos. Esos permisos pueden otorgarse directa o indirectamente agregando el usuario de la aplicación a un equipo al que se le han otorgado permisos en Common Data Service. Puede encontrar más información sobre cómo configurar un usuario de la aplicación para autenticarse con Common Data Service [aquí](/powerapps/developer/common-data-service/use-single-tenant-server-server-authentication).

## <a name="need-help"></a>¿Necesita ayuda?

Estaremos supervisando los [foros](https://powerusers.microsoft.com/t5/Power-Apps-Component-Framework/bd-p/pa_component_framework) de la comunidad ALM y ProDev de Power Apps. Eche un vistazo allí para obtener ayuda sobre cómo resolver diversos problemas o publicar una pregunta.
