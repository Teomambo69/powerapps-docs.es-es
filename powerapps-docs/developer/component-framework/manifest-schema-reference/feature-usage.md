---
title: feature-usage | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87f5e921-4114-4710-a362-db741426a69b
---

# <a name="feature-usage-element"></a>elemento feature-usage

El elemento feature-usage actúa como contenedor de los elementos `uses-feature`, que a su vez permiten a los desarrolladores declarar qué características quieren que utilice su componente. Si no hay elementos uses-feature definidos, el elemento feature-usage no es obligatorio.

## <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|--|--|
|[uses-feature](uses-feature.md)|Indica qué característica desea que utilicen sus componentes.|


## <a name="example"></a>Ejemplo

```XML
<feature-usage>
    <uses-feature name="Device.captureAudio" required="true" />
    <uses-feature name="Device.captureImage" required="true" />
    <uses-feature name="Device.captureVideo" required="true" />
    <uses-feature name="Device.getBarcodeValue" required="true" />
    <uses-feature name="Device.getCurrentPosition" required="true" />
    <uses-feature name="Device.pickFile" required="true" />
    <uses-feature name="Utility" required="true" />
    <uses-feature name="WebAPI" required="true" />
 </feature-usage>
```
