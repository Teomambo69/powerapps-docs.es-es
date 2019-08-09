---
title: ConditionExpression | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd90b3fd-a4b4-4999-8b53-d2a5dce4966b
---

# <a name="conditionexpression"></a>ConditionExpression

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE [conditionexpression-description](includes/conditionexpression-description.md)]

## <a name="properties"></a>Propiedades

## <a name="attributename"></a>attributeName

El nombre de la columna del conjunto de datos a la que se aplicará el filtro.

**Tipo**: `string`

## <a name="conditionoperator"></a>conditionOperator

El operador usado para evaluar la condición.

**Tipo**: `enum`

El valor `conditionOperator` es una enumeración con los siguientes valores posibles:

|Value|Integrante|
|--|--|
|-1|Ninguno|
|0|Es igual a|
|1|NotEqual|
|2|GreaterThan|
|3|LessThan|
|4|GreaterEqual|
|5|LessEqual|
|6|Me gusta|
|8|En|
|12|Null|
|14|Ayer|
|15|Today|
|16|Mañana|
|17|Last7Days|
|18|Next7Days|
|19|LastWeek|
|20|ThisWeek|
|22|LastMonth|
|23|ThisMonth|
|25|El|
|26|OnOrBefore|
|27|OnOrAfter|
|28|LastYear|
|29|ThisYear|
|33|LastXDays|
|34|NextXDays|
|37|LastXMonths|
|38|NextXMonths|
|49|Contiene|
|70|InFiscalPeriodAndYear|
|75|Above|
|76|Menor que|
|77|NotUnder|
|78|AboveOrEqual|
|79|UnderOrEqual|
|87|ContainValues|

## <a name="entityaliasname"></a>entityAliasName

El nombre de alias de entidad para que pueda utilizare el filtrado en entidades vinculadas.

**Tipo**: `string`

## <a name="value"></a>valor

El valor evaluado por la condición.

**Tipo**: `string | string[]`


### <a name="related-topics"></a>Temas relacionados

[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../overview.md)