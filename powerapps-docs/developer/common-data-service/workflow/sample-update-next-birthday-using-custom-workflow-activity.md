---
title: 'Ejemplo: actualizar el siguiente cumpleaños con una actividad de flujo de trabajo personalizada (Common Data Service) | Microsoft Docs'
description: 'La siguiente actividad de flujo de trabajo de ejemplo devuelve el próximo cumpleaños. Use esto en un flujo de trabajo que envíe una felicitación de cumpleaños a un cliente. '
ms.custom: ''
ms.date: 1/28/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: samples
applies_to:
- Dynamics 365 (online)
ms.assetid: 1cff83b0-1f7b-4ddb-a2af-b85f9f785529
caps.latest.revision: 21
author: JimDaly
ms.author: jdaly
manager: KumarVivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b419800c6a556c61a8b9bf1ea0344e6798ea6e79
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154932"
---
# <a name="sample-update-next-birthday-using-a-custom-workflow-activity"></a>Ejemplo: actualizar el siguiente cumpleaños con una actividad de flujo de trabajo personalizada

Descargue el ejemplo completo aquí: [WorkflowActivities](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/WorkflowActivities).

## <a name="prerequisites"></a>Requisitos previos

[!INCLUDE [sdk-prerequisite](../../../includes/sdk-prerequisite.md)]
  
## <a name="requirements"></a>Requisitos 
 
El siguiente campo personalizado debe existir para que esta actividad personalizada de flujo de trabajo funcione:  
  
-   `Contact`.`new_nextbirthday`  
  
## <a name="demonstrates"></a>Demostraciones  
 La siguiente actividad de flujo de trabajo de muestra devuelve el próximo cumpleaños. Use esto en un flujo de trabajo que envíe una felicitación de cumpleaños a un cliente.  
  
## <a name="example"></a>Ejemplo  

[NextBirthday.cs](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/orgsvc/C%23/WorkflowActivities/WorkflowActivities/NextBirthday.cs)
  
### <a name="see-also"></a>Vea también

[Extensiones de flujo de trabajo](workflow-extensions.md)<br />
[Tutorial: Crear extensión de flujo de trabajo](tutorial-create-workflow-extension.md)<br />
[Ejemplo: crear una actividad de flujo de trabajo personalizada](sample-create-custom-workflow-activity.md)<br />
[Ejemplo: Calcular una puntuación de crédito con una actividad de flujo de trabajo personalizada](sample-calculate-credit-score-custom-workflow-activity.md)
