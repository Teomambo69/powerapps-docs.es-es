---
title: Crear soluciones segmentadas con Power Apps | MicrosoftDocs
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
ms.openlocfilehash: 50e9e467727ab637d46dbc82ad0a313b5fe817db
ms.sourcegitcommit: c6906775005aec98973b1f5c3dbe5924aff6d26e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "3341587"
---
# <a name="create-segmented-solutions"></a>Crear soluciones segmentadas 
Utilice la segmentación de la solución para que solo incluya componentes de entidad que se actualicen cuando distribuya actualizaciones de la solución. Con la segmentación de soluciones, puede exportar actualizaciones de solución con activos seleccionados de la entidad, como campos de la entidad, formularios y vistas, en lugar de entidades completas con todos los activos. Para crear una solución segmentada use el área **Soluciones** en Power Apps. Más información: [Usar soluciones segmentadas](/power-platform/alm/segmented-solutions-alm)

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


