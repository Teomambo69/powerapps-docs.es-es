---
title: Elemento emergente | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b0af1803-ae3a-41c2-a8a5-b15970bd6f96
---

# <a name="popup"></a>Ventana emergente

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE [popup-description](includes/popup-description.md)]

## <a name="properties"></a>Propiedades

## <a name="closeonoutsideclick"></a>closeOnOutsideClick

Indica si el elemento emergente se cierra al hacer clic en un mouse externo.

**Tipo**: `boolean`

## <a name="content"></a>content

Elemento DOM estático que se insertará.

**Tipo**: [HTMLElement](https://developer.mozilla.org/docs/Web/API/HTMLElement)

## <a name="id"></a>id.

El Id. que se establecerá como componente de anclaje si lo hay.

**Tipo**: `string`

## <a name="name"></a>nombre

El nombre del elemento emergente. Se usa como referencia para abrir elementos emergentes.

**Tipo**: `string`

## <a name="popuptoopen"></a>popupToOpen

El nombre del elemento emergente que se debe abrir.

**Tipo**: `string`

### <a name="remarks"></a>Comentarios

Se debe definir solo en un elemento emergente de la raíz. Para abrir los elementos emergentes anidadas, se debe proporcionar una cadena como `rootName.nestedName.[allOtherNestedNames]`. Para cerrar los elementos emergentes, se debe proporcionar una cadena vacía. Esta propiedad se propagará automáticamente a los elementos secundarios.

## <a name="type"></a>tipo

Tipo de elemento emergente

**Tipo**: `enum`

El valor `type` es una enumeración con los siguientes valores posibles:

|Value|Integrante|
|--|--|
|1|Raíz|
|2|Anidado|

### <a name="remarks"></a>Comentarios

Solo debe haber un elemento emergente `Root` para cada conjunto de elementos emergentes.

### <a name="related-topics"></a>Temas relacionados

[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../overview.md)