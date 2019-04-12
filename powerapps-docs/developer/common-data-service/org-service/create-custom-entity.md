---
title: Crear una entidad personalizada (Common Data Service) | MicrosoftDocs
description: Muestra cómo mediante programación se crea una entidad personalizada en Common Data Service.
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
# <a name="create-custom-entity"></a>Crear entidad personalizada

En este tema se muestra cómo crear mediante programación una entidad personalizada propiedad del usuario llamada **Cuenta bancaria** y agregar cuatro tipos diferentes de atributos a la misma.  
  
También puede crear entidades personalizadas propiedad de la organización. Más información: [Propiedad de entidad](/dynamics365/customer-engagement/developer/introduction-entities#entity-ownership).  
  
> [!NOTE]
>  No podrá ver esta entidad al navegar por la aplicación a menos que se establezcan las propiedades de entidad que se modifican para establecer **Áreas que muestran esta entidad**.  
  
<a name="BKMK_CreateCustomEntity"></a>   

## <a name="create-a-custom-entity"></a>Crear una entidad personalizada  

 En el siguiente ejemplo usa la <xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest> para crear la entidad y <xref:Microsoft.Xrm.Sdk.Metadata.StringAttributeMetadata><xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest.PrimaryAttribute>.  
  
 El valor `_customEntityName` es “new_bankaccount”.  
  
```csharp
CreateEntityRequest createrequest = new CreateEntityRequest
{

 //Define the entity
 Entity = new EntityMetadata
 {
  SchemaName = _customEntityName,
  DisplayName = new Label("Bank Account", 1033),
  DisplayCollectionName = new Label("Bank Accounts", 1033),
  Description = new Label("An entity to store information about customer bank accounts", 1033),
  OwnershipType = OwnershipTypes.UserOwned,
  IsActivity = false,

 },

 // Define the primary attribute for the entity
 PrimaryAttribute = new StringAttributeMetadata
 {
  SchemaName = "new_accountname",
  RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
  MaxLength = 100,
  FormatName = StringFormatName.Text,
  DisplayName = new Label("Account Name", 1033),
  Description = new Label("The primary attribute for the Bank Account entity.", 1033)
 }

};
_serviceProxy.Execute(createrequest);
Console.WriteLine("The bank account entity has been created.");
```  
  
<a name="BKMK_AddStringAttribute"></a>   

## <a name="add-a-string-attribute-to-the-custom-entity"></a>Agregar un atributo de cadena a la entidad personalizada  

En el siguiente ejemplo se agrega un atributo <xref:Microsoft.Xrm.Sdk.Metadata.StringAttributeMetadata> a la entidad `Bank Account`.  
  
```csharp
CreateAttributeRequest createBankNameAttributeRequest = new CreateAttributeRequest
{
 EntityName = _customEntityName,
 Attribute = new StringAttributeMetadata
 {
  SchemaName = "new_bankname",
  RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
  MaxLength = 100,
  FormatName = StringFormatName.Text,
  DisplayName = new Label("Bank Name", 1033),
  Description = new Label("The name of the bank.", 1033)
 }
};

_serviceProxy.Execute(createBankNameAttributeRequest);
```
  
<a name="BKMK_AddMoneyAttribute"></a>   

## <a name="add-a-money-attribute-to-the-custom-entity"></a>Agregar un atributo monetario a la entidad personalizada  

 En el siguiente ejemplo se agrega un atributo <xref:Microsoft.Xrm.Sdk.Metadata.MoneyAttributeMetadata> a la entidad `Bank Account`.  
  
```csharp
CreateAttributeRequest createBalanceAttributeRequest = new CreateAttributeRequest
{
 EntityName = _customEntityName,
 Attribute = new MoneyAttributeMetadata
 {
  SchemaName = "new_balance",
  RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
  PrecisionSource = 2,
  DisplayName = new Label("Balance", 1033),
  Description = new Label("Account Balance at the last known date", 1033),

 }
};

_serviceProxy.Execute(createBalanceAttributeRequest);

```  
  
<a name="BKMK_AddDateTimeAttribute"></a>   

## <a name="add-a-datetime-attribute-to-the-custom-entity"></a>Agregar un atributo de fecha y hora a la entidad personalizada  

En el siguiente ejemplo se agrega un atributo <xref:Microsoft.Xrm.Sdk.Metadata.DateTimeAttributeMetadata> a la entidad `Bank Account`.  
  
```csharp
CreateAttributeRequest createCheckedDateRequest = new CreateAttributeRequest
{
 EntityName = _customEntityName,
 Attribute = new DateTimeAttributeMetadata
 {
  SchemaName = "new_checkeddate",
  RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
  Format = DateTimeFormat.DateOnly,
  DisplayName = new Label("Date", 1033),
  Description = new Label("The date the account balance was last confirmed", 1033)

 }
};

_serviceProxy.Execute(createCheckedDateRequest);
Console.WriteLine("An date attribute has been added to the bank account entity.");
```
  
<a name="BKMK_AddLookupAttribute"></a>
   
## <a name="add-a-lookup-attribute-to-the-custom-entity"></a>Agregar un atributo de búsqueda a la entidad personalizada 
 
 En el siguiente ejemplo se usa <xref:Microsoft.Xrm.Sdk.Messages.CreateOneToManyRequest> para crear una relación de uno a varios con la entidad `Contact` para agregar un atributo <xref:Microsoft.Xrm.Sdk.Metadata.LookupAttributeMetadata> a la entidad `Bank Account`.  
  
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
  
### <a name="see-also"></a>Vea también  
 [Utilizar el ejemplo IOrganizationService y el código auxiliar](/dynamics365/customer-engagement/developer/use-sample-helper-code)   
 <xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest>   
 [Personalizar metadatos de entidad](../customize-entity-metadata.md)   
 [¿Qué entidades se pueden personalizar?](/dynamics365/customer-engagement/developer/which-entities-are-customizable)   
 [Recuperar, actualizar y eliminar entidades](/dynamics365/customer-engagement/developer/retrieve-update-delete-entities)   
 [Crear y actualizar una entidad que se puede enviar por correo electrónico](/dynamics365/customer-engagement/developer/create-update-entity-emailed)   
 [Crear una entidad de actividad personalizada](/dynamics365/customer-engagement/developer/create-custom-activity-entity)   
 [Cambiar iconos de entidades](/dynamics365/customer-engagement/developer/modify-icons-entity)   
 [Cambiar mensajes de entidades](/dynamics365/customer-engagement/developer/modify-messages-entity)
