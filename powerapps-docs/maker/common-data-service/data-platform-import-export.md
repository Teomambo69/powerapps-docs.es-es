---
title: Importar o exportar datos desde Common Data Service for Apps
description: Uso de las funciones Obtener datos desde Excel y Exportar datos para importar y exportar datos de forma masiva desde archivos de Excel o CSV a las entidades de Common Data Service (CDS) for Apps
author: sabinn-msft
ms.service: powerapps
ms.topic: conceptual
ms.component: cds
ms.date: 05/14/2018
ms.author: sabinn
ms.openlocfilehash: 7f3e16be5bba1874759e0f9e40dc455f1e29c2bc
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697653"
---
# <a name="import-or-export-data-from-the-common-data-service-for-apps"></a>Importar o exportar datos desde Common Data Service for Apps

Si quiere la capacidad de importar y exportar datos de forma masiva desde archivos de Excel o CSV, puede usar las características Obtener datos desde Excel y Exportar datos para entornos actualizados de Common Data Service (CDS) for Apps.

Hay dos maneras de importar archivos a entidades desde un archivo de Excel o CSV.

## <a name="option-1-import-by-creating-and-modifying-a-file-template"></a>Opción 1: Importación mediante la creación y modificación de una plantilla de archivo

Todas las entidades tienen campos obligatorios que deben existir en el archivo de entrada. Para obtener un enfoque más sencillo, se recomienda crear una plantilla; para ello, exporte primero los datos de la entidad y use el mismo archivo (modificado con sus datos) para importar los datos a la entidad. Esto ahorrará tiempo y esfuerzo a la hora de tener en cuenta los campos obligatorios para cada entidad.

1. Prepare la plantilla de archivo.

    - Para empezar, exporte los datos de entidad al archivo .csv mediante los pasos descritos en Exportar datos a CSV.
    - Defina un plan para garantizar la unicidad de los datos, ya sea mediante claves principales o claves alternativas.
    - Consulte la sección siguiente sobre cómo garantizar la unicidad antes de importar los datos a la entidad.

1. Modifique el archivo con los datos.

    - Copie los datos desde el archivo de Excel o CSV a la plantilla que acaba de crear.

