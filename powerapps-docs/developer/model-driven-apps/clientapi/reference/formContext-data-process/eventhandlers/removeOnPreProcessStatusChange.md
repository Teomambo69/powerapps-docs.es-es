---
title: removeOnPreProcessStatusChange (referencia de la API de cliente) en Dynamics 365 for Customer Engagement | MicrosoftDocs
ms.date: 06/30/2019
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 for Customer Engagement (online)
ms.assetid: null
author: MSFTMan
ms.author: Deonhe
manager: KVivek
search.audienceType:
  - developer
search.app:
  - D365CE
---
# <a name="removeonpreprocessstatuschange-client-api-reference"></a>removeOnPreProcessStatusChange (referencia de la API de cliente)

[!INCLUDE[](../../../../../../includes/cc_applies_to_update_9_0_0.md)]

[!INCLUDE[./includes/removeOnPreProcessStatusChange-description.md](./includes/removeOnPreProcessStatusChange-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.process.removeOnPreProcessStatusChange(myFunction);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|myFunction|Referencia de funciones|Sí|La función que se quitará del evento [OnPreProcessStatusChange](../../events/onpreprocessstatuschange.md).|

### <a name="related-topics"></a>Temas relacionados

[addOnProcessStatusChange](addOnProcessStatusChange.md)
 
[formContext.data.process](../../formContext-data-process.md)
 


