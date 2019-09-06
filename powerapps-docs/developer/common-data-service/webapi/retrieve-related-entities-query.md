---
title: Recuperar entidades relacionadas con una consulta (Common Data Service)| Microsoft Docs
description: Lea cómo recuperar entidades relacionadas para una entidad ampliando las propiedades de navegación.
ms.custom: ''
ms.date: 07/15/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 3D8FB9AF-3663-437A-988E-CBAE9579F167
caps.latest.revision: 78
author: susikka
ms.author: susikka
manager: shujoshi
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="retrieve-related-entities-with-a-query"></a>Recuperar entidades relacionadas con una consulta

Use la opción de consulta del sistema `$expand` en las propiedades de navegación para controlar qué datos de entidades relacionadas se devuelven. Hay dos tipos de propiedades de navegación:  
  
- Las propiedades de navegación *de un solo valor* corresponden a atributos de búsqueda que admiten relaciones de varios a uno y permiten establecer una referencia a otra entidad.  
  
- Las propiedades de navegación *valoradas como colección* corresponden a relaciones de uno a varios o de varios a varios.  
  
Si incluye solo el nombre de la propiedad de navegación, recibirá todas las propiedades de registros relacionados. Puede limitar las propiedades devueltas para registros relacionados con la opción de la consulta del sistema `$select` entre paréntesis después del nombre de propiedad de navegación. Use esta opción para las propiedades de navegación de un solo valor y valoradas como colección.  

