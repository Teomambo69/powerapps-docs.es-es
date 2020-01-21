---
title: Creación y uso de flujos de datos en Power Apps | MicrosoftDocs
description: Aprenda a crear y utilizar flujos de datos en Power Apps
ms.custom: ''
ms.date: 12/05/2019
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
ms.openlocfilehash: 03cdea2884f5ae4ac889218c4d9b87a48f1f8d81
ms.sourcegitcommit: c2de40124037825308fbccf71f3a221198a928f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "2944363"
---
# <a name="create-and-use-dataflows-in-power-apps"></a>Creación y uso de flujos de datos en Power Apps

Con la preparación de datos avanzada disponible en Power Apps, puede crear una colección de datos llamada flujo de datos, que puede usar posteriormente para conectar con datos empresariales de varios orígenes, limpiar datos, transformarlos y, a continuación cargarlos a Common Data Service o la cuenta de almacenamiento de Azure Data Lake Gen 2 de la organización.

Un flujo de datos es una colección de entidades (las entidades son similares a las tablas) que se crean y se administran en entornos en el servicio de Power Apps. Puede agregar y editar as entidades en su flujo de datos, así como administrar programaciones de actualización de datos, directamente desde el entorno en el que se creó el flujo de datos.

Una vez que cree un flujo de datos en el portal de Power Apps, puede obtener datos de este utilizando el conector Common Data Service o el conector de flujo de datos de Power BI Desktop, en función del destino que eligió al crear el flujo de datos.

Hay tres pasos primarios para usar un flujo de datos:

1.  Cree el flujo de datos en el portal de Power Apps. Seleccione el destino al que cargar los datos de salida, el origen del que obtener los datos, y pasos de Power Query para transformar los datos mediante herramientas de Microsoft diseñadas para hacerlo directamente.

2.  Programe ejecuciones de flujo de datos. Ésta es la frecuencia con la que el flujo de datos de Power Platform debe actualizar los datos que el flujo de datos cargará y transformará.

3.  Use los datos que cargó en el almacenamiento de destino. Puede crear aplicaciones, flujos, informes Power BI y paneles o conectar directamente a la carpeta Common Data Model del flujo de datos en el lago de su organización mediante servicios de datos de Azure como Azure Data Factory, Azure Databricks o cualquier otro servicio que admita el estándar de carpeta Common Data Model.

Las secciones siguientes examinan cada uno de estos pasos para que pueda estar familiarizado con las herramientas proporcionadas para completar cada paso. 

## <a name="create-a-dataflow"></a>Crear un flujo de datos
Los flujos de datos se crean en un entorno. Por lo tanto, solo podrán verlos y administrarlos desde ese entorno. Además, los individuos que desean obtener datos del flujo de datos deben tener acceso al entorno en el que los creó.

> [!NOTE]
> La creación de flujos de datos no está disponible actualmente con licencias del Plan comunitario de Power Apps.

1.  Inicie sesión en Power Apps, y compruebe en qué entorno está, busque aparece el selector de entorno cerca del lado derecho de la barra de comandos.

    ![Selector de entorno](media/environment-switcher.png)

2.  En el panel de navegación de la izquierda, seleccione la flecha abajo junto a **Datos**.

    ![Seleccionar fecha](media/data-select.png)

3.  En la lista **Datos**, seleccione **Flujos de datos** y, a continuación seleccione **Nuevo flujo de datos**.

    ![Crear un flujo de datos](media/create-a-dataflow.png)

4.  En la página **Seleccionar destino de carga**, seleccione el almacenamiento de destino donde desea almacenar entidades. Los flujos de datos pueden almacenar entidades en Common Data Service o en la cuenta de Azure Data Lake Storage de la organización. Una vez que seleccione un destino al que cargar datos, escriba un **Nombre** para el flujo de datos y, a continuación seleccione **Crear**.

    ![Seleccionar destino de carga](media/select-load-target.png)

     > [!IMPORTANT]
     > Hay un solo propietario de cualquier flujo de datos - la persona que lo creó. Solo el propietario puede editar el flujo de datos. La licencia y el acceso a los datos creadas por el flujo de datos dependen del destino al que cargó los datos. Los datos cargados en Common Data Service estarán disponibles a través del conector de Common Data Service y requieren que la persona que tiene acceso a los datos está autorizada en Common Data Service.
     > Los datos cargados en la cuenta de almacenamiento de Azure Data Lake Gen 2 de la organización están accesibles desde el conector de flujo de datos de Power Platform y el acceso a ellos requiere suscripción en el entorno que se crearon.

