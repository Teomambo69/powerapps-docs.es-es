---
title: Ejecutar operaciones por lotes mediante la API web (Common Data Service)| Microsoft Docs
description: Las operaciones por lotes le permiten agrupar varias operaciones en una sola solicitud HTTP. Lea cómo ejecutar las operaciones por lotes con la API web
ms.custom: ''
ms.date: 07/13/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 799b2346-bda1-4a26-a330-79d0927a7743
caps.latest.revision: 11
author: JimDaly
ms.author: jdaly
ms.reviewer: susikka
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4029b07d07505d15f216279edbfc774026463a4f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753700"
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
POST[Organization URI]/api/data/v9.1/$batch HTTP/1.1  
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
  
POST[Organization URI]/api/data/v9.1/tasks HTTP/1.1  
Content-Type: application/json;type=entry  
  
{"subject":"Task 1 in batch","regardingobjectid_account_task@odata.bind":"[Organization URI]/api/data/v9.1/accounts(00000000-0000-0000-000000000001)"}  
--changeset_BBB456  
Content-Type: application/http  
Content-Transfer-Encoding:binary  
Content-ID: 2  
  
POST[Organization URI]/api/data/v9.1/tasks HTTP/1.1  
Content-Type: application/json;type=entry  
  
{"subject":"Task 2 in batch","regardingobjectid_account_task@odata.bind":"[Organization URI]/api/data/v9.1/accounts(00000000-0000-0000-000000000001)"}  
--changeset_BBB456--  
  
--batch_AAA123  
Content-Type: application/http  
Content-Transfer-Encoding:binary  
  
GET[Organization URI]/api/data/v9.1/accounts(00000000-0000-0000-000000000001)/Account_Tasks?$select=subject HTTP/1.1  
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
Location:[Organization URI]/api/data/v9.1/tasks(a59c24f3-fafc-e411-80dd-00155d2a68cb)  
OData-EntityId:[Organization URI]/api/data/v9.1/tasks(a59c24f3-fafc-e411-80dd-00155d2a68cb)  
  
--changesetresponse_ff83b4f1-ab48-430c-b81c-926a2c596abc  
Content-Type: application/http  
Content-Transfer-Encoding: binary  
Content-ID: 2  
  
HTTP/1.1 204 No Content  
OData-Version: 4.0  
Location:[Organization URI]/api/data/v9.1/tasks(a69c24f3-fafc-e411-80dd-00155d2a68cb)  
OData-EntityId:[Organization URI]/api/data/v9.1/tasks(a69c24f3-fafc-e411-80dd-00155d2a68cb)  
  
