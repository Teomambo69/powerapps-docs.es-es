---
title: Comportamiento de operaciones de actualización especializadas (Common Data Service) | Microsoft Docs
description: Describe el comportamiento especial en complementos y flujos de trabajo para eventos de actualización debido a mensajes obsoletos.
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
ms.openlocfilehash: 97f9c0a917504400170d00cf7764cfeace2cc8a6
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155288"
---
# <a name="behavior-of-specialized-update-operations"></a>Comportamiento de operaciones de actualización especializadas

Hay varios mensajes especializados obsoletos que realizan operaciones de actualización. En versiones anteriores se requería usar estos mensajes, pero ahora las mismas operaciones deben realizarse con <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> o clase <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> con <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>

[!INCLUDE [cc-legacy-update-messages](includes/cc-legacy-update-messages.md)]

Más información: [Mensajes de actualización heredados](org-service/entity-operations-update-delete.md#legacy-update-messages). 

Este cambio introdujo algunos comportamientos especiales que se deben tener en cuenta para complementos y flujos de trabajo. 

## <a name="for-plug-ins"></a>Para complementos

Cuando se procesan solicitudes de actualización que incluyen campos de propietario más otros campos estándar para entidades propiedad de negocio, los complementos registrados para el mensaje **Update** en las fases **PreOperation** y/o **PostOperation** se ejecutan una vez para todos los campos que no son de propietario, y después una vez para los campos de propietario. Los ejemplos de campos de propietario serían `businessunit` y `manager` (para una [entidad SystemUser](reference/entities/systemuser.md)). Los ejemplos de entidades propiedad de negocio incluyen [SystemUser](reference/entities/systemuser.md), [BusinessUnit](reference/entities/businessunit.md),[Equipment](/dynamics365/customer-engagement/developer/entities/equipment) y [Team](reference/entities/team.md).

Cuando se procesan solicitudes de actualización que incluyen campos de estado más otros campos estándar para el mensaje **Update** en las fases **PreOperation** y/o **PostOperation** se ejecutan una vez para todos los campos que no son de estado, y después una vez para los campos de estado.

Para que el código del complemento reciba todos los de datos de la actualización, debe registrar el complemento en la **PreOperation** y después almacenar información relevante en <xref:Microsoft.Xrm.Sdk.IExecutionContext.SharedVariables> en el contexto del complemento para que complementos posteriores (en la canalización) lo consuman.

## <a name="for-workflows"></a>Para flujos de trabajo

Cuando se procesan solicitudes de actualización que incluyen campos de propietario más otros campos estándar para entidades propiedad de negocio, los flujos de trabajo registrados para el mensaje **Update** se ejecutan una vez para todos los campos que no son de propietario, y después una vez para los campos de propietario. Los flujos de trabajo registrados para el mensaje **Assign** por los usuarios se siguen desencadenando mediante actualizaciones en los campos de propietario.

Cuando se procesan solicitudes de actualización que incluyen campos de estado más otros campos estándar para entidades propiedad de negocio, los flujos de trabajo registrados para el mensaje **Update** se ejecutan una vez para todos los campos que no son de estado, y después una vez para los campos de estado. Los flujos de trabajo registrados para el paso **Cambiar estado** se siguen desencadenando mediante actualizaciones en los campos de estado.

### <a name="see-also"></a>Vea también

[Actualizar y eliminar entidades con el servicio de la organización](org-service/entity-operations-update-delete.md)<br />
[Marco de trabajo de eventos](event-framework.md)