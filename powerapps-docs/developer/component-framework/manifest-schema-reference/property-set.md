---
title: Elemento de conjunto de propiedades | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 996f10e5-8057-40ea-9680-555e4cd682ff
---

# <a name="property-set-element"></a>elemento property-set

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE [property-set-description](includes/property-set-description.md)]

## <a name="attributes"></a>Atributos

|Nombre|Descripción|Escriba|Requerido|
|--|--|--|--|
|`name`|Nombre del campo|`string`|Sí|
|`display-name-key`|Se usa en las pantallas de personalización como cadenas localizadas que describen el nombre de la propiedad|`string`|Sí|
|`description-key`|Se usa en las pantallas de personalización como cadenas localizadas que describen la descripción de la propiedad|`string`|Opcional|
|`of-type`|Deeine el tipo de datos de la propiedad|Consulte [Notas](#remarks)|Opcional|
|`required`|Si la propiedad es requerida o no|`boolean`|Opcional|
|`of-type-group`|Nombre del grupo de tipos definido en el manifiesto|`string`|Opcional|

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|

## <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|Repeticiones|
|--|--|--|
|[tipos](types.md)||0 o más|

### <a name="remarks"></a>Comentarios

El valor del atributo `of-type` debe ser uno de los siguientes:

[!INCLUDE [type-table](includes/type-table.md)]

### <a name="related-topics"></a>Temas relacionados

[Referencia de esquema de manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../overview.md)