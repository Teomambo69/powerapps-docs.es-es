---
title: Actividades personalizadas (Common Data Service) | Microsoft Docs
description: Las actividades personalizadas admiten las necesidades de comunicación de una empresa como la mensajería instantánea (IM) y el servicio de mensajes cortos (SMS) en Dynamics 365.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ee86c88222c0385f1fec8458af6ee9d2cfeabf18
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749716"
---
# <a name="custom-activities"></a>Actividades personalizadas

En Common Data Service, puede crear actividades personalizadas para satisfacer las necesidades de comunicación de una empresa como mensajería instantánea (IM) y servicio de mensajes cortos (SMS). Para crear una actividad personalizada en Common Data Service, crear una entidad personalizada, y especificarla como una entidad de actividad utilizando el <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsActivity>. .  
  
 Sin embargo, al contrario que otras entidades personalizadas, no puede especificar un atributo primario para una actividad personalizada porque, de forma predeterminada, cada actividad personalizada debe tener un atributo primario llamado "Asunto".  
  
 Cuando crea una entidad de actividad personalizada, todas las propiedades y privilegios de la entidad `activitypointer` se heredan para la actividad personalizada. Además, todos los tipos del grupo de actividad están disponibles para la actividad personalizada y, por consiguiente, las propiedades correspondientes también se heredan.  
  
 Puede crear relaciones de 1:N (uno a varios) para una actividad personalizada de la misma forma que para cualquier otra actividad. Puede, además, actualizar relaciones existentes.  
  
## <a name="privileges-and-access-rights"></a>Privilegios y derechos de acceso 
 
 Se requiere el mismo conjunto de privilegios y derechos de acceso de Common Data Service para trabajar con actividades personalizadas como los necesarios para trabajar con entidades personalizadas. Para obtener más información acerca de las entidades personalizadas, vea [Personalizar metadatos de entidad](customize-entity-metadata.md).  
  
## <a name="creating-a-custom-activity"></a>Creación de una actividad personalizada  
 Para crear una entidad de actividad personalizada, establezca los valores de las propiedades enumeradas en la tabla siguiente.  
  
|Nombre de propiedad|Valor|Notas|  
|-------------------|-----------|-----------|  
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsActivity>|`true`|Especifique la entidad personalizada como una entidad de actividad.|  
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAvailableOffline>|`true`|Una entidad de actividad personalizada debe tener disponibilidad sin conexión.|  
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsMailMergeEnabled>|`false`|Una entidad de actividad personalizada no puede tener habilitada la combinación de correspondencia.|  
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.OwnershipType>|<xref:Microsoft.Xrm.Sdk.Metadata.OwnershipTypes>. TeamOwned<br />o<br /><xref:Microsoft.Xrm.Sdk.Metadata.OwnershipTypes>. UserOwned|Una entidad de actividad personalizada puede ser propiedad de un usuario o un equipo.|  
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ActivityTypeMask>|0 - Ninguna<br />o<br />1 – Actividad de comunicación|(Opcional) Especifique si una actividad personalizada debe aparecer en los menús de la actividad en la aplicación web.<br /><br /> -   Especifique **0 (ninguna)** para evitar que aparezca en los menús de actividad. La actividad personalizada aparecerá en las cuadrículas asociadas sólo de esas entidades con las que esté asociada (tiene relación).<br />-   Especifique **1 (actividad de comunicación)** para que aparezca en los menús de actividad.<br /><br /> Si no especifica esta propiedad, la actividad personalizada se crea con el valor de propiedad predeterminado: 1. Es decir, la actividad personalizada está disponible en los menús de actividad. Por otro lado, `ActivityTypeMask` se puede establecer en el momento de creación de la actividad solo, y una vez establecido, no se puede editar.|  
|<xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest>.<xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest.HasActivities>|`false`|Una entidad de actividad personalizada no debe tener una relación con actividades.|  
|<xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest>.<xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest.HasNotes>|`true`|Una entidad de actividad personalizada debe tener una relación con notas.|  
|<xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest>. <xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest.PrimaryAttribute>|<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName> es “Asunto”.|El nombre de esquema de `PrimaryAttribute` para todas las actividades debe ser "Asunto".|  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo muestra cómo se puede crear una actividad personalizada.  
  
```csharp
String prefix = "new_";

String customEntityName = prefix + "instantmessage";

// Create the custom activity entity.
CreateEntityRequest request = new CreateEntityRequest
{
    HasNotes = true,
    HasActivities = false,
    PrimaryAttribute = new StringAttributeMetadata
    {
        SchemaName = "Subject",
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
        MaxLength = 100,
        DisplayName = new Label("Subject", 1033)
    },
    Entity = new EntityMetadata
    {
        IsActivity = true,
        SchemaName = customEntityName,
        DisplayName = new Label("Instant Message", 1033),
        DisplayCollectionName = new Label("Instant Messages", 1033),
        OwnershipType = OwnershipTypes.UserOwned,
        IsAvailableOffline = true,

    }
};

_serviceProxy.Execute(request);

//Entity must be published
``` 

### <a name="see-also"></a>Vea también  
 [Entidades de actividad](activity-entities.md)   
 [Entidad ActivityPointer (actividad)](activitypointer-activity-entity.md)   
 [Ejemplo: crear una actividad personalizada](/dynamics365/customer-engagement/developer/sample-create-custom-activity)   
 [Ejemplo: crear y actualizar metadatos de entidad](/dynamics365/customer-engagement/developer/org-service/sample-create-update-entity-metadata)