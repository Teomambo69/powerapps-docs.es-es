---
title: Crear un formulario de resumen en una aplicación de lienzo | Microsoft Docs
description: Crear un formulario de resumen en una aplicación de lienzo para administrar los datos de Northwind Traders
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/25/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5c40cb030241d142a2ee2a68d32f7fb839a350ff
ms.sourcegitcommit: 55bc11ac6a964f22301c9fdadb06ee34e1399f83
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66805405"
ms.PowerAppsDecimalTransform: true
---
# <a name="create-a-summary-form-in-a-canvas-app"></a>Crear un formulario de resumen en una aplicación de lienzo

Siga las instrucciones paso a paso para crear un formulario de resumen en una aplicación de lienzo para administrar datos ficticios de la base de datos de Northwind Traders. En este tema forma parte de una serie que se explica cómo compilar una aplicación empresarial en datos relacionales de Common Data Service. Para obtener mejores resultados, explore estos temas en esta secuencia:

1. [Crear una galería de orden](northwind-orders-canvas-part1.md).
2. Crear un formulario de resumen (**en este tema**).
3. [Crear una galería de detalle](northwind-orders-canvas-part3.md).

> [!div class="mx-imgBorder"]
> ![Definición de áreas de la pantalla](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>Requisitos previos

1. [Instalar las aplicaciones y la base de datos de Northwind Traders](northwind-install.md).
1. Revise el [información general de la aplicación de lienzo](northwind-orders-canvas-overview.md) de Northwind Traders.
1. [Creación de la Galería de orden](northwind-orders-canvas-part1.md) usted mismo, o abra el **Orders de Northwind (lienzo) - 2ª comenzar** aplicación, que ya contiene esa galería.

## <a name="add-a-title-bar"></a>Incorporación de una barra de título

En la parte superior de la aplicación, cree una barra de título, que contendrá los botones de acción al final de este tema.

1. En el **vista de árbol** panel, seleccione **Screen1** para asegurarse de que no agrega accidentalmente un control en la Galería de pedido:

    > [!div class="mx-imgBorder"]
    > ![Seleccione Screen1 en el panel de vista de árbol](media/northwind-orders-canvas-part2/titlebar-01.png)

1. En el **insertar** ficha, seleccione **etiqueta** para insertar un [ **etiqueta** ](controls/control-text-box.md) control:

    > [!div class="mx-imgBorder"]
    > ![Insertar una etiqueta](media/northwind-orders-canvas-part2/titlebar-02.png)

    La nueva etiqueta debe aparecer solo una vez, por encima de la galería. Si aparece en cada elemento de la galería, elimine la primera instancia de la etiqueta, asegúrese de que la pantalla está seleccionada (como se describe en el paso anterior) y, a continuación, vuelva a insertar la etiqueta.

1. Mover y cambiar el tamaño de la nueva etiqueta para abarcar la parte superior de la pantalla:

    > [!div class="mx-imgBorder"]
    > ![Mover y cambiar el tamaño de la etiqueta](media/northwind-orders-canvas-part2/titlebar-03.png)

1. Haga doble clic en el texto de la etiqueta y, a continuación, escriba **Orders de Northwind**.

    Como alternativa, modifique la **texto** propiedad en la barra de fórmulas para lograr el mismo resultado:

    > [!div class="mx-imgBorder"]
    > ![Cambiar el texto en la barra de título](media/northwind-orders-canvas-part2/titlebar-04.png)

1. En el **inicio** pestaña, la etiqueta de formato:
    - Aumentar el tamaño de fuente de 24 puntos.
    - Poner el texto en negrita.
    - Crear el texto en blanco.
    - Centrar el texto.
    - Agregar un relleno azul oscuro para el fondo.

    > [!div class="mx-imgBorder"]
    > ![Opciones de formato en la pestaña Inicio](media/northwind-orders-canvas-part2/titlebar-05.png)

## <a name="add-an-edit-form-control"></a>Agregar un control de formulario de edición

En esta sección, agregará controles para mostrar un resumen de cualquier pedido que el usuario selecciona en la galería.

1. En el **insertar** pestaña, inserte un [ **Editar formulario** ](controls/control-form-detail.md) control:

    > [!div class="mx-imgBorder"]
    > ![Agregar un control de formulario de edición](media/northwind-orders-canvas-part2/form-01.png)

    De forma predeterminada, el formulario aparece en la esquina superior izquierda, donde otros controles podrían hacer que sea difícil encontrar:

    > [!div class="mx-imgBorder"]
    > ![Control de formulario en la ubicación predeterminada de edición](media/northwind-orders-canvas-part2/form-02.png)

1. Mover y cambiar el tamaño del formulario para cubrir la esquina superior derecha de la pantalla en la barra de título:

    > [!div class="mx-imgBorder"]
    > ![Mover y cambiar el tamaño del control de formulario de edición](media/northwind-orders-canvas-part2/form-03.png)

1. En la barra de fórmulas, establezca el **DataSource** propiedad del formulario para este valor:

    ```powerapps-comma
    Orders
    ```

    > [!div class="mx-imgBorder"]
    > ![Establezca la propiedad DataSource del control de formulario de edición](media/northwind-orders-canvas-part2/form-04.png)

    Puede establecer la misma propiedad el **propiedades** pestaña cerca del borde derecho, pero este enfoque agrega los campos que no necesite al formulario. Si usa la barra de fórmulas, el formulario permanece vacío.

## <a name="add-and-arrange-fields"></a>Agregar y organizar campos

1. En el **propiedades** ficha cerca del borde derecho, seleccione **editar campos** para abrir el **campos** panel:

    > [!div class="mx-imgBorder"]
    > ![Abra el panel campos](media/northwind-orders-canvas-part2/form-05.png)

1. En el **campos** panel, seleccione **Agregar campo**y, a continuación, seleccione las casillas de verificación para el **cliente** y **empleado** campos.

    > [!div class="mx-imgBorder"]
    > ![Agregue los campos de clientes y empleados para el control de formulario de edición](media/northwind-orders-canvas-part2/form-06.png)

1. Desplácese hacia abajo hasta que estos campos aparecen y, a continuación, seleccione las casillas de verificación:

    - **Notas**
    - **Fecha de pedido**
    - **Número de pedido**
    - **Estado del pedido**
    - **Fecha de pago**

    > [!div class="mx-imgBorder"]
    > ![Agregar más de cinco campos para el control de formulario de edición](media/northwind-orders-canvas-part2/form-07.png)

1. En la parte inferior de la **campos** panel, seleccione **agregar**y, a continuación, cierre el **campos** panel.

    El formulario muestra siete campos:

    > [!div class="mx-imgBorder"]
    > ![Control de formulario de edición muestra siete campos](media/northwind-orders-canvas-part2/form-08.png)

    > [!NOTE]
    > Si cualquier campo muestra un icono rojo de error, es posible que han producido un problema cuando los datos se extraen desde el origen. Para resolver el error, actualice los datos:
    >
    > 1. En la pestaña **Vista**, seleccione **Orígenes de datos**.
    > 1. En el **datos** panel, seleccione **orígenes de datos**.
    > 1. Junto a **pedidos**, seleccione el botón de puntos suspensivos (...), seleccione **actualizar**y, a continuación, cierre el **datos** panel.
    >
    > Si el cuadro combinado para el nombre del cliente o empleado sigue mostrando un error, compruebe el **texto primario** y **SearchField** de cada cuadro, selecciónela y, a continuación, abrir el **datos** panel. Para el cuadro de cliente, deben establecerse ambos campos **nwind_company**. Para el cuadro de empleado, ambos campos deben establecerse en **nwind_lastname**.

1. Con el formulario seleccionado, cambie el número de columnas en el formulario de 3 a 12 en el **propiedades** ficha cerca del borde derecho.

    Este paso agrega flexibilidad como organice los campos:

    > [!div class="mx-imgBorder"]
    > ![A continuación, cambiar el número de columnas en el control de formulario de edición](media/northwind-orders-canvas-part2/form-08b.png)

    Muchos diseños de interfaz de usuario se basan en los diseños de 12 columnas ya que pueden incluir uniformemente las filas de 1, 2, 3, 4, 6 y 12 controles. En este tema, creará las filas que contienen 1, 2 o 4 controles.

1. Mover y cambiar el tamaño de los campos arrastrando sus controladores, tal como lo haría cualquier otro control, por lo que cada fila contiene estas tarjetas de datos en el orden especificado:

    - Primera fila: **Número de pedido**, **el estado del pedido**, **fecha de pedido**, y **fecha de pago**
    - Segunda fila: **Cliente** y **empleado**
    - Tercera fila: **Notas**

    > [!NOTE]
    > Le resultará más fácil de ampliar el **notas**, **cliente**, y **empleado** tarjetas de datos antes de organizarlos.

    > [!div class="mx-imgBorder"]
    > ![Mover y cambiar el tamaño de los campos](media/northwind-orders-canvas-part2/form-rearrange.gif)

    Obtener más información acerca de cómo organizar los campos de un formulario: [Información sobre el diseño de formularios de datos para las aplicaciones de lienzo](working-with-form-layout.md).

## <a name="hide-time-controls"></a>Ocultar controles de tiempo

En este ejemplo, no necesita las partes de tiempo de los campos de fecha porque ese nivel de granularidad puede distraer al usuario. Si las elimina, puede provocar problemas en las fórmulas que dependen de esos controles para actualizar los valores de fecha o determinar la posición de otro control en la tarjeta de datos. En su lugar, podrá ocultar los controles de tiempo estableciendo sus **Visible** propiedad.

1. En el **vista de árbol** panel, seleccione el **Order Date** tarjeta de datos.

    La tarjeta podría tener un nombre diferente, pero contiene **Order Date**.

1. Mientras mantiene presionada la tecla MAYÚS, seleccione los controles de hora, minuto y separador de dos puntos en el **Order Date** tarjeta de datos.

    > [!div class="mx-imgBorder"]
    > ![Seleccione los controles de tiempo en la tarjeta de la fecha de pedido](media/northwind-orders-canvas-part2/form-09.png)

1. Establecer los controles **Visible** propiedad **false**.

    Todos los controles seleccionados desaparecen del formulario:

    > [!div class="mx-imgBorder"]
    > ![Establezca la propiedad Visible en false.](media/northwind-orders-canvas-part2/form-10.png)

1. Cambiar el tamaño de la [ **selector de fecha** ](controls/control-date-picker.md) control para mostrar la fecha de finalización:

    > [!div class="mx-imgBorder"]
    > ![El tamaño del control de selector de fecha](media/northwind-orders-canvas-part2/form-11.png)

    A continuación, deberá repetir los últimos pasos para la **fecha pago** campo.

1. En el **vista de árbol** panel, seleccione el tiempo que se controla en el **fecha pago** tarjeta de datos:

    > [!div class="mx-imgBorder"]
    > ![Seleccione el control de tiempo en la tarjeta de pago de fecha](media/northwind-orders-canvas-part2/form-12.png)

1. Establecer los controles seleccionados **Visible** propiedad **false**:

    > [!div class="mx-imgBorder"]
    > ![Establezca la propiedad Visible en false.](media/northwind-orders-canvas-part2/form-13.png)

1. Cambiar el tamaño del selector de fecha en la **fecha de pago** tarjeta:

    > [!div class="mx-imgBorder"]
    > ![El tamaño del control de selector de fecha](media/northwind-orders-canvas-part2/form-14.png)

## <a name="connect-the-order-gallery"></a>Conectarse a la Galería de orden

1. En el **vista de árbol** panel, contraer el formulario para encontrar más fácilmente el nombre de la Galería de orden y, a continuación, si es necesario, cambie su nombre a **Gallery1**.

1. Establezca el formulario resumen **elemento** propiedad en esta expresión:

    ```powerapps-comma
    Gallery1.Selected
    ```

    > [!div class="mx-imgBorder"]
    > ![Establece la propiedad de elemento de formulario](media/northwind-orders-canvas-part2/form-15.png)

    El formulario muestra un resumen de orden de cualquier usuario de la aplicación se selecciona en la lista.

    > [!div class="mx-imgBorder"]
    > ![Seleccione un pedido en la lista para mostrar su introducción en el formulario](media/northwind-orders-canvas-part2/form-select.gif)

## <a name="replace-a-data-card"></a>Reemplazar una tarjeta de datos

**Número de pedido** es un identificador que Common Data Service se asigna automáticamente cuando se crea un registro. Este campo tiene un [ **entrada de texto** ](controls/control-text-input.md) control de forma predeterminada, pero va a reemplazar con una etiqueta para que el usuario no puede editar este campo.

1. Seleccione el formulario, seleccione **editar campos** en el **propiedades** pestaña cerca del borde derecho y, a continuación, seleccione el **número de pedido** campo:

    > [!div class="mx-imgBorder"]
    > ![Seleccione el campo de número de pedido](media/northwind-orders-canvas-part2/alt-01.png)

1. Abra el **tipo de Control** lista:

    > [!div class="mx-imgBorder"]
    > ![Abra el ** lista de Control de tipo **](media/northwind-orders-canvas-part2/alt-02,png)

1. Seleccione el **ver texto** tarjeta de datos:

    > [!div class="mx-imgBorder"]
    > ![Seleccione el ** tarjeta de datos de la vista texto **](media/northwind-orders-canvas-part2/alt-02b.png)

1. Cerrar la **campos** panel.

    El usuario ya no puede cambiar el número de pedido:

    > [!div class="mx-imgBorder"]
    > ![Número de pedido es de solo lectura](media/northwind-orders-canvas-part2/alt-03.png)

1. En el **inicio** , modifique el tamaño de fuente del número de pedido en 20 puntos para que sea más fácil encontrar el campo:

    > [!div class="mx-imgBorder"]
    > ![Cambiar el tamaño de fuente del número de pedido](media/northwind-orders-canvas-part2/alt-04.png)

## <a name="use-a-many-to-one-relationship"></a>Usar una relación varios a uno

El **pedidos** entidad tiene una relación de varios a uno con el **empleados** entidad: cada empleado puede crear muchos pedidos, pero cada pedido puede asignarse a un solo empleado. Cuando el usuario selecciona un empleado en el [ **cuadro combinado** ](controls/control-combo-box.md) control, su **seleccionados** propiedad proporciona registro completo de ese empleado desde el **empleados**  entidad. Como resultado, puede configurar un [ **imagen** ](controls/control-image.md) control para mostrar la imagen de cualquier empleado que el usuario selecciona en el cuadro combinado.

1. Seleccione el **empleado** tarjeta de datos:

    > [!div class="mx-imgBorder"]
    > ![Seleccione la ficha de datos de empleado](media/northwind-orders-canvas-part2/employee-01.png)

1. En el **avanzadas** pestaña cerca del borde derecho, desbloquear la tarjeta de datos para que pueda editar las fórmulas que estaban previamente de solo lectura:

    > [!div class="mx-imgBorder"]
    > ![Desbloquear la tarjeta de datos de empleados](media/northwind-orders-canvas-part2/employee-02.png)

1. En la tarjeta de datos, reduzca el ancho del cuadro combinado para dejar espacio a la imagen del empleado:

    > [!div class="mx-imgBorder"]
    > ![El tamaño del control de cuadro combinado](media/northwind-orders-canvas-part2/employee-03b.png)

1. En el **insertar** ficha, seleccione **Media** > **imagen**:

    > [!div class="mx-imgBorder"]
    > ![Insertar una imagen](media/northwind-orders-canvas-part2/employee-04.png)

    Aparece una imagen en la tarjeta de datos, que se expande para dar cabida a él:

    > [!div class="mx-imgBorder"]
    > ![Tarjeta de datos de empleados con control de imagen](media/northwind-orders-canvas-part2/employee-05.png)

1. Cambiar el tamaño de la imagen y muévalo a la derecha del cuadro combinado:

    > [!div class="mx-imgBorder"]
    > ![Mover y cambiar el tamaño del control de imagen](media/northwind-orders-canvas-part2/employee-06.png)

1. Establecer el **imagen** propiedad de la imagen en esta fórmula, reemplazando el número al final de DataCardValue si es necesario:

    ```powerapps-comma
    DataCardValue7.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > ![Establezca la propiedad Image de la imagen](media/northwind-orders-canvas-part2/employee-07.png)

    Aparece la imagen del empleado seleccionado.

1. Mientras mantiene presionada la tecla Alt, seleccione a otro empleado en el cuadro combinado para confirmar que la imagen también cambia.

    > [!div class="mx-imgBorder"]
    > ![Seleccione un empleado para mostrar la imagen del empleado](media/northwind-orders-canvas-part2/employee-select.gif)

## <a name="add-a-save-icon"></a>Agregar un icono de guardar

1. En el **vista de árbol** panel, seleccione **Screen1**y, a continuación, seleccione **insertar** > **iconos**  >  **Comprobar**:

    > [!div class="mx-imgBorder"]
    > ![Icono de marca de verificación INSERT](media/northwind-orders-canvas-part2/save-01.png)

    El [ **comprobar** ](controls/control-shapes-icons.md) icono aparece en la esquina superior izquierda de forma predeterminada, donde otros controles podrían dificultar el icono Buscar:

    > [!div class="mx-imgBorder"]
    > ![Icono en la ubicación predeterminada](media/northwind-orders-canvas-part2/save-02.png)

1. En el **inicio** , modifique la **Color** propiedad del icono en blanco, cambiar el tamaño del icono y muévalo cerca del borde derecho de la barra de título:

    > [!div class="mx-imgBorder"]
    > ![Configurar el color, tamaño y ubicación de la operación de guardar icono](media/northwind-orders-canvas-part2/save-03.png)

1. En el **vista de árbol** panel, confirme que es el nombre del formulario **Form1**y, a continuación, establezca el icono **OnSelect** propiedad en esta fórmula:

    ```powerapps-comma
    SubmitForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![Establece la operación de guardar propiedad OnSelect del icono](media/northwind-orders-canvas-part2/save-04.png)

    Cuando el usuario selecciona el icono, el [ **SubmitForm** ](functions/function-form.md) función recopila todos los valores modificados en el formulario y los envía al origen de datos. Marzo de puntos en la parte superior de la pantalla según los datos se envían y la Galería de orden refleja los cambios después de que finalice el proceso.

1. Establecer el icono **DisplayMode** propiedad en esta fórmula:

    ```powerapps-comma
    If( Form1.Unsaved; DisplayMode.Edit; DisplayMode.Disabled )
    ```

    > [!div class="mx-imgBorder"]
    > ![Establecer propiedad de DisplayMode del icono](media/northwind-orders-canvas-part2/save-05.png)

    Si se han guardado todos los cambios en el formulario, el icono está deshabilitado y aparece en el **DisabledColor**, que se va a configurar a continuación.

1. Establecer el icono **DisabledColor** este valor para propiedad:

    ```powerapps-comma
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![Establecer propiedad de DisabledColor del icono](media/northwind-orders-canvas-part2/save-06.png)

    El usuario puede guardar los cambios a un pedido seleccionando el icono de verificación, que, a continuación, se está deshabilitado y atenuado hasta que el usuario realiza otro cambio:

    > [!div class="mx-imgBorder"]
    > ![guardar los cambios](media/northwind-orders-canvas-part2/save-submit.gif)

## <a name="add-a-cancel-icon"></a>Agregar un icono Cancelar

1. En el **insertar** ficha, seleccione **iconos** > **cancelar**:

    > [!div class="mx-imgBorder"]
    > ![Agregar icono Cancelar](media/northwind-orders-canvas-part2/save-07.png)

    El icono aparece en la esquina superior izquierda de forma predeterminada, donde otros controles podrían dificultar el icono Buscar:

    > [!div class="mx-imgBorder"]
    > ![Icono Cancelar en la ubicación predeterminada](media/northwind-orders-canvas-part2/save-08.png)

1. En el **inicio** , modifique el icono **Color** propiedad en blanco, cambiar el tamaño del icono y muévalo a la izquierda del icono de verificación:

    > [!div class="mx-imgBorder"]
    > ![Cambiar el color, tamaño y ubicación del icono Cancelar](media/northwind-orders-canvas-part2/save-09.png)

1. Establecer el icono cancelar **OnSelect** propiedad en esta fórmula:

    ```powerapps-comma
    ResetForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![Establecer propiedad de OnSelect del icono de cancelación](media/northwind-orders-canvas-part2/save-10.png)

    El [ **ResetForm** ](functions/function-form.md) función descarta todos los cambios en el formulario, que lo devuelve a su estado original.

1. Establecer el icono cancelar **DisplayMode** propiedad en esta fórmula:

    ```powerapps-comma
    If( Form1.Unsaved Or Form1.Mode = FormMode.New; DisplayMode.Edit; DisplayMode.Disabled )
    ```

    > [!div class="mx-imgBorder"]
    > ![Establecer propiedad de DisplayMode del icono de cancelación](media/northwind-orders-canvas-part2/save-11.png)

    Esta fórmula difiere ligeramente de la otra para el icono de verificación. El icono Cancelar se deshabilitará si se guardaron todos los cambios o el formulario está en **New** modo, que permitiremos a continuación. En ese caso, **ResetForm** descarta el nuevo registro.

1. Establecer el icono cancelar **DisabledColor** este valor para propiedad:

    ```powerapps-comma
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![Establecer propiedad de DisabledColor del icono de cancelación](media/northwind-orders-canvas-part2/save-12.png)

    El usuario puede cancelar los cambios en un orden y los iconos de comprobación y cancelar están deshabilitados y atenuados si todos los cambios se han guardado:

    > [!div class="mx-imgBorder"]
    > ![Guardar y cancelar los cambios](media/northwind-orders-canvas-part2/save-cancel.gif)

## <a name="add-an-add-icon"></a>Agregar un icono de agregar

1. En el **insertar** ficha, seleccione **iconos** > **agregar**.

    > [!div class="mx-imgBorder"]
    > ![Insertar un icono de agregar](media/northwind-orders-canvas-part2/save-13.png)

    El **agregar** icono aparece en la esquina superior izquierda de forma predeterminada, donde otros controles podrían hacer que sea difícil encontrar:

    > [!div class="mx-imgBorder"]
    > ![Ubicación predeterminada de agregar icono](media/northwind-orders-canvas-part2/save-14.png)

1. En el **inicio** pestaña, establezca el **Color** propiedad del icono Agregar a blanco, cambiar el tamaño del icono y muévalo a la izquierda del icono Cancelar:

    > [!div class="mx-imgBorder"]
    > ![Cambiar el color, tamaño y ubicación del icono Agregar](media/northwind-orders-canvas-part2/save-15.png)

1. Establecer el icono Agregar **OnSelect** propiedad en esta fórmula:

    ```powerapps-comma
    NewForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![Establecer la propiedad OnSelect del icono de agregar](media/northwind-orders-canvas-part2/save-15b.png)

    El [ **NewForm** ](functions/function-form.md) función muestra un registro en blanco en el formulario.  

1. Establecer el icono Agregar **DisplayMode** propiedad en esta fórmula:

    ```powerapps-comma
    If( Form1.Unsaved Or Form1.Mode = FormMode.New; DisplayMode.Disabled; DisplayMode.Edit )
    ```

    > [!div class="mx-imgBorder"]
    > ![Establecer propiedad de DisplayMode del icono de agregar](media/northwind-orders-canvas-part2/save-16.png)

    La fórmula deshabilita el icono Agregar en estas condiciones:

    - El usuario realiza cambios, pero no guardar o cancelar, que es el comportamiento contrario de los iconos de comprobación y Cancelar.
    - El usuario selecciona el icono Agregar pero no realiza ningún cambio.

1. Establecer el icono Agregar **DisabledColor** este valor para propiedad:

    ```powerapps-comma
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![Establecer propiedad de DisabledColor del icono de agregar](media/northwind-orders-canvas-part2/save-17.png)

    El usuario puede crear un pedido si realiza ningún cambio guardar o cancelarán los cambios que han realizado. (Si el usuario selecciona este icono, puede seleccionar nuevo hasta que realice uno o varios cambios y, a continuación, guardarán o cancelar los cambios):

    > [!div class="mx-imgBorder"]
    > ![Crear un pedido](media/northwind-orders-canvas-part2/save-new.gif)

> [!NOTE]
> Si se crea y guarda un pedido, debe desplazarse hacia abajo en la Galería de orden para mostrar el nuevo orden. No tendrá un precio total porque aún no ha agregado algún detalle de pedidos.

## <a name="add-a-trash-icon"></a>Agregar un icono de Papelera

1. En el **insertar** ficha, seleccione **iconos** > **Papelera**.

    > [!div class="mx-imgBorder"]
    > ![Insertar un icono de Papelera](media/northwind-orders-canvas-part2/save-18.png)

    El **Papelera** icono aparece en la esquina superior izquierda de forma predeterminada, donde otros controles podrían hacer que sea difícil encontrar:

    > [!div class="mx-imgBorder"]
    > ![Ubicación predeterminada del icono Papelera](media/northwind-orders-canvas-part2/save-19.png)

1. En el **inicio** , modifique el icono de Papelera **Color** propiedad en blanco, cambiar el tamaño del icono y muévalo a la izquierda del icono de agregar:

    > [!div class="mx-imgBorder"]
    > ![Cambiar el color, tamaño y ubicación del icono de Papelera](media/northwind-orders-canvas-part2/save-20.png)

1. Establecer el icono de Papelera **OnSelect** propiedad en esta fórmula:

    ```powerapps-comma
    Remove( Orders; Gallery1.Selected )
    ```

    > [!div class="mx-imgBorder"]
    > ![Establezca la propiedad OnSelect del icono de Papelera](media/northwind-orders-canvas-part2/save-21.png)

    El [ **quitar** ](functions/function-remove-removeif.md) función quita un registro de un origen de datos. En esta fórmula, la función quita el registro que está seleccionado en la Galería de orden. El icono de Papelera aparece cerca del formulario de resumen (no en la Galería de orden) porque el formulario muestra más detalles sobre el registro, por lo que el usuario pueda identificar más fácilmente el registro que se eliminará la fórmula.

1. Establecer el icono de Papelera **DisplayMode** propiedad en esta fórmula:

    ```powerapps-comma
    If( Form1.Mode = FormMode.New; DisplayMode.Disabled; DisplayMode.Edit )
    ```

    > [!div class="mx-imgBorder"]
    > ![Establecer propiedad de DisplayMode del icono de Papelera](media/northwind-orders-canvas-part2/save-22.png)

    Esta fórmula deshabilita el icono de Papelera si el usuario está creando un registro. Hasta que el usuario guarda el registro, el **quitar** función no tiene ningún registro para eliminar.

1. Establecer el icono de Papelera **DisabledColor** este valor para propiedad:

    ```powerapps-comma
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![Establecer propiedad de DisabledColor del icono de Papelera](media/northwind-orders-canvas-part2/save-23.png)

    El usuario puede eliminar un pedido.

    > [!div class="mx-imgBorder"]
    > ![Eliminación de pedidos](media/northwind-orders-canvas-part2/save-delete.gif)

## <a name="summary"></a>Resumen

Para recapitular, ha agregado un formulario en el que el usuario puede mostrar y editar un resumen de cada pedido, y usar estos elementos:

- Un formulario que muestra datos de la **pedidos** entidad: **Form1.DataSource =** `Orders`
- Una conexión entre el formulario y la Galería de pedido: **Form1.Item =** `Gallery1.Selected`
- Un control alternativo para el **número de pedido** campo: **Texto de la vista**
- Una relación de varios a uno para mostrar la imagen del empleado en el **empleado** tarjeta de datos: `DataCardValue1.Selected.Picture`
- Un icono para guardar los cambios en un pedido: `SubmitForm( Form1 )`
- Un icono para cancelar los cambios en un orden: `ResetForm( Form1 )`
- Un icono para crear un pedido: `NewForm( Form1 )`
- Un icono para eliminar un pedido: `Remove( Orders; Gallery1.Selected )`

## <a name="next-step"></a>Paso siguiente

En el tema siguiente, agregará otra galería para mostrar los productos en cada pedido y podrá cambiar esos detalles mediante la [ **Patch** ](functions/function-patch.md) función.

> [!div class="nextstepaction"]
> [Creación de la Galería de detalle](northwind-orders-canvas-part3.md)
