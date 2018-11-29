---
title: setDisplayState (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 21368fac-d4bc-4f75-8a9c-cce098fa0b45
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setdisplaystate-client-api-reference"></a>setDisplayState (referencia de la API de cliente)



[!INCLUDE[./includes/setDisplayState-description.md](./includes/setDisplayState-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.ui.process.setDisplayState(state);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|estado|String|Sí|Especifique "expandido", "contraído" o "flotante". El valor "flotante" no se admite en el cliente web.|

### <a name="related-topics"></a>Temas relacionados

[getDisplayState](getDisplayState.md)

[formContext.ui.process](../formContext-ui-process.md)



