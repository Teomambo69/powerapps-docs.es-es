---
title: Registrar y llevar seguimientos (Common Data Service para aplicaciones) | Microsoft Docs
description: Use el registro de seguimiento para almacenar la información de ejecución de los complementos para ayudar en la depuración de los complementos.
ms.custom: ''
ms.date: 1/28/2019
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
# Registro y seguimiento

 El uso del seguimiento es un método alternativo para solucionar problemas en un complemento o una actividad de flujo de trabajo personalizada (código personalizado), en comparación con depurar en [!INCLUDE[pn_Visual_Studio](../../includes/pn-visual-studio.md)]. El seguimiento ayuda a los desarrolladores registrando información personalizada en tiempo de ejecución como ayuda en el diagnóstico de la causa de los errores del código. El seguimiento es especialmente útil para solucionar problemas de código personalizado registrado de [!INCLUDE[pn_CRM_Online](../../includes/pn-crm-online.md)] ya que es el único método que solución de problemas compatible para ese escenario. El seguimiento se admite para código personalizado registrado en espacio aislado (confianza parcial) y de total confianza y durante la ejecución sincrónica o asincrónica. El seguimiento no se admite para código personalizado que se ejecuta en [!INCLUDE[pn_microsoft_dynamics_crm_for_outlook](../../includes/pn-microsoft-dynamics-crm-for-outlook.md)] u otro cliente móvil.  
  
 El registro de información de seguimiento en tiempo de ejecución para aplicaciones [!INCLUDE[pn_dynamics_crm](../../includes/pn-dynamics-crm.md)] se consigue mediante un servicio llamado <xref:Microsoft.Xrm.Sdk.ITracingService>. La información proporcionada a este servicio por el código personalizado se puede registrar en tres distintas secciones que se identifican aquí.  

> [!NOTE]
> El seguimiento de registros con la interfaz `ITracingService` funciona solo cuando el complemento se registra en modo entorno limitado.

- ****Registro de seguimiento****  
  
     Los registro de seguimiento del tipo **PluginTraceLog** pueden encontrarse en la aplicación web accediendo a **Configuración** y eligiendo la ventana **Registro de seguimiento de complementos**. La ventana solo es visible si tiene acceso a los registros de la entidad de registro de seguimiento en su rol de seguridad asignado. La escritura de estos registros se controla mediante la configuración de seguimiento mencionada en la siguiente sección.
  
    > [!NOTE]
    > El registro de seguimiento ocupa espacio de almacenamiento de la organización, especialmente cuando se generan muchos seguimientos y excepciones. Solo debe activar el registro de seguimiento para depurar y solucionar problemas, y desactivarla después de que la investigación esté completa.  
  
- ****Diálogo de errores****  
  
     Un complemento registrado sincrónico o una actividad de flujo de trabajo personalizada que devuelve una excepción a la plataforma produce un cuadro de diálogo de error en la aplicación web que se muestran al usuario que ha iniciado sesión. El usuario puede seleccionar el botón **Descargar archivo de registro** en el cuadro de diálogo para ver el registro que contiene la excepción y la salida de seguimiento.  
  
- ****Trabajo del sistema****  
  
     Para un complemento registrado asincrónico o actividades de flujo de trabajo personalizadas que devuelven una excepción, la información de seguimiento aparece en el área **Detalles** del formulario **Trabajo del sistema** en la aplicación web.  
  
<a name="bkmk_trace-settings"></a>   
## Habilitar registro de seguimiento  
 Para habilitar el registro de seguimiento en una organización que admite esta característica, en la aplicación web vaya a **Configuración** > **Administración** > **Configuración del sistema**. En la pestaña **Personalización**, busque el menú desplegable con la etiqueta **Habilitar registro para registro de seguimientos de complemento** y seleccione una de las opciones disponibles.  
  
|Opción|Descripción|  
|------------|-----------------|  
|Desactivada|La escritura en el registro de seguimiento está deshabilitada. No se creará ningún registro de **PluginTraceLog**. Sin embargo, el código personalizado puede seguir llamando al método <xref:Microsoft.Xrm.Sdk.ITracingService.Trace(System.String,System.Object[])> aunque no se escriba ningún registro.|  
|Excepciones|La información de seguimiento se escribe en el registro si se pasa una excepción a la plataforma desde código personalizado.|  
|Todo|La información de seguimiento se escribe en el registro cuando se completa el código o se pasa una excepción a la plataforma desde el código personalizado.|  
  
 Si el valor del registro de seguimiento se establece en **Excepción** y el código personalizado devuelve una excepción a la plataforma, se crea un registro de seguimiento y también se escribe información de seguimiento en otra ubicación. Para código personalizado que se ejecuta forma sincrónica, la información se muestra al usuario en un cuadro de diálogo de errores, de lo contrario, para código asincrónico, la información se escribe en el trabajo del sistema relacionado.  
  
 De forma predeterminada, los roles de administrador del sistema y personalizador del sistema tienen los privilegios necesarios para cambiar el valor del registro de seguimiento, que se almacena en un registro de entidad <xref:Microsoft.Xrm.Sdk.Deployment.TraceSettings>. La configuración de seguimiento tiene un ámbito de organización.  
  
