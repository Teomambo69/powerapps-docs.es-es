---
title: 'Tutorial: personalización de una galería en una aplicación generada | Microsoft Docs'
description: En este tutorial, personalizará los datos que aparecen en la galería y otros elementos de una aplicación que se generó automáticamente en Power apps.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: tutorial
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/06/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 02d6e3b7a3dc18ab4c7d4d3d5f510b6c3bbd227a
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731720"
---
# <a name="tutorial-customize-a-gallery-in-power-apps"></a>Tutorial: personalización de una galería en Power apps

En este tutorial, personalizará una lista de registros, denominada Galería, y realizará otros cambios en una aplicación que se generó automáticamente en Microsoft Power apps. Los usuarios pueden administrar datos de la aplicación incluso si no realiza estos cambios, pero la aplicación será más fácil de usar si se personaliza de acuerdo con las necesidades de su organización.

Por ejemplo, la galería para este tutorial coincide con este gráfico de forma predeterminada. La dirección de correo electrónico destaca más que otros tipos de datos, y los usuarios pueden ordenar y filtrar la galería en base a texto en dicha dirección:

![Galería predeterminada](./media/customize-layout-sharepoint/gallery-before.png)

Sin embargo, los usuarios podrían estar más interesados en el nombre de cuenta más que en la dirección de correo electrónico, por lo que deberá volver a configurar la galería para que resalte, ordene y filtre en función de los datos clave de su organización. Además, podrá cambiar el título de la pantalla predeterminada para diferenciarlo de las otras pantallas en la aplicación.

![Galería final](./media/customize-layout-sharepoint/gallery-after.png)

También agregará una barra de desplazamiento para que los usuarios que no tienen pantallas táctiles o ruedas de mouse puedan examinar toda la galería.

> [!div class="checklist"]
> * Cambio del diseño de la galería
> * Cambio del tipo de datos que aparecen en la galería
> * Cambio de las columnas que los usuarios pueden utilizar para ordenar y buscar los datos
> * Cambio del título de pantalla
> * Mostrar una barra de desplazamiento

Este tutorial comienza con una aplicación que se generó a partir de un origen de datos específico. Sin embargo, los mismos conceptos se aplican a cualquier aplicación que se genere en Power Apps, ya sea a partir de una lista de SharePoint, una tabla de Excel u otro origen de datos.

Si no se ha registrado en Power Apps, [Regístrese gratuitamente](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) antes de empezar.

## <a name="prerequisites"></a>Requisitos previos

[Genere una aplicación](data-platform-create-app.md) a partir de la entidad **accounts** de Common Data Service.

## <a name="open-the-generated-app"></a>Abrir la aplicación generada

1. Inicie sesión en [Power apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)y, después, seleccione **aplicaciones** cerca del borde izquierdo.

1. Busque la aplicación que ha generado, seleccione su icono de puntos suspensivos ( **...** ) y, a continuación, seleccione **Editar**.

    ![Abrir la aplicación para editarla](./media/customize-layout-sharepoint/open-app.png)

1. Si aparece el cuadro de diálogo **Bienvenido a Power apps Studio** , seleccione **omitir**.

## <a name="change-the-layout"></a>Cambiar el diseño

1. En el panel de navegación izquierdo, seleccione **BrowseGallery1**.

    Cuando se haya seleccionado la galería, aparecerá un cuadro de selección con indicadores alrededor.

    ![Seleccionar la galería](media/customize-layout-sharepoint/select-gallery-1.png)

1. En la pestaña **propiedades** del panel derecho, abra la lista de opciones en **diseño**y, a continuación, seleccione la opción que muestra solo un título.

    ![Seleccionar el diseño de solo título](./media/customize-layout-sharepoint/choose-layout.png)

1. Junto a **campos**, seleccione **Editar**y, a continuación, seleccione la flecha hacia abajo del cuadro título.

    El nombre de este control finalizará en un valor numérico, como **Título1**, pero el número puede diferir en función de otras acciones que haya realizado.

1. En la lista de opciones, seleccione **nombre de cuenta**y, a continuación, cierre el panel **datos** .

    La galería muestra el nombre de cada cuenta.

    ![Galería final](./media/customize-layout-sharepoint/final-gallery.png)

## <a name="change-sort-and-search-columns"></a>Cambiar el orden y buscar en columnas

1. Seleccione la galería como se describe en la sección anterior.

    ![Seleccionar la galería](./media/customize-layout-sharepoint/select-gallery-title.png)

1. Cerca de la esquina superior izquierda, confirme que la lista de propiedades muestra **Elementos**.

    ![Propiedad Elementos](./media/customize-layout-sharepoint/items-property.png)

    El valor de esta propiedad aparece en la barra de fórmulas. Establezca esta propiedad para especificar no solo el origen de datos de la galería, sino también las columnas mediante las cuales los usuarios pueden ordenar y buscar los datos.

1. Copie esta fórmula y, a continuación, péguela en la barra de fórmulas.

    ```SortByColumns(Search(Accounts, TextSearchBox1.Text, "name"), "name", If(SortDescending1, Descending, Ascending))```

    Con esta fórmula, se asegura de que:

    * Si un usuario escribe uno o varios caracteres en la barra de búsqueda, la galería muestra sólo los nombres de cuenta que contengan el texto escrito por el usuario.
    * Si un usuario selecciona el icono de orden, la galería se ordena alfabéticamente por nombre de cuenta en orden ascendente o descendente, según la cantidad de veces que el usuario seleccione el icono.

     Para obtener más información sobre estas y otras funciones, vea la [referencia de fórmulas](formula-reference.md).

### <a name="test-sorting-and-searching"></a>Prueba de ordenación y búsqueda

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

## <a name="show-a-scrollbar"></a>Mostrar una barra de desplazamiento

Si es posible que los usuarios no tengan pantallas táctiles ni ruedas del mouse, configure la galería para que muestre una barra de desplazamiento cuando el usuario mantenga el puntero sobre ella. De este modo, los usuarios pueden mostrar todas las cuentas incluso si no se pueden mostrar a la vez en la pantalla.

1. Seleccione la galería como se describe en el primer procedimiento.

    ![Seleccionar la galería](./media/customize-layout-sharepoint/select-gallery-sorted.png)

1. Establezca la propiedad **Mostrar ScrollBar** de la galería en **true**.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha personalizado la galería y realizado otros cambios en la pantalla predeterminada para examinar registros en una aplicación generada. También puede personalizar las pantallas predeterminadas para mostrar detalles y crear o actualizar cuentas. Como la pantalla de exploración contiene una galería, las otras dos pantallas en la aplicación contienen formularios. Se pueden cambiar, por ejemplo, qué tipos de datos de los formularios se muestran y en qué orden.

> [!div class="nextstepaction"]
> [Personalizar formularios](customize-forms-sharepoint.md)
