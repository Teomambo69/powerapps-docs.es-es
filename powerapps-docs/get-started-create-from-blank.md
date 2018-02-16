---
title: "Creación de una aplicación desde cero | Microsoft Docs"
description: "Cree una aplicación desde cero mediante la configuración de cada elemento y comportamiento de la interfaz de usuario para administrar los datos diarios que necesita su negocio."
services: 
suite: powerapps
documentationcenter: na
author: karthik-1
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/16/2016
ms.author: sharik
ms.openlocfilehash: d530fb5f77f00cb37322383a3817e9c38533ca1d
ms.sourcegitcommit: e827813cd898ca9a1046b5952ea5e32ce2989a65
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="create-an-app-from-scratch"></a>Crear una aplicación desde cero
Cree su propia aplicación desde cero mediante cualquiera de los orígenes de datos existentes. Posteriormente, podrá agregar más orígenes si lo desea. Especifique la apariencia y el comportamiento de cada elemento de la interfaz de usuario para que pueda obtener el mejor resultado de acuerdo con sus objetivos y el flujo de trabajo especificados. Este enfoque es mucho más lento que [crear una aplicación automáticamente](get-started-create-from-data.md), pero los creadores de aplicaciones con experiencia pueden crear aplicaciones mejor adaptadas a sus necesidades.

> [!NOTE]
> Este tema se ha escrito para PowerApps Studio para Windows, pero los pasos serán similares si [abre PowerApps en un explorador](create-app-browser.md).

Si sigue este tutorial, creará una aplicación que contiene dos pantallas. En una pantalla, los usuarios pueden navegar a través de un conjunto de registros:

![Pantalla en la que el usuario puede desplazarse a través de un conjunto de datos](./media/get-started-create-from-blank/first-screen-final.png)

En la otra pantalla, los usuarios pueden crear un registro, actualizar uno o varios campos de un registro o eliminar uno:

![Pantalla en la que un usuario puede agregar o actualizar datos](./media/get-started-create-from-blank/changescreen-final.png)

## <a name="prerequisites"></a>Requisitos previos
Puede consultar este tutorial para ver los conceptos generales o puede seguirlo exactamente y completar estos pasos.

1. Copie estos datos y péguelos en un archivo de Excel.

   | Día de inicio | Hora de inicio | Voluntario 1 | Voluntario 2 |
   | --- | --- | --- | --- |
   | Sábado |10 a.m. a mediodía |Vasquez |Kumashiro |
   | Sábado |mediodía a 2 p.m. |Ice |Singhal |
   | Sábado |2 p.m. a 4 p.m. |Myk |Mueller |
   | Domingo |10 a.m. a mediodía |Li |Adams |
   | Domingo |10 a.m. a mediodía |Singh |Morgan |
   | Domingo |10 a.m. a mediodía |Batye |Nguyen |

2. Dé a los datos un formato de tabla, llamada **Programa**, para que PowerApps pueda analizar la información.

    Para más información, consulte [Crear o eliminar una tabla de Excel](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664).

3. Guarde el archivo con el nombre **eventsignup.xls**y, a continuación, cárguelo en una [cuenta de almacenamiento en la nube](connections/cloud-storage-blob-connections.md), como OneDrive.

4. Si no está familiarizado con PowerApps:

   * Aprenda cómo [agregar un control y establecer sus propiedades](add-configure-controls.md). Esto determinará el aspecto y el comportamiento del control.
   * Aprenda cómo [agregar y cambiar el nombre de una pantalla](add-screen-context-variables.md).

## <a name="create-a-blank-app-and-connect-to-data"></a>Crear una aplicación vacía y conexión a los datos
1. En PowerApps Studio, pulse o haga clic en **Nuevo** en el menú **Archivo** (cerca del borde izquierdo de la pantalla).

    ![Opción Nuevo en el menú Archivo](./media/get-started-create-from-blank/file-new.png)

2. En el icono **Blank app** (Aplicación vacía), pulse o haga clic en **Phone layout** (Diseño de teléfono).

    ![Opción para crear una aplicación a partir de datos](./media/get-started-create-from-blank/create-from-blank.png)

3. Si se le solicita, realice el paseo introductorio para comprender las principales áreas de PowerApps (o haga clic o pulse en **Omitir**).

    ![Paseo introductorio](./media/get-started-create-from-blank/quick-tour.png)

    Siempre puede realizar el paseo más tarde haciendo clic o pulsando en el icono del signo de interrogación situado cerca de la esquina superior izquierda de la pantalla y, a continuación, haciendo clic o pulsando en **Take the intro tour** (Realizar paseo introductorio).

