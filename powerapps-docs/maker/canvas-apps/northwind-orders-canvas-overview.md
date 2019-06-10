---
title: Información general de la aplicación de lienzo de Northwind Traders | Microsoft Docs
description: ''
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e2f28b07f53646e6fbf5afc0b1510bd37e3262b8
ms.sourcegitcommit: e85072f7a80da308c4caabe20adbf2509588ca57
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66761060"
---
# <a name="overview-of-the-canvas-app-for-northwind-traders"></a>Información general de la aplicación de lienzo de Northwind Traders

Obtenga información acerca de la aplicación de lienzo para administrar relacional datos de Northwind Traders base de datos que usted [instalado en su entorno](northwind-install.md). A continuación, siga las instrucciones paso a paso en los temas siguientes para crear esta aplicación desde cero, y así obtener experiencia práctica trabajar con datos relacionales.

En este tema, descubrir:

- Cómo un usuario de la aplicación se muestra y administra datos relacionales en la aplicación.
- Los tipos de datos controlan la aplicación.
- ¿Cómo se crearon las relaciones entre los tipos de datos.

En una sola pantalla, el usuario de la aplicación puede mostrar, actualizar, crear y eliminar pedidos.

> [!div class="mx-imgBorder"]
> ![Aplicación de lienzo completo](media/northwind-orders-canvas-part1/orders-finished.png)

## <a name="explore-the-user-interface"></a>Explorar la interfaz de usuario

### <a name="order-gallery"></a>Galería de orden

En el borde izquierdo de la aplicación, una galería muestra una lista de pedidos, incluido el número de pedido, el estado, el nombre del cliente y el costo total del pedido. El usuario puede desplazarse por la lista para encontrar un pedido y, a continuación, se muestra más información sobre ella seleccionando la flecha del pedido. Más información: [Creación de la Galería de orden](northwind-orders-canvas-part1.md).

### <a name="summary-form"></a>Formulario de resumen

En la esquina superior derecha, un formulario resume en el orden en que el usuario seleccionó en la Galería de orden. El resumen incluye gran parte de la misma información, como hace de dicha galería, pero el resumen muestra también las fechas cuando el pedido se creó y de pago, así como el nombre y la imagen del empleado que administra el orden. El usuario puede cambiar los datos en el formulario, guardar los cambios, cancelarlos o eliminar el pedido seleccionando un icono junto al borde derecho de la barra de título. Más información: [Crear el formulario resumen](northwind-orders-canvas-part2.md).

### <a name="detail-gallery"></a>Galería de detalle

En la esquina inferior derecha, otra galería muestra información acerca de los productos que contiene el pedido seleccionado y en qué cantidades. Cada elemento de esta galería se conoce como un detalle de pedido. Usuario de la aplicación puede agregar y eliminar cualquier elemento de dicha galería mediante el uso de controles en y en él. Más información: [Creación de la Galería de detalle](northwind-orders-canvas-part3.md).

