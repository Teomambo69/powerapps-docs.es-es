---
title: Consultar metadatos con la API web (Common Data Service) | Microsoft Docs
description: La posibilidad de consultar metadatos del sistema está disponible mediante la API web así como usando el servicio de organización mediante RetrieveMetadataChangesRequest
ms.custom: ''
ms.date: 11/04/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 3ad4a332-a304-421f-a9fa-82ea3e0503fe
caps.latest.revision: 18
author: JimDaly
ms.author: jdaly
ms.reviewer: susikka
manager: amyla
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b2a1d133de698402bf880ed37f88b4bd12fd5203
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749519"
---
# <a name="query-metadata-using-the-web-api"></a>Consulta de metadatos utilizando la API web

Puesto que Common Data Service es una aplicación basada en metadatos, los desarrolladores pueden necesitar consultar los metadatos del sistema en tiempo de ejecución para adaptarse a la forma en que se ha configurado una organización. Esta funcionalidad usa un estilo de RESTful de la consulta.

> [!NOTE]
> También puede generar una consulta con un estilo basado en objetos usando <xref href="Microsoft.Dynamics.CRM.EntityQueryExpression?text=EntityQueryExpression ComplexType" /> con <xref href="Microsoft.Dynamics.CRM.RetrieveMetadataChanges?text=RetrieveMetadataChanges Function" />. Esta característica permite capturar cambios en los metadatos entre dos periodos de tiempo así como devolver un conjunto de metadatos definidos por una consulta especificada.

<a name="bkmk_QueryingEntityMetadata"></a>

## <a name="querying-the-entitymetadata-entity-type"></a>Consultar el tipo de entidad EntityMetadata

Usará las mismas técnicas descritas en [Consultar datos utilizando la API web](query-data-web-api.md) cuando consulte EntityMetadata, con algunas variaciones. Use la ruta del conjunto de entidades `EntityDefinitions` para recuperar información acerca del <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" />. Las entidades de EntityMetadata contienen muchos datos por lo que deberá tener cuidado de recuperar solo los datos necesarios. El siguiente ejemplo muestra los datos devueltos solo para las propiedades DisplayName, IsKnowledgeManagementEnabled y EntitySetName de los metadatos de la entidad `Account`. El valor de la propiedad `MetadataId` siempre se devuelve.  
  
 **Solicitud**

```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='account')?$select=DisplayName,IsKnowledgeManagementEnabled,EntitySetName HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```

 **Respuesta**
```http
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  

{  
 "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions(DisplayName,IsKnowledgeManagementEnabled,EntitySetName)",  
 "value": [  
  {  
   "DisplayName": {  
    "LocalizedLabels": [  
     {  
      "Label": "Account",  
      "LanguageCode": 1033,  
      "IsManaged": true,  
      "MetadataId": "2a4901bf-2241-db11-898a-0007e9e17ebd",  
      "HasChanged": null  
     }  
    ],  
    "UserLocalizedLabel": {  
     "Label": "Account",  
     "LanguageCode": 1033,  
     "IsManaged": true,  
     "MetadataId": "2a4901bf-2241-db11-898a-0007e9e17ebd",  
     "HasChanged": null  
    }  
   },  
   "IsKnowledgeManagementEnabled": false,  
   "EntitySetName": "accounts",  
   "MetadataId": "70816501-edb9-4740-a16c-6a5efbc05d84"  
  }  
 ]  
}  
  
```

Puede usar cualquiera de las propiedades `EntityMetadata` con opciones de consulta del sistema `$select` y puede usar `$filter` en cualquier propiedad que use valores primitivos o de enumeración.  

No tiene hay límites en el número al número de entidades de metadatos que serán devueltas en una consulta. No hay paginación. Se devolverán todos los recursos que coincidan en la primera respuesta.  

<a name="bkmk_filterEnumTypes"></a>

## <a name="use-enum-types-in-filter-operations"></a>Use tipos de enumeración en operaciones $filter

