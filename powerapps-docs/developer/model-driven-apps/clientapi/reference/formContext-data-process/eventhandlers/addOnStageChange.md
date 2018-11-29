---
title: addOnStageChange (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: d18136d2-a3cf-4440-8e6b-1703594acd79
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonstagechange-client-api-reference"></a>addOnStageChange (referencia de la API de cliente)



[!INCLUDE[./includes/addOnStageChange-description.md](./includes/addOnStageChange-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.process.addOnStageChange(myFunction);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|myFunction|Referencia de funciones|Sí|La función que se ha de ejecutar cuando cambia la fase de flujo de proceso de negocio.  La función se agregará al final de la canalización del controlador de eventos. El contexto de ejecución se pasa automáticamente como el primer parámetro a la función. Para obtener más información, consulte [contexto de ejecución](../../../clientapi-execution-context.md).<br/><br/>Debe usar una referencia a una función con nombre en lugar de una función anónima por si posteriormente desea quitar el controlador de eventos.|

### <a name="related-topics"></a>Temas relacionados
 
[removeOnStageChange](removeOnStageChange.md)

[formContext.data.process](../../formContext-data-process.md)
 


