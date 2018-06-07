---
title: Funciones Abs, Exp, Ln, Power y Sqrt | Microsoft Docs
description: Información de referencia para las funciones Abs, Sqrt y otras en PowerApps, incluidos ejemplos y sintaxis
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 09/13/2016
ms.author: gregli
ms.openlocfilehash: 15d458142bc1077b1bf55ae6e358c826f813ecb2
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "31829519"
---
# <a name="abs-exp-ln-power-and-sqrt-functions-in-powerapps"></a>Funciones Abs, Exp, Ln, Power y Sqrt en PowerApps
Calcula valores absolutos, logaritmos naturales, raíces cuadradas y los resultados de elevar *e* o cualquier número a una potencia especificada.

## <a name="description"></a>Descripción
La función **Abs** muestra el valor no negativo de su argumento. Si el número es negativo, **Abs** muestra el equivalente positivo.

La función **Exp** muestra *e* elevado a la potencia de su argumento.  El número trascendente *e* comienza con 2,7182818...

La función **Ln** muestra el argumento natural (*e* base) de su argumento.

La función **Power** muestra un número elevado a una potencia.  Es equivalente a usar el operador [**^**](operators.md).

La función **Sqrt** muestra el número que, cuando se multiplica por sí mismo, es igual a su argumento.

Si pasa un solo número, el valor que se muestra es un resultado único basado en la función llamada.  Si pasa una [tabla](../working-with-tables.md) de una sola columna que contiene números, el valor que se muestra es una tabla de resultados de una sola columna, un resultado para cada registro en la tabla del argumento. Si tiene una tabla con varias columnas, puede convertirla en una tabla de una sola columna, como se describe en cómo [trabajar con tablas](../working-with-tables.md).  

Si algún argumento pudiera mostrar un valor no definido, el resultado queda en *blanco*.  Por ejemplo, esto puede pasar con las raíces cuadradas y los logaritmos de números negativos.

## <a name="syntax"></a>Sintaxis
**Abs**( *Number* )<br>**Exp**( *Number* )<br>**Ln**( *Number* )<br>**Sqrt**( *Number* )

* *Number*: requerido. El número sobre el cual operar.

**Power**( *Base*, *Exponent* )

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
2. Agregue un control **Etiqueta** y establezca su propiedad **[Text](../controls/properties-core.md)** en esta fórmula:
   <br>
   **Sqrt( Value( Source.Text ) )**
3. Escriba un número en **Origen** y confirme que el control **Etiqueta** muestra la raíz cuadrada del número que escribió.

