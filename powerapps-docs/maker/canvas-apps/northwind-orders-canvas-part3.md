---
title: Creación de una galería de detalles en una aplicación de lienzo | Microsoft Docs
description: Crear una galería de detalles en una aplicación de lienzo para administrar datos de Northwind Traders
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/06/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7e29674e689ff77599bb49c58e7b0edbc028b6be
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675960"
ms.PowerAppsDecimalTransform: true
---
# <a name="create-a-detail-gallery-in-a-canvas-app"></a>Creación de una galería de detalles en una aplicación de lienzo

Siga las instrucciones paso a paso para crear una galería de detalles en una aplicación de lienzo para administrar datos ficticios en la base de datos Northwind Traders. Este tema forma parte de una serie en la que se explica cómo compilar una aplicación empresarial en datos relacionales en Common Data Service. Para obtener los mejores resultados, explore estos temas en esta secuencia:

1. [Cree una galería de pedidos](northwind-orders-canvas-part1.md).
1. [Cree un formulario de Resumen](northwind-orders-canvas-part2.md).
1. Crear una galería de detalles (**este tema**).

> [!div class="mx-imgBorder"]
> ![definición de áreas de pantalla](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>Requisitos previos

Antes de empezar este tema, debe instalar la base de datos como se describió anteriormente en este tema. A continuación, debe crear la galería de pedidos y el formulario de Resumen, o bien abrir la aplicación **de pedidos de Northwind (canvas)-Begin Part 3** , que ya contiene esa galería y ese formulario.

## <a name="create-another-title-bar"></a>Crear otra barra de título

1. En la parte superior de la pantalla, seleccione el control de [**etiqueta**](controls/control-text-box.md) que actúa como barra de título, cópielo presionando Ctrl + C y, a continuación, péguelo presionando Ctrl-V:

    > [!div class="mx-imgBorder"]
    > ![copiar y pegar la barra de título](media/northwind-orders-canvas-part3/details-01.png)

1. Cambie el tamaño de la copia y muévala para que aparezca justo debajo del formulario de resumen.

1. Quite el texto de la copia de cualquiera de estas maneras:

    - Haga doble clic en el texto para seleccionarlo y, a continuación, presione SUPR.
    - Establezca la propiedad **Text** de la etiqueta en una cadena vacía ( **""** ).

    > [!div class="mx-imgBorder"]
    > ![quitar el texto de la copia de la barra de título](media/northwind-orders-canvas-part3/details-02.png)

## <a name="add-a-gallery"></a>Agregar una galería

1. Inserte un control [**Galería**](controls/control-gallery.md) con un diseño **vertical en blanco** :

    > [!div class="mx-imgBorder"]
    > ![agregar una galería vertical en blanco](media/northwind-orders-canvas-part3/details-03.png)

    La nueva galería, que mostrará los detalles del pedido, aparece en la esquina superior izquierda:

    > [!div class="mx-imgBorder"]
    > ![ubicación predeterminada de la galería de detalles de pedidos](media/northwind-orders-canvas-part3/details-04.png)

1. Cierre el cuadro de diálogo origen de datos de la marcha y, a continuación, cambie el tamaño y mueva la galería de detalles a la esquina inferior derecha, debajo de la nueva barra de título:

    > [!div class="mx-imgBorder"]
    > ![ubicación final de la galería de detalles de pedidos](media/northwind-orders-canvas-part3/details-05.png)

1. Establezca la propiedad **elementos** de la galería de detalles en esta fórmula:

    ```powerapps-comma
    Gallery1.Selected.'Order Details'
    ```

    > [!div class="mx-imgBorder"]
    > ![establecer la propiedad elementos de la galería de detalles](media/northwind-orders-canvas-part3/details-06.png)

    Si aparece un error, confirme que la galería de pedidos se denomine **Gallery1** (en el panel de **vista de árbol** situado cerca del borde izquierdo). Si esa Galería tiene un nombre diferente, cambie su nombre a **Gallery1**.

    Acaba de vincular las dos galerías. Cuando el usuario selecciona un pedido en la galería de pedidos, esa selección identifica un registro en la entidad **pedidos** . Si ese pedido contiene uno o más elementos de línea, el registro de la entidad **Orders** se vincula a uno o varios registros de la entidad **Order Details** y los datos de esos registros aparecen en la galería de detalles. Este comportamiento refleja la relación de uno a varios que se ha creado automáticamente entre las entidades **Orders** y Order **Details** . La fórmula que especificó "recorre" esa relación mediante la notación de puntos:

    > [!div class="mx-imgBorder"]
    > ![relación de uno a varios entre la entidad Orders y la entidad Order Details](media/northwind-orders-canvas-part3/schema-orders-rel.png)

## <a name="show-product-names"></a>Mostrar nombres de producto

1. En la galería de detalles, seleccione **Agregar un elemento de la pestaña insertar** para seleccionar la plantilla de la Galería:

    > [!div class="mx-imgBorder"]
    > ![seleccione la plantilla para la galería de detalles](media/northwind-orders-canvas-part3/details-07.png)

    Asegúrese de que ha seleccionado la plantilla Galería en lugar de la galería. El rectángulo de selección debe aparecer ligeramente dentro del límite de la galería y probablemente menor que el alto de la galería. A medida que se insertan controles en esta plantilla, se repiten para cada elemento de la galería.

1. En la pestaña **Insertar** , inserte una etiqueta en la galería de detalles.

    La etiqueta debe aparecer en la galería; Si no es así, inténtelo de nuevo, pero asegúrese de seleccionar la plantilla de la Galería antes de insertar la etiqueta.

    > [!div class="mx-imgBorder"]
    > ![agregar una etiqueta a la galería de detalles](media/northwind-orders-canvas-part3/details-08.png)

1. Establezca la propiedad **texto** de la nueva etiqueta en esta fórmula:

    ```powerapps-comma
    ThisItem.Product.'Product Name'
    ```

    Si no aparece ningún texto, seleccione la flecha del **orden 0901** cerca de la parte inferior de la galería de pedidos.

1. Cambie el tamaño de la etiqueta para que aparezca el texto completo:

    > [!div class="mx-imgBorder"]
    > ![mostrar el nombre del producto en el detalle del pedido](media/northwind-orders-canvas-part3/details-09.png)

    Esta expresión se dirige desde un registro de la entidad **Order Details** . El registro se mantiene en **ThisItem** en la entidad **Order Products** a través de una relación de varios a uno:

    > [!div class="mx-imgBorder"]
    > ![relación de varios a uno entre la entidad Order Details y el pedido Product Entity](media/northwind-orders-canvas-part3/schema-orderdetails-rel.png)

    Se extraen el campo **nombre de producto** (y otros campos que está a punto de usar):

    > [!div class="mx-imgBorder"]
    > ![campos de la entidad Order Products](media/northwind-orders-canvas-part3/schema-products-fields.png)

## <a name="show-product-images"></a>Mostrar imágenes de producto

1. En la pestaña **Insertar** , inserte un control [**imagen**](controls/control-image.md) en la galería de detalles:

    > [!div class="mx-imgBorder"]
    > ![insertar](media/northwind-orders-canvas-part3/details-10.png) de control de imagen

1. Cambie el tamaño y mueva la imagen y la etiqueta para que esté en paralelo.

    > [!TIP]
    > Para tener un mayor control sobre el tamaño y la posición de un control, empiece a cambiar el tamaño o muévalo sin presionar la tecla Alt y, después, continúe con el cambio de tamaño o mueva el control mientras mantiene presionada la tecla Alt:

    > [!div class="mx-imgBorder"]
    > ![control de imagen de movimiento](media/northwind-orders-canvas-part3/details-11.png)

1. Establezca la propiedad **imagen** de la imagen en esta fórmula:

    ```powerapps-comma
    ThisItem.Product.Picture
    ```

    Una vez más, la expresión hace referencia a un producto que está asociado a este orden y extrae el campo de **imagen** que se va a mostrar.

    > [!div class="mx-imgBorder"]
    > ![Mostrar imagen de producto](media/northwind-orders-canvas-part3/details-12.png)

1. Reduzca el alto de la plantilla de la galería para que aparezca más de un registro de **detalle de pedido** a la vez:

    > [!div class="mx-imgBorder"]
    > ![acortar la plantilla de la Galería](media/northwind-orders-canvas-part3/details-13.png)

## <a name="show-product-quantity-and-cost"></a>Mostrar la cantidad y el costo del producto

1. En la pestaña **Insertar** , inserte otra etiqueta en la galería de detalles y, a continuación, cambie el tamaño y mueva la nueva etiqueta a la derecha de la información del producto.

1. Establezca la propiedad **texto** de la nueva etiqueta en esta expresión:

    ```powerapps-comma
    ThisItem.Quantity
    ```

    Esta fórmula extrae información directamente de la entidad **Order Details** (no se requiere ninguna relación).

    > [!div class="mx-imgBorder"]
    > ![Mostrar la cantidad de producto](media/northwind-orders-canvas-part3/details-13b.png) 

1. En la pestaña **Inicio** , cambie la alineación de este control a **derecha**:

    > [!div class="mx-imgBorder"]
    > ![cambiar la alineación](media/northwind-orders-canvas-part3/details-14.png)

1. En la pestaña **Insertar** , inserte otra etiqueta en la galería de detalles y, a continuación, cambie el tamaño y mueva la etiqueta a la derecha de la etiqueta cantidad.

1. Establezca la propiedad **texto** de la nueva etiqueta en esta fórmula:

    ```powerapps-comma
    Text( ThisItem.'Unit Price'; "[$-en-US]$ #,###.00" )
    ```

    Si no incluye la etiqueta de idioma ( **[$-en-US]** ), se agregará automáticamente en función de su idioma y región. Si usa una etiqueta de idioma diferente, querrá quitar el **$** justo después del corchete de cierre ( **]** ) y, a continuación, agregar su propio símbolo de moneda en esa posición.

    > [!div class="mx-imgBorder"]
    > ![Mostrar precio por unidad](media/northwind-orders-canvas-part3/details-15.png)

