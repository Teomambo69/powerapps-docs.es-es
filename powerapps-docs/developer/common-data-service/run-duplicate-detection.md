---
title: Ejecutar detección de duplicados (Common Data Service) | Microsoft Docs
description: Ejecute la detección de duplicados para un registro específico, un tipo de entidad o en las operaciones de creación o actualización.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 42aea9a1348cd7cbda2ce66f2819b34795064121
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155328"
---
# <a name="run-duplicate-detection"></a>Ejecutar detección de duplicados

Hay varios métodos para realizar la detección de duplicados una vez activada la lista y publicadas las reglas de detección de duplicados.  

<a name="BKMK_RetDupwebapi"></a>

## <a name="retrieve-and-detect-duplicates-for-a-specified-record"></a>Recuperar y detectar duplicados para un registro concreto

Detectar y recuperar duplicados:

- Antes de crear una entidad
- Para una entidad existente
- Para otras entidades que se corresponden con reglas de duplicados entre entidades. Por ejemplo, cualquier entidad de cliente potencial que coincida con una entidad de contacto.

### <a name="options"></a>Opciones:

- API web: <xref href="Microsoft.Dynamics.CRM.RetrieveDuplicates?text=RetrieveDuplicates Function" />.
- Servicio de organización: <xref:Microsoft.Crm.Sdk.Messages.RetrieveDuplicatesRequest>


### <a name="example-detect-duplicates-for-a-specified-record-using-web-api"></a>Ejemplo: detectar duplicados de un registro concreto con la API web

El ejemplo siguiente muestra cómo detectar duplicados de un registro concreto mediante la función `RetrieveDuplicates`.

**Solicitud**
```http
GET [Organization URI]/api/data/v9.0/RetrieveDuplicates(BusinessEntity=@p1,MatchingEntityName=@p2,PagingInfo=@p3)?@p1={'@odata.type':'Microsoft.Dynamics.CRM.account','accountid':'0d1156d2-1598-e711-80e8-00155db64062'}&@p2='account'&@p3={'PageNumber':1,'Count':50} HTTP/1.1
If-None-Match: null
OData-Version: 4.0
OData-MaxVersion: 4.0
Content-Type: application/json
Accept: application/json
```
**Respuesta**
```json
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0

{
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts",
    "value": [
        <Omitted for brevity: JSON data for any matching accounts including all properties>
    ]
}
```

<a name="BKMK_DupEntwebapi"></a>

## <a name="detect-duplicates-for-an-entity-type"></a>Detectar duplicados para un tipo de entidad

Enviar un trabajo de detección de duplicados asincrónico que se ejecuta en segundo plano. Los duplicados se detectan mediante las reglas de duplicados publicadas para el tipo de entidad. Los duplicados detectados se almacenan como registros `DuplicateRecord` en Dynamics 365. 

El trabajo de detección de duplicados devuelve un máximo de 5000 duplicados.

### <a name="options"></a>Opciones

- API web: <xref href="Microsoft.Dynamics.CRM.BulkDetectDuplicates?text=BulkDetectDuplicates Action" />.
- Servicio de organización: <xref:Microsoft.Crm.Sdk.Messages.BulkDetectDuplicatesRequest>

### <a name="example-detect-duplicates-for-an-entity-type-using-the-web-api"></a>Ejemplo: detectar duplicados de un tipo de entidad mediante la API web 

El ejemplo siguiente muestra cómo detectar duplicados para un tipo de entidad creando un trabajo asincrónico con la acción `BulkDetectDuplicates`.

**Solicitud**
```http
POST [Organization URI]/api/data/v9.0/BulkDetectDuplicates HTTP/1.1
If-None-Match: null
OData-Version: 4.0
Content-Type: application/json
Accept: application/json
OData-MaxVersion: 4.0

{
    "Query": {
        "@odata.type": "#Microsoft.Dynamics.CRM.QueryExpression",
        "EntityName": "lead"
    },
    "JobName": "jobname1",
    "SendEmailNotification": false,
    "TemplateId": "07B94C1D-C85F-492F-B120-F0A743C540E6",
    "ToRecipients": [],
    "CCRecipients": [],
    "RecurrencePattern": "",
    "RecurrenceStartTime": "2015-07-15T05:30:00Z"
}  
```
**Respuesta**
```json
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0

{
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.BulkDetectDuplicatesResponse",
    "JobId": "efaff068-7598-e711-80e8-00155db64062"
}
```
La solicitud anterior crea un trabajo de detección de duplicados asincrónico cuyo ID de trabajo se devuelve en la respuesta. Puede usar el ID de trabajo devuelto de la solicitud anterior para obtener registros duplicados en un tipo de entidad, tal como se muestra en el ejemplo siguiente.

