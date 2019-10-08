---
title: Creación de una aplicación de lienzo desde cero a partir de datos de Excel | Microsoft Docs
description: En este tutorial, creará una aplicación de lienzo de dos pantallas para que los usuarios puedan crear, editar y eliminar registros en un archivo de Excel.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/26/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d0a7a164210fcfd9593455f825092417bd31a692
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71983654"
ms.PowerAppsDecimalTransform: true
---
# <a name="create-a-canvas-app-from-scratch-based-on-excel-data"></a>Creación de una aplicación de lienzo desde cero a partir de datos de Excel

Cree su propia aplicación de lienzo desde cero a partir de datos de Excel, en formato de tabla, y agregue luego datos de otros orígenes si quiere. Si sigue este tutorial, creará una aplicación que contiene dos pantallas. En una pantalla, los usuarios pueden navegar a través de un conjunto de registros. En la otra pantalla, los usuarios pueden crear un registro, actualizar uno o varios campos de un registro o eliminar todo un registro. Este enfoque requiere más tiempo que la [creación de una aplicación automáticamente](get-started-create-from-data.md), pero los creadores que tengan más experiencia pueden usarlo para crear aplicaciones mejor adaptadas a sus necesidades.

## <a name="prerequisites"></a>Requisitos previos

Para seguir exactamente los pasos de este tutorial, primero cree un archivo de Excel con estos datos de ejemplo.

1. Copie estos datos y péguelos en un archivo de Excel.

    | StartDay | StartTime | Volunteer | Copiar |
    | --- | --- | --- | --- |
    | Sábado |10 a.m. a mediodía |Vasquez |Kumashiro |
    | Sábado |mediodía a 2 p.m. |Ice |Singhal |
    | Sábado |2 p.m. - 4 p.m. |Myk |Mueller |
    | Domingo |10 a.m. a mediodía |Li |Adams |
    | Domingo | mediodía a 2 p.m. |Singh |Morgan |
    | Domingo | 2 p.m. - 4 p.m. |Batye |Nguyen |

2. Dé a los datos un formato de tabla, llamada **Programa**, para que PowerApps pueda analizar la información.

    Para obtener más información, vea [Dar formato a una tabla en Excel](how-to-excel-tips.md).

3. Guarde el archivo con el nombre **eventsignup. xlsx**, ciérrelo y, a continuación, cárguelo en una [cuenta de almacenamiento en la nube](connections/cloud-storage-blob-connections.md), como OneDrive.

> [!IMPORTANT]
> Para conocer los conceptos generales, puede utilizar su propio archivo de Excel y seguir este tutorial. No obstante, los datos del archivo de Excel deben tener formato de tabla. Para obtener más información, vea [Dar formato a una tabla en Excel](how-to-excel-tips.md).

## <a name="open-a-blank-app"></a>Abra una aplicación en blanco

