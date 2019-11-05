---
title: Habilitar Azure Storage para portales | MicrosoftDocs
description: Instrucciones para habilitar Azure Storage para los portales con el fin de aprovechar las ventajas de la mayor capacidad de almacenamiento de archivos de Azure.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3da40cfdcb88726384218c4b1df370c301f8ac16
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542560"
---
# <a name="enable-azure-storage"></a>Habilitar Azure Storage

La integración de Azure Storage para los portales permite aprovechar las ventajas de la mayor capacidad de almacenamiento de archivos de Azure, con la misma interfaz y proporcionar la misma experiencia de usuario que para los archivos adjuntos predeterminados. Esta característica es compatible con los archivos Web, los formularios de entidad y los formularios Web Forms.

Debe crear una cuenta de almacenamiento con **Resource Manager** como modelo de implementación. [!include[More information](../../includes/proc-more-information.md)] [crear una cuenta de almacenamiento de Azure](https://docs.microsoft.com/azure/storage/storage-create-storage-account#create-a-storage-account).

Una vez que se ejecuta la cuenta de almacenamiento, los portales requieren ciertas configuraciones globales que indican a la aplicación cómo localizar la cuenta de almacenamiento. En la aplicación de administración del portal, vaya a **configuración** > **nuevo**y agregue una nueva configuración denominada **FileStorage/CloudStorageAccount**.

> [!NOTE]
> El tamaño máximo de carga de archivos es 125 MB.

Para buscar el valor de FileStorage/CloudStorageAccount, debe obtener una cadena de conexión de su [!include[Azure portal](../../includes/pn-azure-portal.md)].

1. Inicie sesión en su [!include[Azure portal](../../includes/pn-azure-portal.md)].

2. Vaya a la cuenta de almacenamiento.

3. Seleccione **claves de acceso**.

    ![Busque el valor de cadena de conexión desde el Azure Portal](media/key-azure-storage.png "Busque el valor de la cadena de conexión desde el Azure Portal")

4. En el panel resultante, busque el campo con la etiqueta **cadena de conexión**. Seleccione el icono de **copia** situado junto al campo para el que necesita copiar el valor y, a continuación, péguelo en el nuevo valor:

    ![Valor de cadena de conexión principal](media/primary-connection-string-azure-storage.png "Valor de cadena de conexión principal")

    ![Configuración del portal para la cuenta de almacenamiento en la nube](media/portal-site-setting-cloud-storage-account.png "Configuración del portal para la cuenta de almacenamiento en la nube")

## <a name="specify-the-storage-container"></a>Especificar el contenedor de almacenamiento

Si aún no tiene un contenedor de blobs de Azure en la cuenta de almacenamiento, debe agregar uno mediante el [!include[Azure portal](../../includes/pn-azure-portal.md)].

En la [aplicación de administración del portal](configure/configure-portal.md), vaya a **configuración** > **nuevo**y agregue una nueva configuración denominada **FileStorage/CloudStorageContainerName**, con el nombre del contenedor como valor.

![Configuración del portal para el contenedor de almacenamiento en la nube](media/portal-site-setting-cloud-storage-container.png "Configuración del portal para el contenedor de almacenamiento en nube")

## <a name="add-cors-rule"></a>Agregar regla de CORS

Debe agregar una regla de uso compartido de recursos entre orígenes (CORS) en su cuenta de Azure Storage como se indica a continuación; de lo contrario, verá el icono de datos adjuntos normales en lugar del icono de la nube:

- **Orígenes permitidos**: especifique el dominio. Por ejemplo, contoso.crm.dynamics.com.
- **Verbos permitidos**: get, Put, Delete, Head, post
- **Encabezados permitidos**: especifique los encabezados de solicitud que el dominio de origen puede especificar en la solicitud de CORS. Por ejemplo, x-MS-meta-data\*, x-MS-meta-Target\*. 
- **Encabezados expuestos**: especifique los encabezados de respuesta que se pueden enviar en la respuesta a la solicitud de CORS y que el explorador expone al emisor de la solicitud. Por ejemplo, x-MS-meta-\*.
- **Antigüedad máxima (segundos)** : especifique el tiempo máximo que un explorador debe almacenar en caché la solicitud de opciones preparatorias. Por ejemplo, 200.
 
[!include[More information:](../../includes/proc-more-information.md)] [compatibilidad con CORS para los servicios de Azure Storage](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services)

## <a name="add-site-settings"></a>Agregar configuración del sitio

Agregue la siguiente configuración del sitio de **portales** > **configuración del sitio**. [!include[More information:](../../includes/proc-more-information.md)] [administrar la configuración del sitio de portal](configure/configure-site-settings.md#manage-portal-site-settings).

|Nombre|Value|
|-----|-----|
|WebFiles/CloudStorageAccount|Proporcione la misma cadena de conexión que se proporciona para el valor de FileStorage/CloudStorageAccount.|
|WebFiles/StorageLocation|AzureBlobStorage|
|||

Ahora puede crear un archivo secundario en el portal y mencionar el nombre completo (junto con el contenedor) en la dirección URL de la dirección del BLOB de Azure. Con esta configuración, el portal está listo para empezar a cargar y descargar archivos desde y hacia Azure Storage. Sin embargo, no puede sacar el máximo partido de esta característica hasta que [agregue un recurso Web para habilitar la carga de datos adjuntos en Azure Storage](add-web-resource.md)y configurar [formularios de entidad](configure-notes.md#notes-configuration-for-entity-forms) o [formularios Web Forms](configure-notes.md#notes-configuration-for-web-forms) para que lo usen.

### <a name="see-also"></a>Vea también

[Agregar recurso Web](add-web-resource.md)

[Configurar notas](configure-notes.md)
