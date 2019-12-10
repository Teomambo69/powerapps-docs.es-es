---
title: Funciones Back y Navigate | Microsoft Docs
description: Información de referencia de las funciones de navegación y retroceso en Power Apps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/16/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: db8d2bf349fe61cac154c7456a60231215e6566c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730560"
ms.PowerAppsDecimalTransform: true
---
# <a name="back-and-navigate-functions-in-power-apps"></a>Funciones back y Navigate en Power apps

Cambia la pantalla que se muestra.

## <a name="overview"></a>Información general

La mayoría de las aplicaciones contienen varias pantallas.  Use las funciones **Back** y **Navigate** para cambiar la pantalla que se muestra. Por ejemplo, establezca la propiedad **[OnSelect](../controls/properties-core.md)** de un botón en una fórmula que incluya una función **Navigate** si desea mostrar una pantalla diferente cuando un usuario selecciona ese botón. En esta fórmula, puede especificar una transición visual, como **Fade**, para controlar cómo se cambia de una pantalla a otra.  

**Back** y **Navigate** cambian solo la pantalla que se muestra. Las pantallas que no se muestran actualmente siguen funcionando en segundo plano. Puede crear fórmulas que hagan referencia a propiedades de controles en otras pantallas. Por ejemplo, un usuario puede cambiar el valor de un control deslizante en una pantalla, navegar a una pantalla diferente que use ese valor en una fórmula y determinar cómo afecta a lo que ocurre en la nueva pantalla. El usuario puede volver a navegar a la pantalla original y confirmar que el control deslizante ha conservado su valor.

