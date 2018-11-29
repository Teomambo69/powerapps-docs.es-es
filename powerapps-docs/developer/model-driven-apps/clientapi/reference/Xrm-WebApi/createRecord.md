---
title: createRecord (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 848c277b-bd44-4388-852a-0f59a3a15538
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="createrecord-client-api-reference"></a>createRecord (referencia de API de cliente)



[!INCLUDE[./includes/createRecord-description.md](./includes/createRecord-description.md)] 

## <a name="syntax"></a>Sintaxis

`Xrm.WebApi.createRecord(entityLogicalName, data).then(successCallback, errorCallback);`

## <a name="parameters"></a>Parámetros

<table style="width:100%">
<tr>
<th>Nombre</th>
<th>Tipo</th>
<th>Obligatoria</th>
<th>Descripción</th>
</tr>
<tr>
<td>entityLogicalName</td>
<td>String</td>
<td>Sí</td>
<td>Nombre lógico de la entidad que quiere crear. Por ejemplo: "cuenta".</td>
</tr>
<tr>
<td>Datos de </td>
<td>Objeto</td>
<td>Sí</td>
<td><p>Objeto JSON que define los atributos y valores del registro de entidad nuevo.</p>
<p>Vea ejemplos más adelante en este tema para saber cómo puede definir el objeto <code>data</code> para varios escenarios de creación.</td>
</tr>
<tr>
<td>successCallback</td>
<td>Función</td>
<td>No</td>
<td><p>Una función para llamar cuando se crea un registro. Se pasará un objeto con las propiedades siguientes para identificar el nuevo registro:</p>
<ul>
<li><b>entityType</b>: cadena. Nombre lógico de la entidad del nuevo registro.</li>
<li><b>id</b>: cadena. GUID del nuevo registro.</li>
</ul></td>
</tr>
<tr>
<td>errorCallback</td>
<td>Función</td>
<td>No</td>
<td>Una función para llamar cuando la operación tiene error. Se pasará un objeto con las siguientes propiedades:
<ul>
<li><b>errorCode</b>: Número. Código de error.</li>
<li><b>message</b>: Cadena. Un mensaje de error que describe el problema.</li>
</ul></td>
</tr>
</table>

## <a name="return-value"></a>Valor devuelto

En caso de éxito, devuelve un objeto promesa que contiene los atributos especificados anteriormente en la descripción del parámetro **successCallback**.

## <a name="examples"></a>Ejemplos

Estos ejemplos utilizan algunos de los mismos objetos de solicitud mostrados en [Crear una entidad mediante la API web](../../../../common-data-service/webapi/create-entity-web-api.md) para definir el objeto de datos para crear un registro de entidad.

### <a name="basic-create"></a>Crear básico 

Crea un registro de cuenta de ejemplo.

```JavaScript
// define the data to create new account
var data =
    {
        "name": "Sample Account",
        "creditonhold": false,
        "address1_latitude": 47.639583,
        "description": "This is the description of the sample account",
        "revenue": 5000000,
        "accountcategorycode": 1
    }

// create account record
Xrm.WebApi.createRecord("account", data).then(
    function success(result) {
        console.log("Account created with ID: " + result.id);
        // perform operations on record creation
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

### <a name="create-related-entity-records-along-with-the-primary-record"></a>Crear registros de entidad relacionados junto con el registro principal

 Puede crear entidades relacionadas entre sí definiéndolas como valores de propiedades de navegación. Esto se conoce como *inserción en profundidad*. En este ejemplo, se va a crear un registro de cuenta de ejemplo junto con el registro de contacto principal y un registro de oportunidad asociado.

```JavaScript
// define data to create primary and related entity records
var data =
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

// create account record
Xrm.WebApi.createRecord("account", data).then(
    function success(result) {
        console.log("Account created with ID: " + result.id);
        // perform operations on record creation
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

### <a name="associate-entities-on-creating-new-records"></a>Asociar entidades al crear registros nuevos

Para asociar nuevos registros de entidad a los registros de entidad existentes, debe establecer el valor de las propiedades de navegación de un solo valor mediante la anotación `@odata.bind`. Sin embargo, para los clientes móviles en el modo sin conexión, no puede usar la anotación `@odata.bind` y en su lugar tiene que pasar un objeto **lookup** (**logicalname** e **id**) que apunte al registro de destino. Presentamos ejemplos de código para ambos escenarios: 


**Para escenario en línea (conectado al servidor)**

El ejemplo siguiente crea un registro de cuenta y lo asocia a un registro de contacto existente para establecer este último como contacto principal para el nuevo registro de cuenta:

```JavaScript
var data =
    {
        "name": "Sample Account",
        "primarycontactid@odata.bind": "/contacts(465b158c-541c-e511-80d3-3863bb347ba8)"
    }

// create account record
Xrm.WebApi.createRecord("account", data).then(
    function success(result) {
        console.log("Account created with ID: " + result.id);
        // perform operations on record creation
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

**Para el escenario sin conexión móvil**

Este es el código de ejemplo actualizado para crear un registro de cuenta y asociarlo a un registro de contacto existente para establecer este último como contacto principal para el nuevo registro de cuenta para clientes móviles cuando trabaje en el modo sin conexión:

```JavaScript
var data =
    {
        "name": "Sample Account",
        "primarycontactid":
        {
            "logicalname": "contact",
            "id": "465b158c-541c-e511-80d3-3863bb347ba8"
        } 
    }

// create account record
Xrm.WebApi.offline.createRecord("account", data).then(
    function success(result) {
        console.log("Account created with ID: " + result.id);
        // perform operations on record creation
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
``` 
 
### <a name="related-topics"></a>Temas relacionados

[Cree una entidad usando API web](../../../../common-data-service/webapi/create-entity-web-api.md) 

[Xrm.WebApi](../xrm-webapi.md)