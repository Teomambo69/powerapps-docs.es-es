---
title: Realizar operaciones condicionales utilizando la API web (Common Data Service para aplicaciones)| Microsoft Docs
description: Aprenda a crear condiciones que decidan si y cómo realizar ciertas operaciones mediante la API web
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 771002b0-825a-462d-bbf0-1aeba4b726c8
caps.latest.revision: 16
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="perform-conditional-operations-using-the-web-api"></a>Realizar operaciones condicionales mediante la API web

CDS para aplicaciones ofrece compatibilidad con un conjunto de operaciones condicionales que dependen del mecanismo de control de versiones de recursos HTTP estándar conocido como *ETags*.  
  
<a name="bkmk_ETags"></a>
  
## <a name="etags"></a>ETags

El protocolo HTTP define una *etiqueta de entidad* o [ETag](https://msdn.microsoft.com/en-us/library/dd541486.aspx) en el término abreviado, para identificar versiones específicas de un recurso. Las ETags son identificadores opacos cuyos valores exactos dependen de la implementación. Los valores de ETag se producen en dos variedades: validación segura y débil. La validación segura indica que un recurso único, identificado mediante un URI específico, será idéntico en el nivel binario si su valor de ETag correspondiente no se modifica. La validación débil solo garantiza que la representación del recurso equivale semánticamente al mismo valor de ETag.  
  
Common Data Service para aplicaciones genera una propiedad `@odata.etag` de validación débil para todas las instancias de entidad y esta propiedad se devuelve automáticamente con cada registro de entidad recuperado. Para obtener más información, consulte [Recuperar una entidad usando la API web](retrieve-entity-using-web-api.md).  
  
<a name="bkmk_ifMatchHeaders"></a>
 
## <a name="if-match-and-if-none-match-headers"></a>Encabezados If-Match e If-None-Match

Use los encabezados [If-Match](https://tools.ietf.org/html/rfc7232#section-3.1) e [If-None-Match](https://tools.ietf.org/html/rfc7232#section-3.2) con valores ETag para comprobar si la versión actual de un recurso coincide con la recuperada por última vez, coincide con cualquier versión anterior o no coincide con ninguna versión.  Estas comparaciones conforman la base de la compatibilidad de operaciones condicional. Common Data Service para aplicaciones proporciona ETags para admitir las recuperaciones condicionales, la simultaneidad optimista y las operaciones upsert limitadas.
 
Las consultas que expanden propiedades de navegación valorada como colección pueden devolver datos en caché para las propiedades que no reflejan cambios recientes. Se recomienda usar el encabezado `If-None-Match` con valor `null` para reemplazar el almacenamiento en la memoria caché del explorador. Consulte [Encabezados HTTP](compose-http-requests-handle-errors.md#bkmk_headers) para obtener más información. Utilice el encabezado `If-None-Match` con un valor ETag específico para asegurarse de que solo se devuelven los datos modificados.
  
> [!WARNING]
> El código de cliente no debe proporcionar ningún significado al valor específico de una ETag, ni a ninguna relación aparente entre las ETags más allá de la igualdad o la desigualdad. Por ejemplo, no se garantiza que un valor de ETag para una versión más reciente de un recurso sea mayor que el valor de ETag para una versión anterior. Además, el algoritmo usado para generar nuevos valores de ETag puede cambiar desigualdad entre las versiones de un servicio.  
  
<a name="bkmk_DetectIfChanged"></a>

## <a name="conditional-retrievals"></a>Recuperaciones condicionales

Las Etags le permiten optimizar recuperaciones de registros siempre que tenga acceso al mismo registro varias veces. Si ha recuperado previamente un registro, puede pasar el valor de ETag con el encabezado `If-None-Match` para solicitar que se recuperen datos solo si han cambiado desde la última vez que se recuperaron. Si los datos han cambiado, la solicitud devuelve un estado HTTP de 200 (correcto) con los datos más recientes en el cuerpo de la solicitud. Si los datos no han cambiado, se devuelve el código de estado HTTP 304 (sin modificar) para indicar que la entidad no se ha modificado. El siguiente par de mensajes de ejemplo devuelve datos de una entidad de cuenta con el `accountid` igual a `00000000-0000-0000-0000-000000000001` cuando los datos no se han modificado desde que se recuperaron por última vez.  

> [!NOTE]
> Obtención condicional funciona solo para las entidades que tienen simultaneidad optimista habilitada. Compruebe si una entidad tiene simultaneidad optimista habilitada mediante la solicitud de API Web que se muestra a continuación. Las entidades que tienen simultaneidad optimista habilitada, tendrán la propiedad <xref href="Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsOptimisticConcurrencyEnabled?text=EntityMetadata.IsOptimisticConcurrencyEnabled" /> para establecer `true`.

> ```HTTP
> GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='<Entity Logical Name>')?$select=IsOptimisticConcurrencyEnabled
> ```
<!-- TODO:
> For more information about optimistic concurrency, see [Reduce potential data loss using optimistic concurrency](../org-service/reduce-potential-data-loss-using-optimistic-concurrency.md).   -->

 **Solicitud**  
```http  
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)?$select=accountcategorycode,accountnumber,creditonhold,createdon,numberofemployees,name,revenue   HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
If-None-Match: W/"468026"  
```  
  
 **Respuesta**  
```json  
HTTP/1.1 304 Not Modified  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
```  
  
<a name="bkmk_limitUpsertOperations"></a>
  
## <a name="limit-upsert-operations"></a>Limitar operaciones de upsert

Una operación upsert funciona normalmente creando una entidad si no existe; de lo contrario, actualiza una entidad existente. Sin embargo, las ETags se pueden usar para restringir más upserts para evitar creaciones o actualizaciones.  
  
<a name="bkmk_preventCreateOnUpsert"></a>
 
### <a name="prevent-create-in-upsert"></a>Evitar crear en upsert

Si actualiza datos y hay alguna posibilidad de que se eliminó la entidad forma intencionada, no resulta conveniente volver a crear la entidad. Para evitar este problema, agregue un encabezado `If-Match` a la solicitud con un valor de "`*`".  
  
 **Solicitud**  
```http  
PATCH [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001) HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
If-Match: "*"  
  
{  
    "name": "Updated Sample Account ",  
    "creditonhold": true,  
    "address1_latitude": 47.639583,  
    "description": "This is the updated description of the sample account",  
    "revenue": 6000000,  
    "accountcategorycode": 2  
}  
```  
  
 **Respuesta**  
 Si se encuentra la entidad, recibirá una respuesta normal con estado 204 (sin contenido). Si no se encuentra la entidad, recibirá la siguiente respuesta con estado 404 (no encontrado).  
  
```json  
HTTP/1.1 404 Not Found  
OData-Version: 4.0  
Content-Type: application/json; odata.metadata=minimal  
  
{  
 "error": {  
  "code": "",  
  "message": "account With Id = 00000000-0000-0000-0000-000000000001 Does Not Exist",  
  "innererror": {  
   "message": "account With Id = 00000000-0000-0000-0000-000000000001 Does Not Exist",  
   "type": "System.ServiceModel.FaultException`1[[Microsoft.Xrm.Sdk.OrganizationServiceFault, Microsoft.Xrm.Sdk, Version=8.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35]]",  
   "stacktrace": <stack trace removed for brevity>  
  }  
 }  
}  
```  
  
<a name="bkmk_preventUpdateInUpsert"></a>
  
### <a name="prevent-update-in-upsert"></a>Evitar actualizar en upsert

Si está insertando datos, hay posibilidad de que un registro con el mismo valor `id` ya exista en el sistema y es posible que no desee actualizarlo. Para evitarlo, agregue un encabezado `If-None-Match` a la solicitud con un valor de "`*`".  
  
 **Solicitud**  
```http  
PATCH [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001) HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
If-None-Match: "*"  
  
