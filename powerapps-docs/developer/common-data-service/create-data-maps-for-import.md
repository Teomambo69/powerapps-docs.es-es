---
title: Crear asignaciones de datos para importar (Common Data Service para aplicaciones) | Microsoft Docs
description: Las asignaciones de datos son necesarias para importar datos y contienen asignaciones entre los datos incluidos en el archivo de origen y los correspondientes atributos de entidad.
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
# <a name="create-data-maps-for-import"></a>Crear asignaciones de datos para importar

Para importar datos en Common Data Service para aplicaciones, debe proporcionar las asignaciones de datos adecuadas.  
  
 Puede descargar ejemplos de asignaciones de datos en [Descargas de Microsoft: DataImportMaps.zip](http://download.microsoft.com/download/D/5/F/D5F73E15-439B-4EBC-BFFB-C6837B146C76/DataImportMaps.zip).
  
 Se utilizan asignaciones de datos para asignar los datos contenidos en el archivo de origen a los atributos de entidad de CDS for Apps. Debe asignar cada columna del archivo de origen a un atributo apropiado. Los datos de las columnas o los archivos sin asignar no se importan durante la importación de datos.  
  
 La asignación de datos se representa con la entidad de asignación de importación (asignación de datos). Puede crear una nueva asignación mediante el mensaje de <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> o actualizar una asignación existente mediante el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*>. . La asignación tiene un nombre único que se incluye en el atributo de `ImportMap.Name`. Puede especificar el nombre del origen de importación para el que la asignación de datos se crea mediante el atributo de `ImportMap.Source`.  
  
<a name="BKMK_Column"></a>   
## <a name="column-list-value-and-lookup-mappings"></a>Columna, valor de lista y asignaciones de la búsqueda  
 Para asignar una columna, un valor de lista o el valor de búsqueda del archivo de origen a un atributo de CDS for Apps, use las siguientes asignaciones:  
  
 **Asignación de columnas**  
  
 Asigna una columna de un archivo de origen a un atributo de entidad de CDS for Apps. Para asignaciones de columna, use la entidad de asignaciones de columna (`ColumnMapping`). Puede usar relaciones de 1:1 (uno a uno) o 1:N (uno a varios) entre los atributos de origen y de destino. Por ejemplo, puede asignar la información de dirección de una cuenta a las direcciones de facturación y envío de un pedido.  
  
 **Asignación de valores de lista**  
  
 Asigna un valor de lista de un archivo de origen a un atributo de CDS for Apps del tipo <xref:Microsoft.Xrm.Sdk.OptionSetValue>. Para la asignación de valores de lista, use la entidad de asignación de lista desplegable (`PicklistMapping`).  
  
 Si un valor especificado en la columna del archivo de origen es un valor de lista, como un OptionSetValue, un estado y un booleano, debe proporcionar una asignación de valores de lista además de una asignación de columnas. Por ejemplo, asigne los valores de lista "cuenta" y "enviar" del archivo de origen a los valores de facturación y envío del tipo <xref:Microsoft.Xrm.Sdk.OptionSetValue>.  
  
 **Asignación de búsquedas**  
  
 Asigna un valor de búsqueda de un archivo de origen a un atributo de CDS for Apps del tipo <xref:Microsoft.Xrm.Sdk.EntityReference>. Para asignaciones de búsqueda, use la entidad de asignación de búsqueda (`LookupMapping`).  
  
 Si el valor especificado en el archivo de origen hace referencia a una entidad, debe proporcionar una asignación de búsqueda para este valor. Use el atributo `LookupMapping.LookupSourceCode` para especificar si buscar la entidad a la que se hace referencia en el archivo de origen o en CDS for Apps. Si usa enlaces en tiempo de compilación, puede usar la enumeración de `LookupSourceType` para establecer los valores de búsqueda. Para buscar en el archivo de origen, use el valor de `LookupSourceType.Source`. Para buscar en CDS for Apps, use el valor de `LookupSourceType.System`. Para obtener una lista de valores de LookupSourceCode, consulte los valores de lista desplegable para esta entidad. Para ver los metadatos de las entidades de su organización, instale la solución Explorador de metadatos que se describe en [Exploración de los metadatos de su organización](/dynamics365/customer-engagement/developer/browse-your-metadata). También puede examinar la documentación de referencia para las entidades en la [Referencia de entidad](reference/about-entity-reference.md).  Puede proporcionar varias asignaciones de búsqueda. El trabajo de transformación asíncrona procesa todas las asignaciones disponibles. Encuentra los registros de referencia y actualiza la tabla de análisis con los identificadores únicos de registro. Para obtener más información, vea [Ejecutar importación de datos](run-data-import.md).  
  
<a name="BKMK_Owner"></a>   
## <a name="owner-mapping"></a>Asignación de propietario  
 Use la asignación de propietario para asignar un usuario especificado en el archivo de origen a un usuario de CDS for Apps. Para obtener información de registro, use el nombre de inicio de sesión de usuario de CDS for Apps. Para asignaciones de propietario, use la entidad de asignación de propietario (`OwnerMapping`).  
  
<a name="BKMK_Notes"></a>   
## <a name="notes-and-attachments"></a>Notas y datos adjuntos.  
 La asignación de notas y datos adjuntos se controla de forma diferente de otras entidades. Las notas y datos adjuntos se usan para anexar información adicional a un registro en CDS for Apps. Las notas se almacenan como texto y los datos adjuntos se almacenan como archivos en la base de datos de CDS for Apps.  
  
 Para crear una nota en CDS for Apps, establezca el atributo `Annotation.IsDocument` de la entidad de anotación (nota) en `false`. Para crear datos adjuntos, establezca `IsDocument` en `true`.  
  
 Use la siguiente configuración para asignar notas y datos adjuntos:  
  
- Establezca el atributo `ColumnMapping.SourceAttributeName` en “`true`” o “`false`”. El valor de "`true`" indica datos adjuntos. El valor de "`false`" indica una nota.  
  
- Establezca el atributo `ColumnMapping.TargetAttributeName` en `IsDocument`.  
  
- Si usa enlaces en tiempo de compilación, establezca el atributo `ColumnMapping.ProcessCode` en el valor `ImportProcessCode.Internal` de la enumeración `ImportProcessCode`. Para obtener una lista de valores de ProcessCode, consulte los valores de lista desplegable para esta entidad.  
  
  Si los datos de origen representan una nota, asigne el texto de la nota al atributo de `Annotation.NoteText`. Si está trabajando con los archivos de Salesforce, normalmente se almacenan en el disco en números de identificación únicos. Para importar datos adjuntos, debe asignar un número de identificación del archivo que se incluye en el archivo de origen al atributo de `Annotation.DocumentBody`. El atributo de `DocumentBody` almacena el contenido de los datos adjuntos.  
  
  El trabajo de importación asíncrono comprueba las asignaciones con el nombre del atributo de origen establecido en "`true`" y "`false`" para averiguar notas y datos adjuntos. Si encuentra una asignación de datos adjuntos, busca los archivos especificados en el disco y carga el contenido del archivo como datos adjuntos en CDS for Apps. Si un archivo no se encuentra, se devuelve un error.  
  
  Si no ofrece la asignación de una entidad de anotación (nota), el trabajo de importación genera una asignación predeterminada para la nota.  
  
> [!NOTE]
> El tamaño máximo de los archivos que se pueden cargar se determina mediante la propiedad **Organization.MaxUploadFileSize**. Esta propiedad se define en la pestaña **Correo electrónico** de **Configuración del sistema** en la aplicación CDS for Apps. Esta configuración limita el tamaño de los archivos que pueden adjuntarse a los mensajes de correo electrónico, notas y recursos web. La configuración predeterminada es 5 MB.  No obstante, el tamaño de los datos adjuntos no puede exceder el tamaño máximo solicitado (el valor predeterminado es 16 MB). Para que el cambio se aplique, restablezca Internet Information Services. Para ello, haga clic en **Inicio**, **Ejecutar**, escriba `iisreset` y, a continuación, haga clic en **Aceptar**.  
  
<a name="BKMK_ImportExport"></a>   
## <a name="import-and-export-data-maps"></a>Asignaciones de datos de importación y exportación  
 Puede exportar una asignación de datos existente a un archivo XML e importar asignaciones de datos XML a CDS for Apps. Para exportar una asignación de datos de CDS for Apps, use el mensaje <xref:Microsoft.Crm.Sdk.Messages.ExportMappingsImportMapRequest>. Para importar asignaciones de datos XML y crear una asignación de datos en CDS for Apps, use el mensaje <xref:Microsoft.Crm.Sdk.Messages.ImportMappingsImportMapRequest>.  
  
### <a name="see-also"></a>Vea también

[Importar datos](import-data.md)<br />
[Preparar archivos de origen para importar](prepare-source-files-import.md)<br />
[Agregar asignaciones de transformación para la importación](add-transformation-mappings-import.md)<br />
[Configurar la importación de datos](configure-data-import.md)<br />
[Ejecutar importación de datos](run-data-import.md)<br />
[Entidades de importación de datos](data-import-entities.md)<br />
[Ejemplo: exportar e importar una asignación de datos](org-service/samples/export-import-data-map.md)<br />
[Ejemplo: importar datos mediante la asignación de datos complejos](org-service/samples/import-data-complex-data-map.md)<br />