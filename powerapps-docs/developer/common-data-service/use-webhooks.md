---
title: Uso de WebHooks para crear controladores externos para eventos de servidor (Common Data Service) | Microsoft Docs
description: Puede enviar datos sobre eventos que tienen lugar en el servidor a una aplicación web mediante webhooks. Webhooks es un patrón HTTP ligero para conectar servicios y API web con un modelo de publicación/suscripción. Los remitentes de webhook envían a los receptores notificaciones sobre eventos realizando solicitudes a los extremos de los receptores con información sobre los eventos.
ms.custom: ''
ms.date: 09/04/2019
ms.reviewer: pehecke
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
ms.openlocfilehash: 360bf7689406195c369e74b0f255cd8db32bda8d
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155168"
---
# <a name="use-webhooks-to-create-external-handlers-for-server-events"></a>Utilice webhooks para crear controladores externos para eventos de servidor

Con Common Data Service puede enviar datos sobre eventos que tienen lugar en el servidor a una aplicación web mediante webhooks. Webhooks es un patrón HTTP ligero para conectar servicios y API web con un modelo de publicación/suscripción. Los remitentes de webhook envían a los receptores notificaciones sobre eventos realizando solicitudes a los extremos de los receptores con información sobre los eventos.

Los webhooks permiten a desarrolladores e ISV integrar datos de Common Data Service en su propio código personalizado hospedado en servicios externos. Con el modelo de webhooks, puede proteger el extremo usando un encabezado de autenticación o claves de parámetro de string de consulta. Esto es más sencillo que el modelo de autenticación SAS que se puede usar actualmente para la integración de Azure Service Bus.

Cuando decida entre el modelo de webhook y la integración de Azure Service Bus, aquí se muestran algunos elementos a tener en cuenta:

- Azure Service Bus funciona para un procesamiento de alta escala y proporciona un mecanismo completo de puesta en cola si Common Data Service está impulsando muchos eventos.
- Los webhooks solo se pueden escalar al punto en el que el servicio web hospedado puede controlar los mensajes.
- Los webhooks permiten pasos sincrónicos y asincrónicos. Azure Service Bus solo permite pasos asincrónicos.
- Los webhooks envian solicitudes POST con carga JSON y pueden ser consumidos por cualquier lenguaje de programación o aplicación web hospedada en cualquier lugar.
- Los webhooks y Azure Service Bus se pueden invocar desde un complemento o una actividad personalizada de flujo de trabajo.


## <a name="get-started"></a>Introducción

Existen tres partes para utilizar webhooks:

- Crear o configurar un servicio para consumir solicitudes de webhook.
- Registrar paso de webhook en el servicio de Common Data Service o
- Llamar un webhook desde un complemento o actividad personalizada de flujo de trabajo. 

### <a name="start-by-registering-a-test-webhook"></a>Empezar registrando un webhook de prueba

Para comprender cómo crear y configurar un servicio para consumir una solicitud de webhook de Common Data Service, conviene empezar entendiendo cómo registrar un webhook. Más información: [Registrar un webhook](register-web-hook.md)

Cuando haya registrado un webhook de ejemplo puede usar un sitio de registro de solicitudes para explorar los datos contextuales que se pasarán. Más información: [Probar registro de webhook con sitio de registro de solicitudes](test-webhook-registration.md)

> [!TIP]
> Completar los pasos para registrar un webhook de prueba y examinar los datos contextual que se pasan le ayudará a hacer más fácil de entender el resto de la información de este tema. Complete estos pasos y vuelva a este tema.

<a name="create-or-configure"></a>

## <a name="create-or-configure-a-service-to-consume-webhook-requests"></a>Crear o configurar un servicio para consumir solicitudes de webhook

Los webhooks son simplemente un patrón que se puede aplicar mediante una gran variedad de tecnologías. No es necesario utilizar marcos, plataformas o lenguajes de programación. Utilice las capacidades y conocimiento que tiene para proporcionar la solución apropiada. 

