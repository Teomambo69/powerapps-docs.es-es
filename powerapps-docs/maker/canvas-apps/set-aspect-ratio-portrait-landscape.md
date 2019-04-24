---
title: Cambio del tamaño y la orientación de la pantalla de una aplicación de lienzo | Microsoft Docs
description: Instrucciones paso a paso para cambiar configuraciones tales como el tamaño y la orientación de la pantalla de una aplicación de lienzo en PowerApps
author: evchaki
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2018
ms.author: evchaki
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c4d9f648a4519ef30887d8d0739d7dc3d940555b
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61536067"
---
# <a name="change-screen-size-and-orientation-of-a-canvas-app-in-powerapps"></a>Cambio del tamaño y la orientación de la pantalla de una aplicación de lienzo en PowerApps
Personalice una aplicación de lienzo cambiando el tamaño y la orientación de la pantalla.

## <a name="prerequisites"></a>Requisitos previos

Creación de una aplicación o abra uno para su edición y, a continuación, seleccione **configuración de la aplicación** en el **archivo** menú.

## <a name="change-screen-size-and-orientation"></a>Cambiar el tamaño y la orientación de la pantalla
1. En **Configuración de aplicación**, seleccione **Screen size + orientation** (Tamaño y orientación de pantalla).

    ![Opción para cambiar el tamaño y la orientación de la pantalla de una aplicación](./media/set-aspect-ratio-portrait-landscape/size-orientation.png)

1. En el **orientación** lista, seleccione **vertical** o **horizontal**.

1. (Solo aplicaciones de Tablet PC) En **proporción**, realice uno de estos pasos:

    - Seleccione la relación que coincida con el dispositivo de destino para esta aplicación.
    - Seleccione **personalizado** para establecer su propio tamaño y, a continuación, especifique un ancho entre 50 3840 y un alto entre 50 2160.

    ![Cambiar la relación de aspecto de una aplicación de tableta](./media/set-aspect-ratio-portrait-landscape/aspect-tablet.png)
    
1. En **escala para ajustarse a**, especifique **en** o **desactivar**.

    Esta opción está activada de forma predeterminada para que las pantallas de la aplicación de tamaño para ajustarse al espacio disponible en el dispositivo. Si esta opción está activada, la aplicación **ancho** coincidencias de propiedad su **DesignWidth**y la aplicación **alto** coincide con su **DesignHeight**.

    Si desactiva esta opción, la aplicación se ajusta a la relación de aspecto del dispositivo en el que se está ejecutando y se ocupa de todo el espacio disponible. No se escala la aplicación y, como resultado, las pantallas pueden mostrar más información.

    Cuando esta opción está desactivada, **Bloquear relación de aspecto** automáticamente está desactivada y deshabilitada. Además, el **ancho** se establece la propiedad de todas las pantallas en `Max(App.Width, App.DesignWidth)`y sus **alto** propiedad está establecida en `Max(App.Height, App.DesignHeight)` para que realizan el seguimiento de las dimensiones de la ventana en la que se ejecuta la aplicación. Con este cambio, se pueden crear aplicaciones que responden a diferentes dispositivos y las dimensiones de la ventana. Más información: [Crear un diseño con capacidad de respuesta](create-responsive-layout.md)

1. En **Bloquear relación de aspecto**, especifique **Activar** o **Desactivar**.

    Si esta opción está activada, la aplicación conserva la relación de aspecto que especificó en los pasos 2 y 3, con independencia del dispositivo y la orientación de pantalla. Por ejemplo, una aplicación de teléfono que se está ejecutando en un explorador web conserva la relación para un teléfono, que muestra una barra oscura en cada lado en lugar de rellenar la ventana.

    Si esta opción está desactivada, la aplicación se ajusta a la relación de aspecto del dispositivo en el que se está ejecutando (y distorsión de la interfaz de usuario si es necesario).

1. En **Lock orientation** (Bloquear orientación), especifique **Activar** o **Desactivar**.

    Si se bloquea la orientación de la aplicación, la aplicación conserva la orientación que especifique. Si la aplicación se ejecuta en un dispositivo para que la pantalla está en una orientación diferente, la aplicación de muestra de forma incorrecta y puede mostrar resultados no deseados. Si desbloquea la orientación de la aplicación, ajusta a la orientación de pantalla del dispositivo en el que se está ejecutando.

    También puede modificar la orientación de la aplicación habilitando **aplicación habilitar experiencia del usuario de incrustación** en **configuración avanzada**. Esta característica superior izquierda alinea a la aplicación cuando se inserta y cambia el color de fondo del lienzo de hospedaje en blanco.

1. Seleccione **Aplicar** para guardar los cambios.

## <a name="next-step"></a>Paso siguiente
En el menú **Archivo**, seleccione **Guardar** para volver a publicar la aplicación con la nueva configuración.