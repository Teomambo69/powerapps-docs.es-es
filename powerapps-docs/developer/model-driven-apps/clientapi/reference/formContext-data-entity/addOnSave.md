---
title: addOnSave (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1a66f93d-a47c-4316-91f1-dcf5d09f9d19
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonsave-client-api-reference"></a>addOnSave (referencia de la API de cliente)



[!INCLUDE[./includes/addOnSave-description.md](./includes/addOnSave-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.entity.addOnSave(myFunction)`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|myFunction|referencia de funciones|Sí|La función que se debe ejecutar cuando se guarda el registro.  La función se agregará al final de la canalización del controlador de eventos. El contexto de ejecución se pasa automáticamente como el primer parámetro a la función. Para obtener más información, consulte [contexto de ejecución](../../clientapi-execution-context.md).

### <a name="related-topics"></a>Temas relacionados

[removeOnSave](removeOnSave.md)

[Evento de formulario OnSave](../events/form-onsave.md)

