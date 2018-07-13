---
title: 'Controles Audio y Vídeo: referencia | Microsoft Docs'
description: Información sobre los controles Audio y Vídeo, con propiedades y ejemplos
author: fikaradz
ms.service: powerapps
ms.topic: reference
ms.component: canvas
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: 43328f363926f20d91b49ba422c3bfdae30abbf6
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37898769"
---
# <a name="audio-and-video-controls-in-powerapps"></a>Controles Audio y Vídeo en PowerApps
Un control que reproduce un archivo de audio, un archivo de vídeo o un vídeo en YouTube.

## <a name="description"></a>Descripción
Un control **Audio** reproduce una secuencia de sonido de un archivo, una grabación de un control **[Micrófono](control-microphone.md)** o el audio de una pista de audio de un archivo de vídeo.

Un control **Vídeo** reproduce una secuencia de vídeo de un archivo o de YouTube o Azure Media Services.  Opcionalmente, se pueden mostrar subtítulos cuando se especifique.

## <a name="key-properties"></a>Propiedades principales
**Bucle**: indica si una secuencia de audio o vídeo empieza de nuevo automáticamente en cuanto termina de reproducirse.

**Multimedia**: un identificador de la secuencia que reproduce un control de audio o de vídeo.

**MostrarControles**: indica si se muestra un reproductor de audio o vídeo, por ejemplo, un botón de reproducción y un control deslizante de volumen, y un control de entrada manuscrita muestra, por ejemplo, iconos para dibujar, borrar y borrar todo.

## <a name="additional-properties"></a>Propiedades adicionales
**[AccessibleLabel](properties-accessibility.md)**: etiqueta para lectores de pantalla. Debe ser el título de la secuencia de vídeo o audio.

**PausarAutomáticamente**: indica si un clip de audio o vídeo se detiene automáticamente si el usuario se desplaza a otra pantalla.

**IniciarAutomáticamente**: indica si un control de audio o vídeo empieza a reproducir automáticamente un clip cuando el usuario navega a la pantalla que contiene ese control.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**ClosedCaptionsUrl**: solo control de vídeo.  Dirección URL del archivo de los subtítulos en formato de WebVTT.  Ambas direcciones URL, la del vídeo y la de los subtítulos, deben ser HTTPS. El servidor que hospede los archivos de vídeo y los subtítulos debe tener CORS habilitado.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[FocusedBorderColor](properties-color-border.md)**: el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)**: el grosor del borde de un control cuando el control recibe el foco.

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

**[TabIndex](properties-accessibility.md)**: orden de navegación del teclado en relación con otros controles.

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

    > [!TIP]
   > El botón de reproducción del control **Vídeo** aparece cuando mantiene el puntero sobre el control.
5. Presione Esc para volver al área de trabajo predeterminada.

### <a name="play-a-youtube-video"></a>Reproducir un vídeo de YouTube
1. Agregue un control **Vídeo** y establezca su propiedad **Multimedia** en la dirección URL del vídeo de YouTube entre comillas.
2. Presione F5 y, a continuación, reproduzca la secuencia haciendo clic o pulsando en el botón de reproducción del control **Vídeo**.
3. Presione Esc para volver al área de trabajo predeterminada.

### <a name="play-a-video-from-azure-media-services"></a>Reproducción de un vídeo desde Azure Media Services
1. Una vez que los vídeos se publiquen en AMS, copie la dirección URL del manifiesto. Inicie el punto de conexión de streaming del servicio, si no lo ha hecho todavía.
1. Agregue un control **Vídeo** y establezca su propiedad **Multimedia** en la dirección URL del vídeo de AMS entre comillas.
2. Presione F5 y, a continuación, reproduzca la secuencia haciendo clic o pulsando en el botón de reproducción del control **Vídeo**.
3. Presione Esc para volver al área de trabajo predeterminada.


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="audio-and-video-alternatives"></a>Alternativas de audio y vídeo
* **ShowControls** debe configurarse en true para que los usuarios puedan escuchar o ver elementos multimedia a su propio ritmo. Esto también permite a los usuarios activar o desactivar subtítulos y el modo de pantalla completa en los reproductores de vídeo.
* Deben proporcionarse subtítulos para los vídeos.
  *  En el caso de los vídeos de YouTube, utilice las herramientas de creación proporcionadas por YouTube para agregar subtítulos.
  *  Para otros vídeos, cree subtítulos en formato WebVTT, cárguelos y configure el valor **ClosedCaptionsUrl** con la ubicación de la dirección URL. Existen varias limitaciones. Es necesario que los servidores que hospedan vídeo y subtítulos estén habilitados para CORS y los controlen mediante el protocolo HTTPS. Los subtítulos no funcionan en Internet Explorer.
* Considere la posibilidad de proporcionar una transcripción de audio o vídeo con uno de estos métodos:
  1. Ponga el texto en un elemento **[Label](control-text-box.md)** y colóquelo junto al reproductor multimedia. Opcionalmente, puede crear un elemento **[Button](control-button.md)** para alternar la presentación del texto.
  2. Coloque el texto en otra pantalla. Cree un elemento **[Button](control-button.md)** que vaya a la pantalla y colóquelo junto al reproductor multimedia.
  3. Si la descripción es breve, puede colocarse en **[AccessibleLabel](properties-accessibility.md)**.

### <a name="color-contrast"></a>Contraste de color
Debe haber un contraste de color adecuado entre:
* **[FocusedBorderColor](properties-color-border.md)** y el color exterior
* **[Image](properties-visual.md)** y los controles del reproductor multimedia (si procede)
* **[Fill](properties-color-border.md)** y los controles del reproductor multimedia (si el relleno está visible)

Proporcione subtítulos o transcripción si el contenido de vídeo tiene problemas de contraste de color.

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* La propiedad **[AccessibleLabel](properties-accessibility.md)** debe estar presente.

### <a name="keyboard-support"></a>Compatibilidad con el teclado
* La propiedad **[TabIndex](properties-accessibility.md)** debe ser cero o superior para que los usuarios del teclado puedan desplazarse hasta él.
* Los indicadores de foco deben ser claramente visibles. Use **[FocusedBorderColor](properties-color-border.md)** y **[FocusedBorderThickness](properties-color-border.md)** para conseguirlo.
* **AutoStart** debe ser false porque puede ser difícil para los usuarios del teclado detener la reproducción rápidamente.
