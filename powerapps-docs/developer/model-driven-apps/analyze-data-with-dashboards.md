---
title: Analizar datos con paneles (aplicaciones basadas en modelos) | Microsoft Docs
description: Las entidades de paneles de Dynamics 365 Common Data Service le permiten presentar simultáneamente datos de distintos gráficos, cuadrículas, IFRAMES o recursos web. Los paneles le permiten comparar y analizar distintos componentes de información del cliente y le ofrecen instantáneas de datos.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 4b54597b-5603-2e6e-4630-bc120f711707
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 040fe73d5a4a18043511b9b1d7bc80b48eaa0a67
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115976"
---
# <a name="analyze-data-with-dashboards"></a>Analizar datos con paneles

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/analyze-data-with-dashboards -->

Las entidades de paneles de Common Data Service le permiten presentar simultáneamente datos de distintos gráficos, cuadrículas, IFRAMES o recursos web. Los paneles le permiten comparar y analizar distintos componentes de información del cliente y le ofrecen instantáneas de datos.  
  
## <a name="types-of-dashboards"></a>Tipos de paneles  
Existen dos tipos de paneles: paneles propiedad de la organización y paneles propiedad del usuario.  
  
**Panel propiedad de la organización.**

Un panel propiedad de la organización se representa mediante la entidad `SystemForm` y no se puede asignar ni compartir. Estos paneles son entidades compatibles con la solución. Cuando se realiza una operación de actualización en esta entidad, es necesario publicar los cambios para que las actualizaciones estén disponibles en la organización. Si publica personalizaciones mediante el mensaje <xref:Microsoft.Crm.Sdk.Messages.PublishAllXmlRequest>, los paneles propiedad de la organización recién creados también se publicarán y estarán disponibles en la organización. Como alternativa, puede publicar los cambios realizados en un panel específico utilizando el mensaje <xref:Microsoft.Crm.Sdk.Messages.PublishXmlRequest> y especificar el Id. del panel como parámetro del mensaje de solicitud.  
  
**Panel propiedad del usuario.**

Un panel propiedad del usuario está representado por entidad `UserForm` , se puede asignar y compartir con otros usuarios y puede ser visto por otros usuarios en función de los privilegios de acceso del panel.  
  
> [!NOTE]
> No puede crear o administrar mediante programación los nuevos paneles interactivos. Para obtener información sobre cómo trabajar con paneles interactivos con el cliente web, vea [Configurar panales de experiencia interactiva](../../maker/model-driven-apps/configure-interactive-experience-dashboards.md). 
  
### <a name="see-also"></a>Vea también  
 [Uso de FormXML para paneles](understand-dashboards-dashboard-components-formxml.md)   
 [Acciones en los paneles](actions-dashboards.md)   
 [Crear un panel](create-dashboard.md)   
 [Paneles de ejemplo](sample-dashboards.md)   
 [Entidades de panel](/dynamics365/customer-engagement/developer/customize-dev/dashboard-entities)   <!-- TODO: Need to find the topic in powerapps repo to link-->
 [Ejemplo: crear, recuperar, actualizar y eliminar (CRUD) un panel](/dynamics365/customer-engagement/developer/customize-dev/sample-create-retrieve-update-delete-dashboard) <!-- TODO: Need to find the topic in powerapps repo to link-->  
 [Ejemplo: Asignar un panel propiedad del usuario a otro usuario](/dynamics365/customer-engagement/developer/customize-dev/sample-assign-user-owned-dashboard-another-user)  <!-- TODO: Need to find the topic in powerapps repo to link--> 
 [Esquema de descripción de los datos de visualización](visualization-data-description-schema.md)     
 [Personalizar visualizaciones y paneles](customize-visualizations-dashboards.md)
