---
title: updateRecord | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 179ced61-ff0f-45ef-aa14-835ce99532cf
---

# <a name="updaterecord"></a>updateRecord

[!INCLUDE [updaterecord-description](includes/updaterecord-description.md)]

## <a name="syntax"></a>Sintaxis

`updateRecord(entityLogicalName, id, data).then(successCallback, errorCallback);`

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
<td>El nombre lógico de la entidad del registro que desea actualizar. Por ejemplo: &quot;cuenta&quot;.</td>
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
<td><p>Un objeto JSON que contiene pares <code>key: value</code>, donde <code>key</code> es la propiedad de la entidad y <code>value</code> es el valor de la propiedad que desea actualizar.</p>
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


### <a name="related-topics"></a>Temas relacionados

[API web](../webapi.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)