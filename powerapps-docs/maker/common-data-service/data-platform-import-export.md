---
title: Importar o exportar datos desde Common Data Service for Apps
description: Importación y exportación masivas de datos desde archivos de Excel o CSV a las entidades de Common Data Service for Apps usando las funcionalidades Obtener datos de Excel y Exportar datos
author: sabinn-msft
ms.service: powerapps
ms.topic: conceptual
ms.component: cds
ms.date: 05/14/2018
ms.author: sabinn
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="import-or-export-data-from-common-data-service-for-apps"></a>Importar o exportar datos desde Common Data Service for Apps

Para importar y exportar datos de forma masiva desde archivos de Microsoft Excel o CSV, use las funciones Obtener datos de archivo de Excel y Exportar datos para entornos actualizados de Common Data Service for Apps.

Existen dos formas de importar archivos en entidades desde archivos de Excel o CSV.

## <a name="option-1-import-by-creating-and-modifying-a-file-template"></a>Opción 1: importar creando y modificando una plantilla de archivo

Cada entidad tiene campos necesarios que deben existir en el archivo de entrada. Se recomienda que cree una plantilla. Primero, exporte los datos de la entidad. Use el mismo archivo (modificado con sus datos) para importar los datos en la entidad. Esta plantilla le permite ahorrar tiempo y esfuerzo. No tendrá que preocuparse por los campos necesarios para cada entidad.

1. Prepare la plantilla de archivo.

    a. Exporte los datos de la entidad al archivo CSV. Siga los pasos de **Exportar datos a CSV**.  
    b. Defina un plan para asegurarse de que los datos sean únicos. Use **claves principales** o **claves alternativas**.  
    c. Consulte las instrucciones en la siguiente sección para asegurarse de que los datos sean únicos antes de importarlos a una entidad. 

1. Modifique el archivo con sus datos.

    - Copie los datos de su archivo de Excel o CSV en la plantilla que acaba de crear.

