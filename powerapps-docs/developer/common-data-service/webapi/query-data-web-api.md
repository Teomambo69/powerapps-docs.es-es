---
title: Consultar datos utilizando la API web (Common Data Service para aplicaciones) | Microsoft Docs
description: Lea distintas formas de hacer consultas con Common Data Service para aplicaciones para los datos de las aplicaciones mediante la web API de Common Data Service para aplicaciones y otros sistemas para consultar las opciones que se pueden aplicar en estas consultas
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: fc3ade34-9c4e-4c33-88a4-aa3842c5eee1
caps.latest.revision: 78
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="query-data-using-the-web-api"></a>Consultar datos utilizando la API web

Si desea recuperar los datos para un conjunto de entidades, use una solicitud `GET`. Para recuperar datos, puede aplicar las opciones de consulta para establecer criterios para los datos que desea y las propiedades de entidad que se deben devolver.  
    
<a name="bkmk_basicQuery"></a>
 
## <a name="basic-query-example"></a>Ejemplo de consulta básica

Este ejemplo consulta el conjunto de entidades de cuenta y usa las opciones de consulta del sistema `$select` y `$top` para devolver la propiedad de nombre para las tres primeras cuentas:  
  
 **Solicitud**

```http 
GET [Organization URI]/api/data/v9.0/accounts?$select=name&$top=3 HTTP/1.1  
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
"@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts(name)",  
"value": [  
{  
"@odata.etag": "W/\"501097\"",  
"name": "Fourth Coffee (sample)",  
"accountid": "89390c24-9c72-e511-80d4-00155d2a68d1"  
},  
{  
"@odata.etag": "W/\"501098\"",  
"name": "Litware, Inc. (sample)",  
"accountid": "8b390c24-9c72-e511-80d4-00155d2a68d1"  
},  
{  
"@odata.etag": "W/\"501099\"",  
"name": "Adventure Works (sample)",  
"accountid": "8d390c24-9c72-e511-80d4-00155d2a68d1"  
}  
]  
}  
```  
  
<a name="bkmk_limits"></a>

## <a name="limits-on-number-of-entities-returned"></a>Límites en el número de entidades devueltas

A menos que especifique un tamaño de página más pequeño, se devolverá un máximo de 5000 entidades para cada solicitud. Si hay más entidades que coinciden con los criterios del filtro de consulta, se devolverá una propiedad `@odata.nextLink` con los resultados. Use el valor de la propiedad `@odata.nextLink` con una nueva solicitud `GET` para devolver la siguiente página de datos.  
  
> [!NOTE]
>  Las consultas en las entidades del modelo no se limitan ni paginan. Más información: [Consultar metadatos mediante la API web](query-metadata-web-api.md)  
  
<a name="bkmk_specifyNumber"></a>

## <a name="specify-the-number-of-entities-to-return-in-a-page"></a>Especifique el número de entidades para devolver a una página

Use el valor de la preferencia `odata.maxpagesize` para solicitar al número de entidades devueltas en la respuesta.  
  
> [!NOTE]
>  No puede usar un valor de preferencia `odata.maxpagesize` superior a 5000.  
  
 En el siguiente ejemplo se consulta el conjunto de entidades de cuentas y devuelve la propiedad `name` para las tres primeras cuentas.  
  
 **Solicitud**

```http 
GET [Organization URI]/api/data/v9.0/accounts?$select=name HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Prefer: odata.maxpagesize=3  
```  
  
 **Respuesta**  

```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 402  
Preference-Applied: odata.maxpagesize=3  
  
{  
"@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts(name)",  
"value": [  
{  
"@odata.etag": "W/\"437194\"",  
"name": "Fourth Coffee (sample)",  
"accountid": "7d51925c-cde2-e411-80db-00155d2a68cb"  
},  
{  
"@odata.etag": "W/\"437195\"",  
"name": "Litware, Inc. (sample)",  
"accountid": "7f51925c-cde2-e411-80db-00155d2a68cb"  
},  
{  
"@odata.etag": "W/\"468026\"",  
"name": "Adventure Works (sample)",  
"accountid": "8151925c-cde2-e411-80db-00155d2a68cb"  
}  
],  
"@odata.nextLink": "[Organization URI]/api/data/v9.0/accounts?$select=name&$skiptoken=%3Ccookie%20pagenumber=%222%22%20pagingcookie=%22%253ccookie%2520page%253d%25221%2522%253e%253caccountid%2520last%253d%2522%257b8151925C-CDE2-E411-80DB-00155D2A68CB%257d%2522%2520first%253d%2522%257b7D51925C-CDE2-E411-80DB-00155D2A68CB%257d%2522%2520%252f%253e%253c%252fcookie%253e%22%20/%3E"  
}  
```  
  
