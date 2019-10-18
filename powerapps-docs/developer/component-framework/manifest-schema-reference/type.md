---
title: Tipo | Microsoft Docs
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
ms.assetid: d9fb178c-6cc6-48cc-99c0-9972e37dec3e
ms.openlocfilehash: 960f3aee9007c1bc8391ee7cf85a961234bbf3ae
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345966"
---
# <a name="type"></a>type

[!INCLUDE [type-description](includes/type-description.md)]

## <a name="available-for"></a>Disponible para

Aplicaciones controladas por modelos

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[type-group](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|

## <a name="value-element"></a>Elemento Value

Este elemento contiene un `string` con uno de los siguientes valores:

[!INCLUDE [type-table](includes/type-table.md)]

### <a name="example"></a>Ejemplo

```XML
<type-group name="numbers">
      <type>Whole.None</type>
      <type>Currency</type>
      <type>FP</type>
      <type>Decimal</type>
    </type-group>
```

### <a name="related-topics"></a>Temas relacionados

[Referencia del esquema del manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)