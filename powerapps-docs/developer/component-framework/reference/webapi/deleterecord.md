---
title: deleteRecord | Microsoft Docs
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
ms.assetid: 5c9968bf-d535-425c-b1f1-0db6b7822de1
ms.openlocfilehash: f6c8dd6ea7d156e28ab3ae54d7fe37dad6c4546a
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340768"
---
# <a name="deleterecord"></a>deleteRecord

[!INCLUDE [deleterecord-description](includes/deleterecord-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="syntax"></a>Sintaxis

`context.webAPI.deleteRecord(entityLogicalName, id).then(successCallback, errorCallback);`

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
<td>Nombre lógico de la entidad del registro que se desea eliminar. Por ejemplo: &quot;account &quot;. </td>
</tr>
<tr>
<td>id</td>
<td>Cadena</td>
<td>Sí</td>
<td>GUID del registro de entidad que desea eliminar.</td>
</tr>
<tr>
<td>successCallback</td>
<td>Función</td>
<td>No</td>
<td><p>Función a la que se va a llamar cuando se elimine un registro. Se pasará un objeto con las siguientes propiedades para identificar el registro eliminado:</p>
<ul>
<li><b>entityType</b>: cadena. Tipo de entidad del registro.</li>
<li><b>ID</b>: cadena. GUID del registro.</li>
<li><b>Name</b>: cadena. Nombre del registro.</li>
</ul></td>
</tr>
<tr>
<td>errorCallback</td>
<td>Función</td>
<td>No</td>
<td>Función a la que se va a llamar cuando se produzca un error en la operación.</td>
</tr>
</table>

## <a name="return-value"></a>Valor devuelto

Tipo: [promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) <[EntityReference](../entityreference.md) >

### <a name="related-topics"></a>Temas relacionados

[API Web](../webapi.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)