{  
    "name": "Updated Sample Account ",  
    "creditonhold": true,  
    "address1_latitude": 47.639583,  
    "description": "This is the updated description of the sample account",  
    "revenue": 6000000,  
    "accountcategorycode": 2  
}  
```  
  
 **Respuesta**  
 Si no se encuentra la entidad, recibirá una respuesta normal con estado 204 (sin contenido). Si sí se encuentra la entidad, recibirá la siguiente respuesta con estado 412 (error de condición previa).  
  
```json  
HTTP/1.1 412 Precondition Failed  
OData-Version: 4.0  
Content-Type: application/json; odata.metadata=minimal  
  
{  
  "error":{  
   "code":"",  
   "message":"A record with matching key values already exists.",  
   "innererror":{  
    "message":"Cannot insert duplicate key.",  
    "type":"System.ServiceModel.FaultException`1[[Microsoft.Xrm.Sdk.OrganizationServiceFault, Microsoft.Xrm.Sdk, Version=8.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35]]",  
    "stacktrace":<stack trace removed for brevity>  
    }  
  }  
}  
```  
  
<a name="bkmk_Applyoptimisticconcurrency"></a>

## <a name="apply-optimistic-concurrency"></a>Aplicar simultaneidad optimista

Puede usar simultaneidad optimista para detectar si ha modificado una entidad desde que se recuperó por última vez. Si la entidad que piensa actualizar o eliminar ha cambiado en el servidor desde que la recuperó, no le conviene completar la operación de actualización o eliminación. Aplicando el patrón mostrado aquí puede detectar esta situación, recuperar la versión más reciente de la entidad, y aplicar los criterios necesarios para reevaluar si intentar de nuevo la operación.  
  
<a name="bkmk_Applyoptimisticconcurrencyondelete"></a>

### <a name="apply-optimistic-concurrency-on-delete"></a>Aplicar simultaneidad optimista al eliminar

La siguiente solicitud de eliminación de una cuenta con `accountid` de `00000000-0000-0000-0000-000000000001` da error porque el valor de ETag enviado con el encabezado `If-Match` es diferente del valor actual. Si el valor hubiera coincidido, se esperaría un estado 204 (sin contenido).  
  
 **Solicitud**

```http  
DELETE [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001) HTTP/1.1  
If-Match: W/"470867"  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Respuesta**

