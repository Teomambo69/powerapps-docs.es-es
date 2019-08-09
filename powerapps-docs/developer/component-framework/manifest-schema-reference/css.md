---
title: Elemento CSS | Microsoft Docs
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
ms.assetid: b6119424-c0a4-4412-b25c-8239da6cbe36
---

# <a name="css-element"></a>elemento css

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE [css-description](includes/css-description.md)]

## <a name="attributes"></a>Atributos

|Nombre|Descripción|Escriba|Requerido|
|--|--|--|--|
|`path`|La ruta de acceso relativa con respecto a manifiesta dónde se encuentran los archivos CSS|`string`|Sí|
|`order`|El orden en el que los archivos se deben cargar|`Positive integer`|Opcional|

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[recursos](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

## <a name="example"></a>Ejemplo

```xml
<css path="css/JS_HelloWorldControl.css" order="1" />
```

### <a name="related-topics"></a>Temas relacionados

[Referencia de esquema de manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../overview.md)
