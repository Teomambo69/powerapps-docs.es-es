---
title: Crear una galería de pedido en una aplicación de lienzo | Microsoft Docs
description: Crear una galería de pedido en una aplicación de lienzo para administrar los datos de Northwind Traders
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
ms.openlocfilehash: 94d6c104cb888bb13f3724231d7891d622f5377b
ms.sourcegitcommit: e85072f7a80da308c4caabe20adbf2509588ca57
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66761014"
---
# <a name="create-an-order-gallery-in-a-canvas-app"></a>Crear una galería de pedido en una aplicación de lienzo

Siga las instrucciones paso a paso para crear una galería de pedido en una aplicación de lienzo para administrar datos ficticios de la base de datos de Northwind Traders. En este tema forma parte de una serie que se explica cómo compilar una aplicación empresarial en datos relacionales de Common Data Service. Para obtener mejores resultados, explore estos temas en esta secuencia:

1. Crear una galería de pedido (**en este tema**).
1. [Crear un formulario de resumen](northwind-orders-canvas-part2.md).
1. [Crear una galería de detalle](northwind-orders-canvas-part3.md).

> [!div class="mx-imgBorder"]
> ![Definición de áreas de la pantalla](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>Requisitos previos

- [Instalar las aplicaciones y la base de datos de Northwind Traders](northwind-install.md).
- Lea la [información general de la aplicación de lienzo](northwind-orders-canvas-overview.md) de Northwind Traders.

## <a name="create-a-blank-app"></a>Crear una aplicación en blanco

1. [Inicie sesión en PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)y, a continuación, cree una aplicación de tableta en blanco.

    > [!div class="mx-imgBorder"]
    > ![Aplicación de lienzo de icono en blanco](media/northwind-orders-canvas-part1/start-01.png)

1. El nombre de la aplicación cualquier le gustaría y a continuación, seleccione **crear**.

    > [!div class="mx-imgBorder"]
    > ![Aplicación de lienzo en el cuadro de diálogo en blanco](media/northwind-orders-canvas-part1/start-02.png)

    Se abre PowerApps Studio para que puedan agregar orígenes de datos y controles a la aplicación:

    > [!div class="mx-imgBorder"]
    > ![PowerApps Studio](media/northwind-orders-canvas-part1/start-03.png)

1. Habilitar un [característica experimental](working-with-experimental.md) para mostrar el resultado de una fórmula directamente desde la barra de fórmulas.

    1. En el **archivo** menú, seleccione **configuración de la aplicación**y, a continuación, seleccione **configuración avanzada**.
    1. Desplácese hasta la parte inferior de la lista de características y, a continuación, activar **habilitar la barra de vista de resultados de fórmulas**:

        > [!div class="mx-imgBorder"]
        > ![Lista de características experimentales](media/northwind-orders-canvas-part1/start-04.png)

1. En la esquina superior izquierda, seleccione la flecha Atrás para volver al lienzo en blanco.

## <a name="add-the-data"></a>Agregue los datos

1. En el **vista** ficha, seleccione **orígenes de datos**y, a continuación, seleccione **agregar origen de datos** en el **datos** panel:

    > [!div class="mx-imgBorder"]
    > ![Seleccione la vista de orígenes de datos, agregar origen de datos](media/northwind-orders-canvas-part1/datasource-01.png)

1. Seleccione **de Common Data Service**.

    Si **Common Data Service** no aparece en la lista de conexiones, seleccionadas **nueva conexión**y, a continuación, agréguelo.

    > [!div class="mx-imgBorder"]
    > ![Lista de conexiones](media/northwind-orders-canvas-part1/datasource-02.png)

1. En **elegir una entidad**, tipo **pedidos**, seleccione el **pedidos** casilla de verificación y, a continuación, seleccione **Connect**:

    > [!div class="mx-imgBorder"]
    > ![Lista de entidades](media/northwind-orders-canvas-part1/datasource-03.png)

    Ha agregado el **pedidos** origen de datos a la aplicación:

    > [!div class="mx-imgBorder"]
    > ![Panel de datos](media/northwind-orders-canvas-part1/datasource-04.png)

    El **pedidos** entidad contiene muchos campos de distintos tipos:

    > [!div class="mx-imgBorder"]
    > ![Lista de campos de la entidad pedidos](media/northwind-orders-canvas-part1/datasource-05.png)

    Cada campo tiene un **nombre para mostrar** y un **nombre**, que a veces se denomina el nombre lógico. Ambos nombres hacen referencia a la misma cosa. En general, usará el nombre para mostrar al compilar una aplicación, pero algunos casos requieren más críptica **nombre**, tal y como se indica en un procedimiento.

1. En PowerApps Studio, cierre el **datos** panel seleccionando el icono Cerrar (x) en la esquina superior derecha.

## <a name="create-the-order-gallery"></a>Creación de la Galería de orden

1. En el **insertar** ficha, seleccione **galería** > **en blanco vertical** para agregar un [ **galería** ](controls/control-gallery.md)control, que mostrará los pedidos.

    > [!div class="mx-imgBorder"]
    > ![INSERT, la galería, en blanco vertical](media/northwind-orders-canvas-part1/orders-01.png)

1. En la barra de fórmulas, establezca la galería **elementos** propiedad en esta fórmula:

    ```powerapps-dot
    Sort( Orders, 'Order Number', Descending )
    ```

    El [ **ordenación** ](functions/function-sort.md) función ordena la lista de tal modo que el orden más reciente (que tiene el número de orden más alto) aparece en primer lugar.

    > [!div class="mx-imgBorder"]
    > ![Establece la propiedad de los elementos de la Galería](media/northwind-orders-canvas-part1/orders-02.png)

1. En el **propiedades** ficha cerca del borde derecho, abrirlo el **diseño** lista:

    > [!div class="mx-imgBorder"]
    > ![Lista de opciones de diseño](media/northwind-orders-canvas-part1/orders-03.png)

1. En la lista de opciones, seleccione **título y subtítulo**:

    > [!div class="mx-imgBorder"]
    > ![Seleccione un diseño](media/northwind-orders-canvas-part1/orders-04.png)

    Dos [ **etiqueta** ](controls/control-text-box.md) se agregan controles en la plantilla de la galería. De forma predeterminada, estos controles muestran dos columnas de la **pedidos** entidad, que se va a cambiar a continuación. Plantilla de la galería se replica verticalmente para cada registro de la entidad.

1. Si ha cerrado el **datos** panel, seleccione **editar** (junto a **campos**) en el **propiedades** ficha cerca del borde derecho.

1. En el **datos** panel, seleccione **Title1** (o seleccione la etiqueta superior de la plantilla de la Galería).

1. En la barra de fórmulas, establezca la etiqueta **texto** propiedad en esta expresión:

    ```powerapps-dot
    "Order " & ThisItem.'Order Number'
    ```

    > [!div class="mx-imgBorder"]
    > ![Establezca la propiedad de texto de la etiqueta de título](media/northwind-orders-canvas-part1/orders-06.png)

    El número de pedido aparece en la parte superior de cada elemento de la galería. En la plantilla de la galería, **ThisItem** concede acceso a todos los campos en el **orden** entidad.

1. En el **datos** panel, seleccione **subtítulo1** (o seleccione la etiqueta inferior de la plantilla de la Galería):

    > [!div class="mx-imgBorder"]
    > ![Seleccionar etiqueta de subtítulo](media/northwind-orders-canvas-part1/orders-07.png)

1. En la barra de fórmulas, establezca la etiqueta **texto** propiedad en esta expresión:

    ```powerapps-dot
    ThisItem.Customer.Company
    ```

    > [!div class="mx-imgBorder"]
    > ![Establezca la propiedad de texto de la etiqueta de subtítulo](media/northwind-orders-canvas-part1/orders-08.png)

    Después de escribir esta fórmula, puede mostrar un error roja y serpenteante por un momento. Si selecciona cualquier elemento fuera de la barra de fórmulas y, a continuación, devolver el cursor a la barra de fórmulas, debe borrar el error. Si el error persiste o no se ve un valor, seleccione el **vista** ficha, seleccione **orígenes de datos**y, a continuación, actualice el **pedidos** entidad seleccionando el botón de puntos suspensivos (...) para el derecha del nombre del origen de datos.

    Al especificar **ThisItem.Customer**, podemos aprovechar una relación de varios a uno entre el **pedidos** y **clientes** entidades y recuperar el registro del cliente que se asocia con cada pedido. Desde el registro del cliente, que está extrayendo los datos en el **empresa** columna para mostrar.

    Puede mostrar todas las relaciones de la **pedidos** entidad a otras entidades, incluido el **cliente** entidad:

    > [!div class="mx-imgBorder"]
    > ![Lista de relaciones](media/northwind-orders-canvas-part1/orders-09.png)

1. Cierre el **datos** panel seleccionando el icono Cerrar (x) en la esquina superior derecha.

## <a name="show-each-orders-status"></a>Mostrar estado de cada pedido.

En este procedimiento, deberá agregar espacio en la Galería para una etiqueta y configurarlo para mostrar el estado de cada pedido en un color diferente en función de los datos.

1. En la plantilla de la galería, reduzca el ancho de la primera etiqueta, **Title1**:

    > [!div class="mx-imgBorder"]
    > ![Title1 en la plantilla de la Galería](media/northwind-orders-canvas-part1/status-01.png)

1. Repita el paso anterior con la segunda etiqueta, **subtítulo1**:

    > [!div class="mx-imgBorder"]
    > ![Subtítulo1 en la plantilla de la Galería](media/northwind-orders-canvas-part1/status-02.png)

1. Con la Galería de plantillas (o un control en la plantilla) seleccionado, seleccione **etiqueta** en el **insertar** pestaña:

    > [!div class="mx-imgBorder"]
    > ![Agregue una etiqueta](media/northwind-orders-canvas-part1/status-03.png)

1. Mover la nueva etiqueta a la derecha de la **Title1** etiqueta:

    > [!div class="mx-imgBorder"]
    > ![Mover y cambiar el tamaño de una etiqueta](media/northwind-orders-canvas-part1/status-04.png)

1. Establecer el **texto** propiedad de la nueva etiqueta para esta expresión:

    ```powerapps-dot
    ThisItem.'Order Status'
    ```

    > [!div class="mx-imgBorder"]
    > ![Establezca la propiedad Text](media/northwind-orders-canvas-part1/status-05.png)

    En el **pedidos** entidad, el **estado del pedido** campo contiene un valor de la **estado pedidos** conjunto de opciones. Un conjunto de opciones es similar a una enumeración en otras herramientas de programación. Cada conjunto de opciones se define en la base de datos, por lo que los usuarios pueden especificar sólo las opciones que están en el conjunto. El **estado pedidos** conjunto de opciones también es global, no es local, por lo que puede usar en otras entidades:

    > [!div class="mx-imgBorder"]
    > ![Ordena el conjunto de opciones de estado](media/northwind-orders-canvas-part1/status-06.png)

    Cada opción en un conjunto tiene un nombre que aparece si se muestra en una etiqueta. Estos nombres se pueden localizar y la aplicación reconoce la misma opción si selecciona un usuario inglés **Apple**, selecciona un usuario francés **Pomme**, o un usuario español selecciona **Manzana**. Por este motivo, no se puede crear una fórmula que se basa en una cadena codificada de forma rígida para una opción, como se muestra más adelante en este tema.

    En las fórmulas, se debe encerrar **estado del pedido** con comillas simples porque contiene un espacio. Sin embargo, ese nombre funciona de la misma manera que cualquier otro nombre en PowerApps, como **cliente** o **empresa**, does.

1. En el **inicio** pestaña, aumentar el tamaño de fuente de la etiqueta de estado en 20 puntos y alinear a la derecha el texto:

    > [!div class="mx-imgBorder"]
    > ![Cambiar el tamaño de fuente y la alineación](media/northwind-orders-canvas-part1/status-07.png)

1. En la barra de fórmulas, establezca el **Color** propiedad de la etiqueta de estado en esta fórmula:

    ```powerapps-dot
    Switch( ThisItem.'Order Status',
        'Orders Status'.Closed, Green,
        'Orders Status'.New, Black,
        'Orders Status'.Invoiced, Blue,
        'Orders Status'.Shipped, Purple
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![Establezca la propiedad de Color de la etiqueta de estado](media/northwind-orders-canvas-part1/status-08.png)

    PowerApps le impide crear una fórmula que se basa en una cadena codificada de forma rígida para cada opción en un conjunto, ya que estas fórmulas podrían generar resultados inadecuados si se localizan los nombres de opción. En su lugar, el **conmutador** función determina el color en función de cualquier cadena aparece en la etiqueta basándose en la configuración del usuario.

    Con esta fórmula en su lugar, los valores de estado diferentes aparecen en distintos colores, como se muestra en el gráfico anterior.

## <a name="display-each-orders-total"></a>Mostrar el total de cada uno

1. Seleccione el primer elemento de la galería, que es la plantilla de la Galería:

    > [!div class="mx-imgBorder"]
    > ![Seleccione la plantilla de la Galería](media/northwind-orders-canvas-part1/aggregate-01.png)

1. En el **insertar** ficha, seleccione **etiqueta** para agregar otra etiqueta:

    > [!div class="mx-imgBorder"]
    > ![Agregue una etiqueta](media/northwind-orders-canvas-part1/aggregate-02.png)

1. Mover la nueva etiqueta para que aparezca debajo de la etiqueta de estado:

    > [!div class="mx-imgBorder"]
    > ![Cambiar el tamaño y mover la nueva etiqueta](media/northwind-orders-canvas-part1/aggregate-03.png)

1. En la barra de fórmulas, establezca la nueva etiqueta **texto** propiedad en esta fórmula:

    ```powerapps-dot
    Text( Sum( ThisItem.'Order Details', Quantity * 'Unit Price' ), "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![Fórmula para calcular el costo total de un pedido](media/northwind-orders-canvas-part1/aggregate-04.png)

    En esta fórmula, el [ **suma** ](functions/function-aggregates.md) función agrega los registros en el **Order Details** entidades que están asociados con cada registro de la **orden**entidad a través de una relación uno a varios. Estos elementos de línea componen cada pedido y usará la misma relación de uno a varios para mostrar y editar los elementos de línea en el área inferior derecha de la pantalla.

    Esta fórmula muestra un subrayado azul y un [advertencia de delegación](delegation-overview.md) porque Common Data Service no es compatible con la delegación de funciones de agregado complejas (por ejemplo, la suma de una multiplicación). Puede omitir esta información porque ningún orden en este ejemplo contendrá más de 500 elementos de línea. Si es necesario para una aplicación diferente, puede aumentar dicho límite en **configuración de la aplicación**.

    El [ **texto** ](functions/function-text.md) función en esta fórmula agrega un símbolo de moneda y da formato al resultado con separadores de miles y decimal. Mientras escribe, la fórmula incluye la etiqueta de idioma para EE. UU. Inglés ( **[$-en-US]** ) y un símbolo de dólar ( **$** ). Si quita la etiqueta de idioma, se reemplazará con uno basado en la configuración de idioma y la etiqueta mostrará los formatos adecuados para esa etiqueta. Si deja el símbolo de dólar, la etiqueta mostrará el símbolo de moneda adecuado según la configuración del usuario. Sin embargo, puede forzar otro símbolo aparezcan reemplazando el símbolo de dólar por lo que prefiera.

1. En el **inicio** pestaña, cambiar el tamaño de fuente de la etiqueta más reciente en 20 puntos y alinear a la derecha el texto:

    > [!div class="mx-imgBorder"]
    > ![Cambiar el tamaño de fuente y la alineación de una etiqueta](media/northwind-orders-canvas-part1/aggregate-05.png)

1. Mueva la galería y el borde izquierdo de la pantalla y reducir el ancho de la Galería para cerrar un poco de espacio.

1. Aumentar el alto de la Galería para que sea casi tan alto como la pantalla, pero dejar un poco espacio en la parte superior para una barra de título, que se va a agregar al principio del tema siguiente:

    > [!div class="mx-imgBorder"]
    > ![Mover y cambiar el tamaño de la Galería](media/northwind-orders-canvas-part1/aggregate-06.png)

## <a name="summary"></a>Resumen

Para recapitular, ya comenzó a crear una aplicación de lienzo única pantalla mediante la adición de la Galería de orden, que incluye estos elementos:

- Una expresión para mostrar el número de pedido: `"Orders " & ThisItem.OrderNumber`
- Un campo en una relación varios a uno: `ThisItem.Customer.Company`
- Una etiqueta que muestra el nombre de una opción en un conjunto: `ThisItem.'Order Status'`
- Una etiqueta que cambia el formato basado en la etiqueta de opción en un conjunto de muestra: `Switch( ThisItem.'Order Status', 'Orders Status'.Closed, Green, ...`
- Una función de agregado compleja a través de una relación uno a varios: `Sum( ThisItem.'Order Details', Quantity * 'Unit Price' )`

## <a name="next-topic"></a>Siguiente tema

En el tema siguiente, agregará un [ **Editar formulario** ](controls/control-form-detail.md) control para mostrar y editar un resumen de todo lo que ordenar el usuario selecciona en la galería que acaba de crear.

> [!div class="nextstepaction"]
> [Crear el formulario de resumen](northwind-orders-canvas-part2.md)