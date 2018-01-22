---
title: "Control Gráfico circular: referencia | Microsoft Docs"
description: "Información sobre el control de gráficos circulares, con propiedades y ejemplos"
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
ms.openlocfilehash: 1388eac45e5086f677cb83c8db9593fe01a9819f
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2018
---
# <a name="pie-chart-control-in-powerapps"></a>Control de gráficos circulares en PowerApps
Control que muestra valores relativos comparados entre ellos.

## <a name="description"></a>Descripción
Agregue un control de **gráfico circular** si desea que aparezcan datos relativos de una tabla que contenga las etiquetas de la columna izquierda y valores en la segunda columna de la izquierda.

## <a name="key-properties"></a>Propiedades principales
**[Elementos](properties-core.md)**: origen de datos que aparece en un control, como una galería, una lista o un gráfico.

**ShowLabels**: indica si un gráfico circular muestra el valor asociado con cada una de sus partes.

## <a name="additional-properties"></a>Propiedades adicionales
**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[Color](properties-color-border.md)**: el color del texto en un control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**Seccionar**: distancia entre las partes de un gráfico circular.

**[Font](properties-text.md)**: el nombre de la familia de fuentes en la que aparece el texto.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**ItemBorderColor**: color del borde que rodea cada parte de un gráfico circular.

**ItemBorderThickness**: grosor del borde que rodea cada parte de un gráfico circular.

**ItemColorSet**: color de cada punto de datos de un gráfico.

**LabelPosition**: ubicación de las etiquetas en un gráfico circular con respecto a sus partes.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**[PressedBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario toca o hace clic en ese control.

**[Size](properties-text.md)**: el tamaño de la fuente del texto que aparece en un control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**Max**( *DataSource*, *ColumnName* )](../functions/function-aggregates.md)

## <a name="example"></a>Ejemplo
1. Agregue un control **[Botón](control-button.md)** y establezca su propiedad **[OnSelect](properties-core.md)** en esta fórmula:<br>
   **Collect(Revenue2015, {Product:"Europa", Revenue:27000}, {Product:"Ganymede", Revenue:26300}, {Product:"Callisto", Revenue:29200})**
   
    ¿No sabe cómo [agregar y configurar un control](../add-configure-controls.md)?
   
    ¿Desea más información sobre la función **[Recopilar](../functions/function-clear-collect-clearcollect.md)** u [otras funciones](../formula-reference.md)?
2. Presione F5, pulse o haga clic en el control **[Botón](control-button.md)** y presione Esc para volver al área de trabajo predeterminada.
3. Agregue un control de **gráfico circular** y establezca su propiedad **[Elementos](properties-core.md)** en **Revenue2015**.
   
    El control de **gráfico circular** muestra los datos de ingresos para cada producto en relación con los demás.

