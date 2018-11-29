---
title: Guardar argumentos de evento (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: dff20ae0-c9ec-4413-9cd1-0ff77639ad91
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="save-event-arguments-client-api-reference"></a>Guardar argumentos de evento (Referencia de API de cliente)



Cuando se produce el evento [OnSave](events/form-onsave.md) de formulario, puede usar el método [getEventArgs](executioncontext/getEventArgs.md) del objeto de contexto de ejecución para recuperar un objeto que contenga métodos que puede usar para administrar el evento guardar.

|Método|Descripción|
|--|--|
|[getSaveMode](save-event-arguments/getSaveMode.md)|[!INCLUDE[save-event-arguments/includes/getSaveMode-description.md](save-event-arguments/includes/getSaveMode-description.md)]|
|[isDefaultPrevented](save-event-arguments/isDefaultPrevented.md)|[!INCLUDE[save-event-arguments/includes/isDefaultPrevented-description.md](save-event-arguments/includes/isDefaultPrevented-description.md)]|
|[preventDefault](save-event-arguments/preventDefault.md)|[!INCLUDE[save-event-arguments/includes/preventDefault-description.md](save-event-arguments/includes/preventDefault-description.md)]|


## <a name="related-topics"></a>Temas relacionados

[Contexto de ejecución de la API del cliente](../clientapi-execution-context.md)

[Métodos del contexto de ejecución](execution-context.md)

