---
title: Conectar Azure Data Lake Storage Gen2 para almacenamiento de flujo de datos | MicrosoftDocs
description: Aprender a conectar Azure Data Lake Storage Gen2 para almacenamiento de flujo de datos
ms.custom: ''
ms.date: 09/05/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ''
caps.latest.revision: ''
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d7957f048613045a64af0caf5696e540dbb8f883
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754803"
---
# <a name="connect-azure-data-lake-storage-gen2-for-dataflow-storage"></a>Conexión a Azure Data Lake Storage Gen2 para el almacenamiento del flujo de datos

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Puede configurar flujos de datos para almacenar sus datos en la cuenta de Azure Data Lake Storage Gen2 de la organización. En este artículo se describen los pasos generales necesarios para ello, y proporciona instrucciones y prácticas recomendadas a lo largo del proceso. 

Hay algunas ventajas de configurar flujos de datos para almacenar sus definiciones y archivos de datos en su lago de datos, por ejemplo:
- Azure Data Lake Storage Gen2 proporciona instalaciones de almacenamiento de datos enormemente escalables.
- Los datos de flujo de datos y los archivos de definición se pueden aprovechar por los desarrolladores del departamento de TI para aprovechar servicios de datos y de inteligencia artificial (IA) de Azure como se demuestra en los ejemplos de GitHub de los servicios de datos de Azure.
- Permite a los desarrolladores de la organización integrar datos del flujo de datos en aplicaciones internas y soluciones de línea de negocios, mediante recursos para programadores para flujos de datos y Azure.

## <a name="requirements"></a>Requisitos
Para usar Azure Data Lake Storage Gen2 para flujos de datos, necesita lo siguiente:
- Un entorno de PowerApps. Cualquier plan de PowerApps permitirá crear flujos de datos con Azure Data Lake Storage Gen2 como destino. Deberá estar autorizado en el entorno como fabricante. 
- Una suscripción a Azure. Necesita una suscripción a Azure para usar Azure Data Lake Storage Gen2.
- Un grupo de recursos. Use un grupo de recursos que ya tiene, o bien cree uno nuevo.
- Una cuenta de almacenamiento de Azure. La cuenta de almacenamiento debe tener la característica Data Lake Storage Gen2 habilitada.

