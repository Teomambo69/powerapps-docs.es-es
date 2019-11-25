---
title: Configurar importación de datos (Common Data Service) | Microsoft Docs
description: La información de configuración que se necesita para importar datos se incluye en la entidad de importación de datos y la entidad del archivo de origen.
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
ms.openlocfilehash: de387cf362a8cef5971f7abf16afdd06a07cb32f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753032"
---
# <a name="configure-data-import"></a>Configurar la importación de datos

<!-- 
Was Mike Carter's

https://docs.microsoft.com/dynamics365/customer-engagement/developer/configure-data-import 

Child topic of 
powerapps-docs/developer/common-data-service/import-data.md
-->

La información de configuración que se necesita para importar datos se incluye en la entidad de importación de datos (`Import`) y la entidad del archivo de origen (`ImportFile`).  
  
 Para configurar la importación de datos, haga lo siguiente:  
  
- Use el atributo de `Import.ModeCode` para especificar si crear o actualizar los datos durante la importación. Si usa enlaces de tipo de compilación, puede usar la enumeración `ImportModeCode`. Para obtener una lista de valores de ModeCode, consulte los valores de lista desplegable para esta entidad. Para ver los metadatos de las entidades de su organización, instale la solución Explorador de metadatos que se describe en [Exploración de los metadatos de su organización](/dynamics365/customer-engagement/developer/browse-your-metadata). También puede examinar la documentación de referencia para las entidades en la [Referencia de entidad](/dynamics365/customer-engagement/developer/about-entity-reference).  
  
- Use el atributo de `ImportFile.FileTypeCode` para especificar el tipo de archivo de importación. Si usa enlaces de tipo de compilación, puede usar la enumeración `ImportFileType`. Para obtener una lista de valores de FileTypeCode, consulte los valores de lista desplegable para esta entidad.  
  
- Use el atributo `ImportFile.DataDelimiterCode` para especificar el delimitador de datos de un solo carácter en el archivo de importación. Si usa enlaces de tipo de compilación, puede usar la enumeración `ImportDataDelimiter`. Para obtener una lista de valores de ImportDataDelimiter, consulte los valores de lista desplegable para esta entidad.  
  
- Use el atributo `ImportFile.FieldDelimiterCode` para especificar el delimitador de campos de un solo carácter en el archivo de importación. Si usa enlaces de tipo de compilación, puede usar la enumeración `ImportFieldDelimiter`. Para obtener una lista de valores de FieldDelimiterCode, consulte los valores de lista desplegable para esta entidad.  
  
- Establezca `ImportFile.IsFirstRowHeader` en `true` para indicar que la primera fila del archivo de origen contiene encabezados de columna o en `false` para indicar que la primera fila contiene datos reales. Si se establece en `false`, se generan encabezados de columna predeterminados.  
  
- Establezca `ImportFile.ImportId` en el Id. de la importación (importación de datos) con la que se asocia el archivo de importación.  
  
- Establezca `ImportFile.ImportMapId` en el Id. del mapa de importación asociado (asignación de datos).  
  
- Establezca `ImportFile.EnableDuplicateDetection` en `true` para habilitar la detección de duplicados durante la importación de datos.  
  
- Lea el contenido del archivo de origen en el `ImportFile.Content`.  
  
> [!IMPORTANT]
>  No se recomienda actualizar registros utilizando la importación de datos mediante programación. Para actualizar, use las capacidades de exportación e importación de los datos de la aplicación web de Common Data Service. Use **Exportar a Excel** para exportar registros a un archivo de hoja de cálculo XML 2003 (.xml). Este es el único tipo de archivo de origen válido para el modo de actualización. Volver a importar los datos desde el archivo de origen de hoja de cálculo XML 2003 (.xml) garantiza que la integridad de los datos en Common Data Service se mantenga. Para importar datos actualizados, utilice el Asistente para la importación de datos de Common Data Service. Para obtener más información sobre el Asistente para la importación de datos, consulte la Ayuda de Common Data Service.  
 
### <a name="see-also"></a>Vea también

[Importar datos](import-data.md)<br />
[Entrada de blog: Cómo importar los datos adjuntos mediante programación](https://blogs.msdn.com/b/crm/archive/2012/08/06/how-to-import-attachments-programmatically.aspx)<br />
[Preparar archivos de origen para importar](prepare-source-files-import.md)<br />
[Crear asignaciones de datos para importar](create-data-maps-for-import.md)<br />
[Agregar asignaciones de transformación para la importación](add-transformation-mappings-import.md)<br />
[Ejecutar importación de datos](run-data-import.md)<br />
[Entidades de importación de datos](data-import-entities.md)<br />
[Ejemplo: exportar e importar una asignación de datos](org-service/samples/export-import-data-map.md)<br />
[Ejemplo: importar datos mediante la asignación de datos complejos](org-service/samples/import-data-complex-data-map.md)<br />