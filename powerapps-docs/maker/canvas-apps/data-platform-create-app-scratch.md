---
title: Crear una aplicación de lienzo desde cero con Common Data Service for Apps | Microsoft Docs
description: En PowerApps, cree una aplicación de lienzo para agregar, actualizar y eliminar registros en Common Data Service for Apps.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/18/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dab8caea5679701735685a5c4383c77cd7ed44f6
ms.sourcegitcommit: 452d4ead948591d16aff144006ad84c957eba837
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56091232"
---
# <a name="create-a-canvas-app-from-scratch-using-common-data-service-for-apps"></a>Crear una aplicación de lienzo desde cero con Common Data Service for Apps

Compile una aplicación de lienzo para administrar datos almacenados en Common Data Service for Apps mediante entidades estándar (que están integradas), entidades personalizadas (creadas por la organización) o ambas.

Al compilar una aplicación desde Common Data Service, no es necesario crear una conexión desde PowerApps, como ocurre con orígenes de datos como SharePoint, Dynamics 365 o Salesforce. Solo necesita especificar las entidades que desea mostrar, administrar o usar para ambas actividades en la aplicación.

## <a name="prerequisites"></a>Requisitos previos

- Antes de crear una aplicación desde cero, familiarícese con los conceptos básicos de PowerApps mediante la [generación de una aplicación](data-platform-create-app.md) y, después, personalice la [galería](customize-layout-sharepoint.md), [formularios](customize-forms-sharepoint.md) y [tarjetas](customize-card.md) de esa aplicación.
- [Cambie a un entorno](working-with-environments.md) en el que se haya creado una base de datos con datos de ejemplo. Si tiene una licencia apropiada, puede [crear un entorno](../../administrator/create-environment.md) para satisfacer esta necesidad.
- Para crear una aplicación, debe estar asignado al rol de seguridad [Creador de entorno](https://docs.microsoft.com/power-platform/admin/database-security.md#predefined-security-roles).

## <a name="open-a-blank-app"></a>Abra una aplicación en blanco

1. Inicie sesión en [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

1. En **Cree su propia aplicación**, mantenga el puntero sobre el icono **Iniciar desde cero** de las aplicaciones de lienzo, o bien pulse el icono de teléfono o haga clic en él y, después, **Crear esta aplicación**.

    ![Icono de la aplicación en blanco](./media/data-platform-create-app-scratch/start-from-blank.png)

    Se puede diseñar una aplicación desde cero para teléfonos u otros dispositivos (por ejemplo, tabletas); este tema se centrará en el diseño de una aplicación para teléfonos.

## <a name="specify-an-entity"></a>Especificar una entidad

1. En el centro de la pantalla, pulse o haga clic en **Conectarse a los datos** y, después, en el panel **Datos**, pulse o haga clic en la conexión **Common Data Service**.

1. En el cuadro de búsqueda, escriba o pegue las primeras letras de **Cuentas** para filtrar la lista de entidades, active la casilla **Cuentas** y, después, pulse o haga clic en **Conectar**.

    ![Especificar la entidad Accounts](./media/data-platform-create-app-scratch/cds-connect.png)

1. Cierre el panel **Datos** pulsando o haciendo clic en el icono Cerrar en la esquina superior derecha.

## <a name="add-a-list-screen"></a>Agregar una pantalla de lista

1. En la pestaña **Inicio**, pulse o haga clic en **Nueva pantalla** y luego pulse o haga clic en **Pantalla de lista**.

    ![Agregar una pantalla de lista](./media/data-platform-create-app-scratch/list-screen.png)

1. En la barra de navegación de la izquierda, pulse o haga clic en **TemplateGalleryList1** para seleccionarlo y, después, establezca el valor de la propiedad **Items** en esta fórmula:

    `SortByColumns(Search(Accounts, TextSearchBox1.Text, "name"), "name", If(SortDescending1, SortOrder.Descending, SortOrder.Ascending))`

    Esta fórmula especifica que:

   - La galería debe mostrar datos de la entidad **Accounts**.
   - Los datos se deben ordenar en orden ascendente hasta que un usuario pulse o haga clic en el botón de ordenación para alternar el criterio de ordenación.
   - Si un usuario escribe o pega uno o más caracteres en la barra de búsqueda, en la lista solo se mostrarán las cuentas en las que el campo de nombre contiene los caracteres que el usuario ha especificado.

     Puede usar [estas y otras muchas funciones](formula-reference.md) para especificar el aspecto y el comportamiento de la aplicación.

     ![Establecer la propiedad Items de la galería](./media/data-platform-create-app-scratch/gallery-items.png)

1. Establezca el diseño de la galería para que solo se muestre el nombre de cada cuenta y configure la barra de título para mostrar la palabra **Examinar**, como se describe en [Personalizar una galería](customize-layout-sharepoint.md).

    ![Pantalla de exploración](./media/data-platform-create-app-scratch/final-browse.png)

1. En la barra de navegación de la izquierda, mantenga el puntero sobre **Screen1**, haga clic o pulse en el icono de puntos suspensivos (...) y, luego, en **Eliminar**.

1. En la barra de navegación de la izquierda, mantenga el puntero sobre **Screen2**, haga clic o pulse en el icono de puntos suspensivos (...) y, luego, en **Cambiar el nombre**.

1. Escribe o pegue **BrowseScreen** y, después, cambie el nombre de la galería en esa pantalla por **BrowseGallery**.

    ![Cambiar el nombre de la pantalla de exploración por galería](./media/data-platform-create-app-scratch/rename-browse.png)

## <a name="add-a-form-screen"></a>Agregar una pantalla de formulario

1. Repita el primer paso del procedimiento anterior, pero agregue una **Pantalla de formulario** en lugar de una **Pantalla de lista**.

1. Establezca la propiedad **DataSource** del formulario en **Accounts** y su propiedad **Item** en **BrowseGallery.Selected**, tal y como se muestra en la **pestaña Opciones avanzadas** del panel de la derecha.

    ![Establecer las propiedades Datasource e Item del formulario](./media/data-platform-create-app-scratch/form-datasource.png)

1. En la pestaña **Propiedades** del panel de la derecha, pulse o haga clic en **Cuentas** para abrir el panel **Datos** y, después, active las casillas para estos campos:

    - Nombre de cuenta
    - Dirección 1: Calle 1
    - Dirección 1: Ciudad
    - Dirección 1: Código postal
    - Número de empleados
    - Ingresos anuales

1. Establezca la propiedad **Text** de la barra de título para que muestre **Crear/Editar**.

    La pantalla refleja los cambios.

    ![Establecer las propiedades Datasource e Item del formulario](./media/data-platform-create-app-scratch/field-list.png)

1. Cambie el nombre de esta pantalla a **FormScreen**.

## <a name="configure-icons"></a>Configurar iconos

1. En **BrowseScreen**, pulse o haga clic el icono circular cerca de la parte superior de la pantalla y establezca su propiedad **OnSelect** en esta fórmula:

    `Refresh(Accounts)`

    ![Icono Actualizar](./media/data-platform-create-app-scratch/refresh-icon.png)

1. Pulse o haga clic en el icono más y establezca su propiedad **OnSelect** en esta fórmula:

    `NewForm(EditForm1); Navigate(FormScreen, ScreenTransition.None)`

    ![Icono Agregar](./media/data-platform-create-app-scratch/plus-icon.png)

1. Pulse o haga clic en la primera flecha que apunta a la derecha y establezca su propiedad **OnSelect** en esta fórmula:

    `EditForm(EditForm1); Navigate(FormScreen, ScreenTransition.None)`

    ![Icono Siguiente](./media/data-platform-create-app-scratch/next-icon.png)

1. En **FormScreen**, pulse o haga clic en el icono Cancelar y establezca su propiedad **OnSelect** en esta fórmula:

    `ResetForm(EditForm1);Navigate(BrowseScreen, ScreenTransition.None)`

    ![Icono Cancelar](./media/data-platform-create-app-scratch/cancel-icon.png)

1. Pulse o haga clic en el icono de marca de verificación y establezca su propiedad **OnSelect** en esta fórmula:

    `SubmitForm(EditForm1); Navigate(BrowseScreen, ScreenTransition.None)`

    ![Icono de marca de verificación](./media/data-platform-create-app-scratch/checkmark-icon.png)

1. En la pestaña **Insertar**, pulse o haga clic en **Iconos** y después en **Papelera**.

1. Establezca la propiedad **Color** del icono **Papelera** en **White** y su propiedad **OnSelect** en esta fórmula:

    `Remove(Accounts, BrowseGallery.Selected); Navigate(BrowseScreen, ScreenTransition.None)`

    ![Icono de la papelera](./media/data-platform-create-app-scratch/trash-icon.png)

## <a name="test-the-app"></a>Probar la aplicación

1. En la barra de navegación de la izquierda, seleccione **BrowseScreen** y, después, abra el modo de vista previa presionando F5 (o pulsando o haciendo clic en el icono de reproducción situado en la esquina superior derecha).

    ![Abrir vista previa](./media/data-platform-create-app-scratch/open-preview.png)

1. Alterne la lista entre los criterios de ordenación ascendente y descendente, y filtre la lista por caracteres específicos en cada nombre de cuenta.

1. Agregue una cuenta, modifíquela, empiece a actualizarla pero cancele los cambios y, después, elimine la cuenta.

## <a name="next-steps"></a>Pasos siguientes

- [Vincule esta aplicación a una solución](add-app-solution.md) para poder, por ejemplo, implementarla en un entorno distinto o publicarla en AppSource.
- [Abra una o varias aplicaciones de ejemplo](open-and-run-a-sample-app.md) y explore los distintos tipos de aplicaciones que se pueden crear.
