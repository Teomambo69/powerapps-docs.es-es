---
title: Escribir una aplicación de escucha para una solución de Microsoft Azure (Common Data Service) | Microsoft Docs
description: El tema describe cómo escribir una aplicación de escucha para un solución de Azure que pueda leer y procesar mensajes de Common Data Service de Dynamics 365 (online) que se publican para Azure Service Bus.
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: cf68e0a9-c240-59e7-c501-68cbfa0df455
author: brandonsimons
ms.author: jdaly
manager: ryjones
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="write-a-listener-application-for-a-azure-solution"></a>Escriba una aplicación de escucha para una solución de Azure

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/write-listener-application-azure-solution -->

Este tema describe cómo escribir una aplicación de escucha para un solución de Azure que pueda leer y procesar mensajes de Common Data Service de Dynamics 365 (online) que se publican para Azure Service Bus. Como requisito previo, debería familiarizarse con la manera de escribir un escucha de Azure Service Bus antes de intentar comprender los detalles de un escucha de Dynamics 365. Para obtener más información, consulte la [Documentación del bus de servicio de Azure](https://azure.microsoft.com/en-us/documentation/services/service-bus/).  
  
<a name="bkmk_writequeued"></a>

## <a name="write-a-queue-listener"></a>Escribir un escucha de cola

Una *cola* de mensajes es un repositorio de mensajes recibidos de un extremo de bus de servicio. Un *escucha de cola* es una aplicación que lee y procesa los mensajes en cola. Puesto que los mensajes de bus de servicio se almacenan en una cola, un escucha no tiene que escuchar activamente para que los mensajes sean recibidos en la cola. Un escucha de cola se puede iniciar una vez que los mensajes han llegado a la cola y seguir procesando los mensajes. Otros tipos de escuchas descritos en la siguiente sección deben escuchar activamente o perderán la oportunidad de leer un mensaje. Estos mensajes se pueden originar desde Dynamics 365 o en algún otro origen. 
  
> [!IMPORTANT]
>  Al escribir un escucha de cola, compruebe cada acción del encabezado del mensaje para determinar si el mensaje se originó desde Dynamics 365. Para más información sobre cómo hacer esto, consulte [Filtro de mensajes](write-listener-application-azure-solution.md#filter).  
  
Puede hacer una lectura destructiva del mensaje usando [Recibir](https://docs.microsoft.com/dotnet/api/microsoft.servicebus.messaging.queueclient?redirectedfrom=MSDN&view=azure-dotnet#Microsoft_ServiceBus_Messaging_QueueClient_Receive) en modo [ReceiveAndDelete](https://docs.microsoft.com/dotnet/api/microsoft.servicebus.messaging.receivemode?redirectedfrom=MSDN&view=azure-dotnet#microsoft_servicebus_messaging_receivemode), donde el mensaje se lee y se quita de la cola, o una lectura no destructiva con el modo [PeekLock](https://docs.microsoft.com/dotnet/api/microsoft.servicebus.messaging.receivemode?redirectedfrom=MSDN&view=azure-dotnet#microsoft_servicebus_messaging_receivemode), donde el mensaje se lee, pero se mantiene en la cola. El código de ejemplo persistente de escucha de cola proporcionado en este SDK realiza una lectura destructiva. Para obtener más información acerca de la lectura de mensajes desde una cola, consulte [Cómo recibir mensajes de una cola](http://azure.microsoft.com/documentation/articles/service-bus-dotnet-how-to-use-queues/#how-to-receive-messages-from-a-queue).  
  
Un *tema* es similar a una cola, pero implementa un modelo de publicación o suscripción. Puede haber uno o varios escuchas suscritos al tema que reciben mensajes de su cola. Más información: [Colas, temas y suscripciones](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-queues-topics-subscriptions)  
  
> [!IMPORTANT]
>  Para usar estos contratos de cola o tema, debe escribir sus aplicaciones de escucha mediante [Azure SDK](http://azure.microsoft.com/downloads/archive-net-downloads/) versión 1.7 o superior.  
  
El uso de colas y temas en el diseño de software multisistema puede dar lugar al desemparejamiento del sistema. Si la aplicación de escucha llega a estar no disponible, la entrega del mensaje de Dynamics 365 se realizará correctamente y la aplicación de escucha podrá seguir procesando el mensaje de la cola cuando vuelva a estar en línea. [!INCLUDEMás información: [Colas, temas y suscripciones](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-queues-topics-subscriptions)  
  
<a name="bkmk_writeoneway"></a>

## <a name="write-a-one-way-two-way-or-rest-listener"></a>Escribir un escucha unidireccional, bidireccional o REST

Además de la escucha de cola descrita anteriormente, puede escribir un escucha para otros tres contratos de bus de servicio admitidos por Dynamics 365: unidireccional, bidireccional y REST. Un módulo de escucha unidireccional puede leer y procesar un mensaje publicado en el bus de servicio. Un módulo de escucha bidireccional puede hacer lo mismo, pero también puede devolver una cadena de información a Dynamics 365. Un escucha REST es la misma que la escucha bidireccional, salvo que trabaja con un extremo REST . Tenga en cuenta que estos escuchas deben escuchar activamente en un extremo de servicio para leer un mensaje enviado sobre el bus de servicio. Si el escucha no está escuchando cuando Dynamics 365 intenta publicar un mensaje en el bus de servicio, el mensaje no se enviará.
  
La escritura de un escucha está estructurada sobre lo que en inglés se conoce como ABC: dirección, enlace y contrato. 

### <a name="one-way-listener"></a>Módulo de escucha unidireccional
  
- Dirección: URI de servicio  
  
- Enlace: [WS2007HttpRelayBinding](https://docs.microsoft.com/dotnet/api/microsoft.servicebus.ws2007httprelaybinding?redirectedfrom=MSDN&view=azure-dotnet#microsoft_servicebus_ws2007httprelaybinding)  
  
- Contrato: <xref:Microsoft.Xrm.Sdk.IServiceEndpointPlugin>  
  
Una vez registrado el escucha con un extremo, el método <xref:Microsoft.Xrm.Sdk.IServiceEndpointPlugin.Execute*> de escucha se invoca siempre que Dynamics 365 publique un mensaje en el bus de servicio. El método `Execute` no devuelve los datos de la llamada del método. Para obtener más información, consulte el ejemplo de escucha unidireccional, [Ejemplo: escucha unidireccional](org-service/samples/one-way-listener.md).  
  
### <a name="two-way-listener"></a>Módulo de escucha bidireccional
  
- Dirección: URI de servicio  
  
- Enlace: [WS2007HttpRelayBinding](https://docs.microsoft.com/dotnet/api/microsoft.servicebus.ws2007httprelaybinding?redirectedfrom=MSDN&view=azure-dotnet#microsoft_servicebus_ws2007httprelaybinding)  
  
- Contrato: <xref:Microsoft.Xrm.Sdk.ITwoWayServiceEndpointPlugin>  
  
Para este contrato bidireccional, el método <xref:Microsoft.Xrm.Sdk.ITwoWayServiceEndpointPlugin.Execute*> devuelve una cadena de llamada del método. Para obtener más información, consulte el ejemplo de escucha bidireccional, [Ejemplo: escucha bidireccional](org-service/samples/two-way-listener.md).  
  
### <a name="rest-listener"></a>Escucha de REST
  
- Dirección: URI de servicio  
  
- Enlace: [WebHttpRelayBinding](https://docs.microsoft.com/dotnet/api/microsoft.servicebus.webhttprelaybinding?redirectedfrom=MSDN&view=azure-dotnet#microsoft_servicebus_webhttprelaybinding)
  
- Contrato: <xref:Microsoft.Xrm.Sdk.IWebHttpServiceEndpointPlugin>  
  
Para el contrato de REST, el método <xref:Microsoft.Xrm.Sdk.IWebHttpServiceEndpointPlugin.Execute*> devuelve una cadena de la llamada al método. Para obtener más información, consulte el ejemplo de escucha REST, [Ejemplo: escucha REST](org-service/samples/rest-listener.md). Tenga en cuenta que en el ejemplo de escucha REST, se crea una instancia de <xref:System.ServiceModel.Web.WebServiceHost> y no un <xref:System.ServiceModel.ServiceHost> como se hizo en el ejemplo bidireccional.
  
> [!NOTE]
>  Al usar el complemento predefinido (ServiceBusPlugin) con una escucha REST bidireccional, el complemento no usa los datos de cadena devueltos desde el escucha. Sin embargo, un complemento personalizado basado en Azure podría usar esta información.  
> 
>  Al trabajar con ejemplos de escucha, el secreto de emisor que se le solicitará que escriba es la clave de administración de Azure Service Bus. El enlace de federación HTTP WS2007 usa el modo `token` y el protocolo WS-Trust 1.3.  
  
<a name="filter"></a>

## <a name="filter-messages"></a>Mensajes de filtro

Hay un contenedor de propiedades con información adicional agregado a la propiedad [Propiedades](https://msdn.microsoft.com/library/windowsazure/microsoft.servicebus.messaging.brokeredmessage.properties.aspx) de cada mensaje negociado enviado desde Dynamics 365 (online) y Dynamics 365 (online). El contenedor de propiedades, disponibles con extremos de cola, retransmisión y contrato de tema, contiene la siguiente información:  
  
- URI de organización  
  
- Id. de usuario que llama  
  
- Iniciando Id. de usuario  
  
- Nombre lógico de la entidad  
  
- Nombre de solicitud  
  
Esta información identifica la organización, el usuario, la entidad y la solicitud de mensajes que está procesando Dynamics 365 y que han causado la publicación de un mensaje de bus de servicio. La disponibilidad de esas propiedades indica que el mensaje se envió desde Dynamics 365. El código de escucha puede decidir cómo procesar el mensaje según esos valores.  
  
<a name="bkmk_multiple-formats"></a>
 
## <a name="read-the-data-context-in-multiple-data-formats"></a>Leer el contexto de los datos en varios formatos de datos

El contexto de datos de la operación de Dynamics 365 actual se pasa a la aplicación de escucha de la solución de Azure en el cuerpo de un mensaje del bus de servicio. En versiones anteriores, sólo se admitía un formato binario .NET.  Para la interoperabilidad multiplataforma (no .NET), ahora puede especificar uno de los tres formatos de datos para el cuerpo del mensaje: binario .NET, JSON, o XML.  Este formato se especifica en el atributo [MessageFormat](reference/entities/serviceendpoint.md#BKMK_MessageFormat) de la [Entidad ServiceEndpoint](reference/entities/serviceendpoint.md).
  
Al recibir mensajes, la aplicación de escucha puede leer el contexto de datos en el cuerpo del mensaje según el contentType del mensaje. El código de ejemplo para hacerlo se muestra a continuación.  
  
```csharp
var receivedMessage = inboundQueueClient.Receive(TimeSpan.MaxValue);  
  
if (receivedMessage.ContentType = "application/msbin1")  
{  
    RemoteExecutionContext context = receivedMessage.GetBody<RemoteExecutionContext>();  
}  
else if (receivedMessage.ContentType = "application/json")  
{  
    //string jsonBody = new StreamReader(receivedMessage.GetBody<Stream>(), Encoding.UTF8).ReadToEnd();  
    RemoteExecutionContext contextFromJSON = receivedMessage.GetBody<RemoteExecutionContext>(  
        new DataContractJsonSerializer(typeof(RemoteExecutionContext)));  
}  
else if (receivedMessage.ContentType = "application/xml")  
{  
    //string xmlBody = new StreamReader(receivedMessage.GetBody<Stream>(), Encoding.UTF8).ReadToEnd();  
    RemoteExecutionContext contextFromXML = receivedMessage.GetBody<RemoteExecutionContext>(  
        new DataContractSerializer(typeof(RemoteExecutionContext)));  
}  
```  
  
### <a name="see-also"></a>Vea también

 [Extensiones de Azure](azure-integration.md)   
 [Escribir un complemento personalizado compatible con Azure](write-custom-azure-aware-plugin.md)   
 [Ejemplo: Escucha de cola persistente](org-service/samples/persistent-queue-listener.md)   
 [Ejemplo: escucha unidireccional](org-service/samples/one-way-listener.md)   
 [Ejemplo: Escucha bidireccional](org-service/samples/two-way-listener.md)   
 [Ejemplo: Escucha de REST](org-service/samples/rest-listener.md)   
 [Enviar los datos de Dynamics 365 a través del bus de servicio de Azure](work-data-azure-solution.md)   
 [Trabaje con datos de eventos de Dynamics 365 en la solución del Centro de eventos de Azure](work-event-data-azure-event-hub-solution.md)