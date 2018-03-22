---
title: 'Control Temporizador: referencia | Microsoft Docs'
description: "Información sobre el control Temporizador, con propiedades y ejemplos"
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
ms.openlocfilehash: 008c992ad3452c1844064335a51593c222fb1ac1
ms.sourcegitcommit: 68eee592c351688e5d0bd458f33a70be507fa53f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2018
---
# <a name="timer-control-in-powerapps"></a>Control Temporizador en PowerApps
Control que determina la forma en que la aplicación responde una vez transcurrido un tiempo determinado.

## <a name="description"></a>Descripción
Los temporizadores, por ejemplo, determinan el tiempo que un control va a aparecer o cambian otras propiedades de un control una vez transcurrido un tiempo determinado.

Para que el temporizador se ejecute en el diseñador, tenga en cuenta que necesita obtener una vista previa de la aplicación.  Esto permite al usuario configurar el temporizador en el diseñador sin restricciones de tiempo.

## <a name="key-properties"></a>Propiedades principales
**Duración**: el tiempo durante el que se ejecuta un temporizador, en milisegundos.  No hay valor máximo.

**AlFinalizarTemporizador**: respuesta de la aplicación al finalizar la ejecución del temporizador.

**Repetir**: indica si un temporizador se reinicia automáticamente cuando finaliza la ejecución.

## <a name="additional-properties"></a>Propiedades adicionales
**[Align](properties-text.md)**: la ubicación del texto respecto al centro horizontal de su control.

**PausarAutomáticamente**: indica si un clip de audio o vídeo se detiene automáticamente si el usuario se desplaza a otra pantalla.

**IniciarAutomáticamente**: indica si un control de audio o vídeo empieza a reproducir automáticamente un clip cuando el usuario navega a la pantalla que contiene ese control.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[Color](properties-color-border.md)**: el color del texto en un control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[DisabledColor](properties-color-border.md)**: el color del texto en un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[DisabledFill](properties-color-border.md)**: el color de fondo de un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[Font](properties-text.md)**: el nombre de la familia de fuentes en la que aparece el texto.

**[FontWeight](properties-text.md)**: el peso del texto en un control: **Bold**, **Semibold**, **Normal** o **Lighter**.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**[HoverColor](properties-color-border.md)**: el color del texto de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[HoverFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[Italic](properties-text.md)**: indica si el texto de un control está en cursiva.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**AlIniciarTemporizador**: respuesta de la aplicación cuando se inicia un temporizador.

**[PressedBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario toca o hace clic en ese control.

**[PressedColor](properties-color-border.md)**: el color de texto de un control cuando el usuario toca o hace clic en ese control.

**[PressedFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario toca o hace clic en ese control.

**[Reset](properties-core.md)**: indica si un control vuelve a su valor predeterminado.

**[Size](properties-text.md)**: el tamaño de la fuente del texto que aparece en un control.

**Inicio**: indica si se reproduce un clip de audio o vídeo.

**[Strikethrough](properties-text.md)**: indica si aparece una línea sobre el texto de un control.

**[Text](properties-core.md)**: texto que aparece en un control o que el usuario escribe en un control.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Underline](properties-text.md)**: indica si aparece una línea debajo del texto de un control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**Refresh**( *DataSource* )](../functions/function-refresh.md)

## <a name="examples"></a>Ejemplos
### <a name="show-a-countdown"></a>Mostrar una cuenta atrás
1. Agregue un temporizador y asígnele el nombre **Countdown**.

    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
2. Establezca la propiedad **Duration** en **10000** y sus propiedades **Repetir** e **IniciarAutomáticamente** en **true**.
3. (opcional) Configure la propiedad  **[Altura](properties-size-location.md)**  en **160**, su propiedad  **[Altura](properties-size-location.md)**  en **600** y su propiedad  **[Size](properties-text.md)**  en **60** para facilitar la lectura del temporizador.
4. Agregue una etiqueta y establezca su propiedad **[Text](properties-core.md)** en esta fórmula:
   <br>**"Number of seconds remaining: " & RoundUp(10-Countdown.Value/1000, 0)**

    ¿Desea más información sobre la función **[RedondearMas](../functions/function-round.md)** u [otras funciones](../formula-reference.md)?

    La etiqueta muestra cuántos segundos quedan para que se reinicie el temporizador.
5. (opcional) Establezca la propiedad **[Visible](properties-core.md)** del temporizador en **false**.

### <a name="animate-a-control"></a>Animar un control
1. Agregue un temporizador y asígnele el nombre **FadeIn**.

    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
2. Establezca la propiedad **Duration** en **5000** y sus propiedades **Repetir** e **IniciarAutomáticamente** en **true**.
3. (opcional) Configure la propiedad  **[Altura](properties-size-location.md)**  en **160**, su propiedad  **[Altura](properties-size-location.md)**  en **600** y su propiedad  **[Size](properties-text.md)**  en **60** para facilitar la lectura del temporizador.
4. Agregue una etiqueta y establezca su propiedad **[Texto](properties-core.md)** para que muestre el mensaje **Welcome!** y establezca su propiedad **[Color](properties-color-border.md)** con esta fórmula:
   <br>**ColorFade(Color.BlueViolet, FadeIn.Value/5000)**

    ¿Desea más información sobre la función **[ColorFade](../functions/function-colors.md)** u [otras funciones](../formula-reference.md)?

    El texto de la etiqueta se difumina a blanco, recupera su intensidad y el proceso se repite.
5. (opcional) Establezca la propiedad **[Visible](properties-core.md)** del temporizador en **false**.
