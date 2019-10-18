---
title: Dispositivo | Microsoft Docs
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
ms.assetid: a0f9abc5-c605-4433-bf5a-f8253eeeda3b
ms.openlocfilehash: 0558004b889df59c168cfe9bdcfc7b5b5414fc02
ms.sourcegitcommit: b8148ec3324b7ffed9fa5a28ea1f4df7e444a081
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72347346"
---
# <a name="device"></a>Dispositivos

[!INCLUDE [device-description](includes/device-description.md)]

> [!IMPORTANT]
> Si quiere usar los métodos de la API de dispositivo, debe declarar el uso de estos métodos en el nodo de [uso de características](../manifest-schema-reference/feature-usage.md) en el archivo de manifiesto.

## <a name="syntax"></a>Sintaxis

`context.device`

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="methods"></a>Modalidades

|Forma | Descripción |
| ------------- |-------------|
|[captureAudio](device/captureaudio.md)|[!INCLUDE [captureaudio-description](device/includes/captureaudio-description.md)]|
|[Imagendecaptura](device/captureimage.md)|[!INCLUDE [captureimage-description](device/includes/captureimage-description.md)]|
|[captureVideo](device/capturevideo.md)|[!INCLUDE [capturevideo-description](device/includes/capturevideo-description.md)]|
|[getBarcodeValue](device/getbarcodevalue.md)|[!INCLUDE [getbarcodevalue-description](device/includes/getbarcodevalue-description.md)]|
|[getCurrentPosition](device/getcurrentposition.md)|[!INCLUDE [getcurrentposition-description](device/includes/getcurrentposition-description.md)]|
|[pickFile](device/pickfile.md)|[!INCLUDE [pickfile-description](device/includes/pickfile-description.md)]|

### <a name="related-topics"></a>Temas relacionados

[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)