1. En la pestaña **Inicio** , cambie la alineación de este control a **derecha**:

    > [!div class="mx-imgBorder"]
    > ![cambiar la alineación](media/northwind-orders-canvas-part3/details-16.png)

1. En la pestaña **Insertar** , inserte otro control etiqueta en la galería de detalles y, a continuación, cambie el tamaño y mueva la nueva etiqueta a la derecha del precio por unidad.

1. Establezca la propiedad **texto** de la nueva etiqueta en esta fórmula:

    ```powerapps-comma
    Text( ThisItem.Quantity * ThisItem.'Unit Price'; "[$-en-US]$ #,###.00" )
    ```

    De nuevo, si no incluye la etiqueta de idioma ( **[$-en-US]** ), se agregará automáticamente en función de su idioma y región. Si la etiqueta es diferente, querrá usar su propio símbolo de moneda en lugar del **$** justo después del corchete de cierre ( **]** ).

    > [!div class="mx-imgBorder"]
    > ![Mostrar](media/northwind-orders-canvas-part3/details-17.png) de precios extendidos

1. En la pestaña **Inicio** , cambie la alineación de este control a **derecha**:

    > [!div class="mx-imgBorder"]
    > ![cambiar la alineación](media/northwind-orders-canvas-part3/details-18.png)

    Ya ha terminado de agregar controles a la galería de detalles.

