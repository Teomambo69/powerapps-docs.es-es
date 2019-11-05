---
title: Agregar y configurar un control de aplicación de lienzo| Microsoft Docs
description: Instrucciones paso a paso para agregar y configurar controles de aplicación de lienzo directamente desde la barra de herramientas, en la pestaña Propiedades, o en la barra de fórmulas.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/25/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 29fcc240bdf0dbe926acb702c26d535fb4536c16
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73537118"
---
# <a name="add-and-configure-a-canvas-app-control-in-powerapps"></a>Agregar y configurar un control de aplicación de lienzo en PowerApps

Agregue diversos elementos de interfaz de usuario a su aplicación de lienzo y configure aspectos de su apariencia y comportamiento directamente desde la barra de herramientas, en la pestaña **Propiedades**, o en la barra de fórmulas. Estos elementos de interfaz de usuario se denominan controles y los aspectos que configura se denominan propiedades.

## <a name="prerequisites"></a>Requisitos previos

1. Si aún no tiene una licencia de PowerApps, [Regístrese](../signup-for-powerapps.md)y, a continuación, [inicie sesión](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
1. En **crear su propia aplicación**, mantenga el mouse sobre la **aplicación Canvas en blanco**y, a continuación, seleccione **crear esta aplicación**.
1. Si se le pide que realice el paseo introductorio, seleccione **siguiente** para familiarizarse con las áreas clave de la interfaz de PowerApps (o seleccione **omitir**).

    Siempre puede realizar el paseo más adelante seleccionando el icono de signo de interrogación situado cerca de la esquina superior derecha de la pantalla y, a continuación, seleccionando **realizar el paseo introductorio**.

## <a name="add-and-select-a-control"></a>Agregar y seleccionar un control

En la pestaña **Insertar** , realice cualquiera de estos pasos:

- Seleccione **etiqueta** o **botón** para agregar uno de esos tipos de controles.
- Seleccione una categoría de controles y, a continuación, seleccione el tipo de control que desea agregar.

Por ejemplo, seleccione **nueva pantalla**y, a continuación, seleccione **en blanco** para agregar una pantalla en blanco a la aplicación. (Las pantallas son un tipo de control que puede contener otros tipos de controles).

![Agregar pantalla](./media/add-configure-controls/add-screen.png)

La nueva pantalla se denomina **Screen2** y aparece en el panel de navegación izquierdo. Este panel muestra una lista jerárquica de los controles de la aplicación para que pueda encontrar y seleccionar cada control fácilmente.

![Screen2 en la lista](./media/add-configure-controls/list-screen2.png)

Para demostrar cómo funciona esta lista, seleccione **etiqueta** en la pestaña **Insertar** . El nuevo control aparece en **Screen2** en la lista jerárquica.

![Screen2 en la lista](./media/add-configure-controls/add-label.png)

En la pantalla, un cuadro con seis controladores rodea la etiqueta de forma predeterminada. Ese tipo de cuadro rodea el control que está seleccionado. Si selecciona la pantalla haciendo clic o pulsando en ella (pero fuera de la etiqueta), el cuadro desaparece de la etiqueta. Para volver a seleccionar la etiqueta, puede hacer clic o pulsar en ella, o puede hacer clic o pulsar en su nombre en la lista jerárquica de controles.

> [!IMPORTANT]
> Siempre debe seleccionar un control antes de poder configurarlo.

## <a name="rename-a-control"></a>Cambiar el nombre de un control

En la lista jerárquica de controles, mantenga el mouse sobre el control cuyo nombre desea cambiar, seleccione el botón de puntos suspensivos que aparece y, a continuación, seleccione **cambiar nombre**. Después, puede escribir un nombre único y memorable para facilitar la compilación de la aplicación.

![Cambiar el nombre del control](./media/add-configure-controls/rename-control.png)

## <a name="delete-a-control"></a>Eliminar un control

En la lista jerárquica de controles, mantenga el mouse sobre el control que desea eliminar, seleccione el botón de puntos suspensivos que aparece y, a continuación, seleccione **eliminar**. Para eliminar un control que no es una pantalla, también puede seleccionar el control en el lienzo y, a continuación, presionar la tecla Supr.

![Eliminar control](./media/add-configure-controls/delete-control.png)

## <a name="reorder-screens"></a>Cambiar el orden de las pantallas

En la lista jerárquica de controles, mantenga el mouse sobre una pantalla que desea mover hacia arriba o hacia abajo, seleccione el botón de puntos suspensivos que aparece y, a continuación, seleccione **subir** o **bajar**.

![Volver a ordenar pantalla](./media/add-configure-controls/reorder-screen.png)

> [!NOTE]
> Cuando se abre la aplicación, la pantalla situada en la parte superior de la lista jerárquica de controles suele aparecer en primer lugar. Pero puede especificar una pantalla diferente si establece la propiedad **[OnStart](controls/control-screen.md)** en una fórmula que incluya la función **[Navigate](functions/function-navigate.md)** .

## <a name="move-and-resize-a-control"></a>Movimiento y cambio de tamaño de un control

Para mover un control, selecciónelo, mantenga el mouse sobre el centro para que aparezca la flecha de cuatro puntas y, a continuación, arrastre el control a una ubicación diferente.

![Control de movimiento](./media/add-configure-controls/move-control.png)

Para cambiar el tamaño de un control, selecciónelo, mantenga el mouse sobre cualquier controlador en el cuadro de selección para que aparezca la flecha de dos puntas y, a continuación, arrastre el controlador.

![Control de movimiento](./media/add-configure-controls/resize-control.png)

> [!NOTE]
> Como se describe más adelante en este tema, también puede moverse y cambiar el tamaño de un control modificando cualquier combinación de sus propiedades **[X](controls/properties-size-location.md)** , **[y](controls/properties-size-location.md)** , **[height](controls/properties-size-location.md)** y **[width](controls/properties-size-location.md)** en la barra de fórmulas.

## <a name="change-the-text-of-a-label-or-a-button"></a>Cambiar el texto de una etiqueta o un botón

Seleccione una etiqueta o un botón, haga doble clic en el texto que aparece en el control y, a continuación, escriba el texto que desee.

![Cambiar texto](./media/add-configure-controls/change-text.png)

> [!NOTE]
> Como se describe más adelante en este tema, también puede cambiar este texto modificando su propiedad **[texto](controls/properties-core.md)** en la barra de fórmulas.

## <a name="configure-a-control-from-the-toolbar"></a>Configuración de un control desde la barra de herramientas

Al configurar un control desde la barra de herramientas, puede especificar una mayor variedad de opciones que si lo hace directamente.

Por ejemplo, puede seleccionar una etiqueta, seleccionar la pestaña **Inicio** y, a continuación, cambiar la fuente del texto en la etiqueta.

![Cambiar fuente](./media/add-configure-controls/change-font.png)

## <a name="configure-a-control-from-the-properties-tab"></a>Configuración de un control mediante la pestaña Propiedades

Mediante el uso de la pestaña **propiedades** , puede especificar una mayor variedad de opciones que puede configurar un control desde la barra de herramientas.

Por ejemplo, puede seleccionar un control y, a continuación, mostrar u ocultarlo cambiando su propiedad **visible** .

![Establecer visibilidad](./media/add-configure-controls/set-visibility.png)

## <a name="configure-a-control-in-the-formula-bar"></a>Configuración de un control en la barra de fórmulas

En lugar de configurar un control directamente, desde la barra de herramientas o en la pestaña **propiedades** , puede configurar un control seleccionando una propiedad en la lista de propiedades y, a continuación, especificando un valor en la barra de fórmulas. Con este enfoque, puede buscar una propiedad por orden alfabético y especificar otros tipos de valores.

Por ejemplo, puede seleccionar una etiqueta y, a continuación, configurarla de estas maneras:

- Para moverla, seleccione **X** o **Y** en la lista de propiedades y, a continuación, especifique un número diferente en la barra de fórmulas.

    ![Establecer la propiedad X](./media/add-configure-controls/x-property.png)

- Cambie el tamaño seleccionando **alto** o **ancho** en la lista de propiedades y, a continuación, especificando un número diferente en la barra de fórmulas.

    ![Propiedad Set height](./media/add-configure-controls/height-property.png)

- Cambie su texto seleccionando **texto** en la lista de propiedades y, a continuación, especificando cualquier combinación de una cadena literal, una expresión o una fórmula en la barra de fórmulas.

    - Una cadena literal está entre comillas y aparece exactamente como se escribe. **"Hello, World"** es una cadena literal.

        ![Establecer la propiedad Text en una cadena literal](./media/add-configure-controls/literal-string.png)

    - Una expresión no incluye una función y a menudo se basa en una propiedad de otro control. **Screen1. Height** es una expresión que muestra el alto de **Screen1**.

        ![Establecer la propiedad Text en una expresión](./media/add-configure-controls/expression.png)

    - Una fórmula incluye una o más funciones. La función **Now** devuelve la fecha y hora actuales de la zona horaria local y la función de **texto** da formato a valores como fechas, horas y monedas.

        ![Establecer la propiedad Text en una fórmula](./media/add-configure-controls/formula.png)

        Las fórmulas suelen ser mucho más complejas que este ejemplo para que puedan actualizar los datos, ordenarlos, filtrarlos y realizar otras operaciones. Para obtener más información, vea la [referencia de fórmulas](formula-reference.md).

## <a name="next-steps"></a>Pasos siguientes

- Busque procedimientos paso a paso para configurar controles comunes como [pantallas](add-screen-context-variables.md), [listas](add-list-box-drop-down-list-radio-button.md), [galerías](add-gallery.md), [formularios](add-form.md)y [gráficos](use-line-pie-bar-chart.md).
- Busque información de referencia sobre cada tipo de control en la [referencia de control](reference-properties.md).
