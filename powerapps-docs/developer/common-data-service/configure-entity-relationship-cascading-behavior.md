---
title: Configurar el comportamiento en cascada de las relaciones entre entidades (Common Data Service) | MicrosoftDocs
description: Configure comportamientos en cascada para una relación entre entidades de uno a varios en Common Data Service para preservar la integridad de los datos y automatizar los procesos de negocio.
services: ''
suite: powerapps
documentationcenter: na
author: mayadumesh
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/31/2018
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="configure-entity-relationship-cascading-behavior"></a>Configuración del comportamiento en cascada de las relaciones entre entidades  

 Puede configurar los comportamientos en cascada para una relación entre entidades de uno a varios para preservar la integridad de los datos y automatizar los procesos de negocio. La API web y el servicio de la organización son compatibles con la configuración del comportamiento en cascada.

## <a name="using-web-api-to-configure-cascading-behavior"></a>Uso de la API web para configurar el comportamiento en cascada

Si trabaja con la API web, puede definir una a varias relaciones de uno a varios usando <xref href="Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata?text=OneToManyRelationshipMetadata EntityType" />. Esta definición incluye el nombre de la entidad de intersección que se creará así como la forma en que la relación debería mostrarse en la aplicación utilizando <xref href="Microsoft.Dynamics.CRM.AssociatedMenuConfiguration?text=AssociatedMenuConfiguration ComplexType" />, <xref href="Microsoft.Dynamics.CRM.Label?text=Label ComplexType" /> y <xref href="Microsoft.Dynamics.CRM.LocalizedLabel?text=LocalizedLabel ComplexType" />. 

Más información: [Crear una relación de uno a varios mediante la API web](webapi/create-update-entity-relationships-using-web-api.md#create-a-one-to-many-relationship).

## <a name="using-organization-service-to-configure-cascading-behavior"></a>Uso del servicio de organización para configurar el comportamiento en cascada

Cuando se usa <xref:Microsoft.Xrm.Sdk.Messages.CreateOneToManyRequest> o <xref:Microsoft.Xrm.Sdk.Messages.UpdateRelationshipRequest>, se incluye una instancia de una clase <xref:Microsoft.Xrm.Sdk.Metadata.OneToManyRelationshipMetadata> en el cuerpo de la solicitud. En la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.OneToManyRelationshipMetadata.CascadeConfiguration> de esa clase, se usa la clase <xref:Microsoft.Xrm.Sdk.Metadata.CascadeConfiguration>.  

La clase `CascadeConfiguration` (<xref:Microsoft.Xrm.Sdk.Metadata.CascadeConfiguration> o <xref href="Microsoft.Dynamics.CRM.CascadeConfiguration?text=CascadeConfiguration ComplexType" />) contiene las propiedades que representan las acciones que se pueden realizar en la entidad a la que se hace referencia en la relación de uno a varios entre entidades. A cada propiedad se le puede asignar uno de los valores de <xref href="Microsoft.Dynamics.CRM.CascadeType?text=CascadeType EnumType" />.  

|Value|Etiqueta de aplicación|Descripción|  
|-----------|-----------------------|-----------------|  
|Active|Poner activa en cascada|Realizar la acción en todos los registros de entidad de referencia activos asociados con el registro de entidad al que se hace referencia.|  
|Cascada|Poner todas en cascada|Realizar la acción en todos los registros de entidad de referencia asociados con el registro de entidad al que se hace referencia.|  
|NoCascade|No poner ninguna en cascada|No hacer nada.|  
|RemoveLink|Quitar vínculo|Quitar el valor del atributo de referencia de todos los registros de entidad de referencia asociados con el registro de entidad al que se hace referencia.|  
|Restringir|Restringir|Impedir que el registro de entidad de referencia se elimine cuando existen entidades de referencia.|  
|UserOwned|Poner en cascada las que pertenecen al usuario|Realizar la acción en todos los registros de entidad de referencia que pertenecen al mismo usuario que el registro de entidad de referencia.|  
  
 La clase `CascadeConfiguration` (<xref:Microsoft.Xrm.Sdk.Metadata.CascadeConfiguration> o <xref href="Microsoft.Dynamics.CRM.CascadeConfiguration?text=CascadeConfiguration ComplexType" />) contiene las siguientes propiedades que representan las acciones que se pueden realizar en la entidad a la que se hace referencia en la relación de uno a varios entre entidades.  
  
|Acción|Descripción|Opciones válidas|  
|------------|-----------------|-------------------|  
|Asignar|Se cambia el propietario del registro de entidad al que se hace referencia.|Active<br />Cascada<br />NoCascade<br />UserOwned|  
|Eliminar|Se elimina el registro de entidad al que se hace referencia. **Nota:** Las opciones para esta acción son limitadas.|Cascada<br />RemoveLink<br />Restringir|  
|Combinar|El registro se combina con otro registro. **Nota:** Para las entidades a las que se referencia que se pueden combinar, la única opción válida es Cascade. En otros casos, use NoCascade.|Cascada<br />NoCascade|  
|Cambiar primario|Consulte [Acerca de la acción de cambiar primario](#about-the-reparent-action) más adelante.|Active<br />Cascada<br />NoCascade<br />UserOwned|  
|Compartir|Cuando el registro de entidad al que se hace referencia se comparte con otro usuario.|Active<br />Cascada<br />NoCascade<br />UserOwned|  
|Dejar de compartir|Cuando se quita el uso compartido del registro de entidad al que se hace referencia.|Active<br />Cascada<br />NoCascade<br />UserOwned|  
  
<a name="BKMK_ReparentAction"></a>   
### <a name="about-the-reparent-action"></a>Acerca de la acción de cambiar primario  
 La acción de cambiar primario es muy similar a la acción de compartir, pero se ocupa de los derechos de acceso de lectura heredados en lugar de los derechos de acceso de lectura explícitos. La acción de cambiar primario es cuando se cambia el valor del atributo de referencia en una relación jerárquica. Cuando se produce una acción de cambiar primario, es posible que el ámbito deseado de los derechos de acceso de lectura heredados para las entidades relacionadas cambie. Las acciones en cascada relacionadas con la acción de cambiar primario hacen referencia a los cambios realizados en los derechos de acceso de lectura para el registro de entidad y cualquier registro de entidad relacionado con él.  

### <a name="see-also"></a>Vea también

[Metadatos de relaciones entre entidades](entity-relationship-metadata.md)  

