---
title: Paginación | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 12891e96-972c-4289-bbde-2bc261cd1f12
---

# <a name="paging"></a>Paginación

[!INCLUDE [paging-description](includes/paging-description.md)]

## <a name="totalresultcount"></a>totalResultCount

Número total de resultados en el servidor para la consulta actual.

**Tipo**: `number`

## <a name="hasnextpage"></a>hasNextPage

Si el conjunto de resultados puede ser paginado hacia atrás.

**Tipo**: `boolean`

## <a name="haspreviouspage"></a>hasPreviousPage

Si el conjunto de resultados puede ser paginado hacia atrás.

**Tipo**: `boolean`

## <a name="methods"></a>Métodos

|Método | Descripción |
| ------|-------------|
|[loadNextPage](paging/loadnextpage.md)|[!INCLUDE [loadnextpage-description](paging/includes/loadnextpage-description.md)]|
|[loadPreviousPage](paging/loadpreviouspage.md)|[!INCLUDE [loadpreviouspage-description](paging/includes/loadpreviouspage-description.md)]|
|[reset](paging/reset.md)|[!INCLUDE [reset-description](paging/includes/reset-description.md)]|
|[setPageSize](paging/setpagesize.md)|[!INCLUDE [setpagesize-description](paging/includes/setpagesize-description.md)]|


### <a name="related-topics"></a>Temas relacionados

[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../overview.md)