---
title: Funciones If y Switch | Microsoft Docs
description: Información de referencia de las funciones If y Switch de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/24/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 40ac3089d3563d220ddac29197b0902f4de88a25
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61562908"
ms.PowerAppsDecimalTransform: true
---
# <a name="if-and-switch-functions-in-powerapps"></a>Funciones If y Switch de PowerApps
Determina si se cumple alguna condición de un conjunto (**If**) o si el resultado de una fórmula coincide con algún valor de un conjunto (**Switch**) y luego devuelve un resultado o ejecuta una acción.

## <a name="description"></a>Descripción
La función **If** comprueba una o varias condiciones hasta que encuentra un resultado **verdadero**. Si se encuentra un resultado de este tipo, se devuelve un valor correspondiente. Si no se encuentra ningún resultado de este tipo, se devuelve un valor predeterminado. En cualquier caso, el valor devuelto podría ser una cadena para mostrar, una fórmula para evaluar u otra forma de resultado.

La función **Switch** evalúa una fórmula y determina si el resultado coincide con algún valor de una secuencia que especifique. Si se encuentra una coincidencia, se devuelve un valor correspondiente. Si no se encuentra ninguna coincidencia, se devuelve un valor predeterminado. En cualquier caso, el valor devuelto podría ser una cadena para mostrar, una fórmula para evaluar u otra forma de resultado.

Las funciones **If** y **Switch** son muy parecidas, así que debe usar aquella que mejor se adapte a su situación:

* Use **If** para evaluar una única condición. La sintaxis más común para esta función es **If**( *Condition*; *ThenResult*; *DefaultResult* ), que proporciona el patrón común "if …  then ... else ..." que puede verse en otras herramientas de programación.
* Use **If** para evaluar varias condiciones no relacionadas. En PowerApps (a diferencia de Microsoft Excel), puede especificar varias condiciones sin tener que anidar fórmulas **If**.
* Use **Switch** para evaluar una condición única contra varias coincidencias posibles. También podría usar **If** en este caso, pero tendría que repetir la fórmula con cada posible coincidencia.

Puede usar ambas funciones en [fórmulas de comportamiento](../working-with-formulas-in-depth.md) para crear una bifurcación entre dos o más acciones. Solo una bifurcación desencadenará una acción. Las condiciones y coincidencias se evalúan en orden y se detienen si una condición es **verdadera** o se encuentra una coincidencia.

Se devuelve *en blanco* si ninguna condición es **verdadera**, no se encuentra ninguna coincidencia y no especifica un resultado predeterminado.

## <a name="syntax"></a>Sintaxis
**If**( *Condition*; *ThenResult* [; *DefaultResult* ] )<br>**If**( *Condition1*; *ThenResult1* [; *Condition2*; *ThenResult2*; ... [ ; *DefaultResult* ] ] )

* *Condition(s)*: requerido. Fórmulas para comprobar que una condición es **verdadera**. Tales fórmulas contienen normalmente [operadores](operators.md) de comparación (como **<**, **>** y **=**) y permiten probar funciones como **[IsBlank](function-isblank-isempty.md)** e **[IsEmpty](function-isblank-isempty.md)**.
* *ThenResult(s)*: requerido. El valor correspondiente que se devuelve para una condición que se evalúa como **true**.
* *DefaultResult*: opcional. El valor que se devuelve si ninguna condición se evalúa como **verdadera**.  Si no se especifica este argumento, se devolverá un valor *blank*.

**Switch**( *Formula*; *Match1*; *Result1* [; *Match2*; *Result2*; ... [; *DefaultResult* ] ] )

* *Formula*: requerido. Fórmula para evaluar coincidencias.  Esta fórmula se evalúa solo una vez.
* *Match(s)* (Coincidencias): requerido. Valores para comparar con el resultado de *Fórmula*.  Si se encuentra una coincidencia exacta, se devuelve el *Resultado* correspondiente.
* *Result(s)*: requerido. El valor correspondiente que se devolverá cuando se encuentre una coincidencia exacta.
* *DefaultResult*: opcional. Si no se encuentra una coincidencia exacta, se devuelve este valor. Si no se especifica este argumento, se devolverá un valor *blank*.

