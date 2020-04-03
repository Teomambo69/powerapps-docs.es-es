---
title: 'Barcode-control de escáner: referencia | Microsoft Docs'
description: Información sobre el control de escáner de código de barras, con propiedades y ejemplos
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 11/25/2018
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d2499a597295147cea1b39bb18fee2cbb056b413
ms.sourcegitcommit: ebb4bb7ea7184e31dc95f0c301ebef75fae5fb14
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2020
ms.locfileid: "80624981"
---
# <a name="barcode-scanner-control-for-canvas-apps"></a>Control del lector de código de barras para aplicaciones de lienzo

Explora códigos de barras, códigos QR y códigos de matriz de datos en un dispositivo Android o iOS. No se admite en un explorador Web.

## <a name="description"></a>Descripción

El control abre un escáner nativo en un dispositivo iOS o Android. El escáner detecta automáticamente un código de barras, un código QR o un código de matriz de datos cuando está en la vista. El control no admite el examen en un explorador Web.

## <a name="key-properties"></a>Propiedades principales

**Valor** : propiedad de salida que contiene el valor de texto del código que se analizó más recientemente.

**Type** : propiedad de salida que contiene el tipo del código que se analizó más recientemente.

**Alscan** : cómo responde una aplicación cuando se examina correctamente un código de barras.

**OnCancel** : cómo responde una aplicación cuando el usuario cancela un examen de código de barras.

**BarcodeType** : el tipo de código de barras que se va a examinar. Puede tener como destino varios tipos de código de barras mediante su concatenación. Antiguo. BarcodeType. CODE128 & BarcodeType. CODE39 **default: auto**

**PreferFrontCamera** : indica si la cámara frontal, si está disponible, se utiliza para el examen.

**FlashlightEnabled** : indica si la linterna se habilita automáticamente cuando se abre el escáner.

## <a name="additional-properties"></a>Propiedades adicionales

**Texto: texto** que aparece en el botón que activa el analizador.

**[BorderColor](properties-color-border.md)** : el color de un borde del control.

**[BorderStyle](properties-color-border.md)** : si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)** : el grosor de un borde del control.

**[DisplayMode](properties-core.md)** : indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[Alto](properties-size-location.md)** : el alto del botón que activa el escáner.

**[Información sobre herramientas](properties-core.md)** : texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**Tipo** : el tipo de código que se ha detectado en el examen que se ha realizado correctamente.

**[Visible](properties-core.md)** : indica si un control aparece o está oculto.

**[Ancho](properties-size-location.md)** : el ancho del botón que activa el escáner.

**[X](properties-size-location.md)** : la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)** : la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
Las mismas instrucciones para el control de **[botón](control-button.md)** se aplican al control de **escáner de código de barras** porque es un botón que inicia el examen.

### <a name="visual-alternatives"></a>Alternativas visuales
* El escáner de códigos de barras es un botón que no muestra el resultado del análisis. Considere la posibilidad de mostrar el resultado del examen con un control **[etiqueta](control-text-box.md)** . Establezca la propiedad **[Text](properties-core.md)** de la etiqueta en la propiedad **Value** del escáner de códigos de barras. Establezca la propiedad **[Live](properties-accessibility.md)** de la etiqueta en **Educate** para que se notifiquen los cambios a los usuarios de lector de pantalla. Este cambio hace que el valor explorado sea accesible para todos los usuarios, independientemente de la capacidad visual.

* Los usuarios que tienen discapacidades visuales y del motor prefieren no señalar la cámara en un código de barras. Considere la posibilidad de agregar otra forma de entrada, como un control **[entrada de texto](control-text-input.md)** , para que los usuarios escriban códigos de barras.

## <a name="barcode-availability-by-device"></a>Disponibilidad de código de barras por dispositivo

| Tipo de código de barras | Android | iOS |
|--------------|:-------:|:---:|
|QR_CODE|✔|✔|
|DATA_MATRIX|✔|✔|
|UPC_A|✔|✔|
|UPC_E|✔|✔|
|EAN_8|✔|✔|
|EAN_13|✔|✔|
|CODE_39|✔|✔|
|CODE_93|✔|✔|
|CODE_128|✔|✔|
|CODABAR|✔|✖|
|ITF|✔|✔|
|RSS14|✔|✖|
|PDF_417|✔|✔|
|RSS_EXPANDED|✔|✖|
|MS|✖|✖|
|AZTEC|✔|✔|

**Nota:** PDF_417 y AZTEC no se admiten en el modo auto
