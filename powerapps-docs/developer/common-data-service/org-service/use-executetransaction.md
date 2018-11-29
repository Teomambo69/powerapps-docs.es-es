---
title: Ejecutar mensajes en una sola transacción de la base de datos (Common Data Service para aplicaciones) | Microsoft Docs
description: Puede ejecutar dos o varias solicitudes de servicio de la organización en una sola transacción de la base de datos mediante el uso de la solicitud de mensajes ExecuteTransactionRequest.
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
# <a name="execute-messages-in-a-single-database-transaction"></a>Ejecutar mensajes en una sola transacción de la base de datos

 Un requisito común en aplicaciones de negocios es la coordinación de los cambios de varios registros en el sistema de modo que todos se produzcan todos los cambios de datos ninguno de ellos. En términos de la base de datos, esto se conoce como ejecutar varias operaciones en una sola transacción con la capacidad de revertir todos los cambios de los datos cuando hay error en una operación.  
  
 Puede ejecutar dos o varias solicitudes de servicio de la organización en una sola transacción de base de datos mediante el uso de la solicitud de mensajes <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest>. Para usar este mensaje, rellene la colección <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest.Requests> con dos o más solicitudes de organización que deben ejecutarse en la transacción. Establezca <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest.ReturnResponses> como `true` si desea devolver una colección de respuestas, una para cada solicitud de mensajes ejecutada, en la colección <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionResponse.Responses>. Las solicitudes de mensaje en la colección <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest.Requests> se ejecutan en el orden que aparecen en la colección, donde el elemento en el índice 0 se ejecuta primero. Este mismo orden se mantiene en la colección <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleResponse.Responses>.  
  
 Si se produce un error en cualquiera de las solicitudes y se revierte la transacción, se deshacen los cambios de los datos completados durante la transacción. Además, se devuelve un <xref:Microsoft.Xrm.Sdk.ExecuteTransactionFault> que identifica el índice en la colección de solicitudes del mensaje de solicitud que produjo el error.  
  
 Una <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> puede contener una o varias instancias de <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest>.  Una instancia de <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest> no puede contener una <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> o <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest>. Para obtener más información acerca de <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest>, consulte [Ejecutar varias solicitudes con el servicio de la organización](execute-multiple-requests.md). 

## <a name="example"></a>Ejemplo

Este ejemplo utiliza una sola llamada de método web para ejecutar todas las solicitudes de mensaje en una colección como parte de una sola transacción de base de datos. También se muestran los valores para modificar el comportamiento de la ejecución.

```csharp
// Create an ExecuteTransactionRequest object.
var requestToCreateRecords = new ExecuteTransactionRequest()
{
// Create an empty organization request collection.
Requests = new OrganizationRequestCollection(),
ReturnResponses = true
};

// Create several (local, in memory) entities in a collection. 
var input = new EntityCollection()
{
EntityName = Account.EntityLogicalName,
Entities = {
            new Account { Name = "ExecuteTransaction Example Account 1" },
            new Account { Name = "ExecuteTransaction Example Account 2" },
            new Account { Name = "ExecuteTransaction Example Account 3" },
            new Account { Name = "ExecuteTransaction Example Account 4" },
            new Account { Name = "ExecuteTransaction Example Account 5" }
        }
};

// Add a CreateRequest for each entity to the request collection.
foreach (var entity in input.Entities)
{
CreateRequest createRequest = new CreateRequest { Target = entity };
requestToCreateRecords.Requests.Add(createRequest);
}

// Execute all the requests in the request collection using a single web method call.
try
{
var responseForCreateRecords =
    (ExecuteTransactionResponse)svc.Execute(requestToCreateRecords);

int i = 0;
// Display the results returned in the responses.
foreach (var responseItem in responseForCreateRecords.Responses)
{
    if (responseItem != null)
    Console.WriteLine("Created " + ((Account)requestToCreateRecords.Requests[i].Parameters["Target"]).Name
        + " with account id as " + responseItem.Results["id"].ToString());
    i++;
}
}
catch (FaultException<OrganizationServiceFault> ex)
{
Console.WriteLine("Create request failed for the account{0} and the reason being: {1}",
    ((ExecuteTransactionFault)(ex.Detail)).FaultedRequestIndex + 1, ex.Detail.Message);
throw;
}
```

### <a name="see-also"></a>Vea también

[Utilizar mensajes con el servicio de la organización](use-messages.md)<br />
[Ejecutar varias solicitudes con el servicio de la organización](execute-multiple-requests.md)