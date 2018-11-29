---
title: Importar datos (Common Data Service para aplicaciones) | Microsoft Docs
description: 'Si desea importar datos a Common Data Service para aplicaciones, puede usar la función de *importación de datos*. La importación de datos le permite cargar datos de los distintos sistemas de administración de relaciones con el cliente y orígenes de datos en CDS for Apps'
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
# <a name="import-data"></a>Importar datos

<!--
Was Mike Carter


https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/import-data



This should be the generic high-level content to support either web api or org service

Should there be a separate topic for organization service and Web API?
All these functions & actions exist:

RetrieveParsedDataImportFile Function
https://docs.microsoft.com/en-us/dynamics365/customer-engagement/web-api/retrieveparseddataimportfile?view=dynamics-ce-odata-9
GetDistinctValuesImportFile Function
https://docs.microsoft.com/en-us/dynamics365/customer-engagement/web-api/getdistinctvaluesimportfile?view=dynamics-ce-odata-9
ParseImport Function
https://docs.microsoft.com/en-us/dynamics365/customer-engagement/web-api/parseimport?view=dynamics-ce-odata-9
TransformImport Action
https://docs.microsoft.com/en-us/dynamics365/customer-engagement/web-api/transformimport?view=dynamics-ce-odata-9
ImportRecordsImport Action
https://docs.microsoft.com/en-us/dynamics365/customer-engagement/web-api/importrecordsimport?view=dynamics-ce-odata-9
ExportMappingsImportMap Action
https://docs.microsoft.com/en-us/dynamics365/customer-engagement/web-api/exportmappingsimportmap?view=dynamics-ce-odata-9
ImportMappingsImportMap Action
https://docs.microsoft.com/en-us/dynamics365/customer-engagement/web-api/importmappingsimportmap?view=dynamics-ce-odata-9

Or should the core general content simply include both?

-->
Si desea importar datos a Common Data Service para aplicaciones, puede usar la función de *importación de datos*. La importación de datos le permite cargar datos de los distintos sistemas de administración de relaciones con el cliente y orígenes de datos en CDS for Apps. Puede importar datos a los atributos estándar y personalizados de la mayoría de las entidades de negocio y personalizadas. También puede incluir datos relacionados, como notas y datos adjuntos.  
  
El Common Data Service para aplicaciones incluye una herramienta de aplicación web denominada Asistente para la importación de datos. Use esta herramienta para importar registros de datos de uno o varios valores separados por comas (.csv), de una hoja de cálculo XML 2003 (.xml) o de archivos de texto.  
  
 Para obtener más información sobre el Asistente para la importación de datos, consulte la Ayuda de CDS for Apps.  
  
 Los servicios web de Common Data Service para aplicacones ofrecen las siguientes funcionalidades adicionales que no están disponibles en el Asistente para la importación de datos:  
  
- Crear asignaciones de datos que incluyen la asignación compleja de transformación, como la concatenación, la división y la sustitución.  
  
- Definir asignaciones de transformación personalizadas.  
  
- Ver datos de origen almacenados en las tablas de análisis temporal.  
  
- Acceder a registros de errores para crear herramientas de informes de errores personalizadas con vistas mejoradas de registro de errores.  
  
- Ejecutar importaciones de datos mediante scripts de línea de comandos.  
  
- Agregar etiquetas XML de `LookupMap` en la asignación de datos para indicar que la búsqueda de datos se iniciará y realizará en un archivo de origen utilizado en la importación.  
  
- Agregar etiquetas XML de `OwnerMetadata` en la asignación de datos para que coincidan los registros de usuario del archivo de origen con los registros del usuario (usuario del sistema) de CDS for Apps.  
  
- Utilice comprobaciones de validación opcionales.  
  
  > [!NOTE]
  >  La validación no es opcional en el Asistente para la importación de datos.  
  
  Para implementar la importación de datos, normalmente es necesario hacer lo siguiente:  
  
- Crear un archivo de valores separados por comas (CSV), una hoja de cálculo XML 2003 (XMLSS), o un archivo de origen de texto.  
  
- Crear una asignación de datos o use una asignación de datos existente.  
  
- Asociar un archivo de importación con una asignación de datos.  
  
- Cargar el contenido de un archivo de origen en el archivo de importación asociado.  
  
- Analizar el archivo de importación.  
  
- Transformar los datos analizados.  
  
- Cargar los datos transformados al servidor CDS for Apps de destino.  
  
  Puede importar datos de un archivo de origen o de varios archivos de origen. Un archivo de origen puede contener datos de un tipo de entidad o de varios tipos de entidad.  
  
  El análisis, la transformación y la carga de datos se llevada a cabo por los trabajos asincrónicos que se ejecutan en segundo plano.  
  
> [!NOTE]
>  De forma predeterminada, todas las entidades personalizadas se habilitan para la importación. Para determinar si está habilitada una entidad de negocios para la importación, consulte los metadatos de la entidad para la entidad específica. Si una entidad está habilitada para la importación, la propiedad de metadatos de la entidad `IsImportable` se ajusta en `true`. El valor de esta propiedad no puede modificarse para las entidades de negocio originales. <!--[!INCLUDE[metadata_browser](../includes/metadata-browser.md)]-->  


### <a name="see-also"></a>Vea también

[Preparar archivos de origen para importar](prepare-source-files-import.md)<br />
[Crear asignaciones de datos para importar](create-data-maps-for-import.md)<br />
[Agregar asignaciones de transformación para la importación](add-transformation-mappings-import.md)<br />
[Configurar la importación de datos](configure-data-import.md)<br />
[Ejecutar importación de datos](run-data-import.md)<br />
[Entidades de importación de datos](data-import-entities.md)<br />
[Ejemplo: exportar e importar una asignación de datos](org-service/samples/export-import-data-map.md)<br />
[Ejemplo: importar datos mediante la asignación de datos complejos](org-service/samples/import-data-complex-data-map.md)<br />
