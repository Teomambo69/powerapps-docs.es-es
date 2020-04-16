---
title: 'Ejemplo: Calcular una puntuación de crédito con una actividad de flujo de trabajo personalizada (Common Data Service) | Microsoft Docs'
description: El ejemplo muestra una actividad de flujo de trabajo que calcula la puntuación de crédito basada en el número de la seguridad social (SSN) y el nombre.
ms.custom: ''
ms.date: 1/28/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: samples
applies_to:
- Dynamics 365 (online)
ms.assetid: 9cb7eb41-1a73-44a8-ae58-14120e84243f
caps.latest.revision: 19
author: JimDaly
ms.author: jdaly
manager: KumarVivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5d007765af7f8c22d027a65f2a1c8818e1890410
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154904"
---
# <a name="sample-calculate-a-credit-score-with-a-custom-workflow-activity"></a>Ejemplo: Calcular una puntuación de crédito con una actividad de flujo de trabajo personalizada

Este código de muestra es para Common Data Service. Descargue el ejemplo completo aquí: [WorkflowActivities](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/WorkflowActivities).

## <a name="prerequisites"></a>Requisitos previos

[!INCLUDE [sdk-prerequisite](../../../includes/sdk-prerequisite.md)]
  
## <a name="requirements"></a>Requisitos

Las siguientes personalizaciones deben existir para que esta actividad de flujo de trabajo personalizada funcione:  

-   Nombre de esquema de entidad: `new_loanapplication`  
-   Atributo: `new_loanapplicationid` como clave principal  
-   Atributo: `new_creditscore` de tipo `int` con mínimo de 0 y máximo de 1000 (si se va a actualizar)  
-   Atributo: `new_loanamount` de tipo monetario con mínimo/máximo predeterminados  
-   Personalice el formulario para incluir el atributo `new_loanapplicantid`  
  
La entidad contacto debe tener las siguientes personalizaciones:  
  
-   Atributo: `new_ssn` como **Línea de texto única** con la longitud máxima de 15  
-   Relación de uno a varios con estas propiedades:  
    -   Nombre de esquema de definición de relación: `new_loanapplicant`  
    -   Nombre para mostrar de la entidad relacionada con la definición de relación: Aplicación de préstamo  
    -   Nombre de esquema de atributo de relación: `new_loanapplicantid`  
    -   Tipo de comportamiento de relación: Referencial  
  
## <a name="demonstrates"></a>Demostraciones

La siguiente actividad de flujo de trabajo de ejemplo calcula la puntuación de crédito basada en el número de la seguridad social (SSN) y el nombre.  
  
## <a name="example"></a>Ejemplo  

[RetrieveCreditScore.cs](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/orgsvc/C%23/WorkflowActivities/WorkflowActivities/RetrieveCreditScore.cs)

### <a name="see-also"></a>Vea también

[Extensiones de flujo de trabajo](workflow-extensions.md)<br />
[Tutorial: Crear extensión de flujo de trabajo](tutorial-create-workflow-extension.md)<br />
[Ejemplo: crear una actividad de flujo de trabajo personalizada](sample-create-custom-workflow-activity.md)<br />
[Ejemplo: actualizar el siguiente cumpleaños con una actividad de flujo de trabajo personalizada](sample-update-next-birthday-using-custom-workflow-activity.md)
