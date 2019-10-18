---
title: FilterExpression | Microsoft Docs
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
ms.assetid: 19ad54b8-e044-4f07-a18e-b00d26b75832
ms.openlocfilehash: 7b613238f28987b688d4f2299506fa91b72a99a7
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343988"
---
# <a name="filterexpression"></a>FilterExpression

[!INCLUDE [filterexpression-description](includes/filterexpression-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="properties"></a>Propiedades

### <a name="conditions"></a>Cumplen

Conjunto de condiciones asociadas a este filtro.

**Tipo**: [condición](conditionexpression.md)[]

### <a name="filteroperator"></a>filterOperator

Operador que se usa para combinar condiciones en este filtro.

**Tipo**: `enum`

El valor `filterOperator` es una enumeración con los siguientes valores posibles

|Value|Member|
|--|--|
|0|And|
|1|Or|

### <a name="filters"></a>complementa

Los filtros secundarios que deben evaluarse después de evaluar este filtro.

**Tipo**: [FilterExpression](filterexpression.md)[]<br />

### <a name="related-topics"></a>Temas relacionados

[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)