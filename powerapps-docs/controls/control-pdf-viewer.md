---
title: 'Control Visor de archivos PDF: referencia | Microsoft Docs'
description: "Información sobre el control Visor de archivos PDF, con propiedades y ejemplos"
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
ms.openlocfilehash: c3ed17faae5963f71531b2fdc2ef9b08ee2569cc
ms.sourcegitcommit: c76ec82db5d261be1fb7fdeeec3e119cdfada57f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="pdf-viewer-control-experimental-in-powerapps"></a>Control Visor de archivos PDF (experimental) en PowerApps
Un control experimental que muestra el contenido de un archivo PDF.

## <a name="description"></a>Descripción
Muestre texto, gráficos y otro contenido en un archivo PDF mediante la incorporación de este tipo de control y estableciendo su propiedad **Documento** a la dirección URL, entre comillas dobles, del archivo que desea mostrar.

## <a name="limitations"></a>Limitaciones
Tenga en cuenta que, dada a la arquitectura de seguridad de PowerApps, el visor de PDF solo admite vínculos HTTPS, no HTTP.  
Si el documento PDF reside en un servidor con configuración de CORS con restricciones, es posible que no pueda verlo en su aplicación.  Para resolver este problema, es preciso que el servidor que hospeda los documentos PDF permita solicitudes de CORS procedentes de powerapps.com.

Si el documento no se puede abrir en PowerApps, se brinda al usuario final la posibilidad de abrirlo en un explorador externo.  Esta opción también está disponible en el menú de control para todos los documentos externos.

## <a name="key-properties"></a>Propiedades principales
**Documento**: la dirección URL entre comillas dobles, de un archivo PDF.

## <a name="additional-properties"></a>Propiedades adicionales
**ActualZoom**: el zoom real del control, que puede diferir del zoom solicitado con la propiedad **Ampliar**.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**CurrentFindText**: el término de búsqueda que está en uso en ese momento.

**CurrentPage**: el número de la página en un archivo PDF que se está mostrando en ese momento.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**FindNext**: busca la siguiente instancia de **FindText** en el documento.

**FindPrevious**: busca la instancia anterior de **FindText** en el documento.

**FindText**: el término de búsqueda para buscar en el documento.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**OnStateChange**: cómo una aplicación responde cuando cambia el estado del control.

**[RellenoInferior](properties-size-location.md)**: distancia entre el texto de un control y el borde inferior de ese control.

**[RellenoIzquierdo](properties-size-location.md)**: distancia entre el texto de un control y el borde izquierdo de ese control.

**[RellenoDerecho](properties-size-location.md)**: distancia entre el texto de un control y el borde derecho de ese control.

**[RellenoSuperior](properties-size-location.md)**: distancia entre el texto de un control y el borde superior de ese control.

**Página**: el número de la página que desea mostrar.

**PageCount**: el número de páginas en un documento.

**[PressedBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario toca o hace clic en ese control.

**MostrarControles**: indica si se muestra un reproductor de audio o vídeo, por ejemplo, un botón de reproducción y un control deslizante de volumen, y un control de entrada manuscrita muestra, por ejemplo, iconos para dibujar, borrar y borrar todo.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

**Zoom**: el porcentaje en que se amplía una imagen de una cámara o la vista de un archivo en un visor de PDF.

## <a name="example"></a>Ejemplo
* Agregue un control **Visor de archivos PDF** y establezca su propiedad **Documento** en la dirección URL, entre comillas dobles, de un archivo PDF, como en este ejemplo:<br>
  **"http://www.who.int/gho/publications/world_health_statistics/EN_WHS2015_TOC.pdf?ua=1"**

    El control mostrará el archivo PDF.

    ¿No sabe cómo [agregar y configurar un control](../add-configure-controls.md)?
