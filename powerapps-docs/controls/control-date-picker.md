---
title: 'Control Selector de fecha: referencia | Microsoft Docs'
description: "Información sobre el control Selector de fecha, con propiedades y ejemplos"
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
ms.openlocfilehash: f2605680c7b6e8f7102fd3459230344863a93f55
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="date-picker-control-in-powerapps"></a>Control Selector de fecha en PowerApps
Un control en el que el usuario puede hacer clic o pulsar para especificar una fecha.

## <a name="description"></a>Descripción
Si agrega un control **Selector de fecha** en lugar de un control **[Entrada de texto](control-text-input.md)**, ayuda a garantizar que el usuario especifica una fecha en el formato correcto.

## <a name="key-properties"></a>Propiedades principales
**DefaultDate** (FechaPred): el valor inicial de un control de fecha a menos que el usuario lo modifique.

**SelectedDate**: la fecha seleccionada actualmente en un control de fecha.

**Formato**: el formato de texto en el que el control muestra la fecha y el usuario especifica la fecha. Puede establecer esta propiedad en **FechaCorta** (valor predeterminado) o **FechaLarga** para dar formato a las fechas según la propiedad **Lenguaje** de este control. También puede establecer esta propiedad en una expresión, como **yyyy/mm/dd** si desea el mismo formato con independencia del lenguaje. Por ejemplo:

* El control muestra **12/31/2017** si el usuario pulsa o hace clic en el último día de 2017, la propiedad **Formato** está establecida en **FechaCorta** y la propiedad **Idioma** está establecida en **en-us**.
* El control muestra **dimanche 31 decembre 2017** si el usuario pulsa o hace clic en el último día de 2017, la propiedad **Formato** está establecida en **FechaLarga** y la propiedad **Idioma** está establecida en **fr-fr**.

**Idioma**: determina el idioma utilizado para dar formato a las fechas, como los nombres de los meses. Si no se especifica esta propiedad, la configuración del dispositivo del usuario determina el idioma.

## <a name="additional-properties"></a>Propiedades adicionales
**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[FocusedBorderThickness](properties-color-border.md)**: grosor del borde del control cuando se resalta el teclado.

**[Color](properties-color-border.md)**: el color del texto en un control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (Edit), solo muestra datos (View) o si está deshabilitado (Disabled).

**[DisabledBorderColor](properties-color-border.md)**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[DisabledColor](properties-color-border.md)**: el color del texto en un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[DisabledFill](properties-color-border.md)**: el color de fondo de un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**EndYear**: el último año en el que el usuario puede establecer el valor de un control Selector de fecha.

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[Font](properties-text.md)**: el nombre de la familia de fuentes en la que aparece el texto.

**[FontWeight](properties-text.md)**: el peso del texto en un control: **Bold**, **Semibold**, **Normal** o **Lighter**.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[Italic](properties-text.md)**: indica si el texto de un control está en cursiva.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**[RellenoInferior](properties-size-location.md)**: distancia entre el texto de un control y el borde inferior de ese control.

**[RellenoIzquierdo](properties-size-location.md)**: distancia entre el texto de un control y el borde izquierdo de ese control.

**[RellenoDerecho](properties-size-location.md)**: distancia entre el texto de un control y el borde derecho de ese control.

**[RellenoSuperior](properties-size-location.md)**: distancia entre el texto de un control y el borde superior de ese control.

**[Size](properties-text.md)**: el tamaño de la fuente del texto que aparece en un control.

**StartYear**: el primer año en el que el usuario puede establecer el valor de un control Selector de fecha.

**[TabIndex](properties-accessibility.md)**: personaliza el orden de tabulación de los controles en tiempo de ejecución cuando se establece en un valor distinto de cero.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
**[Año](../functions/function-datetime-parts.md)**( *FechaHoraNúmero* )

## <a name="example"></a>Ejemplo
1. Agregue un control **Selector de fecha** y denomínelo **Deadline**.
   
    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
2. Agregue un control **[Etiqueta](control-text-box.md)** y establezca su propiedad **[Texto](properties-core.md)** en esta fórmula:
   <br>**DateDiff(Today(), Deadline.SelectedDate) & " days to go!"**
   
    ¿Desea más información sobre la función **[DateDiff](../functions/function-dateadd-datediff.md)** u [otras funciones](../formula-reference.md)?
3. Presione F5, elija una fecha en **Deadline** (Fecha límite) y, a continuación, pulse o haga clic en **Aceptar**.
   
    El control **[Etiqueta](control-text-box.md)** muestra el número de días entre hoy y la fecha que eligió.
4. Presione Esc para volver al área de trabajo predeterminada.

