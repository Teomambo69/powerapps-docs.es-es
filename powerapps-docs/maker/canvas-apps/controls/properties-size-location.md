---
title: Propiedades de tamaño y ubicación | Microsoft Docs
description: Material de referencia de propiedades como Height y Width
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 10/25/2016
ms.author: gregli
ms.openlocfilehash: 7df2782bc18d1c999383226e31033035fb59cea1
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="size-and-location-properties-in-powerapps"></a>Propiedades de tamaño y ubicación en PowerApps
## <a name="overview"></a>Información general
Configure el tamaño de un control (o un elemento de control) y dónde se encuentra en relación con la pantalla en la que está.

## <a name="position"></a>Posición
**X**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario). Para un control **[Tarjeta](control-card.md)** en un contenedor con varias columnas, esta propiedad determina la columna en la que aparece la tarjeta.

* Se aplica a los controles **[Agregar imagen](control-add-picture.md)**, **[Audio](control-audio-video.md)**, **[Botón](control-button.md)**, **[Cámara](control-camera.md)**, **[Tarjeta](control-card.md)**, **[Casilla](control-check-box.md)**, **[Gráfico de columnas](control-column-line-chart.md)**, **[Selector de fecha](control-date-picker.md)**, **[Formulario de presentación](control-form-detail.md)**, **[Lista desplegable](control-drop-down.md)**, **[Formulario de edición](control-form-detail.md)**, **[Exportar](control-export-import.md)**, **[Galería](control-gallery.md)**, **[Texto HTML](control-html-text.md)**, **[Icono](control-shapes-icons.md)**, **[Imagen](control-image.md)**, **[Importar](control-export-import.md)**, **[Etiqueta](control-text-box.md)**, **[Gráfico de líneas](control-column-line-chart.md)**, **[Cuadro de lista](control-list-box.md)**, **[Micrófono](control-microphone.md)**, **[Visor de PDF](control-pdf-viewer.md)**, **[Entrada manuscrita](control-pen-input.md)**, **[Gráfico circular](control-pie-chart.md)**, **[Botón de selección](control-radio.md)**, **[Clasificación](control-rating.md)**, **[Forma](control-shapes-icons.md)**, **[Control deslizante](control-slider.md)**, **[Entrada de texto](control-text-input.md)**, **[Temporizador](control-timer.md)**, **[Alternar](control-toggle.md)** y **[Vídeo](control-audio-video.md)**.

**Y**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario). Para un control **[Tarjeta](control-card.md)** en un contenedor con varias filas, esta propiedad determina la fila en la que aparece la tarjeta.

* Se aplica a los controles **[Agregar imagen](control-add-picture.md)**, **[Audio](control-audio-video.md)**, **[Botón](control-button.md)**, **[Cámara](control-camera.md)**, **[Tarjeta](control-card.md)**, **[Casilla](control-check-box.md)**, **[Gráfico de columnas](control-column-line-chart.md)**, **[Selector de fecha](control-date-picker.md)**, **[Formulario de presentación](control-form-detail.md)**, **[Lista desplegable](control-drop-down.md)**, **[Formulario de edición](control-form-detail.md)**, **[Exportar](control-export-import.md)**, **[Galería](control-gallery.md)**, **[Texto HTML](control-html-text.md)**, **[Icono](control-shapes-icons.md)**, **[Imagen](control-image.md)**, **[Importar](control-export-import.md)**, **[Etiqueta](control-text-box.md)**, **[Gráfico de líneas](control-column-line-chart.md)**, **[Cuadro de lista](control-list-box.md)**, **[Micrófono](control-microphone.md)**, **[Visor de PDF](control-pdf-viewer.md)**, **[Entrada manuscrita](control-pen-input.md)**, **[Gráfico circular](control-pie-chart.md)**, **[Botón de selección](control-radio.md)**, **[Clasificación](control-rating.md)**, **[Forma](control-shapes-icons.md)**, **[Control deslizante](control-slider.md)**, **[Entrada de texto](control-text-input.md)**, **[Temporizador](control-timer.md)**, **[Alternar](control-toggle.md)** y **[Vídeo](control-audio-video.md)**.

## <a name="size"></a>Tamaño
**Height**: la distancia entre los bordes superior e inferior de un control.

