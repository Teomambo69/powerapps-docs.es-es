---
title: Crear y editar formularios usando el diseñador de formularios controlado por modelos | MicrosoftDocs
ms.custom: ''
ms.date: 12/13/2018
ms.reviewer: ''
ms.service: crm-online
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

# <a name="create-and-edit-forms-using-the-form-designer"></a>Crear y editar formularios usando el diseñador de formularios 
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Use el nuevo diseñador de formularios para crear y para diseñar formularios para aplicaciones controladas por formularios.

> [!IMPORTANT]
> El nuevo diseñador de formularios controlado por modelos actualmente solo admite crear y editar los formularios principales. Más información: [Tipos de formularios](types-forms.md)

## <a name="create-a-form"></a>Crear un formulario 
1. Iniciar sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). 
2. En el panel de navegación izquierdo, expanda **Datos**, y seleccione **Entidades**. 
3. Seleccione una endidad como la entidad de contable y luego seleccione la pestaña **Formularios**. 
4. Seleccione **Agregar formulario** y, a continuación seleccione **Formulario principal (vista previa)**.     
    El contenido del nuevo formulario se rellena mediante la definición de formulario principal existente. Si existen varios formularios principales, el formulario superior de la lista del orden de formularios se usa para completar el nuevo formulario. 
5. Seleccione **Guardar** para guardar el formulario, o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios de la aplicación.  

## <a name="edit-a-form"></a>Editar un formulario 
1. Iniciar sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). 
2. En el panel de navegación izquierdo, seleccione **Datos**, y seleccione **Entidades**. 
3. Seleccione una endidad como la entidad de contable y luego seleccione la pestaña **Formularios**.
4. Seleccione el formulario que desea editar y luego seleccione **Editar formulario (vista previa)**.  
   O bien seleccione **...** al lado del formulario que quiere y luego seleccione **Editar formulario (vista previa)**. 
5. Seleccione **Guardar** para guardar el formulario, o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios de la aplicación. 

## <a name="add-and-remove-fields"></a>Agregar y eliminar campos 
Para agregar o quitar campos de un formulario, use el panel de Campos . El panel de campos le permite buscar y filtrar y le ayuda a encontrar rápidamente campos. También incluye la opción de mostrar sólo los campos no usados. 