Cuando necesite filtrar entidades de metadatos basadas en el valor de una propiedad que use una enumeración, debe incluir el espacio de nombres de la enumeración delante del valor de cadena. Los tipos de enumeración se utilizan como valores de propiedad solo en entidades de metadatos y tipos complejos. Por ejemplo, si necesita filtrar entidades en función de la propiedad `OwnershipType`, que usa <xref href="Microsoft.Dynamics.CRM.OwnershipTypes?text=OwnershipTypes EnumType" />, puede usar el siguiente `$filter` para devolver únicamente las entidades que son UserOwned .

```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions?$select=LogicalName&$filter=OwnershipType eq Microsoft.Dynamics.CRM.OwnershipTypes'UserOwned'  
```

<a name="bkmk_complexTypesAsFilters"></a>

## <a name="use-complex-types-in-filter-operations"></a>Use tipos complejos en operaciones $filter

Cuando necesite filtrar entidades de metadatos basadas en el valor de una propiedad que use un tipo complejo, debe incluir la ruta al tipo primitivo subyacente. Los tipos complejos se utilizan como valores de propiedad solo en entidades de metadatos. Por ejemplo, si necesita filtrar entidades en función de la propiedad CanCreateAttributes, que usa el <xref href="Microsoft.Dynamics.CRM.BooleanManagedProperty?text=BooleanManagedProperty ComplexType" />, puede usar el siguiente `$filter` para devolver únicamente las entidades que tienen un `Value` de `true`.

```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions?$select=LogicalName&$filter=CanCreateAttributes/Value eq true  
```

Este modelo funciona con <xref href="Microsoft.Dynamics.CRM.BooleanManagedProperty?text=BooleanManagedProperty ComplexType" /> porque el valor primitivo a comprobar tiene un nivel de profundidad. No obstante, esto no funciona en propiedades de <xref href="Microsoft.Dynamics.CRM.Label?text=Label ComplexType" />.  

<a name="bkmk_queryAttributes"></a>

## <a name="querying-entitymetadata-attributes"></a>Consultar atributos EntityMetadata

Puede ver atributos de entidad en el contexto de una entidad expandiendo la propiedad de navegación valorada como colección `Attributes`, pero esto solo incluirá las propiedades comunes disponibles en el <xref href="Microsoft.Dynamics.CRM.AttributeMetadata?text=AttributeMetadata EntityType" /> que todos los atributos comparten. Por ejemplo, la siguiente consulta devolverá el `LogicalName` de la entidad y todos los atributos expandidos que tengan un valor de `AttributeType` igual al valor de <xref href="Microsoft.Dynamics.CRM.AttributeTypeCode?text=AttributeTypeCode EnumType" /> de `Picklist`.

<a name="bkmk_queryAttributesexample"></a>

```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='account')?$select=LogicalName&$expand=Attributes($select=LogicalName;$filter=AttributeType eq Microsoft.Dynamics.CRM.AttributeTypeCode'Picklist')  
```

Pero no puede incluir las propiedades navegación valoradas como colección `OptionSet` o `GlobalOptionSet` que los atributos <xref href="Microsoft.Dynamics.CRM.PicklistAttributeMetadata?text=PicklistAttributeMetadata EntityType" /> tienen en el filtro `$select` de esta consulta.  

Para recuperar las propiedades de un tipo específico de atributo debe convertir la propiedad de navegación valorada como colección `Attributes` al tipo que desee. La siguiente consulta devolverá sólo los atributos <xref href="Microsoft.Dynamics.CRM.PicklistAttributeMetadata?text=PicklistAttributeMetadata EntityType" /> e incluirá además los `LogicalName` y también expandirá las propiedades de navegación valoradas como colección de `OptionSet` y `GlobalOptionSet`.  

```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes/Microsoft.Dynamics.CRM.PicklistAttributeMetadata?$select=LogicalName&$expand=OptionSet,GlobalOptionSet  
```

