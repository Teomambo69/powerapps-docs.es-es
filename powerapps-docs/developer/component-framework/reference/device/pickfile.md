---
title: PickFile | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aae27c64-33c4-47f1-b833-4c04161c01e2
---

# <a name="pickfile"></a>pickFile

[!INCLUDE[./includes/pickfile-description.md](./includes/pickfile-description.md)]

## <a name="syntax"></a>Sintaxis

`pickFile(options)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro|Escriba|Requerido|Descripción|
| ------------- |----|--------|-----------|
|`options`|`object`|no|Opciones para seleccionar archivo.|

## <a name="return-value"></a>Valor de retorno

Tipo: `Promise<File[]>`

Consulte [Promesa](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) y [Archivo](https://developer.mozilla.org/docs/Web/API/File)

## <a name="remarks"></a>Comentarios

El objeto del parámetro `options` tiene las siguientes propiedades:

|Nombre|Escriba|Descripción|
|--|--|--|
|`accept`|`string`|Tipo de archivo de imagen que seleccionar. Los valores válidos son "audio", "vídeo" o "imagen".|
|`allowMultipleFiles`|`boolean`|Indica si se permite seleccionar varios archivos.|
|`maximumAllowedFileSize`|`number`|Tamaño máximo de los archivos que se van a seleccionar.|


### <a name="related-topics"></a>Temas relacionados

[Dispositivo](../device.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)