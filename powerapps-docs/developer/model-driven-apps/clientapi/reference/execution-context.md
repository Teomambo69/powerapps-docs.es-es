---
title: Contexto de ejecución de API de cliente en aplicaciones basadas en modelos| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: conceptual
applies_to:
  - Dynamics 365 (online)
ms.assetid: 1fcbf0fd-4e47-4352-a555-9315f7e57331
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="execution-context-client-api-reference"></a>Contexto de ejecución (referencia de la API de cliente)



El contexto de ejecución define el contexto del evento en el que se ejecuta el código. Más información: [Contexto de ejecución de la API de cliente](../clientapi-execution-context.md).

El objeto del contexto de ejecución proporciona los siguientes métodos.

|Método |Descripción |
|---|---|
|[getDepth](executioncontext/getDepth.md)|Devuelve un valor que indica el orden en el que se ejecuta el controlador.|
|[getEventArgs](executioncontext/getEventArgs.md)|Devuelve un objeto con métodos para administrar el evento **OnSave**.|
|[getEventSource](executioncontext/getEventSource.md)|Devuelve una referencia al objeto en que se produjo el evento.|
|[getFormContext](executioncontext/getFormContext.md)|Devuelve una referencia al formulario o a un elemento del formulario dependiendo de dónde se haya llamado al método.|
|[getSharedVariable](executioncontext/getSharedVariable.md)|Recupera un conjunto de variables con el método [setSharedVariable](executioncontext/setSharedVariable.md).|
|[setSharedVariable](executioncontext/setSharedVariable.md)|Establece el valor de una variable que será usada por un controlador una vez que se complete el controlador actual.|

### <a name="related-topics"></a>Temas relacionados

[Contexto de ejecución de la API de cliente](../clientapi-execution-context.md)

[Guardar argumentos de evento](save-event-arguments.md)

[Comprender el modelo de objetos de la API de cliente](../understand-clientapi-object-model.md) 

