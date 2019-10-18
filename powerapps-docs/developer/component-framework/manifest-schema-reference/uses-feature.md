---
title: Use-Feature | Microsoft Docs
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
ms.openlocfilehash: fe4d384c8dd53fc0f9efcf5558252984a4be74a3
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345897"
---
# <a name="uses-feature-element"></a>elemento use-Feature

Indica qué característica deben usar sus componentes.

## <a name="available-for"></a>Disponible para

Aplicaciones controladas por modelos

## <a name="parent-element"></a>Elemento primario

|Elemento|Descripción|
|--|--|
|uso de características|El elemento de uso de características actúa como un contenedor alrededor de los elementos de la característica de usos, que, a su vez, permiten a los desarrolladores declarar las características que su componente desea usar. Si no hay ningún elemento use-Feature definido, el elemento de uso de características no es necesario.|

## <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|Tipo|Requerido|
|--|--|---|----|
|Name|Nombre de la característica que se declara en el componente|`string`|Sí|
|Obligatorio|Indica si el componente requiere esa característica o no.|`boolean`|Sí|

### <a name="example"></a>Ejemplo 

```XML
<feature-usage>
    <uses-feature name="WebAPI" required="true" />
</feature-usage>
```

En la tabla siguiente se muestra la relación de estos valores con lo que sucede en el código en tiempo de ejecución si la función de característica estará disponible para llamar en función de la configuración de uso-característica definida en el manifiesto.

|Manifiesto|Si el host admite|Si el host no admite|
|----|----|-----|
|`uses-feature name="device.captureImage" required=”true"`|`Context.device.captureImage != null`, no es necesario realizar ninguna comprobación.|ADVERTENCIA en tiempo de diseño. Se producirá un error en la carga de componentes en tiempo de ejecución.|
|`uses-feature name="device.captureImage" required=”false"`|`Context.device.captureImage != null`|`Context.device.captureImage == null`, el componente puede comprobarlo de forma adaptativa en tiempo de ejecución. |
|ninguna|`Context.device.captureImage == null` |`Context.device.captureImage == null` |

### <a name="related-topics"></a>Temas relacionados

[Referencia del esquema del manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)