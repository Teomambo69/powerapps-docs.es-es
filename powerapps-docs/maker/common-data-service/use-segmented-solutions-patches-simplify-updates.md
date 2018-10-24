---
title: Uso de soluciones y revisiones segmentadas para simplificar las actualizaciones de soluciones con PowerApps | MicrosoftDocs
description: Aprenda a usar la segmentación de soluciones para actualizar sus soluciones.
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
ms.assetid: 5c05f683-e1bd-4885-be23-b6973128773f
caps.latest.revision: 15
ms.author: matp
manager: kvivek
ms.openlocfilehash: 274e2914d65b6bcb644821c044adb3b0246a75fc
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39701790"
---
# <a name="use-segmented-solutions-and-patches-to-export-selected-entity-assets"></a>Uso de soluciones y revisiones segmentadas para exportar los recursos de entidad seleccionados

Para obtener un mayor control sobre lo que distribuye en las soluciones y revisiones de soluciones, use la segmentación de soluciones. Con la segmentación de soluciones, puede exportar soluciones con los recursos de entidad seleccionados, como campos de entidad, formularios y vistas, en lugar de entidades completas con todos los recursos. Para crear las soluciones y revisiones segmentadas, puede usar la interfaz de usuario de soluciones, sin escribir código.  
  
 Además de tener un mayor control sobre lo que hay en una solución, podrá controlar lo que incluye una revisión. Puede crear una revisión para una solución primaria y exportarla como una actualización secundaria a la solución base. Al clonar una solución, el sistema acumula todas las revisiones relacionadas en la solución base y crea una versión.  
  
 Cuando trabaje con revisiones y soluciones clonadas, tenga en cuenta la siguiente información:  
  
-   Una revisión representa una actualización secundaria incremental a la solución primaria. Una revisión puede agregar o actualizar componentes y recursos de la solución primaria cuando se instala en el sistema de destino, pero no puede eliminarlos de dicha solución.  
  
-   Una revisión solo puede tener una solución primaria, pero una solución primaria puede tener una o varias revisiones.  
  
-   Una revisión se crea para soluciones no administradas. No se pueden crear revisiones para soluciones administradas.  
  
-   Al exportar una revisión a un sistema de destino, debe exportarla como una revisión administrada. No use revisiones no administradas en entornos de producción.  
  
-   Para instalar una revisión, la solución primaria debe existir en el sistema de destino.  
  
-   Puede eliminar o actualizar una revisión.  
  
-   Si elimina una solución primaria, también se eliminan todas las revisiones secundarias. El sistema le proporciona un mensaje de advertencia de que no puede deshacer la operación de eliminación. La eliminación se realiza en una única transacción. Si una de las revisiones o la solución primaria no se pueden eliminar, se revierte toda la transacción.  
  
-   Después de haber creado la primera revisión para una solución primaria, la solución se bloquea y no se pueden realizar cambios en esta solución ni exportarla. Sin embargo, si elimina todas sus revisiones secundarias, la solución primaria se desbloquea.  
  
-   Al clonar una solución base, todas las revisiones secundarias se acumulan en esta solución base y se convierte en una nueva versión. Puede agregar, editar o eliminar componentes y recursos de la solución clonada.  
  
-   Una solución clonada representa un reemplazo de la solución base cuando se instala en el sistema de destino como una solución administrada. Normalmente, usará una solución clonada para enviar una actualización principal a la solución anterior.  
  
## <a name="understanding-version-numbers-for-cloned-solutions-and-patches"></a>Descripción de los números de versión de soluciones clonadas y revisiones  
 La versión de una solución tiene el siguiente formato: primaria.secundaria.compilación.revisión. Una revisión debe tener un número de compilación o revisión mayor que la solución primaria. No puede tener una versión principal o secundaria mayor. Por ejemplo, en una solución base con la versión 3.1.5.7, una revisión podría ser una versión 3.1.5.8 o 3.1.7.0, pero no 3.2.0.0. En una solución clonada, el número de versión debe ser mayor o igual que el número de versión de la solución base. Por ejemplo, en una solución base con la versión 3.1.5.7, una solución clonada podría ser una versión 3.2.0.0 o 3.1.5.7. En la interfaz de usuario, solo puede establecer los valores de versión principal y secundaria para una solución clonada, y los valores de compilación o revisión de una revisión.  
  
## <a name="create-a-segmented-solution-with-the-entity-assets-you-want"></a>Creación de una solución segmentada con los recursos de entidad que desee  
 Para crear una solución segmentada, comience con la creación de una solución no administrada y la incorporación de los recursos existentes. Puede agregar varias entidades personalizadas o del sistema y, para cada entidad, elegir los recursos que se van a incluir en la solución. El programa de instalación de tipo asistente le lleva paso a paso por el proceso de agregar recursos de entidad.  
  
