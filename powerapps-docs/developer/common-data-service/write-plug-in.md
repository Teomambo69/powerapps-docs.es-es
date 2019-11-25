---
title: Escribir un complemento (Common Data Service) | Microsoft Docs
description: Obtener información sobre los conceptos y los detalles técnicos necesarios para escribir complementos
ms.custom: ''
ms.date: 07/03/2019
ms.reviewer: ''
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
ms.openlocfilehash: d1fa83ed9ac70bcacfc1d76065f09dcae9e96555
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749480"
---
# <a name="write-a-plug-in"></a>Escribir un complemento

El proceso para escribir, registrar y depurar un complemento es:

1. **Crear un proyecto de biblioteca de clases de .NET Framework en Visual Studio**
1. **Agregar el paquete `Microsoft.CrmSdk.CoreAssemblies`NuGet al proyecto**
1. **Implementar la interfaz <xref:Microsoft.Xrm.Sdk.IPlugin> en clases que se registrarán como pasos.**
1. **Agregar su código al método <xref:Microsoft.Xrm.Sdk.IPlugin.Execute*> requerido por la interfaz**
    1. **Obtener las referencias a los servicios que necesita**
    1. **Adición de lógica de negocios**
1. **Firmar y crear el ensamblado**
1. Probar el ensamblado
    1. Registrar el ensamblado en un entorno de prueba
    1. Agregar el ensamblado registrado y pasos a una solución no administrada
    1. Probar el comportamiento del ensamblado
    1. Comprobar que se escriben los registros de seguimiento esperados
    1. Depure el ensamblado según sea necesario

El contenido de este tema analiza los pasos anteriores **en negrita** y ofrece los tutoriales siguientes:

- [Tutorial: Escribir y registrar un complemento](tutorial-write-plug-in.md)
- [Tutorial: Depurar un complemento](tutorial-debug-plug-in.md)
- [Tutorial: Actualizar un complemento](tutorial-update-plug-in.md)

## <a name="assembly-constraints"></a>Restricciones de ensamblado

Tenga en cuenta las siguientes restricciones cuando cree ensamblados.

### <a name="use-net-framework-462"></a>Usar .NET Framework 4.6.2

Los complementos y ensamblados de flujo de trabajo personalizadas deben usar .NET Framework 4.6.2. Si bien los ensamblados construidos con versiones posteriores deben funcionar normalmente, si usan características introducidas después de 4.6.2 se producirá un error.

### <a name="optimize-assembly-development"></a>Optimizar el desarrollo de ensamblados

El ensamblado debe incluir múltiples clases (o tipos) de complementos, pero no pueden ser mayores de 16 MB. Se recomienda consolidar complementos y ensamblados de flujo de trabajo en un único ensamblado siempre que el tamaño se mantenga por debajo de 16 MB. Más información: [Optimizar desarrollo de ensamblados](/dynamics365/customer-engagement/guidance/server/optimize-assembly-development)

### <a name="assemblies-must-be-signed"></a>Las ensamblados deben estar firmados

Todos los ensamblados deben estar firmados antes de poder registrarlos. Esto se puede hacer mediante la pestaña Firma de Visual Studio en el proyecto o mediante [Sn.exe (herramienta Nombre seguro)](/dotnet/framework/tools/sn-exe-strong-name-tool).

### <a name="do-not-depend-on-net-assemblies-that-interact-with-low-level-windows-apis"></a>No dependen de los ensamblados .NET que interactúan con API de Windows de bajo nivel

Los ensamblados de complementos deben contener toda la lógica necesaria dentro del dll respectivo.  Los complementos pueden hacer referencia a algunos ensamblados .Net principales. Sin embargo, no se admiten las dependencias de ensamblados .Net que interactúen con las APIs de Windows de bajo nivel, como la interfaz de diseño gráfico.

## <a name="iplugin-interface"></a>Interfaz de IPlugin

Un complemento es un clase dentro de un ensamblado creada mediante un proyecto de biblioteca de clases de .NET Framework usando .NET Framework 4.6.2 en Visual Studio. Cada clase en el proyecto que se registrará como paso debe implementar la interfaz <xref:Microsoft.Xrm.Sdk.IPlugin> que requiere el método <xref:Microsoft.Xrm.Sdk.IPlugin.Execute*>.

> [!IMPORTANT]
> Al implementar `IPlugin`, la clase debe ser *sin estado*. Esto se debe a que la plataforma almacena en caché una instancia de clase y la reutiliza por razones de rendimiento. Una forma sencilla de ver esto es que no debe agregar ninguna propiedad ni método a la clase y todo debe estar incluido en el método `Execute`. Hay algunas excepciones a esto. Por ejemplo puede tener una propiedad que representa una constante y puede tener métodos que representen las funciones que se llaman desde el método `Execute`. Lo importante es que nunca almacene ninguna instancia de servicio o datos de contexto como propiedad en la clase. Estos cambian con cada invocación y no conviene que los datos se almacenen en caché y se apliquen a invocaciones posteriores.  Más información: [Desarrollar implementaciones de IPlugin como sin estado](/dynamics365/customer-engagement/guidance/server/develop-iplugin-implementations-stateless)

