---
title: Extensiones de flujo de trabajo (Common Data Service para aplicaciones) | Microsoft Docs
description: Puede extender las opciones disponibles en el diseñador para flujos de trabajo. Estas extensiones se agregan agregando un ensamblado que contiene una clase que extiende la clase CodeActivity. Estas extensiones suelen denominarse ensamblados de flujo de trabajo o actividades de flujo de trabajo.
ms.custom: ''
ms.date: 10/31/2018
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
---
# <a name="workflow-extensions"></a>Extensiones de flujo de trabajo

Puede extender las opciones disponibles en el diseñador para flujos de trabajo que se usan en Common Data Service para aplicaciones. Estas extensiones se agregan agregando un ensamblado que contiene una clase que extiende la clase [CodeActivity](/dotnet/api/system.activities.codeactivity). Estas extensiones suelen denominarse ensamblados de flujo de trabajo o actividades de flujo de trabajo.

Puede usar estas extensiones personalizadas en el diseñador usado para flujos de trabajo, acciones personalizadas, y diálogos.

> [!IMPORTANT]
> Siempre que sea posible, primero debe considerar aplicar una de las opciones declarativas para definir la lógica de negocios. Más información: [Aplicar lógica de negocios en Common Data Service para aplicaciones](../../../maker/common-data-service/cds-processes.md)<br/><br/>
> Use las extensiones de flujo de trabajo cuando un proceso declarativo no cumpla su requisito.

## <a name="when-to-create-a-workflow-extension"></a>Cuándo crear una extensión de flujo de trabajo

Si no encuentra la funcionalidad que requiere usando las actividades de proceso predeterminadas, puede agregar actividades personalizadas para que estén disponibles en el editor usado para componer procesos de flujo de trabajo, diálogo, y acción.

De manera predeterminada, estos procesos incluyen un conjunto común de actividades que puede realizar como se muestra en la tabla siguiente:

|Actividad|Flujo de trabajo|Para|Diálogo|
|--|--|--|--|
|Consultar datos|||X|
|Asignar valor||X|X|
|Crear registro|X|X|X|
|Actualizar registro|X|X|X|
|Asignar registro|X|X|X|
|Enviar correo electrónico|X|X|X|
|Iniciar flujo de trabajo secundario|X|X|X|
|Realizar acción|X|X||
|Vincular diálogo secundario|||X|
|Cambiar estado|X|X|X|
|Detener flujo de trabajo|X|X||
|Detener diálogo|||X|

Puede usar la actividad **Realizar acción** para ejecutar cualquier acción personalizada o los mensajes del sistema siguientes denominados **Acciones del comando**:

||||
|--|--|--|
|AddToQueue|AddUserToRecordTeam|RemoveUserFromRecordTeam|
|SetProcess|SetWordTemplate||

Si tiene soluciones de Dynamics 365 Customer Engagement Sales o Service, puede encontrar otras acciones del comando en función de la solución:

||||
|--|--|--|
|ApplyRoutingRule|CalculateActualValue|CloseOpportunity|
|GetQuoteProductsFromOpportunity|GetSalesOrderProductsFromOpportunity|LockInvoicePricing|
|LockSalesOrderPricing|QualifyLead|RemoveUserFromRecordTeam|
|ResolveIncident|ResolveQuote|Revisar|
|UnlockInvoicePricing|UnlockSalesOrderPricing|

Más información: 

- [Configurar fases y pasos del flujo de trabajo](/flow/configure-workflow-steps)
- [Usar diálogos de CDS para aplicaciones para procesos guiados](/flow/use-cds-for-apps-dialogs)
- [Crear una acción personalizada](/flow/create-actions)



## <a name="technology-used"></a>Tecnología utilizada

Puesto que los procesos usan la base de Windows Workflow puede registrar un ensamblado construido mediante la [Biblioteca de actividades de .NET Framework](/dotnet/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library) que define las actividades personalizadas que aparecerán en el editor de la aplicación web y serán invocadas cuando el proceso se ejecute.

Las actividades de flujo de trabajo personalizadas requieren la creación de un ensamblado .NET Framework que incluya una o más clases que se deriven de la [Clase CodeActivity](/dotnet/api/system.activities.codeactivity?view=netframework-4.5.2) de resumen. Esta clase proporciona el [Método Execute(CodeActivityContext)](/dotnet/api/system.activities.codeactivity.execute?view=netframework-4.5.2) llamado por la plataforma CDS para aplicaciones cuando se ejecuta la actividad. Cada clase en el ensamblado definirá una actividad específica.

