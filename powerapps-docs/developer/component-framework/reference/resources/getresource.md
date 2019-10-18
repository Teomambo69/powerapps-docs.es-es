---
title: getResource | Microsoft Docs
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
ms.assetid: 5c04ba7c-acfe-4375-8dd8-6c537ded9352
ms.openlocfilehash: 919606c7b6669265a8bdd4f7b43080564e87a80f
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341412"
---
# <a name="getresource"></a>getResource

[!INCLUDE [getresource-description](includes/getresource-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="syntax"></a>Sintaxis

`context.resources.getResource(id, success, failure)`

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|id|`String`|Sí|Identificador de la cadena de recursos.|
|Realizado|`String`|No|Devolución de llamada de operación correcta. Los datos de recursos se devuelven en formato codificado de base 64.|
|fallida|`String`|No|Devolución de llamada de error.|


### <a name="related-topics"></a>Temas relacionados

[Resources](../resources.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)