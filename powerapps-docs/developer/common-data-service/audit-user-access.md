---
title: Auditoría de acceso de usuario (Common Data Service) | Microsoft Docs
description: Compatibilidad con la capacidad de auditar el acceso de usuario, incluida la identificación de usuario, la hora de acceso y el tipo de cliente.
ms.custom: ''
ms.date: 01/27/2019
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
ms.openlocfilehash: 5bc524f4cfbd4d5623894b4de4607d7b3ff96bf5
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156464"
---
# <a name="audit-user-access"></a>Auditoría de acceso de usuario

Common Data Service es compatible con la capacidad de auditar el acceso de usuarios. La información que se registra incluye cuándo empezó el usuario a acceder a Common Data Service y si el acceso se originó en la aplicación web Common Data Service, en Dynamics 365 for Outlook o en llamadas de SDK a los servicios web.  
  
## <a name="enable-user-access-auditing"></a>Habilitar la auditoría de acceso de usuario  
 La auditoría de acceso del usuario se habilita en toda la organización. Para habilitar o deshabilitar la auditoría de acceso de usuario, debe recuperar el registro de la organización de destino y actualizar el valor del atributo `Organization.IsUserAccessAuditEnabled` para la organización. También se debe habilitar la auditoría global de la organización, definiendo el atributo `Organization.IsAuditEnabled` en `true` en el registro de la organización. Para realizar la auditoría del origen de acceso del usuario, por ejemplo: aplicación web, Dynamics 365 for Outlook o SDK, debe habilitar la auditoría en las entidades a las que se está accediendo.  
  
 La frecuencia de acceso del usuario de auditoría se puede leer y definir mediante el atributo `Organization.UserAccessAuditingInterval` . Un valor de atributo predeterminado igual a 4 indica que el acceso de usuario se audita una vez cada 4 horas.  
  
 Para obtener más información sobre cómo habilitar la auditoría de una organización y la entidad, consulte [Configurar entidades y atributos para auditoría](configure-entities-attributes-auditing.md).  
  
## <a name="filter-on-user-access-events"></a>Filtrar eventos de acceso de usuario  
 Para buscar registros de auditoría relacionados con el acceso del usuario, el código debe recuperar los registros de `Audit` de una organización y filtrar el valor en `Audit.Action`. Se proporciona una enumeración denominada `AuditAction` para identificar las acciones de auditoría compatibles. Las acciones relacionadas con el acceso del usuario se muestran en la siguiente lista.  
  
-   `AuditAction.UserAccessviaWeb`  
  
-   `AuditAction.UserAccessviaWebServices`  
  
-   `AuditAction.UserAccessAuditStarted`  
  
-   `AuditAction.UserAccessAuditStopped`  
  
 `UserAccessviaWeb` indica el acceso desde la aplicación web de Common Data Service o Dynamics 365 for Outlook. `UserAccessviaWebServices` indica una solicitud de servicio web desde el SDK. La enumeración `AuditAction` está disponible para el código al incluir `OptionSets.cs` en el proyecto de la aplicación.  
  
### <a name="see-also"></a>Vea también  
 [Auditar cambios de los datos](/powerapps/developer/common-data-service/auditing-overview)   
 [Configurar entidades y atributos para auditoría](/powerapps/developer/common-data-service/configure-entities-attributes-auditing)     
 [Ejemplo: cambios en los datos de la entidad de auditoría](/powerapps/developer/common-data-service/org-service/samples/audit-entity-data-changes)   
 [Ejemplo: acceso de usuario de auditoría](/powerapps/developer/common-data-service/org-service/samples/audit-user-access)
