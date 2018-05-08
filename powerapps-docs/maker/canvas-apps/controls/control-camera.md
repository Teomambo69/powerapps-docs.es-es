---
title: 'Control Cámara: referencia | Microsoft Docs'
description: Información sobre el control Cámara, con propiedades y ejemplos
documentationcenter: na
author: fikaradz
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: 78cf8d73758e931d009080f03962c3450088a553
ms.sourcegitcommit: 45fac73f04aa03b5796ae6833d777f4757e67945
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="camera-control-in-powerapps"></a>Control Cámara en PowerApps
Un control con el que el usuario puede realizar fotos mediante el uso de la cámara del dispositivo.

## <a name="description"></a>Descripción
Si agrega este control, el usuario puede actualizar un origen de datos con una o más fotos desde donde se esté ejecutando la aplicación.

## <a name="key-properties"></a>Propiedades principales
**Cámara**: en un dispositivo que tenga más de una cámara, el identificador numérico de la cámara que usa la aplicación.

## <a name="additional-properties"></a>Propiedades adicionales
**[AccessibleLabel](properties-accessibility.md)**: etiqueta para lectores de pantalla. Debe describir la finalidad de realizar una foto.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**Brillo**: indica la claridad que el usuario percibirá probablemente en una imagen.

**Contraste**: indica cómo el usuario puede distinguir fácilmente colores similares en una imagen.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[FocusedBorderColor](properties-color-border.md)**: el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)**: el grosor del borde de un control cuando el control recibe el foco.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**EnSecuencia**: indica cómo responde la aplicación cuando la propiedad **Stream** está actualizada.

**Foto**: la imagen capturada cuando el usuario realiza una foto.

**Stream**: la imagen se actualiza automáticamente en la propiedad **TasaSecuencia**.

**TasaSecuencia**: la frecuencia de actualización de la imagen en la propiedad **Stream**, en milisegundos.  Este valor puede oscilar entre 100 (1/10 centésimas de segundo) y 3 600 000 (1 hora).

**[TabIndex](properties-accessibility.md)**: orden de navegación del teclado en relación con otros controles.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>Ejemplo
### <a name="add-photos-to-an-image-gallery-control"></a>Agregar fotos a un control Galería de imágenes
1. Agregue un control **Cámara**, denomínelo **MyCamera** y establezca su propiedad **[AlSeleccionar](properties-core.md)** en esta fórmula:<br>
   **Collect(MyPix, MyCamera.Photo)**

    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?

    ¿Desea más información sobre la función **[Recopilar](../functions/function-clear-collect-clearcollect.md)** u [otras funciones](../formula-reference.md)?
2. Presione F5 y, a continuación, tome una foto haciendo clic o pulsando en **MyCamera**.
3. Agregue un control **[Galería vertical](control-gallery.md)** y, luego, cambie de tamaño su control **[Imagen](control-image.md)**, su plantilla y el propio control **Galería de imágenes** para que quepa en la pantalla.
4. Establezca la propiedad **[Elementos](properties-core.md)** del control **Galería de imágenes** en:<br>**MyPix**.
5. Establezca la propiedad **[Elementos](properties-visual.md)** del control **Imagen** de la galería en esta expresión:<br>
   **ThisItem.Url**

    La foto que realizó aparece en el control **Galería de imágenes**.
6. Realice tantas fotografías como desee y, a continuación, presione Esc para volver al área de trabajo predeterminada.
7. (opcional) Establezca la propiedad **AlSeleccionar** del control **Imagen** del control **Galería de imágenes** en **Remove(MyPix, ThisItem)**, presione F5 y luego pulse o haga clic en una foto para quitarla.

Use la función **[SaveData](../functions/function-savedata-loaddata.md)** para guardar las fotos localmente o la función **[Revisión](../functions/function-patch.md)** para actualizar el origen de datos.


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
Además de mostrar la fuente de la cámara, todo el control de cámara también funciona como un botón que realiza una foto. Por lo tanto, las consideraciones sobre accesibilidad son parecidas a las de los botones.

### <a name="video-alternatives"></a>Alternativas de vídeo
* Considere la posibilidad de agregar una forma alternativa de entrada para los usuarios con discapacidades visuales. Por ejemplo, **[Agregar imagen](control-add-picture.md)** para permitir que los usuarios carguen una imagen desde sus dispositivos.

### <a name="color-contrast"></a>Contraste de color
Debe haber un contraste de color adecuado entre:
* **[FocusedBorderColor](properties-color-border.md)** y el color exterior

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* La propiedad **[AccessibleLabel](properties-accessibility.md)** debe estar presente.

### <a name="keyboard-support"></a>Compatibilidad con el teclado
* La propiedad **[TabIndex](properties-accessibility.md)** debe ser cero o superior para que los usuarios del teclado puedan desplazarse hasta él.
* Los indicadores de foco deben ser claramente visibles. Use **[FocusedBorderColor](properties-color-border.md)** y **[FocusedBorderThickness](properties-color-border.md)** para conseguirlo.
