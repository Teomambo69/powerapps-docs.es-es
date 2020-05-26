---
title: Ver el historial de una solución | MicrosoftDocs
description: Aprender a ver el historial de una solución
keywords: ''
ms.date: 04/20/2020
ms.service: powerapps
ms.custom: ''
ms.topic: article
ms.assetid: ''
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: ''
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 75880ec6d29dbb8e9fa9e5f1c2ef4f9721a479ce
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276030"
---
# <a name="view-the-history-of-a-solution"></a>Ver el historial de una solución
Puede ver los detalles de las operaciones de una solución desde el área **Soluciones** de Power Apps. Una operación puede ser la importación, exportación o desinstalación de una solución. El historial de la solución muestra información como versión de la solución, editor de soluciones, tipo de operación, hora de inicio y finalización de la operación, y estado de la operación.

## <a name="view-solution-history"></a>Ver historial de la solución
1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
2.  En el panel de navegación de la izquierda seleccione **Soluciones**, seleccione la solución que desee y, en la barra de comandos, seleccione **Ver historial**. 

    Se mostrará el historial. 

    > [!div class="mx-imgBorder"] 
    > ![](media/solution-history.png "Solution history")

Seleccione una operación de solución para mostrar la **Página de información**. Cada registro del historial de soluciones es de solo lectura e incluye lo siguiente en el área **Detalles**:
-   **Nombre**. Nombre único de la solución. 
-   **Hora de inicio**. Hora en que se inició la operación.
-   **Hora de finalización**: hora en la que la operación terminó.
-   **Versión**. Versión de la solución.
-   **Editor**. Nombre del editor que está asociado con la operación. 
-   **Operación**. La operación, como importar, exportar, o eliminar. 
-   **Suboperación**: Indica el tipo de operación, como la importación de una nueva solución o la actualización de una solución existente.
-   **Resultado**. El resultado de la operación, como Éxito o Error.

 > [!div class="mx-imgBorder"] 
 > ![](media/solution-history-details.png "Solution history details")

### <a name="view-solution-operation-error-details"></a>Ver detalles de error de operaciones de la solución 
Bajo el área **Detalles** está el área **Más detalles**, que tiene información adicional sobre la solución y, cuando una operación de la solución falla, la información incluye: 
- El **código de error** del error devuelto desde la operación. 
- El **mensaje de excepción**, que puede ayudar a diagnosticar la causa subyacente del fallo de la operación. Algunos errores, incluidos errores de dependencia de la solución, también pueden incluir vínculos a capas de la solución para que sea más fácil diagnosticar el problema. 
- El **Id. de actividad** puede resultar útil en casos en los que necesite ponerse en contacto con el soporte al cliente de Microsoft.

### <a name="see-also"></a>Vea también
[Ver capas de las soluciones](solution-layers.md)  <br />
[Información general de las soluciones](solutions-overview.md) 


