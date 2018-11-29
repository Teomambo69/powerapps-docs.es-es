---
title: getIsPartyList (referencia de la API de cliente)| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 487d0923-9675-4308-b88e-fdbf91853a98
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getispartylist-client-api-reference"></a>getIsPartyList (referencia de la API de cliente)



Devuelve un valor booleano que indica si la búsqueda representa una búsqueda de tipo partylist. Las búsquedas de tipo partylist permiten establecer varios registros, como el campo **Para:** de un registro de entidad de correo electrónico.

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

Búsqueda

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).getIsPartyList()`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Booleano. 

**Descripción**: true si el atributo de búsqueda es de un tipo partylist; de lo contrario, false.

