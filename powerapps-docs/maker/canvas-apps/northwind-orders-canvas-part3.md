---
title: Crear una galería de detalle en una aplicación de lienzo | Microsoft Docs
description: Crear una galería de detalle en una aplicación de lienzo para administrar los datos de Northwind Traders
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
ms.openlocfilehash: 9549b8f389cf696cf3fc8e4659da6b418383ac6e
ms.sourcegitcommit: e85072f7a80da308c4caabe20adbf2509588ca57
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66760968"
ms.PowerAppsDecimalTransform: true
---
# <a name="create-a-detail-gallery-in-a-canvas-app"></a>Crear una galería de detalle en una aplicación de lienzo

Siga las instrucciones paso a paso para crear una galería de detalle en una aplicación de lienzo para administrar datos ficticios de la base de datos de Northwind Traders. En este tema forma parte de una serie que se explica cómo compilar una aplicación empresarial en datos relacionales de Common Data Service. Para obtener mejores resultados, explore estos temas en esta secuencia:

1. [Crear una galería de orden](northwind-orders-canvas-part1.md).
1. [Crear un formulario de resumen](northwind-orders-canvas-part2.md).
1. Crear una galería de detalle (**en este tema**).

> [!div class="mx-imgBorder"]
> ![Definición de áreas de la pantalla](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>Requisitos previos

Antes de empezar este tema, debe instalar la base de datos, como se describe anteriormente en este tema. Debe, a continuación, crear la Galería de orden y el formulario de resumen o abra el **Orders de Northwind (lienzo) - comenzar parte 3** aplicación, que ya contiene ese formulario y esa galería.

## <a name="create-another-title-bar"></a>Crear otra barra de título

1. En la parte superior de la pantalla, seleccione el [ **etiqueta** ](controls/control-text-box.md) control que actúa como una barra de título, cópielo presionando Ctrl-C y, a continuación, péguelo presionando Ctrl-V:

    > [!div class="mx-imgBorder"]
    > ![Copie y pegue la barra de título](media/northwind-orders-canvas-part3/details-01.png)

1. Cambiar el tamaño y mueva la copia para que aparezca justo debajo del formulario de resumen.

1. Quite el texto de la copia de cualquiera de estas maneras:

    - Haga doble clic en el texto para seleccionarlo y, a continuación, presione SUPR.
    - Establezca la etiqueta **texto** propiedad en una cadena vacía ( **""** ).

    > [!div class="mx-imgBorder"]
    > ![Quite el texto de la copia de la barra de título](media/northwind-orders-canvas-part3/details-02.png)

## <a name="add-a-gallery"></a>Agregar una galería

1. Insertar un [ **galería** ](controls/control-gallery.md) controlar con un **en blanco vertical** diseño:

    > [!div class="mx-imgBorder"]
    > ![Agregue una galería vertical en blanco](media/northwind-orders-canvas-part3/details-03.png)

    La galería nueva, que se mostrará los detalles de pedido, aparece en la esquina superior izquierda:

    > [!div class="mx-imgBorder"]
    > ![Ubicación predeterminada de la Galería de detalles del pedido](media/northwind-orders-canvas-part3/details-04.png)

1. Cerrar la **datos** panel y, a continuación, cambiar el tamaño y mueva la Galería de detalle a la esquina inferior derecha, debajo de la nueva barra de título:

    > [!div class="mx-imgBorder"]
    > ![Ubicación final de la Galería de detalles del pedido](media/northwind-orders-canvas-part3/details-05.png)

1. Establecer el **elementos** propiedad de la Galería de detalle en esta fórmula:

    ```powerapps-comma
    Gallery1.Selected.'Order Details'
    ```

    > [!div class="mx-imgBorder"]
    > ![Establezca la propiedad Items de la Galería de detalle](media/northwind-orders-canvas-part3/details-06.png)

    Si aparece un error, confirme que la Galería de orden se denomina **Gallery1** (en el **vista de árbol** panel cerca del borde izquierdo). Si esa galería tiene un nombre diferente, cambie su nombre **Gallery1**.

    Acaba de vincular las dos galerías. Cuando el usuario selecciona un pedido en la Galería de orden, esa selección identifica un registro en el **pedidos** entidad. Si contiene línea uno o varios elementos, el registro en el **pedidos** entidad esté vinculada a uno o más registros en el **detalles de pedidos** entidad y los datos de esos registros aparece en la Galería de detalle. Este comportamiento refleja la relación de uno a varios que se creó automáticamente entre el **pedidos** y **Order Details** entidades. La fórmula que especificó "lo guía" esa relación mediante la notación de puntos:

    > [!div class="mx-imgBorder"]
    > ![Relación de uno a varios entre las entidades de pedidos y los detalles del pedido](media/northwind-orders-canvas-part3/schema-orders-rel.png)

## <a name="show-product-names"></a>Mostrar nombres de producto

1. En la Galería de detalles, seleccione **agregar un elemento desde la pestaña Insertar** para seleccionar la plantilla de la Galería:

    > [!div class="mx-imgBorder"]
    > ![Seleccione la plantilla en la Galería de detalle](media/northwind-orders-canvas-part3/details-07.png)

    Asegúrese de que ha seleccionado la plantilla de galería en lugar de la galería misma. El cuadro de límite debe ser un poco dentro del límite de la galería y probablemente más corto que el alto de la galería. Insertar controles en esta plantilla, se repiten para cada elemento de la galería.

1. En el **insertar** pestaña, inserte una etiqueta en la Galería de detalle.

    La etiqueta debe aparecer dentro de la Galería; Si no es así, vuelva a intentarlo, pero no olvide seleccionar la plantilla de la galería antes de insertar la etiqueta.

    > [!div class="mx-imgBorder"]
    > ![Agregar una etiqueta a la Galería de detalle](media/northwind-orders-canvas-part3/details-08.png)

1. Establecer la nueva etiqueta **texto** propiedad en esta fórmula:

    ```powerapps-comma
    ThisItem.Product.'Product Name'
    ```

    Si no hay texto aparece, seleccione la flecha para **orden 0901** cerca de la parte inferior de la Galería de orden.

1. Cambiar el tamaño de la etiqueta para que aparezca el texto completo:

    > [!div class="mx-imgBorder"]
    > ![Mostrar el nombre de producto en detalle de pedido](media/northwind-orders-canvas-part3/details-09.png)

    Esta expresión se recorre desde un registro en el **Order Details** entidad. El registro se mantiene en **ThisItem** over a la **productos del pedido** entidad a través de una relación varios a uno:

    > [!div class="mx-imgBorder"]
    > ![Relación de varios a uno entre la entidad Order Details y la entidad de producto del pedido](media/northwind-orders-canvas-part3/schema-orderdetails-rel.png)

    El **Product Name** se extraen campo (y otros campos que se va a usar):

    > [!div class="mx-imgBorder"]
    > ![Campos de la entidad de productos del pedido](media/northwind-orders-canvas-part3/schema-products-fields.png)

## <a name="show-product-images"></a>Mostrar imágenes de producto

1. En el **insertar** pestaña, inserte un [ **imagen** ](controls/control-image.md) control en la Galería de detalle:

    > [!div class="mx-imgBorder"]
    > ![Insertar control de imagen](media/northwind-orders-canvas-part3/details-10.png)

1. Cambiar el tamaño y mover la imagen y la etiqueta en paralelo.

    > [!TIP]
    > Para un mayor control sobre el tamaño y la posición de un control, comienza a cambiar el tamaño o moverlo sin tener que presionar la tecla Alt y, a continuación, continúe cambiar el tamaño o mover el control mientras mantiene presionada la tecla Alt:

    > [!div class="mx-imgBorder"]
    > ![Mueva el control de imagen](media/northwind-orders-canvas-part3/details-11.png)

1. Establecer la imagen **imagen** propiedad en esta fórmula:

    ```powerapps-comma
    ThisItem.Product.Picture
    ```

    De nuevo, la expresión hace referencia a un producto que ha asociado a este pedido detalle y extraer el **imagen** campo para mostrar.

    > [!div class="mx-imgBorder"]
    > ![Mostrar la imagen de producto](media/northwind-orders-canvas-part3/details-12.png)

1. Reducir el alto de la plantilla de la galería, lo que más de un **Order Detail** registro aparece a la vez:

    > [!div class="mx-imgBorder"]
    > ![Acorte la plantilla de la Galería](media/northwind-orders-canvas-part3/details-13.png)

## <a name="show-product-quantity-and-cost"></a>Mostrar el costo y la cantidad de productos

1. En el **insertar** pestaña, insertar otra etiqueta en la Galería de detalle y, a continuación, cambiar el tamaño y mover la nueva etiqueta a la derecha de la información del producto.

1. Establecer la nueva etiqueta **texto** propiedad en esta expresión:

    ```powerapps-comma
    ThisItem.Quantity
    ```

    Esta fórmula extrae información directamente desde el **Order Details** entidad (no se requiere ninguna relación).

    > [!div class="mx-imgBorder"]
    > ![Mostrar la cantidad de productos](media/northwind-orders-canvas-part3/details-13b.png) 

1. En el **inicio** , modifique la alineación de este control en **derecha**:

    > [!div class="mx-imgBorder"]
    > ![Cambiar la alineación](media/northwind-orders-canvas-part3/details-14.png)

1. En el **insertar** pestaña, insertar otra etiqueta en la Galería de detalle y, a continuación, cambiar el tamaño y mueva la etiqueta a la derecha de la etiqueta de cantidad.

1. Establecer la nueva etiqueta **texto** propiedad en esta fórmula:

    ```powerapps-comma
    Text( ThisItem.'Unit Price'; "[$-en-US]$ #,###.00" )
    ```

    Si no incluye la etiqueta de idioma ( **[$-en-US]** ), se agregarán según su idioma y región. Si usa una etiqueta de idioma diferente, deseará quitar la **$** justo después del corchete de cierre ( **]** ) y, a continuación, agregue su propio símbolo de moneda en dicha posición.

    > [!div class="mx-imgBorder"]
    > ![Mostrar el precio unitario](media/northwind-orders-canvas-part3/details-15.png)

