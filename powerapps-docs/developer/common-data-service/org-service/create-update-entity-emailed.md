---
title: Crear y actualizar una entidad para enviar actividades de correo electrónico a registros (Common Data Service) | Microsoft Docs
description: Aprenda a crear una entidad que contenga una dirección de correo electrónico que pueda usar para enviar actividades de correo electrónico a los registros de la entidad.
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
ms.openlocfilehash: b5a33e558747eb605ffed08025c3681134666093
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156100"
---
# <a name="create-and-update-an-entity-to-send-email-activities-to-records"></a>Crear y actualizar una entidad para enviar actividades de correo electrónico a registros

Puede crear una entidad que contenga una dirección de correo electrónico que pueda usar para enviar actividades de correo electrónico a los registros de la entidad.  
  
 El código de ejemplo siguiente crea una entidad personalizada y define la propiedad de <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsActivityParty> en `true`. También crea un atributo <xref:Microsoft.Xrm.Sdk.Metadata.StringAttributeMetadata> mediante <xref:Microsoft.Xrm.Sdk.Metadata.StringFormatName>.`Email` Para proporcionar una dirección de correo electrónico a usar.  
  
 Incluso si agrega otros atributos <xref:Microsoft.Xrm.Sdk.Metadata.StringAttributeMetadata> con el formato de una dirección de correo electrónico, sólo se usa el primero especificado.  

```csharp
// Create the custom entity.
CreateEntityRequest createrequest = new CreateEntityRequest
{
    // Define an entity to enable for emailing. In order to do so,
    // IsActivityParty must be set.
    Entity = new EntityMetadata
    {
        SchemaName = _customEntityName,
        DisplayName = new Label("Agent", 1033),
        DisplayCollectionName = new Label("Agents", 1033),
        Description = new Label("Insurance Agents", 1033),
        OwnershipType = OwnershipTypes.UserOwned,
        IsActivity = false,

        // Unless this flag is set, this entity cannot be party to an
        // activity.
        IsActivityParty = true
    },

    // As with built-in emailable entities, the Primary Attribute will
    // be used in the activity party screens. Be sure to choose descriptive
    // attributes.
    PrimaryAttribute = new StringAttributeMetadata
    {
        SchemaName = "new_fullname",
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
        MaxLength = 100,
        FormatName = StringFormatName.Text,
        DisplayName = new Label("Agent Name", 1033),
        Description = new Label("Agent Name", 1033)
    }
};

_serviceProxy.Execute(createrequest);
Console.WriteLine("The emailable entity has been created.");

// The entity will not be selectable as an activity party until its customizations
// have been published. Otherwise, the e-mail activity dialog cannot find
// a correct default view.
PublishAllXmlRequest publishRequest = new PublishAllXmlRequest();
_serviceProxy.Execute(publishRequest);

// Before any emails can be created for this entity, an Email attribute
// must be defined.
CreateAttributeRequest createFirstEmailAttributeRequest = new CreateAttributeRequest
{
    EntityName = _customEntityName,
    Attribute = new StringAttributeMetadata
    {
        SchemaName = "new_emailaddress",
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
        MaxLength = 100,
        FormatName = StringFormatName.Email,
        DisplayName = new Label("Email Address", 1033),
        Description = new Label("Email Address", 1033)
    }
};

_serviceProxy.Execute(createFirstEmailAttributeRequest);
Console.WriteLine("An email attribute has been added to the emailable entity.");

// Create a second, alternate email address. Since there is already one 
// email attribute on the entity, this will never be used for emailing
// even if the first one is not populated.
CreateAttributeRequest createSecondEmailAttributeRequest = new CreateAttributeRequest
{
    EntityName = _customEntityName,
    Attribute = new StringAttributeMetadata
    {
        SchemaName = "new_secondaryaddress",
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
        MaxLength = 100,
        FormatName = StringFormatName.Email,
        DisplayName = new Label("Secondary Email Address", 1033),
        Description = new Label("Secondary Email Address", 1033)
    }
};

_serviceProxy.Execute(createSecondEmailAttributeRequest);

Console.WriteLine("A second email attribute has been added to the emailable entity.");
```

### <a name="see-also"></a>Vea también

[Crear entidades con el servicio de la organización](entity-operations-create.md)  
[Actualizar y eliminar entidades con el servicio de la organización](entity-operations-update-delete.md)
