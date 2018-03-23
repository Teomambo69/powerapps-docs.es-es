---
title: Presentación de una lista de elementos | Microsoft Docs
description: Use una galería para mostrar una lista de elementos de la aplicación y filtre la lista especificando un criterio.
services: ''
suite: powerapps
documentationcenter: na
author: karthik-1
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/28/2017
ms.author: sharik
ms.openlocfilehash: 04499f276e179fe6b57103a3d28a68ba6fe6b7bb
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="show-a-list-of-items-in-powerapps"></a>Mostrar una lista de elementos en PowerApps
Muestre una lista de elementos de cualquier origen de datos mediante la adición de un control **[Galería](controls/control-gallery.md)** a la aplicación. En este tema se utiliza Excel como origen de datos. Filtre la lista mediante la configuración del control **Galería** para mostrar únicamente aquellos elementos que coinciden con el criterio de filtro en un control **[Entrada de texto](controls/control-text-input.md)**.

## <a name="prerequisites"></a>Requisitos previos
* Aprenda a [agregar y configurar un control](add-configure-controls.md) en PowerApps.

* Configure los datos de ejemplo:
    1. Descargue [este archivo de Excel](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx), que contiene datos de ejemplo para este tutorial.

    2. Cargue el archivo de Excel en una [cuenta de almacenamiento en la nube](connections/cloud-storage-blob-connections.md), como OneDrive para la Empresa.

## <a name="add-a-gallery-control"></a>Adición de un control Galería
1. Abra PowerApps y haga clic o pulse en **Nueva aplicación** cerca del borde izquierdo.

2. En el icono **Blank app** (Aplicación vacía), pulse o haga clic en **Phone layout** (Diseño de teléfono).

3. En el cuadro de diálogo **PowerApps Studio**, pulse o haga clic en **Skip** (Omitir).

4. [Agregue una conexión](add-data-connection.md) a la tabla **FlooringEstimates** del archivo de Excel.

5. (opcional) Agregue un control **Galería** a la pantalla predeterminada, para lo que debe hacer clic o pulsar la pestaña **Insertar**, pulsar o hacer clic en **Galería** y, después, pulsar o hacer clic en un control **Galería** que esté vacío (en blanco) o que contenga un conjunto predeterminado de controles.

    Estas opciones incluyen controles **Galería** que se desplazan de forma horizontal o vertical. También se puede agregar un control **Galería** que base automáticamente su tamaño en la cantidad de contenido de cada elemento.

    ![Agregar galería](./media/add-gallery/gallery-dropdown.png)

6. En la pestaña **Inicio**, pulse o haga clic en **Nueva pantalla**.

    Puede agregar una pantalla que esté vacía, que se desplace, que contenga un control **Galería** o que contenga un formulario.

7. Pulse o haga clic en **Pantalla de lista** para agregar una pantalla que contenga un control **Galería** y otros controles, como una barra de búsqueda.

    > [!NOTE]
> Si agrega un control **Galería** a una pantalla nueva o a una existente, puede hacer clic o pulsar cerca de la parte inferior del control **Galería** para seleccionarlo, pulsar o hacer clic en **Flooring Estimates** en el panel derecho y, después, pulsar o hacer clic en otro diseño del panel **Datos**. Para este tutorial, deje el diseño predeterminado.

    ![Elegir el diseño de la galería](./media/add-gallery/select-layout.png)

8. Pulse o haga clic en el control **Galería** de la pantalla que acaba de agregar.

9. En la pestaña **Propiedades** del panel derecho, pulse o haga clic en **CustomGallerySample**.

10. En el panel **Data** (Datos), pulse o haga clic en **CustomGallerySample** y, después, en **FlooringEstimates**.

    ![Seleccionar origen de datos](./media/add-gallery/choose-data.png)

    El control **Galería** muestra los datos de ejemplo.

    ![Mostrar datos](./media/add-gallery/show-data-default.png)

    La ordenación y la búsqueda se configurarán en este mismo tema más adelante.

## <a name="add-a-control-to-the-gallery-control"></a>Agregar un control al control Galería
Antes de realizar cualquier personalización, elija un diseño del control **Galería**. El primer conjunto de controles de un control **Galería** es la plantilla, que determina el aspecto de todos los datos de dicho control.

1. Seleccione la plantilla, para lo que debe hacer clic o pulsar cerca de la parte inferior del control **Galería** y, después, pulsar o hacer clic en el icono del lápiz en la esquina superior izquierda.

    ![Editar plantilla de galería](./media/add-gallery/edit-item.png)