4. En la barra de navegación izquierda, haga clic o pulse en uno de los iconos de la esquina superior derecha para cambiar a la vista en miniatura.

    ![Alternancia de las vistas](./media/get-started-create-from-blank/toggle-view.png)

5. En el panel de la derecha, haga clic o pulse en **Agregar origen de datos**.

    ![Agregar origen de datos](./media/get-started-create-from-blank/add-data-source.png)

6. Realice uno de estos pasos:

   * Si ya tiene una conexión a su cuenta de almacenamiento en la nube, haga clic o pulse en ella.
   * Si no tiene una conexión a la cuenta de almacenamiento en la nube, haga clic o pulse en **Agregar conexión**, después en el tipo de cuenta, posteriormente en **Conectar** y, finalmente (si se le solicita), proporcione sus credenciales.

7. En **Choose an Excel file** (Elegir un archivo de Excel), vaya a **eventsignup.xlsx** y haga clic o pulse en él.

    ![Especifique el archivo de Excel que desea usar](./media/get-started-create-from-blank/select-excel-file.png)

8. En **Choose a table** (Elegir una tabla), seleccione la casilla **Programación** y, a continuación, haga clic o pulse en **Conectar**.

    ![Especifique la tabla de Excel que desea usar](./media/get-started-create-from-blank/select-table.png)

    La pestaña **Orígenes de datos** del panel derecho muestra qué orígenes de datos ha agregado a la aplicación.

    ![Mostrar orígenes de datos conectados](./media/get-started-create-from-blank/data-connect.png)

    Este tutorial requiere un único origen de datos, pero puede agregar más orígenes de datos posteriormente.

## <a name="show-the-data"></a>Mostrar los datos
1. En la pestaña **Inicio**, haga clic o pulse en **Nueva pantalla** y luego haga clic o pulse **Pantalla de lista**.

    ![Agregar un diseño con un título, un subtítulo y un elemento de cuerpo](./media/get-started-create-from-blank/add-gallery.png)

    Se agrega una pantalla con varios controles predeterminados, como un cuadro de búsqueda y un control de **[Galería](controls/control-gallery.md)** . La galería cubre toda la pantalla en el cuadro de búsqueda.

2. Haga clic o pulse en cualquier parte de la galería excepto en una flecha, como directamente debajo del cuadro de búsqueda.

    ![Seleccionar la galería](./media/get-started-create-from-blank/select-gallery.png)

3. En el panel derecho, abra la lista **Diseños** y haga clic o pulse en la opción que muestra un título, un subtítulo y el cuerpo.

    ![Seleccionar la galería](./media/get-started-create-from-blank/select-layout.png)

4. En la lista de propiedades, haga clic o pulse en **[Items](controls/properties-core.md)**, copie esta fórmula y péguela en la barra de fórmulas:

    **SortByColumns(Search(Schedule, TextSearchBox1.Text, "Volunteer_x0020_1"), "Volunteer_x0020_1", If(SortDescending1, SortOrder.Descending, SortOrder.Ascending))**

    Si no está seguro de dónde está la lista de propiedades, consulte cómo [agregar y configurar controles](add-configure-controls.md).

    > [!NOTE]
> En los orígenes de datos de SharePoint y Excel que contienen nombres de columna con espacios, PowerApps los muestra como **"\_x0020\_"**. En este ejemplo, la columna **"Volunteer 1"** aparece en una fórmula tal que **"Volunteer_x0020_1"**.

    Esta galería muestra los datos de la tabla **Programación**.

    ![Se mostrarán los datos de Programación en la galería de forma predeterminada](./media/get-started-create-from-blank/show-data-default.png)

    Un cuadro de búsqueda puede filtrar la galería según el texto que escriba el usuario. Si un usuario escribe al menos una letra en el cuadro de búsqueda, la galería mostrará únicamente aquellos registros en los que el campo **Voluntarios 1** contenga el texto escrito por el usuario.

    El botón de ordenación puede ordenar los registros en función de los datos de la columna **Voluntarios 1**. Si un usuario hace clic o pulsa ese botón, el criterio de ordenación podrá cambiar entre ascendente y descendente.

    La fórmula contiene las funciones **Sort**, **If**, **IsBlank**, **Filter** y **Text**. Para más información sobre estas y otras funciones, consulte la [referencia de las fórmulas](formula-reference.md)

