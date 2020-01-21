---
title: Atributos de archivo (Common Data Service) | Microsoft Docs
description: Obtenga información sobre los atributos de archivo que almacenan datos de archivo en la aplicación, atributos de soporte, recuperación de datos y carga de datos de archivo.
ms.custom: ''
ms.date: 10/04/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: phecke
ms.author: pehecke
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 360194b69e049b7622f1c205c07add069e7f70ba
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "2909113"
---
# <a name="file-attributes"></a>Atributos de archivo

Un atributo de archivo se usa para almacenar datos de archivo hasta un tamaño máximo especificado. Una entidad personalizada o personalizable puede tener cero o más atributos de archivo más una colección de notas (anotación) con cero o un dato adjunto en cada nota. El el <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName> del atributo de archivo es `EntityFile`.

API web (REST) | .NET API (SOAP)
------- | -------
[FieAttributeMetadata](/dynamics365/customer-engagement/web-api/fileattributemetadata) | <xref:Microsoft.Xrm.Sdk.Metadata.FileAttributeMetadata>

Para obtener información sobre los tipos de archivos que no están permitidos, consulte [Pestaña General Configuración del sistema](/power-platform/admin/system-settings-dialog-box-general-tab) en la configuración **Definir las extensiones de archivo bloqueadas para datos adjuntos**.

> [!IMPORTANT]
> Se aplican algunas restricciones al usar el archivo y los tipos de datos de imagen mejorados de Common Data Service. Si están habilitadas claves administradas de cliente (CMK) en el inquilino, los tipos de datos de archivo, imagen e IoT no están disponibles para las organizaciones del inquilino. Las soluciones que contienen tipos de datos excluidos no se instalan. Los clientes deben cancelar la suscripción a CMK para hacer uso de estos tipos de datos.

<!--File data is not passed to plug-ins for performance reasons. You must retrieve the file data in plug-in code using an explicit retrieve call. -->
  
<a name="BKMK_SupportingAttributes"></a>   
## <a name="supporting-attributes"></a>Atributos compatibles  
Cuando se agrega un atributo de archivo a una entidad, se crean algunos atributos adicionales para darle soporte.
  
### <a name="maxsizeinkb-attribute"></a>Atributo MaxSizeInKB

 Este valor representa el tamaño máximo (en kilobytes) de los datos de archivo que el atributo puede contener. Establezca este valor en el tamaño de datos más pequeño que pueda usar para su aplicación específica. Vea la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.FileAttributeMetadata.MaxSizeInKB> para el límite de tamaño permisible y el valor predeterminado.
  
<a name="BKMK_RetrievingFiles"></a>

## <a name="retrieve-file-data"></a>Recuperar datos de archivo
Para recuperar datos de atributo de archivo, use las API siguientes.

API web (REST) | .NET API (SOAP)
------- | -------
 ninguna  | <xref:Microsoft.Crm.Sdk.Messages.InitializeFileBlocksDownloadRequest>,<br/><xref:Microsoft.Crm.Sdk.Messages.InitializeAttachmentBlocksDownloadRequest>,<br/><xref:Microsoft.Crm.Sdk.Messages.InitializeAnnotationBlocksDownloadRequest>
GET /api/data/v9.1/\<entity-type(id)\>/\<file-attribute-name\>/$value   | <xref:Microsoft.Crm.Sdk.Messages.DownloadBlockRequest>

Las transferencias de datos de archivo desde extremos de servicio web están limitadas a un máximo de 16 MB de datos en una sola llamada de servicio. Los datos de archivo más grandes que la cantidad se deben dividir en bloques de datos de 4 MB o más pequeños (fragmentos) donde cada bloque se recibe en una llamada API independiente hasta que se hayan recibido todos los datos de archivo. Es responsabilidad suya unir los bloques de datos descargados para formar el archivo de datos completo combinando los bloques de datos en la misma secuencia en que se recibieron.

Los mensajes como <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> y <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> no se pueden usar para descargar los datos de atributos de archivo.

