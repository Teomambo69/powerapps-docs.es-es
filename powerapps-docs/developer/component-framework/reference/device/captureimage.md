---
title: CaptureImage | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d9c0063-add2-4002-acab-1be07ca1f6b6
---

# <a name="captureimage"></a>captureImage

[!INCLUDE[./includes/captureimage-description.md](./includes/captureimage-description.md)]

## <a name="syntax"></a>Sintaxis

`captureImage(options)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro|Escriba|Requerido|Descripción|
| ------------- |----|--------|-----------|
|`options`|`object`|no|Opciones para capturar imagen.|

## <a name="return-value"></a>Valor de retorno

Tipo: `Promise<FileObject>`

Consulte [Promesa](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) y [Archivo](https://developer.mozilla.org/docs/Web/API/File)

## <a name="remarks"></a>Comentarios

El objeto del parámetro `options` tiene las siguientes propiedades:

|Nombre|Escriba|Descripción|
| ---|----|-----------|
|`allowEdit`|`boolean`|Indica si se edita la imagen antes de guardar.|
|`height`|`number`|Alto de la imagen a capturar|
|`preferFrontCamera`|`boolean`|Indica si se va a capturar la imagen con la cámara delantera del dispositivo|
|`quality`|`number`|Calidad del archivo de imagen en porcentaje|
|`width`|`number`|Ancho de la imagen a capturar|


### <a name="related-topics"></a>Temas relacionados

[Dispositivo](../device.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)