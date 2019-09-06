---
title: Agregar la entidad de equipo como opción de búsqueda en la aplicación| MicrosoftDocs
description: Aprenda a agregar la entidad de equipo como opción de búsqueda en la aplicación
ms.custom: ''
ms.date: 07/24/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: null
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="add-the-team-entity-as-a-lookup-option-in-your-app"></a>Agregar la entidad de equipo como opción de búsqueda en la aplicación

Con aplicaciones de la interfaz unificada, para que la entidad de equipo esté disponible en una búsqueda se debe agregar a la aplicación. Por ejemplo, los registros de contacto tienen la capacidad de asignarse a un usuario o equipo.  

> [!div class="mx-imgBorder"] 
> ![](media/entity-lookup-teams.png "Consulta de entidad con usuarios y equipos disponibles")

Sin embargo, si la entidad de usuario se incluye en la aplicación pero no la entidad de equipo, solo los registros de usuario aparecerán en una búsqueda. 

> [!div class="mx-imgBorder"] 
> ![](media/entity-lookup-user-only.png "Consulta de entidad solo con usuarios")

## <a name="add-the-team-entity-to-an-app"></a>Agregue la entidad de equipo a una aplicación

1. Abra la aplicación en el diseñador de aplicaciones. 
2. Seleccione la pestaña **Componentes**, seleccione **Entidades** y, a continuación, **Equipo**.    

    > [!div class="mx-imgBorder"] 
    > ![](media/add-team-entity-app.png "Agregue la entidad de equipo a la aplicación")

3. Seleccione **Guardar** y luego seleccione **Publicar** para hacer que el cambio esté disponible para los usuarios de la aplicación.   

