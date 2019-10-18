---
title: RetrieveRecord | Microsoft Docs
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
ms.assetid: dddeecc9-5067-420d-8bd7-4c914218e969
ms.openlocfilehash: 9c77bf9975bd1f1f115df9385061c008975cc184
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341711"
---
# <a name="retrieverecord"></a>retrieveRecord

[!INCLUDE [retrieverecord-description](includes/retrieverecord-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="syntax"></a>Sintaxis

`context.webAPI.retrieveRecord(entityLogicalName, id, options).then(successCallback, errorCallback);`

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
<td>Nombre lógico de la entidad del registro que se desea recuperar. Por ejemplo: &quot;account &quot;.</td>
</tr>
<tr>
<td>id</td>
<td>Cadena</td>
<td>Sí</td>
<td>GUID del registro de entidad que desea recuperar.</td>
</tr>
<tr>
<td>Opciones</td>
<td>Cadena</td>
<td>No</td>
<td><p>Opciones de consulta del sistema de OData, <b>$Select</b> y <b>$Expand</b>, para recuperar los datos.</p>
<ul><li>Utilice la opción de consulta del sistema <b>$Select</b> para limitar las propiedades devueltas por la inclusión de una lista separada por comas de nombres de propiedad. Esta es una práctica recomendada de rendimiento importante. Si no se especifican propiedades mediante <b>$Select</b>, se devolverán todas las propiedades.</li>
<li>Utilice la opción de consulta del sistema <b>$Expand</b> para controlar qué datos de las entidades relacionadas se devuelven. Si solo incluye el nombre de la propiedad de navegación, recibirá todas las propiedades de los registros relacionados. Puede limitar las propiedades devueltas para los registros relacionados mediante la opción de consulta del sistema <b>$Select</b> entre paréntesis después del nombre de la propiedad de navegación. Use esto para las propiedades de navegación de valor <i>único</i> y <i>con valores de colección</i> .</li>
</ul>
<p>Especifique las opciones de consulta a partir de <code>?</code>. También puede especificar varias opciones de consulta mediante <code>&amp;</code> para separar las opciones de consulta. Por ejemplo:</p>
<code>?$select=name&amp;$expand=primarycontactid($select=contactid,fullname)</code>
<p>Vea los ejemplos más adelante en este tema para ver cómo puede definir el parámetro <code>options</code> para varios escenarios de recuperación.</td>
</tr>
<tr>
<td>successCallback</td>
<td>Función</td>
<td>No</td>
<td><p>Función a la que se va a llamar cuando se recupere un registro. Un objeto JSON con las propiedades y los valores recuperados se pasará a la función.</p>
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

Tipo: [promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) <[entidad](../entity.md) >



### <a name="related-topics"></a>Temas relacionados

[API Web](../webapi.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)