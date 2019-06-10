---
title: Instalar aplicaciones y la base de datos de Northwind Traders | Microsoft Docs
description: Instalar la base de datos Northwind y las aplicaciones en un entorno para explorar conceptos relacionales.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/06/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 351f9fd4fe369b3073a9edfb0158883140f50693
ms.sourcegitcommit: e85072f7a80da308c4caabe20adbf2509588ca57
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66761037"
---
# <a name="install-northwind-traders-database-and-apps"></a>Instalar aplicaciones y la base de datos de Northwind Traders

Siguiendo los pasos descritos en [esta serie de temas](northwind-orders-canvas-part1.md), puede descubrir conceptos acerca de los datos relacionales como se implementa en una base de datos de ejemplo en Common Data Service. También puede explorar las aplicaciones de negocio de ejemplo, ambos de lienzo y controladas por modelos, para administrar esos datos y ganar experiencia práctica mediante la creación de una aplicación de ese tipo. Este primer tema explica cómo instalar la base de datos de Northwind Traders en su propio entorno y obtener acceso a las aplicaciones de ejemplo que puede abrir para editarlo para mostrar cómo se crearon.

Northwind Traders es una organización ficticia que administra órdenes, productos, clientes, proveedores y muchos otros aspectos de una pequeña empresa. En este ejemplo aparecía con las primeras versiones de Microsoft Access y sigue estando disponible como una plantilla de Access.

## <a name="prerequisites"></a>Requisitos previos

