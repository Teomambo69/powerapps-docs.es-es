---
title: retrieveRecord (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: d4e92999-3b79-4783-8cac-f656fc5f7fda
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="retrieverecord-client-api-reference"></a>retrieveRecord (referencia de API de cliente)



[!INCLUDE[./includes/retrieveRecord-description.md](./includes/retrieveRecord-description.md)] 

## <a name="syntax"></a>Sintaxis

`Xrm.WebApi.retrieveRecord(entityLogicalName, id, options).then(successCallback, errorCallback);`

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
<td>El nombre lógico de la entidad del registro que desea recuperar. Por ejemplo: "cuenta".</td>
</tr>
<tr>
<td>id.</td>
<td>String</td>
<td>Sí</td>
<td>GUID del registro de entidad que desea recuperar.</td>
</tr>
<tr>
<td>opciones</td>
<td>String</td>
<td>No</td>
<td><p>Opciones de consulta del sistema OData, <b>$select</b> y <b>$expand</b>, para recuperar los datos.</p>
<ul><li>Use la opción de consulta del sistema <b>$select</b> para limitar las propiedades devueltas incluyendo una lista separada por comas de nombres de propiedad. Esta es una práctica recomendada importante de rendimiento. Si las propiedades no se especifican con <b>$select</b>, se devolverán todas las propiedades.</li>
<li>Use la opción de consulta del sistema <b>$expand</b> para controlar qué datos de entidades relacionadas se devuelven. Si incluye solo el nombre de la propiedad de navegación, recibirá todas las propiedades de registros relacionados. Puede limitar las propiedades devueltas para registros relacionados con la opción de la consulta del sistema <b>$select</b> entre paréntesis después del nombre de propiedad de navegación. Use esta opción para las propiedades de navegación de <i>un solo valor</i> y <i>valoradas como colección</i>.</li>
</ul>
<p>Especifique las opciones de consulta comenzando con <code>?</code>. Puede especificar también varias opciones de consulta usando <code>&</code> para separar las opciones de consulta. Por ejemplo:</p>
<code>?$select=name&$expand=primarycontactid($select=contactid,fullname)</code>
<p>Vea los ejemplos más adelante en este tema para saber cómo puede definir el parámetro <code>options</code> para distintos escenarios de recuperación.</td>
</tr>
<tr>
<td>successCallback</td>
<td>Función</td>
<td>No</td>
<td><p>Una función para llamar cuando se recupera un registro. Se pasará a la función un objeto JSON con las propiedades y los valores recuperados.</p>
</td>
</tr>
<tr>
<td>errorCallback</td>
<td>Función</td>
<td>No</td>
<td>Una función para llamar cuando la operación tiene error.</td>
</tr>
</table>

## <a name="return-value"></a>Valor devuelto

En caso de resultar correcto, devuelve una promesa con un objeto JSON con los atributos recuperados y sus valores.

## <a name="examples"></a>Ejemplos

### <a name="basic-retrieve"></a>Recuperación básica 

Recupera el nombre y los ingresos de un registro de cuenta con el ID. de registro = 5531d753-95af-e711-a94e-000d3a11e605.

```JavaScript
Xrm.WebApi.retrieveRecord("account", "a8a19cdd-88df-e311-b8e5-6c3be5a8b200", "?$select=name,revenue").then(
    function success(result) {
        console.log("Retrieved values: Name: " + result.name + ", Revenue: " + result.revenue);
        // perform operations on record retrieval
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

El ejemplo anterior muestra lo siguiente en la consola; puede ver otros valores dependiendo de los datos:

`Retrieved values: Name: Sample Account, Revenue: 5000000`

### <a name="retrieve-related-entities-for-an-entity-instance-by-expanding-single-valued-navigation-properties"></a>Recupere entidades relacionadas para una instancia de entidad expandiendo las propiedades de navegación de un solo valor

 El ejemplo siguiente muestra cómo recuperar el contacto para un registro de cuenta con el Id. de registro = a8a19cdd-88df-e311-b8e5-6c3be5a8b200. Para el registro de contacto relacionado, solo estamos recuperando las propiedades **contactid** y **fullname**.

```JavaScript
Xrm.WebApi.retrieveRecord("account", "a8a19cdd-88df-e311-b8e5-6c3be5a8b200", "?$select=name&$expand=primarycontactid($select=contactid,fullname)").then(
    function success(result) {
        console.log("Retrieved values: Name: " + result.name + ", Primary Contact ID: " + result.primarycontactid.contactid +
                ", Primary Contact Name: " + result.primarycontactid.fullname);
        // perform operations on record retrieval
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

El ejemplo anterior muestra lo siguiente en la consola; puede ver otros valores dependiendo de los datos:

`Retrieved values: Name: Adventure Works, Primary Contact ID: 49a0e5b9-88df-e311-b8e5-6c3be5a8b200, Primary Contact Name: Adrian Dumitrascu`

 
### <a name="related-topics"></a>Temas relacionados

[Xrm.WebApi.retrieveMultipleRecords](retrieveMultipleRecords.md)

[Xrm.WebApi](../xrm-webapi.md)




