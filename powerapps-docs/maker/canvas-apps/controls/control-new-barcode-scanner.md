---
title: 'Control escáner de código de barras: referencia | Microsoft Docs'
description: Obtener información, incluidas las propiedades y ejemplos sobre el control escáner de código de barras
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 11/25/2018
ms.author: fikaradz
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 961f8908014ef9cd85eadacb97a7c1dfc7e52b25
ms.sourcegitcommit: eef2d6d9a9c7f5c8a44b9734817f59dc0eac3ecf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "57801006"
---
# <a name="barcode-scanner-control-for-canvas-apps"></a>Control escáner de código de barras para las aplicaciones de lienzo

Examina los códigos de barras, los códigos QR y códigos de la matriz de datos en un dispositivo Android o iOS. No se admite en un explorador web.

## <a name="description"></a>Descripción

El control abre un analizador en un dispositivo Android o iOS nativo. El analizador detecta automáticamente un código de barras, un código QR o un código de la matriz de datos cuando en la vista. El control no admite análisis en un explorador web.

El control admite estos tipos de códigos de barras, los códigos de la matriz de datos y los códigos QR:

- UPC A
- UPC E
- EAN 8
- EAN 13
- CÓDIGO 39
- CÓDIGO 128
- ITF
- PDF 417

## <a name="key-properties"></a>Propiedades principales

**Valor** : salida de la propiedad que contiene el valor de texto del código que ha examinado más recientemente.

**Texto** : texto que aparece en el botón que activa el analizador.

**OnScan** : cómo responde una aplicación cuando un código de barras se analiza correctamente.

## <a name="additional-properties"></a>Propiedades adicionales

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**FlashlightEnabled** : indica si el linterna se habilita automáticamente cuando se abre el analizador.

**[Alto](properties-size-location.md)**  : el alto del botón que activa el analizador.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**Tipo** -el tipo de código que se ha detectado en el examen que recientemente se realizó correctamente.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Ancho](properties-size-location.md)**  : el ancho del botón que activa el analizador.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).
