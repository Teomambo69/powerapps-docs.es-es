---
title: Cambio del tamaño y la orientación de la pantalla de una aplicación de lienzo | Microsoft Docs
description: Instrucciones paso a paso para cambiar configuraciones tales como el tamaño y la orientación de la pantalla de una aplicación de lienzo en PowerApps
author: evchaki
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2018
ms.author: evchaki
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1d3bd48f658e31f795ca3489fa1973c48da94a22
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71995634"
---
# <a name="change-screen-size-and-orientation-of-a-canvas-app-in-powerapps"></a>Cambio del tamaño y la orientación de la pantalla de una aplicación de lienzo en PowerApps
Personalice una aplicación de lienzo cambiando el tamaño y la orientación de la pantalla.

## <a name="prerequisites"></a>Requisitos previos

Cree una aplicación o abra una para editarla y, a continuación, seleccione Configuración de la **aplicación** en el menú **archivo** .

## <a name="change-screen-size-and-orientation"></a>Cambiar el tamaño y la orientación de la pantalla
1. En **Configuración de aplicación**, seleccione **Screen size + orientation** (Tamaño y orientación de pantalla).

    ![Opción para cambiar el tamaño y la orientación de la pantalla de una aplicación](./media/set-aspect-ratio-portrait-landscape/size-orientation.png)

1. En la lista **orientación** , seleccione **vertical** u **horizontal**.

1. (Solo aplicaciones de tableta) En **relación de aspecto**, realice cualquiera de estos pasos:

    - Seleccione la proporción que coincida con el dispositivo de destino para esta aplicación.
    - Seleccione **personalizado** para establecer su propio tamaño y, a continuación, especifique un ancho entre 50-3840 y un alto entre 50-2160.

    ![Cambiar la relación de aspecto de una aplicación de tableta](./media/set-aspect-ratio-portrait-landscape/aspect-tablet.png)
    
1. En **escalar para ajustar**, especifique **activado** o **desactivado**.

    Esta opción está activada de forma predeterminada para que las pantallas de la aplicación cambien de tamaño para ajustarse al espacio disponible en el dispositivo. Cuando esta opción está activada, la propiedad **ancho** de la aplicación coincide con su **DesignWidth**y el **alto** de la aplicación coincide con su **DesignHeight**.

    Si desactiva esta configuración, la aplicación se ajusta a la relación de aspecto del dispositivo en el que se ejecuta y ocupa todo el espacio disponible. La aplicación no escala y, como resultado, las pantallas pueden mostrar más información.

    Cuando esta opción está desactivada, la **relación de aspecto de bloqueo** se desactiva y deshabilita automáticamente. Además, la propiedad **ancho** de todas las pantallas está establecida en `Max(App.Width, App.DesignWidth)` y su propiedad **alto** está establecida en `Max(App.Height, App.DesignHeight)` para que realice el seguimiento de las dimensiones de la ventana en la que se ejecuta la aplicación. Con este cambio, puede crear aplicaciones que respondan a diferentes dispositivos y dimensiones de la ventana. Más información: [Crear diseño con capacidad de respuesta](create-responsive-layout.md)

1. En **Bloquear relación de aspecto**, especifique **Activar** o **Desactivar**.

    Si esta opción está activada, la aplicación conserva la orientación de pantalla y la relación de aspecto que especificó en los pasos 2 y 3, independientemente del dispositivo. Por ejemplo, una aplicación de teléfono que se ejecuta en un explorador Web conserva la proporción de un teléfono, lo que muestra una barra oscura en cada lado en lugar de rellenar la ventana.

    Si esta opción está desactivada, la aplicación se ajusta a la relación de aspecto del dispositivo en el que se ejecuta (y distorsiona la interfaz de usuario si es necesario).

1. En **Lock orientation** (Bloquear orientación), especifique **Activar** o **Desactivar**.

    Si bloquea la orientación de la aplicación, la aplicación conserva la orientación que especifique. Si la aplicación se ejecuta en un dispositivo para el que la pantalla tiene una orientación diferente, la aplicación se muestra incorrectamente y puede mostrar resultados no deseados. Si desbloquea la orientación de la aplicación, se ajusta a la orientación de la pantalla del dispositivo en el que se ejecuta.

    También puede modificar la orientación de la aplicación habilitando **Habilitar la experiencia de usuario de incrustación de aplicaciones** en **Configuración avanzada**. Esta característica, en la parte superior izquierda, alinea la aplicación cuando se inserta y cambia el color de fondo del lienzo de hospedaje a blanco.

1. Seleccione **Aplicar** para guardar los cambios.

## <a name="next-step"></a>Paso siguiente
En el menú **Archivo**, seleccione **Guardar** para volver a publicar la aplicación con la nueva configuración.