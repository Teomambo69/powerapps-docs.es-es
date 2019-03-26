---
title: Suplantar a un usuario (Common Data Service para aplicaciones) | Microsoft Docs
description: Aprenda a escribir el código de complemento para actuar en nombre de un usuario específico.
ms.custom: ''
ms.date: 1/24/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: pehecke
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# Suplantar a un usuario

En ocasiones, necesita tener código en un complemento que se ejecute en el contexto de otro usuario, por ejemplo, para realizar una operación en su nombre.

Hay dos formas de aplicar suplantación en complementos: en el registro o la ejecución.

## En el registro de complementos

Al registrar una paso de complemento puede especificar una cuenta de usuario para usar cuando el código se ejecuta eligiendo desde la opción **Ejecutar en contexto de usuario**. De forma predeterminada esta opción se establece para usar el **Usuario que llama**, que es la cuenta de usuario que inició la acción. Cuando se aplica esta opción predeterminada, el [SdkMessageProcessingStep.ImpersonatingUserId](reference/entities/sdkmessageprocessingstep.md#BKMK_ImpersonatingUserId) se establecerá como nulo o <xref:System.Guid.Empty>.

Más información: [Registrar paso de complemento](register-plug-in.md#register-plug-in-step).

## Durante la ejecución de complemento

Puede reemplazar el valor especificado en el registro en tiempo de ejecución estableciendo el parámetro <xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory>.<xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory.CreateOrganizationService(System.Nullable{System.Guid})><xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory.CreateOrganizationService(System.Nullable{System.Guid})> `userId` `userId`.

Este normalmente se establece con el valor <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.UserId><xref:Microsoft.Xrm.Sdk.IExecutionContext.UserId> que aplicará la cuenta de usuario definida por el registro de paso de complemento.

```csharp
(IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
    IOrganizationService service = serviceFactory.CreateOrganizationService(context.UserId);
```

Si desea reemplazar el registro del paso puede pasar el valor del <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.InitiatingUserId><xref:Microsoft.Xrm.Sdk.IExecutionContext.InitiatingUserId> para tener un servicio que usará la cuenta de usuario que inició la acción que produjo la ejecución del complemento.

También puede proporcionar el [SystemUser.SystemUserId](reference/entities/systemuser.md#BKMK_SystemUserId) desde cualquier cuenta de usuario válida. Esto funcionará siempre que el usuario tenga permisos para realizar las operaciones en el complemento.

### Vea también

[[Complementos](plug-ins.md)](plug-ins.md)  
[[Escribir un complemento](write-plug-in.md)](write-plug-in.md)