---
title: Programación en tiempo de ejecución y en tiempo de compilación con el servicio de la organización (Common Data Service) | Microsoft Docs
description: Describe los diferentes estilos de programación disponibles al usar los ensamblados SDK de .NET con el servicio de la organización.
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
# <a name="late-bound-and-early-bound-programming-using-the-organization-service"></a>Programación de enlace en tiempo de ejecución y de enlace en tiempo de compilación con el servicio de la organización

Cuando trabaje con los ensamblados del servicio de la organización tiene dos estilos que puede usar: *enlace en tiempo de ejecución* y *enlace en tiempo de compilación*.

La diferencia principal entre el enlace anticipado y el enlace en tiempo de ejecución implica la conversión de tipo. Mientras que el enlace anticipado ofrece la comprobación de todos los tipos en tiempo de compilación de modo que no se produzcan conversiones implícitas, el enlace en tiempo de ejecución comprueba los tipos solo cuando se crea el objeto o se realiza una acción en el tipo. La clase <xref:Microsoft.Xrm.Sdk.Entity> requiere que los tipos se especifiquen explícitamente para evitar conversiones implícitas.

El vínculo en tiempo de ejecución le permite trabajar con entidades o atributos personalizados que no estaban disponibles cuando se el código se compiló.

## <a name="late-bound"></a>Enlace en tiempo de ejecución

La programación de enlace en tiempo de ejecución usa la clase <xref:Microsoft.Xrm.Sdk.Entity> y necesita hacer referencia a las entidades y los atributos que utilizan sus valores de propiedad `LogicalName`: 
- <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.LogicalName> 
- <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.LogicalName>

Las relaciones no tienen una propiedad `LogicalName` ni la <xref:Microsoft.Xrm.Sdk.Metadata.RelationshipMetadataBase>. Se utiliza la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.RelationshipMetadataBase.SchemaName> .

La ventaja principal para la programación de enlace en tiempo de ejecución es que no necesita generar las clases ni incluir el archivo generado en los proyectos. El archivo generado puede ser muy grande. 

Las desventajas principales son:

- No se obtiene validación del enlace en tiempo de compilación de los nombres de las entidades, los atributos y las relaciones.
- Necesita conocer los nombres de los atributos y de relaciones en los metadatos. 

> [!TIP]
> Herramienta que puede usar para encontrar esta información fácilmente es el Explorador de metadatos. Se trata de una aplicación que puede descargar e instalar en su organización. Más información: [Examinar los metadatos para su entorno](../browse-your-metadata.md)

### <a name="example"></a>Ejemplo

El siguiente ejemplo crea una cuenta con el estilo de enlace en tiempo de ejecución.

```csharp
//Use Entity class with entity logical name
var account = new Entity("account");

// set attribute values
    // string primary name
    account["name"] = "Contoso";            
    // Boolean (Two option)
    account["creditonhold"] = false;
    // DateTime
    account["lastonholdtime"] = new DateTime(2017, 1, 1);
    // Double
    account["address1_latitude"] = 47.642311;
    account["address1_longitude"] = -122.136841;
    // Int
    account["numberofemployees"] = 500;
    // Money
    account["revenue"] = new Money(new decimal(5000000.00));
    // Picklist (Option set)
    account["accountcategorycode"] = new OptionSetValue(1); //Preferred customer
                
//Create the account
Guid accountid = svc.Create(account);
```

## <a name="early-bound"></a>Enlace en tiempo de compilación

La programación de enlace en tiempo de compilación requiere que primero genere un conjunto de clases basadas en metadatos para una organización específica mediante la herramienta de generación de código (CrmSvcUtil.exe). Más información: [Generar clases para programación de enlace en tiempo de compilación con el servicio de la organización](generate-early-bound-classes.md)

Cuando haya generado tipos de clases de entidad en tiempo de compilación con la herramienta de generación de código disfrutará de una mejor experiencia cuando escriba código gracias a las clases y las propiedades del atributo que usan sus respectivos valores `SchemaName`:

- <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.SchemaName> 
- <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName>
- <xref:Microsoft.Xrm.Sdk.Metadata.RelationshipMetadataBase>.<xref:Microsoft.Xrm.Sdk.Metadata.RelationshipMetadataBase.SchemaName>

Simplemente, cree instancias de la clase y deje que IntelliSense en Visual Studio proporcione los nombres de propiedades y las relaciones.

Las clases generadas para la programación de enlace en tiempo de compilación también pueden incluir las definiciones para cualquier acción personalizada que se definan para el entorno. Esto le brindará un par de clases de solicitud y respuesta para su uso con con estas acciones personalizadas. Más información: [Acciones personalizadas](../custom-actions.md)

También hay una opción para ampliar la herramienta de generación de código para cambiar la salida. Una extensión crea enums para cada valor de opción de optionset. Esto proporciona una mejor experiencia porque no tiene que buscar el valor entero para cada opción. Más información: [Crear extensiones para la herramienta de generación de código](extend-code-generation-tool.md).

