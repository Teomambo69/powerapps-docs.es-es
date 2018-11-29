---
title: removeOnSave (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 14a92f7c-f4c0-475d-8797-dcbb283db37a
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="removeonsave-client-api-reference"></a>removeOnSave (referencia de la API de cliente)



[!INCLUDE[./includes/removeOnSave-description.md](./includes/removeOnSave-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.entity.removeOnSave(myFunction)`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|myFunction|referencia de funciones|Sí|La función que se quitará para el evento **OnSave**.

### <a name="related-topics"></a>Temas relacionados

[addOnSave](addOnSave.md)

[Evento de formulario OnSave](../events/form-onsave.md)

