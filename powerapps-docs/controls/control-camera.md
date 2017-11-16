---
title: "Control Cámara: referencia | Microsoft Docs"
description: "Información sobre el control Cámara, con propiedades y ejemplos"
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
ms.openlocfilehash: a3a724ad42082962ec8aea4e616f1d75aa7299ec
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="camera-control-in-powerapps"></a>Control Cámara en PowerApps
Un control con el que el usuario puede realizar fotos mediante el uso de la cámara del dispositivo.

## <a name="description"></a>Descripción
Si agrega este control, el usuario puede actualizar un origen de datos con una o más fotos desde donde se esté ejecutando la aplicación.

## <a name="key-properties"></a>Propiedades principales
**Cámara**: en un dispositivo que tenga más de una cámara, el identificador numérico de la cámara que usa la aplicación.

## <a name="additional-properties"></a>Propiedades adicionales
**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**Brillo**: indica la claridad que el usuario percibirá probablemente en una imagen.

**Contraste**: indica cómo el usuario puede distinguir fácilmente colores similares en una imagen.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**EnSecuencia**: indica cómo responde la aplicación cuando la propiedad **Stream** está actualizada.

**Foto**: la imagen capturada cuando el usuario realiza una foto.

**Stream**: la imagen se actualiza automáticamente en la propiedad **TasaSecuencia**.

**TasaSecuencia**: la frecuencia de actualización de la imagen en la propiedad **Stream**, en milisegundos.  Este valor puede oscilar entre 100 (1/10 centésimas de segundo) y 3 600 000 (1 hora).

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

**Zoom**: el porcentaje en que se amplía una imagen de una cámara o la vista de un archivo en un visor de PDF.

## <a name="related-functions"></a>Funciones relacionadas
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>Ejemplo
### <a name="add-photos-to-an-image-gallery-control"></a>Agregar fotos a un control Galería de imágenes
1. Agregue un control **Cámara**, denomínelo **MyCamera** y establezca su propiedad **[AlSeleccionar](properties-core.md)** en esta fórmula:<br>
   **Collect(MyPix, MyCamera.Photo)**
   
    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
   
    ¿Desea más información sobre la función **[Recopilar](../functions/function-clear-collect-clearcollect.md)** u [otras funciones](../formula-reference.md)?
2. Presione F5 y, a continuación, tome una foto haciendo clic o pulsando en **MyCamera**.
3. Agregue un control **[Galería de imágenes](control-gallery.md)** y, luego, cambie de tamaño su control **[Imagen](control-image.md)**, su plantilla y el propio control **Galería de imágenes** para que quepa en la pantalla.
4. Establezca la propiedad **[Elementos](properties-core.md)** del control **Galería de imágenes** en esta expresión:<br>**MyPix.Url**.
5. Establezca la propiedad **[Elementos](properties-visual.md)** del control **Imagen** de la galería en esta expresión:<br>
   **ThisItem.Url**
   
    La foto que realizó aparece en el control **Galería de imágenes**.
6. Realice tantas fotografías como desee y, a continuación, presione Esc para volver al área de trabajo predeterminada.
7. (opcional) Establezca la propiedad **AlSeleccionar** del control **Imagen** del control **Galería de imágenes** en **Remove(MyPix, ThisItem)**, presione F5 y luego pulse o haga clic en una foto para quitarla.

Use la función **[SaveData](../functions/function-savedata-loaddata.md)** para guardar las fotos localmente o la función **[Revisión](../functions/function-patch.md)** para actualizar el origen de datos.

