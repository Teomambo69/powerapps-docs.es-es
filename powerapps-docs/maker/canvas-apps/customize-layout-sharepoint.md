---
title: 'Tutorial: personalización de una galería en una aplicación generada | Microsoft Docs'
description: En este tutorial, se personalizan los datos que aparecen en la galería y otros elementos de una aplicación que se generó automáticamente en PowerApps.
author: AFTOwen
ms.service: powerapps
ms.topic: tutorial
ms.component: canvas
ms.date: 04/24/2018
ms.author: anneta
ms.openlocfilehash: 6206d520e8bb07c0919f482700c1af861e41109d
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="tutorial-customize-a-gallery-in-powerapps"></a>Tutorial: Personalización de una galería en PowerApps
En este tutorial, podrá personalizar la galería y realizar otros cambios en una aplicación que se generó automáticamente en Microsoft PowerApps. Los usuarios pueden administrar datos de la aplicación incluso si no realiza estos cambios, pero la aplicación será más fácil de usar si se personaliza de acuerdo con las necesidades de su organización:

> [!div class="checklist"]
> * Cambio del diseño de la galería
> * Cambio del tipo de datos que aparecen en la galería
> * Cambio de las columnas que los usuarios pueden utilizar para ordenar y buscar los datos
> * Cambio del título de pantalla
> * Mostrar una barra de desplazamiento

Este tutorial comienza con una aplicación que se generó a partir de un origen de datos específico. Sin embargo, se aplican los mismos conceptos a cualquier aplicación que se genere en PowerApps desde una lista de SharePoint, una tabla de Excel u otro origen de datos. 

Si no tiene una licencia para PowerApps, puede [registrarse gratuitamente](../signup-for-powerapps.md).

## <a name="prerequisites"></a>Requisitos previos
Puede revisar este tema para obtener solo los conceptos generales, o bien puede seguir cada paso si primero [genera esta aplicación](data-platform-create-app.md).

