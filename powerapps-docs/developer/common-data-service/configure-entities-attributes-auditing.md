---
title: Configurar entidades y atributos para la auditoría (Common Data Service) | Microsoft Docs
description: Explica los requisitos de configuración para habilitar y deshabilitar la auditoría de entidades y sus atributos.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="configure-entities-and-attributes-for-auditing"></a>Configurar entidades y atributos para auditoría

Hay tres niveles donde la auditoría se puede configurar: organización, entidad y atributo. El nivel de la organización es el nivel nivel más alto, seguido del nivel de la entidad y, por último, el nivel del atributo. Para que se efectúe la auditoría de atributos, esta debe estar habilitada a nivel de atributo, entidad y organización. Para que se efectúe la auditoría de entidades, esta debe estar habilitada a nivel de entidad y organización.  
  
 Existe una ligera diferencia en cómo se habilita o deshabilita la auditoría para una organización en comparación con una entidad o un atributo. La auditoría se habilita o deshabilita a nivel de organización mediante el establecimiento de un valor de atributo en particular del registro de la organización. Sin embargo, para las entidades y atributos, define un valor de propiedad de los metadatos de la entidad o del atributo.  
  
 Es necesario asignar el rol de administrador o personalizador del sistema a un usuario para habilitar o deshabilitar la auditoría.  
  
## <a name="enabling-auditing"></a>Habilitar la auditoría  

 Mediante el ajuste de la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAuditEnabled> de los metadatos de una entidad y la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.IsAuditEnabled> de los metadatos de cada atributo deseado en `true`, los cambios de datos en los registros de estas entidades pueden ser registrados por la plataforma. Sin embargo, al habilitar la auditoría de una entidad, todos los atributos de la entidad se habilitan para realizar la auditoría de forma predeterminada. Por supuesto puede deshabilitar explícitamente la auditoría en alguno o todos los atributos según sea necesario. La propiedad <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAuditEnabled> puede establecerse cuando los metadatos de la entidad o el atributo se crean o actualizan a través de las siguientes solicitudes: <xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest>, <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest>, <xref:Microsoft.Xrm.Sdk.Messages.CreateAttributeRequest>, <xref:Microsoft.Xrm.Sdk.Messages.UpdateAttributeRequest>.  
  
 Después de cambiar los metadatos del atributo de la entidad, debe publicar la entidad mediante <xref:Microsoft.Crm.Sdk.Messages.PublishXmlRequest>. Cambiar la propiedad de <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAuditEnabled> a nivel de entidad no requiere efectuar la publicación. Normalmente, la personalización y la publicación son realizadas por el mismo usuario. Sin embargo, si estas tareas son realizadas por distintos usuarios, la auditoría registrará la acción de publicación, el usuario que inició la operación de publicación y no la acción de actualización.  
  
 Además, la auditoría se activa a nivel de organización mediante el ajuste del valor del atributo <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAuditEnabled> del registro de la organización de destino en `true`.  
  
## <a name="disabling-auditing"></a>Deshabilitar la auditoría  
 Para deshabilitar la auditoría, simplemente ajuste <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAuditEnabled>, tal y como se describe anteriormente, en `false`. Publique las personalizaciones de la entidad si ha deshabilitado la auditoría en algún atributo. Puede deshabilitar la auditoría para una organización completa ajustando el atributo <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAuditEnabled> en `false` en el registro de la organización de destino.  
  
## <a name="entities-that-can-be-audited"></a>Entidades que se pueden auditar  
 Todas las entidades personalizadas y las más personalizables se pueden auditar. Para ver una lista con las entidades que puede personalizar, consulte [¿Qué entidades se pueden personalizar?](/dynamics365/customer-engagement/developer/which-entities-are-customizable).  
  
 En la siguiente tabla se enumeran las entidades no personalizables que no se pueden auditar. Esta tabla se obtuvo probando un valor de atributo de `CanModifyAuditSettings` de `false` en los metadatos de cada entidad.  
  
||  
|-|  
|ActivityPointer|  
|Anotación|  
|BulkOperation|  
|Calendario|  
|CalendarRule|  
|CustomerOpportunityRole|  
|Descuento|  
|DiscountType|  
|IncidentResolution|  
|KbArticle|  
|KbArticleComment|  
|KbArticleTemplate|  
|Notificación|  
|OpportunityClose|  
|OrderClose|  
|ProductPriceLevel|  
|QuoteClose|  
|RecurrenceRule|  
|Recurso|  
|ResourceGroup|  
|ResourceGroupExpansion|  
|ResourceSpec|  
|SalesLiteratureItem|  
|SalesProcessInstance|  
|Service|  
|Asunto|  
|Plantilla|  
|Unidad de medida|  
|UoMSchedule|  
|Flujo de trabajo|  
|WorkflowLog|  
  
### <a name="see-also"></a>Vea también  
 [Administración de datos en Dynamics 365](/dynamics365/customer-engagement/developer/manage-data)   
 [Cambios de los datos de la entidad de auditoría](/dynamics365/customer-engagement/developer/audit-entity-data-changes)   
 [Recuperar y eliminar el historial de cambios de datos auditados](retrieve-and-delete-the-history-of-audited-data-changes.md)   
 [Ejemplo: Auditar cambios de datos de entidad](/dynamics365/customer-engagement/developer/sample-audit-entity-data-changes)   
 [Auditar cambios de datos en Dynamics 365](/dynamics365/customer-engagement/developer/audit-entity-data-changes)