Use el valor de la propiedad `@odata.nextLink` para solicitar el siguiente conjunto de registros. No cambie ni anexar opciones de consulta del sistema adicionales al valor. Para cada solicitud posterior de páginas adicionales debe usar el mismo valor de preferencia odata.maxpagesize que usó en la solicitud original. Además, almacene en caché los resultados devueltos o el valor de la propiedad `@odata.nextLink` para que se pueda volver a páginas anteriormente recuperadas.  
  
> [!NOTE]
>  El valor de la propiedad `@odata.nextLink` está codificado con URI. Si codifica con URI el valor antes de enviarlo, la información de cookie XML en la URL generará un error.  
  
<a name="bkmk_applyqueryOptions"></a>

## <a name="apply-system-query-options"></a>Aplicar opciones de consultas del sistema

Cada una de las opciones de consulta del sistema que anexa a la URL para el conjunto de entidades se agrega utilizando la sintaxis de cadenas de consulta. La primera se agrega después de [?] y las opciones de consulta posteriores se separan mediante [&]. Todas las opciones de consulta distinguen mayúsculas de minúsculas tal como se muestra en el siguiente ejemplo.  
  
```http 
GET [Organization URI]/api/data/v9.0/accounts?$select=name,revenue&$top=3&$filter=revenue gt 100000  
```  
  
<a name="bkmk_requestProperties"></a>
 
## <a name="request-specific-properties"></a>Propiedades específicas de solicitud

Use la opción de consulta del sistema `$select` para limitar las propiedades devueltas tal como se muestra en el siguiente ejemplo.  
  
```http 
GET [Organization URI]/api/data/v9.0/accounts?$select=name,revenue  
```  
  
> [!IMPORTANT]
>  Esta es una práctica recomendada de rendimiento. Si las propiedades no se especifican utilizando `$select`, todas las propiedades se devolverán.  
  
Al solicitar determinados tipos de propiedades puede esperar que las propiedades de solo lectura adicionales se devuelvan automáticamente.  
  
