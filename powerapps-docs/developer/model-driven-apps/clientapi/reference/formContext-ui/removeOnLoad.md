---
title: removeOnLoad (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 0b97afc4-1208-4c1b-8599-424d594ea69f
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="removeonload-client-api-reference"></a>removeOnLoad (referencia de la API de cliente)



[!INCLUDE[./includes/removeOnLoad-description.md](./includes/removeOnLoad-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.ui.removeOnLoad(myFunction)`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|myFunction|referencia de funciones|Sí|La función que se quitará del evento de formulario [OnLoad](../events/form-onload.md).

### <a name="related-topics"></a>Temas relacionados

[addOnLoad](addOnLoad.md)

[Evento de datos de formulario OnLoad](../events/form-onload.md)

[formContext.ui](../formContext-ui.md)

[formContext](../../clientapi-form-context.md)

