---
title: Use la entidad de comentarios para administrar comentarios y calificaciones para registros (Common Data Service para aplicaciones) | Microsoft Docs
description: Información sobre la entidad de comentarios para obtener comentarios y calificaciones para los registros.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-the-feedback-entity-to-manage-feedback-and-ratings-for-records"></a>Usar la entidad Comentarios para administrar comentarios y clasificaciones para registros

Mejore los productos y servicios habilitando a los usuarios para proporcionar comentarios y clasificaciones para los registros de entidad en Common Data Service para aplicaciones. Por ejemplo, puede habilitar comentarios y clasificaciones para que la entidad `Product` pueda conocer los comentarios del usuario sobre los productos que vende, o en la entidad (caso) `Incident` para comprender y mejorar la calidad del equipo de soporte del cliente.  
  
 Puede habilitar comentarios y clasificaciones para entidades del sistema y personalizadas en CDS para aplicaciones. De forma predeterminada, la entidad `KnowledgeArticle` está habilitada para comentarios y clasificaciones. Use la nueva entidad `Feedback` para crear y administrar mediante programación los comentarios para registros de entidad.  
  
 Para habilitar comentarios mediante programación para:  
  
- Una entidad del sistema, use el mensaje <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest> para actualizar la entidad, y establezca la propiedad <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest.HasFeedback> como True.  
  
- Una entidad personalizada, establezca la propiedad <xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest>.<xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest.HasFeedback> en true mientras crea la entidad o actualice la entidad personalizada existente para establecer la propiedad <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest>.<xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest.HasFeedback> en true.  
  
  Una vez que haya habilitado una entidad para comentarios y clasificaciones, no puede deshabilitarla. Después de habilitar una entidad para comentarios, se crea una relación de referente a entre la entidad y la entidad `Feedback`.  
  
> [!NOTE]
>  También puede usar las herramientas de personalización en CDS para aplicaciones para habilitar comentarios y clasificaciones para entidades del sistema y personalizadas. Más información: [Habilitar una entidad para comentarios](http://go.microsoft.com/fwlink/p/?LinkId=785436)  
  
 La entidad de `Feedback` almacena la siguiente información:  
  
- Título de comentarios  
  
- Observaciones sobre los comentarios  
  
- Clasificación de comentarios. También puede definir una gama para clasificaciones especificando un valor (numérico) mínimo y máximo para clasificaciones. Por ejemplo, una clasificación de 4 en la escala de 1-5.  
  
- Clasificación normalizada para comentarios que se calcula automáticamente para mostrar la clasificación del usuario especificada a un valor entre 0 y 1 en función de los valores de clasificación mínimo y máximo.  
  
  > [!NOTE]
  >  La clasificación normalizada ayuda a normalizar o incluso igualar el valor de clasificación especificado para diferentes clasificaciones (valores de clasificación mínimo y máximo). La clasificación normalizada se calcula de la siguiente manera: (Clasificación - Clasificación mínima) / (Clasificación máxima - Clasificación mínima).  
  >   
  >  Además, la clasificación de un registro se calcula como media de todas las clasificaciones normalizadas para el registro.  
  
- Estado de comentarios como Abierto o Cerrado  
  
- Origen de los comentarios para mostrar el origen desde donde se enviaron los comentarios. Si los comentarios se crearon desde CDS para aplicaciones, el valor se establece como **Interno**. Los desarrolladores pueden agregar un valor de su elección según la aplicación usada para proporcionar comentarios.  
  
- El usuario que creó o modificó por última vez el registro de comentarios  
  
- Registro de entidad al que están asociados los comentarios.  
  