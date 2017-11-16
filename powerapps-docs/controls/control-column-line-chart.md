---
title: "Controles Gráfico de columnas y Gráfico de líneas: referencia | Microsoft Docs"
description: "Información sobre los controles Gráfico de columnas y Gráfico de líneas, con propiedades y ejemplos"
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
ms.openlocfilehash: 039b267394ef6be5e3038fa0b07149f69fee6a51
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="column-chart-and-line-chart-controls-in-powerapps"></a>Controles Gráfico de columnas y Gráfico de líneas en PowerApps
Controles que muestran datos como gráficos con ejes x e y.

## <a name="description"></a>Descripción
De forma predeterminada, un control **Gráfico de columnas** o un control **Gráfico de líneas** constan de varios controles agrupados juntos. Estos controles muestran un título, datos y una leyenda.

## <a name="key-properties"></a>Propiedades principales
**[Elementos](properties-core.md)**: origen de datos que aparece en un control, como una galería, una lista o un gráfico.

**NúmeroDeSeries**: indica el número de columnas de datos reflejadas en un gráfico de columnas o de líneas.

## <a name="all-properties"></a>Todas las propiedades
**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[Color](properties-color-border.md)**: el color del texto en un control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[Font](properties-text.md)**: el nombre de la familia de fuentes en la que aparece el texto.

**GridStyle**: indica si un gráfico de columnas o de líneas muestra su eje x, su eje y, ambos o ninguno.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**ItemColorSet**: color de cada punto de datos de un gráfico.

**ItemsGap**: indica la distancia entre las columnas de un gráfico de columnas.

* La propiedad **ItemsGap** está disponible para el control **Gráfico de columnas** pero no para el control **Gráfico de líneas**.

**Markers**: indica si un gráfico de columnas o de líneas muestra el valor de cada punto de datos.

**MarkerSuffix**: texto que aparece después de cada valor en un gráfico de columnas para el que la propiedad **Markers** está establecida en **true**.

* La propiedad **MarkerSuffix** está disponible para el control **Gráfico de columnas** pero no para el control **Gráfico de líneas**.

**AnchoDeBarraMínimo**: el ancho mínimo posible de columnas en un gráfico de columnas.

* La propiedad **AnchoDeBarraMínimo** está disponible para el control **Gráfico de columnas** pero no para el control **Gráfico de líneas**.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**[RellenoInferior](properties-size-location.md)**: distancia entre el texto de un control y el borde inferior de ese control.

**[RellenoIzquierdo](properties-size-location.md)**: distancia entre el texto de un control y el borde izquierdo de ese control.

**[RellenoDerecho](properties-size-location.md)**: distancia entre el texto de un control y el borde derecho de ese control.

**[RellenoSuperior](properties-size-location.md)**: distancia entre el texto de un control y el borde superior de ese control.

**[PressedBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario toca o hace clic en ese control.

**SeriesAxisMax**: el valor máximo del eje y para un gráfico de columnas o de líneas.

* La propiedad **SeriesAxisMax** está disponible para el control **Gráfico de columnas** pero no para el control **Gráfico de líneas**.

**SeriesAxisMin**: un número que determina el valor mínimo del eje y de un gráfico de columnas.

* La propiedad **SeriesAxisMin** está disponible para el control **Gráfico de columnas** pero no para el control **Gráfico de líneas**.

**[Size](properties-text.md)**: el tamaño de la fuente del texto que aparece en un control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**XLabelAngle**: el ángulo de las etiquetas debajo del eje x de un gráfico de columnas o de líneas.

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

**EjeYMáximo**: el valor máximo del eje y de un gráfico de columnas o de líneas.

* La propiedad **EjeYMáximo** está disponible para el control **Gráfico de columnas** pero no para el control **Gráfico de líneas**.

**EjeYMínimo**: el valor mínimo del eje y de un gráfico de columnas o de líneas.

* La propiedad **EjeYMínimo** está disponible para el control **Gráfico de columnas** pero no para el control **Gráfico de líneas**.

**YLabelAngle**: el ángulo de las etiquetas junto al eje y de un gráfico de líneas o de columnas.

## <a name="related-functions"></a>Funciones relacionadas
[**Max**( *DataSource*, *ColumnName* )](../functions/function-aggregates.md)

## <a name="example"></a>Ejemplo
1. Agregue un control **[Botón](control-button.md)** y establezca su propiedad **[OnSelect](properties-core.md)** en esta fórmula:<br>
   **Collect(Revenue, {Year:"2013", Europa:24000, Ganymede:22300, Callisto:21200}, {Year:"2014", Europa:26500, Ganymede:25700, Callisto:24700},{Year:"2014", Europa:27900, Ganymede:28300, Callisto:25600})**
   
    ¿No sabe cómo [agregar y configurar un control](../add-configure-controls.md)?
   
    ¿Desea más información sobre la función **[Recopilar](../functions/function-clear-collect-clearcollect.md)** u [otras funciones](../formula-reference.md)?
2. Presione F5, pulse o haga clic en el control **[Botón](control-button.md)** y presione Esc para volver al área de trabajo predeterminada.
3. Agregue un control **Gráfico de columnas** o un control **Gráfico de líneas**, establezca su propiedad **[Elementos](properties-core.md)** en **Ingresos** y establezca su propiedad **NúmeroDeSeries** en **3**.
   
    El control muestra datos de ingresos para cada producto durante tres años.

