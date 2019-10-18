---
title: formatDateShort | Microsoft Docs
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
ms.assetid: e69a9b6c-f737-4ebb-a9c1-901923b85358
ms.openlocfilehash: d9dd72ffdcb9ad69b3aae767effd14f617c0cba9
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343574"
---
# <a name="formatdateshort"></a>formatDateShort

[!INCLUDE [formatdateshort-description](includes/formatdateshort-description.md)]

## <a name="syntax"></a>Sintaxis

`context.formatting.formatDateShort(value, includeTime);`

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|value|`Date`|Sí|Fecha del valor que se va a dar formato.|
|includeTime|`boolean`|Sí|Indica si se va a mostrar la hora en el valor con formato.|

## <a name="return-value"></a>Valor devuelto

Tipo: `string`


### <a name="related-topics"></a>Temas relacionados

[Formato](../formatting.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)