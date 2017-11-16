---
title: 'Control Lista desplegable: referencia | Microsoft Docs'
description: "Información sobre el control Lista desplegable, con propiedades y ejemplos"
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
ms.openlocfilehash: 30b36217b0871b85b3868cd305992d7e4f364557
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="drop-down-control-in-powerapps"></a>Control Lista desplegable en PowerApps
Una lista que muestra solo el primer elemento a menos que el usuario la abra.

## <a name="description"></a>Descripción
Un control **Lista desplegable** conserva el estado real de la pantalla, en especial cuando la lista contiene un gran número de opciones. El control toma una sola línea a menos que el usuario seleccione las comillas angulares para revelar más opciones.

## <a name="key-properties"></a>Propiedades principales
**[Predeterminado](properties-core.md)**: el valor inicial de un control antes de que lo cambie el usuario.

**[Elementos](properties-core.md)**: origen de datos que aparece en un control, como una galería, una lista o un gráfico.

[!INCLUDE [long-items](../../includes/long-items.md)]

**Seleccionados**: el elemento seleccionado.

## <a name="additional-properties"></a>Propiedades adicionales
**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[FocusedBorderThickness](properties-color-border.md)**: grosor del borde del control cuando se resalta el teclado.

**ChevronBackground**: el color detrás de la flecha hacia abajo en una lista desplegable.

**ChevronFill**: el color de la flecha hacia abajo en una lista desplegable.

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

**[AlCambiar](properties-core.md)**: indica cómo responde la aplicación cuando el usuario cambia el valor de un control (por ejemplo, mediante el ajuste de un control deslizante).

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**[RellenoInferior](properties-size-location.md)**: distancia entre el texto de un control y el borde inferior de ese control.

**[RellenoIzquierdo](properties-size-location.md)**: distancia entre el texto de un control y el borde izquierdo de ese control.

**[RellenoDerecho](properties-size-location.md)**: distancia entre el texto de un control y el borde derecho de ese control.

**[RellenoSuperior](properties-size-location.md)**: distancia entre el texto de un control y el borde superior de ese control.

**[PressedBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario toca o hace clic en ese control.

**[PressedColor](properties-color-border.md)**: el color de texto de un control cuando el usuario toca o hace clic en ese control.

**[PressedFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario toca o hace clic en ese control.

**[Reset](properties-core.md)**: indica si un control vuelve a su valor predeterminado.

**[ColorDeSelección](properties-color-border.md)**: color del texto de los elementos seleccionados en una lista o de la herramienta de selección de un control de entrada manuscrita.

**[RellenoDeSelección](properties-color-border.md)**: el color de fondo de uno o varios elementos seleccionados en una lista o un área seleccionada de un control de entrada manuscrita.

**[Size](properties-text.md)**: el tamaño de la fuente del texto que aparece en un control.

**[Strikethrough](properties-text.md)**: indica si aparece una línea sobre el texto de un control.

**[TabIndex](properties-accessibility.md)**: personaliza el orden de tabulación de los controles en tiempo de ejecución cuando se establece en un valor distinto de cero.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Underline](properties-text.md)**: indica si aparece una línea debajo del texto de un control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="example"></a>Ejemplo
1. Agregue un control **[Botón](control-button.md)** y establezca su propiedad **[Texto](properties-core.md)** para mostrar **Recopilar**.
   
    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
2. Establezca la propiedad **[AlSeleccionar](properties-core.md)** del control **[Botón](control-button.md)** en esta fórmula:
   <br>**ClearCollect(CityPopulations, {City:"London", Country:"United Kingdom", Population:8615000}, {City:"Berlin", Country:"Germany", Population:3562000}, {City:"Madrid", Country:"Spain", Population:3165000}, {City:"Rome", Country:"Italy", Population:2874000}, {City:"Paris", Country:"France", Population:2273000}, {City:"Hamburg", Country:"Germany", Population:1760000}, {City:"Barcelona", Country:"Spain", Population:1602000}, {City:"Munich", Country:"Germany", Population:1494000}, {City:"Milan", Country:"Italy", Population:1344000})**
   
    ¿Desea más información sobre la función **[ClearCollect](../functions/function-clear-collect-clearcollect.md)** u [otras funciones](../formula-reference.md)?
3. Presione F5, haga clic o pulse el control **[Botón](control-button.md)** y luego presione Esc.
4. Agregue un control **Lista desplegable**, denomínelo **Países** y establezca su propiedad **[Elementos](properties-core.md)** en esta fórmula:
   <br>**Distinct(CityPopulations, Country)**
5. Agregue un control **Galería de texto** en orientación vertical y establezca su propiedad **[Elementos](properties-core.md)** en esta fórmula:
   <br>**Filter(CityPopulations, Countries.Selected.Value in Country)**
6. En el primer elemento del control **Galería de texto**, establezca la propiedad **[Texto](properties-core.md)** del control **[Etiqueta](control-text-box.md)** superior en **ThisItem.City** y elimine el control **[Etiqueta](control-text-box.md)** inferior.
7. Establezca la propiedad **[TamañoDePlantilla](control-gallery.md)** del control **Galería de texto** en **80**.
8. Presione F5, pulse o haga clic en las comillas angulares de la lista **Countries** y luego elija una opción de esa lista.
   
    El control **Galería de texto** muestra solo esas ciudades del país que eligió.

