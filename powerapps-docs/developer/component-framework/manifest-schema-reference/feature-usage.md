---
title: uso de características | Microsoft Docs
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
ms.assetid: 87f5e921-4114-4710-a362-db741426a69b
ms.openlocfilehash: 21e76a2a17910fe36967364f063ff2fc9b25e153
ms.sourcegitcommit: 63ea15e2f861d43333aacda19230cd8922d7bdfd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2019
ms.locfileid: "72339641"
---
# <a name="feature-usage-element"></a>elemento de uso de características

El elemento de uso de características actúa como contenedor alrededor de los elementos de `uses-feature`, que a su vez permiten a los desarrolladores declarar qué características desea usar su componente. Si no hay ningún elemento use-Feature definido, el elemento de uso de características no es necesario.

## <a name="available-for"></a>Disponible para

Aplicaciones controladas por modelos

## <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|Disponible para|
|--|--|-----|
|[Use-Feature](uses-feature.md)|Indica qué característica deben usar sus componentes.|Aplicaciones controladas por modelos|


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
