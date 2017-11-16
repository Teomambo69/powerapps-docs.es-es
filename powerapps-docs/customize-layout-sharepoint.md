---
title: "Personalización de un diseño de la galería | Microsoft Docs"
description: "Especifique qué controles se mostrarán, qué campos se mostrará en cada control y qué columnas se usarán para ordenar y buscar los registros."
services: 
suite: powerapps
documentationcenter: na
author: skjerland
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/02/2017
ms.author: sharik
ms.openlocfilehash: c581abad70012eb66413a31bd765437df69b7a70
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="customize-a-gallery-layout-in-powerapps"></a>Personalizar un diseño de galería en PowerApps
Después de generar una aplicación automáticamente en PowerApps, personalice la pantalla de exploración que aparece de forma predeterminada. Especifique qué diseño se usará, qué columnas se mostrarán y qué columnas se deben usar al ordenar y filtrar registros.

* Para obtener información acerca de cómo generar una aplicación automáticamente, consulte [Generar una aplicación para administrar los datos de una lista de SharePoint](app-from-sharepoint.md).
* Si no está familiarizado con PowerApps, consulte [Introducción a PowerApps](getting-started.md).

## <a name="prerequisites"></a>Requisitos previos
Puede consultar este tutorial para ver los conceptos generales o puede seguirlo exactamente y completar estos pasos.

1. [Crear una conexión](connect-to-sharepoint.md) desde PowerApps a SharePoint.
2. Cree una lista de SharePoint, llamada **AppGen**, que contenga estas columnas.
   
    ![Columnas de ejemplo de SharePoint](./media/customize-layout-sharepoint/list-columns.png)
3. Agregue estos elementos a la lista que acaba de crear.
   
    ![Muestreo de los datos](./media/customize-layout-sharepoint/sample-data.png)
4. [Genere una aplicación automáticamente](app-from-sharepoint.md) basándose en la lista recién creada.
5. En la barra de navegación izquierda, haga clic o pulse en uno de los iconos de la esquina superior derecha para cambiar a la vista en miniatura.
   
    ![Alternancia de las vistas](./media/customize-layout-sharepoint/toggle-view.png)

## <a name="customize-the-gallery"></a>Personalizar la galería
1. En la barra de navegación izquierda, pulse o haga clic en la miniatura superior para asegurarse de que **BrowseScreen1** (PantallaDeExploración1) esté seleccionada.
   
    ![Miniatura de BrowseScreen1](./media/customize-layout-sharepoint/browse-thumbnail.png)
   
    **BrowseScreen1** (PantallaDeExploración1) muestra **AccountID** (IdDeCuenta) y **Title** (Título) para cada elemento en la lista de SharePoint.
   
    ![La pantalla de exploración muestra los títulos y los identificadores de cuenta](./media/customize-layout-sharepoint/browse-accountid.png)
   
    Después, especifique que aparecerá el valor de **OrderDate** de cada elemento en lugar del valor de **AccountID**.
2. Haga clic o pulse en **AccountID** para el primer elemento de la pantalla.
   
    Al hacer clic o pulsar en un elemento de la interfaz de usuario (llamado control), se selecciona y aparece un borde de selección con controladores de tamaño alrededor de ese control.
   
    ![Seleccionar el cuerpo del primer elemento](./media/customize-layout-sharepoint/select-body.png)
3. En el panel derecho, abra la lista **Title1** (Título1) y haga pulse o haga clic en **OrderDate** (FechaDePedido).
   
    ![Mostrar título](./media/customize-layout-sharepoint/bind-data.png)
   
    **BrowseScreen1** refleja el cambio.
   
    ![Diseño con fechas](./media/customize-layout-sharepoint/browse-dates.png)

Para más información sobre las galerías, consulte [Mostrar una lista de elementos en PowerApps](add-gallery.md).

## <a name="set-the-sort-and-search-columns"></a>Establecer las columnas de ordenación y búsqueda
1. Seleccione el control **Gallery** haciendo clic o pulsando en cualquier registro, excepto en el primero.
   
    ![Seleccionar la galería](./media/customize-layout-sharepoint/select-gallery.png)
