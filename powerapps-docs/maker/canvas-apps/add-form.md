---
title: Mostrar, editar o agregar un registro de una tabla en una aplicación de lienzo | Microsoft Docs
description: Utilice un formulario de aplicación de lienzo para mostrar, editar o agregar un registro de una tabla en el origen de datos.
author: karthik-1
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/06/2017
ms.author: sharik
ms.openlocfilehash: a8c786e499bdc1e4dacc0adbf2bee489d56229ce
ms.sourcegitcommit: e3f5a2bef64085d02aec82e62ff94ae8a4d01d24
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39469980"
---
# <a name="show-edit-or-add-a-record-from-a-table-in-powerapps"></a>Mostrar, editar o agregar un registro de una tabla en PowerApps

Para mostrar todos los campos de un registro, agregue y configure un control **[Mostrar formulario](controls/control-form-detail.md)** en una aplicación de lienzo. Para editar cualquier campo de un registro (o para agregar un registro) y guardar los cambios en un origen de datos, agregue y configure un control **[Editar formulario](controls/control-form-detail.md)** en una aplicación de lienzo.

## <a name="prerequisites"></a>Requisitos previos

* Aprenda a [agregar y configurar un control](add-configure-controls.md) en PowerApps.
* Descargue [este archivo de Excel](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx), que contiene datos de ejemplo para este tutorial.
* Cargue el archivo de Excel en una [cuenta de almacenamiento en la nube](connections/cloud-storage-blob-connections.md), como OneDrive para la Empresa.
* En una aplicación nueva o existente, [agregue una conexión](add-data-connection.md) a la tabla **FlooringEstimates** del archivo de Excel.
* Si usa una aplicación existente, [agregue una pantalla](add-screen-context-variables.md).

## <a name="add-a-form-and-show-data"></a>Agregar un formulario y mostrar datos
1. Agregue un control **[Lista desplegable](controls/control-drop-down.md)**, denomínelo **ChooseProduct** y establezca este valor para su propiedad **[Elementos](controls/properties-core.md)**:

    **FlooringEstimates.Name**

    > [!NOTE]
   > Si no está seguro de cómo agregar un control, cambiar su nombre o establecer una propiedad, consulte [Adición y configuración de un control en PowerApps](add-configure-controls.md).

    La lista muestra nombres de productos para el suelo del origen de datos.

2. Agregue un control **Formulario de edición**, sitúelo bajo **ChooseProduct** y cambie el tamaño del formulario para que cubra la mayor parte de la pantalla.

    ![Agregar un formulario](./media/add-form/add-a-form.png)

    > [!NOTE]
   > En este tema se describe el control **Formulario de edición**, pero se aplican los mismos principios al control **Formulario de presentación**.

3. Establezca la propiedad **[DataSource](controls/control-form-detail.md)** del formulario en **FlooringEstimates** y la propiedad **[Item](controls/control-form-detail.md)** del formulario en esta fórmula:

   **First(Filter(FlooringEstimates, Name=ChooseProduct.Selected.Value))**

   Esta fórmula especifica que, cuando termine de configurar el formulario, aparecerá el registro que el usuario selecciona en **ChooseProduct**.

4. En el panel **Data** (Datos), haga clic o pulse en la casilla de cada campo para mostrarlo.

    > [!NOTE]
   > Si el panel **Data** (Datos) está cerrado, para abrirlo es preciso seleccionar el formulario del panel izquierdo y, después, pulsar o hacer clic en **Data** (Datos) en el panel derecho.

    ![Mostrar campos en el formulario](./media/add-form/checkbox.png)

5. En el panel **Data** (Datos), arrastre la entrada **Name** al principio de la lista.

    ![Mover una tarjeta](./media/add-form/drag-field.png)

    El control **Formulario de edición** reflejará el cambio.

    ![Nombre en la parte superior](./media/add-form/move-card-form.png)

## <a name="set-the-card-type-for-a-field"></a>Establecimiento del tipo de tarjeta de un campo
1. Con el formulario seleccionado, pulse o haga clic en el selector de tarjeta de **Price** en el panel **Data** (Datos).

    ![Seleccionar un selector de tarjeta](./media/add-form/price-card2.png)

2. Desplácese hacia abajo y, a continuación, pulse o haga clic en la opción **Ver texto** para hacer que el campo sea de solo lectura.

    ![Ver texto](./media/add-form/view-text.png)

    El formulario reflejará el cambio.

    ![Número de solo lectura](./media/add-form/read-only.png)  

## <a name="edit-form-only-save-changes"></a>Guardar cambios (Solo para Edit form)
1. En el panel izquierdo, seleccione el formulario y, después, pulse o haga clic en los puntos suspensivos (...).

   ![Seleccionar el formulario](./media/add-form/select-form.png)

2. Pulse o haga clic en **Cambiar nombre** y, después, cambie el nombre del formulario **EditForm**.

3. Agregue un control **[Botón](controls/control-button.md)** y establezca su propiedad **[Texto](controls/properties-core.md)** en **Save**.

    ![Agregar un botón para guardar](./media/add-form/save-button.png)  

4. Establezca la propiedad **[AlSeleccionar](controls/properties-core.md)** del botón **Save** en esta fórmula:

   **SubmitForm(EditForm)**

5. Para abrir el modo de vista previa, seleccione el botón de reproducción situado cerca de la esquina superior derecha (o presione F5).

    ![Abrir el modo de vista previa](./media/add-form/open-preview.png)

6. Cambie el nombre de un producto y, a continuación, pulse o haga clic en el botón **Save** que ha creado.

    La función **[SubmitForm](functions/function-form.md)** guarda los cambios en el origen de datos con el que ha configurado el formulario.

7. (opcional) Seleccione el icono Cerrar para cerrar la vista previa (o presione Esc).

    ![Cerrar vista previa](./media/add-form/close-preview.png)

## <a name="next-steps"></a>Pasos siguientes
Más información sobre [formularios](working-with-forms.md) y [galerías](working-with-formulas.md).
