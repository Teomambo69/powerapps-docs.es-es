---
title: Ver actividades en una escala de tiempo del portal | MicrosoftDocs
description: Instrucciones para ver todas las actividades en una escala de tiempo del portal.
author: tapanm-msft
manager: kumarvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 12/12/2019
ms.author: dileeps
ms.reviewer: tapanm
ms.openlocfilehash: 0536890f5665d6b3f6a3cd94aaf6612d06b97293
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "2914402"
---
# <a name="view-activities-in-a-portal-timeline"></a>Ver actividades en una escala de tiempo del portal

Mientras trabaja en un caso o interactúa con un cliente, puede crear una actividad como una cita, un correo electrónico o una llamada de teléfono. Cuando va a la escala de tiempo en el portal de soporte, podría no encontrar esta actividad porque, de manera predeterminada, no se muestran todas las actividades en el portal de escala de tiempo. 

Para ver todas las actividades en una escala de tiempo del portal: 

1. Establezca la configuración del sitio **CustomerSupport/DisplayAllUserActivitiesOnTimeline** como true.  
    
    > [!NOTE]
    > Si no existe la configuración del sitio de **DisplayAllUserActivitiesOnTimeline** no existe, puede crear una nueva configuración con este nombre.

2. Si no está presente, agregue el tipo de actividad para incluir en el filtro de vista:  
    1. Vaya a [**Configuración**](https://docs.microsoft.com/power-platform/admin/admin-settings#app-settings) > **Personalizaciones** > **Personalizar el sistema**.
    2. Seleccione la entidad **Actividad** y expanda **Vistas**.
    3. Edite la **Vista de escala de tiempo del portal**.
    4. Actualice **Editar criterios de filtrado** y agregue el tipo de actividad requerida, como **Cita, correo electrónico o llamada de teléfono**.
    5. **Guarde** y **publique** las personalizaciones. 

    > [!IMPORTANT]
    > La preparación de personalizaciones puede tardar tiempo. Si aparece un mensaje que indica que la página del explorador ha dejado de responder, espere a que responda y no la cierre.

3. Como se trata de un cambio de metadatos del portal, [borre la caché del lado del servidor](../admin/clear-server-side-cache.md) para garantizar que los datos actualizados se muestren en el portal.
