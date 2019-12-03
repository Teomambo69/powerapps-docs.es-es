---
title: 'Control Temporizador: referencia | Microsoft Docs'
description: Información sobre el control Temporizador, con propiedades y ejemplos
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2462f82420713e93c3ac0598a73e2dc43bc7c0b1
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731958"
---
# <a name="timer-control-in-power-apps"></a>Control de temporizador en Power apps
Control que determina la forma en que la aplicación responde una vez transcurrido un tiempo determinado.

## <a name="description"></a>Descripción
Los temporizadores, por ejemplo, determinan el tiempo que un control va a aparecer o cambian otras propiedades de un control una vez transcurrido un tiempo determinado.

> [!NOTE]
> En Power apps Studio, los temporizadores solo se ejecutan en el modo de vista previa.


## <a name="key-properties"></a>Propiedades principales
**Duración**: el tiempo durante el que se ejecuta un temporizador, en milisegundos.  No hay valor máximo.

**AlFinalizarTemporizador**: respuesta de la aplicación al finalizar la ejecución del temporizador.

**Repetir**: indica si un temporizador se reinicia automáticamente cuando finaliza la ejecución.

## <a name="additional-properties"></a>Propiedades adicionales
**[Align](properties-text.md)** : la ubicación del texto respecto al centro horizontal de su control.

**AutoPause**: indica si el control de temporizador se pausa automáticamente si el usuario se desplaza a otra pantalla.

**AutoStart**: indica si el control de temporizador se empieza a reproducir automáticamente cuando el usuario se desplaza a la pantalla que contiene ese control.

**[BorderColor](properties-color-border.md)** : el color de un borde del control.

**[BorderStyle](properties-color-border.md)** : si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)** : el grosor de un borde del control.

**[Color](properties-color-border.md)** : el color del texto en un control.

**[DisplayMode](properties-core.md)** : indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)** : el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[DisabledColor](properties-color-border.md)** : el color del texto en un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[DisabledFill](properties-color-border.md)** : el color de fondo de un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[Fill](properties-color-border.md)** : el color de fondo de un control.

**[FocusedBorderColor](properties-color-border.md)** : el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)** : el grosor del borde de un control cuando el control recibe el foco.

**[Font](properties-text.md)** : el nombre de la familia de fuentes en la que aparece el texto.

**[FontWeight](properties-text.md)** : el peso del texto en un control: **Bold**, **Semibold**, **Normal** o **Lighter**.

**[Height](properties-size-location.md)** : la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)** : el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**[HoverColor](properties-color-border.md)** : el color del texto de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[HoverFill](properties-color-border.md)** : el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[Italic](properties-text.md)** : indica si el texto de un control está en cursiva.

**[OnSelect](properties-core.md)** : indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**AlIniciarTemporizador**: respuesta de la aplicación cuando se inicia un temporizador.

**[PressedBorderColor](properties-color-border.md)** : el color de un borde del control cuando el usuario toca o hace clic en ese control.

**[PressedColor](properties-color-border.md)** : el color de texto de un control cuando el usuario toca o hace clic en ese control.

**[PressedFill](properties-color-border.md)** : el color de fondo de un control cuando el usuario toca o hace clic en ese control.

**[Reset](properties-core.md)** : indica si un control vuelve a su valor predeterminado.

**[Size](properties-text.md)** : el tamaño de la fuente del texto que aparece en un control.

**Start**: indica si el temporizador se inicia.

**[Strikethrough](properties-text.md)** : indica si aparece una línea sobre el texto de un control.

**[TabIndex](properties-accessibility.md)** : orden de navegación del teclado en relación con otros controles.

**[Text](properties-core.md)** : texto que aparece en un control o que el usuario escribe en un control.

**[Información sobre herramientas](properties-core.md)** : texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Underline](properties-text.md)** : indica si aparece una línea debajo del texto de un control.

**[Visible](properties-core.md)** : indica si un control aparece o está oculto.

**[Width](properties-size-location.md)** : la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)** : la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)** : la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**Refresh**( *DataSource* )](../functions/function-refresh.md)

## <a name="examples"></a>Ejemplos
### <a name="show-a-countdown"></a>Mostrar una cuenta atrás
1. Agregue un temporizador y asígnele el nombre **Countdown**.

    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
