---
title: 'Control Alternar: referencia | Microsoft Docs'
description: Información sobre el control Alternar, con propiedades y ejemplos
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: a2361e2572d62ca4a2574cd668ba0f1834d04ab9
ms.sourcegitcommit: 0f6d7bb9e524202c065b9a7ef92a7f54bdc4bc7c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39022473"
---
# <a name="toggle-control-in-powerapps"></a>Control Alternar en PowerApps
Control que el usuario puede activar o desactivar al mover su identificador.

## <a name="description"></a>Descripción
Alternar está diseñado para las interfaces gráficas de usuario recientes pero se comporta igual que una casilla.

## <a name="key-properties"></a>Propiedades principales
**[Predeterminado](properties-core.md)**: el valor inicial de un control antes de que lo cambie el usuario.

**[Valor](properties-core.md)**: el valor de un control de entrada.

## <a name="additional-properties"></a>Propiedades adicionales
**[AccessibleLabel](properties-accessibility.md)**: etiqueta para lectores de pantalla.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**FalseFill**: el color de relleno de alternancia cuando la alternancia está desactivada.

**FalseHoverFill**: el color de relleno al mantener de alternancia cuando la alternancia está desactivada.

**FalseText**: el texto que se muestra cuando la alternancia está desactivada.

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[FocusedBorderColor](properties-color-border.md)**: el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)**: el grosor del borde de un control cuando el control recibe el foco.

**HandleFill**: el color de relleno del controlador de alternancia.

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

**[TabIndex](properties-accessibility.md)**: orden de navegación del teclado en relación con otros controles.

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


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="color-contrast"></a>Contraste de color
Debe haber un contraste de color adecuado entre:
* **HandleFill** y **FalseFill**
* **HandleFill** y **FalseHoverFill**
* **HandleFill** y **TrueFill**
* **HandleFill** y **TrueHoverFill**
* **FalseFill** y el color de fuera de control
* **FalseHoverFill** y el color de fuera de control
* **TrueFill** y el color de fuera de control
* **TrueHoverFill** y el color de fuera de control

Y esto, además de los [requisitos estándar de contraste de color](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* La propiedad **[AccessibleLabel](properties-accessibility.md)** debe estar presente.
* La propiedad **FalseText** debe existir.
* La propiedad **TrueText** debe existir.

### <a name="low-vision-support"></a>Apoyo para deficiencia visual
* Considere la posibilidad de configurar **ShowLabel** como **true** para que los usuarios puedan determinar rápidamente el valor de alternancia.

### <a name="keyboard-support"></a>Compatibilidad con el teclado
* La propiedad **[TabIndex](properties-accessibility.md)** debe ser cero o superior para que los usuarios del teclado puedan desplazarse hasta él.
* Los indicadores de foco deben ser claramente visibles. Use **[FocusedBorderColor](properties-color-border.md)** y **[FocusedBorderThickness](properties-color-border.md)** para conseguirlo.
