---
title: Detección de datos duplicados con la API web (Common Data Service)| Microsoft Docs
description: Lea cómo detectar duplicados con el encabezado MSCRM.SuppressDuplicateDetection y la API web de Common Data Service
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: AE107774-4545-44B4-94C8-A0271EFA7876
caps.latest.revision: 11
author: susikka
ms.author: susikka
manager: shujoshi
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 73cfe1f28eb95e87e4aedf7eed9e51710ba9b8b2
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "3109071"
---
# <a name="detect-duplicate-data-using-the-web-api"></a>Detección de datos duplicados con la API web

La API web de Common Data Service le permite detectar registros duplicados de un registro existente para mantener la integridad de los datos. Para obtener información detallada sobre Detección de datos duplicados usando código, consulte [Detectar datos duplicados con código](../detect-duplicate-data-with-code.md) 

## <a name="detect-duplicates-during-create-operation"></a>Detectar duplicados durante las operaciones de creación

Utilice el encabezado `MSCRM.SuppressDuplicateDetection` durante una solicitud `POST` para detectar la creación de un registro duplicado de un registro existente. El valor asignado al encabezado `MSCRM.SuppressDuplicateDetection` determina si se puede completar la operación de crear o actualizar:

- `true`: Crear o actualizar el registro, si se encuentra un duplicado.
- `false`: no crear o actualizar el registro si se encuentra un duplicado.

> [!NOTE]
> No es obligatorio pasar los parámetros opcionales de `CalculateMatchCodeSynchronously`. Los códigos de coincidencia usados para detectar duplicados se calculan de forma sincrónica independientemente del valor pasado en este parámetro.

Use encabezado de preferencia `MSCRM.SuppressDuplicateDetection` y establezca el valor en `false` en la solicitud de la API de la Web.


> [!NOTE]
> Asegúrese de que existen reglas de detección de duplicados adecuadas. Common Data Service incluye reglas de detección de duplicados predeterminadas para cuentas, contactos y clientes potenciales, pero no para otros tipos de registros. Si desea que el sistema detecte duplicados para otros tipos de registro, deberá crear una nueva regla. <br/>- Para obtener información sobre cómo crear una regla de detección de duplicados usando la interfaz de usuario, consulte [Configurar reglas de detección de duplicados para mantener limpios los datos](/dynamics365/customer-engagement/admin/set-up-duplicate-detection-rules-keep-data-clean).<br/>- Para obtener información sobre cómo crear reglas de detección de duplicados usando código, [consulte Entidades de regla de duplicados](../duplicaterule-entities.md). 



<a name="bkmk_create"></a>

###  <a name="example-detect-duplicates-during-create-operation-using-the-web-api"></a>Ejemplo: Detectar duplicados durante la operación de crear mediante la API web

El ejemplo siguiente muestra cómo detectar duplicados durante las operaciones `Create` y `Update` mediante el encabezado `MSCRM.SuppressDuplicateDetection` de la solicitud de la API web.

**Solicitud**
```http
POST [Organization URI]/org1/api/data/v9.0/leads HTTP/1.1
If-None-Match: null
OData-Version: 4.0
OData-MaxVersion: 4.0
Content-Type: application/json
Accept: application/json
MSCRM.SuppressDuplicateDetection: false

{
    "firstname":"Monte",
    "lastname":"Orton",
    "emailaddress1":"monteorton@example.com"
}
```
Si ya existe un registro de cliente potencial con el mismo atributo `emailaddress1`, se devuelve la siguiente respuesta.

**Respuesta**
```json
HTTP/1.1 500 Internal Server Error  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0

{
    "error": {
        "code": "0x80040333",
        "message": "A record was not created or updated because a duplicate of the current record already exists.",
        "innererror": {
            "message": "A record was not created or updated because a duplicate of the current record already exists.",
            "type": "Microsoft.Crm.CrmException",
            [ Stack Trace and internal exception details omitted for brevity]
        }
    }
}
```
Asigne el valor `true` al encabezado `MSCRM.SuppressDuplicateDetection` para permitir la creación de un registro duplicado.

<a name="bkmk_update"></a>

## <a name="detect-duplicates-during-update-operation"></a>Detectar duplicados durante las operaciones de actualización

Establezca el valor del encabezado `MSCRM.SuppressDuplicateDetection` como `false` en la solicitud `PATCH` para evitar la creación de un registro duplicado durante la operación de actualizar. De forma predeterminada, se suprime la detección de duplicados cuando se actualizan registros mediante la API web.

###  <a name="example-detect-duplicates-during-update-operation-using-the-web-api"></a>Ejemplo: Detectar duplicados durante la operación de actualización mediante la API web

El ejemplo que aparece a continuación intenta actualizar un registro de entidad cliente potencial existente que incluye el mismo valor del atributo `emailaddress1` que un registro existente.

**Solicitud**
```http
PATCH [Organization URI]/api/data/v9.0/leads(c4567bb6-47a3-e711-811b-e0071b6ac1b1) HTTP/1.1
If-None-Match: null
OData-Version: 4.0
OData-MaxVersion: 4.0
Content-Type: application/json
Accept: application/json
MSCRM.SuppressDuplicateDetection: false

{
    "firstname":"Monte",
    "lastname":"Orton",
    "emailaddress1":"monteorton@example.com"
}
```  

**Respuesta**
```json  
HTTP/1.1 500 Internal Server Error  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0

{
    "error": {
        "code": "0x80040333",
        "message": "A record was not created or updated because a duplicate of the current record already exists.",
        "innererror": {
            "message": "A record was not created or updated because a duplicate of the current record already exists.",
            "type": "Microsoft.Crm.CrmException",
            [ Stack Trace and internal exception details omitted for brevity]
        }
    }
}
```

### <a name="see-also"></a>Vea también

[Detección de datos duplicados con el servicio de organización](../org-service/detect-duplicate-data.md)