* Se aplica a los controles **[Agregar imagen](control-add-picture.md)**, **[Audio](control-audio-video.md)**, **[Botón](control-button.md)**, **[Cámara](control-camera.md)**, **[Tarjeta](control-card.md)**, **[Casilla](control-check-box.md)**, **[Gráfico de columnas](control-column-line-chart.md)**, **[Selector de fecha](control-date-picker.md)**, **[Formulario de presentación](control-form-detail.md)**, **[Lista desplegable](control-drop-down.md)**, **[Formulario de edición](control-form-detail.md)**, **[Exportar](control-export-import.md)**, **[Galería](control-gallery.md)**, **[Texto HTML](control-html-text.md)**, **[Icono](control-shapes-icons.md)**, **[Imagen](control-image.md)**, **[Importar](control-export-import.md)**, **[Etiqueta](control-text-box.md)**, **[Gráfico de líneas](control-column-line-chart.md)**, **[Cuadro de lista](control-list-box.md)**, **[Micrófono](control-microphone.md)**, **[Visor de PDF](control-pdf-viewer.md)**, **[Entrada manuscrita](control-pen-input.md)**, **[Gráfico circular](control-pie-chart.md)**, **[Botón de selección](control-radio.md)**, **[Clasificación](control-rating.md)**, **[Forma](control-shapes-icons.md)**, **[Control deslizante](control-slider.md)**, **[Entrada de texto](control-text-input.md)**, **[Temporizador](control-timer.md)**, **[Alternar](control-toggle.md)** y **[Vídeo](control-audio-video.md)**.

**AutoHeight** (AlturaAutomática): indica si una etiqueta aumenta automáticamente su altura si su propiedad **[Texto](properties-core.md)** contiene más caracteres de los que el control permite mostrar.  

* Se aplica a **[Etiqueta](control-text-box.md)**

**Width**: la distancia entre los bordes derecho e izquierdo de un control.

* Se aplica a los controles **[Agregar imagen](control-add-picture.md)**, **[Audio](control-audio-video.md)**, **[Botón](control-button.md)**, **[Cámara](control-camera.md)**, **[Tarjeta](control-card.md)**, **[Casilla](control-check-box.md)**, **[Gráfico de columnas](control-column-line-chart.md)**, **[Selector de fecha](control-date-picker.md)**, **[Formulario de presentación](control-form-detail.md)**, **[Lista desplegable](control-drop-down.md)**, **[Formulario de edición](control-form-detail.md)**, **[Exportar](control-export-import.md)**, **[Galería](control-gallery.md)**, **[Texto HTML](control-html-text.md)**, **[Icono](control-shapes-icons.md)**, **[Imagen](control-image.md)**, **[Etiqueta](control-text-box.md)**, **[Importar](control-export-import.md)**, **[Gráfico de líneas](control-column-line-chart.md)**, **[Cuadro de lista](control-list-box.md)**, **[Micrófono](control-microphone.md)**, **[Visor de PDF](control-pdf-viewer.md)**, **[Entrada manuscrita](control-pen-input.md)**, **[Gráfico circular](control-pie-chart.md)**, **[Botón de selección](control-radio.md)**, **[Clasificación](control-rating.md)**, **[Forma](control-shapes-icons.md)**, **[Control deslizante](control-slider.md)**, **[Entrada de texto](control-text-input.md)**, **[Temporizador](control-timer.md)**, **[Alternar](control-toggle.md)** y **[Vídeo](control-audio-video.md)**.

**WidthFit** (AjusteDeAncho): indica si un control crece automáticamente en la horizontal para llenar el espacio vacío de un control de contenedor, como un control **[Formulario de edición](control-form-detail.md)**. Si varias tarjetas tienen esta propiedad establecida en **true**, el espacio se divide entre ellas. Para más información, consulte [Understand data form layout in Microsoft PowerApps](../working-with-form-layout.md) (Introducción al diseño de formularios de datos en Microsoft PowerApps).

* Se aplica a **[Tarjeta](control-card.md)**

## <a name="padding"></a>Relleno
**Padding**: la distancia entre el texto de un botón Exportar o Importar y los bordes de ese botón.

* Se aplica a los controles **[Add picture](control-add-picture.md)**, **[Export](control-export-import.md)** y **[Import](control-export-import.md)**.

