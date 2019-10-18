---
title: openUrl | Microsoft Docs
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
ms.assetid: 590078f3-c604-4bd0-ac74-9cf6d8806802
ms.openlocfilehash: 21e097c739364b6cdb3935654ae9bf2b61143a06
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342286"
---
# <a name="openurl"></a>openUrl

[!INCLUDE [openurl-description](includes/openurl-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="syntax"></a>Sintaxis

`context.navigation.openUrl(url, options)`

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|Dirección|`string`|Sí|Dirección URL que se va a abrir.|
|Opciones|`OpenUrlOptions`|No|Opciones para abrir la dirección URL. OpenUrlOptions tiene los siguientes parámetros: <br/>- **alto**: `Number`. Alto de la ventana para mostrar la página resultante en píxeles.<br/>- **width**: `Number`. Ancho de la ventana para mostrar la página resultante en píxeles.|


### <a name="related-topics"></a>Temas relacionados

[Navegación](../navigation.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)