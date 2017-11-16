---
title: "Controles Audio y Vídeo: referencia | Microsoft Docs"
description: "Información sobre los controles Audio y Vídeo, con propiedades y ejemplos"
services: 
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: b3eafd9f37537a083212e9ecbb92c6928ae0f773
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="audio-and-video-controls-in-powerapps"></a>Controles Audio y Vídeo en PowerApps
Un control que reproduce un archivo de audio, un archivo de vídeo o un vídeo en YouTube.

## <a name="description"></a>Descripción
Un control **Audio** reproduce una secuencia de sonido de un archivo, una grabación de un control **[Micrófono](control-microphone.md)** o el audio de una pista de audio de un archivo de vídeo. Un control **Vídeo** reproduce una secuencia de vídeo de un archivo o de YouTube si especifica una dirección URL.

## <a name="key-properties"></a>Propiedades principales
**Bucle**: indica si una secuencia de audio o vídeo empieza de nuevo automáticamente en cuanto termina de reproducirse.

**Multimedia**: un identificador de la secuencia que reproduce un control de audio o de vídeo.

**MostrarControles**: indica si se muestra un reproductor de audio o vídeo, por ejemplo, un botón de reproducción y un control deslizante de volumen, y un control de entrada manuscrita muestra, por ejemplo, iconos para dibujar, borrar y borrar todo.

## <a name="additional-properties"></a>Propiedades adicionales
**PausarAutomáticamente**: indica si un clip de audio o vídeo se detiene automáticamente si el usuario se desplaza a otra pantalla.

**IniciarAutomáticamente**: indica si un control de audio o vídeo empieza a reproducir automáticamente un clip cuando el usuario navega a la pantalla que contiene ese control.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[Imagen](properties-visual.md)**: el nombre de la imagen que aparece en un control de imagen, audio o micrófono.

**[PosiciónDeLaImagen](properties-visual.md)**: posición (**Rellenar**, **Ajustar**, **Estirar**, **Icono** o **Centrar**) de una imagen en una pantalla o un control, si no tiene el mismo tamaño que la imagen.

**AlFinalizar**: indica cómo una aplicación responde cuando finaliza la reproducción de una secuencia de audio o de vídeo.

**AlPausar**: indica cómo responde una aplicación cuando el usuario pausa la secuencia que está reproduciendo un control de audio o de vídeo.

**AlIniciar**: indica cómo la aplicación responde cuando el usuario comienza a grabar con un control de micrófono.

**Paused**: *true* si un control de reproducción multimedia está actualmente en pausa, de lo contrario *false*.

**[Reset](properties-core.md)**: indica si un control vuelve a su valor predeterminado.

**Inicio**: indica si se reproduce un clip de audio o vídeo.

**HoraDeInicio**: la hora después del inicio de una secuencia de audio o de vídeo cuando la secuencia empieza a reproducirse.

**Time**: posición actual del control multimedia.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**First**( *TableName* )](../functions/function-first-last.md)

## <a name="examples"></a>Ejemplos
### <a name="play-an-audio-or-video-file"></a>Reproducir un archivo de audio o de vídeo
1. En el menú **Archivo**, pulse o haga clic en **Multimedia**, pulse o haga clic en **Vídeos** o **Audio** y, luego, pulse o haga clic en **Examinar**.
2. Busque el archivo que desea usar, pulse o haga clic en él y, luego, pulse o haga clic en **Abrir**.
3. Presione Esc para volver al área de trabajo predeterminada, agregue un control **Audio** o **Vídeo** y establezca su propiedad **Multimedia** en el archivo que ha agregado.
   
    ¿No sabe cómo [agregar y configurar un control](../add-configure-controls.md)?
4. Presione F5 y, a continuación, reproduzca la secuencia haciendo clic o pulsando en el botón de reproducción del control que ha agregado.
   
    **Sugerencia:** el botón de reproducción del control **Vídeo** aparece cuando mantiene el puntero sobre el control.
5. Presione Esc para volver al área de trabajo predeterminada.

### <a name="play-a-youtube-video"></a>Reproducir un vídeo de YouTube
1. Agregue un control **Vídeo** y establezca su propiedad **Multimedia** en la dirección URL, incluida entre comillas, de un vídeo de YouTube.
2. Presione F5 y, a continuación, reproduzca la secuencia haciendo clic o pulsando en el botón de reproducción del control **Vídeo**.
3. Presione Esc para volver al área de trabajo predeterminada.

