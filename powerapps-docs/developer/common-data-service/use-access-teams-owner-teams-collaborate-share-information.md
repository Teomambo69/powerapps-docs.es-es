---
title: Usar equipos de acceso y de propietario para colaborar y compartir información (Common Data Service) | Microsoft Docs
description: Aprenda a utilizar equipos de acceso y equipos de propietarios para colaborar y compartir información.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: 1454c5db803851d5d691db05e57af0beeb90a2b3
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753780"
---
# <a name="use-access-teams-and-owner-teams-to-collaborate-and-share-information"></a>Usar equipos de acceso y de propietario para colaborar y compartir información

Con equipos *de propietario* o equipos *de acceso*, es muy fácil compartir objetos de negocio y colaborar con los usuarios en distintas unidades de negocio en Common Data Service. Pese a que un equipo pertenece a una unidad de negocio, puede incluir usuarios de otras unidades de negocio. Un usuario se pueden asociar con más de un equipo.  
  
 Un equipo de propietarios tiene registros y roles de seguridad asignados. Los privilegios del equipo se definen mediante roles de seguridad. Además de los privilegios proporcionados por el equipo, los miembros del equipo tienen los privilegios definidos por sus roles de seguridad individuales y por los roles de los otros equipos de los que son integrantes. Un equipo tiene derechos de acceso completo a los registros propiedad del equipo.  
  
> [!NOTE]
>  Aunque los equipos proporcionan acceso a un grupo de usuarios, debe seguir asociando usuarios individuales con roles de seguridad que conceden los privilegios que necesitan para crear, actualizar, o eliminar registros propiedad del usuario. Estos privilegios no se pueden aplicar asignando roles de seguridad a un equipo y después agregando el usuario a ese equipo.  
  
 Un equipo de acceso no es propietario de registros propios y no tiene los roles de seguridad asignados al equipo. Los miembros del equipo tienen privilegios definidos por sus roles de seguridad individuales y por los roles de los equipos de los que son integrantes. Los registros se comparten con un equipo de acceso y a los integrantes del equipo se les asignan derechos de acceso sobre los registros, como Lectura, Escritura o Anexar.  
  
 La funcionalidad del equipo es compatible con la entidad `Team` y la entidad `TeamTemplate` . La entidad `Team` se utiliza para crear equipos de propietario y equipos de acceso creados por el usuario. En el caso de los equipos de acceso creados automáticamente, se utilizan la entidad `Team` y la entidad `TeamTemplate` .  
  
<a name="BKMK_OwnerAccess"></a>   
## <a name="owner-team-or-access-team"></a>¿Equipo de propietario o equipo de acceso?  
 Elegir el tipo de equipo pueden depender de los objetivos, de la naturaleza del proyecto e incluso del tamaño de la organización. Hay algunas instrucciones que se pueden usar cuando seleccione el tipo del equipo.  
  
### <a name="when-to-use-owner-teams"></a>Cuándo usar los equipos de propietario  
  
- Las directivas empresariales requieren la propiedad de registros por parte de entidades distintas a usuarios.  
  
- El número de equipos se conoce en el momento del diseño del sistema Common Data Service.  
  
- La creación diaria de informes sobre el progreso de los equipos propietarios es obligatoria.  
  
### <a name="when-to-use-access-teams"></a>Cuándo usar los equipos de acceso  
  
- Los equipos se forman y se disuelven dinámicamente. Normalmente, esto ocurre si no se proporcionan criterios claros para definir los equipos, como la zona de ventas, el producto o el volumen.  
  
- El número de equipos no se conoce en el momento del diseño del sistema Common Data Service.  
  
- Los miembros del equipo requieren derechos de acceso diferentes para los registros. Puede compartir un registro con varios equipos de acceso, donde cada equipo proporciona distintos derechos de acceso al registro. Por ejemplo, se asigna a un equipo el derecho de acceso de lectura sobre la cuenta y, a otro equipo, los derechos de acceso de lectura, escritura y uso compartido para la misma cuenta.  
  
- Un único conjunto de usuarios requiere acceso a un solo registro sin tener la propiedad del registro.  
  
