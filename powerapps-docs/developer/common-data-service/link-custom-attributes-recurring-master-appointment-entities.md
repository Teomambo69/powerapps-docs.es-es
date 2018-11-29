---
title: Vincular atributos personalizados de cita periódica maestra y entidades de cita (Common Data Service para aplicaciones) | Microsoft Docs
description: Vincular los atributos personalizados de la entidad RecurringAppointmentMaster con los atributos personalizados de la entidad Appointment para copiar automáticamente los datos.
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
# <a name="link-custom-attributes-of-the-recurring-appointment-master-and-appointment-entities"></a>Vincular los atributos personalizados de las entidades de cita y cita periódica maestra

Puede vincular los atributos personalizados creados para la entidad de `RecurringAppointmentMaster` con los atributos personalizados creados para que la entidad de `Appointment` copie automáticamente los datos del atributo personalizado de la cita periódica maestra en el atributo personalizado vinculado de las instancias de cita periódica, cada vez que se expande.  
  
 Existe una asignación 1:1 entre los atributos personalizados, lo que implica que un atributo personalizado de la entidad de cita periódica maestra puede vincularse con solo un atributo personalizado de la entidad de cita. Además, los atributos personalizados que se vincularán de manera conjunta deben ser del mismo tipo. Por ejemplo, no puede vincular un atributo personalizado de tipo `string` con un atributo personalizado de `decimal`. Para obtener información sobre los diferentes tipos de atributos, consulte [Personalizar los metadatos de los atributos de entidad](/dynamics365/customer-engagement/developer/customize-entity-attribute-metadata).  
  
> [!NOTE]
>  No puede vincular atributos personalizados que tienen la *seguridad de nivel de campo* habilitada. Asimismo, no puede habilitar la seguridad de nivel de campo para atributos personalizados vinculados.  
  
### <a name="link-custom-attributes"></a>Vincular atributos personalizados  
  
1. Cree un atributo personalizado para la entidad cita que usa la clase <xref:Microsoft.Xrm.Sdk.Messages.CreateAttributeRequest>.  
  
2. Crear un atributo personalizado para la entidad de serie de citas periódicas (cita periódica maestra). Cuando especifique los metadatos del atributo para el atributo personalizado, use la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.LinkedAttributeId> para vincularla al atributo personalizado que creó en el paso 1.  
  
3. Publique los cambios en la solución.  
  
   Para ver el código de ejemplo, consulte [Ejemplo: Vincular atributos personalizados entre series e instancias](org-service/samples/link-custom-attributes-between-series-instances.md).  
  
### <a name="see-also"></a>Vea también

 [Entidades de cita periódica](/dynamics365/customer-engagement/developer/recurring-appointment-entities)   
 [Entidad RecurringAppointmentMaster](/reference/entities/recurringappointmentmaster.md)   
 [Ejemplo: Vincular atributos personalizados entre series e instancias](org-service/samples/link-custom-attributes-between-series-instances.md)   
 [Personalizar metadatos de atributos de entidad](/dynamics365/customer-engagement/developer/customize-entity-attribute-metadata)
