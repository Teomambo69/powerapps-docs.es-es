---
title: Creación de una aplicación de Excel desde cero | Microsoft Docs
author: AFTOwen
ms.service: powerapps
ms.topic: conceptual
ms.component: canvas
ms.date: 04/23/2018
ms.author: anneta
ms.openlocfilehash: 29f07162ec2815398cda5bcc359f7388df261bc0
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="create-an-excel-app-from-scratch"></a>Creación de una aplicación de Excel desde cero
Cree su propia aplicación desde cero basándose en datos de Excel y en formato de tabla, y agregue luego datos de otros orígenes si lo desea. Si sigue este tutorial, creará una aplicación que contiene dos pantallas. En una pantalla, los usuarios pueden navegar a través de un conjunto de registros. En la otra pantalla, los usuarios pueden crear un registro, actualizar uno o varios campos de un registro o eliminar todo un registro. Este enfoque requiere más tiempo que la [creación de una aplicación automáticamente](get-started-create-from-data.md), pero los creadores de aplicaciones con experiencia pueden usarlo para crear aplicaciones mejor adaptadas a sus necesidades.

## <a name="prerequisites"></a>Requisitos previos
Para seguir exactamente los pasos de este tutorial, primero cree un archivo de Excel con estos datos de ejemplo.

1. Copie estos datos y péguelos en un archivo de Excel.

    | StartDay | StartTime | Volunteer | Backup |
    | --- | --- | --- | --- |
    | Sábado |10 a.m. a mediodía |Vasquez |Kumashiro |
    | Sábado |mediodía a 2 p.m. |Ice |Singhal |
    | Sábado |2 p.m. a 4 p.m. |Myk |Mueller |
    | Domingo |10 a.m. a mediodía |Li |Adams |
    | Domingo |10 a.m. a mediodía |Singh |Morgan |
    | Domingo |10 a.m. a mediodía |Batye |Nguyen |

2. Dé a los datos un formato de tabla, llamada **Programa**, para que PowerApps pueda analizar la información.

    Para obtener más información, vea [Dar formato a una tabla en Excel](how-to-excel-tips.md).

3. Guarde el archivo con el nombre **eventsignup.xls**, ciérrelo y, a continuación, cárguelo en una [cuenta de almacenamiento en la nube](connections/cloud-storage-blob-connections.md), como OneDrive.

> [!IMPORTANT]
> Para conocer los conceptos generales, puede utilizar su propio archivo de Excel y seguir este tutorial. No obstante, los datos del archivo de Excel deben tener formato de tabla. Para obtener más información, vea [Dar formato a una tabla en Excel](how-to-excel-tips.md).

