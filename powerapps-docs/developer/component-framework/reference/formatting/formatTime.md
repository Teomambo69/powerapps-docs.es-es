---
title: formatTime | Microsoft Docs
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
ms.assetid: 148964b5-106e-4f2e-8038-9086d29dc54f
---

# <a name="formattime"></a>formatTime

[!INCLUDE [formattime-description](includes/formattime-description.md)]

## <a name="syntax"></a>Sintaxis

`formatTime(value, behavior)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro|Escriba|Requerido|Descripción|
| ------------- |----|--------|-----------|
|valor|`Date`|sí|La fecha a la que se dará formato.|
|comportamiento|`DateTimeFieldBehavior`|sí|El comportamiento de objeto de fecha y hora al que se dará formato. El `DateTimeFieldBehavior` tiene los siguientes atributos:<br/>- `None =0`: Comportamiento de fecha y hora desconocido <br/>- `UserLocal =1`: Hora local del usuario correspondiente. Fechas almacenadas como UTC<br/>- `TimeZoneIndependent =3`: Fechas y horas almacenadas sin conversión a UTC|

## <a name="return-value"></a>Valor de retorno

Tipo: `string`


### <a name="related-topics"></a>Temas relacionados

[Formato](../formatting.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)