1. En el **inicio** , modifique la alineación de este control en **derecha**:

    > [!div class="mx-imgBorder"]
    > ![Cambiar la alineación](media/northwind-orders-canvas-part3/details-16.png)

1. En el **insertar** pestaña, inserte otro control de etiqueta en la Galería de detalle y, a continuación, cambiar el tamaño y mover la nueva etiqueta a la derecha del precio unitario.

1. Establecer la nueva etiqueta **texto** propiedad en esta fórmula:

    ```powerapps-comma
    Text( ThisItem.Quantity * ThisItem.'Unit Price'; "[$-en-US]$ #,###.00" )
    ```

    Nuevamente, si no incluye la etiqueta de idioma ( **[$-en-US]** ), se agregarán según su idioma y región. Si la etiqueta es diferente, deseará utilizar su propio símbolo de moneda en lugar de la **$** justo después del corchete de cierre ( **]** ).

    > [!div class="mx-imgBorder"]
    > ![Mostrar el precio total](media/northwind-orders-canvas-part3/details-17.png)

1. En el **inicio** , modifique la alineación de este control en **derecha**:

    > [!div class="mx-imgBorder"]
    > ![Cambiar la alineación](media/northwind-orders-canvas-part3/details-18.png)

    Agregar controles a la Galería de detalle ya ha terminado por ahora.