Las [Funciones de Azure](https://azure.microsoft.com/services/functions/) proporcionan una forma excelente de ofrecer una solución mediante webhooks, pero no es un requisito. Esta sección no proporcionará instrucciones para una solución específica, sino que describirá los datos que se transmitirán a su servicio y permitirá añadir valor a este.

Como se muestra en [Probar el registro de webhook con un sitio de registro de solicitud](test-webhook-registration.md), puede registrar un paso de webhook de prueba y usar el sitio de registro de solicitud para capturar los tipos específicos de datos que pueda procesar su aplicación. 

### <a name="data-passed-to-the-service"></a>Datos que se transmiten al servicio

Existen tres tipos de datos en la solicitud: cadena de consulta, datos de encabezado y cuerpo de la solicitud.

#### <a name="query-string"></a>Cadena de consulta

El único tipo de datos que se transmitirá como una cadena de consulta pueden ser los valores de autenticación transmitidos si el webhook está configurado para usar las opciones **WebhookKey** o **HttpQueryString** como se describe en las [Opciones de autenticación](register-web-hook.md#authentication-options). 

#### <a name="header-data"></a>Datos del encabezado

Si selecciona la opción de autenticación **HttpHeader**, deberá usar los pares de clave/valor que requiera su servicio.

En la siguiente tabla aparecen otros datos que es posible que encuentre transmitidos a su servicio:


|Key|Descripción del valor|
|---------|---------|
|`x-request-id`|Un identificador único para la solicitud|
|`x-ms-dynamics-organization`|El nombre del inquilino que envía la solicitud|
|`x-ms-dynamics-entity-name`|El nombre lógico de la entidad transmitida a los datos de contexto de ejecución.|
|`x-ms-dynamics-request-name`|El nombre del evento para el que se registró el paso de webhook.|
|`x-ms-correlation-request-id`|Identificador único para realizar un seguimiento de cualquier tipo de extensión. La plataforma utiliza esta propiedad para la prevención de bucle infinito. En la mayoría de casos, esta propiedad se puede omitir. Este valor se puede utilizar cuando se trabaja con el soporte técnico, ya que se puede usar para consultar telemetría y comprender lo que ocurrió durante toda la operación.
|`x-ms-dynamics-msg-size-exceeded`|Se envía solo cuando el tamaño de la carga HTTP supera los 256 KB.|


#### <a name="request-body"></a>Cuerpo de la solicitud

El cuerpo contendrá una cadena que representa el valor JSON de una instancia de la clase <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext>. Estos son los mismos datos que se transmiten a las integraciones de bus del servicio de Azure. 

El servicio que cree debe analizar estos datos para extraer los elementos relevantes de información para que su servicio proporcione su función. Cómo decidir analizar estos datos depende de la tecnología que utilice y de sus preferencias.

> [!IMPORTANT]
> Debido a determinadas optimizaciones del bus de servicio, no se recomienda que los desarrolladores de .NET deserialicen el cuerpo de solicitud del mensaje con formato JSON a un objeto <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext>. En su lugar, use [JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm) para analizar el cuerpo del mensaje.

El siguiente es un ejemplo de los datos JSON serializados transmitidos para un paso registrado con las propiedades siguientes:


|Propiedad|Descripción|
|---------|---------|
|**Mensaje**|Actualizar|
|**Entidad principal**|contacto|
|**Entidad secundaria**|ninguna|
|**Atributos de filtro**|firstname,lastname|
|**Ejecutar en contexto de usuario**|Usuario que llama|
|**Pedido de ejecución**|1|
|**Fase de canalización de eventos de ejecución**|PostOperation|
|**Modo de ejecución**|Asincrónico|

```json
{
    "BusinessUnitId": "e2b9dd85-e89e-e711-8122-000d3aa2331c",
    "CorrelationId": "b374239d-4233-41a9-8b17-a86cb4f737b5",
    "Depth": 1,
    "InitiatingUserId": "75c2dd85-e89e-e711-8122-000d3aa2331c",
    "InputParameters": [{
        "key": "Target",
        "value": {
            "__type": "Entity:http:\/\/schemas.microsoft.com\/xrm\/2011\/Contracts",
            "Attributes": [{
                "key": "firstname",
                "value": "James"
            }, {
                "key": "contactid",
                "value": "6d81597f-0f9f-e711-8122-000d3aa2331c"
            }, {
                "key": "fullname",
                "value": "James Glynn (sample)"
            }, {
                "key": "yomifullname",
                "value": "James Glynn (sample)"
            }, {
                "key": "modifiedon",
                "value": "\/Date(1506384247000)\/"
            }, {
                "key": "modifiedby",
                "value": {
                    "__type": "EntityReference:http:\/\/schemas.microsoft.com\/xrm\/2011\/Contracts",
                    "Id": "75c2dd85-e89e-e711-8122-000d3aa2331c",
                    "KeyAttributes": [],
                    "LogicalName": "systemuser",
                    "Name": null,
                    "RowVersion": null
                }
            }, {
                "key": "modifiedonbehalfby",
                "value": null
            }],
            "EntityState": null,
            "FormattedValues": [],
            "Id": "6d81597f-0f9f-e711-8122-000d3aa2331c",
            "KeyAttributes": [],
            "LogicalName": "contact",
            "RelatedEntities": [],
            "RowVersion": null
        }
    }],
    "IsExecutingOffline": false,
    "IsInTransaction": false,
    "IsOfflinePlayback": false,
    "IsolationMode": 1,
    "MessageName": "Update",
    "Mode": 1,
    "OperationCreatedOn": "\/Date(1506409448000-0700)\/",
    "OperationId": "4af10637-4ea2-e711-8122-000d3aa2331c",
    "OrganizationId": "4ef5b371-e89e-e711-8122-000d3aa2331c",
    "OrganizationName": "OrgName",
    "OutputParameters": [],
    "OwningExtension": {
        "Id": "75417616-4ea2-e711-8122-000d3aa2331c",
        "KeyAttributes": [],
        "LogicalName": "sdkmessageprocessingstep",
        "Name": null,
        "RowVersion": null
    },
    "ParentContext": {
        "BusinessUnitId": "e2b9dd85-e89e-e711-8122-000d3aa2331c",
        "CorrelationId": "b374239d-4233-41a9-8b17-a86cb4f737b5",
        "Depth": 1,
        "InitiatingUserId": "75c2dd85-e89e-e711-8122-000d3aa2331c",
        "InputParameters": [{
            "key": "Target",
            "value": {
                "__type": "Entity:http:\/\/schemas.microsoft.com\/xrm\/2011\/Contracts",
                "Attributes": [{
                    "key": "firstname",
                    "value": "James"
                }, {
                    "key": "contactid",
                    "value": "6d81597f-0f9f-e711-8122-000d3aa2331c"
                }],
                "EntityState": null,
                "FormattedValues": [],
                "Id": "6d81597f-0f9f-e711-8122-000d3aa2331c",
                "KeyAttributes": [],
                "LogicalName": "contact",
                "RelatedEntities": [],
                "RowVersion": null
            }
        }, {
            "key": "SuppressDuplicateDetection",
            "value": false
        }],
        "IsExecutingOffline": false,
        "IsInTransaction": false,
        "IsOfflinePlayback": false,
        "IsolationMode": 1,
        "MessageName": "Update",
        "Mode": 1,
        "OperationCreatedOn": "\/Date(1506409448000-0700)\/",
        "OperationId": "4af10637-4ea2-e711-8122-000d3aa2331c",
        "OrganizationId": "4ef5b371-e89e-e711-8122-000d3aa2331c",
        "OrganizationName": "OneFarm",
        "OutputParameters": [],
        "OwningExtension": {
            "Id": "75417616-4ea2-e711-8122-000d3aa2331c",
            "KeyAttributes": [],
            "LogicalName": "sdkmessageprocessingstep",
            "Name": null,
            "RowVersion": null
        },
        "ParentContext": null,
        "PostEntityImages": [],
        "PreEntityImages": [],
        "PrimaryEntityId": "6d81597f-0f9f-e711-8122-000d3aa2331c",
        "PrimaryEntityName": "contact",
        "RequestId": null,
        "SecondaryEntityName": "none",
        "SharedVariables": [{
            "key": "ChangedEntityTypes",
            "value": [{
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "feedback",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "contract",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "salesorder",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "connection",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "socialactivity",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "postfollow",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "incident",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "invoice",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "entitlement",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "lead",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "opportunity",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "quote",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "socialprofile",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "contact",
                "value": "Update"
            }]
        }],
        "Stage": 30,
        "UserId": "75c2dd85-e89e-e711-8122-000d3aa2331c"
    },
    "PostEntityImages": [{
        "key": "AsynchronousStepPrimaryName",
        "value": {
            "Attributes": [{
                "key": "fullname",
                "value": "James Glynn (sample)"
            }, {
                "key": "contactid",
                "value": "6d81597f-0f9f-e711-8122-000d3aa2331c"
            }],
            "EntityState": null,
            "FormattedValues": [],
            "Id": "6d81597f-0f9f-e711-8122-000d3aa2331c",
            "KeyAttributes": [],
            "LogicalName": "contact",
            "RelatedEntities": [],
            "RowVersion": null
        }
    }],
    "PreEntityImages": [],
    "PrimaryEntityId": "6d81597f-0f9f-e711-8122-000d3aa2331c",
    "PrimaryEntityName": "contact",
    "RequestId": null,
    "SecondaryEntityName": "none",
    "SharedVariables": [],
    "Stage": 40,
    "UserId": "75c2dd85-e89e-e711-8122-000d3aa2331c"
}
```
> [!IMPORTANT]
> Cuando el tamaño de toda la carga HTTP supera 256 KB, se incluirá el encabezado `x-ms-dynamics-msg-size-exceeded` y se eliminarán las siguientes propiedades <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext>:
> 
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.ParentContext>
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.InputParameters>
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.PreEntityImages>
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.PostEntityImages>
> 
>Algunas operaciones no incluyen estas propiedades.

## <a name="invoke-a-webhook-from-a-plugin-or-workflow-activity"></a>Llamar un webhook de la actividad de un flujo de trabajo o del complemento

Puesto que un webhook es un tipo de extremo de servicio, también puede llamarlo sin registrar un paso con una actividad de flujo de trabajo o del complemento del mismo modo que puede para un extremo de Azure Service Bus.  Es necesario proporcionar el [ServiceEndpointId](reference/entities/serviceendpoint.md#BKMK_ServiceEndpointId) para la interfaz <xref:Microsoft.Xrm.Sdk.IServiceEndpointNotificationService>. Consulte los siguientes ejemplos de Azure Service Bus para obtener más información: 
- [Ejemplo: complemento personalizado con Azure](org-service/samples/azure-aware-custom-plugin.md)
- [Ejemplo: actividad personalizada de flujo de trabajo basada en Azure](org-service/samples/azure-aware-custom-workflow-activity.md)


## <a name="troubleshoot-web-hook-registrations"></a>Solución de problemas de registros de webhook

Los webhooks son relativamente simples. El servicio enviará la solicitud y evaluará la respuesta. El sistema no puede analizar los datos que se devuelve con el cuerpo de la respuesta, solo buscará en el valor `StatusCode` de respuesta.

El tiempo de espera es de 60 segundos. En general, esto fallará si no se devuelve ninguna respuesta antes del tiempo de espera o si el valor `StatusCode` de respuesta no se encuentra en el intervalo `2xx` para indicar éxito. La excepción se produce cuando el error devuelto se encuentra en la tabla siguiente:

|`StatusCode`|Descripción|
|-|-|
|`502`|Puerta de enlace incorrecta|
|`503`|Servicio no disponible|
|`504`|Tiempo de espera de puerta de enlace|

Estos errores indican un problema de red que se puede resolver con otro intento. El servicio webhook hará un intento más solo cuando se devuelvan estos códigos de error.

### <a name="asynchronous-webhooks"></a>Webhooks asincrónicos

Si su webhook se registra para ejecutarse de forma asincrónica, puede examinar el trabajo del sistema para conocer los detalles del error. Más información: [La consulta produjo error en trabajos asincrónicos para un paso determinado](register-web-hook.md#query-failed-asynchronous-jobs-for-a-given-step)

### <a name="synchronous-webhooks"></a>Webhooks sincrónicos

[!INCLUDE [synchronous-webhook-error](includes/synchronous-webhook-error.md)]

## <a name="next-steps"></a>Pasos siguientes
[Registrar un webhook](register-web-hook.md)<br />
[Probar el registro de webhook con un sitio de registro de solicitud](test-webhook-registration.md)

### <a name="see-also"></a>Vea también

[Escribir un complemento](write-plug-in.md)<br />
[Registro de un complemento](register-plug-in.md)<br />
[Servicio asincrónico en Common Data Service](asynchronous-service.md)<br />
[Ejemplo: complemento personalizado con Azure](org-service/samples/azure-aware-custom-plugin.md)<br />
[Ejemplo: actividad personalizada de flujo de trabajo basada en Azure](org-service/samples/azure-aware-custom-workflow-activity.md)<br />
[Funciones de Azure](https://azure.microsoft.com/services/functions/)<br />
[Entidad ServiceEndpoint](reference/entities/serviceendpoint.md)<br />
[Entidad SdkMessageProcessingStep](reference/entities/sdkmessageprocessingstep.md)<br />
[Entidad AsynchronousOperations](reference/entities/asyncoperation.md)<br />
<xref:Microsoft.Xrm.Sdk.RemoteExecutionContext><br />
<xref:Microsoft.Xrm.Sdk.IServiceEndpointNotificationService><br />
