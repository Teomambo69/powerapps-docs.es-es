---
title: Mostrar una lista de elementos en una aplicación de lienzo | Microsoft Docs
description: Utilice una galería para mostrar una lista de elementos de la aplicación de lienzo y filtre la lista especificando un criterio.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 09/28/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f45948bc16f036669a09ed2c566c60440d24a797
ms.sourcegitcommit: 2180982e57f0d161610be584fdae9424fe7e06b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/29/2019
ms.locfileid: "58616717"
---
# <a name="show-a-list-of-items-in-powerapps"></a>Mostrar una lista de elementos en PowerApps

Muestre una lista de elementos de cualquier origen de datos agregando un control **[Galería](controls/control-gallery.md)** a la aplicación de lienzo. En este tema se utiliza Excel como origen de datos. Filtre la lista mediante la configuración del control **Galería** para mostrar únicamente aquellos elementos que coinciden con el criterio de filtro en un control **[Entrada de texto](controls/control-text-input.md)**.

## <a name="prerequisites"></a>Requisitos previos

- Aprenda a [agregar y configurar un control](add-configure-controls.md) en PowerApps.

- Configure los datos de ejemplo:
    1. Descargue [este archivo de Excel](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx), que contiene datos de ejemplo para este tutorial.

    2. Cargue el archivo de Excel en una [cuenta de almacenamiento en la nube](connections/cloud-storage-blob-connections.md), como OneDrive para la Empresa.

- Abra una aplicación en blanco:
    1. [Inicie sesión en PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

    1. En **Cree su propia aplicación**, seleccione **Aplicación de lienzo en blanco**.

    1. Especifique el nombre de la aplicación, seleccione **Teléfono** y, luego, **Crear**.

    1. Si aparece el cuadro de diálogo de **bienvenida a PowerApps Studio**, seleccione **Omitir**.

    1. [Agregue una conexión](add-data-connection.md) a la tabla **FlooringEstimates** del archivo de Excel.

## <a name="add-a-gallery-to-a-blank-screen"></a>Agregue una galería en una pantalla en blanco

1. En el **insertar** ficha, seleccione **galería**y, a continuación, seleccione **Vertical**.

    ![Agregar galería vertical](./media/add-gallery/gallery-dropdown.png)

1. En el **propiedades** ficha del panel derecho, abrirlo el **elementos** lista y, a continuación, seleccione **Flooring Estimates**.

    ![Estimaciones de suelos](./media/add-gallery/select-layout.png)

1. (opcional) En el **diseño** lista, seleccione una opción diferente.

## <a name="add-a-gallery-in-a-screen"></a>Agregue una galería en una pantalla

1. En el **inicio** ficha, seleccione **nueva pantalla** > **pantalla lista**.

    Una pantalla que contenga un **galería** control y otros controles, como una barra de búsqueda, aparece.

1. Establezca la propiedad **Elementos** de la galería en `FlooringEstimates`.

    El control **Galería** muestra los datos de ejemplo.

    ![Mostrar datos](./media/add-gallery/show-data-default.png)

## <a name="add-a-control-to-the-gallery-control"></a>Agregar un control al control Galería
Antes de realizar cualquier otra personalización, asegúrese de que el diseño de su **galería** control más acerque lo que desea. Desde allí, puede modificar aún más el **galería** plantilla, que determina cómo todos los datos en el **galería** aparezca el control.

1. Seleccione la plantilla haciendo clic o pulsar cerca de la parte inferior de la **galería** control y, a continuación, seleccionando el icono de lápiz en la esquina superior izquierda.

    ![Editar plantilla de galería](./media/add-gallery/edit-item.png)

2. Con la plantilla aún seleccionada, agregue un control **[Etiqueta](controls/control-text-box.md)** y, después, muévalo y ajuste su tamaño para que no se superponga con otros controles de la plantilla.

    ![Agregar etiqueta](./media/add-gallery/add-text-box.png)

3. Seleccione la galería y, a continuación, seleccione **editar** junto a **campos** en el **propiedades** ficha del panel derecho.

4. Seleccione la etiqueta que ha agregado en este procedimiento y abra la lista resaltada en el panel **Data** (Datos).

    ![Lista desplegable abierta](./media/add-gallery/open-dropdown.png)

5. En dicha lista, pulse o haga clic en **Price**.

    El control **Galería** muestra los valores nuevos.

    ![Galería final](./media/add-gallery/final-gallery.png)

## <a name="filter-and-sort-a-gallery"></a>Filtrar y ordenar una galería
La propiedad **[Elementos](controls/properties-core.md)** de una control **Galería** determina los elementos que muestra. En este procedimiento, configurará esa propiedad para que también determina los registros que aparecen se basa en criterios de filtro y en qué orden.

![Icono de ordenación y de cuadro de búsqueda](./media/add-gallery/text-search-box.png)

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

1. Haga doble clic en el cuadro de búsqueda y, a continuación, escriba la totalidad o parte de un nombre de producto en ella.

    Solo los elementos que cumplen el criterio de filtro aparecen.

1. Mientras se presiona la tecla Alt, seleccione el icono de ordenación una o varias veces para cambiar el criterio de ordenación.

    Activar o desactivar los registros entre ascendente y descendente por orden alfabético según el nombre del producto.

## <a name="highlight-the-selected-item"></a>Resalte del elemento seleccionado
Establecer el **galería** del control **Rellenodeplantilla** propiedad en una fórmula que es similar a este ejemplo, pero puede especificar distintos colores si desea:

**If(ThisItem.IsSelected, LightCyan, White)**

## <a name="change-the-default-selection"></a>Cambio de la elección predeterminada
En la propiedad **Default** del control **Galería**, especifique el registro que desea que se seleccione de manera predeterminada. Por ejemplo, puede especificar el quinto elemento de la **FlooringEstimates** origen de datos:

**Last(FirstN(FlooringEstimates, 5))**

En este ejemplo, especifique el primer elemento de la categoría **Hardwood** del origen de datos **FlooringEstimates**:

**First(Filter(FlooringEstimates, Category = "Hardwood"))**

## <a name="next-steps"></a>Pasos siguientes
Aprenda a trabajar con [formularios](working-with-forms.md) y [fórmulas](working-with-formulas.md).
