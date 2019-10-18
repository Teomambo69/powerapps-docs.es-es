---
title: Elemento set de propiedad | Microsoft Docs
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
ms.assetid: 996f10e5-8057-40ea-9680-555e4cd682ff
ms.openlocfilehash: 98e0bcf7588e72f001e45471c87f0050dd0846ba
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346242"
---
# <a name="property-set-element"></a>elemento de conjunto de propiedades

[!INCLUDE [property-set-description](includes/property-set-description.md)]

## <a name="available-for"></a>Disponible para

Aplicaciones controladas por modelos

## <a name="attributes"></a>Atributos

|Nombre|Descripción|Tipo|Requerido|
|--|--|--|--|
|`name`|Nombre del campo|`string`|Sí|
|`display-name-key`|Se utiliza en pantallas de personalización como cadenas traducidas que describen el nombre de la propiedad.|`string`|Sí|
|`description-key`|Se utiliza en pantallas de personalización como cadenas traducidas que describen la descripción de la propiedad.|`string`|Opta|
|`of-type`|Define el tipo de datos de la propiedad.|Ver [comentarios](#remarks)|Opta|
|`required`|Indica si la propiedad es obligatoria o no|`boolean`|Opta|
|`of-type-group`|Nombre del grupo de tipo tal y como se define en el manifiesto|`string`|Opta|
|`usage`|El atributo Usage identifica si la propiedad está pensada para representar un atributo de entidad que el componente puede cambiar (enlazado) o valores de solo lectura (entrada)|`bound` o `input`|Sí|

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|

## <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|Apariciones|
|--|--|--|
|[distintos](types.md)||0 o más|

### <a name="remarks"></a>Sección

El valor del atributo `of-type` debe ser uno de los siguientes:

[!INCLUDE [type-table](includes/type-table.md)]

### <a name="related-topics"></a>Temas relacionados

[Referencia del esquema del manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)