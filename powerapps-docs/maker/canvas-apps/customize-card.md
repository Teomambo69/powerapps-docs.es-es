---
title: Personalización de una tarjeta en una aplicación de lienzo | Microsoft Docs
description: Cambiar el control predeterminado que aparece en una tarjeta en un formulario de detalles o de edición en una aplicación de lienzo
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/18/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5bcf1515f72bdce0872f91c64b5ac4fe5028ee2c
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985916"
---
# <a name="customize-a-card-in-a-canvas-app"></a>Personalización de una tarjeta en una aplicación de lienzo

Realice una personalización básica (sin desbloquear una tarjeta), por ejemplo, cambiando su control. Realizar una personalización avanzada mediante el desbloqueo de la tarjeta y, por ejemplo, agregar un control que no está disponible para esa tarjeta de forma predeterminada.

Para obtener información general, consulte [Introducción a las tarjetas de datos](working-with-cards.md).

## <a name="prerequisites"></a>Requisitos previos

- Aprenda a [agregar y configurar controles](add-configure-controls.md).
- Puede revisar este tema solo para ver los conceptos generales, o bien puede seguirlo paso a paso si primero completa los procedimientos de estos temas:

    1. [Generar una aplicación](data-platform-create-app.md).
    1. [Personalizar su galería](customize-layout-sharepoint.md).
    1. [Personalizar sus formularios](customize-forms-sharepoint.md).

## <a name="customize-a-locked-card"></a>Personalizar una tarjeta bloqueada

En este procedimiento, reemplazará un control **[de entrada de texto](controls/control-text-input.md)** con un control **[Slider] (Controls/control-Slider. MD** sin desbloquear la tarjeta.

1. En la aplicación que ha generado y personalizado, seleccione **EditForm1** en la barra de navegación izquierda y, a continuación, seleccione **Editar campos** en la pestaña **propiedades** del panel derecho.

1. En la lista de campos, seleccione la flecha hacia abajo para **número de empleados**y, a continuación, abra la lista en **tipo de control**.

    > [!div class="mx-imgBorder"]
    > ![Drop: lista de opciones de una tarjeta numérica @ no__t-1

1. Seleccione **Editar control deslizante**.

    La pantalla refleja el cambio.

    > [!div class="mx-imgBorder"]
    > ![EditForm1 con el control deslizante @ no__t-1

## <a name="unlock-and-customize-a-card"></a>Desbloquear y personalizar una tarjeta

En este procedimiento, desbloqueará una tarjeta y actualizará la propiedad **Max** del control **deslizante** que acaba de agregar.

1. En **EditForm1**, seleccione el control **deslizante** en la tarjeta **número de empleados** .

    > [!div class="mx-imgBorder"]
    > ![Select el control deslizante @ no__t-1

1. En la pestaña **Opciones avanzadas** del panel derecho, seleccione el icono de candado para desbloquear la tarjeta.

    > [!div class="mx-imgBorder"]
    > @no__t-tarjeta 0Unlock @ no__t-1

1. Establezca la propiedad **Max** del control **deslizante** en 10.000.

    > [!div class="mx-imgBorder"]
    > @no__t propiedad 0Max en la pestaña Advanced @ no__t-1

    El control **deslizante** muestra un valor más preciso.

    > [!div class="mx-imgBorder"]
    > intervalo de @no__t 0Slider: 0-10000 @ no__t-0

## <a name="next-steps"></a>Pasos siguientes

Ahora que tiene un conocimiento básico de cómo generar una aplicación y personalizar una galería, un formulario y una tarjeta, puede [generar su propia aplicación desde cero](data-platform-create-app-scratch.md).