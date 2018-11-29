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
# <a name="client-api-execution-context"></a>Contexto de ejecución de la API de cliente



El contexto de ejecución define el contexto del evento en el que se ejecuta el código. Se pasa el contexto de ejecución cuando se produce un evento en un formulario o cuadrícula, que puede usar en su controlador de eventos para realizar varias tareas como determinar [formContext](clientapi-form-context.md) o [gridContext](clientapi-grid-context.md), o administrar el evento save. 

El contexto de ejecución se pasa de una de las formas siguientes:

- **Definiendo controladores de eventos con la interfaz de usuario**: el contexto de ejecución es un parámetro *opcional* que se puede pasar a una función de biblioteca JavaScript a través de un controlador de eventos. Utilice la opción **Pasar el contexto de ejecución como primer parámetro** en el cuadro de diálogo **Propiedades del controlador** cuando especifique el nombre de la función para pasar el contexto de ejecución de eventos. El contexto de ejecución es el primer parámetro que se pasa a una función.<br/><br/>
![Pasar el contexto de ejecución](../media/ClientAPI-PassExecutionContext.png)<br/><br/>

- **Definiendo controladores de eventos mediante código**: el contexto de ejecución se pasa automáticamente como el primer parámetro a funciones definidas con este código. Para obtener una lista de métodos que se pueden usar para definir controladores de eventos en código, vea [Agregar o quitar funciones a eventos mediante código](events-forms-grids.md#add-or-remove-event-handler-function-to-event-using-code). 

El objeto de contexto de ejecución proporciona una serie de métodos para trabajar más con el contexto. Más información: [Contexto de ejecución (referencia de la API de cliente)](reference/execution-context.md).


### <a name="related-topics"></a>Temas relacionados

 [Contexto de formulario de la API del cliente](clientapi-form-context.md)<br>
 [Contexto de cuadrícula de la API del cliente](clientapi-grid-context.md)<br>
 [Contexto de formulario y cuadrícula en las acciones de la cinta](../pass-data-page-parameter-ribbon-actions.md#form-and-grid-context-in-ribbon-actions)


