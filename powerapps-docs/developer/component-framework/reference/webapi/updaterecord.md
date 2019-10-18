---
title: updateRecord | Microsoft Docs
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
ms.assetid: 179ced61-ff0f-45ef-aa14-835ce99532cf
ms.openlocfilehash: 96037bcd8ca43448e928abef714ae031222d8e98
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340699"
---
# <a name="updaterecord"></a>updateRecord

[!INCLUDE [updaterecord-description](includes/updaterecord-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="syntax"></a>Sintaxis

`context.webAPI.updateRecord(entityLogicalName, id, data).then(successCallback, errorCallback);`

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
<td>Nombre lógico de la entidad del registro que se desea actualizar. Por ejemplo: &quot;account &quot;.</td>
</tr>
<tr>
<td>id</td>
<td>Cadena</td>
<td>Sí</td>
<td>GUID del registro de entidad que desea actualizar.</td>
</tr>
<tr>
<td>Data</td>
<td>Objeto</td>
<td>Sí</td>
<td><p>Un objeto JSON que contiene <code>key: value</code> pares, donde <code>key</code> es la propiedad de la entidad y <code>value</code> es el valor de la propiedad que desea actualizar.</p>
<p>Vea los ejemplos más adelante en este tema para ver cómo puede definir el objeto de <code>data</code> para varios escenarios de actualización.</td>
</tr>
<tr>
<td>successCallback</td>
<td>Función</td>
<td>No</td>
<td><p>Función a la que se va a llamar cuando se actualice un registro. Se pasará un objeto con las siguientes propiedades para identificar el registro actualizado:</p>
<ul>
<li><b>entityType</b>: cadena. Tipo de entidad del registro actualizado.</li>
<li><b>ID</b>: cadena. GUID del registro actualizado.</li>
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

Tipo: [Promise] ((dateformattinginfo. MD) <[Entityreference](../entityreference.md) >

Descripción: si se ejecuta correctamente, devuelve un objeto Promise que contiene los atributos especificados anteriormente en la descripción del parámetro **successCallback** .


### <a name="related-topics"></a>Temas relacionados

[API Web](../webapi.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)