---
title: Propiedades administradas de aplicaciones basadas en modelos para vistas con PowerApps | MicrosoftDocs
description: Aprenda a configurar las propiedades administradas de una vista.
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
ms.openlocfilehash: 9f33212ae81de0418dfc3695d5ae3c8e5acf36da
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39701469"
---
# <a name="model-driven-app-managed-properties-for-views"></a>Propiedades administradas de aplicaciones basadas en modelos para vistas

<a name="BKMK_ManagedProperties"></a>   
 
 Si crea una vista pública personalizada en PowerApps que quiere incluir en una solución administrada que va a distribuir, tiene la opción de limitar la posibilidad de que alguien que instale la solución personalice la vista.  
  
 De forma predeterminada, la mayoría de las vistas tienen su propiedad administrada **personalizable** establecida en verdadero para que los usuarios puedan personalizarlas. A menos que tenga una muy buena razón para cambiar esto, se recomienda permitir que los usuarios personalicen las vistas de la aplicación.  
  
## <a name="set-managed-properties-for-a-view"></a>Establecimiento de las propiedades administradas de una vista  
  
1.  Abra el [Explorador de soluciones](advanced-navigation.md#solution-explorer), expanda **Entidades**, seleccione la entidad que desee y, luego, seleccione **Vistas**.  
  
2.  Seleccione una vista personalizada pública.  
  
3.  En la barra de menús, seleccione **Más acciones** > **Propiedades administradas**.  

    ![menú de propiedades administradas](media/managed-properties.png)
  
4.  Establezca las opciones **Personalizable** o **Puede eliminarse** en **Verdadero** o **Falso**.  

    ![Establecimiento de propiedades administradas](media/set-managed-properties.png)
  
> [!NOTE]
> La configuración no surtirá efecto hasta que se exporte una solución que contenga la vista como una solución administrada y se instale en un entorno diferente.  

## <a name="next-steps"></a>Pasos siguientes
[Descripción de las vistas](create-edit-views.md)
