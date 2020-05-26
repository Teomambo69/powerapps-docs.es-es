---
title: Editar criterios de filtro y cambiar el orden en vistas de aplicaciones controladas por modelos con Power Apps | MicrosoftDocs
description: Obtenga información sobre cómo editar criterios de filtro y cambiar el orden en vistas
ms.custom: ''
ms.date: 03/26/2020
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
ms.assetid: fecf23c9-05e6-4397-9a5d-37210bcc2816
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: fd5541059b743115a56614671b72e5e00deabfd2
ms.sourcegitcommit: 3c6c5594b73abd5ff438d50f3b579d56cef7241c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "3285584"
---
# <a name="edit-filter-criteria-and-change-sort-order-in-model-driven-app-views"></a>Editar criterios de filtro y cambiar el orden en vistas de aplicaciones controladas por modelos

<a name="BKMK_EditFilterCriteria"></a>   

Junto con las columnas que se muestran en la vista, los criterios de filtro que se aplican a una vista son parte fundamental del valor proporcionado por la vista. Puede agregar o editar criterios de filtro y cambiar el orden de clasificación de las columnas que incluya en una vista. Si no se establece un orden de clasificación para una vista, la vista se ordena de manera predeterminada por el campo primario de la vista en orden ascendente (de la A a la Z).

## <a name="change-the-sort-order-of-a-view"></a>Cambiar el orden de una vista

1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Vistas**.

3.  Seleccione una vista para abrirla en el diseñador de vistas.

    > [!div class="mx-imgBorder"] 
    > ![Editar filtros](media/view-column-menu.png "Editar filtros")

4.  Seleccione un nombre de campo en el encabezado de la columna y, en el menú de la columna, seleccione **Ordenar de la A a la Z** o **Ordenar Z a A**. El orden de clasificación se indica en el encabezado de la columna con una flecha hacia arriba o una flecha hacia abajo.

También puede cambiar el orden de clasificación utilizando el panel de propiedades de vista. 

1.  Si no se ha establecido un orden de clasificación para la vista, seleccione **Ordenar por** y luego seleccione el orden primario por columna.

2.  Si desea ordenar la vista por columnas adicionales, seleccione **Luego ordenar por** y después seleccione un orden adicional por columna para la vista.

    Es posible que desee ordenar por más de una columna cuando tenga datos que desee agrupar por el mismo valor en una columna, y luego ordenar otra columna dentro de ese grupo de valores iguales.

3.  Para eliminar una expresión de clasificación, seleccione **Eliminar expresión de ordenación** (el botón **X**).

## <a name="add-or-edit-filter"></a>Agregar o modificar filtros

1.  Seleccione una columna y, en el menú de la columna, seleccione **Filtrar por**.

    > [!div class="mx-imgBorder"] 
    > ![Editar filtros](media/edit-filter-criteria.png "Editar filtros")

2.  Seleccione el operador condicional que desee usar.

3.  Escriba o seleccione el valor de comparación para la condición.

4.  Seleccione **Aplicar**.

    Las expresiones de filtro para una vista se muestran en el panel de propiedades de Vista.
    
5.  Para editar una expresión de filtro, seleccione la expresión de selección de filtro en el panel de propiedades Vista.

6.  Para eliminar una expresión de filtro, seleccione el botón **X**. 

También puede usar el generador de expresiones en el diseñador de vistas para agregar o editar filtros para cualquier campo de la entidad en la vista actual o cualquier campo en una entidad relacionada. Más información: [Crear o editar filtros en vistas de aplicaciones basadas en modelos](create-edit-view-filters.md)

## <a name="use-solution-explorer-to-edit-filter-criteria-and-change-sort-order"></a>Use el explorador de solución para editar criterios de filtro y cambiar el orden

Cambiar el orden para una vista.

1.  Abra el [explorador de soluciones](advanced-navigation.md#solution-explorer), expanda **Entidades**, seleccione la entidad que desee, seleccione **Vistas** y después abra la vista que quiera.

2.  En el diseñador de vistas, seleccione **Configurar orden**.  

    > [!div class="mx-imgBorder"] 
    > ![Configurar la ordenación](media/configure-sorting.png "Configurar la ordenación")
  
3.  En el cuadro de diálogo **Configurar orden**, en la lista **Ordenar por**, seleccione la columna que desea ordenar y, a continuación, seleccione **Orden ascendente** u **Orden descendente**.  
  
4.  Seleccione **Aceptar** para guardar los cambios del orden.  

Cambiar el criterio de filtro para una vista.

1.  Cuando cree o edite la vista en el diseñador de vistas, en el panel **Tareas comunes** seleccione **Editar criterios de filtrado**.  
  
2.  El cuadro de diálogo muestra una interfaz de usuario similar a **Búsqueda avanzada**. Puede usar las cláusulas **Y** y **O** para especificar y agrupar criterios seleccionando la cláusula de filtro y luego seleccionando **Agrupar con Y** o **Agrupar con O**.  

3.  Seleccione **Aceptar** para guardar los criterios de filtro.  
  
Para obtener más información sobre cómo crear cláusulas de filtro, consulte [Crear, editar o guardar búsquedas avanzadas](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search).   
 
## <a name="next-steps"></a>Pasos siguientes
[Comprender las vistas](create-edit-views.md)
