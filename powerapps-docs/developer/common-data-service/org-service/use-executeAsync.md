---
title: Usar ExecuteAsync para ejecutar mensajes de forma asincrónica (Common Data Service) | Microsoft Docs
description: Puede usar el mensaje de ExecuteAsync para importar soluciones de forma asincrónica
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
# <a name="use-executeasync-to-execute-messages-asynchronously"></a>Uso ExecuteAsync para ejecutar mensajes forma asincrónica  

Salvo una, todas las operaciones de datos utilizando los ensamblados de SDK son sincrónicas. Importar una solución es una operación que puede requerir considerables recursos, por lo que hay una opción para ejecutar esta operación de forma asincrónica mediante la clase <xref:Microsoft.Xrm.Sdk.Messages.ExecuteAsyncRequest>.

Importar una solución de forma asincrónica mejora el rendimiento del sistema al posponer la ejecución de mensajes hasta un tiempo después, cuando se disminuya la carga del servidor. Los usuarios interactivos no tienen que esperar al mensaje de destino para ejecutarse antes de poder continuar. Esto es especialmente útil para importar soluciones que pueden tardar unos minutos o más en ejecutarse.  
  
> [!NOTE]
>  <xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest> es el único mensaje que se puede usar con el mensaje `ExecuteAsync`.  
  
Use el mensaje de <xref:Microsoft.Xrm.Sdk.Messages.ExecuteAsyncRequest> para ejecutar un mensaje asincrónicamente. Configure la solicitud y pase la instancia de solicitud como argumento a <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>. <xref:Microsoft.Xrm.Sdk.Messages.ExecuteAsyncResponse> vuelve con el Id. del trabajo asincrónico. Puede (opcionalmente) crear una consulta del trabajo con el Id. para buscar su estado actual.  
  
Puede usar las soluciones múltiples de cola de mensajes <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> que se importarán forma asincrónica. Para ello, agregue una o varias solicitudes del mensaje `ExecuteAsync` a una solicitud de mensaje `ExecuteMultiple`. Según las restricciones de limitación que mejoran el rendimiento del sistema general, solo puede ejecutarse asincrónicamente un mensaje a la vez para cada organización. 

Para obtener más información acerca de la solicitud de mensaje `ExecuteMultiple`, consulte [Ejecutar varias solicitudes con el servicio de la organización](execute-multiple-requests.md).  

## <a name="example"></a>Ejemplo

El siguiente ejemplo muestra cómo usar la clase de solicitud de mensaje <xref:Microsoft.Xrm.Sdk.Messages.ExecuteAsyncRequest> con la clase de solicitud de mensaje <xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest>.

```csharp
string ManagedSolutionLocation = @"C:\temp\ManagedSolutionForImportExample.zip";

byte[] fileBytes = File.ReadAllBytes(ManagedSolutionLocation);

ImportSolutionRequest impSolReq = new ImportSolutionRequest()
{
CustomizationFile = fileBytes
};

ExecuteAsyncRequest asyncReq = new ExecuteAsyncRequest()
{
Request = impSolReq
};

var asyncResp = (ExecuteAsyncResponse)svc.Execute(asyncReq);

Guid asyncOperationId = asyncResp.AsyncJobId;
```
A continuación puede sondear la entidad [AsyncOperation](../reference/entities/asyncoperation.md) usando el valor `asyncOperationId` del trabajo del sistema con el [AsyncOperationId](../reference/entities/asyncoperation.md#BKMK_AsyncOperationId) que coincide para detectar cuándo el valor de [StatusCode](../reference/entities/asyncoperation.md#BKMK_StatusCode) indica si la operación se ha realizado correctamente (30), con error (31), o se cancela (32).

### <a name="see-also"></a>Vea también

[Utilizar mensajes con el servicio de la organización](use-messages.md)<br />
[Uso de ExecuteTransaction](use-executetransaction.md)<br />
[Ejecutar varias solicitudes con el servicio de la organización](execute-multiple-requests.md)


  