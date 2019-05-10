---
title: Agregar y configurar un control de aplicación de lienzo| Microsoft Docs
description: Instrucciones paso a paso para agregar y configurar controles de aplicación de lienzo directamente desde la barra de herramientas, en la pestaña Propiedades, o en la barra de fórmulas.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/25/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3311433b3950bcf48dc6c7b7969da501e542952c
ms.sourcegitcommit: c52c1869510a9a37d9f7b127e06f07583529588b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670901"
---
# <a name="add-and-configure-a-canvas-app-control-in-powerapps"></a>Agregar y configurar un control de aplicación de lienzo en PowerApps

Agregue diversos elementos de interfaz de usuario a su aplicación de lienzo y configure aspectos de su apariencia y comportamiento directamente desde la barra de herramientas, en la pestaña **Propiedades**, o en la barra de fórmulas. Estos elementos de interfaz de usuario se denominan controles y los aspectos que configura se denominan propiedades.

## <a name="prerequisites"></a>Requisitos previos

1. Si aún no tiene una licencia de PowerApps, [registrarse](../signup-for-powerapps.md)y, a continuación, [inicie sesión en](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
1. En **cree su propia aplicación**, mantenga el mouse sobre **desde cero una aplicación de lienzo**y, a continuación, seleccione **hacer que esta aplicación**.
1. Si se le pedirá que realice el Paseo introductorio, seleccione **siguiente** para familiarizarse con las áreas principales de la interfaz de PowerApps (o seleccione **Skip**).

    Siempre puede realizar el paseo más tarde, selecciona el icono de signo de interrogación situado cerca de la esquina superior derecha de la pantalla y, a continuación, seleccione **realice el Paseo introductorio**.

## <a name="add-and-select-a-control"></a>Agregar y seleccione un control

En el **insertar** , realice uno de estos pasos:

- Seleccione **etiqueta** o **botón** para agregar uno de esos tipos de controles.
- Seleccione una categoría de controles y, a continuación, seleccione el tipo de control que desea agregar.

Por ejemplo, seleccione **nueva pantalla**y, a continuación, seleccione **en blanco** para agregar una pantalla en blanco a la aplicación. (Las pantallas son un tipo de control que puede contener otros tipos de controles).

![Agregar pantalla](./media/add-configure-controls/add-screen.png)

La nueva pantalla se denomina **Screen2** y aparece en el panel de navegación izquierdo. Este panel muestra una lista jerárquica de los controles en la aplicación, por lo que puede encontrar fácilmente y seleccione cada control.

![Screen2 en la lista](./media/add-configure-controls/list-screen2.png)

Para demostrar cómo funciona esta lista, seleccione **etiqueta** en el **insertar** ficha. El nuevo control aparece bajo **Screen2** en la lista jerárquica.

![Screen2 en la lista](./media/add-configure-controls/add-label.png)

En la pantalla, un cuadro con seis identificadores alrededor de la etiqueta de forma predeterminada. Ese tipo de cuadro que rodea a cualquier control que está seleccionado. Si selecciona la pantalla haciendo clic o pulsando en ella (pero fuera de la etiqueta), el cuadro desaparece de la etiqueta. Para seleccionar la etiqueta de nuevo, puede hacer clic o pulse en él, o puede hacer clic o pulse en su nombre en la lista jerárquica de los controles.

> [!IMPORTANT]
> Siempre debe seleccionar un control antes de que pueda configurar.

## <a name="rename-a-control"></a>Cambiar el nombre de un control

En la lista jerárquica de los controles, mantenga el puntero sobre el control que desea cambiar el nombre, seleccione el botón de puntos suspensivos que aparece y, a continuación, seleccione **cambiar el nombre**. A continuación, puede escribir un nombre único y fácil de recordar para crear la aplicación sea más fácil.

![Cambiar el nombre del control](./media/add-configure-controls/rename-control.png)

## <a name="delete-a-control"></a>Eliminar un control

En la lista jerárquica de los controles, mantenga el puntero sobre el control que desea eliminar, seleccione el botón de puntos suspensivos que aparece y, a continuación, seleccione **eliminar**. Para eliminar un control que no sea una pantalla, puede también seleccionar el control en el lienzo y, a continuación, presione la tecla SUPR.

![Eliminar control](./media/add-configure-controls/delete-control.png)

## <a name="reorder-screens"></a>Cambiar el orden de las pantallas

En la lista jerárquica de los controles, mantenga el mouse sobre una pantalla que desea mover hacia arriba o hacia abajo, seleccione el botón de puntos suspensivos que aparece y, a continuación, seleccione **Subir** o **Bajar**.

![Cambiar el orden de pantalla](./media/add-configure-controls/reorder-screen.png)

> [!NOTE]
> Cuando se abre la aplicación, la pantalla en la parte superior de la lista jerárquica de los controles normalmente aparece en primer lugar. Pero puede especificar una pantalla diferente estableciendo el **[OnStart](controls/control-screen.md)** propiedad en una fórmula que incluya el **[Navigate](functions/function-navigate.md)** función.

## <a name="move-and-resize-a-control"></a>Mover y cambiar el tamaño de un control

Para mover un control, selecciónelo, mantenga el mouse sobre su centro para que aparezca la flecha de cuatro puntas y, a continuación, arrastre el control a una ubicación diferente.

![Mover control](./media/add-configure-controls/move-control.png)

Para cambiar el tamaño de un control, selecciónelo, mantenga el puntero sobre cualquiera de ellos en el cuadro de selección para que aparezca la flecha de dos puntas y, a continuación, arrastre el controlador.

![Mover control](./media/add-configure-controls/resize-control.png)

> [!NOTE]
> Como se describe más adelante en este tema, también puede mover y cambiar el tamaño de un control mediante la modificación de cualquier combinación de sus  **[X](controls/properties-size-location.md)**,  **[Y](controls/properties-size-location.md)**,  **[Alto](controls/properties-size-location.md)**, y **[ancho](controls/properties-size-location.md)** propiedades en la barra de fórmulas.

## <a name="change-the-text-of-a-label-or-a-button"></a>Cambiar el texto de una etiqueta o un botón

Seleccione una etiqueta o un botón, haga doble clic en el texto que aparece en el control y, a continuación, escriba el texto que desee.

![Cambio del texto](./media/add-configure-controls/change-text.png)

> [!NOTE]
> Como se describe más adelante en este tema, también puede cambiar este texto modificando su **[texto](controls/properties-core.md)** propiedad en la barra de fórmulas.

## <a name="configure-a-control-from-the-toolbar"></a>Configuración de un control desde la barra de herramientas

Al configurar un control desde la barra de herramientas, puede especificar una mayor variedad de opciones que si lo hace directamente.

Por ejemplo, puede seleccionar una etiqueta, seleccione el **inicio** pestaña y, a continuación, cambie la fuente del texto en la etiqueta.

![Cambiar fuente](./media/add-configure-controls/change-font.png)

## <a name="configure-a-control-from-the-properties-tab"></a>Configuración de un control mediante la pestaña Propiedades

Mediante el uso de la **propiedades** ficha, puede especificar una mayor variedad de opciones que si lo hace mediante la configuración de un control desde la barra de herramientas.

Por ejemplo, puede seleccionar un control y, a continuación, mostrar u ocultarlo cambiando su **Visible** propiedad.

![Visibilidad del conjunto](./media/add-configure-controls/set-visibility.png)

## <a name="configure-a-control-in-the-formula-bar"></a>Configuración de un control en la barra de fórmulas

En lugar de configurar un control directamente, desde la barra de herramientas o en el **propiedades** ficha, puede configurar un control, seleccione una propiedad en la lista de propiedades y, a continuación, especificar un valor en la barra de fórmulas. Con este enfoque, puede buscar una propiedad por orden alfabético y especificar otros tipos de valores.

Por ejemplo, puede seleccionar una etiqueta y, a continuación, la configuración de las siguientes maneras:

- Muévalo seleccionando **X** o **Y** en la lista de propiedades y, a continuación, especificar un número diferente en la barra de fórmulas.

    ![Propiedad establecer X](./media/add-configure-controls/x-property.png)

- Cambiar su tamaño seleccionando **alto** o **ancho** en la lista de propiedades y, a continuación, especificar un número diferente en la barra de fórmulas.

    ![Establezca la propiedad Height](./media/add-configure-controls/height-property.png)

- Cambie su texto seleccionando **texto** en la lista de propiedades y, a continuación, especificar cualquier combinación de una cadena literal, una expresión o una fórmula en la barra de fórmulas.

    - Una cadena literal está delimitada por comillas y aparece exactamente como se escribe. **"¡Hello, world"** es una cadena literal.

        ![Establezca la propiedad de texto en una cadena literal](./media/add-configure-controls/literal-string.png)

    - Una expresión no incluye una función y a menudo se basa en una propiedad de otro control. **Screen1.Height** es una expresión que se muestra el alto de **Screen1**.

        ![Establezca la propiedad de texto en una expresión](./media/add-configure-controls/expression.png)

    - Una fórmula incluye una o más funciones. El **ahora** función devuelve la fecha y hora actuales en la zona horaria local y el **texto** función da formato a valores como fechas, horas y moneda.

        ![Establezca la propiedad de texto en una fórmula](./media/add-configure-controls/formula.png)

        Las fórmulas son normalmente mucho más complejas que en este ejemplo, para que puede actualizar los datos, ordenarlo, filtrarlos y realizar otras operaciones. Para obtener más información, consulte el [referencia sobre fórmula](formula-reference.md).

## <a name="next-steps"></a>Pasos siguientes

- Buscar procedimientos paso a paso para configurar los controles comunes como [pantallas](add-screen-context-variables.md), [enumera](add-list-box-drop-down-list-radio-button.md), [galerías](add-gallery.md), [formularios](add-form.md)y [gráficos](use-line-pie-bar-chart.md).
- Buscar información de referencia acerca de cada tipo de control en el [controlar referencia](reference-properties.md).
