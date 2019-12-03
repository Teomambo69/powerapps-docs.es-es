---
title: Función IfError | Microsoft Docs
description: Información de referencia de la función IfError de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/21/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8d9916c3fa62aab947315b7c31daa96f7e528acd
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74680291"
---
# <a name="iferror-function-in-powerapps"></a>Función IfError en PowerApps

Detecta errores y proporciona un valor alternativo o lleva a cabo una acción.

## <a name="description"></a>Descripción

> [!NOTE]
> Esta función forma parte de una característica experimental y está sujeta a cambios. El comportamiento que se describe en este tema solo está disponible cuando está activada la característica de *Administración de errores de nivel de fórmula* . Esta configuración de nivel de aplicación está desactivada de forma predeterminada. Para activar esta característica, abra la pestaña *archivo* , seleccione Configuración de la *aplicación* en el menú de la izquierda y, a continuación, seleccione *características experimentales*. Sus comentarios son muy valiosos: díganos lo que piensa en los foros de la [comunidad de Power apps](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To).

La **función** de error de prueba comprueba uno o más valores hasta que encuentra un resultado de error. Si la función encuentra un error, la función devuelve un valor correspondiente. De lo contrario, la función devuelve un valor predeterminado. En cualquier caso, la función podría devolver una cadena para mostrar, una fórmula para evaluar u otra forma de resultado. La **función de error** de es similar a la función If **: se** comprueba **si** hay errores, mientras que **si** comprueba **true**.

Use si es un valor erróneo para reemplazar los **valores de error** por valores válidos. Por ejemplo, use esta función si los datos proporcionados por el usuario pueden dar lugar a una división por cero. Cree una fórmula para reemplazar el resultado por un valor 0 u otro que sea adecuado para la aplicación, de modo que los cálculos descendentes puedan continuar. La fórmula puede ser tan sencilla como en este ejemplo:

```powerapps-dot
IfError( 1/x, 0 )
```

Si el valor de **x** no es cero, la fórmula devuelve **1/x**. De lo contrario, **1/x** genera un error y la fórmula devuelve 0 en su lugar.

Use un error en las [fórmulas de comportamiento](../working-with-formulas-in-depth.md) para realizar una acción y comprobar si hay un error **antes de realizar** acciones adicionales, como en este patrón:

```powerapps-dot
IfError(
    Patch( DS1, ... ), Notify( "problem in the first action" ),
    Patch( DS2, ... ), Notify( "problem in the second action" )
)
```

Si la primera revisión detecta un problema, la primera **notificación** se ejecuta, no se realiza ningún otro procesamiento y la segunda revisión no se ejecuta. Si la primera revisión se realiza correctamente, se ejecuta la segunda revisión y, si encuentra un problema, se ejecuta la segunda **notificación** .

Si la fórmula no encuentra errores y ha especificado el argumento opcional *DefaultResult* , la fórmula devuelve el valor que especificó para ese argumento. Si la fórmula no encuentra ningún error y no se ha especificado ese argumento, la fórmula devuelve el último argumento de *valor* evaluado.

## <a name="syntax"></a>Sintaxis

' No se **pudo (** *Value1*, *Fallback1* [, *value2*, *Fallback2*,... [, *DefaultResult* ]] )

* *Value (s)* : requerido. Fórmulas para probar si hay un valor de error.
* *Fallback(s)* : obligatorio. Las fórmulas que se van a evaluar y los valores que se van a devolver si los argumentos de *valor* coincidente devolvieron un error.
* *DefaultResult*: opcional.  Fórmulas que se van a evaluar si la fórmula no encuentra errores.

## <a name="examples"></a>Ejemplos

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **IfError( 1, 2 )** |El primer argumento no es un error. La función no tiene ningún otro error para comprobar y ningún valor devuelto predeterminado. La función devuelve el último argumento de *valor* evaluado.   | 1 |
| **IfError( 1/0, 2 )** | El primer argumento devuelve un valor de error (debido a la división por cero). La función evalúa el segundo argumento y lo devuelve como resultado. | 2 |
| **IfError( 1/0, Notify( "Se produjo un problema interno", NotificationType.Error ) )** | El primer argumento devuelve un valor de error (debido a la división por cero). La función evalúa el segundo argumento y muestra un mensaje al usuario. El valor devuelto de **IfError** es el valor devuelto de **Notify**, convertido al mismo tipo que el primer argumento de **IfError** (un número). | 1 |
| **"No se pudo (1, 2, 3, 4, 5")** | El primer argumento no es un error, por lo que la función no evalúa la reserva correspondiente del argumento. El tercer argumento no es un error, por lo que la función no evalúa la reserva correspondiente del argumento. El quinto argumento no tiene ninguna reserva correspondiente y es el resultado predeterminado. La función devuelve el resultado porque la fórmula no contiene errores. | 5 |

### <a name="step-by-step"></a>Paso a paso

1. Agregue un control **[Text input](../controls/control-text-input.md)** y asígnele el nombre **TextInput1**, siempre que no sea su nombre predeterminado.

2. Agregue un control **[Label](../controls/control-text-box.md)** y asígnele el nombre **Label1**, siempre que no sea su nombre predeterminado.

3. Establezca la fórmula para la propiedad **Text** de **Label1** en:

    **IfError( Value( TextInput1.Text ), -1 )**

4. En **TextInput1**, escriba **1234**.  

    Label1 mostrará el valor **1234**, ya que se trata de una entrada válida para la función Value.

5. En **TextInput1**, escriba **ToInfinity**.

    Label1 mostrará el valor **-1**, ya que se trata de una entrada no válida para la función Value.  Si no se ajustara la función Value con IfError, la etiqueta no mostraría ningún valor, ya que el valor de error se trata como *blank*. 

