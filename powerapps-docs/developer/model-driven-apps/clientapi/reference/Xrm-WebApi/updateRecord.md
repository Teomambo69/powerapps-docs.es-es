---
title: updateRecord (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: f5d4c8a9-4188-472a-83bf-b986dd135754
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="updaterecord-client-api-reference"></a>updateRecord (referencia de API de cliente)



[!INCLUDE[./includes/updateRecord-description.md](./includes/updateRecord-description.md)] 

## <a name="syntax"></a>Sintaxis

`Xrm.WebApi.updateRecord(entityLogicalName, id, data).then(successCallback, errorCallback);`

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
<td>El nombre lógico de la entidad del registro que desea actualizar. Por ejemplo: "cuenta".</td>
</tr>
<tr>
<td>id.</td>
<td>String</td>
<td>Sí</td>
<td>GUID del registro de entidad que desea actualizar.</td>
</tr>
<tr>
<td>Datos de </td>
<td>Objeto</td>
<td>Sí</td>
<td><p>Un objeto JSON que contiene pares <code>key: value</code>, donde `key` es la propiedad de la entidad y <code>value</code> es el valor de la propiedad que desea actualizar.</p>
<p>Vea ejemplos más adelante en este tema para ver cómo puede definir el objeto <code>data</code> para varios escenarios de actualización.</td>
</tr>
<tr>
<td>successCallback</td>
<td>Función</td>
<td>No</td>
<td><p>Una función para llamar cuando se actualiza un registro. Se pasará un objeto con las propiedades siguientes para identificar el registro actualizado:</p>
<ul>
<li><b>entityType</b>: cadena. El tipo de entidad del registro actualizado.</li>
<li><b>id</b>: cadena. GUID del registro actualizado.</li>
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

Estos ejemplos utilizan algunos de los mismos objetos de solicitud demostrados en [Actualizar y eliminar entidades mediante la API web](../../../../common-data-service/webapi/update-delete-entities-using-web-api.md) para definir el objeto de datos para actualizar un registro de entidad.

### <a name="basic-update"></a>Actualización básica 

Actualiza un registro de cuenta existente con el identificador de registro = 5531d753-95af-e711-a94e-000d3a11e605.

```JavaScript
// define the data to update a record
var data =
    {
        "name": "Updated Sample Account ",
        "creditonhold": true,
        "address1_latitude": 47.639583,
        "description": "This is the updated description of the sample account",
        "revenue": 6000000,
        "accountcategorycode": 2
    }
// update the record
Xrm.WebApi.updateRecord("account", "5531d753-95af-e711-a94e-000d3a11e605", data).then(
    function success(result) {
        console.log("Account updated");
        // perform operations on record update
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

### <a name="update-associations-to-the-related-entities"></a>Actualizar asociaciones a las entidades relacionadas

Para actualizar la asociación con los registros de entidades relacionados (búsquedas), defina el valor de las propiedades de navegación de un solo valor utilizando la anotación `@odata.bind` a otro registro. Sin embargo, para los clientes móviles en el modo sin conexión, no puede usar la anotación `@odata.bind` y en su lugar tiene que pasar un objeto **lookup** (**logicalname** e **id**) que apunte al registro de destino. Presentamos ejemplos de código para ambos escenarios:

**Para escenario en línea (conectado al servidor)**

El ejemplo siguiente actualiza un registro de cuenta para asociar otro registro de contacto como contacto principal de la cuenta:

```JavaScript
// define the data to update a record
var data =
    {
        "primarycontactid@odata.bind": "/contacts(61a0e5b9-88df-e311-b8e5-6c3be5a8b200)"
    }
// update the record
Xrm.WebApi.updateRecord("account", "5531d753-95af-e711-a94e-000d3a11e605", data).then(
    function success(result) {
        console.log("Account updated");
        // perform operations on record update
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

**Para el escenario sin conexión móvil**

Este es el código de ejemplo actualizado para actualizar un registro de cuenta para asociarlo a otro registro de contacto como contacto principal para la cuenta de los clientes móviles cuando trabaje en el modo sin conexión:

```JavaScript
// define the data to update a record
var data =
    {
        "primarycontactid":
        {
            "logicalname": "contact",
            "id": "61a0e5b9-88df-e311-b8e5-6c3be5a8b200"
        }
    }
// update the record
Xrm.WebApi.offline.updateRecord("account", "5531d753-95af-e711-a94e-000d3a11e605", data).then(
    function success(result) {
        console.log("Account updated");
        // perform operations on record update
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```
 
### <a name="related-topics"></a>Temas relacionados

[Xrm.WebApi](../xrm-webapi.md)