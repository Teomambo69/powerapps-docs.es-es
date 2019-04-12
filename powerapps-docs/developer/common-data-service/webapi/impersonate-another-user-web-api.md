---
title: Suplantar a otro usuario utilizando la API web (Common Data Service)| Microsoft Docs
description: La suplantación se usa para ejecutar la lógica de negocios (código) en nombre de otro usuario de Common Data Service para proporcionar una característica o servicio deseados con el rol que le corresponde y la seguridad basada en objetos de dicho usuario suplantado. Lea cómo puede suplantar a otro usuario en Common Data Service utilizando la API web
ms.custom: ''
ms.date: 03/18/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 74d07683-63ff-4d05-a434-dcfd44cd634d
caps.latest.revision: 9
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

<!-- TOD0: The higher level topic [Impersonate another user](../impersonate-another-user.md) should include all generic concepts.
This topic should only cover the Web API specific details -->


# <a name="impersonate-another-user-using-the-web-api"></a>Suplantar a otro usuario utilizando la API web

Hay ocasiones en las que el código deberá realizar operaciones en nombre de otro usuario. Si la cuenta del sistema que ejecuta el código tiene los privilegios adecuados, puede realizar operaciones en nombre de otros usuarios.  
  
<a name="bkmk_Requirementsforimpersonation"></a>

## <a name="requirements-for-impersonation"></a>Requisitos de la suplantación

La suplantación se usa para ejecutar la lógica de negocios (código) en nombre de otro usuario de Common Data Service para proporcionar una característica o servicio deseados con el rol que le corresponde y la seguridad basada en objetos de dicho usuario suplantado. Esto es necesario porque varios clientes y servicios en nombre de un usuario de Common Data Service pueden llamar a los servicios web de Common Data Service, por ejemplo, en un flujo de trabajo o una solución de ISV personalizada. La suplantación implica dos cuentas distintas de usuario: una cuenta de usuario (A) que se usa al ejecutar código para realizar algunas tareas en nombre de otro usuario (B).  
  
La cuenta de usuario (A) debe tener el privilegio `prvActOnBehalfOfAnotherUser`, que se incluye en el rol de seguridad Delegado. El conjunto real de privilegios que se utiliza para modificar los datos es la intersección de los privilegios que el usuario con rol de delegado posee con la del usuario que se suplanta. Es decir, al usuario (A) se le permite hacer algo solo si el usuario (A) y el usuario (B) tienen el privilegio necesario para realizar la acción.  
  
<a name="bkmk_Howtoimpersonateauser"></a>

## <a name="how-to-impersonate-a-user"></a>Cómo suplantar a un usuario

Hay dos formas de suplantar a un usuario, ambas posibles pasando un encabezado con el correspondiente identificador de usuario.

 1. **Preferido:** Suplanta a un usuario en función de la identificación de objeto de Azure Active Directory (AAD) pasando ese valor junto con el `CallerObjectId` del encabezado.
2. **Datos heredados:** Para suplantar a un usuario en función de su systemuserid puede aprovechar `MSCRMCallerID` con el valor de guid correspondiente.

 En este ejemplo, se crea una nueva entidad de cuenta en nombre del usuario con un identificador de objeto de Azure Active Directory `e39c5d16-675b-48d1-8e67-667427e9c084`.   
  
 **Solicitud**  
```http 
POST [Organization URI]/api/data/v9.0/accounts HTTP/1.1  
CallerObjectId: e39c5d16-675b-48d1-8e67-667427e9c084  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{"name":"Sample Account created using impersonation"}  
```  
  
 **Respuesta**  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-000000000003)  
```  
  
<a name="bkmk_Determinetheactualuser"></a>

## <a name="determine-the-actual-user"></a>Determinar el usuario real

Cuando una operación como crear una entidad se realiza mediante suplantación, el usuario que realiza la operación se puede encontrar consultando el registro incluida la propiedad de navegación de un solo valor `createdonbehalfby`. Una propiedad de navegación de un solo valor modifiedonbehalfby correspondiente está disponible para operaciones que actualizan la entidad.  
  
 **Solicitud**

```http 
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-000000000003)?$select=name&$expand=createdby($select=fullname),createdonbehalfby($select=fullname),owninguser($select=fullname) HTTP/1.1   
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Respuesta**  
```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
ETag: W/"506868"  
  
{
  "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts(name,createdby(fullname,azureactivedirectoryobjectid),createdonbehalfby(fullname,azureactivedirectoryobjectid),owninguser(fullname,azureactivedirectoryobjectid))/$entity",
  "@odata.etag": "W/\"2751197\"",
  "name": "Sample Account created using impersonation",
  "accountid": "00000000-0000-0000-000000000003",
  "createdby": {
    "@odata.etag": "W/\"2632435\"",
    "fullname": "Impersonated User",
    "azureactivedirectoryobjectid": "e39c5d16-675b-48d1-8e67-667427e9c084",
    "systemuserid": "75df116d-d9da-e711-a94b-000d3a34ed47",
    "ownerid": "75df116d-d9da-e711-a94b-000d3a34ed47"
  },
  "createdonbehalfby": {
    "@odata.etag": "W/\"2632445\"",
    "fullname": "Actual User",
    "azureactivedirectoryobjectid": "3d8bed3e-79a3-47c8-80cf-269869b2e9f0",
    "systemuserid": "278742b0-1e61-4fb5-84ef-c7de308c19e2",
    "ownerid": "278742b0-1e61-4fb5-84ef-c7de308c19e2"
  },
  "owninguser": {
    "@odata.etag": "W/\"2632435\"",
    "fullname": "Impersonated User",
    "azureactivedirectoryobjectid": "e39c5d16-675b-48d1-8e67-667427e9c084",
    "systemuserid": "75df116d-d9da-e711-a94b-000d3a34ed47",
    "ownerid": "75df116d-d9da-e711-a94b-000d3a34ed47"
  }
}
```  
  
### <a name="see-also"></a>Vea también

[Suplantar a otro usuario](../impersonate-another-user.md)<br />
[Suplantar a otro usuario utilizando el servicio de la organización](../impersonate-another-user.md#impersonate-another-user-using-the-organization-service)<br />
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
[Realizar operaciones condicionales mediante la API web](perform-conditional-operations-using-web-api.md)
