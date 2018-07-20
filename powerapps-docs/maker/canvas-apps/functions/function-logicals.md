---
title: Funciones And, Or y Not | Microsoft Docs
description: Información de referencia de las funciones And, Or y Not de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 05e77c97d74312c91f501bfa7a8baa22eff00632
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39021651"
---
# <a name="and-or-and-not-functions-in-powerapps"></a>Funciones And, Or y Not en PowerApps
Funciones de lógica booleana usadas comúnmente para manipular los resultados de pruebas y comparaciones.

## <a name="description"></a>Descripción
La función **And** devuelve **true** si todos los argumentos son **verdaderos**.  El **&&**[operador](operators.md) es equivalente a **And**.

La función **Or** devuelve **true** si todos sus argumentos son **verdaderos**.  El operador **||** es equivalente a **Or**.

La función **Not** devuelve **true** si su argumento es **falso** y devuelve **false** si su argumento es **verdadero**.  El operador **!** es equivalente a **Not**.

Estas funciones trabajan con valores lógicos. No se les puede pasar un número o una cadena directamente, sino que se debe realizar una comparación o prueba. Por ejemplo, una comparación como **x > 1** es una fórmula lógica que se evalúa como el valor booleano **true** si **x** es mayor que **1**. Si **x** es menor que **1**, la fórmula se evalúa como **false.**

## <a name="syntax"></a>Sintaxis
**And**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Or**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Not**( *LogicalFormula* )

* *LogicalFormula(s)*: requerido.  Fórmulas lógicas para evaluar y con las que operar.

## <a name="examples"></a>Ejemplos
### <a name="step-by-step"></a>Paso a paso
Use esta función para determinar si el valor de un control deslizante está fuera del intervalo de 50 a 100:

**Or(Slider1.Value < 50, Slider1.Value> 100)**

Si una [tabla](../working-with-tables.md) contuviera una [columna](../working-with-tables.md#columns) **Dept** y una columna **Salary**, podría usar esta función en una columna **Result** para mostrar **true** en todas las filas donde el valor de la columna **Dept** fuera **HR** o el valor de la columna **Salary** fuera mayor que **200000**:

**Or(Dept = HR, Salary >= 200000)**

Como alternativa, use el operador || para obtener los mismos resultados que los que devuelven las fórmulas anteriores:

**Slider1.Value < 50 || Slider1.Value> 100**

**Dept = "HR" || Salary > 200000**

