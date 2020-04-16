---
title: Crear o editar filtros en vistas de aplicaciones basadas en modelo | MicrosoftDocs
description: Aprenda a crear y editar filtros o vistas para su aplicación
keywords: generador de expresiones
ms.date: 2/04/2020
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: ''
author: iangpgh
ms.author: v-iapr
manager: matp
ms.reviewer: srihas
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 25
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3a36cf57710da4e6306c7de48e19d4af6c722f10
ms.sourcegitcommit: abdc8c609a7a221ce4ca6b051a84b7083bdbe1ab
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2020
ms.locfileid: "3225604"
---
# <a name="create-or-edit-filters-in-model-driven-app-views"></a>Crear o editar filtros en vistas de aplicaciones basadas en modelo

<a name="BKMK_CreateOrEditViewFilters"></a>   

Los filtros de una vista de Power Apps son importantes para el valor proporcionado por la vista. Los filtros que aplique determinan qué registros aparecen en la lista de forma predeterminada. Puede agregar o editar un filtro para las columnas que incluye en una vista seleccionando la columna y seleccionando **Filtrar por**. También puede usar el generador de expresiones en el diseñador de vistas. Use el generador de expresiones para agregar o editar filtros para cualquier campo de la entidad en la vista actual o cualquier campo en una entidad relacionada. 

En este tema, creará o editará filtros realizando las siguientes tareas:

-   [Editar o quitar una condición de filtro](create-edit-view-filters.md#edit-or-remove-a-filter-condition)

-   [Abrir el generador de expresiones](create-edit-view-filters.md#open-the-expression-builder)

-   [Agregar condiciones a un filtro](create-edit-view-filters.md#add-conditions-to-a-filter)

-   [Agregar una condición de grupo a un filtro](create-edit-view-filters.md#add-a-group-condition-to-a-filter)

-   [Agregar una entidad relacionada a una condición](create-edit-view-filters.md#add-a-related-entity-to-a-condition)

-   [Agrupar condiciones de un filtro](create-edit-view-filters.md#group-conditions-of-a-filter)

## <a name="edit-or-remove-a-filter-condition"></a>Editar o quitar una condición de filtro

1. Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

2. Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Vistas**.

3. Seleccione una vista para abrirla. El panel de propiedades de vista enumera los filtros existentes.

    > [!div class="mx-imgBorder"] 
    > ![Ver filtros del panel](media/views-panel-filters.png "Ver filtros del panel")

4. En el panel de propiedades de vista, seleccione una condición de filtro.

    > [!div class="mx-imgBorder"] 
    > ![Editar filtros](media/edit-filter-viewpanel.png "Editar filtros")

5. Seleccione el operador condicional que desee usar.

6. Escriba o seleccione el valor de comparación para la condición.

7. Seleccione **Aplicar**.

8. Para eliminar una condición, seleccione **Cerrar**. La condición se elimina sin confirmación.

### <a name="open-the-expression-builder"></a>Abrir el generador de expresiones

- En el panel de propiedades de vista, seleccione **Editar filtros**.

    > [!div class="mx-imgBorder"] 
    > ![Generador de expresiones](media/edit-create-filters.png "Generador de expresiones")

### <a name="add-conditions-to-a-filter"></a>Agregar condiciones a un filtro

1. En el generador de expresiones, seleccione **Agregar** > **Agregar fila**.

2. Seleccione un campo para la condición.

3. Seleccione un operador condicional.

4. Seleccione un valor de comparación.  

    Algunas condiciones de filtro no requieren un valor de comparación para la condición. Por ejemplo, el operador **Contiene datos** no requiere un valor de comparación. Con otras condiciones de filtro, usted elige el valor de comparación de un conjunto de opciones. Por ejemplo, el campo **Estado** tiene un conjunto de opciones que contiene los valores **Activo** e **Inactivo**.

    > [!div class="mx-imgBorder"] 
    > ![Condición de filtro](media/add-condition-filter.png "Condición de filtro")

5. Seleccione **Aceptar**.

### <a name="add-a-group-condition-to-a-filter"></a>Agregar una condición de grupo a un filtro

1. En el generador de expresiones, seleccione **Agregar** > **Agregar grupo**.

2. Seleccione el operador relacional **O** para el grupo. **Y** es el operador relacional predeterminado.

3. Especifique la primera cláusula de la condición agrupada. Seleccione el campo, el operador condicional y el valor de comparación.

4. Seleccione **Agregar** > **Agregar grupo**.

5. Especifique la segunda cláusula de la condición agrupada.

    > [!div class="mx-imgBorder"] 
    > ![Filtro de condición de grupo](media/add-group-filter.png "Filtro de condición de grupo")

    Puede elegir **Contraer** para mostrar el grupo como una expresión condicional.

### <a name="add-a-related-entity-to-a-condition"></a>Agregar una entidad relacionada a una condición

1. En el generador de expresiones, seleccione **Agregar** > **Agregar entidad relacionada**.

2. Seleccione un campo de la entidad actual que esté relacionado con otra entidad. La entidad relacionada con el campo se muestra entre paréntesis. Puede seleccionar campos que tengan una relación de varios a uno, de uno a varios o de varios a varios con la entidad relacionada.

3. Seleccione un campo de la entidad relacionada para la condición.

4. Seleccione un operador condicional.

5. Seleccione o escriba un valor de comparación.

    > [!div class="mx-imgBorder"] 
    > ![Filtro de entidad relacionado](media/add-relatedentity-filter.png "Filtro de entidad relacionado")

### <a name="group-conditions-of-a-filter"></a>Agrupar condiciones de un filtro

1. En el generador de expresiones, active la casilla para las condiciones que desee agrupar.

2. Seleccione **Más comandos** (...) para una de las condiciones, y luego seleccione **Crear grupo**.

3. Para desagrupar un grupo, seleccione **Más comandos** (...) para el grupo y luego seleccione **Desagrupar**.

    > [!div class="mx-imgBorder"] 
    > ![Filtro de condición agrupado](media/group-conditions-filter.png "Filtro de condición agrupado")

### <a name="see-also"></a>Vea también
[Edite o cree vistas personales utilizando filtros de cuadrícula avanzados](../../user/grid-filters-advanced.md)
[Elegir y configurar columnas](choose-and-configure-columns.md)  
[Edite criterios de filtrado](edit-filter-criteria.md)  
[Crear relaciones 1: N (uno a varios) o N:1 (varios a uno)](../common-data-service/create-edit-1n-relationships.md)
