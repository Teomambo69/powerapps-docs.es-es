---
title: Idoneidad de las relaciones entre entidades (Common Data Service para aplicaciones) | MicrosoftDocs
description: En el artículo se enumeran los mensajes que puede usar para determinar si las entidades pueden participar en relaciones entre entidades.
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
---
# <a name="entity-relationship-eligibility"></a>Idoneidad de la relación entre entidades

Antes de crear una relación entre entidades, debe comprobar si la entidad puede participar en la relación. En la siguiente tabla se enumeran los mensajes que puede usar para determinar si las entidades pueden participar en relaciones entre entidades.  
  
|Mensaje|Operación de la API web|Ensamblado del SDK|  
|-------------|-----------------|----------------|  
|CanBeReferenced</br>Comprueba si la entidad especificada puede ser la entidad principal (uno) en una relación de uno a varios.|<xref href="Microsoft.Dynamics.CRM.CanBeReferenced?text=CanBeReferenced Action" />|<xref:Microsoft.Xrm.Sdk.Messages.CanBeReferencedRequest>|  
|CanBeReferencing</br>Comprueba si la entidad especificada puede ser la entidad de referencia (varios) en una relación de uno a varios.|<xref href="Microsoft.Dynamics.CRM.CanBeReferencing?text=CanBeReferencing Action" />|<xref:Microsoft.Xrm.Sdk.Messages.CanBeReferencingRequest>|  
|CanManyToMany</br>Comprueba si la entidad puede participar en una relación de varios a varios.|<xref href="Microsoft.Dynamics.CRM.CanManyToMany?text=CanManyToMany Action" />|<xref:Microsoft.Xrm.Sdk.Messages.CanManyToManyRequest>|  
|GetValidManyToMany</br>Devuelve el conjunto de entidades que puede participar en una relación varios a varios.|<xref href="Microsoft.Dynamics.CRM.GetValidManyToMany?text=GetValidManyToMany Function" />|<xref:Microsoft.Xrm.Sdk.Messages.GetValidManyToManyRequest>|  
|GetValidReferencedEntities</br>Devuelve el conjunto de entidades que son válidas como entidad principal (una) de la entidad especificada en una relación uno a varios.|<xref href="Microsoft.Dynamics.CRM.GetValidReferencedEntities?text=GetValidReferencedEntities Function" />|<xref:Microsoft.Xrm.Sdk.Messages.GetValidReferencedEntitiesRequest>|  
|GetValidReferencingEntities</br>Devuelve el conjunto de entidades que son válidas como la entidad relacionada (varias) de la entidad especificada en una relación uno a varios.|<xref href="Microsoft.Dynamics.CRM.GetValidReferencingEntities?text=GetValidReferencingEntities Function" />|<xref:Microsoft.Xrm.Sdk.Messages.GetValidReferencingEntitiesRequest>|  
  
### <a name="see-also"></a>Vea también  
 [Personalizar metadatos de relación entre entidades](/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)   
 [Ampliar el modelo de metadatos de Dynamics 365](/dynamics365/customer-engagement/developer/org-service/use-organization-service-metadata)   
 [Metadatos de relación entre entidades](/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)   
 [Mensajes de relaciones entre entidades](entity-relationship-metadata-messages.md)   
 [Comportamiento de las relaciones entre entidades](/dynamics365/customer-engagement/developer/entity-relationship-behavior)   
 [Crear una relación de 1:N entre entidades](/dynamics365/customer-engagement/developer/org-service/create-retrieve-entity-relationships#BKMK_Create1NEntityRelationship)   
 [Crear una relación de N:N entre entidades](/dynamics365/customer-engagement/developer/org-service/create-retrieve-entity-relationships#BKMK_CreateNNEntityRelationship)