- Una licencia de PowerApps que es compatible con Common Data Service. También puede [utilizar una licencia de evaluación gratuita](../signup-for-powerapps.md) durante 30 días.
- Un entorno con una base de datos de Common Data Service. También puede [crear este entorno](https://docs.microsoft.com/power-platform/admin/create-environment) si tiene los permisos adecuados.

## <a name="download-the-solution"></a>Descargar la solución

> [!div class="nextstepaction"]
> [Descargue el archivo de solución de Northwind Traders](https://pwrappssamples.blob.core.windows.net/samples/NorthwindTraders_1_0_0_6.zip)

Esto [solución](../../developer/common-data-service/introduction-solutions.md) archivo (.zip) contiene las definiciones de entidades, conjuntos de opciones y los procesos empresariales; el elemento canvas y aplicaciones controladas por modelos; y los demás datos que se usan juntos.

## <a name="install-the-solution"></a>Instalar la solución

1. Inicie sesión en [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)y, a continuación, asegúrese de que está trabajando en un entorno que contiene una base de datos de Common Data Service.

1. En el panel de navegación izquierdo, seleccione **soluciones**y, a continuación, seleccione **importación** en la barra de herramientas en la parte superior de la pantalla:

    > [!div class="mx-imgBorder"]
    > ![Punto de entrada de la vista y solución de importación de soluciones](media/northwind-install/solution-import.png)

1. En el **Seleccionar paquete de solución** , seleccione **examinar**.

    > [!div class="mx-imgBorder"]
    > ![Seleccione la página del paquete de solución antes de que está seleccionado el paquete](media/northwind-install/select-solution2.png)

1. Busque el archivo que ha descargado y, a continuación, seleccione **abierto**.

    A menos que se ha seleccionado una ubicación diferente, el archivo estará en la carpeta de descargas.

1. Si tiene el archivo correcto (el número de versión puede variar), seleccione **siguiente**:

    > [!div class="mx-imgBorder"]
    > ![Seleccione la página paquete de solución después de selecciona paquete](media/northwind-install/confirm-solution2.png)

1. En el **información de la solución** página, seleccione **siguiente** si es correcto el nombre de la solución y el publicador.

    > [!div class="mx-imgBorder"]
    > ![Página de información de solución](media/northwind-install/confirm-publisher.png)

1. En el **opciones de importación** página, seleccione **importación** para confirmar el control de mensajes SDK, que requiere que el ejemplo:

    > [!div class="mx-imgBorder"]
    > ![Página de opciones de importación](media/northwind-install/confirm-sdk.png)

    Otra página aparece y muestra el progreso se instala la solución a través de los próximos minutos:

    > [!div class="mx-imgBorder"]
    > ![Barra de progreso](media/northwind-install/solution-progress.png)

    Cuando finalice la instalación, la página original muestra el resultado:

    > [!div class="mx-imgBorder"]
    > ![Importación de la página de la solución](media/northwind-install/solution-success.png)

1. Haga clic en **Cerrar**.

## <a name="load-the-sample-data"></a>Cargar los datos de ejemplo

1. Seleccione **aplicaciones**y, a continuación, seleccione **datos de ejemplo Northwind**.

    Espere unos minutos si las aplicaciones de Northwind no aparecen inmediatamente después de instalar la solución:

    > [!div class="mx-imgBorder"]
    > ![Base de datos Northwind en la lista de aplicaciones](media/northwind-install/sample-data-app.png)

1. Cuando la aplicación solicita permiso para interactuar con Common Data Service, seleccione **permitir**:

    > [!div class="mx-imgBorder"]
    > ![Cuadro de diálogo de consentimiento de Common Data Service](media/northwind-install/sample-data-permission.png)

1. Después de la aplicación se carga y se muestra que las entidades de ejemplo no contienen registros, seleccione **carga datos** para rellenar las entidades:

    > [!div class="mx-imgBorder"]
    > ![Botón de cargar datos en el Administrador de datos de ejemplo](media/northwind-install/sample-data-load.png)

    Como la aplicación carga los datos, en la parte superior de la aplicación y los registros aumenta el número de marzo de puntos.

    Las entidades se cargan en un orden específico para que se pueden establecer relaciones entre los registros. Por ejemplo, el **Order Details** entidad tiene una relación de varios a uno con el **pedidos** y **productos del pedido** entidades, que se cargan en primer lugar.

    Puede cancelar el proceso en cualquier momento seleccionando **cancelar**, y se pueden quitar los datos en cualquier momento seleccionando **quitar datos**:

    > [!div class="mx-imgBorder"]
    > ![Administrador de datos de ejemplo, al cargan datos](media/northwind-install/sample-data-progress.png)

    Cuando los datos finalice la carga, la última fila (**muchos a muchos relaciones**) muestra **realiza**y el **carga datos** y **quitar datos** los botones están habilitados de nuevo:

    > [!div class="mx-imgBorder"]
    > ![Administrador de datos de ejemplo después de cargar datos](media/northwind-install/sample-data-complete.png)

## <a name="sample-apps"></a>Aplicaciones de ejemplo

La solución de Northwind incluye estas aplicaciones para interactuar con los datos:

- Orders de Northwind (lienzo)
- Orders de Northwind (controladas por modelos)

Abra estas aplicaciones de la misma manera que abrió la aplicación en el procedimiento anterior.

### <a name="canvas"></a>Lienzo

Esta aplicación única pantalla ofrece una vista principal-detallada simple de la **pedidos** entidad, donde puede ver y editar un resumen del pedido y cada elemento de línea para un pedido. Aparece una lista de pedidos cerca del borde izquierdo, y puede seleccionar una flecha en la lista para mostrar un resumen y los detalles de ese pedido. Más información: [Información general de la aplicación de lienzo de Northwind Traders](northwind-orders-canvas-overview.md).

> [!div class="mx-imgBorder"]
> ![Aplicación de lienzo de la lista de pedidos y detalles de Northwind](media/northwind-install/orders-canvas.png)

### <a name="model-driven"></a>Controlado por modelos

Esta aplicación funciona en los mismos datos (en el **pedidos** entidad) como la aplicación de lienzo. En la lista de pedidos, mostrar más información sobre un pedido seleccionando su número:

> [!div class="mx-imgBorder"]
> ![lista de pedidos en la aplicación controlada por modelos de Northwind](media/northwind-install/orders-model.png)

Aparecerá un resumen del pedido en un formulario independiente:

> [!div class="mx-imgBorder"]
> ![Detalles del pedido en la aplicación controlada por modelos](media/northwind-install/orders-model-2.png)

Si se desplaza hacia abajo en el formulario, se muestran los mismos elementos de línea como hace la aplicación de lienzo:

> [!div class="mx-imgBorder"]
> ![obtener más detalles del pedido en la aplicación controlada por modelos](media/northwind-install/orders-model-3.png)

## <a name="do-it-yourself"></a>Hágalo usted mismo

Puede seguir las instrucciones paso a paso para crear la aplicación de lienzo mostrada anteriormente en este tema.  Las instrucciones se dividen en tres partes:

1. [Crear una galería de orden](northwind-orders-canvas-part1.md).
1. [Crear un formulario de resumen](northwind-orders-canvas-part2.md).
1. [Crear una galería de detalle](northwind-orders-canvas-part3.md).

Si desea continuar, la solución contiene una aplicación de punto de partida para cada parte.  En la lista de aplicaciones, busque **Orders de Northwind (lienzo) - comenzar parte 1** y así sucesivamente.

Esto [información general de la aplicación](northwind-orders-canvas-overview.md) explica el usuario interfaz, los orígenes de datos y cómo se usan las relaciones.

> [!div class="nextstepaction"]
> [Empiece por leer la información general](northwind-orders-canvas-overview.md)
