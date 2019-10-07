---
title: Función Select | Microsoft Docs
description: Información de referencia para la función Select en PowerApps, incluida la sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/11/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ed31bd165eb2289819800b6f2e01121c2681ae9e
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984075"
---
# <a name="select-function-in-powerapps"></a>Función Select en PowerApps
Simula una acción de selección en un control, lo que provoca la evaluación de la fórmula **OnSelect**.

## <a name="description"></a>Descripción
La función **Select** simula una acción de selección en un control como si el usuario hubiera hecho clic en el control o lo hubiera pulsado. Como resultado, la fórmula **OnSelect** se evalúa en el control de destino.

Use **Select** para propagar una acción seleccionada a un control primario. Este tipo de propagación es el comportamiento predeterminado en, por ejemplo, las galerías. De forma predeterminada, la propiedad **OnSelect** de cualquier control en un control **[Galería](../controls/control-gallery.md)** se establece en **Select (primario)** . De este modo, puede establecer el valor de la propiedad **OnSelect** del propio control de la galería y que la fórmula se evaluará independientemente de dónde un usuario podría haga clic o pulsar en la galería.

Si desea que uno o varios controles de la galería realizaran diferentes acciones de la propia galería, establezca la propiedad **OnSelect** para esos controles en un valor distinto del valor predeterminado. Puede dejar los valores predeterminados para las propiedades **OnSelect** de la mayoría de los controles de la galería si desea que realicen la misma acción que la propia galería.

**Select** pone en cola la propiedad **OnSelect** de destino para su posterior procesamiento, que puede ocurrir una vez finalizada la evaluación de la fórmula actual. **Select** no provoca que la propiedad **OnSelect** de destino se evalúe inmediatamente; **Select** tampoco espera a que **OnSelect** termine de evaluarse.

**Select** no puede cruzar los límites de los controles de contenedor, como una galería o un formulario. Controles dentro de un control de contenedor solo pueden ser el sujeto de una función **Select** en las fórmulas que están dentro del mismo control de contenedor. No se puede utilizar **Select** entre pantallas.

Solo puede usar **Select** con controles que tienen una propiedad **OnSelect**.

Se pueden usar **Select** en [fórmulas de comportamiento](../working-with-formulas-in-depth.md).

Un control no puede usar **Select** directa o indirectamente a través de otros controles.

## <a name="syntax"></a>Sintaxis
**Select**( *Control* )

* *Control* (se requiere).  El control para seleccionar en nombre del usuario.

## <a name="examples"></a>Ejemplos

#### <a name="basic-usage"></a>Uso básico

1. Agregue un control **[Botón](../controls/control-button.md)** y, si tiene otro nombre, cámbielo a **Botón1**.

1. Establezca la propiedad **OnSelect** de **Botón1** en esta fórmula:

    **Notify( "Hola mundo" )**

1. En la misma pestaña, agregue un segundo control **Botón** y establezca su propiedad **OnSelect** en esta fórmula:

    **Select( Botón1 )**

1. Mientras mantiene presionada la tecla Alt, seleccione el segundo botón.

    Aparecerá una notificación en la parte superior de la aplicación. La propiedad **OnSelect** de **Button1** generó esta notificación.

    ![Animación que muestra la configuración de la propiedad OnSelect para los dos botones y la notificación cuando se hace clic en el segundo botón](media/function-select/basic-select.gif)

#### <a name="gallery-control"></a>Control Galería

1. Agregue un control **[Galería](../controls/control-gallery.md)** vertical que contiene otros controles.

    ![Seleccione una galería vertical que contiene controles](media/function-select/select-gallery.png)

2. Seleccione la propiedad **OnSelect** de la galería en esta fórmula:
 
    **Notify( "Galería seleccionada" )**

3. Mientras mantiene presionada la tecla Alt, haga clic en el fondo de la galería o en cualquier control en la galería; también puede pulsar dichos elementos.

    Todas las acciones se mostrarán la notificación **Galería seleccionada** en la parte superior de la aplicación.

    Use propiedad **OnSelect** de la galería para especificar la acción predeterminada que se realizará cuando el usuario haga clic en un elemento de dicha galería o pulse ese elemento.

5. Establezca la propiedad **OnSelect** del control de imagen en esta fórmula:

    **Notify( "Imagen seleccionada", operación correcta)**

6. Mientras mantiene presionada la tecla Alt, haga clic en los distintos elementos de la galería o púlselos.

    Al hacer clic en cualquier control en la galería, excepto en la imagen o pulsarlo, **Galería seleccionada** aparecerá como antes. Al hacer clic en la imagen o pulsarla, aparecerá **Imagen seleccionada**.
 
    Use controles individuales en la galería para realizar acciones que difieren de la acción predeterminada de la galería.

    ![Animación que se muestra el valor predeterminado de la propiedad OnSelect para un control de la galería, así como un control que realiza una acción diferente](media/function-select/gallery-select.gif)
