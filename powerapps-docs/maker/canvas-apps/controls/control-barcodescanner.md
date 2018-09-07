---
title: 'Control Escáner de código de barras: referencia | Microsoft Docs'
description: Información sobre el control Escáner de código de barras, con propiedades y ejemplos
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/25/2016
ms.author: fikaradz
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 853558273521491467fa7474688ce9c984ac5db6
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42862477"
---
# <a name="barcode-scanner-control-experimental-in-powerapps"></a>Control Escáner de código de barras (experimental) en PowerApps
Un control experimental con el que el usuario puede realizar fotos mediante el escáner de código de barras del dispositivo.

## <a name="description"></a>Descripción
Si agrega este control, el usuario puede actualizar un origen de datos con una o más fotos desde donde se esté ejecutando la aplicación.

## <a name="key-properties"></a>Propiedades principales
**escáner de código de barras**: en un dispositivo que tenga más de un escáner de códigos de barras, el identificador numérico del escáner de códigos de barras que usa la aplicación.

## <a name="additional-properties"></a>Propiedades adicionales
**[AccessibleLabel](properties-accessibility.md)**: etiqueta para lectores de pantalla.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**ShowLiveBarcodeDetection**: indica si se muestran indicaciones visuales para señalar el estado de la detección de códigos de barras. Los rectángulos amarillos representan áreas que se van a examinar. Una línea verde que atraviesa un rectángulo indica la identificación correcta del código de barras.

**Stream**: la imagen se actualiza automáticamente en la propiedad **TasaSecuencia**.

**TasaSecuencia**: la frecuencia de actualización de la imagen en la propiedad **Stream**, en milisegundos.  Este valor puede oscilar entre 100 (1/10 centésimas de segundo) y 3 600 000 (1 hora).

**Text**: valor del código de barras que el escáner identificó por última vez.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>Ejemplo
### <a name="add-photos-to-an-image-gallery-control"></a>Agregar fotos a un control Galería de imágenes
1. Agregue un control **Escáner de código de barras** y denomínelo **Mybarcode scanner**

    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
2. Agregue un control **Etiqueta** y establezca su salida en el **texto** del código de barras.  
3. Escanee un código de barras del tipo establecido en la propiedad BarcodeType.
4. La etiqueta mostrará el código de barras escaneado.


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="video-alternatives"></a>Alternativas de vídeo
* Considere la posibilidad de agregar un control **[Etiqueta](control-text-box.md)** con su propiedad **[Text](properties-core.md)** establecida en el **texto** del escáner de código de barras. Puesto que el escáner de código de barras no muestra el valor de código de barras identificado, al realizar el paso anterior el escáner se vuelve disponible para todos, y no solo para aquellos con discapacidades visuales.

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* La propiedad **[AccessibleLabel](properties-accessibility.md)** debe estar presente.

    > [!NOTE]
  > Los lectores de pantalla anunciarán cuándo se ha encontrado un nuevo código de barras. El valor no se anunciará. Siempre que el código de barras esté a la vista, los lectores de pantalla recordarán cada 5 segundos que se sigue identificando el mismo código de barras.
