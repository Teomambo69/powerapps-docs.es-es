---
title: 'Control Entrada manuscrita: referencia | Microsoft Docs'
description: Información sobre el control Entrada manuscrita, con propiedades y ejemplos
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1600f765e40849b47cb41b29c5d4c3fab86b4caf
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993379"
---
# <a name="pen-input-control-in-powerapps"></a>Control Entrada manuscrita en PowerApps
Control con el que el usuario puede dibujar, borrar y resaltar áreas de una imagen.

## <a name="description"></a>Descripción
El usuario puede utilizar este control como una pizarra, dibujar diagramas y escribir palabras que se pueden convertir en texto mecanografiado.

## <a name="key-properties"></a>Propiedades principales
**Imagen**: propiedad de salida que representa la imagen dibujada por el usuario final.

**[Color](properties-color-border.md)** : el color de los trazos de entrada.

**Modo**: el control se encuentra en modo **Dibujar** o **Borrar**.  El modo Seleccionar está en desuso.

## <a name="additional-properties"></a>Propiedades adicionales
**[AccessibleLabel](properties-accessibility.md)** : etiqueta para lectores de pantalla. Puede utilizarse para describir el propósito del control, así como métodos de entrada alternativos.

**[BorderColor](properties-color-border.md)** : el color de un borde del control.

**[BorderStyle](properties-color-border.md)** : si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)** : el grosor de un borde del control.

**[DisplayMode](properties-core.md)** : indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[Fill](properties-color-border.md)** : el color de fondo de un control.

**[Height](properties-size-location.md)** : la distancia entre los bordes superior e inferior de un control.

**Input**: **en desuso**. Si la entrada admite entradas de mouse, lápiz o táctiles.  El valor predeterminado (7) admite las tres.

**[OnSelect](properties-core.md)** : indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**[ColorDeSelección](properties-color-border.md)** : color del texto de los elementos seleccionados en una lista o de la herramienta de selección de un control de entrada manuscrita.

**GrosorDeSelección**: grosor de la herramienta de selección de un control Entrada manuscrita.

**MostrarControles**: indica si se muestra un reproductor de audio o vídeo, por ejemplo, un botón de reproducción y un control deslizante de volumen, y un control de entrada manuscrita muestra, por ejemplo, iconos para dibujar, borrar y borrar todo.

**[Size](properties-text.md)** : el tamaño de la fuente del texto que aparece en un control.

**[Información sobre herramientas](properties-core.md)** : texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Visible](properties-core.md)** : indica si un control aparece o está oculto.

**[Width](properties-size-location.md)** : la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)** : la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)** : la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**Recopilar**( *CollectionName*, *DatatoCollect* )](../functions/function-clear-collect-clearcollect.md)

## <a name="example"></a>Ejemplo
### <a name="create-a-set-of-images"></a>Crear un conjunto de imágenes
1. Agregue un control **Entrada manuscrita**, asígnele el nombre **MyDoodles** y establezca su propiedad **MostrarControles** en **true**.
   
    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
2. Agregue un control **[Botón](control-button.md)** , desplácelo bajo **MyDoodles** y establezca la propiedad **[Text](properties-core.md)** del control **[Botón](control-button.md)** para que muestre **Agregar**.
3. Establezca la propiedad **[AlSeleccionar](properties-core.md)** del control **[Botón](control-button.md)** en esta fórmula:<br>
   **Collect(Doodles, {Sketch:MyDoodles.Image})**
4. Agregue un control **Galería de imágenes**, desplácelo bajo el control **[Botón](control-button.md)** y reduzca el ancho del control **Galería de imágenes** hasta que muestre tres elementos.
5. Establezca la propiedad **[Elementos](properties-core.md)** del control **Galería de imágenes** en **Doodles** y presione F5.
6. Dibuje una imagen en **MyDoodles** y pulse o haga clic en el control **[Botón](control-button.md)** .
   
    La imagen que ha dibujado aparecerá en el control **Galería de imágenes**.
7. (opcional) En el control **Entrada manuscrita**, haga clic en o pulse el icono para borrar la imagen que ha dibujado, dibuje otra y pulse o haga clic en el control **[Botón](control-button.md)** .
8. En el control **Galería de imágenes**, establezca la propiedad **[AlSeleccionar](properties-core.md)** del control **[Imagen](control-image.md)** con la siguiente fórmula:<br>
   **Remove(Doodles, ThisItem)**
9. Pulse o haga clic en el control **Galería de imágenes** para eliminar un dibujo.

Use la función **[SaveData](../functions/function-savedata-loaddata.md)** para guardar los dibujos en el entorno local o la función **[Patch](../functions/function-patch.md)** para guardarlas en un origen de datos.


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="color-contrast"></a>Contraste de color
Debe haber un contraste de color adecuado entre:
* **[BorderColor](properties-color-border.md)** y el color situado fuera del control (si hay un borde)
* **[Fill](properties-color-border.md)** y el color situado fuera del control (si no hay un borde)

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* La propiedad **[AccessibleLabel](properties-accessibility.md)** debe existir.

    > [!IMPORTANT]
  > El control **Entrada manuscrita** no es accesible para los usuarios de lector de pantalla. Proporcione siempre una forma de entrada alternativa. Por ejemplo, si se requiere un boceto, considere la posibilidad de agregar un control **[Agregar imagen](control-add-picture.md)**  para que los usuarios carguen una imagen. Se pueden ofrecer ambos métodos y el usuario puede elegir el que mejor le convenga.

### <a name="keyboard-support"></a>Compatibilidad con el teclado

> [!IMPORTANT]
> **Entrada manuscrita** no es accesible para los usuarios de teclado. Proporcione siempre una forma de entrada alternativa. Por ejemplo, si se requiere una firma, podría agregar un control **[Entrada de texto](control-text-input.md)** para que los usuarios escriban su nombre. Se pueden ofrecer ambos métodos y el usuario puede elegir el que mejor le convenga.
