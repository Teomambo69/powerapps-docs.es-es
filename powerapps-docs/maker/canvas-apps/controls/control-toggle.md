---
title: 'Control Alternar: referencia | Microsoft Docs'
description: Información sobre el control Alternar, con propiedades y ejemplos
services: ''
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: dac1f8ea99746f04d2d3305e279a4bc5faf67903
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="toggle-control-in-powerapps"></a>Control Alternar en PowerApps
Control que el usuario puede activar o desactivar al mover su identificador.

## <a name="description"></a>Descripción
Alternar está diseñado para las interfaces gráficas de usuario recientes pero se comporta igual que una casilla.

## <a name="key-properties"></a>Propiedades principales
**[Predeterminado](properties-core.md)**: el valor inicial de un control antes de que lo cambie el usuario.

**[Valor](properties-core.md)**: el valor de un control de entrada.

## <a name="additional-properties"></a>Propiedades adicionales
**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[FocusedBorderThickness](properties-color-border.md)**: grosor del borde del control cuando se resalta el teclado.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**FalseFill**: el color de relleno de alternancia cuando la alternancia está desactivada.

**FalseHoverFill**: el color de relleno al mantener de alternancia cuando la alternancia está desactivada.

**FalseText**: el texto que se muestra cuando la alternancia está desactivada.

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**[AlCambiar](properties-core.md)**: indica cómo responde la aplicación cuando el usuario cambia el valor de un control (por ejemplo, mediante el ajuste de un control deslizante).

**AlActivar**: respuesta de una aplicación cuando el valor de una casilla o de un control Alternar cambia a **true**.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**AlDesactivar**: respuesta de una aplicación cuando el valor de una casilla o de un control Alternar cambia a **false**.

**[PressedBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario toca o hace clic en ese control.

**RellenoDeRaíl**: color de fondo del rectángulo en un control Alternar cuando su valor es **false** o color de la línea a la derecha del identificador en un control deslizante.

**RellenoRaílAlMantenerPuntero**: al mantener el puntero sobre un control Alternar o deslizante, color de fondo del rectángulo del primero cuando su valor es **false** o color de la línea a la derecha del identificador del segundo.

**[Reset](properties-core.md)**: indica si un control vuelve a su valor predeterminado.

**ShowLabel**: indica si se muestra una etiqueta de texto al lado del control de alternancia.

**[TabIndex](properties-accessibility.md)**: personaliza el orden de tabulación de los controles en tiempo de ejecución cuando se establece en un valor distinto de cero.

**TextPosition**: indica si la etiqueta está a la izquierda o la derecha del control de alternancia.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**TrueFill**: color de relleno de alternancia cuando la alternancia está activada.

**TrueHoverFill**: color de relleno al mantener de alternancia cuando la alternancia está activada.

**TrueText**: el texto que se muestra cuando la alternancia está activada.

**RellenoDeValor**: color de fondo del rectángulo en un control Alternar cuando su valor es **true** o color de la línea a la izquierda del identificador en un control deslizante.

**RellenoValorAlMantenerPuntero**: al mantener el puntero del mouse sobre un control Alternar o Control deslizante, color de fondo del rectángulo del primero cuando su valor es **true** o color de la línea a la izquierda del identificador del segundo.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**If**( *Condition*, *Result* )](../functions/function-if.md)

## <a name="example"></a>Ejemplo
1. Agregue un control Alternar y asígnele el nombre **MemberDiscount**.

    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
2. Agregue una etiqueta y establezca su propiedad **[Text](properties-core.md)** en esta fórmula:
   <br>**If(MemberDiscount.Value = true, "Price: $75", "Price: $100")**

    ¿Desea más información sobre la función **[If](../functions/function-if.md)** u [otras funciones](../formula-reference.md)?
3. Presione F5 y cambie el valor de **MemberDiscount**.

    La etiqueta muestra un precio distinto, en función de si **MemberDiscount** está activado o desactivado.
4. Presione Esc para volver al área de trabajo predeterminada.