Si solicita un valor monetario, se devolverá la propiedad de búsqueda `_transactioncurrencyid_value`. Esta propiedad solo contiene el valor GUID de la divisa de transacción para que pueda usar este valor para recuperar información acerca de la divisa con la <xref href="Microsoft.Dynamics.CRM.transactioncurrency?text=transactioncurrency EntityType" />. De forma alternativa, al solicitar anotaciones también puede obtener más datos en la misma solicitud. Más información: [Recuperar datos sobre propiedades de búsqueda](#bkmk_lookupProperty)  
  
Si solicita una propiedad que forma parte de un atributo compuesto para una dirección, obtendrá además la propiedad compuesta. Por ejemplo, si la consulta solicita la propiedad `address1_line1` para un contacto, se devolverá además la propiedad `address1_composite`. 
  
<a name="bkmk_filter"></a>
 
## <a name="filter-results"></a>Filtrar resultados

Use la opción de consulta del sistema `$filter` para establecer criterios por los que se devolverán entidades.  
  
<a name="bkmk_buildInFilterOperators"></a>

### <a name="standard-filter-operators"></a>Operadores estándar de filtro

La API web es compatible con los operadores de filtro OData estándar que se muestran en la tabla siguiente.  
  
|Operador|Descripción|Ejemplo|  
|--------------|-----------------|-------------|  
|**Operadores de comparación**|||  
|`eq`|Es igual a|`$filter=revenue eq 100000`|  
|`ne`|No es igual a|`$filter=revenue ne 100000`|  
|`gt`|Mayor que|`$filter=revenue gt 100000`|  
|`ge`|Mayor o igual que|`$filter=revenue ge 100000`|  
|`lt`|Menor que|`$filter=revenue lt 100000`|  
|`le`|Menor o igual que|`$filter=revenue le 100000`|  
|**Operadores lógicos**|||  
|`and`|Lógico y|`$filter=revenue lt 100000 and revenue gt 2000`|  
|`or`|Disyunción lógica|`$filter=contains(name,'(sample)') or contains(name,'test')`|  
|`not`|Negación lógica|`$filter=not contains(name,'sample')`|  
|**Agrupación de operadores**|||  
|`( )`|Agrupaciones por prioridad|`(contains(name,'sample') or contains(name,'test')) and revenue gt 5000`|  
  
> [!NOTE]
>  Este es un subconjunto de las [operaciones de filtro integradas 11.2.5.1.1](http://docs.oasis-open.org/odata/odata/v4.0/errata02/os/complete/part1-protocol/odata-v4.0-errata02-os-part1-protocol-complete.html). Los operadores aritméticos y el operador de comparación no se admiten en la API web.  
  
<a name="bkmk_buildInQueryFunctions"></a>

### <a name="standard-query-functions"></a>Funciones estándar de consulta

La API web admite estas funciones de consulta de cadena de OData estándar.  
  
|Función|Ejemplo|  
|--------------|-------------|  
|`contains`|`$filter=contains(name,'(sample)')`|  
|`endswith`|`$filter=endswith(name,'Inc.')`|  
|`startswith`|`$filter=startswith(name,'a')`|  
  
> [!NOTE]
>  Este es un subconjunto de las [funciones de consulta integradas 11.2.5.1.2](http://docs.oasis-open.org/odata/odata/v4.0/errata02/os/complete/part1-protocol/odata-v4.0-errata02-os-part1-protocol-complete.html). `Date`, `Math`, `Type`, `Geo` y otras funciones de cadena no se admiten en la API web.  
  
### <a name="common-data-service-for-apps-web-api-query-functions"></a>Usar las funciones de consulta de la API web de Common Data Service para aplicaciones
 
Common Data Service para aplicaciones ofrece varias funciones especiales que aceptan parámetros, devuelven valores booleanos y se pueden usar como criterios de filtro en una consulta. Para obtener una lista de estas funciones, vea <xref:Microsoft.Dynamics.CRM.QueryFunctionIndex>. Lo siguiente es un ejemplo de la búsqueda <xref href="Microsoft.Dynamics.CRM.Between?text=Between Function" /> para cuentas con varios empleados entre 5 y 2000.  
  
```http 
GET [Organization URI]/api/data/v9.0/accounts?$select=name,numberofemployees&$filter=Microsoft.Dynamics.CRM.Between(PropertyName='numberofemployees',PropertyValues=["5","2000"])  
```  
  
Más información: [Crear una consulta con funciones](use-web-api-functions.md#bkmk_composeQueryWithFunctions).  
  
<a name="bkmk_order"></a>
 
## <a name="order-results"></a>Ordenar resultados

Especifique el orden en que los elementos se devuelven mediante la opción de consulta del sistema `$orderby`. Use el sufijo `asc` o `desc` para especificar orden ascendente o descendente respectivamente. El valor predeterminado es ascendente si no se aplica el sufijo. El ejemplo siguiente muestra la recuperación de propiedades de nombre e ingresos de cuentas ordenadas por ingreso ascendente y por nombre descendente.  
  
```http 
GET [Organization URI]/api/data/v9.0/accounts?$select=name,revenue,&$orderby=revenue asc,name desc&$filter=revenue ne null  
```  
  
<a name="bkmk_useParameterAliases"></a>

## <a name="use-parameter-aliases-with-system-query-options"></a>Uso de alias de parámetro con opciones de consulta del sistema

Puede usar de alias de parámetro para opciones de consulta del sistema `$filter` y `$orderby`. Los alias de parámetro permiten usar el mismo valor varias veces en una solicitud. Si al alias no se asigna un valor se da por hecho que es nulo.  
  
Sin alias de parámetros:

```http  
GET [Organization URI]/api/data/v9.0/accounts?$select=name,revenue,&$orderby=revenue asc,name desc&$filter=revenue ne null  
```  
  
 Con alias de parámetros:

```http  
GET [Organization URI]/api/data/v9.0/accounts?$select=name,revenue,&$orderby=@p1 asc,@p2 desc&$filter=@p1 ne @p3&@p1=revenue&@p2=name  
```  
  
También puede usar alias de parámetro al usar funciones. Más información: [Usar funciones web API](use-web-api-functions.md).  
  
<a name="bkmk_limitResults"></a>
 
## <a name="limit-results"></a>Limitar resultados

Puede limitar el número de resultados devueltos mediante la opción de consulta del sistema `$top`. El siguiente ejemplo solo devolverá las primeras tres entidades de cuenta.  
  
```http 
GET [Organization URI]/api/data/v9.0/accounts?$select=name,revenue&$top=3  
```  
  
> [!NOTE]
>  Si limita los resultados mediante `$top` evitará que se aplique la preferencia `odata.maxpagesize`. Puede usar la preferencia `odata.maxpagesize` o `$top`, pero no ambos al mismo tiempo. Para obtener más información acerca de `odata.maxpagesize`, consulte [Especificar el número de entidades que devolver en una página](query-data-web-api.md#bkmk_specifyNumber).  
>   
>  Tampoco debería usar `$top` con `$count`.  
  
<a name="bkmk_retrieveCount"></a>
 
## <a name="retrieve-a-count-of-entities"></a>Recuperar un recuento de entidades

Use la opción de consulta del sistema `$count` con un valor de `true` para incluir un recuento de entidades que coincidan con los criterios de filtro hasta 5000.  
  
> [!NOTE]
>  El valor de recuento no representa el número total de entidades del sistema. Está limitado por el número máximo de entidades que se pueden devueltas. Más información: [Límites en el número de entidades devueltas](#bkmk_limits)  
  
La propiedad de respuesta `@odata.count` contendrá el número de entidades que coinciden con los criterios de filtro con independencia de la limitación de la preferencia `odata.maxpagesize`.  
  
> [!NOTE]
>  No debería usar `$top` con `$count`.  
  
El siguiente ejemplo muestra que existen diez cuentas que coinciden con los criterios donde el nombre contiene "ejemplo", pero solo se devuelven las tres primeras cuentas.  
  
 **Solicitud**

```http 
GET [Organization URI]/api/data/v9.0/accounts?$select=name&$filter=contains(name,'sample')&$count=true HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Prefer: odata.maxpagesize=3  
```  
  
 **Respuesta** 
 
```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.maxpagesize=3  
  
{  
"@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name)",  
"@odata.count":10,  
"value":[  
{  
"@odata.etag":"W/\"502482\"","name":"Fourth Coffee (sample)","accountid":"655eaf89-f083-e511-80d3-00155d2a68d3"  
},{  
"@odata.etag":"W/\"502483\"","name":"Litware, Inc. (sample)","accountid":"675eaf89-f083-e511-80d3-00155d2a68d3"  
},{  
"@odata.etag":"W/\"502484\"","name":"Adventure Works (sample)","accountid":"695eaf89-f083-e511-80d3-00155d2a68d3"  
}  
],"@odata.nextLink":"[Organization URI]/api/data/v9.0/accounts?$select=name&$filter=contains(name,'sample')&$skiptoken=%3Ccookie%20pagenumber=%222%22%20pagingcookie=%22%253ccookie%2520page%253d%25221%2522%253e%253caccountid%2520last%253d%2522%257b695EAF89-F083-E511-80D3-00155D2A68D3%257d%2522%2520first%253d%2522%257b655EAF89-F083-E511-80D3-00155D2A68D3%257d%2522%2520%252f%253e%253c%252fcookie%253e%22%20istracking=%22False%22%20/%3E"  
}  
  
```  
  
 Si no desea que se devuelva ningún dato excepto el recuento, puede aplicar `$count` a cualquier colección para obtener únicamente el valor.  
  
 **Solicitud**  

```http 
GET [Organization URI]/api/data/v9.0/accounts/$count HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Respuesta**  
```http 
HTTP/1.1 200 OK  
Content-Type: text/plain  
OData-Version: 4.0  
  
10  
```  
  
<a name="bkmk_includeFormattedValues"></a>

## <a name="include-formatted-values"></a>Incluir valores con formato

Si desea recibir valores con formato para las propiedades con los resultados, use la preferencia `odata.include-annotations` con el valor de `OData.Community.Display.V1.FormattedValue`. La respuesta incluirá estos valores con propiedades que coinciden con la siguiente convención de nomenclatura:  
  
```  
<propertyname>@OData.Community.Display.V1.FormattedValue  
```  
 El siguiente ejemplo consulta el conjunto de entidades de cuentas y devuelve el primer registro, incluidas las propiedades que admiten valores con formato.  
  
 **Solicitud**

```http 
GET [Organization URI]/api/data/v9.0/accounts?$select=name,donotpostalmail,accountratingcode,numberofemployees,revenue&$top=1 HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Prefer: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
```  
  
 **Respuesta**  
```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
  
{  
"@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts(name,donotpostalmail,accountratingcode,numberofemployees,revenue)",  
"value": [  
{  
"@odata.etag": "W/"502170"",  
"name": "Fourth Coffee (sample)",  
"donotpostalmail@OData.Community.Display.V1.FormattedValue": "Allow",  
"donotpostalmail": false,  
"accountratingcode@OData.Community.Display.V1.FormattedValue": "Default Value",  
"accountratingcode": 1,  
"numberofemployees@OData.Community.Display.V1.FormattedValue": "9,500",  
"numberofemployees": 9500,  
"revenue@OData.Community.Display.V1.FormattedValue": "$100,000.00",  
"revenue": 100000,  
"accountid": "89390c24-9c72-e511-80d4-00155d2a68d1",  
"transactioncurrencyid_value": "50b6dd7b-f16d-e511-80d0-00155db07cb1" } ]  
}    
```  
  
<a name="bkmk_lookupProperty"></a>

## <a name="retrieve-data-about-lookup-properties"></a>Recuperar datos sobre propiedades de búsqueda

Si la consulta incluye propiedades de búsqueda puede solicitar anotaciones que proporcionarán información adicional sobre los datos de esas propiedades. La mayor parte del tiempo, los mismos datos se pueden derivar con el conocimiento de las propiedades de navegación de un solo valor y los datos incluidos en las entidades relacionadas. Sin embargo, en los casos en que la propiedad represente un atributo de búsqueda que puede hacer referencia a más de un tipo de entidad, esta información puede indicarle a qué tipo de entidad hace referencia la propiedad de búsqueda. Más información: [Propiedades de búsqueda](web-api-types-operations.md#bkmk_lookupProperties)  
  
Existen dos tipos de anotaciones adicionales disponibles para estas propiedades,  
  
|Anotación|Descripción|  
|----------------|-----------------|  
|Microsoft.Dynamics.CRM.associatednavigationproperty|El nombre de la propiedad de navegación de un solo valor que incluye la referencia a la entidad.|  
|Microsoft.Dynamics.CRM.lookuplogicalname|El nombre lógico de la entidad a la que hace referencia la búsqueda.|  
  
Estas propiedades también pueden incluir valores con formato como se describe en [Incluir valores con formato](query-data-web-api.md#bkmk_includeFormattedValues). Al igual que los valores con formato, puede devolver las otras anotaciones con la preferencia `odata.include-annotations` establecida con el tipo específico de anotación que desea, o puede establecer el valor como `"*"` y devolver los tres. El siguiente ejemplo muestra la solicitud y la respuesta par recuperar información sobre la propiedad de búsqueda `_customerid_value` de la entidad de incidente con anotaciones incluidas.  
  
 **Solicitud**  

```http 
GET [Organization URI]/api/data/v9.0/incidents(39dd0b31-ed8b-e511-80d2-00155d2a68d4)?$select=title,customerid_value&$expand=customerid_contact($select=fullname) HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Prefer: odata.include-annotations="*"  
```  
  
 **Respuesta**  

```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="*"  
  
{  
"@odata.context":"[Organization URI]/api/data/v9.0/$metadata#incidents(title,_customerid_value,customerid_contact(fullname))/$entity",  
"@odata.etag":"W/\"504696\"",  
"_customerid_value@Microsoft.Dynamics.CRM.associatednavigationproperty":"customerid_contact",  
"_customerid_value@Microsoft.Dynamics.CRM.lookuplogicalname":"contact",  
"_customerid_value@OData.Community.Display.V1.FormattedValue":"Susanna Stubberod (sample)",  
"_customerid_value":"7ddd0b31-ed8b-e511-80d2-00155d2a68d4",  
"incidentid":"39dd0b31-ed8b-e511-80d2-00155d2a68d4",  
"customerid_contact":{  
"@odata.etag":"W/\"503587\"",  
"fullname":"Susanna Stubberod (sample)",  
"contactid":"7ddd0b31-ed8b-e511-80d2-00155d2a68d4"  
}  
}  
```  
  
<a name="BKMK_FilterNavProperties"></a>

## <a name="filter-records-based-on-single-valued-navigation-property"></a>Filtrar registros en función de propiedad de navegación de un solo valor

Las propiedades de navegación le permiten tener acceso a datos relacionados con la entidad actual. Las propiedades de navegación *de un solo valor* corresponden a atributos de búsqueda que admiten relaciones de varios a uno y permiten establecer una referencia a otra entidad. Más información: [Propiedades de navegación](web-api-types-operations.md#bkmk_navprops)  
  
Puede filtrar los registros del conjunto de entidad en función de los valores de propiedad de navegación de un solo valor. Por ejemplo, puede recuperar cuentas secundarias para la cuenta especificado. Solo puede usar el valor del atributo principal de la entidad a la que se hace referencia mediante una propiedad de navegación de un solo valor para filtrar registros.  
  
 Por ejemplo:  
  
-   Recupere todas las cuentas coincidentes para un ID de contacto especificado  
  
    **Solicitud** 
 
    ```http 
    GET [Organization URI]/api/data/v9.0/accounts?$select=name&$filter=primarycontactid/contactid%20eq%20a0dbf27c-8efb-e511-80d2-00155db07c77 HTTP/1.1  
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
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name)",  
    "value":[  
    {  
    "@odata.etag":"W/\"513479\"",  
    "name":"Adventure Works (sample)",  
    "accountid":"3adbf27c-8efb-e511-80d2-00155db07c77"  
    },{  
    "@odata.etag":"W/\"514057\"",  
    "name":"Blue Yonder Airlines (sample)",  
    "accountid":"3edbf27c-8efb-e511-80d2-00155db07c77"  
    }  
    ]  
    }  
    ```  
  
-   Recupere cuentas secundarias para el ID de cuenta especificado.  
  
    **Solicitud**  

    ```http 
    GET [Organization URI]/api/data/v9.0/accounts?$select=name&$filter=parentaccountid/accountid%20eq%203adbf27c-8efb-e511-80d2-00155db07c77  
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
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name)",  
    "value":[  
    {  
    "@odata.etag":"W/\"514058\"",  
    "name":"Sample Child Account 1",  
    "accountid":"915e89f5-29fc-e511-80d2-00155db07c77"  
    },{  
    "@odata.etag":"W/\"514061\"",  
    "name":"Sample Child Account 2",  
    "accountid":"03312500-2afc-e511-80d2-00155db07c77"  
    }  
    ]  
    }    
    ```  
  
<a name="bkmk_expandRelated"></a>

## <a name="retrieve-related-entities-by-expanding-navigation-properties"></a>Recuperar entidades relacionadas ampliando las propiedades de navegación

Use la opción de consulta del sistema `$expand` en las propiedades de navegación para controlar qué datos de entidades relacionadas se devuelven. Hay dos tipos de propiedades de navegación:  
  
- Las propiedades de navegación *de un solo valor* corresponden a atributos de búsqueda que admiten relaciones de varios a uno y permiten establecer una referencia a otra entidad.  
  
- Las propiedades de navegación *valoradas como colección* corresponden a relaciones de uno a varios o de varios a varios.  
  
Si incluye solo el nombre de la propiedad de navegación, recibirá todas las propiedades de registros relacionados. Puede limitar las propiedades devueltas para registros relacionados con la opción de la consulta del sistema `$select` entre paréntesis después del nombre de propiedad de navegación. Use esta opción para las propiedades de navegación de un solo valor y valoradas como colección.  
  
> [!NOTE]
>  Para recuperar entidades relacionadas de una instancia de entidad, vea [Recuperar entidades relacionadas para una entidad expandiendo las propiedades de navegación](retrieve-entity-using-web-api.md#bkmk_expandRelated).  
  
- **Recupere entidades relacionadas expandiendo las propiedades de navegación de un solo valor**: El siguiente ejemplo demuestra cómo recuperar el contacto para todos los registros de cuenta. Para los registros de contacto relacionados, solo recuperamos contactid y fullname.  
  
     **Solicitud**  

    ```http 
    GET [Organization URI]/api/data/v9.0/accounts?$select=name&$expand=primarycontactid($select=contactid,fullname) HTTP/1.1  
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
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name,primarycontactid,primarycontactid(contactid,fullname))","value":[  
    {  
    "@odata.etag":"W/\"513475\"","name":"Fourth Coffee (sample)","accountid":"36dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"9cdbf27c-8efb-e511-80d2-00155db07c77","fullname":"Yvonne McKay (sample)"  
    }  
    },{  
    "@odata.etag":"W/\"513477\"","name":"Litware, Inc. (sample)","accountid":"38dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"9edbf27c-8efb-e511-80d2-00155db07c77","fullname":"Susanna Stubberod (sample)"  
    }  
    },{  
    "@odata.etag":"W/\"513479\"","name":"Adventure Works (sample)","accountid":"3adbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"a0dbf27c-8efb-e511-80d2-00155db07c77","fullname":"Nancy Anderson (sample)"  
    }  
    },{  
    "@odata.etag":"W/\"513481\"","name":"Fabrikam, Inc. (sample)","accountid":"3cdbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"a2dbf27c-8efb-e511-80d2-00155db07c77","fullname":"Maria Campbell (sample)"  
    }  
    },{  
    "@odata.etag":"W/\"514057\"","name":"Blue Yonder Airlines (sample)","accountid":"3edbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"a0dbf27c-8efb-e511-80d2-00155db07c77","fullname":"Nancy Anderson (sample)"  
    }  
    },{  
    "@odata.etag":"W/\"513485\"","name":"City Power & Light (sample)","accountid":"40dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"a6dbf27c-8efb-e511-80d2-00155db07c77","fullname":"Scott Konersmann (sample)"  
    }  
    },{  
    "@odata.etag":"W/\"513487\"","name":"Contoso Pharmaceuticals (sample)","accountid":"42dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"a8dbf27c-8efb-e511-80d2-00155db07c77","fullname":"Robert Lyon (sample)"  
    }  
    },{  
    "@odata.etag":"W/\"513489\"","name":"Alpine Ski House (sample)","accountid":"44dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"aadbf27c-8efb-e511-80d2-00155db07c77","fullname":"Paul Cannon (sample)"  
    }  
    },{  
    "@odata.etag":"W/\"513491\"","name":"A. Datum Corporation (sample)","accountid":"46dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"acdbf27c-8efb-e511-80d2-00155db07c77","fullname":"Rene Valdes (sample)"  
    }  
    },{  
    "@odata.etag":"W/\"513493\"","name":"Coho Winery (sample)","accountid":"48dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "contactid":"aedbf27c-8efb-e511-80d2-00155db07c77","fullname":"Jim Glynn (sample)"  
    }  
    }  
    ]  
    }    
    ```  

En lugar de devolver entidades relacionadas para conjuntos de entidades, también puede devolver referencias (vínculos) a las entidades relacionadas expandiendo la propiedad de navegación de un solo valor con la opción `$ref`. El siguiente ejemplo devuelve vínculos a los registros de contacto para todas las cuentas.  
  
 **Solicitud**

```http  
    GET [Organization URI]/api/data/v9.0/accounts?$select=name&$expand=primarycontactid/$ref HTTP/1.1  
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
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name,primarycontactid)","value":[  
    {  
    "@odata.etag":"W/\"513475\"","name":"Fourth Coffee (sample)","_primarycontactid_value":"9cdbf27c-8efb-e511-80d2-00155db07c77","accountid":"36dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(9cdbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    },{  
    "@odata.etag":"W/\"513477\"","name":"Litware, Inc. (sample)","_primarycontactid_value":"9edbf27c-8efb-e511-80d2-00155db07c77","accountid":"38dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(9edbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    },{  
    "@odata.etag":"W/\"513479\"","name":"Adventure Works (sample)","_primarycontactid_value":"a0dbf27c-8efb-e511-80d2-00155db07c77","accountid":"3adbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(a0dbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    },{  
    "@odata.etag":"W/\"513481\"","name":"Fabrikam, Inc. (sample)","_primarycontactid_value":"a2dbf27c-8efb-e511-80d2-00155db07c77","accountid":"3cdbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(a2dbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    },{  
    "@odata.etag":"W/\"514057\"","name":"Blue Yonder Airlines (sample)","_primarycontactid_value":"a0dbf27c-8efb-e511-80d2-00155db07c77","accountid":"3edbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(a0dbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    },{  
    "@odata.etag":"W/\"513485\"","name":"City Power & Light (sample)","_primarycontactid_value":"a6dbf27c-8efb-e511-80d2-00155db07c77","accountid":"40dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(a6dbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    },{  
    "@odata.etag":"W/\"513487\"","name":"Contoso Pharmaceuticals (sample)","_primarycontactid_value":"a8dbf27c-8efb-e511-80d2-00155db07c77","accountid":"42dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(a8dbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    },{  
    "@odata.etag":"W/\"513489\"","name":"Alpine Ski House (sample)","_primarycontactid_value":"aadbf27c-8efb-e511-80d2-00155db07c77","accountid":"44dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(aadbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    },{  
    "@odata.etag":"W/\"513491\"","name":"A. Datum Corporation (sample)","_primarycontactid_value":"acdbf27c-8efb-e511-80d2-00155db07c77","accountid":"46dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(acdbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    },{  
    "@odata.etag":"W/\"513493\"","name":"Coho Winery (sample)","_primarycontactid_value":"aedbf27c-8efb-e511-80d2-00155db07c77","accountid":"48dbf27c-8efb-e511-80d2-00155db07c77","primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(aedbf27c-8efb-e511-80d2-00155db07c77)"  
    }  
    }  
    ]  
    }  
