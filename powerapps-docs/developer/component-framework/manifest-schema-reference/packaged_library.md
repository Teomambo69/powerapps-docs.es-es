---
title: Elemento de biblioteca empaquetada | Microsoft Docs
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
ms.assetid: 41c50db2-3096-4990-ac2b-e702c161bf4f
ms.openlocfilehash: 011aa2ab527cc2bd16fc99842e2388a3a6b0918e
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346196"
---
# <a name="packaged_library-element"></a>elemento packaged_library

[!INCLUDE [packaged_library-description](includes/packaged_library-description.md)]

## <a name="available-for"></a>Disponible para

Aplicaciones controladas por modelos

## <a name="attributes"></a>Atributos

|Nombre|Descripción|Tipo|Requerido|Disponible para|
|--|--|--|--|-------|
|`path`|Lugar donde se encuentran los archivos de biblioteca empaquetada|`string`|Sí|Aplicaciones controladas por modelos|
|`version`|La versión actual de la biblioteca empaquetada|`string`|Sí|Aplicaciones controladas por modelos|

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[Biblioteca](library.md)|[!INCLUDE [library-description](includes/library-description.md)]|

## <a name="example"></a>Ejemplo

```xml
<resources>
    <library name="AngularJSCore" version=">=1" order="1">
    <packaged_library path="libs/angular.min.js" version="1.5.8" />
    </library>
```

### <a name="related-topics"></a>Temas relacionados

[Referencia del esquema del manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)
