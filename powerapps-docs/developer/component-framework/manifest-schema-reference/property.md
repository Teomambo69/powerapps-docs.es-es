---
title: Elemento Property | Microsoft Docs
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
ms.assetid: 45f4872d-c1d2-4c5a-8721-251b96ede370
ms.openlocfilehash: ee4e0b0259d5978f3e84757d4023827ada45f01e
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346150"
---
# <a name="property-element"></a>elemento Property

[!INCLUDE [property-description](includes/property-description.md)]

## <a name="available-for"></a>Disponible para

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="attributes"></a>Atributos

|Nombre|Descripción|Tipo|Requerido|
|--|--|--|--|
|`name`|Nombre de la propiedad|`string`|Sí|
|`display-name-key`|Se utiliza en las pantallas de personalización como cadenas traducidas que describen el nombre de la propiedad.|`string`|Sí|
|`of-type`|Define el tipo de datos de la propiedad.|Ver [comentarios](#remarks)|Opta|
|`usage`|El atributo Usage identifica si la propiedad está pensada para representar un atributo de entidad que el componente puede cambiar (enlazado) o valores de solo lectura (entrada)|`bound` o `input`|Opta|
|`required`|Si la propiedad es obligatoria o no|`boolean`|Opta|
|`of-type-group`|Nombre del grupo de tipo tal y como se define en el manifiesto|`string`|Opta|
|`description-key`|Se utiliza en las pantallas de personalización como cadenas traducidas que describen la descripción de la propiedad.|`string`|Opta|
|`default-value`|El valor de configuración predeterminado proporcionado al componente. En las aplicaciones controladas por modelos, este atributo solo se permite en las entradas, ya que los parámetros enlazados esperan tener un campo asociado.|`string`|Opta|

### <a name="remarks"></a>Sección

El valor del atributo `of-type` debe ser uno de los siguientes:

[!INCLUDE [type-table](includes/type-table.md)]

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[manifest](manifest.md)|[!INCLUDE [manifest-description](includes/manifest-description.md)]|


## <a name="example"></a>Ejemplo

```xml
<property name="myFirstProperty" display-name-key="myFirstProperty_Display_Key" 
description-key="myFirstProperty_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
```

### <a name="related-topics"></a>Temas relacionados

[Referencia del esquema del manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)
