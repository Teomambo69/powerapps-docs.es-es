---
title: Elemento de recursos | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 66599c2f-6651-4b27-92da-a38897acdfb5
---

# <a name="resources-element"></a>elemento de recursos

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE [resources-description](includes/resources-description.md)]

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|

## <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|Repeticiones|
|--|--|--|
|[code](code.md)|[!INCLUDE [code-description](includes/code-description.md)]|1 o más|
|[css](css.md)|[!INCLUDE [css-description](includes/css-description.md)]|0 o más|
|[img](img.md)|[!INCLUDE [img-description](includes/img-description.md)]|0 o más|
|[html](html.md)|[!INCLUDE [html-description](includes/html-description.md)]|0 o más|
|[resx](resx.md)|[!INCLUDE [resx-description](includes/resx-description.md)]|0 o más|

## <a name="example"></a>Ejemplo

```xml
<resources>
  <code path="JS_HelloWorldControl.js" order="1" />
<css path="css/JS_HelloWorldControl.css" order="1" />
        </resources>
```

### <a name="related-topics"></a>Temas relacionados

[Referencia de esquema de manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../overview.md)