## <a name="open-the-generated-app"></a>Abrir la aplicación generada
1. Inicie sesión en [PowerApps](https://web.powerapps.com) y después, seleccione **Aplicaciones** cerca del borde izquierdo.

    ![Página principal de PowerApps](./media/customize-layout-sharepoint/sign-in.png)

1. Busque la aplicación que ha generado, seleccione su icono de puntos suspensivos (**...** ) y, a continuación, seleccione **Editar**.

## <a name="change-the-layout"></a>Cambiar el diseño
1. En la pantalla de exploración, seleccione la galería haciendo clic o pulsando en cualquier elemento, excepto el primero en la lista de cuentas.

    Cuando se haya seleccionado la galería, aparecerá un cuadro de selección con indicadores alrededor.

    ![Galería seleccionada](./media/customize-layout-sharepoint/select-gallery.png)

1. Cerca del borde derecho, seleccione **Cuentas** para abrir el panel **Datos**.

    ![Abrir el panel **Datos**](./media/customize-layout-sharepoint/open-data-pane.png)

1. En el panel **Datos**, abra la lista de opciones en **Diseño**.

    ![Mostrar las opciones de diseño](./media/customize-layout-sharepoint/show-layouts.png)

1. En la lista de opciones, seleccione la opción que muestra solo un título.

    ![Seleccionar el diseño de solo título](./media/customize-layout-sharepoint/choose-layout.png)

1. En el panel **Datos**, abra la lista de opciones para el título.

    ![Seleccionar el diseño de solo título](./media/customize-layout-sharepoint/show-title-options.png)

1. En la lista de opciones, seleccione **Account name (name)** (Nombre de cuenta [cuenta]) y, a continuación, cierre el panel **Datos**.

    La galería muestra el nombre de cada cuenta.

    ![Galería final](./media/customize-layout-sharepoint/final-gallery.png)

## <a name="change-the-sort-and-search-columns"></a>Cambio de columnas de ordenación y búsqueda
1. Seleccione la galería como se describe en la sección anterior.

    ![Seleccionar la galería](./media/customize-layout-sharepoint/select-gallery-title.png)

2. Cerca de la esquina superior izquierda, confirme que la lista de propiedades muestra **Elementos**.

    ![Propiedad Items](./media/customize-layout-sharepoint/items-property.png)

    El valor de esta propiedad aparece en la barra de fórmulas. Establezca esta propiedad para especificar no solo el origen de datos de la galería, sino también las columnas mediante las cuales los usuarios pueden ordenar y buscar los datos.

1. Copie esta fórmula y, a continuación, péguela en la barra de fórmulas.

    ```SortByColumns(Search(Accounts, TextSearchBox1.Text, "name"), "name", If(SortDescending1, Descending, Ascending))```

    Con esta fórmula, se asegura de que:

    - Si un usuario escribe uno o varios caracteres en la barra de búsqueda, la galería muestra sólo los nombres de cuenta que contengan el texto escrito por el usuario.
    - Si un usuario selecciona el icono de orden, la galería se ordena alfabéticamente por nombre de cuenta en orden ascendente o descendente, según la cantidad de veces que el usuario seleccione el icono.

    Para obtener más información sobre estas y otras funciones, vea la [referencia de fórmulas](formula-reference.md).

## <a name="test-sorting-and-searching"></a>Prueba de ordenación y búsqueda
1. Abra el modo de vista previa presionando F5 (o seleccionado el botón de reproducción cerca de la esquina superior derecha).

    ![Abrir el modo de vista previa](./media/customize-layout-sharepoint/open-preview.png)

1. Cerca de la esquina superior derecha de la pantalla de exploración, seleccione el icono de ordenación una o varias veces para cambiar el orden alfabético de ordenación entre ascendente y descendente.

    ![Probar el icono de ordenación](./media/customize-layout-sharepoint/sort-button.png)

1. En el cuadro de búsqueda, escriba **k** para mostrar solo los nombres que contengan la letra que ha escrito.

    ![Probar la barra de búsqueda](./media/customize-layout-sharepoint/test-filter.png)

1. Quite todo el texto de la barra de búsqueda y cierre el modo de vista previa; para ello, presione Esc (o seleccione el icono de cerrar cerca de la esquina superior derecha).

## <a name="change-the-screen-title"></a>Cambio del título de pantalla
1. Seleccione el título de la pantalla haciendo clic o pulsando en él.

    ![Seleccionar el título de la pantalla](./media/customize-layout-sharepoint/select-title.png)

1. Asegúrese de que la lista de propiedades muestra **Texto** y luego, en la barra de fórmulas, reemplace **Cuentas** por **Examinar** (manteniendo las comillas dobles).

    ![Actualizar el título de la pantalla](./media/customize-layout-sharepoint/change-screen-title.png)

    La pantalla refleja el cambio.

    ![Nuevo título de pantalla](./media/customize-layout-sharepoint/new-screen-title.png)

## <a name="show-a-scroll-bar"></a>Mostrar una barra de desplazamiento
Si es posible que los usuarios no tengan pantallas táctiles o ruedas del mouse, configure la galería para que muestre una barra de desplazamiento cuando el usuario mantenga el puntero sobre ella. De este modo, los usuarios pueden mostrar todas las cuentas incluso si no se pueden mostrar a la vez en la pantalla.

1. Seleccione la galería como se describe en el primer procedimiento.

    ![Seleccionar la galería](./media/customize-layout-sharepoint/select-gallery-sorted.png)

1. En la pestaña **Galería**, seleccione **Mostrar barra de desplazamiento** y confirme que el valor de la propiedad ha cambiado a **true**. 

    ![Mostrar barra de desplazamiento](./media/customize-layout-sharepoint/show-scrollbar.png)

## <a name="next-steps"></a>Pasos siguientes
En este tutorial, ha personalizado la galería y realizado otros cambios en la pantalla predeterminada para examinar registros en una aplicación generada. También puede personalizar las pantallas predeterminadas para mostrar detalles y crear o actualizar cuentas. Como la pantalla de exploración contiene una galería, las otras dos pantallas en la aplicación contienen formularios. Se pueden cambiar, por ejemplo, qué tipos de datos de los formularios se muestran y en qué orden.

> [!div class="nextstepaction"]
> [Personalizar formularios](customize-forms-sharepoint.md)