### <a name="add-a-field"></a>Agregar un campo
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](#create-a-form) y [editar un formulario](#edit-a-form)
2. En la vista previa de formulario, seleccione otro campo o sección existente. 
    - Cuando selecciona un campo existente, el nuevo campo se agrega por debajo del campo existente. 
    - Cuando seleccione una sección, el nuevo campo se agrega en un espacio disponible para distribuir uniformemente campos a través de las columnas. 
3. Seleccione **Agregar campo**, o en el panel izquierdo, seleccione **Campos**.  
   El panel de campos está abierto de forma predeterminada cuando se abre el diseñador de formularios. 
4. En el panel **Campos**, busque, filtre o desplácese para encontrar el campo que desee agregar. 
   Si no encuentra un campo, puede que esté ya en el formulario. Desactive **Mostrar solo los campos no usados** para ver todos los campos, incluidos los que ya están agregados al formulario. 
5. En el panel **Campos** , seleccione un campo para agregarlo al formulario. <br />
   Como alternativa, seleccione **...** junto al campo que desee y, a continuación seleccione **Agregar a la sección seleccionada**. 
6. Seleccione **Guardar** para guardar el formulario, o seleccione **Publicar** si desea guardar los cambios y hacer sean visibles para los usuarios finales. 

### <a name="remove-a-field"></a>Quitar un campo
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](#create-a-form) y [editar un formulario](#edit-a-form)
2. En la vista previa de formularios, seleccione el campo que desee quitar del formulario. 
3. Seleccione **Eliminar**. <br />
4. Seleccione **Guardar**. 

    > [!NOTE]
    >   -  Si quita un campo por error, seleccione **Deshacer** para revertir la acción. 
    >   -  No puede quitar un campo obligatorio o que esté bloqueado. 

## <a name="add-and-remove-tabs-and-sections"></a>Agregar y quitar fichas y las secciones 
Para agregar o quitar una ficha o una sección de un formulario, use el panel de diseños . 

### <a name="add-a-tab"></a>Agregar una ficha
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](#create-a-form) y [editar un formulario](#edit-a-form) 
2. En la vista previa de formulario, seleccione otra ficha o el formulario. 
    - Cuando selecciona una ficha existente, la nueva ficha se agregará a la derecha de la ficha existente. 
    - Cuando se selecciona el formulario, la nueva ficha se agregará como la ficha más a la derecha del formulario. 
3. Seleccione **Agregar control**, o en el panel izquierdo, seleccione **Diseños**.  
4. En el panel **Diseños**, seleccione un control de la ficha, como **ficha de 2 columas**, para agregarlo al formulario. <br />
   Como alternativa, seleccione **...** junto al control de ficha que desee y, a continuación seleccione **Agregar a formulario**.  
5. Seleccione **Guardar**. 


### <a name="remove-a-tab"></a>Quitar una ficha
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](#create-a-form) y [editar un formulario](#edit-a-form)
2. En la vista previa del formulario, seleccione la ficha que desee eliminar y haga clic en **Eliminar**. 
3. Seleccione **Guardar**. 
    > [!NOTE]
    >    - Si elimina una pestaña por error, seleccione **Deshacer** para revertir la acción de eliminación. 
    >     - Un formulario debería tener al menos una ficha. No puede eliminar una pestaña que sea la única ficha del formulario. 
    >    - No puede eliminar una pestaña que tenga secciones bloqueadas. 
    >    - No puede eliminar una pestaña que tenga secciones con campos obligatorios o bloqueados. 

### <a name="add-a-section"></a>Agregar una sección 
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](#create-a-form) y [editar un formulario](#edit-a-form)
2. En la vista previa de formulario, seleccione otra sección o ficha existente. 
    - Cuando selecciona un campo existente, la nueva sección se agregará por debajo de la sección existente. 
    - Si selecciona una ficha, la nueva sección se agregará en la parte inferior de la primera columna de la ficha. 
3. Seleccione **Agregar control**, o en el panel izquierdo, seleccione **Diseños**.
4. En el panel **Diseños** , seleccione un control de sección para agregarlo al formulario. <br />
   Como alternativa, seleccione **...** junto al control de selección que desee y, a continuación seleccione **Agregar a la pestaña seleccionada**.      
5. Seleccione **Guardar**. 
 

### <a name="delete-a-section"></a>Eliminar una sección 
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](#create-a-form) y [editar un formulario](#edit-a-form) 
2. En la vista previa del formulario, seleccione la sección que desee eliminar y haga clic en **Eliminar**.  
3. Seleccione **Guardar**. 
    > [!NOTE]
    >    - Si elimina una sección por error, seleccione **Deshacer** para revertir la acción de eliminación. 
    >    - Una pestaña necesita tener al menos una sección en cada columna.  
    >    - No puede eliminar una sección si es la única en la columna de la ficha. 
    >    - No puede eliminar una sección que esté bloqueada. 
    >    - No puede eliminar una sección que tenga campos obligatorios o bloqueados. 
 
## <a name="use-the-tree-view"></a>Use la vista de árbol 
El panel de vista de árbol muestra una jerarquía visual de controles y de los campos del formulario. Los iconos en la ayuda de la vista de árbol ayudan a identificar rápidamente el tipo de campo o de control. 

También puede usar la vista de árbol para seleccionar los campos y los controles presentes en el formulario. La vista de árbol resulta útil cuando desea seleccionar elementos ocultos y que, por lo tanto, no aparecen en la vista previa de formulario. 

Puede expandir o contraer nodos en la vista de árbol para ver u ocultar los elementos de un nodo. Cuando selecciona un elemento de la vista de árbol, pasa a destacarse en la vista previa del formulario, y el panel de propiedades muestra las propiedades del elemento. 

   ![Vista de árbol](media/tree-view.png)

### <a name="open-the-tree-view"></a>Abra la vista de árbol 
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](#create-a-form) y [editar un formulario](#edit-a-form)  
2. En el panel izquierdo, seleccione **Vista de árbol**.

## <a name="see-also"></a>Vea también
[Información general del diseñador de formularios controlado por modelos](form-designer-overview.md) <br />
[Crear y editar campos](../common-data-service/create-edit-field-portal.md)
