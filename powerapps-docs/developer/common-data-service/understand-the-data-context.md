---
title: Entender el contexto de ejecución (Common Data Service) | Microsoft Docs
description: Información sobre los datos que se pasan a los complementos cuando se ejecutan.
ms.custom: ''
ms.date: 1/23/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: phecke
ms.author: pehecke
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="understand-the-execution-context"></a>Entender el contexto de ejecución

La **Canalización de ejecución de eventos** pasa a los complementos registrados una cantidad grande de datos sobre la operación que se procesa en estos momentos y el entorno de ejecución del complemento. Puede obtener acceso a estos datos en el código del complemento si establece una variable que implemente la interfaz <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext>:

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

## <a name="parametercollections"></a>ParameterCollections

Todas las propiedades del contexto de ejecución son de solo lectura. Pero los `InputParameters`, `OutputParameters`, y `SharedVariables` son valores <xref:Microsoft.Xrm.Sdk.ParameterCollection>. Puede manipular los valores de los elementos de estas colecciones para cambiar el comportamiento de la operación, en función de la fase de la canalización de ejecuciones de eventos para la que está registrado el complemento.

Los valores <xref:Microsoft.Xrm.Sdk.ParameterCollection> se definen como estructuras <xref:System.Collections.Generic.KeyValuePair%602>. Para obtener acceso a una propiedad deberá conocer el nombre de la propiedad que revela el mensaje. Por ejemplo, para obtener acceso a la propiedad <xref:Microsoft.Xrm.Sdk.Entity> que se pasa como parte de <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>, es necesario saber que el nombre de esa propiedad es `Target`. A continuación puede obtener acceso a este valor utilizando código como éste:

```csharp
var entity = (Entity)context.InputParameters["Target"];
```
Use la documentación de <xref:Microsoft.Xrm.Sdk.Messages> y <xref:Microsoft.Crm.Sdk.Messages> para conocer los nombres de los mensajes definidos en los ensamblados del SDK. Para acciones personalizadas, consulte los nombres de los parámetros definidos en el sistema.

## <a name="inputparameters"></a>InputParameters

Los `InputParameters` representan el valor de la propiedad <xref:Microsoft.Xrm.Sdk.OrganizationRequest>.<xref:Microsoft.Xrm.Sdk.OrganizationRequest.Parameters> que representa la operación procedente de los servicios web.

Como se describe en [Usar mensajes con el servicio de la organización](org-service/use-messages.md), todas las operaciones que se producen en el sistema son en definitiva instancias de al case `OrganizationRequest` que está procesando el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> .

Como se describe en [Marco de trabajo de eventos](event-framework.md), las operaciones pasan a través de una serie de fases y puede registrar el complemento en fases que se producen antes de que los datos se escriban en la base de datos. En las fases **PreValidation** y **PreOperation**, puede leer y cambiar los valores de los `InputParameters` de modo que puede controlar el resultado esperado de la operación de datos.

Si encuentra que los valores de la colección de `InputParameters` representan una condición que no puede permitir, puede lanzar una <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> (preferentemente en la fase de **PreValidation**) que cancelará la operación y mostrará un error al usuario con un complemento sincrónico, o registrará el error si el complemento es asincrónico. Más información: [Cancelación de una operación](handle-exceptions.md#cancelling-an-operation)

## <a name="outputparameters"></a>OutputParameters

Los `OutputParameters` representan el valor de la propiedad <xref:Microsoft.Xrm.Sdk.OrganizationResponse>.<xref:Microsoft.Xrm.Sdk.OrganizationResponse.Results> que representa el valor devuelto de la operación. Los `OutputParameters` no se rellenan hasta después de la transacción de base de datos, de modo que solo están disponibles para complementos registrados en la fase **PostOperation**. Si desea cambiar los valores devueltos por la operación, puede modificarlos en los `OutputParameters`.

## <a name="shared-variables"></a>Variables compartidas

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
> [!IMPORTANT]
> Cualquier tipo de datos agregado a la colección de variables compartidas debe ser serializable; en caso contrario, el servidor no sabrá como serializar los datos y la ejecución de complementos no se realizará correctamente.  
  
 Para un complemento registrado en la fase 20 ó 40, para tener acceso a las variables compartidas de un complemento registrado en la fase 10 que se ejecuta al crear, actualizar, eliminar o por una clase <xref:Microsoft.Crm.Sdk.Messages.RetrieveExchangeRateRequest>, debe tener acceso a la colección <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext.ParentContext>.**SharedVariables**. Para el resto de los casos, <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext>.**SharedVariables** contiene la colección. 

## <a name="entity-images"></a>Imágenes de entidad

Al registrar una paso para un complemento que incluye una entidad como uno de los parámetros, tiene la opción de especificar que una copia de los datos de la entidad se incluya como *instantánea* o imagen mediante las propiedades <xref:Microsoft.Xrm.Sdk.IExecutionContext.PreEntityImages> y/o <xref:Microsoft.Xrm.Sdk.IExecutionContext.PostEntityImages>.

Estos datos proporcionan un punto de comparación para los datos de entidad mientras atraviesan la canalización de eventos. El uso de estas imágenes proporciona un rendimiento mucho mejor que incluir código en un complemento para recuperar una entidad solo para comparar los valores de atributo.

Al definir una imagen de la entidad, especifique un valor de alias de entidad que puede usar para tener acceso a la imagen específica. Por ejemplo, si define pre una imagen de preentidad con el alias '`a`', puede usar el siguiente código para acceder al valor del atributo `name`.

```csharp
var oldAccountName = (string)context.PreEntityImages["a"]["name"];
```

Más información: [Definir imágenes de entidad](register-plug-in.md#define-entity-images)

### <a name="see-also"></a>Vea también

[Marco de trabajo de eventos](event-framework.md)  
[Escribir un complemento](write-plug-in.md)