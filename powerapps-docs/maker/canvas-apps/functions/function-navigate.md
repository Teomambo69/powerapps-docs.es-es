---
title: "Funciones Atrás y Navegar | Microsoft Docs"
description: "Información de referencia de las funciones Back y Navigate de PowerApps, con sintaxis y ejemplos"
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/08/2015
ms.author: gregli
ms.openlocfilehash: 58f8c4bf55167e7c891a614a2bfb98ef20dcfd7c
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="back-and-navigate-functions-in-powerapps"></a>Funciones Back y Navigate en PowerApps
Cambia la pantalla que se muestra.

## <a name="overview"></a>Información general
La mayoría de las aplicaciones contienen varias pantallas.  Use las funciones **Back** y **Navigate** para cambiar la pantalla que se muestra. Por ejemplo, establezca la propiedad **[AlSeleccionar](../controls/properties-core.md)** de un botón en una fórmula que incluya una función **Navigate** si desea mostrar una pantalla diferente cuando un usuario selecciona ese botón. En esta fórmula, puede especificar una transición visual, como **Fade**, para controlar cómo se cambia de una pantalla a otra.  

**Back** y **Navigate** cambian solo la pantalla que se muestra. Las pantallas que no se muestran actualmente siguen funcionando en segundo plano. Puede crear fórmulas que hagan referencia a propiedades de controles de otra pantalla. Por ejemplo, un usuario puede cambiar el valor de un control deslizante en una pantalla, navegar a una pantalla diferente que use ese valor en una fórmula y ver cómo afecta a lo que ocurre en la nueva pantalla.  Luego, el usuario puede navegar a la pantalla original y ver que el control deslizante ha conservado su valor.

Las [variables de contexto](../working-with-variables.md#create-a-context-variable) también se conservan cuando un usuario navega entre pantallas. Puede usar **Navigate** para establecer una o varias variables de contexto para la pantalla que mostrará la fórmula, que es la única manera de establecer una variable de contexto desde fuera de la pantalla. Este enfoque se puede usar para pasar parámetros a una pantalla. Si ha usado otra herramienta de programación, este enfoque es similar a pasar parámetros a procedimientos.

## <a name="description"></a>Descripción
### <a name="back"></a>Back
La función **Back** muestra la pantalla que se visualizó más recientemente. No especifique ningún argumento para esta función.

### <a name="navigate"></a>Navigate
En el primer argumento, especifique el nombre de la pantalla para mostrar.  

 En el segundo argumento, especifique cómo se cambia la pantalla anterior a la nueva pantalla:

| Argumento de transición | Descripción |
| --- | --- |
| **ScreenTransition.Cover** |La nueva pantalla se desliza dentro de una vista que cubre la pantalla actual. |
| **ScreenTransition.Fade** |La antigua pantalla desaparece para revelar la nueva pantalla. |
| **ScreenTransition.None** |La pantalla anterior se reemplaza rápidamente por la nueva pantalla. |
| **ScreenTransition.UnCover** |La pantalla anterior se desliza fuera de la vista para descubrir la nueva pantalla. |

Puede usar **Navigate** para crear o actualizar las variables de contexto de la nueva pantalla. Como tercer argumento opcional, pase un [registro](../working-with-tables.md#records) que contenga el nombre de la variable de contexto como un nombre de [columna](../working-with-tables.md#columns) y el nuevo valor para la variable de contexto.  Este registro es el mismo que el registro que se usa con la función **[UpdateContext](function-updatecontext.md)**.

Establezca la propiedad **[AlEstarOculto](../controls/control-screen.md)** de la pantalla anterior, la propiedad **[AlEstarVisible](../controls/control-screen.md)** de la nueva pantalla o ambas para realizar cambios adicionales durante la transición. La propiedad **App.ActiveScreen** se actualizará para reflejar el cambio.

**Back** devuelve normalmente **true** pero si el usuario está en la primera pantalla mostrada y no hay una pantalla anterior, devuelve **false**.  **Navigate** devuelve normalmente **true** pero si hay un problema con uno de sus argumentos, devuelve **false**.

Solo puede utilizar estas funciones dentro de una [fórmula de comportamiento](../working-with-formulas-in-depth.md).

## <a name="syntax"></a>Sintaxis
**Back**()

**Navigate**( *Screen*, *Transition* [, *UpdateContextRecord* ] )

* *Screen*: requerido. La pantalla que se va a mostrar.
* *Transición*: requerido.  La transición visual usada entre la pantalla actual y la siguiente pantalla. Consulte la lista de valores válidos para este argumento anteriormente en este tema.
* *UpdateContextRecord*: valor opcional.  Un registro que contiene el nombre de al menos una columna y un valor para cada columna. Este registro actualiza las variables de contexto de la pantalla nueva como si se pasaran a la función **[UpdateContext](function-updatecontext.md)**.

## <a name="examples"></a>Ejemplos
| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Navigate( Details, ScreenTransition.None )** |Muestra la pantalla **Details** sin transición o cambio en el valor de una variable de contexto. |La pantalla **Details** aparece rápidamente. |
| **Navigate( Details, ScreenTransition.Fade )** |Muestra la pantalla **Details** con una transición **Fade**.  No se cambia ningún valor de una variable de contexto. |La pantalla actual desaparece para mostrar la pantalla **Details**. |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;} )** |Muestra la pantalla **Details** con una transición **Fade** y actualiza el valor de la variable de contexto **ID** a **12**. |La pantalla actual desaparece para mostrar la pantalla **Details** y la variable de contexto **ID** de esa pantalla se establece en **12**. |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;,&nbsp;Shade:&nbsp;Color.Red&nbsp;} )** |Muestra la pantalla **Details** con una transición **Fade**. Actualiza el valor de la variable de contexto **ID** a **12** y actualiza el valor de la variable de contexto **Shade** a **Color.Red**. |La pantalla actual desaparece para mostrar la pantalla **Details**. La variable de contexto **ID** en la pantalla **Details** está establecida en **12** y la variable de contexto **Shade** está establecida en **Color.Red**. Si establece la propiedad **Fill** de un control de la pantalla **Details** en **Shade**, ese control se muestra en rojo. |

### <a name="step-by-step"></a>Paso a paso
1. Asigne un nombre a la pantalla predeterminada **DefaultScreen**, agréguele una etiqueta y establezca la propiedad **[Texto](../controls/properties-core.md)**  de esa etiqueta para que muestre **Default**.
2. Agregue una pantalla y asígnele el nombre **AddlScreen**.
3. Agregue una etiqueta a **AddlScreen** y establezca la propiedad **[Texto](../controls/properties-core.md)** de la etiqueta para que muestre **Addl**.
4. Agregue un botón a **AddlScreen** y establezca su propiedad **[AlSeleccionar](../controls/properties-core.md)** en esta función:<br>**Navigate(DefaultScreen, ScreenTransition.Fade)**
5. En **AddlScreen**, presione F5 y luego seleccione el botón.<br>Aparece **DefaultScreen**.

[Otro ejemplo](../add-screen-context-variables.md)

