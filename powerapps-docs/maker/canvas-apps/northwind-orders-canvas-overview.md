---
title: Información general de la aplicación Canvas para Northwind Traders | Microsoft Docs
description: ''
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 48966659ca12ada12448543492731fff8431fbde
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2019
ms.locfileid: "71995801"
---
# <a name="overview-of-the-canvas-app-for-northwind-traders"></a>Información general de la aplicación Canvas para Northwind Traders

Obtenga información sobre la aplicación Canvas para administrar datos relacionales en la base de datos Northwind Traders que [instaló en su entorno](northwind-install.md). Después, siga las instrucciones paso a paso en los temas siguientes para compilar esta aplicación desde cero, con lo que se consigue experiencia práctica en el trabajo con datos relacionales.

En este tema, descubra:

- Cómo un usuario de la aplicación muestra y administra los datos relacionales en la aplicación.
- Los tipos de datos de la aplicación.
- Cómo se crearon las relaciones entre esos tipos de datos.

En una sola pantalla, el usuario de la aplicación puede mostrar, actualizar, crear y eliminar pedidos.

> [!div class="mx-imgBorder"]
> ![aplicación de lienzo completa](media/northwind-orders-canvas-part1/orders-finished.png)

## <a name="explore-the-user-interface"></a>Exploración de la interfaz de usuario

### <a name="order-gallery"></a>Galería de pedidos

En el borde izquierdo de la aplicación, una galería muestra una lista de pedidos, incluido el número de pedido, el estado, el nombre del cliente y el costo total del pedido. El usuario puede desplazarse por la lista para buscar un pedido y, a continuación, Mostrar más información sobre él seleccionando la flecha del pedido. Más información: [creación de la galería de pedidos](northwind-orders-canvas-part1.md).

### <a name="summary-form"></a>Formulario de Resumen

En la esquina superior derecha, un formulario resume el orden en que el usuario seleccionó en la galería de pedidos. El resumen incluye gran parte de la misma información que la galería, pero en el resumen también se muestran las fechas en las que se creó y se pagó el pedido, así como el nombre y la imagen del empleado que administró el pedido. El usuario puede cambiar los datos en el formulario, guardar los cambios, cancelarlos o eliminar el orden seleccionando un icono cerca del borde derecho de la barra de título. Más información: [crear el formulario de Resumen](northwind-orders-canvas-part2.md).

### <a name="detail-gallery"></a>Galería de detalles

En la esquina inferior derecha, otra galería muestra información sobre qué productos contiene el pedido seleccionado y en qué cantidades. Cada elemento de esta galería se conoce como detalle del pedido. El usuario de la aplicación puede Agregar y eliminar cualquier elemento de la galería mediante el uso de controles en y debajo de él. Más información: [crear la galería de detalles](northwind-orders-canvas-part3.md).

> [!div class="mx-imgBorder"]
> ![definición de áreas de pantalla](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="explore-the-data-sources"></a>Explorar los orígenes de datos

Para crear esta aplicación, se mostrarán los datos de cinco entidades y un conjunto de opciones. De hecho, la mayoría de las áreas de esta aplicación muestran datos de varias entidades. Por ejemplo, la galería de pedidos contiene esta información:

- El número de pedido es un campo de la entidad **Orders** .
- El estado es otro campo de la entidad **pedidos** , una opción de la opción **Estado de pedidos** establecida.
- El nombre del cliente es un campo de la entidad **Customers** .
- El costo total se calcula en función de los datos de la entidad **Order Details** .

El Resumen contiene parte de la misma información que la lista de pedidos, pero también contiene el nombre y la imagen del empleado que administró el pedido. Esa información se extrae de los campos de la entidad **Employees** . La galería de detalles muestra los registros en la entidad **Order Details** , y cada producto de estos detalles es un registro de la entidad **Order Products** .

## <a name="explore-the-relationships"></a>Explorar las relaciones

Puede mostrar datos de orígenes diferentes (por ejemplo, entidades) en la misma Galería o formulario porque esas entidades tienen relaciones que se crearon automáticamente en la base de datos.

### <a name="many-to-one-relationships"></a>Relaciones de varios a uno

Por ejemplo, la información sobre el cliente y el empleado de cada pedido reside en las entidades **Customers** y **Employees** . Por lo tanto, la entidad **Orders** tiene relaciones de varios a uno con esas entidades, ya que hay muchos pedidos, cada uno de los cuales puede ser colocado por un solo cliente y ser administrado por un solo empleado.

Cada pedido también tiene uno o más artículos de línea que representan los productos que el pedido contiene y sus cantidades. Cada elemento de línea es un registro de la entidad Order **Details** , que extrae información sobre cada producto de la entidad **Order Products** . Cada detalle identifica un solo producto, pero cada producto puede aparecer en varios detalles. Por lo tanto, la entidad Order **Details** tiene una relación de varios a uno con la entidad **Order Products** .

### <a name="one-to-many-relationships"></a>Relaciones uno a varios

Cada pedido puede contener varios elementos de línea, pero cada artículo de línea se relaciona con un único pedido. Por lo tanto, la entidad **Orders** tiene una relación de uno a varios con la entidad **Order Details** .

### <a name="dot-notation-for-relationships"></a>Notación de puntos para las relaciones 

Para Mostrar datos en función de una relación entre entidades, puede usar el selector de propiedades de punto para recorrer una relación de una entidad a otra.  Por ejemplo, cada registro de la entidad **Orders** extrae información de la entidad **Customers** para que la galería de pedidos pueda mostrar los nombres de los clientes. En esa Galería, configure este comportamiento estableciendo la propiedad **texto** de una etiqueta en esta expresión:<br>`ThisItem.Customer.Company`

**ThisItem** especifica un registro en la entidad **Orders** y extrae información de la entidad **Customers** sobre el cliente que realizó el pedido. En este caso, la expresión especifica que aparece el nombre de la empresa del cliente. Sin embargo, se extrae todo el registro para ese cliente, por lo que puede mostrar fácilmente, por ejemplo, una dirección de correo electrónico para ese cliente.

Como otro ejemplo de recorrido de una entidad a otra, puede especificar que una galería muestre los registros de una entidad en función de un registro que el usuario seleccionó en otra galería y que se encuentra en otra entidad. Para mostrar los detalles del pedido, establezca la propiedad **Items** de la galería de detalles en esta expresión:<br>`Gallery1.Selected.'Order Details'`

En este caso, **Gallery1. Selected** especifica un registro en la entidad **Orders** , tal y como **ThisItem** hizo en el ejemplo anterior. Sin embargo, esta expresión no extrae un solo registro como hizo la expresión anterior. En su lugar, extrae una tabla completa de registros para mostrar el nombre y el costo por unidad de cada producto (como se refleja en la entidad **Order Products** ) y la cantidad (como se refleja en la entidad Order **Details** ).

## <a name="do-it-yourself"></a>Hágalo usted mismo

Puede seguir las instrucciones paso a paso para crear la aplicación de lienzo Orders de Northwind.  Las instrucciones están divididas en tres partes:

1. [Cree una galería de pedidos](northwind-orders-canvas-part1.md).
1. [Cree un formulario de Resumen](northwind-orders-canvas-part2.md).
1. [Cree una galería de detalles](northwind-orders-canvas-part3.md).

Si desea continuar, la solución contiene una aplicación de punto de partida para cada parte.  En la lista de aplicaciones, busque **Northwind Orders (canvas)-Begin Part 1** , etc.

> [!div class="nextstepaction"]
> [Continúe creando la galería de pedidos](northwind-orders-canvas-part1.md)
