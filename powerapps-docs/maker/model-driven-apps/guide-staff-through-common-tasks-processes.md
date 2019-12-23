---
title: Aplicar la lógica empresarial personalizada con reglas de negocio y flujos en aplicaciones basadas en modelos | Microsoft Docs
description: Obtenga información sobre los diferentes tipos de lógica de negocios que puede usar en su aplicación
ms.custom: ''
ms.date: 08/02/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: 0b4e6602-5701-4859-81cc-6f6fe50901b2
caps.latest.revision: 44
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 60060865ec73dda1abed585c03232a367efb82f5
ms.sourcegitcommit: 0f0b26122be28d674af0833247b491e9367c4932
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "2779937"
---
# <a name="apply-custom-business-logic-with-business-rules-and-flows-in-model-driven-apps"></a>Aplicar la lógica empresarial personalizada con reglas de negocio y flujos en aplicaciones basadas en modelos

Definir y forzar procesos de negocio coherentes es una de las principales razones por las que las personas utilizan aplicaciones basadas en modelos. Los procesos coherentes garantizan a los usuarios que usan una aplicación basada en modelos que puedan concentrarse en su trabajo y no en recordar realizar un conjunto de pasos manuales. 

## <a name="business-rules"></a>Reglas de negocio

Las reglas de negocio proporcionan una interfaz básica para implementar y mantener reglas de evolución rápida y de uso general. El *ámbito* der una regla de negocio define si la regla de negocio se ejecutará:

|||  
|-|-|  
|**Si selecciona este elemento…**|**El ámbito se establece como...**|  
|**Entidad**|Todos los formularios y el servidor|  
|**Todos los formularios**|Todos los formularios|  
|Formulario específico (formulario de **Cuenta**, por ejemplo)|Sólo ese formulario| 

Para obtener más información sobre cómo definir reglas de negocio que se aplique a un formulario en una aplicación basada en modelos, consulte [Crear reglas de negocio para aplicar lógica en un formulario de aplicaciones controladas por modelos](create-business-rules-recommendations-apply-logic-form.md).

> [!NOTE]
> Para definir una regla de negocio para una entidad para que se aplique en el servidor o a *aplicaciones de lienzo* y *aplicaciones basadas en modelos*, consulte [Crear una reglas de negocio para una entidad](/powerapps/maker/common-data-service/data-platform-create-business-rule).

## <a name="flows"></a>Flujos  
  
Power Automate incluye varios tipos de procesos, cada uno diseñado con un objetivo:  

-   Flujos automatizados. Cree un flujo que realizará una o varias tareas automáticamente después de que un evento lo desencadene. Más información: [Crear un flujo](/flow/get-started-logic-flow)
    
-   Flujos de botones. Realice tareas repetitivas simplemente tocando un botón en su dispositivo móvil. Más información: [Introducción a flujos de botones](/flow/introduction-to-button-flows)
  
-   Flujos programados. Cree un flujo que realizará una o varias tareas en un programa como una vez al día, en una fecha específica, o después de una determinada hora. Más información: [Ejecutar flujos en un programa](/flow/run-scheduled-tasks)
  
-   Flujos de proceso de negocio.  Asegúrese de que los usuarios especifiquen datos de manera coherente y siguen los mismos pasos cada vez que trabajan con una aplicación mediante la creación de un flujo de proceso de negocio. Más información: [Información general sobre flujos de proceso de negocio](/flow/business-process-flows-overview)

-   Flujos de trabajo y acciones. Los personalizadores de Dynamics 365 puede estar familiarizados con los procesos clásicos de Common Data Service, que son flujos de trabajo y acciones. Más información: [Usar procesos de flujo de trabajo](/flow/workflow-processes) e [Información general sobre acciones](/flow/actions)
  
## <a name="next-step"></a>Paso siguiente

[Crear reglas de negocio para aplicar lógica en un formulario de aplicaciones basadas en modelos](create-business-rules-recommendations-apply-logic-form.md)

### <a name="see-also"></a>Vea también

[Aplicar la lógica de negocios con Common Data Service](../common-data-service/cds-processes.md)
