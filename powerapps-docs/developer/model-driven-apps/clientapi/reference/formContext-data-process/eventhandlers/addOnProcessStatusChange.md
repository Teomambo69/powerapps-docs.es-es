---
title: addOnProcessStatusChange (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 2bf30298-f52b-4ab7-8833-4838f0d87e12
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonprocessstatuschange-client-api-reference"></a>addOnProcessStatusChange (referencia de la API de cliente)



[!INCLUDE[./includes/addOnProcessStatusChange-description.md](./includes/addOnProcessStatusChange-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.process.addOnProcessStatusChange(myFunction);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|myFunction|Referencia de funciones|Sí|La función que se ha de ejecutar cuando cambia el estado de flujo de proceso de negocio.  La función se agregará al final de la canalización del controlador de eventos. El contexto de ejecución se pasa automáticamente como el primer parámetro a la función. Para obtener más información, consulte [contexto de ejecución](../../../clientapi-execution-context.md).<br/><br/>Debe usar una referencia a una función con nombre en lugar de una función anónima por si posteriormente desea quitar el controlador de eventos.|

### <a name="related-topics"></a>Temas relacionados

[removeOnProcessStatusChange](removeOnProcessStatusChange.md)
 
[formContext.data.process](../../formContext-data-process.md)

