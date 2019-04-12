---
title: Crear y actualizar relaciones de entidades utilizando la API web (Common Data Service) | Microsoft Docs
description: Aprenda a crear y actualizar entidades. Common Data Service usa una arquitectura controlada por metadatos que proporciona flexibilidad para crear entidades personalizadas y atributos adicionales de las entidades del sistema.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 923538e2-15fe-4718-8eae-d939c5d200cd
caps.latest.revision: 15
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-update-entity-relationships-using-the-web-api"></a>Crear y actualizar relaciones de entidad mediante la API web


La API web admite trabajar con metadatos de relación. Los conceptos que se describen en [Metadatos de relaciones entre entidades](../entity-relationship-metadata.md) también se aplican a la API web.  

<a name="bkmk_RelationshipEligibility"></a>

## <a name="eligibility-for-relationships"></a>Idoneidad para relaciones


Antes de crear una relación entre entidades, debe comprobar si la entidad puede participar en la relación. Puede usar los acciones que aparecen en la siguiente tabla para determinar su idoneidad. Estas acciones corresponden a los mensajes de servicio de la organización descritos en [Idoneidad de la relación entre entidades](../entity-relationship-eligibility.md).  


  
|Acción|Descripción|  
|------------|-----------------|  
|<xref href="Microsoft.Dynamics.CRM.CanBeReferenced?text=CanBeReferenced Action" />|Comprueba si la entidad especificada puede ser la entidad principal (uno) en una relación de uno a varios.|  
|<xref href="Microsoft.Dynamics.CRM.CanBeReferencing?text=CanBeReferencing Action" />|Comprueba si la entidad especificada puede ser la entidad de referencia (varios) en una relación de uno a varios.|  
|<xref href="Microsoft.Dynamics.CRM.CanManyToMany?text=CanManyToMany Action" />|Comprueba si la entidad puede participar en una relación de varios a varios.|  
|<xref href="Microsoft.Dynamics.CRM.GetValidManyToMany?text=GetValidManyToMany Function" />|Devuelve el conjunto de entidades que pueden participar en una relación de varios a varios.|  
|<xref href="Microsoft.Dynamics.CRM.GetValidReferencedEntities?text=GetValidReferencedEntities Function" />|Devuelve el conjunto de entidades que son válidas como entidad principal (uno) de la entidad especificada en una relación de uno a varios.|  
|<xref href="Microsoft.Dynamics.CRM.GetValidReferencingEntities?text=GetValidReferencingEntities Function" />|Devuelve el conjunto de entidades que son válidas como la entidad relacionada (varias) de la entidad especificada en una relación uno a varios.|  
  
<a name="bkmk_createOnetoMany"></a>

## <a name="create-a-one-to-many-relationship"></a>Crear nueva relación de uno a varios