--changesetresponse_ff83b4f1-ab48-430c-b81c-926a2c596abc--  
--batchresponse_c1bd45c1-dd81-470d-b897-e965846aad2f  
Content-Type: application/http  
Content-Transfer-Encoding: binary  
  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
  "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#tasks(subject)","value":[  
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
  
GET[Organization URI]/api/data/v9.1/accounts(00000000-0000-0000-000000000001)?$select=name,telephone1,emailaddress1,shippingmethodcode,customersizecode,accountratingcode,followemail,donotemail,donotphone,statuscode HTTP/1.1  
Accept: application/json  
Prefer: odata.include-annotations="*"
  
--batch_AAA123-- 
```
Para obtener más información sobre los encabezados de preferencia, consulte [Preferencia de encabezado](https://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part1-protocol/odata-v4.0-errata03-os-part1-protocol-complete.html#_Toc453752234).

## <a name="reference-uris-in-an-operation"></a>Hacer referencia a URI en una operación

Puede usar `$parameter`, como `$1``$2`, etc. para hacer referencia a URI usados en un conjunto de cambios anterior en una solicitud por lotes. Esta sección muestra diferentes ejemplos sobre cómo `$parameter` se puede usar en el cuerpo de la solicitud de una operación por lotes para hacer referencia a URI.

### <a name="reference-uris-in-request-body"></a>Hacer referencia a URI en el cuerpo de la solicitud

El siguiente ejemplo muestra cómo dos referencias de URI se pueden usar en una sola operación.

**Solicitud**

```http
POST [Organization URI]/api/data/v9.1/$batch HTTP/1.1
Content-Type:  multipart/mixed;boundary=batch_AAA123
Accept:  application/json
OData-MaxVersion:  4.0
OData-Version:  4.0

--batch_AAA123
Content-Type: multipart/mixed; boundary=changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 1

POST [Organization URI]/api/data/v9.1/leads HTTP/1.1
Content-Type: application/json

{
    "firstname":"aaa",
    "lastname":"bbb"
}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 2

POST [Organization URI]/api/data/v9.1/contacts HTTP/1.1
Content-Type: application/json

{"@odata.type":"Microsoft.Dynamics.CRM.contact","firstname":"Oncall Contact-1111"}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 3

POST [Organization URI]/api/data/v9.1/accounts HTTP/1.1
Content-Type: application/json

{
    "name":"IcM Account",
    "originatingleadid@odata.bind":"$1",
    "primarycontactid@odata.bind":"$2"
}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab--
--batch_AAA123--
```

**Respuesta**

```http
200 OK

--batchresponse_3cace264-86ea-40fe-83d3-954b336c0f4a
Content-Type: multipart/mixed; boundary=changesetresponse_1a5db8a1-ec98-42c4-81f6-6bc6adcfa4bc

--changesetresponse_1a5db8a1-ec98-42c4-81f6-6bc6adcfa4bc
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 1

HTTP/1.1 204 No Content
OData-Version: 4.0
Location: [Organization URI]/api/data/v9.1/leads(425195a4-7a75-e911-a97a-000d3a34a1bd)
OData-EntityId: [Organization URI]/api/data/v9.1/leads(425195a4-7a75-e911-a97a-000d3a34a1bd)

--changesetresponse_1a5db8a1-ec98-42c4-81f6-6bc6adcfa4bc
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 2

HTTP/1.1 204 No Content
OData-Version: 4.0
Location: [Organization URI]/api/data/v9.1/contacts(495195a4-7a75-e911-a97a-000d3a34a1bd)
OData-EntityId: [Organization URI]/api/data/v9.1/contacts(495195a4-7a75-e911-a97a-000d3a34a1bd)

--changesetresponse_1a5db8a1-ec98-42c4-81f6-6bc6adcfa4bc
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 3

HTTP/1.1 204 No Content
OData-Version: 4.0
Location: [Organization URI]/api/data/v9.1/accounts(4f5195a4-7a75-e911-a97a-000d3a34a1bd)
OData-EntityId: [Organization URI]/api/data/v9.1/accounts(4f5195a4-7a75-e911-a97a-000d3a34a1bd)

--changesetresponse_1a5db8a1-ec98-42c4-81f6-6bc6adcfa4bc--
--batchresponse_3cace264-86ea-40fe-83d3-954b336c0f4a--
```

### <a name="reference-uri-in-request-url"></a>Hacer referencia a URI en dirección URL de la solicitud

El ejemplo ofrecido a continuación muestra cómo puede hacer referencia a un URI usando `$1` en la dirección URL de una solicitud posterior.

**Solicitud**

```http
POST [Organization URI]/api/data/v9.1/$batch HTTP/1.1
Content-Type:  multipart/mixed;boundary=batch_AAA123
Accept:  application/json
OData-MaxVersion:  4.0
OData-Version:  4.0

--batch_AAA123
Content-Type: multipart/mixed; boundary=changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 1

POST [Organization URI]/api/data/v9.1/contacts HTTP/1.1
Content-Type: application/json

{
  "@odata.type":"Microsoft.Dynamics.CRM.contact",
  "firstname":"Contact",
  "lastname":"AAAAAA"
}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Transfer-Encoding: binary
Content-Type: application/http
Content-ID: 2

PUT $1/lastname HTTP/1.1
Content-Type: application/json

{
  "value":"BBBBB"
}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab--
--batch_AAA123--
```

**Respuesta**

```http
200 OK

--batchresponse_2cb48f48-39a8-41ea-aa52-132fa8ab3c2d
Content-Type: multipart/mixed; boundary=changesetresponse_d7528170-3ef3-41bd-be8e-eac971a8d9d4

--changesetresponse_d7528170-3ef3-41bd-be8e-eac971a8d9d4
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 1

HTTP/1.1 204 No Content
OData-Version: 4.0
Location:[Organization URI]/api/data/v9.1/contacts(f8ea5d2c-8c75-e911-a97a-000d3a34a1bd)
OData-EntityId:[Organization URI]/api/data/v9.1/contacts(f8ea5d2c-8c75-e911-a97a-000d3a34a1bd)


--changesetresponse_d7528170-3ef3-41bd-be8e-eac971a8d9d4
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 2

HTTP/1.1 204 No Content
OData-Version: 4.0


--changesetresponse_d7528170-3ef3-41bd-be8e-eac971a8d9d4--
--batchresponse_2cb48f48-39a8-41ea-aa52-132fa8ab3c2d--
```

### <a name="reference-uris-in-url-and-request-body-using-odataid"></a>Hacer referencia a URI en la dirección URL y el cuerpo de la solicitud usando @odata.id

El ejemplo ofrecido a continuación muestra cómo vincular un registro de entidad Contacto a un registro de entidad Cuenta. Al URI del registro de entidad Cuenta se hace referencia como `$1` y al URI del registro de entidad Contacto se hace referencia como `$2`.

**Solicitud**

```http
POST [Organization URI]/api/data/v9.1/$batch HTTP/1.1
Content-Type:multipart/mixed;boundary=batch_AAA123
Accept:application/json
OData-MaxVersion:4.0
OData-Version:4.0

--batch_AAA123
Content-Type: multipart/mixed; boundary=changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type:application/http
Content-Transfer-Encoding:binary
Content-ID:1

POST [Organization URI]/api/data/v9.1/accounts HTTP/1.1
Content-Type: application/json

{"@odata.type":"Microsoft.Dynamics.CRM.account","name":"IcM Account"}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type:application/http
Content-Transfer-Encoding:binary
Content-ID:2

POST [Organization URI]/api/data/v9.1/contacts HTTP/1.1
Content-Type:application/json

{"@odata.type":"Microsoft.Dynamics.CRM.contact","firstname":"Oncall Contact"}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type:application/http
Content-Transfer-Encoding:binary
Content-ID:3

PUT $1/primarycontactid/$ref HTTP/1.1
Content-Type:application/json

{"@odata.id":"$2"}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab--
--batch_AAA123--
```

**Respuesta**

```http
200 OK

--batchresponse_0740a25c-d8e1-41a5-9202-1b50a297864c
Content-Type: multipart/mixed; boundary=changesetresponse_19ca0da8-d8bb-4273-a3f7-fe0d0fadfe5f

--changesetresponse_19ca0da8-d8bb-4273-a3f7-fe0d0fadfe5f
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 1

HTTP/1.1 204 No Content
OData-Version: 4.0
Location:[Organization URI]/api/data/v9.1/accounts(3dcf8c02-8c75-e911-a97a-000d3a34a1bd)
OData-EntityId:[Organization URI]/api/data/v9.1/accounts(3dcf8c02-8c75-e911-a97a-000d3a34a1bd)

--changesetresponse_19ca0da8-d8bb-4273-a3f7-fe0d0fadfe5f
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 2

HTTP/1.1 204 No Content
OData-Version: 4.0
Location:[Organization URI]/api/data/v9.1/contacts(43cf8c02-8c75-e911-a97a-000d3a34a1bd)
OData-EntityId:[Organization URI]/api/data/v9.1/contacts(43cf8c02-8c75-e911-a97a-000d3a34a1bd)

--changesetresponse_19ca0da8-d8bb-4273-a3f7-fe0d0fadfe5f
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 3

HTTP/1.1 204 No Content
OData-Version: 4.0

--changesetresponse_19ca0da8-d8bb-4273-a3f7-fe0d0fadfe5f--
--batchresponse_0740a25c-d8e1-41a5-9202-1b50a297864c--
```

### <a name="reference-uris-in-url-and-navigation-properties"></a>Hacer referencia a URI en propiedades de dirección URL y navegación

El ejemplo ofrecido a continuación muestra cómo usar el URI de la organización de un registro de contacto y vincularlo a un registro de cuenta utilizando la propiedad de navegación de un solo valor `primarycontactid`. Al URI del registro de entidad Cuenta se hace referencia como `$1` y al URI del registro de entidad Contacto se hace referencia como `$2` en la solicitud `PATCH`.

**Solicitud**

```http
POST [Organization URI]/api/data/v9.1/$batch HTTP/1.1
Content-Type:multipart/mixed;boundary=batch_AAA123
Accept:application/json
OData-MaxVersion:4.0
OData-Version:4.0

--batch_AAA123
Content-Type: multipart/mixed; boundary=changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 1

POST [Organization URI]/api/data/v9.1/accounts HTTP/1.1
Content-Type: application/json

{"@odata.type":"Microsoft.Dynamics.CRM.account","name":"IcM Account"}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 2

POST [Organization URI]/api/data/v9.1/contacts HTTP/1.1
Content-Type: application/json

{
  "@odata.type":"Microsoft.Dynamics.CRM.contact",
  "firstname":"Oncall Contact"
}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 3

PATCH $1 HTTP/1.1
Content-Type: application/json

{
  "primarycontactid@odata.bind":"$2"
}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab--
--batch_AAA123--
```
**Respuesta**

```http
200 OK

--batchresponse_9595d3ae-48f6-414f-a3aa-a3a33559859e
Content-Type: multipart/mixed; boundary=changesetresponse_0c1567a5-ad0d-48fa-b81d-e6db05cad01c

--changesetresponse_0c1567a5-ad0d-48fa-b81d-e6db05cad01c
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 1

HTTP/1.1 204 No Content
OData-Version: 4.0
Location: [Organization URI]/api/data/v9.1/accounts(6cd81853-7b75-e911-a97a-000d3a34a1bd)
OData-EntityId: [Organization URI]/api/data/v9.1/accounts(6cd81853-7b75-e911-a97a-000d3a34a1bd)

--changesetresponse_0c1567a5-ad0d-48fa-b81d-e6db05cad01c
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 2

HTTP/1.1 204 No Content
OData-Version: 4.0
Location: [Organization URI]/api/data/v9.1/contacts(6ed81853-7b75-e911-a97a-000d3a34a1bd)
OData-EntityId: [Organization URI]/api/data/v9.1/contacts(6ed81853-7b75-e911-a97a-000d3a34a1bd)

--changesetresponse_0c1567a5-ad0d-48fa-b81d-e6db05cad01c
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 3

HTTP/1.1 204 No Content
OData-Version: 4.0
Location: [Organization URI]/api/data/v9.1/accounts(6cd81853-7b75-e911-a97a-000d3a34a1bd)
OData-EntityId: [Organization URI]/api/data/v9.1/accounts(6cd81853-7b75-e911-a97a-000d3a34a1bd)

--changesetresponse_0c1567a5-ad0d-48fa-b81d-e6db05cad01c--
--batchresponse_9595d3ae-48f6-414f-a3aa-a3a33559859e--
```

> [!NOTE]
> Al hacer referencia a un identificador de contenido antes de que se haya declarado en el cuerpo de la solicitud se devolverá la solicitud errónea **HTTP 400** del error.
>
> El ejemplo ofrecido debajo muestra un cuerpo de la solicitud que puede producir este error.
> 
> **Cuerpo de la solicitud**
> 
> ```http
> --batch_AAA123
> Content-Type: multipart/mixed; boundary=changeset_BBB456
> 
> --changeset_BBB456
> Content-Type: application/http
> Content-Transfer-Encoding:binary
> Content-ID: 2
> 
> POST [Organization URI]/api/data/v9.1/phonecalls HTTP/1.1
> Content-Type: application/json;type=entry
> 
> {
>     "phonenumber":"911",
>     "regardingobjectid_account_phonecall@odata.bind" : "$1"
> }
> 
> --changeset_BBB456
> Content-Type: application/http
> Content-Transfer-Encoding:binary
> Content-ID: 1
> 
> POST [Organization URI]/api/data/v9.1/accounts HTTP/1.1
> Content-Type: application/json;type=entry
> 
> {
>     "name":"QQQQ",
>     "revenue": 1.50
> }
> 
> --changeset_BBB456--
> --batch_AAA123--
> ```
>
> **Respuesta**
> 
> ```http
> HTTP 400 Bad Request
> Content-ID Reference: '$1' does not exist in the batch context.
> ```

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