1. En el panel de **vista de árbol** , seleccione **Screen1** para asegurarse de que la galería de detalles ya no está seleccionada.

## <a name="add-text-to-the-new-title-bar"></a>Agregar texto a la nueva barra de título

1. En la pestaña **Insertar** , inserte otra etiqueta en la pantalla:

    > [!div class="mx-imgBorder"]
    > ![Insertar etiqueta](media/northwind-orders-canvas-part3/details-19.png)

1. Cambie el tamaño y mueva la nueva etiqueta por encima de las imágenes de los productos en la segunda barra de título y, a continuación, cambie el color del texto a blanco en la pestaña **Inicio** .

1. Haga doble clic en el texto de la etiqueta y, a continuación, escriba **Product**:

    > [!div class="mx-imgBorder"]
    > ![cambiar el texto de la etiqueta a](media/northwind-orders-canvas-part3/details-20.png) de producto

1. Copie y pegue la etiqueta Product y, a continuación, cambie el tamaño de la copia y muévala por encima de la columna quantity.

1. Haga doble clic en el texto de la nueva etiqueta y escriba **Quantity**:

    > [!div class="mx-imgBorder"]
    > ![cambiar el texto de la etiqueta a quantity](media/northwind-orders-canvas-part3/details-21.png)

1. Copie y pegue la etiqueta quantity y, a continuación, cambie el tamaño de la copia y muévala por encima de la columna precio unitario.

