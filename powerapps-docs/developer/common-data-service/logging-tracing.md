---
title: Registro y seguimiento (Common Data Service) | Microsoft Docs
description: Use el registro de seguimiento para almacenar la información de ejecución de los complementos para ayudar en la depuración de los complementos.
ms.custom: ''
ms.date: 09/19/2019
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
ms.openlocfilehash: 9a663c8f6a8f37b36d341c2a20c96c2ff7cff3e0
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749425"
---
# <a name="tracing-and-logging"></a>Registro y seguimiento

Use seguimiento para solucionar problemas de una actividad de flujo de trabajo personalizada o de un complemento (código personalizado). El seguimiento ayuda a los desarrolladores registrando información en tiempo de ejecución como ayuda en el diagnóstico de la causa de los errores del código. El seguimiento es compatible con la ejecución síncrona o asincrónica.
  
El registro de información de seguimiento en tiempo de ejecución para Common Data Service se consigue mediante un servicio llamado <xref:Microsoft.Xrm.Sdk.ITracingService>. La información proporcionada a este servicio por el código personalizado se puede registrar en tres distintas secciones que se identifican aquí.  

- **Registro de seguimiento**  
  
    Los registros del registro de seguimiento se escriben en la [Entidad PluginTraceLog](reference/entities/plugintracelog.md). La escritura de estos registros se controla mediante la configuración de seguimiento mencionada en [Habilitar registro de seguimiento](#enable-trace-logging).

    Estos datos se pueden encontrar en aplicaciones basadas en modelos navegando a **Configuración** y eligiendo la ventana **Registro de seguimiento de complementos**. La ventana solo es visible si tiene acceso a los registros de la entidad de registro de seguimiento en su rol de seguridad asignado.

    Es posible que le resulte más fácil ver estos datos mediante API web en el explorador utilizando el ejemplo mostrado en [Utilizar seguimiento](debug-plug-in.md#use-tracing) o utilizando la herramienta de la comunidad [Visor de seguimiento de complementos](#plug-in-trace-viewer).

    > [!IMPORTANT]
    > El registro de seguimiento ocupa espacio de almacenamiento de la organización, especialmente cuando se generan muchos seguimientos y excepciones. Solo debe activar el registro de seguimiento para depurar y solucionar problemas, y desactivarla después de que la investigación esté completa.  
  
- **Diálogo de errores**  
  
     Un complemento registrado sincrónico o una actividad de flujo de trabajo personalizada que devuelve una excepción de la plataforma produce un cuadro de diálogo de error en la aplicación web que se muestran al usuario que ha iniciado sesión. El usuario puede seleccionar el botón **Descargar archivo de registro** en el cuadro de diálogo para ver el registro que contiene la excepción y la salida de seguimiento.  
  
- **Trabajo del sistema**  
  
     Para un complemento registrado asincrónico o actividades de flujo de trabajo personalizadas que devuelven una excepción, la información de seguimiento aparece en el área **Detalles** del formulario **Trabajo del sistema** en la aplicación web.  
  
<a name="bkmk_trace-settings"></a>

## <a name="enable-trace-logging"></a>Habilitar registro de seguimiento

Si los registros de seguimiento se escriben depende del valor del valor del atributo [PluginTraceLogSetting](/powerapps/developer/common-data-service/reference/entities/organization#BKMK_PluginTraceLogSetting) de la entidad [Organización](/powerapps/developer/common-data-service/reference/entities/organization).

Para habilitar el registro de seguimiento puede actualizar mediante programación este valor o en la aplicación web ir a **Configuración** > **Administración** > **Configuración del sistema**. En la pestaña **Personalización**, busque el menú desplegable con la etiqueta **Habilitar registro para registro de seguimientos de complemento** y seleccione una de las opciones disponibles.  
  
|Value|Opción|Descripción|  
|------------|-----------------|-----------------|  
|0|Desactivado|La escritura en el registro de seguimiento está deshabilitada. No se creará ningún registro de **PluginTraceLog**. Sin embargo, el código personalizado puede seguir llamando al método <xref:Microsoft.Xrm.Sdk.ITracingService.Trace(System.String,System.Object[])> aunque no se escriba ningún registro.|  
|1|Excepciones|La información de seguimiento se escribe en el registro si se pasa una excepción a la plataforma desde código personalizado.|  
|2|Todo|La información de seguimiento se escribe en el registro cuando se completa el código o se pasa una excepción a la plataforma desde el código personalizado.|  
  
Si el valor del registro de seguimiento se establece en **Excepción** y el código personalizado devuelve una excepción a la plataforma, se crea un registro de seguimiento y también se escribe información de seguimiento en otra ubicación. Para código personalizado que se ejecuta forma sincrónica, la información se muestra al usuario en un cuadro de diálogo de errores, de lo contrario, para código asincrónico, la información se escribe en el trabajo del sistema relacionado.  

## <a name="write-to-the-tracing-service"></a>Escriba en el servicio de seguimiento.

Antes de escribir en el servicio de seguimiento, primero debe extraer el objeto de servicio de seguimiento del contexto de ejecución pasado. A continuación, agregue simplemente llamadas <xref:Microsoft.Xrm.Sdk.ITracingService.Trace(System.String,System.Object[])> a su código personalizado donde corresponda pasando la información relevante de diagnóstico en esa llamada al método.  

  
 ```csharp
//Extract the tracing service for use in debugging plug-ins.
 ITracingService tracingService =
     (ITracingService)serviceProvider.GetService(typeof(ITracingService));

 // Use the tracing service 
 tracingService.Trace("Write your message here.");
 
```

A continuación, genere e implemente el complemento o actividad de flujo de trabajo personalizada. Durante la ejecución del código personalizado, la información proporcionada en las llamadas al método **Trace** es escrita en un registro de entidad del registro de seguimiento por <xref:Microsoft.Xrm.Sdk.ITracingService>, si lo admite la organización y está habilitada, y también se puede poner a disposición del usuario en un diálogo web o un trabajo del sistema como se describe en la sección anterior. La información de seguimiento escrita en el registro de seguimiento está configurada en los valores de seguimiento. Para obtener más información, consulte [Habilitar el registro de seguimiento](#bkmk_trace-settings).  
  
> [!NOTE]
> Si el código personalizado se ejecuta en una transacción de la base de datos y se produce una excepción que provoca una reversión de la transacción, todos los cambios en los datos de la entidad realizados por el código se desharán. Sin embargo, los registros [PluginTraceLog](reference/entities/plugintracelog.md) se mantendrán después de que la reversión se complete.  
  
## <a name="additional-information-about-the-tracing-service"></a>Información adicional sobre el servicio de seguimiento.

El <xref:Microsoft.Xrm.Sdk.ITracingService> trata por lotes la información que se le proporciona con el método **Seguimiento**. La información se escribe en un nuevo registro [PluginTraceLog](reference/entities/plugintracelog.md) después de que el código personalizado se ejecuta correctamente hasta completarse o genera una excepción.  

Cada llamada de traza se registra como una nueva línea en el atributo [PluginTraceLog](reference/entities/plugintracelog.md) [MessageBlock](reference/entities/plugintracelog.md#BKMK_MessageBlock). Solo 10 kb de texto se pueden escribir. Se quitarán las líneas de traza para cumplir este límite de modo que solo las líneas más recientes se guardarán.
  
Los registros [PluginTraceLog](reference/entities/plugintracelog.md) tienen una duración finita. Un trabajo en segundo plano de eliminación en masa se ejecuta una vez al día para eliminar los registros que tienen más de 24 horas desde su creación. 

> [!CAUTION]
> Mientras este trabajo se puede deshabilitar o la frecuencia con la que aparece puede ser ajustada, si no se restablece el valor original con frecuencia es la causa de problemas de rendimiento más adelante.

## <a name="community-tools"></a>Herramientas de la Comunidad

 ### <a name="plug-in-trace-viewer"></a>Visor de seguimiento de complementos

**Visor de seguimiento de complementos** es una herramienta desarrollada por la comunidad XrmToolbox. Consulte el tema [Herramientas de la Comunidad para Common Data Service](community-tools.md) para herramientas desarrolladas por la comunidad.

> [!NOTE]
> Las herramientas de la comunidad no son un producto de Microsoft y no se incluyen en el soporte técnico. Si tiene alguna duda relacionada con la herramienta, póngase en contacto con el Editor. Más información: [XrmToolBox](https://www.xrmtoolbox.com).  

### <a name="see-also"></a>Vea también

[Complementos](plug-ins.md)  
[Depurar un complemento](debug-plug-in.md#use-tracing)  
[Ver registros de seguimiento](tutorial-write-plug-in.md#view-trace-logs)  
[Utilizar el servicio de seguimiento.](write-plug-in.md#use-the-tracing-service)  
[Entidad PluginTraceLog](reference/entities/plugintracelog.md)