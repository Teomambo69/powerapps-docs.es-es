---
title: Ejecutar importación de datos (Common Data Service) | Microsoft Docs
description: La importación de datos se ejecuta directamente en Dynamics 365 Server y requiere tres trabajos asincrónicos para hacer el análisis, la transformación guiada por mapa y la carga.
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
ms.openlocfilehash: 42f69903abb225f2746e0ff79eb2d13232e8cc12
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753784"
---
# <a name="run-data-import"></a>Ejecutar importación de datos

La importación de datos se ejecuta directamente en el servidor de Common Data Service. Para ejecutar la importación de datos, configure trabajos asincrónicos para ejecutarse en segundo plano que realicen lo siguiente, en este orden:  
  
- Analizar datos de origen incluidos en el archivo de importación.  
  
- Transformar datos analizados mediante la asignación de datos.  
  
- Cargar datos transformados en Common Data Service.  
  
  Todos los usuarios de Common Data Service que dispongan de los permisos adecuados podrán ejecutar la importación de datos.  
  
<a name="parse"></a>   
## <a name="parse-source-data"></a>Analizar datos de origen  
 El análisis de los datos de origen incluye el análisis de todos los archivos de importación asociados con una importación determinada (importación de datos).  
  
 Los datos analizados se almacena en las tablas de análisis temporales creadas para cada archivo importado. El nombre de la tabla de análisis se almacenan en el atributo `ImportFile.ParsedTableName`. Los encabezados de la columna del archivo de origen se especifican en el atributo `ImportFile.HeaderRow`. Si el archivo de origen no incluye una primera fila que contenga los encabezados de columna, este atributo especifica los encabezados de columna predeterminados generados por el sistema.  
  
 Guarde los datos analizados en la tabla de análisis con el mensaje <xref:Microsoft.Crm.Sdk.Messages.ParseImportRequest>. Recupere datos de la tabla de análisis con el mensaje <xref:Microsoft.Crm.Sdk.Messages.GetDistinctValuesImportFileRequest> y el mensaje <xref:Microsoft.Crm.Sdk.Messages.RetrieveParsedDataImportFileRequest>.  
  
 En la siguiente tabla se enumeran los mensajes que puede usar para analizar los archivos de importación y para recuperar los datos analizados de las tablas de análisis.  
  
|Mensaje|Descripción|  
|-------------|-----------------|  
|<xref:Microsoft.Crm.Sdk.Messages.ParseImportRequest>|Envía un trabajo asincrónico que analiza todos los archivos de importación asociados con la importación especificada (importación de datos). Pase el Id. de importación asociado (importación de datos) en la propiedad de <xref:Microsoft.Crm.Sdk.Messages.ParseImportRequest.ImportId> de esta solicitud. El identificador del trabajo asincrónico que se ejecuta en segundo plano y realiza el análisis de datos se devuelve en la propiedad de <xref:Microsoft.Crm.Sdk.Messages.ParseImportResponse.AsyncOperationId> de respuesta de los mensajes.|  
|<xref:Microsoft.Crm.Sdk.Messages.GetDistinctValuesImportFileRequest>|Devuelve los valores distintos para una columna en el archivo de origen que contiene valores de lista. Pase el identificador del archivo de importación asociado en la propiedad de <xref:Microsoft.Crm.Sdk.Messages.GetHeaderColumnsImportFileRequest.ImportFileId> de esta solicitud. Los valores distintos se devuelven en una matriz de cadenas, en la propiedad de <xref:Microsoft.Crm.Sdk.Messages.GetDistinctValuesImportFileResponse.Values> de respuesta de los mensajes. Use este mensaje después de crear una tabla de análisis con el mensaje de <xref:Microsoft.Crm.Sdk.Messages.ParseImportRequest>. **Importante:** No use este mensaje después de utilizar el mensaje de <xref:Microsoft.Crm.Sdk.Messages.ImportRecordsImportRequest>. No se puede obtener acceso a la tabla de análisis después de que el trabajo de importación enviado por el mensaje de <xref:Microsoft.Crm.Sdk.Messages.ImportRecordsImportRequest> haya finalizado de ejecutarse.|  
|<xref:Microsoft.Crm.Sdk.Messages.RetrieveParsedDataImportFileRequest>|Recupera los datos de la tabla de análisis. Pase el identificador del archivo de importación asociado en la propiedad de <xref:Microsoft.Crm.Sdk.Messages.RetrieveParsedDataImportFileRequest.ImportFileId> de esta solicitud. Los datos analizados se devuelven en una matriz bidimensional de cadenas en la propiedad de <xref:Microsoft.Crm.Sdk.Messages.RetrieveParsedDataImportFileResponse.Values> de respuesta de los mensajes. Los datos se devuelven con el mismo orden de columnas que el del archivo de origen. Use este mensaje después de crear una tabla de análisis con el mensaje de <xref:Microsoft.Crm.Sdk.Messages.ParseImportRequest>. **Importante:** No use este mensaje después de utilizar el mensaje de <xref:Microsoft.Crm.Sdk.Messages.ImportRecordsImportRequest>. No se puede obtener acceso a la tabla de análisis después de que el trabajo de importación enviado por el mensaje de `ImportRecordsMessage` haya finalizado de ejecutarse.|  
  
