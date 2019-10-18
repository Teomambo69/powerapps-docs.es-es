---
title: ConditionExpression | Microsoft Docs
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
ms.assetid: bd90b3fd-a4b4-4999-8b53-d2a5dce4966b
ms.openlocfilehash: 10f7275643c0df4c2a4099a80b490fb5e27ce318
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345552"
---
# <a name="conditionexpression"></a>ConditionExpression

[!INCLUDE [conditionexpression-description](includes/conditionexpression-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="properties"></a>Propiedades

### <a name="attributename"></a>attributeName

Nombre de la columna del conjunto de datos en la que se va a aplicar el filtro.

**Tipo**: `string`

### <a name="conditionoperator"></a>conditionOperator

Operador que se usa para evaluar la condición.

**Tipo**: `enum`

El valor `conditionOperator` es una enumeración con los siguientes valores posibles

|Value|Member|
|--|--|
|-1|Ninguna|
|0|Sea|
|1|NotEqual|
|2|GreaterThan|
|3|LessThan|
|4|Mayor criticalthreshold|
|5|LessEqual|
|6|Forma|
|8|In (En)|
|12|Acepta|
|14|Ayer|
|15|Today|
|dieciséi|Mañana|
|18|Last7Days|
|18|Next7Days|
|19|LastWeek|
|20|ThisWeek|
|56|LastMonth|
|23|ThisMonth|
|15|En|
|26|OnOrBefore|
|,27|OnOrAfter|
|26|LastYear|
|29|ThisYear|
|33|LastXDays|
|34|NextXDays|
|37|LastXMonths|
|38|NextXMonths|
|49|Tuviera|
|70|InFiscalPeriodAndYear|
|75|Anterior|
|76|Objeto|
|77|NotUnder|
|78|AboveOrEqual|
|79|UnderOrEqual|
|87|ContainValues|

### <a name="entityaliasname"></a>entityAliasName

Nombre de alias de entidad. de este modo, se puede usar el filtrado en entidades vinculadas.

**Tipo**: `string`

### <a name="value"></a>value

Valor evaluado por la condición.

**Tipo**: `string | string[]`

### <a name="related-topics"></a>Temas relacionados

[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)