1. Haga doble clic en el texto de la nueva etiqueta y, a continuación, escriba **precio por unidad**:

    > [!div class="mx-imgBorder"]
    > ![cambiar el texto de la etiqueta a precio por unidad](media/northwind-orders-canvas-part3/details-22.png)

1. Copie y pegue la etiqueta de precio unitario y, a continuación, cambie el tamaño de la copia y muévala por encima de la columna de precio ampliado.

1. Haga doble clic en el texto de la nueva etiqueta y, a continuación, escriba **Extended**:

    > [!div class="mx-imgBorder"]
    > ![cambiar el texto de la etiqueta a](media/northwind-orders-canvas-part3/details-23.png) extendido

## <a name="display-order-totals"></a>Mostrar totales de orden

1. Reduzca el alto de la galería de detalles para dejar espacio para los totales de pedido en la parte inferior de la pantalla:

    > [!div class="mx-imgBorder"]
    > ![acortar la galería de detalles de pedidos](media/northwind-orders-canvas-part3/sum-01.png)

1. Copie y pegue la barra de título en el centro de la pantalla y, a continuación, mueva la copia a la parte inferior de la pantalla:

    > [!div class="mx-imgBorder"]
    > ![copiar la barra de título y mueva la copia al borde inferior](media/northwind-orders-canvas-part3/sum-02.png)

1. Copie y pegue la etiqueta Product de la barra de título central y, a continuación, mueva la copia a la barra de título inferior, a la izquierda de la columna **Quantity** .

1. Haga doble clic en el texto de la nueva etiqueta y, a continuación, escriba este texto:<br>**Totales de pedido:**

    > [!div class="mx-imgBorder"]
    > ![agregar etiqueta para los totales de pedido](media/northwind-orders-canvas-part3/sum-03.png)

1. Copie y pegue la etiqueta Order-TOTALS y, a continuación, cambie el tamaño y mueva la copia a la derecha de la etiqueta Order-TOTALS.

1. Establezca la propiedad **texto** de la nueva etiqueta en esta fórmula:

    ```powerapps-comma
    Sum( Gallery1.Selected.'Order Details'; Quantity )
    ```

    Esta fórmula muestra una advertencia de delegación, pero puede ignorarla porque ningún pedido individual contendrá más de 500 productos.

1. En la pestaña **Inicio** , establezca la alineación del texto de la nueva etiqueta en **derecha**:

    > [!div class="mx-imgBorder"]
    > ![cambiar la alineación](media/northwind-orders-canvas-part3/sum-04.png)

1. Copie y pegue este control de etiqueta y, a continuación, cambie el tamaño y mueva la copia en la columna **extendida** .

