---
title: Creación de entidades con el servicio de organización (Common Data Service) | Microsoft Docs
description: <Description>
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
# <a name="create-entities-using-the-organization-service"></a>Creación de entidades con el servicio de la organización

Este tema incluye ejemplos que usan los de enlace en tiempo de ejecución y enlace en tiempo de compilación Más información: 
- [Programación de enlace en tiempo de ejecución y en tiempo de compilación con el servicio de la organización](early-bound-programming.md)
- [Generar clases de enlace en tiempo de compilación para el servicio de la organización](generate-early-bound-classes.md)

## <a name="basic-create"></a>Crear básico

Los ejemplos siguientes muestran cómo crear un registro de entidad con los estilos de enlace en tiempo de ejecución y en tiempo de compilación.

<!-- TODO make this an include? -->
Cada uno de los ejemplos usa una variable `svc` que representa una instancia de una clase que implementa los métodos en la interfaz <xref:Microsoft.Xrm.Sdk.IOrganizationService>. Para obtener más información sobre las clases que admiten esta interfaz, consulte [Interfaz IOrganizationService](iorganizationservice-interface.md).

> [!NOTE]
> Cada entidad tiene un atributo de identificador único que puede especificar el crear una entidad. En la mayoría de los casos debe permitir que el sistema lo establezca automáticamente porque los valores generados por el sistema se optimizan para el máximo rendimiento.


### <a name="late-bound-example"></a>Ejemplo de enlace en tiempo de ejecución

El siguiente ejemplo muestra cómo se usa la clase <xref:Microsoft.Xrm.Sdk.Entity> para crear un registro de cuenta utilizando el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*> . 

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

### <a name="early-bound-example"></a>Ejemplo de enlace en tiempo de compilación

El siguiente ejemplo muestra cómo se usa la clase `Account` generada para crear un registro de cuenta utilizando el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*> .

La clase `Account` se obtiene de la clase <xref:Microsoft.Xrm.Sdk.Entity>

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

## <a name="use-the-createrequest-class"></a>Usar la clase CreateRequest

En lugar de utiliza el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*>, puede utiliza bien la clase <xref:Microsoft.Xrm.Sdk.Entity> de enlace en tiempo de ejecución o las clases de entidad de enlace en tiempo de compilación con la clase <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> configurando la instancia de entidad en la propiedad <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest.Target> y después utilizando el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> para obtener a una <xref:Microsoft.Xrm.Sdk.Messages.CreateResponse>. El identificador de registro creado estará en el valor de la propiedad <xref:Microsoft.Xrm.Sdk.Messages.CreateResponse.id>.

```csharp
var request = new CreateRequest() { Target = account };
var response  = (CreateResponse)svc.Execute(request);
Guid accountid = response.id;
```

### <a name="when-to-use-the-createrequest-class"></a>Cuando utilizar la clase CreateRequest

