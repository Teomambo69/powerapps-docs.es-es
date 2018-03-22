---
title: 'Control Casilla: referencia | Microsoft Docs'
description: "Información sobre el control Casilla, con propiedades y ejemplos"
services: 
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: 3784e90bbf6ed45d2b67b6211efaab279e37feca
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2018
---
# <a name="check-box-control-in-powerapps"></a>Control Casilla en PowerApps
Un control que el usuario puede seleccionar o borrar para establecer su valor en **true** o **false**.

## <a name="description"></a>Descripción
El usuario puede especificar un valor booleano mediante este conocido control, que lleva décadas usándose en las interfaces gráficas de usuario.

## <a name="key-properties"></a>Propiedades principales
**[Predeterminado](properties-core.md)**: el valor inicial de un control antes de que lo cambie el usuario.

**[Text](properties-core.md)**: texto que aparece en un control o que el usuario escribe en un control.

**[Valor](properties-core.md)**: el valor de un control de entrada.

## <a name="additional-properties"></a>Propiedades adicionales
**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**CheckboxBackgroundFill**: el color de fondo del cuadro que rodea la marca de verificación en un control de casilla.

**CheckboxBorderColor**: el color del borde que rodea la marca de verificación en un control de casilla.

**TamañoDeCasilla**: el ancho y el alto del cuadro que rodea la marca de verificación en un control de casilla.

**CheckmarkFill**: el color de la marca de verificación en un control de casilla.

**[Color](properties-color-border.md)**: el color del texto en un control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[DisabledColor](properties-color-border.md)**: el color del texto en un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[DisabledFill](properties-color-border.md)**: el color de fondo de un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[Font](properties-text.md)**: el nombre de la familia de fuentes en la que aparece el texto.

**[FontWeight](properties-text.md)**: el peso del texto en un control: **Bold**, **Semibold**, **Normal** o **Lighter**.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**[HoverColor](properties-color-border.md)**: el color del texto de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[HoverFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[Italic](properties-text.md)**: indica si el texto de un control está en cursiva.

**AlActivar**: respuesta de una aplicación cuando el valor de una casilla o de un control Alternar cambia a **true**.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**AlDesactivar**: respuesta de una aplicación cuando el valor de una casilla o de un control Alternar cambia a **false**.

**[RellenoInferior](properties-size-location.md)**: distancia entre el texto de un control y el borde inferior de ese control.

**[RellenoIzquierdo](properties-size-location.md)**: distancia entre el texto de un control y el borde izquierdo de ese control.

**[RellenoDerecho](properties-size-location.md)**: distancia entre el texto de un control y el borde derecho de ese control.

**[RellenoSuperior](properties-size-location.md)**: distancia entre el texto de un control y el borde superior de ese control.

**[PressedBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario toca o hace clic en ese control.

**[PressedColor](properties-color-border.md)**: el color de texto de un control cuando el usuario toca o hace clic en ese control.

**[PressedFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario toca o hace clic en ese control.

**[Reset](properties-core.md)**: indica si un control vuelve a su valor predeterminado.

**[Size](properties-text.md)**: el tamaño de la fuente del texto que aparece en un control.

**[Strikethrough](properties-text.md)**: indica si aparece una línea sobre el texto de un control.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Underline](properties-text.md)**: indica si aparece una línea debajo del texto de un control.

**[VerticalAlign](properties-text.md)**: la ubicación del texto en un control respecto al centro vertical de ese control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**If**( *Condition*, *Result* )](../functions/function-if.md)

## <a name="example"></a>Ejemplo
1. Agregue un control **Cuadro de texto**, denomínelo **chkReserve** y establezca su propiedad **[Texto](properties-core.md)** para mostrar **Reserve now**.
   
    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
2. Agregue un control **[Selector de fecha](control-date-picker.md)** y establezca su propiedad **[Visible](properties-core.md)** en esta fórmula:
   <br>**If(chkReserve.Value = true, true)**
   
    ¿Desea más información sobre la función **[If](../functions/function-if.md)** u [otras funciones](../formula-reference.md)?
3. Presione F5, pulse o haga clic en **chkReserve** para establecer su propiedad **[Valor](properties-core.md)** en **true** y luego pulse o haga clic de nuevo en **chkReserve** para establecer su propiedad **[Valor](properties-core.md)** en **false**.
   
    El control **[Selector de fecha](control-date-picker.md)** aparece cuando la propiedad **[Valor](properties-core.md)** de **chkReserve** es **true** pero no cuando es **false**.
4. Presione Esc para volver al área de trabajo predeterminada.

