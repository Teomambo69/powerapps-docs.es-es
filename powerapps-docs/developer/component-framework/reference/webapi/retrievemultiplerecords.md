---
title: retrieveMultipleRecords | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 824a53f9-c743-435a-9de2-8128846f3191
ms.openlocfilehash: d708596e9b8e12ead8f84d31d3b35fb5b27843f8
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340814"
---
# <a name="retrievemultiplerecords"></a>retrieveMultipleRecords

[!INCLUDE [retrievemultiplerecords-description](includes/retrievemultiplerecords-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="syntax"></a>Sintaxis

`context.webAPI.retrieveMultipleRecords(entityLogicalName, options, maxPageSize).then(successCallback, errorCallback);`

## <a name="parameters"></a>Parámetros

<table style="width:100%">
<tr>
<th>Nombre</th>
<th>Tipo</th>
<th>Requerido</th>
<th>Descripción</th>
</tr>
<tr>
<td>entityLogicalName</td>
<td>Cadena</td>
<td>Sí</td>
<td>Nombre lógico de la entidad de los registros que desea recuperar. Por ejemplo: &quot;account &quot;.</td>
</tr>
<tr>
<td>Opciones</td>
<td>Cadena</td>
<td>No</td>
<td><p>Opciones de consulta del sistema OData o consulta FetchXML para recuperar los datos. </p> 
<ul>
<li>Se admiten las siguientes opciones de consulta del sistema: <b>$Select</b>, <b>$Top</b>, <b>$Filter</b>, <b>$Expand</b>y <b>$OrderBy</b>.</li>
<li>Para especificar una consulta FetchXML, use el atributo <code>fetchXml</code> para especificar la consulta.</li>
</ul>
<p>Nota: siempre debe utilizar la opción de consulta del sistema <b>$Select</b> para limitar las propiedades devueltas para un registro de entidad incluyendo una lista separada por comas de nombres de propiedad. Esta es una práctica recomendada de rendimiento importante. Si no se especifican propiedades mediante <b>$Select</b>, se devolverán todas las propiedades.</li>
<p>Especifique las opciones de consulta a partir de <code>?</code>. También puede especificar varias opciones de consulta del sistema mediante <code>&amp;</code> para separar las opciones de consulta.
<p>Vea los ejemplos más adelante en este tema para ver cómo puede definir el parámetro <code>options</code> para varios escenarios de recuperación múltiple.</td>
</tr>
<tr>
<td>maxPageSize</td>
<td>Número</td>
<td>No</td>
<td><p>Especifique un número positivo que indique el número de registros de entidad que se van a devolver por página. Si no especifica este parámetro, el valor predeterminado se pasa como 5000.</p>
<p>Si el número de registros que se recuperan es mayor que el valor de <code>maxPageSize</code> especificado, <code>nextLink</code> atributo del objeto Promise devuelto contendrá un vínculo para recuperar el siguiente conjunto de entidades. </td>
</tr>
<tr>
<td>successCallback</td>
<td>Función</td>
<td>No</td>
<td><p>Función a la que se llama cuando se recuperan los registros de entidad. Se pasa a la función un objeto con los siguientes atributos:</p>
<ul>
<li><b>entidades</b>: una matriz de objetos JSON, donde cada objeto representa el registro de entidad recuperado que contiene los atributos y sus valores como pares de <code>key: value</code>. De forma predeterminada, se recupera el identificador del registro de entidad.</li>
<li><b>nextLink</b>: cadena. Si el número de registros que se recuperan es mayor que el valor especificado en el parámetro <code>maxPageSize</code> en la solicitud, este atributo devuelve la dirección URL para devolver el siguiente conjunto de registros.</li>
</ul>
</td>
</tr>
<tr>
<td>errorCallback</td>
<td>Función</td>
<td>No</td>
<td>Función a la que se va a llamar cuando se produzca un error en la operación.</td>
</tr>
</table>

## <a name="return-value"></a>Valor devuelto

Tipo: [promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) <RetrieveMultipleResponse>

Descripción: el `RetrieveMultipleResponse` devuelve un compromiso que contiene una matriz de objetos JSON que contienen los registros de entidad recuperados y el atributo **nextLink** con la dirección URL que apunta al siguiente conjunto de registros en caso de que se especifique la paginación (`maxPageSize`) en la solicitud, y el parámetro el número de registros devueltos supera el valor de paginación. Tiene los siguientes parámetros:

|Parámetro|Valor devuelto|Descripción|
|----|------|-------|
|jurídica|`Entity[]`|Matriz de objetos JSON, donde cada objeto representa el registro de entidad recuperado que contiene los atributos y sus valores.|
|nextLink|`string`|Si el número de registros que se recuperan es mayor que el valor especificado en el parámetro ' maxPageSize ' en la solicitud, este atributo devuelve la dirección URL para devolver el siguiente conjunto de registros.|


### <a name="related-topics"></a>Temas relacionados

[API Web](../webapi.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)