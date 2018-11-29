---
title: Evento OnStageChange (referencia de API de cliente) en aplicaciones basadas en modelos | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 0c85fe34-1368-4d0d-87eb-4109206ce4f7
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="onstagechange-event-client-api-reference"></a>Evento OnStageChange (referencia de la API de cliente)



Este evento se produce cuando la fase de un control de flujo de proceso de negocio cambia. Este evento se produce cuando el usuario hace clic en los botones **Fase siguiente** o **Retroceder a la fase anterior** en la interfaz de usuario o cuando un desarrollador usa los métodos `formContext.data.process.moveNext` o `formContext.data.process.movePrevious`. No puede cancelar el cambio de fase mediante código en un controlador para este evento.

Un objeto de contexto de ejecución se pasa a controladores de eventos para este evento. Puede usar el método [getEventArgs](../executioncontext/getEventArgs.md) para recuperar un objeto que tenga los siguientes métodos:
- **getDirection**: Devuelve una cadena que es “siguiente” o “anterior” para mostrar la dirección del cambio de fase.
- **getStage**: Devuelve un objeto de fase. Excepto cuando la navegación se mueve a una nueva entidad, la fase devuelta representa el objeto de fase de destino, es decir, la siguiente fase activa. Cuando la navegación se mueve a una nueva entidad, la fase es la fase desde la que se navega, es decir, el objeto de fase de destino activa anterior. Más información: [Métodos de fase](../formContext-data-process.md#stage-methods).

## <a name="methods-supported-for-this-event"></a>Métodos admitidos para este evento
- Método **formContext.data.process**.[addOnStageChange](../formcontext-data-process/eventhandlers/addOnStageChange.md) para agregar controladores para este evento.
- Método **formContext.data.process**.[removeOnStageChange](../formcontext-data-process/eventhandlers/removeOnStageChange.md) para quitar controladores de este evento. 



