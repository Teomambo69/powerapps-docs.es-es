---
title: retrieveMultipleRecords (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
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
# <a name="retrievemultiplerecords-client-api-reference"></a>retrieveMultipleRecords (referencia de la API de cliente)



[!INCLUDE[./includes/retrieveMultipleRecords-description.md](./includes/retrieveMultipleRecords-description.md)] 

## <a name="syntax"></a>Sintaxis

`Xrm.WebApi.retrieveMultipleRecords(entityLogicalName, options, maxPageSize).then(successCallback, errorCallback);`

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
<td>El nombre lógico de la entidad de los registros que desea recuperar. Por ejemplo: "cuenta".</td>
</tr>
<tr>
<td>opciones</td>
<td>String</td>
<td>No</td>
<td><p>Opciones de consulta del sistema OData o consulta FetchXML para recuperar los datos. </p> 
<ul>
<li>Se admiten las siguientes opciones de consulta del sistema: <b>$select</b>, <b>$top</b>, <b>$filter</b>, <b>$expand</b> y <b>$orderby</b>.</li>
<li>Para especificar una consulta FetchXML, use el atributo <code>fetchXml</code> para especificar la consulta.</li>
</ul>
<p>Nota: Siempre debe utilizar la opción de consulta del sistema <b>$select</b> para limitar las propiedades que se devuelven para un registro de entidad, incluida una lista separada por comas de nombres de propiedades. Esta es una práctica recomendada importante de rendimiento. Si las propiedades no se especifican con <b>$select</b>, se devolverán todas las propiedades.</li>
<p>Especifique las opciones de consulta comenzando con <code>?</code>. Tambíen puede especificar varias opciones de consulta del sistema usando <code>&</code> para separar las opciones de consulta.
<p>Vea los ejemplos más adelante en este tema para saber cómo puede definir el parámetro <code>options</code> para distintos escenarios de recuperación.</td>
</tr>
<tr>
<td>maxPageSize</td>
<td>Número</td>
<td>No</td>
<td><p>Especifique un número positivo que indique el número de registros de entidad que se volverán por página. Si no especifica este parámetro, el valor predeterminado se pasa como 5000.</p>
<p>Si el número de registros recuperados es superior al valor <code>maxPageSize</code> especificado, el atributo <code>nextLink</code> en el objeto de promesa devuelto contendrá un vínculo para recuperar el siguiente conjunto de entidades. </td>
</tr>
<tr>
<td>successCallback</td>
<td>Función</td>
<td>No</td>
<td><p>Una función para llamar cuando se recuperan registros de entidades. Se pasa a la función un objeto con los siguientes atributos:</p>
<ul>
<li><b>entities</b>: matriz de objetos JSON, donde cada objeto representa el registro de entidad recuperada que contiene los atributos y sus valores como pares <code>key: value</code>. De forma predeterminada se recupera el identificador del registro de entidad.</li>
<li><b>nextLink</b>: cadena. Si el número de registros que se están recuperando es mayor que el valor especificado en el parámetro <code>maxPageSize</code> en la solicitud, este atributo devuelve la dirección URL para devolver el siguiente conjunto de registros.</li>
</ul>
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

Si resulta correcto, devuelve una sugerencia que contiene una matriz de objetos JSON (**entidades**) que contiene los registros de entidades recuperadas y el atributo **nextLink** (opcional) con la dirección URL apuntando al siguiente conjunto de registros en el caso de haberse especificado paginación (`maxPageSize`) en la solicitud y si el número de registros devuelto supera el valor de paginación.

## <a name="examples"></a>Ejemplos

La mayoría de los escenarios o ejemplos que se mencionan en [Consultar datos utilizando la API web](../../../../common-data-service/webapi/query-data-web-api.md) puede lograrse con el método **retrieveMutipleRecords**. Algunos de los ejemplos se listan a continuación.

### <a name="basic-retrieve-multiple"></a>Recuperación básica de varios

Este ejemplo consulta el conjunto de entidades de cuenta y usa las opciones de consulta del sistema `$select` y `$top` para devolver la propiedad de nombre para las tres primeras cuentas:

```JavaScript
Xrm.WebApi.retrieveMultipleRecords("account", "?$select=name&$top=3").then(
    function success(result) {
        for (var i = 0; i < result.entities.length; i++) {
            console.log(result.entities[i]);
        }                    
        // perform additional operations on retrieved records
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

### <a name="specify-the-number-of-entities-to-return-in-a-page"></a>Especifique el número de entidades para devolver a una página

En el ejemplo siguiente se muestra el uso del parámetro `maxPageSize` para especificar el número de registros (3) que mostrar en una página.

```JavaScript
Xrm.WebApi.retrieveMultipleRecords("account", "?$select=name", 3).then(
    function success(result) {
        for (var i = 0; i < result.entities.length; i++) {
            console.log(result.entities[i]);
        }
        console.log("Next page link: " + result.nextLink);
        // perform additional operations on retrieved records
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

Este ejemplo mostrará 3 registros y un vínculo a la página siguiente. Este es un ejemplo de salida de la **consola** en las herramientas de desarrollo del explorador:

```
{@odata.etag: "W/"1035541"", name: "A. Datum", accountid: "475b158c-541c-e511-80d3-3863bb347ba8"}
@odata.etag: "W/"1035541""accountid: "475b158c-541c-e511-80d3-3863bb347ba8"name: "A. Datum"__proto__: Object
VM5595:4 
{@odata.etag: "W/"947306"", name: "Adventure Works", accountid: "a8a19cdd-88df-e311-b8e5-6c3be5a8b200"}
VM5595:4 
{@odata.etag: "W/"1033754"", name: "Alpine Ski House", accountid: "aaa19cdd-88df-e311-b8e5-6c3be5a8b200"}
VM5595:6 
Next page link: [Organization URI]/api/data/v9.0/accounts?$select=name&$skiptoken=%3Ccookie%20pagenumber=%222%22%20pagingcookie=%22%253ccookie%2520page%253d%25221%2522%253e%253caccountid%2520last%253d%2522%257bAAA19CDD-88DF-E311-B8E5-6C3BE5A8B200%257d%2522%2520first%253d%2522%257b475B158C-541C-E511-80D3-3863BB347BA8%257d%2522%2520%252f%253e%253c%252fcookie%253e%22%20istracking=%22False%22%20/%3E
```

Utilice la parte de la consulta en la dirección URL en la propiedad `nextLink` como el valor del parámetro `options` en la llamada subsiguiente **retrieveMultipleRecords** para solicitar el siguiente conjunto de registros. No cambie ni anexar opciones de consulta del sistema adicionales al valor. Para cada solicitud posterior de páginas adicionales, debe usar el mismo valor de preferencia de `maxPageSize` que usó en la solicitud original de recuperación de varios. Además, almacene en caché los resultados devueltos o el valor de la propiedad nextLink para que se pueda volver a páginas anteriormente recuperadas. 

Por ejemplo, para obtener la siguiente página de registros, pasaremos en la consulta parte de la dirección URL `nextLink` al parámetro `options`:

```JavaScript
Xrm.WebApi.retrieveMultipleRecords("account", "?$select=name&$skiptoken=%3Ccookie%20pagenumber=%222%22%20pagingcookie=%22%253ccookie%2520page%253d%25221%2522%253e%253caccountid%2520last%253d%2522%257bAAA19CDD-88DF-E311-B8E5-6C3BE5A8B200%257d%2522%2520first%253d%2522%257b475B158C-541C-E511-80D3-3863BB347BA8%257d%2522%2520%252f%253e%253c%252fcookie%253e%22%20istracking=%22False%22%20/%3E", 3).then(
    function success(result) {
        for (var i = 0; i < result.entities.length; i++) {
            console.log(result.entities[i]);
        }
        console.log("Next page link: " + result.nextLink);
        // perform additional operations on retrieved records
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

Esto devolverá la siguiente página del conjunto de resultados:

```
{@odata.etag: "W/"1035542"", name: "Blue Yonder Airlines", accountid: "aca19cdd-88df-e311-b8e5-6c3be5a8b200"}
VM5597:4 
{@odata.etag: "W/"1031348"", name: "City Power & Light", accountid: "aea19cdd-88df-e311-b8e5-6c3be5a8b200"}
VM5597:4 
{@odata.etag: "W/"1035543"", name: "Coho Winery", accountid: "b0a19cdd-88df-e311-b8e5-6c3be5a8b200"}
VM5597:6 
Next page link: [Organization URI]/api/data/v9.0/accounts?$select=name&$skiptoken=%3Ccookie%20pagenumber=%223%22%20pagingcookie=%22%253ccookie%2520page%253d%25222%2522%253e%253caccountid%2520last%253d%2522%257bB0A19CDD-88DF-E311-B8E5-6C3BE5A8B200%257d%2522%2520first%253d%2522%257bACA19CDD-88DF-E311-B8E5-6C3BE5A8B200%257d%2522%2520%252f%253e%253c%252fcookie%253e%22%20istracking=%22False%22%20/%3E
``` 
  
> [!IMPORTANT]
>  El valor de la propiedad `nextLink` está codificado con URI. Si codifica con URI el valor antes de enviarlo, la información de cookie XML en la URL generará un error.

### <a name="retrieve-related-entities-by-expanding-navigation-properties"></a>Recuperar entidades relacionadas ampliando las propiedades de navegación

Use la opción de consulta del sistema **$expand** en las propiedades de navegación para controlar qué datos se devuelven de las entidades relacionadas. El ejemplo siguiente muestra cómo recuperar el contacto para todos los registros de la cuenta. Para los registros de contacto relacionados, solo recuperamos `contactid` y `fullname`:

```JavaScript
Xrm.WebApi.retrieveMultipleRecords("account", "?$select=name&$top=3&$expand=primarycontactid($select=contactid,fullname)", 3).then(
    function success(result) {
        for (var i = 0; i < result.entities.length; i++) {
            console.log(result.entities[i]);
        }        
        // perform additional operations on retrieved records
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```


Para ver más ejemplos de recuperar varios registros mediante la API de web, consulte [Consultar datos utilizando la API web](../../../../common-data-service/webapi/query-data-web-api.md).

 
### <a name="related-topics"></a>Temas relacionados

[Consultar datos utilizando la API web](../../../../common-data-service/webapi/query-data-web-api.md)

[Xrm.WebApi.retrieveRecord](retrieveRecord.md)

[Xrm.WebApi](../xrm-webapi.md)




