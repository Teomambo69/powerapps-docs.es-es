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
ms.assetid: null
caps.latest.revision: null
ms.author: matp
manager: kvivek
tags: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
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
Antes de configurar Power BI con una cuenta Azure Data Lake Storage Gen2, debe crear y configurar una cuenta de almacenamiento. A continuación se enumeran los requisitos para flujos de datos de Power Platform:
1.  La cuenta de almacenamiento se debe crear en el mismo inquilino de Azure Active Directory que su inquilino de PowerApps.
2.  Es recomendable que la cuenta de almacenamiento se cree en la misma región que el entorno de PowerApps donde planea usarla. Para determinar dónde está el entorno de PowerApps, póngase en contacto con el administrador del entorno.
3.  La cuenta de almacenamiento debe tener la característica de espacio de nombres jerárquico habilitada.
4.  Deben concederse un rol de propietario en la cuenta de almacenamiento.

En las siguientes secciones se indican los pasos necesarios para configurar su cuenta de Azure Data Lake Storage Gen2.

## <a name="create-the-storage-account"></a>Crear la cuenta de almacenamiento
Siga los pasos en [Crear una cuenta de almacenamiento Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account).
1.  Asegúrese de seleccionar la misma ubicación que el inquilino de Power BI y de establecer el almacenamiento como StorageV2 (propósito general v2).
2.  Asegúrese de habilitar la característica de espacio de nombres jerárquico. 
3.  Se recomienda establecer el ajuste de replicación como Almacenamiento con redundancia geográfica de acceso de lectura (RA-GRS).



<!--from editor: I haven't heard of Athena before. Is it the Amazon service, https://aws.amazon.com/athena/? If so, it probably should be identified as Amazon at first mention. -->


## <a name="create-a-cross-origin-resource-sharing-cors-rule-for-the-athena-service"></a>Crear una regla de Uso compartido de recursos de origen cruzado (CORS) para el servicio Athena

> [!NOTE]
> Los flujos de datos Power Platform aprovechan el servicio Athena para conectar un lago de datos con un entorno de PowerApps. En esta sección, se le pide que conceda al servicio Athena un rol a la cuenta de almacenamiento para que pueda configurarse para uso de flujo de datos.

A continuación, debe habilitar el servicio Athena para obtener acceso a la cuenta de almacenamiento a través del explorador web y el portal de PowerApps. Los exploradores web implementan una restricción de seguridad conocida como [directiva del mismo origen](http://www.w3.org/Security/wiki/Same_Origin_Policy) que evita que una página web llame a API en otro dominio; CORS proporciona una forma segura de permitir que un dominio (el dominio de origen) llame a las API de otro dominio. Para obtener más información sobre CORS, vea la [Especificación CORS](http://www.w3.org/TR/cors/).

Siga los pasos en la cuenta de almacenamiento que acaba de crear en la página de configuración del portal de Azure. En el elemento de menú CORS, seleccione la sección Servicio de blob y especifique estos detalles. 

|Configuración  |Value  |
|---------|---------|
|Orígenes permitidos   | https://athena-ui-prod.trafficmanager.net     |
|Métodos permitidos   |  SUPRIMIR, OBTENER, DIRIGIR, COMBINAR, PUBLICAR, OPCIONES, PONER, PARCHE   |
|Encabezados permitidos   | *    |
|Encabezados expuestos   | *    |
|Edad máxima |   *  |


La imagen siguiente muestra la regla de CORS configurada para el servicio Athena.

![Regla de CORS](media/dataflows-cores-rule.png)

## <a name="connect-your-azure-data-lake-storage-gen2-to-powerapps"></a>Conectar Azure Data Lake Storage Gen2 con PowerApps
Una vez que haya configurado su cuenta de Azure Data Lake Storage Gen2 en el portal de Azure, estará listo para conectarlo a un flujo de datos específico o a un entorno de PowerApps. La conexión del lago a un entorno permite que otros fabricantes y administradores del entorno creen flujos de datos que almacenan sus datos en el lago de la organización también. 

Para conectar su cuenta de Azure Data Lake Storage Gen2 con el flujo de datos, siga estos pasos:
1.  Inicie sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) y compruebe en qué entorno está. El selector de entorno se encuentra en la parte derecha del encabezado. 
2. En el panel de navegación de la izquierda, seleccione la flecha abajo junto a **Datos**.

   ![Pestaña Datos del portal del creador de PowerApps](media/powerapps-portal-data.png)