5. En la página **Elegir origen de datos**, seleccione el origen de datos donde se almacenan las entidades, y después seleccione **Crear**. La selección de orígenes de datos mostrada le permite crear entidades de flujo de datos. 

    ![Elegir un origen de datos](media/choose-data-source.png)

6. Después de seleccionar un origen de datos, se le pedirá que proporcione los valores de conexión, incluida la cuenta para usar al conectarse al origen de datos.

    ![Conectar a origen de datos](media/data-source-provide-cred.png)

7. Una vez conectado, seleccione los datos que desea usar para la entidad. Cuando seleccione datos y un origen, el servicio de flujo de datos de Power Platform volverá a conectar posteriormente al origen de datos para mantener los datos en el flujo de datos actualizado, con la frecuencia que seleccione más adelante en el proceso de instalación.


    ![Elegir datos](media/choose-data.png)

Ahora que ha seleccionado los datos para usar en la entidad, puede usar el editor de flujo de datos para dar forma o transformar los datos al formato necesario para usarlos en el flujo de datos.

## <a name="use-the-dataflow-editor-to-shape-or-transform-data"></a>Use el editor de flujo de datos para dar forma o transformar datos
Puede dar forma a la selección de datos en un formulario que funcione mejor para su entidad mediante una experiencia de edición de Power Query, similar al editor de Power Query en Power BI Desktop. Para obtener más información acerca de Power Query, consulte [Información general de consultas en Power BI Desktop](/power-bi/desktop-query-overview).

Si desea ver el código que el editor de consultas está creando con cada paso, o si desea crear su propio código de formato, puede usar el editor avanzado.

![Editor avanzado](media/advanced-editor.png)

## <a name="dataflows-and-the-common-data-model"></a>Flujos de datos y Common Data Model 
Las entidades de flujos de datos incluyen nuevas herramientas para asignar fácilmente los datos empresariales el Common Data Model, enriquecerlos con Microsoft y datos de terceros, y obtener acceso simplificado al aprendizaje automático. Estas nuevas capacidades se pueden aprovechar para proporcionar ideas inteligentes y procesable a los datos profesionales. Cuando haya finalizado las transformaciones en el paso de edición de consultas descrito más abajo, puede asignar columnas de las tablas de origen de datos a campos de entidades estándar definidas por Common Data Model. Las entidades estándar tienen un esquema conocido definido por Common Data Model.

Para obtener más información acerca de este método, y sobre Common Data Model, consulte [Common Data Model](/powerapps/common-data-model/overview).

Para aprovechar Common Data Model con el flujo de datos, seleccione la transformación **Asignar a estándar** en el diálogo **Editar consultas**. En la pantalla **Asignar entidades** que aparece, seleccione la entidad estándar que desee asignar.

![Asignar a entidad estándar](media/map-to-standard-entity.png)

Cuando asigna una columna de origen a un campo estándar, se produce lo siguiente:

1.  La columna de origen toma el nombre del campo estándar (la columna cambia de nombre si los nombres son diferentes). 

2.  La columna de origen obtiene el tipo de datos del campo estándar. 

Para mantener la entidad estándar del Common Data Model, todos los campos estándar que no se asignan obtienen valores *Null*.

Todas las columnas de origen que no están asignadas permanecen como están para asegurarse de que el resultado de la asignación es una entidad estándar con campos personalizados.

Cuando haya finalizado las selecciones y la entidad y la configuración de datos estén completas, estará listo para el siguiente paso, que es seleccionar la frecuencia de actualización del flujo de datos.

## <a name="set-the-refresh-frequency"></a>Establecer la frecuencia de actualización
Una vez que se han definido las entidades, le conviene programar la frecuencia de actualización para cada uno de los orígenes de datos conectados.

