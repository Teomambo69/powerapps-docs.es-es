---
title: Agregar el recurso de web Azure Storage a un formulario | MicrosoftDocs
description: Pasos para agregar un recurso web de Azure Storage a un formulario para permitir la carga de adjuntos a Azure Storage.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/05/2020
ms.author: tapanm
ms.reviewer: tapanm
ms.openlocfilehash: d00b323b33f971ff9c55a7590d3630baadfc09fe
ms.sourcegitcommit: eaf423817d61b57cbde7c4b820b3e44940c3f8af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2020
ms.locfileid: "3340290"
---
# <a name="add-the-azure-storage-web-resource-to-a-form"></a>Agregar el recurso de web Azure Storage a un formulario

Los datos adjuntos cargados en Azure Storage, en lugar de directamente en Common Data Service, se pueden administrar con notas en Common Data Service.

Para que los datos adjuntos de un formulario determinado se puedan cargar en Azure Storage, debe agregar un recurso web al formulario y debe [configurar Azure Storage para la organización](enable-azure-storage.md).

> [!NOTE]
> En este ejemplo, el formulario se agrega al formulario de cliente potencial para la entidad Cliente potencial. Se recomienda tener precaución al editar los formularios existentes.

Cuando un archivo (por ejemplo, attachments.zip) se carga en Azure Storage mediante el portal, es representado por una nota en una entidad y un marcador para el dato adjunto.

![Datos adjuntos en un formulario](media/notes-attachment-lead-form.png "Marcador de posición para datos adjuntos en un formulario")

Tenga en cuenta que el archivo de datos adjuntos ahora se llama attachment.zip.txt. De forma predeterminada, Common Data Service no tiene ningún concepto de archivo Azure, por lo que este archivo placeholder.txt se almacena en Common Data Service en su lugar. El contexto de Azure Storage del archivo con marcadores muestra detalles sobre el archivo.
```
{
 Name: attachment.zip,
 Type: application/x-zip-compressed,
 Size: 24890882,
 "Url": "https://accountname.blob.core.windows.net/storage/81a9a9491c36e51182760026833bcf82/attachment.zip"
}
```

Para ver e interactuar con el archivo almacenado en Azure, debe agregar el recurso web adx.annotations.html al formulario. Como requisito previo, asegúrese de que sus usuarios obtienen acceso de lectura a adx_setting. De lo contrario, el recurso web no generará representaciones correctamente.

1. En el editor de formularios del formulario relevante, seleccione **Recurso web** en la pestaña **Insertar**.

2. En la casilla **Recurso web** , seleccione **adx_annotations/adx.annotations.html**.

3. Escriba una etiqueta de nombre para el recurso.

4. En la casilla **Parámetro personalizado (datos)** introduzca **azureEnabled=true**. <br>También puede usar el recurso web sin habilitar el soporte de Azure de esta forma, en este caso funciona casi completamente del mismo modo que el control predeterminado.</br>

5. En la pestaña **Formato** , elija las reglas de formato que prefiere. Se recomienda desactivar la casilla de verificación **Mostrar el borde**.

6. Seleccione **Aceptar** para guardar el recurso.

7. Opcionalmente, puede quitar el control de notas existente. O muévalo a una pestaña o sección marcada como no visible de forma predeterminada.

8. Guarde el formulario y, a continuación, publique los cambios.

   ![Agregar recurso web](media/add-web-resource.png "Agregar un recurso web")

El nuevo control ahora se generará en la página, dándole la capacidad de administrar sus datos adjuntos en Azure Storage.

![Archivo adjunto Azure en un formulario](media/azure-file-attachment-lead-form.png "Archivo adjunto Azure en un formulario")

El icono de clip de papel se ha reemplazado por un icono de nube para indicar que este archivo se ha almacenado en Azure Storage. Puede continuar almacenando los datos adjuntos de Common Data Service; estos archivos se indicarán con el icono de clip de papel.