1. Establezca la propiedad **Text** de la copia en esta fórmula:

    ```powerapps-comma
    Text( Sum( Gallery1.Selected.'Order Details'; Quantity * 'Unit Price' ); "[$-en-US]$ #,###.00" )
    ```

    Esta fórmula muestra una advertencia de delegación, pero puede ignorarla porque ningún pedido individual contendrá más de 500 productos.

    > [!div class="mx-imgBorder"]
    > ![mostrar el costo total del pedido](media/northwind-orders-canvas-part3/sum-05.png)

## <a name="add-space-for-new-details"></a>Agregar espacio para nuevos detalles

En cualquier galería puede mostrar datos, pero no puede actualizarlos ni agregar registros. En la galería de detalles, agregará un área en la que el usuario puede configurar un registro en la entidad **Order Details** e insertar dicho registro en un pedido.

1. Reduzca el alto de la galería de detalles lo suficiente para dejar espacio para un espacio de edición de un solo elemento en esa Galería.

    En este espacio, agregará controles para que el usuario pueda agregar un detalle de pedido:

    > [!div class="mx-imgBorder"]
    > ![acortar la galería de detalles](media/northwind-orders-canvas-part3/add-details-01.png)

1. En la pestaña **Insertar** , inserte una etiqueta y, a continuación, cambie su tamaño y muévala en la galería de detalles.

    > [!div class="mx-imgBorder"]
    > ![insertar una etiqueta](media/northwind-orders-canvas-part3/add-details-02.png)

1. Haga doble clic en el texto de la nueva etiqueta y, a continuación, presione SUPR.

1. En la pestaña **Inicio** , establezca el color de **relleno** de la nueva etiqueta en **LightBlue**:

    > [!div class="mx-imgBorder"]
    > ![cambiar el relleno de la etiqueta a azul claro](media/northwind-orders-canvas-part3/add-details-03.png)

## <a name="select-a-product"></a>Seleccionar un producto

1. En la pestaña **Insertar** , seleccione **controles** > **cuadro combinado**:

    > [!div class="mx-imgBorder"]
    > ![cuadro combinado insertar](media/northwind-orders-canvas-part3/add-details-08.png)

    El control de [**cuadro combinado**](controls/control-combo-box.md) aparece en la esquina superior izquierda.

1. En el cuadro de diálogo volar hacia fuera, seleccione el origen de datos de **pedidos de productos** :

    > [!div class="mx-imgBorder"]
    > ![establecer la propiedad elementos del cuadro combinado](media/northwind-orders-canvas-part3/add-details-09.png)

1. En la pestaña **propiedades** del cuadro combinado, seleccione **Editar** (junto a **campos**) para abrir el panel **datos** .  Asegúrese de que el texto y los **SearchField** **principales** están establecidos en **nwind_productname**.

    Especifique el nombre lógico porque en este caso el panel **datos** no admite nombres para mostrar:

    > [!div class="mx-imgBorder"]
    > ![establecer el texto principal para el cuadro combinado](media/northwind-orders-canvas-part3/add-details-10.png)

1. Cierre el panel **datos** .

1. En la pestaña **propiedades** situada cerca del borde derecho, desplácese hacia abajo, desactive **Permitir selección múltiple**y asegúrese de que la **opción permitir búsqueda** está activada:

    > [!div class="mx-imgBorder"]
    > ![deshabilitar la selección múltiple y habilitar la búsqueda](media/northwind-orders-canvas-part3/add-details-12.png)

1. Cambie el tamaño y mueva el cuadro combinado al área azul claro, justo debajo de la columna Product-Name de la galería de detalles:

    > [!div class="mx-imgBorder"]
    > ![cuadro combinado de movimiento](media/northwind-orders-canvas-part3/add-details-13.png)

    En este cuadro combinado, el usuario especificará un registro en la entidad **Product** para el registro de **detalles del pedido** que la aplicación creará.

1. Mientras mantiene presionada la tecla Alt, seleccione la flecha hacia abajo del cuadro combinado.

    > [!TIP]
    > Si mantiene presionada la tecla Alt, puede interactuar con los controles de Power apps Studio sin abrir el modo de vista previa.