### <a name="example-rest-download-with-chunking"></a>Ejemplo: Descarga de REST con fragmentación

**Solicitud**
```http
GET [Organization URI]/api/data/v9.1/accounts(id)/myfileattribute/$value
Headers:
Range: 0-1023/8192
```

**Respuesta**
```http
206 Partial Content

Body:
byte[]

Response Headers:
Content-Disposition: attachment; filename="sample.txt"
x-ms-file-name: "sample.txt"
x-ms-file-size: 8192
Location: api/data/v9.1/accounts(id)/myfileattribute?FileContinuationToken
```

La fragmentación se decidirá en función de la existencia de encabezado `Range` en la solicitud. El formato del valor de encabezado Range es: startByte-endByte/total bytes. El archivo completo se descargará (hasta 16 MB) en una solicitud si no hay encabezado `Range` incluido. Para la fragmentación, el encabezado de respuesta `Location` contiene el parámetro consultable `FileContinuationToken`. Use el valor de encabezado de ubicación que se proporciona en la la solicitud GET siguiente para recuperar el siguiente bloque de datos en la secuencia.

### <a name="example-net-c-code-for-download-with-chunking"></a>Ejemplo: Código .NET C# para descarga con fragmentación

```csharp
static async Task ChunkedDownloadAsync(
            Uri urlPrefix,
            string customEntitySetName,
            string entityId,
            string entityFileOrAttributeAttributeLogicalName,
            string fileRootPath,
            string downloadFileName,
            string token)
        {
            var url = new Uri(urlPrefix, $"{customEntitySetName}({entityId})/{entityFileOrAttributeAttributeLogicalName}/$value?size=full");
            var increment = 4194304;
            var from = 0;
            var fileSize = 0;
            byte[] downloaded = null;
            do
            {
                using (var request = new HttpRequestMessage(HttpMethod.Get, url))
                {
                    request.Headers.Range = new System.Net.Http.Headers.RangeHeaderValue(from, from + increment - 1);
                    request.Headers.Authorization = new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
                    using (var response = await Client.SendAsync(request))
                    {
                        if (downloaded == null)
                        {
                            fileSize = int.Parse(response.Headers.GetValues("x-ms-file-size").First());
                            downloaded = new byte[fileSize];
                        }

                        var responseContent = await response.Content.ReadAsByteArrayAsync();
                        responseContent.CopyTo(downloaded, from);
                    }
                }

                from += increment;
            } while (from < fileSize);

            await File.WriteAllBytesAsync(Path.Combine(fileRootPath, downloadFileName), downloaded);
        }
```

<a name="BKMK_UploadingFiles"></a>

## <a name="upload-file-data"></a>Cargar archivo de datos  
Para cargar datos de atributos de archivo, use las API siguientes.

API web (REST) | .NET API (SOAP)
------- | -------
ninguna   | <xref:Microsoft.Crm.Sdk.Messages.InitializeFileBlocksUploadRequest>,<br/><xref:Microsoft.Crm.Sdk.Messages.InitializeAttachmentBlocksUploadRequest>,<br/><xref:Microsoft.Crm.Sdk.Messages.InitializeAnnotationBlocksUploadRequest>
PATCH /api/data/v9.1/\<entity-type(id)\>/\<file-attribute-name\>   | <xref:Microsoft.Crm.Sdk.Messages.UploadBlockRequest>
ninguna   | <xref:Microsoft.Crm.Sdk.Messages.CommitFileBlocksUploadRequest>,<br/><xref:Microsoft.Crm.Sdk.Messages.CommitAttachmentBlocksUploadRequest>,<br/><xref:Microsoft.Crm.Sdk.Messages.CommitAnnotationBlocksUploadRequest>

