---
title: Ver el historial de una solución | MicrosoftDocs
description: Aprender a ver el historial de una solución
keywords: ''
ms.date: 05/19/2019
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
ms.openlocfilehash: 67239062f30efb80fb8ee416614c1088e20c4075
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2702211"
---
# <a name="view-the-history-of-a-solution"></a>Ver el historial de una solución
Puede ver los detalles de las operaciones de una solución desde el área **Soluciones** de una aplicación basada en modelos. Una operación puede ser la importación, exportación o eliminación de una solución. El historial de la solución muestra información como versión de la solución, editor de soluciones, tipo de operación, hora de inicio y finalización de la operación, y estado de la operación.

> [!div class="mx-imgBorder"] 
> ![](media/solutions-history-custom-view.png "Solutions history custom view")

## <a name="view-solution-history"></a>Ver historial de la solución
1. Seleccione **Configuración** y, a continuación, seleccione **Historial de soluciones**.

     > [!div class="mx-imgBorder"] 
     > ![](media/solution-history-sitemap.png "Solution History area")

     > [!NOTE]
     > Para ir al área **Configuración** desde una aplicación basada en modelo de la interfaz unificada de PowerApps, seleccione **Configuración** ![Configuración](../model-driven-apps/media/powerapps-gear.png) en la barra de herramientas de la aplicación y, a continuación seleccione **Opciones avanzadas**. 

2. De forma predeterminada, se muestra la vista **Historial de la solución personalizado**. Las vistas siguientes están disponibles en el área **Historial de soluciones**. 
- **Historial de todas las soluciones**. Muestra el historial de las soluciones personalizadas e internas del sistema. 
- **Historial de la solución personalizado**. Muestra solo el historial de las soluciones personalizadas. 
- **Historial de la solución interno**. Muestra solo el historial de las soluciones internas del sistema. 

Cada registro de historial de soluciones es de solo lectura e incluye las propiedades siguientes: 
- **Hora de inicio**. Hora en que se inició la operación. 
- **Hora de finalización**: Hora en que la operación terminó. 
- **Versión de la solución**. Versión de la solución. 
- **Nombre del editor**. Nombre del editor que está asociado con la operación. Más información: [Cambiar el prefijo del editor de soluciones](change-solution-publisher-prefix.md)  
- **Operación**. La operación, como importar, exportar, o eliminar. Más información: [Importar, actualizar y exportar soluciones](import-update-export-solutions.md)
- **Suboperación**: Indica el tipo de operación, como la importación de una nueva solución o la actualización de una solución existente. 
- **Estado**. El estado actual de la operación, como **Completado** o **No completado**. 
- **Resultado**. El resultado de la operación, como **Éxito** o **Error**. 
- **Código de error**: Código de error devuelto de la operación. Un código de error de 0 significa que la operación se completó correctamente. 

### <a name="view-solution-operation-error-details"></a>Ver detalles de error de operaciones de la solución 
Cuando una operación de solución incluye un error puede seleccionarlo para mostrar una página con los detalles adicionales de error. 

> [!div class="mx-imgBorder"] 
> ![](media/solution-history-with-failure.png "Solution history with operation error")

La página de detalles contiene información que incluye el **Mensaje de excepción** que puede ayudar a diagnosticar la causa subyacente para este error de la operación. Algunos errores, incluidos errores de dependencia de la solución, también pueden incluir vínculos a **capas de la solución** para que sea más fácil diagnosticar el problema. El **Id. de actividad** puede resultar útil en casos en los que necesite ponerse en contacto con el soporte al cliente de Microsoft. 

> [!div class="mx-imgBorder"] 
> ![](media/solution-history-error-details.png "Solution operation error details")

### <a name="see-also"></a>Vea también
[Ver capas de las soluciones](solution-layers.md)  <br />
[Información general de las soluciones](solutions-overview.md) 


