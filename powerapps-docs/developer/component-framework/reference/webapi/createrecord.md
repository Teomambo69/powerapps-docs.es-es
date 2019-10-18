---
title: createRecord | Microsoft Docs
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
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 9179f03b-9d26-4253-9535-13ab544d58ac
ms.openlocfilehash: f3a2b860f17d7efaaf8efebcf2418aef04478947
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340837"
---
# <a name="createrecord"></a>createRecord

[!INCLUDE [createrecord-description](includes/createrecord-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="syntax"></a>Sintaxis

`context.webAPI.createRecord(entityLogicalName, data).then(successCallback, errorCallback);`

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
<td>Nombre lógico de la entidad que desea crear. Por ejemplo: &quot;account &quot;.</td>
</tr>
<tr>
<td>Data</td>
<td>Objeto</td>
<td>Sí</td>
<td><p>Un objeto JSON que define los atributos y valores para el nuevo registro de entidad.</p>
<p>Vea los ejemplos más adelante en este tema para ver cómo puede definir el objeto de <code>data</code> para varios escenarios de creación.</td>
</tr>
<tr>
<td>successCallback</td>
<td>Función</td>
<td>No</td>
<td><p>Función a la que se llama cuando se crea un registro. Se pasará un objeto con las siguientes propiedades para identificar el nuevo registro:</p>
<ul>
<li><b>entityType</b>: cadena. Nombre lógico de la entidad del nuevo registro.</li>
<li><b>ID</b>: cadena. GUID del nuevo registro.</li>
</ul></td>
</tr>
<tr>
<td>errorCallback</td>
<td>Función</td>
<td>No</td>
<td>Función a la que se va a llamar cuando se produzca un error en la operación. Se pasará un objeto con las siguientes propiedades:
<ul>
<li><b>ErrorCode</b>: número. Código de error.</li>
<li><b>Message</b>: cadena. Un mensaje de error que describe el problema.</li>
</ul></td>
</tr>
</table>

## <a name="return-value"></a>Valor devuelto

Tipo: [promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) <[EntityReference](../entityreference.md) >

Descripción: si se ejecuta correctamente, devuelve un objeto Promise que contiene los atributos especificados anteriormente en la descripción del parámetro **successCallback** .

### <a name="related-topics"></a>Temas relacionados

[API Web](../webapi.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)