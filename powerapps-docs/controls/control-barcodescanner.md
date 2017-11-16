---
title: "Control Escáner de código de barras: referencia | Microsoft Docs"
description: "Información sobre el control Escáner de código de barras, con propiedades y ejemplos"
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
ms.openlocfilehash: c27a2319d74db9a50acff84e40ea7df83dc1c126
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="barcode-scanner-control-in-powerapps"></a>Control Escáner de código de barras en PowerApps
Un control con el que el usuario puede realizar fotos mediante el escáner de código de barras del dispositivo.

## <a name="description"></a>Descripción
Si agrega este control, el usuario puede actualizar un origen de datos con una o más fotos desde donde se esté ejecutando la aplicación.

## <a name="key-properties"></a>Propiedades principales
**escáner de código de barras**: en un dispositivo que tenga más de un escáner de códigos de barras, el identificador numérico del escáner de códigos de barras que usa la aplicación.

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

**Ampliar**: el porcentaje en que se amplía una imagen de un escáner de código de barras o la vista de un archivo en un visor PDF.

## <a name="related-functions"></a>Funciones relacionadas
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>Ejemplo
### <a name="add-photos-to-an-image-gallery-control"></a>Agregar fotos a un control Galería de imágenes
1. Agregue un control **Escáner de código de barras** y denomínelo **Mybarcode scanner**
   
    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
2. Agregue un control **Etiqueta** y establezca su salida en el valor del código de barras.  
3. Escanee un código de barras del tipo establecido en la propiedad BarcodeType.
4. La etiqueta mostrará el código de barras escaneado.

