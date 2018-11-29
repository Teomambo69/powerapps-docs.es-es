---
title: La entidad anotación (nota) (Common Data Service para aplicaciones) | Microsoft Docs
description: 'Obtenga información sobre la entidad de anotación para anexar información adicional a cualquier registro en la base de datos. La entidad de anotación representa una anotación y contiene el texto de la anotación, quién creó y modificó la anotación, y si hay un archivo vinculado a la anotación.'
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
# <a name="annotation-note-entity"></a>Entidad de anotación (nota)

Las *anotaciones (notas)* proporcionan formas fáciles de anexar información adicional a los registros en la base de datos de Common Data Service para aplicaciones. Una nota (anotación) es una entrada de texto que puede estar asociada a cualquier entidad en CDS for Apps. Sin embargo, solo puede asociar anotaciones con las entidades personalizadas creadas con la propiedad <xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest.HasNotes> establecida en `true` en la clase <xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest>. Puede actualizar una entidad personalizada, que no está habilitada para notas, para que estas tengan la propiedad <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest>.<xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest.HasNotes> definida en `true`.  

Mediante la API web, establezca que la propiedad `HasNotes` del tipo de entidad <xref:Microsoft.Dynamics.CRM.EntityMetadata> controle esto.
  
 La entidad de `Annotation` representa una anotación (nota), y contiene la siguiente información:  
  
-   Texto de la anotación (nota)  
  
-   Quién creó y modificó la anotación (nota)  
  
-   Si se adjunta un archivo a la anotación (nota)  
  
 Un archivo adjunto puede estar en cualquier formato de archivo de equipo estándar como documentos Office Word, hojas de cálculo de Office Excel, archivos de CAD y archivos PDF. En CDS for Apps , los datos adjuntos pueden estar asociados a cualquier objeto, aparte de una anotación (nota).  
  
 Para cargar o quitar datos adjuntos, use el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> o el mensaje <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> estableciendo las propiedades `Annotation.Filename` y `Annotation.MimeType`. Esto permite cargar un dato adjunto que se ha descodificado en formato de cadena base64. El método [System.Convert.ToBase64String](https://msdn.microsoft.com/library/system.convert.tobase64string.aspx) se puede usar para convertir los contenidos de un archivo de datos en una cadena con formato de base64. El tamaño máximo de los archivos que se pueden cargar se determina mediante la propiedad **Organization.MaxUploadFileSize**. Esta propiedad se define en la pestaña **Correo electrónico** de **Configuración del sistema** en la aplicación Dynamics 365. Esta configuración limita el tamaño de los archivos que pueden adjuntarse a los mensajes de correo electrónico, notas y recursos web. La configuración predeterminada es 5 MB.  
  
## <a name="in-this-section"></a>En esta sección  
 [Ejemplo: Cargar, recuperar y descargar datos adjuntos](/dynamics365/customer-engagement/developer/sample-upload-retrieve-download-attachment)  
  
### <a name="see-also"></a>Vea también 
 [Entidad de anotación](reference/entities/annotation.md)   
 [Modelar los datos profesionales](/dynamics365/customer-engagement/developer/model-business-data)   
 [Entidad UserQuery (vista guardada)](/dynamics365/customer-engagement/developer/userquery-saved-view-entity)