3. En la lista que aparece, seleccione **Flujos de datos** y en la barra de comandos seleccione **Nuevo flujo de datos**.

   ![Crear un flujo de datos nuevo](media/new-dataflow.png) 

4. Seleccione las entidades analíticas que desee. Estas entidades indican qué datos desea almacenar en la cuenta Azure Data Lake Store Gen 2 de la organización. 

   ![Seleccionar entidades analíticas](media/select-analytical-entities.png)

## <a name="select-the-storage-account-to-use-for-dataflow-storage"></a>Seleccione la cuenta de almacenamiento que se usará para almacenamiento de flujo de datos
Si una cuenta de almacenamiento aún no se ha asociado al entorno, aparece un cuadro de diálogo **Vincular a lago de datos**. Deberá iniciar sesión y encontrar el lago de datos que creó en los pasos anteriores. En este ejemplo, no se asocia ningún lago de datos al entorno y por tanto aparece un mensaje para agregar uno. 



<!--from editor: Should "storage account" be in bold because it's something the user has to select? --"

1. Select storage account.

    The **Select Storage Account** screen appears.
    
    ![Select storage account](media/select-storage-account.png)
    
2. Select the **Subscription ID** of the storage account.
3. Select the **Resource group name** in which the storage account was created.
4. Enter the **Storage account name**.
5. Select **Save**.

Once these steps are successfully completed, your Azure Data Lake Storage Gen2 account is connected to Power Platform Dataflows and you can continue to create a dataflow.

## Considerations and limitations
There are a few considerations and limitations to keep in mind when working with your dataflow storage:
- Linking an Azure Data Lake Store Gen2 account for dataflow storage is not supported in the default environment.
- Once a dataflow storage location is configured for a dataflow, it can't be changed.
- By default, any member of the environment can access dataflow data using the Power Platform Dataflows Connector. However, only the owners of a dataflow can access its files directly in Azure Data Lake Storage Gen2. To authorize additional people to access the dataflows data directly in the lake, you must authorize them to the dataflow’s CDM folder in the data lake or the data lake itself.
- When a dataflow is deleted, its CDM folder in the lake will also be deleted. 

> [!IMPORTANT]
> You shouldn't change files created by dataflows in your organization’s lake or add files to a dataflow’s CDM folder. Changing files might damage dataflows or alter their behavior and is not supported. Power Platform Dataflows only grants read access to files it creates in the lake. If you authorize other people or services to the filesystem used by Power Platform Dataflows, only grant them read access to files or folders in that filesystem.

## Frequently asked questions
*What if I had previously created dataflows in my organization’s Azure Data Lake Storage Gen2 and would like to change their storage location?*

   You can't change the storage location of a dataflow after it was created.

*When can I change the dataflow storage location of an environment?*

   Changing the environment's dataflow storage location is not currently supported. 

## Next steps
This article provided guidance about how to connect an Azure Data Lake Storage Gen2 account for dataflow storage. 

For more information about dataflows, the Common Data Model, and Azure Data Lake Storage Gen2, see these articles:
- [Self-service data prep with dataflows](https://go.microsoft.com/fwlink/?linkid=2099972)
- [Creating and using dataflows in PowerApps](https://go.microsoft.com/fwlink/?linkid=2100076)
- [Connect Azure Data Lake Storage Gen2 for dataflow storage](https://go.microsoft.com/fwlink/?linkid=2099973)
- [Add data to an entity in Common Data Service](https://go.microsoft.com/fwlink/?linkid=2100075)

For more information about Azure storage, see this article:
- [Azure Storage security guide](https://docs.microsoft.com/azure/storage/common/storage-security-guide)

For more information about the Common Data Model, see these articles:
- [Common Data Model - overview](https://docs.microsoft.com/powerapps/common-data-model/overview) 
- [Common Data Model folders](https://go.microsoft.com/fwlink/?linkid=2045304)
- [CDM model file definition](https://go.microsoft.com/fwlink/?linkid=2045521)

You can ask questions in the [PowerApps Community](https://go.microsoft.com/fwlink/?linkid=2099971).
