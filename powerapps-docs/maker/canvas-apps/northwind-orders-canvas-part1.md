---
title: Creación de una galería de pedidos en una aplicación de lienzo | Microsoft Docs
description: Creación de una galería de pedidos en una aplicación de lienzo para administrar datos de Northwind Traders
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/25/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ac6586067105d5f6cd1ce2aab5568450804fe4c6
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71991369"
---
# <a name="create-an-order-gallery-in-a-canvas-app"></a>Creación de una galería de pedidos en una aplicación de lienzo

Siga las instrucciones paso a paso para crear una galería de pedidos en una aplicación de lienzo para administrar datos ficticios en la base de datos Northwind Traders. Este tema forma parte de una serie en la que se explica cómo compilar una aplicación empresarial en datos relacionales en Common Data Service. Para obtener los mejores resultados, explore estos temas en esta secuencia:

1. Crear una galería de pedidos (**este tema**).
1. [Cree un formulario de Resumen](northwind-orders-canvas-part2.md).
1. [Cree una galería de detalles](northwind-orders-canvas-part3.md).

> [!div class="mx-imgBorder"]
> ![Definition de las áreas de pantalla @ no__t-1

## <a name="prerequisites"></a>Requisitos previos

- [Instale la base de datos y las aplicaciones de Northwind Traders](northwind-install.md).
- Lea la [información general de la aplicación Canvas](northwind-orders-canvas-overview.md) para Northwind Traders.

## <a name="create-a-blank-app"></a>Crear una aplicación en blanco

1. [Inicie sesión en PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)y, después, cree una aplicación de tableta en blanco.

    > [!div class="mx-imgBorder"]
    > @no__t: aplicación 0Canvas del mosaico en blanco @ no__t-1

1. Asigne a la aplicación el nombre que desee y, a continuación, seleccione **crear**.

    > [!div class="mx-imgBorder"]
    > @no__t: aplicación 0Canvas del cuadro de diálogo en blanco @ no__t-1

    PowerApps Studio se abre para que pueda agregar orígenes de datos y controles a la aplicación:

    > [!div class="mx-imgBorder"]
    > ![PowerApps Studio @ no__t-1

1. Habilite una [característica experimental](working-with-experimental.md) para mostrar el resultado de una fórmula directamente en la barra de fórmulas.

    1. En el menú **archivo** , seleccione **configuración**de la aplicación y, a continuación, seleccione **Configuración avanzada**.
    1. Desplácese hasta la parte inferior de la lista de características y, a continuación, Active **Habilitar vista de resultados de la barra de fórmulas**:

        > [!div class="mx-imgBorder"]
        > ![List de las características experimentales @ no__t-1

1. En la esquina superior izquierda, seleccione la flecha atrás para volver al lienzo en blanco.

## <a name="add-the-data"></a>Agregar los datos

1. En la pestaña **Ver** , seleccione **orígenes de datos**y, a continuación, seleccione **Agregar origen de datos** en el panel **datos** :

    > [!div class="mx-imgBorder"]
    > @no__t: vista 0Select, orígenes de datos, agregar origen de datos @ no__t-1

1. Seleccione **Common Data Service**.

    Si **Common Data Service** no aparece en la lista de conexiones, seleccione **nueva conexión**y, a continuación, agréguela.

    > [!div class="mx-imgBorder"]
    > ![List de las conexiones @ no__t-1

1. En **elegir una entidad**, escriba **pedidos**, active la casilla **pedidos** y, a continuación, seleccione **conectar**:

    > [!div class="mx-imgBorder"]
    > ![List de las entidades @ no__t-1

    Ha agregado el origen de datos de **pedidos** a la aplicación:

    > [!div class="mx-imgBorder"]
    > @no__t: panel 0Data @ no__t-1

    La entidad **Orders** contiene muchos campos de varios tipos:

    > [!div class="mx-imgBorder"]
    > ![List de los campos de la entidad Orders @ no__t-1

    Cada campo tiene un **nombre para mostrar** y un **nombre**, que a veces se denomina nombre lógico. Ambos nombres hacen referencia a lo mismo. En general, usará el nombre para mostrar al compilar una aplicación, pero algunos casos requieren el **nombre**más críptico, como se indica en un procedimiento.

1. En PowerApps Studio, cierre el panel **datos** seleccionando el icono cerrar (x) en la esquina superior derecha.

## <a name="create-the-order-gallery"></a>Crear la galería de pedidos

1. En la pestaña **Insertar** , seleccione **Galería** > **vertical en blanco** para agregar un control [**Galería**](controls/control-gallery.md) , que mostrará los pedidos.

    > [!div class="mx-imgBorder"]
    > ![Insert, Galería, vertical en blanco @ no__t-1

1. En la barra de fórmulas, establezca la propiedad **elementos** de la galería en esta fórmula:

    ```powerapps-dot
    Sort( Orders, 'Order Number', Descending )
    ```

    La función [**Sort**](functions/function-sort.md) ordena la lista para que aparezca en primer lugar el orden más reciente (que tiene el número de pedido más alto).

    > [!div class="mx-imgBorder"]
    > @no__t propiedad items de la Galería @ no__t-1

1. En la pestaña **propiedades** situada cerca del borde derecho, abra la lista **diseño** :

    > [!div class="mx-imgBorder"]
    > ![List de las opciones de diseño @ no__t-1

1. En la lista de opciones, seleccione **título y subtítulo**:

    > [!div class="mx-imgBorder"]
    > @no__t 0Select un diseño @ no__t-1

    Se agregan dos controles [**etiqueta**](controls/control-text-box.md) en la plantilla de la galería. De forma predeterminada, estos controles muestran dos columnas de la entidad **Orders** , que cambiará a continuación. La plantilla de la galería se replica verticalmente para cada registro de la entidad.

1. Si ha cerrado el panel **datos** , seleccione **Editar** (junto a **campos**) en la pestaña **propiedades** situada junto al borde derecho.

1. En el panel **datos** , seleccione **Title1** (o seleccione la etiqueta superior en la plantilla de la galería).

1. En la barra de fórmulas, establezca la propiedad **Text** de la etiqueta en esta expresión:

    ```powerapps-dot
    "Order " & ThisItem.'Order Number'
    ```

    > [!div class="mx-imgBorder"]
    > propiedad de texto de la etiqueta del título de @no__t 0Set @ no__t-1

    El número de pedido aparece en la parte superior de cada elemento de la galería. En la plantilla de la galería, **ThisItem** concede acceso a todos los campos de la entidad **Order** .

1. En el panel **datos** , seleccione **Subtitle1** (o seleccione la etiqueta inferior en la plantilla de la galería):

    > [!div class="mx-imgBorder"]
    > @no__t: etiqueta de subtítulo de 0Select @ no__t-1

1. En la barra de fórmulas, establezca la propiedad **Text** de la etiqueta en esta expresión:

    ```powerapps-dot
    ThisItem.Customer.Company
    ```

    > [!div class="mx-imgBorder"]
    > propiedad de texto de la etiqueta de subtítulo de @no__t 0Set @ no__t-1

    Después de escribir esta fórmula, puede aparecer un error de ondulación de color rojo durante un momento. El error debe desactivarse si selecciona cualquier cosa fuera de la barra de fórmulas y, a continuación, devuelve el cursor a la barra de fórmulas. Si el error persiste o no ve un valor, seleccione la pestaña **vista** , seleccione orígenes de **datos**y, a continuación, actualice la entidad **pedidos** seleccionando los puntos suspensivos (...) a la derecha del nombre del origen de datos.

    Al especificar **ThisItem. Customer**, está aprovechando una relación de varios a uno entre las entidades **Orders** y **Customers** y recuperando el registro del cliente asociado a cada pedido. En el registro del cliente, va a extraer los datos de la columna **Company** para su presentación.

    Puede mostrar todas las relaciones de la entidad **Orders** a otras entidades, incluida la entidad **Customer** :

    > [!div class="mx-imgBorder"]
    > ![List de las relaciones @ no__t-1

1. Cierre el panel **datos** seleccionando el icono cerrar (x) en la esquina superior derecha.

## <a name="show-each-orders-status"></a>Mostrar el estado de cada pedido

En este procedimiento, agregará espacio en la galería para una etiqueta y lo configurará para mostrar el estado de cada pedido en un color diferente en función de los datos.

1. En la plantilla de la galería, reduzca el ancho de la primera etiqueta, **Title1**:

    > [!div class="mx-imgBorder"]
    > ![Title1 en la plantilla de la Galería @ no__t-1

1. Repita el paso anterior con la segunda etiqueta, **Subtitle1**:

    > [!div class="mx-imgBorder"]
    > ![Subtitle1 en la plantilla de la Galería @ no__t-1

1. Con la plantilla de la galería (o un control de la plantilla) seleccionada, seleccione **etiqueta** en la pestaña **Insertar** :

    > [!div class="mx-imgBorder"]
    > ![Add etiqueta @ no__t-1

1. Mueva la etiqueta nueva a la derecha de la etiqueta **Title1** :

    > [!div class="mx-imgBorder"]
    > @no__t 0Move y cambiar el tamaño de una etiqueta @ no__t-1

1. Establezca la propiedad **texto** de la nueva etiqueta en esta expresión:

    ```powerapps-dot
    ThisItem.'Order Status'
    ```

    > [!div class="mx-imgBorder"]
    > ![Set la propiedad de texto @ no__t-1

    En la entidad **pedidos** , el campo **Estado de pedido** contiene un valor del conjunto de opciones de estado de **pedidos** . Un conjunto de opciones es similar a una enumeración en otras herramientas de programación. Cada conjunto de opciones se define en la base de datos, por lo que los usuarios solo pueden especificar las opciones que se encuentran en el conjunto. El conjunto de opciones de **Estado de pedidos** también es global, no local, por lo que puede usarlo en otras entidades:

    > [!div class="mx-imgBorder"]
    > @no__t 0Orders-Option status Set @ no__t-1

    Cada opción de un conjunto tiene un nombre que aparece si se muestra en una etiqueta. Estos nombres se pueden localizar y la aplicación reconoce la misma opción si un usuario en inglés selecciona **Apple**, un usuario en francés selecciona **pomme**o un usuario en Español selecciona **manzana**. Por esta razón, no se puede crear una fórmula que se base en una cadena codificada de forma rígida para una opción, como se muestra en este tema más adelante.

    En las fórmulas, debe poner el estado de la **orden** entre comillas simples porque contiene un espacio. Sin embargo, ese nombre funciona de la misma forma que cualquier otro nombre de PowerApps, como **cliente** o **empresa**.

1. En la pestaña **Inicio** , aumente el tamaño de fuente de la etiqueta estado a 20 puntos y alinee a la derecha el texto:

    > [!div class="mx-imgBorder"]
    > @no__t: tamaño y alineación de la fuente de 0Change @ no__t-1

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
    > ![Set la propiedad color de la etiqueta de estado @ no__t-1

    PowerApps evita que cree una fórmula que se base en una cadena codificada de forma rígida para cada opción de un conjunto, ya que dichas fórmulas podrían producir resultados inadecuados si los nombres de las opciones están localizados. En su lugar, la función **Switch** determina el color en función de la cadena que aparece en la etiqueta en función de la configuración del usuario.

    Con esta fórmula en su lugar, los distintos valores de estado aparecen en colores diferentes, como se muestra en el gráfico anterior.

## <a name="display-each-orders-total"></a>Mostrar el total de cada pedido

1. Seleccione el primer elemento de la galería, que es la plantilla de la Galería:

    > [!div class="mx-imgBorder"]
    > ![Select la plantilla de la Galería @ no__t-1

1. En la pestaña **Insertar** , seleccione **etiqueta** para agregar otra etiqueta:

    > [!div class="mx-imgBorder"]
    > ![Add etiqueta @ no__t-1

1. Mueva la nueva etiqueta para que aparezca debajo de la etiqueta de estado:

    > [!div class="mx-imgBorder"]
    > ![Resize y mueva la nueva etiqueta @ no__t-1

1. En la barra de fórmulas, establezca la propiedad **texto** de la nueva etiqueta en esta fórmula:

    ```powerapps-dot
    Text( Sum( ThisItem.'Order Details', Quantity * 'Unit Price' ), "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![Formula para calcular el costo total de un pedido @ no__t-1

    En esta fórmula, la función [**SUM**](functions/function-aggregates.md) suma los registros de la entidad Order **Details** que están asociados a cada registro de la entidad **Order** a través de una relación de uno a varios. Estos elementos de línea forman cada pedido y se utiliza la misma relación uno a varios para mostrar y editar los elementos de línea en el área inferior derecha de la pantalla.

    Esta fórmula muestra un subrayado azul y una [Advertencia de delegación](delegation-overview.md) porque Common Data Service no admite la delegación de funciones de agregado complejas (por ejemplo, la suma de una multiplicación). Puede omitir esta información porque ningún orden en este ejemplo contendrá más de 500 elementos de línea. Si es necesario para una aplicación diferente, puede aumentar ese límite en la configuración de la **aplicación**.

    La función de [**texto**](functions/function-text.md) de esta fórmula agrega un símbolo de divisa y da formato al resultado con separadores de miles y decimales. Tal como se ha escrito, la fórmula incluye la etiqueta de idioma de EE. UU. English ( **[$-en-US]** ) y un símbolo de dólar ( **$** ). Si quita la etiqueta de idioma, se reemplazará por una en función de la configuración de idioma y la etiqueta mostrará los formatos adecuados para dicha etiqueta. Si deja el símbolo de dólar, la etiqueta mostrará el símbolo de moneda adecuado en función de la configuración del usuario. Sin embargo, puede forzar que aparezca un símbolo diferente si reemplaza el símbolo de dólar por el que prefiera.

1. En la pestaña **Inicio** , cambie el tamaño de fuente de la etiqueta más reciente a 20 puntos y alinee a la derecha su texto:

    > [!div class="mx-imgBorder"]
    > ![Change el tamaño de fuente y la alineación de una etiqueta @ no__t-1

1. Mueva la galería al borde izquierdo de la pantalla y disminuya el ancho de la galería para cerrar algo de espacio.

1. Aumente el alto de la galería para que sea casi tan alto como la pantalla, pero deje un poco de espacio en la parte superior de una barra de título, que agregará al principio del siguiente tema:

    > [!div class="mx-imgBorder"]
    > @no__t 0Move y cambiar el tamaño de la Galería @ no__t-1

## <a name="summary"></a>Resumen

Para recapitular, comenzó a compilar una aplicación de lienzo de pantalla única agregando la galería de pedidos, que incluye estos elementos:

- Una expresión para mostrar el número de pedido: `"Orders " & ThisItem.OrderNumber`
- Campo de una relación de varios a uno: `ThisItem.Customer.Company`
- Una etiqueta que muestra el nombre de una opción de un conjunto: `ThisItem.'Order Status'`
- Etiqueta que cambia el formato en función de la opción de un conjunto que muestra la etiqueta: `Switch( ThisItem.'Order Status', 'Orders Status'.Closed, Green, ...`
- Una función de agregado complejo sobre una relación de uno a varios: `Sum( ThisItem.'Order Details', Quantity * 'Unit Price' )`

## <a name="next-topic"></a>Siguiente tema

En el tema siguiente, agregará un control [**Editar formulario**](controls/control-form-detail.md) para mostrar y editar un resumen de cualquier orden que el usuario seleccione en la galería que acaba de crear.

> [!div class="nextstepaction"]
> [Crear el formulario de Resumen](northwind-orders-canvas-part2.md)