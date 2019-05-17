---
title: Elemento de control | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
ms.assetid: 4dacd337-c9df-458e-86f3-bfb3ab543ea7
---

# <a name="control-element"></a>elemento de control

[!INCLUDE [control-description](includes/control-description.md)]

## <a name="attributes"></a>Atributos

|Nombre|Descripción|Escriba|Requerido|
|--|--|--|--|
|`namespace`|Define el prototipo de objeto del componente|[!INCLUDE [alphanumerictype-description](includes/alphanumerictype-description.md)]|sí|
|`constructor`|Un método para inicializar el objeto|[!INCLUDE [alphanumerictype-description](includes/alphanumerictype-description.md)]|sí|
|`control-type`|Estándar|[!INCLUDE [controltype-description](includes/controltype-description.md)]|no|
|`description-key`|Se usa en las pantallas de personalización como cadenas localizadas que describen la descripción de la propiedad.|`string`|no|
|`display-name-key`|Se usa en las pantallas de personalización como cadenas localizadas que describen el nombre de la propiedad.|`string`|sí|
|`preview-image`|Imagen que se usará en las pantallas de personalización para mostrar una vista previa del componente al personalizador|`string`|no|
|`version`|Define la versión del componente definido en [Control de versiones semántico](https://semver.org)|`string`|sí|
|`hidden`|Define si el componente debe estar oculto o no|[!INCLUDE [booleantype-description](includes/booleantype-description.md)]| no|

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[manifiesto](manifest.md)|[!INCLUDE [manifest-description](includes/manifest-description.md)]|

## <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|Repeticiones|
|--|--|--|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|0 o más|
|[propiedad](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|0 o más|
|[recursos](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|1|
|[type-group](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|0 o más|

## <a name="example"></a>Ejemplo

```xml
<control namespace="MyNameSpace" constructor="JSHelloWorldControl" version="1.0.0"
 display-name-key="JS_HelloWorldControl_Display_Key" description-key="JS_HelloWorldControl_Desc_Key"
 control-type="standard" preview-image="img/preview.png">
</control>
  ```

### <a name="related-topics"></a>Temas relacionados

[Referencia de esquema de manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../overview.md)