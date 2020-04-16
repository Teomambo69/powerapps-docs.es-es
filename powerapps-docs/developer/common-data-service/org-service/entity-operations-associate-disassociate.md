---
title: Asociar y desasociar entidades con el servicio de la organización (Common Data Service) | Microsoft Docs
description: Más información sobre cómo asociar y desasociar entidades con el servicio de la organización
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: f089ca065168430b2b6e04517a1e8d1690b462bf
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156076"
---
# <a name="associate-and-disassociate-entities-using-the-organization-service"></a>Asociar y desasociar entidades con el servicio de la organización

Los registros de entidad están asociados entre sí mediante atributos de búsqueda en la entidad relacionada. La forma más sencilla de asociar dos registros de entidad en una relación de uno a varios es usar un <xref:Microsoft.Xrm.Sdk.EntityReference> para establecer el valor de un atributo de búsqueda en la entidad relacionada.

La forma más sencilla de desasociar dos registros de entidad en una relación de uno a varios es usar establecer el valor del un atributo de búsqueda en null.

Las relaciones mediante una relación de varios a varios también dependen de atributos de búsqueda en la *entidad de intersección* que admita la relación de varios a varios. Estas relaciones se definen mediante la existencia de registros de entidades en esa entidad de intersección. Mientras pueda interactuar con la entidad de intersección directamente, es mucho más fácil de usar la API para que lo haga automáticamente.

## <a name="use-the-associate-method-or-associaterequest"></a>Usar el método Associate o AssociateRequest

El valor principal al usar el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Associate*> o el <xref:Microsoft.Xrm.Sdk.Messages.AssociateRequest> con el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> es que puede:

- Asociar varios registros en una operación
- Asociar fácilmente registros mediante una relación de varios a varios sin hacer referencia a la entidad de intersección.

Para asociar los registros de entidad con estas API necesita tres cosas:

- Una referencia de entidad a la entidad que desee asociar
- El nombre de la relación
- Una o más referencias a las que desee asociar la entidad

Si la relación es de uno a varios o de varios a varios no importará. Los parámetros o las propiedades son equivalentes.

Puede detectar los nombres de las relaciones viendo la interfaz de usuario de personalización o en los metadatos mediante el Explorador de metadatos. Más información: 

- [Crear y editar relaciones 1: N (uno a varios) o N:1 (varios a uno)](../../../maker/common-data-service/create-edit-1n-relationships.md)
- [Crear y editar relaciones de entidad de varios a varios (N:N)](../../../maker/common-data-service/create-edit-nn-relationships.md)
- [Examinar los metadatos del entorno](../browse-your-metadata.md)

El siguiente ejemplo establecerá una entidad específica de contacto (`jimGlynn`) como contacto principal para todas las cuentas que se encuentran en Redmond.


```csharp

// Retrieve the accounts
var query = new QueryByAttribute("account")
{
ColumnSet = new ColumnSet("name")
};
query.AddAttributeValue("address1_city", "Redmond");

EntityCollection accounts = svc.RetrieveMultiple(query);

//Convert the EntityCollection to a EntityReferenceCollection
var accountReferences = new EntityReferenceCollection();

accounts.Entities.ToList().ForEach(x => {
accountReferences.Add(x.ToEntityReference());
});

// The contact to associate to the accounts
var jimGlynn = new EntityReference("contact", 
new Guid("cf76763a-ba1c-e811-a954-000d3af451d6"));

// The relationship to use
var relationship = new Relationship("account_primary_contact");

// Use the Associate method
svc.Associate(jimGlynn.LogicalName, jimGlynn.Id, relationship, accountReferences);
```
Aunque no haya una ventaja específica en hacerlo así, si se desea usar <xref:Microsoft.Xrm.Sdk.Messages.AssociateRequest>, puede reemplazar la última línea con esto:


```csharp
// Use AssociateRequest
AssociateRequest request = new AssociateRequest()
{
RelatedEntities = accountReferences,
Relationship = relationship,
Target = jimGlynn
};

svc.Execute(request);
```

Esta operación equivale a tres operaciones de actualización independientes en el atributo de búsqueda [Account](../reference/entities/account.md).[PrimaryContactId](../reference/entities/account.md#BKMK_PrimaryContactId), pero se usa la relación [account_primary_contact](../reference/entities/contact.md#BKMK_account_primary_contact), que es una relación de entidad de varios uno en la entidad de cuenta y una relación de entidad de uno a varios en la entida de contacto.

Si tiene examina las propiedades de los metadatos de la relación, verá que el valor `ReferencingEntity` es `account` y el valor `ReferencingAttribute` es `primarycontactid`.


## <a name="use-the-disassociate-method-or-disassociaterequest"></a>Usar el método Disassociate o DisassociateRequest

La propiedad <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Disassociate*> o el <xref:Microsoft.Xrm.Sdk.Messages.DisassociateRequest> con el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> son simplemente el camino inverso al proceso para asociar registros de entidad.

El siguiente código invierte las asociaciones creadas en el ejemplo anterior.


```csharp
// Retrieve the accounts
var query = new QueryByAttribute("account")
{
ColumnSet = new ColumnSet("name")
};
query.AddAttributeValue("address1_city", "Redmond");

EntityCollection accounts = svc.RetrieveMultiple(query);

//Convert the EntityCollection to a EntityReferenceCollection
var accountReferences = new EntityReferenceCollection();

accounts.Entities.ToList().ForEach(x => {
accountReferences.Add(x.ToEntityReference());
});

// The contact to associate to the accounts
var jimGlynn = new EntityReference("contact", 
new Guid("cf76763a-ba1c-e811-a954-000d3af451d6"));

// The relationship to use
var relationship = new Relationship("account_primary_contact");

// Use the Disassociate method
svc.Disassociate(jimGlynn.LogicalName, jimGlynn.Id, relationship, accountReferences);
```
Aunque no haya una ventaja específica en hacerlo así, si se desea usar <xref:Microsoft.Xrm.Sdk.Messages.DisassociateRequest>, puede reemplazar la última línea con esto:

```csharp
// Use DisassociateRequest
DisassociateRequest request = new DisassociateRequest()
{
RelatedEntities = accountReferences,
Relationship = relationship,
Target = jimGlynn
};

svc.Execute(request);
```

### <a name="see-also"></a>Vea también

[Crear entidades con el servicio de la organización](entity-operations-create.md)<br />
[Recuperar una entidad usando un servicio de organización](entity-operations-retrieve.md)<br />
[Actualizar y eliminar entidades con el servicio de la organización](entity-operations-update-delete.md)<br />
