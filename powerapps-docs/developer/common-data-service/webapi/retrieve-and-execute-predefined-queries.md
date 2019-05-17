---
title: Recuperar y ejecutar consultas predefinidas (Common Data Service)| Microsoft Docs
description: Common Data Service proporciona una forma de que los administradores creen vistas del sistema que están disponibles para todos los usuarios. Lea cómo puede crear una consulta predefinida y usar FetchXML para crear una cadena de consulta para recuperar datos
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 3d771a18-3dc5-4372-a7c7-40b3b1f986d8
caps.latest.revision: 16
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

# <a name="retrieve-and-execute-predefined-queries"></a>Recuperar y ejecutar consultas predefinidas

Common Data Service proporciona una forma de que los administradores creen vistas del sistema que están disponibles para todos los usuarios. Los usuarios individuales pueden guardar consultas de búsqueda avanzada para su reutilización en la aplicación. Ambas representan consultas predefinidas que puede recuperar y ejecutar utilizando la API web. También puede redactar una consulta utilizando FetchXml y usarla para recuperar datos.

<a name="bkmk_predefinedQueries"></a>

## <a name="predefined-queries"></a>Consultas predefinidas

Common Data Service permite definir, guardar, y ejecutar dos tipos de consultas que se muestran aquí.

|Tipo de consulta|Descripción|
|----------------|-----------------|
|**Consulta guardada**|Vistas definidas por el sistema para una entidad. Estas vistas se almacenan en <xref href="Microsoft.Dynamics.CRM.savedquery?text=savedquery EntityType" />. Más información: [Personalizar vistas de entidad](../../model-driven-apps/customize-entity-views.md)| 
|**Consulta de usuario**|Búsquedas de búsqueda avanzada guardadas por los usuarios para una entidad. Estas vistas se almacenan en <xref href="Microsoft.Dynamics.CRM.userquery?text=userquery EntityType" />. Más información: [Entidad UserQuery (vista guardada)](../saved-queries.md)|

Los registros para ambos tipos de entidades contienen la definición FetchXML para que se devuelvan los datos. Puede buscar el tipo de entidad respectivo para recuperar el valor de clave principal. Con el valor de clave principal, puede ejecutar la consulta pasando el valor de clave principal. Por ejemplo, para ejecutar la consulta guardada **Cuentas activas**, primero debe obtener la clave principal mediante una consulta como ésta.

```http
GET [Organization URI]/api/data/v9.0/savedqueries?$select=name,savedqueryid&$filter=name eq 'Active Accounts'
```

Luego puede usar el valor de `savedqueryid` y pasarlo como el valor al parámetro savedQuery al conjunto de entidades de cuentas.

```http
GET [Organization URI]/api/data/v9.0/accounts?savedQuery=00000000-0000-0000-00aa-000010001002
```

Use el mismo método para obtener el userqueryid y pasarlo como el valor al parámetro `userQuery` al conjunto de entidades que coincida con el `returnedtypecode` correspondiente de la consulta guardada.

```http
GET [Organization URI]/api/data/v9.0/accounts?userQuery=121c6fd8-1975-e511-80d4-00155d2a68d1
```

### <a name="apply-a-query-to-any-collection-of-the-appropriate-type"></a>Aplicar una consulta a cualquier colección del tipo adecuado

Además de simplemente aplicar la consulta guardada a la colección principal del conjunto de entidades, también puede usar una consulta guardada o consulta de usuario para aplicar el mismo filtrado a cualquier colección del tipo adecuado de entidades. Por ejemplo, si desea aplicar una consulta solo a entidades relacionadas con una entidad específica, puede aplicar el mismo patrón. Por ejemplo, la siguiente URL aplicará la consulta **Oportunidades abiertas** a las oportunidades relacionadas con una cuenta específica a través de la propiedad de navegación valorada como colección `opportunity_parent_account`.

```http
GET [Organization URI]/api/data/v9.0/accounts(8f390c24-9c72-e511-80d4-00155d2a68d1)/opportunity_parent_account/?savedQuery=00000000-0000-0000-00aa-000010003001
```

<a name="bkmk_useFetchXML"></a>

## <a name="use-custom-fetchxml"></a>Usar FetchXML personalizado

FetchXML es un lenguaje de consultas propietario que proporciona capacidades para realizar agregación. Más información: [Usar FetchXML para consultar datos](../use-fetchxml-construct-query.md).

