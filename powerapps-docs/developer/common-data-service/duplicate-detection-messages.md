---
title: Mensajes de detección de duplicados (Common Data Service) | Microsoft Docs
description: Use los mensajes BulkDetectDuplicatesRequest o RetrieveDuplicatesRequest para detectar duplicados.
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
# <a name="duplicate-detection-messages"></a>Mensajes de detección de duplicados

Use los mensajes que se muestran en la tabla siguiente para detectar duplicados en Common Data Service.  


|                                                                                                                                                                                                                   Mensaje                                                                                                                                                                                                                   |                                      Operación de API web                                       |                         Ensamblado del SDK                          |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| Detecta duplicados de un tipo de entidad especificado basándose en criterios de consulta y los almacena como instancias de un tipo de entidad de registro duplicado en la base de datos de Common Data Service.<br /><br /> La expresión de la consulta que describe los registros en los que ejecutar el trabajo de detección de duplicados se especifican en la propiedad <xref:Microsoft.Crm.Sdk.Messages.BulkDetectDuplicatesRequest.Query> de la solicitud. | <xref href="Microsoft.Dynamics.CRM.BulkDetectDuplicates?text=BulkDetectDuplicates Action" /> | <xref:Microsoft.Crm.Sdk.Messages.BulkDetectDuplicatesRequest> |
|                                                                                                         Detecta y recupera duplicados para un registro especificado.<br /><br /> El tipo de entidad correspondiente se especifica en la propiedad <xref:Microsoft.Crm.Sdk.Messages.RetrieveDuplicatesRequest.MatchingEntityName> de la solicitud.                                                                                                          |  <xref href="Microsoft.Dynamics.CRM.RetrieveDuplicates?text=RetrieveDuplicates Function" />  |  <xref:Microsoft.Crm.Sdk.Messages.RetrieveDuplicatesRequest>  |

### <a name="see-also"></a>Vea también  
 [Habilitar y deshabilitar la detección de duplicados](enable-disable-duplicate-detection.md)  
 [Ejecutar la detección de duplicados](run-duplicate-detection.md)   
 [Entidades de regla de duplicados](duplicaterule-entities.md)<br />
