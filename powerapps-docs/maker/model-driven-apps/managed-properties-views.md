---
title: Propiedades administradas de aplicaciones controladas por modelos para vistas con PowerApps | MicrosoftDocs
description: Aprenda cómo establecer propiedades administradas de una vista
ms.custom: ''
ms.date: 06/12/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: a9014576-8fb2-4f28-b8bb-5d2d49d76e12
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="model-driven-app-managed-properties-for-views"></a>Propiedades administradas de aplicaciones controladas por modelos para vistas

<a name="BKMK_ManagedProperties"></a>   
 
 Si crea una vista pública personalizada en PowerApps que desea incluir en una solución administrada que distribuirá, tiene la opción de limitar la capacidad de personalizar la vista a cualquier usuario que esté instalando la solución.  
  
 De forma predeterminada, la mayoría de las vistas tienen la propiedad administrada **Personalizable** establecida como verdadero para que los usuarios puedan personalizarlas. A menos que tenga una razón muy buena para cambiar esto, se recomienda permitir que los usuarios personalicen las vistas en la aplicación.  
  
## <a name="set-managed-properties-for-a-view"></a>Establecer las propiedades administradas para una vista  
  
1.  Abra el [explorador de soluciones](advanced-navigation.md#solution-explorer), expanda **Entidades**, seleccione la entidad que desee y, a continuación, seleccione **Vistas**.  
  
2.  Seleccione una vista pública personalizada.  
  
3.  En la barra de menús, seleccione **Más acciones** > **Propiedades administradas**.  

    > [!div class="mx-imgBorder"] 
    > ![menú propiedades administradas](media/managed-properties.png)
  
4.  Establezca las opciones de **Personalizable** o **Puede eliminarse** en **Verdadero** o **Falso**.  

    > [!div class="mx-imgBorder"] 
    > ![Establecer propiedades administradas](media/set-managed-properties.png)
  
> [!NOTE]
> Este valor no surte efecto hasta que exporte una solución que contenga la vista como solución administrada y la instale en otro entorno.  

## <a name="next-steps"></a>Pasos siguientes
[Comprender las vistas ](create-edit-views.md)
