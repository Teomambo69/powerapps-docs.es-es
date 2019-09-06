---
title: openFile | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae94e467-d12c-4a74-96f0-05a09e03c5f8
---
# <a name="openfile"></a>Abrir archivo

[!INCLUDE [openfile-description](includes/openfile-description.md)]

## <a name="syntax"></a>Sintaxis

`openFile(file, options)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro|Escriba|Requerido|Descripción|
| ------------- |----|--------|-----------|
|archivo|`FileObject`|sí|Un objeto que describe el archivo que se va a abrir. FileObject tiene los atributos siguientes: <br/>- **fileContent**: `string`. Contenido del archivo. <br/>- **fileName**: `string`. Nombre del archivo.<br/>- **fileSize**: `number`. Tamaño del archivo en KB. <br/>- **mimeType**: `string`. Tipo MIME de archivo.|

## <a name="return-value"></a>Valor de retorno

Tipo: `Promise`

## <a name="remarks"></a>Comentarios

Consulte [Promesa](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) y [Archivo](https://developer.mozilla.org/docs/Web/API/File)


### <a name="related-topics"></a>Temas relacionados

[Navegación](../navigation.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)