> [!NOTE]
>  Otro tipo "equipo de acceso" está dirigida por las plantillas del equipo de acceso que usa la aplicación web. Este es el tipo de equipo que cambia a menudo, como el equipo de ventas de un registro de cuenta específico. Cuando se agrega un usuario a un equipo de ventas en una cuenta, la aplicación web, en segundo plano, crea un equipo específico para este registro y le agrega el usuario.  
>   
>  No se describe este tipo de equipo de acceso en este tema.  
  
<a name="BKMK_SettingUp"></a>   
## <a name="setting-up-teams"></a>Configuración de equipos  
 Además de los tipos de equipo de propietarios y accesos, los equipos de acceso están subdivididos en equipos creados por el usuario y equipos creados automáticamente (administrados por el sistema). La información de configuración es específica para cada tipo de equipo.  
  
### <a name="owner-team"></a>Equipo de propietarios  
 Un equipo de propietarios puede poseer varios registros. Para crear un equipo de propietarios, use la entidad `Team` y defina el atributo `Team.TeamType` en `Owner`. Para obtener una lista de los valores de `TeamType`, consulte los metadatos de la entidad `Team`.  
  
> [!NOTE]
> Para ver los metadatos de las entidades de su organización, instale la solución Explorador de metadatos que se describe en [Exploración de los metadatos de su organización](/dynamics365/customer-engagement/developer/browse-your-metadata). También puede examinar la documentación de referencia para las entidades en la [Referencia de entidad](/dynamics365/customer-engagement/developer/about-entity-reference). 
  
 Para convertir a un equipo en propietario del registro, tiene que asignar un registro al equipo. Para esto, use el mensaje <xref:Microsoft.Crm.Sdk.Messages.AssignRequest>. Para asignar registros a un equipo de propietarios en masa, use el mensaje <xref:Microsoft.Crm.Sdk.Messages.ReassignObjectsOwnerRequest> o el mensaje <xref:Microsoft.Crm.Sdk.Messages.ReassignObjectsSystemUserRequest> .  
  
 Un registro propiedad del equipo debe tener la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.OwnershipType> establecida en <xref:Microsoft.Xrm.Sdk.Metadata.OwnershipTypes>.`TeamOwned`.  
  
 Si un equipo de propietarios no tiene la propiedad de los registros y no tiene roles de seguridad asignados, se puede convertir en un equipo de acceso utilizando el mensaje <xref:Microsoft.Crm.Sdk.Messages.ConvertOwnerTeamToAccessTeamRequest>. Se trata de una conversión unidireccional. No puede convertir al equipo de acceso de nuevo en un equipo de propietario. Durante la conversión, todos los buzones y las colas asociados con el equipo se eliminan.  
  
 Para agregar o quitar integrantes del equipo, use el mensaje <xref:Microsoft.Crm.Sdk.Messages.AddMembersTeamRequest> y el mensaje <xref:Microsoft.Crm.Sdk.Messages.RemoveMembersTeamRequest> .  
  
### <a name="user-created-access-team"></a>Equipo de acceso creado por el usuario  
 Puede compartir varios registros con un equipo de acceso creado por el usuario. Para crear un equipo de acceso, use la entidad de equipo y defina el atributo `Team.TeamType` en `Access`. Para obtener una lista de los valores de `TeamType`, consulte los metadatos de la entidad `Team`. Encontrará esta información en los metadatos de la organización. Consulte la información de explorador de metadatos precedente.  
  
 Para compartir un registro con el equipo de acceso creado por el usuario, use el mensaje <xref:Microsoft.Crm.Sdk.Messages.GrantAccessRequest> . En el caso de los equipos creados por el usuario, el atributo `Team.SystemManaged` es `false`. Para obtener una lista de los valores de `Team.SystemManaged`, consulte los metadatos de la entidad `Team`. Encontrará esta información en los metadatos de la organización. Consulte la información de explorador de metadatos precedente.  
  
 Para agregar o quitar integrantes del equipo, use el mensaje <xref:Microsoft.Crm.Sdk.Messages.AddMembersTeamRequest> y el mensaje <xref:Microsoft.Crm.Sdk.Messages.RemoveMembersTeamRequest> .  
  
 Para proporcionar a los miembros del equipo distintos derechos de acceso sobre los registros, cree varios equipos y otorgue a cada equipo un conjunto de derechos de acceso distinto sobre los registros.  
  