1. En el **vista de árbol** panel, seleccione **Screen1** para asegurarse de que ya no está seleccionada la Galería de detalle.

## <a name="add-text-to-the-new-title-bar"></a>Agregar texto a la nueva barra de título

1. En el **insertar** pestaña, inserte otra etiqueta en la pantalla:

    > [!div class="mx-imgBorder"]
    > ![Insertar etiqueta](media/northwind-orders-canvas-part3/details-19.png)

1. Cambiar el tamaño y mover la nueva etiqueta por encima de las imágenes de los productos en la segunda barra de título y, a continuación, cambie el color del texto en blanco en el **inicio** ficha.

1. Haga doble clic en el texto de la etiqueta y, a continuación, escriba **producto**:

    > [!div class="mx-imgBorder"]
    > ![Cambiar el texto de etiqueta al producto](media/northwind-orders-canvas-part3/details-20.png)

1. Copie y pegue la etiqueta del producto y, a continuación, cambiar el tamaño y mueva la copia encima de la columna de cantidad.

1. Haga doble clic en el nuevo texto de la etiqueta y, a continuación, escriba **cantidad**:

    > [!div class="mx-imgBorder"]
    > ![Cambiar el texto de la etiqueta a Quantity](media/northwind-orders-canvas-part3/details-21.png)

