---
title: Introducción a la API de administración en línea para Common Data Service| MicrosoftDocs
description: Proporciona información básica para empezar con la API de Online Management para Common Data Service.
ms.date: 09/30/2019
ms.service: powerapps
ms.topic: conceptual
ms.assetid: c292c148-01f0-41f6-a2fe-7ed05a01a733
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
ms.openlocfilehash: 22ea4e2dc02ee272af3cb8fa916d8d20219b6b6a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752956"
---
# <a name="get-started-with-online-management-api"></a>Introducción a la API de Online Management 

Este tema proporciona información básica para empezar con la API de Online Management para Common Data Service.

## <a name="office-365-admin-roles"></a>Roles de administración de Office 365

Para usar la API de Online Management, debe tener uno de los siguientes roles de administración asignados en el inquilino de Office 365:

- Administrador global
- Administrador de servicios

Para obtener más información sobre estos roles, consulte [Acerca de los roles de administración de Office 365](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).

## <a name="service-url"></a>URL del servicio

La dirección URL del servicio define la dirección del extremo de la API de REST de acceso. Para realizar cualquier operación mediante la API de Online Management, deberá especificar la dirección URL de la solicitud en el siguiente formato:

`{ServiceUrl}/api/v1.2/{resource}`

Por ejemplo, puede pasar la siguiente dirección URL con una solicitud **GET** para recuperar las instancias en el inquilino de Office 365 en Norteamérica:

`https://admin.services.crm.dynamics.com/api/v1.2/instances`


La siguiente tabla muestra la dirección URL del servicio de la API de Online Management para los centros de datos de Office 365 en todo el mundo.

|Ubicación | URL del servicio |
|---------|-------------|
|Norteamérica | https://admin.services.crm.dynamics.com |
|Norteamérica 2 | https://admin.services.crm9.dynamics.com |
|Europa, Oriente Medio y África (EMEA) | https://admin.services.crm4.dynamics.com |
|Asia-Pacífico (APAC) | https://admin.services.crm5.dynamics.com |
|Oceanía | https://admin.services.crm6.dynamics.com |
|Japón (JPN) | https://admin.services.crm7.dynamics.com |
|Sudamérica | https://admin.services.crm2.dynamics.com |
|India (IND) | https://admin.services.crm8.dynamics.com |
|Canadá | https://admin.services.crm3.dynamics.com |
|Reino Unido (UK) | https://admin.services.crm11.dynamics.com |
|Francia | https://admin.services.crm12.dynamics.com |

## <a name="standard-headers"></a>Encabezados estándar

La API de Online Management tiene los siguientes encabezados estándar de solicitud y respuesta.

### <a name="request-headers"></a>Encabezados de solicitud

| Encabezado | Tipo | Descripción  |
|--------|------|--------------|
|**Accept-Language**|String|Especifica el idioma preferido para la respuesta. Para obtener más información sobre el encabezado: [aceptación de idioma (documentos web de MDN)](https://developer.mozilla.org/docs/Web/HTTP/Headers/Accept-Language)|
|**Autorización**|String|Especifica las credenciales de inicio de sesión para autenticar a un usuario con el servicio de la API de administración en línea. Para obtener más información sobre el encabezado: [Autorización (documentos web de MDN)](https://developer.mozilla.org/docs/Web/HTTP/Headers/Authorization)|

Vea [Autenticar para usar la API de administración en línea](authentication.md) para saber sobre la configuración de estos encabezados en la solicitud.

### <a name="response-headers"></a>Encabezados de respuesta

| Encabezado | Descripción  |
|--------|--------------|
|**Operation-Location**|Para las operaciones de ejecución prolongada, especifique la ubicación de la consulta de operaciones para comprobar su estado. Por ejemplo:<br />`https://admin.services.crm.dynamics.com/operations/{operationid}`|
|**Retry-After**|Para las operaciones de ejecución prolongada, especifique el período recomendado en segundos después del cual ver el estado de la operación de nuevo. Por ejemplo: **30**|
    
### <a name="related-topics"></a>Temas relacionados  

[Autenticación para usar la API de Online Management](authentication.md)

[Operaciones compatibles con la API Online Management](operations-supported.md)

[Referencia de la API de Online Management](/rest/api/admin.services.crm.dynamics.com)