Las actividades de flujo de trabajo también pueden definir parámetros de entrada y salida que están visibles en el diseñador de procesos y permiten que alguien pase datos a la actividad de flujo de trabajo y reciba salida procesada. Cuando escribe la clase agregará las propiedades para estos parámetros y las anotará con [atributos .NET](/dotnet/standard/attributes/index) para proporcionar los metadatos que CDS para aplicaciones usará para exponer su actividad de flujo de trabajo personalizada con cualquier parámetro en el diseñador.

## <a name="visual-studio-requirements"></a>Requisitos de Visual Studio

Para crear actividades de flujo de trabajo personalizadas, debe instalar Visual Studio con la carga de trabajo de **Desarrollo de escritorio de .NET** y el componente individual **Windows Workflow Foundation**.

Puede usar la edición gratuita Visual Studio 2017 Community o las ediciones Professional y Enterprise.

Para comprobar la instalación o agregar este componente:

1. Abra Visual Studio 2017
1. Seleccione **Herramientas** > **Obtener herramientas y características…** . Se abrirá el instalador de Visual Studio
1. En la pestaña **Cargas de trabajo**, asegúrese de que la carga de trabajo **Desarrollo de escritorio .NET** está seleccionada.
    ![Cargas de trabajo de Visual Studio necesarias](media/visual-studio-workloads-workflow-extensions.png)
1. Seleccione **Componentes individuales** y baje hasta la sección **Actividades de desarrollo**.
    ![Componentes individuales de Visual Studio requeridos](media/visual-studio-individual-components-workflow-extensions.png)
1. Si **Windows Workflow Foundation** no está seleccionado, selecciónelo. El componente **Windows Communication Foundation** se incluirá también.
1. Si ha agregado nuevas cargas de trabajo o componentes, haga clic en **Modificar** para permitir que el programa de instalación de Visual Studio lo instale. De lo contrario, cierre del instalador de Visual Studio.

Más información: [Instalación de Visual Studio 2017](/visualstudio/install/install-visual-studio)

## <a name="create-a-custom-workflow-activity-assembly"></a>Crear un ensamblado de actividad de flujo de trabajo personalizado

Estos son pasos generales usados para crear una actividad de flujo de trabajo personalizada mediante Visual Studio. Para ver un ejemplo paso a paso completo consulte [Tutorial: Crear extensión de flujo de trabajo ](tutorial-create-workflow-extension.md).