5. Escriba **i** en el cuadro de búsqueda y pulse o haga clic en el botón de ordenación una vez (o un número impar de veces).

    La galería muestra estos resultados.

    ![Ordenar y filtrar la galería](./media/get-started-create-from-blank/sort-filter.png)

    Más información acerca de **[Ordenar](functions/function-sort.md)**, **[Filtrar](functions/function-filter-lookup.md)** y [otras funciones](formula-reference.md)

6. Seleccione el control **[Etiqueta](controls/control-text-box.md)** de la parte superior de la pantalla haciendo clic o pulsando en él.

    ![Seleccionar la barra de título](./media/get-started-create-from-blank/select-title-bar.png)

7. En la lista de propiedades, haga clic o pulse en **[Texto](controls/properties-core.md)**, copie este texto y péguelo en la barra de fórmulas.<br>
   **"Ver registros"**

    ![Cambiar la barra de título](./media/get-started-create-from-blank/change-title-bar.png)

## <a name="create-the-changescreen-and-its-banner"></a>Crear la pantalla ChangeScreen y su banner
1. Eliminar **Screen1**y cambiar el nombre de **Screen2** a **ViewScreen**.

    ![Cambiar el nombre de pantalla](./media/get-started-create-from-blank/rename-screen.png)

2. Agregue una pantalla y cámbiele el nombre por **ChangeScreen**.

    ![Agregar y cambiar el nombre de pantalla](./media/get-started-create-from-blank/add-screen.png)

3. En la pestaña **Insertar**, haga clic o pulse en **Texto** y luego haga clic o pulse en **[Etiqueta](controls/control-text-box.md)**.

4. Configure el control **Etiqueta** que acaba de agregar:

   * Establezca la propiedad **Text** en esta fórmula:
     <br>**"Cambiar registro"**

   * Establezca la propiedad **Fill** en esta fórmula:
     <br>**RGBA(62, 96, 170, 1)**.

   * Establezca su propiedad **Color** en esta fórmula:
     <br>**RGBA(255, 255, 255, 1)**

   * Establezca su propiedad **Align** en **Center**.
   * Establezca su propiedad **X** en **0**.

   * Establezca su propiedad **Width** en **640**.
     El control **Etiqueta** refleja los cambios.

     ![ChangeScreen con banner](./media/get-started-create-from-blank/change-screen-blank.png)

## <a name="add-and-configure-a-form"></a>Agregar y configurar un formulario
1. En la pestaña **Insertar**, pulse o haga clic en **Formularios** y, a continuación, en **Editar**.

2. Mueva y cambie el tamaño del formulario para que cubra la mayor parte de la pantalla.

    ![Agregar un formulario](./media/get-started-create-from-blank/add-form.png)

    El formulario se denominará **Form1** de forma predeterminada a menos que ya haya agregado y quitado algún formulario. En ese caso, cambie el nombre del formulario a **Form1**.

3. Establezca la propiedad  **[DataSource](controls/control-form-detail.md)**  de **Form1** en **Schedule**.

4. Establezca la propiedad **Item** de **Form1** en esta expresión:
   <br>**BrowseGallery1.Selected**

5. En el panel derecho, haga clic o pulse en la casilla de cada campo para mostrarlo.

    ![Mostrar campos en el formulario](./media/get-started-create-from-blank/schedule-checkbox.png)

6. En la parte inferior de la pantalla, pulse o haga clic en **Agregar una tarjeta personalizada**.

    ![Agregar una tarjeta personalizada](./media/get-started-create-from-blank/add-custom-card.png)

7. Agregue un control **[Etiqueta](controls/control-text-box.md)** en la nueva tarjeta.

8. Establezca la propiedad **[AutoHeight](controls/control-text-box.md)** del nuevo control en **true** y su propiedad **[Text](controls/properties-core.md)** en esta fórmula:
   <br>**Form1.Error**

    La etiqueta mostrará cualquier error del formulario.

9. En la barra de navegación izquierda, pulse o haga clic en la miniatura de **ChangeScreen** para seleccionarla.

10. En la pestaña **Insertar**, pulse o haga clic en **Iconos**, pulse o haga clic en la opción para agregar una **flecha Anterior** y, a continuación, mueva la flecha a la esquina inferior izquierda de la pantalla.

11. Establezca la propiedad **[AlSeleccionar](controls/properties-core.md)** de la flecha en esta fórmula:

     **ResetForm(Form1);Navigate(ViewScreen,ScreenTransition.None)**

      Cuando el usuario pulse o haga clic en la flecha, la función **[Navigate](functions/function-navigate.md)** abre la pantalla **ViewScreen**.

