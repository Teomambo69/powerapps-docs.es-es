---
title: addOnPreProcessStatusChange (referencia de la API de cliente) en Dynamics 365 for Customer Engagement | MicrosoftDocs
ms.date: 08/05/2017
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 for Customer Engagement (online)
ms.assetid: null
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - D365CE
---
# <a name="addonpreprocessstatuschange-client-api-reference"></a>addOnPreProcessStatusChange (referencia de la API de cliente)

[!INCLUDE[](../../../../../../includes/cc_applies_to_update_9_0_0.md)]

[!INCLUDE[./includes/addOnPreProcessStatusChange-description.md](./includes/addOnPreProcessStatusChange-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.process.addOnPreProcessStatusChange(myFunction);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|myFunction|Referencia de funciones|Sí|La función que se ha de ejecutar cuando cambia el estado de flujo de proceso de negocio. La función se agregará al principio de la canalización del controlador de eventos. El contexto de ejecución se pasa automáticamente como el primer parámetro a la función. Para obtener más información, consulte [contexto de ejecución](../../../clientapi-execution-context.md).<br/><br/>Debe usar una referencia a una función con nombre en lugar de una función anónima por si posteriormente desea quitar el controlador de eventos.|

Esta API de cliente solo se admite en la interfaz unificada. El cliente web heredado no admite esta API de cliente.

### <a name="related-topics"></a>Temas relacionados

[removeOnPreProcessStatusChange](removeOnPreProcessStatusChange.md)

[formContext.data.process](../../formContext-data-process.md)
