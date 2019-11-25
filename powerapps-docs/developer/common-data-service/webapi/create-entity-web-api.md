---
title: Crear un registro de entidad con la API web (Common Data Service) | Microsoft Docs
description: Lea cómo crear una solicitud POST para enviar datos para crear un registro de entidad en Common Data Service mediante la API web
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 244259ca-2fbc-4fd4-9a74-6166e6683355
caps.latest.revision: 51
author: JimDaly
ms.author: jdaly
ms.reviewer: susikka
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 64561c0b655e02a7537af4268b2a92b7a1677f9a
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749512"
---
# <a name="create-an-entity-record-using-the-web-api"></a>Crear un registro de entidad usando la API web

Use una solicitud POST para enviar datos para crear una entidad. Puede crear varios registros de entidad relacionados en una sola operación mediante "inserción en profundidad". También necesita saber cómo establecer los valores para asociar un nuevo registro de entidad a entidades existentes mediante la anotación @odata.bind.  

> [!NOTE]
> Para obtener información sobre cómo crear y actualizar los metadatos de la entidad mediante la API web, consulte [Crear y actualizar definiciones de entidad mediante la API web](create-update-entity-definitions-using-web-api.md).

<a name="bkmk_basicCreate"></a>

## <a name="basic-create"></a>Crear básico

 En este ejemplo crea un nuevo registro de entidad de cuenta. El encabezado `OData-EntityId` de respuesta contiene el Uri de la entidad creada.

 **Solicitud**

```http

POST [Organization URI]/api/data/v9.0/accounts HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

{
    "name": "Sample Account",
    "creditonhold": false,
    "address1_latitude": 47.639583,
    "description": "This is the description of the sample account",
    "revenue": 5000000,
    "accountcategorycode": 1
}
```

 **Respuesta**

```http

HTTP/1.1 204 No Content
OData-Version: 4.0
OData-EntityId: [Organization URI]/api/data/v9.0/accounts(7eb682f1-ca75-e511-80d4-00155d2a68d1)

```

