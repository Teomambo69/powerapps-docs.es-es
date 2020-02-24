---
title: Modificar el código para usar el servicio de detección global (Common Data Service) | Microsoft Docs
description: Actualice el código de su aplicación para realizar llamadas del servicio de detección utilizando una API RESTful moderna.
ms.custom: ''
ms.date: 1/16/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: bpevans
ms.author: bevans
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ca4a6ad8d86999a878ce51d8fffe08039230a12f
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2975900"
---
# <a name="modify-your-code-to-use-global-discovery-service"></a>Modificar su código para usar el servicio de detección global

Su aplicación puede utilizar las API del servicio de detección para descubrir instancias de organización empresarial a las que el usuario de la aplicación tiene acceso. Si su aplicación actualmente usa la API del servicio de organización en el extremo 2011 SOAP para descubrir instancias de la organización, puede seguir los pasos en este tema y convertir su aplicación para acceder a los detalles de la organización con la OData V4 RESTful API con la URL global del servicio de detección. Si su aplicación accede al servicio de detección con la URL del servicio de detección regional, deberá cambiar el código de la aplicación de usar la URL regional a la URL del servicio de detección global.

Puede encontrar una descripción detallada del uso del servicio de detección con la RESTful API en la página [Detectar la URL de su organización](/powerapps/developer/common-data-service/webapi/discover-url-organization-web-api).

> [!IMPORTANT]
> Al acceder al servicio de detección, se recomienda encarecidamente que su aplicación utilice el extremo de servicio de detección *global* (https://globaldisco.crm.dynamics.com), en lugar del extremo del servicio de detección *regional*, que será quedará [obsoleto](/power-platform/important-changes-coming#regional-discovery-service-is-deprecated) el 2 de marzo de 2020. El servicio de detección global solo está disponible cuando se utiliza la API RESTful.

El resto de este documento describe los cambios que pueden ser necesarios para llamar al servicio de detección utilizando la API RESTful.

## <a name="authentication"></a>Autenticación
Para acceder al servicio de detección con la API RESTful se requiere autenticación con un token de acceso de OAuth 2.0.
Si el código de su aplicación utiliza tokens SAML de WS-Trust para la autenticación, debe cambiar el código de su aplicación para adquirir un token Oauth 2.0 de Azure Active Directory (AD), y luego agregar ese token en el encabezado de autorización de las llamadas a la API del servicio de detección. Más información: [Uso de OAuth con Common Data Service](../authenticate-oauth.md).

## <a name="odata-api-calls"></a>Llamadas API de OData
Los ejemplos de solicitudes HTTP que se muestran a continuación son compatibles con la API RESTful del servicio de detección. Estos ejemplos utilizan la API de instancias para devolver los mismos datos de organización que <xref:Microsoft.Xrm.Sdk.Discovery.RetrieveOrganizationsRequest> y las solicitudes de mensajes de <xref:Microsoft.Xrm.Sdk.Discovery.RetrieveOrganizationRequest> de la API del servicio de organización.

-    Obtenga todas las instancias para el usuario en todas las regiones.
```http  
GET https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances
```  
-    Obtenga todas las instancias para el usuario en una región específica.
```http  
GET  https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances(Region={region})
```
Respuesta
```javascript
{
  "value":[
    {
      "Id":"<GUID>",
      "UniqueName":"myorg",
      "UrlName":"orgurlname",
      "FriendlyName":"My Org",
      "State":0,
      "Version":"<Version>",
      "Url":"https://orgurlname.crm.dynamics.com",
      "ApiUrl":"https://orgurlname.api.crm.dynamics.com"
    }
  ]
}
```

-    Obtener una sola instancia por identificador
```http  
GET https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances(<guid>)
```  
-    Obtener una sola instancia por nombre único
```http  
GET https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances(UniqueName='myorg')  
```  

Respuesta
```javascript
{
  "Id":"<GUID>",
  "UniqueName":"myorg",
  "UrlName":"orgurlname",
  "FriendlyName":"My Org",
  "State":0,
  "Version":"<Version>",
  "Url":"https://orgurlname.crm.dynamics.com",
  "ApiUrl":"https://orgurlname.api.crm.dynamics.com"
}
```

## <a name="mapping-of-fields"></a>Asignación de campos
La tabla que se muestra a continuación muestra la asignación de campo en las respuestas devueltas del servicio de detección cuando se utilizan las dos API. Estas son aplicables a todas las llamadas de ejemplo anteriores.

Campo de respuesta (extremo de SOAP) |    Campo de respuesta (extremo de OData V4 RESTful)
------------------------------------|---------------------------------
Extremos[WebApplication] | Dirección URL
Extremos[OrganizationService]  | {ApiUrl}/XRMServices/2011/Organization.svc
Extremos[OrganizationDataService] |{ApiUrl}//XRMServices/2011/OrganizationData.svc
FriendlyName|FriendlyName
OrganizationId|Id.
OrganizationVersion|Versión
Estado | Estado<br/><ul><li>0: Habilitada</li><li>1: Deshabilitada</li><ul>
UniqueName|UniqueName
UrlName|UrlName

## <a name="deprecated-api-call"></a>Llamada de API obsoleta
El mensaje de API de servicio de organización GetUserIdByExternalId no es compatible con la API RESTful.

## <a name="see-also"></a>Vea también
[Servicios de detección](/powerapps/developer/common-data-service/discovery-service)

[Usar la API web de Common Data Service](/powerapps/developer/common-data-service/webapi/discover-url-organization-web-api)
