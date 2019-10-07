---
title: Personalizar un formulario en una aplicación de lienzo | Microsoft Docs
description: En PowerApps, especifique qué datos se mostrarán en un formulario de aplicación de lienzo, en qué orden y en qué controles.
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
ms.openlocfilehash: 67e7e0074259731bb1d3c50474e8020e3f4fcf1b
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993174"
---
# <a name="customize-a-canvas-app-form-in-powerapps"></a>Personalizar un formulario de aplicación de lienzo en PowerApps

En una aplicación de lienzo, personalice un control **Mostrar formulario** y un control **Editar formulario** para que muestren los datos más importantes y en el orden más intuitivo para ayudar a los usuarios a comprender y actualizar los datos fácilmente.

Cada formulario consta de una o más tarjetas, cada una de las cuales muestra datos de una columna determinada del origen de datos. Siga los pasos descritos en este tema para especificar qué tarjetas aparecen en un formulario y subir o bajar las tarjetas dentro de un formulario.

Si no está familiarizado con Canvas-PPS, consulte [¿Qué son las aplicaciones de lienzo?](getting-started.md).

## <a name="prerequisites"></a>Requisitos previos

[Generar una aplicación](data-platform-create-app.md) desde Common Data Service y, después, [personalizar la galería](customize-layout-sharepoint.md) en esa aplicación.

## <a name="show-and-hide-cards"></a>Mostrar y ocultar las tarjetas

1. Inicie sesión en [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)y, a continuación, abra la aplicación que ha generado y personalizado.

1. En la barra de navegación izquierda, escriba o pegue **D** en la barra de búsqueda para filtrar la lista de elementos y, a continuación, seleccione **DetailForm1**.

    > [!div class="mx-imgBorder"]
    > @no__t pantalla de detalles de 0Select @ no__t-1

1. En la pestaña **Propiedades** del panel del lateral derecho, seleccione **Editar campos** para abrir el panel **Campos**.

    > [!div class="mx-imgBorder"]
    > @no__t el panel de campos de 0Open @ no__t-1

1. Oculte un campo, como la **Descripción**, manteniendo el puntero sobre él, seleccionando los puntos suspensivos (...) que aparece y, a continuación, seleccionando **quitar**.

    > [!div class="mx-imgBorder"]
    > ![List de campos @ no__t-1

1. Para mostrar un campo, seleccione **Agregar campo**, escriba o pegue las primeras letras del nombre del campo en el cuadro de búsqueda, active la casilla del campo y, a continuación, seleccione **Agregar**.

    > [!div class="mx-imgBorder"]
    > ![List de campos @ no__t-1

## <a name="reorder-the-cards"></a>Reordenar las tarjetas

1. En el panel **campos** , arrastre el campo **nombre de cuenta** hasta la parte superior de la lista de campos.

    Las tarjetas de **DetailForm1** reflejan el cambio.

    > [!div class="mx-imgBorder"]
    > @no__t-tarjetas 0Reordered @ no__t-1

1. opta Reordene las otras tarjetas a esta secuencia:

    - Nombre de cuenta
    - Número de empleados
    - Ingresos anuales
    - Teléfono principal
    - Dirección 1: Calle 1
    - Dirección 1: Calle 2
    - Dirección 1: Ciudad
    - Dirección 1: Código postal

1. En la barra de navegación izquierda, escriba o pegue **Ed** en la barra de búsqueda y, a continuación, seleccione **EditForm1** para seleccionarlo.

1. Repita los pasos descritos en el procedimiento anterior y en este para que los campos de **EditForm1** coincidan con los de **DetailForm1**.

## <a name="run-the-app"></a>Ejecutar la aplicación

1. En la barra de navegación izquierda, escriba o pegue **br** en la barra de búsqueda y, a continuación, seleccione **BrowseScreen1** para seleccionarlo.

1. Para abrir el modo de vista previa, presione F5 (o seleccione el icono de **vista previa** situado cerca de la esquina superior derecha).

    > [!div class="mx-imgBorder"]
    > @no__t: icono de 0Preview @ no__t-1

1. En la esquina superior derecha, seleccione el icono de signo más para agregar un registro en **EditScreen1**.

    > [!div class="mx-imgBorder"]
    > ![Add registro @ no__t-1

1. Agregue los datos que desee y, a continuación, seleccione el icono de marca de verificación en la esquina superior derecha para guardar los cambios y volver a **BrowseScreen1**.

    > [!div class="mx-imgBorder"]
    > ![Save registro @ no__t-1

1. Seleccione la flecha del elemento que acaba de crear para mostrar los detalles de ese elemento en **DetailScreen1**.

    > [!div class="mx-imgBorder"]
    > @no__t: flecha 0Right @ no__t-1

1. En la esquina superior derecha, seleccione el icono de edición para actualizar el registro en **EditScreen1**.

    > [!div class="mx-imgBorder"]
    > ![Edit registro @ no__t-1

1. Cambie la información de uno o varios campos y, a continuación, active la marca de verificación situada en la esquina superior derecha para guardar los cambios y volver a **DetailScreen1**.

    > [!div class="mx-imgBorder"]
    > ![Save cambia @ no__t-1

1. Cerca de la esquina superior derecha, seleccione el icono de la papelera para eliminar el registro que acaba de actualizar y volver a **BrowseScreen1**.

    > [!div class="mx-imgBorder"]
    > ![Delete registro @ no__t-1

1. Cierre el modo de vista previa presionando ESC (o seleccionando el icono cerrar situado cerca de la esquina superior izquierda).

## <a name="next-steps"></a>Pasos siguientes

- [Guardar y publicar](save-publish-app.md) la aplicación.
- [Personalizar una tarjeta](customize-card.md) en la aplicación.