<a name="transform"></a>   
## <a name="transform-parsed-data"></a>Datos de análisis de transformación  
 Durante la transformación, cambia datos analizados aplicando todas las asignaciones y transformaciones de datos disponibles asociadas con una importación determinada (importación de datos) a los datos.  
  
 Utilice el mensaje <xref:Microsoft.Crm.Sdk.Messages.TransformImportRequest> para enviar un trabajo asincrónico para transformar los datos analizados. Pase un identificador único de la importación asociada (importación de datos) en el atributo de `Import.ImportId` de la solicitud. Un identificador único del trabajo asincrónico que se ejecuta en segundo plano y realiza la transformación se devuelve en la propiedad de <xref:Microsoft.Crm.Sdk.Messages.TransformImportResponse.AsyncOperationId> de respuesta del mensaje.  
  
<a name="upload"></a>   
## <a name="upload-transformed-data-to-the-target-server"></a>Cargar datos transformados al servidor de destino  
 Tras completar correctamente la transformación, los datos están listos para cargarse en el servidor de Common Data Service.  
  
 Utilice el mensaje <xref:Microsoft.Crm.Sdk.Messages.ImportRecordsImportRequest> para enviar un trabajo asincrónico para cargar los datos transformados en Common Data Service. El identificador único de la importación asociada (importación de datos) debe especificarse en la propiedad de <xref:Microsoft.Crm.Sdk.Messages.ImportRecordsImportRequest.ImportId> de la solicitud. Un identificador único del trabajo asincrónico que se ejecuta en segundo plano y carga los datos en Common Data Service se devuelve en la propiedad de <xref:Microsoft.Crm.Sdk.Messages.ImportRecordsImportResponse.AsyncOperationId> de respuesta del mensaje. Todos los archivos de importación asociados con la importación especificada (importación de datos) se importan.  
  
 Cada trabajo de importación tiene un número de secuencia único que almacena en el atributo de `ImportSequenceNumber` de registros que crea. El atributo de `Organization.CurrentImportSequenceNumber` contiene un número de secuencia único del pasado trabajo de importación que se ejecutó en el sistema. Puede usar estos números de secuencia únicos para efectuar un seguimiento de los registros que pertenecen a un trabajo de importación.  
  
<a name="log"></a>   
## <a name="log-failures"></a>Errores de registro  
 Se puede producir un error de importación de un registro durante el análisis, la transformación o la carga de datos. Los motivos del error y otra información detallada sobre los registros que no se importaron se capturan en la entidad del registro de importación (ImportLog).  
  
 Para averiguar cuántos registros no se importaron correctamente, recupere el atributo de `ImportFile.FailureCount` del registro. Para comprobar cuántos registros tenían errores parciales durante la importación, recupere el atributo de `ImportData.HasError`. Si el atributo de `HasError` es `true`, se ha producido un error parcial, si es `false`, el registro se ha importado correctamente.  
  
<a name="import_audit"></a>   
## <a name="import-auditing-data"></a>Importación de datos de auditoría  
 Las entidades de Common Data Service disponen de cuatro atributos predeterminados que se usan para el seguimiento de la fecha y hora en que se ha creado y modificado un registro por última vez, así como la persona que lo ha creado y modificado.  
  
 El atributo de `createdon` especifica la fecha y la hora en que se creó el registro. Para importar datos en el atributo de `createdon`, asigne la columna de origen que incluye estos datos al atributo de `overriddencreatedon`. Durante la importación, el atributo de `createdon` del registro se actualiza con el valor que se asignó al atributo de `overriddencreatedon` y el atributo de `overriddencreatedon` se establece en la fecha y hora en que se importaron los datos. Si no se asigna ningún valor de origen al atributo de `overriddencreatedon`, el atributo de `createdon` se establece en la fecha y hora de importación de los datos y el atributo de `overriddencreatedon` no se establece en ningún valor.  
  
> [!NOTE]
>  Para reemplazar el valor del atributo de `createdon` durante la importación, necesita disponer del privilegio de `prvOverrideCreatedOnCreatedBy`. Tenga en cuenta que el nombre del privilegio implica que también puede reemplazar el atributo de `createdby` durante la importación. Sin embargo, actualmente esta función no es compatible.  
  
 No puede importar datos en los atributos de `modifiedon`, `createdby` y `modifiedby`. Si tiene que almacenar datos relacionados con la persona que creó y modificó los datos y cuándo se han modificado los datos, puede crear atributos personalizados en Common Data Service y asignar las columnas de origen a los nuevos atributos personalizados.  
  
### <a name="see-also"></a>Vea también

[Importar datos](import-data.md)<br />
[Preparar archivos de origen para importar](prepare-source-files-import.md)<br />
[Crear asignaciones de datos para importar](create-data-maps-for-import.md)<br />
[Agregar asignaciones de transformación para la importación](add-transformation-mappings-import.md)<br />
[Configurar la importación de datos](configure-data-import.md)<br />
[Entidades de importación de datos](data-import-entities.md)<br />
[Ejemplo: exportar e importar una asignación de datos](org-service/samples/export-import-data-map.md)<br />
[Ejemplo: importar datos mediante la asignación de datos complejos](org-service/samples/import-data-complex-data-map.md)<br />
[Entrada de blog: Cómo importar los datos adjuntos mediante programación](https://blogs.msdn.com/b/crm/archive/2012/08/06/how-to-import-attachments-programmatically.aspx) 