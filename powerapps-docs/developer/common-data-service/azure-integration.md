---
title: Integración de Azure (Common Data Service) | Microsoft Docs
description: <Description>
ms.custom: ''
ms.date: 06/01/2019
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
ms.openlocfilehash: 46f7c5506f8c26a70188e8b3cec59b26bf13cb1e
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861861"
---
# <a name="azure-integration"></a>Integración de Azure

Common Data Service admite la integración con Azure. Los desarrolladores pueden registrar complementos con Common Data Service que pueden pasar datos de mensajes en tiempo de ejecución, conocidos como el contexto de la ejecución, a una o varias soluciones de Azure en la nube. Esto es especialmente importante porque Azure es una de las dos soluciones compatibles para comunicar el contexto de tiempo de ejecución obtenido en un complemento a las aplicaciones de línea de negocio (LOB) externas. La otra solución es la funcionalidad de acceso a los extremos personalizados externos desde un complemento registrado en el espacio asilado.

Azure Service Bus proporciona un canal de comunicación seguro y fiable entre datos en tiempo de ejecución de Common Data Service y aplicaciones externas de línea de negocio (LOB) basadas en la nube. Esta funcionalidad es especialmente útil para mantener los sistemas dispares de Common Data Service u otros servidores de Common Data Service sincronizados con los cambios en los datos profesionales.

## <a name="key-elements-of-the-connection"></a>Elementos principales de la conexión  

 Los elementos clave que implementan la conexión entre Common Data Service y Azure Service Bus se describen más adelante. Un diagrama en la siguiente sección muestra estos elementos en funcionamiento.  
  
### <a name="data-context"></a>Contexto de datos 

 El *contexto de datos* contiene los datos de negocio que se procesan como parte de la operación actual de Common Data Service. Este proceso se inició cuando se efectuó una solicitud para realizar una determinada operación por un usuario, un flujo de trabajo, o una aplicación, a la plataforma de Dynamics 365. El contexto de datos se pasa a los complementos o las actividades de flujo de trabajo personalizadas que estén registradas con la canalización de eventos para ejecutarse en la combinación de solicitud y entidad específica que se esté procesando actualmente. El contexto de datos es del tipo <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext> cuando se está pasando con la canalización de ejecución del evento y <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext> cuando se publica en el bus de servicio.  
  
 El contexto de datos contenido en el mensaje que se publica en el Azure Service Bus se puede formatear en XML o JSON además del formato binario .NET predeterminado. Esto proporciona interoperabilidad multiplataforma donde los clientes no .NET hospedados en Azure pueden leer datos de Common Data Service desde el bus de servicio. 

