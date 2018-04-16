---
title: Tutorial para personalizar una galería | Microsoft Docs
description: En este tutorial, personalizará la pantalla de exploración predeterminada, incluida la galería, de una aplicación generada en PowerApps.
services: ''
suite: powerapps
documentationcenter: na
author: AFTOwen
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/11/2018
ms.author: anneta
ms.openlocfilehash: 30ec6be11b40e01dddfe09cf0ac8af0ed3a8a437
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="tutorial-customize-a-gallery-in-powerapps"></a>Tutorial: Personalización de una galería en PowerApps
En este tutorial, personalizará la pantalla de exploración predeterminada, incluida la galería, de una aplicación generada en PowerApps. Puede administrar los datos mediante la aplicación predeterminada sin personalizarla, pero será mucho más eficaz y fácil de usar si realiza estos cambios:

> [!div class="checklist"]
> * Cambiar el diseño
> * Cambiar los datos que aparecen
> * Establecer las columnas para filtrar y ordenar
> * Probar el filtrado y la ordenación
> * Cambiar el título
> * Mostrar una barra de desplazamiento

Este tutorial comienza con una aplicación generada a partir de [Common Data Service for Apps](../common-data-service/data-platform-intro.md), pero los mismos conceptos se aplican a las aplicaciones generadas a partir de SharePoint, Excel y otros orígenes de datos. 

Si no tiene una licencia para PowerApps, puede [registrarse gratuitamente](../signup-for-powerapps.md).

## <a name="prerequisites"></a>Requisitos previos
Antes de empezar este tutorial, [genere una aplicación](data-platform-create-app.md) desde Common Data Service for Apps.

