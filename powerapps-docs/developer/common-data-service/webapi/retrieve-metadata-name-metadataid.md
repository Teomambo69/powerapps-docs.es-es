---
title: Recuperar metadatos por nombre o MetadataId (Common Data Service) | Microsoft Docs
description: Common Data Service usa una arquitectura controlada por metadatos que proporciona flexibilidad para crear entidades personalizadas y atributos adicionales de las entidades del sistema.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 80bcdd8e-7c4f-4fd5-8708-00345f5d0408
caps.latest.revision: 8
author: brandonsimons
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="retrieve-metadata-by-name-or-metadataid"></a>Recuperar metadatos por nombre o identificador de metadatos

Los aplicaciones pueden adaptarse a los cambios de configuración consultando los metadatos. Cuando conoce una de las propiedades clave de un elemento de metadatos, puede recuperar definiciones de metadatos mediante la API web.  

<a name="bkmk_byName"></a>

## <a name="retrieve-metadata-items-by-name"></a>Recuperar elementos de metadatos por nombre
  
Todos los elementos de metadatos recuperables tienen una clave principal `MetadataId` que se puede usar para recuperar elementos individuales. Para los tipos de metadatos que tienen una clave alternativa definida, puede recuperarlos por nombre.  
  
Recuperar elementos por nombre normalmente es más fácil porque probablemente tiene ya cierta referencia al nombre del elemento de metadatos en su código. La siguiente tabla enumera las propiedades de clave alternativa para recuperar elementos de metadatos por nombre  
  
|Elemento de metadatos|Clave alternativa|Ejemplo|  
|-------------------|-------------------|-------------|  
|Entidad|LogicalName|`GET /api/data/v9.0/EntityDefinitions(LogicalName='account')`|  
|Atributo|LogicalName|`GET /api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes(LogicalName='emailaddress1')`|  
|Relación|SchemaName|`GET /api/data/v9.0/RelationshipDefinitions(SchemaName='Account_Tasks')`|  
|Conjunto de opciones globales|Nombre|`GET /api/data/v9.0/GlobalOptionSetDefinitions(Name='metric_goaltype')`|  
  
<a name="bkmk_exampleByName"></a>

### <a name="example-retrieve-metadata-items-by-name"></a>Ejemplo: Recuperar elementos de metadatos por nombre

Un elemento común de metadatos que las personas desean recuperar son las opciones configuradas para un atributo determinado. El siguiente ejemplo muestra cómo recuperar las propiedades de `OptionSet` y `GlobalOptionSet` de un <xref href="Microsoft.Dynamics.CRM.PicklistAttributeMetadata?text=PicklistAttributeMetadata EntityType" />.  
  
> [!NOTE]
>  Expandir las propiedades de navegación de un solo valor `OptionSet` y `GlobalOptionSet` <xref href="Microsoft.Dynamics.CRM.PicklistAttributeMetadata?text=PicklistAttributeMetadata EntityType" /> le permite obtener la definición de opción si el atributo está configurado para usar conjuntos de opciones globales o el conjunto de opciones “local” en la entidad. Si es un conjunto de opciones “local”, la propiedad `GlobalOptionSet` será nula como se muestra a continuación.  
>   
>  Si el atributo usó un conjunto de opciones global, la propiedad `GlobalOptionSet` contendría las opciones definidas y la propiedad `OptionSet` sería nula.  
  
 **Solicitud**  

```http  
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes(LogicalName='accountcategorycode')/Microsoft.Dynamics.CRM.PicklistAttributeMetadata?$select=LogicalName&$expand=OptionSet($select=Options),GlobalOptionSet($select=Options) HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
```  
  
 **Respuesta**  

