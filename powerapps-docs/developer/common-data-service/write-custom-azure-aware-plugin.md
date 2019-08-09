---
title: Escribir un complemento con Azure personalizado (Common Data Service) | Microsoft Docs
description: El ejemplo muestra como el código del pluggin puede ser agragado para obtener el proveedor de servicio Azure e iniciar la publicación del contexto de ejecución en el bus de servicio mediante la llamada IExecutionContext .
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 93d0442e-5fc9-c43c-c8c1-a433687f3d0a
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

# <a name="write-a-custom-azure-aware-plug-in"></a>Escribir un complemento con Azure personalizado

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/write-custom-azure-aware-plugin -->

Escribir un complemento que funcione con Azure es similar a escribir cualquier otro complemento de Dynamics 365 Common Data Service. Sin embargo, además de invocar todos los métodos de servicio web que desee, el complemento debe incluir código para iniciar la publicación del contexto de la ejecución en Azure Service Bus.  
  
<a name="bkmk_design"></a>

## <a name="plug-in-design-considerations"></a>Consideraciones de diseño de complementos  
Para un complemento que se ejecute de forma sincrónica, el diseño recomendada es que el complemento envíe un mensaje a Azure con el fin de recuperar la información de la aplicación de escucha o de otro servicio externo. El uso de un contrato bidireccional o REST en el extremo final de Azure Service Bus permite que se devuelva una cadena de datos al pluggin.  
  
No se recomienda que un complemento sincrónico utilice el Azure Service Bus para actualizar los datos con un servicio externo. Podrían surgir problemas si el servicio externo llega a estar no disponible o si hay muchos datos que actualizar. Los complementos sincrónicos deben ejecutarse rápido y no mantener a todos los usuarios que han iniciado sesión en una organización mientras se realiza una operación muy larga. Además, si se produce una retrotracción de la operación actual de base que invocó al complemento, los cambios en los datos realizados por el complemento se desharán. Esto podría dejar Dynamics 365 y un servicio externo en estado no sincronizado.  
  
Tenga en cuenta que es posible que los complementos registrados sincrónicos publiquen el contexto de la ejecución en el Azure Service Bus.  
  
<a name="bkmk_writing"></a>
  
## <a name="write-the-plug-in-code"></a>Escritura del código de complementos 
 
El siguiente código de complementos de ejemplo se ha agregado para obtener el proveedor de servicios de Azure e iniciar la publicación del contexto de ejecución en el bus de servicio llamando a <xref:Microsoft.Xrm.Sdk.IServiceEndpointNotificationService.Execute(Microsoft.Xrm.Sdk.EntityReference,Microsoft.Xrm.Sdk.IExecutionContext)>. Se ha agregado código de seguimiento para facilitar la depuración de complementos porque el complemento se debe ejecutar en el espacio asilado.  

> [!NOTE]
> El `serviceEndpointId` que se ha pasado al constructor en este código es el único que obtiene de la creación de un extremo de servicio como el que se describe en [Tutorial: Configurar Azure (SAS) para integración con Common Data Service.](walkthrough-configure-azure-sas-integration.md)
>
> Puede consultar los extremos de servicio disponibles para su entorno mediante una solicitud `GET` a una API web con su explorador con una consulta como esta: *`[organization Uri]`*`/api/data/v9.0/serviceendpoints?$select=name,description,serviceendpointid`.
  
