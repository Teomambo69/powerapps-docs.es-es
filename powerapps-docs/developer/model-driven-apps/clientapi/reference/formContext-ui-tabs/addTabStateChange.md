---
title: addTabStateChange (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 51b0dbf3-28bd-4eea-9ee9-50b322e9af9b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addtabstatechange-client-api-reference"></a>addTabStateChange (referencia de la API de cliente)



[!INCLUDE[./includes/addTabStateChange-description.md](./includes/addTabStateChange-description.md)].

## <a name="syntax"></a>Sintaxis

`tabObj.addTabStateChange(myFunction);` 

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|myFunction|referencia de funciones|Sí|La función que se ejecutará en el evento [TabStateChange](../events/tabstatechange.md).  La función se agregará al final de la canalización del controlador de eventos. El contexto de ejecución se pasa automáticamente como el primer parámetro a la función. Para obtener más información, consulte [contexto de ejecución](../../clientapi-execution-context.md).|

### <a name="related-topics"></a>Temas relacionados

[formContext.ui](../formContext-ui.md)

[formContext](../../clientapi-form-context.md)


