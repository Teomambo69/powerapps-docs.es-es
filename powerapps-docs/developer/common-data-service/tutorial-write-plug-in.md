---
title: 'Tutorial: Escribir y registrar un complemento (Common Data Service) | Microsoft Docs'
description: Este tutorial es el primero de una serie que le muestra cómo trabajar con los complementos.
ms.custom: ''
ms.date: 02/23/2019
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
# <a name="tutorial-write-and-register-a-plug-in"></a>Tutorial: Escribir y registrar un complemento

Este tutorial es el primero de una serie que le muestra cómo trabajar con los complementos. Este tutorial es un requisito previo para los tutoriales siguientes:

- [Tutorial: Depurar un complemento](tutorial-debug-plug-in.md)
- [Tutorial: Actualizar un complemento](tutorial-update-plug-in.md)

Para una explicación detallada de los conceptos relacionados y la información técnica, consulte:

- [Use complementos para ampliar los procesos de negocio](plug-ins.md)
- [Escribir un complemento](write-plug-in.md)
- [Registrar un complemento](register-plug-in.md)
- [Depuración de complementos](debug-plug-in.md)

## <a name="goal"></a>Objetivo

Crear un complemento asincrónico registrado en el mensaje Crear de la entidad de cuenta. El complemento creará una actividad de tarea que recordará al creador la cuenta que realice seguimiento una semana más tarde.

> [!NOTE]
> Este objetivo se puede conseguir fácilmente utilizando un flujo de trabajo sin escribir código. Estamos usando este ejemplo simple para poder centrarnos en el proceso de creación y de implementar un complemento.

## <a name="prerequisites"></a>Requisitos previos

- Acceso de nivel de administrador a un entorno Common Data Service
- Una aplicación basada en modelos que incluye las entidades de cuenta y tarea.
    - Si no dispone de una aplicación basada en modelos que incluya estas, vea [Crear la primera aplicación basada en modelos desde cero](../../maker/model-driven-apps/build-first-model-driven-app.md) para conocer los pasos para crear una en unos minutos.
- Visual Studio 2017
- Conocimientos del lenguaje de programación Visual C#
- Descargue la herramienta de registro de complementos.
    - Información sobre la descarga de la herramientas de registro de complementos en: [Descargar herramientas de NuGet](download-tools-nuget.md). Este tema incluye instrucciones para usar un script de PowerShell para descargar las últimas herramientas de NuGet.

<a name="BKMK_create"></a>

## <a name="create-a-plug-in-project"></a>Crear un proyecto de complemento

Debe usar Visual Studio para escribir un complemento. Use estos pasos para escribir un complemento básico. Como alternativa, puede encontrar los archivos de la solución del complemento aquí: [Ejemplo: Crear un complemento básico](org-service/samples/basic-followup-plugin.md).

### <a name="create-a-visual-studio-project-for-the-plug-in"></a>Crear un proyecto en Visual Studio para el complemento

1. Abra Visual Studio 2017 y abra un nuevo proyecto **Biblioteca de clase (.NET Framework)** mediante **.NET Framework 4.6.2**

    ![abra un nuevo proyecto de biblioteca de clases (.NET Framework) mediante .NET Framework 4.6.2](media/tutorial-write-plug-in-create-visual-studio-project.png)

    El nombre usado para el proyecto será el nombre del complemento. Este tutorial usa el nombre `BasicPlugin`.
1. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto y seleccione **Administrar paquetes de NuGet...** en el menú contextual.

    ![Administrar paquetes de NuGet](media/tutorial-write-plug-in-manage-nuget-packages.png)

1. Seleccione **Buscar** y busque `Microsoft.CrmSdk.CoreAssemblies` e instale la versión más reciente.

    ![Instalar el paquete Microsoft.CrmSdk.CoreAssemblies NuGet](media/tutorial-write-plug-in-install-microsoft.crmsdk.coreassemblies.png)

1. Debe seleccionar **Acepto** en el diálogo **Aceptación de licencia**.
1. En **Explorador de soluciones**, haga clic con el botón secundario en el archivo `Class1.cs` y seleccione **Cambiar nombre** en el menú contextual.

    ![Cambiar nombre de la clase](media/tutorial-write-plug-in-rename-class.png)

