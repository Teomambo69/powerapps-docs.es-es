---
title: Suplantar a un usuario (Common Data Service) | Microsoft Docs
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
ms.openlocfilehash: 27022b8ffb76128e70ef2985059f6dc7dea504ef
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749434"
---
# <a name="impersonate-a-user"></a>Suplantar a un usuario

En ocasiones, necesita tener código en un complemento que se ejecute en el contexto de otro usuario, por ejemplo, para realizar una operación en su nombre.

Hay dos formas de aplicar suplantación en complementos: en el registro o la ejecución.

## <a name="at-plug-in-registration"></a>En el registro de complementos

Al registrar una paso de complemento puede especificar una cuenta de usuario para usar cuando el código se ejecuta eligiendo desde la opción **Ejecutar en contexto de usuario**. De forma predeterminada esta opción se establece para usar el **Usuario que llama**, que es la cuenta de usuario que inició la acción. Cuando se aplica esta opción predeterminada, el [SdkMessageProcessingStep.ImpersonatingUserId](reference/entities/sdkmessageprocessingstep.md#BKMK_ImpersonatingUserId) se establecerá como nulo o <xref:System.Guid.Empty>.

Más información: [Registrar paso de complemento](register-plug-in.md#register-plug-in-step).

## <a name="during-plug-in-execution"></a>Durante la ejecución de complemento

Puede reemplazar el valor especificado en el registro en tiempo de ejecución estableciendo el parámetro <xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory>.<xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory.CreateOrganizationService(System.Nullable{System.Guid})> `userId`.

Este normalmente se establece con el valor <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.UserId> que aplicará la cuenta de usuario definida por el registro de paso de complemento.

```csharp
(IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
    IOrganizationService service = serviceFactory.CreateOrganizationService(context.UserId);
```

Si desea reemplazar el registro del paso puede pasar el valor del <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.InitiatingUserId> para tener un servicio que usará la cuenta de usuario que inició la acción que produjo la ejecución del complemento.

También puede proporcionar el [SystemUser.SystemUserId](reference/entities/systemuser.md#BKMK_SystemUserId) desde cualquier cuenta de usuario válida. Esto funcionará siempre que el usuario tenga permisos para realizar las operaciones en el complemento.

### <a name="see-also"></a>Vea también

[Complementos](plug-ins.md)  
[Escribir un complemento](write-plug-in.md)