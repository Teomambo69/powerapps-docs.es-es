---
title: Asociar y eliminar la asociación de entidades utilizando la API web (Common Data Service para aplicaciones)| Microsoft Docs
description: 'Aprenda a agregar referencia a una propiedad de navegación valorada como colección, eliminar una referencia y cambiar una referencia existente mediante la API web'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: ad4e4eac-117a-4958-9df0-b7353305b0c7
caps.latest.revision: 13
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="associate-and-disassociate-entities-using-the-web-api"></a>Asociar y anular la asociación de entidades mediante la API web

Hay varios métodos que puede usar para asociar y anular la asociación de entidades. El método que aplique depende de si está creando o actualizando las entidades y si está trabajando en el contexto de la entidad a la que se hace referencia o la entidad de referencia.  

<a name="bkmk_Addareferencetoacollection"></a>

## <a name="add-a-reference-to-a-collection-valued-navigation-property"></a>Agregue una referencia a una propiedad de navegación valorada como colección

 En el siguiente ejemplo se muestra cómo asociar una entidad de oportunidad existente con el valor de `opportunityid` de `00000000-0000-0000-0000-000000000001` a la propiedad de navegación `opportunity_customer_accounts` valorada como colección de una entidad de cuenta con el valor de `accountid` de `00000000-0000-0000-0000-000000000002`. Esta es una relación 1:N pero puede realizar la misma operación para una relación N:N.  
  
**Solicitud**  
```http  
POST [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000002)/opportunity_customer_accounts/$ref HTTP/1.1   
Content-Type: application/json   
Accept: application/json   
OData-MaxVersion: 4.0   
OData-Version: 4.0  
  
{  
"@odata.id":"[Organization URI]/api/data/v9.0/opportunities(00000000-0000-0000-0000-000000000001)"  
}  
```  
  
**Respuesta**  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
```  
  
<a name="bkmk_Removeareferencetoanentity"></a>

## <a name="remove-a-reference-to-an-entity"></a>Quite una referencia a una entidad

 Use una solicitud DELETE para quitar una referencia a una entidad. La forma en que se realiza es diferente en función de si se hace referencia a una propiedad de navegación valorada como colección o una propiedad de navegación de un solo valor.  
  
 **Solicitud**  
 Para una propiedad de navegación valorada como colección, use lo siguiente.  
  
```http  
DELETE [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000002)/opportunity_customer_accounts/$ref?$id=[Organization URI]/api/data/v9.0/opportunities(00000000-0000-0000-0000-000000000001) HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 O use esto.  
  
```http 
DELETE [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000002)/opportunity_customer_accounts(00000000-0000-0000-0000-000000000001)/$ref HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Solicitud**  
 Para una propiedad de navegación de un solo valor, quite el parámetro de cadena de consulta `$id`.  
  
```http 
DELETE [Organization URI]/api/data/v9.0/opportunities(00000000-0000-0000-0000-000000000001)/customerid_account/$ref HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Respuesta**  
 En cualquier caso, una respuesta correcta tiene el estado 204.  
  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
```  
  
<a name="bkmk_Changethereferenceinasingle"></a>
 
## <a name="change-the-reference-in-a-single-valued-navigation-property"></a>Cambie la referencia en una propiedad de navegación de un solo valor

 Puede asociar entidades estableciendo el valor de una propiedad de navegación de un solo valor utilizando la solicitud PUT con el patrón siguiente.  
  
 **Solicitud**

```http 
PUT [Organization URI]/api/data/v9.0/opportunities(00000000-0000-0000-0000-000000000001)/customerid_account/$ref HTTP/1.1  
Content-Type: application/json  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{  
 "@odata.id":"[Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000002)"  
}  
```  
  
 **Respuesta**  

```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
```  
  
<a name="bkmk_Associateentitiesoncreate"></a>

## <a name="associate-entities-on-create"></a>Asociar entidades en la creación

 Tal como se explica en [Crear entidades relacionadas en una operación](create-entity-web-api.md#bkmk_CreateRelated), se pueden crear entidades nuevas con relaciones mediante *inserción en profundidad*.  
  
<a name="bkmk_Associateentitiesonupdate"></a>

## <a name="associate-entities-on-update-using-single-valued-navigation-property"></a>Asociar entidades en la actualización mediante una propiedad de navegación de un solo valor

 Puede asociar entidades en la actualización usando el mismo mensaje descrito en [Actualización básica](update-delete-entities-using-web-api.md#bkmk_update) pero debe usar la anotación @odata.bind para establecer el valor de una propiedad de navegación de un solo valor. El siguiente ejemplo cambia la cuenta asociada a una oportunidad utilizando la propiedad de navegación de un solo valor `customerid_account`.  
  
 **Solicitud**

```http 
PATCH [Organization URI]/api/data/v9.0/opportunities(00000000-0000-0000-0000-000000000001) HTTP/1.1  
Content-Type: application/json  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{  
 "customerid_account@odata.bind":"[Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000002)"  
}  
```  
  
 **Respuesta**  

```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
```  
<a name="bkmk_Associateentitiesonupdate_multi"></a>

## <a name="associate-entities-on-update-using-collection-valued-navigation-property"></a>Asociar entidades en la actualización mediante una propiedad de navegación de colección valorada

El ejemplo siguiente muestra cómo asociar varias existentes entidades [ActividadParte](../reference/entities/activityparty.md) con una entidad [Correo electrónico](../reference/entities/email.md) mediante la propiedad de navegación de colección valorada `email_activity_parties`.

> [!NOTE]
> Asociar varias entidades con una entidad en la actualización es un escenario especial que es posible solo con <xref href="Microsoft.Dynamics.CRM.activityparty?text=activityparty EntityType" />.

**Solicitud**

```HTTP
PUT [Organization URI]/api/data/v9.0/emails(2479d20d-3a39-e711-8145-e0071b6a2001)/email_activity_parties
Content-Type: application/json  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0

{
    "value": [
        {
            "partyid_contact@odata.bind":"contacts(a30d4045-fc46-e711-8115-e0071b66df51)",
            "participationtypemask":3
            
        },
        {
            "partyid_contact@odata.bind":"contacts(1dcdda07-3a39-e711-8145-e0071b6a2001)",
            "participationtypemask":2
            
        }
        ]
}
```

**Respuesta**

```HTTP
HTTP/1.1 204 No Content  
OData-Version: 4.0 
```

### <a name="see-also"></a>Vea también

 [Ejemplo de operaciones básicas de la API web (C#)](samples/basic-operations-csharp.md)   
 [Ejemplo de operaciones básicas de la API web (JavaScript del lado del cliente)](samples/basic-operations-client-side-javascript.md)   
 [Realizar operaciones mediante la API web](perform-operations-web-api.md)   
 [Componer solicitudes HTTP y administrar errores](compose-http-requests-handle-errors.md)   
 [Consultar datos utilizando la API web](query-data-web-api.md)   
 [Cree una entidad usando API web](create-entity-web-api.md)   
 [Recuperar una entidad usando API web](retrieve-entity-using-web-api.md)   
 [Actualizar y eliminar entidades mediante la API web](update-delete-entities-using-web-api.md)   
 [Usar funciones de la API web](use-web-api-functions.md)   
 [Usar acciones de la API web](use-web-api-actions.md)   
 [Ejecute las operaciones por lotes mediante API web](execute-batch-operations-using-web-api.md)   
 [Suplantar a otro usuario utilizando la API web](impersonate-another-user-web-api.md)   
 [Realizar operaciones condicionales mediante la API web](perform-conditional-operations-using-web-api.md)
