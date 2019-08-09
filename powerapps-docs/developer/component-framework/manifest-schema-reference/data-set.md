---
title: Elemento DataSet | Microsoft Docs
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
ms.assetid: 9ffe8930-b290-4252-98d4-a1195b00205f
---

# <a name="data-set-element"></a>elemento data-set

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE [data-set-description](includes/data-set-description.md)]

## <a name="attributes"></a>Atributos

|Nombre|Descripción|Escriba|Requerido|
|--|--|--|--|
|`description-key`|Se usa en la pantalla de personalización como cadenas localizadas que describen la descripción de la propiedad.|`string`|Opcional|
|`display-name-key`|Se usa en las pantallas de personalización como cadenas localizadas que describen el nombre de la propiedad.|`string`|Sí|
|`name`|Nombre de la cuadrícula|`string`|Sí|

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|

## <a name="example"></a>Ejemplo

```xml
 <data-set name="dataSetGrid" display-name-key="DataSetGridProperty">
 </data-set>
```

### <a name="related-topics"></a>Temas relacionados

[Referencia de esquema de manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../overview.md)