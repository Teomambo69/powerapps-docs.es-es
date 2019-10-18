---
title: formatDecimal | Microsoft Docs
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
ms.assetid: 05c1c54d-14b5-4dad-9cd8-eec07e750c00
ms.openlocfilehash: 02f31ce76df0300fae517bbf4699c6d559b04591
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343505"
---
# <a name="formatdecimal"></a>formatDecimal

[!INCLUDE [formatdecimal-description](includes/formatdecimal-description.md)]

## <a name="syntax"></a>Sintaxis

`context.formatting.formatDecimal(value, precision);`

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|value|`number`|Sí|Fecha a la que se va a dar formato.|
|precisión|`number`|Sí|Número de dígitos después del separador decimal.|

## <a name="return-value"></a>Valor devuelto

Tipo: `string`


### <a name="related-topics"></a>Temas relacionados

[Formato](../formatting.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)