---
title: isOnPremise (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 855767c5-c48f-47a2-8f99-52423221d974
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="isonpremise-client-api-reference"></a>isOnPremise (referencia de la API de cliente)



Devuelve un valor booleano que indica si la instancia de las aplicaciones basadas en modelos se hospeda en localmente o en línea. 

## <a name="syntax"></a>Sintaxis

```JavaScript
var globalContext = Xrm.Utility.getGlobalContext();
globalContext.isOnPremises();
```

## <a name="return-value"></a>Valor de retorno

**Tipo:** Booleano

**Descripción**: **true** si la instancia de aplicaciones basadas en modelos es local; **false** lo contrario.

### <a name="related-topics"></a>Temas relacionados

[Xrm.Utility.getGlobalContext](../getGlobalContext.md)