1. Vaya a **[Configuración](../model-driven-apps/advanced-navigation.md#settings)** > **Soluciones**.   
  
2.  Seleccione **Nueva** y cree una solución. Especifique información en los campos necesarios. Seleccione **Guardar y cerrar**.  
  
3.  Abra la solución que acaba de crear. En la lista desplegable **Agregar existente**, seleccione **Entidad**.  
  
4.  En el cuadro de diálogo **Seleccionar componentes de la solución**, seleccione una o varias entidades que quiera agregar a la solución. Seleccione **Aceptar**.  
  
5.  Se abre el asistente. Siga el asistente para agregar a la solución recursos de cada entidad seleccionada.  
  
6.  Seleccione **Publicar** para que los cambios surtan efecto.  
  
 En las ilustraciones siguientes se proporciona un ejemplo de creación de una solución segmentada mediante la elección de recursos de las entidades `Account`, `Case`, y `Contact`.  
  
 Para comenzar, elija el componente **Entidad**.  
  
 ![Agregar los recursos existentes.](media/solution-segmentation-add-existing-resources-admin.png "Add existing resources.")  
  
 A continuación, seleccione los componentes de la solución.  
  
 ![Seleccionar los componentes de la solución.](media/solution-segmentation-select-components-admin.png "Select solution's components.")  
  
 Siga los pasos del asistente. En el paso 1, comenzando en orden alfabético, seleccione los recursos de la primera entidad, que es `Account`, como se muestra aquí.  
  
 ![Iniciar el asistente.](media/solution-segmentation-wizard-starts-admin.png "Start the wizard.")  
  
 Abra la pestaña **Campos** y seleccione el campo **Número de cuenta**.  
  
 ![Seleccionar los recursos de la entidad Account.](media/solution-segmentation-select-account-assets-admin.png "Select the Account entity assets.")  
  
 En el paso 2, en la entidad **Case**, agregue todos los recursos.  
  
 ![Seleccionar los recursos de la entidad Case.](media/solution-segmentation-select-case-assets-admin.png "Select the Case entity assets.")  
  
 En el paso 3, agregue el campo **Aniversario** para la entidad **Contact**.  
  
 ![Seleccionar los recursos de la entidad Contact.](media/solution-segmentation-select-contact-assets-admin.png "Select the Contact entity assets.")  
  
 Como resultado, la solución segmentada que se crea contiene tres entidades `Account`, `Case` y `Contact`. Cada entidad contiene solo los recursos que se han elegido.  
  
 ![Solución con entidades.](media/solution-segmentation-solution-entities-admin.png "Solution with entities.")  
  
## <a name="create-a-solution-patch"></a>Creación de una revisión de la solución  
 Una revisión contiene cambios en la solución primaria, como agregar o editar componentes y recursos. No tiene que incluir los componentes de la solución primaria a no ser que tenga pensado editarlos.  
  
 #### <a name="create-a-patch-for-an-unmanaged-solution"></a>Creación de una revisión para una solución no administrada  
  
1. Vaya a **[Configuración](../model-driven-apps/advanced-navigation.md#settings)** > **Soluciones**.   
  
2.  En la lista, seleccione una solución no administrada para la que crear una revisión. Seleccione **Clonar una revisión**. El cuadro de diálogo que se abre contiene el nombre y el número de versión de la revisión de la solución base. Seleccione **Guardar**.  
  
3.  En la cuadrícula, busque y abra la revisión recién creada. Al igual que con la solución base, siga el asistente para agregar los componentes y recursos deseados.  
  
4.  Seleccione **Publicar** para que los cambios surtan efecto.  
  
 En las ilustraciones siguientes se proporciona un ejemplo de creación de una revisión para una solución existente. Para comenzar, seleccione **Clonar una revisión** (en la vista comprimida, el icono **Clonar una revisión** se representa como dos pequeños cuadrados, como se muestra a continuación).  
  
 ![Icono Clonar una revisión.](media/solution-segmentation-click-patch-icon-admin.png "Clone a patch icon.")  
  
 En el cuadro de diálogo **Clonar para revisar**, puede ver que el número de versión de la revisión se basa en el número de versión de la solución primaria, pero el número de compilación se incrementa en uno. Cada revisión sucesiva tiene un número de compilación o revisión mayor que la revisión anterior.  
  
 ![Usar el cuadro de diálogo Clonar para revisar.](media/solution-segmentation-clone-patch-dialog-admin.png "Use Clone To Patch dialog.")  
  
 En la captura de pantalla siguiente se muestra la solución base **SegmentedSolutionExample**, versión **1.0.1.0** y la revisión **SegmentedSolutionExample_Patch**, versión **1.0.2.0**.  
  
 ![Una cuadrícula con soluciones y revisiones.](media/solution-segmentation-solution-patch-grid-admin.png "A grid with solutions and patches.")  
  
 En la revisión se ha agregado una nueva entidad personalizada llamada `Book` y se han incluido todos los recursos de la entidad `Book` en la revisión.  
  
 ![Agregar la entidad personalizada en la revisión.](media/solution-segmentation-add-book-patch-admin.png "Add custom entity in the patch.")  
  
## <a name="clone-a-solution"></a>Clonación de una solución  
 Al clonar una solución no administrada, todas las revisiones relacionadas con esta solución se acumulan en la versión recién creada de la solución original.  
  
1. Vaya a **[Configuración](../model-driven-apps/advanced-navigation.md#settings)** > **Soluciones**.   
  
2.  En la lista, seleccione una solución no administrada que quiera clonar. Seleccione **Clonar solución**. El cuadro de diálogo que se abre contiene el nombre y el nuevo número de versión de la solución base. Seleccione **Guardar**.  
  
3.  Seleccione **Publicar** para que los cambios surtan efecto.  
  
 Continuando con el ejemplo, verá el cuadro de diálogo **Clonar para solucionar** que muestra el nuevo número de versión de la solución.  
  
 ![Usar el cuadro de diálogo Clonar para solucionar.](media/solution-segmentation-clone-solution-dialog-admin.png "Use Clone To Solution dialog.")  
  
 Después de la clonación, la nueva versión de la solución contiene tres entidades originales (`Account`, `Case`, y `Contact`), y la entidad personalizada denominada `Book` que se agregó en la revisión. Cada entidad contiene solo los recursos que se han agregado en el ejemplo.  
  
 ![Una solución clonada con la revisión acumulada.](media/solution-segmentation-solution-rolled-up-patch-admin.png "A cloned solution with rolled up patch.")  
  
## <a name="next-steps"></a>Pasos siguientes  
 [Introducción a las soluciones](solutions-overview.md) [Creación de revisiones para simplificar las actualizaciones de soluciones]

