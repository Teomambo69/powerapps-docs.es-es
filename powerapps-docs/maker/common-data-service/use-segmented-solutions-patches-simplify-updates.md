---
title: Use soluciones y revisiones divididas en segmentos para simplificar las actualizaciones de la solución con PowerApps | MicrosoftDocs
description: Aprenda a usar la segmentación de la solución para actualizar sus soluciones
ms.custom: ''
ms.date: 06/18/2018
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
ms.assetid: 5c05f683-e1bd-4885-be23-b6973128773f
caps.latest.revision: 15
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8f2b890766c6643da0a5363f49ef9b5c233b0b0b
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2703135"
---
# <a name="use-segmented-solutions-and-patches-to-export-selected-entity-assets"></a>Usar soluciones y revisiones segmentadas para exportar activos seleccionados de la entidad

Para conseguir un control más estrecho sobre lo que distribuye en soluciones y revisiones de solución, utilice segmentación de la solución. Con la segmentación de soluciones, puede exportar soluciones con activos seleccionados de la entidad, como campos de la entidad, formularios y vistas, en lugar de entidades completas con todos los activos. Para crear soluciones y revisiones segmentadas, puede usar la interfaz de usuario de las soluciones sin escribir código.  
  
 Además de tener más control sobre qué contiene una solución, podrá controlar qué incluye una revisión. Puede crear una revisión para una solución primaria y exportarla como actualización de menor importancia en la solución base. Cuando se clona una solución, el sistema resume todas las revisiones relacionadas en la solución base y crea una nueva versión.  
  
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
  
## <a name="create-a-segmented-solution-with-the-entity-assets-you-want"></a>Crear una solución segmentada con los activos de entidad que desee  
 Para crear una solución segmentada, comience con la creación de una solución no administrada y agregue los recursos existentes. Puede agregar varias entidades del sistema o personalizadas y, para cada entidad, elija los activos que desea incluir en la solución. El programa de instalación de tipo asistente le orienta paso a paso en el proceso de agregar activos de entidad.  
  
