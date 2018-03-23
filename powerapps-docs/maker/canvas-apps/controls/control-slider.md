---
title: 'Control deslizante: referencia | Microsoft Docs'
description: Información sobre el control deslizante, con propiedades y ejemplos
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
ms.openlocfilehash: dc10ac44c1c14f182c39176a6b0216f3ede3816d
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="slider-control-in-powerapps"></a>Control deslizante en PowerApps
Un control con el que el usuario puede especificar un valor arrastrando un controlador.

## <a name="description"></a>Descripción
El usuario puede indicar un valor comprendido entre un valor mínimo y un máximo que puede especificar arrastrando el controlador de un control deslizante de derecha a izquierda o de arriba a abajo, dependiendo de la dirección que desee.

## <a name="key-properties"></a>Propiedades principales
**[Predeterminado](properties-core.md)**: el valor inicial de un control antes de que lo cambie el usuario.

**Max**: el valor máximo para el que el usuario puede establecer un control deslizante o una clasificación.

**Max**: el valor mínimo para el que el usuario puede establecer un control deslizante.

**[Valor](properties-core.md)**: el valor de un control de entrada.

## <a name="additional-properties"></a>Propiedades adicionales
**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[FocusedBorderThickness](properties-color-border.md)**: grosor del borde del control cuando se resalta el teclado.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**RellenoDeControladorActivo**: el color del controlador de un control deslizante cuando el usuario cambia el valor.

**RellenoDeControlador**: el color del controlador (el elemento que cambia de posición) en un control de alternancia o control deslizante.

**RellenoDeControladorAlMantener**: el color del texto del controlador cuando el usuario mantiene el puntero sobre él.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**Layout**: indica si el usuario se desplaza por la galería o ajusta un control deslizante de arriba a abajo (**Vertical**) o de izquierda a derecha (**Horizontal**).

**[AlCambiar](properties-core.md)**: indica cómo responde la aplicación cuando el usuario cambia el valor de un control (por ejemplo, mediante el ajuste de un control deslizante).

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**[PressedBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario toca o hace clic en ese control.

**RellenoDeRaíl**: color de fondo del rectángulo en un control Alternar cuando su valor es **false** o color de la línea a la derecha del identificador en un control deslizante.

**RellenoRaílAlMantenerPuntero**: al mantener el puntero sobre un control Alternar o deslizante, color de fondo del rectángulo del primero cuando su valor es **false** o color de la línea a la derecha del identificador del segundo.

**ReadOnly**: indica si un usuario puede cambiar el valor de un control deslizante o el control de clasificación.

**[Reset](properties-core.md)**: indica si un control vuelve a su valor predeterminado.

**MostrarValor**: indica si el valor de un control deslizante o una clasificación aparece cuando el usuario cambia ese valor o mantiene el puntero sobre el control.

**[TabIndex](properties-accessibility.md)**: personaliza el orden de tabulación de los controles en tiempo de ejecución cuando se establece en un valor distinto de cero.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**RellenoDeValor**: color de fondo del rectángulo en un control Alternar cuando su valor es **true** o color de la línea a la izquierda del identificador en un control deslizante.

**RellenoValorAlMantenerPuntero**: al mantener el puntero del mouse sobre un control Alternar o Control deslizante, color de fondo del rectángulo del primero cuando su valor es **true** o color de la línea a la izquierda del identificador del segundo.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**Sum**( *Value1*, *Value2* )](../functions/function-aggregates.md)

## <a name="example"></a>Ejemplo
1. Agregue un botón y establezca su propiedad **[OnSelect](properties-core.md)** en esta fórmula:
   <br>**ClearCollect(CityPopulations, {City:"London", Country:"United Kingdom", Population:8615000}, {City:"Berlin", Country:"Germany", Population:3562000}, {City:"Madrid", Country:"Spain", Population:3165000}, {City:"Rome", Country:"Italy", Population:2874000}, {City:"Paris", Country:"France", Population:2273000}, {City:"Hamburg", Country:"Germany", Population:1760000}, {City:"Barcelona", Country:"Spain", Population:1602000}, {City:"Munich", Country:"Germany", Population:1494000}, {City:"Milan", Country:"Italy", Population:1344000})**
   
    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
   
    ¿Desea más información sobre la función **[ClearCollect](../functions/function-clear-collect-clearcollect.md)** u [otras funciones](../formula-reference.md)?
2. Presione F5, seleccione el botón y presione Esc.
3. Agregue un control deslizante, muévalo debajo del botón y llámelo **MinPopulation**.
4. Establezca la propiedad **Max** del control deslizante en **5000000** y la propiedad **Min** en **1000000**.
5. Agregue una galería de texto en orientación vertical, muévala debajo del control deslizante y establezca la propiedad **[Elementos](properties-core.md)** de la galería en esta fórmula:<br>
   **Filter(CityPopulations, Population > MinPopulation)**
6. En el primer elemento de la galería, establezca la propiedad **[Texto](properties-core.md)** de la etiqueta superior en **ThisItem.City** y establezca la propiedad **[Texto](properties-core.md)** de la etiqueta inferior en esta fórmula:<br> **Text(ThisItem.Population, "##,###")**
7. Presione F5 y, a continuación, ajuste **MinPopulation** para que se muestren solo aquellas ciudades que tengan una población mayor que el valor especificado.
8. Presione Esc para volver al área de trabajo predeterminada.

