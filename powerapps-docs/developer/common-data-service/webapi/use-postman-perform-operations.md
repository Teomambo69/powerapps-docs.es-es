---
title: Usar Postman para realizar operaciones con la API web (Common Data Service para aplicaciones)| MicrosoftDocs
description: Aprenda a crear y enviar a solicitudes web API mediante envío.
ms.custom: ''
ms.date: 03/22/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: AB50128B-D8E3-47A3-A0F8-9594EF6B7022
caps.latest.revision: 7
author: susikka
ms.author: susikka
manager: shujoshi
search.audienceType:
- developer
search.app:
- D365CE
ms.openlocfilehash: c651dbc8ba553192f4ff3b09b84518684ac4b866
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749747"
---
# <a name="use-postman-to-perform-operations-with-the-web-api"></a>Use Postman para realizar operaciones con la API web

Use el envío para crear y enviar las solicitudes web API y ver respuestas. Este tema describe cómo usar Postman para crear las solicitudes web API que realizan operaciones de creación, recuperación, actualización y eliminación (CRUD) y usar funciones y acciones.

> [!IMPORTANT]
> Deberá tener un entorno creado mediante los pasos descritos en [Configure un entorno Postman](setup-postman-environment.md)

El entorno creado mediante las instrucciones en [Configure un entorno de Postman](setup-postman-environment.md), crea `{{webapiurl}}` una variable de Postman que proporciona la dirección URL base para atender solicitudes. Anexar a esta variable para definir la dirección URL de las solicitudes.

Los métodos y valores HTTP que use dependen del tipo de operación que desea realizar. En las siguientes secciones se muestran ejemplos de operaciones comunes.

## <a name="retrieve-multiple-records"></a>Recuperar múltiples registros

Use la solicitud `GET` para recuperar un conjunto de opciones globales. El siguiente ejemplo devuelve las primeras tres registros de cuenta.

