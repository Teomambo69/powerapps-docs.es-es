---
title: retrieveMultipleRecords | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 824a53f9-c743-435a-9de2-8128846f3191
---

# <a name="retrievemultiplerecords"></a>retrieveMultipleRecords

[!INCLUDE [retrievemultiplerecords-description](includes/retrievemultiplerecords-description.md)]

## <a name="syntax"></a>Sintaxis

`retrieveMultipleRecords(entityLogicalName, options, maxPageSize).then(successCallback, errorCallback);`

## <a name="parameters"></a>Parámetros

<table style="width:100%">
<tr>
<th>Nombre</th>
<th>Escriba</th>
<th>Requerido</th>
<th>Descripción</th>
</tr>
<tr>
<td>entityLogicalName</td>
<td>String</td>
<td>Sí</td>
<td>El nombre lógico de la entidad de los registros que desea recuperar. Por ejemplo: &quot;cuenta&quot;.</td>
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
<p>Especifique las opciones de consulta comenzando con <code>?</code>. Tambíen puede especificar varias opciones de consulta del sistema usando <code>&amp;</code> para separar las opciones de consulta.
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


### <a name="related-topics"></a>Temas relacionados

[API web](../webapi.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)