---
title: Establecimiento de propiedades administradas en metadatos de Common Data Service | MicrosoftDocs
description: Aprenda cómo establecer propiedades administradas para elementos de metadatos en una solución
ms.custom: ''
ms.date: 03/03/2020
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
ms.assetid: edaa7d4a-a95f-4d66-a9d9-2ad6051332f7
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0f75c9c38b3fbd74f330de5e80a2c0f7df8d6e13
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "3124977"
---
# <a name="set-managed-properties-in-common-data-service-metadata"></a>Establecer propiedades administradas en metadatos de Common Data Service 
Puede controlar cuáles componentes de la solución administrada se pueden personalizar mediante el uso de propiedades administradas. Los ISV deberían permitir la personalización para los componentes de la solución cuando tenga sentido. Esto permite que las organizaciones personalicen la solución según sus requisitos únicos. Limite o elimine la personalización de los componentes críticos de la solución que ofrecen la funcionalidad básica para que pueda respaldarla y mantenerla de manera previsible. Para la mayoría de los entornos de desarrollo que no son ISV, recomendamos que no permita la personalización para sus componentes de solución administrada. 

Las propiedades administradas se proporcionan para proteger la solución de modificaciones que pueden causar problemas. Las propiedades administradas no proporcionan administración de derechos digitales (DRM), ni capacidades para otorgar la licencia de la solución o controlar quién puede instalarla.

Aplica propiedades administradas cuando la solución no se administra en la capa no administrada de su entorno de desarrollo. Las propiedades administradas se harán efectivas una vez que empaquete la solución administrada y la instale en un entorno diferente. Una vez instalada la solución administrada se importa, las propiedades administradas no se pueden actualizar excepto mediante una actualización de la solución realizada por el editor original. 

La mayoría de los componentes de la solución tienen un elemento de menú **Propiedades administradas** disponible al ver una lista de los componentes de la solución. Cuando importa el solución administrada que contiene los componentes, puede ver pero no cambiar sus propiedades administradas.

## <a name="view-and-edit-entity-managed-properties"></a>Ver y editar las propiedades administradas de la entidad
1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) y seleccione **Soluciones** en el panel izquierdo. 
2.  Abra la solución que desee. 
3.  En la lista de comonentes de la solución, seleccione **...** junto a la entidad de la que desea ver las propiedades administradas y luego seleccione **Propiedades administradas**. 

    > [!div class="mx-imgBorder"] 
    > ![Comando Propiedades administradas de entidad](media/entity-managed-properties.png "Comando Propiedades administradas de entidad")

    Se muestra la página de propiedades administradas. 

    > [!div class="mx-imgBorder"] 
    > <img src="media/managed-properties-dialog.png" alt="Managed properties pane" height="572" width="300">

Las entidades tienen más propiedades administradas que ningún otro tipo de componente de la solución. Si la entidad es personalizable, puede definir las siguientes opciones:  

|Opción|Descripción|
|--|--|
|**Permitir personalizaciones** |Controla el resto de opciones. Si esta opción es `False`, no se aplicará ninguno de los demás valores. Si es `True`, puede especificar las demás opciones de personalización. Cuando `False`, es equivalente a establecer el resto de opciones en falso.|
|**Se puede modificar el nombre para mostrar**|Si el nombre para mostrar de la entidad puede modificarse.|
|**Se puede cambiar propiedades adicionales** |Se aplica a cualquier elemento no cubierto por las otras opciones.|
|**Se pueden crear nuevos formularios**|Si se pueden crear nuevos formularios para la entidad.|
|**Se pueden crear nuevos gráficos**|Si se pueden crear nuevos gráficos para la entidad.|
|**Se pueden crear vistas nuevas** |Si se pueden crear nuevas vistas para la entidad.|
|**Puede cambiar la relación jerárquica**|Si los valores de las relaciones jerárquicas se pueden cambiar. Más información: [Definir y consultar datos relacionados jerárquicamente](define-query-hierarchical-data.md)|
|**Puede habilitarse el seguimiento de cambios** |Si la propiedad **Seguimiento de cambios** de la entidad puede cambiar.|
|**Se puede habilitar la sincronización con el índice de búsqueda externo** |Si la entidad se puede configurar para habilitar la búsqueda por relevancia. Más información: [Configurar la búsqueda por relevancia para mejorar resultados de búsquedas y rendimiento](/dynamics365/customer-engagement/admin/configure-relevance-search-organization) |

## <a name="view-and-edit-field-managed-properties"></a>Ver y editar las propiedades administradas del campo
Junto a un campo personalizado en una solución, seleccione **...** y luego seleccione **Propiedades administradas**.

Esto abrirá el panel **Propiedades administradas**.
> [!div class="mx-imgBorder"] 
> <img src="media/field-managed-prop.png" alt="Field managed properties" height="525" width="295">

La opción **Permitir personalizaciones** controla el resto de opciones. Si esta opción está deshabilitada, no se aplicará ninguno de los demás valores. Cuando está habilitada, puede especificar las demás opciones de personalización.  
  
Si el campo es personalizable, puede habilitar las siguientes opciones.  
  
- **Se puede modificar el nombre para mostrar**
- **Se puede cambiar propiedades adicionales**: esta propiedad controla cualquier otra personalización que no tiene una propiedad administrada específica. 
- **Se pueden crear nuevos formularios** 
- **Se pueden crear nuevos gráficos** 
- **Se pueden crear vistas nuevas** 
- **Puede cambiar la relación jerárquica** 
- **Puede habilitarse el seguimiento de cambios** 
- **Se puede habilitar la sincronización con el índice de búsqueda externo**

Deshabilitar todas las opciones individuales es equivalente a deshabilitar **Permitir personalizaciones**.  

Aplique sus elecciones y selecciona **Hecho** para cerrar el panel.

> [!NOTE]
> Si este campo es un campo de **Fecha y hora**, habrá disponible una propiedad adicional de **Puede cambiar el comportamiento de fecha y hora**. Más información: [Comportamiento y formato del campo de fecha y hora](behavior-format-date-time-field.md) 

Consulte [Crear y editar campos para Common Data Service usando el explorador de soluciones de Power Apps](create-edit-field-solution-explorer.md) para obtener información sobre cómo editar campos.

## <a name="view-and-edit-other-component-managed-properties"></a>Ver y editar propiedades administradas de otros componentes
Puede ver y editar propiedades administradas para muchos otros componentes de la solución, como un recurso web, procesos, gráficos o paneles. Junto al componente de una solución seleccione **...** y luego seleccione **Propiedades administradas**. 

## <a name="view-and-edit-relationship-managed-properties"></a>Ver y editar las propiedades administradas de relaciones
Mientras visualiza relaciones de entidad en el [explorador de soluciones](../model-driven-apps/advanced-navigation.md#solution-explorer), seleccione una relación de una solución no administrada y elija **Más acciones** > **Propiedades administradas** en la barra de menús.
  
Con las relaciones, la única propiedad administrada es **Se puede personalizar**. Este valor único controla todos los cambios que se pueden realizar en la relación entre entidades. 

### <a name="see-also"></a>Vea también

[Exportar soluciones](export-solutions.md) <br />
[Información general de las soluciones](solutions-overview.md)