**Solicitud**
```http
GET [Organization URI]/api/data/v9.0/asyncoperations(efaff068-7598-e711-80e8-00155db64062)/AsyncOperation_DuplicateBaseRecord
If-None-Match: null
OData-Version: 4.0
OData-MaxVersion: 4.0
Content-Type: application/json
Accept: application/json
```
A continuación, se muestra el equivalente FetchXML de la solicitud anterior.

```xml
<fetch>
    <entity name="duplicaterecord">
        <attribute name="owninguser" />
        <attribute name="ownerid" />
        <attribute name="baserecordid" />
        <attribute name="duplicateid" />
        <attribute name="owningbusinessunit" />
        <attribute name="createdon" />
        <attribute name="asyncoperationid" />
        <filter>
            <condition attribute="asyncoperationid" operator="eq" value="efaff068-7598-e711-80e8-00155db64062" />
        </filter>
    </entity>
</fetch>
```

**Respuesta**
```json
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0

{  
   "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#duplicaterecords",
   "value":[  
      {  
         "owninguser":"b3ac4144-6d9a-e711-811c-000d3a75ce72",
         "_ownerid_value":"b3ac4144-6d9a-e711-811c-000d3a75ce72",
         "_baserecordid_value":"3a6fc65b-3f9c-e711-811c-000d3a75ce72",
         "duplicateid":"489a879c-019b-4c28-8539-51ebc850d18f",
         "createdon":"2017-09-19T03:34:25Z",
         "owningbusinessunit":"20a44144-6d9a-e711-811c-000d3a75ce72",
         "_asyncoperationid_value":"efaff068-7598-e711-80e8-00155db64062",
         "_duplicateruleid_value":null,
         "_duplicaterecordid_value":null
      },
      {  
         "owninguser":"b3ac4144-6d9a-e711-811c-000d3a75ce72",
         "_ownerid_value":"b3ac4144-6d9a-e711-811c-000d3a75ce72",
         "_baserecordid_value":"406fc65b-3f9c-e711-811c-000d3a75ce72",
         "duplicateid":"0a4a7dea-1488-4e05-b5eb-c2925ad2925a",
         "createdon":"2017-09-19T03:34:25Z",
         "owningbusinessunit":"20a44144-6d9a-e711-811c-000d3a75ce72",
         "_asyncoperationid_value":"efaff068-7598-e711-80e8-00155db64062",
         "_duplicateruleid_value":null,
         "_duplicaterecordid_value":null
      }
   ]
}
```
El GUID del registro base de se almacena como `baserecordid` en los registros `DuplicateRecord`. `duplicateid` en la respuesta anterior es el identificador único del registro duplicado. `asyncoperationid` es el identificador único del trabajo del sistema que creó ese registro. Y `ownerid` es el identificador único del usuario o del equipo propietario del registro duplicado. Para obtener más información, consulte [Entidad DuplicateRecord](reference/entities/duplicaterecord.md).

> [!NOTE]
>  Antes de crear y ejecutar trabajos de detección de duplicados, asegúrese de que existen reglas de detección de duplicados adecuadas. Dynamics 365 incluye reglas de detección de duplicados predeterminadas para cuentas, contactos y clientes potenciales, pero no para otros tipos de registros. Si desea que el sistema detecte duplicados para otros tipos de registro, deberá crear una nueva regla. Para obtener información sobre cómo crear una regla de detección de duplicados, consulte [Reglas de detección de duplicados](/dynamics365/customer-engagement/admin/set-up-duplicate-detection-rules-keep-data-clean).

<a name="BKMK_CRwebapi"></a>

## <a name="detect-duplicates-during-create-and-update-operations"></a>Detectar duplicados durante operaciones de creación y actualización

La detección de duplicados al crear o actualizar registros solo se aplica cuando la organización ha habilitado la detección de duplicados, la entidad está habilitada para la detección de duplicados y se aplican reglas de detección de duplicados activas. De forma predeterminada, se suprime la detección de duplicados cuando se crean o actualizan registros mediante la API web o el servicio de la organización. 

Para detectar datos duplicados al crear y actualizar registros, consulte:

- WebAPI: [Detección de datos duplicados con la API web](webapi/manage-duplicate-detection-create-update.md)
- Servicio de la organización: [Detección de datos duplicados con el servicio de organización](org-service/detect-duplicate-data.md)

  
### <a name="see-also"></a>Vea también  
 [Mensajes de detección de duplicados](duplicate-detection-messages.md)