1. Los flujos de datos usan un proceso de actualización de datos para mantener los datos actualizados. En la **Herramienta de creación de flujo de datos de Power Platform**, puede seleccionar actualizar el flujo de datos manualmente o automáticamente en un intervalo programado que elija. Para programar una actualización automáticamente, seleccione **Actualizar automáticamente**.

   ![Actualizar automáticamente](media/refresh-automatically.png)

2. Escriba la frecuencia de actualización del flujo de datos, la fecha de inicio, y la hora en UTC.

3. Seleccione **Crear.**
<!-- 
## Connect to your dataflow in Power BI Desktop
Once you’ve created your dataflow and you have scheduled the refresh frequency
for each data source that will populate the model, you’re ready for the final task, which is connecting to your dataflow from within Power BI Desktop.

To connect to the dataflow, in Power BI Desktop select **Get Data** > **Power Platform** > **Power Platform dataflows** > **Connect**.

![Connect to the dataflow](media/get-data.png)

Navigate to the environment where you saved your dataflow, select
the dataflow, and then select the entities that you created from the list.

You can also use the search bar, near the top of the window, to quickly find the
name of your dataflow or entities from among many dataflow entities.

When you select the entity and then select the **Load** button, the entities
appear in the **Fields** pane in Power BI Desktop, and appear and behave just
like tables from any other dataset. -->

## <a name="using-dataflows-stored-in-azure-data-lake-storage-gen2"></a>Usar flujos de datos almacenados en Azure Data Lake Storage Gen2
Algunas organizaciones pueden usar su propio almacenamiento para la creación y administración de flujos de datos. Puede integrar flujos de datos con Azure Data Lake Storage Gen2 si sigue los requisitos para configurar la cuenta de almacenamiento correctamente. Más información: [Conexión a Azure Data Lake Storage Gen2 para el almacenamiento del flujo de datos](/power-bi/service-dataflows-connect-azure-data-lake-storage-gen2) 

## <a name="troubleshooting-data-connections"></a>Solución de problemas de conexión de datos
Es posible que haya ocasiones en las que al conectarse a orígenes de datos para ejecuciones de flujos de datos se produzcan problemas. En esta sección se proporcionan sugerencias de solución a los problemas aparecen.

-   **Conector de Salesforce.** El uso de una cuenta de prueba para Salesforce con flujos de datos produce un error de conexión sin información proporcionada. Para solucionar esto, use una cuenta de Salesforce de producción o una cuenta de desarrollador para pruebas.

-   **Conector de SharePoint.** Asegúrese de proporcionar la dirección raíz del sitio de SharePoint, sin subcarpetas o documentos. Por ejemplo, use un vínculo similar a *https://microsoft.sharepoint.com/teams/ObjectModel*.


-   **Conector de archivos JSON.** Puede conectar actualmente a un archivo JSON mediante autenticación básica únicamente. Por ejemplo, no se admite una dirección URL similar a *https://XXXXX.blob.core.windows.net/path/file.json?sv=2019-01-01&si=something&sr=c&sig=123456abcdefg* actualmente.

-   **Azure SQL Data Warehouse.** Los flujos de datos no admiten actualmente autenticación de Azure Active Directory para Azure SQL Data Warehouse. Use autenticación básica para este escenario.

## <a name="next-steps"></a>Pasos siguientes
Los siguientes artículos son útiles para obtener más información y escenarios al usar flujos de datos:

-   [Agregar datos a una entidad en Common Data Service](data-platform-cds-newentity-pq.md)

-   [Uso de flujos de datos con orígenes de datos locales](using-dataflows-with-on-premises-data.md)

-   [Conexión a Azure Data Lake Storage Gen2 para el almacenamiento del flujo de datos](/power-bi/service-dataflows-connect-azure-data-lake-storage-gen2)

Para obtener más información sobre Common Data Model:

-   [Common Data Model - visión general](/powerapps/common-data-model/overview)

-   [Más información sobre el esquema y entidades de Common Data Model en GitHub](https://github.com/Microsoft/CDM)
