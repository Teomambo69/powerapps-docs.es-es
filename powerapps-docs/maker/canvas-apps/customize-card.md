---
title: Personalización de una tarjeta | Microsoft Docs
description: Cambie el control predeterminado que aparece en una tarjeta de un formulario de detalles o edición en PowerApps
documentationcenter: ''
author: AFTOwen
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 03/18/2018
ms.author: anneta
ms.openlocfilehash: aa9d5785f1c005da7c22c63bd94cb41e1a643ad3
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="customize-a-card-in-powerapps"></a>Personalización de una tarjeta en PowerApps
Realice una personalización básica (sin desbloquear una tarjeta), por ejemplo, cambiando su control. Realizar una personalización avanzada mediante el desbloqueo de la tarjeta y, por ejemplo, agregar un control que no está disponible para esa tarjeta de forma predeterminada.

Para obtener información general, consulte [Introducción a las tarjetas de datos](working-with-cards.md).

## <a name="prerequisites"></a>Requisitos previos

* Aprenda a [agregar y configurar controles](add-configure-controls.md).
* Puede consultar este tema para ver solo los conceptos generales, o bien puede seguirlo paso a paso si completa los procedimientos de estos temas:

  1. [Generar una aplicación](data-platform-create-app.md).
  2. [Personalizar su galería](customize-layout-sharepoint.md).
  3. [Personalizar sus formularios](customize-forms-sharepoint.md).

## <a name="customize-a-locked-card"></a>Personalizar una tarjeta bloqueada
En este procedimiento, se va a reemplazar un control **[Entrada de texto](controls/control-text-input.md)** por un **[Control deslizante](controls/control-slider.md)** sin desbloquear la tarjeta.

1. Inicie sesión en [PowerApps](http://web.powerapps.com).

    ![Página principal de PowerApps](./media/customize-card/sign-in.png)

1. Abra la aplicación que ha generado y personalizado, seleccione **EditForm1** y, después, abra el panel **Datos** haciendo clic en **Cuentas** en el panel de la derecha.

1. En la lista de campos, haga clic en la flecha hacia abajo de **Número de empleados** para mostrar una lista de opciones y, después, haga clic en **Editar control deslizante**.

    ![Lista desplegable de opciones para una tarjeta de número](./media/customize-card/card-selector.png)

    La pantalla refleja el cambio.

    ![EditForm1 con el control deslizante](./media/customize-card/add-slider.png)

## <a name="unlock-and-customize-a-card"></a>Desbloquear y personalizar una tarjeta
En este procedimiento, se desbloqueará una tarjeta y se reemplazará un control **[Alternar](controls/control-toggle.md)** por un control **[Casilla](controls/control-check-box.md)**.

1. En **EditForm1**, muestre el campo **Enviar materiales de marketing**.

    ![Mostrar el campo Enviar materiales de marketing](./media/customize-card/show-field.png)

2. Con esa tarjeta seleccionada, pulse o haga clic en **Opciones avanzadas** junto a la parte superior del panel derecho y, después, pulse o haga clic en el icono de candado para desbloquear la tarjeta.

    ![Mostrar el campo Enviar materiales de marketing](./media/customize-card/unlock-card.png)

1. En la tarjeta, elimine el control **Alternar**, agregue un control **Casilla** y asígnele el nombre **chkMktg**.

    ![Reemplazar Alternar con Casilla](./media/customize-card/add-checkbox.png)

1. Seleccione la tarjeta que acaba de actualizar.

    ![Seleccionar tarjeta](./media/customize-card/select-card.png)

1. En el panel de la derecha, asegúrese de que se sigue mostrando la pestaña **Opciones avanzadas** y, después, pulse o haga clic en **Más opciones**.

    ![Botón Más opciones](./media/customize-card/more-options.png)

1. Cambie el valor de la propiedad **Update** de la tarjeta por esta expresión:
<br>`chkMktg.Value`

1. Cambie el valor de la propiedad **Y** del mensaje de error de esa tarjeta por esta expresión:<br>
`chkMktg.Y + chkMktg.Height`

    ![Seleccionar el mensaje de error para la nueva tarjeta](./media/customize-card/select-error.png)

1. Cambie el valor de la propiedad **Text** de **chkMktg** a **Sí**.

    La pantalla refleja los cambios y se resuelven los errores.

    ![Pantalla final con los errores resueltos](./media/customize-card/final-screen.png)

## <a name="next-steps"></a>Pasos siguientes
Ahora que tiene un conocimiento básico de cómo generar una aplicación y personalizar una galería, un formulario y una tarjeta, puede [generar su propia aplicación desde cero](data-platform-create-app-scratch.md).