1. Copie y pegue la etiqueta de la cantidad y, a continuación, cambiar el tamaño y mueva la copia encima de la columna precio unitario.

1. Haga doble clic en el nuevo texto de la etiqueta y, a continuación, escriba **precio unitario**:

    > [!div class="mx-imgBorder"]
    > ![Cambiar el texto de la etiqueta a precio unitario](media/northwind-orders-canvas-part3/details-22.png)

1. Copie y pegue la etiqueta del precio de venta y, a continuación, cambiar el tamaño y mueva la copia por encima de la columna precio total.

1. Haga doble clic en el texto de la nueva etiqueta y, a continuación, escriba **extendido**:

    > [!div class="mx-imgBorder"]
    > ![Cambiar el texto de la etiqueta a extendida](media/northwind-orders-canvas-part3/details-23.png)

## <a name="display-order-totals"></a>Mostrar los totales de pedido

1. Reducir el alto de la Galería de detalle para dejar espacio para los totales de pedidos en la parte inferior de la pantalla:

    > [!div class="mx-imgBorder"]
    > ![Acorte la Galería de detalles del pedido](media/northwind-orders-canvas-part3/sum-01.png)

1. Copie y pegue la barra de título en el medio de la pantalla y, a continuación, mueva la copia a la parte inferior de la pantalla:

    > [!div class="mx-imgBorder"]
    > ![Barra de título de copiar y mover copia hasta el borde inferior](media/northwind-orders-canvas-part3/sum-02.png)

1. Copie y pegue la etiqueta del producto de la barra de título central y, a continuación, mueva la copia en la barra de título de la parte inferior, justo a la izquierda de la **cantidad** columna.

1. Haga doble clic en el nuevo texto de la etiqueta y, a continuación, escriba el texto siguiente:<br>**Totales de pedidos:**

    > [!div class="mx-imgBorder"]
    > ![Agregar etiqueta de totales de pedidos](media/northwind-orders-canvas-part3/sum-03.png)

1. Copie y pegue la etiqueta de totales de pedidos y, a continuación, cambiar el tamaño y mueva la copia a la derecha de la etiqueta de totales de pedidos.

1. Establecer la nueva etiqueta **texto** propiedad en esta fórmula:

    ```powerapps-comma
    Sum( Gallery1.Selected.'Order Details'; Quantity )
    ```

    Esta fórmula muestra una advertencia de delegación, pero puede ignorar porque ningún orden solo contendrá más de 500 productos.

1. En el **inicio** pestaña, establezca la alineación del texto de la etiqueta nueva en **derecha**:

    > [!div class="mx-imgBorder"]
    > ![Cambiar la alineación](media/northwind-orders-canvas-part3/sum-04.png)

1. Copie y pegue este control de etiqueta y, a continuación, cambiar el tamaño y mueva la copia en el **extendido** columna.

1. Establezca la copia **texto** propiedad en esta fórmula:

    ```powerapps-comma
    Text( Sum( Gallery1.Selected.'Order Details'; Quantity * 'Unit Price' ); "[$-en-US]$ #,###.00" )
    ```

    Esta fórmula muestra una advertencia de delegación, pero puede ignorar porque ningún orden solo contendrá más de 500 productos.

    > [!div class="mx-imgBorder"]
    > ![Mostrar el costo total de pedido](media/northwind-orders-canvas-part3/sum-05.png)

## <a name="add-space-for-new-details"></a>Agregar espacio para los nuevos detalles

En una galería, puede mostrar datos, pero no se puede actualizar o agregar registros. En la Galería de detalle, agregará un área donde el usuario puede configurar un registro en el **Order Details** entidad e inserción que se registre en un pedido.

1. Reducir el alto de la Galería de detalle suficiente para dejar espacio para un espacio de edición de elemento único en esa galería.

    En este espacio, agregará controles para que el usuario puede agregar un detalle de pedido:

    > [!div class="mx-imgBorder"]
    > ![Acorte la Galería de detalle](media/northwind-orders-canvas-part3/add-details-01.png)

1. En el **insertar** pestaña, insertar una etiqueta y, a continuación, cambiar el tamaño y muévalo a la Galería de detalle.

    > [!div class="mx-imgBorder"]
    > ![Insertar una etiqueta](media/northwind-orders-canvas-part3/add-details-02.png)

