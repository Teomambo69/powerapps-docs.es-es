---
title: 'Control Radio: referencia | Microsoft Docs'
description: Información sobre el control Radio, con propiedades y ejemplos
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
ms.openlocfilehash: f28247ab3fce610571e2d5c27106bcf15c00cc8b
ms.sourcegitcommit: 4710a56d308efe67fe60a7688143e61f5e5f2b44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="radio-control-in-powerapps"></a>Control Radio en PowerApps
Lista que muestra todas las opciones, pero el usuario solo puede seleccionarlas de una en una.

## <a name="description"></a>Descripción
Control **Radio**, con el que los usuarios tienen años de experiencia, se utiliza mejor con pocas opciones incompatibles entre sí.

## <a name="key-properties"></a>Propiedades principales
**[Predeterminado](properties-core.md)**: el valor inicial de un control antes de que lo cambie el usuario.

**[Elementos](properties-core.md)**: origen de datos que aparece en un control, como una galería, una lista o un gráfico.

[!INCLUDE [long-items](../../../includes/long-items.md)]

**[Valor](properties-core.md)**: el valor de un control de entrada.

## <a name="all-properties"></a>Todas las propiedades
**[Align](properties-text.md)**: la ubicación del texto respecto al centro horizontal de su control.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[Color](properties-color-border.md)**: el color del texto en un control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[DisabledColor](properties-color-border.md)**: el color del texto en un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[DisabledFill](properties-color-border.md)**: el color de fondo de un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[FocusedBorderColor](properties-color-border.md)**: el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)**: el grosor del borde de un control cuando el control recibe el foco.

**[Font](properties-text.md)**: el nombre de la familia de fuentes en la que aparece el texto.

**[FontWeight](properties-text.md)**: el peso del texto en un control: **Bold**, **Semibold**, **Normal** o **Lighter**.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[HoverColor](properties-color-border.md)**: el color del texto de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[HoverFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[Italic](properties-text.md)**: indica si el texto de un control está en cursiva.

**[AlturaDeLínea](properties-text.md)**: distancia entre, por ejemplo, líneas de texto o elementos de una lista.

**[AlCambiar](properties-core.md)**: indica cómo responde la aplicación cuando el usuario cambia el valor de un control (por ejemplo, mediante el ajuste de un control deslizante).

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**[RellenoInferior](properties-size-location.md)**: distancia entre el texto de un control y el borde inferior de ese control.

**[RellenoIzquierdo](properties-size-location.md)**: distancia entre el texto de un control y el borde izquierdo de ese control.

**[RellenoDerecho](properties-size-location.md)**: distancia entre el texto de un control y el borde derecho de ese control.

**[RellenoSuperior](properties-size-location.md)**: distancia entre el texto de un control y el borde superior de ese control.

**[PressedColor](properties-color-border.md)**: el color de texto de un control cuando el usuario toca o hace clic en ese control.

**[PressedFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario toca o hace clic en ese control.

**RadioBackgroundFill**: color de fondo de los círculos en un control de botón de radio.

**RadioBorderColor**: color de la circunferencia de cada opción de un control de botón de radio.

**RadioSelectionFill**: color que aparece dentro del círculo de la opción seleccionada en un control de botón de radio.

**TamañoDeBotónDeRadio**: diámetro de los círculos de un control de botón de radio.

**[Reset](properties-core.md)**: indica si un control vuelve a su valor predeterminado.

**[Size](properties-text.md)**: el tamaño de la fuente del texto que aparece en un control.

**[Strikethrough](properties-text.md)**: indica si aparece una línea sobre el texto de un control.

**[TabIndex](properties-accessibility.md)**: orden de navegación del teclado en relación con otros controles.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Underline](properties-text.md)**: indica si aparece una línea debajo del texto de un control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**Distinct**( *DataSource*, *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>Ejemplo
1. Agregue un control **Radio**, asígnele el nombre **Pricing** y establezca su propiedad **[Elementos](properties-core.md)** en esta fórmula:
   <br>**["Standard", "Premium"]**
   
    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
2. Agregue un control **[Etiqueta](control-text-box.md)**, desplácelo bajo el control **Radio** y establezca la propiedad **[Texto](properties-core.md)** del control **[Etiqueta](control-text-box.md)** en esta fórmula:
   <br>**If("Premium" in Pricing.Selected.Value, "$200 per day", "$150 per day")**
   
    ¿Desea más información sobre la función **[If](../functions/function-if.md)** u [otras funciones](../formula-reference.md)?
3. Presione F5 y elija cualquiera de las opciones del control **Radio**.
   
    El control **[Etiqueta](control-text-box.md)** muestra el texto adecuado para su elección.
4. (opcional) En el control **Radio**, elija la otra opción para confirmar que aparece el texto adecuado.
5. Presione Esc para volver al área de trabajo predeterminada.


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="color-contrast"></a>Contraste de color
Debe haber un contraste de color adecuado entre:
* **RadioSelectionFill** y **RadioBackgroundFill**
* **RadioBackgroundFill** y **[Fill](properties-color-border.md)**

Y esto, además de los requisitos estándar de contraste de color.

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* Debe haber un **[valor](properties-core.md)** para cada opción de radio.
* Podría también agregar un control **[Etiqueta](control-text-box.md)** inmediatamente delante del control **Radio** para que actúe como encabezado.

### <a name="keyboard-support"></a>Compatibilidad con el teclado
* La propiedad **[TabIndex](properties-accessibility.md)** debe ser cero o superior para que los usuarios del teclado puedan desplazarse hasta él.
* Los indicadores de foco deben ser claramente visibles. Use **[FocusedBorderColor](properties-color-border.md)** y **[FocusedBorderThickness](properties-color-border.md)** para conseguirlo.
 