---
title: Funciones Average, Max, Min, StdevP, Sum y VarP | Microsoft Docs
description: Información de referencia de las funciones Average, Max, min, StdevP, SUM y VarP en Power Apps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/15/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7ff5e8440295f97268127cdc8a2d5646d5b676fa
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731447"
ms.PowerAppsDecimalTransform: true
---
# <a name="average-max-min-stdevp-sum-and-varp-functions-in-power-apps"></a>Funciones Average, Max, min, StdevP, SUM y VarP en Power apps
Funciones de agregado que resumen un conjunto de números.

## <a name="description"></a>Descripción
La función **Average** calcula el promedio, o media aritmética, de los argumentos.

La función **Max** encuentra el valor máximo.

La función **Min** encuentra el valor mínimo.

La función **Sum** calcula la suma de los argumentos.

La función **StdevP** calcula la desviación estándar de los argumentos.

La función **VarP** calcula la varianza de los argumentos.

Puede proporcionar los valores de estas funciones como:

* Argumentos independientes. Por ejemplo, **Sum( 1; 2; 3 )** da 6 como resultado.
* Una [tabla](../working-with-tables.md) y una fórmula para operar sobre esa tabla.  La suma total se calculará según los valores de la fórmula para cada [registro](../working-with-tables.md#records).  

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

Estas funciones solo operan sobre valores numéricos. Se omiten otros tipos de valores, como cadenas o registros. Use la función **[Value](function-value.md)** para convertir en número una cadena.

Las funciones **Average**, **Max**, **Min** y **Sum** se pueden delegar cuando se usan con un [origen de datos que admite la delegación de dichas funciones](../delegation-list.md).  Sin embargo, **StdevP** y **VarP** no se puede delegar en ningún origen de datos.  Si no se admite la delegación, solo se recuperará la primera parte de los datos y, después, la función se aplicará localmente.  Es posible que el resultado no represente la situación completa.  Aparece una advertencia de delegación durante la creación para recordarle esta limitación y sugerirle que cambie a alternativas que puedan delegarse siempre que sea posible. Para más información, consulte la [introducción a la delegación](../delegation-overview.md).

## <a name="syntax"></a>Sintaxis
**Average**( *NumericalFormula1*; [ *NumericalFormula2*; ... ] )<br>**Max**( *NumericalFormula1*; [ *NumericalFormula2*; ... ] )<br>**Min**( *NumericalFormula1*; [ *NumericalFormula2*; ... ] )<br>**Sum**( *NumericalFormula1*; [ *NumericalFormula2*; ... ] )<br>**StdevP**( *NumericalFormula1*; [ *NumericalFormula2*; ... ] )<br>**VarP**( *NumericalFormula1*; [ *NumericalFormula2*; ... ] )

* *NumericalFormula(s)* : requerido.  Los valores numéricos en que se va a operar.

**Average**( *Table*; *NumericalFormula* )<br>**Max**( *Table*; *NumericalFormula* )<br>**Min**( *Table*; *NumericalFormula* )<br>**Sum**( *Table*; *NumericalFormula* )<br>**StdevP**( *Table*; *NumericalFormula* )<br>**VarP**( *Table*; *NumericalFormula* )

* *Table*: requerido.  La tabla sobre la cual se opera.
* *NumericalFormula*: requerido. La fórmula que se evalúa en cada registro. El resultado de esta fórmula se usa para la agregación. Puede usar columnas de la tabla en la fórmula.

## <a name="examples"></a>Ejemplos
### <a name="step-by-step"></a>Paso a paso
Imaginemos que tiene un [origen de datos](../working-with-data-sources.md) llamado **Sales** que contiene una columna **CostPerUnit** y una columna **UnitsSold**, y establece la propiedad **[Text](../controls/properties-core.md)** de una etiqueta en esta función:<br>
**Sum(Sales; CostPerUnit * UnitsSold)**

Para mostrar las ventas totales, la etiqueta multiplicaría los valores de esas columnas para cada registro y luego agregaría juntos los resultados de todos los registros:<br>![Cálculo de las ventas totales de unidades vendidas y el costo por unidad](./media/function-aggregates/total-sales.png)

Pongamos otro ejemplo: imaginemos que tiene controles deslizantes llamados **Slider1**, **Slider2** y **Slider3** y una etiqueta con la propiedad **[Text](../controls/properties-core.md)** establecida en esta fórmula:<br>
**Sum(Slider1.Value; Slider2.Value; Slider3.Value)**

La etiqueta mostraría la suma de todos los valores en los que se establecieron los controles deslizantes.

