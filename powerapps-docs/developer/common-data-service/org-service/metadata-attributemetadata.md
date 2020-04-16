---
title: Trabajar con metadatos de atributo (Common Data Service) | Microsoft Docs
description: Describe operaciones comunes en metadatos del atributo.
ms.custom: ''
ms.date: 04/05/2019
ms.reviewer: pehecke
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
ms.openlocfilehash: 2ae64d15ac0b5213f2f34c69cf771e8ab725021f
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156036"
---
# <a name="work-with-attribute-metadata"></a>Trabajar con metadatos de atributos

Este tema describe varias operaciones comunes que se pueden aplicar a metadatos del atributo.

<a name="BKMK_CreateAttributes"></a>   
## <a name="create-attributes"></a>Crear atributos

 Puede crear atributos al definir uno de los tipos de <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> y luego pasarlo al mensaje de <xref:Microsoft.Xrm.Sdk.Messages.CreateAttributeRequest>.  
  
 El siguiente ejemplo define el <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> para distintos tipos de atributos y los agrega a `List<AttributeMetadata>`. Al final del código las definiciones de atributo se pasan a una instancia de la clase <xref:Microsoft.Xrm.Sdk.Messages.CreateAttributeRequest> y el atributo es creado usando el método <xref:Microsoft.Xrm.Sdk.IOrganizationService><xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>. .  
  
 El siguiente código de ejemplo presupone que el prefijo actual de personalización es "nuevo" porque ese es el prefijo de personalización predeterminado para el editor de soluciones de la organización. Debe usar el prefijo de personalización para el editor de soluciones que mejor se ajuste al contexto de la solución.  

