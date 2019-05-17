---
title: Funciones Back y Navigate | Microsoft Docs
description: Información de referencia de las funciones Back y Navigate de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/16/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e57cc541c753ff3f24f66a78c6e30d6e5683b41a
ms.sourcegitcommit: 57dfad065318263e162e949e26b5c2684ba0dccb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65828173"
---
# <a name="back-and-navigate-functions-in-powerapps"></a>Funciones Back y Navigate en PowerApps

Cambia la pantalla que se muestra.

## <a name="overview"></a>Información general

La mayoría de las aplicaciones contienen varias pantallas.  Use las funciones **Back** y **Navigate** para cambiar la pantalla que se muestra. Por ejemplo, establezca la propiedad **[OnSelect](../controls/properties-core.md)** de un botón en una fórmula que incluya una función **Navigate** si desea mostrar una pantalla diferente cuando un usuario selecciona ese botón. En esta fórmula, puede especificar una transición visual, como **Fade**, para controlar cómo se cambia de una pantalla a otra.  

**Back** y **Navigate** cambian solo la pantalla que se muestra. Las pantallas que no se muestran actualmente siguen funcionando en segundo plano. Puede crear fórmulas que hagan referencia a las propiedades de los controles en otras pantallas. Por ejemplo, un usuario puede cambiar el valor de un control deslizante en una pantalla, vaya a una pantalla diferente que use ese valor en una fórmula y determinar cómo afecta a lo que ocurre en la nueva pantalla. El usuario puede desplazarse a la pantalla original y confirme que el control deslizante ha conservado su valor.

