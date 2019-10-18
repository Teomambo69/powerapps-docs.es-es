---
title: Elemento Code | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/4/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 44d9fcfb-0cd8-48cc-aace-dd589099dd79
ms.openlocfilehash: 2caf89a73dba006240c5bb6e8c874dfdd795d8c2
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346656"
---
# <a name="code-element"></a>elemento Code

[!INCLUDE [code-description](includes/code-description.md)]

## <a name="available-for"></a>Disponible para

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="attributes"></a>Atributos

|Nombre|Descripción|Tipo|Requerido|Disponible para|
|--|--|--|--|-----|
|`path`|Lugar donde se encuentran los archivos de recursos|`String`|Sí|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental) (versión preliminar experimental)|
|`order`|El orden en que deben cargarse los archivos de recursos|`Positive integer`|Sí|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental) (versión preliminar experimental)|

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

### <a name="example"></a>Ejemplo

```XML
<code path="TS_IncrementControl.js" order="1" />
        <css path="css/TS_IncrementControl.css" order="1" />
      <resx path="strings/TSIncrementControl.1033.resx" version="1.0.0" />
```

### <a name="related-topics"></a>Temas relacionados

[Referencia del esquema del manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)