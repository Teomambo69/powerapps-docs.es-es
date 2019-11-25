---
title: Establecimiento de propiedades administradas en metadatos de Common Data Service | MicrosoftDocs
description: Aprenda cómo establecer propiedades administradas para elementos de metadatos en una solución
ms.custom: ''
ms.date: 05/30/2018
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
ms.openlocfilehash: c58e70e596bc2382907da5baebfe8d901cb9f420
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2702343"
---
# <a name="set-managed-properties-in-common-data-service-metadata"></a>Establecer propiedades administradas en metadatos de Common Data Service 

Las propiedades administradas se aplican únicamente al incluir metadatos con una solución administrada e importarlos en otro entorno. Estos valores permiten al responsable de la solución tener un determinado control sobre el nivel de personalización que desea permitir a los usuarios que instalen su solución administrada. 

> [!TIP]
> Normalmente es una buena idea permitir a los usuarios ampliar metadatos en su solución que funcionen con los datos profesionales. Esto les permitirá adaptar su solución a sus necesidades de la misma forma que pueden hacer para entidades estándar.
>
>Para los metadatos que ofrecen funcionalidades para admitir la solución pero no contienen datos empresariales, ésta es una buena idea para limitar qué personalizaciones se permiten.

La definición de las propiedades administradas debe hacerse mediante el explorador de soluciones.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="entity-managed-properties"></a>Propiedades administradas de entidad

Mientras [visualiza entidades](create-edit-entities-solution-explorer.md#view-entities), seleccione la entidad y seleccione **Propiedades administradas** en la barra de menús.  Se abrirá el cuadro de diálogo **Establecer propiedades administradas**.

![Establecer propiedades administradas de entidad](media/set-managed-properties.png)
  
Las entidades tienen más propiedades administradas que ningún otro tipo de componente de la solución. Si la entidad es personalizable, puede definir las siguientes opciones:  

|Opción|Descripción|
|--|--|
|**Se puede personalizar** |Controla el resto de opciones. Si esta opción es `False`, no se aplicará ninguno de los demás valores. Si es `True`, puede especificar las demás opciones de personalización. Cuando `False`, es equivalente a establecer el resto de opciones en falso.|
|**Se puede modificar el nombre para mostrar**|Si el nombre para mostrar de la entidad puede modificarse.|
|**Se puede cambiar propiedades adicionales** |Se aplica a cualquier elemento no cubierto por las otras opciones.|
|**Se pueden crear nuevos formularios**|Si se pueden crear nuevos formularios para la entidad.|
|**Se pueden crear nuevos gráficos**|Si se pueden crear nuevos gráficos para la entidad.|
|**Se pueden crear vistas nuevas** |Si se pueden crear nuevas vistas para la entidad.|
|**Puede cambiar la relación jerárquica**|Si los valores de las relaciones jerárquicas se pueden cambiar. Más información: [Definir y consultar datos relacionados jerárquicamente](define-query-hierarchical-data.md)|
|**Puede habilitarse el seguimiento de cambios** |Si la propiedad **Seguimiento de cambios** de la entidad puede cambiar.|
|**Se puede habilitar la sincronización con el índice de búsqueda externo** |Si la entidad se puede configurar para habilitar la búsqueda por relevancia. Más información: [Configurar la búsqueda por relevancia para mejorar resultados de búsquedas y rendimiento](/dynamics365/customer-engagement/admin/configure-relevance-search-organization) |

## <a name="field-managed-properties"></a>Propiedades administradas de campos

Consulte [Crear y editar campos para Common Data Service usando el explorador de soluciones de PowerApps](create-edit-field-solution-explorer.md) para obtener información sobre cómo editar campos.

Mientras [visualiza campos](create-edit-field-solution-explorer.md#view-fields), seleccione un campo personalizado de una solución no administrada y elija **Más acciones** >  **Propiedades administradas** en la barra de menús.

![Ver propiedades administradas de campos](media/view-field-managed-properties-solution-explorer.png)  
  
Se abrirá el cuadro de diálogo **Establecer propiedades administradas**.

![Establecer propiedades administradas de campos](media/set-field-managed-property.png)

La opción **Se puede personalizar** controla el resto de opciones. Si esta opción es **False**, no se aplicará ninguno de los demás valores. Si es **Verdadero**, puede especificar las demás opciones de personalización.  
  
Si el campo es personalizable, defina las siguientes opciones como **Verdadero** o **Falso**.  
  
- **Se puede modificar el nombre para mostrar**
- **Se puede cambiar el nivel de requisito** 
- **Se puede cambiar propiedades adicionales** : esta propiedad controla cualquier otra personalización que no tiene una propiedad administrada específica.

Si establece todas las opciones individuales como **Falso**, es equivalente a establecer **Se puede personalizar** como **Falso**.  

Aplique sus opciones y haga clic en **Establecer** para cerrar el cuadro de diálogo.

> [!NOTE]
> Si este campo es un campo de **Fecha y hora**, habrá disponible una propiedad adicional de **Puede cambiar el comportamiento de fecha y hora**. Más información: [Comportamiento y formato del campo de fecha y hora](behavior-format-date-time-field.md)

## <a name="relationship-managed-properties"></a>Propiedades administradas de la relación

Mientras visualiza relaciones de entidad, seleccione una relación de una solución no administrada y elija **Más acciones** > **Propiedades administradas** en la barra de menús.
  
Con las relaciones, la única propiedad administrada es **Se puede personalizar**. Este valor único controla todos los cambios que se pueden realizar en la relación entre entidades. 


### <a name="see-also"></a>Vea también

[Propiedades administradas](solutions-overview.md#managed-properties)<br />
[Crear y editar entidades con el explorador de soluciones](create-edit-entities-solution-explorer.md)<br />
[Crear y editar campos para Common Data Service con el explorador de soluciones de PowerApps](create-edit-field-solution-explorer.md)<br />
[Creación y edición de relaciones entre entidades 1:N (uno a varios) o N:1 (varios a uno) con el explorador de soluciones](create-edit-1n-relationships-solution-explorer.md)<br />
[Crear relaciones entre entidades N:N (varios a varios) en Common Data Service mediante el explorador de soluciones](create-edit-nn-relationships-solution-explorer.md)
