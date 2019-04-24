---
title: 'Control Gráfico circular: referencia | Microsoft Docs'
description: Información sobre el control de gráficos circulares, con propiedades y ejemplos
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8c2a48941629e98f58ea6d6ac7894e6a244b5e69
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61548096"
---
# <a name="pie-chart-control-in-powerapps"></a>Control de gráficos circulares en PowerApps
Control que muestra valores relativos comparados entre ellos.

## <a name="description"></a>Descripción
Agregue un control de **gráfico circular** si desea que aparezcan datos relativos de una tabla que contenga las etiquetas de la columna izquierda y valores en la segunda columna de la izquierda.

Este control es un control agrupado que contiene tres controles: un control **[Etiqueta](control-text-box.md)** para el título, el gráfico y un control **Leyenda**.

## <a name="chart-key-properties"></a>Propiedades principales del gráfico
**[Elementos](properties-core.md)**: origen de datos que aparece en un control, como una galería, una lista o un gráfico.

**ShowLabels**: indica si un gráfico circular muestra el valor asociado con cada una de sus partes.

## <a name="additional-chart-properties"></a>Propiedades adicionales del gráfico
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

**[TabIndex](properties-accessibility.md)**: orden de navegación del teclado en relación con otros controles.

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


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="color-contrast"></a>Contraste de color
Debe haber un contraste de color adecuado entre:
* Cada elemento de **ItemColorSet**
* Cada elemento de **ItemColorSet** y el color de fondo
* La propiedad **[Color](properties-color-border.md)** y el color de fondo

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* Debe haber un control **[Etiqueta](control-text-box.md)** inmediatamente delante del gráfico para que sirva de título.

    > [!NOTE]
  > Los gráficos y el control **Leyenda** están ocultos para los usuarios de lector de pantalla. Como alternativa, se les presenta los datos en formato tabular. También pueden recorrer los botones que seleccionan datos en el gráfico.

### <a name="low-vision-support"></a>Apoyo para deficiencia visual
* Debe haber un control **Leyenda**.
* Considere la posibilidad de establecer **ShowLabels** en **true**. Esto ayuda a los usuarios con deficiencia visual a determinar rápidamente qué representa cada sector del gráfico circular.
* Considere la posibilidad de establecer **LabelPosition** en **LabelPosition.Outside**. De esta forma, aumenta la legibilidad de las etiquetas debido a un contraste de color más uniforme.

### <a name="keyboard-support"></a>Compatibilidad con el teclado
* La propiedad **[TabIndex](properties-accessibility.md)** debe ser cero o superior para que los usuarios del teclado puedan desplazarse hasta él.

    > [!NOTE]
  > Cuando los usuarios de teclado se desplazan al gráfico, pueden recorrer los botones que seleccionan datos del gráfico.
