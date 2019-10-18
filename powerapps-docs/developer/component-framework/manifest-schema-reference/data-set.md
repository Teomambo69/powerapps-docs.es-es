---
title: Elemento DataSet | Microsoft Docs
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
ms.assetid: 9ffe8930-b290-4252-98d4-a1195b00205f
ms.openlocfilehash: adf672b036d1f49619cbc4a5ef72661fbeebf013
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346564"
---
# <a name="data-set-element"></a>elemento de conjunto de datos

[!INCLUDE [data-set-description](includes/data-set-description.md)]

## <a name="attributes"></a>Atributos

|Nombre|Descripción|Tipo|Requerido|Disponible para|
|--|--|--|--|-------|
|`description-key`|Define la descripción de la propiedad.|`string`|Opta|
|`display-name-key`|Define el nombre de la propiedad.|`string`|Sí|
|`name`|Nombre de la cuadrícula|`string`|Sí|
|`cds-data-set-options`|Muestra CommandBar, ViewSelector, QuickFindSearch si está establecido en true. |`boolean`|Sí|

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|

## <a name="example"></a>Ejemplo

```xml
 <data-set name="dataSetGrid" display-name-key="DataSetGridProperty" cds-data-set-options="displayCommandBar:true;displayViewSelector:true;displayQuickFindSearch:true">
 </data-set>
```

### <a name="related-topics"></a>Temas relacionados

[Referencia del esquema del manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)