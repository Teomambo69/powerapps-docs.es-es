---
title: openWebResource | Microsoft Docs
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
ms.assetid: 27a1e54c-71fe-450f-8f84-b4cc125970bf
ms.openlocfilehash: 577c26dd87149fabebafe32b77395029ef4df335
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342263"
---
# <a name="openwebresource"></a>openWebResource

[!INCLUDE [openwebresource-description](includes/openwebresource-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="syntax"></a>Sintaxis

`context.navigation.openWebResource(name, options, data)`

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|Name|`String`|Sí|Nombre del recurso web HTML que se va a abrir.|
|Opciones|`OpenWebResourceOptions`|No|Opciones de ventana para abrir el recurso Web. OpenWebResourceOptions tiene los siguientes atributos:<br/>- **alto**: `Number`. Alto de la ventana para mostrar la página resultante en píxeles.<br/>- **width**: `Number`. Ancho de la ventana para mostrar la página resultante en píxeles.<br/>- **openInNewWindow**: `Boolean`. Indica si se debe abrir el recurso Web en una nueva ventana.|
|Data|`String`|No|Datos que se van a pasar al parámetro Data.

### <a name="related-topics"></a>Temas relacionados

[Navegación](../navigation.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)