## <a name="open-the-generated-app"></a>Abrir la aplicación generada
1. Inicie sesión en [PowerApps](https://web.powerapps.com) y pulse o haga clic en **Aplicaciones** cerca del borde izquierdo.

    ![Página principal de PowerApps](./media/customize-layout-sharepoint/sign-in.png)

1. Busque la aplicación que ha generado y, después, pulse o haga clic en el icono de puntos suspensivos (**...**) cerca del borde derecho.

    ![Lista de aplicaciones](./media/customize-layout-sharepoint/open-for-edit.png)

1. En el menú que aparece, pulse o haga clic en la opción para editar la aplicación. 

## <a name="customize-the-gallery"></a>Personalizar la galería
1. En la pantalla de exploración, pulse o haga clic en cualquier elemento, menos el primero, de la lista de cuentas.

    En este paso se selecciona el control **Galería**, en el que se muestra la lista de cuentas.

    ![Galería seleccionada](./media/customize-layout-sharepoint/select-gallery.png)

1. En el panel de la derecha, pulse o haga clic en **Cuentas** a la derecha de la etiqueta **Datos**.

    ![Abrir el panel **Datos**](./media/customize-layout-sharepoint/open-data-pane.png)

1. En el panel **Datos**, pulse o haga clic en la flecha hacia abajo para abrir la lista de opciones bajo **Diseño**.

    ![Mostrar las opciones de diseño](./media/customize-layout-sharepoint/show-layouts.png)

1. En la lista de opciones, pulse o haga clic en la opción que muestra solo un título.

    ![Seleccionar el diseño de solo título](./media/customize-layout-sharepoint/choose-layout.png)

1. En el panel **Datos**, pulse o haga clic en la flecha hacia abajo para abrir la lista de opciones para el título.

    ![Seleccionar el diseño de solo título](./media/customize-layout-sharepoint/show-title-options.png)

1. En la lista de opciones, pulse o haga clic en **nombre** para mostrar esos datos en el control **Galería**.

    ![Galería final](./media/customize-layout-sharepoint/final-gallery.png)


## <a name="set-the-sort-and-search-columns"></a>Establecer las columnas de ordenación y búsqueda
1. Seleccione el control **Galería** como se describe en la sección anterior.

    ![Seleccionar la galería](./media/customize-layout-sharepoint/select-gallery-title.png)

2. Cerca de la esquina superior izquierda, asegúrese de que la lista de propiedades muestra **Items**.

    ![Propiedad Items](./media/customize-layout-sharepoint/items-property.png)

    El valor de esta propiedad aparece en la barra de fórmulas y determina no solo el origen de datos de la galería, sino también las columnas de filtro y ordenación.

1. En la barra de fórmulas, reemplace ambas instancias de **emailaddress1** por **nombre** y conserve las marcas de comillas dobles que rodean a cada instancia.

    La fórmula debe coincidir con este ejemplo:

    ![Fórmula para la propiedad Items](./media/customize-layout-sharepoint/items-value.png)

    La primera instancia de **nombre** especifica que el usuario puede filtrar la lista para mostrar solo los registros para los que el nombre de cuenta contiene texto que el usuario ha escrito en la barra de búsqueda. La segunda instancia de **nombre** especifica que el usuario puede ordenar la lista alfabéticamente por nombre de cuenta. Para obtener más información sobre estas y otras funciones, vea la [referencia de fórmulas](formula-reference.md).

## <a name="test-sorting-and-searching"></a>Prueba de ordenación y búsqueda
1. Para abrir el modo de vista previa, presione F5 (o haga clic o pulse en el icono de reproducción situado cerca de la esquina superior derecha).

    ![Abrir el modo de vista previa](./media/customize-layout-sharepoint/open-preview.png)

1. Cerca de la esquina superior derecha de la pantalla de exploración, pulse o haga clic en el icono de ordenación una o varias veces para cambiar el orden alfabético de ordenación entre ascendente y descendente.

    ![Probar el icono de ordenación](./media/customize-layout-sharepoint/sort-button.png)

1. En el cuadro de búsqueda, escriba **k** para mostrar únicamente las cuentas en las que el nombre contiene la letra que ha escrito.

    ![Probar la barra de búsqueda](./media/customize-layout-sharepoint/test-filter.png)

1. Quite todo el texto de la barra de búsqueda y cierre el modo de vista previa; para ello, presione F5 (o haga clic o pulse en el icono Cerrar situado *debajo* de la barra de título de PowerApps).

## <a name="change-the-title-of-the-screen"></a>Cambiar el título de la pantalla
1. Haga clic o pulse en el título de la pantalla para seleccionarla.

    ![Seleccionar el título de la pantalla](./media/customize-layout-sharepoint/select-title.png)

1. Asegúrese de que la lista de propiedades muestra **Text**, y, después, escriba **Examinar**, entre comillas dobles, en la barra de fórmulas.

    ![Actualizar el título de la pantalla](./media/customize-layout-sharepoint/change-screen-title.png)

    La pantalla refleja el cambio.

    ![Nuevo título de pantalla](./media/customize-layout-sharepoint/new-screen-title.png)

## <a name="show-a-scroll-bar"></a>Mostrar una barra de desplazamiento
Si es posible que los usuarios no tengan pantallas táctiles o ruedas del mouse, configure el control **Galería** para que muestre una barra cuando el usuario mantenga el puntero sobre ella con el ratón. De este modo, los usuarios pueden mostrar todas las cuentas incluso si no se pueden mostrar a la vez en la pantalla.

1. Seleccione el control **Galería** como se describe en el primer procedimiento.

    ![Seleccionar la galería](./media/customize-layout-sharepoint/select-gallery-sorted.png)

1. En la pestaña **Galería**, pulse o haga clic en **Mostrar barra de desplazamiento** y confirme que el valor de la propiedad ha cambiado a **true**. 

    ![Mostrar barra de desplazamiento](./media/customize-layout-sharepoint/show-scrollbar.png)

## <a name="next-steps"></a>Pasos siguientes
En este tutorial, ha personalizado el control **Galería** y el título de la pantalla de exploración predeterminada de una aplicación generada. También puede personalizar las pantallas predeterminadas para mostrar detalles y crear o actualizar cuentas. Esas pantallas contienen controles **Mostrar formulario** y **Editar formulario**, y se pueden cambiar (por ejemplo) los tipos de datos que muestran y en qué orden.

> [!div class="nextstepaction"]
> [Personalizar formularios](customize-forms-sharepoint.md)