> [!IMPORTANT]
> Cuando el tamaño de la carga HTTP completa supera 192 Kb, las propiedades siguientes se quitarán:
>
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.ParentContext>
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.InputParameters>
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.PreEntityImages>
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.PostEntityImages>
>
> Algunas operaciones no incluyen estas propiedades. 
>
> - Si el tamaño de la carga está por debajo de 192 Kb después de quitar los datos adicionales, una propiedad `MessageMaxSizeExceeded` adicional se agrega al [BrokeredMessage](/dotnet/api/microsoft.servicebus.messaging.brokeredmessage) enviado por el sistema. Esto indica que algunos de los datos se han truncado.
> - Si el tamaño de la carga supera 192 Kb después de quitar los datos adicionales, se produce un error y el mensaje no se envía.
  
 Para obtener más información acerca de las tecnologías descritas anteriormente, consulte:
 - [Canalización de ejecución del evento](event-framework.md#event-execution-pipeline)
 - [Escriba una aplicación de escucha para una solución de Microsoft Azure](write-listener-application-azure-solution.md).  
  
### <a name="plug-ins"></a>Complementos

Los complementos son uno de los dos métodos usados para iniciar la publicación del mensaje que contiene el contexto de datos en el Azure Service Bus, el otro método es una actividad de flujo de trabajo personalizada. Existen dos tipos de complementos compatibles con la característica de conexión Common Data Service-Azure: predefinidos (OOB) y personalizados. En ambos casos, se recomienda registrar el complemento para ejecutarlo asincrónicamente para obtener un rendimiento óptimo del sistema.  
  
Se proporciona un complemento OOB apto para Azure con Common Data Service y se puede registrar a través de la herramienta de registro de complementos. Este complemento se ejecuta en plena confianza con la plataforma de Common Data Service. Debe registrar un "paso" de complemento"en la canalización de ejecución de eventos que identifique la combinación de mensaje y entidad que desencadena la ejecución del complemento y la realización de la notificación de publicación. Cuando se ejecuta, el complemento notifica el servicio asincrónico con un servicio de notificación de extremo de servicio (<xref:Microsoft.Xrm.Sdk.IServiceEndpointNotificationService>), para publicar el contexto de datos de la solicitud actual en el Azure Service Bus.  
  
También puede escribir su propio complemento personalizado que sea "compatible con Azure". El complemento personalizado se ejecuta en el modo de confianza parcial en el espacio aislado. Un complemento personalizado puede iniciar la publicación del contexto de datos en el bus de servicio a través del servicio de notificación de extremo de servicio. Si agrega código para llamar a este servicio hará que el complemento sea "apto para Azure". 
 
Para obtener más información acerca de los complementos en general, consulte [Escribir un complemento](write-plug-in.md). Para obtener más información acerca de los complementos compatibles con Azure, consulte [Escribir un complemento con Azure personalizado](write-custom-azure-aware-plugin.md).  
  
### <a name="custom-workflow-activities"></a>Actividades personalizadas del flujo de trabajo

De forma similar a los complementos, las actividades de flujo de trabajo personalizadas se pueden escribir para iniciar la publicación del contexto de datos de mensaje de la solicitud actual en el Azure Service Bus utilizando el servicio de notificación de extremo de servicio. Más información: [Extensiones de flujo de trabajo](workflow/workflow-extensions.md) 
  
### <a name="asynchronous-service"></a>Servicio asincrónico

Una vez notificado por el servicio de notificación de extremo de servicio, el servicio asincrónico controla la publicación del contexto de datos del mensaje de solicitud que está procesando actualmente la canalización de ejecución de eventos en el Azure Service Bus. Cada publicación la realiza un trabajo del sistema del servicio asincrónico. Un usuario puede ver el estado de cada trabajo del sistema con la vista **Trabajos del sistema** de la aplicación web de Power Apps.  
  
Para obtener más información sobre el servicio asincrónico consulte [Servicio asincrónico](asynchronous-service.md).  
  
### <a name="microsoft-azure-service-bus"></a>Bus de servicio de Microsoft Azure

El bus de servicio retransmite el contexto de datos del mensajes de solicitud entre Common Data Service y las aplicaciones de escucha de la solución de Azure Service Bus. El bus de servicio también proporciona seguridad de datos de manera que solo las aplicaciones autorizadas puedan tener acceso a los datos de Dynamics 365 publicados.  La autorización de aplicaciones Common Data Service para publicar el contexto de datos en el bus de servicio y para que las aplicaciones de escucha lo lean se administra mediante firmas de acceso compartido (SAS) de Azure.  
  
  
 Para obtener más información acerca del bus de servicio, consulte [Bus de servicio](https://azure.microsoft.com/services/service-bus/). Para obtener más información sobre la autorización del bus de servicio, consulte [Autenticación y autorización de bus de servicio](https://azure.microsoft.com/documentation/articles/service-bus-authentication-and-authorization/).  
  
### <a name="microsoft-azure-solution"></a>Solución Microsoft Azure

Para que la conexión Common Data Service y la conexión de Azure funcionen, debe tener al menos una solución en una cuenta de soluciones de Azure Service Bus, donde la solución contenga uno o varios extremos de servicio. Para un contrato de extremo de retransmisión, una aplicación de escucha que es "compatible con Common Data Service" debe escuchar activamente en el extremo para la solicitud de Common Data Service en el bus del servicio. Para un contrato de extremo de cola, un agente de escucha no tiene que escuchar activamente. Un agente de escucha es compatible con Common Data Service al vincularlo con el ensamblado de <xref:Microsoft.Xrm.Sdk>, de manera que se define el tipo <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext>. Más información: [Escribir un agente de escucha para una solución de Microsoft Azure](write-listener-application-azure-solution.md).  
  
Common Data Service admite el envío de datos de eventos a una solución Azure Event Hubs. Más información acerca de los centros de eventos, consulte [Trabajar con datos de eventos en la solución del Centro de eventos de Azure](work-event-data-azure-event-hub-solution.md).  
  
<a name="bkmk_describing"></a>  
 
## <a name="common-data-service-to-service-bus-scenario"></a>Escenario de Common Data Service para el bus de servicio  

Ahora vamos a identificar un escenario que implementa los componentes de conexión mencionados anteriormente. Como requisito previo, SAS se ha configurado para reconocer a aplicaciones Common Data Service como el emisor compatible y la solución de bus de servicio de Azure se ha configurado con reglas para permitir que Common Data Service pueda publicar en el extremo donde está el agente de escucha.  
  
En el siguiente diagrama se muestran los elementos físicos que constituyen el escenario.  
  
![Escenario de Dynamics 365 para el bus de servicio](media/crm-v5s-az.png "Escenario de Common Data Service para el bus de servicio")  
  
La secuencia de eventos como se identifica en este diagrama es la siguiente:  
  
1. Una aplicación de escucha está registrada en un extremo de la solución de Azure Service Bus y comienza la escucha activa para el contexto remoto de ejecución de Common Data Service en el bus del servicio.  

2. Un usuario realiza una operación determinada en Common Data Service que desencadena la ejecución del complemento OOB registrado o un complemento compatible de Azure personalizado. El complemento inicia una publicación, a través de un trabajo del sistema de servicio asincrónico, del contexto de datos de solicitud actual para el bus del servicio.  
3. Se autentican las notificaciones publicadas por Common Data Service. A continuación, el bus del servicio retransmite el contexto remoto de ejecución al agente de escucha. El agente de escucha procesa la información de contexto y realiza alguna tarea de negocio relacionada con esa información. El bus de servicio notifica al servicio asincrónico de una publicación correcta y establece el trabajo del sistema relacionado con un estado completado.  
  
<a name="bkmk_establising"></a>  

## <a name="establish-a-contract-between-common-data-service-and-an-azure-solution"></a>Establecer un contrato entre Common Data Service y una solución de Azure

Para cada extremo de la solución, configure un contrato que defina la administración de estos contextos remotos de ejecución "mensajes" en el bus del servicio y la seguridad que deben usarse en el extremo. Los mensajes de bus del servicio se reciben en un extremo mediante uno de los contratos admitidos que se muestran a continuación.  
  
### <a name="queue"></a>Cola

Un contrato de cola proporciona una cola de mensajes en la nube. Con un contrato de cola, un agente de escucha no tiene que escuchar activamente los mensajes del extremo. Para las colas, hay una lectura destructiva y una lectura no destructiva. Una lectura destructiva lee un mensaje disponible de la cola y el mensaje se quita. Una lectura no destructiva no quita un mensaje de la cola.  
  
El tipo de cola compatible con Common Data Service se llama cola persistente. Las colas persistentes tienen una duración de la disponibilidad del mensaje larga pero finita que se puede especificar en el código.  
  
### <a name="one-way"></a>Unidireccional

Un contrato unidireccional necesita un agente de escucha activo. Si no hay una escucha activa en un extremo, la publicación en el bus de servicio no se realizará correctamente. Common Data Service reintentará la publicación en intervalos de tiempo exponencialmente cada vez más grandes hasta que el trabajo del sistema asincrónico que está publicando la solicitud se anule eventual y su estado se establezca como "error".  
  
### <a name="two-way"></a>Bidireccional

Un contrato bidireccional se asemeja a un contrato unidireccional, salvo que el valor de una cadena se puede devolver desde una escucha al complemento o la actividad de flujo de trabajo personalizada que inició la publicación.  
  
### <a name="rest"></a>REST

Un contrato REST se asemeja a un contrato bidireccional en un extremo REST.  
  
### <a name="topic"></a>Tema

Similar a una cola salvo que uno o varios agentes de escucha pueden suscribirse para recibir mensajes del tema.  
  
### <a name="event-hub"></a>Centro de eventos de 

Este tipo de contrato se aplica a las soluciones del centro de eventos de Azure.  
  
> [!IMPORTANT]
>  Para usar estos contratos, debe especificar sus aplicaciones de escucha mediante el [SDK de Azure](https://www.windowsazure.com/develop/downloads/) versión 1.7 o posterior.  
  
Identificar el tipo de seguridad que usa un contrato forma parte de la configuración del contrato. Un contrato puede usar la seguridad de transporte, que usa Seguridad de la capa de transporte (TLS) o Capa de sockets seguros (SSL) (https).  
  
La autenticación de notificaciones se usa para un acceso seguro al bus del servicio. La notificación que se usa para realizar la autenticación en el bus del servicio se genera a partir de Common Data Service y está firmada por el certificado AppFabricIssuer que se especifica en la base de datos de configuración de Common Data Service.  
  
<a name="bkmk_management"></a>

## <a name="manage-run-time-errors"></a>Administración de errores en tiempo de ejecución  

Si se produce un error después de intentar realizar una publicación en el bus del servicio, compruebe el estado del trabajo del sistema relacionado en la aplicación web para obtener más información sobre el error. Si el bus del servicio está inactivo o un agente de escucha/extremo no está disponible, el mensaje actual que se está procesando en Common Data Service no se publicará en el bus. El servicio asincrónico seguirá intentando publicar el mensaje en un patrón exponencial donde al principio tratará de realizar la publicación con frecuencia y después lo intentará en intervalos cada vez más largos. Para un error interno de Common Data Service, las publicaciones del mensaje no se intentan. Para servicio del bus externo o error de red, el trabajo del sistema relacionado estará en un estado de "espera".