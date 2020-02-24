---
title: Exportar a lago de datos | Microsoft Docs
description: Obtenga información sobre cómo exportar datos de entidades a un lago de datos de Azure en Power Apps
ms.custom: ''
ms.date: 01/28/2020
ms.reviewer: Mattp123
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- powerapps
author: sabinn-msft
ms.assetid: ''
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 152fc65e69ccb728727f92ed77d6495f6dc5dcab
ms.sourcegitcommit: 303d5aed44f2bbb406cabeb6b9c8474d738d9114
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "3005298"
---
# <a name="export-entity-data-to-azure-data-lake-gen-2"></a>Exportar datos de entidades a Azure Data Lake Gen 2

El servicio Exportar a lago de datos es una canalización para exportar continuamente datos de Common Data Service a Azure Data Lake Gen 2. El servicio Exportar a lago de datos está diseñado para el análisis empresarial de macrodatos al ofrecer una alta disponibilidad escalable con capacidades de recuperación de desastres. Los datos se almacenan en el formato Common Data Model (CDM), que proporciona coherencia semántica en las aplicaciones y las implementaciones. 

![Información general sobre Exportar a lago de datos](media/export-data-lake-overview.png)

Exportar a lago de datos proporciona estas características: 
- Vincule o desvincule el entorno de Common Data Service a un lago de datos Gen 2 en su suscripción de Azure. 
- Replicación continua de entidades en Azure Data Lake Gen 2.
- Escritura inicial seguida de escrituras incrementales para datos y metadatos. 
- Replica entidades estándar y personalizadas. 
- Replica la creación, actualización y eliminación de transacciones. 
- Continuas actualizaciones de instantáneas para grandes escenarios de análisis. 
- Facilita el descubrimiento de metadatos y la interoperabilidad entre productores y consumidores de datos, como Power BI, Azure Data Factory, Azure Databricks y el servicio Azure Machine Learning.

## <a name="how-data-and-metadata-are-exported"></a>Cómo se exportan los datos y los metadatos
El servicio Exportar a lago de datos admite escrituras iniciales e incrementales para datos y metadatos de entidad. Cualquier cambio de datos o metadatos en Common Data Service se inserta automáticamente en el lago de datos sin ninguna acción adicional. Se trata de una operación de inserción en lugar de extracción. Los cambios se insertan en el destino sin necesidad de configurar intervalos de actualización. 

Se pueden exportar entidades estándar y personalizadas. Tenga en cuenta que el atributo de entidad de seguimiento de cambios en Common Data Service se utiliza para mantener los datos sincronizados de forma eficiente detectando qué datos se han modificado desde se extrajeron inicialmente o se sincronizaron por última vez. 

Todas las operaciones de creación, actualización, eliminación (CrUD) se exportan de Common Data Service al lago de datos. Por ejemplo, cuando un usuario elimina un registro de entidad de cuenta en Common Data Service, la transacción se replica en el lago de datos de destino.

## <a name="prerequisites"></a>Requisitos previos
Antes de que pueda exportar datos de Common Data Service a un lago de datos, debe crear y configurar una cuenta de almacenamiento Azure StorageV2 (uso general v2). 

Siga los pasos en el artículo  [Crear una cuenta Azure Storage](/azure/storage/blobs/data-lake-storage-quickstart-create-account)  y tenga en cuenta estos requisitos: 
- Deben concederse un rol de propietario en la cuenta de almacenamiento. 
- Establezca su tipo de almacenamiento como **Storagev2 (uso general v2)**. 
- La cuenta de almacenamiento debe tener la característica **Espacio de nombres jerárquico** habilitada. 
 - Se recomienda establecer la replicación como almacenamiento con redundancia geográfica de acceso de lectura (RA-GRS). Más información: [Almacenamiento con redundancia geográfica de acceso de lectura](/azure/storage/common/storage-redundancy-grs#read-access-geo-redundant-storage) 
>   ![Propiedades de cuenta de almacenamiento](media/storage-account-properties.png)

> [!NOTE]
> - La cuenta de almacenamiento se debe crear en el mismo inquilino de Azure AD que su inquilino de PowerApps.  
> - La cuenta de almacenamiento debe crearse en la misma región que el entorno de PowerApps en el que utilizará la característica.  
>  - Para vincular el entorno de Common Data Service a Azure Data Lake Gen 2, debe ser un administrador de Common Data Service. 
>  - Solo se pueden exportar las entidades que tienen seguimiento de cambios habilitado. 


## <a name="select-and-export-common-data-service-entity-data-to-azure-data-lake-gen-2"></a>Seleccionar y exportar datos de entidades de Common Data Service a Azure Data Lake Gen 2
1. Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), expanda **Datos** y luego seleccione **Entidades**. 
2. En la barra de comandos, seleccione **Exportar a lago de datos** y, en la página **Exportar a lago de datos**, seleccione **Nuevo vínculo a lago de datos**. 
3. Seleccione cada una de las siguientes configuraciones y, a continuación, seleccione **Siguiente**. 
   - **Suscripción**. Seleccione su suscripción a Azure. 
   - **Grupo de recursos**. Seleccione el grupo de recursos que contiene la cuenta de almacenamiento Storagev2 (uso general v2).
   - **Cuenta de almacenamiento**. Seleccione la cuenta de almacenamiento Storagev2 (uso general v2) que desea usar para la exportación. 
