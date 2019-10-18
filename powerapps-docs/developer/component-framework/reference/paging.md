---
title: Paging | Microsoft Docs
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
ms.assetid: 12891e96-972c-4289-bbde-2bc261cd1f12
ms.openlocfilehash: ccf68c94e0b11f8a1227199609a9c21c1923ad7b
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342194"
---
# <a name="paging"></a>Paging

[!INCLUDE [paging-description](includes/paging-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="properties"></a>Propiedades

### <a name="totalresultcount"></a>totalResultCount

Número total de resultados en el servidor para la consulta actual.

**Tipo**: `number`

### <a name="hasnextpage"></a>hasNextPage

Si el conjunto de resultados se puede paginar hacia atrás.

**Tipo**: `boolean`

### <a name="haspreviouspage"></a>hasPreviousPage

Si el conjunto de resultados se puede paginar hacia atrás.

**Tipo**: `boolean`

## <a name="methods"></a>Modalidades

|Forma | Descripción |
| ------|-------------|
|[loadNextPage](paging/loadnextpage.md)|[!INCLUDE [loadnextpage-description](paging/includes/loadnextpage-description.md)]|
|[loadPreviousPage](paging/loadpreviouspage.md)|[!INCLUDE [loadpreviouspage-description](paging/includes/loadpreviouspage-description.md)]|
|[determinado](paging/reset.md)|[!INCLUDE [reset-description](paging/includes/reset-description.md)]|
|[setPageSize](paging/setpagesize.md)|[!INCLUDE [setpagesize-description](paging/includes/setpagesize-description.md)]|
|pageSize|Número de registros que se van a devolver por página de conjunto de archivos. En los formularios, las páginas del conjunto de datos se aplican al formato (número de filas) y, en otras personas, puede elegir las opciones personales.|


### <a name="related-topics"></a>Temas relacionados

[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)