1. Haga doble clic en el texto de la nueva etiqueta y, a continuación, presione SUPR.

1. En el **inicio** pestaña, establezca la nueva etiqueta **rellenar** al color **LightBlue**:

    > [!div class="mx-imgBorder"]
    > ![Cambiar el relleno de la etiqueta azul claro](media/northwind-orders-canvas-part3/add-details-03.png)

## <a name="add-the-order-details-data-source"></a>Agregar el origen de datos de detalles del pedido

1. En el **vista** ficha, seleccione **orígenes de datos**y, a continuación, seleccione **agregar origen de datos** en el **datos** panel:

    > [!div class="mx-imgBorder"]
    > ![Agregar origen de datos](media/northwind-orders-canvas-part3/add-details-04.png)

1. Seleccione **de Common Data Service**:

    > [!div class="mx-imgBorder"]
    > ![Seleccione de Common Data Service](media/northwind-orders-canvas-part3/add-details-05.png)

1. En la parte superior de la **datos** panel, escriba **orden** en el cuadro de búsqueda, seleccione el **Order Details** casilla de verificación y, a continuación, seleccione **Connect** en el parte inferior del panel:

    > [!div class="mx-imgBorder"]
    > ![Especifique la entidad de los detalles de pedido](media/northwind-orders-canvas-part3/add-details-06.png)

    Acaba de agregar otro origen de datos a la aplicación:

    > [!div class="mx-imgBorder"]
    > ![Lista de orígenes de datos](media/northwind-orders-canvas-part3/add-details-07.png)

    Debe agregar este origen de datos porque, aunque la aplicación puede leer a través de una relación uno a varios, la aplicación no se ha escribir los cambios. La aplicación debe realizar cambios directamente con la entidad relacionada.

1. Cerrar la **datos** panel.

## <a name="select-a-product"></a>Seleccione un producto

1. En el **insertar** ficha, seleccione **controles** > **cuadro combinado**:

    > [!div class="mx-imgBorder"]
    > ![Insertar cuadro combinado](media/northwind-orders-canvas-part3/add-details-08.png)

    El [ **cuadro combinado** ](controls/control-combo-box.md) control aparece en la esquina superior izquierda.

1. Establezca el cuadro combinado **elementos** propiedad en esta fórmula:

    ```powerapps-comma
    Choices( 'Order Details'.Product )
    ```

    > [!div class="mx-imgBorder"]
    > ![Establezca la propiedad de los elementos del cuadro combinado](media/northwind-orders-canvas-part3/add-details-09.png)

    El [ **opciones** ](functions/function-choices.md) función devuelve una tabla de todos los valores posibles para el **producto** campo el **Order Details** entidad. Este campo es una búsqueda en una relación varios a uno, por lo que **opciones** devuelve todos los registros de la **productos del pedido** entidad.

    > [!NOTE]
    > También puede usar **opciones** con conjuntos de opciones para devolver una tabla de todas las opciones. Los pasos no mencionan este enfoque, pero usa ya cuando se agregó el cuadro combinado que muestra **estado del pedido** en el formulario de resumen.

1. En el **datos** panel, abra el **texto primario** lista y, a continuación, seleccione **nwind_productname**. 

1. Abra el **SearchField** lista y, a continuación, seleccione **nwind_productname**.

    Especifique el nombre lógico porque el **datos** panel todavía no admite nombres para mostrar en este caso:

    > [!div class="mx-imgBorder"]
    > ![Establecer el texto principal para el cuadro combinado](media/northwind-orders-canvas-part3/add-details-10.png)

1. Cerrar la **datos** panel.

1. En el **propiedades** pestaña cerca del borde derecho, desplácese hacia abajo, desactive la opción **permitir la selección múltiple**y asegúrese de que **permitir búsquedas** está activado:

    > [!div class="mx-imgBorder"]
    > ![Selección múltiple de deshabilitar y habilitar la búsqueda](media/northwind-orders-canvas-part3/add-details-12.png)

