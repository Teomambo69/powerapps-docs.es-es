---
title: Ejecución de varias solicitudes con el servicio de la organización (Common Data Service) | Microsoft Docs
description: El mensaje ExecuteMultipleRequest admite un rendimiento mayor de los mensajes en masa que pasan escenarios en Common Data Service.
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
# <a name="execute-multiple-requests-using-the-organization-service"></a>Ejecución de varias solicitudes con el servicio de la organización

<!-- 

https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/use-executemultiple-improve-performance-bulk-data-load 

-->
El objetivo principal de ejecutar varias solicitudes es mejorar el rendimiento en entornos de latencia alta mediante la reducción de volumen de datos total que se transmite a través de la red.

Puede utilizar el mesaje <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> para admitir un rendimiento superior de mensajes en masa que pasan entre escenarios de Common Data Service. <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> acepta una colección de entrada de <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest.Requests> de mensajes, ejecuta cada una de las solicitudes de mensajes en el orden que aparecen en la colección de entrada y opcionalmente devuelve una colección de <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleResponse.Responses> que contiene la respuesta de cada mensaje o el error que se han producido. Cada solicitud de mensaje en la colección de entrada se procesa en una transacción independiente de la base de datos. <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> se ejecuta usando el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> .  
  
En general, <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> se comporta de la misma manera que si ejecutara cada solicitud de mensaje en la colección de solicitudes de entrada por separado, excepto que con mejor rendimiento. Se respeta el uso del parámetro <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy.CallerId> del proxy de servicio y se aplicará a la ejecución de cada mensaje en la colección de solicitudes de entrada. Los complementos y las actividades de flujo de trabajo se ejecutan como se podría esperar para cada mensaje procesado.  
  
Incluso el código personalizado en la forma de complementos y actividades personalizadas del flujo de trabajo puede ejecutar <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest>. Sin embargo, hay algunos puntos clave para tener en cuenta. Se devuelve una excepción generada por un complemento registrado sincrónico en el parámetro <xref:Microsoft.Xrm.Sdk.ExecuteMultipleResponseItem.Fault> del elemento de la colección de respuesta. Si un complemento se ejecuta en una transacción de la base de datos, el complemento ejecuta <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest>, y se inicia una reversión de la transacción, la cual incluye los cambios de datos que derivan de las solicitudes ejecutadas por <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest>.  
  
<a name="example"></a>

## <a name="example"></a>Ejemplo

 El siguiente código de ejemplo muestra un solo <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> que realiza varias operaciones de creación. Se utilizan opciones de ejecución en tiempo de ejecución denominadas *Configuración* para controlar el procesamiento de la solicitud y los resultados obtenidos. Estas opciones de tiempo de ejecución se tratan en la sección siguiente.  
  
```csharp

// Create an ExecuteMultipleRequest object.
requestWithResults = new ExecuteMultipleRequest()
{
    // Assign settings that define execution behavior: continue on error, return responses. 
    Settings = new ExecuteMultipleSettings()
    {
        ContinueOnError = false,
        ReturnResponses = true
    },
    // Create an empty organization request collection.
    Requests = new OrganizationRequestCollection()
};

// Create several (local, in memory) entities in a collection. 
EntityCollection input = GetCollectionOfEntitiesToCreate();

// Add a CreateRequest for each entity to the request collection.
foreach (var entity in input.Entities)
{
    CreateRequest createRequest = new CreateRequest { Target = entity };
    requestWithResults.Requests.Add(createRequest);
}

// Execute all the requests in the request collection using a single web method call.
ExecuteMultipleResponse responseWithResults =
    (ExecuteMultipleResponse)service.Execute(requestWithResults);

// Display the results returned in the responses.
foreach (var responseItem in responseWithResults.Responses)
{
    // A valid response.
    if (responseItem.Response != null)
        DisplayResponse(requestWithResults.Requests[responseItem.RequestIndex], responseItem.Response);

    // An error has occurred.
    else if (responseItem.Fault != null)
        DisplayFault(requestWithResults.Requests[responseItem.RequestIndex], 
            responseItem.RequestIndex, responseItem.Fault);
}
```
  
Más información: [Ejemplo: ejecutar varias solicitudes](samples/execute-multiple-requests.md)
  
<a name="options"></a>
 
## <a name="specify-run-time-execution-options"></a>Especificación de las opciones de ejecución en tiempo de ejecución  

El parámetro <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest.Settings> de <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> se aplica a todas las solicitudes de la colección de solicitudes que controlan el comportamiento de ejecución y los resultados obtenidos. Analicemos estas opciones con mayor detalle.  
  
