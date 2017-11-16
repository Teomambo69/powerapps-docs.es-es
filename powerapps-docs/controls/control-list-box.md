---
title: 'Control Cuadro de lista: referencia | Microsoft Docs'
description: "Información sobre el control Cuadro de lista, con propiedades y ejemplos"
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
ms.openlocfilehash: ada7fed1ac9fabb9a89f79a876fcce68b4415d30
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="list-box-control-in-powerapps"></a>Control Cuadro de lista en PowerApps
Una lista en la que el usuario puede seleccionar uno o varios elementos.

## <a name="description"></a>Descripción
Un control **Cuadro de lista** siempre muestra todas las opciones disponibles (a diferencia de un control **[Lista desplegable](control-drop-down.md)**) y a diferencia de un control **[Radio](control-radio.md)**, el usuario puede seleccionar varios elementos al mismo tiempo.

## <a name="key-properties"></a>Propiedades principales
**[Predeterminado](properties-core.md)**: el valor inicial de un control antes de que lo cambie el usuario.

**[Elementos](properties-core.md)**: origen de datos que aparece en un control, como una galería, una lista o un gráfico.

[!INCLUDE [long-items](../../includes/long-items.md)]

## <a name="additional-properties"></a>Propiedades adicionales
**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[FocusedBorderThickness](properties-color-border.md)**: grosor del borde del control cuando se resalta el teclado.

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

**ItemPaddingLeft**: la distancia entre el texto en un cuadro de lista y su borde izquierdo.

**[AlturaDeLínea](properties-text.md)**: distancia entre, por ejemplo, líneas de texto o elementos de una lista.

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

**SelecciónMúltiple**: indica si un usuario puede seleccionar más de un elemento en un cuadro de lista.

**[Size](properties-text.md)**: el tamaño de la fuente del texto que aparece en un control.

**[Strikethrough](properties-text.md)**: indica si aparece una línea sobre el texto de un control.

**[TabIndex](properties-accessibility.md)**: personaliza el orden de tabulación de los controles en tiempo de ejecución cuando se establece en un valor distinto de cero.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Underline](properties-text.md)**: indica si aparece una línea debajo del texto de un control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**Distinct**( *DataSource*, *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>Ejemplo
1. Agregue un control **Cuadro de lista**, denomínelo **CategoryList** y establezca su propiedad **[Elementos](properties-core.md)** en esta fórmula:<br>
   **["Moqueta", "Parquet", "Mosaico"]**
   
    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
   
    ![Categorías de suelo en el cuadro de lista](./media/control-list-box/category-listbox.png)
2. Agregar tres controles **[Lista desplegable](control-drop-down.md)**, muévalas a **CategoryList**y asígneles un nombre **ListaMoqueta**, **ListaParquet**, y **ListaMosaico**.
3. Establecer la propiedad **[Elementos](properties-core.md)** de cada control **[Lista desplegable](control-drop-down.md)** en uno de estos valores:
   
   * ListaMoqueta: **["Caserta Stone Beige","Ageless Beauty Clay", "Lush II Tundra"]**
   * ListaParquet: **["Golden Teak","Natural Hickory", "Victoria Mahogany"]**
   * ListaMosaico: **["Honey Onyx Marble","Indian Autumn Slate", "Panaria Vitality Ceramic"]**
     
     ![Nombres de suelos en las listas desplegables](./media/control-list-box/flooring-names.png)
4. Establezca la propiedad **[Elementos](properties-core.md)** de cada control **[Lista desplegable](control-drop-down.md)** en uno de estos valores:
   
   * ListaMoqueta: **If("Moqueta" en CategoryList.SelectedItems.Value, true)**
   * ListaParquet: **If("Parquet" en CategoryList.SelectedItems.Value, true)**
   * ListaMosaico: **If("Mosaico" en CategoryList.SelectedItems.Value, true)**
     
     ¿Desea más información sobre la función **[If](../functions/function-if.md)** u [otras funciones](../formula-reference.md)?
5. Presione F5 y, a continuación, elija uno o más elementos de **CategoryList**.
   
    Aparecerá el control o controles apropiados **[Lista desplegable](control-drop-down.md)**  en función de su elección.
   
    ![Nombres de suelos en las listas desplegables](./media/control-list-box/selected-lists.png)
6. (opcional) Presione Esc para volver al área de trabajo predeterminada.