1. Cambiar el tamaño y mueva el cuadro combinado para el área de color azul claro, justo debajo de la columna de nombre de producto en la Galería de detalle:

    > [!div class="mx-imgBorder"]
    > ![Mover el cuadro combinado](media/northwind-orders-canvas-part3/add-details-13.png)

    En este cuadro combinado, el usuario especificará un registro en el **producto** entidad para el **Order Details** registro que va a crear la aplicación.

1. Mientras mantiene presionada la tecla Alt, seleccione la flecha hacia abajo del cuadro combinado.

    > [!TIP]
    > Manteniendo presionada la tecla Alt, puede interactuar con los controles de PowerApps Studio sin tener que abrir el modo de vista previa.

1. En la lista de productos que aparece, seleccione un producto:

    > [!div class="mx-imgBorder"]
    > ![Seleccione un producto en el cuadro combinado](media/northwind-orders-canvas-part3/add-details-14.png)

## <a name="add-a-product-image"></a>Agregar una imagen de producto

1. En el **insertar** ficha, seleccione **Media** > **imagen**:

    > [!div class="mx-imgBorder"]
    > ![Insertar control de imagen](media/northwind-orders-canvas-part3/add-details-15.png)

    El [ **imagen** ](controls/control-image.md) control aparece en la esquina superior izquierda:

    > [!div class="mx-imgBorder"]
    > ![Ubicación predeterminada de control de imagen](media/northwind-orders-canvas-part3/add-details-16.png)

1. Cambiar el tamaño de la imagen y muévala hasta el área de color azul claro en las imágenes de otros productos y junto al cuadro combinado.

