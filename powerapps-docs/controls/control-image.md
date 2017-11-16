---
title: 'Control Imagen: referencia | Microsoft Docs'
description: "Información sobre el control Imagen, con propiedades y ejemplos"
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
ms.openlocfilehash: 5bf844e4debf7b4614fafe948a6ec15943fd35f5
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="image-control-in-powerapps"></a>Control Imagen en PowerApps
Un control que muestra una imagen desde, por ejemplo, un archivo local o un origen de datos.

## <a name="description"></a>Descripción
Si agrega uno o varios controles **Imagen** controles a la aplicación, puede mostrar imágenes individuales que no forman parte de un conjunto de datos, o puede incorporar imágenes desde registros de orígenes de datos.

## <a name="key-properties"></a>Propiedades principales
**[Imagen](properties-visual.md)**: el nombre de la imagen que aparece en un control de imagen, audio o micrófono.

## <a name="additional-properties"></a>Propiedades adicionales
**AutoDisableOnSelect**: deshabilita automáticamente el control mientras se ejecuta el comportamiento AlSeleccionar.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[FocusedBorderThickness](properties-color-border.md)**: grosor del borde del control cuando se resalta el teclado.

**CalculateOriginalDimensions**: habilita las propiedades **AltoOriginal** y **AnchoOriginal**.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[DisabledFill](properties-color-border.md)**: el color de fondo de un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**[HoverFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[PosiciónDeLaImagen](properties-visual.md)**: posición (**Rellenar**, **Ajustar**, **Estirar**, **Icono** o **Centrar**) de una imagen en una pantalla o un control, si no tiene el mismo tamaño que la imagen.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**AltoOriginal**: la altura original de una imagen, habilitada con la propiedad **CalculateOriginalDimensions**.

**AnchoOriginal**: el ancho original de una imagen, habilitada con la propiedad **CalculateOriginalDimensions**.

**[RellenoInferior](properties-size-location.md)**: distancia entre el texto de un control y el borde inferior de ese control.

**[RellenoIzquierdo](properties-size-location.md)**: distancia entre el texto de un control y el borde izquierdo de ese control.

**[RellenoDerecho](properties-size-location.md)**: distancia entre el texto de un control y el borde derecho de ese control.

**[RellenoSuperior](properties-size-location.md)**: distancia entre el texto de un control y el borde superior de ese control.

**[PressedBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario toca o hace clic en ese control.

**[PressedFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario toca o hace clic en ese control.

**[RadiusBottomLeft](properties-size-location.md)**: el grado al que se redondea la esquina inferior izquierda de un control.

**[RadiusBottomRight](properties-size-location.md)**: el grado al que se redondea la esquina inferior derecha de un control.

**[RadiusTopLeft](properties-size-location.md)**: el grado al que se redondea la esquina superior izquierda de un control.

**[RadiusTopRight](properties-size-location.md)**: el grado al que se redondea la esquina superior derecha de un control.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**Transparencia**: el grado en el los controles permanecen visibles detrás de una imagen.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**Quitar**( *DataSource*, EsteElemento)](../functions/function-remove-removeif.md)

## <a name="examples"></a>Ejemplos
### <a name="show-an-image-from-a-local-file"></a>Mostrar una imagen desde un archivo local
1. En la pestaña **Contenido**, pulse o haga clic en **Multimedia** y, a continuación, en **Examinar**.
2. Pulse o haga clic en el archivo de imagen que desea agregar, pulse o haga clic en **Abrir**, y, a continuación, presione Esc para volver al área de trabajo predeterminada.
3. Agregue un control **Imagen**, establezca la propiedad de sus **[Artículos](properties-core.md)** en el nombre del archivo que agregó.
   
    ¿No sabe cómo [agregar y configurar un control](../add-configure-controls.md)?
   
    El control **Imagen** muestra la imagen que ha especificado.

### <a name="show-a-set-of-images-from-a-data-source"></a>Mostrar un conjunto de imágenes desde un origen de datos
1. Descargue este [archivo de Excel](https://pwrappssamples.blob.core.windows.net/samples/FlooringEstimates.xlsx)y guárdelo en el dispositivo local.
2. En PowerApps Studio, cree o abra una aplicación y, a continuación, haga clic o pulse **Agregar origen de datos** en el panel derecho.
   
    Si **Agregar origen de datos** no aparece en el panel de la derecha, pulse o haga clic en la barra de navegación izquierda de una pantalla.
3. Pulse o haga clic en **Agregar datos estáticos a la aplicación**, pulse o haga clic en el archivo de Excel que descargó y, a continuación en **Abrir**.
4. Seleccione la casilla **Flooring Estimates** y a continuación, pulse o haga clic en **Conectar**.
5. Agregue un control **Galería** con imágenes y establezca su propiedad **[Artículos](properties-core.md)** en **FlooringEstimates**.
   
    ¿No sabe cómo [agregar y configurar un control](../add-configure-controls.md)?
   
    El control **Galería** muestra imágenes de productos de moqueta, parquet y mosaico basados en vínculos en el archivo de Excel que ha descargado.

