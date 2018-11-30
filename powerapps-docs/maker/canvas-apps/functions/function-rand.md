---
title: Función Rand | Microsoft Docs
description: Información de referencia para la función Rand en PowerApps, incluida la sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/09/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: abb64d57e53f292dc42cb44ef2b1c9f35bbad944
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42850231"
---
# <a name="rand-function-in-powerapps"></a>Función Rand en PowerApps
Devuelve un número pseudoaleatorio.

## <a name="description"></a>Descripción
La función **Rand** devuelve un número seudoaleatorio que es mayor o igual que 0 y menor que 1.

## <a name="volatile-functions"></a>Funciones volátiles
**Rand** es una función volátil.  Cada vez que se evalúa la función, esta devuelve un valor diferente.  

Cuando se usa en una fórmula de flujo de datos, una función volátil solo devuelve un valor diferente si se vuelve a evaluar la fórmula en la que aparece.  Si no hay ningún otro cambio en la fórmula, presenta el mismo valor durante la ejecución de la aplicación.

Por ejemplo, un control de etiqueta con **Label1.Text = Rand()** no cambiará mientras la aplicación esté activa.  Solo se generará un nuevo valor si se cierra y se vuelve a abrir la aplicación.

Si la función forma parte de una fórmula en la que haya cambiado algún elemento más, se volverá a evaluar.  Por ejemplo, si modificamos el ejemplo para incluir un control deslizante con **Label1.Text = Slider1.Value + Rand()**, se generará un nuevo número aleatorio cada vez que cambie el valor del control deslizante. Asimismo, se volverá a evaluar la propiedad de texto de la etiqueta.  Encontrará el ejemplo a continuación.

Cuando se usa en una [fórmula de comportamiento](../working-with-formulas-in-depth.md), **Rand** se evalúa cada vez que se evalúa la fórmula de comportamiento.  Encontrará un ejemplo a continuación.

## <a name="syntax"></a>Sintaxis
**Rand**()

## <a name="examples"></a>Ejemplos

#### <a name="display-a-different-random-number-as-user-input-changes"></a>Mostrar un número aleatorio diferente a medida que cambia la entrada del usuario
1. Agregue un control **[Control deslizante](../controls/control-slider.md)** y, si tiene otro nombre, cámbielo a **Slider1**.

1. Agregue un control **[Label](../controls/control-text-box.md)** y establezca su propiedad **Text** en esta fórmula:

    **Slider1.Value + Rand()**

    La etiqueta muestra **50**, que es el valor predeterminado del control deslizante, más un decimal aleatorio:

    ![Pantalla en la que se muestra un control de etiqueta con 50,741.](media/function-rand/rand-slider-1.png)

1. Cambie el valor del control deslizante manteniendo la tecla Alt presionada.

    Cada vez que cambie el valor del control deslizante, la parte decimal de la etiqueta mostrará un número aleatorio diferente:

    ![Cuatro pantallas en las que se muestra un control de etiqueta con cuatro valores decimales aleatorios para cada una de las cuatro opciones de configuración de control deslizante diferentes: 70,899, 84,667, 90,134 y 99,690.](media/function-rand/rand-slider-results.png)

#### <a name="create-a-table-of-random-numbers"></a>Creación de una tabla de números aleatorios
1. Agregue un control **[Botón](../controls/control-button.md)** y establezca su propiedad **[OnSelect](../controls/properties-core.md)** en esta fórmula:

    **ClearCollect( RandomNumbers, ForAll( [ 1, 2, 3, 4, 5 ], Rand() ))**

    Con esta fórmula, se crea una tabla de una sola columna que se usa para iterar cinco veces, lo que produce cinco números aleatorios.

1. Agregue una **[tabla de datos](../controls/control-data-table.md)**, establezca su propiedad **Items** en **RandomNumbers** y muestre el campo **Value**.

    ![Pantalla en la que se muestra una tabla de datos con cinco valores decimales diferentes: 0,857, 0,105, 0,979, 0,167 y 0,814.](media/function-rand/set-show-data.png)

1. Haga clic en el botón o púlselo para seleccionarlo, manteniendo la tecla Alt presionada.

    En la tabla de datos se muestran cinco números decimales aleatorios:

    ![Pantalla en la que se muestra una tabla de datos con cinco valores decimales diferentes: 0,857, 0,105, 0,979, 0,167 y 0,814.](media/function-rand/rand-collection-1.png)

1. Vuelva a seleccionar el botón para mostrar una lista de números aleatorios diferentes:

    ![Misma pantalla en la que se muestra una tabla de datos con un nuevo conjunto de cinco valores decimales diferentes: 0,414, 0,128, 0,860, 0,303 y 0,568.](media/function-rand/rand-collection-2.png)

Para generar un número aleatorio único en lugar de una tabla, use **Set( RandomNumber, Rand() )**.
