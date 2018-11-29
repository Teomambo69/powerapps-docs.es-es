---
title: Actualizar y eliminar entidades utilizando la API web (Common Data Service para aplicaciones)| Microsoft Docs
description: Lea cómo realizar operaciones de actualización y eliminación de entidades utilizando la API web
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 694889fd-2b85-43a0-97bc-1e760695db31
caps.latest.revision: 17
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="update-and-delete-entities-using-the-web-api"></a>Actualizar y eliminar entidades mediante la API web

Las operaciones para modificar datos son una parte básica de la API web. Además de una simple actualización y eliminación, puede realizar operaciones en atributos individuales y crear solicitudes *upsert* que actualizarán o insertarán una entidad en función de si existe.  
  
> [!NOTE]
>  Los metadatos que definen las entidades se actualizan de otra manera. Más información:[Crear y actualizar entidades de modelo mediante la API web](create-update-entity-definitions-using-web-api.md)  
  
<a name="bkmk_update"></a>

## <a name="basic-update"></a>Actualización básica

Las operaciones de actualización usan el verbo HTTP `PATCH`. Pase un objeto JSON que contenga las propiedades que desee actualizar a la URL que representa la entidad. Se devolverá una respuesta con un estado de 204 si la actualización es correcta.  
  
 Este ejemplo actualiza un registro de cuenta existente con el valor `accountid` de 00000000-0000-0000-0000-000000000001.  
  
> [!IMPORTANT]
>  Al actualizar una entidad, incluya únicamente las propiedades que está modificando en el cuerpo de la solicitud. Actualizando simplemente las propiedades de una entidad que recuperó anteriormente, e incluyendo ese JSON en su solicitud, se actualizará cada propiedad aunque el valor sea el mismo. Esto puede provocar eventos del sistema que pueden desencadenar la lógica de negocios que espera que los valores hayan cambiado. Esto puede hacer que parezca que las propiedades se han actualizado en auditoría de datos cuando de hecho no han cambiado realmente.

