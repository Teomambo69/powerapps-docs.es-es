---
title: Crear y recuperar la relación de entidad (Common Data Service) | Microsoft Docs
description: Muestra ejemplos de códigos para crear y recuperar relaciones entre entidades.
ms.custom: ''
ms.date: 01/28/2020
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
ms.openlocfilehash: 228ddbab089d695ff22ff2d954aa1e10d6270931
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156020"
---
# <a name="create-and-retrieve-entity-relationships"></a>Crear y recuperar relaciones entre entidades

Este tema muestra cómo crear y recuperar relaciones entre entidades. Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CreateRetrieveEntityRelationships).
  
<a name="BKMK_Create1NEntityRelationship"></a>   

## <a name="create-a-1n-entity-relationship"></a>Crear una relación de 1:N entre entidades  

 El siguiente ejemplo usa el método [EligibleCreateOneToManyRelationship](#eligiblecreateonetomanyrelationship) para comprobar que las entidades `Account` y `Campaign` puedan participar en una relación de 1:N entre entidades y luego crea la relación entre entidades con <xref:Microsoft.Xrm.Sdk.Messages.CreateOneToManyRequest>.  
  
```csharp
bool eligibleCreateOneToManyRelationship =
    EligibleCreateOneToManyRelationship("account", "campaign");

if (eligibleCreateOneToManyRelationship)
{
    CreateOneToManyRequest createOneToManyRelationshipRequest =
        new CreateOneToManyRequest
    {
        OneToManyRelationship =
        new OneToManyRelationshipMetadata
        {
            ReferencedEntity = "account",
            ReferencingEntity = "campaign",
            SchemaName = "new_account_campaign",
            AssociatedMenuConfiguration = new AssociatedMenuConfiguration
            {
                Behavior = AssociatedMenuBehavior.UseLabel,
                Group = AssociatedMenuGroup.Details,
                Label = new Label("Account", 1033),
                Order = 10000
            },
            CascadeConfiguration = new CascadeConfiguration
            {
                Assign = CascadeType.NoCascade,
                Delete = CascadeType.RemoveLink,
                Merge = CascadeType.NoCascade,
                Reparent = CascadeType.NoCascade,
                Share = CascadeType.NoCascade,
                Unshare = CascadeType.NoCascade
            }
        },
        Lookup = new LookupAttributeMetadata
        {
            SchemaName = "new_parent_accountid",
            DisplayName = new Label("Account Lookup", 1033),
            RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
            Description = new Label("Sample Lookup", 1033)
        }
    };


    CreateOneToManyResponse createOneToManyRelationshipResponse =
        (CreateOneToManyResponse)service.Execute(
        createOneToManyRelationshipRequest);

    _oneToManyRelationshipId =
        createOneToManyRelationshipResponse.RelationshipId;
    _oneToManyRelationshipName = 
        createOneToManyRelationshipRequest.OneToManyRelationship.SchemaName;

    Console.WriteLine(
        "The one-to-many relationship has been created between {0} and {1}.",
        "account", "campaign");
}
```
  
<a name="BKMK_EligibleCreateOneToManyRelationship"></a>   

### <a name="eligiblecreateonetomanyrelationship"></a>EligibleCreateOneToManyRelationship  

 El siguiente ejemplo crea un método de `EligibleCreateOneToManyRelationship` que usa <xref:Microsoft.Xrm.Sdk.Messages.CanBeReferencedRequest> y <xref:Microsoft.Xrm.Sdk.Messages.CanBeReferencingRequest> para comprobar si dos entidades pueden participar en una relación de 1:N entre entidades.  
  
```csharp
/// <summary>
/// Determines whether two entities are eligible to participate in a relationship
/// </summary>
/// <param name="referencedEntity">Primary Entity</param>
/// <param name="referencingEntity">Referencing Entity</param>
/// <returns></returns>
public bool EligibleCreateOneToManyRelationship(string referencedEntity, 
    string referencingEntity)
{
    //Checks whether the specified entity can be the primary entity in one-to-many
    //relationship.
    CanBeReferencedRequest canBeReferencedRequest = new CanBeReferencedRequest
    {
        EntityName = referencedEntity
    };

    CanBeReferencedResponse canBeReferencedResponse =
        (CanBeReferencedResponse)service.Execute(canBeReferencedRequest);

    if (!canBeReferencedResponse.CanBeReferenced)
    {
        Console.WriteLine(
            "Entity {0} can't be the primary entity in this one-to-many relationship", 
            referencedEntity);
    }

    //Checks whether the specified entity can be the referencing entity in one-to-many
    //relationship.
    CanBeReferencingRequest canBereferencingRequest = new CanBeReferencingRequest
    {
        EntityName = referencingEntity
    };

    CanBeReferencingResponse canBeReferencingResponse =
        (CanBeReferencingResponse)service.Execute(canBereferencingRequest);

    if (!canBeReferencingResponse.CanBeReferencing)
    {
        Console.WriteLine(
            "Entity {0} can't be the referencing entity in this one-to-many relationship", 
            referencingEntity);
    }


    if (canBeReferencedResponse.CanBeReferenced == true
        && canBeReferencingResponse.CanBeReferencing == true)
    {
        return true;
    }
    else
    {
        return false;
    }
}
```
  
<a name="BKMK_CreateNNEntityRelationship"></a>   

## <a name="create-an-nn-entity-relationship"></a>Crear una relación de N:N entre entidades  

 El siguiente ejemplo usa un método [EligibleCreateManyToManyRelationship](#BKMK_EligibleCreateManyToManyRelationship) para comprobar que las entidades `Account` y `Campaign` puedan participar en una relación de N:N entre entidades y luego crea la relación entre entidades con <xref:Microsoft.Xrm.Sdk.Messages.CreateManyToManyRequest>.  
  
```csharp
bool accountEligibleParticipate =
    EligibleCreateManyToManyRelationship("account");
bool campaignEligibleParticipate =
    EligibleCreateManyToManyRelationship("campaign");

if (accountEligibleParticipate && campaignEligibleParticipate)
{

    CreateManyToManyRequest createManyToManyRelationshipRequest =
        new CreateManyToManyRequest
    {
        IntersectEntitySchemaName = "new_accounts_campaigns",
        ManyToManyRelationship = new ManyToManyRelationshipMetadata
        {
            SchemaName = "new_accounts_campaigns",
            Entity1LogicalName = "account",
            Entity1AssociatedMenuConfiguration =
            new AssociatedMenuConfiguration
            {
                Behavior = AssociatedMenuBehavior.UseLabel,
                Group = AssociatedMenuGroup.Details,
                Label = new Label("Account", 1033),
                Order = 10000
            },
            Entity2LogicalName = "campaign",
            Entity2AssociatedMenuConfiguration =
            new AssociatedMenuConfiguration
            {
                Behavior = AssociatedMenuBehavior.UseLabel,
                Group = AssociatedMenuGroup.Details,
                Label = new Label("Campaign", 1033),
                Order = 10000
            }
        }
    };

    CreateManyToManyResponse createManytoManyRelationshipResponse =
        (CreateManyToManyResponse)service.Execute(
        createManyToManyRelationshipRequest);


    _manyToManyRelationshipId =
        createManytoManyRelationshipResponse.ManyToManyRelationshipId;
    _manyToManyRelationshipName =
        createManyToManyRelationshipRequest.ManyToManyRelationship.SchemaName;

    Console.WriteLine(
        "The many-to-many relationship has been created between {0} and {1}.",
        "account", "campaign");
}
```
  
<a name="BKMK_EligibleCreateManyToManyRelationship"></a>   

### <a name="eligiblecreatemanytomanyrelationship"></a>EligibleCreateManyToManyRelationship  

 El siguiente ejemplo crea un método de `EligibleCreateManyToManyRelationship` que usa <xref:Microsoft.Xrm.Sdk.Messages.CanManyToManyRequest> para comprobar si una entidad puede participar en una relación de N:N entre entidades.  
  
```csharp
/// <summary>
/// Determines whether the entity can participate in a many-to-many relationship.
/// </summary>
/// <param name="entity">Entity</param>
/// <returns></returns>
public bool EligibleCreateManyToManyRelationship(string entity)
{
    CanManyToManyRequest canManyToManyRequest = new CanManyToManyRequest
    {
        EntityName = entity
    };

    CanManyToManyResponse canManyToManyResponse =
        (CanManyToManyResponse)service.Execute(canManyToManyRequest);

    if (!canManyToManyResponse.CanManyToMany)
    {
        Console.WriteLine(
            "Entity {0} can't participate in a many-to-many relationship.", 
            entity);
    }

    return canManyToManyResponse.CanManyToMany;
}
```
  
<a name="BKMK_RetrieveEntityRelationships"></a>   
## <a name="retrieve-entity-relationships"></a>Recuperar relaciones entre entidades  
 El siguiente ejemplo recupera las dos relaciones entre entidades creadas anteriormente con <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRelationshipRequest>. El primer ejemplo usa `MetadataId` y el segundo usa `Name`.  
  
```csharp
//You can use either the Name or the MetadataId of the relationship.

//Retrieve the One-to-many relationship using the MetadataId.
RetrieveRelationshipRequest retrieveOneToManyRequest =
    new RetrieveRelationshipRequest { MetadataId = _oneToManyRelationshipId };
RetrieveRelationshipResponse retrieveOneToManyResponse =
    (RetrieveRelationshipResponse)service.Execute(retrieveOneToManyRequest);

Console.WriteLine("Retrieved {0} One-to-many relationship by id", retrieveOneToManyResponse.RelationshipMetadata.SchemaName);

//Retrieve the Many-to-many relationship using the Name.
RetrieveRelationshipRequest retrieveManyToManyRequest =
    new RetrieveRelationshipRequest { Name = _manyToManyRelationshipName};
RetrieveRelationshipResponse retrieveManyToManyResponse =
    (RetrieveRelationshipResponse)service.Execute(retrieveManyToManyRequest);

Console.WriteLine("Retrieved {0} Many-to-Many relationship by Name", retrieveManyToManyResponse.RelationshipMetadata.MetadataId);
```
  
### <a name="see-also"></a>Vea también  
 
 [Mensajes de metadatos de relación entre entidades](../entity-relationship-metadata-messages.md)   