2. Cerca de la esquina superior izquierda, asegúrese de que la lista de propiedades muestra **Items**.
   
    ![Propiedad Items](./media/customize-layout-sharepoint/items-property.png)
   
    El valor de esta propiedad, que aparece en la barra de fórmulas, determina no solo el origen de los datos que aparecen en la pantalla, sino también las columnas de filtro y ordenación.
   
    Por ejemplo, la barra de fórmulas podría contener esta fórmula de forma predeterminada.
   
    ![Propiedad Items predeterminada](./media/customize-layout-sharepoint/default-items.png)
   
    Con esta fórmula, los usuarios pueden mostrar solamente los registros que comienzan por una o varias letras en la columna **AccountID** (IdDeCuenta).
   
    ![Columnas de búsqueda predeterminadas](./media/customize-layout-sharepoint/default-search.png)
   
    Si un usuario escribe la letra "A" en la barra de búsqueda, la pantalla muestra el registro para Europa. El título de ese registro no coincide con el criterio de búsqueda, pero el identificador de cuenta sí. Más adelante en este procedimiento, cambiaremos la fórmula para filtrar los registros según la columna **Título**.
   
    En cualquier aplicación generada, los usuarios pueden ordenar los registros alfabéticamente en orden ascendente o descendente haciendo clic o pulsando en el botón de ordenación cerca de la esquina superior derecha. Esta fórmula especifica que los registros se ordenarán en función de la columna **AccountID**.
   
    ![Columna de ordenación predeterminada](./media/customize-layout-sharepoint/default-sort.png)
   
    Más adelante en este procedimiento, cambiaremos la fórmula para ordenar los registros según la columna **Title**.
3. En la barra de fórmulas, reemplace ambas instancias de **AccountID** (IdDeCuenta) por **Title** (Título) (incluidas las comillas dobles de la segunda instancia).
   
    La barra de fórmulas ahora contendrá una fórmula que se parece a la de este ejemplo:<br>
    **SortByColumns(Filter(AppGen, StartsWith(Title, TextSearchBox1.Text)), "Title", If(SortDescending1, Descending, Ascending))**
   
    **Nota**: El número que aparece después de **TextSearchBox** podría ser mayor, según las acciones que haya realizado previamente. Sin embargo, la fórmula seguirá funcionando según lo previsto.

## <a name="test-sorting-and-searching"></a>Prueba de ordenación y búsqueda
1. Para abrir el modo de vista previa, presione F5 (o haga clic o pulse en el icono de reproducción situado cerca de la esquina superior derecha).
   
    ![Abrir el modo de vista previa](./media/customize-layout-sharepoint/open-preview.png)
2. Cerca de la esquina superior derecha de **BrowseScreen1**, haga clic o pulse en el botón de ordenación una o varias veces para cambiar el orden alfabético de ordenación entre ascendente y descendente.
   
    ![Probar el botón de ordenación](./media/customize-layout-sharepoint/test-sort.png)
3. En el cuadro de búsqueda, escriba una o varias letras para mostrar solo aquellos registros cuyo título empiece por la letra o letras que escriba.
   
    ![Probar la barra de búsqueda](./media/customize-layout-sharepoint/test-search.png)
4. Quite todo el texto de la barra de búsqueda y cierre el modo de vista previa; para ello, presione F5 (o haga clic o pulse en el icono Cerrar situado *debajo* de la barra de título de PowerApps).
   
    ![Cerrar el modo de vista previa](./media/customize-layout-sharepoint/close-preview.png)

## <a name="change-the-title-of-the-screen"></a>Cambiar el título de la pantalla
1. Haga clic o pulse en el título de la pantalla para seleccionarla.
   
    ![Seleccionar el título de la pantalla](./media/customize-layout-sharepoint/select-screen-title.png)
2. Asegúrese de que la lista muestra **Text**, y, después, escriba el nombre que desee, entre comillas dobles, en la barra de fórmulas.
   
    ![Actualizar el título de la pantalla](./media/customize-layout-sharepoint/update-screen-title.png)
   
    **BrowseScreen1** refleja el cambio.
   
    ![Nuevo título de pantalla](./media/customize-layout-sharepoint/new-screen-title.png)

## <a name="next-steps"></a>Pasos siguientes
* Presione Ctrl+S para guardar los cambios.
* [Personalice los formularios](customize-forms-sharepoint.md) en la aplicación; para ello, muestre, oculte o reordene los campos que muestran los formularios.

