---
title: addOnLoad (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 31a146de-9e25-43be-ae3e-83a2a5c86543
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonload-client-api-reference"></a>addOnLoad (referencia de la API de cliente)



[!INCLUDE[./includes/addOnLoad-description.md](./includes/addOnLoad-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.ui.addOnLoad(myFunction)`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|myFunction|referencia de funciones|Sí|La función que se ejecutará en el evento de formulario [OnLoad](../events/form-onload.md).  La función se agregará al final de la canalización del controlador de eventos. El contexto de ejecución se pasa automáticamente como el primer parámetro a la función. Para obtener más información, consulte [contexto de ejecución](../../clientapi-execution-context.md).|

### <a name="related-topics"></a>Temas relacionados

[removeOnLoad](removeOnLoad.md)

[Evento de formulario OnLoad](../events/form-onload.md)

[formContext.ui](../formContext-ui.md)

[formContext](../../clientapi-form-context.md)