> [!NOTE]
>  Para recuperar entidades relacionadas de una instancia de entidad, vea [Recuperar entidades relacionadas para una entidad expandiendo las propiedades de navegación](retrieve-entity-using-web-api.md#bkmk_expandRelated).  

<a bkmk="bkmk_retrieverelatedentityexpandsinglenavprop"></a>

## <a name="retrieve-related-entities-by-expanding-single-valued-navigation-properties"></a>Recuperar entidades relacionadas ampliando las propiedades de navegación con un valor

El ejemplo siguiente muestra cómo recuperar el contacto para todos los registros de la cuenta. Para los registros de contacto relacionados, solo recuperamos contactid y fullname.  
  
**Solicitud**  

```http 
GET [Organization URI]/api/data/v9.1/accounts?$select=name&$expand=primarycontactid($select=contactid,fullname) HTTP/1.1  
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
   "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name,primarycontactid,primarycontactid(contactid,fullname))",
   "value":[  
      {  
         "@odata.etag":"W/\"513475\"",
         "name":"Fourth Coffee (sample)",
         "accountid":"36dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"9cdbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Yvonne McKay (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"513477\"",
         "name":"Litware, Inc. (sample)",
         "accountid":"38dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"9edbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Susanna Stubberod (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"513479\"",
         "name":"Adventure Works (sample)",
         "accountid":"3adbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"a0dbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Nancy Anderson (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"513481\"",
         "name":"Fabrikam, Inc. (sample)",
         "accountid":"3cdbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"a2dbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Maria Campbell (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"514057\"",
         "name":"Blue Yonder Airlines (sample)",
         "accountid":"3edbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"a0dbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Nancy Anderson (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"513485\"",
         "name":"City Power & Light (sample)",
         "accountid":"40dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"a6dbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Scott Konersmann (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"513487\"",
         "name":"Contoso Pharmaceuticals (sample)",
         "accountid":"42dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"a8dbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Robert Lyon (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"513489\"",
         "name":"Alpine Ski House (sample)",
         "accountid":"44dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"aadbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Paul Cannon (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"513491\"",
         "name":"A. Datum Corporation (sample)",
         "accountid":"46dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"acdbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Rene Valdes (sample)"
         }
      },
      {  
         "@odata.etag":"W/\"513493\"",
         "name":"Coho Winery (sample)",
         "accountid":"48dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "contactid":"aedbf27c-8efb-e511-80d2-00155db07c77",
            "fullname":"Jim Glynn (sample)"
         }
      }
   ]
}    
```  

En lugar de devolver entidades relacionadas para conjuntos de entidades, también puede devolver referencias (vínculos) a las entidades relacionadas expandiendo la propiedad de navegación de un solo valor con la opción `$ref`. El siguiente ejemplo devuelve vínculos a los registros de contacto para todas las cuentas.  
  
 **Solicitud**

```http  
GET [Organization URI]/api/data/v9.1/accounts?$select=name&$expand=primarycontactid/$ref HTTP/1.1  
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
   "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name,primarycontactid)",
   "value":[  
      {  
         "@odata.etag":"W/\"513475\"",
         "name":"Fourth Coffee (sample)",
         "_primarycontactid_value":"9cdbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"36dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(9cdbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"513477\"",
         "name":"Litware, Inc. (sample)",
         "_primarycontactid_value":"9edbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"38dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(9edbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"513479\"",
         "name":"Adventure Works (sample)",
         "_primarycontactid_value":"a0dbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"3adbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(a0dbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"513481\"",
         "name":"Fabrikam, Inc. (sample)",
         "_primarycontactid_value":"a2dbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"3cdbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(a2dbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"514057\"",
         "name":"Blue Yonder Airlines (sample)",
         "_primarycontactid_value":"a0dbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"3edbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(a0dbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"513485\"",
         "name":"City Power & Light (sample)",
         "_primarycontactid_value":"a6dbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"40dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(a6dbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"513487\"",
         "name":"Contoso Pharmaceuticals (sample)",
         "_primarycontactid_value":"a8dbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"42dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(a8dbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"513489\"",
         "name":"Alpine Ski House (sample)",
         "_primarycontactid_value":"aadbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"44dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(aadbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"513491\"",
         "name":"A. Datum Corporation (sample)",
         "_primarycontactid_value":"acdbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"46dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(acdbf27c-8efb-e511-80d2-00155db07c77)"
         }
      },
      {  
         "@odata.etag":"W/\"513493\"",
         "name":"Coho Winery (sample)",
         "_primarycontactid_value":"aedbf27c-8efb-e511-80d2-00155db07c77",
         "accountid":"48dbf27c-8efb-e511-80d2-00155db07c77",
         "primarycontactid":{  
            "@odata.id":"[Organization URI]/api/data/v9.1/contacts(aedbf27c-8efb-e511-80d2-00155db07c77)"
         }
      }
   ]
}  
```  

<a bkmk="bkmk_retrieverelatedentityexpandcollectionnavprop"></a>

## <a name="retrieve-related-entities-by-expanding-collection-valued-navigation-properties"></a>Recuperar entidades relacionadas ampliando las propiedades de navegación de una colección

Si expande parámetros de navegación valorados como colección para recuperar entidades relacionadas para conjuntos de entidades, una propiedad `@odata.nextLink` será devuelta en su lugar para las entidades relacionadas. Debe usar el valor de la propiedad `@odata.nextLink` con una nueva solicitud `GET` para devolver los datos requeridos.  

El siguiente ejemplo recupera las tareas asignados a los 5 mejores registros de cuenta.  
  
**Solicitud**

```http 
GET [Organization URI]/api/data/v9.1/accounts?$top=5&$select=name&$expand=Account_Tasks($select%20=%20subject,%20scheduledstart) HTTP/1.1  
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
   "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name,Account_Tasks,Account_Tasks(subject,scheduledstart))",
   "value":[  
      {  
         "@odata.etag":"W/\"513475\"",
         "name":"Fourth Coffee (sample)",
         "accountid":"36dbf27c-8efb-e511-80d2-00155db07c77",
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(36dbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"
      },
      {  
         "@odata.etag":"W/\"513477\"",
         "name":"Litware, Inc. (sample)",
         "accountid":"38dbf27c-8efb-e511-80d2-00155db07c77",
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(38dbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"
      },
      {  
         "@odata.etag":"W/\"514074\"",
         "name":"Adventure Works (sample)",
         "accountid":"3adbf27c-8efb-e511-80d2-00155db07c77",
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(3adbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"
      },
      {  
         "@odata.etag":"W/\"513481\"",
         "name":"Fabrikam, Inc. (sample)",
         "accountid":"3cdbf27c-8efb-e511-80d2-00155db07c77",
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(3cdbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"
      },
      {  
         "@odata.etag":"W/\"514057\"",
         "name":"Blue Yonder Airlines (sample)",
         "accountid":"3edbf27c-8efb-e511-80d2-00155db07c77",
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(3edbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"
          }
       ]
    }
 
```  

<a bkmk="bkmk_retrieverelatedentitysingleandcollectionnavprop"></a>
  
## <a name="retrieve-related-entities-by-expanding-both-single-valued-and-collection-valued-navigation-properties"></a>Recuperar entidades relacionadas para una instancia de entidad expandiendo las propiedades de navegación valoradas tanto como de un valor como colección:

El siguiente ejemplo muestra cómo puede expandir entidades relacionadas para los conjuntos de entidad mediante propiedades de navegación únicas o de colección. Como se ha explicado anteriormente, si expande parámetros de navegación valorados como colección para recuperar entidades relacionadas para conjuntos de entidades, se devuelve una propiedad `@odata.nextLink` para las entidades relacionadas. Debe usar el valor de la propiedad `@odata.nextLink` con una nueva solicitud `GET` para devolver los datos requeridos.  
  
En este ejemplo, recuperamos el contacto y tareas asignadas a las 3 cuentas superiores.  
  
**Solicitud**

```http 
GET [Organization URI]/api/data/v9.1/accounts?$top=3&$select=name&$expand=primarycontactid($select=contactid,fullname),Account_Tasks($select=subject,scheduledstart)  HTTP/1.1  
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
   "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name,primarycontactid,Account_Tasks,primarycontactid(contactid,fullname),Account_Tasks(subject,scheduledstart))",
   "value":[  
      {  
         "@odata.etag":"W/\"550614\"",
         "name":"Fourth Coffee (sample)",
         "accountid":"5b9648c3-68f7-e511-80d3-00155db53318",
         "primarycontactid":{  
            "contactid":"c19648c3-68f7-e511-80d3-00155db53318",
            "fullname":"Yvonne McKay (sample)"
         },
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(5b9648c3-68f7-e511-80d3-00155db53318)/Account_Tasks?$select=subject,scheduledstart"
      },
      {  
         "@odata.etag":"W/\"550615\"",
         "name":"Litware, Inc. (sample)",
         "accountid":"5d9648c3-68f7-e511-80d3-00155db53318",
         "primarycontactid":{  
            "contactid":"c39648c3-68f7-e511-80d3-00155db53318",
            "fullname":"Susanna Stubberod (sample)"
         },
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(5d9648c3-68f7-e511-80d3-00155db53318)/Account_Tasks?$select=subject,scheduledstart"
      },
      {  
         "@odata.etag":"W/\"550616\"",
         "name":"Adventure Works (sample)",
         "accountid":"5f9648c3-68f7-e511-80d3-00155db53318",
         "primarycontactid":{  
            "contactid":"c59648c3-68f7-e511-80d3-00155db53318",
            "fullname":"Nancy Anderson (sample)"
         },
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(5f9648c3-68f7-e511-80d3-00155db53318)/Account_Tasks?$select=subject,scheduledstart"
      }
   ]
}
  
```
## <a name="filter-collection-values-based-on-data-in-related-entities"></a>Filtrar valores de colección en función de datos de entidades relacionadas

La API web permite usar dos operadores lambda, que son `any` y `all` para evaluar una expresión booleana en una colección. Más información: [Usar Operadores lambda](query-data-web-api.md#bkmk_LambdaOperators).

## <a name="see-also"></a>Vea también

[Consultar datos utilizando la API web](query-data-web-api.md)<br />
[Realizar operaciones mediante la API web](perform-operations-web-api.md)<br />
[Componer solicitudes HTTP y administrar errores](compose-http-requests-handle-errors.md)<br />
[Cree una entidad usando API web](create-entity-web-api.md)<br />
[Recuperar una entidad usando API web](retrieve-entity-using-web-api.md)<br />
[Actualizar y eliminar entidades mediante la API web](update-delete-entities-using-web-api.md)<br />
[Asociar y anular la asociación de entidades mediante la API web](associate-disassociate-entities-using-web-api.md)