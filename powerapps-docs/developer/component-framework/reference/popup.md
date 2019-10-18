---
title: Popup | Microsoft Docs
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
ms.assetid: b0af1803-ae3a-41c2-a8a5-b15970bd6f96
ms.openlocfilehash: bb28a979ac721eded06025a56588023c211ea6f9
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342217"
---
# <a name="popup"></a>Popup

[!INCLUDE [popup-description](includes/popup-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="properties"></a>Propiedades

### <a name="closeonoutsideclick"></a>closeOnOutsideClick

Indica si el control popup se cierra con un clic fuera del mouse. Cuando se establece en `false`, el elemento emergente no se cerrará al hacer clic fuera del mouse.

**Tipo**: `boolean`

### <a name="content"></a>Content

Elemento DOM estático que se va a insertar.

**Tipo**: [HtmlElement](https://developer.mozilla.org/docs/Web/API/HTMLElement)

### <a name="id"></a>id

Identificador que se va a establecer en el componente de delimitador, si existe.

**Tipo**: `string`

### <a name="name"></a>Name

Nombre del elemento emergente. Se usa como referencia para abrir los elementos emergentes.

**Tipo**: `string`

### <a name="popuptoopen"></a>popupToOpen

Nombre del elemento emergente que debe abrirse.

**Tipo**: `string`

### <a name="remarks"></a>Sección

Debe definirse solo en una ventana emergente raíz. Para abrir elementos emergentes anidados, se debe proporcionar una cadena como `rootName.nestedName.[allOtherNestedNames]`. Para cerrar los elementos emergentes, se debe proporcionar una cadena vacía. Esta propiedad se propagará automáticamente a los elementos secundarios.

## <a name="type"></a>type

El tipo de popup, que se describe en la enumeración PopupType. Solo debe haber un elemento emergente `root` para cada conjunto de elementos emergentes.

**Tipo**: `enum`

El valor `type` es una enumeración con los siguientes valores posibles

|Value|Member|
|--|--|
|1|Raíces|
|2|Anidada|

### <a name="remarks"></a>Sección

Debe ser solo una `Root` ventana emergente para cada conjunto de elementos emergentes.

### <a name="related-topics"></a>Temas relacionados

[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)