**PaddingBottom**: distancia entre el texto de un control y el borde inferior de ese control.

* Se aplica a los controles **[Botón](control-button.md)**, **[Casilla](control-check-box.md)**, **[Gráfico de columnas](control-column-line-chart.md)**, **[Selector de fecha](control-date-picker.md)**, **[Lista desplegable](control-drop-down.md)**, **[Texto HTML](control-html-text.md)**, **[Imagen](control-image.md)**, **[Gráfico de líneas](control-text-box.md)**, **[Cuadro de lista](control-column-line-chart.md)**, **[Visor de PDF](control-list-box.md)**, **[Botón de selección](control-pdf-viewer.md)**, **[Cuadro de texto](control-radio.md)** y **[Entrada de texto](control-text-input.md)**.

**PaddingLeft**: distancia entre el texto de un control y el borde izquierdo de ese control.

* Se aplica a los controles **[Botón](control-button.md)**, **[Casilla](control-check-box.md)**, **[Gráfico de columnas](control-column-line-chart.md)**, **[Selector de fecha](control-date-picker.md)**, **[Lista desplegable](control-drop-down.md)**, **[Texto HTML](control-html-text.md)**, **[Imagen](control-image.md)**, **[Gráfico de líneas](control-text-box.md)**, **[Cuadro de lista](control-column-line-chart.md)**, **[Visor de PDF](control-list-box.md)**, **[Botón de selección](control-pdf-viewer.md)**, **[Cuadro de texto](control-radio.md)** y **[Entrada de texto](control-text-input.md)**.

**PaddingRight**: distancia entre el texto de un control y el borde derecho de ese control.

* Se aplica a los controles **[Botón](control-button.md)**, **[Casilla](control-check-box.md)**, **[Gráfico de columnas](control-column-line-chart.md)**, **[Selector de fecha](control-date-picker.md)**, **[Lista desplegable](control-drop-down.md)**, **[Texto HTML](control-html-text.md)**, **[Imagen](control-image.md)**, **[Gráfico de líneas](control-text-box.md)**, **[Cuadro de lista](control-column-line-chart.md)**, **[Visor de PDF](control-list-box.md)**, **[Botón de selección](control-pdf-viewer.md)**, **[Cuadro de texto](control-radio.md)** y **[Entrada de texto](control-text-input.md)**.

**PaddingTop**: distancia entre el texto de un control y el borde superior de ese control.

* Se aplica a los controles **[Botón](control-button.md)**, **[Casilla](control-check-box.md)**, **[Gráfico de columnas](control-column-line-chart.md)**, **[Selector de fecha](control-date-picker.md)**, **[Lista desplegable](control-drop-down.md)**, **[Texto HTML](control-html-text.md)**, **[Imagen](control-image.md)**, **[Gráfico de líneas](control-text-box.md)**, **[Cuadro de lista](control-column-line-chart.md)**, **[Visor de PDF](control-list-box.md)**, **[Botón de selección](control-pdf-viewer.md)**, **[Cuadro de texto](control-radio.md)** y **[Entrada de texto](control-text-input.md)**.

## <a name="radius"></a>Radio
**RadiusBottomLeft**: el grado al que se redondea la esquina inferior izquierda de un control.

* Se aplica a los controles **[Button](control-button.md)**, **[Export](control-export-import.md)**, **[Image](control-image.md)**, **[Import](control-export-import.md)** y **[Text input](control-text-input.md)**.

**RadiusBottomRight**: el grado al que se redondea la esquina inferior derecha de un control.

* Se aplica a los controles **[Button](control-button.md)**, **[Export](control-export-import.md)**, **[Image](control-image.md)**, **[Import](control-export-import.md)** y **[Text input](control-text-input.md)**.

**RadiusTopLeft**: el grado al que se redondea la esquina superior izquierda de un control.

* Se aplica a los controles **[Button](control-button.md)**, **[Export](control-export-import.md)**, **[Image](control-image.md)**, **[Import](control-export-import.md)** y **[Text input](control-text-input.md)**.

**RadiusTopRight**: el grado al que se redondea la esquina superior derecha de un control.

* Se aplica a los controles **[Button](control-button.md)**, **[Export](control-export-import.md)**, **[Image](control-image.md)**, **[Import](control-export-import.md)** y **[Text input](control-text-input.md)**.

