---
title: Propiedades principales | Microsoft Docs
description: Información de referencia acerca de las propiedades Disabled, Visible y ReadOnly
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: gregli
ms.openlocfilehash: 98a8e22e4101c1c151fa197e967d21942041bef4
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39015165"
---
# <a name="core-properties-in-powerapps"></a>Propiedades principales en PowerApps
Configure la posibilidad de que el usuario puede ver un control e interactuar con él.

### <a name="properties"></a>Propiedades
**Default**: el valor inicial de un control antes de que lo cambie el usuario.

* Se aplica a los controles **[Tarjeta](control-card.md)**, **[Casilla](control-check-box.md)**, **[Desplegable](control-drop-down.md)**, **[Galería](control-gallery.md)**, **[Cuadro de lista](control-list-box.md)**, **[Radio](control-radio.md)**, **[Clasificación](control-rating.md)**, **[Control deslizante](control-slider.md)**, **[Entrada de texto](control-text-input.md)** y **[Alternancia](control-toggle.md)**.

**DelayOutput**: establézcalo en true para retrasar la acción durante la entrada de texto.

* Se aplica a **[Text input](control-text-input.md)** y **[Card](control-card.md)**.

**DisplayMode**: los valores pueden ser **Edit, View** o **Disabled**. Configura si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).  En el modo **View**, los controles de entrada como **[Entrada de texto](control-text-input.md)**, **[Lista desplegable](control-drop-down.md)** y **[Selector de fecha](control-date-picker.md)** solo mostrarán el valor del texto y no representarán ninguna otra decoración ni elemento interactivo.  Esto hace que sean adecuados para mostrarse en formularios o en forma de salida legible.

* Se aplica a los controles **[Agregar imagen](control-add-picture.md)**, **[Audio](control-audio-video.md)**, **[Botón](control-button.md)**, **[Cámara](control-camera.md)**, **[Casilla](control-check-box.md)**, **[Gráfico de columnas](control-column-line-chart.md)**, **[Selector de fecha](control-date-picker.md)**, **[Lista desplegable](control-drop-down.md)**, **[Exportar](control-export-import.md)**, **[Galería](control-gallery.md)**, **[Texto HTML](control-html-text.md)**, **[Icono](control-shapes-icons.md)**, **[Imagen](control-image.md)**, **[Importar](control-export-import.md)**, **[Etiqueta](control-text-box.md)**, **[Gráfico de líneas](control-column-line-chart.md)**, **[Cuadro de lista](control-list-box.md)**, **[Micrófono](control-microphone.md)**, **[Visor de PDF](control-pdf-viewer.md)**, **[Entrada manuscrita](control-pen-input.md)**, **[Gráfico circular](control-pie-chart.md)**, **[Botón de selección](control-radio.md)**, **[Clasificación](control-rating.md)**, **[Forma](control-shapes-icons.md)**, **[Control deslizante](control-slider.md)**, **[Entrada de texto](control-text-input.md)**, **[Temporizador](control-timer.md)**, **[Alternar](control-toggle.md)** y **[Vídeo](control-audio-video.md)**.

**Items**: origen de datos que aparece en un control como una galería, una lista o un gráfico.

* Se aplica a los controles **[Column chart](control-column-line-chart.md)**, **[Drop down](control-drop-down.md)**, **[Gallery](control-gallery.md)**, **[Line chart](control-column-line-chart.md)**, **[List Box](control-list-box.md)**, **[Pie chart](control-pie-chart.md)** y **[Radio](control-radio.md)**.

**OnChange**: indica cómo responde la aplicación cuando el usuario cambia el valor de un control (por ejemplo, mediante el ajuste de un control deslizante).

* Se aplica a los controles **[Add picture](control-add-picture.md)**, **[Drop down](control-drop-down.md)**, **[List Box](control-list-box.md)**, **[Radio](control-radio.md)**, **[Rating](control-rating.md)**, **[Slider](control-slider.md)**, **[Text input](control-text-input.md)** y **[Toggle](control-toggle.md)**.

**OnSelect**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

