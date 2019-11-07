---
title: Creación de una galería de pedidos en una aplicación de lienzo | Microsoft Docs
description: Creación de una galería de pedidos en una aplicación de lienzo para administrar datos de Northwind Traders
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
ms.openlocfilehash: bbc6111800a817ecb71eec60fdba1d2dabd6c698
ms.sourcegitcommit: 32542f1d17fee757dcdaf9c247f4051f59b86434
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "73741513"
---
# <a name="create-an-order-gallery-in-a-canvas-app"></a>Creación de una galería de pedidos en una aplicación de lienzo

Siga las instrucciones paso a paso para crear una galería de pedidos en una aplicación de lienzo para administrar datos ficticios en la base de datos Northwind Traders. Este tema forma parte de una serie en la que se explica cómo compilar una aplicación empresarial en datos relacionales en Common Data Service. Para obtener los mejores resultados, explore estos temas en esta secuencia:

1. Crear una galería de pedidos (**este tema**).
1. [Cree un formulario de Resumen](northwind-orders-canvas-part2.md).
1. [Cree una galería de detalles](northwind-orders-canvas-part3.md).

> [!div class="mx-imgBorder"]
> ![definición de áreas de pantalla](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>Requisitos previos

- [Instale la base de datos y las aplicaciones de Northwind Traders](northwind-install.md).
- Lea la [información general de la aplicación Canvas](northwind-orders-canvas-overview.md) para Northwind Traders.

## <a name="create-a-blank-app"></a>Crear una aplicación en blanco

1. [Inicie sesión en PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)y, después, cree una aplicación de tableta en blanco.

    > [!div class="mx-imgBorder"]
    > ![aplicación de lienzo del mosaico en blanco](media/northwind-orders-canvas-part1/start-01.png)

1. Asigne a la aplicación el nombre que desee y, a continuación, seleccione **crear**.

    > [!div class="mx-imgBorder"]
    > ![aplicación de lienzo del cuadro de diálogo en blanco](media/northwind-orders-canvas-part1/start-02.png)

    PowerApps Studio se abre para que pueda agregar orígenes de datos y controles a la aplicación:

    > [!div class="mx-imgBorder"]
    > ![PowerApps Studio](media/northwind-orders-canvas-part1/start-03.png)

## <a name="add-the-data"></a>Agregar los datos

1. En la pestaña **Ver** , seleccione **orígenes de datos**:

    > [!div class="mx-imgBorder"]
    > ![seleccionar vista, orígenes de datos, agregar origen de datos](media/northwind-orders-canvas-part1/datasource-01.png)

1. Escriba **Orders** en el cuadro de búsqueda:

    > [!div class="mx-imgBorder"]
    > ![lista de conexiones](media/northwind-orders-canvas-part1/datasource-02.png)

1. Seleccione el origen de datos de **pedidos** que se va a usar en la aplicación:

    > [!div class="mx-imgBorder"]
    > ![lista de entidades](media/northwind-orders-canvas-part1/datasource-03.png)

    La entidad **Orders** contiene muchos campos de varios tipos:

    > [!div class="mx-imgBorder"]
    > ![lista de campos de la entidad Orders](media/northwind-orders-canvas-part1/datasource-05.png)

    Cada campo tiene un **nombre para mostrar** y un **nombre**, que a veces se denomina nombre lógico. Ambos nombres hacen referencia a lo mismo. En general, usará el nombre para mostrar al compilar una aplicación, pero algunos casos requieren el **nombre**más críptico, como se indica en un procedimiento.

1. Como vamos a trabajar con pantallas y controles a continuación, en PowerApps Studio vuelva a la **vista de árbol** en el lado izquierdo presionando el icono de tres cuadrados apilados. Puede volver a los **orígenes de datos** en cualquier momento presionando el icono del cilindro.

## <a name="create-the-order-gallery"></a>Crear la galería de pedidos

1. En la pestaña **Insertar** , seleccione **Galería** > **vertical en blanco** para agregar un control [**Galería**](controls/control-gallery.md) , que mostrará los pedidos.

    > [!div class="mx-imgBorder"]
    > ![insertar, Galería,](media/northwind-orders-canvas-part1/orders-01.png) vertical en blanco

    El control se colocará en el lienzo y aparecerá un cuadro de diálogo emergente que le preguntará a qué origen de datos se va a conectar.  


    > [!div class="mx-imgBorder"]
    > ![propiedad Set items de la Galería](media/northwind-orders-canvas-part1/orders-02.png)

1. Podríamos conectarlo directamente a los **pedidos** , pero en su lugar nos gustaría controlar el criterio de ordenación de la galería.  Omita el cuadro de diálogo volar hacia fuera y, en la barra de fórmulas, establezca la propiedad **elementos** de la galería en esta fórmula:

    ```powerapps-dot
    Sort( Orders, 'Order Number', Descending )
    ```

    La función [**Sort**](functions/function-sort.md) ordena la lista para que aparezca en primer lugar el orden más reciente (que tiene el número de pedido más alto).

    > [!div class="mx-imgBorder"]
    > ![propiedad Set items de la Galería](media/northwind-orders-canvas-part1/orders-02b.png)

1. Transcurridos unos instantes, la vista de resultados aparecerá debajo de la barra de fórmulas.  Desplácese hacia abajo en la flecha de la izquierda para ver el resultado de la fórmula.  Desplácese hacia la derecha para ver la columna **número de pedido** y asegúrese de que esté ordenada de la forma deseada (de mayor a menor).  

    > [!div class="mx-imgBorder"]
    > ![propiedad Set items de la Galería](media/northwind-orders-canvas-part1/orders-02c.png)

1. En la pestaña **propiedades** situada cerca del borde derecho, abra la lista **diseño** :

    > [!div class="mx-imgBorder"]
    > ![lista de opciones de diseño](media/northwind-orders-canvas-part1/orders-03.png)

1. En la lista de opciones, seleccione **título y subtítulo**:

    > [!div class="mx-imgBorder"]
    > ![seleccionar un diseño](media/northwind-orders-canvas-part1/orders-04.png)

    Se agregan dos controles [**etiqueta**](controls/control-text-box.md) en la plantilla de la galería. De forma predeterminada, estos controles muestran dos columnas de la entidad **Orders** , que cambiará a continuación. La plantilla de la galería se replica verticalmente para cada registro de la entidad.

1. Seleccione **Editar** (junto a **campos**) en la pestaña **propiedades** situada junto al borde derecho.

    > [!div class="mx-imgBorder"]
    > ![seleccionar un diseño](media/northwind-orders-canvas-part1/orders-04b.png)

1. En el panel **datos** , seleccione **Title1** (o seleccione la etiqueta superior en la plantilla de la galería).

1. En la barra de fórmulas, establezca la propiedad **Text** de la etiqueta en esta expresión:

    ```powerapps-dot
    "Order " & ThisItem.'Order Number'
    ```

    > [!div class="mx-imgBorder"]
    > ![establecer la propiedad Text de la etiqueta del título](media/northwind-orders-canvas-part1/orders-06.png)

    El número de pedido aparece en la parte superior de cada elemento de la galería. En la plantilla de la galería, **ThisItem** concede acceso a todos los campos de la entidad **Order** .

1. En el panel **datos** , seleccione **Subtitle1** (o seleccione la etiqueta inferior en la plantilla de la galería):

    > [!div class="mx-imgBorder"]
    > ![seleccionar etiqueta de subtítulo](media/northwind-orders-canvas-part1/orders-07.png)

1. En la barra de fórmulas, establezca la propiedad **Text** de la etiqueta en esta expresión:

    ```powerapps-dot
    ThisItem.Customer.Company
    ```

    > [!div class="mx-imgBorder"]
    > ![establecer la propiedad Text de la etiqueta del subtítulo](media/northwind-orders-canvas-part1/orders-08.png)

    Después de escribir esta fórmula, puede aparecer un error de ondulación de color rojo durante un momento. El error debe desactivarse si selecciona cualquier cosa fuera de la barra de fórmulas y, a continuación, devuelve el cursor a la barra de fórmulas. Si el error persiste o no ve un valor, seleccione la pestaña **vista** , seleccione orígenes de **datos**y, a continuación, actualice la entidad **pedidos** seleccionando los puntos suspensivos (...) a la derecha del nombre del origen de datos.

    Al especificar **ThisItem. Customer**, está aprovechando una relación de varios a uno entre las entidades **Orders** y **Customers** y recuperando el registro del cliente asociado a cada pedido. En el registro del cliente, va a extraer los datos de la columna **Company** para su presentación.

    Puede mostrar todas las relaciones de la entidad **Orders** a otras entidades, incluida la entidad **Customer** :

    > [!div class="mx-imgBorder"]
    > ![lista de relaciones](media/northwind-orders-canvas-part1/orders-09.png)

1. Cierre el panel **datos** seleccionando el icono cerrar (x) en la esquina superior derecha.

## <a name="show-each-orders-status"></a>Mostrar el estado de cada pedido

En este procedimiento, agregará espacio en la galería para una etiqueta y lo configurará para mostrar el estado de cada pedido en un color diferente en función de los datos.

1. En la plantilla de la galería, reduzca el ancho de la primera etiqueta, **Title1**:

    > [!div class="mx-imgBorder"]
    > ![Title1 en la plantilla de la Galería](media/northwind-orders-canvas-part1/status-01.png)

1. Repita el paso anterior con la segunda etiqueta, **Subtitle1**:

    > [!div class="mx-imgBorder"]
    > ![Subtitle1 en la plantilla de la Galería](media/northwind-orders-canvas-part1/status-02.png)

1. Con la plantilla de la galería (o un control de la plantilla) seleccionada, seleccione **etiqueta** en la pestaña **Insertar** :

    > [!div class="mx-imgBorder"]
    > ![agregar una etiqueta](media/northwind-orders-canvas-part1/status-03.png)

1. Mueva la etiqueta nueva a la derecha de la etiqueta **Title1** :

    > [!div class="mx-imgBorder"]
    > ![moverse y cambiar el tamaño de una etiqueta](media/northwind-orders-canvas-part1/status-04.png)

1. Establezca la propiedad **texto** de la nueva etiqueta en esta expresión:

    ```powerapps-dot
    ThisItem.'Order Status'
    ```

    > [!div class="mx-imgBorder"]
    > ![establecer la propiedad Text](media/northwind-orders-canvas-part1/status-05.png)

    En la entidad **pedidos** , el campo **Estado de pedido** contiene un valor del conjunto de opciones de estado de **pedidos** . Un conjunto de opciones es similar a una enumeración en otras herramientas de programación. Cada conjunto de opciones se define en la base de datos, por lo que los usuarios solo pueden especificar las opciones que se encuentran en el conjunto. El conjunto de opciones de **Estado de pedidos** también es global, no local, por lo que puede usarlo en otras entidades:

    > [!div class="mx-imgBorder"]
    > ![conjunto de opciones de estado de pedidos](media/northwind-orders-canvas-part1/status-06.png)

    Cada opción de un conjunto tiene un nombre que aparece si se muestra en una etiqueta. Estos nombres se pueden localizar y la aplicación reconoce la misma opción si un usuario en inglés selecciona **Apple**, un usuario en francés selecciona **pomme**o un usuario en Español selecciona **manzana**. Por esta razón, no se puede crear una fórmula que se base en una cadena codificada de forma rígida para una opción, como se muestra en este tema más adelante.

    En las fórmulas, debe poner el estado de la **orden** entre comillas simples porque contiene un espacio. Sin embargo, ese nombre funciona de la misma forma que cualquier otro nombre de PowerApps, como **cliente** o **empresa**.

1. En la pestaña **Inicio** , aumente el tamaño de fuente de la etiqueta estado a 20 puntos y alinee a la derecha el texto:

    > [!div class="mx-imgBorder"]
    > ![cambiar el tamaño y la alineación de la fuente](media/northwind-orders-canvas-part1/status-07.png)

1. En la barra de fórmulas, establezca la propiedad **color** de la etiqueta estado en esta fórmula:

    ```powerapps-dot
    Switch( ThisItem.'Order Status',
        'Orders Status'.Closed, Green,
        'Orders Status'.New, Black,
        'Orders Status'.Invoiced, Blue,
        'Orders Status'.Shipped, Purple
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![establecer la propiedad color de la etiqueta de estado](media/northwind-orders-canvas-part1/status-08.png)

    PowerApps evita que cree una fórmula que se base en una cadena codificada de forma rígida para cada opción de un conjunto, ya que dichas fórmulas podrían producir resultados inadecuados si los nombres de las opciones están localizados. En su lugar, la función **Switch** determina el color en función de la cadena que aparece en la etiqueta en función de la configuración del usuario.

    Con esta fórmula en su lugar, los distintos valores de estado aparecen en colores diferentes, como se muestra en el gráfico anterior.

## <a name="display-each-orders-total"></a>Mostrar el total de cada pedido

1. Seleccione el primer elemento de la galería, que es la plantilla de la Galería:

    > [!div class="mx-imgBorder"]
    > ![seleccione la plantilla de la Galería](media/northwind-orders-canvas-part1/aggregate-01.png)

1. En la pestaña **Insertar** , seleccione **etiqueta** para agregar otra etiqueta:

    > [!div class="mx-imgBorder"]
    > ![agregar una etiqueta](media/northwind-orders-canvas-part1/aggregate-02.png)

1. Mueva la nueva etiqueta para que aparezca debajo de la etiqueta de estado:

    > [!div class="mx-imgBorder"]
    > ![cambiar el tamaño de la nueva etiqueta y moverla](media/northwind-orders-canvas-part1/aggregate-03.png)

1. En la barra de fórmulas, establezca la propiedad **texto** de la nueva etiqueta en esta fórmula:

    ```powerapps-dot
    Text( Sum( ThisItem.'Order Details', Quantity * 'Unit Price' ), "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![fórmula para calcular el costo total de un pedido](media/northwind-orders-canvas-part1/aggregate-04.png)

    En esta fórmula, la función [**SUM**](functions/function-aggregates.md) suma los registros de la entidad Order **Details** que están asociados a cada registro de la entidad **Order** a través de una relación de uno a varios. Estos elementos de línea forman cada pedido y se utiliza la misma relación uno a varios para mostrar y editar los elementos de línea en el área inferior derecha de la pantalla.

    Esta fórmula muestra un subrayado azul y una [Advertencia de delegación](delegation-overview.md) porque Common Data Service no admite la delegación de funciones de agregado complejas (por ejemplo, la suma de una multiplicación). Puede omitir esta información porque ningún orden en este ejemplo contendrá más de 500 elementos de línea. Si es necesario para una aplicación diferente, puede aumentar ese límite en la configuración de la **aplicación**.

    La función de [**texto**](functions/function-text.md) de esta fórmula agrega un símbolo de divisa y da formato al resultado con separadores de miles y decimales. Tal como se ha escrito, la fórmula incluye la etiqueta de idioma para Inglés de EE. UU. (**[$-en-US]**) y un símbolo de dólar (**$**). Si quita la etiqueta de idioma, se reemplazará por una en función de la configuración de idioma y la etiqueta mostrará los formatos adecuados para dicha etiqueta. Si deja el símbolo de dólar, la etiqueta mostrará el símbolo de moneda adecuado en función de la configuración del usuario. Sin embargo, puede forzar que aparezca un símbolo diferente si reemplaza el símbolo de dólar por el que prefiera.

1. En la pestaña **Inicio** , cambie el tamaño de fuente de la etiqueta más reciente a 20 puntos y alinee a la derecha su texto:

    > [!div class="mx-imgBorder"]
    > ![cambiar el tamaño de fuente y la alineación de una etiqueta](media/northwind-orders-canvas-part1/aggregate-05.png)

1. Mueva la galería al borde izquierdo de la pantalla y disminuya el ancho de la galería para cerrar algo de espacio.

1. Aumente el alto de la galería para que sea casi tan alto como la pantalla, pero deje un poco de espacio en la parte superior de una barra de título, que agregará al principio del siguiente tema:

    > [!div class="mx-imgBorder"]
    > ![moverse y cambiar el tamaño de la Galería](media/northwind-orders-canvas-part1/aggregate-06.png)

## <a name="summary"></a>Resumen

Para recapitular, comenzó a compilar una aplicación de lienzo de pantalla única agregando la galería de pedidos, que incluye estos elementos:

- Una expresión para mostrar el número de pedido: `"Orders " & ThisItem.OrderNumber`
- Campo de una relación de varios a uno: `ThisItem.Customer.Company`
- Etiqueta que muestra el nombre de una opción de un conjunto: `ThisItem.'Order Status'`
- Etiqueta que cambia el formato en función de la opción de un conjunto que muestra la etiqueta: `Switch( ThisItem.'Order Status', 'Orders Status'.Closed, Green, ...`
- Función de agregado compleja sobre una relación de uno a varios: `Sum( ThisItem.'Order Details', Quantity * 'Unit Price' )`

## <a name="next-topic"></a>Siguiente tema

En el tema siguiente, agregará un control [**Editar formulario**](controls/control-form-detail.md) para mostrar y editar un resumen de cualquier orden que el usuario seleccione en la galería que acaba de crear.

> [!div class="nextstepaction"]
> [Crear el formulario de Resumen](northwind-orders-canvas-part2.md)