2. Con la plantilla aún seleccionada, agregue un control **[Etiqueta](controls/control-text-box.md)** y, después, muévalo y ajuste su tamaño para que no se superponga con otros controles de la plantilla.

    ![Agregar etiqueta](./media/add-gallery/add-text-box.png)
3. Abra el panel **Data** (Datos), para lo que debe seleccionar la plantilla y, después, pulsar o hacer clic en **Flooring Estimates** en el panel derecho.

4. Seleccione la etiqueta que ha agregado en este procedimiento y abra la lista resaltada en el panel **Data** (Datos).

    ![Lista desplegable abierta](./media/add-gallery/open-dropdown.png)

5. En dicha lista, pulse o haga clic en **Price**.

    ![Cambiar el enlace de la etiqueta](./media/add-gallery/change-binding.png)

    El control **Galería** muestra los valores nuevos.

    ![Galería final](./media/add-gallery/final-gallery.png)

## <a name="filter-the-gallery-control"></a>Filtro del control Galería
La propiedad **[Elementos](controls/properties-core.md)** de una control **Galería** determina los elementos que muestra. En este procedimiento, se configura esa propiedad para que el control **Galería** muestre solo los elementos para los que el nombre del producto contenga el texto de **TextSearchBox1**.

![Cuadro de búsqueda de texto](./media/add-gallery/text-search-box.png)

1. Seleccione el control **Galería**, para lo que debe hacer clic o pulsar cerca de la parte inferior del control Galería.

2. En la pestaña **Opciones avanzadas**, establezca la pestaña**[Elementos](controls/properties-core.md)** del control **Galería** en esta fórmula:

    **If(IsBlank(TextSearchBox1.Text), FlooringEstimates, Filter(FlooringEstimates, TextSearchBox1.Text in Text(Name)))**

    Para más información acerca de las funciones de esta fórmula, consulte la [referencia de las fórmulas](formula-reference.md).

3. Escriba una parte o la totalidad de un nombre de producto en el cuadro de búsqueda.

    El control **Galería** muestra solo los elementos que cumplen el criterio de filtro.

## <a name="sort-the-gallery-control"></a>Orden del control Galería
La propiedad **[Elementos](controls/properties-core.md)** de un control **Galería** determina el orden en que muestra los elementos. En este procedimiento, configurará esa propiedad para que el control **Galería** muestra el orden de los elementos según lo establecido por **ImageSortUpDown1**.

![Imagen para ordenar](./media/add-gallery/image-sorting.png)

1. Establezca la propiedad **[Elementos](controls/properties-core.md)** del control **Galería** en esta fórmula:

    **Sort(If(IsBlank(TextSearchBox1.Text), FlooringEstimates, Filter(FlooringEstimates, TextSearchBox1.Text in Text(Name))), Name, If(SortDescending1, SortOrder.Descending, SortOrder.Ascending))**

2. Seleccione el icono de ordenación para cambiar el criterio de ordenación del control **Galería** por los nombres de los productos.

Para ordenar *y* filtrar un control **Galería**:

* Reemplace las dos instancias de *DataSource* de esta fórmula por el nombre del origen de datos.

* Reemplace las dos instancias de *ColumnName* por el nombre de la columna por la que desea ordenar y filtrar.

**Sort(If(IsBlank(TextSearchBox1.Text),** *DataSource*, **Filter(** *DataSource*, **TextSearchBox1.Text in Text(** *ColumnName* **))),** *ColumnName*, **If(SortDescending1, SortOrder.Descending, SortOrder.Ascending))**

## <a name="highlight-the-selected-item"></a>Resalte del elemento seleccionado
En la propiedad **RellenoDePlantilla** del control **Galería** escriba una fórmula similar a la de este ejemplo:

**If(ThisItem.IsSelected, LightCyan, White)**

## <a name="change-the-default-selection"></a>Cambio de la elección predeterminada
En la propiedad **Default** del control **Galería**, especifique el registro que desea que se seleccione de manera predeterminada. Por ejemplo, especifique el quinto elemento del origen de datos **FlooringEstimates**:

**Last(FirstN(FlooringEstimates, 5))**

En este ejemplo, especifique el primer elemento de la categoría **Hardwood** del origen de datos **FlooringEstimates**:

**First(Filter(FlooringEstimates, Category = "Hardwood"))**

## <a name="next-steps"></a>Pasos siguientes
Aprenda a trabajar con [formularios](working-with-forms.md) y [fórmulas](working-with-formulas.md).
