---
title: ' Marco de trabajo de eventos (Common Data Service para aplicaciones) | Microsoft Docs'
description: Describe el marco de trabajo de eventos y los desarrolladores de información deben saber cuándo utilizarlo.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="event-framework"></a>Marco de trabajo de eventos

<!-- Re-write from
https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/introduction-event-framework
https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/event-execution-pipeline

See notes at https://microsoft-my.sharepoint.com/:w:/p/jdaly/EfmTW7DQXNREuqj1s7tBtIIB4VZmvasZ1Nsbl4F5zlD1ZQ?e=FNlBmr 


Make sure to call out the changes due to the legacy update messages. That information was moved.

See 
https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/org-service/perform-specialized-operations-using-update#impact-of-this-change-on-plug-ins

https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/org-service/perform-specialized-operations-using-update#impact-of-this-change-on-workflows


-->

La capacidad de ampliar el comportamiento predeterminado de Common Data Service para aplicaciones depende de detectar cuándo se producen eventos en el servidor. El *marco de trabajo de eventos* proporciona la capacidad de registrar el código personalizado para que se ejecute en respuesta a eventos específicos. 

Todas las funcionalidades de ampliar el comportamiento predeterminado de la plataforma dependen del marco de trabajo de eventos. Cuando se configura un flujo de trabajo para responder a un evento usando el diseñador de flujo de trabajo sin necesidad de escribir código, el evento lo proporciona el marco de trabajo de eventos. 

Como desarrollador, usará la *herramienta de registro de complementos* para configurar los complementos, las integraciones con Azure, los proveedores de datos visuales de la entidad y los webhooks para responder a los eventos proporcionados por el marco de trabajo de eventos. Cuando se producen eventos y una extensión se registra para dar respuesta a los anteriores, la información contextual sobre los datos que intervengan en la operación se pasa a la extensión. Según como se configure el registro del evento, la extensión puede modificar los datos que se pasan,iniciar algún proceso automatizado que se aplicará inmediatamente o definir que una acción se agrega a una cola que se vaya a desarrollar más adelante.

Para aprovechar el marco de trabajo de eventos para las extensiones personalizadas debe conocer lo siguiente:

 - Qué eventos están disponibles
 - Cómo se procesa el evento
 - Qué tipo de datos está disponible para la extensión cuando el evento se produce
 - Qué limitaciones de tiempo y recursos existen
 - Cómo supervisar el rendimiento

## <a name="available-events"></a>Eventos disponibles

Como se describe en [Uso de mensajes con el servicio de la organización](org-service/use-messages.md), las operaciones de datos en la plataforma de CDS for Apps se basan en los mensajes y cada mensaje tiene un nombre. Hay mensajes , `Create`, `Retrieve`, `RetrieveMultiple`, `Update`, `Delete`, `Associate` y `Disassociate` que satisfacen las operaciones de datos principales que se producen con las entidades. Hay también mensajes especializados para operaciones más complejas. Las acciones personalizadas agregan nuevos mensajes.

Cuando se usa la herramienta de registro de complementos para asociar una extensión con un mensaje en particular, lo registrará como *paso*. La captura de pantalla siguiente es el cuadro de diálogo **Registrar nuevo paso** utilizado al registrar un complemento.

![Cuadro de diálogo para registrar un paso](media/register-new-step-plug-in.png)

Un paso proporciona la información sobre a qué mensaje deben responder las extensiones, así como otras opciones de configuración. Use el campo **Mensaje** para elegir el mensaje al que la extensión responderá.

Normalmente, se puede esperar encontrar un mensaje para la mayoría de las clases *Request* en los espacios de nombres <xref:Microsoft.Crm.Sdk.Messages> o<xref:Microsoft.Xrm.Sdk.Messages>, pero también encontrará mensajes para cualquier acción personalizada que se haya creado en la organización. Las operaciones que conlleven metadatos de la entidad no están disponibles.

Los datos sobre mensajes se almacena en las entidades [SdkMessage](reference/entities/sdkmessage.md) y [SdkMessageFilter](reference/entities/sdkmessagefilter.md). La herramienta de registro de complementos filtrará esta información para mostrar solo los mensajes válidos.

> [!CAUTION]
> El mensaje `Execute` está disponible, pero no debe registrar normalmente las extensiones ya que lo llaman todas las operaciones.

> [!NOTE]
> Existen algunos casos donde los complementos y los flujos de trabajo que se registran para el evento de actualizar se pueden llamar dos veces. Más información: [Comportamiento de operaciones de actualización especializadas](special-update-operation-behavior.md)

## <a name="event-execution-pipeline"></a>Canalización de ejecución del evento

