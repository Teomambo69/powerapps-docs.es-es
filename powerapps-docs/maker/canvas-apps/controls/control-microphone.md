---
title: 'Control Micrófono: referencia | Microsoft Docs'
description: Información sobre el control Micrófono, con propiedades y ejemplos
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/16/2020
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 353485baf6726314f6009c57838b3aa68d145fa0
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79436755"
ms.PowerAppsDecimalTransform: true
---
# <a name="microphone-control-in-power-apps"></a>Control de micrófono en Power apps

Un control que permite a los usuarios de la aplicación grabar sonidos desde su dispositivo.

## <a name="description"></a>Descripción

Use el control **micrófono** para capturar audio con el micrófono de un dispositivo.  El dispositivo debe tener un micrófono y el usuario debe autorizar a la aplicación para que use el micrófono.  El control de micrófono se admite cuando se ejecuta en un explorador Web.  

El clip de audio grabado más recientemente está disponible a través de la propiedad **audio** . Con esta propiedad, el audio grabado puede ser:

- **Se reproduce con el control de audio.**  Use el control [audio](control-audio-video.md) para escuchar la grabación. Para obtener más información, vea los [ejemplos](#examples).
- **Se coloca temporalmente en una variable o una colección.**  Use las funciones [set](../functions/function-set.md) o [Collect](../functions/function-clear-collect-clearcollect.md) para almacenar los clips de audio en una variable o una colección.  Tenga cuidado con varios clips de audio de una colección al mismo tiempo con la memoria limitada del dispositivo.  Use las funciones [savedata](../functions/function-savedata-loaddata.md) y [LoadData](../functions/function-savedata-loaddata.md) para trasladar clips de audio al almacenamiento local en el dispositivo y para [escenarios sin conexión](../offline-apps.md).
- **Almacenado en una base de datos.**  Utilice la función [patch](../functions/function-patch.md) para almacenar clips de audio en una base de datos.
- **Se transmite como una cadena de texto codificada en Base64.**  Use la función [JSON](../functions/function-json.md) para codificar los clips de audio en Base64.

Formato del audio grabado:

- formato *3GP* para *Android*.
- Formato *AAC* para *iOS*.
- Formato *OGG* para los *exploradores Web*.

Un URI de cadena de texto hace referencia a los medios capturados. Para obtener más información, lea la [documentación del tipo de datos](../functions/data-types.md#uris-for-images-and-other-media).

## <a name="key-properties"></a>Propiedades principales

**Audio** : el clip de audio capturado cuando el usuario registra con el micrófono del dispositivo. 

**MIC** : identificador numérico del micrófono en un dispositivo que tiene más de un micrófono.

**AlDetener**: indica cómo la aplicación responde cuando el usuario detiene la grabación con un control de micrófono.

## <a name="additional-properties"></a>Propiedades adicionales

[AccessibleLabel](properties-accessibility.md): etiqueta para lectores de pantalla. Debe describir la finalidad del micrófono.

[BorderColor](properties-color-border.md): el color de un borde del control.

[BorderStyle](properties-color-border.md) : si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

[BorderThickness](properties-color-border.md): el grosor de un borde del control.

[Color](properties-color-border.md): el color del texto en un control.

[DisplayMode](properties-core.md) : indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**deshabilitado**).

[DisabledBorderColor](properties-color-border.md) : el color del borde de un control si la propiedad [DisplayMode](properties-core.md) del control está establecida en **Disabled**.

[DisabledColor](properties-color-border.md) : el color del texto de un control si su propiedad [DisplayMode](properties-core.md) está establecida en **Disabled**.

[DisabledFill](properties-color-border.md) : el color de fondo de un control si su propiedad [DisplayMode](properties-core.md) está establecida en **Disabled**.

[Fill](properties-color-border.md): el color de fondo de un control.

[FocusedBorderColor](properties-color-border.md) : el color del borde de un control cuando el control tiene el foco.

[FocusedBorderThickness](properties-color-border.md) : el grosor del borde de un control cuando el control tiene el foco.

[Height](properties-size-location.md): la distancia entre los bordes superior e inferior de un control.

[HoverBorderColor](properties-color-border.md): el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

[HoverColor](properties-color-border.md): el color del texto de un control cuando el usuario mantiene el puntero del mouse sobre él.

[HoverFill](properties-color-border.md): el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

[Image](properties-visual.md): el nombre de la imagen que aparece en un control de imagen, audio o micrófono.

[ImagePosition](properties-visual.md): la posición (**Fill**, **Fit**, **Stretch**, **Tile** o **Center**) de una imagen en una pantalla o un control, si no tiene el mismo tamaño que la imagen.

[Alseleccionar](properties-core.md) : cómo responde la aplicación cuando el usuario selecciona un control.

**AlIniciar**: indica cómo la aplicación responde cuando el usuario comienza a grabar con un control de micrófono.

[PressedBorderColor](properties-color-border.md) : el color del borde de un control cuando el usuario selecciona ese control.

[PressedColor](properties-color-border.md) : el color del texto de un control cuando el usuario selecciona ese control.

[PressedFill](properties-color-border.md) : el color de fondo de un control cuando el usuario selecciona ese control.

[Reset](properties-core.md): indica si un control vuelve a su valor predeterminado.

[TabIndex](properties-accessibility.md) : orden de navegación por el teclado comparado con otros controles.

[Tooltip](properties-core.md): texto explicativo que aparece cuando el usuario mantiene el mouse sobre un control.

[Visible](properties-core.md): indica si un control aparece o está oculto.

[Width](properties-size-location.md): la distancia entre los bordes derecho e izquierdo de un control.

[X](properties-size-location.md) : la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor o pantalla primaria.

[Y](properties-size-location.md) : la distancia entre el borde superior de un control y el borde superior del contenedor o la pantalla primarios.

## <a name="examples"></a>Ejemplos:

### <a name="simple-direct-playback"></a>Reproducción directa simple

En este ejemplo, conectaremos directamente un control de **micrófono** con un control de **audio** para la reproducción inmediata:

1. [Agregue](../add-configure-controls.md) un control de **micrófono** a la aplicación.
1. Autorice a la aplicación a usar el micrófono del dispositivo si se le solicita.
1. Agregue un control de **audio** a la aplicación.
1. Establezca la propiedad **multimedia** del control de **audio** en la fórmula:

    ```powerapps-comma
    Microphone1.Audio
    ```

    > [!NOTE]
    > Reemplace el nombre del control de micrófono *Microphone1* según corresponda.

1. Obtenga una vista previa de la aplicación.
1. Seleccione el control de **micrófono** para empezar a grabar.
1. Hable para grabar audio.
1. Vuelva a seleccionar el control de **micrófono** para finalizar la grabación.
1. Seleccione el control **audio** para oír la grabación.  

### <a name="add-sounds-to-a-gallery-control"></a>Agregar sonidos a un control Galería

En este ejemplo, vamos a crear una galería de clips de audio almacenada en una colección que se puede seleccionar individualmente para la reproducción:

1. [Agregue](../add-configure-controls.md) un control de **micrófono** .

1. Establezca su propiedad **OnStop** en esta fórmula con la función [Collect](../functions/function-clear-collect-clearcollect.md) :

    ```powerapps-comma
    Collect( MySounds; MyMic.Audio )
    ```

1. Agregue un control **Galería** , muévalo debajo de **MyMic**.

1. Establezca la propiedad [elementos](properties-core.md) de la galería en esta fórmula:

    ```powerapps-comma
    MySounds
    ```

1. En la plantilla del control **Galería personalizada** , agregue un control [audio](control-audio-video.md) .

1. Establezca la propiedad **multimedia** del control de audio en esta fórmula:

    ```powerapps-comma
    ThisItem.Url
    ```

1. Presione F5 para obtener una vista previa de la aplicación.

1. Seleccione **MyMic** para iniciar la grabación y luego vuelva a seleccionarlo para detener la grabación.

1. En el control **Galería** , seleccione el botón reproducir en el control **audio** para reproducir la grabación.

1. Agregue tantas grabaciones como desee y, a continuación, vuelva al área de trabajo predeterminada presionando la tecla ESC.

1. opta En la plantilla del control **Galería** , agregue un control [botón](control-button.md) .

1. Establezca su propiedad [alseleccionar](properties-core.md) en la fórmula:

    ```powerapps-comma
    Remove( MySounds; ThisItem )
    ```

1. Presione F5 y, a continuación, quite una grabación seleccionando el control de **botón** correspondiente.

Utilice la función [savedata](../functions/function-savedata-loaddata.md) para guardar las grabaciones localmente o la función [patch](../functions/function-patch.md) para actualizar un origen de datos.

## <a name="accessibility-guidelines"></a>Directrices de accesibilidad

Se aplican las mismas directrices para [Button](control-button.md) porque el **micrófono** es simplemente un botón especializado. Además, tenga en cuenta lo siguiente:

### <a name="audio-alternatives"></a>Alternativas de audio

Considere la posibilidad de agregar una forma alternativa de entrada para los usuarios con discapacidades del habla o que no tienen micrófono. Por ejemplo, [entrada de texto](control-text-input.md) para permitir que los usuarios escriban texto.

### <a name="color-contrast"></a>Contraste de color

- Lea los [requisitos de contraste de color estándar](../accessible-apps-color.md).
- Garantizar el contraste de color adecuado entre la [imagen](properties-visual.md) y el texto del botón y el icono (si procede).

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla

- [Propiedad accessiblelabel](properties-accessibility.md) debe estar presente.