1. Cambiar el nombre del archivo `Class1.cs` a `FollowupPlugin.cs`.
1. Cuando se solicite, permita que Visual Studio cambie el nombre de la clase para que coincida con el nombre de archivo.

    ![Diálogo Confirmar cambio de nombre](media/tutorial-write-plug-in-rename-class-confirm.png)

### <a name="edit-the-class-file-to-enable-a-plug-in"></a>Edite el archivo de clase para habilitar un complemento

1. Agregue las instrucciones `using` siguientes a la parte superior del archivo `FollowupPlugin.cs`:

    ```csharp
    using System.ServiceModel;  
    using Microsoft.Xrm.Sdk;
    ```

1. Implementar la interfaz <xref:Microsoft.Xrm.Sdk.IPlugin> editando la clase.

    > [!NOTE]
    > Si sólo escribe `: IPlugin` después del nombre de clase, Visual Studio sugerirá automáticamente la implementación de un stub para el método **Execute**.

    ```csharp
    public class FollowupPlugin : IPlugin
    {
        public void Execute(IServiceProvider serviceProvider)
        {
            throw new NotImplementedException();
        }
    }
    ```


1. Reemplace el contenido del método `Execute` con el siguiente código:


```csharp
// Obtain the tracing service
ITracingService tracingService =
(ITracingService)serviceProvider.GetService(typeof(ITracingService));

// Obtain the execution context from the service provider.  
IPluginExecutionContext context = (IPluginExecutionContext)
    serviceProvider.GetService(typeof(IPluginExecutionContext));

// The InputParameters collection contains all the data passed in the message request.  
if (context.InputParameters.Contains("Target") &&
    context.InputParameters["Target"] is Entity)
{
    // Obtain the target entity from the input parameters.  
    Entity entity = (Entity)context.InputParameters["Target"];

    // Obtain the organization service reference which you will need for  
    // web service calls.  
    IOrganizationServiceFactory serviceFactory =
        (IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
    IOrganizationService service = serviceFactory.CreateOrganizationService(context.UserId);

    try
    {
        // Plug-in business logic goes here.  
    }

    catch (FaultException<OrganizationServiceFault> ex)
    {
        throw new InvalidPluginExecutionException("An error occurred in FollowUpPlugin.", ex);
    }

    catch (Exception ex)
    {
        tracingService.Trace("FollowUpPlugin: {0}", ex.ToString());
        throw;
    }
}
```

### <a name="about-the-code"></a>Acerca del código

