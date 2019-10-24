---
title: Instalar la base de datos y las aplicaciones de Northwind Traders | Microsoft Docs
description: Instale la base de datos y las aplicaciones Northwind en un entorno para explorar los conceptos relacionales.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/06/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3a2c3b468c7ccc09c49221c65113e66b562f5ed1
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2019
ms.locfileid: "71990852"
---
# <a name="install-northwind-traders-database-and-apps"></a>Instalar la base de datos y las aplicaciones de Northwind Traders

Al seguir los pasos de [esta serie de temas](northwind-orders-canvas-part1.md), puede detectar conceptos sobre los datos relacionales tal como se implementan en una base de datos de ejemplo en Common Data Service. También puede explorar aplicaciones empresariales de ejemplo, tanto de lienzo como basadas en modelos, para administrar esos datos y obtener una experiencia práctica mediante la creación de una aplicación de este tipo. En este primer tema se explica cómo instalar la base de datos Northwind Traders en su propio entorno y obtener acceso a las aplicaciones de ejemplo, que puede abrir para editar para mostrar cómo se compilaron.

Northwind Traders es una organización ficticia que administra pedidos, productos, clientes, proveedores y muchos otros aspectos de una pequeña empresa. Este ejemplo apareció con las primeras versiones de Microsoft Access y sigue estando disponible como una plantilla de acceso.

## <a name="prerequisites"></a>Requisitos previos

