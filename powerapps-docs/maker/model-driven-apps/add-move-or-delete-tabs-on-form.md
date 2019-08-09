---
title: 'Agregar, mover o eliminar pestañas en un formulario usando el diseñador de formularios | MicrosoftDocs'
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

# <a name="add-move-or-delete-tabs-on-a-form"></a>Agregar, mover o eliminar pestañas de un formulario  
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Agregar, mover o eliminar pestañas en un formulario usando el diseñador de formularios.

## <a name="add-tabs-to-a-form"></a>Agregar pestañas a un formulario
Para agregar pestañas a un formulario, use el panel **Diseños**.  

> [!div class="mx-imgBorder"] 
> ![](media/layouts-pane.png "Panel Diseños")
   
  > [!NOTE]
  >  Solo se pueden agregar pestañas a los formularios principales. Más información: [Tipos de formularios](types-forms.md)

### <a name="add-tabs-to-a-form-using-drag-and-drop"></a>Agregar pestañas a un formulario mediante arrastrar y colocar

1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la barra de comandos, seleccione **Agregar control**, o en el panel izquierdo, seleccione **Diseños**. 
3. En el panel **Diseños**, seleccione un control de pestaña y arrástrelo sobre la vista previa de formulario. Cuando arrastra la pestaña sobre la vista previa de formulario verá destinos de colocación en los que podrá agregar la pestaña. 
4. Coloque la pestaña en la ubicación que desea. Tenga en cuenta lo siguiente: 
    - Las pestañas se pueden colocar antes o después de cualquier pestaña existente manteniendo el cursor sobre los encabezados de la pestaña.
    - Las pestañas también se pueden colocar antes o después de la pestaña actual manteniendo el cursor sobre el borde izquierdo o derecho de la pestaña actual.
5. Repita los pasos 3-4 anteriores si desea agregar más pestañas.
6. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

### <a name="add-tabs-to-a-form-using-selection"></a>Agregar pestañas a un formulario utilizando selección 

1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formulario, seleccione otra pestaña o el formulario. Tenga en cuenta lo siguiente:
    - Cuando selecciona una pestaña existente, la nueva pestaña se agregará después de la pestaña existente. 
    - Cuando se selecciona el formulario, la nueva pestaña se agregará como la última pestaña del formulario. 
3. En la barra de comandos, seleccione **Agregar control**, o en el panel izquierdo, seleccione **Diseños**.  
4. En el panel **Diseños** , seleccione un control de pestaña para agregarlo al formulario. Como alternativa, seleccione **...** junto al control de ficha que desee y, a continuación seleccione **Agregar a formulario**. 
5. Repita los pasos 2-4 anteriores si desea agregar más pestañas.
6. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

## <a name="move-tabs-on-a-form"></a>Mover pestañas en un formulario

### <a name="move-tabs-on-a-form-using-drag-and-drop"></a>Mover pestañas en un formulario mediante arrastrar y colocar

1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En a vista previa de formulario, seleccione el encabezado de la pestaña que desea mover e inicie la acción de arrastrar. Cuando arrastra la pestaña sobre la vista previa de formulario verá destinos de colocación en los que podrá mover la pestaña.  
3. Coloque la pestaña en la ubicación que desea. Tenga en cuenta lo siguiente:
    - Las pestañas se pueden colocar antes o después de cualquier pestaña existente manteniendo el cursor sobre los encabezados de la pestaña.
    - Las pestañas también se pueden colocar antes o después de la pestaña actual manteniendo el cursor sobre el borde izquierdo o derecho de la pestaña actual.
4. Repita los pasos 2-3 anteriores si desea mover más pestañas.
5. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

### <a name="move-tabs-on-a-form-using-cut-and-paste"></a>Mover pestañas en un formulario mediante cortar y pegar

1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formulario, seleccione la pestaña que desee mover.
3. En la barra de comandos, seleccione **Cortar**.
4. En la vista previa de formulario, seleccione otra pestaña o el formulario.
5. En la barra de comandos, seleccione **Pegar** o seleccione el botón de contenido adicional, y después seleccione **Pegar delante**. Tenga en cuenta lo siguiente: 
    - Cuando selecciona **Pegar**, la pestaña movida se pega después de la pestaña existente. 
    - Cuando selecciona **Pegar delante**, la pestaña se pega delante de la pestaña existente.
    - Cuando se selecciona el formulario, la pestaña que se está moviendo se agregará como la última pestaña del formulario. La acción **Pegar delante** no es aplicable y por tanto no está disponible en este caso.
6. Repita los pasos 2-5 anteriores si desea mover más pestañas.
7. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

## <a name="delete-tabs-on-a-form"></a>Eliminar pestañas en un formulario
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formularios, seleccione la pestaña que desee eliminar del formulario. 
3. En la barra de comandos, seleccione **Eliminar**.
4. Repita los pasos 2-3 anteriores si desea eliminar más pestañas.
4. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

    > [!NOTE]
    >   - Solo se pueden eliminar pestañas en los formularios principales. Más información: [Tipos de formularios](types-forms.md)
    >   - Si elimina una pestaña por error, en la barra de comandos seleccione **Deshacer** para revertir el formulario al estado anterior. 
    >   - No puede eliminar una pestaña que contenga secciones con campos obligatorios o bloqueados. 
    >   - No puede eliminar una pestaña que tenga secciones bloqueadas. 
    >   - Un formulario debería tener al menos una pestaña. No puede eliminar la última pestaña que quede en el formulario. 

### <a name="see-also"></a>Vea también
[Información general del diseñador de formularios controlado por modelos](form-designer-overview.md)  
[Crear o editar formularios usando el diseñador de formularios](create-and-edit-forms.md)  
[Agregar, mover o eliminar campos en un formulario usando el diseñador de formularios](add-move-or-delete-fields-on-form.md)  
[Agregar, mover o eliminar secciones en un formulario usando el diseñador de formularios](add-move-or-delete-sections-on-form.md)  
[Propiedades disponibles en el diseñador de formularios](form-designer-properties.md)  
[Use la vista de árbol del diseñador de formularios](using-tree-view-on-form.md)  
[Crear y editar campos](../common-data-service/create-edit-field-portal.md) 
