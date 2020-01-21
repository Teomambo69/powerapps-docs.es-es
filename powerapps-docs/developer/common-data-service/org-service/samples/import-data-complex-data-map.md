---
title: 'Ejemplo: Importar datos mediante la asignación de datos complejos (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo crear nuevos registros mediante la importación de datos
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 721b4da846aaca0433caf8aac8759fb35dd8199d
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934288"
---
# <a name="sample-import-data-using-complex-data-map"></a>Ejemplo: importar datos mediante la asignación de datos complejos

Este ejemplo muestra cómo crear nuevos registros mediante la importación de datos. El ejemplo usa una asignación de datos compleja. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ImportComplexDataMap).

>[!NOTE]
> Los datos de origen para esta muestra se incluyen en el siguiente archivo `ImportComplexDataMap\import accounts.csv`

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito anteriormente, el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. El método `ImportMap` crea una asignación de importación.
1. El método `ColumnMapping` crea una asignación de columna para un campo de tipo `text`.
1. El método `EntityReference` relaciona la asignación de columnas con la asignación de datos.
1. El método `LookUpMapping` crea una asignación de búsqueda a la cuenta primaria.
1. El método `ImportFile` crea un archivo de importación.
1. El método `GetHeaderColumnsImportFileRequest` recupera las columnas de encabezado usadas en el archivo de importación.
1. El método `ParseImportRequest` analiza el archivo de importación. 
1. El método `RetrievedParsedDataImportFileRequest` recupera los datos de la tabla de análisis.
1. El método `TransformImportRequest` transforma la importación.


### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en la [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.


### <a name="see-also"></a>Vea también

[Importar datos](../../import-data.md)<br />
[Preparar archivos de origen para importar](../../prepare-source-files-import.md)<br />
[Crear asignaciones de datos para importar](../../create-data-maps-for-import.md)<br />
[Agregar asignaciones de transformación para la importación](../../add-transformation-mappings-import.md)<br />
[Configurar la importación de datos](../../configure-data-import.md)<br />
[Ejecutar importación de datos](../../run-data-import.md)<br />
[Entidades de importación de datos](../../data-import-entities.md)<br />
[Ejemplo: exportar e importar una asignación de datos](export-import-data-map.md)<br />
