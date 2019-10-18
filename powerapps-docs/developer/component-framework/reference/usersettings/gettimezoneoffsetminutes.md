---
title: getTimeZoneOffsetMinutes | Microsoft Docs
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
ms.assetid: 86290d20-7dbb-4932-adaa-31121ae7a3f6
ms.openlocfilehash: bc621299b19b1387225b8532ee03ff65e0e6471f
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341021"
---
# <a name="gettimezoneoffsetminutes"></a>getTimeZoneOffsetMinutes

[!INCLUDE [gettimezoneoffsetminutes-description](includes/gettimezoneoffsetminutes-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="syntax"></a>Sintaxis

`context.usersettings.getTimeZoneOffsetMinutes(date)`

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|Posteriormente|`Date`|Sí|fecha para la que se va a obtener el desplazamiento de la hora UTC.|

## <a name="return-value"></a>Valor devuelto

Tipo: `Number` Descripción: ajuste de zona horaria en minutos.


### <a name="related-topics"></a>Temas relacionados

[Configuración de usuario](../usersettings.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)