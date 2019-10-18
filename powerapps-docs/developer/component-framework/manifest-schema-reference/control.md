---
title: Control (elemento) | Microsoft Docs
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
ms.assetid: 4dacd337-c9df-458e-86f3-bfb3ab543ea7
ms.openlocfilehash: aa02b89ce1e032a3cf2fdedca8f0fdf79cb84045
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346633"
---
# <a name="control-element"></a>control (elemento)

[!INCLUDE [control-description](includes/control-description.md)]

## <a name="available-for"></a>Disponible para

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="attributes"></a>Atributos

|Nombre|Descripción|Tipo|Requerido|Disponible para|
|--|--|--|--|--------|
|`namespace`|Define el prototipo de objeto del componente.|[!INCLUDE [alphanumerictype-description](includes/alphanumerictype-description.md)]|Sí|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental) (versión preliminar experimental)|
|`constructor`|Método para inicializar el objeto.|[!INCLUDE [alphanumerictype-description](includes/alphanumerictype-description.md)]|Sí|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental) (versión preliminar experimental)|
|`control-type`|Normal|[!INCLUDE [controltype-description](includes/controltype-description.md)]|No|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental) (versión preliminar experimental)|
|`description-key`|Define la descripción del componente que se verá en la interfaz de usuario.|`string`|No|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental) (versión preliminar experimental)|
|`display-name-key`|Define el nombre del control que se muestra en la interfaz de usuario.|`string`|Sí|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental) (versión preliminar experimental)|
|`preview-image`|Imagen que se usará en las pantallas de personalización para mostrar una vista previa del componente.|`string`|No|Aplicaciones controladas por modelos|
|`version`|Define la versión del componente definido en el [control de versiones semántico](https://semver.org)|`string`|Sí|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental) (versión preliminar experimental)|
<!--|`hidden`|Define si el componente debe estar oculto o no|[!INCLUDE [booleantype-description](includes/booleantype-description.md)]| No|Aplicaciones controladas por modelos|-->

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[manifest](manifest.md)|[!INCLUDE [manifest-description](includes/manifest-description.md)]|

## <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|Apariciones|
|--|--|--|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|0 o más|
|[property](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|0 o más|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|1|
|[type-group](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|0 o más|

## <a name="example"></a>Ejemplo

```xml
<control namespace="MyNameSpace" constructor="JSHelloWorldControl" version="1.0.0"
 display-name-key="JS_HelloWorldControl_Display_Key" description-key="JS_HelloWorldControl_Desc_Key"
 control-type="standard" preview-image="img/preview.png">
</control>
  ```

### <a name="related-topics"></a>Temas relacionados

[Referencia del esquema del manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)