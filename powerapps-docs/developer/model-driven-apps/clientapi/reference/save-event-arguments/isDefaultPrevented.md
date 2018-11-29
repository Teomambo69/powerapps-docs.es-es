---
title: isDefaultPrevented (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9a8802ad-80aa-4386-a192-573280587546
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="isdefaultprevented-client-api-reference"></a>isDefaultPrevented (referencia de la API de cliente)



[!INCLUDE[./includes/isDefaultPrevented-description.md](./includes/isDefaultPrevented-description.md)]

## <a name="syntax"></a>Sintaxis

`executionContext.getEventArgs().isDefaultPrevented();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: booleano

**Descripción**: **true** si el evento guardar se ha cancelado porque se usó el método preventDefault; **false** lo contrario.


### <a name="related-topics"></a>Temas relacionados

[getSaveMode](getSaveMode.md)

[preventDefault](preventDefault.md)