Al registrar un paso mediante la herramienta de registro de complementos también debe elegir **Fase de la canalización de eventos de ejecución**.  Cada mensaje se procesa en una serie de 4 fases como se describe en la siguiente tabla:

|Nombre|Descripción|
|--|--|
|**PreValidation**<br />Fase: 10|[!INCLUDE [cc-prevalidation-description](../../includes/cc-prevalidation-description.md)]|
|**PreOperation**<br />Fase: 20|[!INCLUDE [cc-preoperation-description](../../includes/cc-preoperation-description.md)]|
|**MainOperation**<br />Fase: 30|Solo para uso interno.|
|**PostOperation**<br />Fase: 40|[!INCLUDE [cc-postoperation-description](../../includes/cc-postoperation-description.md)]|

La fase que debe elegir depende del fin de la extensión. No es necesario aplicar toda la lógica empresarial en un solo paso. Puede aplicar múltiples pasos para que la lógica sobre si permite que una operación continúe esté en la fase **PreValidation** y que la lógica para modificar las propiedades del mensaje puede se produzca en la fase **PostOperation**.

> [!IMPORTANT]
> Una excepción que produzca el código en alguna fase hará que la transacción completa que se revierta. Debe asegurarse de que los posibles casos de excepción los gestiona el código. Si desea cancelar la operación, debe detectar esto en la fase **PreValidation** y solo lanzar una <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> que contenga un mensaje adecuado que explique por qué la operación se ha cancelado.

Se pueden registrarse múltiples extensiones para el mismo mensaje y la fase. En el registro del paso el valor de **Orden de ejecución** determina el orden en el que las diversas extensiones deben procesarse para una fase determinada.

La información sobre los pasos registrados se almacena en la [entidad SdkMessageProcessingStep](reference/entities/sdkmessageprocessingstep.md).

## <a name="event-context"></a>Contexto del evento

Si la extensión es un complemento, recibirá un parámetro que implementa la interfaz <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext>. Esta clase proporciona información sobre la <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext.Stage> para el que está registrado el complemento, así como información sobre el <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext.ParentContext> que proporciona información sobre cualquier operación en otro complemento que activó la operación actual.

Si la extensión es un webhook o extremo de bus de Azure Service, los datos que se enviarán al extremo registrado estarán en el formulario de un <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext> que implementa ambos <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext> y <xref:Microsoft.Xrm.Sdk.IExecutionContext>

### <a name="information-about-the-operation"></a>Información acerca de la operación

Las propiedades de la interfaz <xref:Microsoft.Xrm.Sdk.IExecutionContext> son las que ofrecen la mayor parte de los detalles sobre el operación que se ha producido.

Dos de las propiedades clave acerca del evento se encuentran en las propiedades <xref:Microsoft.Xrm.Sdk.IExecutionContext.InputParameters> y <xref:Microsoft.Xrm.Sdk.IExecutionContext.OutputParameters>. Estos valores <xref:Microsoft.Xrm.Sdk.ParameterCollection> contienen los datos de la operación.

Todas las propiedades de <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext> son de solo lectura, pero la extensión puede modificar el contenido de las propiedades que son colecciones.

En las fases **PreValidation** y **PreOperation**, la propiedad <xref:Microsoft.Xrm.Sdk.IExecutionContext.InputParameters> contiene los parámetros de la clase <xref:Microsoft.Xrm.Sdk.OrganizationRequest>.

En la fase **PostOperation**, <xref:Microsoft.Xrm.Sdk.IExecutionContext.OutputParameters> contiene los parámetros de la clase <xref:Microsoft.Xrm.Sdk.OrganizationResponse> que devolvió la operación.

### <a name="shared-variables"></a>Variables compartidas

La propiedad <xref:Microsoft.Xrm.Sdk.IExecutionContext.SharedVariables> permite incluir los datos que se pueden pasar de un complemento a un paso que se produce después en la canalización de ejecuciones. Dado que este es un valor de <xref:Microsoft.Xrm.Sdk.ParameterCollection>, los complementos pueden agregar, leer o modificar propiedades para compartir datos con pasos posteriores.

### <a name="entity-images"></a>Imágenes de entidad

Al registrar una paso para un complemento que incluye una entidad como uno de los parámetros, tiene la opción de especificar que una copia de los datos de la entidad se incluya como *instantánea* o imagen mediante las propiedades <xref:Microsoft.Xrm.Sdk.IExecutionContext.PreEntityImages> y/o <xref:Microsoft.Xrm.Sdk.IExecutionContext.PostEntityImages>.

Estos datos proporcionan un punto de comparación para los datos de entidad mientras atraviesan la canalización de eventos. El uso de estas imágenes proporciona un rendimiento mucho mejor que incluir código en un complemento para recuperar una entidad solo para comparar los valores de atributo



