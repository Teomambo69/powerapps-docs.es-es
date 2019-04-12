---
title: 'Recuperar, actualizar y eliminar entidades (Common Data Service) | Microsoft Docs'
description: <Description>
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="retrieve-update-and-delete-entities"></a>Recuperar, actualizar y eliminar entidades

Este tema muestra cómo recuperar, actualizar y eliminar entidades con la entidad personalizada `Bank Account` creada en [Crear una entidad personalizada](create-custom-entity.md).  
  
<a name="BKMK_RetrieveAndUpdateEntity"></a>  
 
## <a name="retrieve-and-update-an-entity"></a>Recuperación y actualización de una entidad  

 El siguiente ejemplo recupera una entidad usando el mensaje <xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityRequest>. Después actualiza la entidad para deshabilitar la combinación de correspondencia estableciendo la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsMailMergeEnabled> en `false` y establece <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest.HasNotes> en `true` en el objeto <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest> para especificar que la entidad debe incluir una relación con la entidad `Annotation` de manera que la entidad pueda mostrar notas.  
  
```csharp

RetrieveEntityRequest retrieveBankAccountEntityRequest = new RetrieveEntityRequest
{
 EntityFilters = EntityFilters.Entity,
 LogicalName = _customEntityName
};
RetrieveEntityResponse retrieveBankAccountEntityResponse = (RetrieveEntityResponse)_serviceProxy.Execute(retrieveBankAccountEntityRequest);
EntityMetadata BankAccountEntity = retrieveBankAccountEntityResponse.EntityMetadata;

// Disable Mail merge
BankAccountEntity.IsMailMergeEnabled = new BooleanManagedProperty(false);
// Enable Notes
UpdateEntityRequest updateBankAccountRequest = new UpdateEntityRequest
{
 Entity = BankAccountEntity,
 HasNotes = true
};



_serviceProxy.Execute(updateBankAccountRequest);
```
  
<a name="BKMK_DeleteCustomEntity"></a>   

## <a name="delete-a-custom-entity"></a>Eliminación de entidades personalizadas  

El siguiente ejemplo usa el mensaje <xref:Microsoft.Xrm.Sdk.Messages.DeleteEntityRequest> para eliminar la entidad con el nombre lógico especificado por la variable `_customEntityName`.  
  
```csharp

DeleteEntityRequest request = new DeleteEntityRequest()
{
 LogicalName = _customEntityName,
};
_serviceProxy.Execute(request);
```
  
### <a name="see-also"></a>Vea también  
 [Utilizar el ejemplo IOrganizationService y el código auxiliar](/dynamics365/customer-engagement/developer/use-sample-helper-code)   
 [Personalizar metadatos de entidad](../customize-entity-metadata.md)   
 [Crear y actualizar una entidad que se puede enviar por correo electrónico](/dynamics365/customer-engagement/developer/create-update-entity-emailed)   
 [Crear una entidad personalizada](create-custom-entity.md)