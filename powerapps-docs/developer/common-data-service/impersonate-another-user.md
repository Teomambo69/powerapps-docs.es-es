---
title: Suplantar a otro usuario (Common Data Service) | Microsoft Docs
description: Use la suplantación para ejecutar la lógica de negocios en nombre de otro usuario de Common Data Service para proporcionar una característica o servicio deseado con el rol que le corresponde y la seguridad basada en objetos de dicho usuario suplantado.
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
ms.openlocfilehash: e817468da9cf506acbaedf6b1617ca1a563661e9
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156160"
---
# <a name="impersonate-another-user"></a>Suplantar a otro usuario

Use la suplantación para ejecutar la lógica de negocios en nombre de otro usuario de Common Data Service para proporcionar una característica o servicio deseado con el rol que le corresponde y la seguridad basada en objetos de dicho usuario suplantado. 

Esto es necesario porque varios clientes y servicios de los servicios web de Common Data Service pueden llamar en nombre de un usuario de Common Data Service.

La suplantación implica dos diferentes cuentas de usuario: 

|Suplantador|Usuario suplantado|
|--|--|
|Cuenta de usuario utilizada cuando se ejecuta código|Cuenta de usuario en nombre de la cual se realiza la tarea.|

## <a name="required-privileges"></a>Privilegios requeridos

El *suplantador* necesita el privilegio de **Actuar en nombre de otro usuario** (`prvActOnBehalfOfAnotherUser`), que se incluye en el rol de seguridad **Delegado** o se puede habilitar para cualquier rol de seguridad.

> [!NOTE]
> Recuerde que los usuarios se pueden asociar a más de un rol de seguridad. La asignación del rol de seguridad **Delegado** a un usuario le concederá el privilegio `prvActOnBehalfOfAnotherUser` así como los privilegios proporcionados por cualquier otro rol de seguridad asociados a la cuenta de usuario.

El conjunto real de privilegios que se utiliza para modificar los datos es la intersección de los privilegios que el usuario *suplantador* posee con los del *usuario suplantado*. 

Es decir, al *suplantador* se le permite hacer algo *solo si* el *suplantador* y el *usuario suplantado* tienen el privilegio necesario para realizar la acción.

## <a name="impersonation-with-server-to-server-authentication"></a>Suplantación con la autenticación de servidor a servidor

Si está creando una aplicación de cliente web que requiere una cuenta de usuario que pueda actuar en nombre del usuario de suscripción, puede usar la cuenta especial *usuario de la aplicación* de modo que no sea necesario usar una licencia de usuario de Common Data Service de pago.

Más información: [Crear aplicaciones web mediante la autenticación de servidor a servidor (S2S)](build-web-applications-server-server-s2s-authentication.md).

## <a name="impersonate-another-user-using-the-web-api"></a>Suplantar a otro usuario utilizando la API web

Para suplantar a un usuario, agregue un encabezado de solicitud llamado `MSCRMCallerID` con un valor GUID igual al `systemuserid` del usuario suplantado antes de enviar la solicitud al servicio web. 

Más información: [Suplantar a otro usuario utilizando la API web](webapi/impersonate-another-user-web-api.md).


## <a name="impersonate-another-user-using-the-organization-service"></a>Suplantar a otro usuario utilizando el servicio de la organización

Para suplantar a otro usuario, establezca la propiedad `CallerId` al valor de GUID del usuario suplantado. Las siguientes clases que implementan <xref:Microsoft.Xrm.Sdk.IOrganizationService> incluyen esta propiedad.

- <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.CallerId>
- <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy.CallerId>
- <xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient>.<xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient.CallerId>

## <a name="impersonate-another-user-using-plug-ins"></a>Suplantar a otro mediante complementos

Puede registrar un complemento en el que puede especificar un usuario que deben usar las operaciones. En el código de un complemento puede reemplazar esta configuración.
Más información: [Suplantar a un usuario](impersonate-a-user.md).


### <a name="see-also"></a>Vea también

[Crear aplicaciones web mediante autenticación de servidor a servidor (S2S)](build-web-applications-server-server-s2s-authentication.md)<br />
[Suplantar a otro usuario utilizando la API web](webapi/impersonate-another-user-web-api.md)<br />
[Escribir un complemento](write-plug-in.md)
