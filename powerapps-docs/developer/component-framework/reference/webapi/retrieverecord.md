---
title: RetrieveRecord | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dddeecc9-5067-420d-8bd7-4c914218e969
---

# <a name="retrieverecord"></a>retrieveRecord

[!INCLUDE [retrieverecord-description](includes/retrieverecord-description.md)]

## <a name="syntax"></a>Sintaxis

`retrieveRecord(entityLogicalName, id, options).then(successCallback, errorCallback);`

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
<td>El nombre lógico de la entidad del registro que desea recuperar. Por ejemplo: &quot;cuenta&quot;.</td>
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
<p>Especifique las opciones de consulta comenzando con <code>?</code>. Puede especificar también varias opciones de consulta usando <code>&amp;</code> para separar las opciones de consulta. Por ejemplo:</p>
<code>?$select=name&amp;$expand=primarycontactid($select=contactid,fullname)</code>
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


### <a name="related-topics"></a>Temas relacionados

[API web](../webapi.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)