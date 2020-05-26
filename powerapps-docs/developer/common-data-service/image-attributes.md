---
title: Atributos de imagen (Common Data Service) | Microsoft Docs
description: Obtenga información sobre los atributos de imagen que almacenan datos de imagen, atributos de soporte, recuperando datos de imagen y cargando datos de imagen.
ms.custom: ''
ms.date: 04/27/2020
ms.reviewer: pehecke
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
ms.openlocfilehash: 924fb17728ff1681bcba3d4dd60dc6723156694e
ms.sourcegitcommit: 9f83d4c09f09256493bc5d49c7b4a4fc02d9342a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2020
ms.locfileid: "3293009"
---
# <a name="image-attributes"></a>Atributos de imagen

Algunas entidades del sistema y todas las entidades personalizadas admiten imágenes. Esas entidades que admiten imágenes pueden contener una miniatura y una imagen principal de tamaño completo. La imagen en miniatura se puede ver en la aplicación web al ver los datos del formulario de la entidad. Puede haber varios atributos de imagen múltiples en una instancia de entidad pero únicamente puede haber una imagen principal. Sin embargo, puede cambiar la imagen principal de una imagen a otra estableciendo [IsPrimaryImage](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.metadata.imageattributemetadata.isprimaryimage?view=dynamics-general-ce-9#Microsoft_Xrm_Sdk_Metadata_ImageAttributeMetadata_IsPrimaryImage) para ese atributo en `true`. Cada atributo de imagen de tamaño completo está limitada a 30 MB de tamaño. El <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName> del atributo de imagen de entidad es `EntityImage`. Más información: [Imágenes de entidad](/dynamics365/customer-engagement/developer/introduction-entities#entity-images).

Las imágenes en miniatura y los metadatos de las imágenes se almacenan en Common Data Service, que incluye la información necesaria para recuperar la imagen completa. Las imágenes completas se almacenan en el almacenamiento de archivos en el blob de Azure para reducir el consumo de almacenamiento de datos.

API web (REST) | .NET API (SOAP) 
------- | -------
[ImageAttributeMetadata](/dynamics365/customer-engagement/web-api/imageattributemetadata) | <xref:Microsoft.Xrm.Sdk.Metadata.ImageAttributeMetadata>
IsPrimaryImage, MaxHeight, MaxWidth | [IsPrimaryImage](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.metadata.imageattributemetadata.isprimaryimage?view=dynamics-general-ce-9#Microsoft_Xrm_Sdk_Metadata_ImageAttributeMetadata_IsPrimaryImage), [MaxHeight](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.metadata.imageattributemetadata.maxheight?view=dynamics-general-ce-9), [MaxWidth](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.metadata.imageattributemetadata.maxwidth?view=dynamics-general-ce-9)

Además de atributos de imagen, las entidades personalizadas admiten cero o más atributos de archivo que pueden contener datos de cualquier archivo. Estos atributos de archivo pueden contener una cantidad mucho mayor de datos que atributos de imagen. Para obtener más información, vea [Editar atributos](file-attributes.md).

> [!NOTE]
> En <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy.SdkClientVersion> 9.0.45.329 o superior y la API web versión 9.1 o superior se admiten la capacidad de almacenar más de un atributo de imagen en una instancia de entidad, el almacenamiento de datos de imagen en un blob de Azure, un tamaño máximo de imagen de 30 MB y atributos de archivo.

<a name="BKMK_SupportingAttributes"></a>   
## <a name="supporting-attributes"></a>Atributos compatibles  
 Cuando se agrega un atributo de imagen a una entidad, se crean algunos atributos adicionales para darle soporte.  
  
### <a name="entityimage_timestamp-attribute"></a>Atributo EntityImage_Timestamp  
 Nombre del tipo de atributo: `BigIntType`  
  
 El valor representa el momento en que la imagen se actualizó por última vez y se usa para asegurarse de que la versión más reciente de la imagen se descarga y se almacena en caché en el cliente.  
  
### <a name="entityimage_url-attribute"></a>Atributo EntityImage_URL  
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

### <a name="maxsizeinkb-attribute"></a>Atributo MaxSizeInKB

 Este valor representa el tamaño máximo (en kilobytes) de los datos de imagen que el atributo puede contener. Establezca este valor en el tamaño de datos más pequeño que pueda usar para su aplicación específica. Vea la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.ImageAttributeMetadata.MaxSizeInKB> para el límite de tamaño permisible y el valor predeterminado.

### <a name="canstorefullimage-attribute"></a>Atributo CanStoreFullImage

 Este valor indica si un atributo de imagen puede almacenar una imagen completa. Vea la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.ImageAttributeMetadata.CanStoreFullImage>.

<a name="BKMK_RetrievingImages"></a>   
## <a name="retrieve-image-data"></a>Recuperar datos de imagen  

Para descargar los datos del atributo de imagen en miniatura, use las API siguientes.

API web (REST) | .NET API (SOAP)
------- | -------
GET /api/data/v9.1/\<entity-type(id)\>/\<image-attribute-name\>/$value   | <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> o <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest>

 > [!NOTE]
> Cuando use <xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> o <xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*>, `EntityImage` no se incluye cuando la propiedad <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>.`AllColumns` se establece en `true`. Debido al tamaño que pueden alcanzar los datos de este atributo, para devolver este atributo debe solicitarlo explícitamente.

Las transferencias de datos de imagen desde extremos de servicio web están limitadas a un máximo de 16 MB de datos en una sola llamada de servicio. Los datos de imagen más grandes que la cantidad se deben dividir en bloques de datos de 4 MB o más pequeños (fragmentos) donde cada bloque se recibe en una llamada API independiente hasta que se hayan recibido todos los datos de imagen. Es responsabilidad suya unir los bloques de datos descargados para formar la imagen completa combinando los bloques de datos en la misma secuencia en que se recibieron.

 Más información sobre fragmentos: [Atributos de archivo](file-attributes.md).

Para descargar los datos del atributo de imagen completa, use las API siguientes.

API web (REST) | .NET API (SOAP)
------- | -------
 ninguna  | <xref:Microsoft.Crm.Sdk.Messages.InitializeFileBlocksDownloadRequest>
GET /api/data/v9.1/\<entity-type(id)\>/\<image-attribute-name\>/$value?size=full   | <xref:Microsoft.Crm.Sdk.Messages.DownloadBlockRequest>

Tenga en cuenta que en este caso la descarga del atributo de imagen usa las solicitudes de mensajes de atributo de archivo. 

### <a name="example-rest-thumbnail-download"></a>Ejemplo: descarga de miniatura REST

**Solicitud**
```http
GET [Organization URI]/api/data/v9.1/accounts(b9ccec62-f266-e911-8196-000d3a6de638)/myentityimage/$value

Headers:
Content-Type: application/octet-stream
```

**Respuesta**
```http
204 No Content

Body:
byte[]
```

### <a name="example-rest-full-image-download-16mb"></a>Ejemplo: Descarga de imagen completa REST (<=16MB)

**Solicitud**
```http
GET [Organization URI]/api/data/v9.1/accounts(C0864F1C-0B71-E911-8196-000D3A6D09B3)/myentityimage/$value?size=full

Headers:
Content-Type: application/octet-stream
```
**Respuesta**
```http
204 No Content

Body:
byte[]

Response Headers:
x-ms-file-name: "sample.png"
x-ms-file-size: 12345
```

En el ejemplo anterior, el parámetro de cadena de consulta `size=full` indica descargar la imagen completa. El nombre de archivo y el tamaño se proporcionarán en los encabezados de respuesta.

### <a name="example-rest-full-image-download-16mb"></a>Ejemplo: Descarga de imagen completa REST (>16MB)

**Solicitud**
```http
GET [Organization URI]/api/data/v9.1/accounts(C0864F1C-0B71-E911-8196-000D3A6D09B3)/myentityimage/$value?size=full

Header:
Range: bytes=0-1023/8192
```
**Respuesta**
```http
206 Partial Content

Body:
byte[]

Response Headers:
x-ms-file-name: "sample.png"
x-ms-file-size: 8192
Location: api/data/v9.1/accounts(id)/myentityimage?FileContinuationToken
```
En el ejemplo anterior, el encabezado **Intervalo** indica la primera descarga en fragmentos de 1024 bytes para una imagen que tiene 8192 bytes en total.
  
<a name="BKMK_UploadingImages"></a>   
## <a name="upload-image-data"></a>Carga de datos de imagen  
 Para actualizar las imágenes, establezca el valor del atributo de imagen en una matriz de bits que contenga el contenido del archivo de imagen. Las imágenes en miniatura se recortan y ajustan de tamaño en un cuadrado de 144x144 píxeles por el servicio web para reducir el tamaño de los datos antes de guardarlos. La reducción de tamaño sigue estas reglas:
  
- Las imágenes que tengan al menos un lado de más de 144 píeles se recortan en el centro a 144x144.  
  
- Las imágenes que tengan ambos lados con menos de 144 píxeles se recortarán con forma de cuadrado cuyo lado coincide con la dimensión más pequeña.  
  
  En la siguiente tabla se muestran dos ejemplos.  
  
|Antes|Después|  
|------------|-----------|  
|![Imagen antes de cambio de tamaño](media/crm-itpro-cust-imagebeforeresize.png "Imagen antes de cambio de tamaño")<br /><br /> 300x428|![imagen después de cambiar el tamaño](media/crm-itpro-cust-imageafterresize.jpg "imagen después de cambiar el tamaño")<br /><br /> 144x144|  
|![Segunda ejemplo de cambio de tamaño de imagen](media/crm-itpro-cust-imagebeforeresizeexample2.png "Segunda ejemplo de cambio de tamaño de imagen")<br /><br /> 91x130|![segundo ejemplo de cambio de tamaño](media/crm-itpro-cust-imageafterresizeexample2.jpg "segundo ejemplo de cambio de tamaño")<br /><br /> 91x91|

Para cargar datos de imagen iguales o inferiores a 16 MB de tamaño, use las API siguientes.

API web (REST) | .NET API (SOAP)
------- | -------
PUT o PATCH /api/data/v9.1/\<entity-type(id)\>/\<image-attribute-name\>   | <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> o <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>

Las transferencias de datos de imagen desde extremos de servicio web están limitadas a un máximo de 16 MB de datos en una sola llamada de servicio. Los datos de imagen más grandes que la cantidad se deben dividir en bloques de datos de 4 MB o más pequeños (fragmentos) donde cada bloque se carga en una llamada API independiente hasta que se hayan recibido todos los datos de imagen. Es su responsabilidad dividir los datos de imagen en bloques de hasta 4MB de tamaño y cargarlos en la secuencia correcta.

 Más información sobre fragmentos: [Atributos de archivo](file-attributes.md).

Para cargar datos de imagen de más de 16 MB de tamaño, use las API siguientes.

API web (REST) | .NET API (SOAP)
------- | -------
ninguna   | <xref:Microsoft.Crm.Sdk.Messages.InitializeFileBlocksUploadRequest>
PATCH /api/data/v9.1/\<entity-type(id)\>/\<image-attribute-name\>   | <xref:Microsoft.Crm.Sdk.Messages.UploadBlockRequest>
ninguna   | <xref:Microsoft.Crm.Sdk.Messages.CommitFileBlocksUploadRequest>

También utilizar las solicitudes de mensaje de bloque Initialize/Upload/Commit para un atributo de imagen <=16MB de tamaño (en lugar de solicitudes de mensaje Create/Update) si fragmenta los datos de imagen.

### <a name="example-rest-full-image-upload-16mb"></a>Ejemplo: Carga de imagen completa REST (<=16MB)

**Solicitud**
```http
PUT [Organization URI]/api/data/v9.1/accounts(C0864F1C-0B71-E911-8196-000D3A6D09B3)/myentityimage

Header:
Content-Type: application/octet-stream
x-ms-file-name: sample.png

Body:
byte[]
```
Una vez completada la carga, una imagen en miniatura es creada automáticamente por el servicio web. 

### <a name="example-rest-upload-with-chunking-first-request"></a>Ejemplo: Carga de REST con fragmentación (primera solicitud)

**Solicitud**
```http
PATCH [Organization URI]/api/data/v9.1/accounts(id)/myentityimage

Headers:
x-ms-transfer-mode: chunked
x-ms-file-name: sample.png
```

**Respuesta**
```http
Response:
200 OK

Response Headers:
x-ms-chunk-size: 4096
Accept-Ranges: bytes 
Location: api/data/v9.1/accounts(id)/myentityimage?FileContinuationToken
```
En el ejemplo anterior, el encabezado `x-ms-transfer-mode: chunked` indica una carga fragmentada.
 
### <a name="example-rest-upload-with-chunking-next-request"></a>Ejemplo: Carga de REST con fragmentación (siguiente solicitud)

**Solicitud**
```http
PATCH [Organization URI]/api/data/v9.1/accounts(id)/myentityimage?FileContinuationToken

Headers:
Content-Range: bytes 0-4095/8192
Content-Type: application/octet-stream
x-ms-file-name: sample.png

Body:
byte[]
```

**Respuesta**
```http
204 No Content
```
En la solicitud anterior, el siguiente bloque de datos está siendo cargado. Después de que todos los datos de imagen han sido recibidos por el servicio web, una imagen en miniatura es creada automáticamente por el servicio web.

### <a name="see-also"></a>Vea también  
[Atributos de archivo](file-attributes.md)  
[Introducción a las entidades en Dynamics 365](/dynamics365/customer-engagement/developer/introduction-entities)   
[Introducción a los atributos de entidad en Dynamics 365](/dynamics365/customer-engagement/developer/introduction-entity-attributes)   
[Ejemplo: establecer y recuperar imágenes de entidad](/dynamics365/customerengagement/on-premises/developer/sample-set-retrieve-entity-images)