Debe usar la clase <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> si desea pasar parámetros opcionales. Hay dos casos donde es posible que necesite parámetros especiales.
 - Cuando quiere que se apliquen reglas de detección de duplicados. Más información: [Buscar registros de duplicados](#check-for-duplicate-records)
 - Cuando cree un registro que represente un componente de la solución, como un [WebResource](../reference/entities/webresource.md) y desee asociarlo con una solución específica. En este caso, incluiría el valor de [Solution.UniqueName](../reference/entities/solution.md#BKMK_UniqueName) con el parámetro `SolutionUniqueName`. Más información: [Usar mensajes con el servicio de la organización](use-messages.md)

## <a name="create-related-entities-in-one-operation"></a>Crear entidades relacionadas en una operación

Cuando cree un nuevo registro de la entidad también puede crear registros de entidad relacionados en la misma operación.

Los siguientes ejemplos de enlace en tiempo de ejecución y en tiempo de compilación crearán las entidades [Account](../reference/entities/account.md) y [Contact](../reference/entities/contact.md) relacionadas con esa cuenta mediante la relación [ account_primary_contact del contacto](../reference/entities/contact.md#BKMK_account_primary_contact) de uno a varios donde la búsqueda de [primarycontactid de la cuenta](../reference/entities/account.md#BKMK_PrimaryContactId) es `ReferencingAttribute`.

Los ejemplos también crearán tres registros de entidad [Task](../reference/entities/task.md) relacionados con la relación [Account_Tasks de la cuenta](../reference/entities/account.md#BKMK_Account_Tasks) de uno a varios donde la búsqueda [regardingobjectid de la tarea](../reference/entities/task.md#BKMK_RegardingObjectId) es `ReferencingAttribute`.

### <a name="late-bound-example"></a>Ejemplo de enlace en tiempo de ejecución

En el estilo de enlace en tiempo de ejecución debe agregar explícitamente las entidades relacionadas a una <xref:Microsoft.Xrm.Sdk.EntityCollection> y después usar la clase <xref:Microsoft.Xrm.Sdk.Relationship> para especificar la relación utilizando el `SchemaName` de la relación antes de poder agregarlas a la propiedad <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.RelatedEntities> .

```csharp
// Use Entity class with entity logical name
var account = new Entity("account");

// Set attribute values
    // string primary name
    account["name"] = "Sample Account";

// Create Primary contact
var primaryContact = new Entity("contact");
primaryContact["firstname"] = "John";
primaryContact["lastname"] = "Smith";

// Add the contact to an EntityCollection
EntityCollection primaryContactCollection = new EntityCollection();
primaryContactCollection.Entities.Add(primaryContact);

// Set the value to the relationship
account.RelatedEntities[new Relationship("account_primary_contact")] = primaryContactCollection;

// Add related tasks to create
var taskList = new List<Entity>() {
            new Entity("task") { ["subject"] = "Task 1" },
            new Entity("task") { ["subject"] = "Task 2" },
            new Entity("task") { ["subject"] = "Task 3" }
        };

// Add the tasks to an EntityCollection
EntityCollection tasks = new EntityCollection(taskList);

// Set the value to the relationship
account.RelatedEntities[new Relationship("Account_Tasks")] = tasks;

// Create the account
Guid accountid = svc.Create(account);
```

### <a name="early-bound-example"></a>Ejemplo de enlace en tiempo de compilación

Con las clases de enlace en tiempo de compilación puede escribir menos código porque las clases incluyen definiciones de las relaciones.

```csharp
var account = new Account();
// set attribute values
    // string primary name
    account.Name = "Sample Account";

    // Set the account primary contact
    account.account_primary_contact = new Contact()
    { FirstName = "John", LastName = "Smith" };

// Set a list of Tasks to create
account.Account_Tasks = new List<Task>() {
        new Task() { Subject = "Task 1" },
        new Task() { Subject = "Task 2" },
        new Task() { Subject = "Task 3" }
    };

// Create the account
Guid accountid = svc.Create(account);
```

## <a name="associate-entities-on-create"></a>Asociar entidades en la creación

Puede asociar cualquier registro nuevo con un registro existente cuando lo crea que dispone de la misma forma que haría al actualizarlo. Debe usar una <xref:Microsoft.Xrm.Sdk.EntityReference> para establecer el valor de un atributo de búsqueda.

Esta asignación de atributo de búsqueda es el mismo para los estilos de enlace en tiempo de ejecución y en tiempo de compilación.

```csharp
//Use Entity class with entity logical name
var account = new Entity("account");

// set attribute values
    //string primary name
    account["name"] = "Sample Account";

Guid primarycontactid = new Guid("e6fa5509-2582-e811-a95e-000d3af40ae7");

account["primarycontactid"] = new EntityReference("contact", primarycontactid);

//Create the account
Guid accountid = svc.Create(account);
```

### <a name="use-alternate-keys"></a>Claves alternativas de uso

Si no sabe cuál es el identificador de la entidad y se cumplen las condiciones siguientes:
- Ha configurado claves alternativas para la entidad
- Conoce los valores de las claves

Puede usar los constructores <xref:Microsoft.Xrm.Sdk.EntityReference> alternativos mediante los parámetros `keyName` y `keyValue`.
```csharp
account["primarycontactid"] = new EntityReference("contact", "sample_username", "john.smith123");
```
> [!NOTE]
> Las claves alternativas se usan normalmente solo para los escenarios de integración de datos

Más información: 
- [Definir claves alternativas para hacer referencia a registros](../../../maker/common-data-service/define-alternate-keys-reference-records.md)
- [Usar una clave alternativa para crear un registro](../use-alternate-key-create-record.md)
- [Trabajar con claves alternativas](../define-alternate-keys-entity.md)


## <a name="check-for-duplicate-records"></a>Comprobar registros duplicados

Más información: [Detección de datos duplicados con el servicio de la organización](detect-duplicate-data.md)

## <a name="set-default-values-from-the-primary-entity"></a>Establezca los valores predeterminados desde la entidad principal

Cuando las personas crean registros nuevos en la aplicación, se crean normalmente en el contexto de otro registro. Por ejemplo, se puede crear un nuevo registro de contacto en el contexto de una cuenta. Cuando esto ocurre es posible que algunos valores de atributo de la entidad de la cuenta se copien en el formulario de contacto. Esto agiliza la creación del nuevo registro relacionado porque el nuevo registro tendrá algunos valores predeterminados establecidos para que la persona que edita el registro que se va a crear no necesite especificar esos valores. Pueden cambiar los valores si quieren antes de guardar.

Los valores que se copiarán cuando se crea un nuevo registro de esta manera están controlados por las configuraciones que se aplican al entorno de Common Data Service, por lo que puede variar entre entornos. 

Más información: 
- [Asignar campos de entidad](../../../maker/common-data-service/map-entity-fields.md)
- [Personalizar asignaciones de entidad y atributo](../customize-entity-attribute-mappings.md)

Como desarrollador, puede usar la clase <xref:Microsoft.Crm.Sdk.Messages.InitializeFromRequest> para generar una entidad con esos valores predeterminados ya establecidos.

El siguiente código creará un nuevo contacto asociado a una cuenta existente. La entidad contacto se asociará a la cuenta especificada y a determinados valores de atributo, como `Telephone1` y los diferentes valores de dirección compartidos entre la cuenta y la entidad contacto se establecerán de forma predeterminada.

```csharp
//The account that the contact will be associated with:
var parentAccount = new EntityReference("account", new Guid("a976763a-ba1c-e811-a954-000d3af451d6"));

// Initialize a new contact entity with default values from the account.
var request = new InitializeFromRequest()
{
    EntityMoniker = parentAccount,
    TargetEntityName = "contact"

};

var response = (InitializeFromResponse)svc.Execute(request);
//Get the Entity from the response
Entity contact = response.Entity;

// Set values that are not from the account
contact["firstname"] = "Joe";
contact["lastname"] = "Smith";

// Create the contact
Guid contactid = svc.Create(contact);
```

## <a name="use-upsert"></a>Usar upsert

Otra forma de crear una entidad es usando la clase <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest>. Un upsert creará una nueva entidad cuando no haya ningún registro existente con identificadores únicos incluidos en la entidad que se pasó con la solicitud.

Más información: [Usar upsert](entity-operations-update-delete.md#use-upsert)


### <a name="see-also"></a>Vea también

[Recuperar una entidad usando un servicio de organización](entity-operations-retrieve.md)<br />
[Actualizar y eliminar entidades con el servicio de la organización](entity-operations-update-delete.md)<br />
[Asociar y desasociar entidades con el servicio de la organización](entity-operations-associate-disassociate.md)<br />

