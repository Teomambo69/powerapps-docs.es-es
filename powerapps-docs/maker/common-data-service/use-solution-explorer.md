---
title: Uso del Explorador de soluciones en PowerApps | Microsoft Docs
description: Aprenda a usar el Explorador de soluciones para crear o personalizar aplicaciones.
ms.custom: ''
ms.date: 06/18/2018
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
ms.assetid: 72bacfbb-96a3-4daa-88ff-11bdaaac9a3d
caps.latest.revision: 57
ms.author: matp
manager: kvivek
ms.openlocfilehash: 6abbe701a6207e68ac367fbe80495a7d04a6e682
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39699742"
---
# <a name="use-the-solution-explorer"></a>Uso del Explorador de soluciones

 En el Explorador de soluciones se puede navegar por la jerarquía de nodos mediante el panel de navegación del lado izquierdo, como se muestra en la captura de pantalla siguiente:  
  
 ![Solución predeterminada con entidades contraídas](media/crm-itpro-cust-defaultsolutionentitiescollapsed.PNG "Solución predeterminada con entidades contraídas")  
  
> [!NOTE]
>  Use el mouse y el teclado cuando para trabajar con las herramientas de personalización en el Explorador de soluciones. Esta parte de la aplicación no está optimizada para pantallas táctiles.  
  
 Al seleccionar cada nodo, puede ver una lista de los componentes de la solución. Las acciones disponibles en la barra de comandos cambiarán según el contexto del nodo que ha seleccionado y si la solución es la solución predeterminada o una solución administrada. Con las soluciones administradas que no son la solución predeterminada, puede usar el comando **Agregar existente** para reunir los componentes de la solución que todavía no están en la solución.  
  
Con las soluciones administradas, no habrá ningún comando disponible y verá el mensaje:  

> [!NOTE]
> No se pueden editar directamente los componentes dentro de una solución administrada. Si se establecen las propiedades administradas de los componentes de la solución para permitir las personalizaciones, puede modificarlas con una herramienta de diseño de PowerApps o desde otra solución no administrada.    
  
 Deberá buscar el componente de la solución en la solución predeterminada e intentar editarlo allí o agregarlo a otra solución no administrada que haya creado. El componente de la solución podría no ser personalizable. Más información: [Propiedades administradas](solutions-overview.md#managed-properties)
  
 Muchas de las personalizaciones que desea aplicar afectan a las entidades. Puede expandir el nodo **Entidades** para mostrar una lista de todas las entidades del sistema que se pueden personalizar de alguna manera. Puede expandir cada entidad para ver los componentes de las soluciones que forman parte de la entidad, como se muestra en la entidad de cuenta en la captura de pantalla siguiente:  
  
 ![Solución predeterminada que muestra la entidad de cuenta expandida](media/crm-itpro-cust-defaultsolution.PNG "Solución predeterminada que muestra la entidad de cuenta expandida")  
  
 Para más información sobre cómo personalizar los componentes individuales de una solución que se encuentran en el Explorador de soluciones, vea los temas siguientes:  
  
-   Para las personalizaciones de entidades, relaciones entre entidades, campos y mensajes, vea [Metadatos](create-edit-metadata.md).  
  
-   Para los formularios de entidad, vea [Formularios](../model-driven-apps/create-design-forms.md).  
  
-   Para los procesos, vea [Procesos](../model-driven-apps/guide-staff-through-common-tasks-processes.md).  
  
-   Para las reglas de negocios, vea [Reglas de negocio](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md).  