- Una licencia de PowerApps que admita Common Data Service. Puede [usar una licencia de evaluación gratuita](../signup-for-powerapps.md) durante 30 días.
- Un entorno con una base de datos de Common Data Service. Puede [crear este tipo de entorno](https://docs.microsoft.com/power-platform/admin/create-environment) si tiene los permisos adecuados.

## <a name="download-the-solution"></a>Descarga de la solución

> [!div class="nextstepaction"]
> [Descargar el archivo de solución de Northwind Traders](https://pwrappssamples.blob.core.windows.net/samples/NorthwindTraders_1_0_0_6.zip)

Este archivo de [solución](../../developer/common-data-service/introduction-solutions.md) (. zip) contiene las definiciones de entidades, conjuntos de opciones y procesos empresariales; las aplicaciones de lienzo y controladas por modelos; y cualquier otra pieza que se use conjuntamente.

## <a name="install-the-solution"></a>Instalar la solución

1. Inicie sesión en [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)y, a continuación, asegúrese de que está trabajando en un entorno que contiene una base de datos Common Data Service.

1. En el panel de navegación izquierdo, seleccione **soluciones**y, a continuación, seleccione **importar** en la barra de herramientas situada en la parte superior de la pantalla:

    > [!div class="mx-imgBorder"]
    > ![Solutions ver e importar ](media/northwind-install/solution-import.png) de punto de entrada de la solución

1. En la página **seleccionar paquete de solución** , seleccione **examinar**.

    > [!div class="mx-imgBorder"]
    > ![Select página paquete de solución antes de que se seleccione el paquete ](media/northwind-install/select-solution2.png)

1. Busque el archivo que ha descargado y, a continuación, seleccione **abrir**.

    A menos que haya seleccionado una ubicación diferente, el archivo estará en la carpeta downloads.

1. Si tiene el archivo correcto (el número de versión puede variar), seleccione **siguiente**:

    > [!div class="mx-imgBorder"]
    > ![Select página paquete de solución una vez seleccionado el paquete ](media/northwind-install/confirm-solution2.png)

1. En la página información de la **solución** , seleccione **siguiente** si el nombre de la solución y el publicador son correctos.

    > [!div class="mx-imgBorder"]
    > ![Solution página de información ](media/northwind-install/confirm-publisher.png)

1. En la página **Opciones de importación** , seleccione **importar** para confirmar el control de mensajes del SDK, que requiere el ejemplo:

    > [!div class="mx-imgBorder"]
    > ![Import página Opciones ](media/northwind-install/confirm-sdk.png)

    Aparece otra página en la que se muestra el progreso de la instalación de la solución en los próximos minutos:

    > [!div class="mx-imgBorder"]
    > barra de ![progress ](media/northwind-install/solution-progress.png)

    Una vez finalizada la instalación, la página original muestra el resultado:

    > [!div class="mx-imgBorder"]
    > ![Importing página de la solución ](media/northwind-install/solution-success.png)

1. Haga clic en **Cerrar**.

## <a name="load-the-sample-data"></a>Carga de los datos de ejemplo

1. Seleccione **aplicaciones**y, a continuación, seleccione **datos de ejemplo Northwind**.

    Espere unos minutos si las aplicaciones Northwind no aparecen inmediatamente después de instalar la solución:

    > [!div class="mx-imgBorder"]
    > ![Northwind base de datos en la lista de aplicaciones ](media/northwind-install/sample-data-app.png)

1. Cuando la aplicación Pida permiso para interactuar con Common Data Service, seleccione **permitir**:

    > [!div class="mx-imgBorder"]
    > cuadro de diálogo ![Consent para Common Data Service ](media/northwind-install/sample-data-permission.png)

1. Una vez que la aplicación se carga y muestra que las entidades de ejemplo no contienen registros, seleccione **cargar datos** para rellenar las entidades:

    > [!div class="mx-imgBorder"]
    > botón ![Load datos de la Data Manager de ejemplo ](media/northwind-install/sample-data-load.png)

    A medida que la aplicación carga los datos, los puntos de marzo de la parte superior de la aplicación y el número de registros aumenta.

    Las entidades se cargan en un orden específico para que se puedan establecer relaciones entre los registros. Por ejemplo, la entidad Order **Details** tiene una relación de varios a uno con las entidades **Orders** y **Order Products** , que se cargan en primer lugar.

    Puede cancelar el proceso en cualquier momento seleccionando **Cancelar**y puede quitar los datos en cualquier momento seleccionando **Quitar datos**:

    > [!div class="mx-imgBorder"]
    > ![Sample Data Manager a medida que se cargan los datos ](media/northwind-install/sample-data-progress.png)

    Cuando los datos terminan de cargarse **, se muestra la**última fila (**relaciones de varios a varios**) y se vuelven a habilitar los botones **cargar datos** y **Quitar datos** :

    > [!div class="mx-imgBorder"]
    > ![Sample Data Manager una vez cargados los datos ](media/northwind-install/sample-data-complete.png)

## <a name="sample-apps"></a>Aplicaciones de ejemplo

La solución Northwind incluye estas aplicaciones para interactuar con estos datos:

- Pedidos de Northwind (lienzo)
- Pedidos de Northwind (controlados por modelos)

Abra estas aplicaciones de la misma manera que abrió la aplicación en el procedimiento anterior.

### <a name="canvas"></a>Lienzo

Esta aplicación de una sola pantalla ofrece una vista de maestro-detalle simple de la entidad **Orders** , donde puede ver y editar un resumen del pedido y cada artículo de línea de un pedido. Una lista de pedidos aparece cerca del borde izquierdo y puede seleccionar una flecha en esa lista para mostrar un resumen y los detalles de dicho pedido. Más información: [información general de la aplicación Canvas para Northwind Traders](northwind-orders-canvas-overview.md).

> [!div class="mx-imgBorder"]
> ![List de pedidos y detalles en la aplicación de lienzo Northwind ](media/northwind-install/orders-canvas.png)

### <a name="model-driven"></a>Controlado por modelos

Esta aplicación opera en los mismos datos (en la entidad **Orders** ) que la aplicación Canvas. En la lista de pedidos, para mostrar más información sobre un pedido, seleccione su número:

> [!div class="mx-imgBorder"]
> ![list de pedidos en la aplicación controlada por modelos de Northwind ](media/northwind-install/orders-model.png)

Un resumen del pedido aparece en un formulario independiente:

> [!div class="mx-imgBorder"]
> ![order detalles de la aplicación controlada por modelos ](media/northwind-install/orders-model-2.png)

Si se desplaza hacia abajo en el formulario, muestra los mismos elementos de línea que la aplicación Canvas:

> [!div class="mx-imgBorder"]
> ![more detalles del pedido en la aplicación controlada por modelos ](media/northwind-install/orders-model-3.png)

## <a name="do-it-yourself"></a>Hágalo usted mismo

Puede seguir las instrucciones paso a paso para crear la aplicación de lienzo mostrada anteriormente en este tema.  Las instrucciones están divididas en tres partes:

1. [Cree una galería de pedidos](northwind-orders-canvas-part1.md).
1. [Cree un formulario de Resumen](northwind-orders-canvas-part2.md).
1. [Cree una galería de detalles](northwind-orders-canvas-part3.md).

Si desea continuar, la solución contiene una aplicación de punto de partida para cada parte.  En la lista de aplicaciones, busque **Northwind Orders (canvas)-Begin Part 1** , etc.

En esta [información general de la aplicación](northwind-orders-canvas-overview.md) se explica la interfaz de usuario, los orígenes de datos y cómo se usan las relaciones.

> [!div class="nextstepaction"]
> [Para empezar, lea la información general](northwind-orders-canvas-overview.md)
