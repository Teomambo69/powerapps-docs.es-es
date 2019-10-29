---
title: Agregar un recurso Web de Azure Storage a un formulario | MicrosoftDocs
description: Pasos para agregar el recurso Web de Azure Storage a un formulario para habilitar la carga de datos adjuntos en Azure Storage.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ed1053c758f97234ad94a09832683ff00ef17744
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977574"
---
# <a name="add-the-azure-storage-web-resource-to-a-form"></a>Adición del recurso web de Azure Storage a una forma

Los datos adjuntos cargados en Azure Storage en lugar de directamente en Common Data Service se pueden administrar mediante el uso de notas en Common Data Service.

Para habilitar la carga de datos adjuntos de un determinado formulario en Azure Storage, debe agregar un recurso Web a ese formulario y debe [configurar Azure Storage para su organización](enable-azure-storage.md).

> [!Note]
> En este ejemplo, el formulario se agrega al formulario de cliente potencial de la entidad del cliente potencial. Se recomienda tener cuidado al editar formularios existentes.

Cuando se carga un archivo (por ejemplo, Attachments. zip) en Azure Storage mediante el portal, se representa con una nota en una entidad y un marcador de posición para los datos adjuntos.

![Datos adjuntos en un](media/notes-attachment-lead-form.png "marcador de posición de formulario para los datos adjuntos en un formulario")

Tenga en cuenta que el archivo de datos adjuntos ahora se denomina Attachment. zip. txt. De forma predeterminada, Common Data Service no tiene ninguna concepción de un archivo de Azure, por lo que este archivo placeholder. txt se almacena en Common Data Service en su lugar. El contexto de Azure Storage para el archivo de marcador de posición muestra detalles sobre el archivo.
```
{
 Name: attachment.zip,
 Type: application/x-zip-compressed,
 Size: 24890882,
 "Url": "https://accountname.blob.core.windows.net/storage/81a9a9491c36e51182760026833bcf82/attachment.zip"
}
```

Para ver e interactuar con el archivo almacenado en Azure, debe agregar el recurso Web ADX. Annotations. html al formulario. Como requisito previo, asegúrese de que los usuarios tienen acceso de lectura a adx_setting. De lo contrario, el recurso Web no se representará correctamente.

1. En el editor de formularios para el formulario pertinente, seleccione **recurso Web** en la pestaña **Insertar** .

2. En el cuadro **recurso Web** , seleccione **adx_annotations/ADX. Annotations. html**.

3. Escriba un nombre y una etiqueta para el recurso.

4. En el cuadro **parámetro personalizado (datos)** , escriba **azureEnabled = true**. <br>También puede usar el recurso Web sin habilitar el soporte técnico de Azure de esta manera, en cuyo caso funcionará casi totalmente igual que el control predeterminado.</br>

5. En la pestaña **formato** , elija las reglas de formato que prefiera. Se recomienda desactivar la casilla **Mostrar borde** .

6. Seleccione **Aceptar** para guardar el recurso.

7. Opcionalmente, puede que desee quitar el control de notas existente o moverlo a una pestaña o sección marcada para que no sea visible de forma predeterminada.

8. Guarde el formulario y, a continuación, publique los cambios.

   ![Agregar recurso Web](media/add-web-resource.png "Agregar un recurso Web")

El nuevo control se representará ahora en la página, lo que le permitirá administrar los datos adjuntos en Azure Storage.

![Datos adjuntos de archivos de Azure en un formulario](media/azure-file-attachment-lead-form.png "de archivo adjunto de Azure en un formulario")

El icono de clip de papel se ha reemplazado por un icono de nube para indicar que este archivo se almacena en Azure Storage. Puede continuar con el almacenamiento de datos adjuntos en Common Data Service; esos archivos se denotarán con el icono de clip de papel.

> [!Note]
> Debe agregar una regla de uso compartido de recursos entre orígenes (CORS) en su cuenta de Azure Storage como se indica a continuación; de lo contrario, verá el icono de datos adjuntos normales en lugar del icono de la nube.
> - **Orígenes permitidos**: especifique el dominio. Por ejemplo, contoso.crm.dynamics.com.
> - **Verbos permitidos**: get, Put, Delete, Head, post
> - **Encabezados permitidos**: especifique los encabezados de solicitud que el dominio de origen puede especificar en la solicitud de CORS. Por ejemplo, x-MS-meta-data\*, x-MS-meta-Target\*. En este escenario, debe especificar *; de lo contrario, el recurso Web no se representará correctamente.
> - **Encabezados expuestos**: especifique los encabezados de respuesta que se pueden enviar en la respuesta a la solicitud de CORS y que el explorador expone al emisor de la solicitud. Por ejemplo, x-MS-meta-\*.
> - **Antigüedad máxima (segundos)** : especifique el tiempo máximo que un explorador debe almacenar en caché la solicitud de opciones preparatorias. Por ejemplo, 200.
> 
> [!include[More information](../../includes/proc-more-information.md)] [compatibilidad con CORS para los servicios de Azure Storage](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services).

Si el archivo adjunto es una imagen, el control mostrará la imagen como una miniatura, tanto si está almacenada en Common Data Service como en Azure Storage.

> [!Note]
> La característica de miniaturas se limita a las imágenes con un tamaño inferior a 1 MB.

(media/notes-thumbnail.png "Miniaturas") de notas ![en miniatura]notas

## <a name="cors-protocol-support"></a>Compatibilidad con el protocolo CORS

El protocolo de [uso compartido de recursos entre orígenes (CORS)](http://www.w3.org/TR/cors/) se compone de un conjunto de encabezados que indica si una respuesta se puede compartir con otro dominio.
La siguiente configuración del sitio se usa para configurar CORS:

|                 Nombre                  |                                                                            Descripción                                                                            |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| HTTP/Access-Control-Allow-Credentials | El único valor válido para este encabezado es true (distingue mayúsculas de minúsculas). Si no necesita credenciales, omita completamente este encabezado (en lugar de establecer su valor en false). |
|   HTTP/Access-Control-Allow-headers   |                                                   Una lista delimitada por comas de los encabezados de solicitud HTTP admitidos.                                                   |
|   HTTP/Access-Control-Allow-Methods   |                                      Una lista delimitada por comas de los métodos de solicitud HTTP permitidos, como GET, POST, OPTIONs.                                       |
|   HTTP/Access-Control-Allow-Origin    |                   Para permitir que cualquier recurso tenga acceso a los recursos, puede especificar \*. De lo contrario, especifique el URI que puede tener acceso a los recursos.                   |
|  Encabezados HTTP/Access-Control-exexpote   |                Una lista delimitada por comas de nombres de encabezado HTTP distintos de los encabezados de respuesta simples que el recurso podría usar y que se pueden exponer.                 |
|      HTTP/Access-Control-Max-Age      |                                                       Número máximo de segundos que los resultados se pueden almacenar en caché.                                                        |
|                                       |                                                                                                                                                                   |

