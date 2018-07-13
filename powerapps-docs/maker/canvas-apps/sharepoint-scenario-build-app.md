---
title: Creación de una aplicación para administrar proyectos | Microsoft Docs
description: En esta tarea, se va a crear una aplicación desde el principio. Esta aplicación permite a un usuario asignar un administrador a proyectos y actualizar los detalles de proyectos.
documentationcenter: na
author: mgblythe
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 06/12/2017
ms.author: mblythe
ms.openlocfilehash: fcf1bcec976e34f07745c315d75569bbc86e583f
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37899534"
---
# <a name="create-an-app-to-manage-projects"></a>Crear una aplicación para administrar proyectos
> [!NOTE]
> Este artículo forma parte de una serie de tutoriales acerca del uso de PowerApps, Microsoft Flow y Power BI con SharePoint Online. Asegúrese de leer la [introducción a la serie](sharepoint-scenario-intro.md) para hacerse una idea general, así como para obtener descargas relacionadas.

En esta tarea, se va a crear una aplicación desde el principio. Esta aplicación permite a un usuario asignar un administrador a proyectos y actualizar los detalles de proyectos. Va a ver algunos de los mismos controles y fórmulas que en la primera aplicación, pero creará más partes de la aplicación en esta ocasión. El proceso es más complejo, pero aprenderá más, por lo que el equilibrio debería ser razonable.

