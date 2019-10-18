---
title: UserSettings | Microsoft Docs
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
ms.assetid: c237ff96-9268-4068-9d61-aea0bdc79fc2
ms.openlocfilehash: 5325091d8f82ffd98cfc4e5fdab4e0228a5d541e
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341044"
---
# <a name="usersettings"></a>UserSettings

[!INCLUDE [usersettings-description](includes/usersettings-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="properties"></a>Propiedades

### <a name="dateformattinginfo"></a>dateFormattingInfo

Información de formato de fecha recuperada del servidor.

**Tipo**: [DateFormattingInfo](dateformattinginfo.md)

### <a name="isrtl"></a>isRTL

Devuelve true si el idioma es de derecha a izquierda.

**Tipo**: `boolean`

### <a name="languageid"></a>languageId

Identificador de idioma del usuario actual.

**Tipo**: `number`

### <a name="numberformattinginfo"></a>numberFormattingInfo

Información de formato de número tal como se recupera del servidor.

**Tipo**: [NumberFormattingInfo](numberformattinginfo.md)

### <a name="securityroles"></a>securityRoles

Roles de usuario actuales.

**Tipo**: `string[]`

### <a name="userid"></a>Deberían

Identificador del usuario actual.

**Tipo**: `string`

### <a name="username"></a>NombreUsuario

Nombre del usuario actual.

**Tipo**: `string`

## <a name="methods"></a>Modalidades

|Forma | Descripción | 
| ------|-------------|
|[getTimeZoneOffsetMinutes](usersettings/gettimezoneoffsetminutes.md)|[!INCLUDE [gettimezoneoffsetminutes-description](usersettings/includes/gettimezoneoffsetminutes-description.md)]|

### <a name="related-topics"></a>Temas relacionados

[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)