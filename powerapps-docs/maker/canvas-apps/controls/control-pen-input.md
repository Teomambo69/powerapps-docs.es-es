---
title: 'Control Entrada manuscrita: referencia | Microsoft Docs'
description: Información sobre el control Entrada manuscrita, con propiedades y ejemplos
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
ms.openlocfilehash: 7e5be9b68b501279329c23f9afe5d451487fa8d1
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="pen-input-control-in-powerapps"></a>Control Entrada manuscrita en PowerApps
Control con el que el usuario puede dibujar, borrar y resaltar áreas de una imagen.

## <a name="description"></a>Descripción
El usuario puede utilizar este control como una pizarra, dibujar diagramas y escribir palabras que se pueden convertir en texto mecanografiado.

## <a name="key-properties"></a>Propiedades principales
**[Color](properties-color-border.md)**: el color de los trazos de entrada.

**Modo**: el control se encuentra en modo **Dibujar** o **Borrar**.  El modo Seleccionar está en desuso.

## <a name="additional-properties"></a>Propiedades adicionales
**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**Input**: entrada.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**[ColorDeSelección](properties-color-border.md)**: color del texto de los elementos seleccionados en una lista o de la herramienta de selección de un control de entrada manuscrita.

**GrosorDeSelección**: grosor de la herramienta de selección de un control Entrada manuscrita.

**MostrarControles**: indica si se muestra un reproductor de audio o vídeo, por ejemplo, un botón de reproducción y un control deslizante de volumen, y un control de entrada manuscrita muestra, por ejemplo, iconos para dibujar, borrar y borrar todo.

**[Size](properties-text.md)**: el tamaño de la fuente del texto que aparece en un control.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**Recopilar**( *CollectionName*, *DatatoCollect* )](../functions/function-clear-collect-clearcollect.md)

## <a name="example"></a>Ejemplo
### <a name="create-a-set-of-images"></a>Crear un conjunto de imágenes
1. Agregue un control **Entrada manuscrita**, asígnele el nombre **MyDoodles** y establezca su propiedad **MostrarControles** en **true**.
   
    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
2. Agregue un control **[Botón](control-button.md)**, desplácelo bajo **MyDoodles** y establezca la propiedad **[Text](properties-core.md)** del control **[Botón](control-button.md)** para que muestre **Agregar**.
3. Establezca la propiedad **[AlSeleccionar](properties-core.md)** del control **[Botón](control-button.md)** en esta fórmula:<br>
   **Collect(Doodles, {Sketch:MyDoodles.Image})**
4. Agregue un control **Galería de imágenes**, desplácelo bajo el control **[Botón](control-button.md)** y reduzca el ancho del control **Galería de imágenes** hasta que muestre tres elementos.
5. Establezca la propiedad **[Elementos](properties-core.md)** del control **Galería de imágenes** en **Doodles** y presione F5.
6. Dibuje una imagen en **MyDoodles** y pulse o haga clic en el control **[Botón](control-button.md)**.
   
    La imagen que ha dibujado aparecerá en el control **Galería de imágenes**.
7. (opcional) En el control **Entrada manuscrita**, haga clic en o pulse el icono para borrar la imagen que ha dibujado, dibuje otra y pulse o haga clic en el control **[Botón](control-button.md)**.
8. En el control **Galería de imágenes**, establezca la propiedad  **[AlSeleccionar](properties-core.md)**  del control  **[Imagen](control-image.md)**  con la siguiente fórmula:<br>
   **Remove(Doodles, ThisItem)**
9. Pulse o haga clic en el control **Galería de imágenes** para eliminar un dibujo.

Use la función **[SaveData](../functions/function-savedata-loaddata.md)** para guardar los dibujos en el entorno local o la función **[Patch](../functions/function-patch.md)** para guardarlas en un origen de datos.

