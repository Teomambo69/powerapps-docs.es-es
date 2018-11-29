---
title: Mensajes de metadatos de relaciones entre entidades (Common Data Service para aplicaciones) | MicrosoftDocs
description: 'El artículo describe los mensajes que se pueden usar para crear, recuperar, actualizar y eliminar relaciones entre entidades con la API web y el servicio de la organización.'
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
# <a name="entity-relationship-metadata-messages"></a>Mensajes de metadatos de relación entre entidades

Las relaciones de entidades definen cómo se relacionan las entidades entre ellas. Incluye información sobre cómo se representan las relaciones en la aplicación. Además, cuando las acciones se ejecutan en un registro, la relación indica las acciones que realizar en registros relacionados.  
  
La siguiente tabla muestra los mensajes que se pueden usar para crear, recuperar, actualizar y eliminar relaciones entre entidades.  
  
|API web|Servicio de organización|Descripción|  
|-------------|-------------|-----------------|  
|Solicitud `POST` basada en la entidad `RelationshipDefinitions`. <br/>Más información: [Creación de una relación de varios a varios](webapi/create-update-entity-relationships-using-web-api.md#create-a-many-to-many-relationship). |<xref:Microsoft.Xrm.Sdk.Messages.CreateManyToManyRequest>|Crea una relación varios a varios entre dos entidades.|  
|Solicitud `POST` basada en la entidad `RelationshipDefinitions`. <br/>Más información: [Creación de una relación de uno a varios](webapi/create-update-entity-relationships-using-web-api.md#create-a-one-to-many-relationship).|<xref:Microsoft.Xrm.Sdk.Messages.CreateOneToManyRequest>|Crea una relación uno a varios entre dos entidades.|  
|Solicitud `DELETE` basada en la entidad `RelationshipDefinitions`.<br/>Más información: [Eliminación de relaciones](webapi/create-update-entity-relationships-using-web-api.md#delete-relationships)|<xref:Microsoft.Xrm.Sdk.Messages.DeleteRelationshipRequest>|Elimina una relación entre entidades.|  
|Solicitud `GET` basada en la entidad `RelationshipDefinitions`.|<xref:Microsoft.Xrm.Sdk.Messages.RetrieveRelationshipRequest>|Recupera una relación entre entidades.|  
|Solicitud `PUT` basada en la entidad `RelationshipDefinitions`.<br/>Más información: [Actualización de relaciones](webapi/create-update-entity-relationships-using-web-api.md#update-relationships)|<xref:Microsoft.Xrm.Sdk.Messages.UpdateRelationshipRequest>|Actualiza una relación entre entidades.|  
  
### <a name="see-also"></a>Vea también  

 [Idoneidad de la relación entre entidades](entity-relationship-eligibility.md)   
 [Configuración del comportamiento en cascada de las relaciones entre entidades](configure-entity-relationship-cascading-behavior.md)