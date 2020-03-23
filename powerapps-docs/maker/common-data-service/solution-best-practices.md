---
title: Prácticas recomendadas de soluciones en Power Apps | MicrosoftDocs
description: Información sobre prácticas recomendadas cuando trabaja con soluciones
ms.custom: ''
ms.date: 10/08/2019
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
ms.assetid: ''
caps.latest.revision: 55
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 39f3780d0c8bbe33512b5eaec2719bd6f3912d91
ms.sourcegitcommit: efb05dbd29c4e4fb31ade1fae340260aeba2e02b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "3100079"
---
# <a name="best-practices-when-working-with-solutions"></a>Prácticas recomendadas cuando trabaja con soluciones 
Este tema describe las prácticas recomendadas cuando trabaja con soluciones. 


## <a name="use-a-single-managed-solution-to-manage-a-model-driven-app"></a>Use una sola solución administrada para administrar una aplicación basada en modelo 
Para actualizar la aplicación que se incluyó en la solución administrada, use actualizar o revisar soluciones. No instale diferentes soluciones administradas en un entorno que tiene la misma aplicación basada en modelos. Más información: [Actualizar soluciones](update-solutions.md) y [Usar soluciones segmentadas y parches para exportar activos seleccionados de la entidad](use-segmented-solutions-patches-simplify-updates.md) 


## <a name="use-security-roles-to-manage-app-access"></a>Use roles de seguridad para gestionar el acceso a aplicaciones
Las aplicaciones basadas en modelo deben tener roles de seguridad asignados para controlar el acceso de usuarios. Más información: [Compartir una aplicación basada en modelo con Power Apps](../model-driven-apps/share-model-driven-app.md) 

## <a name="delete-the-managed-solution-to-delete-a-model-driven-app"></a>Eliminar la solución administrada para eliminar una aplicación basada en modelos 
Para eliminar una aplicación basada en modelo que se instaló en la solución predeterminada como parte de una solución administrada, elimine la solución administrada. 

No elimine directamente una aplicación o el mapa del sitio de una aplicación del entorno predeterminado que se instaló como parte de una solución administrada. Si lo hace podría producirse un error en la actualización de la solución usada para instalar la aplicación. Un ejemplo de eliminar directamente una aplicación basada en modelo sería abrir la solución predeterminada en el Explorador de soluciones e ir a **Aplicaciones basadas en modelo**, seleccionar la aplicación y, a continuación seleccionar **Eliminar**.

### <a name="see-also"></a>Vea también
[Información general de las soluciones](solutions-overview.md)