> [!div class="mx-imgBorder"]
> ![Definición de áreas de la pantalla](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="explore-the-data-sources"></a>Explorar los orígenes de datos

Para crear esta aplicación, mostraré los datos de cinco entidades y un conjunto de opciones. De hecho, la mayoría de las áreas de la aplicación muestra datos de varias entidades. Por ejemplo, la Galería de pedido contiene esta información:

- El número de pedido es un campo en el **pedidos** entidad.
- El estado es otro campo en el **pedidos** entidad, una opción de la **estado pedidos** conjunto de opciones.
- El nombre del cliente es un campo en el **clientes** entidad.
- El costo total se calcula según los datos en el **Order Details** entidad.

Contiene el resumen de algunas de la misma información que la lista de pedidos, pero también contiene el nombre y la imagen del empleado que administra el orden. Que se extrae la información de los campos de la **empleados** entidad. La Galería de detalle muestra registros en el **Order Details** entidad y cada producto en esos detalles es un registro en el **productos del pedido** entidad.

## <a name="explore-the-relationships"></a>Explorar las relaciones

Puede mostrar datos de orígenes diferentes (por ejemplo, las entidades) en la misma galería o formulario porque las entidades tienen relaciones que se han creado en la base de datos.

### <a name="many-to-one-relationships"></a>Relaciones de varios a uno

Por ejemplo, información sobre el cliente y el empleado de cada pedido reside en el **clientes** y **empleados** entidades. Por lo tanto, el **pedidos** entidad tiene relaciones de varios a uno con esas entidades porque hay muchos pedidos, cada uno de los cuales puede realizado por un solo cliente y administrado por un solo empleado.

Cada pedido también tiene uno o varios elementos de línea que representan los productos que contiene el orden y sus cantidades. Cada elemento de línea es un registro en el **Order Details** entidad, que extrae información sobre cada producto desde la **productos del pedido** entidad. Cada detalle identifica un solo producto, pero cada producto puede aparecer en varios detalles. Por lo tanto, el **Order Details** entidad tiene una relación de varios a uno con el **productos del pedido** entidad.

### <a name="one-to-many-relationships"></a>Relaciones uno a varios

Cada pedido puede contener varios elementos de línea, pero cada elemento de línea se relaciona con un único pedido. Por lo tanto, el **pedidos** entidad tiene una relación uno a varios con el **Order Details** entidad.

### <a name="dot-notation-for-relationships"></a>La notación de puntos para las relaciones 

Para mostrar datos en función de una relación entre entidades, puede usar el selector de propiedad dot para recorrer a través de una relación de una entidad a otra.  Por ejemplo, cada registro de la **pedidos** entidad extrae información desde el **clientes** entidad para que la Galería de pedido puede mostrar los nombres de cliente. En la galería, configura este comportamiento estableciendo el **texto** propiedad de una etiqueta en esta expresión:<br>`ThisItem.Customer.Company`

**ThisItem** especifica un registro en el **pedidos** entidad y extrae la información de la **clientes** entidad sobre el cliente que realizó el pedido. En este caso, la expresión especifica que aparece el nombre de la empresa del cliente. Sin embargo, todo el registro para ese cliente se extrae, por lo que puede fácilmente mostrar, por ejemplo, una dirección de correo electrónico para ese cliente en su lugar.

Otro ejemplo del recorrido de una entidad a otra, puede especificar que una galería debe mostrar registros en una entidad basada en un registro que el usuario seleccionó en la Galería de otra y que se encuentra en otra entidad. Para mostrar los detalles del pedido, estableceremos la Galería de detalle **elementos** propiedad en esta expresión:<br>`Gallery1.Selected.'Order Details'`

En este caso, **Gallery1.Selected** especifica un registro en el **pedidos** entidad, al igual que **ThisItem** hizo en el ejemplo anterior. Sin embargo, esta expresión no extraer únicamente un solo registro como hacía la expresión anterior. En su lugar, extrae una tabla entera de registros para mostrar el costo por unidad y de nombre de cada producto (como se refleja en el **productos del pedido** entidad) y la cantidad (tal como se refleja en el **Order Details** entidad).

## <a name="do-it-yourself"></a>Hágalo usted mismo

Puede seguir las instrucciones paso a paso para crear la aplicación de lienzo Orders de Northwind.  Las instrucciones se dividen en tres partes:

1. [Crear una galería de orden](northwind-orders-canvas-part1.md).
1. [Crear un formulario de resumen](northwind-orders-canvas-part2.md).
1. [Crear una galería de detalle](northwind-orders-canvas-part3.md).

Si desea continuar, la solución contiene una aplicación de punto de partida para cada parte.  En la lista de aplicaciones, busque **Orders de Northwind (lienzo) - comenzar parte 1** y así sucesivamente.

> [!div class="nextstepaction"]
> [Siga creando la Galería de orden](northwind-orders-canvas-part1.md)