1. Importe el archivo.
    - En [powerapps.com](https://web.powerapps.com/), expanda la sección **Datos** y pulse o haga clic en **Entidades** en el panel de navegación de la izquierda.
    - Seleccione la entidad a la que quiera importar los datos.
    - Haga clic en el botón de puntos suspensivos o el menú situado en la parte superior y seleccione **Obtener datos** y pulse o haga clic en **Obtener datos desde Excel**.

> [!NOTE]
> Para importar datos a más de una entidad, en el menú situado en la parte superior, seleccione **Obtener datos** y pulse o haga clic en **Obtener datos desde Excel**. Podrá elegir varias entidades y pulsar **Siguiente**.

![Ejemplo de importación de datos a la entidad Cuenta](./media/data-platform-import-export/import-data-to-account.png)

- Esto le llevará a la pantalla **Importar datos**, donde puede elegir importar los datos a través de un archivo de Excel o CSV.
- Pulse o haga clic en **Cargar**.
- Seleccione el archivo y siga las indicaciones para iniciar la carga del archivo.

![Ejemplo de carga de un archivo a la entidad Cuenta](./media/data-platform-import-export/upload-account.png)

- Una vez cargado el archivo y cuando el estado de asignación sea de color verde, haga clic en **Importar** en la esquina superior derecha. Si se producen errores durante la asignación, consulte la sección siguiente para desplazarse a los errores de asignación y corregirlos.

![Ejemplo de asignación de estado correcta y botón Importar](./media/data-platform-import-export/success-map-imp.png)

- Cuando la **importación se realice correctamente**, mostrará el total de inserciones y actualizaciones.

![Ejemplo de importación correcta en el que se muestra el número de inserciones y actualizaciones](./media/data-platform-import-export/success-imp-insert.png)

> [!NOTE]
> Se usa la lógica de Upsert (actualización o inserción) para actualizar el registro si ya existe, o bien para insertar uno nuevo.

## <a name="option-2-import-by-bringing-your-own-source-file"></a>Opción 2: Importar con un archivo de origen propio

Si es un usuario avanzado y está familiarizado con los campos obligatorios para una entidad determinada para la entidad Common Data Service for Apps, puede definir su propio archivo de origen de Excel o CSV, y seguir los pasos documentados en **Importar el archivo**

## <a name="navigating-mapping-errors"></a>Navegar por los errores de asignación

Si se producen errores de asignación, después de cargar el archivo, haga clic en **Asignación de estado** y siga estos pasos para inspeccionar y corregir los errores de asignación de campos.

- Use la lista desplegable de la derecha, en **Mostrar**, para desplazarse por los **Campos no asignados** o **Campos con error**, o bien los **Campos obligatorios**.

> [!TIP]
> En función de si recibe una advertencia o un error, comience con la inspección de los **Campos no asignados** o **Campos con error** mediante la experiencia de listas desplegables de **Asignaciones de campos**.

![Ejemplo de una coincidencia parcial debido a advertencias con las asignaciones de campos](./media/data-platform-import-export/partial-match.png)

![Ejemplo de navegación por los problemas de asignación de campos](./media/data-platform-import-export/navigate-mappings.png)

![ Ejemplo de inspección y corrección de las advertencias con las asignaciones de campos](./media/data-platform-import-export/inspect-warnings.png)

- Una vez corregidos todos los errores o advertencias, haga clic en **Guardar cambios** en la esquina superior derecha, lo que debería llevarle de vuelta a la pantalla **Importar datos**.
- Cuando en la columna **Estado de asignación** se indique **Completado** en color verde, haga clic en **Importar** en la esquina superior derecha.
- Cuando reciba el mensaje **La importación se realizó correctamente**, se mostrará el total de inserciones y actualizaciones.

## <a name="ensuring-uniqueness-while-importing-data-into-entity-from-excel-or-csv"></a>Asegurar la unicidad al importar datos a la entidad desde Excel o CSV

Las entidades de Common Data Service for Apps usan una clave principal para identificar los registros de forma única dentro de una tabla de entidad CDS. La clave principal de una entidad CDS es un identificador único global (GUID) y forma la base predeterminada para la identificación de los registros. Las operaciones de datos como la importación de datos a la entidad CDS detectarán las claves principales predeterminadas.

Ejemplo: la clave principal de la entidad Cuenta es accountid

![Archivo de exportación de ejemplo desde la entidad Cuenta en el se que muestra accountid como clave principal](./media/data-platform-import-export/export-pk.png)

En ocasiones, una clave principal puede no ser suficiente o satisfacer las necesidades mientras se integran datos desde un origen externo. Para este fin, CDS permite definir claves alternativas para identificar de forma exclusiva un registro en lugar de la clave principal.

Ejemplo: para la entidad Cuenta, se podría establecer "transactioncurrencyid" como una clave alternativa mediante la identificación basada en una clave natural (por ejemplo, use "Dólar estadounidense" en lugar de un valor GUID de *88c6c893-5b45-e811-a953-000d3a33bcb9* mostrado anteriormente). También puede elegir el símbolo o el nombre de moneda como claves.

![Ejemplo de creación de una clave alternativa en la entidad Moneda](./media/data-platform-import-export/create-ak.png)

![Archivo de exportación de ejemplo desde la entidad Cuenta en el se que muestra el nombre de moneda como clave natural](./media/data-platform-import-export/export-nk.png)

El usuario puede seguir usando las claves principales como identificador después de especificar las claves alternativas. Por tanto, en el ejemplo anterior, el primer archivo sigue siendo válido siempre que los GUID proporcionados sean datos válidos.

## <a name="export-data-to-csv"></a>Exportar datos a CSV

Puede realizar una única exportación de datos desde una entidad estándar o una personalizada, y puede exportar datos de más de una entidad a la vez. Si exporta datos de más de una entidad, cada entidad se exporta a su propio archivo .csv de Microsoft.

1. En [powerapps.com](https://web.powerapps.com/), expanda la sección **Datos** y pulse o haga clic en **Entidades** en el panel de navegación de la izquierda.
1. Seleccione la entidad desde la que quiera exportar los datos.
1. Haga clic en el botón de puntos suspensivos o el menú situado en la parte superior y seleccione **Exportar** y pulse o haga clic en **Datos**.

    ![Ejemplo de exportación de datos desde la entidad Cuenta](./media/data-platform-import-export/export-account.png)

    > [!NOTE]
    > Para exportar datos de varias entidades, en el menú situado en la parte superior, seleccione **Exportar** y pulse o haga clic en **Datos**. Podrá elegir varias entidades.

1. Una vez completada correctamente la exportación, debería poder **Descargar datos exportados**, lo que le proporcionará un vínculo al archivo CSV que se puede descargar.

    ![Ejemplo de exportación en el que se muestra una exportación correcta con el archivo de vínculo de descarga](./media/data-platform-import-export/export-success.png)

## <a name="unsupported-data-types"></a>Tipos de datos no admitidos

No se admiten los tipos de datos siguientes:

- Zona horaria
- Conjunto de opciones de selección múltiple
- Imagen
