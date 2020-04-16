---
title: Ejemplos de operaciones condicionales de la API web (Common Data Service)| Microsoft Docs
description: Este grupo de ejemplos demuestra cómo realizar operaciones que se basen condicionalmente en la versión del registro de entidad contenido en el servidor de Common Data Service y/o mantenido actualmente por el cliente.
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: f2e5d22b-93fe-43b7-af15-3e281f3b3084
caps.latest.revision: 13
author: JimDaly
ms.author: jdaly
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 924368f5d72a11fb94445b5e283bfe180871c681
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154964"
---
# <a name="web-api-conditional-operations-sample"></a>Ejemplo de operaciones condicionales de la API web

Este grupo de ejemplos demuestra cómo realizar operaciones que se basen condicionalmente en la versión del registro de entidad contenido en el servidor de Common Data Service y/o mantenido actualmente por el cliente. Para obtener más información, consulte [realizar operaciones condicionales mediante la API web](perform-conditional-operations-using-web-api.md). Este ejemplo se implementa como proyecto independiente para los siguientes idiomas:  
  
 [Ejemplo de operaciones condicionales de la API web (C#)](samples/conditional-operations-csharp.md)  
 
 La API web de Common Data Service sigue las convenciones del protocolo [OData v4.0](https://www.odata.org/documentation/), que usa [ETags](https://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part1-protocol/odata-v4.0-errata03-os-part1-protocol-complete.html#_Toc453752236) para implementar el control de versiones del recurso. Las operaciones condicionales de la API web dependen de este mecanismo de versiones.  
  
 En este tema se explican la estructura y el contenido de los ejemplos en un nivel superior de lenguaje neutro. Detalla las solicitudes y las respuestas HTTP, y la salida del programa asociada, en el caso correspondiente. Revise los temas de ejemplo vinculados anteriores para obtener implementaciones específicas del idioma y detalles relacionados sobre cómo realizar las operaciones descritas en este tema.  
  
## <a name="demonstrates"></a>Demostraciones

 Este ejemplo se divide en tres secciones principales, enumeradas en la tabla siguiente.   Cada sección contiene un conjunto de operaciones API Web relacionadas que se analizan con más detalle en la sección conceptual asociada del tema [realizar operaciones condicionales mediante la API Web](perform-conditional-operations-using-web-api.md).  
  
|Sección de código|Temas conceptuales asociados|  
|------------------|----------------------------------|  
|[GET condicional](#bkmk_conditionalGet)|[Recuperaciones condicionales](perform-conditional-operations-using-web-api.md#bkmk_DetectIfChanged)|  
|[Simultaneidad optimista al eliminar y actualizar](#bkmk_optimisiticConcurrency)|[Aplicar simultaneidad optimista](perform-conditional-operations-using-web-api.md#bkmk_Applyoptimisticconcurrency)|  
|[Controlar operaciones de upsert](#bkmk_controllingUpsert)|[Limitar operaciones de upsert](perform-conditional-operations-using-web-api.md#bkmk_limitUpsertOperations)|  
  
 Las siguientes secciones contienen una breve explicación de las operaciones de la API web de Common Data Service realizadas, junto con mensajes HTTP correspondientes y la salida asociada de la consola, que es la misma para cada implementación de idioma. Para razones de brevedad, se han omitido los encabezados HTTP menos pertinentes. Las direcciones URI de los registros variarán con la dirección de la organización base y el identificador del registro asignado por el servidor de Common Data Service.  
  
<a name="bkmk_sampleData"></a>
   
## <a name="sample-data"></a>Datos de ejemplo

 El ejemplo crea el registro siguiente antes de que ejecuten las secciones de código principales.  
  
|Tipo de entidad|Propiedades asignadas por el cliente|Propiedades asignadas por el servidor|  
|-----------------|---------------------------------|---------------------------------|  
|<xref:Microsoft.Dynamics.CRM.account>|Nombre: `Contoso Ltd.` <br />Ingresos: `5000000`<br />Teléfono: `555-0000`<br />Descripción: `Parent company of Contoso Pharmaceuticals, etc.`|ID: `14e151db-9b4f-e611-80e0-00155da84c08`<br />Etag inicial: `W/"628448"`|  
  
<a name="bkmk_conditionalGet"></a>

## <a name="conditional-get"></a>GET condicional

 Esta sección del programa muestra cómo realizar recuperaciones condicionales para optimizar el ancho de banda de red y el procesamiento del servidor mientras se mantiene el estado del registro más actual en el cliente. Más información:[Recuperaciones condicionales](perform-conditional-operations-using-web-api.md#bkmk_DetectIfChanged).  
  
1.  Intente recuperar la cuenta `Contoso Ltd.` solo si *no* coincide con la versión actual, identificada por el valor de ETag inicial que se devolvió al crear el registro de cuenta. Esta condición se representa por el encabezado `If-None-Match`.  
  
 **Solicitud**  
  
   ```http  
   GET https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08)?$select=name,revenue,telephone1,description HTTP/1.1  
   If-None-Match: W/"628448"  
   OData-MaxVersion: 4.0  
   OData-Version: 4.0  
   Accept: application/json  

   ```  
  
 **Respuesta**  
  
   ```http  
   HTTP/1.1 304 Not Modified  
   ```  
  
 **Salida de la consola**  
  
   ```  
   Instance retrieved using ETag: W/"628448"  
   Expected outcome: Entity was not modified so nothing was returned.  
   ```  

   El valor de respuesta, `304 Not Modified`, indica que el registro actual es el más actual, por lo que el servidor *no* devuelve el registro solicitado en el cuerpo de respuesta.  
  
2.  Actualice la cuenta modificando su propiedad de número de teléfono principal.  
  
 **Solicitud**  
  
   ```http
   PUT https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08)/telephone1 HTTP/1.1  
   OData-MaxVersion: 4.0  
   OData-Version: 4.0  
   Accept: application/json  
   Content-Type: application/json  
   {  
      "value": "555-0001"  
   }  
   ```  
  
 **Respuesta**  
  
   ```http
   HTTP/1.1 204 No Content  
   ```  
  
 **Salida de la consola**  
  
   ```  
   Account telephone number updated.  
   ```  
  
3.  Reintente la misma operación GET condicional, de nuevo con el valor de ETag original. Esta vez la operación devuelve los datos solicitados porque la versión en el servidor es diferente (y más reciente) que la versión identificada en la solicitud. Como en todas las recuperaciones de registro, la respuesta incluye un encabezado de ETag que identifica la versión actual.  
  
 **Solicitud**  
  
   ```http
   GET https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08)?$select=name,revenue,telephone1,description HTTP/1.1  
   If-None-Match: W/"628448"  
   OData-MaxVersion: 4.0  
   OData-Version: 4.0  
   Accept: application/json  
   ```  
  
 **Respuesta**  
  
   ```http
   HTTP/1.1 200 OK  
   Content-Type: application/json; odata.metadata=minimal  
   ETag: W/"628460"  
   {  
      "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,revenue,telephone1,description)/$entity",  
      "@odata.etag":"W/\"628460\"",  
      "name":"Contoso Ltd",  
      "revenue":5000000.0000,  
      "telephone1":"555-0001",  
      "description":"Parent company of Contoso Pharmaceuticals, etc.",  
      "accountid":"14e151db-9b4f-e611-80e0-00155da84c08",  
      "_transactioncurrencyid_value":"0d4ed62e-95f7-e511-80d1-00155da84c03"  
   }  
   ```  
  
 **Salida de la consola**  
  
   ```
   Instance retrieved using ETag: W/"628448"  
   {  
      "@odata.context": "https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,revenue,telephone1,description)/$entity",  
      "@odata.etag": "W/\"628460\"",  
      "name": "Contoso Ltd",  
      "revenue": 5000000.0,  
      "telephone1": "555-0001",  
      "description": "Parent company of Contoso Pharmaceuticals, etc.",  
      "accountid": "14e151db-9b4f-e611-80e0-00155da84c08",  
      "_transactioncurrencyid_value": "0d4ed62e-95f7-e511-80d1-00155da84c03"  
   }  
  
   ```  
  
<a name="bkmk_optimisiticConcurrency"></a>
  
## <a name="optimistic-concurrency-on-delete-and-update"></a>Simultaneidad optimista al eliminar y actualizar
 
 Esta sección del programa muestra cómo realizar operaciones de eliminación y actualización condicionales.  El uso más común para tales operaciones es implementar un enfoque de simultaneidad optimista del procesamiento de registros en un entorno multiusuario. Más información:[Aplicar simultaneidad optimista](perform-conditional-operations-using-web-api.md#bkmk_Applyoptimisticconcurrency)  
  
1.  Intente eliminar la cuenta original si y solo si coincide con la versión original (valor de ETag).  Esta condición se representa por el encabezado `If-Match`.  Esta operación produce error porque el registro de cuenta se actualizó en la sección anterior, por lo que su versión se actualizó en el servidor.  
  
 **Solicitud**  
  
   ```http
   DELETE https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08) HTTP/1.1  
   If-Match: W/"628448"  
   OData-MaxVersion: 4.0  
   OData-Version: 4.0  
   Accept: application/json  
   ```  
  
 **Respuesta**  
  
   ```http  
    HTTP/1.1 412 Precondition Failed  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  
    {  
      "error":{  
        "code":"","message":"The version of the existing record doesn't match the RowVersion property provided.", . . .  
        }  
    }  
   ```  
  
 **Salida de la consola**  
  
   ```  
   Expected Error: The version of the existing record doesn't match the property provided.  
         Account not deleted using ETag 'W/"628448"', status code: '412'.  
   ```  
  
2.  Intente actualizar la cuenta si y solo si coincide con el valor de ETag original.  Una vez más esta condición está representada por el encabezado `If-Match` y la operación produce un error por la misma razón.  
  
 **Solicitud**  
  
   ```http  
    PATCH https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08) HTTP/1.1  
    If-Match: W/"628448"  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    Accept: application/json  
    Content-Type: application/json; charset=utf-8  
    {  
      "telephone1": "555-0002",  
      "revenue": 6000000  
    }    
   ```  
  
 **Respuesta**  
  
   ```http  
    HTTP/1.1 412 Precondition Failed  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  
    {  
      "error":{  
        "code":"","message":"The version of the existing record doesn't match the RowVersion property provided.", . . .   
      }  
    }    
   ```  
  
 **Salida de la consola**  
  
   ```  
    Expected Error: The version of the existing record doesn't match the property provided.  
            Account not updated using ETag 'W/"628448"', status code: '412'.  
   ```  
  
3.  Reintente una actualización, pero en lugar de usar el valor de ETag actual obtenido de la última recuperación de registro de la sección anterior.  
  
 **Solicitud**  
  
   ```http
    PATCH https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08) HTTP/1.1  
    If-Match: W/"628460"  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    Accept: application/json  
    {  
      "telephone1": "555-0003",  
      "revenue": 6000000  
    }  
   ```  
  
 **Respuesta**  
  
   ```http
    HTTP/1.1 204 No Content  
   ```  
  
 **Salida de la consola**  
  
   ```  
    Account successfully updated using ETag: W/"628460", status code: '204'.  
   ```  
  
4.  Confirme que la actualización se realizado satisfactoriamente recuperando y generando el estado de cuenta actual.  Esto usa una solicitud GET básica.  
  
 **Solicitud**  
  
   ```http 
    GET https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08)?$select=name,revenue,telephone1,description HTTP/1.1  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    Accept: application/json  
   ```  
  
 **Respuesta**  
  
   ```http
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    ETag: W/"628461"  
    OData-Version: 4.0  
    {  
      "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,revenue,telephone1,description)/$entity",  
      "@odata.etag":"W/\"628461\"",  
      "name":"Contoso Ltd",  
      "revenue":6000000.0000,  
      "telephone1":"555-0003",  
      "description":"Parent company of Contoso Pharmaceuticals, etc.",  
      "accountid":"14e151db-9b4f-e611-80e0-00155da84c08",  
      "_transactioncurrencyid_value":"0d4ed62e-95f7-e511-80d1-00155da84c03"  
    }  
   ```  
  
 **Salida de la consola**  
  
   ```
    {  
      "@odata.context": "https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,revenue,telephone1,description)/$entity",  
      "@odata.etag": "W/\"628461\"",  
      "name": "Contoso Ltd",  
      "revenue": 6000000.0,  
      "telephone1": "555-0003",  
      "description": "Parent company of Contoso Pharmaceuticals, etc.",  
      "accountid": "14e151db-9b4f-e611-80e0-00155da84c08",  
      "_transactioncurrencyid_value": "0d4ed62e-95f7-e511-80d1-00155da84c03"  
    }  
   ```  
  
<a name="bkmk_controllingUpsert"></a>

## <a name="controlling-upsert-operations"></a>Controlar operaciones de upsert

 Esta sección del programa muestra cómo realizar operaciones `PATCH` condicionales, limitando las operaciones de upsert a realizarse como operaciones solo de actualización o solo de inserción. Más información:[Limitar operaciones de upsert](perform-conditional-operations-using-web-api.md#bkmk_limitUpsertOperations).  
  
1.  Intente insertar, sin actualizar, las propiedades de teléfono principal e ingresos para esta cuenta. El encabezado `If-None-Match` con el valor de `*` representa esta condición de upsert. Esta operación produce error porque este registro de cuenta aún existe en el servidor (a menos que se haya eliminado simultáneamente por otro usuario o proceso).  
  
 **Solicitud**  
  
   ```http
    PATCH https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08) HTTP/1.1  
    If-None-Match: *  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    Accept: application/json  
    Content-Type: application/json; charset=utf-8  
    {  
      "telephone1": "555-0004",  
      "revenue": 7500000  
    }  
   ```  
  
 **Respuesta**  
  
   ```http
    HTTP/1.1 412 Precondition Failed  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  
    {  
      "error":{  
        "code":"","message":"A record with matching key values already exists.", . . .  
      }  
    }  
   ```  
  
 **Salida de la consola**  
  
   ```   
    Expected Error: A record with matching key values already exists.  
            Account not updated using ETag 'W/"628448", status code: '412'.    
   ```  
  
2.  Intente realizar la misma operación de actualización sin creación. Para lograrlo, el encabezado `If-Match` condicional se usa con un valor de `*`.  Esta operación se realiza correctamente porque el registro existe en el servidor.  
  
 **Solicitud**  
  
   ```http
    PATCH https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08) HTTP/1.1  
    If-Match: *  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    Accept: application/json  
    Content-Type: application/json; charset=utf-8  
    {  
      "telephone1": "555-0005",  
      "revenue": 7500000  
    }  
   ```  
  
 **Respuesta**  
  
   ```http
    HTTP/1.1 204 No Content  
   ```  
  
 **Salida de la consola**  
  
   ```  
    Account updated using If-Match '*'  
   ```  
  
3.  Recupere y genere el estado de cuenta actual con una solicitud `GET` básica. Tenga en cuenta que el valor de ETag devuelto ha cambiado para reflejar la versión nueva y actualizada del registro de cuenta.  
  
 **Solicitud**  
  
   ```http  
    GET https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08)?$select=name,revenue,telephone1,description HTTP/1.1  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    Accept: application/json    
   ```  
  
 **Respuesta**  
  
   ```http  
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    ETag: W/"628463"  
    OData-Version: 4.0  
    {  
      "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,revenue,telephone1,description)/$entity",  
      "@odata.etag":"W/\"628463\"",  
      "name":"Contoso Ltd","revenue":7500000.0000,  
      "telephone1":"555-0005",  
      "description":"Parent company of Contoso Pharmaceuticals, etc.",  
      "accountid":"14e151db-9b4f-e611-80e0-00155da84c08",  
      "_transactioncurrencyid_value":"0d4ed62e-95f7-e511-80d1-00155da84c03"  
    }    
   ```  
  
 **Salida de la consola**  
  
   ```http    
    {  
      "@odata.context": "https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,revenue,telephone1,description)/$entity",  
      "@odata.etag": "W/\"628463\"",  
      "name": "Contoso Ltd",  
      "revenue": 7500000.0,  
      "telephone1": "555-0005",  
      "description": "Parent company of Contoso Pharmaceuticals, etc.",  
      "accountid": "14e151db-9b4f-e611-80e0-00155da84c08",  
      "_transactioncurrencyid_value": "0d4ed62e-95f7-e511-80d1-00155da84c03"  
    }    
   ```  
  
4.  Elimine la cuenta con un `DELETE` básico.  
  
 **Solicitud**  
  
   ```http    
    DELETE https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08) HTTP/1.1  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    Accept: application/json    
   ```  
  
 **Respuesta**  
  
   ```http
    HTTP/1.1 204 No Content  
   ```  
  
 **Salida de la consola**  
  
   ```  
    Account was deleted.  
   ```  
  
5.  Igual que en el paso 2, intente actualizar la cuenta si existe.  Una vez más, esta condición se representa por el encabezado `If-Match` con un valor de `*`.  Esta operación produce error porque este registro se acababa de eliminar. Sin embargo, si este encabezado `If-Match` estaba ausente, la operación básica resultante de upsert debe crear correctamente un nuevo registro.  
  
 **Solicitud**  
  
   ```http  
    PATCH https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08) HTTP/1.1  
    If-Match: *  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    Accept: application/json  
    Content-Type: application/json; charset=utf-8  
    {  
      "telephone1": "555-0006",  
      "revenue": 7500000  
    }    
   ```  
  
 **Respuesta**  
  
   ```http    
    HTTP/1.1 404 Not Found  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  
    {  
      "error":{  
        "code":"","message":"account With Id = 14e151db-9b4f-e611-80e0-00155da84c08 Does Not Exist", . . .  
      }  
    }    
   ```  
  
 **Salida de la consola**  
  
   ```    
    Expected Error: Account with Id = 14e151db-9b4f-e611-80e0-00155da84c08 does not exist.  
    Account not updated because it does not exist, status code: '404'.    
   ```  
  
 No hay necesidad de limpiar datos de ejemplo porque la cuenta de registro ya se eliminó en el paso 4.  
  
### <a name="see-also"></a>Vea también

[Usar la API web de Common Data Service](overview.md)<br />
[Realizar operaciones condicionales mediante la API web](perform-conditional-operations-using-web-api.md)<br />
[Ejemplo de operaciones condicionales de la API web (C#)](samples/conditional-operations-csharp.md)   
