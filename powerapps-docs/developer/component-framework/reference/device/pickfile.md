---
title: PickFile | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aae27c64-33c4-47f1-b833-4c04161c01e2
ms.openlocfilehash: a36731edc7ee5cc8edede499fc791595bc00bc8c
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72344632"
---
# <a name="pickfile"></a>pickFile

[!INCLUDE[./includes/pickfile-description.md](./includes/pickfile-description.md)]

## <a name="syntax"></a>Sintaxis

`context.device.pickFile(options)`

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|`options`|`Object`|No|Opciones para seleccionar el archivo.|

## <a name="return-value"></a>Valor devuelto

Tipo: `Promise<FileObject[]>`

Vea [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) and [FileObject](../fileobject.md)

## <a name="remarks"></a>Sección

El objeto de parámetro `options` tiene las siguientes propiedades:

|Nombre|Tipo|Descripción|
|--|--|--|
|`accept`|`String`|Tipos de archivo de imagen que se van a seleccionar. Los valores válidos son *audio*, *vídeo*o *imagen*.|
|`allowMultipleFiles`|`Boolean`|Indica si se permite la selección de varios archivos|
|`maximumAllowedFileSize`|`Number`|Tamaño máximo de los archivos que se van a seleccionar|


### <a name="related-topics"></a>Temas relacionados

[Dispositivos](../device.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)