> [!TIP]
> El [paquete de descarga](https://aka.ms/o4ia0f) de este escenario incluye una versión terminada de esta aplicación: project-details-app.msapp.

## <a name="quick-review-of-powerapps-studio"></a>Repaso rápido de PowerApps Studio
PowerApps Studio tiene tres paneles y una cinta de opciones que hacen que crear aplicaciones sea similar a crear un conjunto de diapositivas en PowerPoint:

1. Barra de navegación izquierda, que muestra una vista jerárquica de todas las pantallas y los controles de la aplicación, así como miniaturas de las pantallas.
2. Panel central, que contiene la pantalla de la aplicación con la que está trabajando.
3. Panel derecho, donde se establecen opciones como los orígenes de datos y el diseño.
4. Lista desplegable Propiedad, donde se seleccionan las propiedades a las que se aplican las fórmulas.
5. Barra de fórmulas, donde se agregan las fórmulas (como en Excel) que definen el comportamiento de la aplicación.
6. Cinta de opciones, donde puede agregar controles y personalizar los elementos de diseño.

![PowerApps Studio](./media/sharepoint-scenario-build-app/04-00-00-powerapps-studio.png)

## <a name="step-1-create-screens"></a>Paso 1: Creación de pantallas
Una vez terminado el repaso, empiece a crear una aplicación.

### <a name="create-and-save-the-app"></a>Crear y guardar la aplicación
1. En PowerApps Studio, pulse o haga clic en **Nuevo**, en **Aplicación vacía** y en **Diseño de teléfono**.
   
    ![Aplicación vacía, diseño de teléfono](./media/sharepoint-scenario-build-app/04-01-01-blank-phone-app.png)
2. Pulse o haga clic en **Archivo**, lo que abre en una pestaña **Configuración de la aplicación**. Escriba el nombre "Project Management app".
   
    ![Nombre de la aplicación](./media/sharepoint-scenario-build-app/04-01-02-app-name.png)
3. Pulse o haga clic en **Guardar como**, compruebe que la aplicación se guardará en la nube y haga clic en **Guardar** en la esquina inferior derecha.
   
    ![Guardar en la nube](./media/sharepoint-scenario-build-app/04-01-03-save-to-cloud.png)

4. Haga clic o pulse ![en Icono Volver a la aplicación](./media/sharepoint-scenario-build-app/icon-back-to-app.png) para volver a la aplicación.

### <a name="add-four-screens-to-the-app"></a>Agregar cuatro pantallas a la aplicación
En este paso, se van a crear cuatro pantallas en blanco para la aplicación. Se usarán diseños de pantalla diferentes, según el propósito de la pantalla. Se agregarán más pantallas en pasos posteriores.

| **Pantalla** | **Propósito** |
| --- | --- |
| **SelectTask** |Pantalla de apertura; navegar a otras pantallas. |
| **AssignManager** |Asignar un administrador a un proyecto aprobado. |
| **ViewProjects** |Ver una lista de proyectos, con información de resumen. |
| **UpdateDetails** |Ver y actualizar los detalles de un proyecto. |

1. En la pestaña **Inicio**, pulse o haga clic en **Nueva pantalla** y en **Pantalla desplazable**.
   
    ![Pantalla desplazable](./media/sharepoint-scenario-build-app/04-01-03a-scrollable-screen.png)
2. Cambie el nombre de la pantalla a **SelectTask**.
   
    ![Cambiar el nombre de pantalla](./media/sharepoint-scenario-build-app/04-01-04-rename-screen.png)
3. Cree y cambie el nombre de pantallas adicionales:
   
   1. Pulse o haga clic en **Nueva pantalla** y en **Pantalla desplazable**. Cambie el nombre de la pantalla a **AssignManager**.
   2. Pulse o haga clic en **Nueva pantalla** y en **Pantalla de lista**. Cambie el nombre de la pantalla a **ViewProjects**.
   3. Pulse o haga clic en **Nueva pantalla** y en **Pantalla de formulario**. Cambie el nombre de la pantalla a **UpdateDetails**.
4. Seleccione los puntos suspensivos (**…**) junto a **Screen1** y pulse o haga clic en **Eliminar**.
   
    ![Eliminar pantalla](./media/sharepoint-scenario-build-app/04-01-04a-delete-screen.png)

Ahora la aplicación debería parecerse a la siguiente imagen.

![Todas las pantallas de la aplicación](./media/sharepoint-scenario-build-app/04-01-05-all-screens.png)

## <a name="step-2-connect-to-a-sharepoint-list"></a>Paso 2: Conexión a una lista de SharePoint
En este paso, se conectará a la lista de SharePoint **Detalles del producto**. Solo se usa una lista en esta aplicación, pero puede conectarse fácilmente a ambas si desea ampliarla.

1. En la barra de navegación izquierda, pulse o haga clic en la pantalla **SelectTask**.
2. En el panel derecho, pulse o haga clic en **Agregar origen de datos**.
   
    ![Conectarse a datos](./media/sharepoint-scenario-build-app/04-02-01-connect.png)
3. Pulse o haga clic en **Nueva conexión**.
   
    ![Nueva conexión](./media/sharepoint-scenario-build-app/04-02-02-new-connection.png)
4. Pulse o haga clic en **SharePoint**.
   
    ![Conexión de SharePoint](./media/sharepoint-scenario-build-app/04-02-03-sharepoint-connection.png)
5. Seleccione **Conectar directamente (servicios en la nube)** y pulse o haga clic en **Crear**.
   
    ![Conectar directamente (servicios en la nube)](./media/sharepoint-scenario-build-app/04-02-03a-sharepoint-cloud.png)
6. Escriba una dirección URL de SharePoint y pulse o haga clic en **Ir**.
   
    ![Dirección URL de SharePoint para la conexión](./media/sharepoint-scenario-build-app/04-02-04-sharepoint-url.png)
7. Seleccione la lista **Project Details** y pulse o haga clic en **Conectar**.
   
    ![Seleccionar la lista Project Details](./media/sharepoint-scenario-build-app/04-02-05-sharepoint-lists.png)
   
    La pestaña **Orígenes de datos** en el panel derecho muestra ahora la conexión que ha creado.
   
    ![Pestaña Orígenes de datos](./media/sharepoint-scenario-build-app/04-02-06-data-sources.png)

## <a name="step-3-build-the-selecttask-screen"></a>Paso 3: Preparación de la pantalla SelectTask
En este paso, se proporciona una forma de navegar hasta las restantes pantallas de la aplicación mediante el uso de algunos de los controles, las fórmulas y las opciones de formato que proporciona PowerApps.

### <a name="update-the-title-and-insert-introductory-text"></a>Actualizar el título e insertar el texto de introducción
1. En la barra de navegación izquierda, seleccione la pantalla **SelectTask**.
2. En el panel central, seleccione el valor predeterminado **[Título]** y, en la barra de fórmulas, actualice la propiedad **Texto** a "Contoso Project Management".
   
    ![Propiedad Texto en la barra de fórmulas](./media/sharepoint-scenario-build-app/04-03-02-text-property.png)
3. En la pestaña **Insertar**, pulse o haga clic en **Etiqueta** y arrastre la etiqueta debajo del título superior.
   
    ![Agregar etiqueta](./media/sharepoint-scenario-build-app/04-03-03-text-default.png)
4. En la barra de fórmulas, establezca las siguientes propiedades para la etiqueta:
   
   * Propiedad **Color** = **GrisOscuro**

   * Propiedad **Tamaño** = **18**

   * Propiedad **Texto** = "**Click or tap a task to continue…"**
     
     ![Actualizar el texto de la etiqueta](./media/sharepoint-scenario-build-app/04-03-04-text-updated.png)

### <a name="add-two-navigation-buttons"></a>Agregar dos botones de navegación
1. En la pestaña **Insertar**, pulse o haga clic en **Botón** y arrastre el botón debajo de la etiqueta.
   
    ![Botón Agregar](./media/sharepoint-scenario-build-app/04-03-05-button-default.png)
2. En la barra de fórmulas, establezca las siguientes propiedades para el botón:
   
   * Propiedad **AlSeleccionar** = **Navigate(AssignManager, Fade)**. Cuando ejecute la aplicación y haga clic en este botón, irá a la segunda pantalla de la aplicación, con una transición de fundido entre las pantallas.

   * Propiedad **Texto** = **"Assign Manager"**

3. Cambie el tamaño del botón para dar cabida al texto.
   
    ![Actualizar texto del botón](./media/sharepoint-scenario-build-app/04-03-06-button-updated.png)
4. Inserte otro botón con las siguientes propiedades:
   
   * Propiedad **AlSeleccionar** = **Navigate(ViewProjects, Fade)**.

   * Propiedad **Texto** = **"Update Details"**
     
     ![Actualizar texto del botón](./media/sharepoint-scenario-build-app/04-03-08-buttons-final.png)
     
     > [!NOTE]
     > El botón se etiqueta como **Update Details**, pero primero va a ir a la pantalla **ViewProjects** para seleccionar un proyecto para actualizar.

### <a name="run-the-app"></a>Ejecutar la aplicación
La aplicación aún no hace mucho, pero se puede ejecutar si así lo desea:

1. Pulse o haga clic en la pantalla **SelectTask** (la aplicación siempre se inicia desde la pantalla seleccionada en el modo de vista previa de PowerApps Studio).

2. Haga clic o pulse ![Icono Ejecutar aplicación](./media/sharepoint-scenario-build-app/icon-run-arrow.png) en la esquina superior derecha para ejecutar la aplicación.

3. Pulse o haga clic en uno de los botones para ir a otra pantalla.

4. Haga clic o pulse ![en Icono Cerrar vista previa de aplicación](./media/sharepoint-scenario-build-app/icon-close-preview.png) en la esquina superior derecha para cerrar la aplicación.

## <a name="step-4-build-the-assignmanager-screen"></a>Paso 4: Preparación de la pantalla AssignManager
En este paso, se va a usar una galería para mostrar todos los proyectos que se han aprobado pero aún carecen de administrador. Se agregarán otros controles, para que pueda asignar un administrador.

> [!NOTE]
>  Más adelante, se va a crear en la aplicación una página que permite editar todos los campos de un proyecto (incluido el de administrador), pero también podría estar bien crear una pantalla como esta.

1. Guarde los cambios que haya realizado hasta ahora.

2. En la barra de navegación izquierda, pulse o haga clic en la pantalla **AssignManager**.

### <a name="update-the-title-and-insert-introductory-text"></a>Actualizar el título e insertar el texto de introducción

1. Cambie **[Título]** a **Assign Manager**.

2. Agregue una etiqueta con las siguientes propiedades:
   
   * Propiedad **Color** = **GrisOscuro**

   * Propiedad **Tamaño** = **18**

   * Propiedad **Texto** = "**Select a project, then assign a manager"**
     
     ![Diseño de Assign Manager](./media/sharepoint-scenario-build-app/04-04-01-layout.png)

### <a name="add-a-back-arrow-to-return-to-the-selecttask-screen"></a>Agregar una flecha Atrás para volver a la pantalla SelectTask

1. Pulse o haga clic en la barra azul en la parte superior de la pantalla.

2. En la pestaña **Insertar**, pulse o haga clic en **Iconos** y en **Izquierda**.
   
    ![Insertar flecha izquierda](./media/sharepoint-scenario-build-app/04-04-02-icon-left.png)

3. Mueva la flecha al lado izquierdo de la barra azul y establezca las siguientes propiedades:
   
   * Propiedad **Color** = **Blanco**

   * Propiedad **Alto** = **40**

   * Propiedad **AlSeleccionar** = **Navigate(SelectTask, Fade)**

   * Propiedad **Ancho** = **40**
     
     ![Agregar botón Atrás](./media/sharepoint-scenario-build-app/04-04-03-left-arrow.png)

### <a name="add-and-modify-a-gallery"></a>Agregar y modificar una galería

1. En la pestaña **Insertar**, pulse o haga clic en **Galería** y en **Vertical**.
   
    ![Agregar una galería vertical](./media/sharepoint-scenario-build-app/04-04-04-gallery.png)

2. Seleccione **Título, subtítulo y cuerpo** en el menú **Diseño** en el panel derecho. 
   
    ![Cambiar el diseño de la galería](./media/sharepoint-scenario-build-app/04-04-04a-gallery-layout.png)
   
    La galería tiene ahora el diseño correcto, pero aún contiene el texto de ejemplo predeterminado. Esto se va a solucionar a continuación.
   
    ![Galería con texto predeterminado](./media/sharepoint-scenario-build-app/04-04-05-gallery-default.png)

3. Establezca las siguientes propiedades para la galería:
   
   * Propiedad **GrosorDelBorde** = **1**

   * Propiedad **EstiloDelBorde** = **Punteado**

   * Propiedad **Elementos** = **Filter('Project Details', PMAssigned="Unassigned")**. Solo se incluyen en la galería los proyectos que no tienen ningún administrador asignado.
     
     ![Galería con texto de lista](./media/sharepoint-scenario-build-app/04-04-06-gallery-updated.png)

4. En el panel derecho, actualice los campos para que coincidan con la siguiente lista:
   
   * **ApprovedDate**

   * **Status**

   * **Title**
     
     ![Campos de la galería](./media/sharepoint-scenario-build-app/04-04-07-gallery-fields.png)

5. Cambie el tamaño de las etiquetas en la galería según corresponda y quite la flecha del primer elemento de la galería (no es necesario salir de esta galería).
   
    ![Quitar icono de flecha](./media/sharepoint-scenario-build-app/04-04-07a-remove-arrow.png)
   
    Ahora la pantalla debería parecerse a la siguiente imagen.
   
    ![Galería con formato](./media/sharepoint-scenario-build-app/04-04-07b-gallery-size-text.png)

### <a name="change-the-color-of-an-item-if-its-selected"></a>Cambiar el color de un elemento si está seleccionado

1. Seleccione la galería y establezca la propiedad **RellenoDePlantilla** en **If (ThisItem.IsSelected=true, Orange, White)**.

2. Seleccione un elemento en la galería. Ahora la pantalla debería parecerse a la siguiente imagen.
   
    ![Galería con elemento seleccionado](./media/sharepoint-scenario-build-app/04-04-08-gallery-selected.png)

### <a name="add-a-label-text-input-and-ok-button-to-submit-manager-assignments"></a>Agregar una etiqueta, entrada de texto y un botón OK para asignaciones de administrador

1. Pulse o haga clic fuera de la galería en la que ha estado trabajando.

2. En la pestaña **Insertar**, pulse o haga clic en **Etiqueta**. Arrastre la etiqueta debajo de la galería, a la izquierda. Establezca las siguientes propiedades para la etiqueta:
   
   * Propiedad **Tamaño** = **20**

   * Propiedad **Texto** = **"Manager:"**
   
   ![Agregar la etiqueta Manager](./media/sharepoint-scenario-build-app/04-04-09-controls-text.png)

3. En la pestaña **Insertar**, pulse o haga clic en **Texto** y en **Entrada de texto**. Arrastre la entrada de texto debajo de la galería, en el centro. Establezca las siguientes propiedades para la lista desplegable:
   
   * Propiedad **Predeterminado** = **""**

   * Propiedad **Alto** = **60**

   * Propiedad **Tamaño** = **20**

   * Propiedad **Ancho** = **250**
   
   ![Agregar entrada de texto](./media/sharepoint-scenario-build-app/04-04-10-controls-text-box.png)

4. En la pestaña **Insertar**, pulse o haga clic en **Botón**. Arrastre el botón debajo de la galería, a la derecha. Establezca las siguientes propiedades para el botón:
   
   * Propiedad **Alto** = **60**

   * Propiedad **AlSeleccionar** = **Patch('Project Details', LookUp('Project Details', ID = Gallery1.Selected.ID), {PMAssigned: TextInput1.Text})**. Para más información, consulte [Análisis en profundidad de una fórmula](#formula-deep-dive).

   * Esta fórmula actualiza la lista **Project Details** y establece un valor para el campo PMAssigned.

   * Propiedad **Tamaño** = **20**

   * Propiedad **Texto** = **"OK"**

   * Propiedad **Ancho** = **80**
   
   ![Agregar el botón OK](./media/sharepoint-scenario-build-app/04-04-11-controls-button.png)

Ahora la pantalla completada debería parecerse a la siguiente imagen.

![Pantalla Assign Manager completada](./media/sharepoint-scenario-build-app/04-04-12-complete.png)

## <a name="step-5-build-the-viewprojects-screen"></a>Paso 5: Preparación de la pantalla ViewProjects
En este paso, se cambiarán las propiedades para la galería en la pantalla **ViewProjects**. Esta galería muestra elementos de la lista **Project Details**. Seleccione un elemento en esta pantalla y edite los detalles en la pantalla **UpdateDetails**.

1. En la barra de navegación izquierda, pulse o haga clic en la pantalla **ViewProjects**.

2. Cambie **[Título]** a **"View Projects"**.

3. En la barra de navegación izquierda, pulse o haga clic en **BrowseGallery1﻿** en **ViewProjects**.

4. Seleccione **Título, subtítulo y cuerpo** en el menú **Diseño** en el panel derecho. 
   
    ![Cambiar el diseño de la galería](./media/sharepoint-scenario-build-app/04-04-04a-gallery-layout.png)
   
    La galería tiene ahora el diseño correcto, con el texto de ejemplo predeterminado.
   
    ![Galería con texto predeterminado](./media/sharepoint-scenario-build-app/04-04-04b-gallery-default.png)

5. Seleccione el botón Actualizar ![Icono Actualizar](./media/sharepoint-scenario-build-app/icon-refresh.png) y establezca su propiedad **AlSeleccionar** en **Refresh('Project Details')**.

6. Seleccione el botón Nuevo elemento ![Icono Agregar nuevo](./media/sharepoint-scenario-build-app/icon-add-item.png) y establezca su propiedad **AlSeleccionar** en **NewForm(EditForm1); Navigate(UpdateDetails, ScreenTransition.None)**.

### <a name="add-a-back-arrow-to-return-to-the-selecttask-screen"></a>Agregar una flecha Atrás para volver a la pantalla SelectTask

1. En la barra de navegación izquierda, pulse o haga clic en la pantalla **AssignManager**.

2. Seleccione la flecha Atrás que agregó allí y cópiela.

3. Pegue la flecha en la pantalla **ViewProjects** y colóquela a la izquierda del botón Actualizar. 
   
    ![Botón Atrás](./media/sharepoint-scenario-build-app/04-05-04-left-arrow-v.png)
   
    La acompañan todas sus propiedades, incluida la propiedad **AlSeleccionar** de **Navigate(SelectTask, Fade)**.

### <a name="change-the-data-source-for-the-browsegallery1-gallery"></a>Cambiar el origen de datos de la galería BrowseGallery1 (GaleríaExamen1)

1. Seleccione la galería **BrowseGallery1** y establezca la propiedad **Elementos** de la galería en **SortByColumns(Filter('Project Details', StartsWith(Title, TextSearchBox1.Text)), "Title", If(SortDescending1, Descending, Ascending))**.
   
    Esto establece el origen de datos de la galería en la lista **Project Details** y usa el campo **Título** para búsquedas y clasificación.

2. Seleccione ![Icono de flecha de detalles](./media/sharepoint-scenario-build-app/icon-details-arrow.png) en el primer elemento de la galería y establezca la propiedad **AlSeleccionar** en **Navigate(UpdateDetails, None)**.
   
    ![ Galería View Projects; primer elemento seleccionado](./media/sharepoint-scenario-build-app/04-05-05b-gallery-arrow-v.png)

3. En el panel derecho, actualice los campos para que coincidan con la siguiente lista:
   
   * **Status**

   * **PMAssigned**

   * **Title**
     
     ![Campos de la galería](./media/sharepoint-scenario-build-app/04-05-06-gallery-fields.png)
     
     Ahora la pantalla completada debería parecerse a la siguiente imagen.
     
     ![Pantalla View Project completada](./media/sharepoint-scenario-build-app/04-05-07-viewprojects-final.png)

## <a name="step-6-build-the-updatedetails-screen"></a>Paso 6: Preparación de la pantalla UpdateDetails
En este paso, se conectará el formulario de edición en la pantalla **UpdateDetails** al origen de datos, y se harán algunos cambios en propiedades y campos. En esta pantalla, puede editar los detalles de un proyecto que haya seleccionado en la pantalla **View Projects**.

1. En la barra de navegación izquierda, pulse o haga clic en la pantalla **UpdateDetails**.

2. Cambie **[Título]** a **"Update Details"**.

3. En la barra de navegación izquierda, pulse o haga clic en **EditForm1** en **UpdateDetails**.

4. Establezca las siguientes propiedades para el formulario:
   
   * Propiedad **OrigenDeDatos** = **'Project Details'**

   * Propiedad **Elemento** = **BrowseGallery1.Selected**

5. Con el formulario aún seleccionado, en el panel derecho, pulse o haga clic en la casilla de los siguientes campos, en el orden mostrado:
   
   * **Title**

   * **PMAssigned**

   * **Status**

   * **ProjectedStartDate**

   * **ProjectedEndDate**

   * **ProjectedDays**

   * **ActualDays**
     
     ![Editar campos de formulario](./media/sharepoint-scenario-build-app/04-06-03-edit-fields.png)
6. Seleccione el botón Cancelar ![Icono Cancelar](./media/sharepoint-scenario-build-app/icon-cancel.png) y establezca su propiedad **AlSeleccionar** en **ResetForm(EditForm1); Back()**.

7. Seleccione el botón Guardar ![Icono Guardar con marca de verificación](./media/sharepoint-scenario-build-app/icon-check-mark.png) y consulte la fórmula de **AlSeleccionar**: **SubmitForm(EditForm1)**. Como se va a usar el control de formulario de edición, se puede utilizar **Submit()** en lugar de **Patch()**, como antes.

La pantalla completada debería parecerse a la siguiente imagen (si los campos están vacíos, asegúrese de seleccionar un elemento en la pantalla **View Projects**).

![Pantalla Update Details completada](./media/sharepoint-scenario-build-app/04-06-06-edit-final.png)

## <a name="step-7-run-the-app"></a>Paso 7: Ejecución de la aplicación
Ahora que la aplicación está completa, ejecútela para ver cómo funciona. Se agregará un vínculo en el sitio de SharePoint a la aplicación. Podrá ejecutar la aplicación en el explorador, pero es posible que tenga que compartirla para que otras personas la ejecuten. Para más información, consulte [Uso compartido de las aplicaciones](https://powerapps.microsoft.com/guided-learning/learning-manage-share-apps).

### <a name="add-a-link-to-the-app"></a>Agregar un vínculo a la aplicación
1. En el iniciador de aplicaciones de Office 365, pulse o haga clic en **PowerApps**.
   
    ![PowerApps en el iniciador de aplicaciones de Office 365](./media/sharepoint-scenario-build-app/04-07-02a-waffle.png)

2. En PowerApps, pulse o haga clic en el botón de puntos suspensivos (**…**) para **Project Management app** y en **Abrir**.
   
    ![Seleccionar Project Management app](./media/sharepoint-scenario-build-app/04-07-02b-select-app.png)

3. Copie la dirección (URL) de la aplicación en el explorador.
   
    ![Copiar la dirección URL de la aplicación](./media/sharepoint-scenario-build-app/04-07-02ba-copy-url.png)

4. En SharePoint, pulse o haga clic en **EDITAR VÍNCULOS**.
   
    ![Editar vínculos de sitio de SharePoint](./media/sharepoint-scenario-build-app/04-07-02c-edit-links.png)

5. Pulse o haga clic en **(+) vínculo**.
   
    ![Agregar vínculo de la aplicación al sitio de SharePoint](./media/sharepoint-scenario-build-app/04-07-02d-add-link.png)

6. Escriba "Project Management app" y pegue la dirección para la aplicación.
   
    ![Editar propiedades del vínculo](./media/sharepoint-scenario-build-app/04-07-02e-link-dialog.png)

7. Pulse o haga clic en **Aceptar** y en **Guardar**.
   
    ![Guardar cambios de vínculo](./media/sharepoint-scenario-build-app/04-07-02f-save.png)

### <a name="assign-a-manager-to-a-project"></a>Asignar un administrador a un proyecto
Ahora que la aplicación está en este sitio de SharePoint, se va a asumir el rol de aprobador de proyecto; se buscarán proyectos sin administrador asignado y se asignará un administrador a uno de ellos. A continuación, se asumirá el rol de administrador del proyecto y se agregará alguna información sobre un proyecto que se tenga asignado.

1. En primer lugar, se va a echar un vistazo a la lista **Project Details** en SharePoint. Dos proyectos tienen el valor **Sin asignar** en la columna **PMAssigned**. Se verán en la aplicación.
   
    ![Proyectos sin asignar en la lista de SharePoint](./media/sharepoint-scenario-build-app/04-07-01-unassigned.png)

2. Pulse o haga clic en el vínculo que ha creado a la aplicación.

3. En la primera pantalla, pulse o haga clic en **Assign Manager**.
   
    ![Pantalla de introducción de la aplicación](./media/sharepoint-scenario-build-app/04-07-03-intro-screen.png)

4. En la pantalla **Assign Manager**, verá los dos proyectos sin asignar en la lista. Seleccione el proyecto **New BI software**.
   
    ![Galería con elemento seleccionado](./media/sharepoint-scenario-build-app/04-07-04-selected.png)

5. En la entrada de texto **Manager**, escriba "Joni Sherman" y haga clic en **OK**.
   
    Se aplica el cambio a la lista y la galería se actualiza, de forma que solo se muestra el proyecto sin asignar restante.
   
    ![Asignar administrador al proyecto](./media/sharepoint-scenario-build-app/04-07-05-updated.png)

6. Vuelva a la lista de SharePoint y actualice la página. Verá que la entrada del proyecto se ha actualizado con el nombre del administrador de proyecto.
   
    ![Administrador de proyecto asignado en la lista de SharePoint](./media/sharepoint-scenario-build-app/04-07-07-assigned.png)

### <a name="update-details-for-the-project"></a>Actualizar detalles para el proyecto

1. Pulse o haga clic en ![Icono Atrás](./media/sharepoint-scenario-build-app/icon-back.png) para volver a la primera pantalla y en **Update Details**.
   
   ![Pantalla de introducción de la aplicación](./media/sharepoint-scenario-build-app/04-07-08-intro-screen.png)

2. En la pantalla **View Projects**, escriba "New" en el cuadro de búsqueda.
   
   ![Buscar en la galería de aplicaciones](./media/sharepoint-scenario-build-app/04-07-09-search-new.png)

3. Haga clic en ![Icono de flecha de detalles](./media/sharepoint-scenario-build-app/icon-details-arrow.png) para el elemento **New BI software**.
   
   ![Elemento de la galería seleccionado](./media/sharepoint-scenario-build-app/04-07-10-select-project.png)

4. En la pantalla **Update Details**, establezca los valores siguientes:
   
   * El campo **ProjectedStartDate** = "3/6/2017"

   * El campo **ProjectedEndDate** = "3/24/2017"

   * El campo **ProjectedDays** = "15"
   
   ![Actualizar detalles de los elementos](./media/sharepoint-scenario-build-app/04-07-11-update.png)

5. Haga clic o pulse ![en Icono de marca de verificación](./media/sharepoint-scenario-build-app/icon-check-mark.png) para aplicar el cambio a la lista de SharePoint.

6. Cierre la aplicación y vuelva a la lista. Verá que la entrada del proyecto se ha actualizado con los cambios de fecha y día.
   
    ![Lista de SharePoint actualizada](./media/sharepoint-scenario-build-app/04-07-11-updated-list.png)

## <a name="formula-deep-dive"></a>Análisis en profundidad de una fórmula
Se trata de la segunda sección opcional sobre las fórmulas de PowerApps. En la primera, se analizó una de las fórmulas que PowerApps genera para la galería de examen en una aplicación de tres pantallas. En este análisis en profundidad, se examinará una fórmula que se usa para la pantalla **AssignManager** de nuestra segunda aplicación. Esta es la fórmula:

**Patch ( 'Project Details', LookUp ( 'Project Details', ID = Gallery1.Selected.ID ), {PMAssigned: TextInput1.Text} )**

¿Qué hace esta fórmula? Cuando selecciona un elemento en la galería y hace clic en el botón **Aceptar**, la fórmula actualiza la lista **Project Details**, lo que establece la columna **PMAssigned** en el valor que especifique en la entrada de texto. La fórmula usa funciones para realizar su trabajo:

* La función [**Revisión** ](functions/function-patch.md)modifica uno o varios registros de un origen de datos.

* La función [**Búsqueda** ](functions/function-filter-lookup.md)busca el primer registro de una tabla que satisfaga una fórmula.

Cuando se juntan las funciones en la fórmula, ocurre lo siguiente:

1. Al hacer clic en el botón **Aceptar**, se llama a la función **Revisión** para actualizar la lista **Project Details**.

2. En la función **Revisión**, la función **Búsqueda** identifica qué fila de la lista **Project Details** se debe actualizar. Para ello, compara el identificador del elemento seleccionado de la galería con el identificador de la lista. Por ejemplo, el identificador 12 significa que la entrada de **New BI software** debe actualizarse.

3. Ahora que la función **Revisión** tiene el identificador correcto, actualiza el campo **PMAssigned** con el valor de **TextInput1.Text**.

## <a name="next-steps"></a>Pasos siguientes
El siguiente paso en esta serie de tutoriales es [crear un informe de Power BI para analizar proyectos](sharepoint-scenario-build-report.md).

