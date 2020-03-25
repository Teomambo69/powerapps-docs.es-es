---
title: Recuperar un registro de entidad con la API web (Common Data Service)| Microsoft Docs
description: Lea cómo formar una solicitud GET mediante la API web de Common Data Service para recuperar datos de una entidad especificada como el recurso con un identificador único
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: abae4614-9e03-45e7-94fa-9e6e7225ece5
caps.latest.revision: 21
author: JimDaly
ms.author: jdaly
ms.reviewer: susikka
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 767c0ed29643c51057d9f3d794136dc56915e161
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "3109076"
---
# <a name="retrieve-an-entity-record-using-the-web-api"></a>Recuperar un registro de entidad usando la API web

Use una solicitud `GET` para recuperar los datos para una entidad especificada como recurso con un identificador único. Para recuperar un registro de entidad también puede solicitar propiedades específicas y expandir las propiedades de navegación para devolver propiedades de entidades relacionadas.  

> [!NOTE]
>  Para obtener información sobre cómo recuperar metadatos de entidades, consulte [Consultar metadatos con la API web](query-metadata-web-api.md).

<a name="bkmk_basicRetrieve"></a>

## <a name="basic-retrieve-example"></a>Ejemplo de recuperación básica

Este ejemplo devuelve datos de una instancia de entidad de cuenta con el valor de clave principal igual a 00000000-0000-0000-0000-000000000001.

```http
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)
```

