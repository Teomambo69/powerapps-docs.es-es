---
title: 'Agregar, configurar, mover o eliminar secciones en un formulario usando el diseñador de formularios | MicrosoftDocs'
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="add-configure-move-or-delete-sections-on-a-form"></a>Agregar, configurar, mover o eliminar secciones de un formulario 
Agregar, configurar, mover o eliminar secciones en un formulario usando el diseñador de formularios. 

## <a name="add-sections-to-a-form"></a>Agregar secciones a un formulario
Para agregar secciones a un formulario, use el panel **Componentes**. 

> [!div class="mx-imgBorder"] 
> ![](media/FormDesignerComponentsLayout.png "Componentes de diseño")

  > [!NOTE]
  >   Las secciones solo se pueden agregar a formularios principales y formularios de la vista rápida. Más información: [Tipos de formularios](types-forms.md)

### <a name="add-sections-to-a-form-using-drag-and-drop"></a>Agregar secciones a un formulario mediante arrastrar y colocar
> [!NOTE]
> Cuando se agregan o mueven secciones utilizando arrastrar y colocar tenga en cuenta que la vista previa de formularios es dinámica y puede representar columnas de varias pestañas como apiladas. Para asegurarse de que la sección que se agrega o mueve está en la columna de la pestaña correcta, colóquela o péguela anclada a otra sección que ya esté en esa columna de pestaña.
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la barra de comandos, seleccione **Agregar componente**, o en el panel izquierdo, seleccione **Componentes**. 
3. En el panel **Componente**, seleccione un componente de sección y arrástrelo sobre la vista previa de formulario. Cuando arrastra la sección sobre la vista previa de formulario verá destinos de colocación en los que podrá agregar la sección. 
4. Coloque la sección en la ubicación que desea. Tenga en cuenta lo siguiente: 
    - Las secciones se pueden colocar antes o después de cualquier sección existente.
    - Las secciones también se pueden colocar en el área vacía de una pestaña. En este caso la sección se agregará en un espacio disponible para distribuir uniformemente secciones a lo largo de las columnas de la pestaña.
    - Si mantiene el puntero sobre un encabezado de sección cuando arrastra un campo cambiará la pestaña actualmente seleccionada, permitiendo que agregue la sección a una pestaña diferente.   
5. Repita los pasos 3-4 anteriores si desea agregar más secciones.
6. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

### <a name="add-sections-to-a-form-using-selection"></a>Agregar secciones a un formulario utilizando selección 
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formulario, seleccione otra sección o pestaña existente. Observe lo siguiente:
    - Cuando selecciona un campo existente, la nueva sección se agrega después de la sección existente. 
    - Cuando seleccione una pestaña, la nueva sección se agrega en un espacio disponible para distribuir uniformemente secciones a lo largo de las columnas de pestaña. 
3. En la barra de comandos, seleccione **Agregar componente**, o en el panel izquierdo, seleccione **Componentes**.  
4. En el panel **Componentes**, seleccione un componente de sección para agregarlo al formulario. Como alternativa, seleccione **...** junto al componente de selección que desee y, a continuación seleccione **Agregar a la pestaña seleccionada**. 
5. Repita los pasos 2-4 anteriores si desea agregar más secciones.
6. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

## <a name="configure-sections-on-a-form"></a>Configurar secciones en un formulario
Éstas son las propiedades disponibles para configurar una sección cuando crea o edita un formulario usando el diseñador de formularios.

|Área   |Nombre  |Descripción  |
|---------|---------|---------|
|**Opciones de visualización** | **Etiqueta de sección**    | Etiqueta localizable de la sección visible para los usuarios. <br /><br />Se requiere esta propiedad.      |
|**Opciones de visualización** | **Nombre** | El nombre único de la sección que se usa al hacerle referencia en los scripts. El nombre solo puede contener caracteres alfanuméricos y de subrayado. <br /><br />Se requiere esta propiedad. |
|**Opciones de visualización** | **Ocultar etiqueta** |  Cuando se selecciona, la etiqueta de la sección está oculta. |
|**Opciones de visualización** | **Bloquear sección** | Bloquee esta sección para evitar que se elimine. |
|**Opciones de visualización** | **Ocultar sección** | Cuando se selecciona, la sección está oculta de forma predeterminada y se puede mostrar con código. |
|**Opciones de visualización** | **Ocultar en teléfono** |  La sección se puede ocultar para representar una versión condensada de este formulario en pantallas de teléfono. |
|**Formato** |  **Columnas** |  Especifique hasta cuatro columnas para la sección. |

