---
title: 'Control de vídeo Microsoft Stream: referencia | Microsoft Docs'
description: Información sobre el control de vídeo Microsoft Stream, con propiedades y ejemplos
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 11/26/2019
ms.author: fikaradz
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c9d3594ecf338c6cfa93786f56a09606b2de6296
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732019"
---
# <a name="microsoft-stream-video-control-in-power-apps"></a>Microsoft Stream el control de vídeo en Power apps
Un reproductor de vídeo para Microsoft Stream vídeos y canales.

## <a name="description"></a>Descripción
El control permitirá a los usuarios de la aplicación reproducir vídeos y examinar los canales desde el servicio de Microsoft Stream.

## <a name="key-properties"></a>Propiedades principales
**StreamUrl** : la dirección URL del Microsoft Stream vídeo o canal que se va a mostrar en el control.

**ShowControls** : indica si los controles de reproducción de vídeo se muestran al usuario final.

## <a name="additional-properties"></a>Propiedades adicionales
**[AccessibleLabel](properties-accessibility.md)** : etiqueta para lectores de pantalla. Debe ser el título de la secuencia de vídeo o audio.

**IniciarAutomáticamente**: indica si un control de audio o vídeo empieza a reproducir automáticamente un clip cuando el usuario navega a la pantalla que contiene ese control.

**[BorderColor](properties-color-border.md)** : el color de un borde del control.

**[BorderStyle](properties-color-border.md)** : si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)** : el grosor de un borde del control.

**[DisplayMode](properties-core.md)** : indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[Fill](properties-color-border.md)** : el color de fondo de un control.

**[FocusedBorderColor](properties-color-border.md)** : el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)** : el grosor del borde de un control cuando el control recibe el foco.

**[Height](properties-size-location.md)** : la distancia entre los bordes superior e inferior de un control.

**HoraDeInicio**: la hora después del inicio de una secuencia de audio o de vídeo cuando la secuencia empieza a reproducirse.

**[TabIndex](properties-accessibility.md)** : orden de navegación del teclado en relación con otros controles.

**[Información sobre herramientas](properties-core.md)** : texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Visible](properties-core.md)** : indica si un control aparece o está oculto.

**[Width](properties-size-location.md)** : la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)** : la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)** : la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="example"></a>Ejemplo

### <a name="play-an-audio-or-video-file-from-microsoft-stream"></a>Reproducir un archivo de audio o vídeo desde Microsoft Stream

1. En el menú **archivo** , seleccione **Insertar** y, a continuación, abra el menú desplegable **multimedia** . 
2. Seleccione **Microsoft Stream** de la lista de controles multimedia:

    ![Microsoft Stream](./media/control-stream-video/stream-icon.png "Microsoft Stream")

3. Pegue el vínculo de vídeo dentro de la propiedad **Stream URL** de la izquierda:

    ![Personalizar la propiedad StreamUrl](./media/control-stream-video/stream-url.png "Personalizar la propiedad StreamUrl")

4. Presione F5 y seleccione el botón de reproducción del control que ha agregado.

    > [!NOTE]
   > **Microsoft Stream** requiere autenticación para reproducir el vídeo. Asegúrese de que el usuario de la aplicación tiene el permiso necesario.
5. Presione ESC para salir del modo de vista previa.

## <a name="browser-considerations"></a>Consideraciones sobre el explorador

### <a name="ios"></a>iOS
El reproductor de iOS de Power apps no admite la reproducción directa de vídeos insertados en la aplicación.  Para ver el vídeo, haga clic en el icono de la secuencia para iniciar el reproductor de vídeo en modo de pantalla completa.

### <a name="safari"></a>Safari

Para ver Microsoft Stream vídeos en una aplicación en el explorador Safari, tendrá que desactivar la opción para [evitar el seguimiento entre sitios](https://support.apple.com/guide/safari/sfri40732/mac).

## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="audio-and-video-alternatives"></a>Alternativas de audio y vídeo
* **ShowControls** debe configurarse en true para que los usuarios puedan escuchar o ver elementos multimedia a su propio ritmo. Esto también permite a los usuarios activar o desactivar subtítulos y el modo de pantalla completa en los reproductores de vídeo.
* Deben proporcionarse subtítulos para los vídeos.
 * Considere la posibilidad de proporcionar una transcripción de audio o vídeo con uno de estos métodos:
  1. Ponga el texto en un elemento **[Label](control-text-box.md)** y colóquelo junto al reproductor multimedia. Opcionalmente, puede crear un elemento **[Button](control-button.md)** para alternar la presentación del texto.
  2. Coloque el texto en otra pantalla. Cree un elemento **[Button](control-button.md)** que vaya a la pantalla y colóquelo junto al reproductor multimedia.
  3. Si la descripción es breve, puede colocarse en **[AccessibleLabel](properties-accessibility.md)** .

### <a name="color-contrast"></a>Contraste de color
Debe haber un contraste de color adecuado entre:
* **[FocusedBorderColor](properties-color-border.md)** y el color exterior
* **[Fill](properties-color-border.md)** y los controles del reproductor multimedia (si el relleno está visible)

Proporcione subtítulos o transcripción si el contenido de vídeo tiene problemas de contraste de color.

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* La propiedad **[AccessibleLabel](properties-accessibility.md)** debe estar presente.

### <a name="keyboard-support"></a>Compatibilidad con el teclado
* La propiedad **[TabIndex](properties-accessibility.md)** debe ser cero o superior para que los usuarios del teclado puedan desplazarse hasta él.
* Los indicadores de foco deben ser claramente visibles. Use **[FocusedBorderColor](properties-color-border.md)** y **[FocusedBorderThickness](properties-color-border.md)** para conseguirlo.
* **AutoStart** debe ser false porque puede ser difícil para los usuarios del teclado detener la reproducción rápidamente.