4. Seleccione las entidades que desea exportar al lago de datos y luego seleccione **Guardar**. Solo se pueden exportar las entidades con seguimiento de cambios habilitado. Más información: [Habilitar el seguimiento de cambios](/dynamics365/customer-engagement/admin/enable-change-tracking-control-data-synchronization)

   > [!div class="mx-imgBorder"] 
   > ![Seleccionar entidades para exportar](media/export-data-lake-select-entity.png)

Su entorno de Common Data Service está vinculado a la cuenta de almacenamiento de Azure Data Lake Gen 2. El sistema de archivos en la cuenta de almacenamiento de Azure se crea con una carpeta para cada entidad seleccionada para replicarla en el lago de datos. 

## <a name="manage-entity-data-to-the-data-lake"></a>Administrar los datos de entidad en el lago de datos
Una vez que haya configurado la exportación de datos al Azure Data Lake Gen 2 en su suscripción, puede administrar la exportación de datos de la entidad al lago de datos de una de dos maneras. 

- En el portal del creador de Power Apps, en el área **Exportar a lago de datos**, seleccione **Administrar entidades** en la barra de comandos para agregar o eliminar una o más entidades vinculadas.
- En el portal del creador de Power Apps, en el área **Entidades**, seleccione **...** junto a una entidad y luego seleccione el lago de datos vinculados en el que desea exportar los datos de la entidad. 
   ![Seleccionar entidad para exportación](media/select-entity-export.png)


Para desvincular todas las entidades vinculadas, en el portal del creador de Power Apps, en el **área Exportar al lago de datos**, seleccione **Desvincular lago de datos**. 