Para crear un nuevo registro de entidad debe identificar los nombres y los tipos de propiedad válidos. Para todas las entidades y atributos del sistema, puede buscar esta información en el tema de la entidad en [Acerca de la referencia de entidades](../reference/about-entity-reference.md). Para entidades o atributos personalizados, consulte la definición de esa entidad en [Documento de $metadatos CSDL](web-api-types-operations.md#csdl-metadata-document). Más información:[Tipos de entidad](web-api-types-operations.md#entity-types)

<a name="bkmk_CreateRelated"></a>

## <a name="create-related-entity-records-in-one-operation"></a>Crear registros de entidad relacionados en una operación

 Puede crear entidades relacionadas entre sí definiéndolas como valores de propiedades de navegación. Esto se conoce como *inserción en profundidad*.

 Como con un Crear básico, el encabezado `OData-EntityId` de respuesta contiene el URI de la entidad creada. Los URI de las entidades relacionadas creadas no se devuelven.

 Por ejemplo, el siguiente cuerpo de solicitud enviado al conjunto de entidades `Account` creará un total de cuatro nuevas entidades en el contexto de creación de una cuenta.

- Se crea un contacto porque se define como propiedad de objeto de la propiedad de navegación de un solo valor `primarycontactid`.

- Se crea una oportunidad porque se define como un objeto en una matriz que se establece en el valor de una propiedad de navegación valorada como colección `opportunity_customer_accounts`.

- Se crea una tarea porque se define como un objeto en una matriz que se establece en el valor de una propiedad de navegación valorada como colección `Opportunity_Tasks`.

**Solicitud**

```http
POST [Organization URI]/api/data/v9.0/accounts HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

{
 "name": "Sample Account",
 "primarycontactid":
 {
     "firstname": "John",
     "lastname": "Smith"
 },
 "opportunity_customer_accounts":
 [
  {
      "name": "Opportunity associated to Sample Account",
      "Opportunity_Tasks":
      [
       { "subject": "Task associated to opportunity" }
      ]
  }
 ]
}

```

**Respuesta**

 ```http

HTTP/1.1 204 No Content
OData-Version: 4.0
OData-EntityId: [Organization URI]/api/data/v9.0/accounts(3c6e4b5f-86f6-e411-80dd-00155d2a68cb)

```

<a name="bkmk_associateOnCreate"></a>

## <a name="associate-entity-records-on-create"></a>Asociar registros de entidad en la creación

 Para asociar nuevas entidades a las entidades existentes cuando se crean debe establecer el valor de las propiedades de navegación de un solo valor mediante la anotación `@odata.bind`.

 El siguiente cuerpo de solicitud enviado al conjunto de entidades de cuenta creará una nueva cuenta asociada a un contacto existentes con el valor `contactid` de 00000000-0000-0000-0000-000000000001.

**Solicitud**

```http

POST [Organization URI]/api/data/v9.0/accounts HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

{
"name":"Sample Account",
"primarycontactid@odata.bind":"/contacts(00000000-0000-0000-0000-000000000001)"
}

```

**Respuesta**

```http

HTTP/1.1 204 No Content
OData-Version: 4.0
OData-EntityId: [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000002)

```

> [!NOTE]
> La API web no permite asociar entidades de esta manera utilizando una propiedad de navegación valorada como colección.

<a name="bkmk_SuppressDuplicateDetection"></a>

## <a name="check-for-duplicate-records"></a>Verificar registros duplicados


De forma predeterminada, se suprime la detección de duplicados cuando se crean registros mediante la API web. Debe incluir el encabezado `MSCRM.SuppressDuplicateDetection: false` con la solicitud POST para habilitar la detección de duplicados. La detección de duplicados solo se aplica cuando la organización ha habilitado la detección de duplicados, la entidad está habilitada para la detección de duplicados y se aplican reglas de detección de duplicados activas. Más información: [Detectar datos duplicados usando código](../detect-duplicate-data-with-code.md).

Consulte [Detectar duplicados mediante la API web](manage-duplicate-detection-create-update.md#bkmk_create) para obtener más información sobre cómo buscar registros duplicados durante la operación de creación.

<a name="bkmk_initializefrom"></a>

## <a name="create-a-new-entity-record-from-another-entity"></a>Cree un nuevo registro de entidad a partir de otra entidad

Utilice `InitializeFrom function` para crear un registro nuevo en el contexto de un registro existente donde existe una asignación entre las entidades a las que pertenecen los registros. 

El ejemplo siguiente muestra cómo crear un registro de cuenta con los valores de atributo de un registro existente de la entidad de cuenta con un valor de `accountid` igual a c65127ed-2097-e711-80eb-00155db75426.

**Solicitud**

```http
GET [Organization URI]/api/data/v9.0/InitializeFrom(EntityMoniker=@p1,TargetEntityName=@p2,TargetFieldType=@p3)?@p1={'@odata.id':'accounts(c65127ed-2097-e711-80eb-00155db75426)'}&@p2='account'&@p3=Microsoft.Dynamics.CRM.TargetFieldType'ValidForCreate' HTTP/1.1
If-None-Match: null
OData-Version: 4.0
OData-MaxVersion: 4.0
Content-Type: application/json
Accept: application/json
```

**Respuesta**

```json
{
        "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts/$entity",
        "@odata.type": "#Microsoft.Dynamics.CRM.account",
        "parentaccountid@odata.bind": "accounts(c65127ed-2097-e711-80eb-00155db75426)",
        "transactioncurrencyid@odata.bind": "transactioncurrencies(732e87e1-1d96-e711-80e4-00155db75426)",
        "address1_line1":"123 Maple St.",
        "address1_city":"Seattle",
        "address1_country":"United States of America"
}
```

La respuesta recibida de la solicitud InitializeFrom consta de valores de atributos asignados entre la entidad de origen y la entidad de destino y el GUID del registro primario. La asignación de atributos entre las entidades que tienen una relación de entidad es diferente para conjuntos de entidades diferentes y se puede personalizar, por lo que la respuesta de la solicitud de la función InitializeFrom puede variar para organizaciones y entidades diferentes. Cuando se pasa esta respuesta en el cuerpo de la solicitud de creación del nuevo registro, estos valores de atributo se replican en el nuevo registro. Los valores de los atributos asignados personalizados también se definen en el nuevo registro durante el proceso.

> [!NOTE]
> Para determinar si se pueden asignar dos entidades, utilice esta consulta:  
GET [URI organización]/api/data/v9.0/entitymaps?$select=sourceentityname,targetentityname&$orderby=sourceentityname

También se pueden establecer o modificar otros valores de atributo para el nuevo registro agregándolos al cuerpo de la solicitud JSON, tal como se muestra en el ejemplo siguiente.

```http
POST [Organization URI]/api/data/v9.0/accounts HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

    {
        "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts/$entity",
        "@odata.type": "#Microsoft.Dynamics.CRM.account",
        "parentaccountid@odata.bind": "accounts(c65127ed-2097-e711-80eb-00155db75426)",
        "transactioncurrencyid@odata.bind": "transactioncurrencies(732e87e1-1d96-e711-80e4-00155db75426)",
        "name":"Contoso Ltd",
        "numberofemployees":"200",
        "address1_line1":"100 Maple St.",
        "address1_city":"Seattle",
        "address1_country":"United States of America",
        "fax":"73737"
    }
}
```

<a name="bkmk_createWithDataReturned"></a>

## <a name="create-with-data-returned"></a>Crear con datos devueltos

Puede crear su solicitud POST de forma que los datos del registro creado sean devueltos con un estado de 201 (Creados).  Para obtener su resultado, debe usar la preferencia `return=representation` en los encabezados de solicitud.

Para controlar qué propiedades se devuelven, anexe la opción de consulta `$select` a la dirección URL del conjunto de entidades.  Se ignorará la opción de consulta `$expand` si se utiliza.

Cuando se crea una entidad de esta forma, el encabezado `OData-EntityId` que contiene el URI al registro creado no se vuelve.

Este ejemplo crea una nueva entidad de cuenta y devuelve los datos solicitados en la respuesta.

**Solicitud**

 ```http

POST [Organization URI]/api/data/v9.0/accounts?$select=name,creditonhold,address1_latitude,description,revenue,accountcategorycode,createdon HTTP/1.1
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json
Content-Type: application/json; charset=utf-8
Prefer: return=representation

{
    "name": "Sample Account",
    "creditonhold": false,
    "address1_latitude": 47.639583,
    "description": "This is the description of the sample account",
    "revenue": 5000000,
    "accountcategorycode": 1
}

```

**Respuesta**

```http

HTTP/1.1 201 Created
Content-Type: application/json; odata.metadata=minimal
Preference-Applied: return=representation
OData-Version: 4.0

{
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts/$entity",
    "@odata.etag": "W/\"536530\"",
    "accountid": "d6f193fc-ce85-e611-80d8-00155d2a68de",
    "accountcategorycode": 1,
    "description": "This is the description of the sample account",
    "address1_latitude": 47.63958,
    "creditonhold": false,
    "name": "Sample Account",
    "createdon": "2016-09-28T22:57:53Z",
    "revenue": 5000000.0000,
    "_transactioncurrencyid_value": "048dddaa-6f7f-e611-80d3-00155db5e0b6"
}

```

### <a name="see-also"></a>Vea también

[Ejemplo de operaciones básicas de la API web (C#)](samples/basic-operations-csharp.md)<br />
[Ejemplo de operaciones básicas de la API web (JavaScript del lado del cliente)](samples/basic-operations-client-side-javascript.md)<br />
<xref href="Microsoft.Dynamics.CRM.InitializeFrom?text=InitializeFrom Function" />  
[Realizar operaciones mediante la API web](perform-operations-web-api.md)<br />
[Componer solicitudes HTTP y administrar errores](compose-http-requests-handle-errors.md)<br />
[Consultar datos utilizando la API web](query-data-web-api.md)<br />
[Recuperar una entidad usando API web](retrieve-entity-using-web-api.md)<br />
[Actualizar y eliminar entidades mediante la API web](update-delete-entities-using-web-api.md)<br />
[Asociar y anular la asociación de entidades mediante la API web](associate-disassociate-entities-using-web-api.md)<br />
[Usar funciones de la API web](use-web-api-functions.md)<br />
[Usar acciones de la API web](use-web-api-actions.md)<br />
[Ejecute las operaciones por lotes mediante API web](execute-batch-operations-using-web-api.md)<br />
[Suplantar a otro usuario utilizando la API web](impersonate-another-user-web-api.md)<br />
[Realizar operaciones condicionales mediante la API web](perform-conditional-operations-using-web-api.md)<br />
