---
title: Actualización y eliminación de entidades con el servicio de la organización (Common Data Service) | Microsoft Docs
description: Más información sobre cómo actualizar y eliminar entidades con el servicio de la organización.
ms.custom: ''
ms.date: 04/21/2019
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
# <a name="update-and-delete-entities-using-the-organization-service"></a>Actualización y eliminación de entidades con el servicio de la organización

Este tema incluye ejemplos que usan los de enlace en tiempo de ejecución y enlace en tiempo de compilación Más información: [Programación en tiempo de ejecución y en tiempo de compilación con el servicio de la organización](early-bound-programming.md)

Cada uno de los ejemplos usa una variable `svc` que representa una instancia de una clase que implementa los métodos en la interfaz <xref:Microsoft.Xrm.Sdk.IOrganizationService>. Para obtener más información sobre las clases que admiten esta interfaz, consulte [Interfaz IOrganizationService](iorganizationservice-interface.md).

> [!IMPORTANT]
>  Al actualizar una entidad, incluya únicamente los atributos que está cambiando. Actualizar simplemente los atributos de una entidad que se recuperó anteriormente actualizará cada atributo aunque el valor no se modifica. Esto puede provocar eventos del sistema que pueden desencadenar la lógica de negocios que espera que los valores hayan cambiado realmente. Esto también puede hacer que parezca que las atributos se han actualizado en auditoría de datos cuando de hecho no han cambiado realmente. 
>
> Debe crear una nueva instancia de entidad, establecer el atributo de identificador y los valores de atributo que está cambiando, y utilizar esa instancia de entidad para actualizar el registro.

