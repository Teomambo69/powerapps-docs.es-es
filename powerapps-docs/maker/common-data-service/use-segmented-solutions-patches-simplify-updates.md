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
ms.openlocfilehash: 16730151eb6d7ec45fad7a6803eed3e76f68f8d4
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "3109520"
---
# <a name="use-segmented-solutions"></a>Usar soluciones segmentadas 

Utilice la segmentación de la solución para que solo incluya componentes de entidad que se actualicen cuando distribuya actualizaciones de la solución. Con la segmentación de soluciones, puede exportar actualizaciones de solución con activos seleccionados de la entidad, como campos de la entidad, formularios y vistas, en lugar de entidades completas con todos los activos. <!-- Depending on the complexity of your app, segmentation of the solution can be as simple as everything in a single solution to segmenting by component type, such as entities in one solution, canvas apps in another, and plugins in a third. --> Para crear una solución segmentada use el área **Soluciones** en Power Apps.  

Puede segmentar una solución cuando selecciona entre las siguientes opciones para agregar una entidad existente a la solución: 
- Incluir ningún componente. Cuando no selecciona ningún componente o metadato, la información mínima de la entidad se agrega a la solución. Por lo tanto, aparte del nombre descriptivo, no se incluirán los atributos de la entidad (metadatos) o los componentes.   
- **Seleccionar componentes**. Puede segmentar su solución seleccionando de forma individual cada componente asociado con la entidad, como campos, relaciones, reglas de negocios, vistas, formularios y gráficos. Use esta opción para seleccionar solo los componentes que se han agregado o cambiado con la entidad, como un nuevo campo personalizado o agregar un formulario.  
- **Incluir metadatos de la entidad**. Esta opción no incluye componentes, como entidades relacionadas, pero incluye *todos* los metadatos asociados con la entidad. Los metadatos incluyen los atributos de la entidad, como auditoría, detección de duplicados o seguimiento de cambios. 
- **Incluir todos los componentes**. Esta opción incluye todos los componentes *y* metadatos asociados con la entidad. Puede incluir otras entidades o componentes de la entidad, como flujos de procesos de negocio, informes, conexiones y colas. Solo debe usar esta opción cuando esté distribuyendo una entidad no administrada que no existe en el entorno de destino. 

    > [!WARNING]
    > No agregue componentes a su solución que no pretendía. Cuando su actualización se importa al entorno de destino, una solución con componentes no deseados puede causar un comportamiento inesperado a los componentes existentes que ahora se encuentran debajo de la capa que introdujo con la actualización de su solución. Por ejemplo, si agrega una vista para una entidad que no está actualizada y la vista en la capa existente tiene personalizaciones, las personalizaciones existentes pueden quedar inactivas. Para obtener más información, consulte [Capas de solución](solution-layers.md).

<!-- The below was from Per but I don't think it fits in this topic that is only about solution segmentation with entities. 
Similar to the planning that goes into how you model the data that goes into your app, planning for segmentation should be considered before you distribute your solution. Segmenting solutions from a single solution into multiple solutions a month or two years after the initial app has been built can be complex and is prone to cause issues.  -->

## <a name="create-a-segmented-solution-with-entity-assets"></a>Crear una solución segmentada con los activos de entidad 
 Para crear una solución segmentada, comience con la creación de una solución no administrada y agregue solo los componentes que ha actualizado. El programa de instalación de tipo asistente le orienta paso a paso en el proceso de agregar activos de entidad. 

Por ejemplo, imagine que ha creado una nueva entidad personalizada que no existe en ningún otro entorno denominada *Entidad personalizada* y también agregó un nuevo campo llamado *los diez mejores* para la entidad de cuenta. Para crear una solución segmentada, siga estos pasos. 
  
1. Vaya al portal Power Apps y luego seleccione **Soluciones**.  
  
2.  Seleccione **Nueva solución** y cree una solución. Especifique la información en los campos obligatorios. Seleccione **Crear**.  
  
3.  Abra la solución que ha creado. En la barra de comandos, seleccione **Agregar existentes** y, después, **Entidad**.  
  
4.  En el panel **Agregar entidades existentes**, seleccione una o varias entidades que desea agregar a la solución. Por ejemplo, seleccione **Cuenta** y **Entidad personalizada**. Seleccione **Siguiente**.  

5.  En el panel **Seleccionar entidades**, puede elegir entre los activos a incluir: 
    - **Incluir todos los componentes**. Esta opción incluye todos los componentes *y* metadatos asociados con la entidad. Puede incluir otras entidades o componentes de la entidad, como flujos de procesos de negocio, informes, conexiones y colas. 
    - **Incluir metadatos de la entidad**. Esta opción incluye *solo* los metadatos asociados con la entidad. Los metadatos incluyen los atributos de la entidad, como auditoría, detección de duplicados o seguimiento de cambios. 
    - **Seleccionar componentes**. Esta opción le permite seleccionar individualmente cada componente asociado con la entidad, como campos, relaciones, reglas de negocios, vistas, formularios y gráficos. 
    - No incluya ningún componente. 

      Para este ejemplo, como *Entidad personalizada* nunca se ha importado al entorno de destino, junto a **Entidad personalizada** seleccione **Incluir todos los componentes**. En **Cuenta**, elija **Seleccionar componentes**.  
      > [!div class="mx-imgBorder"] 
      > ![Agregar entidades existentes](media/add-existing-entities1.png)
  
6.  Ya que solo el campo personalizado *los diez mejores* es nuevo para la entidad de cuenta, seleccione **Los diez mejores** y luego seleccione **Agregar**.  
     > [!div class="mx-imgBorder"] 
     > ![Seleccionar de componentes de la entidad](media/add-existing-entities2.png)

7. Seleccione **Agregar** para agregar los componentes a la solución. 

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
  
  
### <a name="see-also"></a>Vea también  
 [Información general de las soluciones](solutions-overview.md)


