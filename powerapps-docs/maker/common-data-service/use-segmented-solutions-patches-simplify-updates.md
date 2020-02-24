---
title: Utilizar soluciones segmentadas con Power Apps | MicrosoftDocs
description: Aprenda a usar la segmentación de la solución para actualizar sus soluciones
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
ms.assetid: 5c05f683-e1bd-4885-be23-b6973128773f
caps.latest.revision: 15
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d13eafa6858a6eec86de2db08504575c7fab9acd
ms.sourcegitcommit: 60a721432b3fa2abd14ccb3bd16a6b34e13ada85
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2020
ms.locfileid: "3026389"
---
# <a name="use-segmented-solutions"></a>Usar soluciones segmentadas 

Para conseguir un control más estrecho sobre lo que distribuye en soluciones y revisiones de solución, utilice segmentación de la solución. Dependiendo de la complejidad de su aplicación, la segmentación de la solución puede ser tan simple como todo en una solución única para segmentar por tipo de componente, como entidades de una solución, aplicaciones de lienzo en otra y complementos en una tercera. Para crear soluciones segmentadas, puede usar el área de soluciones de Power Apps sin escribir código.  

Hay tres formas principales de segmentar soluciones: 
- Cree soluciones segmentadas a medida que crea su aplicación. Para ello, agregue componentes específicos para controlar lo que entra en la solución. Más información: [Crear una solución segmentada con activos de entidad](#create-a-segmented-solution-with-entity-assets)
- Cree soluciones segmentadas para crear y lanzar actualizaciones menores a una solución. Para ello, clone una revisión. Más información: [Crear una revisión de la solución](#create-a-solution-patch)
- Cree soluciones segmentadas para crear y lanzar actualizaciones principales a una solución. Para ello, clone la solución. Más información: [Clonar una solución](#clone-a-solution)

## <a name="when-to-plan-for-segmentation"></a>Cuándo planificar la segmentación 
Al igual que la planificación que se aplica al modelado de los datos que se utilizan en la aplicación, se debe considerar la planificación de la segmentación antes de distribuir la solución. La segmentación de soluciones de una sola solución a múltiples soluciones un mes o dos años después de que se haya creado la aplicación inicial puede ser compleja y es propensa a causar problemas.  

## <a name="solutions-as-patches"></a>Soluciones como revisiones
Con la segmentación de soluciones, puede exportar revisiones de la solución con activos seleccionados de la entidad, como campos de la entidad, formularios y vistas, en lugar de entidades completas con todos los activos. 

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
  
### <a name="understanding-version-numbers-for-cloned-solutions-and-patches"></a>Descripción de los números de versión para soluciones clonadas y revisiones  
 La versión de una solución tiene el siguiente formato: primaria.secundaria.compilación.revisión. Una revisión debe tener un número de compilación o de revisión más alto que la solución primaria. No puede tener una versión importante o de menor importancia más alta. Por ejemplo, para una versión de solución base 3.1.5.7, una revisión podría ser una versión 3.1.5.8 o versión 3.1.7.0, pero no versión 3.2.0.0. Una solución clonada debe tener el número de versión mayor o igual que el número de versión de la solución base. Por ejemplo, para una versión de solución base 3.1.5.7, una solución clonada podría ser una versión 3.2.0.0 o versión 3.1.5.7. En la interfaz de usuario, solo puede establecer los valores de versión importante y secundaria para una solución clonada, y los valores de compilación o de revisiones para una revisión.  
  
## <a name="create-a-segmented-solution-with-entity-assets"></a>Crear una solución segmentada con los activos de entidad 
 Para crear una solución segmentada, comience con la creación de una solución no administrada y agregue los recursos existentes. Puede agregar varias entidades del sistema o personalizadas y, para cada entidad, elija los activos que desea incluir en la solución. El programa de instalación de tipo asistente le orienta paso a paso en el proceso de agregar activos de entidad.  
  
1. Vaya al portal Power Apps y luego seleccione **Soluciones**.  
  
2.  Seleccione **Nueva solución** y cree una solución. Especifique la información en los campos obligatorios. Seleccione **Crear**.  
  
3.  Abra la solución que ha creado. En la barra de comandos, seleccione **Agregar existentes** y, después, **Entidad**.  
  
4.  En el panel **Agregar entidades existentes**, seleccione una o varias entidades que desea agregar a la solución, como una entidad estándar como contacto, y una entidad personalizada. Seleccione **Siguiente**.  
    > [!div class="mx-imgBorder"] 
    > ![Agregar entidades existentes](media/add-existing-entities1.png)

5.  En el panel **Seleccionar entidades**, puede elegir entre los activos a incluir. 
    - **Incluir todos los componentes**. Esta opción incluye todos los componentes *y* metadatos asociados con la entidad. Puede incluir otras entidades o componentes de la entidad, como flujos de procesos de negocio, informes, conexiones y colas. 
    - **Incluir metadatos de la entidad**. Esta opción incluye *solo* los metadatos asociados con la entidad. Los metadatos incluyen los atributos de la entidad, como auditoría, detección de duplicados o seguimiento de cambios. 
    - **Seleccionar componentes**. Esta opción le permite seleccionar individualmente cada componente asociado con la entidad, como campos, relaciones, reglas de negocios, vistas, formularios y gráficos. 
      > [!div class="mx-imgBorder"] 
      > ![Seleccionar de componentes de la entidad](media/add-existing-entities2.png)
  
6.  Seleccione **Agregar**.  

### <a name="create-a-segmented-solution-using-solution-explorer"></a>Crear una solución segmentada usando el explorador de soluciones  
Las ilustraciones siguientes proporcionan un ejemplo de crear una solución segmentada eligiendo activos de entidad desde las entidades `Account`, `Case` y `Contact`.  

> [!NOTE]
> La entidad del caso se incluye con algunas aplicaciones de Dynamics 365, como Dynamics 365 Customer Service. 
  
Comience abriendo una solución no administrada que creó. Elija el componente **Entidad**.  

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
  
### <a name="create-a-patch-for-an-unmanaged-solution"></a>Crear una revisión de una solución no administrada  
  
1. Vaya al portal Power Apps y luego seleccione **Soluciones**.   
  
2. En la lista de soluciones, seleccione una solución no administrada para la que crear una revisión. En la barra de comandos, seleccione **Clonar** y, después, **Clonar una revisión**. El panel derecho que se abre contiene el nombre de la solución base y el número de versión de la revisión. Seleccione **Guardar**.  
   > [!div class="mx-imgBorder"] 
   > <img src="media/clone-a-patch.png" alt="Clone a patch" height="735" width="408">
 
3. En la lista de soluciones, busque y abra la revisión recién creada. Observe que el nombre único de la solución se ha agregado con _Patch_*hexnumber*. Al igual con la solución base, agregue los componentes y los activos que desee.  
  
#### <a name="create-a-patch-using-solution-explorer"></a>Crear una revisión usando el explorador de soluciones
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
  
  
### <a name="next-steps"></a>Pasos siguientes  
 [Información general de las soluciones](solutions-overview.md)


