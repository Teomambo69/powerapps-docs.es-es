---
title: 'Ejemplo: Exportación e importación de datos mediante la asignación de datos complejos (Common Data Service para aplicaciones) | Microsoft Docs'
description: Este ejemplo muestra cómo crear un mapa de datos y exportarlo
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-export-and-import-a-data-map"></a>Ejemplo: exportar e importar una asignación de datos

Este ejemplo muestra cómo crear una asignación de importación (asignación de datos) en Common Data Service para aplicaciones, exportarla como datos con formato XML, importar las asignaciones modificadas y crear una nueva asignación de importación en CDS for Apps basada en las asignaciones importadas. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ExportImportDataMap).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `BulkDeleteRequest` está diseñado para usarse en un escenario donde contenga los datos necesarios para crear la solicitud de eliminación en masa.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización. 
2. El método `CreateImportMapping` crea el registro de la asignación de importación.
3. El método `RetrieveMappingXML` exporta la asignación que se va a crear.
4. El método `ChangeMappingName` analiza el XML para cambiar el atributo de nombre.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.


### <a name="see-also"></a>Vea también

[Importar datos](../../import-data.md)<br />
[Preparar archivos de origen para importar](../../prepare-source-files-import.md)<br />
[Crear asignaciones de datos para importar](../../create-data-maps-for-import.md)<br />
[Agregar asignaciones de transformación para la importación](../../add-transformation-mappings-import.md)<br />
[Configurar la importación de datos](../../configure-data-import.md)<br />
[Ejecutar importación de datos](../../run-data-import.md)<br />
[Entidades de importación de datos](../../data-import-entities.md)<br />
[Ejemplo: importar datos mediante la asignación de datos complejos](import-data-complex-data-map.md)<br />
