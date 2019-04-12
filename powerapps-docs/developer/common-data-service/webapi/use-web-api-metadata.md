---
title: Usar la API web con metadatos (Common Data Service) | Microsoft Docs
description: La sección proporciona instrucciones sobre cómo usar la API web con los tipos de entidad incluidos en la referencia EntityType de metadatos de la API web.
ms.custom: ''
ms.date: 11/04/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: a0edc029-c6db-48ac-9538-b0270fe94440
caps.latest.revision: 10
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-the-web-api-with-metadata"></a>Usar la API web con metadatos

Puede realizar cualquier operación de metadatos con la API web que puede realizar mediante el servicio de la organización. Esta sección proporciona instrucciones sobre cómo usar la API web con los tipos de entidad incluidos en <xref:Microsoft.Dynamics.CRM.MetadataEntityTypeIndex>.  
  
 Hay cuatro rutas del conjunto de entidades expuestas para realizar operaciones con las entidades de metadatos como se describe en la siguiente tabla.  
  
|Ruta del conjunto de entidades|Descripción|  
|---------------------|-----------------|  
|*[URI de organización]*/api/data/v9.0/EntityDefinitions|Contiene entidades <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" />.|  
|*[URI de organizacón]*/api/data/v9.0/RelationshipDefinitions|Contiene <xref href="Microsoft.Dynamics.CRM.ManyToManyRelationshipMetadata?text=ManyToManyRelationshipMetadata EntityType" /> y <xref href="Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata?text=OneToManyRelationshipMetadata EntityType" /> ya que ambas se heredan de <xref href="Microsoft.Dynamics.CRM.RelationshipMetadataBase?text=RelationshipMetadataBase EntityType" />.|  
|*[URI de organización]*/api/data/v9.0/GlobalOptionSetDefinitions|Contiene entidades <xref href="Microsoft.Dynamics.CRM.BooleanOptionSetMetadata?text=BooleanOptionSetMetadata EntityType" /> y <xref href="Microsoft.Dynamics.CRM.OptionSetMetadata?text=OptionSetMetadata EntityType" /> definidas globalmente ya que ambas se heredan de <xref href="Microsoft.Dynamics.CRM.OptionSetMetadata?text=OptionSetMetadata EntityType" />.|  
|*[URI de organización]*/api/data/v9.0/ManagedPropertyDefinitions|Solo para uso interno|  
  
Cada tipo de entidad de metadatos usa `MetadataId` como propiedad de identificador único, que se hereda del <xref href="Microsoft.Dynamics.CRM.MetadataBase?text=MetadataBase EntityType" />. Mientras todas las entidades de metadatos tienen una `MetadataId`, no se puede consultar todas ellas directamente. Por ejemplo, puede consultar y realizar operaciones en atributos solo en el contexto de la entidad `EntityMetadata` que los contiene.  
  
Estas entidades tienen algunas diferencias sustanciales respecto de las entidades que almacenan datos de negocios y aplicaciones, por ejemplo:  
  
- Las propiedades de las entidades de metadatos usan muchos de los tipos complejos y de enumeración definidos en <xref:Microsoft.Dynamics.CRM.ComplexTypeIndex> y <xref:Microsoft.Dynamics.CRM.EnumTypeIndex> en lugar de los tipos de datos primitivos usados para las propiedades en las entidades que se heredan de <xref href="Microsoft.Dynamics.CRM.crmbaseentity?text=crmbaseentity EntityType" />.  
  
- Las entidades de metadatos siguen otra convención de nomenclatura y mantienen el estilo de nomenclatura de mayúsculas y minúsculas Pascal usado en los ensamblados del servicio de la organización.  
  
- Los campos de metadatos hacen un uso más extenso de la herencia, lo que requiere que quizá deba realizar conversiones para recuperar los datos que desee.  
  
## <a name="in-this-section"></a>En esta sección 

[Consulta metadatos utilizando la API web](query-metadata-web-api.md)<br />
Puede usar API web para consultar metadatos mediante un estilo de consulta REST.  

[Recuperar metadatos por nombre o identificador de metadatos](retrieve-metadata-name-metadataid.md)<br />
Los aplicaciones pueden adaptarse a los cambios de configuración consultando los metadatos. Cuando conoce una de las propiedades clave de un elemento de metadatos, puede recuperar definiciones de metadatos mediante la API web.  

[Crear y actualizar definiciones de entidad mediante la API web](create-update-entity-definitions-using-web-api.md)<br />
Puede crear y actualizar entidades y atributos mediante la web API para lograr los mismos resultados que obtiene con el servicio de la organización <xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest>, <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest>, <xref:Microsoft.Xrm.Sdk.Messages.CreateAttributeRequest> y <xref:Microsoft.Xrm.Sdk.Messages.UpdateAttributeRequest>.  

[Crear y actualizar relaciones de entidad mediante la API web](create-update-entity-relationships-using-web-api.md)<br />
Puede comprobar si las entidades son elegibles para participar en una relación con otras entidades y luego crear o actualizar esas relaciones con la API web.  

### <a name="see-also"></a>Vea también


<!-- TODO [Metadata and data models](../metadata-data-models.md)<br /> -->
[Examinar los metadatos del entorno](../browse-your-metadata.md)<br />
<!--  TODO [Use the Organization service with Common Data Service metadata](../org-service/use-organization-service-metadata.md)<br /> -->
[Utilizar API Web de Common Data Service](overview.md)
