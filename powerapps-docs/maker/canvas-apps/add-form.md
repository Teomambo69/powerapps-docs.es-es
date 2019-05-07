---
title: Mostrar, editar o agregar un registro en una aplicación de lienzo | Microsoft Docs
description: Utilice un formulario de aplicación de lienzo para mostrar, editar o agregar un registro de una tabla en el origen de datos.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/06/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e94aa48ed3fba1b4591e196e3b81d3fb0f76666f
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63321442"
ms.PowerAppsDecimalTransform: true
---
# <a name="show-edit-or-add-a-record-in-a-canvas-app"></a>Mostrar, editar o agregar un registro en una aplicación de lienzo

En una aplicación de lienzo, agregue y configure un **[mostrar](controls/control-form-detail.md)** control formulario para mostrar todos los campos en un registro, también puede agregar y configurar un **[editar](controls/control-form-detail.md)** control de formulario para editar cualquier campo de un registro, agregue un registro y guarde los cambios en un origen de datos.

## <a name="prerequisites"></a>Requisitos previos

- Aprenda a [agregar y configurar un control](add-configure-controls.md) en PowerApps.
- Descargue [este archivo de Excel](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx), que contiene datos de ejemplo para este tutorial.
- Cargue el archivo de Excel en una [cuenta de almacenamiento en la nube](connections/cloud-storage-blob-connections.md), como OneDrive para la Empresa.
- Cree o abra una aplicación para teléfonos, [agregar una conexión](add-data-connection.md) a la **FlooringEstimates** tabla en el archivo de Excel.

    Puede agregar un formulario a una aplicación de tableta, pero no coincide con este tema debido a que el formulario tiene tres columnas de forma predeterminada.

- Si abre una aplicación existente, [agregar una pantalla](add-screen-context-variables.md) a él.

## <a name="add-a-form-and-show-data"></a>Agregar un formulario y mostrar datos
1. En una pantalla en blanco, agregue un **[desplegable](controls/control-drop-down.md)** controlar y asígnele el nombre **ChooseProduct**.

    > [!NOTE]
   > Si no está seguro de cómo agregar un control, cambiar su nombre o establecer una propiedad, consulte [Adición y configuración de un control en PowerApps](add-configure-controls.md).

1. En el **propiedades** ficha del panel derecho, establezca **elementos** a `FlooringEstimates` y **valor** a `Name`.

    ![Establezca la propiedad de los elementos del formulario](./media/add-form/items-property.png)

    La lista muestra nombres de productos para el suelo del origen de datos.

1. Agregar un **editar** control de formulario, desplácelo bajo **ChooseProduct**y, a continuación, cambie el tamaño del formulario para cubrir la mayor parte de la pantalla.

    ![Agregar un formulario](./media/add-form/add-a-form.png)

    > [!NOTE]
   > Este tema se describe la **editar** control de formulario, pero los principios similares se aplican a la **mostrar** control de formulario.

1. Establezca la **[DataSource](controls/control-form-detail.md)** propiedad **FlooringEstimates** y su **[elemento](controls/control-form-detail.md)** propiedad Esta fórmula:

    `First(Filter(FlooringEstimates; Name=ChooseProduct.Selected.Value))`

   Esta fórmula especifica que, cuando termine de configurar el formulario, aparecerá el registro que el usuario selecciona en **ChooseProduct**.

1. En el **propiedades** ficha del panel derecho, seleccione **editar campos**.

    ![Editar campos](./media/add-form/edit-fields.png)

1. En el panel **Campos**, seleccione **Agregar campo**, marque la casilla de cada campo y, luego, seleccione **Agregar**.

    ![Agregar campos](./media/add-form/add-fields.png)

1. Seleccione los puntos suspensivos (...) junto a **Agregar campo**, seleccione **Contraer todo**y, a continuación, arrastre **nombre** a la parte superior de la lista.

    ![Mover campo](./media/add-form/move-field.png)

    El **editar** control de formulario reflejará el cambio.

    ![Mostrar formulario](./media/add-form/show-form1.png)

## <a name="set-the-card-type-for-a-field"></a>Establecimiento del tipo de tarjeta de un campo
1. En el **campos** panel, expanda el **precio** campo seleccionando la flecha hacia abajo.

1. Abra el **tipo de Control** lista y, a continuación, seleccione **editar control deslizante**.

    ![Editar control deslizante](./media/add-form/edit-slider.png)

    En el formulario, el **precio** campo se muestra un **control deslizante** control en lugar de un **entrada de texto** control.

1. (opcional) Siga el mismo proceso para cambiar el control para el **información general sobre** campo a un **editar texto multilínea** control.

## <a name="edit-form-only-save-changes"></a>Guardar cambios (Solo para Edit form)

1. Cambie el nombre del formulario **EditForm**.

1. Agregue un control **[Botón](controls/control-button.md)** y establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:

   `SubmitForm(EditForm)`

1. Presione F5 para abrir la vista previa, cambiar el nombre de un producto y, a continuación, seleccione el botón que ha creado.

    El **[SubmitForm](functions/function-form.md)** función guarda los cambios en el origen de datos.

1. (opcional) Cerrar vista previa presionando Esc (o seleccionando el icono Cerrar situado en la esquina superior derecha).

## <a name="next-steps"></a>Pasos siguientes
Más información sobre [formularios](working-with-forms.md) y [galerías](working-with-formulas.md).
