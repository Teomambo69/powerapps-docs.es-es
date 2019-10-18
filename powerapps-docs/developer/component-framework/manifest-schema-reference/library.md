---
title: Elemento Library | Microsoft Docs
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
ms.assetid: 90f2b4c9-7396-4ab9-bc9f-810189dc18b7
ms.openlocfilehash: bd766864e6ef971b5245afad7d49af54b9369087
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346311"
---
# <a name="library-element"></a>elemento Library

[!INCLUDE [library-description](includes/library-description.md)]

## <a name="attributes"></a>Atributos

|Nombre|Descripción|Tipo|Requerido|
|--|--|--|--|
|`name`|Nombre de la biblioteca|`string`|Sí|
|`version`|La versión actual de la biblioteca|Entero positivo|Sí|
|`order`|El orden en que deben cargarse los archivos de biblioteca|Entero positivo|Sí|

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

## <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|Apariciones|
|--|--|--|
|[packaged_library]||0 o más|

## <a name="example"></a>Ejemplo

```xml
<resources>
<library name="AngularJSCore" version=">=1" order="1">
<packaged_library path="libs/angular.min.js" version="1.5.8" />
</library>
  </resources>
```

### <a name="related-topics"></a>Temas relacionados

[Referencia del esquema del manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)