> [!NOTE]
> La solicitudes web API deben incluir determinados encabezados HTTP. Cada solicitud debe incluir el valor del encabezado `Accept` de `application/json`, aunque no se espere ningún cuerpo de la respuesta. La versión actual de OData es `4.0`, por lo que encabezado de incluyen `OData-Version: 4.0`. Incluya el encabezado `OData-MaxVersion` de forma que no haya ambigüedades sobre la versión cuando haya nuevos lanzamientos de OData. Más información: [Ecabezados HTTP](compose-http-requests-handle-errors.md#http-headers)

**Ejemplo**


`GET` `{{webapiurl}}accounts?$select=name,accountnumber&$top=3`

![Recuperar varios registros mediante Postman](media/postman-retrieve-multiple.png "Recuperar varios registros mediante Postman")

El cuerpo de la respuesta se parecerá a esto:

```json
{
    "@odata.context": "https://yourorg.crm.dynamics.com/api/data/v9.0/$metadata#accounts(name,accountnumber)",
    "value": [
        {
            "@odata.etag": "W/\"2291741\"",
            "name": "Contoso Ltd",
            "accountnumber": null,
            "accountid": "9c706dc8-d2f5-e711-a956-000d3a328903"
        },
        {
            "@odata.etag": "W/\"2291742\"",
            "name": "Fourth Coffee",
            "accountnumber": null,
            "accountid": "a2706dc8-d2f5-e711-a956-000d3a328903"
        },
        {
            "@odata.etag": "W/\"2291743\"",
            "name": "Contoso Ltd",
            "accountnumber": null,
            "accountid": "9c3216b8-3efb-e711-a957-000d3a328903"
        }
    ]
}
```

Para obtener más información, consulte [Consulta de datos mediante la API web](query-data-web-api.md).

## <a name="retrieve-a-particular-record"></a>Recupere un registro en particular

Use la solicitud `GET` para recuperar un conjunto de opciones globales. El siguiente ejemplo recupera dos propiedades de una cuenta específica y expande información sobre el contacto principal relacionados para incluir su nombre completo.


`GET` `{{webapiurl}}accounts(`*&lt;accountid&gt;*`)?$select=name,accountnumber&$expand=primarycontactid($select=fullname)`

![Recuperar un registro mediante Postman](media/postman-retrieve-record.png "Recuperar un registro mediante Postman")

El cuerpo de la respuesta se parecerá a esto:

```json
{
    "@odata.context": "https://yourorg.crm.dynamics.com/api/data/v9.0/$metadata#accounts(name,accountnumber,primarycontactid(fullname))/$entity",
    "@odata.etag": "W/\"2291742\"",
    "name": "Fourth Coffee",
    "accountnumber": null,
    "accountid": "a2706dc8-d2f5-e711-a956-000d3a328903",
    "primarycontactid": {
        "@odata.etag": "W/\"1697263\"",
        "fullname": "Susie Curtis",
        "contactid": "a3706dc8-d2f5-e711-a956-000d3a328903"
    }
}
```
Para obtener más información, consulte [Recuperar una entidad usando la API web](retrieve-entity-using-web-api.md).

## <a name="create-a-record"></a>Crear un registro

Use una solicitud `POST` para enviar datos para crear una entidad. Establezca la dirección URL del nombre fijado para entidad, en este caso, `accounts`, y establezca los encabezados como se muestra aquí.

`POST` `{{webapiurl}}accounts`

![Crear un nuevo registro mediante la API web](media/postman-create-records.png "Crear un nuevo registro mediante la API web")

Establezca el cuerpo de la solicitud con información sobre la cuenta a crear.

![Cuerpo de la solicitud para crear el registro usando la API web](media/postman-create-record-body.png "Cuerpo de la solicitud para crear el registro usando la API web")

Cuando envía esta solicitud, el cuerpo estará vacío, pero el identificador de la cuenta creada estará en el valor encabezado `OData-EntityId`.

Para obtener más información, consulte [Recuperar una entidad usando la API web](create-entity-web-api.md).

## <a name="update-a-record"></a>Actualizar un registro

Use el método `PATCH` para actualizar un registro de entidad, como se muestra aquí.

`PATCH` `{{webapiurl}}accounts(`*&lt;accountid&gt;*`)`

![Actualizar un registro usando la API web](media/postman-update-record.png "Actualizar un registro usando la API web")

Cuando envía esta solicitud, la respuesta estará vacía, pero el identificador de la cuenta actualizada estará en el valor encabezado `OData-EntityId`.

Más información: [Crear y actualizar definiciones de entidad mediante la API web](update-delete-entities-using-web-api.md).

## <a name="delete-a-record"></a>Eliminar registros

Use el método `DELETE` para eliminar un registro existente.

`DELETE` `{{webapiurl}}accounts(`*&lt;accountid&gt;*`)`

![Eliminar un registro usando la API web](media/postman-delete-record.png "Eliminar un registro usando la API web")

Cuando envíe esta solicitud, el registro de cuenta con lo dado `accountid` obtiene eliminar.

Más información: [Crear y actualizar definiciones de entidad mediante la API web](update-delete-entities-using-web-api.md).

## <a name="use-a-function"></a>Use una función

Use una solicitud `GET` con las funciones enumeradas en [Referencia de función de la API Web](https://docs.microsoft.com/dynamics365/customer-engagement/web-api/functions?view=dynamics-ce-odata-9) para realizar operaciones que pueden reutilizarse con API web. El siguiente ejemplo muestra cómo enviar una solicitud web API que use <xref href="Microsoft.Dynamics.CRM.RetrieveDuplicates?text=RetrieveDuplicates function" /> para detectar y para recuperar los duplicados de un registro especificado.

|||
|----|----|
|`GET`|`{{webapiurl}}RetrieveDuplicates(BusinessEntity=@p1,MatchingEntityName=@p2,PagingInfo=@p3)?@p1={'@odata.type':'Microsoft.Dynamics.CRM.account','accountid':'`*&lt;accountid&gt;*`'}&@p2='account'&@p3={'PageNumber':1,'Count':50}`|

![Crear una solicitud de la API web que utiliza funciones](media/postman-use-function.png "Crear una solicitud de la API web que utiliza funciones")

Las funciones devuelven una colección o un tipo complejo. La respuesta anterior de <xref href="Microsoft.Dynamics.CRM.RetrieveDuplicates?text=RetrieveDuplicates function" /> debería verse así:

```json
{
        {
    "@odata.context": "https://yourorgname.crm.dynamics.com/api/data/v9.0/$metadata#accounts",
    "value": [
        <Omitted for brevity: JSON data for any matching accounts including all properties>
    ]
}
}
```

Más infomación: [Usar funciones web API](use-web-api-functions.md).

## <a name="use-an-action"></a>Usar una acción

Use una solicitud `POST` con las acciones listadas en [Referencia de acción de la API Web](https://docs.microsoft.com/dynamics365/customer-engagement/web-api/actions?view=dynamics-ce-odata-9) para realizar operaciones que tienen efectos secundarios.

Este ejemplo muestra cómo usar <xref href="Microsoft.Dynamics.CRM.BulkDetectDuplicates?text=BulkDetectDuplicates action" />.

`POST` `{{webapiurl}}BulkDetectDuplicates`

![Crear una solicitud de la API web que utiliza acciones](media/postman-use-action.png "Crear una solicitud de la API web que utiliza acciones")

La solicitud en el ejemplo que acaba de ver envía un trabajo de detección duplicado asíncrono que se ejecuta en segundo plano. Los duplicados se detectan mediante las reglas de duplicados publicadas para el tipo de entidad. <xref href="Microsoft.Dynamics.CRM.BulkDetectDuplicatesResponse?text=BulkDetectDuplicatesResponse ComplexType" /> se vuelve como una respuesta desde <xref href="Microsoft.Dynamics.CRM.BulkDetectDuplicates?text=BulkDetectDuplicates action" />. La respuesta incluye la propiedad `JobId`, que contiene el GUID de trabajo duplicado asincrónico de detección de duplicados que detecta y registra registros duplicados.

Más infomación: [Usar acciones web API](use-web-api-actions.md).

## <a name="see-also"></a>Vea también

[Usar Postman con API web](use-postman-web-api.md)<br>
[Realizar operaciones mediante la API web](perform-operations-web-api.md)