## <a name="open-a-blank-app"></a>Abra una aplicación en blanco
1. Inicie sesión en [PowerApps](http://web.powerapps.com).

    ![Página principal de PowerApps](./media/get-started-create-from-blank/sign-in.png)

    Puede diseñar una aplicación desde cero para teléfonos o para otros dispositivos (por ejemplo, tabletas). Este tema se centra en el diseño de una aplicación para teléfonos.

1. En **Crear aplicaciones como estas**, mantenga el puntero sobre el icono **Iniciar desde cero**, seleccione el icono del teléfono y, después, seleccione **Crear esta aplicación**.

    ![Icono de la aplicación en blanco](./media/get-started-create-from-blank/blank-app.png)

    PowerApps Studio crea una aplicación en blanco para teléfonos.

1. Si aparece el cuadro de diálogo de **bienvenida a PowerApps Studio**, seleccione **Omitir**.

## <a name="connect-to-data"></a>Conectarse a datos
1. En el centro de la pantalla, seleccione **Conectarse a datos**.

1. En el panel **Datos**, seleccione la conexión de su cuenta de almacenamiento en la nube, si aparece. De lo contrario, siga estos pasos para agregar una conexión:

    1. Seleccione **Nueva conexión**, seleccione el icono de la cuenta de almacenamiento en la nube y, a continuación, seleccione **Crear**.
    2. Si se le solicita, proporcione las credenciales para esa cuenta.

1. En **Elegir un archivo de Excel**, escriba o pegue las primeras letras de **eventsignup** para filtrar la lista y, a continuación, seleccione el archivo que ha cargado.

1. En **Elegir una tabla**, active la casilla de **Programa** y, a continuación, seleccione **Conectar**.

## <a name="create-the-view-screen"></a>Creación de la pantalla de vista

1. En la pestaña **Inicio**, seleccione la flecha abajo junto a **Nueva pantalla** para abrir una lista de tipos de pantalla y, a continuación, seleccione **Pantalla de lista**.

    ![Agregar una pantalla de lista](./media/get-started-create-from-blank/add-list-screen.png)

    Se agrega una pantalla con varios controles predeterminados, como un cuadro de búsqueda y un control de **[Galería](controls/control-gallery.md)** . La galería cubre toda la pantalla en el cuadro de búsqueda.

2. Seleccione la galería haciendo clic o pulsando hacia el centro.

    Se muestra un cuadro de selección con indicadores alrededor de la galería.

    ![Agregar una pantalla de lista](./media/get-started-create-from-blank/select-gallery.png)

3. En el panel derecho, seleccione **CustomGallerySample** para abrir el panel **Datos**.

    ![Apertura del panel de datos](./media/get-started-create-from-blank/custom-gallery-sample.png)

1. En **Origen de datos**, seleccione la flecha hacia abajo para abrir la lista de orígenes de datos para la aplicación y, a continuación, seleccione **Programa**.

    ![Selección de origen de datos](./media/get-started-create-from-blank/select-schedule.png)

1. En **Diseño**, seleccione la flecha hacia abajo para abrir la lista de los diseños y, a continuación, seleccione **Título, subtítulo y cuerpo**.

    ![Seleccionar diseño](./media/get-started-create-from-blank/select-layout.png)

1. En **Title2** (Título 2), cambie la columna que aparece de **Backup** a **Volunteer**.

     ![Cambio de columna en etiqueta](./media/get-started-create-from-blank/change-title2.png)

1. Cierre el panel **Datos** seleccionando el icono Cerrar en la esquina superior derecha.

    La galería muestra el nombre de cada voluntario y el día y la hora del turno de ese voluntario.

    ![Datos de Programa en la galería no ordenados](./media/get-started-create-from-blank/show-data-unsorted.png)

4. Seleccione la galería y confirme que la lista de propiedades muestra **[Elementos](controls/properties-core.md)**.

    Como se muestra en la barra de fórmulas, el valor de esta propiedad es **Programa**.

    ![Datos de Programa en la galería no ordenados](./media/get-started-create-from-blank/set-property.png)

1. Cambie el valor de la propiedad **Elementos** copiando esta fórmula y pegándola en la barra de fórmulas:

    **SortByColumns(Search(Schedule, TextSearchBox1.Text, "Volunteer"), "Volunteer", If(SortDescending1, SortOrder.Descending, SortOrder.Ascending))**

    La galería muestra datos en orden alfabético por nombre de voluntario.

    ![Datos de Programa en la galería ordenados](./media/get-started-create-from-blank/show-data-sorted.png)

    Los usuarios pueden ordenar y filtrar la galería por nombre de voluntario tomando como base las funciones **SortByColumns** y **Search** en esa fórmula.

    - Si un usuario escribe al menos una letra en el cuadro de búsqueda, la galería mostrará únicamente aquellos registros en los que el campo **Volunteer** contenga el texto escrito por el usuario.
    - Si el usuario selecciona el botón de ordenación, la galería muestra los registros en orden ascendente o descendente (dependiendo de cuántas veces seleccione el botón el usuario) tomando como referencia el campo **Volunteer**.

    Para obtener más información sobre estas y otras funciones, vea la [referencia de fórmulas](formula-reference.md).

5. Escriba una **i** en el cuadro de búsqueda, seleccione el botón de ordenación haciendo clic o pulsando en él y, a continuación, selecciónelo otra vez (o un número impar de veces más).

    La galería muestra estos resultados.

    ![Ordenar y filtrar la galería](./media/get-started-create-from-blank/sort-filter.png)

1. Borre todo el texto del cuadro de búsqueda.

6. En la parte superior de la pantalla, seleccione el control **[Label](controls/control-text-box.md)** y luego reemplace **[Title]** (Título) por **View records** (Ver registros).

    ![Cambiar la barra de título](./media/get-started-create-from-blank/change-title-bar.png)

## <a name="create-the-change-screen"></a>Creación de la pantalla de cambio
1. En la pestaña **Inicio**, seleccione la flecha abajo junto a **Nueva pantalla** y, a continuación, seleccione **Pantalla de formulario**.

     ![Adición de pantalla de formulario](./media/get-started-create-from-blank/add-form-screen.png)

1. En la pantalla que acaba de agregar, seleccione **Conectarse a datos** para abrir el panel **Datos** y, a continuación, establezca el origen de datos en **Programa**.

1. En **Campos**, seleccione todas las casillas para mostrar todos los campos en el formulario.

     ![Mostrar campos](./media/get-started-create-from-blank/show-fields.png)

1. Arrastre campo **Volunteer** para que aparezca en la parte superior de la lista de campos.

     ![Cambio del orden de los campos](./media/get-started-create-from-blank/reorder-fields.png)

1. Seleccione el formulario y establezca su propiedad **Elemento** en la expresión escribiéndola o pegándola en la barra de fórmulas:<br>**BrowseGallery1.Selected**

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

1. Establezca la propiedad **OnSelect** para ese icono en esta fórmula:<br>**Refresh(Programa)**

    Cuando el usuario seleccione este icono, los datos de **Programa** se actualizarán desde el archivo de Excel.

    Para obtener más información sobre estas y otras funciones, vea la [referencia de fórmulas](formula-reference.md).

1. En la esquina superior derecha de **ViewScreen**, seleccione el icono del signo más.

    ![Agregar registro](./media/get-started-create-from-blank/add-record.png)

1. Establezca la propiedad **OnSelect** para ese icono en esta fórmula:<br>**NewForm(EditForm1);Navigate(ChangeScreen,ScreenTransition.None)**

    Cuando el usuario selecciona este icono, aparece la pantalla **ChangeScreen** con los campos vacíos, de forma que el usuario puede crear un registro más fácilmente.

1. Seleccione la flecha que apunta a la derecha para el primer registro de la galería.

    ![Selección de flecha](./media/get-started-create-from-blank/select-arrow.png)

1. Establezca la propiedad **OnSelect** de la flecha en esta fórmula:<br>**EditForm(EditForm1); Navigate(ChangeScreen, ScreenTransition.None)**

    Cuando el usuario selecciona este icono, **ChangeScreen** aparece con cada campo que muestra los datos para el registro seleccionado, por lo que el usuario puede editar o eliminar el registro más fácilmente.

## <a name="configure-icons-on-the-change-screen"></a>Configuración de iconos en la pantalla de cambio
1. En **ChangeScreen**, seleccione el icono "x" en la esquina superior izquierda.

    ![Icono Cancelar](./media/get-started-create-from-blank/cancel-icon.png)

1. Establezca la propiedad **OnSelect** para ese icono en esta fórmula:<br>**ResetForm(EditForm1);Navigate(ViewScreen, ScreenTransition.None)**

    Cuando el usuario selecciona este icono, los cambios realizados en esta pantalla por el usuario se descartan y se abre la pantalla de vista.

1. En la esquina superior derecha, seleccione el icono de marca de verificación.

    ![Icono de marca de verificación](./media/get-started-create-from-blank/checkmark-icon.png)

1. Establezca la propiedad **OnSelect** de la marca de verificación en esta fórmula:<br>**SubmitForm(EditForm1); Navigate(ViewScreen, ScreenTransition.None)**

    Cuando el usuario selecciona este icono, los cambios realizados en esta pantalla por el usuario se guardan y se abre la pantalla de vista.

1. En la pestaña **Insertar**, seleccione **Iconos** y, a continuación, el icono **Papelera**.

1. Establezca la propiedad **Color** del nuevo icono en **Blanco** y mueva el nuevo icono para que aparezca junto al icono de la marca de verificación.

    ![Icono de la papelera](./media/get-started-create-from-blank/trash-icon.png)

1. Establezca la propiedad **OnSelect** para el icono de papelera en esta fórmula:<br>**Remove(Schedule, BrowseGallery1.Selected); Navigate(ViewScreen, ScreenTransition.None)**

    Cuando el usuario selecciona este icono, el registro seleccionado se elimina del origen de datos y se abre la pantalla de vista.

## <a name="test-the-app"></a>Probar la aplicación
1. Seleccione **ViewScreen** y abra el modo de vista previa presionando F5 (o seleccionando el icono de **Vista previa** situado cerca de la esquina superior derecha).

    ![Abrir el modo de vista previa](./media/get-started-create-from-blank/open-preview.png)

1. Agregue un registro.

1. Actualice el registro que ha agregado y, a continuación, guarde los cambios.

1. Actualice el registro que ha agregado y, a continuación, cancele los cambios.

1. Elimine el registro que ha agregado.

1. Cierre el modo de vista previa presionando Esc (o seleccionando el icono de cerrar de la esquina superior derecha).

## <a name="next-steps"></a>Pasos siguientes
* Presione Ctrl-S para guardar la aplicación en la nube para que se pueda ejecutar desde otros dispositivos.
* [Comparta la aplicación](share-app.md) para que otras personas puedan ejecutarla.
* Obtenga más información sobre [funciones](working-with-formulas.md) como **Revisión**, que puede usar para administrar los datos sin necesidad de crear un formulario estándar.
