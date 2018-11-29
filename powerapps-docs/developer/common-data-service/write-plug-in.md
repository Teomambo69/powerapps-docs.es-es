---
title: Escribir un complemento (Common Data Service para aplicaciones) | Microsoft Docs
description: Obtener información sobre los conceptos y los detalles técnicos necesarios para escribir complementos
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
# <a name="write-a-plug-in"></a>Escribir un complemento

El proceso para escribir, registrar y depurar un complemento es:

1. **Crear un proyecto de biblioteca de clases de .NET Framework en Visual Studio**
1. **Agregar el paquete `Microsoft.CrmSdk.CoreAssemblies` NuGet al proyecto**
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

### <a name="optimize-assembly-development"></a>Optimizar el desarrollo de ensamblados

El ensamblado debe incluir múltiples clases (o tipos) de complementos, pero no pueden ser mayores de 16 MB. Se recomienda consolidar complementos y ensamblados de flujo de trabajo en un único ensamblado siempre que el tamaño se mantenga por debajo de 16 MB. Más información: [Optimizar desarrollo de ensamblados](/dynamics365/customer-engagement/guidance/server/optimize-assembly-development)

### <a name="assemblies-must-be-signed"></a>Las ensamblados deben estar firmados

Todos los ensamblados deben estar firmados antes de poder registrarlos. Esto se puede hacer mediante la pestaña Firma de Visual Studio en el proyecto o mediante [Sn.exe (herramienta Nombre seguro)](/dotnet/framework/tools/sn-exe-strong-name-tool)el.

### <a name="do-not-depend-on-net-assemblies-that-interact-with-low-level-windows-apis"></a>No dependen de los ensamblados .NET que interactúan con API de Windows de bajo nivel

Los ensamblados de complementos deben contener toda la lógica necesaria dentro del dll respectivo.  Los complementos pueden hacer referencia a algunos ensamblados .Net principales. Sin embargo, no se admiten las dependencias de ensamblados .Net que interactúen con las APIs de Windows de bajo nivel, como la interfaz de diseño gráfico.

## <a name="iplugin-interface"></a>Interfaz de IPlugin

