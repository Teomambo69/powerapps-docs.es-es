---
title: Usar ITracingService en los complementos | MicrosoftDocs
description: Depurar o solucionar los problemas de los complementos o los comportamientos de la solución es complicado sin tener registros o un seguimiento variados y detallados.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/12/2018
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d6849e0038dab80a8275b247e8bfd4239a4ec1ec
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749391"
---
# <a name="use-itracingservice-in-plug-ins"></a>Usar ITracingService en los complementos

**Categoría**: mantenimiento, compatibilidad

**Potencial de impacto**: medio

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

Depurar o solucionar los problemas de los complementos o los comportamientos de la solución es complicado sin tener registros o un seguimiento variados y detallados.

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

La interfaz <xref:Microsoft.Xrm.Sdk.ITracingService> ayuda a los programadores con el registro de información personalizada para ayudar en el diagnóstico de la causa de los errores de código o comportamientos inesperados código en los complementos. Antes de escribir en el servicio de seguimiento, primero debe extraer el objeto de servicio de seguimiento del contexto de ejecución pasado. A continuación, agregue simplemente llamadas [Trace](/dotnet/api/microsoft.xrm.sdk.itracingservice.trace) a su código personalizado donde corresponda pasando la información relevante de diagnóstico en esa llamada al método.

> [!NOTE]
> El registro de seguimiento mediante la interfaz `ITracingService` funciona únicamente cuando el complemento se registra en modo de espacio aislado y debe habilitar el registro de seguimiento para recopilar datos en tiempo de ejecución. Para obtener más información, consulte [Registro y seguimiento](/dynamics365/customer-engagement/developer/debug-plugin#logging-and-tracing).

```csharp
//Extract the tracing service for use in debugging sandboxed plug-ins.
ITracingService tracingService =
    (ITracingService)serviceProvider.GetService(typeof(ITracingService));

// Obtain the execution context from the service provider.
IPluginExecutionContext context = (IPluginExecutionContext)
    serviceProvider.GetService(typeof(IPluginExecutionContext));

// For this sample, execute the plug-in code only while the client is online. 
tracingService.Trace("AdvancedPlugin: Verifying the client is not offline.");
if (context.IsExecutingOffline || context.IsOfflinePlayback)
    return;

// The InputParameters collection contains all the data passed 
// in the message request.
if (context.InputParameters.Contains("Target") &&
    context.InputParameters["Target"] is Entity)
{
    // Obtain the target entity from the Input Parameters.
    tracingService.Trace("AdvancedPlugin: Getting the target entity from Input Parameters.");
    Entity entity = (Entity)context.InputParameters["Target"];

    // Obtain the image entity from the Pre Entity Images.
    tracingService.Trace("AdvancedPlugin: Getting image entity from PreEntityImages.");
    Entity image = (Entity)context.PreEntityImages["Target"];
}
```

<a name='additional'></a>

## <a name="additional-information"></a>Información adicional

El seguimiento es especialmente útil para solucionar problemas de código personalizado registrado ya que es el único método que solución de problemas compatible para ese escenario. El seguimiento se admite para código personalizado registrado en `sandboxed` (confianza parcial) y de total confianza y durante la ejecución sincrónica o asincrónica. El seguimiento no se admite para código personalizado que se ejecuta en Microsoft Dynamics 365 for Outlook u otro cliente móvil.

<a name='seealso'></a>

### <a name="see-also"></a>Vea también

[Escribir un complemento](../../write-plug-in.md)  
[Registro y seguimiento](../../logging-tracing.md)