Como se mencionó anteriormente en [Recuperar datos de archivo](#retrieve-file-data), cargar un archivo de datos de 16 MB o menos puede realizarse en una sola llamada API mientras que cargar más de 16 MB de datos requiere que los datos de archivo se dividan en bloques de 4 MB o menos de datos. Cuando el conjunto completo de bloques de datos se ha cargado y se ha enviado una solicitud de confirmación, el servicio web combinará automáticamente los bloques, en la misma secuencia que los bloques de datos se cargaron, en un archivo de datos único en Azure Blob Storage.

Los mensajes como <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> y <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> no se pueden usar para cargar los datos de atributos de archivo.

### <a name="example-rest-upload-with-chunking-first-request"></a>Ejemplo: Carga de REST con fragmentación (primera solicitud)

**Solicitud**
```http
PATCH [Organization URI]/api/data/v9.1/accounts(id)/myfileattribute 

Headers: 
x-ms-transfer-mode: chunked 
x-ms-file-name: sample.png
```
**Respuesta**
```http
200 OK 

Response Headers: 
x-ms-chunk-size: 4096 
Accept-Ranges: bytes 
Location: api/data/v9.1/accounts(id)/myfileattribute?FileContinuationToken 
```

### <a name="example-rest-upload-with-chunking-next-request"></a>Ejemplo: Carga de REST con fragmentación (siguiente solicitud)
**Solicitud**
```http
PATCH [Organization URI]/api/data/v9.1/accounts(id)/myfileattribute?FileContinuationToken 

Headers: 
Content-Range: 0-4095/8192 
Content-Type: application/octet-stream
x-ms-file-name: sample.png

Body:
byte[]
```

**Respuesta**
```http
206 Partial Content
```

### <a name="example-net-c-code-for-upload-with-chunking"></a>Ejemplo: Código .NET C# para carga con fragmentación

```csharp
static async Task ChunkedUploadAsync(
            Uri urlPrefix,
            string customEntitySetName,
            string entityId,
            string entityFileOrAttributeAttributeLogicalName,
            string fileRootPath,
            string uploadFileName,
            string accessToken)
        {
            var filePath = Path.Combine(fileRootPath, uploadFileName);
            var fileBytes = await File.ReadAllBytesAsync(filePath);
            var url = new Uri(urlPrefix, $"{customEntitySetName}({entityId})/{entityFileOrAttributeAttributeLogicalName}");

            var chunkSize = 0;
            using (var request = new HttpRequestMessage(HttpMethod.Patch, url))
            {
                request.Headers.Add("x-ms-transfer-mode", "chunked");
                request.Headers.Authorization = new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", accessToken);
                request.Headers.Add("x-ms-file-name", uploadFileName);
                using (var response = await Client.SendAsync(request))
                {
                    response.EnsureSuccessStatusCode();
                    url = response.Headers.Location;
                    chunkSize = int.Parse(response.Headers.GetValues("x-ms-chunk-size").First());
                }
            }

            for (var offset = 0; offset < fileBytes.Length; offset += chunkSize)
            {
                var count = (offset + chunkSize) > fileBytes.Length ? fileBytes.Length % chunkSize : chunkSize;
                using (var content = new ByteArrayContent(fileBytes, offset, count))
                using (var request = new HttpRequestMessage(HttpMethod.Patch, url))
                {
                    content.Headers.Add("Content-Type", "application/octet-stream");
                    content.Headers.ContentRange = new System.Net.Http.Headers.ContentRangeHeaderValue(offset, offset + (count - 1), fileBytes.Length);
                    request.Headers.Add("x-ms-file-name", uploadFileName);
                    request.Headers.Authorization = new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", accessToken);
                    request.Content = content;
                    using (var response = await Client.SendAsync(request))
                    {
                        response.EnsureSuccessStatusCode();
                    }
                }
            }
        }
```
 
<a name="BKMK_DeletingFiles"></a>

## <a name="delete-file-data"></a>Eliminar datos de archivo  
Para eliminar los datos del atributo de archivo del almacenamiento, use las API siguientes.

API web (REST) | .NET API (SOAP)
------- | -------
DELETE /api/data/v9.1/\<entity-type(id)\>/\<attribute-name\> | <xref:Microsoft.Crm.Sdk.Messages.DeleteFileRequest>

### <a name="see-also"></a>Vea también
[Atributos de imagen](image-attributes.md)