Las [variables de contexto](../working-with-variables.md#use-a-context-variable) también se conservan cuando un usuario navega entre pantallas. Puede usar **Navigate** para establecer una o varias variables de contexto para la pantalla que mostrará la fórmula, que es la única manera de establecer una variable de contexto desde fuera de la pantalla. Este enfoque se puede usar para pasar parámetros a una pantalla. Si ha usado otra herramienta de programación, este enfoque es similar a pasar parámetros a procedimientos.

Puede utilizar cualquier función dentro un [fórmula de comportamiento](../working-with-formulas-in-depth.md).

## <a name="navigate"></a>Navigate

En el primer argumento, especifique el nombre de la pantalla para mostrar.  

 En el segundo argumento, especifique cómo se cambia la pantalla anterior a la nueva pantalla:

| Argumento de transición | Descripción | Ver demostración |
| --- | --- | --- |
| **ScreenTransition.Cover** |La nueva pantalla se desliza dentro de una vista, se desplaza de derecha a izquierda, para cubrir la pantalla actual. | ![animación de portada de transiciones de pantalla](media/function-navigate/cover.gif) |
| **ScreenTransition.CoverRight** |Las diapositivas de pantalla nueva vista, se mueve de izquierda a derecha, para cubrir la pantalla actual. | ![animación derecho de portada de transición de pantalla](media/function-navigate/coverright.gif) |
| **ScreenTransition.Fade** |Transiciones de pantalla actual para mostrar la nueva pantalla. | ![animación de atenuación de transición de pantalla](media/function-navigate/fade.gif) |
| **ScreenTransition.None** (predeterminado) |La nueva pantalla reemplaza rápidamente la pantalla actual. | ![pantalla de transición ninguna animación](media/function-navigate/none.gif) |
| **ScreenTransition.UnCover** | La pantalla actual se desliza fuera de la vista, se desplaza de derecha a izquierda, para descubrir la nueva pantalla. | ![transición de la pantalla revelar animación](media/function-navigate/uncover.gif) |
| **ScreenTransition.UnCoverRight** | Las diapositivas de pantalla actual fuera de la vista, se mueve de izquierda a derecha, para descubrir la nueva pantalla. | ![transición de la pantalla revelar animación derecho](media/function-navigate/uncoverright.gif) |

Puede usar **Navigate** para crear o actualizar las variables de contexto de la nueva pantalla. Como tercer argumento opcional, pase un [registro](../working-with-tables.md#records) que contenga el nombre de la variable de contexto como un nombre de [columna](../working-with-tables.md#columns) y el nuevo valor para la variable de contexto.  Este registro es el mismo que el registro que se usa con la función **[UpdateContext](function-updatecontext.md)**.

Establezca la propiedad **[OnHidden](../controls/control-screen.md)** de la pantalla anterior, la propiedad **[OnVisible](../controls/control-screen.md)** de la nueva pantalla o ambas para realizar cambios adicionales durante la transición. La propiedad **App.ActiveScreen** se actualizará para reflejar el cambio.

**Navegue** normalmente devuelve **true** pero devolverá **false** si se produce un error.

## <a name="back"></a>Back

El **volver** función vuelve a la pantalla que se visualizó más recientemente.

Para cada **Navigate** llamada, la aplicación realiza el seguimiento de la pantalla que aparece y la transición. Puede usar sucesivas **volver** llamadas para devolver hasta la pantalla que aparece cuando el usuario inició la aplicación.

Cuando el **volver** función que se ejecuta, la transición inversa se usa de forma predeterminada. Por ejemplo, si aparece una pantalla a través de la **CoverRight** transición, **Atrás** usa **descubrir** (que es a la izquierda) para devolver.  **Atenuar** y **ninguno** son sus propios inversos. Pasar un argumento opcional para **volver** para forzar una transición concreta.

**Atrás** normalmente devuelve **true** pero devuelve **false** si el usuario no ha navegado a otra pantalla después de iniciar la aplicación.

## <a name="syntax"></a>Sintaxis

**Atrás**([ *transición* ])

* *Transición* : opcional. La transición visual usada entre la pantalla actual y la pantalla anterior. Consulte la lista de valores válidos para este argumento anteriormente en este tema. De forma predeterminada, la transición a través del cual se devuelve una pantalla es el inverso de la transición a través del cual se puso de manifiesto.

**Navigate**( *Screen* [, *Transition* [, *UpdateContextRecord* ] ] )

* *Screen*: requerido. La pantalla que se va a mostrar.
* *Transición* : opcional.  La transición visual usada entre la pantalla actual y la siguiente pantalla. Consulte la lista de valores válidos para este argumento anteriormente en este tema. El valor predeterminado es **ninguno**.
* *UpdateContextRecord*: valor opcional.  Un registro que contiene el nombre de al menos una columna y un valor para cada columna. Este registro actualiza las variables de contexto de la pantalla nueva como si se pasaran a la función **[UpdateContext](function-updatecontext.md)**.

## <a name="examples"></a>Ejemplos

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Navegar (detalles)** |Muestra la pantalla **Details** sin transición o cambio en el valor de una variable de contexto. |La pantalla **Details** aparece rápidamente. |
| **Navigate( Details, ScreenTransition.Fade )** |Muestra la pantalla **Details** con una transición **Fade**.  No se cambia ningún valor de una variable de contexto. |La pantalla actual desaparece para mostrar la pantalla **Details**. |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;} )** |Muestra la pantalla **Details** con una transición **Fade** y actualiza el valor de la variable de contexto **ID** a **12**. |La pantalla actual desaparece para mostrar la pantalla **Details** y la variable de contexto **ID** de esa pantalla se establece en **12**. |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;,&nbsp;Shade:&nbsp;Color.Red&nbsp;} )** |Muestra la pantalla **Details** con una transición **Fade**. Actualiza el valor de la variable de contexto **ID** a **12** y actualiza el valor de la variable de contexto **Shade** a **Color.Red**. |La pantalla actual desaparece para mostrar la pantalla **Details**. La variable de contexto **ID** en la pantalla **Details** está establecida en **12** y la variable de contexto **Shade** está establecida en **Color.Red**. Si establece la propiedad **Fill** de un control de la pantalla **Details** en **Shade**, ese control se muestra en rojo. |
| **Back()** | Muestra la pantalla anterior con la transición de valor devuelto predeterminado. | Muestra la pantalla anterior a través de la transición inversa de la transición a través del cual aparece la pantalla actual. |
| **Back (ScreenTransition.Cover)** |  Muestra la pantalla anterior con el **cubrir** transición. | Muestra la pantalla anterior a través de la **cubrir** transición, independientemente de la transición a través del cual aparece la pantalla actual. |

### <a name="step-by-step"></a>Paso a paso

1. Creación de una aplicación en blanco.

1. Agregar una segunda pantalla.

    La aplicación contiene dos pantallas en blanco: **Screen1** y **Screen2**.

1. Establecer el **rellenar** propiedad de **Screen2** al valor `Gray`.

1. En **Screen2**, agregue un botón y establezca su **[Alseleccionar](../controls/properties-core.md)** propiedad en esta fórmula:

    ```powerapps-dot
    Navigate( Screen1, ScreenTransition.Cover )
    ```

1. Mientras mantiene presionada la **Alt** clave, seleccione el botón.

    **Screen1** aparece con un fondo blanco a través de una transición que cubre a la izquierda.

1. En **Screen1**, agregue un botón y establezca su **OnSelect** propiedad en esta fórmula:

    ```powerapps-dot
    Back()
    ```

1. Mientras mantiene presionada la **Alt** clave, seleccione el botón.

    La segunda pantalla aparece con un fondo gris a través de una transición que revela a la derecha (el inverso de **cubrir**).

1. Seleccione el botón en cada pantalla repetidamente para desplazarse.

[Otro ejemplo](../add-screen-context-variables.md)
