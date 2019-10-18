---
title: formatTime | Microsoft Docs
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
ms.assetid: 148964b5-106e-4f2e-8038-9086d29dc54f
ms.openlocfilehash: cc2c7dfdbe9952d69dcda9fdd4c813965f539478
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343344"
---
# <a name="formattime"></a>formatTime

[!INCLUDE [formattime-description](includes/formattime-description.md)]

## <a name="syntax"></a>Sintaxis

`context.formatting.formatTime(value, behavior);`

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|value|`Date`|Sí|Fecha a la que se va a dar formato.|
|Conducta|`DateTimeFieldBehavior`|Sí|Comportamiento del objeto DateTime al que se va a dar formato. El `DateTimeFieldBehavior` tiene los siguientes atributos:<br/>-  `None =0`: comportamiento de fecha y hora desconocido <br/>-  `UserLocal =1`: respetar la hora local del usuario. Fechas almacenadas como UTC<br/>-  `TimeZoneIndependent =3`: fechas y horas almacenadas sin conversión a UTC|

## <a name="return-value"></a>Valor devuelto

Tipo: `string`


### <a name="related-topics"></a>Temas relacionados

[Formato](../formatting.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)