```http   
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions('account')/Attributes/Microsoft.Dynamics.CRM.PicklistAttributeMetadata(LogicalName,OptionSet,GlobalOptionSet,OptionSet(Options),GlobalOptionSet(Options))/$entity",  
    "LogicalName": "accountcategorycode",  
    "MetadataId": "118771ca-6fb9-4f60-8fd4-99b6124b63ad",  
    "OptionSet@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions('account')/Attributes(118771ca-6fb9-4f60-8fd4-99b6124b63ad)/Microsoft.Dynamics.CRM.PicklistAttributeMetadata/OptionSet(Options)/$entity",  
    "OptionSet": {  
        "Options": [{  
            "Value": 1,  
            "Label": {  
                "LocalizedLabels": [{  
                    "Label": "Preferred Customer",  
                    "LanguageCode": 1033,  
                    "IsManaged": true,  
                    "MetadataId": "0bd8a218-2341-db11-898a-0007e9e17ebd",  
                    "HasChanged": null  
                }],  
                "UserLocalizedLabel": {  
                    "Label": "Preferred Customer",  
                    "LanguageCode": 1033,  
                    "IsManaged": true,  
                    "MetadataId": "0bd8a218-2341-db11-898a-0007e9e17ebd",  
                    "HasChanged": null  
                }  
            },  
            "Description": {  
                "LocalizedLabels": [  
  
                ],  
                "UserLocalizedLabel": null  
            },  
            "Color": null,  
            "IsManaged": true,  
            "MetadataId": null,  
            "HasChanged": null  
        }, {  
            "Value": 2,  
            "Label": {  
                "LocalizedLabels": [{  
                    "Label": "Standard",  
                    "LanguageCode": 1033,  
                    "IsManaged": true,  
                    "MetadataId": "0dd8a218-2341-db11-898a-0007e9e17ebd",  
                    "HasChanged": null  
                }],  
                "UserLocalizedLabel": {  
                    "Label": "Standard",  
                    "LanguageCode": 1033,  
                    "IsManaged": true,  
                    "MetadataId": "0dd8a218-2341-db11-898a-0007e9e17ebd",  
                    "HasChanged": null  
                }  
            },  
            "Description": {  
                "LocalizedLabels": [  
  
                ],  
                "UserLocalizedLabel": null  
            },  
            "Color": null,  
            "IsManaged": true,  
            "MetadataId": null,  
            "HasChanged": null  
        }],  
        "MetadataId": "b994cdd8-5ce9-4ab9-bdd3-8888ebdb0407"  
    },  
    "GlobalOptionSet": null  
}  
```  
  
<a name="bkmk_byMetadataId"></a>
   
## <a name="retrieve-metadata-items-by-metadataid"></a>Recuperar elementos de metadatos por identificador de metadatos

Puesto que el `MetadataId` es la clave principal de los elementos de metadatos, para recuperar elementos individuales se sigue el mismo patrón usado para recuperar entidades de datos de negocio.  
  
|Elemento de metadatos|Ejemplo|  
|-------------------|-------------|  
|Entidad|`GET /api/data/v9.0/EntityDefinitions(<Entity MetadataId>)`|  
|Atributo|`GET /api/data/v9.0/EntityDefinitions(<Entity MetadataId>)/Attributes(<Attribute MetadataId>)`|  
|Relación|`GET /api/data/v9.0/RelationshipDefinitions(<Relationship MetadataId>)`|  
|Conjunto de opciones globales|`GET /api/data/v9.0/GlobalOptionSetDefinitions(<OptionSet MetadataId>)`|  
  
### <a name="example-retrieve-metadata-items-by-metadataid"></a>Ejemplo: Recuperar elementos de metadatos por identificador de metadatos  

