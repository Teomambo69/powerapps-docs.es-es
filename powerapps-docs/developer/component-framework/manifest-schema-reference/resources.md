---
title: Elemento Resources | Microsoft Docs
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
ms.assetid: 66599c2f-6651-4b27-92da-a38897acdfb5
ms.openlocfilehash: a7df2dde98667fd0de8489943094ad6f4ff210f0
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346081"
---
# <a name="resources-element"></a>elemento Resources

[!INCLUDE [resources-description](includes/resources-description.md)]

## <a name="available-for"></a>Disponible para

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|

## <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|Apariciones|
|--|--|--|
|[code](code.md)|[!INCLUDE [code-description](includes/code-description.md)]|1|
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

[Referencia del esquema del manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)