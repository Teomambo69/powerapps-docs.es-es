---
title: Entidades de importación de datos (Common Data Service) | Microsoft Docs
description: 'Elabora una lista de las entidades de importación de datos utilizadas para crear asignaciones de datos, configurar y ejecutar importaciones de datos, y registrar la información de errores.'
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
# <a name="data-import-entities"></a>Entidades de importación de datos

Las entidades de importación de datos de Common Data Service están configuradas para crear asignaciones de datos, configurar y ejecutar importaciones de datos, y registrar la información con errores.  

 En la siguiente tabla se muestran las entidades que se usan para configurar, ejecutar y registrar los errores de las operaciones de importación.  

|Nombre de entidad (nombre)|Descripción|  
|----------------------------------|-----------------|  
|import (importar datos)|Estado e información de propiedad del trabajo de importación.|  
|importfile (archivo de importación de origen)|Archivo de origen lógico.|  
|importlog (registro de importación)|Motivo del error y otra información detallada de un registro que no se pudo importar.|  

 En la siguiente tabla se muestran las entidades que se usan para crear asignaciones de datos.  


|                    Nombre de entidad (nombre)                     |                                                                                                                      Descripción                                                                                                                       |
|-------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                       importmap (asignación de datos)                        |                                                                                                           Asignación de datos que se usa para importar.                                                                                                            |
|                  columnmapping (asignación de columna)                   |                                                           Asignación entre una columna en el archivo de origen y un atributo de destino en Common Data Service.                                                           |
|                  lookupmapping (asignación de búsqueda)                   |       Asignación entre una columna en el archivo de origen, o el resultado de una transformación compleja y un atributo de destino de tipo <xref:Microsoft.Xrm.Sdk.EntityReference>. Se usa junto con la asignación de columnas o la asignación compleja de transformación.        |
|                   ownermapping (asignación de propietario)                    |                                                             Asignación entre un usuario especificado en el archivo de origen y un usuario en Common Data Service.                                                             |
|                picklistmapping (asignación de lista desplegable)                 | Asignación entre una columna en el archivo de origen y un atributo de destino de <xref:Microsoft.Xrm.Sdk.OptionSetValue>, booleano, estado o tipo de estado de Common Data Service. Se usa junto con la asignación de columnas. |
|          transformationmapping (asignación de transformación)           |                                                                                                            Asignación compleja de transformación.                                                                                                             |
| transformationparametermapping (asignación de parámetros de transformación) |                                                                                           Asignación de parámetros que se usa en la asignación compleja de transformación.                                                                                            |

### <a name="see-also"></a>Vea también  
 [Importar datos en Dynamics 365](import-data.md)   
 [Entidad de importación](reference/entities/import.md)   
 [Entidad ImportFile](reference/entities/importfile.md)   
 [Entidad ImportLog](reference/entities/importlog.md)   
 [Entidad ImportMap](reference/entities/importmap.md)   
 <!-- jdaly These links will have content when we re-gen docs after bug 689487 is checked in. START -->
 [Entidad ColumnMapping](reference/entities/columnmapping.md)   
 [Entidad LookupMapping](reference/entities/lookupmapping.md)   
 [Entidad OwnerMapping](reference/entities/ownermapping.md)   
 [Entidad PicklistMapping](reference/entities/picklistmapping.md)   
 [Entidad TransformationMapping](reference/entities/transformationmapping.md)    
 [Entidad TransformationParameterMapping](reference/entities/transformationparametermapping.md)   
 <!-- jdaly These links will have content  when we re-gen docs after bug 689487 is checked in. END -->
 [Ejemplo: exportar e importar una asignación de datos](/dynamics365/customer-engagement/developer/sample-export-import-data-map)   
 [Crear asignaciones de datos para importar](create-data-maps-for-import.md)<br />
 [Agregar asignaciones de transformación para la importación](add-transformation-mappings-import.md)<br />
 [Configurar la importación de datos](configure-data-import.md)<br />
 [Ejecutar importación de datos](run-data-import.md)<br />
 [Ejemplo: exportar e importar una asignación de datos](/dynamics365/customer-engagement/developer/org-service/samples/export-import-data-map)<br />
 [Ejemplo: importar datos mediante la asignación de datos complejos](/dynamics365/customer-engagement/developer/org-service/samples/import-data-complex-data-map)<br />