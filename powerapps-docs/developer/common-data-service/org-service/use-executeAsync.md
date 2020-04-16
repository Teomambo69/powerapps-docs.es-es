---
title: Uso ExecuteAsync para ejecutar mensajes forma asincrónica (Common Data Service) | Microsoft Docs
description: Puede usar el mensaje de ExecuteAsync para importar soluciones de forma asincrónica
ms.custom: ''
ms.date: 06/08/2019
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
ms.openlocfilehash: 101934aa1e114d85dd1059ba62dd1f7e1c5bd686
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155460"
---
# <a name="use-executeasync-to-execute-messages-asynchronously"></a>Uso ExecuteAsync para ejecutar mensajes forma asincrónica

Salvo dos, todas las operaciones de datos utilizando clases de solicitud de ensamblado SDK son sincrónicas.

Importar una solución es una operación que puede requerir considerables recursos, por lo que hay una opción para ejecutar esta operación de forma asincrónica mediante la clase de solicitud <xref:Microsoft.Xrm.Sdk.Messages.ExecuteAsyncRequest>. La clase de solicitud <xref:Microsoft.Crm.Sdk.Messages.DeleteAndPromoteRequest> realiza operaciones con un uso intensivo de recursos similar.

Importar una solución de forma asincrónica mejora el rendimiento del sistema al posponer la ejecución de mensajes hasta un tiempo después, cuando se disminuya la carga del servidor. Los usuarios interactivos no tienen que esperar al mensaje de destino para ejecutarse antes de poder continuar. Esto es especialmente útil para importar soluciones que pueden tardar unos minutos o más en ejecutarse.  
  
> [!NOTE]
>  <xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest> y <xref:Microsoft.Crm.Sdk.Messages.DeleteAndPromoteRequest> son las únicas clases de solicitud que se pueden usar con el mensaje `ExecuteAsync`.
  
Use la clase de solicitud de <xref:Microsoft.Xrm.Sdk.Messages.ExecuteAsyncRequest> para ejecutar un mensaje asincrónicamente. Configure la solicitud y pase la instancia de solicitud como argumento a <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>. <xref:Microsoft.Xrm.Sdk.Messages.ExecuteAsyncResponse> vuelve con el Id. del trabajo asincrónico. Puede (opcionalmente) crear una consulta del trabajo con el Id. para buscar su estado actual.  
  
Puede usar la clase de solicitud de <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> para poner en cola múltiples soluciones que se importarán forma asincrónica. Para ello, agregue una o varias solicitudes del mensaje `ExecuteAsync` a una solicitud de mensaje `ExecuteMultiple`. Según las restricciones de limitación que mejoran el rendimiento del sistema general, solo puede ejecutarse asincrónicamente un mensaje a la vez para cada organización.

Para obtener más información acerca del mensaje `ExecuteMultiple`, consulte [Ejecutar varias solicitudes con el servicio de la organización](execute-multiple-requests.md).  

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


  