## Escriba en el servicio de seguimiento.  
 Antes de escribir en el servicio de seguimiento, primero debe extraer el objeto de servicio de seguimiento del contexto de ejecución pasado. A continuación, agregue simplemente llamadas <xref:Microsoft.Xrm.Sdk.ITracingService.Trace(System.String,System.Object[])> a su código personalizado donde corresponda pasando la información relevante de diagnóstico en esa llamada al método.  

 Descargue el ejemplo: [Trabajar con complementos](https://code.msdn.microsoft.com/Sample-Create-a-basic-plug-64d86ade).
  
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
     tracingService.Trace
         ("AdvancedPlugin: Getting the target entity from Input Parameters.");
     Entity entity = (Entity)context.InputParameters["Target"];

     // Obtain the image entity from the Pre Entity Images.
     tracingService.Trace
         ("AdvancedPlugin: Getting image entity from PreEntityImages.");
     Entity image = (Entity)context.PreEntityImages["Target"];
```

  
 A continuación, genere e implemente el complemento o actividad de flujo de trabajo personalizada. Durante la ejecución del código personalizado, la información proporcionada en las llamadas al método **Trace** es escrita en un registro de entidad del registro de seguimiento por <xref:Microsoft.Xrm.Sdk.ITracingService>, si lo admite la organización y está habilitada, y también se puede poner a disposición del usuario en un diálogo web o un trabajo del sistema como se describe en la sección anterior. La información de seguimiento escrita en el registro de seguimiento está configurada en los valores de seguimiento. Para obtener más información, consulte [Habilitar el registro de seguimiento](#bkmk_trace-settings).  
  
> [!NOTE]
> Si el código personalizado se ejecuta en una transacción de la base de datos y se produce una excepción que provoca una reversión de la transacción, todos los cambios en los datos de la entidad realizados por el código se desharán. Sin embargo, los registros **PluginTraceLog** se mantendrán después de que la reversión se complete.  
  
## Información adicional sobre el servicio de seguimiento.

 El <xref:Microsoft.Xrm.Sdk.ITracingService> trata por lotes la información que se le proporciona con el método **Seguimiento**. La información se escribe en un nuevo registro **PluginTraceLog** después de que el código personalizado se ejecuta correctamente hasta completarse o genera una excepción.  
  
 Los registros PluginTraceLog tienen una duración finita. Un trabajo en segundo plano de eliminación en masa se ejecuta una vez al día para eliminar los registros que tienen más de 24 horas desde su creación. Este trabajo puede deshabilitarse cuando es necesario. 

## Herramientas de la Comunidad

 ### Visor de seguimiento de complementos

**Visor de seguimiento de complementos** es una herramienta desarrollada por Comunidad XrmToolbox para aplicaciones [!INCLUDE[pn_dynamics_crm](../../includes/pn-dynamics-crm.md)]. Consulte el tema [herramientas para desarrolladores](developer-tools.md) para comunidad de herramientas desarrolladas.

> [!NOTE]
> Las herramientas de la Comunidad no son un producto de aplicaciones [!include[pn_microsoft_dynamics](../../includes/pn-microsoft-dynamics.md)] y no se amplía el soporte para las herramientas de comunidad. Si tiene alguna duda relacionada con la herramienta, póngase en contacto con el Editor. Más información: [XrmToolBox](https://www.xrmtoolbox.com).  

### Vea también

[[Complementos](plug-ins.md)](plug-ins.md)  
[[Depurar un complemento](debug-plug-in.md#use-tracing)](debug-plug-in.md#use-tracing)  
[[Ver registros de seguimiento](tutorial-write-plug-in.md#view-trace-logs)](tutorial-write-plug-in.md#view-trace-logs)  
[[Utilizar el servicio de seguimiento.](write-plug-in.md#use-the-tracing-service)](write-plug-in.md#use-the-tracing-service)  
[[Entidad PluginTraceLog](reference/entities/plugintracelog.md)](reference/entities/plugintracelog.md)