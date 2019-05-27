---
title: Función IfError | Microsoft Docs
description: Información de referencia de la función IfError de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 03/21/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 63a837eff2944569f5f66223690b11ddcfd399f6
ms.sourcegitcommit: aa9f78c304fe46922aecfe3b3fadb6bda72dfb23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66215929"
---
# <a name="iferror-function-in-powerapps"></a>Función IfError en PowerApps

Detecta errores y proporciona un valor alternativo o lleva a cabo una acción.

## <a name="description"></a>Descripción

> [!NOTE]
> Esta función forma parte de una característica experimental y está sujeta a cambios. El comportamiento que se describe en este tema solo está disponible cuando el *administración de errores de nivel de fórmula* característica está activada. Esta configuración de nivel de aplicación está desactivada de forma predeterminada. Para activar esta característica, abra el *archivo* ficha, seleccione *configuración de la aplicación* en el menú izquierdo y, a continuación, seleccione *características experimentales*. Sus comentarios nos sirven mucho: denos su opinión en los [foros de la comunidad de PowerApps](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To).

El **IfError** función prueba uno o más valores hasta que encuentra un resultado de error. Si la función no encuentra un error, la función devuelve un valor correspondiente. En caso contrario, la función devuelve un valor predeterminado. En cualquier caso, la función podría devolver una cadena para mostrar, una fórmula para evaluar u otra forma de resultado. El **IfError** función es similar a la **si** función: **IfError** pruebas para errores, mientras que **si** comprueba **true**.

Use **IfError** para reemplazar los valores de error con los valores válidos. Por ejemplo, puede usar esta función si proporcionados por el usuario pueden dar lugar a una división por cero. Generar una fórmula para reemplazar el resultado con un 0 u otro valor que sea adecuada para su aplicación para que los cálculos descendentes. La fórmula puede ser tan simple como en este ejemplo:

```powerapps-dot
IfError( 1/x, 0 )
```

Si el valor de **x** no es cero, la fórmula devuelve **1 / x**. En caso contrario, **1 / x** produce un error y la fórmula devuelve 0 en su lugar.

Use **IfError** en [fórmulas de comportamiento](../working-with-formulas-in-depth.md) para realizar una acción y compruebe si hay un error antes de realizar acciones adicionales, como se muestra en este patrón:

```powerapps-dot
IfError(
    Patch( DS1, ... ), Notify( "problem in the first action" ),
    Patch( DS2, ... ), Notify( "problem in the second action" )
)
```

Si la primera revisión detecta un problema, la primera **Notify** ejecuciones, ningún procesamiento adicional se produce y no se ejecuta la revisión de segundo. Si la primera revisión se realiza correctamente, se ejecuta la segunda revisión y, si encuentra un problema, el segundo **Notify** se ejecuta.

Si la fórmula no encuentra ningún error y que haya especificado el elemento opcional *DefaultResult* argumento, la fórmula devuelve el valor que especificó para ese argumento. Si la fórmula no encuentra ningún error y no ha especificado dicho argumento, la fórmula devuelve el último *valor* evaluado el argumento.

## <a name="syntax"></a>Sintaxis

**IfError**( *Value1*, *Fallback1* [, *Value2*, *Fallback2*, ... [, *DefaultResult* ] ] )

* *Valores* : requerido. Fórmulas para probar si hay un valor de error.
* *Fallback(s)* : obligatorio. Las fórmulas para evaluar y los valores que se devuelve si la coincidencia *valor* argumentos devuelven un error.
* *DefaultResult*: opcional.  Las fórmulas para evaluar si la fórmula no encuentra ningún error.

## <a name="examples"></a>Ejemplos

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **IfError( 1, 2 )** |El primer argumento no es un error. La función tiene otros errores de comprobación y no tiene valor predeterminado devuelve el valor. La función devuelve el último *valor* evaluado el argumento.   | 1 |
| **IfError( 1/0, 2 )** | El primer argumento devuelve un valor de error (debido a la división por cero). La función evalúa el segundo argumento y lo devuelve como resultado. | 2 |
| **IfError( 1/0, Notify( "Se produjo un problema interno", NotificationType.Error ) )** | El primer argumento devuelve un valor de error (debido a la división por cero). La función evalúa el segundo argumento y muestra un mensaje al usuario. El valor devuelto de **IfError** es el valor devuelto de **Notify**, convertido al mismo tipo que el primer argumento de **IfError** (un número). | 1 |
| **IfError( 1, 2, 3, 4, 5 )** | El primer argumento no es un error, por lo que no se evalúa la función que argumento correspondiente a la reserva. El tercer argumento tampoco es un error, por lo que no se evalúa la función que argumento correspondiente a la reserva. El quinto argumento no tiene ninguna reserva correspondiente y el resultado predeterminado. La función devuelve ese resultado porque la fórmula no contiene ningún error. | 5 |

### <a name="step-by-step"></a>Paso a paso

1. Agregue un control **[Text input](../controls/control-text-input.md)** y asígnele el nombre **TextInput1**, siempre que no sea su nombre predeterminado.

2. Agregue un control **[Label](../controls/control-text-box.md)** y asígnele el nombre **Label1**, siempre que no sea su nombre predeterminado.

3. Establezca la fórmula para la propiedad **Text** de **Label1** en:

    **IfError( Value( TextInput1.Text ), -1 )**

4. En **TextInput1**, escriba **1234**.  

    Label1 mostrará el valor **1234**, ya que se trata de una entrada válida para la función Value.

5. En **TextInput1**, escriba **ToInfinity**.

    Label1 mostrará el valor **-1**, ya que se trata de una entrada no válida para la función Value.  Si no se ajustara la función Value con IfError, la etiqueta no mostraría ningún valor, ya que el valor de error se trata como *blank*. 