Las [variables de contexto](../working-with-variables.md#use-a-context-variable) también se conservan cuando un usuario navega entre pantallas. Puede usar **Navigate** para establecer una o varias variables de contexto para la pantalla que mostrará la fórmula, que es la única manera de establecer una variable de contexto desde fuera de la pantalla. Este enfoque se puede usar para pasar parámetros a una pantalla. Si ha usado otra herramienta de programación, este enfoque es similar a pasar parámetros a procedimientos.

Puede utilizar cualquiera de las funciones solo dentro de una [fórmula de comportamiento](../working-with-formulas-in-depth.md).

## <a name="navigate"></a>Navigate

En el primer argumento, especifique el nombre de la pantalla para mostrar.  

 En el segundo argumento, especifique cómo se cambia la pantalla anterior a la nueva pantalla:

| Argumento de transición | Descripción | Demostración |
| --- | --- | --- |
| **ScreenTransition.Cover** |La nueva pantalla se desplaza a la vista, de derecha a izquierda, para cubrir la pantalla actual. | ![animación de portada de transición de pantalla](media/function-navigate/cover.gif) |
| **ScreenTransition. CoverRight** |La nueva pantalla se desplaza a la vista, de izquierda a derecha, para cubrir la pantalla actual. | ![animación derecha de la transición de pantalla](media/function-navigate/coverright.gif) |
| **ScreenTransition.Fade** |La pantalla actual desaparece para mostrar la nueva pantalla. | ![animación de fundido de transición de pantalla](media/function-navigate/fade.gif) |
| **ScreenTransition. None** (valor predeterminado) |La nueva pantalla reemplaza rápidamente la pantalla actual. | ![animación de ninguno de transición de pantalla](media/function-navigate/none.gif) |
| **ScreenTransition.UnCover** | La pantalla actual se desplaza fuera de la vista, de derecha a izquierda, para descubrir la nueva pantalla. | ![animación de descubierta de transición de pantalla](media/function-navigate/uncover.gif) |
| **ScreenTransition. UnCoverRight** | La pantalla actual se desplaza fuera de la vista, de izquierda a derecha, para descubrir la nueva pantalla. | ![animación a la derecha de la transición de pantalla](media/function-navigate/uncoverright.gif) |

Puede usar **Navigate** para crear o actualizar las variables de contexto de la nueva pantalla. Como tercer argumento opcional, pase un [registro](../working-with-tables.md#records) que contenga el nombre de la variable de contexto como un nombre de [columna](../working-with-tables.md#columns) y el nuevo valor para la variable de contexto.  Este registro es el mismo que el registro que se usa con la función **[UpdateContext](function-updatecontext.md)** .

Establezca la propiedad **[OnHidden](../controls/control-screen.md)** de la pantalla anterior, la propiedad **[OnVisible](../controls/control-screen.md)** de la nueva pantalla o ambas para realizar cambios adicionales durante la transición. La propiedad **App.ActiveScreen** se actualizará para reflejar el cambio.

**Navigate** normalmente devuelve **true** , pero devolverá **false** si se produce un error.

## <a name="back"></a>Back

La función **atrás** vuelve a la pantalla que se mostró más recientemente.

Para cada llamada a **Navigate** , la aplicación realiza un seguimiento de la pantalla que apareció y la transición. Puede usar llamadas sucesivas hacia **atrás** para volver a la pantalla que aparecía cuando el usuario inició la aplicación.

Cuando se ejecuta la función **back** , se usa de forma predeterminada la transición inversa. Por ejemplo, si aparece una pantalla a través de la transición **CoverRight** , el **retroceso** usa la **descubierta** (que a la izquierda) para volver.  **Desvanecer** y **ninguno** son sus propios inversos. Pase un argumento opcional al de **vuelta** para forzar una transición específica.

**Back** devuelve normalmente **true** , pero devuelve **false** si el usuario no ha navegado a otra pantalla desde el inicio de la aplicación.

## <a name="syntax"></a>Sintaxis

**Atrás**([ *transición* ])

* *Transición* : opcional. Transición visual que se va a usar entre la pantalla actual y la pantalla anterior. Consulte la lista de valores válidos para este argumento anteriormente en este tema. De forma predeterminada, la transición a través de la que se devuelve una pantalla es el inverso de la transición a través de la cual apareció.

**Navegar**( *pantalla* [; *transición* [; *UpdateContextRecord* ]])

* *Screen*: requerido. La pantalla que se va a mostrar.
* *Transición* : opcional.  La transición visual usada entre la pantalla actual y la siguiente pantalla. Consulte la lista de valores válidos para este argumento anteriormente en este tema. El valor predeterminado es **None**.
* *UpdateContextRecord*: valor opcional.  Un registro que contiene el nombre de al menos una columna y un valor para cada columna. Este registro actualiza las variables de contexto de la pantalla nueva como si se pasaran a la función **[UpdateContext](function-updatecontext.md)** .

## <a name="examples"></a>Ejemplos

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Navegar (detalles)** |Muestra la pantalla **Details** sin transición o cambio en el valor de una variable de contexto. |La pantalla **Details** aparece rápidamente. |
| **Navigate( Details; ScreenTransition.Fade )** |Muestra la pantalla **Details** con una transición **Fade**.  No se cambia ningún valor de una variable de contexto. |La pantalla actual desaparece para mostrar la pantalla **Details**. |
| **Navigate( Details; ScreenTransition.Fade; {&nbsp;ID:&nbsp;12&nbsp;} )** |Muestra la pantalla **Details** con una transición **Fade** y actualiza el valor de la variable de contexto **ID** a **12**. |La pantalla actual desaparece para mostrar la pantalla **Details** y la variable de contexto **ID** de esa pantalla se establece en **12**. |
| **Navigate( Details; ScreenTransition.Fade; {&nbsp;ID:&nbsp;12&nbsp;;&nbsp;Shade:&nbsp;Color.Red&nbsp;} )** |Muestra la pantalla **Details** con una transición **Fade**. Actualiza el valor de la variable de contexto **ID** a **12** y actualiza el valor de la variable de contexto **Shade** a **Color.Red**. |La pantalla actual desaparece para mostrar la pantalla **Details**. La variable de contexto **ID** en la pantalla **Details** está establecida en **12** y la variable de contexto **Shade** está establecida en **Color.Red**. Si establece la propiedad **Fill** de un control de la pantalla **Details** en **Shade**, ese control se muestra en rojo. |
| **Back()** | Muestra la pantalla anterior con la transición de devolución predeterminada. | Muestra la pantalla anterior a través de la transición inversa de la transición a través de la que apareció la pantalla actual. |
| **Atrás (ScreenTransition. Cover)** |  Muestra la pantalla anterior con la transición de **portada** . | Muestra la pantalla anterior a través de la transición de la **portada** , independientemente de la transición a través de la que apareció la pantalla actual. |

### <a name="step-by-step"></a>Paso a paso

1. Cree una aplicación vacía.

1. Agregue una segunda pantalla a ella.

    La aplicación contiene dos pantallas en blanco: **Screen1** y **Screen2**.

1. Establezca la propiedad **Fill** de **Screen2** en el valor `Gray`.

1. En **Screen2**, agregue un botón y establezca su propiedad **[alseleccionar](../controls/properties-core.md)** en esta fórmula:

    ```powerapps-comma
    Navigate( Screen1; ScreenTransition.Cover )
    ```

1. Mientras mantiene presionada la tecla **Alt** , seleccione el botón.

    **Screen1** aparece con un fondo blanco a través de una transición que se cubre hacia la izquierda.

1. En **Screen1**, agregue un botón y establezca su propiedad **alseleccionar** en esta fórmula:

    ```powerapps-comma
    Back()
    ```

1. Mientras mantiene presionada la tecla **Alt** , seleccione el botón.

    La segunda pantalla aparece con un fondo gris a través de una transición que se descubre hacia la derecha (la inversa de la **portada**).

1. Seleccione el botón de cada pantalla varias veces para rebotar hacia atrás y hacia delante.

[Otro ejemplo](../add-screen-context-variables.md)
