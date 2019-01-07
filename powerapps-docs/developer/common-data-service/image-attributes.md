---
title: Atributos de imagen (Common Data Service para aplicaciones) | Microsoft Docs
description: 'Obtenga información sobre los atributos de la imagen que incluyen datos de la imagen con la aplicación y sobre los atributos de soporte, la recuperación de datos de la imagen y la carga de datos de la imagen.'
ms.custom: ''
ms.date: 11/26/2018
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
# <a name="image-attributes"></a>Atributos de imagen

Los registros de entidad que incluyen datos de imagen proporcionan una experiencia única dentro de la aplicación. Como programador, usted necesita comprender cómo trabaja con datos de imagen.  
  
 Sólo determinadas entidades del sistema y las entidades personalizadas admiten imágenes. Para obtener información acerca de qué entidades del sistema admiten imágenes, consulte [Imágenes de entidad](/dynamics365/customer-engagement/developer/introduction-entities.md#entity-images).  
  
<a name="BKMK_SupportingAttributes"></a>   
## <a name="supporting-attributes"></a>Atributos compatibles  
 Para las entidades que admitan atributos de imagen, el atributo <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName> de la entidad de imagen siempre es `EntityImage`. Cuando se agrega un atributo de imagen a una entidad, se crean algunos atributos adicionales para darle soporte.  
  
> [!NOTE]
>  Los clientes que no usan los ensamblados actuales de .NET deben incluir <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy.SdkClientVersion> con un valor de ‘6.0.0.0’ o posterior para recibir los atributos de <xref:Microsoft.Xrm.Sdk.Metadata.ImageAttributeMetadata>. Más información: <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy.SdkClientVersion>.  
  
### <a name="entityimagetimestamp-attribute"></a>Atributo EntityImage_Timestamp  
 Nombre del tipo de atributo: `BigIntType`  
  
 El valor representa el momento en que la imagen se actualizó por última vez y se usa para asegurarse de que la versión más reciente de la imagen se descarga y se almacena en caché en el cliente.  
  
### <a name="entityimageurl-attribute"></a>Atributo EntityImage_URL  
 Nombre del tipo de atributo: `StringType`  
  
 Dirección URL absoluta para mostrar la imagen de la entidad en un cliente.  
  
 La dirección URL se compone de lo siguiente:  
  
```http  
{0}/image/download.aspx?entity={1}&attribute={2}&id={3}&timestamp={4}
```  
  
- 0: la URL de la organización  
  
- 1: el nombre lógico de la entidad  
  
- 2: el nombre lógico del atributo  
  
- 3: el valor de EntityImageId.  
  
- 4: El valor de EntityImage_Timestamp  
  
  Por ejemplo:   
  `https://myorg.crm.dynamics.com/image/download.aspx?attribute=entityimage&entity=contact&id={ECB6D3DF-4A04-E311-AFE0-00155D9C3020}&timestamp=635120312218444444`  
  
### <a name="entityimageid"></a>EntityImageId  
 Nombre del tipo de atributo: `UniqueIdentifierType`  
  
 El identificador único de la imagen.  
  
<a name="BKMK_RetrievingImages"></a>   
## <a name="retrieving-image-data"></a>Recuperar datos de imagen  
 Cuando use <xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> o <xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*> `EntityImage` no se incluye cuando <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>.`AllColumns` se establece en true. Debido al tamaño que pueden alcanzar los datos de este atributo, para devolver este atributo debe solicitarlo explícitamente.  
  
 Los datos binarios que representan la imagen no se devuelven con la clase obsoleta <xref:Microsoft.Crm.Sdk.Messages.ExecuteFetchRequest>. Debe usar <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> en su lugar.  
  
 Más información: [Ejemplo: establecer y recuperar imágenes de entidad](/dynamics365/customer-engagement/developer/sample-set-retrieve-entity-images).  
  
<a name="BKMK_UploadingImages"></a>   
## <a name="uploading-image-data"></a>Carga de datos de imagen  
 Para actualizar las imágenes, establezca el valor de `EntityImage` en un `byte[]` que contenga el contenido del archivo. Todas las imágenes se muestran en un cuadrado de 144x144 píxeles. Las imágenes se recortarán y se redimensionarán para reducir el tamaño de los datos antes de guardarlos.  
  
- Las imágenes que tengan al menos un lado de más de 144 píeles se recortan en el centro a 144x144.  
  
- Las imágenes que tengan ambos lados con menos de 144 píxeles se recortarán con forma de cuadrado cuyo lado coincide con la dimensión más pequeña.  
  
  En la siguiente tabla se muestran dos ejemplos.  
  
|Antes|Después|  
|------------|-----------|  
|![Imagen antes del cambio de tamaño](media/crm-itpro-cust-imagebeforeresize.png "Imagen antes del cambio de tamaño")<br /><br /> 300x428|![Imagen después del cambio de tamaño](media/crm-itpro-cust-imageafterresize.jpg "Imagen después del cambio de tamaño")<br /><br /> 144x144|  
|![Segundo ejemplo de cambio de tamaño de la imagen](media/crm-itpro-cust-imagebeforeresizeexample2.png "Segundo ejemplo de cambio de tamaño de la imagen")<br /><br /> 91x130|![Segundo ejemplo de cambio de tamaño](media/crm-itpro-cust-imageafterresizeexample2.jpg "Segundo ejemplo de cambio de tamaño")<br /><br /> 91x91|  
  
 Más información: [Ejemplo: establecer y recuperar imágenes de entidad](/dynamics365/customer-engagement/developer/sample-set-retrieve-entity-images.md).  
  
### <a name="see-also"></a>Vea también  
 [Introducción a las entidades en Dynamics 365](/dynamics365/customer-engagement/developer/introduction-entities)   
 [Introducción a los atributos de entidad en Dynamics 365](/dynamics365/customer-engagement/developer/introduction-entity-attributes)   
 [Ejemplo: establecer y recuperar imágenes de entidad](/dynamics365/customer-engagement/developer/sample-set-retrieve-entity-images.md)
