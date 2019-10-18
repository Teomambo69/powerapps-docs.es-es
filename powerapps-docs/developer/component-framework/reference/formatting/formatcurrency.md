---
title: FormatCurrency | Microsoft Docs
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
ms.assetid: 87e433e6-573f-414f-b49d-1213f2bd8cf4
ms.openlocfilehash: 6089e88ce5814ca24c8310435726bff07cc97894
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343252"
---
# <a name="formatcurrency"></a>formatCurrency

[!INCLUDE [formatcurrency-description](includes/formatcurrency-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="syntax"></a>Sintaxis

`context.formatting.formatCurrency(value, precision, symbol)`

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|value|`number`|yes| Valor al que se va a dar formato.|
|precisión|`number`|yes| Número de dígitos después del separador decimal.|
|Símbolo|`string`|yes| Símbolo de moneda o código que se va a agregar con el valor de moneda.|

## <a name="return-value"></a>Valor devuelto

Tipo: `string`


### <a name="related-topics"></a>Temas relacionados

[Formato](../formatting.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)