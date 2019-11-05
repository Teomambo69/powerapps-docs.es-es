---
title: Mostrar una lista de elementos en una aplicación de lienzo | Microsoft Docs
description: Utilice una galería para mostrar una lista de elementos de la aplicación de lienzo y filtre la lista especificando un criterio.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/28/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6d48b7b6ef1d9d691b733bea9af6ce74d0f2b07a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540929"
---
# <a name="show-a-list-of-items-in-powerapps"></a>Mostrar una lista de elementos en PowerApps

Muestre una lista de elementos de cualquier origen de datos agregando un control **[Galería](controls/control-gallery.md)** a la aplicación de lienzo. En este tema se utiliza Excel como origen de datos. Filtre la lista mediante la configuración del control **Galería** para mostrar únicamente aquellos elementos que coinciden con el criterio de filtro en un control **[Entrada de texto](controls/control-text-input.md)** .

## <a name="prerequisites"></a>Requisitos previos

- Aprenda a [agregar y configurar un control](add-configure-controls.md) en PowerApps.

- Configure los datos de ejemplo:
    1. Descargue [este archivo de Excel](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx), que contiene datos de ejemplo para este tutorial.

    2. Cargue el archivo de Excel en una [cuenta de almacenamiento en la nube](connections/cloud-storage-blob-connections.md), como OneDrive para la Empresa.

- Abra una aplicación en blanco:
    1. [Inicie sesión en PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

    1. En **Cree su propia aplicación**, seleccione **Aplicación de lienzo en blanco**.

    1. Especifique el nombre de la aplicación, seleccione **Teléfono** y, luego, **Crear**.

    1. Si aparece el cuadro de diálogo de **bienvenida a PowerApps Studio**, seleccione **Skip** (Omitir).

    1. [Agregue una conexión](add-data-connection.md) a la tabla **FlooringEstimates** del archivo de Excel.

## <a name="add-a-gallery-to-a-blank-screen"></a>Agregar una galería a una pantalla en blanco

1. En la pestaña **Insertar** , seleccione **Galería**y, a continuación, seleccione **vertical**.

    ![Agregar Galería vertical](./media/add-gallery/gallery-dropdown.png)

1. En la pestaña **propiedades** del panel derecho, abra la lista **elementos** y, a continuación, seleccione las **estimaciones de suelos**.

    ![Estimaciones de suelos](./media/add-gallery/select-layout.png)

1. opta En la lista **diseño** , seleccione una opción diferente.

## <a name="add-a-gallery-in-a-screen"></a>Agregar una galería en una pantalla

1. En la pestaña **Inicio** , seleccione **nueva pantalla** > **pantalla lista**.

    Aparece una pantalla que contiene un control **Galería** y otros controles, como una barra de búsqueda.

1. Establezca la propiedad **Elementos** de la galería en `FlooringEstimates`.

    El control **Galería** muestra los datos de ejemplo.

    ![Mostrar datos](./media/add-gallery/show-data-default.png)

## <a name="add-a-control-to-the-gallery-control"></a>Agregar un control al control Galería
Antes de realizar cualquier otra personalización, asegúrese de que el diseño del control de **Galería** coincida mejor con el que desee. Desde allí, puede modificar aún más la plantilla de la **Galería** , que determina cómo se muestran todos los datos del control de la **Galería** .

1. Seleccione la plantilla haciendo clic o pulsando cerca de la parte inferior del control **Galería** y seleccionando después el icono de lápiz en la esquina superior izquierda.

    ![Editar plantilla de galería](./media/add-gallery/edit-item.png)

2. Con la plantilla aún seleccionada, agregue un control **[Etiqueta](controls/control-text-box.md)** y, después, muévalo y ajuste su tamaño para que no se superponga con otros controles de la plantilla.

    ![Agregar etiqueta](./media/add-gallery/add-text-box.png)

3. Seleccione la galería y, a continuación, seleccione **Editar** junto a **campos** en la pestaña **propiedades** del panel derecho.

4. Seleccione la etiqueta que ha agregado en este procedimiento y abra la lista resaltada en el panel **Data** (Datos).

    ![Lista desplegable abierta](./media/add-gallery/open-dropdown.png)

5. En dicha lista, pulse o haga clic en **Price**.

    El control **Galería** muestra los valores nuevos.

    ![Galería final](./media/add-gallery/final-gallery.png)

## <a name="filter-and-sort-a-gallery"></a>Filtrar y ordenar una galería
La propiedad **[Elementos](controls/properties-core.md)** de una control **Galería** determina los elementos que muestra. En este procedimiento, configurará esa propiedad para que también determine qué registros aparecen según los criterios de filtro y en qué orden.

![Cuadro de búsqueda y icono de ordenación](./media/add-gallery/text-search-box.png)

1. Establezca la propiedad **[Elementos](controls/properties-core.md)** del control **Galería** en esta fórmula:

    ```powerapps-dot
    Sort
        (If
            (IsBlank(TextSearchBox1.Text),
            FlooringEstimates,
            Filter(
                FlooringEstimates,
                TextSearchBox1.Text in Text(Name)
            )
        ),
        Name,
        If(
            SortDescending1,
            SortOrder.Descending,
            SortOrder.Ascending
        )
    )
    ```

    Para más información acerca de las funciones de esta fórmula, consulte la [referencia de las fórmulas](formula-reference.md).

1. Haga doble clic en el cuadro de búsqueda y, a continuación, escriba parte o todo el nombre del producto en él.

    Solo aparecen los elementos que cumplen el criterio de filtro.

1. Mientras presiona la tecla Alt, seleccione el icono de ordenación una o varias veces para cambiar el criterio de ordenación.

    Los registros alternan entre orden alfabético ascendente y descendente según el nombre del producto.

## <a name="highlight-the-selected-item"></a>Resalte del elemento seleccionado
Establezca la propiedad **rellenodeplantilla** del control de **Galería** en una fórmula similar a la de este ejemplo, pero puede especificar distintos colores si lo desea:

**If(ThisItem.IsSelected, LightCyan, White)**

## <a name="change-the-default-selection"></a>Cambio de la elección predeterminada
En la propiedad **Default** del control **Galería**, especifique el registro que desea que se seleccione de manera predeterminada. Por ejemplo, puede especificar el quinto elemento en el origen de datos **FlooringEstimates** :

**Last(FirstN(FlooringEstimates, 5))**

En este ejemplo, especifique el primer elemento de la categoría **Hardwood** del origen de datos **FlooringEstimates**:

**First(Filter(FlooringEstimates, Category = "Hardwood"))**

## <a name="next-steps"></a>Pasos siguientes
Aprenda a trabajar con [formularios](working-with-forms.md) y [fórmulas](working-with-formulas.md).
