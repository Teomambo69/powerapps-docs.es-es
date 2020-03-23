---
title: Crear revisiones de solución | MicrosoftDocs
description: Aprenda cómo crear revisiones de solución
ms.custom: ''
ms.date: 02/04/2020
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
caps.latest.revision: 15
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b2a498ab6b5efbca0e3970769dcc3e19c4ecd77d
ms.sourcegitcommit: efb05dbd29c4e4fb31ade1fae340260aeba2e02b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "3100188"
---
# <a name="create-solution-patches"></a>Crear revisiones de solución 
Una revisión contiene solo los cambios en una solución administrada primaria, como agregar o editar componentes y activos. Cuando se importan revisiones, se colocan en capas sobre la solución principal. Cuando se clona una solución, el sistema resume todas las revisiones relacionadas en la solución base y crea una nueva versión.  
  
 Cuando trabaja con las revisiones y soluciones clonadas, tenga en cuenta la siguiente información:  
  
-   Una revisión representa una actualización incremental de menor importancia de la solución primaria. Una revisión puede agregar o actualizar componentes y activos en la solución primaria cuando se instala en el sistema de destino, pero no puede eliminar ningún componente o activo de la solución primaria.  
  
-   Una revisión solo puede tener una solución primaria, pero una solución primaria tiene una o más revisiones.  
  
-   Una revisión se crea para una solución no administrada. No se puede crear una revisión para una solución administrada.  
  
-   Cuando exporta una revisión a un sistema de destino, debe exportarlo como revisión administrada. No use revisiones no administradas en entornos de producción.  
  
-   La solución primaria debe estar presente en el sistema de destino para instalar una revisión.  
  
-   Puede eliminar o actualizar una revisión.  
  
-   Si elimina una solución primaria, todas las revisiones secundarias también se eliminan. El sistema muestra un mensaje de advertencia de que no puede deshacer la operación de eliminación. La eliminación se realiza en una sola transacción. Si una de revisiones o la solución primaria no se elimina, la transacción completa se revertirá.  
  
-   Una vez que haya creado la primera revisión para una solución primaria, la solución pasa a estar bloqueada, y no puede realizar ningún cambio en esta solución o exportarla. Sin embargo, si elimina todas sus revisiones secundarias, la solución primaria se desbloquea.  
  
-   Cuando se clona una solución base, todas las revisiones secundarias se resumen en la solución base y pasa a ser una nueva versión. Puede agregar, editar, o eliminar componentes y activos en la solución clonada.  
  
-   Una solución clonada representa la sustitución de la solución base cuando se instala en el sistema de destino como solución administrada. Normalmente, puede usar una solución clonada para enviar una actualización importante a la solución precedente.  
  
## <a name="understanding-version-numbers-for-cloned-solutions-and-patches"></a>Descripción de los números de versión para soluciones clonadas y revisiones  
 La versión de una solución tiene el siguiente formato: primaria.secundaria.compilación.revisión. Una revisión debe tener un número de compilación o de revisión más alto que la solución primaria. No puede tener una versión importante o de menor importancia más alta. Por ejemplo, para una versión de solución base 3.1.5.7, una revisión podría ser una versión 3.1.5.8 o versión 3.1.7.0, pero no versión 3.2.0.0. Una solución clonada debe tener el número de versión mayor o igual que el número de versión de la solución base. Por ejemplo, para una versión de solución base 3.1.5.7, una solución clonada podría ser una versión 3.2.0.0 o versión 3.1.5.7. En la interfaz de usuario, solo puede establecer los valores de versión importante y secundaria para una solución clonada, y los valores de compilación o de revisiones para una revisión.  
  

## <a name="create-a-solution-patch"></a>Crear una revisión de la solución  
 Una revisión contiene cambios en la solución primaria, como agregar o editar componentes y activos. No es necesario incluir los componentes primarios a menos que prevea modificarlos.  
  
## <a name="create-a-patch-for-an-unmanaged-solution"></a>Crear una revisión de una solución no administrada  
  
1. Vaya al portal Power Apps y luego seleccione **Soluciones**.   
  
2. En la lista de soluciones, seleccione una solución no administrada para la que crear una revisión. En la barra de comandos, seleccione **Clonar** y, después, **Clonar una revisión**. El panel derecho que se abre contiene el nombre de la solución base y el número de versión de la revisión. Seleccione **Guardar**.  
   > [!div class="mx-imgBorder"] 
   > <img src="media/clone-a-patch.png" alt="Clone a patch" height="735" width="408">
 
3. En la lista de soluciones, busque y abra la revisión recién creada. Observe que el nombre único de la solución se ha agregado con _Patch_*hexnumber*. Al igual con la solución base, agregue los componentes y los activos que desee.  
  
### <a name="create-a-patch-using-solution-explorer"></a>Crear una revisión usando el explorador de soluciones
 Las ilustraciones siguientes proporcionan un ejemplo de crear una revisión para una solución existente. Empiece seleccionando **Clonar una revisión** (en la vista comprimida, el icono **Clonar una revisión** se muestra como dos cuadrados pequeños, como se indica a continuación).  
  
 > [!div class="mx-imgBorder"] 
 > ![Clonar un icono de revisión.](media/solution-segmentation-click-patch-icon-admin.png "Clonar un icono de revisión.")  
  
 En el cuadro de diálogo **Clonar para revisar** se ve que el número de versión de la revisión se basa en el número de versión de la solución primaria, pero el número de compilación se incrementa en uno. Cada revisión posterior tiene un número de compilación o de revisión más alto que la revisión precedente.  
  
 ![Usar diálogo Clonar para revisar.](media/solution-segmentation-clone-patch-dialog-admin.png "Usar diálogo Clonar para revisar.")  
  
 La captura de pantalla siguiente muestra la solución base **SegmentedSolutionExample**, versión **1.0.1.0**, y la revisión **SegmentedSolutionExample_Patch**, versión **1.0.2.0**.  
  
 > [!div class="mx-imgBorder"] 
 > ![Una cuadrícula con soluciones y revisiones.](media/solution-segmentation-solution-patch-grid-admin.png "Una cuadrícula con soluciones y revisiones.")  
  
 En la revisión agregamos una nueva entidad personalizada llamada `Book`, e incluimos todos los activos de la entidad `Book` en la revisión.  
  
 ![Agregar entidad personalizada en la revisión.](media/solution-segmentation-add-book-patch-admin.png "Agregar entidad personalizada en la revisión.")  
  
## <a name="clone-a-solution"></a>Clonar una solución  
 Cuando se clona una solución no administrada, la solución original y todas las revisiones relacionadas con la solución se resumen en una versión recién creada de la solución original. Después de clonar, la nueva versión de la solución contiene las tres entidades originales más los componentes o entidades que se agregan en una revisión. 

![Clonar una solución](media/cloned-solution.png)

> [!IMPORTANT]
> Clonar una solución elimina la solución original y las revisiones asociadas. 
  
1. Vaya al portal Power Apps y luego seleccione **Soluciones**.   
  
2.  En la lista de soluciones, seleccione una solución no administrada para crear un clon. En la barra de comandos, seleccione **Clonar** y, después, **Clonar solución**. El panel derecho muestra el nombre de la solución base y el número de la nueva versión. Seleccione **Guardar**.  
  
### <a name="see-also"></a>Vea también
[Información general de las soluciones](solutions-overview.md)