---
title: Personalizar un formulario en una aplicación de lienzo | Microsoft Docs
description: En Power Apps, especifique los datos que se van a mostrar en un formulario de canvas-App, en el que se deben mostrar y en qué controles.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/17/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6732dabea803cd7680ef618e4e8d1c4e88f7afe5
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678635"
---
# <a name="customize-a-canvas-app-form-in-powerapps"></a>Personalizar un formulario de aplicación de lienzo en PowerApps

En una aplicación de lienzo, personalice un control **Mostrar formulario** y un control **Editar formulario** para que muestren los datos más importantes y en el orden más intuitivo para ayudar a los usuarios a comprender y actualizar los datos fácilmente.

Cada formulario consta de una o más tarjetas, cada una de las cuales muestra datos de una columna determinada del origen de datos. Siga los pasos descritos en este tema para especificar qué tarjetas aparecen en un formulario y subir o bajar las tarjetas dentro de un formulario.

Si no está familiarizado con Canvas-PPS, consulte [¿Qué son las aplicaciones de lienzo?](getting-started.md).

## <a name="prerequisites"></a>Requisitos previos

[Generar una aplicación](data-platform-create-app.md) desde Common Data Service y, después, [personalizar la galería](customize-layout-sharepoint.md) en esa aplicación.

## <a name="show-and-hide-cards"></a>Mostrar y ocultar las tarjetas

1. Inicie sesión en [PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)y, a continuación, abra la aplicación que ha generado y personalizado.

1. En la barra de navegación izquierda, escriba o pegue **D** en la barra de búsqueda para filtrar la lista de elementos y, a continuación, seleccione **DetailForm1**.

    > [!div class="mx-imgBorder"]
    > ![seleccionar pantalla de detalles](./media/customize-forms-sharepoint/select-detailform.png)

1. En la pestaña **Propiedades** del panel del lateral derecho, seleccione **Editar campos** para abrir el panel **Campos**.

    > [!div class="mx-imgBorder"]
    > ![panel abrir campos](./media/customize-forms-sharepoint/edit-fields.png)

1. Oculte un campo, como la **Descripción**, manteniendo el puntero sobre él, seleccionando los puntos suspensivos (...) que aparece y, a continuación, seleccionando **quitar**.

    > [!div class="mx-imgBorder"]
    > ![lista de campos](./media/customize-forms-sharepoint/hide-fields.png)

1. Para mostrar un campo, seleccione **Agregar campo**, escriba o pegue las primeras letras del nombre del campo en el cuadro de búsqueda, active la casilla del campo y, a continuación, seleccione **Agregar**.

    > [!div class="mx-imgBorder"]
    > ![lista de campos](./media/customize-forms-sharepoint/show-field.png)

## <a name="reorder-the-cards"></a>Reordenar las tarjetas

1. En el panel **campos** , arrastre el campo **nombre de cuenta** hasta la parte superior de la lista de campos.

    Las tarjetas de **DetailForm1** reflejan el cambio.

    > [!div class="mx-imgBorder"]
    > ![las tarjetas reordenadas](./media/customize-forms-sharepoint/reordered-card.png)

1. opta Reordene las otras tarjetas a esta secuencia:

    - Nombre de cuenta
    - Número de empleados
    - Ingresos anuales
    - Teléfono principal
    - Dirección 1: Calle 1
    - Dirección 1: calle 2
    - Dirección 1: Ciudad
    - Dirección 1: Código postal

1. En la barra de navegación izquierda, escriba o pegue **Ed** en la barra de búsqueda y, a continuación, seleccione **EditForm1** para seleccionarlo.

1. Repita los pasos descritos en el procedimiento anterior y en este para que los campos de **EditForm1** coincidan con los de **DetailForm1**.

## <a name="run-the-app"></a>Ejecutar la aplicación

1. En la barra de navegación izquierda, escriba o pegue **br** en la barra de búsqueda y, a continuación, seleccione **BrowseScreen1** para seleccionarlo.

1. Para abrir el modo de vista previa, presione F5 (o seleccione el icono de **vista previa** situado cerca de la esquina superior derecha).

    > [!div class="mx-imgBorder"]
    > ![icono de vista previa](./media/customize-forms-sharepoint/open-preview.png)

1. En la esquina superior derecha, seleccione el icono de signo más para agregar un registro en **EditScreen1**.

    > [!div class="mx-imgBorder"]
    > ![agregar registro](./media/customize-forms-sharepoint/add-record.png)

1. Agregue los datos que desee y, a continuación, seleccione el icono de marca de verificación en la esquina superior derecha para guardar los cambios y volver a **BrowseScreen1**.

    > [!div class="mx-imgBorder"]
    > ![guardar](./media/customize-forms-sharepoint/save-record.png) de registro

1. Seleccione la flecha del elemento que acaba de crear para mostrar los detalles de ese elemento en **DetailScreen1**.

    > [!div class="mx-imgBorder"]
    > ![flecha derecha](./media/customize-forms-sharepoint/right-arrow.png)

1. En la esquina superior derecha, seleccione el icono de edición para actualizar el registro en **EditScreen1**.

    > [!div class="mx-imgBorder"]
    > ![editar](./media/customize-forms-sharepoint/edit-record.png) de registro

1. Cambie la información de uno o varios campos y, a continuación, active la marca de verificación situada en la esquina superior derecha para guardar los cambios y volver a **DetailScreen1**.

    > [!div class="mx-imgBorder"]
    > ![guardar los cambios](./media/customize-forms-sharepoint/save-record.png)

1. Cerca de la esquina superior derecha, seleccione el icono de la papelera para eliminar el registro que acaba de actualizar y volver a **BrowseScreen1**.

    > [!div class="mx-imgBorder"]
    > ![eliminar registro](./media/customize-forms-sharepoint/delete-record.png)

1. Cierre el modo de vista previa presionando ESC (o seleccionando el icono cerrar situado cerca de la esquina superior izquierda).

## <a name="next-steps"></a>Pasos siguientes

- [Guardar y publicar](save-publish-app.md) la aplicación.
- [Personalizar una tarjeta](customize-card.md) en la aplicación.