```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Runtime.Serialization;

using System.ServiceModel;
using System.ServiceModel.Channels;
using System.ServiceModel.Description;

using Microsoft.Xrm.Sdk;

namespace Microsoft.Crm.Sdk.Samples
{
    /// <summary>
    /// A custom plug-in that can post the execution context of the current message to the Windows
    /// Azure Service Bus. The plug-in also demonstrates tracing which assist with
    /// debugging for plug-ins that are registered in the sandbox.
    /// </summary>
    /// <remarks>This sample requires that a service endpoint be created first, and its ID passed
    /// to the plug-in constructor through the unsecure configuration parameter when the plug-in
    /// step is registered.</remarks>
    public sealed class SandboxPlugin : IPlugin
    {
        private Guid serviceEndpointId; 

        /// <summary>
        /// Constructor.
        /// </summary>
        public SandboxPlugin(string config)
        {
            if (String.IsNullOrEmpty(config) || !Guid.TryParse(config, out serviceEndpointId))
            {
                throw new InvalidPluginExecutionException("Service endpoint ID should be passed as config.");
            }
        }

        public void Execute(IServiceProvider serviceProvider)
        {
            // Retrieve the execution context.
            IPluginExecutionContext context = (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));

            // Extract the tracing service.
            ITracingService tracingService = (ITracingService)serviceProvider.GetService(typeof(ITracingService));
            if (tracingService == null)
                throw new InvalidPluginExecutionException("Failed to retrieve the tracing service.");

            IServiceEndpointNotificationService cloudService = (IServiceEndpointNotificationService)serviceProvider.GetService(typeof(IServiceEndpointNotificationService));
            if (cloudService == null)
                throw new InvalidPluginExecutionException("Failed to retrieve the service bus service.");

            try
            {
                tracingService.Trace("Posting the execution context.");
                string response = cloudService.Execute(new EntityReference("serviceendpoint", serviceEndpointId), context);
                if (!String.IsNullOrEmpty(response))
                {
                    tracingService.Trace("Response = {0}", response);
                }
                tracingService.Trace("Done.");
            }
            catch (Exception e)
            {
                tracingService.Trace("Exception: {0}", e.ToString());
                throw;
            }
        }
    }
}
```  
  
En el código de complemento, puede actualizar los datos grabables en contexto antes de iniciar la publicación. Por ejemplo, puede agregar un par de clave/valor a las variables compartidas en contexto. 
  
<a name="bkmk_registration"></a>

## <a name="plug-in-registration"></a>Registro de complementos

Hay algunas restricciones cuando se registra un complemento personalizado basado en Azure. El complemento se debe registrar para ejecutarse en el espacio asilado. Por este motivo, el complemento se limita a llamar a los métodos de <xref:Microsoft.Xrm.Sdk.IOrganizationService>, los métodos de soluciones de Azure o a acceder a una red mediante un cliente web. No se permite ningún otro acceso externo, como el acceso a un sistema de archivos local.  
  
Para un complemento registrado para ejecutarse en modo asincrónico, esto implica que el orden de la ejecución de complementos en comparación con otros complementos asincrónicos no está garantizado. Además, los complementos asincrónicos se ejecutan siempre después de la operación de la base de Dynamics 365.  
  
<a name="bkmk_failure"></a>
 
## <a name="handle-a-failed-service-bus-post"></a>Gestión de una publicación de bus de servicio con errores

El comportamiento esperado de una publicación de bus de servicio con errores depende de si complemento se ha registrado para su ejecución sincrónica o asincrónica. Para complementos asincrónicos, el trabajo del sistema que publica realmente el contexto de la ejecución en el bus de servicio reintentará la publicación. Para un complemento registrado sincrónico, se devuelve una excepción. Más información [Administración y notificación de errores en tiempo de ejecución](azure-integration.md)  
  
> [!IMPORTANT]
>  Solo para complementos registrados asincrónicos, cuando se reintenta realizar el trabajo asincrónico que publica en el Azure Service Bus después de un error de publicación, se vuelve a ejecutar la lógica completa de complementos. Por este motivo, no puede agregar ninguna otra lógica al complemento personalizado basado en Azure, aparte de modificar el contexto y realizar publicaciones en el bus de servicio.  
  
Para un complemento registrado para ejecutarse asincrónicamente, el <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext> contenido en el cuerpo del mensaje que se enviará sobre el bus de servicio incluye una propiedad de <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.OperationId> y una propiedad de <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.OperationCreatedOn>. Estas propiedades contienen los mismos datos que los atributos `AsyncOperationId` y `CreatedOn` del registro relacionado del trabajo del sistema (`AsyncOperation`). Estas propiedades adicionales facilitan la secuenciación y la detección de duplicados si la publicación de Azure Service Bus debe ser reintentada.  
  
### <a name="see-also"></a>Vea también

[Extensiones de Azure para Dynamics 365](azure-integration.md)<br />
[Enviar datos de Dynamics 365 a través del Bus de servicio de Microsoft Azure](work-data-azure-solution.md)<br />
[Escribir un complemento](write-plug-in.md)<br />
[Canalización de ejecución del evento](event-framework.md)<br />
[Registrar e implementar complementos](register-plug-in.md)
