---
title: Crear y actualizar definiciones de entidades utilizando la API web (Common Data Service) | Microsoft Docs
description: Obtenga información sobre cómo crear y actualizar definiciones de entidad mediante la API web.
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 1f430d2d-e829-4ffa-922e-dfcfb7c9e86e
caps.latest.revision: 24
author: brandonsimons
ms.author: jdaly
ms.reviewer: susikka
manager: annbe
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-update-entity-definitions-using-the-web-api"></a>Crear y actualizar definiciones de entidad mediante la API web



Puede realizar todas las mismas operaciones en entidades de modelo que con el servicio de organización. Este tema se centra en trabajar con entidades de metadatos usando la API web. Para encontrar los detalles acerca de las propiedades de los metadatos de la entidad, vea [Personalizar metadatos de entidad](../customize-entity-metadata.md) y <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" />.  

<a name="bkmk_createEntities"></a>

## <a name="create-entities"></a>Crear entidades

Para crear una entidad, realice el POST de la representación JSON de los datos de la entidad en la ruta del conjunto de entidades `EntityDefinitions`. La entidad debe incluir la definición del atributo de nombre principal para la entidad. No necesita establecer valores para todas las propiedades. Se requieren los elementos de la lista excepto Description, aunque se recomienda establecer una descripción. Los valores de propiedad que no especifica se establecerán como valores predeterminados. Para comprender los valores predeterminados, vea el ejemplo en la sección [Actualizar entidades](create-update-entity-definitions-using-web-api.md#bkmk_updateEntities). El ejemplo en este tema usa las siguientes propiedades de la entidad.  
  
|Propiedad de entidad|Value|  
|---------------------|-----------|  
|SchemaName|new_BankAccount **Nota:** debe incluir el prefijo de personalización que coincide con el editor de soluciones. Aquí se usa el valor predeterminado " new_", pero debe elegir el prefijo que funcione para la solución.|  
|DisplayName|Cuenta bancaria|  
|DisplayCollectionName|Cuentas bancarias|  
|Descripción|Una entidad para almacenar información acerca de las cuentas bancarias del cliente.|  
|OwnershipType|UserOwned **Nota:** para los valores que puede establecer aquí, consulte <xref href="Microsoft.Dynamics.CRM.OwnershipTypes?text=OwnershipTypes EnumType" />.|  
|IsActivity|false|  
|HasActivities|false|  
|HasNotes|false|  
  
 Además de las propiedades enumeradas anteriormente, la propiedad `EntityMetadataAttributes` debe contener una matriz que incluya un <xref href="Microsoft.Dynamics.CRM.StringAttributeMetadata?text=StringAttributeMetadata EntityType" /> para representar el atributo de nombre principal para la entidad. La propiedad IsPrimaryName del atributo debe ser true. En la siguiente tabla se describen las distintas propiedades establecidas en el ejemplo.  
  
|Propiedad Atributo principal|Value|  
|--------------------------------|-----------|  
|SchemaName|new_AccountName|  
|RequiredLevel|Ninguno <br />**Nota:** para los valores que puede establecer aquí, consulte <xref href="Microsoft.Dynamics.CRM.AttributeRequiredLevelManagedProperty?text=AttributeRequiredLevelManagedProperty ComplexType" /> y <xref href="Microsoft.Dynamics.CRM.AttributeRequiredLevel?text=AttributeRequiredLevel EnumType" />.|  
|MaxLength|100|  
|FormatName|Text <br />**Nota:** el atributo de nombre principal debe usar formato de texto. Para las opciones de formato disponibles para otros atributos de cadena, consulte [Formatos de cadena](../entity-attribute-metadata.md#string-formats).|  
|DisplayName|Nombre de cuenta|  
|Descripción|Escriba el nombre de la cuenta bancaria.|  
|IsPrimaryName|verdadero|  
  
> [!NOTE]
>  Cuando se crean o se actualizan etiquetas con <xref href="Microsoft.Dynamics.CRM.Label?text=Label ComplexType" />, solo debe establecer la propiedad `LocalizedLabels`. El valor `UserLocalizedLabel` devuelto se basa en la preferencia de idioma del usuario y es de solo lectura.  
  
El siguiente ejemplo muestra la creación de una entidad personalizada con las propiedades establecidas. El idioma es inglés con el Id. de configuración regional (LCID) de 1033. [!INCLUDE [lcid](../../../includes/lcid.md)]  
  
 **Solicitud**  
```http 
POST [Organization URI]/api/data/v9.0/EntityDefinitions HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{  
  "@odata.type": "Microsoft.Dynamics.CRM.EntityMetadata",  
 "Attributes": [  
  {  
   "AttributeType": "String",  
   "AttributeTypeName": {  
    "Value": "StringType"  
   },  
   "Description": {  
     "@odata.type": "Microsoft.Dynamics.CRM.Label",  
    "LocalizedLabels": [  
     {  
       "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
      "Label": "Type the name of the bank account",  
      "LanguageCode": 1033  
     }  
    ]  
   },  
   "DisplayName": {  
     "@odata.type": "Microsoft.Dynamics.CRM.Label",  
    "LocalizedLabels": [  
     {  
       "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
      "Label": "Account Name",  
      "LanguageCode": 1033  
     }  
    ]  
   },  
   "IsPrimaryName": true,  
   "RequiredLevel": {  
    "Value": "None",  
    "CanBeChanged": true,  
    "ManagedPropertyLogicalName": "canmodifyrequirementlevelsettings"  
   },  
   "SchemaName": "new_AccountName",  
    "@odata.type": "Microsoft.Dynamics.CRM.StringAttributeMetadata",  
   "FormatName": {  
    "Value": "Text"  
   },  
   "MaxLength": 100  
  }  
 ],  
 "Description": {  
   "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
     "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "An entity to store information about customer bank accounts",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "DisplayCollectionName": {  
   "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
     "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Bank Accounts",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "DisplayName": {  
   "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
     "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Bank Account",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "HasActivities": false,  
 "HasNotes": false,  
 "IsActivity": false,  
 "OwnershipType": "UserOwned",  
 "SchemaName": "new_BankAccount"  
}  
```  
  
 **Respuesta**  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: [Organization URI]/api/data/v9.0/EntityDefinitions(417129e1-207c-e511-80d2-00155d2a68d2)  
```  
  
<a name="bkmk_updateEntities"></a>
 
## <a name="update-entities"></a>Actualizar entidades
  
> [!IMPORTANT]
>  No puede usar el método HTTP PATCH para actualizar las entidades de modelo. Las entidades de metadatos tienen paridad con el servicio de organización <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest> que reemplaza la definición de entidad con la que está incluida. Por lo tanto, debe usar el método HTTP PUT al actualizar las entidades del modelo y tener cuidado de incluir todas las propiedades existentes que no desea cambiar. No puede actualizar propiedades individuales.  
  
 Cuando actualice las entidades de metadatos con etiquetas, debe incluir un encabezado `MSCRM.MergeLabels` personalizado para controlar cómo las etiquetas en la actualización deben ser manejadas. Si una etiqueta para un elemento tiene etiquetas para otros idiomas y lo actualiza con una etiqueta que contiene sólo una etiqueta para un idioma específico, el encabezado `MSCRM.MergeLabels` controla si sobrescribe las etiquetas existentes o combina la nueva etiqueta con etiquetas de idioma existentes. Con `MSCRM.MergeLabels` establecido como `true`, las etiquetas nuevas definidas solo sobrescribirán las etiquetas existentes cuando el código de idioma coincida. Si desea sobrescribir las etiquetas existentes para incluir solo las etiquetas que incluye, establezca `MSCRM.MergeLabels` como `false`.  
  
> [!IMPORTANT]
>  Si no incluye un encabezado `MSCRM.MergeLabels`, el comportamiento predeterminado es como si el valor fuera `false` y las etiquetas localizadas no incluidas en la actualización se perderán.  
  
 Cuando se actualiza una entidad o atributo, debe usar la <xref href="Microsoft.Dynamics.CRM.PublishXml?text=PublishXml Action" /> o <xref href="Microsoft.Dynamics.CRM.PublishAllXml?text=PublishAllXml Action" /> para que los cambios que realice se apliquen a la aplicación. Más información: [Publicación de personalizaciones](../../model-driven-apps/publish-customizations.md)  
  
 Normalmente, se recuperará la definición JSON del atributo y modificará las propiedades antes de volver a enviarla. El siguiente ejemplo contiene todas las propiedades de metadatos de la entidad creada en el ejemplo [Crear entidades](create-update-entity-definitions-using-web-api.md#bkmk_createEntities), pero con DisplayName cambiado a “Bank Business Name.” Puede resultar útil observar que el JSON aquí proporciona los valores predeterminados de las propiedades no establecidas en el ejemplo [Crear entidades](create-update-entity-definitions-using-web-api.md#bkmk_createEntities).  
  
 **Solicitud**  
```http 
PUT [Organization URI]/api/data/v9.0/EntityDefinitions(417129e1-207c-e511-80d2-00155d2a68d2) HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
MSCRM.MergeLabels: true  
  
{  
 "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions/$entity",  
 "ActivityTypeMask": 0,  
 "AutoRouteToOwnerQueue": false,  
 "CanTriggerWorkflow": true,  
 "Description": {  
  "LocalizedLabels": [  
   {  
    "Label": "An entity to store information about customer bank accounts",  
    "LanguageCode": 1033,  
    "IsManaged": false,  
    "MetadataId": "edc3abd7-c5ae-4822-a3ed-51734fdd0469",  
    "HasChanged": null  
   }  
  ]  
 },  
 "DisplayCollectionName": {  
  "LocalizedLabels": [  
   {  
    "Label": "Bank Accounts",  
    "LanguageCode": 1033,  
    "IsManaged": false,  
    "MetadataId": "7c758e0c-e9cf-4947-93b0-50ec30b20f60",  
    "HasChanged": null  
   }  
  ]  
 },  
 "DisplayName": {  
  "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Bank Business Name",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "EntityHelpUrlEnabled": false,  
 "EntityHelpUrl": null,  
 "IsDocumentManagementEnabled": false,  
 "IsOneNoteIntegrationEnabled": false,  
 "IsInteractionCentricEnabled": false,  
 "IsKnowledgeManagementEnabled": false,  
 "AutoCreateAccessTeams": false,  
 "IsActivity": false,  
 "IsActivityParty": false,  
 "IsAuditEnabled": {  
  "Value": false,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifyauditsettings"  
 },  
 "IsAvailableOffline": false,  
 "IsChildEntity": false,  
 "IsAIRUpdated": false,  
 "IsValidForQueue": {  
  "Value": false,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifyqueuesettings"  
 },  
 "IsConnectionsEnabled": {  
  "Value": false,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifyconnectionsettings"  
 },  
 "IconLargeName": null,  
 "IconMediumName": null,  
 "IconSmallName": null,  
 "IsCustomEntity": true,  
 "IsBusinessProcessEnabled": false,  
 "IsCustomizable": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "iscustomizable"  
 },  
 "IsRenameable": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "isrenameable"  
 },  
 "IsMappable": {  
  "Value": true,  
  "CanBeChanged": false,  
  "ManagedPropertyLogicalName": "ismappable"  
 },  
 "IsDuplicateDetectionEnabled": {  
  "Value": false,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifyduplicatedetectionsettings"  
 },  
 "CanCreateAttributes": {  
  "Value": true,  
  "CanBeChanged": false,  
  "ManagedPropertyLogicalName": "cancreateattributes"  
 },  
 "CanCreateForms": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "cancreateforms"  
 },  
 "CanCreateViews": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "cancreateviews"  
 },  
 "CanCreateCharts": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "cancreatecharts"  
 },  
 "CanBeRelatedEntityInRelationship": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canberelatedentityinrelationship"  
 },  
 "CanBePrimaryEntityInRelationship": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canbeprimaryentityinrelationship"  
 },  
 "CanBeInManyToMany": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canbeinmanytomany"  
 },  
 "CanEnableSyncToExternalSearchIndex": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canenablesynctoexternalsearchindex"  
 },  
 "SyncToExternalSearchIndex": false,  
 "CanModifyAdditionalSettings": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifyadditionalsettings"  
 },  
 "CanChangeHierarchicalRelationship": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canchangehierarchicalrelationship"  
 },  
 "IsOptimisticConcurrencyEnabled": true,  
 "ChangeTrackingEnabled": false,  
 "IsImportable": true,  
 "IsIntersect": false,  
 "IsMailMergeEnabled": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifymailmergesettings"  
 },  
 "IsManaged": false,  
 "IsEnabledForCharts": true,  
 "IsEnabledForTrace": false,  
 "IsValidForAdvancedFind": true,  
 "IsVisibleInMobile": {  
  "Value": false,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifymobilevisibility"  
 },  
 "IsVisibleInMobileClient": {  
  "Value": false,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifymobileclientvisibility"  
 },  
 "IsReadOnlyInMobileClient": {  
  "Value": false,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifymobileclientreadonly"  
 },  
 "IsOfflineInMobileClient": {  
  "Value": false,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifymobileclientoffline"  
 },  
 "DaysSinceRecordLastModified": 0,  
 "IsReadingPaneEnabled": true,  
 "IsQuickCreateEnabled": false,  
 "LogicalName": "new_bankaccount",  
 "ObjectTypeCode": 10009,  
 "OwnershipType": "UserOwned",  
 "PrimaryNameAttribute": "new_accountname",  
 "PrimaryImageAttribute": null,  
 "PrimaryIdAttribute": "new_bankaccountid",  
 "Privileges": [  
  {  
   "CanBeBasic": true,  
   "CanBeDeep": true,  
   "CanBeGlobal": true,  
   "CanBeLocal": true,  
   "CanBeEntityReference": false,  
   "CanBeParentEntityReference": false,  
   "Name": "prvCreatenew_BankAccount",  
   "PrivilegeId": "d1a8de4b-27df-42e1-bc5c-b863e002b37f",  
   "PrivilegeType": "Create"  
  },  
  {  
   "CanBeBasic": true,  
   "CanBeDeep": true,  
   "CanBeGlobal": true,  
   "CanBeLocal": true,  
   "CanBeEntityReference": false,  
   "CanBeParentEntityReference": false,  
   "Name": "prvReadnew_BankAccount",  
   "PrivilegeId": "726043b1-de2c-487e-9d6d-5629fca2bf22",  
   "PrivilegeType": "Read"  
  },  
  {  
   "CanBeBasic": true,  
   "CanBeDeep": true,  
   "CanBeGlobal": true,  
   "CanBeLocal": true,  
   "CanBeEntityReference": false,  
   "CanBeParentEntityReference": false,  
   "Name": "prvWritenew_BankAccount",  
   "PrivilegeId": "fa50c539-b6c7-4eaf-bd49-fd8224bc51b6",  
   "PrivilegeType": "Write"  
  },  
  {  
   "CanBeBasic": true,  
   "CanBeDeep": true,  
   "CanBeGlobal": true,  
   "CanBeLocal": true,  
   "CanBeEntityReference": false,  
   "CanBeParentEntityReference": false,  
   "Name": "prvDeletenew_BankAccount",  
   "PrivilegeId": "17c1fd6e-f856-45e7-b563-796f53108b85",  
   "PrivilegeType": "Delete"  
  },  
  {  
   "CanBeBasic": true,  
   "CanBeDeep": true,  
   "CanBeGlobal": true,  
   "CanBeLocal": true,  
   "CanBeEntityReference": false,  
   "CanBeParentEntityReference": false,  
   "Name": "prvAssignnew_BankAccount",  
   "PrivilegeId": "133ca81d-668e-4c19-a71e-10c6dfe099cd",  
   "PrivilegeType": "Assign"  
  },  
  {  
   "CanBeBasic": true,  
   "CanBeDeep": true,  
   "CanBeGlobal": true,  
   "CanBeLocal": true,  
   "CanBeEntityReference": false,  
   "CanBeParentEntityReference": false,  
   "Name": "prvSharenew_BankAccount",  
   "PrivilegeId": "15f27df4-9c67-47c9-b1f1-274e1c44f24a",  
   "PrivilegeType": "Share"  
  },  
  {  
   "CanBeBasic": true,  
   "CanBeDeep": true,  
   "CanBeGlobal": true,  
   "CanBeLocal": true,  
   "CanBeEntityReference": false,  
   "CanBeParentEntityReference": false,  
   "Name": "prvAppendnew_BankAccount",  
   "PrivilegeId": "ac8b1920-8f93-4e9d-94e3-c680e2a2f228",  
   "PrivilegeType": "Append"  
  },  
  {  
   "CanBeBasic": true,  
   "CanBeDeep": true,  
   "CanBeGlobal": true,  
   "CanBeLocal": true,  
   "CanBeEntityReference": false,  
   "CanBeParentEntityReference": false,  
   "Name": "prvAppendTonew_BankAccount",  
   "PrivilegeId": "f63a5f46-3bc7-4eac-81d0-7f77f566ef46",  
   "PrivilegeType": "AppendTo"  
  }  
 ],  
 "RecurrenceBaseEntityLogicalName": null,  
 "ReportViewName": "Filterednew_BankAccount",  
 "SchemaName": "new_BankAccount",  
 "IntroducedVersion": "1.0",  
 "IsStateModelAware": true,  
 "EnforceStateTransitions": false,  
 "EntityColor": null,  
 "LogicalCollectionName": "new_bankaccounts",  
 "CollectionSchemaName": "new_BankAccounts",  
 "EntitySetName": "new_bankaccounts",  
 "IsEnabledForExternalChannels": false,  
 "IsPrivate": false,  
 "MetadataId": "417129e1-207c-e511-80d2-00155d2a68d2",  
 "HasChanged": null  
}  
```  
  
 **Respuesta**  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
```  
  
