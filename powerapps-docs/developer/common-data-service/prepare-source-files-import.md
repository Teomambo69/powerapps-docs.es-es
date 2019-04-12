---
title: Preparar archivos de origen para la importación (Common Data Service) | Microsoft Docs
description: 'La importación de datos es compatible con archivos de origen con formato de valores separados por comas (.csv), hoja de cálculo XML 2003 (.xml) o archivos de texto.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="prepare-source-files-for-import"></a>Preparar archivos de origen para importar

Antes de que pueda importar datos a Common Data Service debe crear los archivos de origen de datos.  
  
Los archivos de origen de datos que se usan en una importación deben tener el formato de valores separados por comas (.csv), hoja de cálculo XML 2003 (.xml) o archivos de texto. El uso de archivos de origen permite la transferencia de datos desde sistemas de bases de datos que utilizan diferentes formatos a Common Data Service.  
  
Un archivo de origen puede contener datos para un tipo de entidad o varios tipos de entidades, como cuentas y contactos. Para los archivos de origen que contienen datos de varias entidades, debe proporcionar una asignación que incluya la etiqueta `<EntitiesPerFile>`. Establezca el valor de esta etiqueta en múltiple para indicar que hay más de un tipo de entidad en el archivo de origen. Agregue el atributo `Dedupe = “Eliminate”` a la etiqueta `<EntityMap>`. Esto garantiza que, si el archivo contiene filas duplicadas para el tipo de entidad, se usa una sola fila para minimizar los errores relacionados con las búsquedas.  
  
Puede descargar un ejemplo de un mapa de datos con varios tipos de entidades en [Descargas de Microsoft: DataImportMaps.zip](http://download.microsoft.com/download/D/5/F/D5F73E15-439B-4EBC-BFFB-C6837B146C76/DataImportMaps.zip). Mire el archivo `MapForSalesForceContactAccount.xml`.  
  
 Los valores de los campos del archivo de origen pueden separarse mediante comas, tabulaciones u otros caracteres que se definen mediante el atributo `ImportFile.FieldDelimiterCode`.  
  
> [!NOTE]
>  No use caracteres no imprimibles, **null** (\0) o break (\b), como delimitadores para los valores de los campos.  
  
 La primera fila del archivo de origen debe contener los encabezados de columna. Si no incluye los encabezados, use el atributo `ImportFile.IsFirstRowHeader` para especificar que la primera fila representa datos reales. En este caso, se crean encabezados de columna predeterminados con los nombres Col1, Col2, etc.  

### <a name="see-also"></a>Vea también

[Importar datos](import-data.md)<br />
[Crear asignaciones de datos para importar](create-data-maps-for-import.md)<br />
[Agregar asignaciones de transformación para la importación](add-transformation-mappings-import.md)<br />
[Configurar la importación de datos](configure-data-import.md)<br />
[Ejecutar importación de datos](run-data-import.md)<br />
[Entidades de importación de datos](data-import-entities.md)<br />
[Ejemplo: exportar e importar una asignación de datos](org-service/samples/export-import-data-map.md)<br />
[Ejemplo: importar datos mediante la asignación de datos complejos](org-service/samples/import-data-complex-data-map.md)<br />