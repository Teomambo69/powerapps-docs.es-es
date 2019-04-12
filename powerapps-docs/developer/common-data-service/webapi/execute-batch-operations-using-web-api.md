---
title: Ejecución de operaciones por lotes utilizando la API web (Common Data Service)| Microsoft Docs
description: Las operaciones por lotes le permiten agrupar varias operaciones en una sola solicitud HTTP. Lea cómo ejecutar las operaciones por lotes con la API web
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 799b2346-bda1-4a26-a330-79d0927a7743
caps.latest.revision: 11
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="execute-batch-operations-using-the-web-api"></a>Ejecute las operaciones por lotes mediante API web

Puede agrupar varias operaciones en una sola solicitud HTTP con una operación por lotes.  
  
<a name="bkmk_Whentousebatchrequests"></a>

## <a name="when-to-use-batch-requests"></a>Cuándo usar solicitudes por lotes

El valor que las solicitudes por lotes proporcionan es que pueden incluir conjuntos de cambios, que proporcionan una forma de empaquetar varias operaciones que se realizan correcta o incorrectamente como grupo. En comparación con otras operaciones que se pueden realizar a través de la API web, estas son más difíciles de crear sin algún modelo de objetos que incluya la serialización de objetos o una descripción más profunda del protocolo HTTP porque el cuerpo de la solicitud es esencialmente un documento de texto que debe cumplir requisitos muy específicos.  
  
Recuerde que las entidades asociadas se pueden crear en una sola operación más fácilmente que usando una solicitud por lotes. La solicitudes por lotes son más convenientes al realizar operaciones en entidades que no están asociadas entre sí cuando todas las operaciones se deben realizar en una sola operación transaccional.  
  
Además, las respuestas devueltas son esencialmente documentos de texto en lugar de objetos que pueden fácilmente ser analizados en JSON. Necesitará analizar el texto de la respuesta o localizar una biblioteca de código auxiliar para tener acceso a los datos de la respuesta.  
 
>[!NOTE]
>  La solicitudes por lotes pueden contener hasta 100 solicitudes individuales y no pueden contener otras solicitudes por lotes.  
  
<a name="bkmk_BatchRequests"></a> 

## <a name="batch-requests"></a>Solicitudes por lotes

Use una solicitud POST para enviar una operación por lotes que contenga varias solicitudes. Una solicitud por lotes puede incluir solicitudes GET y conjuntos de cambios. Para usar las funcionalidades transaccionales de solicitudes por lotes, solo las operaciones que cambiarán datos se pueden incluir en un conjunto de cambios. Las solicitudes GET no se deben incluir en el conjunto de cambios.  
  
La solicitud POST que contiene el lote debe tener un encabezado del tipo contenido con un valor establecido como multiparte/mixto con un conjunto de límites para incluir el identificador del lote utilizando este patrón:  
  
```  
--batch_<unique identifier>  
```  
  
El identificador único no necesita ser un GUID, pero debe ser único. Cada elemento dentro del lote debe ir precedido del identificador de lote con un encabezado Content-Type y Content-Transfer-Encoding como el siguiente:  
  
```  
--batch_WKQS9Yui9r  
Content-Type: application/http  
Content-Transfer-Encoding:binary  
```  
  
El final del lote debe contener un indicador de finalización como el siguiente:  
  
```  
--batch_WKQS9Yui9r--  
```   
  
<a name="bkmk_ChangeSets"></a>

## <a name="change-sets"></a>Conjuntos de cambios

Cuando un conjunto de cambios contiene varias operaciones, todas ellas se consideran atómicas, lo que significa que si alguna de las operaciones produce error, se revertirán las operaciones completadas. Como una solicitud de lote, los conjuntos de cambios deben tener un encabezado de tipo contenido con un valor establecido como multiparte/mixto con un conjunto de límites para incluir el identificador del conjunto de cambios utilizando este patrón:  
  
```  
--changeset_<unique identifier>  
```  
  
El identificador único no necesita ser un GUID, pero debe ser único. Cada elemento dentro del conjunto de cambios debe ir precedido del identificador del conjunto de cambios con un encabezado Content-Type y Content-Transfer-Encoding como el siguiente:  
  
```  
--changeset_BBB456  
Content-Type: application/http  
Content-Transfer-Encoding:binary  
```  
  
Los conjuntos de cambios también pueden incluir un encabezado Content-ID con un valor único. Este valor, cuando va precedido de `$`, representa una variable que contiene la Uri para cualquier entidad creada en esa operación. Por ejemplo, cuando establece el valor de 1, puede hacer referencia a esa entidad usando `$1` más adelante en el conjunto de cambios.  
  
El final del conjunto de cambios debe contener un indicador de finalización como el siguiente:  
  
```  
--changeset_BBB456--  
```  
  
<a name="bkmk_Example"></a>

## <a name="example"></a>Ejemplo

El siguiente ejemplo incluye un lote con un identificador único de AAA123 y un conjunto de cambios establecido con un identificador único de BBB456.  
  
Dentro del conjunto de cambios, se crean dos tareas usando POST y se asocian con una cuenta existente con accountid = 00000000-0000-0000-000000000001.  
  
Finalmente, se incluye una solicitud GET fuera del conjunto de cambios para devolver las seis tareas asociadas con la cuenta, incluidas las dos que se crearon en la solicitud por lotes.  
  
 **Solicitud**