## <a name="examples"></a>Ejemplos
### <a name="values-in-formulas"></a>Valores en las fórmulas
En los ejemplos siguientes, un control **Control deslizante** (llamado **Slider1**) tiene un valor de **25**.

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **If( Slider1.Value&nbsp;=&nbsp;25; "Result1" )** |La condición es **true** y se devuelve el resultado correspondiente. |"Result1" |
| **If( Slider1.Value&nbsp;=&nbsp;25; "Result1"; "Result2" )** |La condición es **true** y se devuelve el resultado correspondiente. |"Result1" |
| **If( Slider1.Value&nbsp;>&nbsp;1000; "Result1" )** |La condición es **falsa** y no se proporcionó ningún valor para *DefaultResult*. |*blank* |
| **If( Slider1.Value&nbsp;>&nbsp;1000; "Result1"; "Result2" )** |La condición es **falsa**, se proporcionó un valor para *DefaultResult*, que es el que se devuelve. |"Result2" |
| **If( Slider1.Value&nbsp;=&nbsp;25; "Result1"; Slider1.Value&nbsp;>&nbsp;0; "Result2" )** |La primera condición es **true** y se devuelve el resultado correspondiente. La segunda condición es también **verdadera**, pero no se evalúa ya que aparece más adelante en la lista de argumentos que una condición que se evalúa como **verdadera**. |"Result1" |
| **If( IsBlank(&nbsp;Slider1.Value&nbsp;); "Result1"; IsNumeric(&nbsp;Slider1.Value&nbsp;); "Result2" )** |La primera condición es **falsa** porque el control deslizante no es *blank*. La segunda condición es **true** porque el valor del control deslizante es un número y se devolverá el resultado correspondiente. |"Result2" |
| **If( Slider1.Value&nbsp;>&nbsp;1000; "Result1"; Slider1.Value&nbsp;>&nbsp;50; "Result2"; "Result3")** |Las condiciones primera y segunda son **falsas**, se proporcionó un valor para *DefaultResult*, y es el que se devuelve. |"Result3" |
| **Switch( Slider1.Value; 25; "Result1" )** |El valor del control deslizante coincide con el primer valor que se comprueba, y se devuelve el resultado correspondiente. |"Result1" |
| **Switch( Slider1.Value; 20; "Result1"; 25; "Result2"; 30; "Result3" )** |El valor del control deslizante coincide con el segundo valor que se comprueba, y se devuelve el resultado correspondiente. |"Result2" |
| **Switch( Slider1.Value; 20; "Result1"; 10; "Result2"; 0; "Result3"; "DefaultResult" )** |El valor del control deslizante no coincide con ningún valor que se comprueba.  Se proporcionó un valor para *DefaultResult*, que es el que se devuelve. |"DefaultResult" |

### <a name="branching-in-behavior-formulas"></a>Bifurcación en fórmulas de comportamiento
En los ejemplos siguientes, un control **[Entrada de texto](../controls/control-text-input.md)** denominado **FirstName** tiene escrito el valor "John".

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **If( ! IsBlank( FirstName.Text ); Navigate(&nbsp;Screen1; ScreenTransition.None ) )** |La condición es **true**, así que se ejecuta la función **[Navigate](function-navigate.md)**. Puede usar la función **[IsBlank](function-isblank-isempty.md)** para comprobar si se ha rellenado un campo de formulario obligatorio.  Si **FirstName** (Nombre) fuese [blank](function-isblank-isempty.md), esta fórmula no tendría ningún efecto. |**true**<br><br>La pantalla cambia a **Screen1**. |
| **If( IsBlank( FirstName.Text ); Navigate(&nbsp;Screen1; ScreenTransition.None ); Back() )** |Sin el operador **!**, la condición es **false**, así que no se ejecuta la función **[Navigate](function-navigate.md)**. La función **[Back](function-navigate.md)** se proporcionó como *DefaultResult*, así que es la que se ejecuta. |**true**<br><br>Se vuelve a la pantalla que aparecía anteriormente. |
| **Switch( FirstName.Text; "Carlos"; Navigate(&nbsp;Screen1; ScreenTransition.None ); "Kirstin"; Navigate( Screen2; ScreenTransition.None ); "John"; Navigate( Screen3; ScreenTransition.None ) )** |El valor de **FirstName.Text** se compara con "Carlos", "Kirstin" y "John" en ese orden. Se encuentra una coincidencia con "John", por lo que la aplicación se desplaza a **Screen3**. |**true**<br><br>La pantalla cambia a **Screen3**. |

### <a name="step-by-step"></a>Paso a paso
1. Agregue un control **[Entrada de texto](../controls/control-text-input.md)** y asígnele el nombre **Text1**, siempre que no sea su nombre predeterminado.
2. En **Text1**, escriba **30**.
3. Agregue un control **Label** y establezca su propiedad **[Text](../controls/properties-core.md)** en esta fórmula:<br>
   **If( Value(Text1.Text) < 20; "Order MANY more!"; Value(Text1.Text) < 40; "Order more!"; Text1.Text )**
   
    El control **Etiqueta** muestra **Order more!** dado que el valor de **Text1** es superior a 20, pero inferior a 40.
4. En **Text1**, escriba **15**.
   
    El control **Etiqueta** muestra **Order MANY more!** dado que el valor de **Text1** es inferior a 20.
5. En **Text1**, escriba **50**.
   
    El control **Etiqueta** muestra el valor que escribió porque es superior a 40.