1. Vaya a **[Configuración](../model-driven-apps/advanced-navigation.md#settings)** > **Soluciones**.   
  
2.  Seleccione **Nueva** para crear una solución. Especifique la información en los campos obligatorios. Seleccione **Guardar y cerrar**.  
  
3.  Abra la solución que acaba de crear. En la lista desplegable **Agregar existente**, seleccione **Entidad**.  
  
4.  En el cuadro de diálogo **Seleccionar componentes de la solución**, seleccione una o varias entidades que desea agregar a la solución. Seleccione **Aceptar**.  
  
5.  Se abrirá el asistente. Siga las indicaciones del asistente para agregar activos para cada entidad seleccionada a la solución.  
  
6.  Seleccione **Publicar** para que los cambios surtan efecto.  
  
 Las ilustraciones siguientes proporcionan un ejemplo de crear una solución segmentada eligiendo activos de entidad desde las entidades `Account`, `Case` y `Contact`.  
  
 Comience eligiendo el componente **Entidad**.  

 > [!div class="mx-imgBorder"] 
 > ![Agregar recursos existentes](media/solution-segmentation-add-existing-resources-admin.png "Agregar recursos existentes")  
  
 A continuación, seleccione los componentes de la solución.  
  
 ![Seleccionar componentes de la solución.](media/solution-segmentation-select-components-admin.png "Seleccionar componentes de la solución.")  
  
 Siga el asistente. En el paso 1, empiece en orden alfabético, seleccione los activos para la primera entidad, entidad `Account`, como se indica aquí.  
  
 ![Inicie el asistente.](media/solution-segmentation-wizard-starts-admin.png "Inicie el asistente.")  
  
 Abra la pestaña **Campos** y seleccione el campo **Número de cuenta**.  
  
 ![Seleccione los activos de la entidad Cuenta.](media/solution-segmentation-select-account-assets-admin.png "Seleccione los activos de la entidad Cuenta.")  
  
 En el paso 2, para la entidad **Caso**, agregue todos los activos.  
  
 ![Seleccione los activos de la entidad Caso.](media/solution-segmentation-select-case-assets-admin.png "Seleccione los activos de la entidad Caso.")  
  
 En el paso 3, agregue el campo **Aniversario** para la entidad **Contacto**.  
  
 ![Seleccione los activos de la entidad Contacto.](media/solution-segmentation-select-contact-assets-admin.png "Seleccione los activos de la entidad Contacto.")  
  
 Como resultado, la solución segmentada que se crea contiene tres entidades, `Account`, `Case`, y `Contact`. Cada entidad solo contiene los activos que fueron elegidos.  
  
 > [!div class="mx-imgBorder"] 
 > ![Solución con entidades.](media/solution-segmentation-solution-entities-admin.png "Solución con entidades.")  
  
## <a name="create-a-solution-patch"></a>Crear una revisión de la solución  
 Una revisión contiene cambios en la solución primaria, como agregar o editar componentes y activos. No es necesario incluir los componentes primarios a menos que prevea modificarlos.  
  
 #### <a name="create-a-patch-for-an-unmanaged-solution"></a>Crear una revisión de una solución no administrada  
  
1. Vaya a **[Configuración](../model-driven-apps/advanced-navigation.md#settings)** > **Soluciones**.   
  
2.  En la lista, seleccione una solución no administrada para la que crear una revisión. Seleccione **Clonar una revisión**. El cuadro de diálogo que se abre contiene el nombre de la solución base y el número de versión de la revisión. Seleccione **Guardar**.  
  
3.  En la cuadrícula, busque y abra la revisión recién creada. Al igual con la solución base, siga las indicaciones del asistente para agregar los componentes y los activos que desee.  
  
4.  Seleccione **Publicar** para que los cambios surtan efecto.  
  
 Las ilustraciones siguientes proporcionan un ejemplo de crear una revisión para una solución existente. Empiece seleccionando **Clonar una revisión** (en la vista comprimida, el icono **Clonar una revisión** se muestra como dos cuadrados pequeños, como se indica a continuación).  
  
 > [!div class="mx-imgBorder"] 
 > ![Clonar un icono de revisión.](media/solution-segmentation-click-patch-icon-admin.png "Clonar un icono de revisión.")  
  
 En el cuadro de diálogo **Clonar para revisar** se ve que el número de versión de la revisión se basa en el número de versión de la solución primaria, pero el número de compilación se incrementa en uno. Cada revisión posterior tiene un número de compilación o de revisión más alto que la revisión precedente.  
  
 ![Usar diálogo Clonar para revisar.](media/solution-segmentation-clone-patch-dialog-admin.png "Usar diálogo Clonar para revisar.")  
  
 La captura de pantalla siguiente muestra la solución base **SegmentedSolutionExample**, versión **1.0.1.0** y revisión **SegmentedSolutionExample_Patch**, versión **1.0.2.0**.  
  
 > [!div class="mx-imgBorder"] 
 > ![Una cuadrícula con soluciones y revisiones.](media/solution-segmentation-solution-patch-grid-admin.png "Una cuadrícula con soluciones y revisiones.")  
  
 En la revisión agregamos una nueva entidad personalizada llamada `Book`, e incluimos todos los activos de la entidad `Book` en la revisión.  
  
 ![Agregar entidad personalizada en la revisión.](media/solution-segmentation-add-book-patch-admin.png "Agregar entidad personalizada en la revisión.")  
  
## <a name="clone-a-solution"></a>Clonar una solución  
 Cuando se clona una solución no administrada, todas las revisiones relacionadas con esta solución se resumen en la versión recién creada de la solución original.  
  
1. Vaya a **[Configuración](../model-driven-apps/advanced-navigation.md#settings)** > **Soluciones**.   
  
2.  En la lista, seleccione una solución no administrada que desea clonar. Seleccione **Clonar solución**. El cuadro de diálogo que se abre contiene el nombre de la solución base y el nuevo número de versión. Seleccione **Guardar**.  
  
3.  Seleccione **Publicar** para que los cambios surtan efecto.  
  
 Continuando con el ejemplo, verá el cuadro de diálogo **Clonar para solucionar** que indica el nuevo número de versión de la solución.  
  
 ![Usar diálogo Clonar para solucionar.](media/solution-segmentation-clone-solution-dialog-admin.png "Usar diálogo Clonar para solucionar.")  
  
 Después de clonar, la nueva versión de la solución contiene tres entidades originales (`Account`, `Case`, y `Contact`), y la entidad personalizada llamada `Book` que se agregó en su revisión. Cada entidad solo contiene los activos que se agregaron en el ejemplo.  
  
 > [!div class="mx-imgBorder"] 
 > ![Solución clonada con revisión resumida.](media/solution-segmentation-solution-rolled-up-patch-admin.png "Solución clonada con revisión resumida.")  
  
## <a name="next-steps"></a>Pasos siguientes  
 [Información general de las soluciones](solutions-overview.md) [Crear revisiones para simplificar las actualizaciones de la solución]

