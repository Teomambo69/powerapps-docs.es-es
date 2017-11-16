---
title: Propiedades de accesibilidad | Microsoft Docs
description: "Información de referencia acerca de propiedades como TabIndex y Tooltip"
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
ms.date: 01/26/2017
ms.author: anneta
ms.openlocfilehash: d8cc9d6c8586856dcaa27f67d3ea1fdc17fa0433
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="accessibility-properties-in-powerapps"></a>Propiedades de accesibilidad en PowerApps
## <a name="overview"></a>Información general
Configuración de propiedades que contribuyen a formas alternativas de interacción con los controles adecuados para los usuarios con discapacidades visuales.

## <a name="properties"></a>Propiedades
**Tooltip**: texto explicativo que aparece cuando el usuario mantiene el mouse sobre un control.  Este texto lo usan las etiquetas Aria que ayudan a los lectores de pantalla.

* Se aplica a los controles **[Audio](control-audio-video.md)**, **[Botón](control-button.md)**, **[Cámara](control-camera.md)**, **[Casilla](control-check-box.md)**, **[Lista desplegable](control-drop-down.md)**, **[Texto HTML](control-html-text.md)**, **[Imagen](control-image.md)**, **[Etiqueta](control-text-box.md)**, **[Cuadro de lista](control-list-box.md)**, **[Micrófono](control-microphone.md)**, **[Visor de PDF](control-pdf-viewer.md)**, **[Entrada manuscrita](control-pen-input.md)**, **[Botón de selección](control-radio.md)**, **[Clasificación](control-rating.md)**, **[Control deslizante](control-slider.md)**, **[Entrada de texto](control-text-input.md)**, **[Temporizador](control-timer.md)**, **[Alternar](control-toggle.md)** y **[Vídeo](control-audio-video.md)**.

**TabIndex**: personaliza el orden de tabulación de los controles en tiempo de ejecución.

El valor predeterminado cero especifica el orden de tabulación predeterminado, en función de la coordenada XY del control.  Establecer un valor mayor que cero moverá el orden de tabulación del control por delante de todos los controles con los valores predeterminados.  Un control con un valor TabIndex de 2 estará precedido por uno con un valor TabIndex de 3 o superior cuando se aplique la tabulación.

Tenga en cuenta que los contenedores como los controles Form y Gallery siempre tabularán todos los elementos del contenedor antes de continuar con los controles fuera del contenedor.  El orden de tabulación del contenedor es el valor más bajo de TabIndex de un control secundario.

Establecer TabIndex en -1 deshabilitará el acceso de la tabulación al control; en el caso de imágenes, iconos y formas, también serán invisibles para el lector de pantalla.

* Se aplica a los controles **[Button](control-button.md)**, **[Date Picker](control-date-picker.md)**, **[Drop down](control-drop-down.md)**, **[Image](control-image.md)**, **[Import](control-export-import.md)**, **[List Box](control-list-box.md)**, **[Radio](control-radio.md)**, **[Rating](control-rating.md)**, **[Slider](control-slider.md)**, **[Text input](control-text-input.md)** y **[Toggle](control-toggle.md)**.