> [!NOTE]
> A pesar de que las propiedades de navegación valoradas como colección `OptionSet` y `GlobalOptionSet` se definen en <xref href="Microsoft.Dynamics.CRM.EnumAttributeMetadata?text=EnumAttributeMetadata EntityType" />, no puede convertir los atributos a este tipo. Esto significa que si desea filtrar por otros tipos que también hereden estas propiedades (consulte [Tipos de entidades que heredan de EnumAttributeMetadata](/dynamics365/customer-engagement/web-api/enumattributemetadata?view=dynamics-ce-odata-9#Derived_Types) ), debe realizar consultas aparte para filtrar por cada tipo.

Otro ejemplo de esto es acceder a la propiedad `Precision` disponible en los atributos <xref href="Microsoft.Dynamics.CRM.MoneyAttributeMetadata?text=MoneyAttributeMetadata EntityType" /> y <xref href="Microsoft.Dynamics.CRM.DecimalAttributeMetadata?text=DecimalAttributeMetadata EntityType" />. Para acceder a esta propiedad debe convertir la colección de atributos como <xref href="Microsoft.Dynamics.CRM.MoneyAttributeMetadata?text=MoneyAttributeMetadata EntityType" /> o <xref href="Microsoft.Dynamics.CRM.DecimalAttributeMetadata?text=DecimalAttributeMetadata EntityType" />. Un ejemplo que muestra la conversión a `MoneyAttributeMetadata` se muestra a continuación.

```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes/Microsoft.Dynamics.CRM.MoneyAttributeMetadata?$select=LogicalName,Precision
```

### <a name="filtering-by-required-level"></a>Filtrar por nivel requerido

La propiedad <xref href="Microsoft.Dynamics.CRM.AttributeMetadata?text=AttributeMetadata EntityType" /> `RequiredLevel` usa un <xref href="Microsoft.Dynamics.CRM.AttributeRequiredLevelManagedProperty?text=AttributeRequiredLevelManagedProperty ComplexType" /> especial donde la propiedad `Value` es un <xref href="Microsoft.Dynamics.CRM.AttributeRequiredLevel?text=AttributeRequiredLevel EnumType" />. En este caso, debe combinar patrones de [Utilizar tipos complejos en operaciones $filter](query-metadata-web-api.md#bkmk_complexTypesAsFilters) y [Utilizar tipos de enumeración en operaciones $filter](query-metadata-web-api.md#bkmk_filterEnumTypes) para filtrar por esta propiedad única. La siguiente consulta filtrará esos atributos en la entidad de cuenta que sean ApplicationRequired.

```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes?$select=SchemaName&$filter=RequiredLevel/Value eq Microsoft.Dynamics.CRM.AttributeRequiredLevel'ApplicationRequired'  
```

<a name="bkmk_retrieveAttributes"></a>

## <a name="retrieving-attributes"></a>Recuperar atributos

Si conoce el MetadataId para EntityMetadata y AttributeMetadata, puede recuperar un atributo individual y acceder a los valores de las propiedades mediante una consulta como la siguiente. Esta consulta recupera la propiedad LogicalName del atributo además de expandir la propiedad de navegación valorada como colección OptionSet. Tenga en cuenta que debe convertir el atributo como Microsoft.Dynamics.CRM.PicklistAttributeMetadata para obtener acceso a la propiedad de navegación valorada como colección OptionSet.  

 **Solicitud**
 ```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes(5967e7cc-afbb-4c10-bf7e-e7ef430c52be)/Microsoft.Dynamics.CRM.PicklistAttributeMetadata?$select=LogicalName&$expand=OptionSet HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```

 **Respuesta**
 ```http
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0

{
 "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions(70816501-edb9-4740-a16c-6a5efbc05d84)/Attributes/Microsoft.Dynamics.CRM.PicklistAttributeMetadata(LogicalName,OptionSet)/$entity",  
 "LogicalName": "preferredappointmentdaycode",  
 "MetadataId": "5967e7cc-afbb-4c10-bf7e-e7ef430c52be",  
 "OptionSet@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions(70816501-edb9-4740-a16c-6a5efbc05d84)/Attributes(5967e7cc-afbb-4c10-bf7e-e7ef430c52be)/Microsoft.Dynamics.CRM.PicklistAttributeMetadata/OptionSet/$entity",  
 "OptionSet": {  
  "Options": [  
   {  
    "Value": 0,  
    "Label": {  
     "LocalizedLabels": [  
      {  
       "Label": "Sunday",  
       "LanguageCode": 1033,  
       "IsManaged": true,  
       "MetadataId": "21d6a218-2341-db11-898a-0007e9e17ebd",  
       "HasChanged": null  
      }  
     ],  
     "UserLocalizedLabel": {  
      "Label": "Sunday",  
      "LanguageCode": 1033,  
      "IsManaged": true,  
      "MetadataId": "21d6a218-2341-db11-898a-0007e9e17ebd",  
      "HasChanged": null  
     }  
    },  
    "Description": {  
     "LocalizedLabels": [],  
     "UserLocalizedLabel": null  
    },  
    "Color": null,  
    "IsManaged": true,  
    "MetadataId": null,  
    "HasChanged": null  
   }  
Additional options removed for brevity  
  ],  
  "Description": {  
   "LocalizedLabels": [  
    {  
     "Label": "Day of the week that the account prefers for scheduling service activities.",  
     "LanguageCode": 1033,  
     "IsManaged": true,  
     "MetadataId": "1b67144d-ece0-4e83-a38b-b4d48e3f35d5",  
     "HasChanged": null  
    }  
   ],  
   "UserLocalizedLabel": {  
    "Label": "Day of the week that the account prefers for scheduling service activities.",  
    "LanguageCode": 1033,  
    "IsManaged": true,  
    "MetadataId": "1b67144d-ece0-4e83-a38b-b4d48e3f35d5",  
    "HasChanged": null  
   }  
  },  
  "DisplayName": {  
   "LocalizedLabels": [  
    {  
     "Label": "Preferred Day",  
     "LanguageCode": 1033,  
     "IsManaged": true,  
     "MetadataId": "ebb7e979-f9e3-40cd-a86d-50b479b1c5a4",  
     "HasChanged": null  
    }  
   ],  
   "UserLocalizedLabel": {  
    "Label": "Preferred Day",  
    "LanguageCode": 1033,  
    "IsManaged": true,  
    "MetadataId": "ebb7e979-f9e3-40cd-a86d-50b479b1c5a4",  
    "HasChanged": null  
   }  
  },  
  "IsCustomOptionSet": false,  
  "IsGlobal": false,  
  "IsManaged": true,  
  "IsCustomizable": {  
   "Value": true,  
   "CanBeChanged": false,  
   "ManagedPropertyLogicalName": "iscustomizable"  
  },  
  "Name": "account_preferredappointmentdaycode",  
  "OptionSetType": "Picklist",  
  "IntroducedVersion": null,  
  "MetadataId": "53f9933c-18a0-40a6-b4a5-b9610a101735",  
  "HasChanged": null  
 }  
}  
```

Si no requiere ninguna propiedad del atributo y solo desea los valores de una propiedad de navegación valorada como colección como OptionsSet, puede incluir esto en la URL y limitar las propiedades con una opción de consulta del sistema `$select` para una consulta algo más eficaz. En el siguiente ejemplo solo la propiedad Options del OptionSet está incluida.  

 **Solicitud**
 ```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes(5967e7cc-afbb-4c10-bf7e-e7ef430c52be)/Microsoft.Dynamics.CRM.PicklistAttributeMetadata/OptionSet?$select=Options HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```

 **Respuesta**
 ```http
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  

{  
 "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions('account')/Attributes(5967e7cc-afbb-4c10-bf7e-e7ef430c52be)/Microsoft.Dynamics.CRM.PicklistAttributeMetadata/OptionSet(Options)/$entity",  
 "Options": [{  
   "Value": 0,  
   "Label": {  
    "LocalizedLabels": [{  
     "Label": "Sunday",  
     "LanguageCode": 1033,  
     "IsManaged": true,  
     "MetadataId": "21d6a218-2341-db11-898a-0007e9e17ebd",  
     "HasChanged": null  
    }],  
    "UserLocalizedLabel": {  
     "Label": "Sunday",  
     "LanguageCode": 1033,  
     "IsManaged": true,  
     "MetadataId": "21d6a218-2341-db11-898a-0007e9e17ebd",  
     "HasChanged": null  
    }  
   },  
   "Description": {  
    "LocalizedLabels": [],  
    "UserLocalizedLabel": null  
   },  
   "Color": null,  
   "IsManaged": true,  
   "MetadataId": null,  
   "HasChanged": null  
  }  
Additional options removed for brevity  
 ],  
 "MetadataId": "53f9933c-18a0-40a6-b4a5-b9610a101735"  
}  
```

<a name="bkmk_queryRelationshipMetadata"></a>

## <a name="querying-relationship-metadata"></a>Consultar metadatos de relaciones

Puede recuperar metadatos de relaciones en el contexto de una entidad determinada en gran parte de la misma forma que pueda consultar atributos. Las propiedades de navegación valorada como colección `ManyToManyRelationships`, `ManyToOneRelationships` y `OneToManyRelationships` se pueden consultar como la propiedad de navegación valorada como colección `Attributes`. Más información: [Consultar atributos EntityMetadata](query-metadata-web-api.md#bkmk_queryAttributes)  

Sin embargo, las relaciones entre entidades también se pueden consultar con el conjunto de entidades `RelationshipDefinitions`. Puede usar una consulta como la siguiente para obtener la propiedad `SchemaName` para cada relación.

```http
GET [Organization URI]/api/data/v9.0/RelationshipDefinitions?$select=SchemaName  
```

Las propiedades disponibles al consultar este conjunto de entidades se limitan a las que están en <xref href="Microsoft.Dynamics.CRM.RelationshipMetadataBase?text=RelationshipMetadataBase EntityType" />. Para tener acceso a propiedades de los tipos de entidad que se heredan de `RelationshipMetadataBase` es necesario incluir una conversión en la consulta como la siguiente para devolver solo <xref href="Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata?text=OneToManyRelationshipMetadata EntityType" />.  

```http
GET [Organization URI]/api/data/v9.0/RelationshipDefinitions/Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata?$select=SchemaName  
```

Puesto que las entidades devueltas tienen el tipo `OneToManyRelationshipMetadata`, puede filtrar por propiedades como `ReferencedEntity` para crear una consulta para devolver solo las relaciones entre entidades de una a varias para una entidad específica, como la entidad de cuenta como se muestra en la siguiente consulta:  

```http
GET [Organization URI]/api/data/v9.0/RelationshipDefinitions/Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata?$select=SchemaName&$filter=ReferencedEntity eq 'account' 
```

Esa consulta esencialmente devolverá los mismos resultados que la siguiente consulta, que se filtra porque está incluida en propiedad de navegación valorada como colección de `EntityMetadataOneToManyRelationships` de la entidad de cuenta. La diferencia es que para la consulta anterior no necesita saber el `MetadataId` para la entidad de cuenta.  

```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='account')/OneToManyRelationships?$select=SchemaName  
```

<a name="bkmk_GlobalOptionSets"></a>

## <a name="querying-global-optionsets"></a>Consultar conjuntos de opciones globales

Puede usar la ruta de conjuntos de entidades `GlobalOptionSetDefinitions` para recuperar información sobre conjuntos de opciones globales, pero esta ruta de acceso no admite el uso de la opción de consulta del sistema `$filter`. Por lo tanto, a menos que conozca el `MetadataId` para un conjunto de opciones globales específico, solo puede recuperarlas todas. También puede obtener acceso a la definición de un conjunto de opciones globales dentro de la propiedad de navegación valorada como colección `GlobalOptionSet` para cualquier atributos que la utilice. Esto está disponible para todos los [tipos derivados EnumAttributeMetadata EntityType](/dynamics365/customer-engagement/web-api/enumattributemetadata?view=dynamics-ce-odata-9#Derived_Types). Más información: [Recuperar atributos](query-metadata-web-api.md#bkmk_retrieveAttributes)  

### <a name="see-also"></a>Vea también

[Usar la API web con metadatos de Common Data Service](use-web-api-metadata.md)<br />
[Recuperar metadatos por nombre o identificador de metadatos](retrieve-metadata-name-metadataid.md)<br />
[Entidades de metadatos y atributos con la API web](create-update-entity-definitions-using-web-api.md)<br />
[Relaciones de entidades de metadatos con la API web](create-update-entity-relationships-using-web-api.md)
