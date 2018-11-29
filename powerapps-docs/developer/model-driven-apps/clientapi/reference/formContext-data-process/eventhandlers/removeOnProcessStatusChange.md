---
title: removeOnProcessStatusChange (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 5e41f59e-ddb3-4d47-b45b-454aa9e04439
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="removeonprocessstatuschange-client-api-reference"></a>removeOnProcessStatusChange (referencia de la API de cliente)



[!INCLUDE[./includes/removeOnProcessStatusChange-description.md](./includes/removeOnProcessStatusChange-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.process.removeOnProcessStatusChange(myFunction);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|myFunction|Referencia de funciones|Sí|La función que se quitará del evento [OnProcessStatusChange](../../events/onprocessstatuschange.md).|

### <a name="related-topics"></a>Temas relacionados

[addOnProcessStatusChange](addOnProcessStatusChange.md)
 
[formContext.data.process](../../formContext-data-process.md)
 


