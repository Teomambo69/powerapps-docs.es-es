---
title: Elemento resx | Microsoft Docs
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
ms.assetid: 38acfda3-4adc-4aa2-bb8b-f29ba572a6e5
ms.openlocfilehash: 29c89541c2519b36559ab49d2b0483f19b545573
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346035"
---
# <a name="resx-element"></a>elemento resx

[!INCLUDE [resx-description](includes/resx-description.md)]

## <a name="available-for"></a>Disponible para

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="attributes"></a>Atributos

|Nombre|Descripción|Tipo|Requerido|
|--|--|--|--|
|`path`|Manifiesto de ruta de acceso relativa w. t donde se encuentran los archivos resx|`string`|Sí|
|`version`|Versión actual del archivo resx|`string`|Sí|

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

## <a name="example"></a>Ejemplo

```xml
<resources>
      <code path="TS_LocalizationAPI.js" order="1" />
        <css path="css/TS_LocalizationAPI.css" order="1" />
      <resx path="strings/TSLocalizationAPI.1033.resx" version="1.0.0" />
      <resx path="strings/TSLocalizationAPI.1035.resx" version="1.0.0" />
      <resx path="strings/TSLocalizationAPI.3082.resx" version="1.0.0" />
    </resources>
```

### <a name="related-topics"></a>Temas relacionados

[Referencia del esquema del manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)
