---
title: Personalizar un formulario en una aplicación de lienzo | Microsoft Docs
description: En PowerApps, especifique qué datos se mostrarán en un formulario de aplicación de lienzo, en qué orden y en qué controles.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/17/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1a6465a00f135489d594bad75b8a25942e05dd25
ms.sourcegitcommit: f84095d964fe1fe5cc5290e5edbee284bd768e1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58870940"
---
# <a name="customize-a-canvas-app-form-in-powerapps"></a>Personalizar un formulario de aplicación de lienzo en PowerApps

En una aplicación de lienzo, personalice un control **Mostrar formulario** y un control **Editar formulario** para que muestren los datos más importantes y en el orden más intuitivo para ayudar a los usuarios a comprender y actualizar los datos fácilmente.

Cada formulario consta de una o más tarjetas, cada una de las cuales muestra datos de una columna determinada del origen de datos. Siga los pasos descritos en este tema para especificar qué tarjetas aparecen en un formulario y subir o bajar las tarjetas dentro de un formulario.

Si no está familiarizado con el lienzo pps, consulte [¿cuáles son las aplicaciones de lienzo?](getting-started.md).

## <a name="prerequisites"></a>Requisitos previos

[Generar una aplicación](data-platform-create-app.md) desde Common Data Service y, después, [personalizar la galería](customize-layout-sharepoint.md) en esa aplicación.

## <a name="show-and-hide-cards"></a>Mostrar y ocultar las tarjetas

1. Inicie sesión en [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)y, a continuación, abra la aplicación que ha generado y personalizado.

1. En la barra de navegación izquierda, escriba o pegue **d.** en la barra de búsqueda para filtrar la lista de elementos y, a continuación, seleccione **DetailForm1**.

    > [!div class="mx-imgBorder"]
    > ![Seleccione la pantalla de detalles](./media/customize-forms-sharepoint/select-detailform.png)

1. En la pestaña **Propiedades** del panel del lateral derecho, seleccione **Editar campos** para abrir el panel **Campos**.

    > [!div class="mx-imgBorder"]
    > ![Panel campos abierto](./media/customize-forms-sharepoint/edit-fields.png)

1. Ocultar un campo, como **descripción**, al mantener el mouse sobre él, seleccionando el botón de puntos suspensivos (...) que aparece y, a continuación, seleccionando **quitar**.

    > [!div class="mx-imgBorder"]
    > ![Lista de campos](./media/customize-forms-sharepoint/hide-fields.png)

1. Mostrar un campo seleccionando **Agregar campo**, escriba o pegue las primeras letras del nombre del campo en el cuadro de búsqueda, seleccione la casilla de verificación del campo y, a continuación, seleccione **agregar**.

    > [!div class="mx-imgBorder"]
    > ![Lista de campos](./media/customize-forms-sharepoint/show-field.png)

## <a name="reorder-the-cards"></a>Reordenar las tarjetas

1. En el **campos** panel, arrastre el **nombreCuenta** campo a la parte superior de la lista de campos.

    Las tarjetas en **DetailForm1** reflejar el cambio.

    > [!div class="mx-imgBorder"]
    > ![Tarjetas Reordenadas](./media/customize-forms-sharepoint/reordered-card.png)

1. (opcional) Reordene las demás tarjetas en esta secuencia:

    - Nombre de cuenta
    - Número de empleados
    - Ingresos anuales
    - Teléfono principal
    - Dirección 1: Calle 1
    - Dirección 1: Calle 2
    - Dirección 1: Ciudad
    - Dirección 1: Código Postal

1. En la barra de navegación izquierda, escriba o pegue **Ed** en la búsqueda de la barra y, a continuación, seleccione **EditForm1** para seleccionarlo.

1. Repita los pasos descritos en el procedimiento anterior y en este para que los campos de **EditForm1** coincidan con los de **DetailForm1**.

## <a name="run-the-app"></a>Ejecutar la aplicación

1. En la barra de navegación izquierda, escriba o pegue **Br** en la búsqueda de la barra y, a continuación, seleccione **BrowseScreen1** para seleccionarlo.

1. Para abrir el modo de vista previa, presione F5 (o seleccione el icono de **vista previa** situado cerca de la esquina superior derecha).

    > [!div class="mx-imgBorder"]
    > ![Icono de vista previa](./media/customize-forms-sharepoint/open-preview.png)

1. En la esquina superior derecha, seleccione el icono del signo más para agregar un registro en **EditScreen1**.

    > [!div class="mx-imgBorder"]
    > ![Agregar registro](./media/customize-forms-sharepoint/add-record.png)

1. Agregue los datos que desee y, a continuación, seleccione el icono de marca de verificación en la esquina superior derecha para guardar los cambios y volver a **BrowseScreen1**.

    > [!div class="mx-imgBorder"]
    > ![Guardar registro](./media/customize-forms-sharepoint/save-record.png)

1. Seleccione la flecha para el elemento que acaba de crear para mostrar los detalles de ese elemento en **DetailScreen1**.

    > [!div class="mx-imgBorder"]
    > ![Flecha derecha](./media/customize-forms-sharepoint/right-arrow.png)

1. En la esquina superior derecha, seleccione el icono de edición para actualizar el registro en **EditScreen1**.

    > [!div class="mx-imgBorder"]
    > ![Editar registro](./media/customize-forms-sharepoint/edit-record.png)

1. Cambie la información en uno o varios campos y, a continuación, seleccione la marca de verificación en la esquina superior derecha para guardar los cambios y volver a **DetailScreen1**.

    > [!div class="mx-imgBorder"]
    > ![Guardar cambios](./media/customize-forms-sharepoint/save-record.png)

1. Cerca de la esquina superior derecha, seleccione el icono de Papelera para eliminar el registro que acaba de actualizar y volver a **BrowseScreen1**.

    > [!div class="mx-imgBorder"]
    > ![Eliminar registro](./media/customize-forms-sharepoint/delete-record.png)

1. Cierre el modo de vista previa presionando Esc (o seleccionando el icono Cerrar situado cerca de la esquina superior izquierda).

## <a name="next-steps"></a>Pasos siguientes

- [Guardar y publicar](save-publish-app.md) la aplicación.
- [Personalizar una tarjeta](customize-card.md) en la aplicación.