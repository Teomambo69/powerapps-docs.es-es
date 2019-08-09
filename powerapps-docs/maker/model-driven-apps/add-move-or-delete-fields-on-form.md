---
title: 'Agregar, mover o eliminar campos de un formulario | MicrosoftDocs'
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

# <a name="add-move-or-delete-fields-on-a-form"></a>Agregar, mover o eliminar campos de un formulario  
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Agregue, mueva, y elimine campos mediante el diseñador de formularios.

> [!NOTE]
> Cuando se agregan o mueven campos utilizando arrastrar y colocar tenga en cuenta que la vista previa de formularios es dinámica y puede representar columnas de varias secciones como apiladas. Para asegurarse de que el campo que se agrega o mueve está en la columna de la sección correcta, colóquelo o péguelo anclado a otro campo que ya esté en esa columna de sección.

## <a name="add-fields-to-a-form"></a>Agregar campos a un formulario
Para agregar campos a un formulario, use el panel **Campos**. El panel **Campos** le permite buscar y filtrar y le ayuda a encontrar rápidamente campos. También incluye la opción de mostrar sólo los campos no usados. 

> [!div class="mx-imgBorder"] 
> ![](media/fields-pane.png "Panel Campos")

### <a name="add-fields-to-a-form-using-drag-and-drop"></a>Agregar campos a un formulario mediante arrastrar y colocar

1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la barra de comandos, seleccione **Agregar campo**, o en el panel izquierdo, seleccione **Campos**.  El panel **Campos** está abierto de forma predeterminada cuando se abre el diseñador de formularios. 
3. En el panel **Campos**, busque, filtre o desplácese para encontrar el campo que desee agregar. Si no encuentra un campo, puede que esté ya en el formulario. Desactive **Mostrar solo los campos no usados** para ver todos los campos, incluidos los ya agregados al formulario. 
4. En el panel **Campos**, seleccione un campo y arrástrelo sobre la vista previa de formulario. Cuando arrastra el campo sobre la vista previa de formulario verá destinos de colocación en los que podrá agregar el campo. 
5. Coloque el campo en la ubicación que desea. Tenga en cuenta lo siguiente: 
    - Los campos se pueden colocar antes o después de cualquier campo existente.
    - Los campos también se pueden colocar en el área vacía de una sección. En este caso, el campo se agregará en un espacio disponible para distribuir uniformemente campos a través de las columnas de sección.
    - Si mantiene el puntero sobre un encabezado de pestaña cuando arrastra un campo cambiará la pestaña actualmente seleccionada, permitiendo que agregue el campo a una pestaña diferente.   
6. Repita los pasos 3-5 anteriores si desea agregar más campos.
7. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

### <a name="add-fields-to-a-form-using-selection"></a>Agregar campos a un formulario utilizando selección 

1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formulario, seleccione otro campo o sección existente. Tenga en cuenta lo siguiente:
    - Cuando selecciona un campo existente, el nuevo campo se agrega después del campo existente. 
    - Cuando seleccione una sección, el nuevo campo se agrega en un espacio disponible para distribuir uniformemente campos a través de las columnas de sección. 
3. En la barra de comandos, seleccione **Agregar campo**, o en el panel izquierdo, seleccione **Campos**. El panel **Campos** está abierto de forma predeterminada cuando se abre el diseñador de formularios. 
4. En el panel **Campos**, busque, filtre o desplácese para encontrar el campo que desee agregar. Si no encuentra un campo, puede que esté ya en el formulario. Desactive **Mostrar solo los campos no usados** para ver todos los campos, incluidos los ya agregados al formulario. 
5. En el panel **Campos** , seleccione un campo para agregarlo al formulario. Como alternativa, seleccione **...** junto al campo que desee y, a continuación seleccione **Agregar a la sección seleccionada**. 
6. Repita los pasos 2-5 anteriores si desea agregar más campos.
7. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

## <a name="move-fields-on-a-form"></a>Mover campos de un formulario

### <a name="move-fields-on-a-form-using-drag-and-drop"></a>Mover campos en un formulario mediante arrastrar y colocar

1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En a vista previa de formulario, seleccione el campo que desea mover e inicie la acción de arrastrar. Cuando arrastra el campo sobre la vista previa de formulario verá destinos de colocación a los que podrá mover el campo. 
3. Coloque el campo en la ubicación que desea. Tenga en cuenta lo siguiente: 
    - Los campos se pueden colocar antes o después de cualquier campo existente.
    - Los campos también se pueden colocar en el área vacía de una sección. En este caso, el campo se agregará en un espacio disponible para distribuir uniformemente campos a través de las columnas de sección.
    - Si mantiene el puntero sobre un encabezado de pestaña cuando arrastra un campo cambiará la pestaña actualmente seleccionada, permitiendo que agregue el campo a una pestaña diferente.   
4. Repita los pasos 2-3 anteriores si desea mover más campos.
5. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

    > [!NOTE]
    >   Los campos móviles del encabezado y del pie de página mediante arrastrar y colocar aún no se admiten. 

### <a name="move-fields-on-a-form-using-cut-and-paste"></a>Mover campos en un formulario mediante cortar y pegar

1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formulario, seleccione el campo que desee mover.
3. En la barra de comandos, seleccione **Cortar**.
4. En la vista previa de formulario, seleccione otro campo o sección existente. También puede cambiar a una pestaña diferente si es necesario.
5. En la barra de comandos, seleccione **Pegar** o seleccione el botón de contenido adicional, y después seleccione **Pegar delante**. Tenga en cuenta lo siguiente:
    - Cuando selecciona **Pegar**, el campo movido se pega después del campo existente. 
    - Cuando selecciona **Pegar delante**, el campo movido se pega delante del campo existente.
    - Cuando seleccione una sección, el campo que se está moviendo se agrega en un espacio disponible para distribuir uniformemente campos a través de las columnas de sección. La acción **Pegar delante** no es aplicable y por tanto no está disponible en este caso.
6. Repita los pasos 2-5 anteriores si desea mover más campos.
7. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

## <a name="delete-fields-on-a-form"></a>Eliminar campos de un formulario
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formularios, seleccione el campo que desee eliminar del formulario. 
3. En la barra de comandos, seleccione **Eliminar**. 
4. Repita los pasos 2-3 anteriores si desea eliminar más campos.
5. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

     > [!NOTE]
     >   -  Si elimina un campo por error, en la barra de comandos seleccione **Deshacer** para revertir el formulario al estado anterior. 
     >   -  No puede eliminar un campo obligatorio o que esté bloqueado. 

### <a name="see-also"></a>Vea también
[Información general del diseñador de formularios controlado por modelos](form-designer-overview.md)  
[Crear o editar formularios usando el diseñador de formularios](create-and-edit-forms.md)  
[Agregar, mover o eliminar secciones en un formulario usando el diseñador de formularios](add-move-or-delete-sections-on-form.md)  
[Agregar, mover o eliminar pestañas en un formulario usando el diseñador de formularios](add-move-or-delete-tabs-on-form.md)  
[Propiedades disponibles en el diseñador de formularios](form-designer-properties.md)  
[Use la vista de árbol del diseñador de formularios](using-tree-view-on-form.md)  
[Crear y editar campos](../common-data-service/create-edit-field-portal.md)