```json  
HTTP/1.1 412 Precondition Failed  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
  "error":{  
    "code":"","message":"The version of the existing record doesn't match the RowVersion property provided.",  
    "innererror":{  
      "message":"The version of the existing record doesn't match the RowVersion property provided.",  
      "type":"System.ServiceModel.FaultException`1[[Microsoft.Xrm.Sdk.OrganizationServiceFault, Microsoft.Xrm.Sdk, Version=8.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35]]",  
"stacktrace":"  <stack trace details omitted for brevity>  
    }  
  }  
}  
```  
  
<a name="bkmk_Applyoptimisticconcurrencyonupdate"></a>

### <a name="apply-optimistic-concurrency-on-update"></a>Aplicar simultaneidad optimista al actualizar

La siguiente solicitud de actualización de una cuenta con `accountid` de `00000000-0000-0000-0000-000000000001` da error porque el valor de ETag enviado con el encabezado `If-Match` es diferente del valor actual. Si el valor hubiera coincidido, se esperaría un estado 204 (sin contenido).  
  
 **Solicitud**

```http  
PATCH [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001) HTTP/1.1  
If-Match: W/"470867"  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{"name":"Updated Account Name"}  
```  
  
 **Respuesta**

```json  
HTTP/1.1 412 Precondition Failed  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
  "error":{  
    "code":"","message":"The version of the existing record doesn't match the RowVersion property provided.",  
    "innererror":{  
      "message":"The version of the existing record doesn't match the RowVersion property provided.",  
      "type":"System.ServiceModel.FaultException`1[[Microsoft.Xrm.Sdk.OrganizationServiceFault, Microsoft.Xrm.Sdk, Version=8.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35]]",  
"stacktrace":"  <stack trace details omitted for brevity>  
    }  
  }  
}  
```  
  
### <a name="see-also"></a>Vea también

[Ejemplo de operaciones condicionales de la API web (C#)](samples/conditional-operations-csharp.md)<br />
[Ejemplo de operaciones condicionales de la API web (JavaScript del lado del cliente)](samples/conditional-operations-client-side-javascript.md)<br />
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
[Suplantar a otro usuario utilizando la API web](impersonate-another-user-web-api.md)