## <a name="view-your-data-in-the-azure-data-lake-gen-2"></a>Ver sus datos en Azure Data Lake Gen 2
1. Inicie sesión en [Azure](https://portal.azure.com), seleccione la cuenta de almacenamiento y, en el panel de navegación izquierdo, seleccione **Explorador de Storage**. 
2. Expanda **Sistemas de archivos** y luego seleccione commondataservice-*environmentName*-org-*Id*. 

El archivo model.json, junto con el nombre y la versión, proporciona una lista de entidades que se han exportado al lago. El archivo model.json también incluye el estado de sincronización inicial y el tiempo completado. 

Se muestra una carpeta para cada entidad exportada al lago de datos que incluye archivos de formato delimitado por comandos (CSV) de una instantánea. 
   > [!div class="mx-imgBorder"] 
   > ![Datos de la entidad en el lago](media/entity-data-in-lake.png) 

### <a name="continuous-snapshot-updates"></a>Continuas actualizaciones de instantáneas
Los datos de Common Data Service pueden cambiar continuamente mediante la creación, actualización y eliminación de transacciones. Las instantáneas proporcionan una copia de datos de solo lectura que se actualiza a un intervalo regular, que es cada hora. Esto garantiza que, en un momento punto dado, un consumidor de análisis de datos pueda consumir datos de manera fiable en el lago.   

![Continuas actualizaciones de instantáneas](media/snapshot-updates.png)

Cuando se agregan entidades como parte de la exportación inicial, los datos de la entidad se escriben en los archivos entity.csv en las carpetas correspondientes en el lago. Este es el intervalo T1, donde se crea un archivo de solo lectura de instantáneas llamado *entity*-T1.csv, como Account-T1.csv y Contacts-T1.csv. Además, el archivo model.json se actualiza para que apunte a estos archivos de instantáneas. Al abrir el archivo model.json, puede ver los detalles de la instantánea. 

Aquí se muestra un ejemplo del archivo particionado Account.csv y la carpeta de instantáneas en el lago.
![Instantánea de entidad de cuentas](media/export-data-lake-account-snapshots.png) 

Los cambios en Common Data Service se insertan continuamente en los archivos csv correspondientes utilizando el motor de alimentación por goteo. Este es el intervalo T2, donde se toma otra instantánea. *Entity*-T2.csv, como Accounts-T2.csv y Contacts-T2.csv (suponiendo que haya cambios para ambas entidades) y model.json se actualizan a los nuevos archivos de instantáneas. Cualquier persona nueva que vea datos de instantáneas desde T2 en adelante se dirige a los archivos de instantáneas más nuevos. De esta manera, el visor de instantáneas original puede continuar trabajando en los archivos T1 de instantáneas más antiguos, mientras que los nuevos visores pueden leer las últimas actualizaciones. Esto resulta útil en escenarios con procesos de bajada más largos. 

Aquí se muestra un ejemplo del archivo model.json, que siempre apunta al último archivo de instantánea de la cuenta con marca de tiempo. 

![Json de instantánea de ejemplo](media/sample-snapshot-json.png) 

## <a name="transporting-export-to-data-lake-configuration-across-environments"></a>Transportar la configuración de la exportación al lago de datos a través de entornos
En Power Apps, las soluciones se aprovechan para transportar aplicaciones y componentes desde un entorno a otro o para aplicar un conjunto de personalizaciones a aplicaciones existentes. Para que la solución de configuraciones de exportación al lago de datos sea consciente, importe la solución Exportar a Data Lake Core al entorno. Esto permite las capacidades básicas de administración del ciclo de vida de la aplicación (ALM), como la distribución, y la copia de seguridad y restauración de la configuración de la exportación al lago de datos. 

### <a name="import-the-export-to-data-lake-core-solution"></a>Importar la solución Exportar a Data Lake Core 
1.  Desde el portal del creador de Power Apps, seleccione el entorno en el que desea distribuir la configuración del la exportación al lago de datos.
2.  En el panel de navegación izquierdo, seleccione **Soluciones**, seleccione **Abrir AppSource**, busque la solución llamada **Exportar a Data Lake Core** y luego importe la solución.

### <a name="add-an-export-to-data-lake-configuration-to-a-solution"></a>Agregar una configuración de la exportación al lago de datos a una solución

> [!IMPORTANT]
> Antes de poder agregar una exportación a la configuración del lago de datos, debe instalar la solución Exportar a Data Lake Core descrita anteriormente. 

1.  Desde el portal del creador de Power Apps, seleccione el entorno en el que desea distribuir la configuración de la exportación al lago de datos y, en el panel de navegación izquierdo, seleccione **Soluciones**. 
2.  Seleccione **Nueva solución**, proporcione un nombre, seleccione un editor y luego especifique un número de versión.  
3.  Abra la solución que creó en el paso anterior, seleccione **Agregar existente** > **Otro** > **Configuración de la exportación al lago de datos**. 
4.  Seleccione las configuraciones del lago de datos vinculado que desea y luego seleccione **Agregar**. 
5.  En el área **Soluciones**, seleccione la solución y, en la barra de comandos, seleccione **Exportar**. 
6.  En el panel **Antes de exportar**, seleccione **Publicar** para publicar todos los cambios antes de la exportación y, a continuación, seleccione **Siguiente**. 

### <a name="import-the-solution-that-contains-the-export-to-data-lake-configuration"></a>Importar la solución que contiene la exportación a la configuración del lago de datos
En el entorno donde desea importar su solución, en el portal del creador de Power Apps, en el área **Soluciones**, importe la solución. 

#### <a name="verify-the-export-to-data-lake-configuration"></a>Verificar la configuración de la exportación al lago de datos
Desde el portal del creador de Power Apps en el entorno donde importó la configuración de la exportación al lago de datos, verifique que puede ver su lago de datos vinculado, así como las entidades que transportó desde su otro entorno.
> [!div class="mx-imgBorder"] 
> ![Exportación importada a entidades del lago de datos](media/imported-export-entities.png) 

### <a name="see-also"></a>Vea también
[Blog: Exportar datos de CDS a Azure Data Lake](https://powerapps.microsoft.com/blog/exporting-cds-data-to-azure-data-lake-preview/)