El método <xref:Microsoft.Xrm.Sdk.IPlugin.Execute*> acepta un único parámetro <xref:System.IServiceProvider>. El `IServiceProvider` tiene un solo método:  <xref:System.IServiceProvider.GetService*>. Usará este método para obtener varios tipos distintos de servicios que puede usar en su código. Más información: [Servicios que puede usar en el código](#services-you-can-use-in-your-code)

## <a name="pass-configuration-data-to-your-plug-in"></a>Pasar datos de configuración al complemento

Al registrar un complemento tiene la capacidad de pasarle datos de configuración. Los datos de configuración permiten definir cómo una instancia específica de un complemento registrado debe comportarse. Esta información se pasa como datos de cadena a los parámetros en el constructor de la clase. Hay dos parámetros: `unsecure` y `secure`.
Use el primer parámetro `unsecure` para datos que no le importe que vea la gente. Use el segundo parámetro `secure` para datos confidenciales. 

El código siguiente muestra las tres firmas posibles para una clase de complemento llamada `SamplePlugin`.

```csharp
public SamplePlugin()  
public SamplePlugin(string unsecure)  
public SamplePlugin(string unsecure, string secure)
```
Los datos de configuración seguro se almacenan en una entidad aparte que sólo los administradores del sistema tienen privilegios para leer. Más información: [Registrar paso del complemento > Establecer datos de configuración](register-plug-in.md#set-configuration-data)

## <a name="services-you-can-use-in-your-code"></a>Servicios que puede usar en el código

En el complemento deberá:
 
- Obtener acceso a la información contextual sobre lo que ocurre en el evento que el complemento se registró para administrar. Esto se llama *contexto de ejecución*.
- Obtener acceso al servicio web de la organización para poder escribir código para consultar datos, trabajar con registros de entidad, usar mensajes para realizar operaciones.
- Escribir mensajes al servicio de seguimiento para poder evaluar cómo se está ejecutando el código.

La propiedad <xref:System.IServiceProvider>.<xref:System.IServiceProvider.GetService*> el método proporciona una forma de tener acceso a estos servicios según sea necesario. Para obtener una instancia del servicio invoque el método `GetService` que pasa el tipo de servicio.

> [!NOTE]
> Cuando escribe un complemento que usa la integración Azure Service Bus, usará un servicio de notificación que implementa la interfaz <xref:Microsoft.Xrm.Sdk.IServiceEndpointNotificationService>, pero esto no se describirá aquí. Más información: [Integración de Azure](azure-integration.md)

## <a name="organization-service"></a>Servicio de organización

Para trabajar con datos en un complemento, use el servicio de la organización. No intente usar la API web. Los complementos están optimizados para usar ensamblados del .NET SDK.

Para obtener acceso a una variable `svc` que implemente la interfaz <xref:Microsoft.Xrm.Sdk.IOrganizationService>, use el siguiente código:


```csharp
// Obtain the organization service reference which you will need for  
// web service calls.  
IOrganizationServiceFactory serviceFactory =
    (IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
IOrganizationService svc = serviceFactory.CreateOrganizationService(context.UserId);
```

La variable `context.UserId` usada con <xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory>.<xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory.CreateOrganizationService(System.Nullable{System.Guid})> procede del contexto de ejecución de la propiedad <xref:Microsoft.Xrm.Sdk.IExecutionContext.UserId>, por lo que se llama después de haber accedido al contexto de ejecución.

Más información:

- [Operaciones de la entidad](org-service/entity-operations.md)
- [Consultar datos](org-service/entity-operations-query-data.md)
- [Crear entidades](org-service/entity-operations-create.md)
- [Recuperar una entidad](org-service/entity-operations-retrieve.md)
- [Actualizar y eliminar entidades](org-service/entity-operations-update-delete.md)
- [Asociar y desasociar entidades](org-service/entity-operations-associate-disassociate.md)
- [Usar mensajes](org-service/use-messages.md)
- [Programación en tiempo de ejecución y en tiempo de compilación](org-service/early-bound-programming.md)

Puede usar tipos de compilación en un complemento. Basta incluir el archivo de tipos generado en el proyecto. Pero debería tener en cuenta que todos los tipos de entidad proporcionados por los parámetros de entrada del contexto de ejecución serán tipos de ejecución. Deberá convertirlos a tipos de compilación. Por ejemplo puede realizar las siguientes acciones cuando sabe que el parámetro `Target` representa una entidad de cuenta.

```csharp
Account acct = context.InputParameters["Target"].ToEntity<Account>();
``` 
Pero nunca debe intentar establecer el valor con un tipo de compilación. No intente hacer esto:

```csharp
context.InputParameters["Target"] = new Account() { Name = "MyAccount" }; // WRONG: Do not do this. 
```

Esto hará que se produzca una <xref:System.Runtime.Serialization.SerializationException>.

## <a name="use-the-tracing-service"></a>Utilizar el servicio de seguimiento.

Use el servicio de seguimiento para escribir mensajes a la [Entidad PluginTraceLog](reference/entities/plugintracelog.md) para poder revisar los registros y comprender qué sucedió cuando se ejecutó el complemento.

Para escribir el registro de seguimientos, debe obtener una instancia del servicio de seguimiento. El siguiente código muestra cómo obtener una instancia del servicio de seguimiento mediante el método <xref:System.IServiceProvider> el.<xref:System.IServiceProvider.GetService*> .


```csharp
// Obtain the tracing service
ITracingService tracingService =
(ITracingService)serviceProvider.GetService(typeof(ITracingService));
```

Para escribir el seguimiento, use el método <xref:Microsoft.Xrm.Sdk.ITracingService>.<xref:Microsoft.Xrm.Sdk.ITracingService.Trace*> .

```csharp
tracingService.Trace("Write {0} {1}.", "your", "message");
```

Más información: [Usar el seguimiento](debug-plug-in.md#use-tracing), [Registro y seguimiento](logging-tracing.md).

## <a name="performance-considerations"></a>Consideraciones sobre el rendimiento

Al agregar lógica de negocios para el complemento necesita tener muy en cuenta el impacto que tendrán en el rendimiento general.

> [!IMPORTANT]
> La lógica de negocios en complementos registrados para pasos sincrónicos no debe tardar más de 2 segundos en completarse.

### <a name="time-and-resource-constraints"></a>Restricciones de tiempo y de recursos

Hay un límite de tiempo de 2 minutos para que las operaciones de mensaje se completen. También existen limitaciones de la cantidad de CPU y recursos de memoria que pueden usar las extensiones. Si se superan los límites se lanza una excepción y la operación se cancelará.

Si se supera el límite de tiempo, se producirá una <xref:System.TimeoutException>. Si alguna extensión personalizada supera el umbral de la CPU, la memoria o el control de límites, o si de otra manera no responde, la plataforma eliminará ese proceso. En ese momento cualquier extensión actual de dicho proceso producirá un error con excepciones. Sin embargo, la próxima vez que se ejecute la extensión se ejecutará normalmente.

### <a name="monitor-performance"></a>Supervisar el rendimiento

La información en tiempo de ejecución sobre complementos y extensiones de flujo de trabajo personalizadas se capturan y almacenan en [Entidad PluginTypeStatistic](reference/entities/plugintypestatistic.md). Estos registros se rellenan entre 30 minutos y una hora después de que el código personalizado se ejecute. Esta entidad proporciona los puntos de datos siguientes:

|**Atributo**|**Descripción**|
|--|--|
|AverageExecuteTimeInMilliseconds|Tiempo de ejecución promedio (en milisegundos) para el tipo de complemento. |
|CrashContributionPercent|Porcentaje de contribución del tipo de complemento con respecto a los bloqueos. |
|CrashCount|Número de veces que el tipo de complemento se bloqueó. |
|CrashPercent|Porcentaje de bloqueos para el tipo de complemento. |
|ExecuteCount|Número de veces que se ejecutó el tipo de complemento. |
|FailureCount |Número de veces que se produjo un error en el tipo de complemento. |
|FailurePercent|Porcentaje de errores para el tipo de complemento. |
|PluginTypeIdName|Identificador único del usuario que modificó las estadísticas del tipo de complemento por última vez. |
|TerminateCpuContributionPercent |Finalización del porcentaje de contribución del tipo de complemento al proceso de trabajo debido al uso excesivo de la CPU. |
|TerminateHandlesContributionPercent |Finalización del porcentaje de contribución del tipo de complemento al proceso de trabajo debido al uso excesivo del identificador. |
|TerminateMemoryContributionPercent|Finalización del porcentaje de contribución del tipo de complemento al proceso de trabajo debido al uso excesivo de la memoria. |
|TerminateOtherContributionPercent|Finalización del porcentaje de contribución del tipo de complemento al proceso de trabajo por razones desconocidas. |

Estos datos también están disponibles para que los examine mediante el [Centro de administración de Power Platform](https://admin.powerplatform.microsoft.com/). Seleccione **Análisis** > **Common Data Service** > **Complementos**.


## <a name="next-steps"></a>Pasos siguientes

[Registro de un complemento](register-plug-in.md)<br />
[Depuración de complementos](debug-plug-in.md)

### <a name="see-also"></a>Vea también

[Escriba complementos para ampliar los procesos de negocio](plug-ins.md)<br />
[Prácticas recomendadas e instrucciones sobre el desarrollo de complementos y flujos de trabajo](best-practices/business-logic/index.md)
[Administrar excepciones](handle-exceptions.md)<br />
[Suplantar a un usuario](impersonate-a-user.md)<br />
[Tutorial: Escribir y registrar un complemento](tutorial-write-plug-in.md)<br />
[Tutorial: Depurar un complemento](tutorial-debug-plug-in.md)<br />
[Tutorial: Actualizar un complemento](tutorial-update-plug-in.md)<br />
