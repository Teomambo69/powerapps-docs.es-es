---
title: Uso del seguimiento de cambios para sincronizar los datos con sistemas externos (Common Data Service) | Microsoft Docs
description: La característica de seguimiento proporciona una forma de mantener los datos sincronizados de forma eficiente detectando qué datos se han modificado desde que los datos se extrajeron inicialmente o se sincronizaron por última vez.
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
ms.openlocfilehash: 157ddf1f1ddcfce1e479caf12c2a7197c5dc96c1
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155196"
---
# <a name="use-change-tracking-to-synchronize-data-with-external-systems"></a>Uso del seguimiento de cambios para sincronizar los datos con sistemas externos

La característica de seguimiento de Common Data Service proporciona una forma de mantener los datos sincronizados de forma eficiente detectando qué datos se han modificado desde que los datos se extrajeron inicialmente o se sincronizaron por última vez. Anteriormente, sin esta nueva característica, era difícil crear un mecanismo confiable y eficaz para determinar los registros que se habían cambiado en Common Data Service. Este tema analiza cómo recuperar los cambios de una entidad.  
  
<a name="BKMK_enable"></a>   
## <a name="enable-change-tracking-for-an-entity"></a>Habilitar el seguimiento de cambios de una entidad  

 Antes de recuperar los cambios para una entidad, asegúrese de que la característica de seguimiento de cambios está habilitada para esa entidad. Esta característica se pueden habilitar en la interfaz de usuario (UI) de personalización o mediante programación estableciendo la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ChangeTrackingEnabled> como `True`. La anotación `Org.OData.Capabilities.V1.ChangeTracking` se agrega a los conjuntos de entidades que tienen habilitado el seguimiento de cambios. Para ver las anotaciones en los metadatos de la entidad, haga lo siguiente 

 ```http 
 GET [Organization URI]/api/data/v9.0/$metadata?annotations=true
 ```
 Más información sobre anotaciones de metadatos en [Anotaciones de metadatos](webapi/web-api-types-operations.md#bkmk_metannot).
 
 Para obtener más información sobre el uso de la interfaz de usuario (UI) de personalización, consulte [Habilitar seguimiento de cambios para controlar la sincronización de datos](https://technet.microsoft.com/library/3fa9c316-9dc9-4b28-9abf-43a3fce5b01d.aspx).  
  
<a name="BKMK_webapi"></a>   
## <a name="retrieve-changes-for-an-entity-using-the-web-api"></a>Recuperar cambios de una entidad usando API web  
Los cambios realizados en las entidades pueden seguirse mediante solicitudes de la API Web, agregando `odata.track-changes` como encabezado preferente. El encabezado preferente `odata.track-changes` se usa para solicitar que se devuelva un *vínculo diferencial* que pueda usarse después para recuperar los cambios de la entidad.

Los vínculos diferenciales son vínculos opacos generados por servicios que el cliente utiliza para recuperar los cambios posteriores a un resultado. Se basan en una consulta de definición que describe el conjunto de resultados cuyos cambios se están siguiendo, por ejemplo, la solicitud que genera los resultados que contienen el vínculo diferencial. El vínculo diferencial codifica el conjunto de entidades cuyos se están siguiendo, junto con un punto de partida desde el que desea realizar un seguimiento de los cambios. Más información acerca de los vínculos diferenciales [Oasis OData versión 4.0 - Vínculos diferenciales](https://docs.oasis-open.org/odata/odata/v4.0/cs01/part1-protocol/odata-v4.0-cs01-part1-protocol.html#_Toc365046305)

<a name="BKMK_webapiexample"></a>   
## <a name="retrieve-changes-in-entities-using-web-api-example"></a>Ejemplo de recuperación de cambios en entidades usando la API Web

En este ejemplo se muestra cómo recuperar los cambios realizados en los datos de cuentas mediante la API web.

Solicitud
```http
GET [Organization URI]/org1/api/data/v9.0/accounts?$select=name,accountnumber,telephone1,fax HTTP/1.1
Prefer: odata.track-changes
Cache-Control: no-cache
OData-Version: 4.0
Content-Type: application/json
```
Respuesta
```json
{
  "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name,accountnumber,telephone1,fax)",
"@odata.deltaLink": "[Organization URI]/api/data/v9.0/accounts?$select=name,accountnumber,telephone1,fax&$deltatoken=919042%2108%2f22%2f2017%2008%3a10%3a44",
"value":[
           {
              "@odata.etag":"W/\"915244\"",
              "name":"Monte Orton",
              "accountnumber":null,
              "telephone1":"555000",
              "fax":"10101",
              "accountid":"60c4e274-0d87-e711-80e5-00155db19e6d"
           }
       ]
}
```
Puede usar el vínculo diferencial devuelto en el ejemplo anterior para capturar cambios en entidades. En este ejemplo que se ha creado una cuenta y se ha eliminado una cuenta existente. El vínculo diferencial devuelto desde la solicitud anterior recopila estos cambios, tal como se muestra en el ejemplo siguiente.

Solicitud
```http
GET [Organization URI]/api/data/v9.0/accounts?$select=name,accountnumber,telephone1,fax&$deltatoken=919042%2108%2f22%2f2017%2008%3a10%3a44
```
Respuesta
```json
{
          "@odata.context":"[Organization URI]/data/v9.0/$metadata#accounts(name,telephone1,fax)/$delta",
          "@odata.deltaLink":"[Organization URI]/api/data/v9.0/accounts?$select=name,telephone1,fax&$deltatoken=919058%2108%2f22%2f2017%2008%3a21%3a20",
"value":
    [
        {
            "@odata.etag":"W/\"915244\"",
            "name":"Monte Orton",
            "telephone1":"555000",
            "fax":"10101",
            "accountid":"60c4e274-0d87-e711-80e5-00155db19e6d"
        },
        {
            "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts/$deletedEntity",
            "id":"2e451703-c686-e711-80e5-00155db19e6d",
            "reason":"deleted"
        }
    ]
}
```
La respuesta para el vínculo diferencial devuelto en la solicitud de seguimiento de cambio inicial contiene otro vínculo diferencial. Este vínculo diferencial ayuda a recuperar todos los cambios posteriores de entidades. Si no hay cambios de entidad realizados después de la solicitud de seguimiento de cambio inicial invocada, se recibe una respuesta JSON vacía.

<a name="bkmk_count"></a>
## <a name="retrieve-count-of-the-changes-made-in-entities-using-web-api"></a>Recuperar el número de cambios efectuados en entidades usando la API Web
`$count` puede agregarse al vínculo diferencial devuelto en la primera solicitud de cambio inicial, como se muestra en el ejemplo siguiente para obtener el número de los cambios efectuados.

Solicitud
```http
GET [Organization URI]/api/data/v9.0/accounts/$count?$deltatoken=919042%2108%2f22%2f2017%2008%3a10%3a44
```

<a name="bkmk_unsupported"></a>
## <a name="query-options-not-supported-in-change-tracking-web-api-request"></a>Opciones de la consulta no admitidas en la solicitud de la API Web de seguimiento de cambios
Las opciones de consulta del sistema `$filter`, `$orderby` y `$top` no se admiten cuando se utiliza `odata.track-changes` como encabezado de la solicitud de la API web. Un mensaje de error de tipo "El parámetro de consulta `$filter`/ `$orderby`/ `$top` no se admite cuando está habilitado el seguimiento de cambios está habilitado." aparece al usar estas opciones de consulta en la solicitud de la API web.

<a name="BKMK_retrieve"></a>   
## <a name="retrieve-changes-for-an-entity-using-the-organization-service"></a>Recuperar cambios de una entidad usando un servicio de organización
 Cuando el seguimiento de cambios está habilitado para una entidad, puede usar el mensaje <xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityChangesRequest> para recuperar los cambios para esa entidad. La primera vez que se usa este mensaje devuelve todos los registros de la entidad y que los datos se pueden usar para rellenar el almacenamiento externo. El mensaje también devuelve un número de versión que se enviará con el uso siguiente del mensaje <xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityChangesRequest> de modo que solo se devolverán los datos de los cambios que se han producido desde esa versión.  
  
 Debe conocer las siguientes restricciones para recuperar los cambios de una entidad:  
  
- Solo se realizará seguimiento de una entidad en recuperación de cambios. Si recuperación de cambios se ejecuta sin la versión o token, el servidor lo tratará como la versión mínima del sistema, devolviendo todos los registros como nuevos. Los objetos eliminados no se devolverán.  
  
- Los cambios se devolverán si el último token se encuentra dentro de un valor predeterminado de 90 días. Si es superior a 90 días, el sistema devolverá todos los registros.  
  
- Si un cliente tiene un conjunto de cambios para una entidad, supongamos la versión 1, un registro se crea y elimina antes de la siguiente consulta cambios, éste obtendrá el elemento eliminado incluso aunque no tuviera el elemento para empezar.  
  
- Los registros se recuperan en el orden determinado por la lógica del lado del servidor. Normalmente, el usuario final obtendrá siempre todos los registros nuevos o actualizados primero (clasificados por número de versión) seguidos de los registros eliminados.  Si hay 3000 registros creados o actualizados y 2000 registros eliminados, Common Data Service devuelve una colección de 5000 registros, que tienen las primeras 3000 entradas formadas por registros nuevos o actualizados y las 2000 últimas entradas de registros eliminados.  
  
- Si la colección de registros nuevos o actualizados es superior a 5000, el usuario puede desplazarse entre las páginas de la colección.  
  
<a name="BKMK_SampleCode"></a>   
## <a name="sample-code"></a>Código de ejemplo   
 El fragmento de código siguiente muestra cómo el mensaje de `RetrieveEntityChangesRequest` se usa para recuperar los cambios de una entidad. Para ver el ejemplo completo, vea [Sincronizar datos con sistemas externos utilizando seguimiento de cambios](https://go.microsoft.com/fwlink/p/?LinkId=533957).  
  
```csharp
string token;

// Initialize page number.
int pageNumber = 1;
List<Entity> initialrecords = new List<Entity>();

// Retrieve records by using Change Tracking feature.
RetrieveEntityChangesRequest request = new RetrieveEntityChangesRequest();
request.EntityName = _customBooksEntityName.ToLower();
request.Columns = new ColumnSet("sample_bookcode", "sample_name", "sample_author");
request.PageInfo = new PagingInfo() { Count = 5000, PageNumber = 1, ReturnTotalRecordCount = false };


// Initial Synchronization. Retrieves all records as well as token value.
Console.WriteLine("Initial synchronization....retrieving all records.");
while (true)
{
    RetrieveEntityChangesResponse response = (RetrieveEntityChangesResponse)_serviceProxy.Execute(request);

    initialrecords.AddRange(response.EntityChanges.Changes.Select(x => (x as NewOrUpdatedItem).NewOrUpdatedEntity).ToArray());
    initialrecords.ForEach(x => Console.WriteLine("initial record id:{0}", x.Id));
    if (!response.EntityChanges.MoreRecords)
    {
        // Store token for later query
        token = response.EntityChanges.DataToken;
        break;

    }
    // Increment the page number to retrieve the next page.
    request.PageInfo.PageNumber++;
    // Set the paging cookie to the paging cookie returned from current results.
    request.PageInfo.PagingCookie = response.EntityChanges.PagingCookie;
}

```  
  
### <a name="see-also"></a>Vea también  
 [Defina claves alternativas para una entidad](define-alternate-keys-entity.md)   
 [Uso de claves alternativas](use-alternate-key-create-record.md)   
 [Actualizar Dynamics 365 con datos externos usando Upsert](use-upsert-insert-update-record.md)