1. En la lista de productos que aparece, seleccione un producto:

    > [!div class="mx-imgBorder"]
    > ![seleccionar un producto en el cuadro combinado](media/northwind-orders-canvas-part3/add-details-14.png)

## <a name="add-a-product-image"></a>Agregar una imagen de producto

1. En la pestaña **Insertar** , seleccione **media** > **imagen**:

    > [!div class="mx-imgBorder"]
    > ![insertar](media/northwind-orders-canvas-part3/add-details-15.png) de control de imagen

    El control [**imagen**](controls/control-image.md) aparece en la esquina superior izquierda:

    > [!div class="mx-imgBorder"]
    > ![ubicación predeterminada del control de imagen](media/northwind-orders-canvas-part3/add-details-16.png)

1. Cambie el tamaño de la imagen y muévala al área azul claro bajo las demás imágenes del producto y junto al cuadro combinado.

1. Establezca la propiedad **imagen** de la imagen en:

    ```powerapps-comma
    ComboBox1.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > ![establecer la propiedad imagen de la imagen](media/northwind-orders-canvas-part3/add-details-17.png)

    Está usando el mismo truco que usó para mostrar la imagen del empleado en el formulario de resumen. La propiedad **seleccionada** del cuadro combinado devuelve todo el registro de cualquier producto que seleccione el usuario, incluido el campo de **imagen** .

## <a name="add-a-quantity-box"></a>Agregar un cuadro de cantidad

1. En la pestaña **Insertar** , seleccione **texto** > **entrada de texto**:

    > [!div class="mx-imgBorder"]
    > ![agregar el cuadro de entrada de texto](media/northwind-orders-canvas-part3/add-details-18.png)

    El control [**entrada de texto**](controls/control-text-input.md) aparece en la esquina superior izquierda:

    > [!div class="mx-imgBorder"]
    > ![ubicación predeterminada del cuadro de entrada de texto](media/northwind-orders-canvas-part3/add-details-19.png)

1. Cambie el tamaño y mueva el cuadro de entrada de texto a la derecha del cuadro combinado, en la columna cantidad de la galería de detalles:

    > [!div class="mx-imgBorder"]
    > ![cambiar el tamaño y desplace el cuadro de entrada de texto](media/northwind-orders-canvas-part3/add-details-20.png)

    Mediante este cuadro de entrada de texto, el usuario especificará el campo **cantidad** del registro de **detalles del pedido** .

1. Establezca la propiedad **default** de este control en **""** :

    > [!div class="mx-imgBorder"]
    > ![establecer la propiedad * * default * * del cuadro de entrada de texto](media/northwind-orders-canvas-part3/add-details-21.png)

1. En la pestaña **Inicio** , establezca la alineación del texto de este control en **derecha**:

    > [!div class="mx-imgBorder"]
    > ![cambiar la alineación](media/northwind-orders-canvas-part3/add-details-22.png)

## <a name="show-the-unit-and-extended-prices"></a>Mostrar la unidad y los precios extendidos

1. En la pestaña **Insertar** , inserte un control **etiqueta** .

    La etiqueta aparece en la esquina superior izquierda de la pantalla:

    > [!div class="mx-imgBorder"]
    > ![insertar una etiqueta](media/northwind-orders-canvas-part3/add-details-23.png)

1. Cambie el tamaño y mueva la etiqueta a la derecha del control de entrada de texto y establezca la propiedad **texto** de la etiqueta en esta fórmula:

    ```powerapps-comma
    Text( ComboBox1.Selected.'List Price'; "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![establecer la propiedad Text de la etiqueta](media/northwind-orders-canvas-part3/add-details-24.png)

    Este control muestra el **precio de venta** de la entidad **Order Products** . Este valor determinará el campo de **precio por unidad** en el registro de **detalles del pedido** .

    > [!NOTE]
    > En este escenario, el valor es de solo lectura, pero otros escenarios pueden llamar a para que el usuario de la aplicación lo modifique. En ese caso, use un control de **entrada de texto** y establezca su propiedad **predeterminada** en **lista de precios**.

1. En la pestaña **Inicio** , establezca la alineación del texto de la etiqueta lista-precio en **derecha**:

    > [!div class="mx-imgBorder"]
    > ![cambiar la alineación](media/northwind-orders-canvas-part3/add-details-25.png)

1. Copie y pegue la etiqueta de precio de lista y, a continuación, cambie el tamaño y mueva la copia a la derecha de la etiqueta lista-precio.

1. Establezca la propiedad **texto** de la nueva etiqueta en esta fórmula:

    ```powerapps-comma
    Text( Value(TextInput1.Text) * ComboBox1.Selected.'List Price'; "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![establecer la propiedad de texto de la nueva etiqueta](media/northwind-orders-canvas-part3/add-details-27.png)

    Este control muestra el precio extendido en función de la cantidad especificada por el usuario de la aplicación y el precio de venta del producto seleccionado por el usuario de la aplicación. Es meramente informativo para el usuario de la aplicación.

1. Haga doble clic en el control de entrada de texto para quantity y, a continuación, escriba un número.

    La etiqueta del precio **extendido** se vuelve a calcular para mostrar el nuevo valor:

    > [!div class="mx-imgBorder"]
    > ![especificar una cantidad y mostrar el precio extendido](media/northwind-orders-canvas-part3/add-details-28.png)

## <a name="add-an-add-icon"></a>Agregar un icono Agregar

1. En la pestaña **Insertar** , seleccione **iconos** > **Agregar**:

    > [!div class="mx-imgBorder"]
    > ![insertar icono Agregar](media/northwind-orders-canvas-part3/add-details-29.png)

    El icono aparece en la esquina superior izquierda de la pantalla.

    > [!div class="mx-imgBorder"]
    > ![ubicación predeterminada del icono Agregar](media/northwind-orders-canvas-part3/add-details-30.png)

1. Cambie el tamaño y mueva este icono al borde derecho del área de color azul claro y, a continuación, establezca la propiedad **alseleccionar** del icono en esta fórmula:

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
    > ![establecer la propiedad alseleccionar del icono](media/northwind-orders-canvas-part3/add-details-31.png)

    En general, la función [**patch**](functions/function-patch.md) actualiza y crea registros, y los argumentos específicos de esta fórmula determinan los cambios exactos que realizará la función.

    - El primer argumento especifica el origen de datos (en este caso, la entidad **Order Details** ) en la que la función actualizará o creará un registro.
    - El segundo argumento especifica que la función creará un registro con los valores predeterminados para la entidad **Order Details** , a menos que se especifique lo contrario en el tercer argumento.
    - El tercer argumento especifica que cuatro columnas del nuevo registro contendrán valores del usuario.

      - La columna **orden** contendrá el número del pedido que el usuario seleccionó en la galería de pedidos.
      - La columna **Product** contendrá el nombre del producto que el usuario seleccionó en el cuadro combinado que muestra Products.
      - La columna **Quantity** contendrá el valor que el usuario especificó en el cuadro de entrada de texto.
      - La columna **precio por unidad** contendrá el precio de venta del producto que el usuario seleccionó para este detalle de pedido.

    > [!NOTE]
    > Puede generar fórmulas que usan datos de cualquier columna (en la entidad **Order Products** ) para cualquier producto que seleccione el usuario de la aplicación en el cuadro combinado que muestra productos. Cuando el usuario selecciona un registro en la entidad **Order Products** , no solo el nombre del producto aparece en ese cuadro combinado, sino que también el precio unitario del producto aparece en una etiqueta. Cada valor de búsqueda en una aplicación de lienzo hace referencia a un registro completo, no solo a una clave principal.

    La función de **actualización** garantiza que la entidad **Orders** refleja el registro que acaba de agregar a la entidad **Order Details** . La función de **restablecimiento** borra los datos de productos, cantidades y precios unitarios para que el usuario pueda crear más fácilmente otros detalles de pedido para el mismo pedido.

1. Presione F5 y, a continuación, seleccione el icono **Agregar** .

    El orden refleja la información que especificó:

    > [!div class="mx-imgBorder"]
    > ![animación de agregar un detalle de pedido](media/northwind-orders-canvas-part3/add-details.gif)

1. opta Agregue otro elemento al pedido.

1. Presione ESC para cerrar el modo de vista previa.

## <a name="remove-an-order-detail"></a>Quitar un detalle del pedido

1. En el centro de la pantalla, seleccione la plantilla de la galería de detalles:

    > [!div class="mx-imgBorder"]
    > ![seleccione la plantilla de la Galería](media/northwind-orders-canvas-part3/remove-details-01.png)

1. En la pestaña **Insertar** , seleccione **iconos** > **Trash**:

    > [!div class="mx-imgBorder"]
    > ![icono insertar papelera](media/northwind-orders-canvas-part3/remove-details-02.png)

    El icono de la papelera aparece en la esquina superior izquierda de la plantilla de la galería.

    > [!div class="mx-imgBorder"]
    > ![ubicación predeterminada del icono](media/northwind-orders-canvas-part3/remove-details-03.png)

1. Cambie el tamaño y mueva el icono de la papelera a la parte derecha de la plantilla de la galería de detalles y establezca la propiedad **alseleccionar** del icono en esta fórmula:

    ```powerapps-comma
    Remove( 'Order Details'; ThisItem );; Refresh( Orders )
    ```

    > [!div class="mx-imgBorder"]
    > ![establecer la propiedad alseleccionar del icono](media/northwind-orders-canvas-part3/remove-details-04.png)

    En el que se redactó este documento, no se puede quitar un registro directamente de una relación, por lo que la función [**Remove**](functions/function-remove-removeif.md) quita un registro directamente de la entidad relacionada. **ThisItem** especifica el registro que se va a quitar, tomado del mismo registro en la galería de detalles donde aparece el icono de la papelera.

    De nuevo, la operación utiliza datos en caché, por lo que la función **Refresh** informa a la entidad **Orders** de que la aplicación ha cambiado una de sus entidades relacionadas.

1. Presione F5 para abrir el modo de vista previa y, a continuación, seleccione el icono de la papelera junto a cada registro de **detalles de pedido** que desea quitar del pedido.

1. Intente agregar y quitar varios detalles de pedido de los pedidos:

    > [!div class="mx-imgBorder"]
    > ![animación de adición y eliminación de detalles de pedidos](media/northwind-orders-canvas-part3/remove-details.gif)

## <a name="in-conclusion"></a>En conclusión

En Resumen, ha agregado otra galería para mostrar los detalles del pedido y controla la adición y eliminación de los detalles de un pedido en la aplicación. Ha usado estos elementos:

- Un segundo control de galería, vinculado a la galería de pedidos, a través de una relación de uno a varios: **Gallery2. items** = `Gallery1.Selected.'Order Details'`
- Una relación de varios a uno desde la entidad **Order Details** hasta la entidad **Order products** : `ThisItem.Product.'Product Name'` y `ThisItem.Product.Picture`
- La función de **Opciones** para obtener una lista de productos: `Choices( 'Order Details'.Product' )`
- La propiedad **seleccionada** de un cuadro combinado como el registro relacionado de varios a uno completo: `ComboBox1.Selected.Picture` y `ComboBox1.Selected.'List Price'`
- La función **patch** para crear un registro **Order Details** : `Patch( 'Order Details'; Defaults( 'Order Details' ); ... )`
- La función **Remove** para eliminar un registro de **detalles de pedido** : `Remove( 'Order Details'; ThisItem )`

Esta serie de temas ha sido un tutorial rápido sobre el uso de Common Data Service relaciones y conjuntos de opciones en una aplicación de lienzo con fines educativos. Antes de publicar cualquier aplicación en producción, debe considerar la validación de campos, el control de errores y muchos otros factores.
