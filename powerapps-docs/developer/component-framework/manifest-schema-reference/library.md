---
title: Library Element | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 90f2b4c9-7396-4ab9-bc9f-810189dc18b7
---

# <a name="library-element"></a>elemento de biblioteca

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE [library-description](includes/library-description.md)]

## <a name="attributes"></a>Atributos

|Nombre|Descripción|Escriba|Requerido|
|--|--|--|--|
|`name`|Nombre de la biblioteca|`string`|Sí|
|`version`|La versión de la biblioteca actual|Entero positivo|Sí|
|`order`|El orden en el que los archivos de biblioteca se deben cargar|Entero positivo|Sí|

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[recursos](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

## <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|Repeticiones|
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

[Referencia de esquema de manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../overview.md)