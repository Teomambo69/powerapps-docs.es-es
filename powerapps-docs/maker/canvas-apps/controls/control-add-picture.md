---
title: 'Control Agregar imagen: referencia | Microsoft Docs'
description: Información sobre el control Agregar imagen, con propiedades y ejemplos
author: fikaradz
ms.service: powerapps
ms.topic: reference
ms.component: canvas
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: e20d76c9e8913197d4b59380a5f91dea3851c959
ms.sourcegitcommit: 7354a0c61578fcc0b9965bf557b9d7c553c73e96
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34803544"
---
# <a name="add-picture-control-in-powerapps"></a>Control Agregar imagen en PowerApps
Toma una fotografía o carga imágenes desde el dispositivo local.

## <a name="description"></a>Descripción
Con este control los usuarios pueden tomar fotografías o cargar archivos de imagen desde su dispositivo y actualizar el origen de datos con este contenido. En un dispositivo móvil se presenta al usuario el cuadro de diálogo de elección del dispositivo para que elija entre tomar una foto o seleccionar una ya disponible.

Este control es un control agrupado que contiene dos controles: un control **Imagen** y un control **Add media button** (Agregar botón multimedia). El control **Imagen** muestra la imagen cargada o un marcador de posición si no se ha cargado ninguna imagen. El control **Add media button** (Agregar botón multimedia) le solicita una imagen para cargar.

Consulte la [referencia del control Imagen](control-image.md) para conocer las propiedades de **Imagen**.

## <a name="add-media-button-properties"></a>Propiedades de Add media button (Agregar botón multimedia)
**[AccessibleLabel](properties-accessibility.md)**: etiqueta para lectores de pantalla. Debe describir el fin de agregar una imagen.

**[Align](properties-text.md)**: la ubicación del texto respecto al centro horizontal de su control.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**ChangePictureText**: texto que aparece en el botón cuando se ha cargado una imagen.

**[Color](properties-color-border.md)**: el color del texto en un control.

**[DisabledBorderColor](properties-color-border.md)**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[DisabledColor](properties-color-border.md)**: el color del texto en un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[DisabledFill](properties-color-border.md)**: el color de fondo de un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**Error**: si hay un problema al cargar una imagen, esta propiedad contendrá una cadena de error apropiada.

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[FocusedBorderColor](properties-color-border.md)**: el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)**: el grosor del borde de un control cuando el control recibe el foco.

**[Font](properties-text.md)**: el nombre de la familia de fuentes en la que aparece el texto.

**[FontWeight](properties-text.md)**: el peso del texto en un control: **Bold**, **Semibold**, **Normal** o **Lighter**.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**[HoverColor](properties-color-border.md)**: el color del texto de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[HoverFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[Italic](properties-text.md)**: indica si el texto de un control está en cursiva.

**Multimedia**: un identificador de la secuencia que reproduce un control de audio o de vídeo.

**[AlCambiar](properties-core.md)**: indica cómo responde la aplicación cuando el usuario cambia el valor de un control (por ejemplo, mediante el ajuste de un control deslizante).

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**[Padding](properties-size-location.md)**: la distancia entre el texto de un botón Exportar o Importar y los bordes de ese botón.

**[PressedBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario toca o hace clic en ese control.

**[PressedColor](properties-color-border.md)**: el color de texto de un control cuando el usuario toca o hace clic en ese control.

**[PressedFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario toca o hace clic en ese control.

**[Reset](properties-core.md)**: indica si un control vuelve a su valor predeterminado.

**[Size](properties-text.md)**: el tamaño de la fuente del texto que aparece en un control.

**[Strikethrough](properties-text.md)**: indica si aparece una línea sobre el texto de un control.

**[TabIndex](properties-accessibility.md)**: orden de navegación del teclado en relación con otros controles.

**[Text](properties-core.md)**: texto que aparece en el botón cuando no se ha cargado una imagen.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Underline](properties-text.md)**: indica si aparece una línea debajo del texto de un control.

**[VerticalAlign](properties-text.md)**: la ubicación del texto en un control respecto al centro vertical de ese control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="examples"></a>Ejemplos
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


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
Se aplican las mismas directrices para **[Botón](control-button.md)** e **[Imagen](control-image.md)**. Además, tenga en cuenta lo siguiente:

### <a name="color-contrast"></a>Contraste de color
* El control **Add media button** (Agregar botón multimedia) debe tener el contraste adecuado entre su texto y el fondo. Dado que la imagen cargada puede tener diversos colores, use una propiedad **[Fill](properties-color-border.md)** opaca en el control **Add media button** (Agregar botón multimedia) para garantizar un contraste uniforme.

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* El control **Add media button** (Agregar botón multimedia) debe tener las propiedades **Text** y **ChangePictureText** que soliciten al usuario que agregue o cambie una imagen.

### <a name="keyboard-support"></a>Compatibilidad con el teclado
* **Add media button** (Agregar botón multimedia) debe tener la propiedad **[TabIndex](properties-accessibility.md)** igual a cero o superior para que los usuarios del teclado puedan desplazarse hasta él.
* **Add media button** (Agregar botón multimedia) debe tener claramente visibles los indicadores de enfoque. Use **[FocusedBorderColor](properties-color-border.md)** y **[FocusedBorderThickness](properties-color-border.md)** para conseguirlo.
 