<a name="bkmk_CreateAttributes"></a>

## <a name="create-attributes"></a>Crear atributos

Puede crear atributos a la vez que crea la entidad incluyendo la definición JSON de los atributos en la matriz `Attributes` de la entidad que publica además del atributo de cadena que sirve como atributo de nombre principal. Si desea agregar atributos a una entidad que ya está creada, puede enviar una solicitud POST incluyendo su definición JSON a la propiedad de navegación valorada como colección `Attributes` de la entidad.  
  
<a name="bkmk_CreateString"></a>

### <a name="create-a-string-attribute"></a>Crear un atributo de cadena

El siguiente ejemplo usará estas propiedades para crear un atributo de cadena.  
  
|Propiedades del atributo de cadena|Valores|  
|---------------------------------|------------|  
|SchemaName|new_BankName|  
|DisplayName|Nombre del banco|  
|Descripción|Escriba el nombre del banco.|  
|RequiredLevel|Ninguna|  
|MaxLength|100|  
|FormatName|Texto|  
  
El siguiente ejemplo crea un atributo de cadena mediante las propiedades y lo agrega a la entidad con el valor MetadataId de 402fa40f-287c-e511-80d2-00155d2a68d2.

El URI para el atributo se devuelve en la respuesta.  
  
 **Solicitud**