2. Establezca la propiedad **Duration** en **10000** y sus propiedades **Repetir** e **IniciarAutomáticamente** en **true**.
3. (opcional) Configure la propiedad **[Altura](properties-size-location.md)** en **160**, su propiedad **[Altura](properties-size-location.md)** en **600** y su propiedad **[Size](properties-text.md)** en **60** para facilitar la lectura del temporizador.
4. Agregue una etiqueta y establezca su propiedad **[Text](properties-core.md)** en esta fórmula:
   <br>**"Number of seconds remaining: " & RoundUp(10-Countdown.Value/1000, 0)**

    ¿Desea más información sobre la función **[RedondearMas](../functions/function-round.md)** u [otras funciones](../formula-reference.md)?

    La etiqueta muestra cuántos segundos quedan para que se reinicie el temporizador.

### <a name="animate-a-control"></a>Animar un control
1. Agregue un temporizador y asígnele el nombre **FadeIn**.

    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
2. Establezca la propiedad **Duration** del temporizador en **5000**, su propiedad **Repeat** en **true** y su propiedad **[Text](properties-core.md)** en **Toggle animation**.
3. (opcional) Configure la propiedad **[Altura](properties-size-location.md)** en **160**, su propiedad **[Altura](properties-size-location.md)** en **600** y su propiedad **[Size](properties-text.md)** en **60** para facilitar la lectura del temporizador.
4. Agregue una etiqueta y establezca su propiedad **[Texto](properties-core.md)** para que muestre el mensaje **Welcome!** y establezca su propiedad **[Color](properties-color-border.md)** con esta fórmula:
   <br>**ColorFade(Color.BlueViolet, FadeIn.Value/5000)**

    ¿Desea más información sobre la función **[ColorFade](../functions/function-colors.md)** u [otras funciones](../formula-reference.md)?

5. Seleccione el botón de temporizador para iniciar o detener la animación. El texto de la etiqueta se difumina a blanco, recupera su intensidad y el proceso se repite.

## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
Las mismas instrucciones para el control de **[botón](control-button.md)** se aplican al control de **temporizador** si los usuarios pueden interactuar con él.

### <a name="background-timers"></a>Temporizadores de fondo
Los temporizadores en segundo plano se ejecutan automáticamente y están ocultos. Úselos en un rol de soporte en el que el tiempo transcurrido sea de poca interés para el usuario. Por ejemplo, puede actualizar los datos cada minuto o mostrar un mensaje de notificación solo durante un período de tiempo determinado.

Los temporizadores de fondo deben tener la propiedad **[visible](properties-core.md)** establecida en false para que estén ocultos para todos los usuarios.

### <a name="timing-considerations"></a>Consideraciones de sincronización
Si un **temporizador** se ejecuta automáticamente, considere si los usuarios tienen tiempo suficiente para leer y usar el contenido. Los usuarios de teclado y de lectura de pantalla pueden necesitar más tiempo para reaccionar a un evento con hora.

Cualquiera de estas estrategias es suficiente:
* Permite a los usuarios cancelar el evento con hora.
* Permite a los usuarios ajustar el límite de tiempo antes de comenzar.
* Advierta 20 segundos antes de que expire el límite de tiempo y proporcione una manera fácil de ampliar el límite.

Algunos escenarios están exentos de estos requisitos. Aprenda más sobre las [directrices de WCAG 2.0 para los límites de tiempo](https://www.w3.org/TR/WCAG20/#time-limits).

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* Si un temporizador desencadena cambios en la pantalla actual, use una [región activa](../accessible-apps-live-regions.md) para indicar a los usuarios del lector de pantalla lo que ha cambiado.

    > [!NOTE]
    > Si el temporizador está visible y en ejecución, los lectores de pantalla anunciarán el tiempo transcurrido cada cinco segundos.

* No use la propiedad **[texto](properties-core.md)** de un control para obtener información importante y sensible al tiempo. Los lectores de pantalla no anunciarán cambios en el **[texto](properties-core.md)** .
* Para temporizadores interactivos:
    * La propiedad **[Text](properties-core.md)** debe existir.
    * Considere la posibilidad de agregar un control **[etiqueta](control-text-box.md)** para mostrar el tiempo transcurrido. Use la propiedad **[Text](properties-core.md)** del temporizador para indicar al usuario que inicie o detenga el temporizador.
