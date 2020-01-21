---
title: Habilitar Azure Storage para los portales | MicrosoftDocs
description: Instrucciones para habilitar Azure Storage para portales para que aproveche la mayor capacidad de almacenamiento de archivos de Azure.
author: sbmjais
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/07/2020
ms.author: shjais
ms.reviewer: tapanm
ms.openlocfilehash: 38705c143fdf3e85ec18f60c20423cc404aee043
ms.sourcegitcommit: df15c909ba27c9ed83197305a4ee1f01e46a826b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "2936123"
---
# <a name="enable-azure-storage"></a>Habilitar Azure Storage

La integración de Azure Storage para los portales le permite aprovechar la mayor capacidad de almacenamiento de archivo de Azure, utilizando la misma interfaz y proporcionando la misma experiencia de usuario que para los datos adjuntos del archivo predeterminado. Esta característica se admite para los archivos web, los formularios de entidades, y los formularios web.

Debe crear una cuenta de almacenamiento con **Administrador de recursos** como el modelo de implementación. [!include[More information](../../includes/proc-more-information.md)] [Crear una cuenta de almacenamiento de Azure](https://docs.microsoft.com/azure/storage/storage-create-storage-account#create-a-storage-account).

Una vez que la cuenta de almacenamiento esté activa, los portales requieren una determinada configuración global que indique a aplicación cómo buscar su cuenta de almacenamiento. En la aplicación Administración del portal, vaya a **Configuración** > **Nuevo**, y agregue un valor nuevo con el nombre **FileStorage/CloudStorageAccount**.

> [!NOTE]
> El límite máximo de carga de archivos es 125MB.

Para buscar el valor de FileStorage/CloudStorageAccount, debe obtener una cadena de conexión de su [!include[Azure portal](../../includes/pn-azure-portal.md)].

1. Inicie sesión en su [!include[Azure portal](../../includes/pn-azure-portal.md)].

2. Desplácese a su cuenta de almacenamiento.

3. Seleccione **Teclas de acceso**.

    ![Busque el valor de la cadena de conexión del portal de Azure](media/key-azure-storage.png "Busque el valor de la cadena de conexión del portal de Azure")

4. En el panel resultante, localice el campo etiquetado con **Cadena de conexión**. Seleccione el icono **Copiar** junto al campo del que necesita copiar el valor y, a continuación, pegue el valor en la nueva configuración:

    ![Valor de cadena de conexión principal](media/primary-connection-string-azure-storage.png "Valor de cadena de conexión principal")

    ![Configuración de portal para la cuenta de almacenamiento en nube](media/portal-site-setting-cloud-storage-account.png "Configuración del portal para la cuenta de almacenamiento en nube")

## <a name="specify-the-storage-container"></a>Especifique el contenedor de almacenamiento

Si no tiene todavía un contenedor Blob de Azure en su cuenta de almacenamiento, debe agregar uno con su [!include[Azure portal](../../includes/pn-azure-portal.md)].

En la [aplicación Administración del portal](configure/configure-portal.md), vaya a **Configuración** > **Nuevo** y agregue un nuevo valor denominado **FileStorage/CloudStorageContainerName**, con el nombre del contenedor como el valor.

![Configuración de portal para el contenedor de almacenamiento en nube](media/portal-site-setting-cloud-storage-container.png "Configuración del portal para el contenedor de almacenamiento en nube")

## <a name="add-cors-rule"></a>Agregar regla de CORS

También debe agregar la regla de uso compartido de recursos de origen cruzado (CORS) en su cuenta de Azure Storage como sigue; de lo contrario, verá el icono normal de los datos adjuntos en lugar del icono de nube:

- **Orígenes permitidos**: Especifique el dominio. Por ejemplo, `https://contoso.crm.dynamics.com`.
- **Verbos permitidos**: OBTENER, PONER, ELIMINAR, ENCABEZAR, PUBLICAR
- **Encabezados permitidos**: Especifique los encabezados de solicitud que el dominio de origen puede especificar en la solicitud de CORS. Por ejemplo, x-ms-meta-data\*, x-ms-meta-target\*. 
- **Encabezados expuestos**: Especifique los encabezados de respuesta que se pueden enviar en la respuesta a la solicitud de CORS y que expone el explorador al emisor de la solicitud. Por ejemplo, x-ms-meta-\*.
- **Edad máxima (segundos)**: Especifique la cantidad máxima de tiempo que un explorador debe almacenar en caché la solicitud OPCIONES de preparación. Por ejemplo, 200.
 
[!include[More information:](../../includes/proc-more-information.md)] [Soporte CORS para Azure Storage Services](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services)

## <a name="add-site-settings"></a>Agregar configuraciones de sitios

Agregue la siguiente configuración de sitio de **portales** > **configuración del sitio**. [!include[More information:](../../includes/proc-more-information.md)] [Administrar la configuración del sitio de portal](configure/configure-site-settings.md#manage-portal-site-settings)

|Nombre|Value|
|-----|-----|
|WebFiles/CloudStorageAccount|Proporcione la misma cadena de conexión que se ha proporcionado para la configuración de FileStorage/CloudStorageAccount.|
|WebFiles/StorageLocation|AzureBlobStorage|
|||

Ahora puede crear un archivo secundario en el portal y mencionar el nombre completo (junto con contenedor) en la dirección URL de Azure Blob. Con esta configuración, el portal está listo para comenzar mediante la descarga y la carga de los archivos desde Azure Storage. Sin embargo, no puede aprovechar por completo esta característica hasta que usted [agregue un recurso web que permita cargar los datos adjuntos en Azure Storage](add-web-resource.md), y configurar [formularios de entidad](configure-notes.md#notes-configuration-for-entity-forms) o [formularios web](configure-notes.md#notes-configuration-for-web-forms).

### <a name="see-also"></a>Vea también

[Agregar recurso web](add-web-resource.md)

[Configuración de notas](configure-notes.md)
