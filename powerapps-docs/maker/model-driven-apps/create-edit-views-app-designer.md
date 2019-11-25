---
title: Crear y editar vistas públicas o del sistema de aplicaciones controladas por modelos con PowerApps | MicrosoftDocs
description: Aprender ahora a crear o editar vistas mediante el diseñador de aplicaciones
keywords: ''
ms.date: 11/27/2018
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 666ab3f3-abda-468c-b248-3a0b410286b0
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 1
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3c3e7133076eb46718ed3f60d1df4f36a012c520
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753910"
---
# <a name="create-and-edit-public-or-system-model-driven-app-views"></a>Crear y editar vistas públicas o del sistema de aplicaciones controladas por modelos

En este tema realizará varias tareas necesarias para trabajar con las vistas, como crear una vista pública, agregar una vista existente a una aplicación y cambiar las columnas, los filtros y el criterio de ordenación para una vista.

En PowerApps, las vistas definen cómo se muestran los registros de una entidad específica. Una vista define lo siguiente:
-  Las columnas (atributos) que aparecen
-  Ancho de las columnas
-  Cómo se ordenan los registros de forma predeterminada
-  Qué filtros se aplican para determinar qué registros aparecen en la lista de forma predeterminada

Las vistas se clasifican generalmente en tres tipos:
- **Personal:** los usuarios individuales pueden crear vistas personales según sus requisitos personales. Estas vistas solo son visibles para el usuario que las creó y para cualquier usuario con el que hubiera elegido compartirlas. 
- **Pública:** como creador de aplicaciones, puede crear y editar vistas públicas para adaptarse a los requisitos de su organización. Estas vistas están disponibles en el selector de vistas y puede utilizarlas en subcuadrículas en un formulario o como lista en un panel.
- **Sistema:** como creador de aplicaciones, también puede modificar vistas del sistema para cumplir los requisitos de su organización. Son vistas especiales de las que depende la aplicación, que existen para entidades del sistema o se crean automáticamente cuando se crean entidades personalizadas. Estas vistas están disponibles para algunos o para todos los usuarios, en función de sus permisos.

Más información: [Comprender las vistas](create-edit-views.md)

