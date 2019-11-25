---
title: " Marco de trabajo de eventos (Common Data Service) | Microsoft Docs"
description: Describe el marco de trabajo de eventos y los desarrolladores de información deben saber cuándo utilizarlo.
ms.custom: ''
ms.date: 06/18/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4c055dbac811186dde54cc4a002ee721e3ca25cf
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752984"
---
# <a name="event-framework"></a>Marco de trabajo de eventos

La capacidad de ampliar el comportamiento predeterminado de Common Data Service depende de detectar cuándo se producen eventos en el servidor. El *marco de trabajo de eventos* proporciona la capacidad de registrar el código personalizado para que se ejecute en respuesta a eventos específicos. 

Todas las funcionalidades de ampliar el comportamiento predeterminado de la plataforma dependen del marco de trabajo de eventos. Cuando se configura un flujo de trabajo para responder a un evento usando el diseñador de flujo de trabajo sin necesidad de escribir código, el evento lo proporciona el marco de trabajo de eventos. 

Como desarrollador, usará la *herramienta de registro de complementos* para configurar los complementos, las integraciones con Azure, los proveedores de datos visuales de la entidad y los webhooks para responder a los eventos proporcionados por el marco de trabajo de eventos. Cuando se producen eventos y una extensión se registra para dar respuesta a los anteriores, la información contextual sobre los datos que intervengan en la operación se pasa a la extensión. Según como se configure el registro del evento, la extensión puede modificar los datos que se pasan,iniciar algún proceso automatizado que se aplicará inmediatamente o definir que una acción se agrega a una cola que se vaya a desarrollar más adelante.

Para aprovechar el marco de trabajo de eventos para las extensiones personalizadas debe conocer lo siguiente:

 - Qué eventos están disponibles
 - Cómo se procesa el evento
 - Qué tipo de datos está disponible para la extensión cuando el evento se produce
 - Qué limitaciones de tiempo y recursos existen
 - Cómo supervisar el rendimiento

## <a name="available-events"></a>Eventos disponibles

Como se describe en [Uso de mensajes con el servicio de la organización](org-service/use-messages.md), las operaciones de datos en la plataforma de Common Data Service se basan en los mensajes y cada mensaje tiene un nombre. Hay mensajes , `Create`, `Retrieve`, `RetrieveMultiple`, `Update`, `Delete`, `Associate` y `Disassociate` que satisfacen las operaciones de datos principales que se producen con las entidades. Hay también mensajes especializados para operaciones más complejas. Las acciones personalizadas agregan nuevos mensajes.

Cuando se usa la herramienta de registro de complementos para asociar una extensión con un mensaje en particular, lo registrará como *paso*. La captura de pantalla siguiente es el cuadro de diálogo **Registrar nuevo paso** utilizado al registrar un complemento.

![Cuadro de diálogo para registrar un paso](media/register-new-step-plug-in.png)

Un paso proporciona la información sobre a qué mensaje deben responder las extensiones, así como otras opciones de configuración. Use el campo **Mensaje** para elegir el mensaje al que la extensión responderá.

Normalmente, se puede esperar encontrar un mensaje para la mayoría de las clases *Request* en los espacios de nombres <xref:Microsoft.Crm.Sdk.Messages> o<xref:Microsoft.Xrm.Sdk.Messages>, pero también encontrará mensajes para cualquier acción personalizada que se haya creado en la organización. Las operaciones que conlleven metadatos de la entidad no están disponibles.

Los datos sobre mensajes se almacena en las entidades [SdkMessage](reference/entities/sdkmessage.md) y [SdkMessageFilter](reference/entities/sdkmessagefilter.md). La herramienta de registro de complementos filtrará esta información para mostrar solo los mensajes válidos.

Para comprobar si un mensaje y una combinación de entidad admite la ejecución de complementos utilizando una consulta de base de datos, puede usar la consulta de la API web siguiente:

```
{{webapiurl}}sdkmessages?$select=name
&$filter=isprivate eq false 
and (name ne 'SetStateDynamicEntity' 
and name ne 'RemoveRelated' 
and name ne 'SetRelated' and 
name ne 'Execute') 
and sdkmessageid_sdkmessagefilter/any(s:s/iscustomprocessingstepallowed eq true 
and s/isvisible eq true)
&$expand=sdkmessageid_sdkmessagefilter($select=primaryobjecttypecode;
$filter=iscustomprocessingstepallowed eq true and isvisible eq true)
&$orderby=name
```