> [!NOTE] 
> Los metadatos de los atributos incluyen una propiedad `RequiredLevel`. Cuando esta opción se establece en `SystemRequired`, no puede establecer estos atributos a un valor nulo. Más información: [Nivel de requisito de atributo](../entity-attribute-metadata.md#attribute-requirement-level)
  
 **Solicitud**

```http
PATCH [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001) HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
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

```http
HTTP/1.1 204 No Content  
OData-Version: 4.0  
  
```  
  
> [!NOTE]
>  Consulte [Asociar entidades en la actualización](associate-disassociate-entities-using-web-api.md#bkmk_Associateentitiesonupdate) para obtener información acerca de la asociación entidades de actualización.  
  
<a name="bkmk_updateWithDataReturned"></a>

## <a name="update-with-data-returned"></a>Actualizar con datos devueltos
  
Para recuperar datos de una entidad que está actualizando puede crear la solicitud `PATCH` de forma que los datos del registro creado sean devueltos con un estado de 200 (OK).  Para obtener su resultado, debe usar la preferencia `return=representation` en los encabezados de solicitud.  
  
 Para controlar qué propiedades se devuelven, anexe la opción de consulta `$select` a la dirección URL del conjunto de entidades.  Se ignorará la opción de consulta `$expand` si se utiliza.  
  
 Este ejemplo actualiza una entidad de cuenta y devuelve los datos solicitados en la respuesta.  
  
 **Solicitud**

```http
PATCH [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)?$select=name,creditonhold,address1_latitude,description,revenue,accountcategorycode,createdon HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
Prefer: return=representation  
  
{"name":"Updated Sample Account"}  
```  
  
 **Respuesta** 
 
```http
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
Preference-Applied: return=representation  
OData-Version: 4.0  
  
{  
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts/$entity",  
    "@odata.etag": "W/\"536537\"",  
    "accountid": "00000000-0000-0000-0000-000000000001",  
    "accountcategorycode": 1,  
    "description": "This is the description of the sample account",  
    "address1_latitude": 47.63958,  
    "creditonhold": false,  
    "name": "Updated Sample Account",  
    "createdon": "2016-09-28T23:14:00Z",  
    "revenue": 5000000.0000,  
    "_transactioncurrencyid_value": "048dddaa-6f7f-e611-80d3-00155db5e0b6"  
}  
  
```  
  
<a name="bkmk_updateSingleProperty"></a> 
  
## <a name="update-a-single-property-value"></a>Actualizar un solo valor de propiedad  

Cuando desee actualizar únicamente un solo valor de propiedad, utilice una solicitud PUT con el nombre de propiedad anexado a la Uri de la entidad.  
  
 El siguiente ejemplo actualiza la propiedad de nombre de una entidad de cuenta existente con el valor `accountid` de 00000000-0000-0000-0000-000000000001.  
  
 **Solicitud**  

```http
PUT [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)/name HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{"value": "Updated Sample Account Name"}  
```  
  
 **Respuesta**

```http
HTTP/1.1 204 No Content  
OData-Version: 4.0  
  
```  
  
<a name="bkmk_deleteSingleProperty"></a>

## <a name="delete-a-single-property-value"></a>Eliminar un solo valor de propiedad

Para eliminar el valor de una sola propiedad, utilice una solicitud DELETE con el nombre de propiedad anexado a la Uri de la entidad.  
  
El siguiente ejemplo elimina el valor de la propiedad `description` de una entidad de cuenta existente con el valor `accountid` de 00000000-0000-0000-0000-000000000001.  
  
 **Solicitud**

```http
DELETE [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)/description HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Respuesta**

```http
HTTP/1.1 204 No Content  
OData-Version: 4.0  
  
```  
  
> [!NOTE]
>  Esto no se puede usar con una propiedad de navegación de un solo valor para anular la asociación de dos entidades. Para un enfoque alternativo, consulte [Quitar una referencia a una entidad](associate-disassociate-entities-using-web-api.md#bkmk_Removeareferencetoanentity).  
  
<a name="bkmk_upsert"></a>

## <a name="upsert-an-entity"></a>Aplicar Upsert a una entidad

Una operación *upsert* es exactamente igual que una actualización. Usa una solicitud `PATCH` y usa una URI para hacer referencia a una entidad específica. La diferencia es que si la entidad no existe, se creará. Si ya existe, será actualizada. Normalmente al crear una nueva entidad usted deja que el sistema asigne un identificador único. Esta es una práctica recomendada. Pero si necesita crear un registro con un valor `id` específico, una operación `upsert` proporciona una forma de hacerlo. Esto puede ser útil en una situación en la que esté sincronizando datos en sistemas distintos.  
  
A veces, hay situaciones donde desea realizar `upsert`, pero desea evitar una de las acciones potenciales predeterminadas: crear o actualizar.      Puede lograrlo mediante la adición encabezados `If-Match` o `If-None-Match`. Para obtener más información, consulte [Limitar operaciones de upsert](perform-conditional-operations-using-web-api.md#bkmk_limitUpsertOperations).  
  
<a name="bkmk_delete"></a>
  
## <a name="basic-delete"></a>Eliminación básica

Una operación de eliminación es muy sencilla. Utilice el verbo DELETE con el URI de la entidad que desea borrar. Este mensaje de ejemplo elimina una entidad de cuenta con el valor de clave principal `accountid` igual a 00000000-0000-0000-0000-000000000001.  
  
 **Solicitud**

```http
DELETE [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001) HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Respuesta**

 Si ya existe la entidad, recibirá una respuesta normal con estado 204 para indicar que la eliminación fue correcta. Si no se encuentra la entidad, recibirá una respuesta con estado 404.  
  
```http
HTTP/1.1 204 No Content  
OData-Version: 4.0  
```  

<a name="bkmk_duplicate"></a>

## <a name="check-for-duplicate-records"></a>Verificar registros duplicados

<!-- TODO:
By default, duplicate detection is suppressed when you are updating records using the Web API. You must include the `MSCRM.SuppressDuplicateDetection: false` header with your PATCH request to enable duplicate detection . Duplicate detection only applies when the organization has enabled duplicate detection, the entity is enabled for duplicate detection, and there are active duplicate detection rules being applied. For more information, see [Detect duplicate data for developers](../detect-duplicate-data-for-developers.md). -->

Consulte [Detectar duplicados durante la operación de actualizaicón mediante la API web](manage-duplicate-detection-create-update.md#bkmk_update) para obtener más información sobre cómo buscar registros duplicados durante la operación de actualización.

### <a name="see-also"></a>Vea también

[Ejemplo de operaciones básicas de la API web (C#)](samples/basic-operations-csharp.md)<br />
[Ejemplo de operaciones básicas de la API web (JavaScript del lado del cliente)](samples/basic-operations-client-side-javascript.md)<br />
[Realizar operaciones mediante la API web](perform-operations-web-api.md)<br />
[Componer solicitudes HTTP y administrar errores](compose-http-requests-handle-errors.md)<br />
[Consultar datos utilizando la API web](query-data-web-api.md)<br />
[Cree una entidad usando API web](create-entity-web-api.md)<br />
[Recuperar una entidad usando API web](retrieve-entity-using-web-api.md)<br />
[Asociar y anular la asociación de entidades mediante la API web](associate-disassociate-entities-using-web-api.md)<br />
[Usar funciones de la API web](use-web-api-functions.md)<br />
[Usar acciones de la API web](use-web-api-actions.md)<br />
[Ejecute las operaciones por lotes mediante API web](execute-batch-operations-using-web-api.md)<br />
[Suplantar a otro usuario utilizando la API web](impersonate-another-user-web-api.md)<br />
[Realizar operaciones condicionales mediante la API web](perform-conditional-operations-using-web-api.md)
