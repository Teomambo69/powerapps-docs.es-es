---
title: setFullScreen | Microsoft Docs
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
ms.assetid: 1faf3e79-969e-4c1e-ac01-8e2155c609fa
ms.openlocfilehash: b7fb38bcb0102356d8d1ea2540edf0dd1f845cbd
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342631"
---
# <a name="setfullscreen"></a>setFullScreen

[!INCLUDE [setfullscreen-description](includes/setfullscreen-description.md)]

## <a name="syntax"></a>Sintaxis

`context.mode.setControlState(mode);`

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|value|`Boolean`|Sí|`True` si el componente debe ajustarse automáticamente a la pantalla completa. `False` si el componente debe ajustarse automáticamente al ancho asignado.|


### <a name="related-topics"></a>Temas relacionados

[Mode](../mode.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)