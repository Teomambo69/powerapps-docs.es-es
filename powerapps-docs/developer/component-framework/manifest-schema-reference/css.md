---
title: Elemento CSS | Microsoft Docs
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
ms.assetid: b6119424-c0a4-4412-b25c-8239da6cbe36
ms.openlocfilehash: b7c96ba2bbb3e5d6d20df92e58ef0bc4005e7d37
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346587"
---
# <a name="css-element"></a>elemento CSS

[!INCLUDE [css-description](includes/css-description.md)]

## <a name="available-for"></a>Disponible para

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="attributes"></a>Atributos

|Nombre|Descripción|Tipo|Requerido|Disponible para|
|--|--|--|--|-----|
|`path`|Manifiesto de ruta de acceso relativa, donde se encuentran los archivos CSS|`string`|Sí|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental) (versión preliminar experimental)|
|`order`|El orden en el que deben cargarse los archivos CSS|`Positive integer`|Opta|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental) (versión preliminar experimental)|

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

## <a name="example"></a>Ejemplo

```xml
<css path="css/JS_HelloWorldControl.css" order="1" />
```

### <a name="related-topics"></a>Temas relacionados

[Referencia del esquema del manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)
