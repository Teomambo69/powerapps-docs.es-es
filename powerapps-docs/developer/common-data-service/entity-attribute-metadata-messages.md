---
title: Mensajes de metadatos de atributos de entidad (Common Data Service para aplicaciones) | MicrosoftDocs
description: 'Acerca de los mensajes usados para editar los metadatos de atributos de entidad, también conocidos como propiedades o campos.'
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
# <a name="entity-attribute-metadata-messages"></a>Mensajes de metadatos de atributos de entidad

<!-- 
Was Mike Carter
https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/entity-attribute-metadata-messages -->

Un atributo de entidad es un contenedor para un grupo de datos en una entidad. Los términos *atributo* y *propiedad* (propiedad de clase) se usan indistintamente con el término *atributo de entidad*. Las aplicaciones basadas en modelos utilizan el término *campo* para referirse a atributos de entidad.  

> [!NOTE]
> Es posible crear y actualizar atributos de entidad mediante la API web. Vea [Crear atributos](webapi/create-update-entity-definitions-using-web-api.md#create-attributes) para obtener más detalles.

## <a name="entity-attribute-messages"></a>Mensajes de atributos de entidad  
 La siguiente tabla muestra los mensajes que puede usar para realizar acciones en atributos de entidad.  
  
|Mensaje|Operación de la API web|Ensamblado del SDK|   
|-------------|-----------------|-----------------|  
|CreateAttribute</br></br>Crear atributos de entidad|PUBLICAR en la propiedad de navegación valorada como colección de los atributos de EntityMetadata con la definición JSON del atributo. Más información: [Crear atributos](webapi/create-update-entity-definitions-using-web-api.md#create-attributes)|<xref:Microsoft.Xrm.Sdk.Messages.CreateAttributeRequest>| 
|DeleteAttribute</br></br>Eliminar atributos de entidad|ELIMINAR la dirección URL del atributo.|<xref:Microsoft.Xrm.Sdk.Messages.DeleteAttributeRequest>|  
|DeleteOptionValue</br></br>Eliminar una opción de los atributos <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata> o <xref:Microsoft.Xrm.Sdk.Metadata.StatusAttributeMetadata>.|<xref href="Microsoft.Dynamics.CRM.DeleteOptionValue?text=DeleteOptionValue Action" />|<xref:Microsoft.Xrm.Sdk.Messages.DeleteOptionValueRequest>|  
|InsertOptionValue</br></br>Agregar una opción a un atributo de <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata>.|<xref href="Microsoft.Dynamics.CRM.InsertOptionValue?text=InsertOptionValue Action" />|<xref:Microsoft.Xrm.Sdk.Messages.InsertOptionValueRequest>|Agregar una opción a un atributo de <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata>.|  
|InsertStatusValue</br></br>Agregar una opción a un atributo de <xref:Microsoft.Xrm.Sdk.Metadata.StatusAttributeMetadata>.|<xref href="Microsoft.Dynamics.CRM.InsertStatusValue?text=InsertStatusValue Action" />|<xref:Microsoft.Xrm.Sdk.Messages.InsertStatusValueRequest>|  |Cambia el orden de las opciones presentadas en un atributo de <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata>.|<xref href="Microsoft.Dynamics.CRM.OrderOption?text=OrderOption Action" />|<xref:Microsoft.Xrm.Sdk.Messages.OrderOptionRequest>|  
|RetrieveAttribute</br></br>Recuperar atributos de entidad|Utilice la consulta de la API web que se menciona en [Consultar atributos EntityMetadata](webapi/query-metadata-web-api.md#bkmk_queryAttributesexample) para recuperar los atributos de entidad.|<xref:Microsoft.Xrm.Sdk.Messages.RetrieveAttributeRequest>|  
|UpdateAttribute</br></br>Actualizar atributos de entidad|Consulte [Actualizar entidades](webapi/create-update-entity-definitions-using-web-api.md#update-entities)|<xref:Microsoft.Xrm.Sdk.Messages.UpdateAttributeRequest>|  
|UpdateStateValue</br></br>Actualizar una etiqueta para un atributo de <xref:Microsoft.Xrm.Sdk.Metadata.StateAttributeMetadata>|<xref href="Microsoft.Dynamics.CRM.UpdateStateValue?text=UpdateStateValue Action" />|<xref:Microsoft.Xrm.Sdk.Messages.UpdateStateValueRequest>|  

### <a name="see-also"></a>Vea también  

[Metadatos del atributo](entity-attribute-metadata.md)<br />
[Crear atributo de numeración automática](create-auto-number-attributes.md)<br />
<!-- TODO: [Work with Attributes](org-service/work-attribute-metadata.md)<br />
[Sample: Work with Attributes](org-service/sample-work-attribute-metadata.md) -->