Puede pasar FetchXML codificado de dirección URL como consulta al conjunto de entidades correspondiente a la entidad raíz de la consulta con el parámetro de cadena de consulta `fetchXml` para devolver los resultados de la API web. Por ejemplo, puede tener el siguiente FetchXML que tiene cuenta como entidad.  

```xml  
<fetch mapping='logical'>
   <entity name='account'>
      <attribute name='accountid'/>
      <attribute name='name'/>
</entity>
</fetch>
```

El valor codificado de dirección URL de este FetchXML es como se indica a continuación.

```text
%3Cfetch%20mapping='logical'%3E%3Centity%20name='account'%3E%3Cattribute%20name='accountid'/%3E%3Cattribute%20name='name'/%3E%3C/entity%3E%3C/fetch%3E
```

La mayoría de los lenguaje de programación incluyen una función para codificar como dirección URL una cadena. Por ejemplo, en JavaScript se usa la función [encodeURI](http://www.ecma-international.org/ecma-262/5.1/). Debe codificar como dirección URL cualquier solicitud que envíe a cualquier servicio web RESTful. Si pega una dirección URL en la barra de direcciones del explorador debe codificar como dirección URL la dirección automáticamente. El siguiente ejemplo muestra una solicitud GET mediante el FetchXML indicado anteriormente con la ruta del conjunto de entidades para cuentas.

**Solicitud**

```http
GET [Organization URI]/api/data/v9.0/accounts?fetchXml=%3Cfetch%20mapping='logical'%3E%3Centity%20name='account'%3E%3Cattribute%20name='accountid'/%3E%3Cattribute%20name='name'/%3E%3C/entity%3E%3C/fetch%3E HTTP/1.1
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
  "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(accountid,name)","value":[  
    {  
      "@odata.etag":"W/\"506678\"","accountid":"89390c24-9c72-e511-80d4-00155d2a68d1","name":"Fourth Coffee (sample)"  
    },{  
      "@odata.etag":"W/\"502172\"","accountid":"8b390c24-9c72-e511-80d4-00155d2a68d1","name":"Litware, Inc. (sample)"  
    },{  
      "@odata.etag":"W/\"502174\"","accountid":"8d390c24-9c72-e511-80d4-00155d2a68d1","name":"Adventure Works (sample)"  
    },{  
      "@odata.etag":"W/\"506705\"","accountid":"8f390c24-9c72-e511-80d4-00155d2a68d1","name":"Fabrikam, Inc. (sample)"  
    },{  
      "@odata.etag":"W/\"506701\"","accountid":"91390c24-9c72-e511-80d4-00155d2a68d1","name":"Blue Yonder Airlines (sample)"  
    },{  
      "@odata.etag":"W/\"502180\"","accountid":"93390c24-9c72-e511-80d4-00155d2a68d1","name":"City Power & Light (sample)"  
    },{  
      "@odata.etag":"W/\"502182\"","accountid":"95390c24-9c72-e511-80d4-00155d2a68d1","name":"Contoso Pharmaceuticals (sample)"  
    },{  
      "@odata.etag":"W/\"506704\"","accountid":"97390c24-9c72-e511-80d4-00155d2a68d1","name":"Alpine Ski House (sample)"  
    },{  
      "@odata.etag":"W/\"502186\"","accountid":"99390c24-9c72-e511-80d4-00155d2a68d1","name":"A. Datum Corporation (sample)"  
    },{  
      "@odata.etag":"W/\"502188\"","accountid":"9b390c24-9c72-e511-80d4-00155d2a68d1","name":"Coho Winery (sample)"  
    },{  
      "@odata.etag":"W/\"504177\"","accountid":"0a3238d4-f973-e511-80d4-00155d2a68d1","name":"Litware, Inc."  
    }  
  ]  
}  
```

<a name="bkmk_WebAPIFetchPaging"></a>

### <a name="paging-with-fetchxml"></a>Paginación con FetchXML

Con FetchXML puede aplicar paginación estableciendo los atributos `page` y `count` del elemento `fetch`. Por ejemplo, para establecer una consulta para cuentas y limitar el número de entidades a 2 y devolver solamente la primera página, el fetchXML siguiente:

```xml
<fetch mapping="logical" page="1" count="2">  
 <entity name="account">  
  <attribute name="accountid" />  
  <attribute name="name" />  
  <attribute name="industrycode" />  
 <order attribute="name" />  
 </entity>  
</fetch>
```

<!-- TODO:
With a request using FetchXML you can also request a paging cookie and include it with your query. More information:[Page large result sets with FetchXML](../org-service/page-large-result-sets-with-fetchxml.md)   -->

Una cookie de paginación debe solicitarse como anotación. Establezca la preferencia `odata.include-annotations` para usar (o incluir) `Microsoft.Dynamics.CRM.fetchxmlpagingcookie` y una propiedad `@Microsoft.Dynamics.CRM.fetchxmlpagingcookie` será devuelta con el resultado.

<a name="bkmk_FetchXMLwithinBatch"></a>

### <a name="use-fetchxml-within-a-batch-request"></a>Use FetchXML en una solicitud de lote

La longitud de una dirección URL en una solicitud `GET` está limitada. Incluir FetchXML como parámetro en la dirección URL pueden alcanzar este límite.  Puede ejecutar una operación `$batch` con una solicitud `POST` como método para mover el FetchXML de la dirección URL al cuerpo de la solicitud donde no aplica este límite. Más información:[Ejecute las operaciones por lotes mediante API web](execute-batch-operations-using-web-api.md)

#### <a name="example"></a>Ejemplo

**Solicitud**

```http
POST [Organization URI]/api/data/v9.0/$batch HTTP/1.1

Content-Type:multipart/mixed;boundary=batch_AAA123
Accept:application/json
OData-MaxVersion:4.0
OData-Version:4.0

--batch_AAA123
Content-Type: application/http
Content-Transfer-Encoding: binary

GET [Organization URI]/api/data/v9.0/accounts?fetchXml=%3Cfetch%20mapping='logical'%3E%3Centity%20name='account'%3E%3Cattribute%20name='accountid'/%3E%3Cattribute%20name='name'/%3E%3Cattribute%20name='telephone1'/%3E%3Cattribute%20name='accountid'/%3E%3Cattribute%20name='creditonhold'/%3E%3C/entity%3E%3C/fetch%3E HTTP/1.1
Content-Type: application/json
OData-Version: 4.0
OData-MaxVersion: 4.0

--batch_AAA123--
```

**Respuesta**

```json
--batchresponse_cbfd44cd-a322-484e-913b-49e18af44e34
Content-Type: application/http
Content-Transfer-Encoding: binary

HTTP/1.1 200 OK
Content-Type: application/json; odata.metadata=minimal
OData-Version: 4.0

{  
   "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(accountid,name,telephone1,creditonhold)",
   "value":[  
      {  
         "@odata.etag":"W/\"563737\"",
         "accountid":"1f55c679-485e-e811-8151-000d3aa3c22a",
         "name":"Fourth Coffee (sample)",
         "telephone1":"+1-425-555-0121",
         "creditonhold":false
      },
      {  
         "@odata.etag":"W/\"563739\"",
         "accountid":"2555c679-485e-e811-8151-000d3aa3c22a",
         "name":"Litware, Inc. (sample)",
         "telephone1":"+1-425-555-0120",
         "creditonhold":false
      }
   ]
}
--batchresponse_cbfd44cd-a322-484e-913b-49e18af44e34--
```



## <a name="see-also"></a>Vea también

[Ejemplo de datos de consulta API (C#)](samples/query-data-csharp.md)<br />
[Ejemplo de datos de consulta de la API web (JavaScript del lado del cliente)](samples/query-data-client-side-javascript.md)<br />
[Realizar operaciones mediante la API web](perform-operations-web-api.md)<br />
[Componer solicitudes HTTP y administrar errores](compose-http-requests-handle-errors.md)<br />
[Consultar datos utilizando la API web](query-data-web-api.md)<br />
[Cree una entidad usando API web](create-entity-web-api.md)<br />
[Recuperar una entidad usando API web](retrieve-entity-using-web-api.md)<br />
[Actualizar y eliminar entidades mediante la API web](update-delete-entities-using-web-api.md)<br />
[Asociar y anular la asociación de entidades mediante la API web](associate-disassociate-entities-using-web-api.md)<br />
[Usar funciones de la API web](use-web-api-functions.md)<br />
[Usar acciones de la API web](use-web-api-actions.md)<br />
[Ejecute las operaciones por lotes mediante API web](execute-batch-operations-using-web-api.md)<br />
[Suplantar a otro usuario utilizando la API web](impersonate-another-user-web-api.md)<br />
[Realizar operaciones condicionales mediante la API web](perform-conditional-operations-using-web-api.md)<br />
