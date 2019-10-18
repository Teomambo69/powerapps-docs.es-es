---
title: Imagendecaptura | Microsoft Docs
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
ms.assetid: 1d9c0063-add2-4002-acab-1be07ca1f6b6
ms.openlocfilehash: e642af17e02334b45041df87386885536e1810af
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345690"
---
# <a name="captureimage"></a>captureImage

[!INCLUDE[./includes/captureimage-description.md](./includes/captureimage-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="syntax"></a>Sintaxis

`context.device.captureImage(options)`

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|`options`|`Object`|No|Opciones para capturar la imagen.|

## <a name="return-value"></a>Valor devuelto

Tipo: `Promise<FileObject>`

Vea [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) and [FileObject](../fileobject.md)

## <a name="remarks"></a>Sección

El objeto de parámetro `options` tiene las siguientes propiedades:

|Nombre|Tipo|Descripción|
| ---|----|-----------|
|`allowEdit`|`Boolean`|Indica si se debe editar la imagen antes de guardarla.|
|`height`|`Number`|Alto de la imagen que se va a capturar.|
|`preferFrontCamera`|`Boolean`|Indica si se va a capturar la imagen mediante la cámara frontal del dispositivo.|
|`quality`|`Number`|Calidad del archivo de imagen en porcentaje.|
|`width`|`Number`|Ancho de la imagen que se va a capturar.|


### <a name="related-topics"></a>Temas relacionados

[Dispositivos](../device.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)