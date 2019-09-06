---
title: 'Agregar, mover o eliminar secciones en un formulario usando el diseñador de formularios | MicrosoftDocs'
ms.custom: ''
ms.date: 04/21/2019
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

# <a name="add-move-or-delete-sections-on-a-form"></a>Agregar, mover o eliminar secciones de un formulario 
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Agregar, mover o eliminar secciones en un formulario usando el diseñador de formularios. 

> [!NOTE]
> Cuando se agregan o mueven secciones utilizando arrastrar y colocar tenga en cuenta que la vista previa de formularios es dinámica y puede representar columnas de varias pestañas como apiladas. Para asegurarse de que la sección que se agrega o mueve está en la columna de la pestaña correcta, colóquela o péguela anclada a otra sección que ya esté en esa columna de pestaña.

## <a name="add-sections-to-a-form"></a>Agregar secciones a un formulario
Para agregar secciones a un formulario, use el panel **Diseños**. 

> [!div class="mx-imgBorder"] 
> ![](media/layouts-pane.png "Panel Diseños")

  > [!NOTE]
  >   Las secciones solo se pueden agregar a formularios principales y formularios de la vista rápida. Más información: [Tipos de formularios](types-forms.md)

### <a name="add-sections-to-a-form-using-drag-and-drop"></a>Agregar secciones a un formulario mediante arrastrar y colocar

1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la barra de comandos, seleccione **Agregar control**, o en el panel izquierdo, seleccione **Diseños**. 
3. En el panel **Diseños**, seleccione un control de sección y arrástrelo sobre la vista previa de formulario. Cuando arrastra la sección sobre la vista previa de formulario verá destinos de colocación en los que podrá agregar la sección. 
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
3. En la barra de comandos, seleccione **Agregar control**, o en el panel izquierdo, seleccione **Diseños**.  
4. En el panel **Diseños** , seleccione un control de sección para agregarlo al formulario. Como alternativa, seleccione **...** junto al control de selección que desee y, a continuación seleccione **Agregar a la pestaña seleccionada**. 
5. Repita los pasos 2-4 anteriores si desea agregar más secciones.
6. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

## <a name="move-sections-on-a-form"></a>Mover secciones de un formulario

### <a name="move-sections-on-a-form-using-drag-and-drop"></a>Mover secciones en un formulario mediante arrastrar y colocar

1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formularios, seleccione la etiqueta de la sección o el espacio en blanco vacío dentro de la sección que desea mover e inicie la acción de arrastrar. Cuando arrastra la sección sobre la vista previa de formulario verá destinos de colocación a los que podrá mover la sección. 
3. Coloque la sección en la ubicación que desea. Tenga en cuenta lo siguiente: 
    - Las secciones se pueden colocar antes o después de cualquier sección existente.
    - Las secciones también se pueden colocar en el área vacía de una pestaña. En este caso la sección se agregará en un espacio disponible para distribuir uniformemente secciones a lo largo de las columnas de la pestaña.
    - Si mantiene el puntero sobre un encabezado de sección cuando arrastra un campo cambiará la pestaña actualmente seleccionada, permitiendo que agregue la sección a una pestaña diferente.   
4. Repita los pasos 2-3 anteriores si desea mover más secciones.
5. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

### <a name="move-sections-on-a-form-using-cut-and-paste"></a>Mover secciones en un formulario mediante cortar y pegar

1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formulario, seleccione la sección que desee mover.
3. En la barra de comandos, seleccione **Cortar**.
4. En la vista previa de formularios, seleccione otra sección o pestaña existente. También puede cambiar a una pestaña diferente si es necesario.
5. En la barra de comandos, seleccione **Pegar** o seleccione el botón de contenido adicional, y después seleccione **Pegar delante**. Tenga en cuenta lo siguiente: 
    - Cuando selecciona **Pegar**, la sección movida se pega después de la sección existente. 
    - Cuando selecciona **Pegar delante**, la sección movida se pega delante de la sección existente.
    - Cuando seleccione una pestaña, la sección que se está moviendo se agrega en un espacio disponible para distribuir uniformemente secciones a lo largo de las columnas de pestaña. La acción **Pegar delante** no es aplicable y por tanto no está disponible en este caso.
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
[Crear o editar formularios usando el diseñador de formularios](create-and-edit-forms.md)  
[Agregar, mover o eliminar campos en un formulario usando el diseñador de formularios](add-move-or-delete-fields-on-form.md)  
[Agregar, mover o eliminar pestañas en un formulario usando el diseñador de formularios](add-move-or-delete-tabs-on-form.md)  
[Propiedades disponibles en el diseñador de formularios](form-designer-properties.md)  
[Configurar propiedades de encabezado en el diseñador de formularios](form-designer-header-properties.md)  
[Use la vista de árbol del diseñador de formularios](using-tree-view-on-form.md)  
[Crear y editar campos](../common-data-service/create-edit-field-portal.md)
