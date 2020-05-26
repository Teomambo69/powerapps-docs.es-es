---
title: Eliminar o desactivar una vista de aplicación controlada por modelos en Power Apps | MicrosoftDocs
description: Aprenda cómo eliminar o desactivar una vista
ms.custom: ''
ms.date: 03/30/2020
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
ms.assetid: 60865f78-7482-42da-8960-adbd3c155028
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4c0eea329561fdf35646a04d50ac1b01915ff52b
ms.sourcegitcommit: 3c6c5594b73abd5ff438d50f3b579d56cef7241c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "3285779"
---
# <a name="delete-or-deactivate-a-model-driven-app-view"></a>Eliminar o desactivar una vista de aplicación controlada por modelos 

<a name="BKMK_RemoveViews"></a>   

 Puede que tenga una vista que no desea que la vea nadie. Según el tipo de vista, puede eliminarla o desactivarla. Si no desea eliminar la vista de forma permanente, puede desactivarla.
 
  * Puede eliminar cualquier vista pública personalizada. Una vez que compruebe que realmente desea eliminar la vista, se eliminará permanentemente.

  * No se pueden eliminar ni desactivar las [vistas del sistema](create-edit-views.md#system-views), incluidas las vistas públicas que ha creado el sistema. Puede desactivar cualquier vista pública, incluidas las vistas públicas que ha creado el sistema.

## <a name="delete-a-view"></a>Eliminar una vista

1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Vistas**.

3.  Seleccione **Más comandos** ![botón Más comandos](media/more-commands.gif "Botón Más comandos para formularios") junto a la vista que desea y luego seleccione **Eliminar vista**. También puede seleccionar **Eliminar vista** en la barra de menú.

## <a name="deactivate-or-activate-views"></a>Desactive o active vistas  

1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Vistas**.

3.  Seleccione **Más comandos** ![botón Más comandos](media/more-commands.gif "Botón Más comandos para formularios") junto a la vista que desea y luego seleccione **Desactivar** o **Activar**. También puede seleccionar **Desactivar** o **Activar** en la barra de menú.

## <a name="delete-a-view-in-solution-explorer"></a>Eliminar una vista en el Explorador de soluciones  

Puede eliminar cualquier vista pública personalizada. Use los pasos descritos en [Acceso a definiciones de vistas](accessing-view-definitions.md#open-a-view-for-editing-in-solution-explorer) para buscar la vista que desee eliminar y utilice el comando ![Botón Eliminar](media/delete.gif "Botón Eliminar")**Eliminar**. Una vez que compruebe que realmente desea eliminar la vista, se eliminará permanentemente.  
  
## <a name="deactivate-or-activate-views-in-solution-explorer"></a>Desactivar o activar vistas en el explorador de soluciones 

1.  Acceda a **Vistas del sistema**, tal y como se describe en [Acceso a definiciones de vistas](accessing-view-definitions.md#open-a-view-for-editing-in-solution-explorer).  
  
2.  Seleccione una vista pública. Para ver las vistas inactivas, use la vista **Vistas públicas inactivas**.  
  
3.  En la barra de menús, seleccione **Más acciones** y seleccione **Desactivar** o **Activar**.  
  
4.  Seleccione **Publicar todas las personalizaciones**. 

## <a name="next-steps"></a>Pasos siguientes
[Crear o editar vistas](create-and-edit-views.md)
