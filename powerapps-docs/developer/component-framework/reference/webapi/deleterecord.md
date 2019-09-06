---
title: deleteRecord | Microsoft Docs
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
ms.assetid: 5c9968bf-d535-425c-b1f1-0db6b7822de1
---

# <a name="deleterecord"></a>deleteRecord

[!INCLUDE [deleterecord-description](includes/deleterecord-description.md)]

## <a name="syntax"></a>Sintaxis

`deleteRecord(entityLogicalName, id).then(successCallback, errorCallback);`

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
<td>El nombre lógico de la entidad del registro que desea eliminar. Por ejemplo: &quot;cuenta&quot;. </td>
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


### <a name="related-topics"></a>Temas relacionados

[API web](../webapi.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)