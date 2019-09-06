---
title: Evento OnPreStageChange (referencia de la API de cliente) en Dynamics 365 for Customer Engagement| MicrosoftDocs
ms.date: 07/20/2019
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 for Customer Engagement (online)
ms.assetid: null
author: msftman
ms.author: deonhe
manager: kvivek
search.audienceType:
  - developer
search.app:
  - D365CE
---
# <a name="onprestagechange-event-client-api-reference"></a>Evento OnPreStageChange (referencia de la API de cliente)

Este evento se produce **antes** de que la fase de un control de flujo de proceso de negocio cambie. Este evento se produce cuando el usuario selecciona los botones **Fase siguiente**, **Retroceder a la fase anterior** o **Establecer fase activa** en la interfaz de usuario o cuando un desarrollador usa los métodos `formContext.data.process.moveNext`, `formContext.data.process.movePrevious` o `formContext.data.process.setActiveStage`.

Desde un script de recurso web registrado al evento onPreStageChange, un programador puede invocar lo siguiente en el objeto executionContext pasado en el script de recurso web: 

`executionContext.getEventArgs().preventDefault();` 

Cuando se invoca `preventDefault`:

- La navegación de fase no se procesará. La instancia de proceso se mantendrá en la fase original.
- No se procesará el guardado del formulario principal. Si el formulario principal está en estado modificado, se mantendría en estado modificado.
- No invocará ningún recurso web que haya registrado onStageChange.


Un objeto de contexto de ejecución se pasa a controladores de eventos para este evento. Puede usar el método [getEventArgs](../executioncontext/getEventArgs.md) para recuperar un objeto que tenga los siguientes métodos:
- **getDirection**: Devuelve una cadena que es “siguiente” o “anterior” para mostrar la dirección del cambio de fase.
- **getStage**: Devuelve un objeto de fase. Excepto cuando la navegación se mueve a una nueva entidad, la fase devuelta representa el objeto de fase de destino, es decir, la siguiente fase activa. Cuando la navegación se mueve a una nueva entidad, la fase es la fase desde la que se navega, es decir, el objeto de fase de destino activa anterior. Más información: [Métodos de fase](../formContext-data-process.md#stage-methods).

Esta API de cliente solo se admite en la interfaz unificada. El cliente web heredado no admite esta API de cliente.

## <a name="methods-supported-for-this-event"></a>Métodos admitidos para este evento
- Método **formContext.data.process**.[addOnPreStageChange](../formcontext-data-process/eventhandlers/addOnPreStageChange.md) para agregar controladores para este evento.
- Método **formContext.data.process**.[removeOnPreStageChange](../formcontext-data-process/eventhandlers/removeOnPreStageChange.md) para quitar controladores de este evento. 