* Se aplica a los controles **[Agregar imagen](control-add-picture.md)**, **[Botón](control-button.md)**, **[Cámara](control-camera.md)**, **[Casilla](control-check-box.md)**, **[Gráfico de columnas](control-column-line-chart.md)**, **[Selector de fecha](control-date-picker.md)**, **[Lista desplegable](control-drop-down.md)**, **[Exportar](control-export-import.md)**, **[Texto HTML](control-html-text.md)**, **[Icono](control-shapes-icons.md)**, **[Imagen](control-image.md)**, **[Importar](control-export-import.md)**, **[Etiqueta](control-text-box.md)**, **[Gráfico de líneas](control-column-line-chart.md)**, **[Cuadro de lista](control-list-box.md)**, **[Micrófono](control-microphone.md)**, **[Visor de PDF](control-pdf-viewer.md)**, **[Entrada manuscrita](control-pen-input.md)**, **[Gráfico circular](control-pie-chart.md)**, **[Botón de selección](control-radio.md)**, **[Clasificación](control-rating.md)**, **[Forma](control-shapes-icons.md)**, **[Control deslizante](control-slider.md)**, **[Entrada de texto](control-text-input.md)**, **[Temporizador](control-timer.md)** y **[Alternar](control-toggle.md)**.

**Reset**: indica si un control vuelve a su valor predeterminado.  Consulte también la función **[Reset](../functions/function-reset.md)**.

* Se aplica a los controles **[Audio](control-audio-video.md)**, **[Check box](control-check-box.md)**, **[Drop down](control-drop-down.md)**, **[List Box](control-list-box.md)**, **[Microphone](control-microphone.md)**, **[Radio](control-radio.md)**, **[Rating](control-rating.md)**, **[Slider](control-slider.md)**, **[Text input](control-text-input.md)**, **[Timer](control-timer.md)**, **[Toggle](control-toggle.md)** y **[Video](control-audio-video.md)**.

**Text**: texto que aparece en un control o que el usuario escribe en un control.

* Se aplica a los controles **[Agregar imagen](control-add-picture.md)**, **[Botón](control-button.md)**, **[Casilla](control-check-box.md)**, **[Exportar](control-export-import.md)**, **[Importar](control-export-import.md)**, **[Etiqueta](control-text-box.md)**, **[Entrada de texto](control-text-input.md)** y **[Temporizador](control-timer.md)**.

**Tooltip**: texto explicativo que aparece cuando el usuario mantiene el mouse sobre un control.

* Se aplica a los controles **[Audio](control-audio-video.md)**, **[Botón](control-button.md)**, **[Cámara](control-camera.md)**, **[Casilla](control-check-box.md)**, **[Lista desplegable](control-drop-down.md)**, **[Texto HTML](control-html-text.md)**, **[Imagen](control-image.md)**, **[Etiqueta](control-text-box.md)**, **[Cuadro de lista](control-list-box.md)**, **[Micrófono](control-microphone.md)**, **[Visor de PDF](control-pdf-viewer.md)**, **[Entrada manuscrita](control-pen-input.md)**, **[Botón de selección](control-radio.md)**, **[Clasificación](control-rating.md)**, **[Control deslizante](control-slider.md)**, **[Entrada de texto](control-text-input.md)**, **[Temporizador](control-timer.md)**, **[Alternar](control-toggle.md)** y **[Vídeo](control-audio-video.md)**.

**Value**: el valor de un control de entrada.

* Se aplica a los controles **[Check box](control-check-box.md)**, **[Radio](control-radio.md)**, **[Slider](control-slider.md)** y **[Toggle](control-toggle.md)**.

**Visible**: indica si un control aparece o está oculto.

* Se aplica a los controles **[Agregar imagen](control-add-picture.md)**, **[Audio](control-audio-video.md)**, **[Botón](control-button.md)**, **[Cámara](control-camera.md)**, **[Tarjeta](control-card.md)**, **[Casilla](control-check-box.md)**, **[Gráfico de columnas](control-column-line-chart.md)**, **[Selector de fecha](control-date-picker.md)**, **[Formulario de presentación](control-form-detail.md)**, **[Lista desplegable](control-drop-down.md)**, **[Formulario de edición](control-form-detail.md)**, **[Exportar](control-export-import.md)**, **[Galería](control-gallery.md)**, **[Texto HTML](control-html-text.md)**, **[Icono](control-shapes-icons.md)**, **[Imagen](control-image.md)**, **[Importar](control-export-import.md)**, **[Etiqueta](control-text-box.md)**, **[Gráfico de líneas](control-column-line-chart.md)**, **[Cuadro de lista](control-list-box.md)**, **[Micrófono](control-microphone.md)**, **[Visor de PDF](control-pdf-viewer.md)**, **[Entrada manuscrita](control-pen-input.md)**, **[Gráfico circular](control-pie-chart.md)**, **[Botón de selección](control-radio.md)**, **[Clasificación](control-rating.md)**, **[Forma](control-shapes-icons.md)**, **[Control deslizante](control-slider.md)**, **[Entrada de texto](control-text-input.md)**, **[Temporizador](control-timer.md)**, **[Alternar](control-toggle.md)** y **[Vídeo](control-audio-video.md)**.

