---
title: removeOnPreStageChange (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 08/05/2019
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
author: MsftMan
ms.author: DeonHe
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="removeonprestagechange-client-api-reference"></a>removeOnPreStageChange (referencia de la API de cliente)

[!INCLUDE[./includes/removeOnPreStageChange-description.md](./includes/removeOnPreStageChange-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.process.removeOnPreStageChange(myFunction);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|myFunction|Referencia de funciones|Sí|La función que se quitará del evento [OnPreStageChange](../../events/onprestagechange.md).|

### <a name="related-topics"></a>Temas relacionados

[addOnPreStageChange](addOnPreStageChange.md)
 
[formContext.data.process](../../formContext-data-process.md)
 