Para recuperar más de un registro de entidad a la vez, consulte [Ejemplo de consulta básica](query-data-web-api.md#bkmk_basicQuery) en el tema [Consultar datos con la API web](query-data-web-api.md).

> [!CAUTION]
>  El ejemplo anterior devolverá todas las propiedades del registro de cuenta, algo que va en contra de las recomendaciones de rendimiento para recuperar datos. Este ejemplo sirve para ilustrar cómo puede realizar una recuperación básica de una instancia de entidad en Common Data Service. Puesto que todas las propiedades se devolvieron, no hemos incluido la información de respuesta para la solicitud en este ejemplo.
>
>  Como práctica recomendada para mejorar el rendimiento, debe usar siempre la opción de consulta del sistema `$select` para limitar las propiedades devueltas al recuperar datos. Consulte la siguiente sección, **Recuperar propiedades específicas**, para obtener información sobre este.
  
<a name="bkmk_requestProperties"></a>

## <a name="retrieve-specific-properties"></a>Recuperar propiedades específicas

Use la opción de consulta del sistema `$select` para limitar las propiedades devueltas incluyendo una lista separada por comas de nombres de propiedad. Esta es una práctica recomendada importante de rendimiento. Si las propiedades no se especifican utilizando `$select`, todas las propiedades se devolverán.  

El ejemplo siguiente recupera propiedades `name` y `revenue` para la entidad de cuenta con el valor de clave principal igual a 00000000-0000-0000-0000-000000000001

**Solicitud**
```http
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)?$select=name,revenue HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
```

**Respuesta**
```http
HTTP/1.1 200 OK
Content-Type: application/json; odata.metadata=minimal
OData-Version: 4.0

{
"@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts(name,revenue)/$entity",  
"@odata.etag": "W/\"502186\"",  
"name": "A. Datum Corporation (sample)",  
"revenue": 10000,  
"accountid": "00000000-0000-0000-0000-000000000001",  
"_transactioncurrencyid_value":"b2a6b689-9a39-e611-80d2-00155db44581"  
}  

```

Al solicitar determinados tipos de propiedades puede esperar que las propiedades de solo lectura adicionales se devuelvan automáticamente.

Si solicita un valor monetario, se devolverá la propiedad de búsqueda `_transactioncurrencyid_value`. Esta propiedad solo contiene el valor GUID de la divisa de transacción para que pueda usar este valor para recuperar información acerca de la divisa con la <xref href="Microsoft.Dynamics.CRM.transactioncurrency?text=transactioncurrency EntityType" />. De forma alternativa, al solicitar anotaciones también puede obtener más datos en la misma solicitud. Más información:[Recuperar datos sobre propiedades de búsqueda](query-data-web-api.md#bkmk_lookupProperty)  

Si solicita una propiedad que forma parte de un atributo compuesto para una dirección, obtendrá además la propiedad compuesta. Por ejemplo, si la consulta solicita la propiedad `address1_line1` para un contacto, se devolverá además la propiedad `address1_composite`. 

<a name="BKMK_UsingAltKeys"></a>

## <a name="retrieve-using-an-alternate-key"></a>Recuperar con una clave alternativa

Si una entidad tiene una clave alternativa definida, también puede usar la clave alternativa para recuperar la entidad en lugar del identificador único para la entidad. Por ejemplo, si la entidad `Contact` tiene una definición de clave alternativa que incluye las propiedades firstname y emailaddress1, puede recuperar el contacto mediante el uso de una consulta con los datos proporcionados para esas claves como se indica a continuación.

```http
GET [Organization URI]/api/data/v9.0/contacts(firstname='Joe',emailaddress1='abc@example.com')
```
Si la definición de clave alternativa contiene un campo de tipo búsqueda (por ejemplo, la propiedad primarycontactid para la entidad Cuenta), puede recuperar la cuenta mediante la [propiedad de consulta](/powerapps/developer/common-data-service/webapi/web-api-types-operations#lookup-properties) como se muestra aquí.

```http
GET [Organization URI]/api/data/v9.0/accounts(_primarycontactid_value=00000000-0000-0000-0000-000000000001) 
```

En cualquier momento que necesite identificar de forma exclusiva una entidad para recuperar, actualizar o eliminar, puede usar las claves alternativas configuradas para la entidad. De forma predeterminada, no hay claves alternativas configuradas para entidades. Las claves alternativas sólo estarán disponibles si la organización las agrega.

<a name="bkmk_retrieveSingleValue"></a>

## <a name="retrieve-a-single-property-value"></a>Recuperar un solo valor de propiedad

Cuando solo necesita recuperar el valor de una sola propiedad de una entidad, se puede anexar el nombre de la propiedad a la URI para una entidad para devolver solo el valor de esa propiedad. Esto es una recomendación de rendimiento porque necesitan devolverse menos datos en la respuesta.

Este ejemplo sólo devuelve el valor de la propiedad de nombre de una entidad de cuenta.

**Solicitud**
```http
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)/name HTTP/1.1
Accept: application/json
OData-MaxVersion: 4.0
OData-Version: 4.0
```
**Respuesta**
 ```http
HTTP/1.1 200 OK
Content-Type: application/json; odata.metadata=minimal
OData-Version: 4.0

{
"@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(00000000-0000-0000-0000-000000000001)/name",
"value":"Adventure Works (sample)"
}
```

<a name="bkmk_retrieveNavigationPropertyValues"></a>

## <a name="retrieve-navigation-property-values"></a>Recuperar valores de propiedad de navegación

De la misma forma que puede recuperar valores de propiedad individuales, también puede obtener acceso a los valores de propiedades de navegación (campos de búsqueda) anexando el nombre de la propiedad de navegación a la URI que hace referencia a una entidad individual.

El siguiente ejemplo devuelve el nombre completo del contacto principal de una cuenta usando la propiedad de navegación de un solo valor `primarycontactid`.  

**Solicitud**
 ```http
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)/primarycontactid?$select=fullname HTTP/1.1
Accept: application/json
OData-MaxVersion: 4.0
OData-Version: 4.0
```
**Respuesta**
```http
HTTP/1.1 200 OK
Content-Type: application/json; odata.metadata=minimal
OData-Version: 4.0

{  
"@odata.context": "[Organization URI]/api/data/v9.0/$metadata#contacts(fullname)/$entity",  
"@odata.etag": "W/\"500128\"",  
"fullname": "Rene Valdes (sample)",  
"contactid": "ff390c24-9c72-e511-80d4-00155d2a68d1"  
}

```

Para propiedades de navegación valoradas como colección tiene la opción de solicitar devolver solo referencias a las entidades relacionadas o simplemente un recuento de entidades relacionadas.

El siguiente ejemplo solo devolverá referencias a las tareas relacionadas con una cuenta específica agregando `/$ref` a la solicitud.

**Solicitud**
```http
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)/AccountTasks/$ref HTTP/1.1
Accept: application/json
OData-MaxVersion: 4.0
OData-Version: 4.0
```

**Respuesta**
```http
HTTP/1.1 200 OK
Content-Type: application/json; odata.metadata=minimal
OData-Version: 4.0
  
{  
"@odata.context": "[Organization URI]/api/data/v9.0/$metadata#Collection($ref)",  
"value": [  
{  
"@odata.id": "[Organization URI]/api/data/v9.0/tasks(6b5941dd-d175-e511-80d4-00155d2a68d1)"  
},  
{  
"@odata.id": "[Organization URI]/api/data/v9.0/tasks(fcbb60ed-d175-e511-80d4-00155d2a68d1)"  
}  
]  
}  
  
```
El siguiente ejemplo devuelve el número de tareas relacionadas con una cuenta específica mediante la propiedad de navegación valorada como colección Account_Tasks con `/$count` anexado.  

 **Solicitud**
```http
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)/Account_Tasks/$count HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
```
**Respuesta**
```http
ï»¿2
```
> [!NOTE]
> El valor devuelto incluye caracteres de marca de orden de butes (BOM) UTF-8 (`ï»¿`) que representan que es un documento UTF-8.

<a name="bkmk_expandRelated"></a>

## <a name="retrieve-related-entities-for-an-entity-by-expanding-navigation-properties"></a>Recuperar entidades relacionadas para una entidad ampliando las propiedades de navegación

Use la opción de consulta del sistema `$expand` para controlar qué datos de entidades relacionadas se devuelven. Hay dos tipos de propiedades de navegación:  

- Las propiedades de navegación *de un solo valor* corresponden a atributos de búsqueda que admiten relaciones de varios a uno y permiten establecer una referencia a otra entidad.
- Las propiedades de navegación *valoradas como colección* corresponden a relaciones de uno a varios o de varios a varios.  

Si incluye simplemente el nombre de la propiedad de navegación, recibirá todas las propiedades de registros relacionados. Puede limitar las propiedades devueltas para registros relacionados con la opción de la consulta del sistema `$select` entre paréntesis después del nombre de propiedad de navegación. Use esta opción para las propiedades de navegación de un solo valor y valoradas como colección.

> [!NOTE]
> Para recuperar entidades relacionadas de conjuntos de entidades, consulte [Recuperar entidades relacionadas ampliando las propiedades de navegación](query-data-web-api.md#bkmk_expandRelated).  

- **Recuperar entidades relacionadas para una instancia de entidad expandiendo las propiedades de navegación de un solo valor** <br />El ejemplo siguiente muestra cómo recuperar el contacto para una entidad de cuenta. Para el registro de contacto relacionado, solo recuperamos contactid y fullname.

  **Solicitud**
  ```http
    GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)?$select=name&$expand=primarycontactid($select=contactid,fullname) HTTP/1.1  
    Accept: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
  ```

  **Respuesta**
  ```http
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  

    {  
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name,primarycontactid,primarycontactid(contactid,fullname))/$entity",  
    "@odata.etag":"W/\"550616\"",  
    "name":"Adventure Works (sample)",  
    "accountid":"00000000-0000-0000-0000-000000000001",  
    "primarycontactid":{  
    "@odata.etag":"W/\"550626\"",  
    "contactid":"c59648c3-68f7-e511-80d3-00155db53318",  
    "fullname":"Nancy Anderson (sample)"  
    }  
    }  
  
  ```
  En lugar de devolver entidades relacionadas para instancias de entidad, también puede devolver referencias (vínculos) a las entidades relacionadas expandiendo la propiedad de navegación de un solo valor con la opción `$ref`. El siguiente ejemplo devuelve vínculos al registro de contacto para la entidad de cuenta.  

  **Solicitud**
  ```http
    GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)?$select=name&$expand=primarycontactid/$ref HTTP/1.1  
    Accept: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
  ```

  **Respuesta**
  ```http
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  
  
    {  
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name,primarycontactid)/$entity",  
    "@odata.etag":"W/\"550616\"",  
    "name":"Adventure Works (sample)",  
    "accountid":"00000000-0000-0000-0000-000000000001",  
    "_primarycontactid_value":"c59648c3-68f7-e511-80d3-00155db53318",  
    "primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(c59648c3-68f7-e511-80d3-00155db53318)"  
    }  
    }
  ```
- **Recuperar entidades relacionadas para una instancia de entidad expandiendo las propiedades de navegación valorada como colección**:<br /> El ejemplo siguiente muestra cómo recuperar todas las tareas asignadas a un registro de cuenta.

  **Solicitud**

  ```http
  GET [Organization URI]/api/data/v9.0/accounts(915e89f5-29fc-e511-80d2-00155db07c77)?$select=name&$expand=Account_Tasks($select=subject,scheduledstart)
  Accept: application/json
  OData-MaxVersion: 4.0
  OData-Version: 4.0
  ```

  **Respuesta**

  ```http
  HTTP/1.1 200 OK  
  Content-Type: application/json; odata.metadata=minimal  
  OData-Version: 4.0

  {
  "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name,Account_Tasks,Account_Tasks(subject,scheduledstart))/$entity",  
    "@odata.etag":"W/\"514069\"","name":"Sample Child Account 1","accountid":"915e89f5-29fc-e511-80d2-00155db07c77",  
    "Account_Tasks":[  
    {  
    "@odata.etag":"W/\"514085\"",  
    "subject":"Sample Task 1",  
    "scheduledstart":"2016-04-11T15:00:00Z",  
    "activityid":"a983a612-3ffc-e511-80d2-00155db07c77"  
    },{  
    "@odata.etag":"W/\"514082\"",  
    "subject":"Sample Task 2",  
    "scheduledstart":"2016-04-13T15:00:00Z",  
    "activityid":"7bcc572f-3ffc-e511-80d2-00155db07c77"  
   }  
  ]  
  }
  ```
  
 > [!NOTE]
 > Si expande parámetros de navegación valorados como colección para recuperar entidades relacionadas para *conjuntos de entidades*, una propiedad @odata.nextLink será devuelta en su lugar para las entidades relacionadas. Debe usar el valor de la propiedad @odata.nextLink con una nueva solicitud GET para devolver los datos requeridos. Más información:[Recuperar entidades relacionadas ampliando las propiedades de navegación](query-data-web-api.md#bkmk_expandRelated)

- **Recupere entidades relacionadas para una instancia de entidad expandiendo las propiedades de navegación de un solo valor y valoradas como colección**: El siguiente ejemplo demuestra cómo puede expandir entidades relacionadas para una instancia de entidad utilizando propiedades de navegación de un solo valor y valoradas como colección.  

  **Solicitud**

  ```http 
    GET [Organization URI]/api/data/v9.0/accounts(99390c24-9c72-e511-80d4-00155d2a68d1)?$select=accountid&$expand=parentaccountid($select%20=%20createdon,%20name),Account_Tasks($select%20=%20subject,%20scheduledstart) HTTP/1.1  
    Accept: application/json  
    Content-Type: application/json; charset=utf-8  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0
  ```

  **Respuesta**

  ```http
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  

    {  
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(accountid,parentaccountid,Account_Tasks,parentaccountid(createdon,name),Account_Tasks(subject,scheduledstart))/$entity","@odata.etag":"W/\"514069\"","accountid":"915e89f5-29fc-e511-80d2-00155db07c77",  
    "parentaccountid":{  
    "@odata.etag":"W/\"514074\"","createdon":"2016-04-06T00:29:04Z",  
    "name":"Adventure Works (sample)",  
    "accountid":"3adbf27c-8efb-e511-80d2-00155db07c77"  
    },"Account_Tasks":[  
    {  
    "@odata.etag":"W/\"514085\"",  
    "subject":"Sample Task 1",  
    "scheduledstart":"2016-04-11T15:00:00Z",  
    "activityid":"a983a612-3ffc-e511-80d2-00155db07c77"  
    },{  
    "@odata.etag":"W/\"514082\"",  
    "subject":"Sample Task 2",  
    "scheduledstart":"2016-04-13T15:00:00Z",  
    "activityid":"7bcc572f-3ffc-e511-80d2-00155db07c77"  
    }  
    ]  
    }
  ```

> [!NOTE]
> No puede usar los segmentos de ruta `/$ref` o `/$count` para devolver solo el URI para la entidad relacionada o el número de entidades relacionadas.

<a name="bkmk_optionsOnExpand"></a>

## <a name="options-to-apply-to-expanded-entities"></a>Opciones para aplicar a entidades expandidas

 Puede aplicar algunas opciones de consulta del sistema a las entidades devueltas para una propiedad de navegación valorada como colección. Use una lista separada por punto y coma de opciones de consulta del sistema entre paréntesis después del nombre de la propiedad de navegación valorada como colección. Puede utilizar `$select`, `$filter`, `$orderby` y `$top`.

 El siguiente ejemplo filtra los resultados de las entidades de tareas relacionadas con una cuenta dejando aquellas cuyo asunto termina en "1".

```http
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)?$expand=Account_Tasks($filter=endswith(subject,'1');$select=subject)  
```

El siguiente ejemplo especifica que las tareas relacionadas deben devolverse en orden ascendente basándose en la propiedad `createdon`.

```http
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)?$expand=Account_Tasks($orderby=createdon asc;$select=subject,createdon)  
```

 El siguiente ejemplo devuelve solamente la primera tarea relacionada.

```http
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)?$expand=Account_Tasks($top=1;$select=subject)
```

> [!NOTE]
> Este es un subconjunto de las opciones de consulta del sistema descritas en la sección 11.2.4.2 .1 de opciones de ampliación de [OData versión 4.0 parte 1, Protocol Plus Errata 02](https://docs.oasis-open.org/odata/odata/v4.0/errata02/os/complete/part1-protocol/odata-v4.0-errata02-os-part1-protocol-complete.html). Las opciones `$skip`, `$count`, `$search`, `$expand` y `$levels` no se admiten para la API web.

<a name="bkmk_DetectIfChanged"></a>

## <a name="detect-if-an-entity-has-changed-since-it-was-retrieved"></a>Detectar si una entidad se ha modificado desde que se recuperó

Como recomendación de rendimiento solo debe solicitar los datos que necesite. Si ha recuperado anteriormente un registro de entidad, puede usar la *ETag* asociada a un registro anteriormente recuperado para realizar recuperaciones condicionales en dicho registro.  Para obtener más información, consulte [Recuperaciones condicionales](perform-conditional-operations-using-web-api.md#bkmk_DetectIfChanged).  

<a name="bkmk_formattedValues"></a>

## <a name="retrieve-formatted-values"></a>Recuperar valores con formato

La solicitud de valores con formato para recuperaciones de registros individuales se hace la misma forma que cuando se consultan conjuntos de entidades. Más información:[Incluir valores con formato](query-data-web-api.md#bkmk_includeFormattedValues).

### <a name="see-also"></a>Vea también

[Ejemplo de operaciones básicas de la API web (C#)](samples/basic-operations-csharp.md)<br />
[Ejemplo de operaciones básicas de la API web (JavaScript del lado del cliente)](samples/basic-operations-client-side-javascript.md)<br />
[Realizar operaciones mediante la API web](perform-operations-web-api.md)<br />
[Componer solicitudes HTTP y administrar errores](compose-http-requests-handle-errors.md)<br />
[Consultar datos utilizando la API web](query-data-web-api.md)<br />
[Cree una entidad usando API web](create-entity-web-api.md)<br />
[Actualizar y eliminar entidades mediante la API web](update-delete-entities-using-web-api.md)<br />
[Asociar y anular la asociación de entidades mediante la API web](associate-disassociate-entities-using-web-api.md)<br />
[Usar funciones de la API web](use-web-api-functions.md)<br />
[Usar acciones de la API web](use-web-api-actions.md)<br />
[Ejecute las operaciones por lotes mediante API web](execute-batch-operations-using-web-api.md)<br />
[Suplantar a otro usuario utilizando la API web](impersonate-another-user-web-api.md)<br />
[Realizar operaciones condicionales mediante la API web](perform-conditional-operations-using-web-api.md)<br />