1. Establecer el **imagen** propiedad de la imagen:

    ```powerapps-comma
    ComboBox1.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > ![Establezca la propiedad Image de la imagen](media/northwind-orders-canvas-part3/add-details-17.png)

    Está usando el mismo truco que utilizó para mostrar la imagen del empleado en el formulario de resumen. El **seleccionados** propiedad del cuadro combinado devuelve todo el registro de cualquier producto que el usuario selecciona, incluyendo la **imagen** campo.

## <a name="add-a-quantity-box"></a>Agregue un cuadro de cantidad

1. En el **insertar** ficha, seleccione **texto** > **entrada de texto**:

    > [!div class="mx-imgBorder"]
    > ![Agregar cuadro de texto](media/northwind-orders-canvas-part3/add-details-18.png)

    El [ **entrada de texto** ](controls/control-text-input.md) control aparece en la esquina superior izquierda:

    > [!div class="mx-imgBorder"]
    > ![Ubicación predeterminada del cuadro de entrada de texto](media/northwind-orders-canvas-part3/add-details-19.png)

1. Cambiar el tamaño y mueva el cuadro de entrada de texto a la derecha del cuadro combinado, en la columna de cantidad en la Galería de detalle:

    > [!div class="mx-imgBorder"]
    > ![Cambiar el tamaño y mover el cuadro de texto](media/northwind-orders-canvas-part3/add-details-20.png)

    Mediante este cuadro de entrada de texto, el usuario especificará la **cantidad** campo de la **Order Details** registro.

1. Establecer el **predeterminado** propiedad de este control en **""** :

    > [!div class="mx-imgBorder"]
    > ![Establecer el ** predeterminada ** propiedad del cuadro de entrada de texto](media/northwind-orders-canvas-part3/add-details-21.png)

1. En el **inicio** pestaña, establezca la alineación del texto de este control en **derecha**:

    > [!div class="mx-imgBorder"]
    > ![Cambiar la alineación](media/northwind-orders-canvas-part3/add-details-22.png)

## <a name="show-the-unit-and-extended-prices"></a>Mostrar los precios unitarios y totales

1. En el **insertar** pestaña, inserte un **etiqueta** control.

    La etiqueta aparece en la esquina superior izquierda de la pantalla:

    > [!div class="mx-imgBorder"]
    > ![Insertar una etiqueta](media/northwind-orders-canvas-part3/add-details-23.png)

1. Cambiar el tamaño y mueva la etiqueta a la derecha del control de entrada de texto y establezca la etiqueta **texto** propiedad en esta fórmula:

    ```powerapps-comma
    Text( ComboBox1.Selected.'List Price'; "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![Establezca la propiedad de texto de la etiqueta](media/northwind-orders-canvas-part3/add-details-24.png)

    Este control muestra el **precio** desde el **productos del pedido** entidad. Este valor se determinará el **precio unitario** campo el **Order Details** registro.

    > [!NOTE]
    > En este escenario, el valor es de solo lectura, pero podrían llamar otros escenarios de usuario de la aplicación que lo modifique. En ese caso, utilice un **entrada de texto** y establezca su **predeterminado** propiedad **precio de venta**.

1. En el **inicio** pestaña, establezca la alineación del texto de la etiqueta del precio de venta en **derecha**:

    > [!div class="mx-imgBorder"]
    > ![Cambiar la alineación](media/northwind-orders-canvas-part3/add-details-25.png)

1. Copie y pegue la etiqueta del precio de lista y, a continuación, cambiar el tamaño y mueva la copia a la derecha de la etiqueta del precio de venta.

1. Establecer la nueva etiqueta **texto** propiedad en esta fórmula:

    ```powerapps-comma
    Text( Value(TextInput1.Text) * ComboBox1.Selected.'List Price'; "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![Establezca la propiedad de texto de la nueva etiqueta](media/northwind-orders-canvas-part3/add-details-27.png)

    Este control muestra el precio total según la cantidad que especifica el usuario de la aplicación y el precio de venta del producto que ha seleccionado el usuario de la aplicación. Es puramente informativo para el usuario de la aplicación.

1. Haga doble clic en el control de entrada de texto de la cantidad y, a continuación, escriba un número.

    El **extendido** etiqueta precio se actualiza para mostrar el nuevo valor:

    > [!div class="mx-imgBorder"]
    > ![Especifique una cantidad y mostrar el precio total](media/northwind-orders-canvas-part3/add-details-28.png)

## <a name="add-an-add-icon"></a>Agregar un icono de agregar

1. En el **insertar** ficha, seleccione **iconos** > **agregar**:

    > [!div class="mx-imgBorder"]
    > ![Icono Agregar INSERT](media/northwind-orders-canvas-part3/add-details-29.png)

    El icono aparece en la esquina superior izquierda de la pantalla.

    > [!div class="mx-imgBorder"]
    > ![Ubicación predeterminada de agregar icono](media/northwind-orders-canvas-part3/add-details-30.png)

1. Cambiar el tamaño y mover este icono para el borde derecho del área de color azul claro y, a continuación, establecer el icono **OnSelect** propiedad en esta fórmula:

    ```powerapps-comma
    Patch( 'Order Details';
        Defaults('Order Details');
        {
            Order: Gallery1.Selected;
            Product: ComboBox1.Selected;
            Quantity: Value(TextInput1.Text);
            'Unit Price': ComboBox1.Selected.'List Price'
        }
    );;
    Refresh( Orders );;
    Reset( ComboBox1 );;
    Reset( TextInput1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![Establezca la propiedad OnSelect del icono](media/northwind-orders-canvas-part3/add-details-31.png)

    En general, el [ **Patch** ](functions/function-patch.md) función actualiza y crea registros y los argumentos específicos en esta fórmula determinan los cambios exactos que harán que la función.

    - El primer argumento especifica el origen de datos (en este caso, el **Order Details** entidad) en el que se actualice o cree un registro de la función.
    - El segundo argumento especifica que la función creará un registro con los valores predeterminados para el **Order Details** entidad a menos que se especifique lo contrario en el tercer argumento.
    - El tercer argumento especifica que las cuatro columnas en el nuevo registro contendrá los valores del usuario.

      - El **orden** columna contendrá el número del pedido que el usuario seleccionó en la Galería de orden.
      - El **producto** columna contendrá el nombre del producto que el usuario seleccionado en el cuadro combinado que muestra los productos.
      - El **cantidad** columna contendrá el valor especificado por el usuario en el cuadro de entrada de texto.
      - El **precio unitario** columna contendrá el precio del producto que ha seleccionado el usuario para este detalle de pedidos.

    > [!NOTE]
    > Puede crear fórmulas que usan datos de cualquier columna (en el **productos del pedido** entidad) para cualquier producto de usuario de la aplicación se selecciona en el cuadro combinado que muestra los productos. Cuando el usuario selecciona un registro en el **productos del pedido** entidad, no solo el nombre del producto aparece en ese cuadro combinado sino también aparece el precio del producto en una etiqueta. Cada valor de búsqueda en una aplicación de lienzo hace referencia a un registro completo, no solo una clave principal.

    El **actualizar** función garantiza que el **pedidos** entidad refleja el registro que acaba de agregar a la **Order Details** entidad. El **restablecer** función borra los datos de producto, cantidad y precio de venta para que el usuario puede crear más fácilmente otro detalle de pedido para el mismo orden.

1. Presione F5 y, a continuación, seleccione el **agregar** icono.

    El orden refleja la información que ha especificado:

    > [!div class="mx-imgBorder"]
    > ![Animación de agregar un detalle de pedido](media/northwind-orders-canvas-part3/add-details.gif)

1. (opcional) Agregue otro elemento al pedido.

1. Presione Esc para cerrar el modo de vista previa.

## <a name="remove-an-order-detail"></a>Quitar un detalle de pedido

1. En el centro de la pantalla, seleccione la plantilla de la Galería de detalle:

    > [!div class="mx-imgBorder"]
    > ![Seleccione la plantilla de la Galería](media/northwind-orders-canvas-part3/remove-details-01.png)

1. En el **insertar** ficha, seleccione **iconos** > **Papelera**:

    > [!div class="mx-imgBorder"]
    > ![Icono de Papelera INSERT](media/northwind-orders-canvas-part3/remove-details-02.png)

    Aparece el icono de Papelera en la esquina superior izquierda de la plantilla de la galería.

    > [!div class="mx-imgBorder"]
    > ![Ubicación predeterminada de icono](media/northwind-orders-canvas-part3/remove-details-03.png)

1. Cambiar el tamaño y mueva el icono de Papelera en el lado derecho de la plantilla de la Galería de detalle y establece el icono **OnSelect** propiedad en esta fórmula:

    ```powerapps-comma
    Remove( 'Order Details'; ThisItem );; Refresh( Orders )
    ```

    > [!div class="mx-imgBorder"]
    > ![Establezca la propiedad OnSelect del icono](media/northwind-orders-canvas-part3/remove-details-04.png)

    Cuando se redactó este documento, no se puede quitar un registro directamente desde una relación, por lo que la [ **quitar** ](functions/function-remove-removeif.md) función quita un registro directamente desde la entidad relacionada. **ThisItem** especifica que el registro para quitar, tomado del mismo registro en la Galería de detalles donde aparece el icono de Papelera.

    Nuevamente, la operación utiliza datos almacenados en caché, por lo que la **actualizar** función informa a la **pedidos** entidad que esa aplicación ha cambiado uno de sus entidades relacionadas.

1. Presione F5 para abrir el modo de vista previa y, a continuación, seleccione el icono de Papelera junto a cada **Order Details** registro que desee quitar de la orden.

1. Pruebe a agregar y quitar distintos detalles de pedido de los pedidos:

    > [!div class="mx-imgBorder"]
    > ![Animación de agregar y eliminar los detalles del pedido](media/northwind-orders-canvas-part3/remove-details.gif)

## <a name="in-conclusion"></a>En conclusión

Para recapitular, ha agregado otra galería para mostrar detalles del pedido y los controles de adición y eliminación de un detalle de pedido en la aplicación. Utiliza estos elementos:

- Un segundo control de galería, vinculado a la Galería de pedido a través de una relación uno a varios: **Gallery2.Items** = `Gallery1.Selected.'Order Details'`
- Una relación de varios a uno de los **Order Details** entidad a la **productos del pedido** entidad: `ThisItem.Product.'Product Name'` y `ThisItem.Product.Picture`
- El **opciones** función para obtener una lista de productos: `Choices( 'Order Details'.Product' )`
- El **seleccionados** registro relacionados con la propiedad de un cuadro combinado como la completa varios a uno: `ComboBox1.Selected.Picture` y `ComboBox1.Selected.'List Price'`
- El **Patch** función para crear un **Order Details** registro: `Patch( 'Order Details'; Defaults( 'Order Details' ); ... )`
- El **quitar** función para eliminar un **Order Details** registro: `Remove( 'Order Details'; ThisItem )`

Esta serie de temas ha sido un tutorial rápido del uso de relaciones de Common Data Service y opción se establece en una aplicación de lienzo con fines formativos. Antes de publicar cualquier aplicación en producción, debe considerar la validación de campos, control de errores y muchos otros factores.
