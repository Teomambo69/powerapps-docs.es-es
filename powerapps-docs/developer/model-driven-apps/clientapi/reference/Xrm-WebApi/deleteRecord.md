---
title: deleteRecord (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
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
# <a name="deleterecord-client-api-reference"></a>deleteRecord (referencia de la API de cliente)



[!INCLUDE[./includes/deleteRecord-description.md](./includes/deleteRecord-description.md)] 

## <a name="syntax"></a>Sintaxis

`Xrm.WebApi.deleteRecord(entityLogicalName, id).then(successCallback, errorCallback);`

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
<td>El nombre lógico de la entidad del registro que desea eliminar. Por ejemplo: "cuenta". </td>
</tr>
<tr>
<td>id.</td>
<td>String</td>
<td>Sí</td>
<td>GUID del registro de entidad que desea eliminar.</td>
</tr>
<tr>
<td>successCallback</td>
<td>Función</td>
<td>No</td>
<td><p>Una función para llamar cuando se elimina un registro. Se pasará un objeto con las propiedades siguientes para identificar el registro eliminado:</p>
<ul>
<li><b>entityType</b>: cadena. Tipo de entidad del registro.</li>
<li><b>id</b>: cadena. GUID del registro.</li>
<li><b>name</b>: cadena. Nombre del registro.</li>
</ul></td>
</tr>
<tr>
<td>errorCallback</td>
<td>Función</td>
<td>No</td>
<td>Una función para llamar cuando la operación tiene error.</td>
</tr>
</table>

## <a name="return-value"></a>Valor devuelto

En caso de éxito, devuelve un objeto promesa que contiene los atributos especificados anteriormente en la descripción del parámetro **successCallback**.

## <a name="examples"></a>Ejemplos

Estos ejemplos utilizan algunos de los mismos objetos de solicitud mostrados en [Actualizar y eliminar entidades mediante la API web](../../../../common-data-service/webapi/update-delete-entities-using-web-api.md) para definir el objeto de datos para actualizar un registro de entidad.

Elimina una cuenta existente con el identificador de registro = 5531d753-95af-e711-a94e-000d3a11e605.

```JavaScript
Xrm.WebApi.deleteRecord("account", "5531d753-95af-e711-a94e-000d3a11e605").then(
    function success(result) {
        console.log("Account deleted");
        // perform operations on record deletion
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```
 
### <a name="related-topics"></a>Temas relacionados

[Xrm.WebApi](../xrm-webapi.md)