```csharp
// Create storage for new attributes being created
addedAttributes = new List<AttributeMetadata>();

// Create a boolean attribute
BooleanAttributeMetadata boolAttribute = new BooleanAttributeMetadata
{
    // Set base properties
    SchemaName = "new_Boolean",
    LogicalName = "new_boolean",
    DisplayName = new Label("Sample Boolean", _languageCode),
    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
    Description = new Label("Boolean Attribute", _languageCode),
    // Set extended properties
    OptionSet = new BooleanOptionSetMetadata(
        new OptionMetadata(new Label("True", _languageCode), 1),
        new OptionMetadata(new Label("False", _languageCode), 0)
        )
};

// Add to list
addedAttributes.Add(boolAttribute);

// Create a date time attribute
DateTimeAttributeMetadata dtAttribute = new DateTimeAttributeMetadata
{
    // Set base properties
    SchemaName = "new_Datetime",
    LogicalName = "new_datetime",
    DisplayName = new Label("Sample DateTime", _languageCode),
    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
    Description = new Label("DateTime Attribute", _languageCode),
    // Set extended properties
    Format = DateTimeFormat.DateOnly,
    ImeMode = ImeMode.Disabled
};

// Add to list
addedAttributes.Add(dtAttribute);

// Create a decimal attribute   
DecimalAttributeMetadata decimalAttribute = new DecimalAttributeMetadata
{
    // Set base properties
    SchemaName = "new_Decimal",
    LogicalName = "new_decimal",
    DisplayName = new Label("Sample Decimal", _languageCode),
    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
    Description = new Label("Decimal Attribute", _languageCode),
    // Set extended properties
    MaxValue = 100,
    MinValue = 0,
    Precision = 1
};

// Add to list
addedAttributes.Add(decimalAttribute);

// Create a integer attribute   
IntegerAttributeMetadata integerAttribute = new IntegerAttributeMetadata
{
    // Set base properties
    SchemaName = "new_Integer",
    LogicalName = "new_integer",
    DisplayName = new Label("Sample Integer", _languageCode),
    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
    Description = new Label("Integer Attribute", _languageCode),
    // Set extended properties
    Format = IntegerFormat.None,
    MaxValue = 100,
    MinValue = 0
};

// Add to list
addedAttributes.Add(integerAttribute);

// Create a memo attribute 
MemoAttributeMetadata memoAttribute = new MemoAttributeMetadata
{
    // Set base properties
    SchemaName = "new_Memo",
    LogicalName = "new_memo",
    DisplayName = new Label("Sample Memo", _languageCode),
    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
    Description = new Label("Memo Attribute", _languageCode),
    // Set extended properties
    Format = StringFormat.TextArea,
    ImeMode = ImeMode.Disabled,
    MaxLength = 500
};

// Add to list
addedAttributes.Add(memoAttribute);

// Create a money attribute 
MoneyAttributeMetadata moneyAttribute = new MoneyAttributeMetadata
{
    // Set base properties
    SchemaName = "new_Money",
    LogicalName = "new_money",
    DisplayName = new Label("Money Picklist", _languageCode),
    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
    Description = new Label("Money Attribue", _languageCode),
    // Set extended properties
    MaxValue = 1000.00,
    MinValue = 0.00,
    Precision = 1,
    PrecisionSource = 1,
    ImeMode = ImeMode.Disabled
};

// Add to list
addedAttributes.Add(moneyAttribute);

// Create a picklist attribute  
PicklistAttributeMetadata pickListAttribute =
    new PicklistAttributeMetadata
    {
        // Set base properties
        SchemaName = "new_Picklist",
        LogicalName = "new_picklist",
        DisplayName = new Label("Sample Picklist", _languageCode),
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
        Description = new Label("Picklist Attribute", _languageCode),
        // Set extended properties
        // Build local picklist options
        OptionSet = new OptionSetMetadata
        {
            IsGlobal = false,
            OptionSetType = OptionSetType.Picklist,
            Options =
        {
            new OptionMetadata(
                new Label("Created", _languageCode), null),
            new OptionMetadata(
                new Label("Updated", _languageCode), null),
            new OptionMetadata(
                new Label("Deleted", _languageCode), null)
        }
        }
    };

// Add to list
addedAttributes.Add(pickListAttribute);

// Create a string attribute
StringAttributeMetadata stringAttribute = new StringAttributeMetadata
{
    // Set base properties
    SchemaName = "new_String",
    LogicalName = "new_string",

    DisplayName = new Label("Sample String", _languageCode),
    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
    Description = new Label("String Attribute", _languageCode),
    // Set extended properties
    MaxLength = 100
};

// Add to list
addedAttributes.Add(stringAttribute);

//Multi-select attribute requires version 9.0 or higher.
if (_productVersion > new Version("9.0"))
{

    // Create a multi-select optionset
    MultiSelectPicklistAttributeMetadata multiSelectOptionSetAttribute = new MultiSelectPicklistAttributeMetadata()
    {
        SchemaName = "new_MultiSelectOptionSet",
        LogicalName = "new_multiselectoptionset",
        DisplayName = new Label("Multi-Select OptionSet", _languageCode),
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
        Description = new Label("Multi-Select OptionSet description", _languageCode),
        OptionSet = new OptionSetMetadata()
        {
            IsGlobal = false,
            OptionSetType = OptionSetType.Picklist,
            Options = {
        new OptionMetadata(new Label("First Option",_languageCode),null),
        new OptionMetadata(new Label("Second Option",_languageCode),null),
        new OptionMetadata(new Label("Third Option",_languageCode),null)
        }
        }
    };
    // Add to list
    addedAttributes.Add(multiSelectOptionSetAttribute);
}

// NOTE: LookupAttributeMetadata cannot be created outside the context of a relationship.
// Refer to the WorkWithRelationships.cs reference SDK sample for an example of this attribute type.

// NOTE: StateAttributeMetadata and StatusAttributeMetadata cannot be created via the SDK.

foreach (AttributeMetadata anAttribute in addedAttributes)
{
    // Create the request.
    CreateAttributeRequest createAttributeRequest = new CreateAttributeRequest
    {
        EntityName = Contact.EntityLogicalName,
        Attribute = anAttribute
    };

    // Execute the request.
    _serviceProxy.Execute(createAttributeRequest);

    Console.WriteLine("Created the attribute {0}.", anAttribute.SchemaName);
}
```

