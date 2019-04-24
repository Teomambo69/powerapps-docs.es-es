---
title: Personalizar una tarjeta en una aplicación de lienzo | Microsoft Docs
description: Cambie el control predeterminado que aparece en una tarjeta de detalles o edición de formulario en una aplicación de lienzo
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/18/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ddc1c677ed95caf10d8cd6e0e7e12e6aaf88a0f5
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61559871"
---
# <a name="customize-a-card-in-a-canvas-app"></a>Personalizar una tarjeta en una aplicación de lienzo

Realice una personalización básica (sin desbloquear una tarjeta), por ejemplo, cambiando su control. Realizar una personalización avanzada mediante el desbloqueo de la tarjeta y, por ejemplo, agregar un control que no está disponible para esa tarjeta de forma predeterminada.

Para obtener información general, consulte [Introducción a las tarjetas de datos](working-with-cards.md).

## <a name="prerequisites"></a>Requisitos previos

- Aprenda a [agregar y configurar controles](add-configure-controls.md).
- Puede revisar este tema para ver los conceptos generales, o bien puede seguir paso a paso si completa los procedimientos descritos en estos temas en primer lugar:

    1. [Generar una aplicación](data-platform-create-app.md).
    1. [Personalizar su galería](customize-layout-sharepoint.md).
    1. [Personalizar sus formularios](customize-forms-sharepoint.md).

## <a name="customize-a-locked-card"></a>Personalizar una tarjeta bloqueada

En este procedimiento, va a reemplazar un **[entrada de texto](controls/control-text-input.md)** controlar con un **[control deslizante] (controles, control-slider.md** control sin desbloquear la tarjeta.

1. En la aplicación que ha generado y personalizado, seleccione **EditForm1** en el panel de navegación izquierdo de la barra y, a continuación, seleccione **editar campos** en el **propiedades** ficha del panel derecho.

1. En la lista de campos, seleccione la flecha hacia abajo para **Number of Employees**y, a continuación, abra la lista bajo **tipo de Control**.

    > [!div class="mx-imgBorder"]
    > ![Lista desplegable de opciones para una tarjeta de número](./media/customize-card/card-selector.png)

1. Seleccione **editar control deslizante**.

    La pantalla refleja el cambio.

    > [!div class="mx-imgBorder"]
    > ![EditForm1 con el control deslizante](./media/customize-card/add-slider.png)

## <a name="unlock-and-customize-a-card"></a>Desbloquear y personalizar una tarjeta

En este procedimiento, desbloqueará una tarjeta y actualizar la **Max** propiedad de la **control deslizante** control que acaba de agregar.

1. En **EditForm1**, seleccione el **control deslizante** en controlar la **Number of Employees** tarjeta.

    > [!div class="mx-imgBorder"]
    > ![Seleccione el control deslizante](./media/customize-card/select-slider.png)

1. En el **avanzadas** ficha del panel derecho, seleccione el icono de candado para desbloquear la tarjeta.

    > [!div class="mx-imgBorder"]
    > ![Desbloqueo de tarjeta](./media/customize-card/lock-icon.png)

1. Establecer el **Max** propiedad de la **control deslizante** control a 10 000.

    > [!div class="mx-imgBorder"]
    > ![Max (propiedad) en la ficha Opciones avanzadas](./media/customize-card/max-property.png)

    El **control deslizante** control muestra un valor más preciso.

    > [!div class="mx-imgBorder"]
    > ![Intervalo del control deslizante: 0-10,000](./media/customize-card/final-slider.png)

## <a name="next-steps"></a>Pasos siguientes

Ahora que tiene un conocimiento básico de cómo generar una aplicación y personalizar una galería, un formulario y una tarjeta, puede [generar su propia aplicación desde cero](data-platform-create-app-scratch.md).