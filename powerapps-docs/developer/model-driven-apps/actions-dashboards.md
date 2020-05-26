---
title: Acciones en paneles (aplicaciones basadas en modelos) | Microsoft Docs
description: Obtenga información sobre cómo realizar acciones como crear, recuperar, actualizar o eliminar en paneles que pertenecen a una organización y a un usuario.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 339eb79d-5dec-885b-496f-bfa26e9cae08
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: fdb1fc5ceb8ec5ead1b5e43bc79e500de0f6a39a
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276136"
---
# <a name="actions-on-dashboards"></a>Acciones en los paneles

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/actions-dashboards -->

Puede realizar acciones, como crear, recuperar, actualizar o eliminar paneles que pertenecen a una organización y a un usuario.  
  
## <a name="actions-on-an-organization-owned-dashboard"></a>Acciones en un panel que pertenece a una organización  
 Para realizar las siguientes acciones en un panel que pertenece a una organización (`SystemForm`), debe tener el rol de administrador del sistema o del personalizador del sistema asignado a su cuenta en Common Data Service:  
  
- Crear, recuperar, actualizar y eliminar. Puede crear o actualizar un panel de propiedad de la organización mediante los servicios web de Common Data Service o mediante la personalización del formulario de entidad. Para obtener información detallada acerca de cómo crear un panel, consulte [Crear un panel](create-dashboard.md).  
  
- Defina un panel que pertenece a la organización como el panel predeterminado para una organización al definir el valor de atributo de `SystemForm.IsDefault` en `true` mientras crea o actualiza el panel.  
  
  > [!IMPORTANT]
  >  Mediante los métodos disponibles en los servicios web de Common Data Service para aplicaciones, es posible establecer dos paneles como el valor predeterminado. Asegúrese de que no ningún otro panel sea el panel predeterminado para la organización antes de actualizar esta configuración mediante programación.  
  
  Después de actualizar un panel que pertenece a una organización, debe publicar los cambios en los metadatos para hacerlos visibles en la organización. Puede usar el mensaje de <xref:Microsoft.Crm.Sdk.Messages.PublishAllXmlRequest> o el mensaje de <xref:Microsoft.Crm.Sdk.Messages.PublishXmlRequest> para publicar los cambios realizados en un panel que pertenece a una organización. Para un código de ejemplo que muestre esta situación, consulte [Ejemplo: Crear, recuperar, actualizar y eliminar un panel](/dynamics365/customer-engagement/developer/customize-dev/sample-create-retrieve-update-delete-dashboard)<!-- TODO Need to update the powerapps repo's topic link. As of now not found-->.  
  
  Para obtener una lista de mensajes admitidos en la entidad de paneles que pertenecen a la organización, vea [Entidad SystemForm](../common-data-service/reference/entities/systemform.md).  
  
## <a name="actions-on-a-user-owned-dashboard"></a>Acciones en un panel propiedad del usuario  
 Puede realizar las siguientes acciones en un panel propiedad del usuario (`UserForm`):  
  
- Crear, recuperar, actualizar y eliminar. Para obtener información detallada acerca de cómo crear un panel que pertenece del usuario, consulte [Crear un panel](create-dashboard.md).  
  
- Cambiar la propiedad de un panel propiedad del usuario al asignarlo a otro usuario o equipo con el mensaje de <xref:Microsoft.Crm.Sdk.Messages.AssignRequest>.  
  
- Recupere el acceso que la entidad de seguridad especificada (usuario o equipo) tiene sobre un panel propiedad del usuario mediante el mensaje de <xref:Microsoft.Crm.Sdk.Messages.RetrievePrincipalAccessRequest>. También puede recuperar todas las entidades de seguridad (usuarios o equipos) con acceso a un panel propiedad del usuario, junto con sus derechos de acceso al panel de usuario mediante el mensaje de <xref:Microsoft.Crm.Sdk.Messages.RetrieveSharedPrincipalsAndAccessRequest>.  
  
- Colaborar con otros usuarios y equipos en áreas específicas al compartir un panel propiedad de usuario con ellos mediante <xref:Microsoft.Crm.Sdk.Messages.GrantAccessRequest>, <xref:Microsoft.Crm.Sdk.Messages.ModifyAccessRequest>, y los mensajes de <xref:Microsoft.Crm.Sdk.Messages.RevokeAccessRequest>.  
  
  Para obtener una lista de mensajes admitidos en la entidad de paneles que pertenecen al usuario, vea [Entidad UserForm](../common-data-service/reference/entities/userform.md).  
  
### <a name="see-also"></a>Vea también  

 [Paneles para Microsoft Dynamics 365](analyze-data-with-dashboards.md)   
 [Uso de FormXML para paneles](understand-dashboards-dashboard-components-formxml.md)   
 [Crear un panel](create-dashboard.md)   
 [Paneles de ejemplo](sample-dashboards.md)   
 [Entidades de panel](/dynamics365/customer-engagement/developer/customize-dev/dashboard-entities) <!-- TODO Need to update the powerapps repo's topic link. As of now not found-->  
 [Ejemplo: crear, recuperar, actualizar y eliminar (CRUD) un panel](/dynamics365/customer-engagement/developer/customize-dev/sample-create-retrieve-update-delete-dashboard) <!-- TODO Need to update the powerapps repo's topic link. As of now not found-->   
 [Ejemplo: Asignar un panel propiedad del usuario a otro usuario](/dynamics365/customer-engagement/developer/customize-dev/sample-assign-user-owned-dashboard-another-user) <!-- TODO Need to update the powerapps repo's topic link. As of now not found-->