1. Importe el archivo.  
    a. En [powerapps.com](https://web.powerapps.com/), expanda la sección **Datos**. Seleccione **Entidades** en el panel de navegación izquierdo.  
    b. Seleccione la entidad a la que desea importar los datos.  
    c. Seleccione los puntos suspensivos o el menú de la parte superior. Seleccione **Obtener datos**. Seleccione **Obtener datos de Excel**.  

    > [!NOTE]
    > Para importar datos en más de una entidad, en el menú superior, seleccione **Obtener datos**. Seleccione **Obtener datos de Excel**. Después puede elegir varias entidades y seleccionar **Siguiente**.

    > [!div class="mx-imgBorder"] 
    > ![Ejemplo de importación de datos a una entidad **Cuenta**](./media/data-platform-import-export/import-data-to-account.png)

    d. En la pantalla **Importar datos**, elija si desea importar datos de un archivo de Excel o CSV.  
    e. Seleccione **Cargar**.  
    f. Elija su archivo. Siga las indicaciones para cargar el archivo.  

    > [!div class="mx-imgBorder"] 
    > ![Ejemplo de carga de un archivo en una entidad **Cuenta**](./media/data-platform-import-export/upload-account.png)

    g. Después de cargar el archivo y cuando el **Estado de asignación** sea verde, seleccione **Importar** en la esquina superior derecha. Consulte la siguiente sección para navegar y corregir los errores de asignación.  

    > [!div class="mx-imgBorder"] 
    > ![Ejemplo de un **Estado de asignación** y un botón **Importar** correctos](./media/data-platform-import-export/success-map-imp.png)

    h. Una vez que la importación finalice correctamente, verá el número total de inserciones y actualizaciones.  

    > [!div class="mx-imgBorder"] 
    > ![Ejemplo de una importación correcta que muestra el número de inserciones y de actualizaciones](./media/data-platform-import-export/success-imp-insert.png)

    > [!NOTE]
    > Use la lógica de Upsert (Actualizar o Insertar) para actualizar el registro, si ya existe, o para insertar un nuevo registro.

## <a name="option-2-import-by-bringing-your-own-source-file"></a>Opción 2: Importar incorporando su propio archivo de origen

Si es un usuario avanzado y conoce los campos necesarios para una determinada entidad par Common Data Service for Apps, defina su propio archivo de origen de Excel o CSV. Siga los pasos de **Importar el archivo**.

## <a name="navigate-mapping-errors"></a>Desplazarse por los errores de la asignación

Si obtiene errores de asignación después de cargar el archivo, seleccione **Estado de asignación**. Siga estos pasos para inspeccionar y rectificar los errores de asignación de campos.

1. Use el menú desplegable de la derecha, en **Mostrar**, para desplazarse por **Campos no asignados**, **Campos con errores**o **Campos obligatorios**.

    > [!TIP]
    > En función de si obtiene una advertencia o un error, inspeccione **Campos no asignados** o **Campos con errores** a través del menú desplegable de **Asignaciones de campos**.

    > [!div class="mx-imgBorder"] 
    > ![Ejemplo de una coincidencia parcial debido a las advertencias sobre asignaciones de campos](./media/data-platform-import-export/partial-match.png)

    > [!div class="mx-imgBorder"] 
    > ![Ejemplo de problemas de navegación por la asignación de campos](./media/data-platform-import-export/navigate-mappings.png)

    > [!div class="mx-imgBorder"] 
    > ![Ejemplo de inspeccionar y rectificar advertencias sobre asignaciones de campos](./media/data-platform-import-export/inspect-warnings.png)

2. Cuando resuelva todos los errores y advertencias, seleccione **Guardar cambios** en la esquina superior derecha. Volverá a la pantalla **Importar datos**.
3. Cuando la columna **Estado de asignación** muestre **Completado** en verde, seleccione **Importar** en la esquina superior derecha.
4. Cuando reciba el mensaje **Importe realizada correctamente** se mostrará el total de inserciones y actualizaciones.

## <a name="ensure-uniqueness-when-you-import-data-into-an-entity-from-excel-or-csv"></a>Asegurar la univocidad al importar datos en una entidad de Excel o de CSV

Las entidades de Common Data Service for Apps usan una clave principal para identificar de forma exclusiva los registros dentro de una tabla de entidades de Common Data Service. La clave principal de una entidad de Common Data Service es un identificador único global (GUID). Forma la base predeterminada para la identificación de registro. Las operaciones de datos, como la importación de datos en entidades de Common Data Service, exponen las claves principales predeterminadas.

Ejemplo:  
La clave principal de una entidad **Cuenta** es **accountid**.

   > [!div class="mx-imgBorder"] 
   > ![Archivo de exportación de muestra de una entidad **Cuenta** que muestra **accountid** como clave principal](./media/data-platform-import-export/export-pk.png)

A veces, una clave principal puede que no funcione cuando se integran datos desde un origen externo. Use Common Data Service para definir claves alternativas que identifiquen de forma exclusiva un registro en lugar de la clave principal.

Ejemplo:  
Para una entidad **Cuenta**, puede establecer **transactioncurrencyid** como clave alternativa usando una identificación basada en claves naturales. Por ejemplo, use **Dólar americano** en lugar del valor de GUID **88c6c893-5b45-e811-a953-000d3a33bcb9** mostrado anteriormente. También puede elegir **símbolo de moneda** o **nombre de la moneda** como claves.

   > [!div class="mx-imgBorder"] 
   > ![Ejemplo de crear una clave alternativa en la entidad **Moneda**](./media/data-platform-import-export/create-ak.png)

   > [!div class="mx-imgBorder"] 
   > ![Archivo de exportación de muestra de una entidad **Cuenta** que muestra **nombre de la moneda** como clave natural](./media/data-platform-import-export/export-nk.png)

Los usuarios pueden seguir usando claves principales como identificadores después de especificar claves alternativas. En el ejemplo anterior, el primer archivo sigue siendo válido si los GUID son datos válidos.

## <a name="export-data-to-csv"></a>Exportar datos a CSV

Puede realizar una exportación de datos única desde una entidad estándar o entidad personalizada. También puede exportar datos desde más de una entidad a la vez. Si exporta datos de más de una entidad, cada entidad se exporta en su propio archivo CSV de Microsoft.

1. En [powerapps.com](https://web.powerapps.com/), expanda la sección **Datos**. Seleccione **Entidades** en el panel de navegación izquierdo.
1. Seleccione la entidad de la que desea importar los datos.
1. Seleccione los puntos suspensivos o el menú de la parte superior. Seleccione **Exportar**. Seleccione **Datos**.

    > [!div class="mx-imgBorder"] 
    > ![Ejemplo de exportación de datos desde una entidad **Cuenta**](./media/data-platform-import-export/export-account.png)

    > [!NOTE]
    > Para exportar datos desde varias entidades, en el menú superior, seleccione **Exportar**. Seleccione **Datos**. Puede elegir varias entidades.

1. Cuando la exportación finalice correctamente, podrá **Descargar los datos exportados**. Esta descarga proporciona un vínculo al archivo CSV descargable.

    > [!div class="mx-imgBorder"] 
    > ![Ejemplo de exportación que muestra la exportación correcta con un vínculo al archivo descargable](./media/data-platform-import-export/export-success.png)

## <a name="unsupported-data-types"></a>Tipos de datos no admitidos

Actualmente no se admiten los siguientes tipos de datos.

- Zona horaria
- Conjunto de opciones de selección múltiple
- Imagen
