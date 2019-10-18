---
title: Elemento manifest | Microsoft Docs
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
ms.assetid: a48831c6-133a-4747-99fa-7cc1df4558d0
ms.openlocfilehash: d62b72c43a9c77a41c0a434a723d330ffa4b890a
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346265"
---
# <a name="manifest-element"></a>Elemento manifest

[!INCLUDE [manifest-description](includes/manifest-description.md)]

## <a name="available-for"></a>Disponible para

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|Apariciones|Disponible para|
|--|--|--|-------|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|1 o más|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental) (versión preliminar experimental)|
|[type-group](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|0 o más|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental) (versión preliminar experimental)|
|[property](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|0 o más|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental) (versión preliminar experimental)|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|0 o más|Aplicaciones controladas por modelos|
|[recurso](resources.md)|[!INCLUDE [resource-description](includes/resources-description.md)]|1 o más|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental) (versión preliminar experimental)|

## <a name="example"></a>Ejemplo

```xml
<?xml version="1.0" encoding="utf-8" ?>
<manifest>
    <control namespace="MyNameSpace" constructor="JSHelloWorldControl" version="1.0.0" display-name-key="JS_HelloWorldControl_Display_Key" description-key="JS_HelloWorldControl_Desc_Key" control-type="standard">
        <property name="myFirstProperty" display-name-key="myFirstProperty_Display_Key" description-key="myFirstProperty_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
        <resources>
            <code path="JS_HelloWorldControl.js" order="1" />
            <css path="css/JS_HelloWorldControl.css" order="1" />
        </resources>
    </control>
</manifest>
```

### <a name="related-topics"></a>Temas relacionados

[Referencia del esquema del manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)
