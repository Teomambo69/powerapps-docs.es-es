---
title: 'Control Agregar imagen: referencia | Microsoft Docs'
description: Información sobre el control Agregar imagen, con propiedades y ejemplos
services: ''
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: 6a7c60755f5623803d20bec4ec9881108b1116c6
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="add-picture-control-in-powerapps"></a>Control Agregar imagen en PowerApps
Toma una fotografía o carga imágenes desde el dispositivo local.

## <a name="description"></a>Descripción
Con este control los usuarios pueden tomar fotografías o cargar archivos de imagen desde su dispositivo y actualizar el origen de datos con este contenido. En un dispositivo móvil se presenta al usuario el cuadro de diálogo de elección del dispositivo para que elija entre tomar una foto o seleccionar una ya disponible.

Este control es un control compuesto, formado por dos controles.  Presione o pulse una vez para seleccionar el control externo que muestra la imagen que se ha cargado.  Presione o pulse de nuevo para seleccionar el control de etiqueta interno.

## <a name="outer-control-properties"></a>Propiedades del control externo
Estas propiedades se aplican al control externo.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[DisabledFill](properties-color-border.md)**: el color de fondo de un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**Error**: si hay un problema al cargar una imagen, esta propiedad contendrá una cadena de error apropiada.

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**[HoverFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

**Multimedia**: un identificador de la secuencia que reproduce un control de audio o de vídeo.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**[PressedBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario toca o hace clic en ese control.

**[PressedFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario toca o hace clic en ese control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="inner-text-properties"></a>Propiedades del texto interno
Estas propiedades se aplican al control de etiqueta interno que dice de forma predeterminada "Pulse o haga clic para agregar una imagen".  Para seleccionar este control interno, presione o pulse el control **Agregar imagen** una vez y, luego, otra.

**[Align](properties-text.md)**: la ubicación del texto respecto al centro horizontal de su control.

**[Color](properties-color-border.md)**: el color del texto en un control.

**[DisabledColor](properties-color-border.md)**: el color del texto en un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[Font](properties-text.md)**: el nombre de la familia de fuentes en la que aparece el texto.

**[FontWeight](properties-text.md)**: el peso del texto en un control: **Bold**, **Semibold**, **Normal** o **Lighter**.

**[HoverColor](properties-color-border.md)**: el color del texto de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[Italic](properties-text.md)**: indica si el texto de un control está en cursiva.

**[AlCambiar](properties-core.md)**: indica cómo responde la aplicación cuando el usuario cambia el valor de un control (por ejemplo, mediante el ajuste de un control deslizante).

**[Padding](properties-size-location.md)**: la distancia entre el texto de un botón Exportar o Importar y los bordes de ese botón.

**[PressedColor](properties-color-border.md)**: el color de texto de un control cuando el usuario toca o hace clic en ese control.

**[Size](properties-text.md)**: el tamaño de la fuente del texto que aparece en un control.

**[Strikethrough](properties-text.md)**: indica si aparece una línea sobre el texto de un control.

**[Text](properties-core.md)**: texto que aparece en un control o que el usuario escribe en un control.

**[Underline](properties-text.md)**: indica si aparece una línea debajo del texto de un control.

**[VerticalAlign](properties-text.md)**: la ubicación del texto en un control respecto al centro vertical de ese control.

## <a name="related-functions"></a>Funciones relacionadas
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>Ejemplo
### <a name="add-images-to-an-image-gallery-control"></a>Agregar imágenes a un control Galería de imágenes
1. Agregue un control **Agregar imagen** y, a continuación, haga clic en él tres veces.
   
    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
2. En el cuadro de diálogo **Abrir**, pulse o haga clic en un archivo de imagen y luego pulse o haga clic en **Abrir**.
3. Agregue un control **[Botón](control-button.md)**, muévalo al control **Agregar imagen** y establezca la propiedad **[AlSeleccionar](properties-core.md)** del control **[Botón](control-button.md)** en esta fórmula:<br>
   **Collect(MyPix, AddMediaButton1.Media)**
   
    ¿Desea más información sobre la función **[Recopilar](../functions/function-clear-collect-clearcollect.md)** u [otras funciones](../formula-reference.md)?
4. Agregue un control **Galería de imágenes** y establezca su propiedad **[Elementos](properties-core.md)** en **MyPix**.
5. Presione F5 y pulse o haga clic en el control **[Botón](control-button.md)**.
   
    La imagen del control **Agregar imagen** aparece en el control **Galería de imágenes**. Si la imagen no tiene la misma relación de aspecto que el control **[Imagen](control-image.md)** del control **Galería de imágenes**, establezca la propiedad **[PosiciónDeLaImagen](properties-visual.md)** del control **[Imagen](control-image.md)** en **Ajustar**.
6. Pulse o haga clic en el control **Agregar imagen**, pulse o haga clic en **Abrir** y luego pulse o haga clic en el control **[Botón](control-button.md)** que agregó.
   
    La segunda imagen aparece en el control **Galería de imágenes**.
7. (opcional) Repita el paso anterior una o más veces y, a continuación, presione Esc para volver al área de trabajo predeterminada.

Use la función **[SaveData](../functions/function-savedata-loaddata.md)** para guardar las imágenes localmente o la función **[Patch](../functions/function-patch.md)** para actualizar el origen de datos.

