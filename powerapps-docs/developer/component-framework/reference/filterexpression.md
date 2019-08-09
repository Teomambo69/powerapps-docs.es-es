---
title: FilterExpression | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19ad54b8-e044-4f07-a18e-b00d26b75832
---

# <a name="filterexpression"></a>FilterExpression

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE [filterexpression-description](includes/filterexpression-description.md)]

## <a name="properties"></a>Propiedades

## <a name="conditions"></a>condiciones

El conjunto de condiciones asociadas a este filtro.

**Tipo**: [ConditionExpression](conditionexpression.md)[]

## <a name="filteroperator"></a>filterOperator

El operador usado para combinar condiciones en este filtro.

**Tipo**: `enum`

El valor `filterOperator` es una enumeración con los siguientes valores posibles:

|Value|Integrante|
|--|--|
|0|Y|
|1|Or|

## <a name="filters"></a>filtros

Los filtros secundarios que se deben evaluar después de evaluar este filtro.

**Tipo**: [FilterExpression](filterexpression.md)[]<br />

### <a name="related-topics"></a>Temas relacionados

[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../overview.md)