---
title: Entidades de usuario y equipo (Common Data Service) | Microsoft Docs
description: Obtenga más información sobre la administración de usuarios y equipos mediante la cual puede crear y mantener cuentas y perfiles de usuario.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4757fc868e9d3b9d893c81511338729de1918a4a
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155144"
---
# <a name="user-and-team-entities"></a>Entidades de usuarios y equipos

La administración de usuarios y equipos es el área de Common Data Service donde puede crear y mantener cuentas y perfiles de usuario.  

 Un *usuario* es cualquier persona que trabaje para una unidad de negocio que use Common Data Service. Cada usuario tiene una cuenta de usuario. Todos los usuarios deben estar asociados con una sola unidad de negocio. Esta asociación controla los datos de cliente a los que tendrá acceso el usuario. Se incluye en la cuenta de usuario información como los números de teléfono del usuario, la dirección de correo electrónico y un vínculo al administrador del usuario. Todos los usuarios tienen privilegios y derechos para administrar sus propias configuraciones personales. Cada usuario corresponde a un usuario del Azure Active Directory para esa organización. Al crear un usuario, debe asignarle al menos un rol de seguridad. Incluso si el usuario forma parte de un equipo que tiene roles asignados, se debe asignar un rol al usuario. Para obtener más información acerca de los niveles y roles, consulte [Cómo se puede usar la seguridad basada en roles para controlar el acceso a las entidades de Dynamics 365](/dynamics365/customer-engagement/developer/security-dev/how-role-based-security-control-access-entities).  

 Un *equipo* es un grupo de usuarios. Los equipos permiten a los usuarios de una organización colaborar y compartir información. Para obtener más información sobre los equipos, consulte [Usar equipos para colaborar y compartir información](use-access-teams-owner-teams-collaborate-share-information.md).  

 Los registros pueden ser propiedad de usuarios o equipos. Establezca la <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.OwnershipType> como <xref:Microsoft.Xrm.Sdk.Metadata.OwnershipTypes>.`UserOwned` o bien <xref:Microsoft.Xrm.Sdk.Metadata.OwnershipTypes>.`TeamOwned` para habilitar la propiedad. Puede usar el mensaje <xref:Microsoft.Crm.Sdk.Messages.ReassignObjectsOwnerRequest> o <xref:Microsoft.Crm.Sdk.Messages.ReassignObjectsSystemUserRequest> para realizar la reasignación masiva de todos los registros para un propietario.  

 La siguiente ilustración muestra las relaciones entre entidades para usuarios y equipos.  

 ![Diagrama de relaciones de entidad de usuario y equipo](media/crm-v5s-em-userteam.gif "Diagrama de relaciones de entidad de usuario y equipo")  

## <a name="users"></a>Usuarios  
 En Common Data Service, se pueden deshabilitar los usuarios pero no se pueden eliminar. Para buscar el usuario que ha iniciado la sesión actual o que ha sido suplantado, llame al mensaje <xref:Microsoft.Crm.Sdk.Messages.WhoAmIRequest>.  

 La siguiente tabla proporciona detalles sobre los atributos relevantes para la entidad de usuario del sistema.  


