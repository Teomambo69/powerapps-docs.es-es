---
title: setControlState | Microsoft Docs
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
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 1052db82-7002-44ca-ad1f-9d3d4c311817
ms.openlocfilehash: 56c2221916781db646d27b131dfc00e61e742be3
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342677"
---
# <a name="setcontrolstate"></a>setControlState

[!INCLUDE [setcontrolstate-description](includes/setcontrolstate-description.md)]

## <a name="syntax"></a>Sintaxis

`context.mode.setControlState(state);`

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental) 

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|State|`Dictionary`|Sí|Datos que se conservan en una sesión para un solo usuario.|

## <a name="return-value"></a>Valor devuelto

Tipo: `boolean`


### <a name="related-topics"></a>Temas relacionados

[Mode](../mode.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)