---
title: 'Código de barras web-control de escáner: referencia | Microsoft Docs'
description: Información sobre el control de escáner de código de barras, con propiedades y ejemplos
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/25/2016
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a116d812f8be7d8c1fb15ba2b05805536240084c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74727485"
ms.PowerAppsDecimalTransform: true
---
# <a name="web-barcode-scanner-control-experimental-in-power-apps"></a>Código de barras Web: control de escáner (experimental) en Power apps

El control de exploración de código de barras heredado, que está obsoleto, pero podría ser útil para examinar códigos en un explorador Web.

## <a name="description"></a>Descripción

El control muestra la fuente de la cámara en la aplicación para que los usuarios puedan examinar códigos de barras en todos los dispositivos. El control está obsoleto debido a un rendimiento deficiente y el control de **[escáner de código de barras](control-new-barcode-scanner.md)** móvil reemplaza a este control.

## <a name="key-properties"></a>Propiedades principales

**escáner de código de barras**: en un dispositivo que tenga más de un escáner de códigos de barras, el identificador numérico del escáner de códigos de barras que usa la aplicación.

## <a name="additional-properties"></a>Propiedades adicionales

**[AccessibleLabel](properties-accessibility.md)** : etiqueta para lectores de pantalla.

**[BorderColor](properties-color-border.md)** : el color de un borde del control.

**[BorderStyle](properties-color-border.md)** : si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)** : el grosor de un borde del control.

**[DisplayMode](properties-core.md)** : indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[Height](properties-size-location.md)** : la distancia entre los bordes superior e inferior de un control.

**ShowLiveBarcodeDetection**: indica si se muestran indicaciones visuales para señalar el estado de la detección de códigos de barras. Los rectángulos amarillos representan áreas que se van a examinar. Una línea verde que atraviesa un rectángulo indica la identificación correcta del código de barras.

**Stream**: la imagen se actualiza automáticamente en la propiedad **TasaSecuencia**.

**TasaSecuencia**: la frecuencia de actualización de la imagen en la propiedad **Stream**, en milisegundos.  Este valor puede oscilar entre 100 (1/10 centésimas de segundo) y 3 600 000 (1 hora).

**Text**: valor del código de barras que el escáner identificó por última vez.

**[Información sobre herramientas](properties-core.md)** : texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Visible](properties-core.md)** : indica si un control aparece o está oculto.

**[Width](properties-size-location.md)** : la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)** : la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)** : la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas

[**Patch**( *DataSource*; *BaseRecord*; *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>Ejemplo

### <a name="add-photos-to-an-image-gallery-control"></a>Agregar fotos a un control Galería de imágenes

1. Agregue un control **Escáner de código de barras** y denomínelo **Mybarcode scanner**

    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?

1. Agregue un control **etiqueta** y establezca su salida en la propiedad **texto** del escáner del código de barras.

1. Digitalice un código de barras del tipo establecido en la propiedad **BarcodeType** .

    La etiqueta muestra el código de barras escaneado.

## <a name="accessibility-guidelines"></a>Directrices de accesibilidad

### <a name="video-alternatives"></a>Alternativas de vídeo

* Considere la posibilidad de agregar un control **[Etiqueta](control-text-box.md)** con su propiedad **[Text](properties-core.md)** establecida en el **texto** del escáner de código de barras. Puesto que el escáner de código de barras no muestra el valor de código de barras identificado, al realizar el paso anterior el escáner se vuelve disponible para todos, y no solo para aquellos con discapacidades visuales.

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla

* La propiedad **[AccessibleLabel](properties-accessibility.md)** debe estar presente.

    > [!NOTE]
  > Los lectores de pantalla anunciarán cuando se encuentre un nuevo código de barras. No se anunciará el valor. Siempre que el código de barras esté a la vista, los lectores de pantalla recordarán al usuario cada cinco segundos que todavía se está identificando el mismo código de barras.