<a name="BKMK_RetrieveAttribute"></a>

## <a name="retrieve-an-attribute"></a>Recuperar un atributo

 Este ejemplo muestra cómo recuperar el <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> para un atributo mediante <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAttributeRequest>. Este ejemplo recupera los metadatos para un atributo <xref:Microsoft.Xrm.Sdk.Metadata.StringAttributeMetadata>cliente llamado "new_string" desde la entidad Contacto que fue creada en [Crear Atributos](#BKMK_CreateAttributes)
  
> [!NOTE]
> Porque <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAttributeRequest.RetrieveAsIfPublished> es verdadero, esta solicitud devuelve la definición actual sin publicar de este atributo. Puede usar esta opción si está creando un editor de Atributo y desea recuperar la definición del atributo sin publicar. De lo contrario, no debe especificar `RetrieveAsIfPublished`. Más información: [Recuperar metadatos no publicados](/dynamics365/customer-engagement/developer/customize-dev/publish-customizations#retrieving-unpublished-metadata).  

```csharp
// Create the request
RetrieveAttributeRequest attributeRequest = new RetrieveAttributeRequest
{
    EntityLogicalName = Contact.EntityLogicalName,
    LogicalName = "new_string",
    RetrieveAsIfPublished = true
};

// Execute the request
RetrieveAttributeResponse attributeResponse =
    (RetrieveAttributeResponse)_serviceProxy.Execute(attributeRequest);

Console.WriteLine("Retrieved the attribute {0}.",
    attributeResponse.AttributeMetadata.SchemaName);
```

<a name="BKMK_UpdateAttribute"></a>

## <a name="update-an-attribute"></a>Actualizar un atributo

 Este código de ejemplo muestra cómo actualizar un atributo. Este ejemplo usa la <xref:Microsoft.Xrm.Sdk.Messages.UpdateAttributeRequest> para cambiar al <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.DisplayName> propiedad de un atributo personalizado previamente recuperado para la entidad `Contact`.  

```csharp
// Modify the retrieved attribute
AttributeMetadata retrievedAttributeMetadata =
    attributeResponse.AttributeMetadata;
retrievedAttributeMetadata.DisplayName =
    new Label("Update String Attribute", _languageCode);

// Update an attribute retrieved via RetrieveAttributeRequest
UpdateAttributeRequest updateRequest = new UpdateAttributeRequest
{
    Attribute = retrievedAttributeMetadata,
    EntityName = Contact.EntityLogicalName,
    MergeLabels = false
};

// Execute the request
_serviceProxy.Execute(updateRequest);

Console.WriteLine("Updated the attribute {0}.",
    retrievedAttributeMetadata.SchemaName);
```

<a name="BKMK_CreateLookupAttribute"></a>

## <a name="create-a-lookup-attribute"></a>Crear un atributo de búsqueda

 Un atributo de búsqueda se crea mediante el <xref:Microsoft.Xrm.Sdk.Messages.CreateOneToManyRequest>.  

```csharp
CreateOneToManyRequest req = new CreateOneToManyRequest()
{
    Lookup = new LookupAttributeMetadata()
    {
        Description = new Label("The referral (lead) from the bank account owner", 1033),
        DisplayName = new Label("Referral", 1033),
        LogicalName = "new_parent_leadid",
        SchemaName = "New_Parent_leadId",
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.Recommended)
    },
    OneToManyRelationship = new OneToManyRelationshipMetadata()
    {
        AssociatedMenuConfiguration = new AssociatedMenuConfiguration()
        {
            Behavior = AssociatedMenuBehavior.UseCollectionName,
            Group = AssociatedMenuGroup.Details,
            Label = new Label("Bank Accounts", 1033),
            Order = 10000
        },
        CascadeConfiguration = new CascadeConfiguration()
        {
            Assign = CascadeType.Cascade,
            Delete = CascadeType.Cascade,
            Merge = CascadeType.Cascade,
            Reparent = CascadeType.Cascade,
            Share = CascadeType.Cascade,
            Unshare = CascadeType.Cascade
        },
        ReferencedEntity = "lead",
        ReferencedAttribute = "leadid",
        ReferencingEntity = _customEntityName,
        SchemaName = "new_lead_new_bankaccount"
    }
};
_serviceProxy.Execute(req);
```

<a name="BKMK_createcustlookup"></a>

## <a name="create-a-customer-lookup-attribute"></a>Crear un atributo de búsqueda de clientes

 A diferencia de un atributo de búsqueda, un atributo de búsqueda de cliente se crea con el mensaje <xref:Microsoft.Xrm.Sdk.Messages.CreateCustomerRelationshipsRequest>, que agrega dos relaciones al atributo de búsqueda: uno a la entidad `Account` y otro a la entidad `Contact`. No puede agregar relación a ninguna otra entidad salvo a las entidades `Account` y `Contact` para un atributo de búsqueda de cliente.  

```csharp
CreateCustomerRelationshipsRequest createCustomerReq = new CreateCustomerRelationshipsRequest
{
    Lookup = new LookupAttributeMetadata
    {
        Description = new Label("The owner of the bank account", 1033),
        DisplayName = new Label("Account owner", 1033),
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.ApplicationRequired),
        SchemaName = "new_customerid"
    },
    OneToManyRelationships = new OneToManyRelationshipMetadata[]
    {
        new OneToManyRelationshipMetadata()
        {
            ReferencedEntity = "account",
            ReferencingEntity = _customEntityName,
            SchemaName = "new_bankaccount_customer_account",
        },
        new OneToManyRelationshipMetadata()
        {
            ReferencedEntity = "contact",
            ReferencingEntity = _customEntityName,
            SchemaName = "new_bankaccount_customer_contact",
        }
    },
};
_serviceProxy.Execute(createCustomerReq);
```

<a name="BKMK_CreatePicklistGlobalOptionSet"></a>

## <a name="create-a-picklist-that-uses-a-global-option-set"></a>Crear una lista desplegable que usa un conjunto de opciones global

 Este código de ejemplo muestra cómo crear un atributo de <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata> que está asociado con un conjunto de opciones globales.  
  
 El siguiente ejemplo se usa <xref:Microsoft.Xrm.Sdk.Messages.CreateAttributeRequest> para establecer las opciones para que un atributo de <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata> use un conjunto de opciones global con un nombre representado por la variable de cadena `_globalOptionSetName`. Más información: [Personalizar conjuntos de opciones](metadata-option-sets.md)  
 
```csharp
// Create a Picklist linked to the option set.
// Specify which entity will own the picklist, and create it.
CreateAttributeRequest createRequest = new CreateAttributeRequest
{
    EntityName = Contact.EntityLogicalName,
    Attribute = new PicklistAttributeMetadata
    {
        SchemaName = "sample_examplepicklist",
        LogicalName = "sample_examplepicklist",
        DisplayName = new Label("Example Picklist", _languageCode),
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),

        // In order to relate the picklist to the global option set, be sure
        // to specify the two attributes below appropriately.
        // Failing to do so will lead to errors.
        OptionSet = new OptionSetMetadata
        {
            IsGlobal = true,
            Name = _globalOptionSetName
        }
    }
};

_serviceProxy.Execute(createRequest);
```

<a name="BKMK_InsertNewStatusValue"></a>

## <a name="insert-a-new-status-value"></a>Insertar un nuevo valor de estado

 Este código de ejemplo muestra cómo insertar una nueva opción **Razón para el estado** para el atributo de <xref:Microsoft.Xrm.Sdk.Metadata.StatusAttributeMetadata>.  
  
 El siguiente código deejemplo usa <xref:Microsoft.Xrm.Sdk.Messages.InsertStatusValueRequest> para especificar una nueva opción para el atributo `Contact.StatusCode` de la entidad `Contact` que es válido cuando `Contact.StateCode` es 0 (activo). La propiedad <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> método procesa la solicitud.  
  
 El siguiente código de ejemplo permite dos opciones válidas de **Razón para el estado** para los contactos activos: **Activo** e **Inactivo**.  
  
```csharp
// Use InsertStatusValueRequest message to insert a new status 
// in an existing status attribute. 
// Create the request.
InsertStatusValueRequest insertStatusValueRequest =
    new InsertStatusValueRequest
{
    AttributeLogicalName = "statuscode",
    EntityLogicalName = Contact.EntityLogicalName,
    Label = new Label("Dormant", _languageCode),
    StateCode = 0
};

// Execute the request and store newly inserted value 
// for cleanup, used later part of this sample. 
_insertedStatusValue = ((InsertStatusValueResponse)_serviceProxy.Execute(
    insertStatusValueRequest)).NewOptionValue;

Console.WriteLine("Created {0} with the value of {1}.",
    insertStatusValueRequest.Label.LocalizedLabels[0].Label,
    _insertedStatusValue);
```

<a name="BKMK_UpdateStateValue"></a>

## <a name="update-a-state-value"></a>Actualizar un valor de estado

 Este código de ejemplo muestra cómo cambiar la etiqueta para una opción en un atributo de <xref:Microsoft.Xrm.Sdk.Metadata.StateAttributeMetadata>.  
  
 El siguiente código de ejemplo usa <xref:Microsoft.Xrm.Sdk.Messages.UpdateStateValueRequest> para cambiar la etiqueta de la opción de `Contact.StateCode` **Activo** a **Abrir**.  

```csharp
// Modify the state value label from Active to Open.
// Create the request.
UpdateStateValueRequest updateStateValue = new UpdateStateValueRequest
{
    AttributeLogicalName = "statecode",
    EntityLogicalName = Contact.EntityLogicalName,
    Value = 1,
    Label = new Label("Open", _languageCode)
};

// Execute the request.
_serviceProxy.Execute(updateStateValue);

Console.WriteLine(
    "Updated {0} state attribute of {1} entity from 'Active' to '{2}'.",
    updateStateValue.AttributeLogicalName,
    updateStateValue.EntityLogicalName,
    updateStateValue.Label.LocalizedLabels[0].Label
    );
```

 No puede agregar o quitar las opciones de `StateCode`, pero puede cambiar las etiquetas para las opciones.  
  
<a name="BKMK_InsertNewOptionLocalOptionSet"></a>

## <a name="insert-a-new-option-in-a-local-option-set"></a>Insertar una opción nueva en un conjunto de opciones local.

 Este código de ejemplo muestra cómo agregar una nueva opción a un conjunto de opciones local. El siguiente ejemplo usa <xref:Microsoft.Xrm.Sdk.Messages.InsertOptionValueRequest> para agregar una opción nueva a un atributo personalizado de <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata> para la entidad de `Contact`.  

```csharp
// Create a request.
InsertOptionValueRequest insertOptionValueRequest =
    new InsertOptionValueRequest
{
    AttributeLogicalName = "new_picklist",
    EntityLogicalName = Contact.EntityLogicalName,
    Label = new Label("New Picklist Label", _languageCode)
};

// Execute the request.
int insertOptionValue = ((InsertOptionValueResponse)_serviceProxy.Execute(
    insertOptionValueRequest)).NewOptionValue;

Console.WriteLine("Created {0} with the value of {1}.",
    insertOptionValueRequest.Label.LocalizedLabels[0].Label,
    insertOptionValue);
```

<a name="BKMK_ChangeOrderOptionLocalOptionSet"></a>

## <a name="change-the-order-of-options-in-a-local-option-set"></a>Cambiar el orden de las opciones en un conjunto de opciones local

 Este código de ejemplo muestra cómo cambiar el orden de las opciones de un conjunto de opciones local. El siguiente ejemplo recupera un atributo <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata>de cliente y cambia el orden de las opciones originales usando la [Order By](https://msdn.microsoft.com/library/system.linq.enumerable.orderby.aspx)**LINQ**función para ordenar los artículos en orden ascendente por la etiqueta de texto.  Después usa <xref:Microsoft.Xrm.Sdk.Messages.OrderOptionRequest> para establecer el nuevo pedido de las opciones para el atributo.  
  
 Use la función [OrderByDecending](https://msdn.microsoft.com/library/system.linq.enumerable.orderbydescending.aspx) linq para ordenar los artículos por orden descendente.  

```csharp
// Use the RetrieveAttributeRequest message to retrieve  
// a attribute by it's logical name.
RetrieveAttributeRequest retrieveAttributeRequest =
    new RetrieveAttributeRequest
{
    EntityLogicalName = Contact.EntityLogicalName,
    LogicalName = "new_picklist",
    RetrieveAsIfPublished = true
};

// Execute the request.
RetrieveAttributeResponse retrieveAttributeResponse =
    (RetrieveAttributeResponse)_serviceProxy.Execute(
    retrieveAttributeRequest);

// Access the retrieved attribute.
PicklistAttributeMetadata retrievedPicklistAttributeMetadata =
    (PicklistAttributeMetadata)
    retrieveAttributeResponse.AttributeMetadata;

// Get the current options list for the retrieved attribute.
OptionMetadata[] optionList =
    retrievedPicklistAttributeMetadata.OptionSet.Options.ToArray();

// Change the order of the original option's list.
// Use the OrderBy (OrderByDescending) linq function to sort options in  
// ascending (descending) order according to label text.
// For ascending order use this:
var updateOptionList =
    optionList.OrderBy(x => x.Label.LocalizedLabels[0].Label).ToList();

// For descending order use this:
// var updateOptionList =
//      optionList.OrderByDescending(
//      x => x.Label.LocalizedLabels[0].Label).ToList();

// Create the request.
OrderOptionRequest orderOptionRequest = new OrderOptionRequest
{
    // Set the properties for the request.
    AttributeLogicalName = "new_picklist",
    EntityLogicalName = Contact.EntityLogicalName,
    // Set the changed order using Select linq function 
    // to get only values in an array from the changed option list.
    Values = updateOptionList.Select(x => x.Value.Value).ToArray()
};

// Execute the request
_serviceProxy.Execute(orderOptionRequest);

Console.WriteLine("Option Set option order changed");
```

<a name="BKMK_DeleteAttribute"></a>

## <a name="delete-an-attribute"></a>Eliminar un atributo

 Este ejemplo muestra como eliminar atributos almacenados en una `List<`<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>`>`que fue creada por la`Contact`entidad en [Crear Atributos](#BKMK_CreateAttributes). Para cada <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> el <xref:Microsoft.Xrm.Sdk.Messages.DeleteAttributeRequest> prepara la solicitud que se procesa mediante <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>.  

```csharp
// Delete all attributes created for this sample.
foreach (AttributeMetadata anAttribute in addedAttributes)
{
    // Create the request object
    DeleteAttributeRequest deleteAttribute = new DeleteAttributeRequest
    {
        // Set the request properties 
        EntityLogicalName = Contact.EntityLogicalName,
        LogicalName = anAttribute.SchemaName
    };
    // Execute the request
    _serviceProxy.Execute(deleteAttribute);
}
```
