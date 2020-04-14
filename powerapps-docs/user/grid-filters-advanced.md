---
title: Creación de una vista personal mediante filtros de cuadrícula avanzados | MicrosoftDocs
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 04/02/2020
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0a27f7104b85b8ae45146ea7a3626cd1b0e2157c
ms.sourcegitcommit: 3e6c499a65ada8a9f28022a02f64030b0c069a17
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/04/2020
ms.locfileid: "80661334"
---
# <a name="edit-or-create-personal-views-using-advanced-grid-filters"></a>Edición o creación de vistas personales mediante filtros de cuadrícula avanzados 

Use las opciones de filtro avanzadas para crear una vista personal y ver los registros que considere importantes. Las opciones de filtro avanzadas permiten crear una amplia gama de vistas de simples a complejas. También permite agregar condiciones agrupadas y anidadas a los filtros.


> [!NOTE]
> La opción de filtro avanzada solo está disponible en las versiones en inglés.

Al crear y guardar una vista personal, ésta aparece en la lista de vistas personales en **Mis vistas**.

> [!div class="mx-imgBorder"]
> ![Vistas personales](media/my_peronsal_view.png "Vistas personales")


## <a name="see-the-current-view-definition"></a>Vista de la definición de la vista actual

Para ver los filtros que se aplicaron a la vista actual, seleccione una vista y, luego, elija **Filtro** ![icono Filtro](media/commandbar_filter_icon.png "Icono de Filtro"). Se abre el generador de expresiones y se muestra la definición de vista predeterminada.

> [!div class="mx-imgBorder"] 
> ![Definición de vista actual](media/current_view_def.gif "En esta imagen se muestra cómo ver los filtros de la vista.")

## <a name="add-conditions-to-filters"></a>Adición de condiciones a los filtros

1. Para editar la vista actual y agregar más filtros, seleccione una vista y, luego, elija **Filtro** ![icono Filtro](media/commandbar_filter_icon.png "Icono de Filtro").
2. En la pantalla **Filtros avanzados**, use el generador de expresiones para agregar condiciones a los filtros. Para más información sobre cómo agregar condiciones, consulte [Agregar condiciones a un filtro](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-view-filters#add-conditions-to-a-filter).
3. Cuando finalice, seleccione **Aplicar**. 

   > [!div class="mx-imgBorder"] 
   > ![Agregar filtros](media/add_filters.gif "En esta imagen se muestra cómo agregar filtros mediante el generador de expresiones.")

### <a name="add-grouped-or-nested-conditions"></a>Adición de condiciones agrupadas o anidadas

Para profundizar aún más en los datos, puede agregar condiciones agrupadas o anidadas a los filtros. Para más información, consulte [Agregar una condición de grupo a un filtro](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-view-filters#add-a-group-condition-to-a-filter).

   > [!div class="mx-imgBorder"] 
   > ![Adición de un grupo o una condición anidada](media/group_condition.gif "En esta imagen se muestra cómo agregar una condición agrupada o anidada a un filtro.")

### <a name="clear-filters"></a>Borrado de filtros

Para borrar los filtros que se aplicaron y restablecer la vista a la definición original, seleccione **Borrar filtro** ![icono Borrar filtro](media/clear_filter_icon.png "Icono Borrar filtro").

### <a name="save-your-personal-view"></a>Guardar la vista personal

Un asterisco junto al nombre de una vista indica que la vista no se ha guardado. 

   > [!div class="mx-imgBorder"] 
   > ![Vista sin guardar](media/unsaved_view.png "Vista sin guardar")

1. Para guardar una vista personal, en la barra de comandos seleccione **Más** ![icono Más](media/commandbar_more_icon.png "Icono Más"). 
2. Seleccione **Crear vista** > **Save filter as new view** (Guardar filtro como nueva vista).
3. En el cuadro de diálogo **Save as new view** (Guardar como nueva vista), escriba un nombre y una descripción para la vista y, luego, seleccione **Guardar**.
4. La vista aparecerá en la lista de vistas personales en **Mis vistas**.

   > [!div class="mx-imgBorder"] 
   > ![Guardar una vista personal](media/save_personal_view.gif "En esta imagen se muestra cómo guardar una vista personal.")


   
