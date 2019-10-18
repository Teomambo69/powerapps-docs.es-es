---
title: hasEntityPrivilege | Microsoft Docs
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
ms.assetid: f22723f0-c606-465c-abba-0a8c46a10e32
ms.openlocfilehash: f370d14f0b978d7ac4b6e6535677e06e7cf3f86e
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340906"
---
# <a name="hasentityprivilege"></a>hasEntityPrivilege

[!INCLUDE [hasentityprivilege-description](includes/hasentityprivilege-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="syntax"></a>Sintaxis

`context.utils.hasEntityPrivilege(entityTypeName, privilegeType, privilegeDepth)`

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|entityTypeName|`string`|Sí|Nombre del tipo de entidad|
|privilegeType|`enum`|No|Tipos de privilegios de entidad. Tiene los siguientes atributos:<br/>- `None = 0`<br/>- `Create = 1` <br/>- `Read = 2`<br/>- `Write = 3`<br/>- `Delete = 4`<br/>- `Assign =5`<br/>- `Share =6`<br/>- `Append =7`<br/>- `AppendTo =8`|
|privilegeDepth|`enum`|No|Profundidad de privilegios de entidad. Tiene el atributo siguiente: <br/>- `None = -1`<br/>- `Basic = 0`<br/>- `Local = 1`<br/>- `Deep = 2`<br/>- `Global = 3`|

## <a name="return-value"></a>Valor devuelto

**Tipo**: `boolean`

### <a name="related-topics"></a>Temas relacionados

[Utility](../utility.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)