> [!TIP]
> Si no dispone de una suscripción con Azure, [cree una cuenta gratuita](https://azure.microsoft.com/free/) antes de comenzar.

## <a name="prepare-your-azure-data-lake-storage-gen2-for-power-platform-dataflows"></a>Preparar Azure Data Lake Storage Gen2 para flujos de datos de Power Platform
Antes de configurar el entorno con una cuenta Azure Data Lake Storage Gen2, debe crear y configurar una cuenta de almacenamiento. A continuación se enumeran los requisitos para flujos de datos de Power Platform:
1.  La cuenta de almacenamiento se debe crear en el mismo inquilino de Azure Active Directory que su inquilino de PowerApps.
2.  Es recomendable que la cuenta de almacenamiento se cree en la misma región que el entorno de PowerApps donde planea usarla. Para determinar dónde está el entorno de PowerApps, póngase en contacto con el administrador del entorno.
3.  La cuenta de almacenamiento debe tener la característica de espacio de nombres jerárquico habilitada.
4.  Deben concederse un rol de propietario en la cuenta de almacenamiento.

En las siguientes secciones se indican los pasos necesarios para configurar su cuenta de Azure Data Lake Storage Gen2.

## <a name="create-the-storage-account"></a>Crear la cuenta de almacenamiento
Siga los pasos en [Crear una cuenta de almacenamiento Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account).
1.  Asegúrese de seleccionar la misma región que el entorno y establecer el almacenamiento como StorageV2 (propósito general v2).
2.  Asegúrese de habilitar la característica de espacio de nombres jerárquico. 
3.  Se recomienda establecer el ajuste de replicación como Almacenamiento con redundancia geográfica de acceso de lectura (RA-GRS).

## <a name="connect-your-azure-data-lake-storage-gen2-to-powerapps"></a>Conectar Azure Data Lake Storage Gen2 con PowerApps
Una vez que haya configurado su cuenta de Azure Data Lake Storage Gen2 en el portal de Azure, estará listo para conectarlo a un flujo de datos específico o a un entorno de PowerApps. La conexión del lago a un entorno permite que otros fabricantes y administradores del entorno creen flujos de datos que almacenan sus datos en el lago de la organización también. 

Para conectar su cuenta de Azure Data Lake Storage Gen2 con el flujo de datos, siga estos pasos:
1.  Inicie sesión en [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) y compruebe en qué entorno está. El selector de entorno se encuentra en la parte derecha del encabezado. 
2. En el panel de navegación de la izquierda, seleccione la flecha abajo junto a **Datos**.

   ![Pestaña Datos del portal del creador de PowerApps](media/powerapps-portal-data.png)

3. En la lista que aparece, seleccione **Flujos de datos** y en la barra de comandos seleccione **Nuevo flujo de datos**.

   ![Crear un flujo de datos nuevo](media/new-dataflow.png) 

4. Seleccione las entidades analíticas que desee. Estas entidades indican qué datos desea almacenar en la cuenta Azure Data Lake Store Gen 2 de la organización. 

   ![Seleccionar entidades analíticas](media/select-analytical-entities.png)

## <a name="select-the-storage-account-to-use-for-dataflow-storage"></a>Seleccione la cuenta de almacenamiento que se usará para almacenamiento de flujo de datos
Si una cuenta de almacenamiento aún no se ha asociado al entorno, aparece un cuadro de diálogo **Vincular a lago de datos**. Deberá iniciar sesión y encontrar el lago de datos que creó en los pasos anteriores. En este ejemplo, no se asocia ningún lago de datos al entorno y por tanto aparece un mensaje para agregar uno. 


1. Seleccione cuenta de almacenamiento.

    La pantalla **Seleccionar cuenta de almacenamiento** aparece.
    
    ![Seleccionar cuenta de almacenamiento](media/select-storage-account.png)
    
2. Seleccione el **Identificador de la suscripción** de la cuenta de almacenamiento.
3. Seleccione el **Nombre de grupo de recursos** en el que la cuenta de almacenamiento se creó.
4. Especifique el **Nombre de la cuenta de almacenamiento**.
5. Seleccione **Guardar**.

Una vez que estos pasos se completan correctamente, la cuenta de Azure Data Lake Storage Gen2 está conectada con flujos de datos de Power Platform y puede continuar creando un flujo de datos.

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones
Hay algunas consideraciones y limitaciones a tener presentes para trabajar con almacenamiento de flujo de datos:
- No se admite la vinculación de una cuenta de Azure Data Lake Store Gen 2 para almacenamiento de flujo de datos en el entorno predeterminado.
- Una vez que una ubicación de almacenamiento de flujo de datos está configurada para un flujo de datos, no se puede cambiar.
- De forma predeterminada, cualquier miembro del entorno puede tener acceso a los datos de flujo de datos con el Conector de flujos de datos de Power Platform. Sin embargo, solo los propietarios de un flujo de datos podrán tener acceso a sus archivos directamente en Azure Data Lake Storage Gen2. Para autorizar que usuarios adicionales obtengan acceso a los datos de flujo de datos directamente en el lago, debe autorizarlos en la **Carpeta de CDM** del lago de datos o en el propio lago de datos.
- Cuando se elimina un flujo de datos, su **Carpeta de CDM** en el lago también se eliminará. 

> [!IMPORTANT]
> No debería cambiar los archivos creados por flujos de datos en el lago de su organización o agregar archivos a la **Carpeta de CDM**de un flujo de datos. El cambio de los archivos podría afectar negativamente a flujos de datos o modificar su comportamiento y no se admite. Los flujos de datos de Power Platform sólo conceden acceso a los archivos que crea en el lago. Si autoriza a otros usuarios o servicios al filesystem usado por flujos de datos de Power Platform, solo concederá acceso de lectura a los archivos o a las carpetas de ese filesystem.

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes
*¿Qué sucede si había creado anteriormente flujos de datos en Azure Data Lake Storage Gen2 de mi organización y deseo cambiar su ubicación de almacenamiento?*

   No puede cambiar la ubicación de almacenamiento de un flujo de datos después de que se ha creado.

*¿Cuándo puedo cambiar la ubicación de almacenamiento de flujo de datos de un entorno?*

   Cambiar la ubicación de almacenamiento de flujo de datos del entorno no se admite actualmente. 

## <a name="next-steps"></a>Pasos siguientes
Este artículo proporcionó instrucciones sobre cómo conectar una cuenta de Azure Data Lake Storage Gen2 para almacenamiento de flujo de datos. 

Para obtener más información sobre flujos de datos, el Common Data Model, y Azure Data Lake Storage Gen2, consulte estos artículos:
- [Preparación de los datos de autoservicio con flujos de datos](https://go.microsoft.com/fwlink/?linkid=2099972)
- [Creación y uso de flujos de datos en PowerApps](https://go.microsoft.com/fwlink/?linkid=2100076)
- [Conexión a Azure Data Lake Storage Gen2 para el almacenamiento del flujo de datos](https://go.microsoft.com/fwlink/?linkid=2099973)
- [Agregar datos a una entidad en Common Data Service](https://go.microsoft.com/fwlink/?linkid=2100075)

Para obtener más información sobre Azure Storage, consulte este artículo:
- [Guía de seguridad de Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-security-guide)

Para obtener más información sobre el Common Data Model, consulte estos artículos:
- [Common Data Model - visión general](https://docs.microsoft.com/powerapps/common-data-model/overview) 
- [Carpetas de Common Data Model](https://go.microsoft.com/fwlink/?linkid=2045304)
- [Definición del archivo de modelo de CDM](https://go.microsoft.com/fwlink/?linkid=2045521)

Puede formular preguntas en la [Comunidad de PowerApps](https://go.microsoft.com/fwlink/?linkid=2099971).
