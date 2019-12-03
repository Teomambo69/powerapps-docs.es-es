---
title: Creación de una aplicación de lienzo desde cero con Common Data Service | Microsoft Docs
description: En Power Apps, cree una aplicación de lienzo para agregar, actualizar y eliminar registros en Common Data Service.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/21/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 48cd98481cff354d4e54cb54dc38865f6dfa6a14
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74679693"
ms.PowerAppsDecimalTransform: true
---
# <a name="create-a-canvas-app-from-scratch-using-common-data-service"></a>Creación de una aplicación de lienzo desde cero con Common Data Service

Compile una aplicación de lienzo para administrar datos almacenados en Common Data Service mediante entidades estándar (que están integradas), entidades personalizadas (creadas por la organización) o ambas.

Al compilar una aplicación desde Common Data Service, no es necesario crear una conexión desde Power Apps, como se hace con los orígenes de datos como SharePoint, Dynamics 365 o Salesforce. Solo deberá especificar las entidades que quiere mostrar o administrar en la aplicación.

## <a name="prerequisites"></a>Requisitos previos

- Antes de crear una aplicación desde cero, familiarícese con los conceptos básicos de Power apps mediante la [generación de una aplicación](data-platform-create-app.md) y, a continuación, la personalización de la [Galería](customize-layout-sharepoint.md), los [formularios](customize-forms-sharepoint.md)y las [tarjetas](customize-card.md)de esa aplicación.
- [Cambie a un entorno](working-with-environments.md) en el que se haya creado una base de datos con datos de ejemplo. Si tiene una licencia apropiada, puede [crear un entorno](../../administrator/create-environment.md) para satisfacer esta necesidad.
- Para crear una aplicación, debe estar asignado al rol de seguridad [Creador de entorno](https://docs.microsoft.com/power-platform/admin/database-security#predefined-security-roles).

## <a name="open-a-blank-app"></a>Abra una aplicación en blanco

1. Inicie sesión en [PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

1. En **Cree su propia aplicación**, seleccione **Aplicación de lienzo en blanco**.

    ![Icono de la aplicación en blanco](./media/data-platform-create-app-scratch/blank-app.png)

1. Especifique el nombre de la aplicación, seleccione **Teléfono** y, luego, **Crear**.

    Puede crear una aplicación desde cero para tabletas, pero este tema muestra la creación de una aplicación para teléfonos.

## <a name="specify-an-entity"></a>Especificar una entidad

1. En el centro de la pantalla, seleccione **Conectarse a datos**.

1. En el panel **Datos**, seleccione **Common Data Service**, seleccione la casilla **Cuentas** y, después, **Conectar**.

1. Cierre el panel **Datos** seleccionando el icono Cerrar en la esquina superior derecha.

## <a name="add-a-list-screen"></a>Agregar una pantalla de lista

1. En la pestaña **Inicio**, seleccione la flecha hacia abajo junto a **Nueva pantalla** y, después, **Formulario**.

    ![Agregar una pantalla de lista](./media/data-platform-create-app-scratch/list-screen.png)

1. En la barra de navegación izquierda, seleccione **BrowseGallery1** y establezca el valor de la propiedad **Items** en esta fórmula:

    `SortByColumns(Search(Accounts; TextSearchBox1.Text; "name"); "name"; If(SortDescending1; SortOrder.Descending; SortOrder.Ascending))`

    Esta fórmula especifica que:

   - La galería debe mostrar datos de la entidad **Accounts**.
   - Los datos se deben organizar en orden ascendente hasta que un usuario seleccione el botón de ordenación para alternar el criterio.
   - Si un usuario escribe o pega uno o más caracteres en la barra de búsqueda (**TextSearchBox1**), en la lista solo se mostrarán las cuentas en las que el campo **nombre** contiene los caracteres que el usuario ha especificado.

     Puede usar [estas y otras muchas funciones](formula-reference.md) para especificar el aspecto y el comportamiento de la aplicación.

     ![Establecer la propiedad Items de la galería](./media/data-platform-create-app-scratch/gallery-items.png)

1. Establezca el diseño de la galería para que solo se muestre el nombre de cada cuenta y configure la barra de título para mostrar la palabra **Examinar**, como se describe en [Personalizar una galería](customize-layout-sharepoint.md).

    ![Pantalla de exploración](./media/data-platform-create-app-scratch/final-browse.png)

1. En la barra de navegación izquierda, pase el mouse sobre **Screen1**, seleccione el botón de puntos suspensivos (...) y seleccione **Eliminar**.

1. En la barra de navegación izquierda, pase el mouse sobre **Screen2**, seleccione el botón de puntos suspensivos (...) y seleccione **Cambiar nombre**.

1. Escribe o pegue **BrowseScreen** y, después, cambie el nombre de la galería en esa pantalla por **BrowseGallery**.

    ![Cambiar el nombre de la pantalla de exploración por galería](./media/data-platform-create-app-scratch/rename-browse.png)

## <a name="add-a-form-screen"></a>Agregar una pantalla de formulario

1. Repita el primer paso del procedimiento anterior, pero agregue una pantalla de **Formulario** en lugar de una pantalla de **Lista**.

1. Establezca la propiedad **DataSource** del formulario en **Accounts** y su propiedad **Item** en **BrowseGallery.Selected**, tal y como se muestra en la **pestaña Opciones avanzadas** del panel de la derecha.

    ![Establecer las propiedades Datasource e Item del formulario](./media/data-platform-create-app-scratch/form-datasource.png)

1. En la pestaña **propiedades** del panel derecho, seleccione **Editar campos** para abrir el panel **campos** .

1. Seleccione **Agregar campo** y seleccione las casillas para estos campos:

    - **Nombre de cuenta**
    - **Dirección 1: calle 1**
    - **Dirección 1: City**
    - **Dirección 1: código postal**
    - **Número de empleados**
    - **Ingresos anuales**

    > [!NOTE]
    > Fuera de este escenario, puede crear un campo personalizado seleccionando **nuevo campo**, proporcionando la información necesaria y, a continuación, seleccionando **listo**. Más información: [crear un campo](../common-data-service/create-edit-field-portal.md#create-a-field).<br><br>![](media/data-platform-create-app-scratch/choose-or-add-fields.png "Select and add a field")

1. Seleccione **Agregar**.

1. Establezca la propiedad **Text** de la barra de título para que muestre **Crear/Editar**.

    La pantalla refleja los cambios.

    ![Establecer las propiedades Datasource e Item del formulario](./media/data-platform-create-app-scratch/field-list.png)

1. Cambie el nombre de esta pantalla a **FormScreen**.

## <a name="configure-icons"></a>Configurar iconos

1. En **BrowseScreen**, establezca la propiedad **OnSelect** del icono circular de la parte superior de la pantalla en esta fórmula:

    `Refresh(Accounts)`

    ![Icono Actualizar](./media/data-platform-create-app-scratch/refresh-icon.png)

1. Establezca la propiedad **OnSelect** del icono "más" en esta fórmula:

    `NewForm(EditForm1);; Navigate(FormScreen; ScreenTransition.None)`

    ![Icono Agregar](./media/data-platform-create-app-scratch/plus-icon.png)

1. Establezca la propiedad **OnSelect** de la primera flecha que apunta a la derecha en esta fórmula:

    `EditForm(EditForm1);; Navigate(FormScreen; ScreenTransition.None)`

    ![Icono Siguiente](./media/data-platform-create-app-scratch/next-icon.png)

1. En **FormScreen**, establezca la propiedad **OnSelect** del icono Cancelar en esta fórmula:

    `ResetForm(EditForm1);;Navigate(BrowseScreen; ScreenTransition.None)`

    ![Icono Cancelar](./media/data-platform-create-app-scratch/cancel-icon.png)

1. Establezca la propiedad **OnSelect** del icono de marca de verificación en esta fórmula:

    `SubmitForm(EditForm1);; Navigate(BrowseScreen; ScreenTransition.None)`

    ![Icono de marca de verificación](./media/data-platform-create-app-scratch/checkmark-icon.png)

1. En la pestaña **Insertar**, seleccione **Iconos** y, a continuación, el icono **Papelera**.

1. Establezca la propiedad **Color** del icono **Papelera** en **White** y su propiedad **OnSelect** en esta fórmula:

    `Remove(Accounts; BrowseGallery.Selected);; Navigate(BrowseScreen; ScreenTransition.None)`

    ![Icono de la papelera](./media/data-platform-create-app-scratch/trash-icon.png)

## <a name="test-the-app"></a>Probar la aplicación

1. En la barra de navegación izquierda, seleccione **BrowseScreen** y abra el modo de vista previa presionando F5 (o seleccionando el icono de reproducción situado en la esquina superior derecha).

    ![Abrir vista previa](./media/data-platform-create-app-scratch/open-preview.png)

1. Alterne la lista entre los criterios de ordenación ascendente y descendente y fíltrela por uno o más caracteres en el nombre de cuenta.

1. Agregue una cuenta, modifíquela, empiece a actualizarla pero cancele los cambios y, después, elimine la cuenta.

## <a name="next-steps"></a>Pasos siguientes

- [Vincule esta aplicación a una solución](add-app-solution.md) para poder, por ejemplo, implementarla en un entorno distinto o publicarla en AppSource.
- [Abra una o varias aplicaciones de ejemplo](open-and-run-a-sample-app.md) y explore los distintos tipos de aplicaciones que se pueden crear.