```http 
POST [Organization URI]/api/data/v9.0/EntityDefinitions(402fa40f-287c-e511-80d2-00155d2a68d2)/Attributes HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{  
 "AttributeType": "String",  
 "AttributeTypeName": {  
  "Value": "StringType"  
 },  
 "Description": {  
  "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Type the name of the bank",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "DisplayName": {  
  "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Bank Name",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "RequiredLevel": {  
  "Value": "None",  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifyrequirementlevelsettings"  
 },  
 "SchemaName": "new_BankName",  
 "@odata.type": "Microsoft.Dynamics.CRM.StringAttributeMetadata",  
 "FormatName": {  
  "Value": "Text"  
 },  
 "MaxLength": 100  
}  
  
```  
  
 **Respuesta**  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: [Organization URI]/api/data/v9.0/EntityDefinitions(402fa40f-287c-e511-80d2-00155d2a68d2)/Attributes(f01bef16-287c-e511-80d2-00155d2a68d2)  
```  
  
<a name="bkmk_createMoney"></a>

### <a name="create-a-money-attribute"></a>Crear un atributo monetario

El siguiente ejemplo usará estas propiedades para crear un atributo monetario.  
  
|Propiedades del atributo monetario|Valores|  
|--------------------------------|------------|  
|SchemaName|new_Balance|  
|DisplayName|Saldo|  
|Descripción|Especifique el importe de saldo.|  
|RequiredLevel|Ninguna|  
|PrecisionSource|2 <br />**Nota:**  para obtener información sobre los valores válidos para PrecisionSource, vea [MoneyType](../entity-attribute-metadata.md#money_type). El valor 2 indica que el nivel de precisión decimal coincidirá con TransactionCurrency.CurrencyPrecision, que está asociada con el registro actual.|  


  
El siguiente ejemplo crea un atributo monetario mediante las propiedades y lo agrega a la entidad con el valor MetadataId de 402fa40f-287c-e511-80d2-00155d2a68d2. El URI para el atributo se devuelve en la respuesta.  
  
 **Solicitud**  
```http   
POST [Organization URI]/api/data/v9.0/EntityDefinitions(402fa40f-287c-e511-80d2-00155d2a68d2)/Attributes HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{  
 "AttributeType": "Money",  
 "AttributeTypeName": {  
  "Value": "MoneyType"  
 },  
 "Description": {  
  "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Enter the balance amount",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "DisplayName": {  
  "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Balance",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "RequiredLevel": {  
  "Value": "None",  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifyrequirementlevelsettings"  
 },  
 "SchemaName": "new_Balance",  
 "@odata.type": "Microsoft.Dynamics.CRM.MoneyAttributeMetadata",  
 "PrecisionSource": 2  
}  
```  
  
 **Respuesta**  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: [Organization URI]/api/data/v9.0/EntityDefinitions(402fa40f-287c-e511-80d2-00155d2a68d2)/Attributes(f11bef16-287c-e511-80d2-00155d2a68d2)  
```  
  
<a name="bkmk_createDateTime"></a>

### <a name="create-a-datetime-attribute"></a>Crear un atributo de fecha y hora

El siguiente ejemplo usará estas propiedades para crear un atributo de fecha y hora.  
  
|Propiedades del atributo de fecha y hora|Valores|  
|-----------------------------------|------------|  
|SchemaName|new_Checkeddate|  
|DisplayName|Fecha|  
|Descripción|Fecha en que se confirmó por última vez el saldo de cuenta.|  
|RequiredLevel|Ninguna|  
|Formato|DateOnly **Nota:** para las opciones válidas para esta propiedad, consulte <xref href="Microsoft.Dynamics.CRM.DateTimeFormat?text=DateTimeFormat EnumType" />.|  
  
El siguiente ejemplo crea un atributo de fecha y hora mediante las propiedades y lo agrega a la entidad con el valor MetadataId de 402fa40f-287c-e511-80d2-00155d2a68d2. El URI para el atributo se devuelve en la respuesta.  
  
 **Solicitud**

```http 
POST [Organization URI]/api/data/v9.0/EntityDefinitions(402fa40f-287c-e511-80d2-00155d2a68d2)/Attributes HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{  
 "AttributeType": "DateTime",  
 "AttributeTypeName": {  
  "Value": "DateTimeType"  
 },  
 "Description": {  
  "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "The date the account balance was last confirmed",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "DisplayName": {  
  "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Date",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "RequiredLevel": {  
  "Value": "None",  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifyrequirementlevelsettings"  
 },  
 "SchemaName": "new_Checkeddate",  
 "@odata.type": "Microsoft.Dynamics.CRM.DateTimeAttributeMetadata",  
 "Format": "DateOnly"  
}  
```  
  
 **Respuesta**  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: [Organization URI]/api/data/v9.0/EntityDefinitions(402fa40f-287c-e511-80d2-00155d2a68d2)/Attributes(fe1bef16-287c-e511-80d2-00155d2a68d2)  
```  
  
<a name="bkmk_CreateCustomerLookup"></a>

### <a name="create-a-customer-lookup-attribute"></a>Crear un atributo de búsqueda de clientes

A diferencia de otros atributos, un atributo de búsqueda de cliente se crea mediante la acción <xref href="Microsoft.Dynamics.CRM.CreateCustomerRelationships?text=CreateCustomerRelationships Action" />. 

Los parámetros de esta acción requieren la definición del atributo de búsqueda y un par de relaciones de uno a varios. Un atributo de búsqueda de cliente tiene dos relaciones de uno a varios: una para la entidad de cuenta y la otra para la entidad de contacto.  
  
 El siguiente ejemplo usará estas propiedades para crear un atributo de búsqueda de clientes.  
  
|Propiedades del atributo de búsqueda de clientes|Valores|  
|------------------------------------------|------------|  
|SchemaName|new_CustomerId|  
|DisplayName|Cliente|  
|Descripción|Atributo de búsqueda de clientes de ejemplo|  
  
El ejemplo crea un atributo de búsqueda de clientes `new_CustomerId`, y lo agrega a la entidad personalizada:  `new_bankaccount`. La respuesta es un <xref href="Microsoft.Dynamics.CRM.CreateCustomerRelationshipsResponse?text=CreateCustomerRelationshipsResponse ComplexType" />.  
  
 **Solicitud**

```http 
POST [Organization URI]/api/data/v9.0/CreateCustomerRelationships HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
  
{  
    "OneToManyRelationships": [{  
        "SchemaName": "new_bankaccount_customer_account",  
        "ReferencedEntity": "account",  
        "ReferencingEntity": "new_bankaccount"  
    }, {  
        "SchemaName": "new_bankaccount_customer_contact",  
        "ReferencedEntity": "contact",  
        "ReferencingEntity": "new_bankaccount"  
    }],  
    "Lookup": {  
        "AttributeType": "Lookup",  
        "AttributeTypeName": {  
            "Value": "LookupType"  
        },  
        "Description": {  
            "@odata.type": "Microsoft.Dynamics.CRM.Label",  
            "LocalizedLabels": [{  
                "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
                "Label": "Sample Customer Lookup Attribute",  
                "LanguageCode": 1033  
            }],  
            "UserLocalizedLabel": {  
                "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
                "Label": "Sample Customer Lookup Attribute",  
                "LanguageCode": 1033  
            }  
        },  
        "DisplayName": {  
            "@odata.type": "Microsoft.Dynamics.CRM.Label",  
            "LocalizedLabels": [{  
                "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
                "Label": "Customer",  
                "LanguageCode": 1033  
            }],  
            "UserLocalizedLabel": {  
                "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
                "Label": "Customer",  
                "LanguageCode": 1033  
            }  
        },  
        "SchemaName": "new_CustomerId",  
        "@odata.type": "Microsoft.Dynamics.CRM.ComplexLookupAttributeMetadata"  
    }  
}  
```  
  
 **Respuesta**  
```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.CreateCustomerRelationshipsResponse",  
    "RelationshipIds": [  
        "a7d261bc-3580-e611-80d7-00155d2a68de", "aed261bc-3580-e611-80d7-00155d2a68de"  
    ],  
    "AttributeId": "39a5d94c-e8a2-4a41-acc0-8487242d455e"  
}  
  
```  
  
<a name="bkmk_updateAttribute"></a>
 
## <a name="update-an-attribute"></a>Actualizar un atributo

Como se menciona en [Actualizar entidades](create-update-entity-definitions-using-web-api.md#bkmk_updateEntities), las entidades de modelo se actualizan mediante el método HTTP PUT con la definición JSON completa en el elemento actual. Esto se aplica a atributos así como a entidades. Al igual con las entidades, tiene la opción de sobrescribir etiquetas mediante el encabezado `MSCRM.MergeLabels` con el valor establecido en `false`, y debe publicar personalizaciones antes de que estén activas en el sistema.  
  
### <a name="see-also"></a>Vea también

[Usar la API web con metadatos de Common Data Service](use-web-api-metadata.md)<br />
[Consulta metadatos utilizando la API web](query-metadata-web-api.md)<br />
[Recuperar metadatos por nombre o identificador de metadatos](retrieve-metadata-name-metadataid.md)<br />
[Relaciones entre entidades de modelo mediante la API web](create-update-entity-relationships-using-web-api.md)<br />

[Trabajar con metadatos usando el servicio de la organización](../org-service/work-with-metadata.md)<br />
[Metadatos del atributo](../entity-attribute-metadata.md)