> [!NOTE]
> Los metadatos de los atributos incluyen una propiedad `RequiredLevel`. Cuando esta opción se establece en `SystemRequired`, no puede establecer estos atributos a un valor nulo. Si intenta esto obtendrá el código de error `-2147220989` con el mensaje `Attribute: <attribute name> cannot be set to NULL`.
> 
> Más información: [Nivel de requisito de atributo](../entity-attribute-metadata.md#attribute-requirement-level)

## <a name="basic-update"></a>Actualización básica

Los dos ejemplos abajo usan el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> para establecer los valores de atributo de una entidad que se recuperó anteriormente.

Use la propiedad <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.Id> para transferir el valor del identificador único de la entidad recuperada para la instancia de entidad que se utiliza para realizar la operación de actualización.

> [!NOTE]
> Si intenta actualizar un registro sin un valor de clave principal se mostrará el error: `Entity Id must be specified for Update`.
> 
> Si no tiene un valor de clave principal, también puede actualizar registros usando las claves alternativas. Más información: [Actualización con clave alternativa](#update-with-alternate-key)

### <a name="late-bound-example"></a>Ejemplo de enlace en tiempo de ejecución

El siguiente ejemplo muestra cómo se usa la clase <xref:Microsoft.Xrm.Sdk.Entity> para crear un registro de cuenta utilizando el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> . 

```csharp
var retrievedAccount = new Entity("account", new Guid("a976763a-ba1c-e811-a954-000d3af451d6"));

//Use Entity class with entity logical name
var account = new Entity("account");
account.Id = retrievedAccount.Id;
// set attribute values
// Boolean (Two option)
account["creditonhold"] = true;
// DateTime
account["lastonholdtime"] = DateTime.Now;
// Double
account["address1_latitude"] = 47.642311;
account["address1_longitude"] = -122.136841;
// Int
account["numberofemployees"] = 400;
// Money
account["revenue"] = new Money(new Decimal(2000000.00));
// Picklist (Option set)
account["accountcategorycode"] = new OptionSetValue(2); //Standard customer

//Update the account
svc.Update(account);
```

### <a name="early-bound-example"></a>Ejemplo de enlace en tiempo de compilación

El siguiente ejemplo muestra cómo se usa la clase `Account` generada para actualizar un registro de cuenta utilizando el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> .

```csharp
var retrievedAccount = new Account()
{ Id = new Guid("a976763a-ba1c-e811-a954-000d3af451d6") };

var account = new Account();
account.Id = retrievedAccount.Id;
// set attribute values
// Boolean (Two option)
account.CreditOnHold = true;
// DateTime
account.LastOnHoldTime = DateTime.Now;
// Double
account.Address1_Latitude = 47.642311;
account.Address1_Longitude = -122.136841;
// Int
account.NumberOfEmployees = 400;
// Money
account.Revenue = new Money(new Decimal(2000000.00));
// Picklist (Option set)
account.AccountCategoryCode = new OptionSetValue(2); //Standard customer

//Update the account
svc.Update(account);
```

## <a name="use-the-updaterequest-class"></a>Usar la clase UpdateRequest

En lugar de utiliza el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*>, puede utiliza bien la clase <xref:Microsoft.Xrm.Sdk.Entity> de enlace en tiempo de ejecución o las clases de entidad de enlace en tiempo de compilación generadas con la clase <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> configurando la instancia de entidad en la propiedad <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest.Target> y después utilizando el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> .

> [!NOTE]
> <xref:Microsoft.Xrm.Sdk.Messages.UpdateResponse> no tiene propiedades. Aunque lo devuelve el método <xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>, no es necesario referirse al mismo.
 
```csharp
var request = new UpdateRequest()
{ Target = account };
svc.Execute(request);
```
### <a name="when-to-use-the-updaterequest-class"></a>Cuando utilizar la clase UpdateRequest

Debe usar la clase <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> si desea pasar parámetros opcionales. Hay dos casos donde es posible que necesite parámetros especiales.
 - Cuando quiere que se apliquen reglas de detección de duplicados. Más información: [Búsqueda de registros de duplicados](entity-operations-create.md#check-for-duplicate-records)
 - Cuando cree un registro de entidad que represente un componente de la solución, como un [WebResource](../reference/entities/webresource.md) y desee asociarlo con una solución específica. En este caso, incluiría el valor de [Solution.UniqueName](../reference/entities/solution.md#BKMK_UniqueName) con el parámetro `SolutionUniqueName`. Más información: [Usar mensajes con el servicio de la organización](use-messages.md)

Debe usar la clase <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> si desea especificar un comportamiento de la simultaneidad optimista. Más información: [Comportamiento de simultaneidad optimista](#optimistic-concurrency-behavior)

## <a name="update-related-entities-in-one-operation"></a>Actualización de entidades relacionadas en una operación

De la misma forma en que puede [crear entidades relacionadas en una operación](entity-operations-create.md#create-related-entities-in-one-operation), también puede actualizar las entidades relacionadas.

Para ello, tiene que recuperar una entidad con los registros relacionados para que pueda tener acceso a los valores de identificador. Más información: [Recuperación con registros relacionados](entity-operations-retrieve.md#retrieve-with-related-records)

> [!IMPORTANT]
> Las actualizaciones de los registros se realizan en un orden específico. Primero se procesan las entidades principales y luego se procesan las entidades relacionadas. Si la entidad principal para una búsqueda o un atributo de entidad relacionada realiza un cambio, y luego una entidad relacionada actualiza el mismo atributo, se mantiene el valor de la entidad relacionada. Normalmente, un valor de atributo de búsqueda y el equivalente en el <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.RelatedEntities> para la misma relación no deben usarse a la vez.

### <a name="late-bound-example"></a>Ejemplo de enlace en tiempo de ejecución


```csharp
var account = new Entity("account");
account.Id = retrievedAccount.Id;

//Define relationships
var primaryContactRelationship = new Relationship("account_primary_contact");
var AccountTasksRelationship = new Relationship("Account_Tasks");

//Update the account name
account["name"] = "New Account name";

//Update the email address for the primary contact of the account
var contact = new Entity("contact");
contact.Id = retrievedAccount.RelatedEntities[primaryContactRelationship]
.Entities.FirstOrDefault().Id;
contact["emailaddress1"] = "someone_a@example.com";

List<Entity> primaryContacts = new List<Entity>();
primaryContacts.Add(contact);  
account.RelatedEntities.Add(primaryContactRelationship, new EntityCollection(primaryContacts));

// Find related Tasks that need to be updated
List<Entity> tasksToUpdate = retrievedAccount
.RelatedEntities[AccountTasksRelationship].Entities
.Where(t => t["subject"].Equals("Example Task")).ToList();

// A list to put the updated tasks
List<Entity> updatedTasks = new List<Entity>();

//Fill the list of updated tasks based on the tasks that need to but updated
tasksToUpdate.ForEach(t => {
var updatedTask = new Entity("task");
updatedTask.Id = t.Id;
updatedTask["subject"] = "Updated Subject";

updatedTasks.Add(updatedTask);
});

//Set the updated tasks to the collection
account.RelatedEntities.Add(AccountTasksRelationship, new EntityCollection(updatedTasks));

//Update the account and related contact and tasks
svc.Update(account);
```


### <a name="early-bound-example"></a>Ejemplo de enlace en tiempo de compilación

```csharp
var account = new Account();
account.Id = retrievedAccount.Id;

//Update the account
account.Name = "New Account name";

//Update the email address for the primary contact of the account
account.account_primary_contact = new Contact
{ Id = retrievedAccount.PrimaryContactId.Id, EMailAddress1 = "someone_a@example.com" };

// Find related Tasks that need to be updated
List<Task> tasksToUpdate = retrievedAccount.Account_Tasks
    .Where(t => t.Subject.Equals("Example Task")).ToList();

// A list to put the updated tasks
List<Task> updatedTasks = new List<Task>();

//Fill the list of updated tasks based on the tasks that need to but updated
tasksToUpdate.ForEach(t =>
{
    updatedTasks
    .Add(new Task() {
        ActivityId = t.ActivityId,
        Subject = "Updated Subject"
    });

});

//Set the updated tasks to the collection
account.Account_Tasks = updatedTasks;

//Update the account and related contact and tasks
svc.Update(account);
```

## <a name="check-for-duplicate-records"></a>Comprobar registros duplicados

Para actualizar una entidad puede cambiar los valores para que el registro represente un duplicado de otro registro. Más información: [Detección de datos duplicados con el servicio de la organización](detect-duplicate-data.md)

## <a name="update-with-alternate-key"></a>Actualizar con clave alternativa

Si tiene una clave alternativa definida para una entidad, puede usarla en lugar de la clave principal para actualizar un registro. No puede usar la clase enlazada en tiempo de compilación para especificar la clave alternativa. Debe usar el constructor [Entity(String, KeyAttributeCollection)](/dotnet/api/microsoft.xrm.sdk.entity.-ctor#Microsoft_Xrm_Sdk_Entity__ctor_System_String_Microsoft_Xrm_Sdk_KeyAttributeCollection_) para especificar la clave alternativa.

Si desea usar enlaces de tipo de compilación, puede convertir <xref:Microsoft.Xrm.Sdk.Entity> en una clase enlazada en tiempo de compilación mediante el método <xref:Microsoft.Xrm.Sdk.Entity.ToEntity``1>.

El siguiente ejemplo muestra cómo actualizar una entidad `Account` mediante una clave alternativa definida para el atributo `accountnumber`.

> [!IMPORTANT]
> De forma predeterminada, no hay claves alternativas definida para ninguna entidad. Este método se puede usar únicamente cuando el entorno está configurado para definir una clave alternativa para una entidad.

```csharp
var accountNumberKey = new KeyAttributeCollection();
accountNumberKey.Add(new KeyValuePair<string, object>("accountnumber", "123456"));

Account exampleAccount = new Entity("account", accountNumberKey).ToEntity<Account>();
exampleAccount.Name = "New Account Name";
svc.Update(exampleAccount);
```

Más información: 
- [Trabajar con claves alternativas](../define-alternate-keys-entity.md)
- [Usar una clave alternativa para crear un registro](../use-alternate-key-create-record.md)

## <a name="use-upsert"></a>Usar upsert

Normalmente, en escenarios de integración de datos deberá crear o actualizar los datos en Common Data Service desde otros orígenes. Common Data Service puede tener ya registros con el mismo identificador único, que puede ser una clave alternativa. Si existe un registro de entidad, debe actualizarlo. Si no existe, debe crearlo para sincronizar los datos que se agregan con los datos de origen. Es cuando hay que usar upsert.

El siguiente ejemplo usa <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest> dos veces. La primera vez se crea el registro de la entidad cuenta, y la segunda vez que se actualiza porque tiene un valor `accountnumber` y hay una clave alternativa que está usando ese atributo.

Para ambas llamadas, la propiedad <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse>.<xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse.RecordCreated> indica si la operación creó un registro o no.

```csharp
// This environment has an alternate key set for the accountnumber attribute.

//Instantiate account entity with accountnumber value
var account = new Entity("account", "accountnumber", "0003");
account["name"] = "New Account";

//Use Upsert the first time
UpsertRequest request1 = new UpsertRequest() {
Target = account
};

//The new entity is created
var response1 = (UpsertResponse)svc.Execute(request1);
Console.WriteLine("Record Created: {0}",response1.RecordCreated); //true

//Update the name of the existing account entity
account["name"] = "Updated Account";

//Use Upsert for the second time
UpsertRequest request2 = new UpsertRequest()
{
Target = account
};

//The existing entity is updated.
var response2 = (UpsertResponse)svc.Execute(request1);
Console.WriteLine("Record Created: {0}", response2.RecordCreated); //false
```
Más información: [Uso de Upsert para insertar o actualizar un registro](../use-upsert-insert-update-record.md)

## <a name="delete"></a>Eliminar

El método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*> requiere simplemente el nombre lógico de la entidad y de identificador único. Independientemente de si usa la clase <xref:Microsoft.Xrm.Sdk.Entity> de enlace en tiempo de ejecución o una clase de entidad generada de enlace de tiempo de compilación, puede usar la siguiente sintaxis para eliminar una operación si pasa <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.LogicalName> y <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.Id> propiedades

```csharp
svc.Delete(retrievedEntity.LogicalName, retrievedEntity.Id);
```
O bien, puede los valores:
```csharp
svc.Delete("account", new Guid("e5fa5509-2582-e811-a95e-000d3af40ae7"));
```
> [!IMPORTANT]
> Las operaciones de eliminación pueden iniciar operaciones en cascada que pueden eliminar registros secundarios para mantener la integridad de los datos en función de la lógica definida para las relaciones en el entorno. Más información: [Comportamiento de las relaciones de entidad](../../../maker/common-data-service/entity-relationship-behavior.md)

## <a name="use-the-deleterequest-class"></a>Uso de la clase DeleteRequest

Puede usar <xref:Microsoft.Xrm.Sdk.Messages.DeleteRequest> en lugar del método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*>, pero solo es necesario cuando quiere especificar el comportamiento de la simultaneidad optimista.

```csharp
var retrievedEntity = new Entity("account")
{
    Id = new Guid("c81ffd82-cd82-e811-a95c-000d3af49bf8"),
    RowVersion = "986335"

};

var request = new DeleteRequest()
{
    Target = retrievedEntity.ToEntityReference(),
    ConcurrencyBehavior = ConcurrencyBehavior.IfRowVersionMatches
};

svc.Execute(request);
```

## <a name="optimistic-concurrency-behavior"></a>Comportamiento de la simultaneidad optimista

Puede especificar el comportamiento de la simultaneidad optimista de la operación configurando la propiedad `ConcurrencyBehavior` de las clases <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> o <xref:Microsoft.Xrm.Sdk.Messages.DeleteRequest>.

La lógica para actualizar o eliminar el registro se puede basar en datos antiguos. Si los datos actuales son diferentes porque han cambiado desde que se recuperaron, la simultaneidad optimista proporciona una forma de cancelar una operación de actualizar o eliminar por lo que es posible que la recupera de nuevo y use los datos actuales para determinar si proseguir.

Para determinar si se ha cambiado la entidad, no necesita comparar todos los valores, puede usar la propiedad <xref:Microsoft.Xrm.Sdk.Entity.RowVersion> para ver si ha cambiado.

El siguiente ejemplo saldrá bien solamente cuando:
- `RowVersion` de la entidad de la base de datos es igual a `986323`
- La entidad cuenta está habilitada para la simultaneidad optimista (<xref href="Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsOptimisticConcurrencyEnabled?text=EntityMetadata.IsOptimisticConcurrencyEnabled" /> está en `true`)
- La propiedad `RowVersion` está establecida en la entidad que se pasó con la solicitud.

Si `RowVersion` no coincide, se producirá un error con el mensaje `The version of the existing record doesn't match the RowVersion property provided.`.

```csharp
var retrievedAccount = new Account()
{   
    Id = new Guid("a976763a-ba1c-e811-a954-000d3af451d6"), 
    RowVersion = "986323" 
};

var account = new Account();
account.Id = retrievedAccount.Id;
account.RowVersion = retrievedAccount.RowVersion;

// set attribute values
account.CreditOnHold = true;

//Update the account
var request = new UpdateRequest()
{ 
    Target = account,
    ConcurrencyBehavior = ConcurrencyBehavior.IfRowVersionMatches 
};

try
{
    svc.Execute(request);
}
catch (FaultException<OrganizationServiceFault> ex)
{
    switch (ex.Detail.ErrorCode)
    {
        case -2147088254: // ConcurrencyVersionMismatch 
        case -2147088253: // OptimisticConcurrencyNotEnabled 
            throw new InvalidOperationException(ex.Detail.Message);
        case -2147088243: // ConcurrencyVersionNotProvided
            throw new ArgumentNullException(ex.Detail.Message);
        default:
            throw ex;
    }
}
```

Más información: 
- [Simultaneidad optimista](../optimistic-concurrency.md)
- <xref href="Microsoft.Xrm.Sdk.ConcurrencyBehavior?text=ConcurrencyBehavior Enum"  />

## <a name="legacy-update-messages"></a>Mensajes de actualización heredados

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/perform-specialized-operations-using-update -->

Hay varios mensajes especializados obsoletos que realizan operaciones de actualización. En versiones anteriores se requería usar estos mensajes, pero ahora las mismas operaciones deben realizarse con <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> o la clase <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> con <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>

[!INCLUDE [cc-legacy-update-messages](../includes/cc-legacy-update-messages.md)]

Más información: [Comportamiento de operaciones de actualización especializadas](../special-update-operation-behavior.md)

### <a name="see-also"></a>Vea también

[Crear entidades con el servicio de la organización](entity-operations-create.md)<br />
[Recuperar una entidad usando un servicio de organización](entity-operations-retrieve.md)<br />
[Asociar y desasociar entidades con el servicio de la organización](entity-operations-associate-disassociate.md)<br />