### <a name="auto-created-system-managed-access-team"></a>Equipo de acceso (administrado por el sistema) creado automáticamente  
 Se crea un equipo (administrado por el sistema) creado automáticamente para un registro específico y no se puede compartir con otros registros. Para equipos administrados por el sistema, es necesario proporcionar una plantilla del equipo. Para crear una plantilla, use la entidad de plantilla del equipo. En la plantilla, tiene que indicar el tipo de entidad y los derechos de acceso, como lectura o escritura, sobre el registro de entidades que se asignan a los usuarios del equipo cuando este se crea. La entidad especificada en la plantilla debe estar habilitada para equipos de acceso creados automáticamente. Para proporcionar a los miembros del equipo distintos derechos de acceso al registro, cree varias plantillas de equipo. Por ejemplo, para la entidad de cuenta, proporcione una plantilla con derecho de acceso de lectura al equipo que solo necesita ver el registro. Proporcione una segunda plantilla con derechos de acceso de lectura, escritura y uso compartido al equipo que requiera más acceso al mismo registro.  
  
 Para habilitar una entidad para los equipos de acceso creados automáticamente, defina el atributo <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.AutoCreateAccessTeams> en `true`.  
  
 El número máximo de plantillas del equipo que puede crear para una entidad se especifica en el valor de la implementación de <xref:Microsoft.Xrm.Sdk.Deployment.TeamSettings.MaxAutoCreatedAccessTeamsPerEntity>. El valor predeterminado es 2. Un número máximo de entidades que puede habilitar para equipos de acceso creados automáticamente se especifica en el valor de la implementación de <xref:Microsoft.Xrm.Sdk.Deployment.TeamSettings.MaxEntitiesEnabledForAutoCreatedAccessTeams>. El valor predeterminado es 5. Más información: [Entidades de implementación y opciones de configuración de implementación](https://msdn.microsoft.com/library/gg328063.aspx) y [Uso de Windows PowerShell para administrar la implementación](https://technet.microsoft.com/library/dn531202.aspx)  
  
 En el equipo administrado por el sistema, los usuarios se agregan o se quitan automáticamente al agregar o quitar los usuarios de un registro determinado con el mensaje <xref:Microsoft.Crm.Sdk.Messages.AddUserToRecordTeamRequest> y el mensaje <xref:Microsoft.Crm.Sdk.Messages.RemoveUserFromRecordTeamRequest> . El equipo real se crea cuando se agrega el primer usuario al registro y se devuelve el Id. de equipo en <xref:Microsoft.Crm.Sdk.Messages.AddUserToRecordTeamResponse.AccessTeamId>. El atributo `Team.SystemManaged` para este equipo se establece en `true`. Para obtener una lista de los valores de `Team.SystemManaged`, consulte los metadatos de la entidad `Team`. Encontrará esta información en los metadatos de la organización. Consulte la información de explorador de metadatos precedente.  El autor de la llamada del mensaje debe tener el privilegio de uso compartido sobre la entidad y unos derechos de acceso sobre el registro que coincidan con los derechos de acceso proporcionados en la plantilla. Por ejemplo, si la plantilla especifica derechos de acceso de lectura, el usuario de la llamada debe tener derechos de acceso de lectura sobre el registro. Para agregarlo al equipo, el nivel de acceso mínimo que un usuario debe tener para la entidad especificada en la plantilla es el de lectura básico (usuario).  
  
 Debido a la relación jerárquica entre la plantilla del equipo y los equipos de acceso administrados por el sistema, cuando se elimina una plantilla, todos los equipos asociados a la plantilla se eliminan según las reglas en cascada.  
  
 Si cambia los derechos de acceso de la plantilla del equipo, los cambios solo se aplican a los nuevos equipos de acceso creados automáticamente. Los equipos existentes no se ven afectados.  
  
<a name="BKMK_ShortSummary"></a>   
## <a name="quick-reference-to-teams"></a>Referencia rápida de equipos  
 Use la siguiente información como referencia rápida para los equipos disponibles.  
  
|Equipo|¿Cuándo se usa?|¿Qué entidad usar?|¿Utilizar plantilla de equipo?|¿Qué mensajes se utilizan para agregar o quitar integrantes del equipo?|¿Es propietario de registros?|¿Cuántos registros son de su propiedad o a cuántos puede acceder?|¿Tiene roles de seguridad asignados?|  
|----------|------------------|-------------------------|------------------------|---------------------------------------------------------|-------------------|---------------------------------------------|----------------------------------|  
|Propietario|Es necesario que el equipo tenga la propiedad de los registros.<br /><br /> El número de equipos se conoce en el momento del diseño.|`Team`|No|<xref:Microsoft.Crm.Sdk.Messages.AddMembersTeamRequest> <br /> <xref:Microsoft.Crm.Sdk.Messages.RemoveMembersTeamRequest>.|Sí|Puede tener la propiedad de varios registros.|Sí|  
|Acceso, creado por el usuario|Se tienen que compartir varios registros con el equipo.<br /><br /> El número de equipos se desconoce en el momento del diseño.<br /><br /> Los miembros del equipo requieren derechos de acceso distintos para los registros.|`Team`|No|<xref:Microsoft.Crm.Sdk.Messages.AddMembersTeamRequest> <br /> <xref:Microsoft.Crm.Sdk.Messages.RemoveMembersTeamRequest>|No|Puede acceder a varios registros.|Núm. Proporciona derechos de acceso sobre el registro.|  
|Acceso, creado automáticamente (administrado por el sistema)|El conjunto único de usuarios trabaja en un solo registro.<br /><br /> Los miembros del equipo requieren derechos de acceso distintos para los registros.<br /><br /> Se recomienda crear automáticamente equipos por registro.|`TeamTemplate`<br /><br /> `Team`|Sí|<xref:Microsoft.Crm.Sdk.Messages.AddUserToRecordTeamRequest> <br /> <xref:Microsoft.Crm.Sdk.Messages.RemoveUserFromRecordTeamRequest>|No|Solo se puede acceder a un registro.|Núm. Proporciona derechos de acceso sobre el registro.|  
  
> [!NOTE]
>  Los equipos del propietario y equipos de acceso proporcionan derechos de acceso al registro y a registros relacionados, como una cuenta y a todas las oportunidades relacionadas con esta cuenta. En caso de relación jerárquica entre registros, se aplican reglas en cascada. En el caso de los equipos de propietarios, se puede acceder a las entidades en función de los roles asignados al usuario junto con los roles asignados al equipo al que pertenece un usuario. Esto permite que un usuario tenga privilegios fuera de su unidad de negocio. Más información: [Comportamiento de las relaciones de entidad](/dynamics365/customer-engagement/developer/entity-relationship-behavior)  
> 
> [!NOTE]
>  Un usuario debe tener privilegios suficientes para unirse a un equipo de acceso. Por ejemplo, si el equipo de acceso tiene derecho de acceso Eliminación en una cuenta, el usuario debe tener el privilegio Eliminación en la entidad de cuenta para unirse al equipo. Si intenta agregar un usuario con privilegios insuficientes, verá este error: "No se puede agregar el usuario al equipo de acceso porque el usuario no tiene privilegios suficientes en la entidad."  
  
### <a name="see-also"></a>Vea también  
 [Ejemplo: Compartir un registro utilizando un equipo de acceso](org-service/samples/share-record-using-access-team.md)   
 [Administrar equipos](https://technet.microsoft.com/library/dn531089.aspx)   
 [Notas del producto: Equipos de acceso con Microsoft Dynamics CRM 2013](https://download.microsoft.com/download/E/9/0/E9009308-CA01-4B37-B03C-435B8ACB49B4/Access%20Teams%20with%20Microsoft%20Dynamics%20CRM%202013.pdf)   
 [Notas del producto: Modelado de seguridad escalable con Microsoft Dynamics CRM](https://go.microsoft.com/fwlink/p/?LinkID=328757)   
 [Entidades de usuarios y equipos](user-team-entities.md)   
 [Entidad de equipo](reference/entities/team.md)   
 [Entidad de TeamTemplate](reference/entities/teamtemplate.md)   
 [Uso de Windows PowerShell para administrar la implementación](https://technet.microsoft.com/library/dn531202.aspx)   
 [Usar seguridad basada en registros para controlar el acceso a registros](/dynamics365/customer-engagement/developer/security-dev/use-record-based-security-control-access-records)   
 [Cómo se puede usar la seguridad basada en roles para controlar el acceso a las entidades de Dyamics 365.](/dynamics365/customer-engagement/developer/security-dev/how-role-based-security-control-access-entities)   
 [Comportamiento en cascada](/dynamics365/customer-engagement/developer/entity-relationship-behavior#BKMK_CascadingBehavior)