|Miembro de ExecuteMultipleSettings|Descripción|  
|------------------------------------|-----------------|  
|<xref:Microsoft.Xrm.Sdk.ExecuteMultipleSettings.ContinueOnError>|Si está establecida en `true`, siga procesando la siguiente solicitud de la colección aunque haya obtenido un error por procesar la solicitud actual en la colección. Si está establecida en `false`, no siga procesando la solicitud siguiente.|  
|<xref:Microsoft.Xrm.Sdk.ExecuteMultipleSettings.ReturnResponses>|Si está establecida en `true`, devuelve las respuestas de cada solicitud de mensaje procesada. Si está establecida en `false`, no devuelve respuestas.<br /><br /> Si está establecida en `true` y una solicitud no devuelve una respuesta, porque ese es el diseño, el parámetro <xref:Microsoft.Xrm.Sdk.ExecuteMultipleResponseItem> de esa solicitud se establece en `null`.<br /><br /> Sin embargo, aunque esté establecida en `false`, la colección de <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleResponse.Responses> no estará vacía si se devuelven errores. Si se devuelven errores, habrá un elemento de respuesta en la colección de cada solicitud procesada que devolvió un error y <xref:Microsoft.Xrm.Sdk.ExecuteMultipleResponseItem.Fault> se establecerá en el error real que se produjo.|  
  
 Por ejemplo, para una colección de solicitudes que contiene seis solicitudes en las que la tercera y la quinta solicitud devuelven errores, la siguiente tabla indica qué contendría la colección de <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleResponse.Responses>.  
  
|Configuración|Contenido de la colección de respuestas|  
|--------------|-----------------------------------|  
|ContinueOnError=true, ReturnResponses=true|6 elementos de respuesta: 2 tienen <xref:Microsoft.Xrm.Sdk.ExecuteMultipleResponseItem.Fault> establecido en un valor.|  
|ContinueOnError=false, ReturnResponses=true|3 elementos de respuesta: 1 tiene <xref:Microsoft.Xrm.Sdk.ExecuteMultipleResponseItem.Fault> establecido en un valor.|  
|ContinueOnError=true, ReturnResponses=false|2 elementos de respuesta: 2 tienen <xref:Microsoft.Xrm.Sdk.ExecuteMultipleResponseItem.Fault> establecido en un valor.|  
|ContinueOnError=false, ReturnResponses=false|1 elemento de respuesta: 1 tiene <xref:Microsoft.Xrm.Sdk.ExecuteMultipleResponseItem.Fault> establecido en un valor.|  
  
 Un parámetro <xref:Microsoft.Xrm.Sdk.ExecuteMultipleResponseItem.RequestIndex> en el elemento de respuesta indica el número de secuencia, a partir de cero, de la solicitud con la que está asociada la respuesta. En el ejemplo anterior, la tercera solicitud tiene un índice de solicitudes de 2.  
  
<a name="limitations"></a>

## <a name="run-time-limitations"></a>Limitaciones al tiempo de ejecución

Existen varias restricciones relacionadas con el uso de <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> tal como se describe en la siguiente lista.  
  
-   **No se permite la recursión**: <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> no puede invocar a <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest>. Un parámetro <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> que se encuentre en la colección de solicitudes generará un error para ese elemento de la solicitud.  
  
-   **Tamaño de lote máximo**: hay un límite en cuanto a la cantidad de solicitudes que se pueden agregar a una colección de solicitudes. Si se supera ese límite, se genera un error incluso antes de que se ejecute la primera solicitud. Un límite de 1000 solicitudes es típico aunque este cantidad máxima puede establecerse para la implementación de aplicaciones Common Data Service.
  
-   **Limitación de llamadas simultáneas**: para Common Data Service hay un límite de 2 ejecuciones simultáneas de <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> por organización. Si se supera ese límite, se genera un error de *Servidor ocupado* incluso antes de que se ejecute la primera solicitud. 

  
<a name="fault"></a>

## <a name="handle-a-batch-size-fault"></a>Cómo administrar un error de tamaño de lote

¿Qué debe hacer cuando la colección de solicitudes de entrada supera el tamaño de lote máximo? El código no puede consultar directamente el tamaño de lote máximo con el servicio web de implementación a menos que se ejecute con una cuenta que tiene el rol de administrador de implementaciones.  
  
Afortunadamente, hay otro método que puede usar. Cuando el número de solicitudes en la colección <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest.Requests> de entrada supera el tamaño de lote máximo permitido para una organización, la llamada <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> devuelve un error. El tamaño de lote máximo se devuelve en el error. El código puede comprobar ese valor, cambiar el tamaño de la colección de solicitudes de entrada de que modo que esté dentro del límite indicado y volver a enviar <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest>. El siguiente fragmento de código muestra parte de esta lógica.  
  
```csharp
catch (FaultException<OrganizationServiceFault> fault)
{
    // Check if the maximum batch size has been exceeded. The maximum batch size is only included in the fault if it
    // the input request collection count exceeds the maximum batch size.
    if (fault.Detail.ErrorDetails.Contains("MaxBatchSize"))
    {
        int maxBatchSize = Convert.ToInt32(fault.Detail.ErrorDetails["MaxBatchSize"]);
        if (maxBatchSize < requestWithResults.Requests.Count)
        {
            // Here you could reduce the size of your request collection and re-submit the ExecuteMultiple request.
            // For this sample, that only issues a few requests per batch, we will just print out some info. However,
            // this code will never be executed because the default max batch size is 1000.
            Console.WriteLine("The input request collection contains %0 requests, which exceeds the maximum allowed (%1)",
                requestWithResults.Requests.Count, maxBatchSize);
        }
    }
    // Re-throw so Main() can process the fault.
    throw;
}
```

### <a name="see-also"></a>Vea también

[Uso de mensajes con el servicio de la organización](use-messages.md)<br />
[Uso de ExecuteAsync](use-executeAsync.md)<br />
[Uso de ExecuteTransaction](use-executetransaction.md)<br />
