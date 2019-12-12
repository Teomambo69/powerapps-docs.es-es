---
title: Propiedades de color y bordes | Microsoft Docs
description: Información de referencia acerca de propiedades como BorderColor, HoverBorderColor y PressedBorderColor
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 69b15887894bba576364ced8bab9f47eceeb8f96
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731905"
---
# <a name="color-and-border-properties-in-power-apps"></a>Propiedades de color y borde en Power apps

## <a name="overview"></a>Información general

Configure el estilo de un control en función de cómo el usuario interactúa con él.

Puede especificar los colores de muchas maneras:

- Enumeración de [**color**](../functions/function-colors.md) : Especifique los nombres de colores de las hojas de estilos en cascada, como en estos ejemplos:

  - **Color.Red**
  - **Color.Indigo**

- Función [**ColorValue**](../functions/function-colors.md) : Especifique cadenas de texto como nombres de colores de hojas de estilos en cascada y notación de código hexadecimal ( **#** ), como en estos ejemplos:

  - **ColorValue ("AliceBlue")**
  - **ColorValue( "#ff00ff" )**

- Función [**ColorFade**](../functions/function-colors.md) : Especificar el modo en que se descolorida un color, de todo el negro (-100%) a todo el blanco (100%), como en este ejemplo:

  - **ColorFade (color, rojo, 50%)**

- [**RGBA**](../functions/function-colors.md) (función): Especifique los componentes rojo, verde y azul de un color de 0 a 255 y especifique un canal alfa de 0% (totalmente transparente) a 100% (totalmente opaco), como en este ejemplo:

  - **RGBA (255, 0, 255, 25%)**

Las propiedades de color también pueden hacer referencia a otras propiedades de color. Por ejemplo, **Label. PressedColor** se puede establecer en la fórmula **Label1. color**, y en cascada automáticamente un cambio de una propiedad a otra.

## <a name="normal"></a>Normal

Estas propiedades estarán en vigor normalmente cuando el usuario no está interactúe con el control.

**BorderColor**: el color de un borde del control.

- Se aplica a los controles **[Agregar imagen](control-add-picture.md)** , **[Audio](control-audio-video.md)** , **[Botón](control-button.md)** , **[Cámara](control-camera.md)** , **[Tarjeta](control-card.md)** , **[Casilla](control-check-box.md)** , **[Gráfico de columnas](control-column-line-chart.md)** , **[Selector de fecha](control-date-picker.md)** , **[Mostrar formulario](control-form-detail.md)** , **[Desplegable](control-drop-down.md)** , **[Formulario de edición](control-form-detail.md)** , **[Exportar](control-export-import.md)** , **[Galería](control-gallery.md)** , **[Texto HTML](control-html-text.md)** , **[Imagen](control-image.md)** , **[Importar](control-export-import.md)** , **[Etiqueta](control-text-box.md)** , **[Gráfico de líneas](control-column-line-chart.md)** , **[Cuadro de lista](control-list-box.md)** , **[Micrófono](control-microphone.md)** , **[Visor de PDF](control-pdf-viewer.md)** , **[Entrada manuscrita](control-pen-input.md)** , **[Gráfico circular](control-pie-chart.md)** , **[Radio](control-radio.md)** , **[Clasificación](control-rating.md)** , **[Control deslizante](control-slider.md)** , **[Entrada de texto](control-text-input.md)** , **[Temporizador](control-timer.md)** , **[Alternancia](control-toggle.md)** y **[Video](control-audio-video.md)** .

**BorderStyle**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

- Se aplica a los controles **[Agregar imagen](control-add-picture.md)** , **[Audio](control-audio-video.md)** , **[Botón](control-button.md)** , **[Cámara](control-camera.md)** , **[Tarjeta](control-card.md)** , **[Casilla](control-check-box.md)** , **[Gráfico de columnas](control-column-line-chart.md)** , **[Selector de fecha](control-date-picker.md)** , **[Mostrar formulario](control-form-detail.md)** , **[Desplegable](control-drop-down.md)** , **[Formulario de edición](control-form-detail.md)** , **[Exportar](control-export-import.md)** , **[Galería](control-gallery.md)** , **[Texto HTML](control-html-text.md)** , **[Imagen](control-image.md)** , **[Importar](control-export-import.md)** , **[Etiqueta](control-text-box.md)** , **[Gráfico de líneas](control-column-line-chart.md)** , **[Cuadro de lista](control-list-box.md)** , **[Micrófono](control-microphone.md)** , **[Visor de PDF](control-pdf-viewer.md)** , **[Entrada manuscrita](control-pen-input.md)** , **[Gráfico circular](control-pie-chart.md)** , **[Radio](control-radio.md)** , **[Clasificación](control-rating.md)** , **[Control deslizante](control-slider.md)** , **[Entrada de texto](control-text-input.md)** , **[Temporizador](control-timer.md)** , **[Alternancia](control-toggle.md)** y **[Video](control-audio-video.md)** .

**BorderThickness**: el grosor de un borde del control.

- Se aplica a los controles **[Agregar imagen](control-add-picture.md)** , **[Audio](control-audio-video.md)** , **[Botón](control-button.md)** , **[Cámara](control-camera.md)** , **[Tarjeta](control-card.md)** , **[Casilla](control-check-box.md)** , **[Gráfico de columnas](control-column-line-chart.md)** , **[Selector de fecha](control-date-picker.md)** , **[Mostrar formulario](control-form-detail.md)** , **[Desplegable](control-drop-down.md)** , **[Formulario de edición](control-form-detail.md)** , **[Exportar](control-export-import.md)** , **[Galería](control-gallery.md)** , **[Texto HTML](control-html-text.md)** , **[Imagen](control-image.md)** , **[Importar](control-export-import.md)** , **[Etiqueta](control-text-box.md)** , **[Gráfico de líneas](control-column-line-chart.md)** , **[Cuadro de lista](control-list-box.md)** , **[Micrófono](control-microphone.md)** , **[Visor de PDF](control-pdf-viewer.md)** , **[Entrada manuscrita](control-pen-input.md)** , **[Gráfico circular](control-pie-chart.md)** , **[Radio](control-radio.md)** , **[Clasificación](control-rating.md)** , **[Control deslizante](control-slider.md)** , **[Entrada de texto](control-text-input.md)** , **[Temporizador](control-timer.md)** , **[Alternancia](control-toggle.md)** y **[Video](control-audio-video.md)** .

**Color**: el color del texto en un control.

- Se aplica a los controles **[Agregar imagen](control-add-picture.md)** , **[Botón](control-button.md)** , **[Casilla](control-check-box.md)** , **[Gráfico de columnas](control-column-line-chart.md)** , **[Selector de fecha](control-date-picker.md)** , **[Desplegable](control-drop-down.md)** , **[Exportar](control-export-import.md)** , **[Texto HTML](control-html-text.md)** , **[Importar](control-export-import.md)** , **[Gráfico de líneas](control-text-box.md)** , **[Cuadro de lista](control-column-line-chart.md)** , **[Micrófono](control-list-box.md)** , **[Entrada manuscrita](control-microphone.md)** , **[Gráfico circular](control-pen-input.md)** , **[Radio](control-pie-chart.md)** , **[Cuadro de texto](control-radio.md)** , **[Entrada de texto](control-text-input.md)** y **[Temporizador](control-timer.md)** .

**Fill**: el color de fondo de un control.

- Se aplica a los controles **[Agregar imagen](control-add-picture.md)** , **[Audio](control-audio-video.md)** , **[Botón](control-button.md)** , **[Tarjeta](control-card.md)** , **[Casilla](control-check-box.md)** , **[Selector de fecha](control-date-picker.md)** , **[Mostrar formulario](control-form-detail.md)** , **[Desplegable](control-drop-down.md)** , **[Formulario de edición](control-form-detail.md)** , **[Exportar](control-export-import.md)** , **[Galería](control-gallery.md)** , **[Texto HTML](control-html-text.md)** , **[Icono](control-shapes-icons.md)** , **[Imagen](control-image.md)** , **[Importar](control-export-import.md)** , **[Cuadro de lista](control-text-box.md)** , **[Micrófono](control-list-box.md)** , **[Visor de PDF](control-microphone.md)** , **[Entrada manuscrita](control-pdf-viewer.md)** , **[Radio](control-pen-input.md)** , **[Clasificación](control-radio.md)** , **[Pantalla](control-rating.md)** , **[Forma](control-screen.md)** , **[Cuadro de texto](control-shapes-icons.md)** , **[Entrada de texto](control-text-input.md)** , **[Temporizador](control-timer.md)** , **[Alternancia](control-toggle.md)** y **[Vídeo](control-audio-video.md)** .

## <a name="focused"></a>Enfocado

Estas propiedades tienen efecto cuando el control recibe el foco.

**FocusedBorderColor**: el color del borde de un control cuando recibe el foco.

**FocusedBorderThickness**: el grosor del borde de un control cuando recibe el foco.

- Estas propiedades se aplican a **[Agregar imagen](control-add-picture.md)** , **[Datos adjuntos](control-attachments.md)** , **[Audio](control-audio-video.md)** , **[Botón](control-button.md)** , **[Cámara](control-camera.md)** , **[Casilla](control-check-box.md)** , **[Cuadro combinado](control-combo-box.md)** , **[selector de fecha](control-date-picker.md)** , **[Lista desplegable](control-drop-down.md)** , **[Exportar](control-export-import.md)** , **[Galería](control-gallery.md)** , **[Icono](control-shapes-icons.md)** , **[Imagen](control-image.md)** , **[Importar](control-export-import.md)** , **[Etiqueta](control-text-box.md)** , **[Cuadro de lista](control-list-box.md)** , **[Micrófono](control-microphone.md)** , **[Radio](control-radio.md)** , **[Clasificación](control-rating.md)** , **[Forma](control-shapes-icons.md)** , **[Control deslizante](control-slider.md)** , **[Entrada de texto](control-text-input.md)** , **[Temporizador](control-timer.md)** , **[Alternar](control-toggle.md)** y **[Vídeo](control-audio-video.md)** .

## <a name="disabled"></a>Disabled

Estas propiedades tienen efecto cuando el control está deshabilitado.  Se puede deshabilitar un control si se estable la propiedad **[Disabled](properties-core.md)** en *true*.

**DisabledBorderColor**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

- Se aplica a los controles **[Agregar imagen](control-add-picture.md)** , **[Botón](control-button.md)** , **[Casilla](control-check-box.md)** , **[Gráfico de columnas](control-column-line-chart.md)** , **[Selector de fecha](control-date-picker.md)** , **[Desplegable](control-drop-down.md)** , **[Exportar](control-export-import.md)** , **[Texto HTML](control-html-text.md)** , **[Imagen](control-image.md)** , **[Importar](control-export-import.md)** , **[Gráfico de líneas](control-text-box.md)** , **[Cuadro de lista](control-column-line-chart.md)** , **[Micrófono](control-list-box.md)** , **[Visor de PDF](control-microphone.md)** , **[Gráfico circular](control-pdf-viewer.md)** , **[Radio](control-pie-chart.md)** , **[Control deslizante](control-radio.md)** , **[Cuadro de texto](control-slider.md)** , **[Entrada de texto](control-text-input.md)** , **[Temporizador](control-timer.md)** y **[Alternancia](control-toggle.md)** .

**DisabledColor**: el color del texto en un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

- Se aplica a los controles **[Agregar imagen](control-add-picture.md)** , **[Botón](control-button.md)** , **[Casilla](control-check-box.md)** , **[Selector de fechas](control-date-picker.md)** , **[Desplegable](control-drop-down.md)** , **[Exportar](control-export-import.md)** , **[Importar](control-export-import.md)** , **[Cuadro de lista](control-text-box.md)** , **[Micrófono](control-list-box.md)** , **[Radio](control-microphone.md)** , **[Cuadro de texto](control-radio.md)** , **[Entrada de texto](control-text-input.md)** y **[Temporizador](control-timer.md)** .

**DisabledFill**: el color de fondo de un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

- Se aplica a los controles **[Agregar imagen](control-add-picture.md)** , **[Botón](control-button.md)** , **[Casilla](control-check-box.md)** , **[Selector de fechas](control-date-picker.md)** , **[Desplegable](control-drop-down.md)** , **[Exportar](control-export-import.md)** , **[Texto HTML](control-html-text.md)** , **[Imagen](control-image.md)** , **[Importar](control-export-import.md)** , **[Cuadro de lista](control-text-box.md)** , **[Micrófono](control-list-box.md)** , **[Radio](control-microphone.md)** , **[Cuadro de texto](control-radio.md)** , **[Entrada de texto](control-text-input.md)** y **[Temporizador](control-timer.md)** .

## <a name="hover"></a>Hover

Estas propiedades tienen efecto cuando el usuario mantiene el mouse sobre el control.

**HoverBorderColor**: el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

- Se aplica a los controles **[Agregar imagen](control-add-picture.md)** , **[Botón](control-button.md)** , **[Casilla](control-check-box.md)** , **[Gráfico de columnas](control-column-line-chart.md)** , **[Desplegable](control-drop-down.md)** , **[Exportar](control-export-import.md)** , **[Texto HTML](control-html-text.md)** , **[Imagen](control-image.md)** , **[Importar](control-export-import.md)** , **[Gráfico de líneas](control-text-box.md)** , **[Cuadro de lista](control-column-line-chart.md)** , **[Micrófono](control-list-box.md)** , **[Visor de PDF](control-microphone.md)** , **[Gráfico circular](control-pdf-viewer.md)** , **[Control deslizante](control-pie-chart.md)** , **[Cuadro de texto](control-slider.md)** , **[Entrada de texto](control-text-input.md)** , **[Temporizador](control-timer.md)** y **[Alternancia](control-toggle.md)** .

**HoverColor**: el color del texto de un control cuando el usuario mantiene el puntero del mouse sobre él.

- Se aplica a los controles **[Agregar imagen](control-add-picture.md)** , **[Botón](control-button.md)** , **[Casilla](control-check-box.md)** , **[Desplegable](control-drop-down.md)** , **[Exportar](control-export-import.md)** , **[Importar](control-export-import.md)** , **[Cuadro de lista](control-text-box.md)** , **[Micrófono](control-list-box.md)** , **[Radio](control-microphone.md)** , **[Cuadro de texto](control-radio.md)** , **[Entrada de texto](control-text-input.md)** y **[Temporizador](control-timer.md)** .

**HoverFill**: el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

- Se aplica a los controles **[Agregar imagen](control-add-picture.md)** , **[Botón](control-button.md)** , **[Casilla](control-check-box.md)** , **[Desplegable](control-drop-down.md)** , **[Exportar](control-export-import.md)** , **[Icono](control-shapes-icons.md)** , **[Imagen](control-image.md)** , **[Importar](control-export-import.md)** , **[Cuadro de lista](control-text-box.md)** , **[Micrófono](control-list-box.md)** , **[Radio](control-microphone.md)** , **[Forma](control-radio.md)** , **[Cuadro de texto](control-shapes-icons.md)** , **[Entrada de texto](control-text-input.md)** y **[Temporizador](control-timer.md)** .

## <a name="pressed"></a>Pressed

Estas propiedades tienen efecto cuando se presiona un botón o un control de imagen.

**PressedBorderColor**: el color de un borde del control cuando el usuario toca o hace clic en ese control.

- Se aplica a los controles **[Agregar imagen](control-add-picture.md)** , **[Botón](control-button.md)** , **[Casilla](control-check-box.md)** , **[Gráfico de columnas](control-column-line-chart.md)** , **[Desplegable](control-drop-down.md)** , **[Exportar](control-export-import.md)** , **[Icono](control-shapes-icons.md)** , **[Imagen](control-image.md)** , **[Importar](control-export-import.md)** , **[Gráfico de líneas](control-text-box.md)** , **[Cuadro de lista](control-column-line-chart.md)** , **[Micrófono](control-list-box.md)** , **[Visor de PDF](control-microphone.md)** , **[Gráfico circular](control-pdf-viewer.md)** , **[Forma](control-pie-chart.md)** , **[Control deslizante](control-shapes-icons.md)** , **[Cuadro de texto](control-slider.md)** , **[Entrada de texto](control-text-input.md)** , **[Temporizador](control-timer.md)** y **[Alternancia](control-toggle.md)** .

**PressedColor**: el color de texto de un control cuando el usuario toca o hace clic en ese control.

- Se aplica a los controles **[Agregar imagen](control-add-picture.md)** , **[Botón](control-button.md)** , **[Casilla](control-check-box.md)** , **[Desplegable](control-drop-down.md)** , **[Exportar](control-export-import.md)** , **[Importar](control-export-import.md)** , **[Cuadro de lista](control-text-box.md)** , **[Micrófono](control-list-box.md)** , **[Radio](control-microphone.md)** , **[Cuadro de texto](control-radio.md)** , **[Entrada de texto](control-text-input.md)** y **[Temporizador](control-timer.md)** .

**PressedFill**: el color de fondo de un control cuando el usuario toca o hace clic en ese control.

- Se aplica a los controles **[Agregar imagen](control-add-picture.md)** , **[Botón](control-button.md)** , **[Casilla](control-check-box.md)** , **[Desplegable](control-drop-down.md)** , **[Exportar](control-export-import.md)** , **[Imagen](control-image.md)** , **[Importar](control-export-import.md)** , **[Cuadro de lista](control-text-box.md)** , **[Micrófono](control-list-box.md)** , **[Radio](control-microphone.md)** , **[Cuadro de texto](control-radio.md)** , **[Entrada de texto](control-text-input.md)** y **[Temporizador](control-timer.md)** .

## <a name="selection"></a>Selection

Estas propiedades tienen efecto cuando el usuario selecciona un elemento en un control.

**SelectionColor**: color del texto de los elementos seleccionados en una lista o de la herramienta de selección de un control de lápiz.

- Se aplica a los controles **[Drop down](control-drop-down.md)** , **[List Box](control-list-box.md)** y **[Pen input](control-pen-input.md)** .

**SelectionFill**: el color de fondo de uno o varios elementos seleccionados en una lista o un área seleccionada de un control de lápiz.

- Se aplica a los controles **[Drop down](control-drop-down.md)** y **[List Box](control-list-box.md)** .