```  

- **Recupere entidades relacionadas expandiendo las propiedades de navegación valoradas como colección**: Si expande los parámetros de navegación valorados como una colección-para recuperar entidades relacionadas para conjuntos de entidades, se devolverá una propiedad @odata.nextLink para las entidades relacionadas. Debe usar el valor de la propiedad @odata.nextLink con una nueva solicitud GET para devolver los datos requeridos.  
  
    El siguiente ejemplo recupera las tareas asignados a los 5 mejores registros de cuenta.  
  
     **Solicitud**

    ```http 
        GET [Organization URI]/api/data/v9.0/accounts?$top=5&$select=name&$expand=Account_Tasks($select%20=%20subject,%20scheduledstart) HTTP/1.1  
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
        "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name,Account_Tasks,Account_Tasks(subject,scheduledstart))","value":[  
        {  
        "@odata.etag":"W/\"513475\"","name":"Fourth Coffee (sample)","accountid":"36dbf27c-8efb-e511-80d2-00155db07c77","Account_Tasks":[  
  
        ],"Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.0/accounts(36dbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"  
        },{  
        "@odata.etag":"W/\"513477\"","name":"Litware, Inc. (sample)","accountid":"38dbf27c-8efb-e511-80d2-00155db07c77","Account_Tasks":[  
  
        ],"Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.0/accounts(38dbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"  
        },{  
        "@odata.etag":"W/\"514074\"","name":"Adventure Works (sample)","accountid":"3adbf27c-8efb-e511-80d2-00155db07c77","Account_Tasks":[  
  
        ],"Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.0/accounts(3adbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"  
        },{  
        "@odata.etag":"W/\"513481\"","name":"Fabrikam, Inc. (sample)","accountid":"3cdbf27c-8efb-e511-80d2-00155db07c77","Account_Tasks":[  
  
        ],"Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.0/accounts(3cdbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"  
        },{  
        "@odata.etag":"W/\"514057\"","name":"Blue Yonder Airlines (sample)","accountid":"3edbf27c-8efb-e511-80d2-00155db07c77","Account_Tasks":[  
  
        ],"Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.0/accounts(3edbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select%20=%20subject,%20scheduledstart"  
        }  
        ]  
        }  
    ```  
  
- **Recupere entidades relacionadas expandiendo las propiedades de navegación de un solo valor y valoradas como colección**: El siguiente ejemplo demuestra cómo puede expandir entidades relacionadas para conjuntos de entidades utilizando propiedades de navegación de un solo valor y valoradas como colección. Como se ha explicado anteriormente, si expande parámetros de navegación valorados como colección para recuperar entidades relacionadas para conjuntos de entidades, se devuelve una propiedad @odata.nextLink para las entidades relacionadas. Debe usar el valor de la propiedad @odata.nextLink con una nueva solicitud GET para devolver los datos requeridos.  
  
     En este ejemplo, recuperamos el contacto y tareas asignadas a las 3 cuentas superiores.  
  
     **Solicitud**

    ```http 
    GET [Organization URI]/api/data/v9.0/accounts?$top=3&$select=name&$expand=primarycontactid($select=contactid,fullname),Account_Tasks($select=subject,scheduledstart)  HTTP/1.1  
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
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name,primarycontactid,Account_Tasks,primarycontactid(contactid,fullname),Account_Tasks(subject,scheduledstart))","value":[  
    {  
    "@odata.etag":"W/\"550614\"",  
    "name":"Fourth Coffee (sample)",  
    "accountid":"5b9648c3-68f7-e511-80d3-00155db53318",  
    "primarycontactid":{  
    "contactid":"c19648c3-68f7-e511-80d3-00155db53318",  
    "fullname":"Yvonne McKay (sample)"  
    },  
    "Account_Tasks":[  
  
    ],"Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.0/accounts(5b9648c3-68f7-e511-80d3-00155db53318)/Account_Tasks?$select=subject,scheduledstart"  
    },{  
    "@odata.etag":"W/\"550615\"",  
    "name":"Litware, Inc. (sample)",  
    "accountid":"5d9648c3-68f7-e511-80d3-00155db53318",  
    "primarycontactid":{  
    "contactid":"c39648c3-68f7-e511-80d3-00155db53318",  
    "fullname":"Susanna Stubberod (sample)"  
    },"Account_Tasks":[  
  
    ],"Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.0/accounts(5d9648c3-68f7-e511-80d3-00155db53318)/Account_Tasks?$select=subject,scheduledstart"  
    },{  
    "@odata.etag":"W/\"550616\"",  
    "name":"Adventure Works (sample)",  
    "accountid":"5f9648c3-68f7-e511-80d3-00155db53318",  
    "primarycontactid":{  
    "contactid":"c59648c3-68f7-e511-80d3-00155db53318",  
    "fullname":"Nancy Anderson (sample)"  
    },"Account_Tasks":[  
  
    ],"Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.0/accounts(5f9648c3-68f7-e511-80d3-00155db53318)/Account_Tasks?$select=subject,scheduledstart"  
    }  
    ]  
    }  
    ```

## <a name="filter-results-based-on-values-of-collection-valued-navigation-properties"></a>Filtrar resultados según los valores de las propiedades de navegación valorada como colección

No puede usar OData $filter para establecer criterios aplicables a valores en propiedades de navegación valorada como colección en una sola operación.
Tiene dos opciones:
- Crear una consulta con FetchXML.  Más información: Usar FetchXML personalizado
- Iterar en los resultados filtrando entidades individuales basadas en valores en la colección con varias operaciones.

Normalmente, el uso de FetchXML debe proporcionar un mejor rendimiento, porque el filtrado se puede aplicar del lado del servidor en una sola operación. El ejemplo siguiente muestra cómo aplicar el filtro en valores de propiedades de colección para una entidad de vínculo.

```xml
<fetch version="1.0" output-format="xml-platform" mapping="logical" distinct="true">
  <entity name="systemuser">
    <attribute name="fullname" />
    <attribute name="businessunitid" />
    <attribute name="title" />
    <attribute name="address1_telephone1" />
    <attribute name="positionid" />
    <attribute name="systemuserid" />
    <order attribute="fullname" descending="false" />
    <link-entity name="teammembership" from="systemuserid" to="systemuserid" visible="false" intersect="true">
      <link-entity name="team" from="teamid" to="teamid" alias="ab">
        <filter type="and">
          <condition attribute="administratorid" operator="eq-userid" />
        </filter>
      </link-entity>
    </link-entity>
  </entity>