> [!Note]
> También debe agregar la regla de uso compartido de recursos de origen cruzado (CORS) en su cuenta de Azure Storage como sigue; de lo contrario, verá el icono normal de los datos adjuntos en lugar del icono de nube.
> - **Orígenes permitidos**: Especifique el dominio. Por ejemplo, `https://contoso.crm.dynamics.com`.
> - **Verbos permitidos**: OBTENER, PONER, ELIMINAR, ENCABEZAR, PUBLICAR
> - **Encabezados permitidos**: Especifique los encabezados de solicitud que el dominio de origen puede especificar en la solicitud de CORS. Por ejemplo, x-ms-meta-data\*, x-ms-meta-target\*. En este escenario, debe especificar *, si no el recurso web no generará representaciones correctamente.
> - **Encabezados expuestos**: Especifique los encabezados de respuesta que se pueden enviar en la respuesta a la solicitud de CORS y que expone el explorador al emisor de la solicitud. Ejemplos: \* o x-ms-meta-\*. En este escenario, debe especificar *, si no el recurso web no generará representaciones correctamente.
> - **Edad máxima (segundos)**: Especifique la cantidad máxima de tiempo que un explorador debe almacenar en caché la solicitud OPCIONES de preparación. Por ejemplo, 200.
> 
> [!include[More information](../../includes/proc-more-information.md)] [Soporte CORS para Azure Storage Services](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services).

Si el archivo adjunto es una imagen, el control mostrará la imagen como miniatura si está almacenada en Common Data Service o Azure Storage.

> [!Note]
> La característica de la miniatura está limitada a las imágenes de menos de 1 MB de tamaño.

![Miniatura de notas](media/notes-thumbnail.png "Miniatura de notas")

### <a name="processes-for-azure-blob-storage"></a>Procesos para Azure Blob Storage

Hay dos procesos necesarios para cargar archivos adjuntos en Azure Storage: **URL de Azure Blob Storage** y **AzureBlobStorageEnabled**.

![Procesos de Blob Storage](media/blob-storage-processes.png "Procesos de Blob Storage")

Durante la migración, los procesos pueden desactivarse. Esto puede hacer que los archivos adjuntos se carguen en Common Data Service en lugar de Azure Storage después de seguir los pasos para agregar recursos web. Asegúrese de que estos dos procesos estén activados para cargar archivos adjuntos en Azure Storage.

## <a name="cors-protocol-support"></a>Admisión de protocolo CORS

El protocolo [Uso compartido de recursos de origen cruzado (CORS)](https://www.w3.org/TR/cors/) se compone de un conjunto de encabezados que indican si una respuesta se puede compartir con otro dominio.
La siguiente configuración se usa para configurar CORS.

| Configuración del sitio | Encabezado de solicitud | Descripción |
|-|-|-|
| HTTP/Access-Control-Allow-Credentials | Access-Control-Allow-Credentials | El único valor válido para este encabezado es verdadero (con distinción entre mayúsculas de minúsculas). Si no necesita las credenciales, omita este encabezado completamente (en lugar de establecer el valor en falso). 
| HTTP/Access-Control-Allow-Headers | Access-Control-Allow-Headers | Una lista delimitada por comas de los encabezados de solicitud HTTP admitidos.
| HTTP/Access-Control-Allow-Methods | Access-Control-Allow-Methods | Una lista delimitada por comas de los métodos de solicitud HTTP admitidos como OBTENER, CORREO, OPCIONES.
| HTTP/Access-Control-Allow-Origin | Access-Control-Allow-Origin | URL de la instancia de Dynamics 365, como https://contoso.crm.dynamics.com. Para permitir que cualquier URI acceda a sus recursos, use \*.                 |
|  HTTP/Access-Control-Expose-Headers | Access-Control-Expose-Headers | Una lista delimitada por comas de nombres de encabezado HTTP distintos a los encabezados de respuesta sencillos que el recurso puede usar y a los que puede ser expuesto.
| HTTP/Access-Control-Max-Age | Access-Control-Max-Age |  El número máximo de segundos que se pueden almacenar los resultados en la caché.
| HTTP/Content-Security-Policy | Content-Security-Policy | Controla los recursos que el agente de usuario puede cargar para una página determinada.
| HTTP/Content-Security-Policy-Report-Only | Content-Security-Policy-Report-Only | Permite a los desarrolladores web experimentar con directivas monitorizando, pero no forzando, sus efectos. Estos informes de infracción consisten en documentos JSON enviados a través de una solicitud HTTP POST al URI especificado.
| HTTP/X-Frame-Options | X-Frame-Options | Indica si se debe permitir a un explorador representar una página en un *\<frame\>*, *\<iframe\>*, *\<embed\>* u *\<object\>*.
| HTTP/X-Content-Type-Options | X-Content-Type-Options | Deshabilita el análisis MIME y fuerza al explorador a usar el tipo dado en *Tipo de contenido*.