- El <xref:Microsoft.Xrm.Sdk.ITracingService> permite escribir en el registro de seguimiento.  Puede ver un ejemplo en la bloque de captura final. Más información: [Usar seguimiento](debug-plug-in.md#use-tracing)
- El <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext> proporciona el acceso al contexto del evento que ejecutó el complemento.  Más información: [Entender el contexto de ejecución](understand-the-data-context.md).
- El código comprueba que el contexto <xref:Microsoft.Xrm.Sdk.IExecutionContext.InputParameters> incluya los parámetros esperados para la <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> para la que se registrará este complemento. Si la propiedad <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest.Target> está presente, la <xref:Microsoft.Xrm.Sdk.Entity> que se pasó a la solicitud estará disponible.
- La interfaz <xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory> proporciona acceso a una variable de servicio que implementa la interfaz <xref:Microsoft.Xrm.Sdk.IOrganizationService> que proporciona los métodos que usted usará para interactuar con el servicio para crear la tarea.


## <a name="add-business-logic"></a>Adición de lógica de negocios

El complemento creará una actividad de tarea que recordará al creador la cuenta que realice seguimiento una semana más tarde.

Agregue el siguiente código al bloque de prueba. Reemplace el comentario: `// Plug-in business logic goes here`. con lo siguiente:


```csharp
// Create a task activity to follow up with the account customer in 7 days. 
Entity followup = new Entity("task");

followup["subject"] = "Send e-mail to the new customer.";
followup["description"] =
    "Follow up with the customer. Check if there are any new issues that need resolution.";
followup["scheduledstart"] = DateTime.Now.AddDays(7);
followup["scheduledend"] = DateTime.Now.AddDays(7);
followup["category"] = context.PrimaryEntityName;

// Refer to the account in the task activity.
if (context.OutputParameters.Contains("id"))
{
    Guid regardingobjectid = new Guid(context.OutputParameters["id"].ToString());
    string regardingobjectidType = "account";

    followup["regardingobjectid"] =
    new EntityReference(regardingobjectidType, regardingobjectid);
}

// Create the task in Microsoft Dynamics CRM.
tracingService.Trace("FollowupPlugin: Creating the task activity.");
service.Create(followup);
```

### <a name="about-the-code"></a>Acerca del código

- Este código usa el estilo de enlace en tiempo de ejecución para crear una tarea y para asociarla a la cuenta que se está creando. Más información: [Crear entidades usando el servicio de la organización](org-service/entity-operations-create.md)
- Pueden utilizarse clases de enlaces en tiempo de compilación, pero esto requiere generar las clases para las entidades e incluir el archivo que define esas clases con el proyecto de ensamblados. Se trata sobre todo de una preferencia personal, por lo que estos pasos se ha dejado fuera de este tutorial por brevedad. Más información: [Programación en tiempo de ejecución y en tiempo de compilación con el servicio de la organización](org-service/early-bound-programming.md)
- La <xref:Microsoft.Xrm.Sdk.Entity.Id> de la cuenta que se está creando se encuentra en el contexto <xref:Microsoft.Xrm.Sdk.IExecutionContext.OutputParameters> y está establecida como atributo de búsqueda `regardingobjectid` para la tarea.

## <a name="build-plug-in"></a>Crear el complemento

En Visual Studio, presione **F6** para crear el ensamblado. Compruebe que se compila sin errores.

## <a name="sign-plug-in"></a>Firmar el complemento

1. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto **BasicPlugin** y seleccione **Propiedades** en el menú contextual.

    ![Abrir propiedades del proyecto](media/tutorial-write-plug-in-project-properties.png)

1. En las propiedades del proyecto, seleccione la pestaña **Firma** y seleccione la casilla **Firmar el ensamblado**.

    ![Firmar el ensamblado](media/tutorial-write-plug-in-sign-assembly.png)

1. En la lista desplegable **Elija un archivo de clave de alta seguridad**:, seleccione **<Nuevo…>**. 
1. En el diálogo **Crear clave de alta seguridad**, introduzca un **nombre de archivo de clave** y desactive la casilla **Proteger mi archivo de clave con contraseña**.
1. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Crear una clave de alta seguridad**.
1. En la pestaña **Generar** de las propiedades del proyecto, compruebe que la opción **Configuración** esté establecida como **Depurar**.
1. Pulse **F6** para crear el complemento de nuevo.
1. Usando el Explorador de Windows, busque el complemento creado en:`\bin\Debug\BasicPlugin.dll`.

> [!NOTE]
> Cree el ensamblado usando la configuración de **Depuración** porque usará el generador de perfiles de complementos para depurarlo en un tutorial posterior.   Antes de incluir un complemento con la solución, debe generarlo mediante la configuración de versión.

<a name="BKMK_register"></a>

## <a name="register-plug-in"></a>Registrar complemento

Para registrar un complemento necesitará la herramienta de registro de complementos

[!INCLUDE [cc-connect-plugin-registration-tool](includes/cc-connect-plugin-registration-tool.md)]

### <a name="register-your-assembly"></a>Registrar el ensamblado

1. En el desplegable **Registrar**, seleccione **Nueva ensamblado**.

    ![Registrar nuevo ensamblado](media/tutorial-write-plug-in-register-new-assembly.png)

1. En el diálogo **Registrar nuevo ensamblado**, seleccione el botón de puntos suspensivos (**…**) y busque el ensamblado que generó en el paso anterior.

    ![Cuadro de diálogo de registro de nuevo ensamblado](media/tutorial-write-plug-in-register-new-assembly-dialog.png)

1. Para los usuarios de Office 365, compruebe que el **modo aislado** sea **espacio aislado** y la **ubicación** para almacenar el ensamblado sea **Base de datos**.

    > [!NOTE]
    > Otras opciones para **modo aislado** y **ubicación** se aplican a implementaciones locales de Microsoft Dynamics 365. Para la ubicación, puede especificar la base de datos del servidor de D365, el almacenamiento local del servidor (disco) o los ensamblados de la caché de ensamblados global. Para obtener más información, vea [Almacenamiento de complementos](/dynamics365/customer-engagement/developer/register-deploy-plugins#plug-in-storage).

1. Haga clic en **Registrar complementos seleccionados**.
1. Verá un diálogo de confirmación **Complementos registrados**.

    ![Diálogo de confirmación de complementos registrados](media/tutorial-write-plug-in-register-new-assembly-dialog-confirm.png)

1. Haga clic en **Aceptar** para cerrar el cuadro diálogo y cerrar el diálogo **Registrar nuevo ensamblado**. 
1. Ahora aparecerá el ensamblado **(Assembly) BasicPlugin** que puede expandir para ver el complemento **(Plugin) BasicPlugin.FollowUpPlugin**.

    ![Complemento (Plugin) BasicPlugin.FollowUpPlugin.](media/tutorial-write-plug-in-basic-followupplugin-plugin.png)


### <a name="register-a-new-step"></a>Registrar un nuevo paso

1. Haga clic con el botón secundario en **(Plugin) BasicPlugin.FollowUpPlugin** y seleccione **Registrar nuevo paso**.

    ![Registrar un nuevo paso](media/tutorial-write-plug-in-register-new-step.png)

1. En el cuadro de diálogo **Registrar nuevo paso**, establezca los siguientes campos:

    |Configuración|Value|
    |--|--|
    |Mensaje|Crear|
    |Entidad principal|account|
    |Fase de canalización de eventos de ejecución|PostOperation|
    |Modo de ejecución|Asincrónico|

    ![Registrar un nuevo paso](media/tutorial-write-plug-in-register-new-step-dialog.png)

1. Haga clic en **Registrar nuevo paso** para completar el registro y cerrar el diálogo **Registrar nuevo paso**.
1. Ahora puede ver el paso registrado.

    ![Vea el paso registrado](media/tutorial-write-plug-in-view-registered-step.png)

> [!NOTE]
> En este punto el ensamblado y los pasos son parte de la **solución predeterminada** del sistema. Este es un buen momento para agregarlos a la solución no administrada que se distribuirá. Estos pasos no se incluyen en este tutorial. Consulte [Agregar el ensamblado a una solución](register-plug-in.md#add-your-assembly-to-a-solution) y [Agregar paso a la solución](register-plug-in.md#add-step-to-solution) para obtener más información.

## <a name="test-plug-in"></a>Probar complemento

1. Abra una aplicación basada en modelos y cree una entidad Cuenta.
1. En un breve período de tiempo, abra la cuenta y podrá comprobar la creación de la tarea.

    ![Registro de entidad Cuenta con actividad de tarea relacionada creada por complemento](media/tutorial-write-plug-in-test-plugin-in-model-app.png)

### <a name="what-if-the-task-wasnt-created"></a>¿Qué ocurre si la tarea no se creó?

Dado que se trata de un complemento asincrónico, la operación de crear la tarea se produce una vez creada la cuenta. Normalmente, esto ocurrirá inmediatamente, pero si no es así, puede seguir viendo el trabajo del sistema en la cola en espera de aplicarse. Este registro del pasos usó la opción **Delete AsyncOperation if StatusCode = Successful** que es una práctica recomendada. Esto quiere decir que tan pronto como el trabajo del sistema finaliza correctamente, no podrá ver los datos del trabajo del sistema a menos que vuelva a registrar el complemento con la opción **Delete AsyncOperation if StatusCode = Successful**.

Sin embargo, si se produjo un error, puede ver el trabajo del sistema para ver el mensaje de error.

## <a name="view-system-jobs"></a>Ver trabajos del sistema

Use la aplicación **Dynamics 365 --personalizado** para ver trabajos del sistema.

1. En la aplicación basada en modelos, vaya a la 

    ![ver la aplicación personalizada de Dynamics 365](media/dynamics-365-custom-app.png)

1. En la aplicación **Dynamics 365 --personalizado**, vaya a **Configuración** > **Sistema** > .**Trabajos del sistema**.

    ![navegar a trabajos del sistema](media/navigate-system-jobs.png)

1. Cuando ve trabajos del sistema, puede filtrar por **Entidad**. Seleccione **Cuenta**.

    ![foo](media/system-jobs-filter-entity-account.png)

1. Si el trabajo tiene error, debe ver un registro con el nombre **BasicPlugin.FollowupPlugin: Creación de cuenta**

    ![Error de trabajo del sistema](media/failed-system-job.png)

1. Si abre el trabajo del sistema, puede expandir la sección **Detalles** para ver la información escrita en el seguimiento y detalles sobre el error.

    ![detalles del trabajo del sistema](media/system-job-failed-plug-in.png)

### <a name="query-system-jobs"></a>Consultar trabajos del sistema

Puede usar la consulta API web siguiente para devolver trabajos del sistema con error para complementos asincrónicos

```
GET <your org uri>/api/data/v9.0/asyncoperations?$filter=operationtype eq 1 and statuscode eq 31&$select=name,message
```
Para obtener más información, consulte [Consultar datos mediante la API web](webapi/query-data-web-api.md)


O usar el FetchXml siguiente:

```xml
<fetch top='50' >
  <entity name='asyncoperation' >
    <attribute name='message' />
    <attribute name='name' />
    <filter type='and' >
      <condition attribute='operationtype' operator='eq' value='1' />
      <condition attribute='statuscode' operator='eq' value='31' />
    </filter>
  </entity>
</fetch>
```
Más información: [Uso de FetchXML con FetchExpression](org-service/entity-operations-query-data.md)


## <a name="view-trace-logs"></a>Ver registros de seguimiento

El código de ejemplo escribió un mensaje en el registro de seguimiento. Los pasos a continuación describen cómo ver los registros.

De forma predeterminada, los registros de seguimiento de complementos no están habilitados. 

> [!TIP]
> Si prefiere cambiar este valor en código: Este valor está en el [Atributo PluginTraceLogSetting de la entidad de la organización](reference/entities/organization.md#BKMK_PluginTraceLogSetting).
> 
> Los valores válidos son:
> 
> |Value|Etiqueta|
> |--|--|
> |0|Desactivado|
> |1|Excepción|
> |2|Todo|

Use los siguientes pasos para habilitarlos en una aplicación basada en modelos.

1. Abra la aplicación personalizada de Dynamics 365.

    ![Abra la aplicación personalizada de Dynamics 365](media/tutorial-write-plug-in-open-dynamics365-custom-app.png)

1. Vaya a **Configuración** > **Sistema** > **Administración**.

    ![vaya a administración](media/tutorial-write-plug-in-navigate-administration.png)

1. En **Administración**, seleccione **Configuración del sistema**.
1. En el diálogo **Configuración del sistema**, en la pestaña de personalización, establezca **Habilitar registro para registro de seguimientos de complemento** como **Todos**.

    ![Pestaña Personalización de Configuración del sistema](media/tutorial-write-plug-in-system-settings-customization-tab.png)

    > [!NOTE]
    > Debe deshabilitar el registro después de que haya finalizado de probar el complemento, o al menos establecerlo como **Excepción** en lugar de **Todos**.

1. Haga clic en **Aceptar** para cerrar el diálogo **Configuración del sistema**.
1. Repita los pasos para probar el complemento creando una nueva cuenta.
1. En la **Aplicación predeterminada de Dynamics 365**, vaya a **Configuración** > **Personalización** > .**Registro de seguimiento del complemento**.
1. Deberá ver que se ha creado un nuevo registro de seguimiento de complementos.

    ![Registro de seguimiento de complementos](media/tutorial-write-plug-in-plug-in-trace-log.png)

1. Si abre el registro puede esperar que incluya la información que estableció en su seguimiento, pero no es así. Solo comprueba que el seguimiento se ha producido.
1. Para ver los detalles, es más fácil consultar estos datos mediante API web en el explorador usando la consulta siguiente con el <xref href="Microsoft.Dynamics.CRM.plugintracelog?text=plugintracelog EntityType" />, usando la propiedad `typename` para filtrar resultados en la propiedad `messageblock` basándose en el nombre de la clase de complemento:

    `GET <your org uri>/api/data/v9.0/plugintracelogs?$select=messageblock&$filter=typename eq 'BasicPlugin.FollowUpPlugin'`

1. Puede esperar ver lo siguiente devuelto con la consulta de la API web.

    ```json
    {
        "@odata.context": "<your org uri>/api/data/v9.0/$metadata#plugintracelogs(messageblock)",
        "value": [{
            "messageblock": "FollowupPlugin: Creating the task activity.",
            "plugintracelogid": "f0c221d1-7f84-4f89-acdb-bbf8f7ce9f6c"
        }]
    }
    ```

## <a name="next-steps"></a>Pasos siguientes

En este tutorial ha creado un complemento simple y lo ha registrado. Complete [Tutorial: Depurar un complemento](tutorial-debug-plug-in.md) para aprender a depurar este complemento.