|   Nombre de atributo    |                                                                                                                                                                                                                                                                                                                              Descripción                                                                                                                                                                                                                                                                                                                              |
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     AccessMode      | Especifica el tipo de acceso que este usuario tiene a Common Data Service. Esto se conoce a veces como el tipo de usuario.<br /><br /> -   Administrativo: el usuario tiene acceso al área Configuración pero no tiene acceso a las áreas Ventas, Marketing y Servicio.<br />-   No interactivo: el usuario tiene acceso al sistema pero solo a través del servicio web.<br />-   Lectura: el usuario tiene acceso de solo lectura.<br />-   Lectura y escritura: el usuario tiene acceso de lectura y escritura.<br />-   Usuario de soporte: el usuario lo creó el equipo de soporte de Common Data Service. |
|       CalType       |                                                               Especifica el tipo de licencia del usuario.<br /><br /> -   Administrativo: el usuario posee derechos de usuario administrativo.<br />-   Dispositivo lleno: el usuario que usa el dispositivo donde se ejecuta Common Data Service tiene acceso tanto de lectura como de escritura.<br />-   Dispositivo limitado: el usuario que usa el dispositivo donde se ejecuta Common Data Service solo tiene acceso de lectura.<br />-   Completo: el usuario tiene acceso de lectura y escritura.<br />-   Limitado: el usuario solo tiene acceso de lectura.                                                                |
|     IsDisabled      |                                                                                                                                                                                                                                             Especifica si se deshabilita el usuario. Solo se pueden habilitar los usuarios con licencia o los que tengan un modo de acceso de soporte o no interactivo. Los usuarios de soporte no se pueden deshabilitar.                                                                                                                                                                                                                                              |
|     IsLicensed      |                                                                                                                                                                             Especifica si el usuario tiene licencia. Esto se aplica a los clientes que tienen acceso a Common Data Service para aplicaciones a través del entorno de Microsoft Online Services. Este atributo es de solo lectura, y lo actualiza el sistema.                                                                                                                                                                              |
| IsSyncWithDirectory |                                                                                                                                 Especifica si el usuario está sincronizado con el directorio Office 365. Esto se aplica a los clientes que tienen acceso a Common Data Service para aplicaciones a través del entorno de Microsoft Online Services. Este atributo solo se puede establecer en la creación y es de lo contrario de solo lectura.                                                                                                                                 |
|       QueueId       |                                                                                                                                                                                                                                                                                                               Especifica la cola predeterminada para el usuario.                                                                                                                                                                                                                                                                                                               |

 Las comprobaciones de acceso son aditivas. Puede acceder a las entidades en función de los roles asignados al usuario más los roles asignados al equipo al que pertenece un usuario. Esto permite que un usuario tenga privilegios fuera de su unidad de negocio.  

> [!NOTE]
>  El conjunto de privilegios de un usuario es una combinación de los privilegios y los roles del usuario de todos los roles de los equipos a los que pertenece.  


 Los usuarios no interactivos se usan con frecuencia al escribir código de servicio a servicio porque no utilizan ninguna licencia. Common Data Service permite cinco usuarios no interactivos gratuitos. Para deshabilitar un usuario no interactivo, actualice el registro de usuario cambiando el valor `accessmode` por cualquier otro valor. El usuario se deshabilitará automáticamente.

## <a name="community-tools"></a>Herramientas de la Comunidad

**Configuración de utilidad de usuario** es una herramienta desarrollada por Comunidad XrmToolbox para Common Data Service. Consulte el tema [herramientas para desarrolladores](developer-tools.md) para comunidad de herramientas desarrolladas.

> [!NOTE]
> Las herramientas de la Comunidad no son un producto de Common Data Service y no se amplía el soporte para las herramientas de comunidad.
> Si tiene alguna duda relacionada con la herramienta, póngase en contacto con el Editor. Más información: [XrmToolBox](https://www.xrmtoolbox.com).

### <a name="see-also"></a>Vea también  
 [Entidades de administración y seguridad](/dynamics365/customer-engagement/developer/administration-security-entities)   
 [Usar equipos para colaborar y compartir información](use-access-teams-owner-teams-collaborate-share-information.md)   
 [Entidad de equipo](reference/entities/team.md)   
 [Especificación de la configuración de zona horaria para un usuario](specify-time-zone-settings-user.md)   
 [Entidad de TeamTemplate](reference/entities/teamtemplate.md)   
 [Entidad SystemUser](reference/entities/systemuser.md)   
 [Entidad UserSettings](reference/entities/usersettings.md)   
 [Ejemplo: deshabilitar a un usuario](/dynamics365/customer-engagement/developer/sample-disable-user)   
 [Ejemplo: Compartir registros utilizando los mensajes GrantAccess, ModifyAccess y RevokeAccess](org-service/samples/share-records-using-grantaccess-modifyaccess-revokeaccess-messages.md)   
 [Ejemplo: Compartir un registro utilizando un equipo de acceso](org-service/samples/share-record-using-access-team.md)   
 [Blog: Service Accounts – Non-Interactive Users](https://go.microsoft.com/fwlink/p/?LinkId=234350)   
 [Entidades de privilegio y rol](/dynamics365/customer-engagement/developer/privilege-role-entities)
