---
title: Mostrar, editar o agregar un registro en una aplicación de lienzo | Microsoft Docs
description: Utilice un formulario de aplicación de lienzo para mostrar, editar o agregar un registro de una tabla en el origen de datos.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/06/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 37b7117f599c29f886da3cafeb158db145ad1364
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74724908"
ms.PowerAppsDecimalTransform: true
---
# <a name="show-edit-or-add-a-record-in-a-canvas-app"></a>Mostrar, editar o agregar un registro en una aplicación de lienzo

En una aplicación de lienzo, agregue y configure un control **[Mostrar](controls/control-form-detail.md)** formulario para mostrar todos los campos de un registro, también puede Agregar y configurar un control **[Editar](controls/control-form-detail.md)** formulario para editar cualquier campo de un registro, agregar un registro y guardar los cambios de nuevo en un origen de datos.

## <a name="prerequisites"></a>Requisitos previos

- Obtenga información sobre cómo [Agregar y configurar un control](add-configure-controls.md) en Power apps.
- Descargue [este archivo de Excel](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx), que contiene datos de ejemplo para este tutorial.
- Cargue el archivo de Excel en una [cuenta de almacenamiento en la nube](connections/cloud-storage-blob-connections.md), como OneDrive para la Empresa.
- Cree o abra una aplicación para teléfonos y [agregue una conexión](add-data-connection.md) a la tabla **FlooringEstimates** en el archivo de Excel.

    Puede Agregar un formulario a una aplicación de Tablet PC, pero no coincidirá con este tema porque el formulario tendrá tres columnas de forma predeterminada.

- Si abre una aplicación existente, [agregue una pantalla](add-screen-context-variables.md) a ella.

## <a name="add-a-form-and-show-data"></a>Agregar un formulario y mostrar datos
1. En una pantalla en blanco, agregue un control **[lista](controls/control-drop-down.md)** desplegable y asígnele el nombre **ChooseProduct**.

    > [!NOTE]
   > Si no está seguro de cómo agregar un control, cambiar su nombre o establecer una propiedad, consulte [Adición y configuración de un control en PowerApps](add-configure-controls.md).

1. En la pestaña **propiedades** del panel derecho, establezca **elementos** en `FlooringEstimates` y **valor** en `Name`.

    ![Establecer la propiedad elementos del formulario](./media/add-form/items-property.png)

    La lista muestra nombres de productos para el suelo del origen de datos.

1. Agregue un control **Editar** formulario, muévalo debajo de **ChooseProduct**y, a continuación, cambie el tamaño del formulario para que cubra la mayor parte de la pantalla.

    ![Agregar un formulario](./media/add-form/add-a-form.png)

    > [!NOTE]
   > En este tema se describe el control formulario de **edición** , pero los principios similares se aplican al control **Mostrar** formulario.

1. Establezca la propiedad **[DataSource](controls/control-form-detail.md)** del formulario en **FlooringEstimates** y su propiedad **[Item](controls/control-form-detail.md)** en esta fórmula:

    `First(Filter(FlooringEstimates; Name=ChooseProduct.Selected.Value))`

   Esta fórmula especifica que, cuando termine de configurar el formulario, aparecerá el registro que el usuario selecciona en **ChooseProduct**.

1. En la pestaña **propiedades** del panel derecho, seleccione **Editar campos**.

    ![Editar campos](./media/add-form/edit-fields.png)

1. En el panel **Campos**, seleccione **Agregar campo**, marque la casilla de cada campo y, luego, seleccione **Agregar**.

    ![Agregar campos](./media/add-form/add-fields.png)

1. Seleccione los puntos suspensivos (...) junto a **Agregar campo**, seleccione **contraer todo**y, a continuación, arrastre **nombre** hasta la parte superior de la lista.

    ![Campo de movimiento](./media/add-form/move-field.png)

    El control **Editar** formulario refleja el cambio.

    ![Mostrar formulario](./media/add-form/show-form1.png)

## <a name="set-the-card-type-for-a-field"></a>Establecimiento del tipo de tarjeta de un campo
1. En el panel **campos** , expanda el campo **precio** seleccionando la flecha hacia abajo.

1. Abra la lista **tipo de control** y, a continuación, seleccione **Editar control deslizante**.

    ![Editar control deslizante](./media/add-form/edit-slider.png)

    En el formulario, el campo **precio** muestra un control **deslizante** en lugar de un control **entrada de texto** .

1. opta Siga el mismo proceso para cambiar el control para el campo de **información general** a un control de **texto de varias líneas** .

## <a name="edit-form-only-save-changes"></a>Guardar cambios (Solo para Edit form)

1. Cambie el nombre del formulario a **EditForm**.

1. Agregue un control **[Botón](controls/control-button.md)** y establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:

   `SubmitForm(EditForm)`

1. Presione F5 para abrir la vista previa, cambie el nombre de un producto y, a continuación, seleccione el botón que creó.

    La función **[SubmitForm](functions/function-form.md)** guarda los cambios en el origen de datos.

1. opta Cierre la vista previa presionando ESC (o seleccionando el icono cerrar en la esquina superior derecha).

## <a name="next-steps"></a>Pasos siguientes
Más información sobre [formularios](working-with-forms.md) y [galerías](working-with-formulas.md).