Al crear una relación de uno a varios, la define mediante<xref href="Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata?text=OneToManyRelationshipMetadata EntityType" /> el. Esta definición incluye el atributo de búsqueda, que se define utilizando <xref href="Microsoft.Dynamics.CRM.LookupAttributeMetadata?text=LookupAttributeMetadata EntityType" /> y también requiere propiedades complejas utilizando <xref href="Microsoft.Dynamics.CRM.AssociatedMenuConfiguration?text=AssociatedMenuConfiguration ComplexType" />, <xref href="Microsoft.Dynamics.CRM.CascadeConfiguration?text=CascadeConfiguration ComplexType" />, <xref href="Microsoft.Dynamics.CRM.Label?text=Label ComplexType" /> y <xref href="Microsoft.Dynamics.CRM.LocalizedLabel?text=LocalizedLabel ComplexType" />. El atributo de búsqueda se establece como la propiedad de navegación de un solo valor Lookup del objeto `OneToManyRelationshipMetadata` y se crea a la vez mediante *inserción profunda*. Más información: [Crear entidades relacionadas en una operación](create-entity-web-api.md#bkmk_CreateRelated) y [Metadatos de relaciones entre entidades](../entity-relationship-metadata.md)
  
Si desea aplicar un nombre de propiedad de navegación personalizado para una relación de uno a varios puede establecer valores para las propiedades `ReferencingEntityNavigationPropertyName` y `ReferencedEntityNavigationPropertyName`.  
  
Una vez que ha generado el JSON necesario para definir la relación y el atributo de búsqueda, `POST` el JSON en el conjunto de entidades RelationshipDefinitions. Debe incluir el valor de propiedad `@odata.type` de Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata para aclarar el tipo de relación que está creando porque este mismo conjunto de entidades sirve para crear relaciones de varios a varios. El uri para la relación resultante se devuelve en la respuesta.  
  
 **Solicitud**  
```http 
POST [Organization URI]/api/data/v9.0/RelationshipDefinitions HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{  
 "SchemaName": "new_contact_new_bankaccount",  
 "@odata.type": "Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata",  
 "AssociatedMenuConfiguration": {  
  "Behavior": "UseCollectionName",  
  "Group": "Details",  
  "Label": {  
   "@odata.type": "Microsoft.Dynamics.CRM.Label",  
   "LocalizedLabels": [  
    {  
     "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
     "Label": "Bank Accounts",  
     "LanguageCode": 1033  
    }  
   ],  
   "UserLocalizedLabel": {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Bank Accounts",  
    "LanguageCode": 1033  
   }  
  },  
  "Order": 10000  
 },  
 "CascadeConfiguration": {  
  "Assign": "Cascade",  
  "Delete": "Cascade",  
  "Merge": "Cascade",  
  "Reparent": "Cascade",  
  "Share": "Cascade",  
  "Unshare": "Cascade"  
 },  
 "ReferencedAttribute": "contactid",  
 "ReferencedEntity": "contact",  
 "ReferencingEntity": "new_bankaccount",  
 "Lookup": {  
  "AttributeType": "Lookup",  
  "AttributeTypeName": {  
   "Value": "LookupType"  
  },  
  "Description": {  
   "@odata.type": "Microsoft.Dynamics.CRM.Label",  
   "LocalizedLabels": [  
    {  
     "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
     "Label": "The owner of the account",  
     "LanguageCode": 1033  
    }  
   ],  
   "UserLocalizedLabel": {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "The owner of the account",  
    "LanguageCode": 1033  
   }  
  },  
  "DisplayName": {  
   "@odata.type": "Microsoft.Dynamics.CRM.Label",  
   "LocalizedLabels": [  
    {  
     "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
     "Label": "Account Owner",  
     "LanguageCode": 1033  
    }  
   ],  
   "UserLocalizedLabel": {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Account Owner",  
    "LanguageCode": 1033  
   }  
  },  
  "RequiredLevel": {  
   "Value": "ApplicationRequired",  
   "CanBeChanged": true,  
   "ManagedPropertyLogicalName": "canmodifyrequirementlevelsettings"  
  },  
  "SchemaName": "new_AccountOwner",  
  "@odata.type": "Microsoft.Dynamics.CRM.LookupAttributeMetadata"  
 }  
}  
```  
  
 **Respuesta**  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: [Organization URI]/api/data/v9.0/RelationshipDefinitions(d475020f-5d7c-e511-80d2-00155d2a68d2)  
```  
  
<a name="bkmk_CreateManyToMany"></a>
  
## <a name="create-a-many-to-many-relationship"></a>Crear nueva relación de varios a varios

<!-- TODO:
When you create a many-to-many relationship, you must the relationship by using the <xref href="Microsoft.Dynamics.CRM.ManyToManyRelationshipMetadata?text=ManyToManyRelationshipMetadata EntityType" />. This definition includes the name of the intersect entity to be created as well as how the relationship should be displayed in the application by using <xref href="Microsoft.Dynamics.CRM.AssociatedMenuConfiguration?text=AssociatedMenuConfiguration ComplexType" />, <xref href="Microsoft.Dynamics.CRM.Label?text=Label ComplexType" /> and <xref href="Microsoft.Dynamics.CRM.LocalizedLabel?text=LocalizedLabel ComplexType" />. More information:[Many-to-many relationships](../customize-entity-relationship-metadata.md#BKMK_ManyToManyRelationships)   -->
  
 Si desea aplicar un nombre de propiedad de navegación personalizado para una relación de varios a varios puede establecer valores para las propiedades `Entity1NavigationPropertyName` y `Entity2NavigationPropertyName`.  
  
 Una vez que ha generado el JSON necesario para definir la relación, `POST` el JSON en el conjunto de entidades RelationshipDefinitions. Debe incluir el valor de propiedad `@odata.type` de Microsoft.Dynamics.CRM.ManyToManyRelationshipMetadata para aclarar el tipo de relación que está creando porque este mismo conjunto de entidades sirve para crear relaciones de uno a varios. El uri para la relación resultante se devuelve en la respuesta.  
  
 **Solicitud**
  
```http 
POST [Organization URI]/api/data/v9.0/RelationshipDefinitions HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{  
 "SchemaName": "new_accounts_campaigns",  
 "@odata.type": "Microsoft.Dynamics.CRM.ManyToManyRelationshipMetadata",  
 "Entity1AssociatedMenuConfiguration": {  
  "Behavior": "UseLabel",  
  "Group": "Details",  
  "Label": {  
   "@odata.type": "Microsoft.Dynamics.CRM.Label",  
   "LocalizedLabels": [  
    {  
     "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
     "Label": "Account",  
     "LanguageCode": 1033  
    }  
   ],  
   "UserLocalizedLabel": {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Account",  
    "LanguageCode": 1033  
   }  
  },  
  "Order": 10000  
 },  
 "Entity1LogicalName": "account",  
 "Entity2AssociatedMenuConfiguration": {  
  "Behavior": "UseLabel",  
  "Group": "Details",  
  "Label": {  
   "@odata.type": "Microsoft.Dynamics.CRM.Label",  
   "LocalizedLabels": [  
    {  
     "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
     "Label": "Campaign",  
     "LanguageCode": 1033  
    }  
   ],  
   "UserLocalizedLabel": {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Campaign",  
    "LanguageCode": 1033  
   }  
  },  
  "Order": 10000  
 },  
 "Entity2LogicalName": "campaign",  
 "IntersectEntityName": "new_accounts_campaigns"  
}  
```  
  
 **Respuesta**  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: [Organization URI]/api/data/v9.0/RelationshipDefinitions(420245fa-c77c-e511-80d2-00155d2a68d2)    
```  
  
<a name="bkmk_updateRelationships"></a>

## <a name="update-relationships"></a>Actualizar relaciones

Tal como se explica en [Actualizar entidades](create-update-entity-definitions-using-web-api.md#bkmk_updateEntities), puede actualizar las relaciones con el método HTTP PUT para reemplazar la definición existente con los cambios que desee aplicar. No puede editar propiedades individuales mediante el método HTTP PATCH como con entidades de datos de negocio. Como ocurre con entidades y atributos, debe incluir un encabezado `MSCRM.MergeLabels` con el valor establecido como `true` para evitar sobrescribir etiquetas localizadas no incluidas en la actualización y debe publicar personalizaciones antes de que estén activas en el sistema.  
  
<a name="bkmk_deleteRelationship"></a>
 
## <a name="delete-relationships"></a>Eliminar relaciones

Para eliminar una relación mediante web API, use el método HTTP DELETE con el identificador uniforme de recursos para la relación.  
  
### <a name="see-also"></a>Vea también

<!-- TODO:
[Customize entity relationship metadata](../customize-entity-relationship-metadata.md)<br /> -->
[Usar la API web con metadatos de Common Data Service](use-web-api-metadata.md)<br />
[Consulta metadatos utilizando la API web](query-metadata-web-api.md)<br />
[Recuperar metadatos por nombre o identificador de metadatos](retrieve-metadata-name-metadataid.md)<br />
[Entidades de modelo y atributos mediante la API web](create-update-entity-definitions-using-web-api.md)