Sin embargo, debido a que las clases se generan mediante metadatos desde una instancia específica, y cada instancia puede tener distintas entidades y atributos, y estos pueden cambiar a lo largo del tiempo. Es posible que tenga que escribir código que funcione con entidades que no estén presentes cuando genera clases con establecimiento inflexible de tipos.

> [!IMPORTANT]
> Si usa <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> para proporcionar los métodos <xref:Microsoft.Xrm.Sdk.IOrganizationService> que se usará, debe invocar al método <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy.EnableProxyTypes> para habilitar tipos de enlace en tiempo de compilación.


### <a name="example"></a>Ejemplo

El siguiente ejemplo crea una cuenta con el estilo de enlace en tiempo de compilación.

```csharp
var account = new Account();
// set attribute values
    // string primary name
    account.Name = "Contoso";
    // Boolean (Two option)
    account.CreditOnHold = false;
    // DateTime
    account.LastOnHoldTime = new DateTime(2017, 1, 1);
    // Double
    account.Address1_Latitude = 47.642311;
    account.Address1_Longitude = -122.136841;
    // Int
    account.NumberOfEmployees = 500;
    // Money
    account.Revenue = new Money(new decimal(5000000.00));
    // Picklist (Option set)
    account.AccountCategoryCode = new OptionSetValue(1); //Preferred customer

//Create the account
Guid accountid = svc.Create(account);
```

## <a name="choose-which-style"></a>Elegir un estilo

El estilo que elija depende de usted. La siguiente tabla ofrece las ventajas y las desventajas de cada uno.

|Enlace en tiempo de compilación|Enlace en tiempo de ejecución|
|--|--|
|Puede comprobar los nombres de entidad, atributo y relación en tiempo de compilación|No puede compilar la comprobación de los nombres de entidad, atributo y relación|
|Debe generar clases de entidad|No necesita generar tipos de entidad|
|Mejor compatibilidad con IntelliSense|Menor compatibilidad con IntelliSense|
|Menos código y más legible| Más código y menos legible|
|Ligeramente menos rendimiento|Ligeramente más rendimiento|


## <a name="mix-early-and-late-bound"></a>Combinación de enlace en tiempo de ejecución y en tiempo de compilación

Porque todas las clases heredan desde la clase <xref:Microsoft.Xrm.Sdk.Entity> que se utiliza con programación de enlace en tiempo de ejecución, puede trabajar con las entidades, los atributos y las relaciones no definidas en las clases.

### <a name="examples"></a>Ejemplos

El siguiente ejemplo muestra una forma de mezclar los de enlace en tiempo de ejecución y en tiempo de compilación utilizando <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.  
  
```csharp  
// Create an organization service context object  
AWCServiceContext context = new AWCServiceContext(_serviceProxy);  
  
// Instantiate an account object using the Entity class.  
Entity testaccount = new Entity("account");  
  
// Set several attributes. For account, only the name is required.   
testaccount["name"] = "Fourth Coffee";  
testaccount["emailaddress1"] = "marshd@contoso.com";  
  
// Save the entity using the organization service context object.  
context.AddToAccountSet(testaccount);  
context.SaveChanges();  
  
```  

Si un atributo personalizado no estaba incluido en las clases generadas, aún puede usarlo.


```csharp
var account = new Account();
// set attribute values
    // string primary name
    account.Name = "Contoso";
    // A custom boolean attribute not included in the generated classes.
    account["sample_customboolean"] = false;


//Create the account
Guid accountid = svc.Create(account);
```

#### <a name="assign-an-early-bound-instance-to-a-late-bound-instance"></a>Asignar una instancia con enlace en tiempo de compilación a una instancia con enlace en tiempo de ejecución  
 El siguiente ejemplo muestra cómo asignar una instancia con enlace en tiempo de compilación a una instancia con enlace en tiempo de ejecución.  
  
```csharp
Entity incident = ((Entity)context.InputParameters[ParameterName.Target]).ToEntity<Incident>();  
Task relatedEntity = new Task() { Id = this.TaskId };  
  
incident.RelatedEntities[new Relationship("Incident_Tasks")] =   
new EntityCollection(new Entity[] { relatedEntity.ToEntity<Entity>() });  
```

### <a name="see-also"></a>Vea también

[Operaciones de la entidad con el servicio de organización](entity-operations.md)<br />
[Crear entidades con el servicio de la organización](entity-operations-create.md)<br />
[Recuperar una entidad usando un servicio de organización](entity-operations-retrieve.md)<br />
[Consulta de datos duplicados con el servicio de organización](entity-operations-query-data.md)<br />
[Actualizar y eliminar entidades con el servicio de la organización](entity-operations-update-delete.md)<br />
[Asociar y desasociar entidades con el servicio de la organización](entity-operations-associate-disassociate.md)<br />
[Interfaz IOrganizationService](iorganizationservice-interface.md)<br />
[Uso de OrganizationServiceContext](organizationservicecontext.md)<br />