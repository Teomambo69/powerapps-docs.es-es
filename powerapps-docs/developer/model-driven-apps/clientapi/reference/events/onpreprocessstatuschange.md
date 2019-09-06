---
title: Evento onPreProcessStatusChange (referencia de la API de cliente) en Dynamics 365 for Customer Engagement| MicrosoftDocs
ms.date: 06/30/2019
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 for Customer Engagement (online)
ms.assetid: null
author: MSFTMan
ms.author: Deonhe
manager: KVivek
search.audienceType:
  - developer
search.app:
  - D365CE
---
# <a name="onpreprocessstatuschange-event-client-api-reference"></a>Evento onPreProcessStatusChange (referencia de la API de cliente)

[!INCLUDE[](../../../../../includes/cc_applies_to_update_9_0_0.md)]

Este evento se produce **antes** de que cambie el estado de un proceso de instancia. 

Use el método **formContext.data.process**.[addOnPreProcessStatusChange](../formContext-data-process/eventhandlers/addOnPreProcessStatusChange.md) para agregar controladores de evento para este evento y el método **formContext.data.process**.[removeOnPreProcessStatusChange](../formContext-data-process/eventhandlers/removeOnPreProcessStatusChange.md) para quitarlos. 

Desde un script de recurso web registrado al evento onPreProcessStatusChange, un programador puede invocar lo siguiente en el objeto executionContext pasado en el script de recurso web: 

`executionContext.getEventArgs().preventDefault();` 

Cuando se invoca `preventDefault`:

- El cambio de estado no se procesará. La instancia de proceso seguirá en la fase original en el estado original.
- No se procesará el guardado del formulario principal. Si el formulario principal está en estado modificado, se mantendría en estado modificado.
- No se invocarán recursos web que registraron onProcessStatusChange.

Esta API de cliente solo se admite en la interfaz unificada. El cliente web heredado no admite esta API de cliente.

## <a name="methods-supported-for-this-event"></a>Métodos admitidos para este evento
- Método **formContext.data.process**.[addOnPreProcessStatusChange](../formcontext-data-process/eventhandlers/addOnPreProcessStatusChange.md) para agregar controladores para este evento.
- Método **formContext.data.process**.[removeOnPreProcessStatusChange](../formcontext-data-process/eventhandlers/removeOnPreProcessStatusChange.md) para quitar controladores de este evento. 