## <a name="move-sections-on-a-form"></a>Mover secciones de un formulario
Puede mover secciones mediante arrastrar y colocar o cortar y pegar acciones. 

### <a name="move-sections-on-a-form-using-drag-and-drop"></a>Mover secciones en un formulario mediante arrastrar y colocar
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formularios, seleccione la etiqueta de la sección o el espacio vacío dentro de la sección que desea arrastrar y colocar. Cuando arrastra la sección sobre la vista previa de formulario verá destinos de colocación a los que podrá mover la sección. 
   Tenga en cuenta lo siguiente: 
    - Las secciones se pueden colocar antes o después de cualquier sección existente.
    - Las secciones también se pueden colocar en el área vacía de una pestaña. En este caso la sección se agregará en un espacio disponible para distribuir uniformemente secciones a lo largo de las columnas de la pestaña.
    - Si mantiene el puntero sobre un encabezado de sección cuando arrastra un campo cambiará la pestaña actualmente seleccionada, permitiendo que agregue la sección a una pestaña diferente.   
3. Repita el paso 2 anterior si desea mover más secciones.
5. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

### <a name="move-sections-on-a-form-using-cut-and-paste"></a>Mover secciones en un formulario mediante cortar y pegar
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formulario, seleccione la sección que desee mover.
3. En la barra de comandos, seleccione **Cortar**.
4. En la vista previa de formularios, seleccione otra sección o pestaña existente. También puede cambiar a una pestaña diferente si es necesario.
5. En la barra de comandos, seleccione **Pegar** o seleccione el botón de contenido adicional, y después seleccione **Pegar delante**.      Tenga en cuenta lo siguiente: 
    - Cuando selecciona **Pegar**, la sección movida se pega después de la sección existente. 
    - Cuando selecciona **Pegar delante**, la sección movida se pega delante de la sección existente.
    - Cuando seleccione una pestaña, la sección movida se agrega en un espacio disponible para distribuir uniformemente secciones a lo largo de las columnas de pestaña. La acción **Pegar delante** no es aplicable y por tanto no está disponible en este caso.
6. Repita los pasos 2-5 anteriores si desea mover más secciones.
7. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

## <a name="delete-sections-on-a-form"></a>Eliminar secciones de un formulario
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formularios, seleccione la sección que desee eliminar del formulario. 
3. En la barra de comandos, seleccione **Eliminar**.
4. Repita los pasos 2-3 anteriores si desea eliminar más secciones.
4. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

    > [!NOTE]
    >   - Las secciones solo se pueden eliminar en formularios principales y formularios de la vista rápida. Más información: [Tipos de formularios](types-forms.md)
    >   - Si elimina una sección por error, en la barra de comandos seleccione **Deshacer** para revertir el formulario al estado anterior. 
    >   - No puede eliminar una sección que contenga un campo obligatorio o bloqueado. 
    >   - No puede eliminar una sección que esté bloqueada. 
    >   - Una pestaña necesita tener al menos una sección en cada columna de pestaña. Si elimina la última sección restante de una columna de pestaña se agregará automáticamente una nueva sección. 

### <a name="see-also"></a>Vea también
[Información general del diseñador de formularios controlado por modelos](form-designer-overview.md)  
[Crear, editar o configurar formularios usando el diseñador de formularios](create-and-edit-forms.md)  
[Agregar, configurar, mover o eliminar campos de un formulario](add-move-or-delete-fields-on-form.md)  
[Agregar, configurar, mover o eliminar componentes de un formulario](add-move-configure-or-delete-components-on-form.md)  
[Agregar, configurar, mover o eliminar pestañas de un formulario](add-move-or-delete-tabs-on-form.md)  
[Configurar propiedades de encabezado en el diseñador de formularios](form-designer-header-properties.md)  
[Agregar y configurar un componente de subcuadrícula en un formulario](form-designer-add-configure-subgrid.md)  
[Agregar y configurar un componente de vista rápida en un formulario](form-designer-add-configure-quickview.md)  
[Configurar un componente de búsqueda en un formulario](form-designer-add-configure-lookup.md)  
[Use la vista de árbol del diseñador de formularios](using-tree-view-on-form.md)  
[Crear y editar campos](../common-data-service/create-edit-field-portal.md)  