12. Agregue un control **[Botón](controls/control-button.md)** en el formulario y establezca la propiedad **[Text](controls/properties-core.md)** del botón en **"Save"**.

     ![Agregar un botón para guardar](./media/get-started-create-from-blank/add-save-button.png)

13. Establezca la propiedad **[OnSelect](controls/properties-core.md)** del botón en esta fórmula:

    **SubmitForm(Form1); If(Form1.ErrorKind = ErrorKind.None, Navigate(ViewScreen, ScreenTransition.None))**

    Cuando el usuario hace clic o pulsa el botón, la función **[SubmitForm](functions/function-form.md)** guarda los cambios en el origen de datos y la pantalla **ViewScreen** vuelve a aparecer.

14. En la parte inferior de la pantalla, agregue otro botón, establezca su propiedad **[Text](controls/properties-core.md)** en **"Remove"** y establezca la propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:

    **Remove(Schedule,BrowseGallery1.Selected);<br>If(IsEmpty(Errors(Schedule)),Navigate(ViewScreen,ScreenTransition.None))**

    Cuando el usuario hace clic o pulsa este botón, la función **[Remove](functions/function-remove-removeif.md)** quita el registro y la pantalla **ViewScreen** vuelve a aparecer.

15. Establezca la propiedad **[Visible](controls/properties-core.md)** del botón **Remove** en esta fórmula:
    <br>**Form1.Mode=FormMode.Edit**

    Este paso oculta el botón **Quitar** cuando el usuario está creando un registro.

    La pantalla **ChangeScreen** coincide con este ejemplo:

    ![Pantalla ChangeScreen final](./media/get-started-create-from-blank/changescreen-final.png)

## <a name="set-navigation-from-viewscreen"></a>Establecer navegación desde ViewScreen
1. En la barra de navegación izquierda, pulse o haga clic en la miniatura superior de **ViewScreen**.

    ![Abrir ViewScreen](./media/get-started-create-from-blank/select-viewscreen.png)

2. Pulse o haga clic en la **flecha Siguiente** para ir al primer registro de la galería.

    ![Flecha siguiente](./media/get-started-create-from-blank/next-arrow.png)

3. Establezca la propiedad **[OnSelect](controls/properties-core.md)** de la flecha en esta fórmula:

    **Navigate(ChangeScreen,ScreenTransition.None)**

4. En la esquina superior derecha, pulse o haga clic en el icono del signo más.

    ![Agregar registro](./media/get-started-create-from-blank/add-record.png)

5. Establezca la propiedad **[OnSelect](controls/properties-core.md)** del icono seleccionado en esta fórmula:

    **NewForm(Form1);Navigate(ChangeScreen,ScreenTransition.None)**`

     Cuando el usuario hace clic o pulsa este icono, aparece la pantalla **ChangeScreen** con los campos vacíos, de forma que el usuario puede crear un registro más fácilmente.

## <a name="run-the-app"></a>Ejecutar la aplicación
A medida que personaliza la aplicación, pruebe los cambios mediante la ejecución de la aplicación en el modo de vista previa como se describe en los pasos de esta sección.

1. En la barra de navegación izquierda, pulse o haga clic en la miniatura superior para seleccionar **ViewScreen**.

    ![Seleccionar ViewScreen](./media/get-started-create-from-blank/select-viewscreen.png)

2. Abra el modo de vista previa presionando F5 (o haga clic o pulse en el icono de **vista previa** situado cerca de la esquina superior derecha).

    ![Abrir el modo de vista previa](./media/get-started-create-from-blank/open-preview.png)

3. Haga clic o pulse en la flecha siguiente para que un registro muestre los detalles sobre él.

4. En la pantalla **ChangeScreen**, cambie la información de uno o varios campos y, a continuación, pulse o haga clic en **Guardar** para guardar los cambios, pulse o haga clic en **Quitar** para eliminar el registro.

5. Cierre el modo de vista previa presionando Esc (o haciendo clic o pulsando en el icono Cerrar en la barra de título).

    ![Cerrar el modo de vista previa](./media/get-started-create-from-blank/close-preview.png)

## <a name="next-steps"></a>Pasos siguientes
* Presione Ctrl-S para guardar la aplicación en la nube para que se pueda ejecutar desde otros dispositivos.
* [Comparta la aplicación](share-app.md) para que otras personas puedan ejecutarla.
* Obtenga más información sobre [galerías](add-gallery.md), [formularios](add-form.md) y [fórmulas](working-with-formulas.md).
