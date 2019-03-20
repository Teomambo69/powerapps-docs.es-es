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
ms.openlocfilehash: 1bf9f3cf075441dd3264b5a2f6533671d2e08654
ms.sourcegitcommit: 4db9c763455d141a7e1dd569a50c86bd9e50ebf0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2019
ms.locfileid: "57802317"
---
# <a name="iferror-function-in-powerapps"></a>Función IfError en PowerApps
Detecta errores y proporciona un valor alternativo o lleva a cabo una acción.

## <a name="description"></a>Descripción
> [!NOTE]
> Esta función forma parte de una característica experimental y está sujeta a cambios.  El comportamiento descrito aquí solo está disponible cuando la característica *Administración de errores a nivel de fórmula* está activada.  Se trata de una configuración de nivel de aplicación que está desactivada de forma predeterminada.  Para activar esta característica, vaya a la pestaña *Archivo*, a *Configuración de la aplicación* en el menú izquierdo y, después, a *Características experimentales*.  Sus comentarios nos sirven mucho: denos su opinión en los [foros de la comunidad de PowerApps](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To).

La función **IfError** comprueba todos sus argumentos en orden para detectar valores de error y se detiene cuando se encuentra el primer valor sin errores.  Los argumentos posteriores al valor sin errores encontrado se ignoran y no se evalúan.

Use **IfError** para reemplazar los valores de error por un valor válido.  Por ejemplo, si es posible que la entrada del usuario pueda tener como resultado una división por cero, reemplácela por un 0 u otro valor válido que sea adecuado para su aplicación de modo que se puedan efectuar cálculos descendentes.

Use **IfError** en las [fórmulas de comportamiento](../working-with-formulas-in-depth.md) para llevar a cabo acciones, comprobar los resultados de los errores y, si es necesario, llevar a cabo otras acciones o mostrar un mensaje de error al usuario con [**Notify**](function-showerror.md).

Si todos los argumentos de **IfError** generan un error, se devuelve el valor del último argumento (que será un valor de error). 

## <a name="syntax"></a>Sintaxis
**IfError**( *Value*, *Fallback1* [, *Fallback2*, ... ] )

* *Value* (se requiere). Fórmulas para probar si hay un valor de error. 
* *Fallback(s)*: obligatorio. Las fórmulas que se deben evaluar y los valores que se deben devolver si los argumentos anteriores devuelven un error.  *Reserva* argumentos se evalúan en orden hasta que se encuentra un valor sin errores.

## <a name="examples"></a>Ejemplos

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **IfError( 1, 2 )** |El primer argumento no es un error.  Se devuelve y no se evalúan los argumentos subsiguientes.   | 1 |
| **IfError( 1/0, 2 )** | El primer argumento devuelve un valor de error (debido a la división por cero).  Se evalúa el segundo argumento, que genera un valor sin errores que se devuelve. | 2 | 
| **IfError( 1/0, Notify( "Se produjo un problema interno", NotificationType.Error ) )** | El primer argumento devuelve un valor de error (debido a la división por cero).  Se evalúa el segundo argumento, que muestra un mensaje al usuario.  El valor devuelto de **IfError** es el valor devuelto de **Notify**, convertido al mismo tipo que el primer argumento de **IfError** (un número). | 1 |
| **IfError( 1/0, 1/0, 2, 1/0, 3 )** | El primer argumento devuelve un valor de error (debido a la división por cero).  Se evalúa el segundo argumento, que también genera un valor de error (otra división por cero).  Se evalúa el tercer argumento, que no genera un valor de error que se devuelve.  Se ignoran los argumentos cuarto y quinto.  | 2 |

### <a name="step-by-step"></a>Paso a paso

1. Agregue un control **[Text input](../controls/control-text-input.md)** y asígnele el nombre **TextInput1**, siempre que no sea su nombre predeterminado.

2. Agregue un control **[Label](../controls/control-text-box.md)** y asígnele el nombre **Label1**, siempre que no sea su nombre predeterminado.

3. Establezca la fórmula para la propiedad **Text** de **Label1** en:

    **IfError( Value( TextInput1.Text ), -1 )**

4. En **TextInput1**, escriba **1234**.  

    Label1 mostrará el valor **1234**, ya que se trata de una entrada válida para la función Value.

5. En **TextInput1**, escriba **ToInfinity**.

    Label1 mostrará el valor **-1**, ya que se trata de una entrada no válida para la función Value.  Si no se ajustara la función Value con IfError, la etiqueta no mostraría ningún valor, ya que el valor de error se trata como *blank*. 

