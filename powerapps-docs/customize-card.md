---
title: "Personalización de una tarjeta | Microsoft Docs"
description: "Realizar una personalización básica y avanzada en una tarjeta"
services: 
suite: powerapps
documentationcenter: 
author: skjerland
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/30/2016
ms.author: sharik
ms.openlocfilehash: 9fdde89b254e491f2dc333261649df7fd156f2c2
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="customize-a-card-in-microsoft-powerapps"></a>Personalizar una tarjeta en Microsoft PowerApps
Realice una personalización básica (sin desbloquear una tarjeta), por ejemplo, cambiando su control. Realizar una personalización avanzada mediante el desbloqueo de la tarjeta y, por ejemplo, agregar un control que no está disponible para esa tarjeta de forma predeterminada.

Para obtener información general, consulte [Introducción a las tarjetas de datos](working-with-cards.md).

## <a name="prerequisites"></a>Requisitos previos

* Aprenda a [agregar y configurar controles](add-configure-controls.md).
* Puede revisar este tema limitándose a los conceptos generales. Para seguirlo exactamente (paso a paso), lleve a cabo los pasos descritos en estos temas:

  1. [Cree una aplicación a partir de SharePoint](app-from-sharepoint.md).
  2. [Personalice el diseño](customize-layout-sharepoint.md).
  3. [Personalice el formulario](customize-forms-sharepoint.md).

## <a name="customize-a-locked-card"></a>Personalizar una tarjeta bloqueada
En este procedimiento, va a reemplazar un control **[Alternar](controls/control-toggle.md)** por un control **[Botón de selección](controls/control-radio.md)** sin desbloquear la tarjeta.

1. En **EditarPantalla1**, pulse o haga clic en la tarjeta **Pagado** para seleccionarla.

    ![](./media/customize-card/select-paid-card.png)

2. En el panel derecho, pulse o haga clic en el selector de la tarjeta **Pagado** y pulse o haga clic en **Editar opciones**.

    ![](./media/customize-card/select-toggle-paid.png)

    La pantalla refleja el cambio.

    ![](./media/customize-card/display-radio.png)
   
    Para información acerca de qué tipos de columnas de SharePoint admiten los distintos tipos de tarjetas, consulte [Problemas conocidos](connections/connection-sharepoint-online.md#known-issues).

## <a name="unlock-and-customize-a-card"></a>Desbloquear y personalizar una tarjeta
En este procedimiento, desbloqueará una tarjeta y reemplazará un control **[Entrada de texto](controls/control-text-input.md)** por un control **[Control deslizante](controls/control-slider.md)**.

1. En **EditarPantalla1**, pulse o haga clic en la tarjeta **Cantidad**.

2. En el panel derecho, pulse o haga clic en el icono de puntos suspensivos de esa tarjeta y pulse o haga clic en **Opciones avanzadas**.

    ![Abrir Opciones avanzadas](./media/customize-card/advanced-options.png)
3. En la parte superior del panel derecho, haga clic o pulse en el icono de candado para desbloquear la tarjeta.

    ![Desbloquear una tarjeta](./media/customize-card/unlock-card.png)
4. En la tarjeta, elimine el control **Entrada de texto**, agregue un control **Control deslizante** y asígnele el nombre **QtySlider**.

5. En el panel derecho, establezca la propiedad **Actualizar** de la tarjeta **Cantidad** en esta fórmula:<br>
   **QtySlider.Value**

   > [!NOTE]
> Si la propiedad **Actualizar** no aparece, haga clic o pulse **Más opciones** en la parte inferior de la sección **Datos**.


6. Pulse o haga clic en el control deslizante para seleccionarlo y, después, abra la lista de controles en la parte superior del panel derecho.

7. Pulse o haga clic en **MensajeError4** y establezca su propiedad **Altura** en esta fórmula:<br>
   **QtySlider.Y + QtySlider.Height**
