---
title: Funciones Abs, Exp, Ln, Power y Sqrt | Microsoft Docs
description: Información de referencia para las funciones ABS, sqrt y otras en Power Apps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/13/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 925297a8e1a3f4c454cb8bbb09f75a87419cf5cb
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730482"
---
# <a name="abs-exp-ln-power-and-sqrt-functions-in-power-apps"></a>Funciones ABS, exp, LN, Power y sqrt en Power apps
Calcula valores absolutos, logaritmos naturales, raíces cuadradas y los resultados de elevar *e* o cualquier número a una potencia especificada.

## <a name="description"></a>Descripción
La función **Abs** muestra el valor no negativo de su argumento. Si el número es negativo, **Abs** muestra el equivalente positivo.

La función **Exp** muestra *e* elevado a la potencia de su argumento.  El número trascendente *e* comienza con 2,7182818...

La función **Ln** muestra el argumento natural (*e* base) de su argumento.

La función **Power** muestra un número elevado a una potencia.  Es equivalente a usar el operador [ **^** ](operators.md).

La función **Sqrt** muestra el número que, cuando se multiplica por sí mismo, es igual a su argumento.

Si pasa un solo número, el valor que se muestra es un resultado único basado en la función llamada.  Si pasa una [tabla](../working-with-tables.md) de una sola columna que contiene números, el valor que se muestra es una tabla de resultados de una sola columna, un resultado para cada registro en la tabla del argumento. Si tiene una tabla con varias columnas, puede convertirla en una tabla de una sola columna, como se describe en cómo [trabajar con tablas](../working-with-tables.md).  

Si algún argumento pudiera mostrar un valor no definido, el resultado queda en *blanco*.  Por ejemplo, esto puede pasar con las raíces cuadradas y los logaritmos de números negativos.

## <a name="syntax"></a>Sintaxis
**Abs**( *Number* )<br>**Exp**( *Number* )<br>**Ln**( *Number* )<br>**Sqrt**( *Number* )

* *Number*: requerido. El número sobre el cual operar.

**Power**( *Base*, *Exponente* )

* *Base*: requerido. Número base que se va a elevar.
* *Exponent*: requerido. El exponente al que se eleva el número base.

**Abs**( *SingleColumnTable* )<br>**Exp**( *SingleColumnTable* )<br>**Ln**( *SingleColumnTable* )<br>**Sqrt**( *SingleColumnTable* )

* *SingleColumnTable*: requerido. Una tabla de números de una sola columna sobre la cual operar.

## <a name="examples"></a>Ejemplos
### <a name="single-number"></a>Número único

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Abs( -55 )** |Muestra el número sin el signo negativo. |55 |
| **Exp( 2 )** |Muestra *e* elevado a la potencia de 2, o *e* \* *e*. |7,389056... |
| **Ln( 100 )** |Muestra el algoritmo natural (*e* base) del número 100. |4,605170... |
| **Power( 5, 3 )** |Muestra 5 elevado a la potencia de 3, o 5 \* 5 \* 5. |125 |
| **Sqrt( 9 )** |Muestra el número que, cuando se multiplica por sí mismo, da como resultado 9. |3 |

### <a name="single-column-table"></a>Tabla de una sola columna
Los ejemplos de esta sección usan un [origen de datos](../working-with-data-sources.md) denominado **ValueTable** que contiene estos datos:

![](media/function-numericals/values.png)

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Abs(&nbsp;ValueTable&nbsp;)** |Muestra el valor absoluto de cada número en la tabla. |<style> img { max-width: none } </style> ![](media/function-numericals/values-abs.png) |
| **Exp(&nbsp;ValueTable&nbsp;)** |Muestra *e* elevado a la potencia de cada número en la tabla. |<style> img { max-width: none } </style> ![](media/function-numericals/values-exp.png) |
| **Ln(&nbsp;ValueTable&nbsp;)** |Muestra el logaritmo natural de cada número en la tabla. |<style> img { max-width: none } </style> ![](media/function-numericals/values-ln.png) |
| **Sqrt(&nbsp;ValueTable&nbsp;)** |Muestra la raíz cuadrada de cada número en la tabla. |![](media/function-numericals/values-sqrt.png) |

### <a name="step-by-step-example"></a>Ejemplo paso a paso
1. Agregue un control **[Entrada de texto](../controls/control-text-input.md)** y denomínelo **Origen**.
2. Agregue un control **Label** y establezca su propiedad **[Text](../controls/properties-core.md)** en esta fórmula:
   <br>
   **Sqrt( Value( Source.Text ) )**
3. Escriba un número en **Origen** y confirme que el control **Etiqueta** muestra la raíz cuadrada del número que escribió.

