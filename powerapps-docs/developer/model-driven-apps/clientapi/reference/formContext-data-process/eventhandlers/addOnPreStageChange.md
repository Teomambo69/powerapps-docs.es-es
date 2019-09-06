---
title: addOnPreStageChange (referencia de la API de cliente) en Dynamics 365 for Customer Engagement | MicrosoftDocs
ms.date: 07/19/2019
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 for Customer Engagement (online)
ms.assetid: null
author: msftman
ms.author: deonhe
manager: KVivek
search.audienceType:
  - developer
search.app:
  - D365CE
---
# <a name="addonprestagechange-client-api-reference"></a>addOnPreStageChange (referencia de la API de cliente)

[!INCLUDE[./includes/addOnStageChange-description.md](./includes/AddOnPreStageChange-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.process.addOnPreStageChange(myFunction);`

## <a name="parameter"></a>Parámetro

Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|myFunction|Referencia de funciones|Sí|La función que ejecutar **antes** de que cambie la fase de flujo de proceso de negocio. La función se agregará al principio de la canalización del controlador de eventos. El contexto de ejecución se pasa automáticamente como el primer parámetro a la función. Para obtener más información, consulte [contexto de ejecución](../../../clientapi-execution-context.md).<br/><br/>Debe usar una referencia a una función con nombre en lugar de una función anónima por si posteriormente desea quitar el controlador de eventos.|

Esta API de cliente solo se admite en la interfaz unificada. El cliente web heredado no admite esta API de cliente.

### <a name="related-topics"></a>Temas relacionados

- [addOnStageChange](addOnStageChange.md)
 
- [removeOnStageChange](removeOnStageChange.md)

- [formContext.data.process](../../formContext-data-process.md)
 


