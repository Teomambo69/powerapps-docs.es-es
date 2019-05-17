---
title: createRecord | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
ms.assetid: 9179f03b-9d26-4253-9535-13ab544d58ac
---

# <a name="createrecord"></a>createRecord

[!INCLUDE [createrecord-description](includes/createrecord-description.md)]

## <a name="syntax"></a>Sintaxis

`createRecord(entityLogicalName, data).then(successCallback, errorCallback);`

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
<td>Nombre lógico de la entidad que quiere crear. Por ejemplo: &quot;cuenta&quot;.</td>
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

### <a name="related-topics"></a>Temas relacionados

[API web](../webapi.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)