Un complemento es un clase dentro de un ensamblado creada mediante un proyecto de biblioteca de clases de .NET Framework usando .NET Framework 4.5.2 en Visual Studio. Cada clase en el proyecto que se registrará como paso debe implementar la interfaz <xref:Microsoft.Xrm.Sdk.IPlugin> que requiere el método <xref:Microsoft.Xrm.Sdk.IPlugin.Execute*>.

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
Los datos de configuración seguro se almacenan en una entidad aparte que sólo los administradores del sistema tienen privilegios para leer. Más información: [Establecer datos de configuración](register-plug-in.md#set-configuration-data)

## <a name="services-you-can-use-in-your-code"></a>Servicios que puede usar en el código

En el complemento deberá:
 
- Obtener acceso a la información contextual sobre lo que ocurre en el evento que el complemento se registró para administrar. Esto se llama *contexto de ejecución*.
- Obtener acceso al servicio web de la organización para poder escribir código para consultar datos, trabajar con registros de entidad, usar mensajes para realizar operaciones.
- Escribir mensajes al servicio de seguimiento para poder evaluar cómo se está ejecutando el código.

La propiedad <xref:System.IServiceProvider>.<xref:System.IServiceProvider.GetService*> el método proporciona una forma de tener acceso a estos servicios según sea necesario. Para obtener una instancia del servicio invoque el método `GetService` que pasa el tipo de servicio.

> [!NOTE]
> Cuando escribe un complemento que usa la integración Azure Service Bus, usará un servicio de notificación que implementa la interfaz <xref:Microsoft.Xrm.Sdk.IServiceEndpointNotificationService>, pero esto no se describirá aquí. Más información: [Integración de Azure](azure-integration.md)

## <a name="execution-context"></a>Contexto de ejecución

Puede obtener una variable que implemente la interfaz <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext> mediante el siguiente código:

```csharp
// Obtain the execution context from the service provider.  
IPluginExecutionContext context = (IPluginExecutionContext)
    serviceProvider.GetService(typeof(IPluginExecutionContext));
```

Este <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext> proporciona información sobre la <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext.Stage> para el que está registrado el complemento, así como información sobre el <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext.ParentContext> que proporciona información sobre cualquier operación en otro complemento que activó la operación actual.

Pero el resto de la información disponible es proporcionada por la interfaz <xref:Microsoft.Xrm.Sdk.IExecutionContext> que implementa esta clase. Todas las propiedades de esta clase proporcionan información útil que puede necesitar para acceder en el código, pero dos de las más importante son las propiedades <xref:Microsoft.Xrm.Sdk.IExecutionContext.InputParameters> y <xref:Microsoft.Xrm.Sdk.IExecutionContext.OutputParameters>. 

Otras propiedades usadas con frecuencia son <xref:Microsoft.Xrm.Sdk.IExecutionContext.SharedVariables>, <xref:Microsoft.Xrm.Sdk.IExecutionContext.PreEntityImages> y <xref:Microsoft.Xrm.Sdk.IExecutionContext.PostEntityImages>.

> [!TIP]
> Una buena manera de visualizar los datos que se pasan al contexto de ejecución es instalar la solución del generador de perfiles de complementos que está disponible como parte de la herramienta de registro de complementos. El generador de perfiles capturará la información de contexto así como información que permite reproducir el evento localmente para poder depurar. En la herramienta de registro de complementos, puede descargar un documento xml con todos los datos del evento que desencadenó el flujo de trabajo. Más información: [Ver datos del perfil de complementos](debug-plug-in.md#view-plug-in-profile-data)

### <a name="work-with-parametercollections"></a>Trabajar con ParameterCollections

Todas las propiedades del contexto de ejecución son de solo lectura. Pero los `InputParameters`, `OutputParameters`, y `SharedVariables` son valores <xref:Microsoft.Xrm.Sdk.ParameterCollection>. Puede manipular los valores de los elementos de estas colecciones para cambiar el comportamiento de la operación, en función de la fase de la canalización de ejecuciones de eventos para la que está registrado el complemento.

Los valores <xref:Microsoft.Xrm.Sdk.ParameterCollection> se definen como estructuras <xref:System.Collections.Generic.KeyValuePair%602>. Para obtener acceso a una propiedad deberá conocer el nombre de la propiedad que revela el mensaje. Por ejemplo, para obtener acceso a la propiedad <xref:Microsoft.Xrm.Sdk.Entity> que se pasa como parte de <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>, es necesario saber que el nombre de esa propiedad es `Target`. A continuación puede obtener acceso a este valor utilizando código como éste:

```csharp
var entity = (Entity)context.InputParameters["Target"];
```
Use la documentación de <xref:Microsoft.Xrm.Sdk.Messages> y <xref:Microsoft.Crm.Sdk.Messages> para conocer los nombres de los mensajes definidos en los ensamblados del SDK. Para acciones personalizadas, consulte los nombres de los parámetros definidos en el sistema.

### <a name="inputparameters"></a>InputParameters

Los `InputParameters` representan el valor de la propiedad <xref:Microsoft.Xrm.Sdk.OrganizationRequest>.<xref:Microsoft.Xrm.Sdk.OrganizationRequest.Parameters> que representa la operación procedente de los servicios web.

Como se describe en [Usar mensajes con el servicio de la organización](org-service/use-messages.md), todas las operaciones que se producen en el sistema son en definitiva instancias de al case `OrganizationRequest` que está procesando el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> .

Como se describe en [Marco de trabajo de eventos](event-framework.md), las operaciones pasan a través de una serie de fases y puede registrar el complemento en fases que se producen antes de que los datos se escriban en la base de datos. En las fases **PreValidation** y **PreOperation**, puede leer y cambiar los valores de los `InputParameters` de modo que puede controlar el resultado esperado de la operación de datos.

Si encuentra que los valores de la colección de `InputParameters` representan una condición que no puede permitir, puede lanzar una <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> (preferentemente en la fase de **PreValidation**) que cancelará la operación y mostrará un error al usuario con un complemento sincrónico, o registrará el error si el complemento es asincrónico. Más información: [Cancelación de una operación](#cancelling-an-operation)

### <a name="outputparameters"></a>OutputParameters

Los `OutputParameters` representan el valor de la propiedad <xref:Microsoft.Xrm.Sdk.OrganizationResponse>.<xref:Microsoft.Xrm.Sdk.OrganizationResponse.Results> que representa el valor devuelto de la operación. Los `OutputParameters` no se rellenan hasta después de la transacción de base de datos, de modo que solo están disponibles para complementos registrados en la fase **PostOperation**. Si desea cambiar los valores devueltos por la operación, puede modificarlos en los `OutputParameters`.

### <a name="shared-variables"></a>Variables compartidas

La propiedad <xref:Microsoft.Xrm.Sdk.IExecutionContext.SharedVariables> permite incluir los datos que se pueden pasar de un complemento a un paso que se produce después en la canalización de ejecuciones. Dado que este es un valor de <xref:Microsoft.Xrm.Sdk.ParameterCollection>, los complementos pueden agregar, leer o modificar propiedades para compartir datos con pasos posteriores.

El siguiente ejemplo muestra cómo se puede pasar un valor `PrimaryContact` desde un complemento registrado para un paso de **PreOperation** a un paso **PostOperation**.

```csharp
public class PreOperation : IPlugin
{
    public void Execute(IServiceProvider serviceProvider)
    {
        // Obtain the execution context from the service provider.
        Microsoft.Xrm.Sdk.IPluginExecutionContext context = (Microsoft.Xrm.Sdk.IPluginExecutionContext)
            serviceProvider.GetService(typeof(Microsoft.Xrm.Sdk.IPluginExecutionContext));

        // Create or retrieve some data that will be needed by the post event
        // plug-in. You could run a query, create an entity, or perform a calculation.
        //In this sample, the data to be passed to the post plug-in is
        // represented by a GUID.
        Guid contact = new Guid("{74882D5C-381A-4863-A5B9-B8604615C2D0}");

        // Pass the data to the post event plug-in in an execution context shared
        // variable named PrimaryContact.
        context.SharedVariables.Add("PrimaryContact", (Object)contact.ToString());
    }
}

public class PostOperation : IPlugin
{
    public void Execute(IServiceProvider serviceProvider)
    {
        // Obtain the execution context from the service provider.
        Microsoft.Xrm.Sdk.IPluginExecutionContext context = (Microsoft.Xrm.Sdk.IPluginExecutionContext)
            serviceProvider.GetService(typeof(Microsoft.Xrm.Sdk.IPluginExecutionContext));

        // Obtain the contact from the execution context shared variables.
        if (context.SharedVariables.Contains("PrimaryContact"))
        {
            Guid contact =
                new Guid((string)context.SharedVariables["PrimaryContact"]);

            // Do something with the contact.
        }
    }
}
```


### <a name="entity-images"></a>Imágenes de entidad

Al registrar una paso para un complemento que incluye una entidad como uno de los parámetros, tiene la opción de especificar que una copia de los datos de la entidad se incluya como *instantánea* o imagen mediante las propiedades <xref:Microsoft.Xrm.Sdk.IExecutionContext.PreEntityImages> y/o <xref:Microsoft.Xrm.Sdk.IExecutionContext.PostEntityImages>.

Estos datos proporcionan un punto de comparación para los datos de entidad mientras atraviesan la canalización de eventos. El uso de estas imágenes proporciona un rendimiento mucho mejor que incluir código en un complemento para recuperar una entidad solo para comparar los valores de atributo.

Al definir una imagen de la entidad, especifique un valor de alias de entidad que puede usar para tener acceso a la imagen específica. Por ejemplo, si define pre una imagen de preentidad con el alias '`a`', puede usar el siguiente código para acceder al valor del atributo `name`.

```csharp
var oldAccountName = (string)context.PreEntityImages["a"]["name"];
```

Más información: [Definir imágenes de entidad](register-plug-in.md#define-entity-images)

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

## <a name="impersonation"></a>Suplantación

A veces necesita el código en un complemento para ejecutarse en el contexto de otro usuario.

Hay dos formas de aplicar suplantación en complementos: en el registro o la ejecución.

### <a name="at-plug-in-registration"></a>En el registro de complementos

Al registrar una paso de complemento puede especificar una cuenta de usuario para usar cuando el código se ejecuta eligiendo desde la opción **Ejecutar en contexto de usuario**. De forma predeterminada esta opción se establece para usar el **Usuario que llama**, que es la cuenta de usuario que inició la acción. Cuando se aplica esta opción predeterminada, el [SdkMessageProcessingStep.ImpersonatingUserId](reference/entities/sdkmessageprocessingstep.md#BKMK_ImpersonatingUserId) se establecerá como nulo o <xref:System.Guid.Empty>.

Más información: [Registrar paso de complemento](register-plug-in.md#register-plug-in-step).

### <a name="during-plug-in-execution"></a>Durante la ejecución de complemento

Puede reemplazar el valor especificado en el registro en tiempo de ejecución estableciendo el parámetro <xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory>.<xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory.CreateOrganizationService(System.Nullable{System.Guid})> `userId`.

Este normalmente se establece con el valor <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.UserId> que aplicará la cuenta de usuario definida por el registro de paso de complemento.

```csharp
(IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
    IOrganizationService service = serviceFactory.CreateOrganizationService(context.UserId);
```

Si desea reemplazar el registro del paso puede pasar el valor del <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.InitiatingUserId> para tener un servicio que usará la cuenta de usuario que inició la acción que produjo la ejecución del complemento.

También puede proporcionar el [SystemUser.SystemUserId](reference/entities/systemuser.md#BKMK_SystemUserId) desde cualquier cuenta de usuario válida. Esto funcionará siempre que el usuario tenga permisos para realizar las operaciones en el complemento.

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

Más información: [Usar seguimiento](debug-plug-in.md#use-tracing).



## <a name="cancelling-an-operation"></a>Cancelación de una operación

El código puede ocasionar que una operación se cancele lanzando una excepción. Cualquier excepción no controlada hará que la operación se cancele, por lo que es importante que aplique prácticas de código para administrar las excepciones que se lancen y decidir si permite cancelar la operación o no.

Si la lógica de negocios dicta que la operación debe ser cancelada, debe lanzar una excepción <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> y proporcionar un mensaje para explicar por qué la operación se ha cancelado.

Cuando lanza una excepción <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> en un complemento sincrónico se mostrará al usuario un diálogo de error con el mensaje. Si no proporciona un mensaje, se mostrará un diálogo de error genérico al usuario. Si lanza a cualquier otro tipo de excepción, el usuario verá un diálogo de error con un mensaje genérico y el mensaje de excepción y el seguimiento de la pila se escribirán en la [Entidad PluginTraceLog](reference/entities/plugintracelog.md)

Idealmente, debe cancelar solo operaciones que utilicen complementos síncronos registrados en la fase de **PreValidation**. Esta fase *normalmente* se produce fuera de la transacción de la base de datos principal. La cancelación de una operación antes de que alcance la transacción es muy deseable porque la operación cancelada tiene que revertirse. La reversión de la operación requiere recursos significado y tiene un impacto en el rendimiento del sistema. Las operaciones en las fases **PreOperation** y **PostOperation** están siempre en la transacción de la base de datos.

Las fases **PreValidation** a veces estarán en una transacción cuando las inicie la lógica en otra operación. Por ejemplo, si crea un registro de entidad de tarea en la fase **PreOperation** de la creación de una cuenta, la creación de tarea pasará a través de la canalización de ejecuciones de eventos y se producirá en la fase **PreValidation**, pero será parte de la transacción que está creando el registro de la entidad de cuenta. Puede saber si una operación está en una transacción para el valor de la propiedad <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.IsInTransaction> .

## <a name="performance-considerations"></a>Consideraciones sobre el rendimiento

Al agregar lógica de negocios para el complemento necesita tener muy en cuenta el impacto que tendrán en el rendimiento general. La lógica de negocios en complementos no debe tardar más de 2 segundos en completarse.

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

Estos datos también están disponibles para que usted los examine mediante [Panel Complementos de Información de la organización](/dynamics365/customer-engagement/admin/use-organization-insights-solution-view-instance-metrics#plug-ins), junto con muchos otros informes útiles.


## <a name="next-steps"></a>Pasos siguientes

[Registrar un complemento](register-plug-in.md)<br />
[Depuración de complementos](debug-plug-in.md)

### <a name="see-also"></a>Vea también

[Escriba complementos para ampliar los procesos de negocio](plug-ins.md)<br />
[Tutorial: Escribir y registrar un complemento](tutorial-write-plug-in.md)<br />
[Tutorial: Depurar un complemento](tutorial-debug-plug-in.md)<br />
[Tutorial: Actualizar un complemento](tutorial-update-plug-in.md)<br />