1. Inicie sesión en [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

1. En **Cree su propia aplicación**, seleccione **Aplicación de lienzo en blanco**.

    > [!div class="mx-imgBorder"]
    >![Creación de una aplicación de lienzo en blanco](./media/get-started-create-from-blank/blank-app.png)

1. Especifique el nombre de la aplicación, seleccione **Teléfono** y, luego, **Crear**.

    Puede diseñar una aplicación desde cero para teléfonos o para otros dispositivos (por ejemplo, tabletas). Este tema se centra en el diseño de una aplicación para teléfonos.

    > [!div class="mx-imgBorder"]
    >![Especificación del nombre y el formato de la aplicación](./media/get-started-create-from-blank/excel-demo.png)

    PowerApps Studio crea una aplicación en blanco para teléfonos.

1. Si aparece el cuadro de diálogo de **bienvenida a PowerApps Studio**, seleccione **Omitir**.

## <a name="connect-to-data"></a>Conectarse a datos

1. En el centro de la pantalla, seleccione **Conectarse a datos**.

1. En el panel **Datos**, seleccione la conexión de su cuenta de almacenamiento en la nube, si aparece. De lo contrario, siga estos pasos para agregar una conexión:

    1. Seleccione **Nueva conexión**, seleccione el icono de la cuenta de almacenamiento en la nube y, a continuación, seleccione **Crear**.
    2. Si se le solicita, proporcione las credenciales para esa cuenta.

1. En **Elegir un archivo de Excel**, escriba o pegue las primeras letras de **eventsignup** para filtrar la lista y, a continuación, seleccione el archivo que ha cargado.

1. En **Elegir una tabla**, active la casilla de **Programa** y, a continuación, seleccione **Conectar**.

1. Cierre el panel **Datos** mediante el icono de cierre (X) que encontrará en la esquina superior derecha.

## <a name="create-the-view-screen"></a>Creación de la pantalla de vista

1. En la pestaña **Inicio**, seleccione la flecha abajo junto a **Nueva pantalla** para abrir una lista de tipos de pantalla y, luego, seleccione **Lista**.

    Se agrega una pantalla con varios controles predeterminados, como un cuadro de búsqueda y un control de **[Galería](controls/control-gallery.md)** . La galería cubre toda la pantalla en el cuadro de búsqueda.

1. En la parte superior de la pantalla nueva, seleccione el control **[Etiqueta](controls/control-text-box.md)** y reemplace **[Título]** por **Ver registros**.

     ![Cambiar la barra de título](./media/get-started-create-from-blank/change-title-bar.png)

1. En la barra de navegación izquierda, seleccione **BrowseGallery1**.

    Se muestra un cuadro de selección con indicadores alrededor de la galería.

    ![Agregar una pantalla de lista](./media/get-started-create-from-blank/select-gallery.png)

1. En la pestaña **Propiedades** del panel del lateral derecho, seleccione la flecha abajo del menú **Diseño**.

    ![Apertura del menú de diseño](./media/get-started-create-from-blank/select-layout.png)

1. Seleccione **Título, subtítulo y cuerpo**.

1. En la barra de fórmulas, reemplace **CustomGallerySample** por **Programa** y ambas instancias de **SampleText** por **Volunteer**.

1. En el borde derecho de la barra de fórmulas, seleccione la flecha abajo y, luego, **Aplicar formato al texto**.

    La fórmula coincide con la de este ejemplo:

    ```powerapps-comma
    SortByColumns(
        Search(
            Schedule;
            TextSearchBox1.Text;
            "Volunteer"
        );
        "Volunteer";
        If(
            SortDescending1;
            SortOrder.Descending;
            SortOrder.Ascending
        )
    )
    ```

1. En la pestaña **Propiedades** del panel del lateral derecho, seleccione **Editar**, junto a la etiqueta **Campos**.

1. En el cuadro **Title2** , seleccione **voluntarios**, en el cuadro **Subtitle2** , seleccione **StartDay**y, en el cuadro **cuerpo1** , seleccione **startTime**.

1. Cierre el panel **Datos** mediante el icono de cierre (X) que encontrará en la esquina superior derecha.

Los usuarios pueden ordenar y filtrar la galería por nombre de voluntario tomando como base las funciones **SortByColumns** y **Search** en esa fórmula.

- Si un usuario escribe al menos una letra en el cuadro de búsqueda, la galería mostrará únicamente aquellos registros en los que el campo **Volunteer** contenga el texto escrito por el usuario.
- Si el usuario selecciona el botón de ordenación (entre el de actualización y el "más" de la barra de títulos), la galería mostrará los registros en orden ascendente o descendente, dependiendo de cuántas veces seleccione el botón el usuario, tomando como referencia el campo **Volunteer**.

Para obtener más información sobre estas y otras funciones, vea la [referencia de fórmulas](formula-reference.md).

## <a name="create-the-change-screen"></a>Creación de la pantalla de cambio

1. En la pestaña **Inicio**, seleccione la flecha abajo junto a **Nueva pantalla** y, luego, seleccione **Formulario**.

1. En la barra de navegación izquierda, seleccione **EditForm1**.

1. En la pestaña **Propiedades** del panel del lateral derecho, seleccione la flecha abajo junto a **Origen de datos** y, luego, **Programa** en la lista que aparece.

1. Junto al origen de datos que acaba de especificar, seleccione **Editar campos**.

1. En el panel **Campos**, seleccione **Agregar campo**, marque la casilla de cada campo y, luego, seleccione **Agregar**.

1. Seleccione la flecha junto al nombre de cada campo para contraerlo y, luego, arrastre el campo **Volunteer** para que aparezca al principio de la lista de campos.

     ![Cambio del orden de los campos](./media/get-started-create-from-blank/reorder-fields.png)

1. Cierre el panel **Campos** mediante el icono de cierre (X) que encontrará en la esquina superior derecha.

1. Para establecer la propiedad **Elemento** del formulario, escriba o pegue la expresión en la barra de fórmulas:

    `BrowseGallery1.Selected`

1. En la parte superior de la pantalla, seleccione el control **[Label](controls/control-text-box.md)** y luego reemplace **[Title]** (Título) por **Change records** (Cambiar registros).

    ![Cambiar la barra de título](./media/get-started-create-from-blank/change-title-bar2.png)

## <a name="delete-and-rename-screens"></a>Eliminación y cambio de nombre de pantallas

1. En la barra de navegación izquierda, seleccione el botón de puntos suspensivos (...) para **Screen1**y, a continuación, seleccione **Eliminar**.

    ![Eliminar pantalla](./media/get-started-create-from-blank/delete-screen.png)

1. Seleccione los puntos suspensivos (...) para **Screen2**, seleccione **Cambiar nombre** y, a continuación, escriba o pegue **ViewScreen**.

1. Seleccione los puntos suspensivos (...) para **Screen3**, seleccione **Cambiar nombre** y, a continuación, escriba o pegue **ChangeScreen**.

## <a name="configure-icons-on-the-view-screen"></a>Configuración de iconos en la pantalla de vista

1. Cerca de la parte superior de **ViewScreen**, seleccione el icono de flecha circular.

    ![Agregar registro](./media/get-started-create-from-blank/refresh-icon.png)

1. Establezca la propiedad **OnSelect** para ese icono en esta fórmula:

    `Refresh(Schedule)`

    Cuando el usuario seleccione este icono, los datos de **Programa** se actualizarán desde el archivo de Excel.

    Para obtener más información sobre estas y otras funciones, vea la [referencia de fórmulas](formula-reference.md).

1. En la esquina superior derecha de **ViewScreen**, seleccione el icono del signo más.

    ![Agregar registro](./media/get-started-create-from-blank/add-record.png)

1. Establezca la propiedad **OnSelect** para ese icono en esta fórmula:

    `NewForm(EditForm1);;Navigate(ChangeScreen;ScreenTransition.None)`

    Cuando el usuario selecciona este icono, aparece la pantalla **ChangeScreen** con los campos vacíos, de forma que el usuario puede crear un registro más fácilmente.

1. Seleccione la flecha que apunta a la derecha para el primer registro de la galería.

    ![Selección de flecha](./media/get-started-create-from-blank/select-arrow.png)

1. Establezca la propiedad **OnSelect** de la flecha en esta fórmula:

    `EditForm(EditForm1);; Navigate(ChangeScreen; ScreenTransition.None)`

    Cuando el usuario selecciona este icono, **ChangeScreen** aparece con cada campo que muestra los datos para el registro seleccionado, por lo que el usuario puede editar o eliminar el registro más fácilmente.

## <a name="configure-icons-on-the-change-screen"></a>Configuración de iconos en la pantalla de cambio

1. En **ChangeScreen**, seleccione el icono "X" en la esquina superior izquierda.

    ![Icono Cancelar](./media/get-started-create-from-blank/cancel-icon.png)

1. Establezca la propiedad **OnSelect** para ese icono en esta fórmula:

    `ResetForm(EditForm1);;Navigate(ViewScreen; ScreenTransition.None)`

    Cuando el usuario selecciona este icono, los cambios realizados en esta pantalla por el usuario se descartan y se abre la pantalla de vista.

1. En la esquina superior derecha, seleccione el icono de marca de verificación.

    ![Icono de marca de verificación](./media/get-started-create-from-blank/checkmark-icon.png)

1. Establezca la propiedad **OnSelect** de la marca de verificación en esta fórmula:

    `SubmitForm(EditForm1);; Navigate(ViewScreen; ScreenTransition.None)`

    Cuando el usuario selecciona este icono, los cambios realizados en esta pantalla por el usuario se guardan y se abre la pantalla de vista.

1. En la pestaña **Insertar**, seleccione **Iconos** y, a continuación, el icono **Papelera**.

1. Establezca la propiedad **Color** del nuevo icono en **Blanco** y mueva el nuevo icono para que aparezca junto al icono de la marca de verificación.

    ![Icono de la papelera](./media/get-started-create-from-blank/trash-icon.png)

1. Establezca la propiedad **Visible** para el icono de papelera en esta fórmula:

    `EditForm1.Mode = FormMode.Edit`

    Este icono solo aparecerá si el formulario está en el modo **Editar**, no en el modo **Nuevo**.

1. Establezca la propiedad **OnSelect** para el icono de papelera en esta fórmula:

    `Remove(Schedule; BrowseGallery1.Selected);; Navigate(ViewScreen; ScreenTransition.None)`

    Cuando el usuario selecciona este icono, el registro seleccionado se elimina del origen de datos y se abre la pantalla de vista.

## <a name="test-the-app"></a>Probar la aplicación

1. Seleccione **ViewScreen** y abra el modo de vista previa presionando F5 o mediante el icono de **Vista previa** cerca de la esquina superior derecha.

    ![Abrir el modo de vista previa](./media/get-started-create-from-blank/open-preview.png)

1. Escriba o pegue una o varias letras en el cuadro de búsqueda para filtrar la lista en función del nombre del voluntario.

1. Seleccione el icono de ordenación una o varias veces para mostrar los datos en orden ascendente o descendente, según el nombre del voluntario.

1. Agregue un registro.

1. Actualice el registro que ha agregado y, a continuación, guarde los cambios.

1. Actualice el registro que ha agregado y, a continuación, cancele los cambios.

1. Elimine el registro que ha agregado.

1. Cierre el modo de vista previa presionando Esc (o seleccionando el icono de cerrar de la esquina superior derecha).

## <a name="next-steps"></a>Pasos siguientes

- Presione Ctrl-S para guardar la aplicación en la nube para que se pueda ejecutar desde otros dispositivos.
- [Comparta la aplicación](share-app.md) para que otras personas puedan ejecutarla.
- Obtenga más información sobre [funciones](working-with-formulas.md) como **Revisión**, que puede usar para administrar los datos sin necesidad de crear un formulario estándar.
- [Vincule esta aplicación a una solución](add-app-solution.md) para poder, por ejemplo, implementarla en un entorno distinto o publicarla en AppSource.
