---
title: hasEntityPrivilege | Microsoft Docs
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
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
ms.assetid: f22723f0-c606-465c-abba-0a8c46a10e32
---

# <a name="hasentityprivilege"></a>hasEntityPrivilege

[!INCLUDE [hasentityprivilege-description](includes/hasentityprivilege-description.md)]

## <a name="syntax"></a>Sintaxis

`hasEntityPrivilege(entityTypeName, privilegeType, privilegeDepth)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro|Escriba|Requerido|Descripción|
| ------------- |----|--------|-----------|
|entityTypeName|`string`|sí|Nombre del tipo de entidad|
|privilegeType|`enum`|no|Tipos de privilegio de entidad. Tiene los siguientes atributos:<br/>- `None =1`<br/>- `Create =1` <br/>- `Read =2`<br/>- `Write =3`<br/>- `Delete =4`<br/>- `Assign =5`<br/>- `Share =6`<br/>- `Append =7`<br/>- `AppendTo =8`|
|privilegeDepth|`enum`|no|Profundidad de privilegio de entidad. Tiene el siguiente atributo: <br/>- `None =-1`<br/>- `Basic =0`<br/>- `Local =1`<br/>- `Deep =2`<br/>- `Global =3`|

## <a name="return-value"></a>Valor de retorno

**Tipo**: `boolean`

### <a name="related-topics"></a>Temas relacionados

[Utilidad](../utility.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)