1. Crear un proyecto de biblioteca de actividades de flujo de trabajo mediante .NET Framework 4.5.2 como marco de trabajo de destino
1. Eliminar el archivo Activity1.xaml generado con el proyecto
1. Instalar el paquete [Microsoft.CrmSdk.Workflow](https://www.nuget.org/packages/Microsoft.CrmSdk.Workflow/) NuGet.

    Este paquete incluye el paquete [Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/).

1. (Opcional) Si desea usar clases de entidad en tiempo de compilación, inclúyalas en el proyecto.

    Más información: 

    - [Programación en tiempo de ejecución y en tiempo de compilación con el servicio de la organización](../org-service/early-bound-programming.md)
    - [Generar clases en tiempo de compilación para el servicio de la organización](../org-service/generate-early-bound-classes.md) 

1. Agregar una clase pública. El nombre de la clase debe corresponder con la acción llevará a cabo la actividad.
1. Agregue lo siguiente mediante directivas

    ```csharp
    using System.Activities;
    using Microsoft.Xrm.Sdk;
    using Microsoft.Xrm.Sdk.Workflow;
    ```

1. Agregue las propiedades a la clase para representar cualquier parámetro de entrada o de salida y use [atributos .NET](/dotnet/standard/attributes/index) para proporcionar metadatos necesarios para exponer estas propiedades al diseñador de procesos de flujo de trabajo.

    Más información: [Agregar parámetros](#add-parameters)

1. Haga que su clase se derive de la [Clase CodeActivity](/dotnet/api/system.activities.codeactivity?view=netframework-4.5.2) e implemente el [Método Execute(CodeActivityContext)](/dotnet/api/system.activities.codeactivity.execute?view=netframework-4.5.2) que contiene las operaciones que realizará la actividad.

    Más información: [Agregar código al método Execute](#add-your-code-to-the-execute-method)

1. Firmar el ensamblado
1. Crear el ensamblado.
1. Registre el ensamblado mediante la herramienta de registro de complementos y establezca las propiedades Name y WorkflowActivityGroupName para definir el texto que será visible en el diseñador de procesos de Dyn365CE.

    Más información: [Registrar el ensamblado](#register-your-assembly)

1. Pruebe la actividad de flujo de trabajo invocándola desde un flujo de trabajo, un diálogo o procesos de acción
1. (Recomendado) Agregue la actividad de flujo de trabajo a una solución.

## <a name="add-parameters"></a>Agregar parámetros

Al definir los parámetros para la clase debe definirlos como tipos [InArgument<T>](/dotnet/api/system.activities.inargument-1), [OutArgument<T>](/dotnet/api/system.activities.outargument-1), o [InOutArgument<T>](/dotnet/api/system.activities.inoutargument-1). Estos tipos proporcionan métodos heredados de una [Clase de argumento](/dotnet/api/system.activities.argument) común para Obtener o Establecer los parámetros. El código usará estos métodos en el método Execute . Más información: [Agregar código al método Execute](#add-your-code-to-the-execute-method)

Si su actividad de flujo de trabajo personalizada utiliza parámetros de entrada o salida debe agregar los atributos .NET adecuados a las propiedades de clase pública que las definen. Estos datos los leerá el diseñador de procesos para definir cómo los parámetros se pueden configurar en el diseñador de procesos.

Puede usar los siguientes tipos de propiedades como parámetros de entrada o salida:

||||
|--|--|--|
|[bool](/dotnet/api/system.boolean)|[Fecha y hora](/dotnet/api/system.datetime)|[Decimal](/dotnet/api/system.decimal)|
|[Doble](/dotnet/api/system.double)|<xref:Microsoft.Xrm.Sdk.EntityReference>|[int](/dotnet/api/system.int32)|
|<xref:Microsoft.Xrm.Sdk.Money>|<xref:Microsoft.Xrm.Sdk.OptionSetValue>|[cadena](/dotnet/api/system.string)|

### <a name="input-and-output-parameters"></a>Parámetros de entrada y salida

Para definir el texto que desea mostrar para un parámetro de entrada o de salida en el diseñador de procesos, usará el siguiente patrón mediante[Atributos .NET](/dotnet/standard/attributes/index).

```csharp
[Input("Integer input")]
public InArgument<int> IntInput { get; set; }
```

o

```csharp
[Output("Integer output")]
public OutArgument<int> IntOutput { get; set; }
```

Una única propiedad en la clase puede ser un parámetro de entrada y de salida incluyendo ambos atributos:

```csharp
[Input("Int input")]  
[Output("Int output")]  
public InOutArgument<int> IntParameter { get; set; }
```


### <a name="required-values"></a>Valores requeridos

Si desea hacer que un parámetro de entrada sea necesario al usar la actividad de flujo de trabajo en un proceso debe usar el atributo `[RequiredArgument]`.

### <a name="default-values"></a>Valores predeterminados

Cuando no se define un valor pasado como parámetro de entrada o establecido como parámetro de salida, puede especificar un valor predeterminado. Por ejemplo, para establecer el valor predeterminado de una propiedad bool:

```csharp
[Input("Bool input")]
[Default("True")]
public InArgument<bool> Bool { get; set; }
```

El formato del valor predeterminado depende del tipo de propiedad. Algunos ejemplos aparecen en la tabla siguiente:

|Escriba|Ejemplo|
|--|--|
|[bool](/dotnet/api/system.boolean)|[Default("True")]|
|[Fecha y hora](/dotnet/api/system.datetime)|[Default("2004-07-09T02:54:00Z")]|
|[Decimal](/dotnet/api/system.decimal)|[Default("23.45")]|
|[Doble](/dotnet/api/system.double)|[Default("23.45")]|
|<xref:Microsoft.Xrm.Sdk.Money>|[Default("23.45")]|
|<xref:Microsoft.Xrm.Sdk.EntityReference>|[Default("3B036E3E-94F9-DE11-B508-00155DBA2902", "account")]|
|[int](/dotnet/api/system.int32)|[Default("23")]|
|<xref:Microsoft.Xrm.Sdk.OptionSetValue>|[Default("3")]|
|[cadena](/dotnet/api/system.string)|[Default("string default")]|

### <a name="entityreference-parameters"></a>Parámetros de EntityReference

Al definir una propiedad para un parámetro <xref:Microsoft.Xrm.Sdk.EntityReference> debe usar el atributo `ReferenceTarget`. Este establece qué tipo de atributo se permite. Por ejemplo:

```csharp
[Input("EntityReference input")]
[Output("EntityReference output")]
[ReferenceTarget("account")]
public InOutArgument<EntityReference> AccountReference { get; set; }
```

### <a name="optionsetvalue-parameters"></a>Parámetros OptionSetValue

Al definir una propiedad para un parámetro <xref:Microsoft.Xrm.Sdk.OptionSetValue> debe usar el atributo `AttributeTarget`. Este atributo define qué entidad y atributo contiene el conjunto de valores válido para el parámetro. Por ejemplo:

```csharp
[Input("Account IndustryCode value")]
[AttributeTarget("account", "industrycode")]
[Default("3")]
public InArgument<OptionSetValue> IndustryCode { get; set; }
```

## <a name="add-your-code-to-the-execute-method"></a>Agregue su código al método Execute

La lógica que incluye en el método [Método CodeActivity.Execute(CodeActivityContext)](/dotnet/api/system.activities.codeactivity.execute?view=netframework-4.5.2) define lo que hace la actividad de flujo de trabajo.

> [!IMPORTANT]
> El código en el método `Execute` debe escribirse como sin estado. No se recomienda usar variables globales o de miembro para pasar datos de una invocación a otra.
> Para mejorar el rendimiento, CDS para aplicaciones almacena en caché las instancias de actividad personalizada de flujo de trabajo. Por este motivo, no se llama al constructor para cada invocación de la actividad personalizada de flujo de trabajo. Además, varios subprocesos del sistema podrían ejecutar la actividad personalizada de flujo de trabajo al mismo tiempo. Solo debe usar la información que se pasa mediante el parámetro [CodeActivityContext](/dotnet/api/system.activities.codeactivitycontext) al método `Execute`.

### <a name="reference-parameters"></a>Parámetros de referencia

Para hacer referencia a los parámetros definidos para su clase usará los métodos [Argument.Get](/dotnet/api/system.activities.argument.get?view=netframework-4.5.2) o [Argument.Set(ActivityContext, Object)](/dotnet/api/system.activities.argument.set?view=netframework-4.5.2) que proporcionan que requieren que la instancia [CodeActivityContext](/dotnet/api/system.activities.codeactivitycontext) se pase al método `Execute`. El siguiente ejemplo muestra el acceso al valor de un parámetro de entrada y el establecimiento del valor de un parámetro de salida.

```csharp
using Microsoft.Xrm.Sdk.Workflow;
using System.Activities;

namespace SampleWorkflowActivity
{
  public class IncrementByTen : CodeActivity
  {
    [RequiredArgument]
    [Input("Decimal input")]
    public InArgument<decimal> DecInput { get; set; }

    [Output("Decimal output")]
    public OutArgument<decimal> DecOutput { get; set; }

    protected override void Execute(CodeActivityContext context)
    {
      decimal input = DecInput.Get(context);
      DecOutput.Set(context, input + 10);
    }
  }
}
```

### <a name="get-contextual-information"></a>Obtener información contextual

Cuando el código requiere información contextual puede tener acceso a esta mediante el [método CodeActivityContext.GetExtension<T>](/dotnet/api/system.activities.activitycontext.getextension) con la interfaz <xref:Microsoft.Xrm.Sdk.Workflow.IWorkflowContext>. Este objeto se obtiene de la interfaz <xref:Microsoft.Xrm.Sdk.IExecutionContext> que proporciona acceso a muchas propiedades de sólo lectura que describen el contexto de la operación. El `IWorkflowContext` proporciona información contextual similar específica del flujo de trabajo que se ejecuta que usa el ensamblado de flujo de trabajo.

Use el siguiente código en la función `Execute` para acceder a `IWorkflowContext`:

```csharp
protected override void Execute(CodeActivityContext context)
{
 IWorkflowContext workflowContext = context.GetExtension<IWorkflowContext>();

...
```

### <a name="use-the-organization-service"></a>Usar el servicio de la organización

Cuando necesite realizar operaciones de datos con el servicio de la organización puede tener acceso a este mediante el método [CodeActivityContext.GetExtension<T>](/dotnet/api/system.activities.activitycontext.getextension) con la interfaz <xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory>. Desde ahí puede usar el método <xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory.CreateOrganizationService(System.Nullable{System.Guid})> para acceder a una sesión del proxy de servicio que puede usar para realizar operaciones de datos. La propiedad <xref:Microsoft.Xrm.Sdk.Workflow.IWorkflowContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.InitiatingUserId> se puede usar para determinar el contexto del usuario a usar si desea que la operación se realice en el mismo contexto que el proceso que llama.
Use el siguiente código en la función `Execute` para acceder al servicio de la organización:

```csharp
protected override void Execute(CodeActivityContext context)
{
 IWorkflowContext workflowContext = context.GetExtension<IWorkflowContext>();
 IOrganizationServiceFactory serviceFactory = context.GetExtension<IOrganizationServiceFactory>();

 // Use the context service to create an instance of IOrganizationService.             
 IOrganizationService service = serviceFactory.CreateOrganizationService(workflowContext.InitiatingUserId);

...
```

## <a name="register-your-assembly"></a>Registrar el ensamblado

Usará la herramienta de registro de complementos (PRT) para registrar ensamblados que contienen actividades personalizadas de flujo de trabajo. Ésta es la misma herramienta que sirve para registrar complementos. Para complementos y actividades de flujo de trabajo personalizadas, debe registrar el ensamblado que la cargará al entorno. Sin embargo, no registre los pasos para actividades de flujo de trabajo personalizadas.

Para los actividades de flujos de trabajo personalizadas debe especificar las propiedades siguientes para controlar qué se muestra en el diseñador de procesos de flujo de trabajo.

|Campo|Descripción|
|--|--|
|Descripción|No es visible en la interfaz de usuario del diseñador de procesos, pero puede resultar útil al generar documentación de los datos extraídos de la entidad PluginType que almacena esta información.|
|FriendlyName|Nombre descriptivo para el complemento.|
|Nombre|El nombre del menú representado|
|WorkflowActivityGroupName|El nombre del submenú agregado al menú principal del diseñador del proceso de CDS para aplicaciones.|

![Establecer propiedades descriptivas](media/create-workflow-activity-set-properties.png)

> [!NOTE]
> Estos valores no serán visibles en la solución no administrada al probar la actividad de flujo de trabajo. No obstante, cuando se exporta una solución administrada que incluye esta actividad de flujo de trabajo estos valores serán visibles en el diseñador de procesos.

## <a name="debug-workflow-activities"></a>Depurar actividades de flujo de trabajo personalizadas

Con las actividades de flujo de trabajo personalizadas implementadas en CDS para aplicaciones puede capturar perfiles para reproducir para depuración local y usar el servicio de seguimiento para escribir la información en una entidad. 

El siguiente ejemplo muestra el uso del servicio de seguimiento para escribir el mensaje siguiente: `Add your message.`

```csharp
protected override void Execute(CodeActivityContext context)
{
//Create the tracing service
ITracingService tracingService = executionContext.GetExtension<ITracingService>();

//Use the tracing service
tracingService.Trace("{0} {1} {2}.","Add","your","message");

...
```

Más información:
 - [Depurar actividades de flujo de trabajo personalizadas](debug-workflow-activites.md)
 - [Usar seguimiento](../debug-plug-in.md#use-tracing)
 - [Ver registros de seguimiento](../tutorial-write-plug-in.md#view-trace-logs)

## <a name="add-to-solution"></a>Agregar a solución

Cuando registra ensamblados usando la herramienta de registro de complementos, se agregarán a la **Solución predeterminada**, que no debe confundirse con la **Solución predeterminada de Common Data Service**. Dado que la **Solución predeterminada** contiene todas las personalizaciones no administradas aplicadas al entorno, para poder distribuir la actividad de flujo de trabajo personalizada mediante una solución debe agregarla a una solución no administrada. Por ejemplo, puede agregarla a la **Solución predeterminada de Common Data Service** o a cualquier solución no administrada que haya creado.

## <a name="manage-changes-to-custom-workflow-activities"></a>Administrar cambios en actividades de flujo de trabajo personalizadas

Deberá mantener el código de las actividades de flujo de trabajo personalizadas. Puesto que los cambios de código pueden incluir cambios importantes, deberá administrar este cambio. Usará diferentes pasos para actualizar o cambiar la versión de los ensamblados de flujo de trabajo personalizados.

Cuando registra un ensamblado que contiene actividades de flujo de trabajo personalizadas se incluye la versión del ensamblado. Esta información se extrae mediante la reflexión del ensamblado. Puede controlar el número de versión mediante el archivo `AssemblyInfo.cs` en el proyecto de Visual Studio.

Encontrará una sección en la parte inferior similar a esta:


```
// Version information for an assembly consists of the following four values:
//
//      Major Version
//      Minor Version 
//      Build Number
//      Revision
//
// You can specify all the values or you can default the Build and Revision Numbers 
// by using the '*' as shown below:
//[assembly: AssemblyVersion("1.0.0.*")]
[assembly: AssemblyVersion("1.0.0.0")]
[assembly: AssemblyFileVersion("1.0.0.0")]
```

Esta información de versión es importante porque permite aplicar actualizaciones a ensamblados implementados o cambiar la versión de ensamblados cuando desea incluir nuevas capacidades.

### <a name="update-a-custom-workflow-activity-assembly"></a>Actualizar un ensamblado de actividad de flujo de trabajo personalizado

Al realizar cambios para depurar errores o corregir código que no realizan cambios importantes en clases públicas o firmas de métodos, puede actualizar el ensamblado para que todos los procesos en ejecución se inicien automáticamente usando la nueva versión del ensamblado.

#### <a name="to-update-an-assembly"></a>Para actualizar un ensamblado:

1. Cambie únicamente el **Número de compilación** y **Valores de revisión** en el atributo `AssemblyInfo.cs` `AssemblyVersion`. Por ejemplo, cambie de `1.0.0.0` a `1.0.10.5`.
1. Use la herramienta de registro de complementos para actualizar el ensamblado. Más información: [Actualizar un ensamblado](../register-plug-in.md#update-an-assembly)

#### <a name="upgrade-a-custom-workflow-activity-assembly"></a>Cambiar de versión un ensamblado de actividad de flujo de trabajo personalizado:

Si realiza cambios que incluyen cambios importantes en clases públicas o firmas de método, como cambiar los parámetros, interrumpiría los procesos actualmente en ejecución definidos para usar las firmas originales. En este caso debe cambiar la versión del ensamblado. Esto creará una nueva actividad de flujo de trabajo personalizado que expone opciones para definir qué versión se aplicará en el diseñador del proceso. Esto permite que cada proceso que utilice esta actividad se reconfigure para adaptarse a los cambios incluidos en el nuevo ensamblado. Tras actualizar todos los procesos que usan el ensamblado original para usar el ensamblado actualizado, puede anular el registro del ensamblado más antiguo.

#### <a name="to-upgrade-an-assembly"></a>Para cambiar la versión de un ensamblado:

1. Asegúrese de que el nuevo ensamblado tiene los mismos `Name`, `PublicKeyToken`, y `Culture` que el ensamblado existente.
1. Cambie los valores de **Versión principal** y/o **Versión secundaria** en el atributo `AssemblyInfo.cs` `AssemblyVersion`. Por ejemplo, cambie de `1.0.0.0` a `2.0.0.0`.
1. Use la herramienta de registro de complementos para registrar el ensamblado como nuevo. Más información: [Registrar un ensamblado](../register-plug-in.md#register-an-assembly)
1. Para cada proceso que se la actividad de flujo de trabajo personalizada, deberá desactivar el proceso y editar los pasos que usan la actividad de flujo de trabajo personalizada.

    Encontrará un selector **Versión** en el diseñador de procesos que puede usar para elegir la versión del ensamblado que se debe usar.

    ![versión establecida del flujo de trabajo](media/workflow-set-version.png)

Cuando todos los procesos se convierten para usar el nuevo ensamblado, puede usar la herramienta de registro de complementos para anular el registro del ensamblado, por lo que dejará de estar disponible. Más información: [Anular registro de componentes](../register-plug-in.md#unregister-components)


### <a name="see-also"></a>Vea también

[Tutorial: Crear extensión de flujo de trabajo](tutorial-create-workflow-extension.md)<br />
[Ejemplo: crear una actividad de flujo de trabajo personalizada](sample-create-custom-workflow-activity.md)<br />
[Ejemplo: actualizar el siguiente cumpleaños con una actividad de flujo de trabajo personalizada](sample-update-next-birthday-using-custom-workflow-activity.md)<br />
[Ejemplo: Calcular una puntuación de crédito con una actividad de flujo de trabajo personalizada](sample-calculate-credit-score-custom-workflow-activity.md)