Para lograr el mismo resultado que se muestra en [Ejemplo: Recuperar elementos de metadatos por nombre](#bkmk_exampleByName), deberá realizar una serie de operaciones de consulta para obtener `MetadataId` filtrando por la entidad `LogicalName` y después por el atributo `LogicalName`.  
  
 **Solicitud**

```http  
GET [Organization URI]/api/data/v9.0/EntityDefinitions?$filter=LogicalName%20eq%20'account'&$select=MetadataId HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
```  
  
 **Respuesta**

```http  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
  "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions(MetadataId)","value":[  
    {  
      "MetadataId":"70816501-edb9-4740-a16c-6a5efbc05d84"  
    }  
  ]  
}  
```  
  
 **Solicitud**

```http  
GET [Organization URI]/api/data/v9.0/EntityDefinitions(70816501-edb9-4740-a16c-6a5efbc05d84)/Attributes?$filter=LogicalName%20eq%20'accountcategorycode'&$select=MetadataId HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
```  
  
 **Respuesta**

```http  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions(70816501-edb9-4740-a16c-6a5efbc05d84)/Attributes(MetadataId)","value":[  
    {  
        "@odata.type": "#Microsoft.Dynamics.CRM.PicklistAttributeMetadata",  
        "MetadataId": "118771ca-6fb9-4f60-8fd4-99b6124b63ad"  
    }  
    ]  
}  
```  
  
 **Solicitud**

```http  
GET [Organization URI]/api/data/v9.0/EntityDefinitions(70816501-edb9-4740-a16c-6a5efbc05d84)/Attributes(118771ca-6fb9-4f60-8fd4-99b6124b63ad)/Microsoft.Dynamics.CRM.PicklistAttributeMetadata?$select=LogicalName&$expand=OptionSet($select=Options),GlobalOptionSet($select=Options) HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
```  
  
 **Respuesta**

```http
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions(70816501-edb9-4740-a16c-6a5efbc05d84)/Attributes/Microsoft.Dynamics.CRM.PicklistAttributeMetadata(LogicalName,OptionSet,GlobalOptionSet,OptionSet(Options),GlobalOptionSet(Options))/$entity",  
    "LogicalName": "accountcategorycode",  
    "MetadataId": "118771ca-6fb9-4f60-8fd4-99b6124b63ad",  
    "OptionSet@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions(70816501-edb9-4740-a16c-6a5efbc05d84)/Attributes(118771ca-6fb9-4f60-8fd4-99b6124b63ad)/Microsoft.Dynamics.CRM.PicklistAttributeMetadata/OptionSet(Options)/$entity",  
    "OptionSet": {  
        "Options": [{  
            "Value": 1,  
            "Label": {  
                "LocalizedLabels": [{  
                    "Label": "Preferred Customer",  
                    "LanguageCode": 1033,  
                    "IsManaged": true,  
                    "MetadataId": "0bd8a218-2341-db11-898a-0007e9e17ebd",  
                    "HasChanged": null  
                }],  
                "UserLocalizedLabel": {  
                    "Label": "Preferred Customer",  
                    "LanguageCode": 1033,  
                    "IsManaged": true,  
                    "MetadataId": "0bd8a218-2341-db11-898a-0007e9e17ebd",  
                    "HasChanged": null  
                }  
            },  
            "Description": {  
                "LocalizedLabels": [  
  
                ],  
                "UserLocalizedLabel": null  
            },  
            "Color": null,  
            "IsManaged": true,  
            "MetadataId": null,  
            "HasChanged": null  
        }, {  
            "Value": 2,  
            "Label": {  
                "LocalizedLabels": [{  
                    "Label": "Standard",  
                    "LanguageCode": 1033,  
                    "IsManaged": true,  
                    "MetadataId": "0dd8a218-2341-db11-898a-0007e9e17ebd",  
                    "HasChanged": null  
                }],  
                "UserLocalizedLabel": {  
                    "Label": "Standard",  
                    "LanguageCode": 1033,  
                    "IsManaged": true,  
                    "MetadataId": "0dd8a218-2341-db11-898a-0007e9e17ebd",  
                    "HasChanged": null  
                }  
            },  
            "Description": {  
                "LocalizedLabels": [  
  
                ],  
                "UserLocalizedLabel": null  
            },  
            "Color": null,  
            "IsManaged": true,  
            "MetadataId": null,  
            "HasChanged": null  
        }],  
        "MetadataId": "b994cdd8-5ce9-4ab9-bdd3-8888ebdb0407"  
    },  
    "GlobalOptionSet": null  
}  
```  
  
### <a name="see-also"></a>Vea también

[Usar la API web con metadatos de Common Data Service](use-web-api-metadata.md)<br />
[Consulta de metadatos utilizando la API web](query-metadata-web-api.md)<br />
[Crear y actualizar definiciones de entidad mediante la API web](create-update-entity-definitions-using-web-api.md)<br /> 
[Crear y actualizar relaciones de entidad mediante la API web](create-update-entity-relationships-using-web-api.md)