```http 
POST[Organization URI]/api/data/v9.0/$batch HTTP/1.1  
Content-Type: multipart/mixed;boundary=batch_AAA123  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
--batch_AAA123  
Content-Type: multipart/mixed;boundary=changeset_BBB456  
  
--changeset_BBB456  
Content-Type: application/http  
Content-Transfer-Encoding:binary  
Content-ID: 1  
  
POST[Organization URI]/api/data/v9.0/tasks HTTP/1.1  
Content-Type: application/json;type=entry  
  
{"subject":"Task 1 in batch","regardingobjectid_account_task@odata.bind":"[Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-000000000001)"}  
--changeset_BBB456  
Content-Type: application/http  
Content-Transfer-Encoding:binary  
Content-ID: 2  
  
POST[Organization URI]/api/data/v9.0/tasks HTTP/1.1  
Content-Type: application/json;type=entry  
  
{"subject":"Task 2 in batch","regardingobjectid_account_task@odata.bind":"[Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-000000000001)"}  
--changeset_BBB456--  
  
--batch_AAA123  
Content-Type: application/http  
Content-Transfer-Encoding:binary  
  
GET[Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-000000000001)/Account_Tasks?$select=subject HTTP/1.1  
Accept: application/json  
  
--batch_AAA123--  
```  
  
 **Respuesta**

```http 
--batchresponse_c1bd45c1-dd81-470d-b897-e965846aad2f  
Content-Type: multipart/mixed; boundary=changesetresponse_ff83b4f1-ab48-430c-b81c-926a2c596abc  
  
--changesetresponse_ff83b4f1-ab48-430c-b81c-926a2c596abc  
Content-Type: application/http  
Content-Transfer-Encoding: binary  
Content-ID: 1  
  
HTTP/1.1 204 No Content  
OData-Version: 4.0  
Location:[Organization URI]/api/data/v9.0/tasks(a59c24f3-fafc-e411-80dd-00155d2a68cb)  
OData-EntityId:[Organization URI]/api/data/v9.0/tasks(a59c24f3-fafc-e411-80dd-00155d2a68cb)  
  
--changesetresponse_ff83b4f1-ab48-430c-b81c-926a2c596abc  
Content-Type: application/http  
Content-Transfer-Encoding: binary  
Content-ID: 2  
  
HTTP/1.1 204 No Content  
OData-Version: 4.0  
Location:[Organization URI]/api/data/v9.0/tasks(a69c24f3-fafc-e411-80dd-00155d2a68cb)  
OData-EntityId:[Organization URI]/api/data/v9.0/tasks(a69c24f3-fafc-e411-80dd-00155d2a68cb)  
  
--changesetresponse_ff83b4f1-ab48-430c-b81c-926a2c596abc--  
--batchresponse_c1bd45c1-dd81-470d-b897-e965846aad2f  
Content-Type: application/http  
Content-Transfer-Encoding: binary  
  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
  "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#tasks(subject)","value":[  
    {  
      "@odata.etag":"W/\"474122\"","subject":"Task Created with Test Account","activityid":"919c24f3-fafc-e411-80dd-00155d2a68cb"  
    },{  
      "@odata.etag":"W/\"474125\"","subject":"Task 1","activityid":"a29c24f3-fafc-e411-80dd-00155d2a68cb"  
    },{  
      "@odata.etag":"W/\"474128\"","subject":"Task 2","activityid":"a39c24f3-fafc-e411-80dd-00155d2a68cb"  
    },{  
      "@odata.etag":"W/\"474131\"","subject":"Task 3","activityid":"a49c24f3-fafc-e411-80dd-00155d2a68cb"  
    },{  
      "@odata.etag":"W/\"474134\"","subject":"Task 1 in batch","activityid":"a59c24f3-fafc-e411-80dd-00155d2a68cb"  
    },{  
      "@odata.etag":"W/\"474137\"","subject":"Task 2 in batch","activityid":"a69c24f3-fafc-e411-80dd-00155d2a68cb"  
    }  
  ]  
}  
--batchresponse_c1bd45c1-dd81-470d-b897-e965846aad2f--  
```  
Incluya el encabezado preferencia `odata.include-annotations` con las solicitudes `GET` y establezca su valor en "*" para especificar que todas las anotaciones relacionadas con las propiedades deben devolverse.

```HTTP
--batch_AAA123  
Content-Type: application/http  
Content-Transfer-Encoding:binary  
  
GET[Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-000000000001)?$select=name,telephone1,emailaddress1,shippingmethodcode,customersizecode,accountratingcode,followemail,donotemail,donotphone,statuscode HTTP/1.1  
Accept: application/json  
Prefer: odata.include-annotations="*"
  
--batch_AAA123-- 
```
Para obtener más información sobre los encabezados de preferencia, consulte [Preferencia de encabezado](http://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part1-protocol/odata-v4.0-errata03-os-part1-protocol-complete.html#_Toc453752234).

### <a name="see-also"></a>Vea también

[Realizar operaciones mediante la API web](perform-operations-web-api.md)<br />
[Componer solicitudes HTTP y administrar errores](compose-http-requests-handle-errors.md)<br />
[Consultar datos utilizando la API web](query-data-web-api.md)<br />
[Cree una entidad usando API web](create-entity-web-api.md)<br />
[Recuperar una entidad usando API web](retrieve-entity-using-web-api.md)<br />
[Actualizar y eliminar entidades mediante la API web](update-delete-entities-using-web-api.md)<br />
[Asociar y anular la asociación de entidades mediante la API web](associate-disassociate-entities-using-web-api.md)<br />
[Usar funciones de la API web](use-web-api-functions.md)<br />
[Usar acciones de la API web](use-web-api-actions.md)<br />
[Suplantar a otro usuario utilizando la API web](impersonate-another-user-web-api.md)<br />
[Realizar operaciones condicionales mediante la API web](perform-conditional-operations-using-web-api.md)
