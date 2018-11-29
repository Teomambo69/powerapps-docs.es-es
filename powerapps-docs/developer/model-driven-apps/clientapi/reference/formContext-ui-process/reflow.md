---
title: reflow (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 6833e4ea-70fc-4ee0-8aab-68cc55e21444
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="reflow-client-api-reference"></a>reflow (referencia de la API de cliente)



[!INCLUDE[./includes/reflow-description.md](./includes/reflow-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.ui.process.reflow(updateUI, parentStage, nextStage);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|updateUI|Boolean|Sí|Especifique **true** para actualizar la interfaz de usuario del control de proceso; si no, **false**.|
|parentStage|String|Sí|Especifique el identificador de la fase principal en formato GUID.|
|nextStage|String|Sí|Especifique el identificador de la fase siguiente en formato GUID.|

### <a name="related-topics"></a>Temas relacionados

[formContext.ui.process](../formContext-ui-process.md)