## <a name="create-a-public-view-in-powerapps"></a>Crear una vista pública en PowerApps
Como creador de aplicaciones, puede crear y editar vistas públicas usando PowerApps.
1. Inicie sesión en [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  


    > [!IMPORTANT]
    > “Si el modo de diseño **Controlado por modelos** no está disponible, puede que tenga que [Crear un entorno](https://docs.microsoft.com/powerapps/administrator/create-environment).   
  
2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Vistas**. 

3. En la barra de herramientas, seleccione **Agregar vista**. 

4. En el cuadro de diálogo **Crear vista**, introduzca un nombre y, si lo desea, una descripción, y, a continuación, seleccione **Crear**. 
    
5. En el diseñador de vistas, seleccione la columna más para agregar las columnas adicionales que desee mostrar en la vista. Más información: [Agregar una columna a su vista en diseñador de aplicaciones](#add-a-column-to-your-view-in-app-designer) 

   ![Agregar columna](../common-data-service/media/add-column-to-view.png)

6. En el diseñador de vistas, puede realizar las tareas siguientes: 
   - Para cambiar el filtro de la columna seleccione el encabezado de columna que desea filtrar y en la lista desplegable seleccione **Filtrar por**.
   - Para cambiar el orden de la columna seleccione el encabezado de columna que desea filtrar y en la lista desplegable seleccione Filtrar **Ordenar de la A a la Z** u **Ordenar de la Z a la A**.
   - Configure el ancho de columna haciendo clic en la columna y arrastrándola a la posición deseada.
   - Reordene las columnas arrastrando una columna hasta la posición que desee. 

    > [!NOTE]
    > También puede cambiar el orden de la columna haciendo clic en el encabezado de columna y seleccionando **Mover a la derecha** o **Mover a la izquierda**.

10. Elija **Publicar** para guardar la vista y hacer que esté disponible para otros usuarios de su organización. 
   

## <a name="work-with-views-in-app-designer"></a>Trabajar con vistas en el diseñador de aplicaciones
En la siguiente sección se describe cómo crear y editar las vistas en diseñador de aplicaciones.

### <a name="open-and-add-a-view-in-the-app-designer"></a>Abrir y agregar una vista en el diseñador de aplicaciones.

En los pasos siguientes se explica cómo abrir y agregar una vista en el diseñador de aplicaciones.
1. En PowerApps seleccione **Aplicaciones** en el panel de navegación de la izquierda, seleccione **...** junto a la aplicación que desee y seleccione **Editar**. 

2. En sección **Vista de entidad** del diseñador de aplicaciones, seleccione **Vistas**.

    En este ejemplo, hemos seleccionado **Vistas** en la entidad **Cuenta**.

    ![Vista del diseñador de aplicaciones](media/ViewAppDesigner_AccountAppDesignerView.png "Vista de diseñador de aplicaciones de la entidad Cuenta")

3. Para agregar una vista, selecciónela usando tipos de vista como Pública, Búsqueda avanzada, Asociada y Búsqueda. La vista se agregar automáticamente a la lista **Vistas**.

    > [!NOTE]
    > Las vistas se muestran en función de la entidad que ha seleccionado. Por ejemplo, si selecciona **Cuenta**, se muestran las vistas relacionadas con la entidad Cuenta.

Para obtener más información sobre el diseñador de aplicaciones: [Diseñar aplicaciones de negocio personalizadas mediante el diseñador de aplicaciones](design-custom-business-apps-using-app-designer.md)


### <a name="add-a-column-to-your-view-in-app-designer"></a>Agregue una columna a la vista en diseñador de aplicaciones
Las vistas muestran registros en una tabla que contiene filas y columnas. Cada fila es un registro y los campos que se muestra desde el registro dependen de las columnas que agregue a la vista.

1. En el diseñador de la aplicación, seleccione la vista de la entidad que desea y en el panel derecho junto a la vista que desee seleccione editar (botón de lápiz).  
2. En la ficha **Componentes**, seleccione la lista **Atributos de columna** de la **Entidad principal** o la **Entidad relacionada**.

    ![Agregar una columna](media/ViewAppDesigner_AddColumn.png "Agregar una columna a una vista") 

3. En la lista, seleccione el atributo que desee y arrástrelo hacia el encabezado de la columna. También puede agregar el atributo haciendo doble clic en él.
4. Repita el paso 3 hasta que haya agregado todos los atributos que desee mostrar en la vista.

A medida que agrega atributos, puede arrastrarlos a cualquier posición entre los encabezados de columna existentes. También puede mover columnas después de agregarlas a la vista.


### <a name="define-filter-criteria-in-app-designer"></a>Defina los criterios de filtro en diseñador de la aplicación
Puede establecer criterios de filtrado para que solo se muestre un subconjunto de registros en una vista. Cuando un usuario abre la vista, se muestran solo los registros que cumplan los criterios de filtro definidos. Puede seleccionar campos para filtrar entre las entidades principales y las relacionadas.
1. En el diseñador de aplicaciones, expanda la sección **Criterios de filtro**.
   
    ![Establecer criterios de filtro](media/ViewAppDesigner_FilterCriteria.png "Establecer criterios de filtro") 

2. Seleccione **Agregar filtro**.
3. Seleccione un atributo de la lista desplegable de la primera columna. 
4. Seleccione un operador de la lista desplegable de la segunda columna.

    ![Establecer operador de criterios de filtro](media/ViewAppDesigner_FilterCriteriaOption.png "Establecer operador de criterios de filtro")

5. Escriba un valor por el que filtrar la tercera columna.

Puede filtrar los datos según los atributos de entidades relacionadas, además de la entidad principal. 

1. En la ficha **Componentes**, seleccione la lista **Atributos de columna** para **Entidad relacionada**, seleccione la flecha hacia abajo **Seleccionar una entidad** en el campo superior y, después, elija la entidad que desee.

    Así se agregará una sección independiente.

2. Repita los pasos 2 a 5 del procedimiento anterior.

Más información: [Crear y editar relaciones entre entidades](../common-data-service/create-edit-entity-relationships.md)

#### <a name="group-multiple-filters-in-app-designer"></a>Agrupar varios filtros en el diseñador de aplicaciones
Puede agregar varios filtros para la vista si desea filtrar los registros usando más de un campo. 

1. Seleccione los filtros que desea agrupar.
    ![Establecer filtro de grupo](media/ViewAppDesigner_GroupFilter.png "Seestablecer filtro de grupo")
2. Seleccione Agrupar con Y o Agrupar con O para agrupar los filtros.
    ![Selección de filtro de grupo](media/ViewAppDesigner_GroupFilterSelection.png "Seseleccionar filtro de grupo") Al seleccionar **Agrupar por Y**, solo los registros que satisfagan ambos criterios se muestran en la vista. Si selecciona **Agrupar por O**, se muestran los registros que cumplan cualquiera de los criterios de filtro. Por ejemplo, para mostrar solo los registros que tienen prioridad Alta o Normal y el estado de Activo, seleccione **Agrupar por Y**.

Para quitar el filtro de un grupo, seleccione el grupo y seleccione **Desagrupar**. 

### <a name="set-primary-and-secondary-sort-order-for-columns-in-app-designer"></a>Establecer el criterio de ordenación primario y secundario de las columnas del diseñador de aplicaciones
Cuando se abre una vista, se ordenan los registros que se muestra en el orden que se establece cuando se crea la vista.   De forma predeterminada, los registros se ordenan según la primera columna en una vista cuando no se selecciona ningún orden. Puede elegir ordenar por una sola columna, o bien, elegir dos columnas —una principal y otra secundaria— para ordenar. Cuando se abre la vista, los registros se ordenan primero por la columna que desea usar para la ordenación principal y, después, por la columna que desea usar para la ordenación secundaria. 

> [!NOTE]
> Solo puede establecer ordenaciones principales y secundarias para los atributos de columna que ha agregado desde la entidad principal.

1. Seleccione la columna que desea usar para la ordenación.
2. Seleccione la flecha abajo y, después, elija **Ordenación principal** u **Ordenación secundaria**.
 
    ![Ordenar registro](media/ViewAppDesigner_SortRecords.png "Ordenar registros en función de la ordenación principal y secundaria") 

Si quita la columna elegida para el orden principal, la columna elegida para el orden secundario se convierte en la principal.

### <a name="define-a-web-resource-in-app-designer"></a>Definir un recurso web en diseñador de aplicaciones
Especifique un recursos web de tipo script, para asociar a una columna en la vista. Estos scripts ayudan a mostrar iconos para las columnas.

1. Seleccione la columna a la que desea agregar el recurso web.
2. En la pestaña **Propiedades**, seleccione **Avanzadas**.
3. En la lista despegable **Recurso web**, seleccione el recurso web que desee usar.
4. En el cuadro de texto **Nombre de función**, escriba un nombre de función.

### <a name="edit-a-public-or-system-view-in-app-designer"></a>Editar una vista pública o del sistema en diseñador de la aplicación
Puede cambiar la forma en que se muestra una vista pública o de sistema agregando, configurando o quitando columnas.
1. En la lista **Vistas** de una entidad, seleccione la flecha abajo **Mostrar la lista de referencias** ![Desplegable](media/DownArrow.png "Flecha desplegable").
    ![Editar vista](media/ViewAppDesigner_EditView.png "EdEditar una vista pública o de sistema")
2. Junto a la vista que desea editar, seleccione **Abrir el diseñador de vistas** ![Abrir el diseñador de vistas](media/dynamics365-open-designer.png "Abrir diseñador de vistas"). 

    La vista se abre en el diseñador de vistas. 

Cuando edite una vista pública o de sistema, debe guardar y publicar los cambios antes de que estén visibles en la aplicación.


## <a name="community-tools"></a>Herramientas de la Comunidad
**Ver diseño del Duplicador** y **Ver diseñador** son herramientas que la comunidad XrmToolbox desarrolló para PowerApps.

Más información: [Herramientas del desarrollador](/powerapps/developer/common-data-service/developer-tools).

> [!NOTE]
> Estas herramientas se proporcionan por XrmToolBox y no se admiten por Microsoft. Si tiene alguna duda relacionada con la herramienta, póngase en contacto con el Editor. Más información: [XrmToolBox](https://www.xrmtoolbox.com/). 

### <a name="next-steps"></a>Pasos siguientes
[Crear relaciones 1: N (uno a varios) o N:1 (varios a uno)](../common-data-service/create-edit-1n-relationships.md)
