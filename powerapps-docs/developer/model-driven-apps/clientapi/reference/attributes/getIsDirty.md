---
title: getIsDirty (referencia de la API de cliente)| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 5f75ecae-a946-47a0-b748-96525b556f31
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getisdirty-client-api-reference"></a>getIsDirty (referencia de la API de cliente)



Devuelve un valor booleano que indica si hay cambios no guardados en el valor del atributo. 

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

Todas

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).getIsDirty()`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Booleano. 

**Descripción**: true si hay cambios no guardados; en caso contrario, false.