</fetch>
```
  
### <a name="see-also"></a>Vea también

[Ejemplo de datos de consulta API (C#)](samples/query-data-csharp.md)<br />
[Ejemplo de datos de consulta de la API web (JavaScript del lado del cliente)](samples/query-data-client-side-javascript.md)<br />
[Realizar operaciones mediante la API web](perform-operations-web-api.md)<br />
[Componer solicitudes HTTP y administrar errores](compose-http-requests-handle-errors.md)<br />
[Cree una entidad usando API web](create-entity-web-api.md)<br />
[Recuperar una entidad usando API web](retrieve-entity-using-web-api.md)<br />
[Actualizar y eliminar entidades mediante la API web](update-delete-entities-using-web-api.md)<br />
[Asociar y anular la asociación de entidades mediante la API web](associate-disassociate-entities-using-web-api.md)<br />
[Usar funciones de la API web](use-web-api-functions.md)<br />
[Usar acciones de la API web](use-web-api-actions.md)<br />
[Ejecute las operaciones por lotes mediante API web](execute-batch-operations-using-web-api.md)<br />
[Suplantar a otro usuario utilizando la API web](impersonate-another-user-web-api.md)<br />
[Realizar operaciones condicionales mediante la API web](perform-conditional-operations-using-web-api.md)