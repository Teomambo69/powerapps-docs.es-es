---
title: Evento OnStageSelected (referencia de API de cliente) en aplicaciones basadas en modelos | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1ef0f11c-6188-4492-ae61-260a402223b8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="onstageselected-event-client-api-reference"></a>Evento OnStageSelected (referencia de la API de cliente)



Este evento se produce cuando se selecciona una fase de un control de flujo de proceso de negocio. No puede cancelar la selección de fase mediante código en un controlador para este evento.

Puede usar el método [getEventArgs](../executioncontext/getEventArgs.md) para recuperar un objeto que tenga el siguiente método:

**getStage**: Devuelve un objeto de fase que representa la fase seleccionada. Más información: [Métodos de fase](../formContext-data-process.md#stage-methods).

## <a name="methods-supported-for-this-event"></a>Métodos admitidos para este evento
- Método **formContext.data.process**.[addOnStageSelected](../formcontext-data-process/eventhandlers/addOnStageSelected.md) para agregar controladores para este evento.
- Método **formContext.data.process**.[removeOnStageSelected](../formcontext-data-process/eventhandlers/addOnStageSelected.md) para quitar controladores de este evento. 