> [!TIP]
> Puede exportar estos datos a una hoja de cálculo de Excel usando esta consulta y las instrucciones proporcionadas en esta entrada de blog: [Encontrar mensajes y entidades elegibles para complementos mediante Common Data Service](https://powerapps.microsoft.com/blog/find-messages-and-entities-eligible-for-plug-ins-using-the-common-data-service/)


También puede usar el FetchXML siguiente para recuperar esta información. El [Creador de FetchXML](https://fxb.xrmtoolbox.com) es una herramienta útil para ejecutar este tipo de consulta.

```xml
<fetch>
  <entity name='sdkmessage' >
    <attribute name='name' />
    <link-entity name='sdkmessagefilter' alias='filter' to='sdkmessageid' from='sdkmessageid' link-type='inner' >
      <filter type='and' >
        <condition attribute='iscustomprocessingstepallowed' operator='eq' value='1' />
        <condition attribute='isvisible' operator='eq' value='1' />
      </filter>
      <attribute name='primaryobjecttypecode' />
    </link-entity>
    <filter>
      <condition attribute='isprivate' operator='eq' value='0' />
      <condition attribute='name' operator='not-in' >
        <value>SetStateDynamicEntity</value>
        <value>RemoveRelated</value>
        <value>SetRelated</value>
          <value>Execute</value>
      </condition>
    </filter>
    <order attribute='name' />
  </entity>
</fetch>
```

> [!CAUTION]
> El mensaje `Execute` está disponible, pero no debe registrar las extensiones ya que lo llaman todas las operaciones.

> [!NOTE]
> Existen algunos casos donde los complementos y los flujos de trabajo que se registran para el evento de actualizar se pueden llamar dos veces. Más información: [Comportamiento de operaciones de actualización especializadas](special-update-operation-behavior.md)

## <a name="event-execution-pipeline"></a>Canalización de ejecución del evento

Al registrar un paso mediante la herramienta de registro de complementos también debe elegir **Fase de la canalización de eventos de ejecución**.  Cada mensaje se procesa en una serie de 4 fases como se describe en la siguiente tabla:

|Nombre|Descripción|
|--|--|
|**PreValidation**|[!INCLUDE [cc-prevalidation-description](../../includes/cc-prevalidation-description.md)]|
|**PreOperation**|[!INCLUDE [cc-preoperation-description](../../includes/cc-preoperation-description.md)]|
|**MainOperation**|Solo para uso interno.|
|**PostOperation**|[!INCLUDE [cc-postoperation-description](../../includes/cc-postoperation-description.md)]|

La fase que debe elegir depende del fin de la extensión. No es necesario aplicar toda la lógica empresarial en un solo paso. Puede aplicar múltiples pasos para que la lógica sobre si permite que una operación continúe esté en la fase **PreValidation** y que la lógica para modificar las propiedades del mensaje puede se produzca en la fase **PostOperation**.

> [!IMPORTANT]
> Una excepción que produzca el código en alguna fase hará que la transacción completa que se revierta. Debe asegurarse de que los posibles casos de excepción los gestiona el código. Si desea cancelar la operación, debe detectar esto en la fase **PreValidation** y solo lanzar una <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> que contenga un mensaje adecuado que explique por qué la operación se ha cancelado.

Se pueden registrarse múltiples extensiones para el mismo mensaje y la fase. En el registro del paso el valor de **Orden de ejecución** determina el orden en el que las diversas extensiones deben procesarse para una fase determinada.

La información sobre los pasos registrados se almacena en la [entidad SdkMessageProcessingStep](reference/entities/sdkmessageprocessingstep.md).

## <a name="event-context"></a>Contexto del evento

Si la extensión es un complemento, recibirá un parámetro que implementa la interfaz <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext>. Esta clase proporciona información sobre la <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext.Stage> para el que está registrado el complemento, así como información sobre el <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext.ParentContext> que proporciona información sobre cualquier operación en otro complemento que activó la operación actual.

Si la extensión es un webhook o extremo de bus de Azure Service, los datos que se enviarán al extremo registrado estarán en el formulario de un <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext> que implementa ambos <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext> y <xref:Microsoft.Xrm.Sdk.IExecutionContext>

Para obtener más información sobre el contexto de ejecución, lea [Conocer el contexto de ejecución](understand-the-data-context.md).