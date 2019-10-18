---
title: formatDateAsFilterStringUTC | Microsoft Docs
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
ms.assetid: a604fbbf-6d09-450d-b686-7a5cb3f3a2bc
ms.openlocfilehash: 2242e1badabd740bf414340ae3d11b29e6000ebb
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343160"
---
# <a name="formatdateasfilterstringinutc"></a>formatDateAsFilterStringInUTC

[!INCLUDE [formatdateasfilterstringinutc-description](includes/formatdateasfilterstringinutc-description.md)]

## <a name="syntax"></a>Sintaxis

`context.formatting.formatDateAsFilterStringInUTC(value, includeTime)`

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|value|`Date`|yes|Fecha a la que se va a dar formato.|
|includeTime|`boolean`|yes| Si el componente de hora debe incluirse en el valor devuelto.|

## <a name="return-value"></a>Valor devuelto

Tipo: `string`


### <a name="related-topics"></a>Temas relacionados

[Formato](../formatting.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)