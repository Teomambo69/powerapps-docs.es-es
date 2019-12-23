---
title: Agregar, configurar, mover o eliminar campos de un formulario | MicrosoftDocs
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
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d711a46676003786363f3496515dbd387024dadb
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2860695"
---
# <a name="add-configure-move-or-delete-fields-on-a-form"></a>Agregar, configurar, mover o eliminar campos de un formulario  
Agregar, configurar, mover o eliminar campos usando el diseñador de formularios.

## <a name="add-fields-to-a-form"></a>Agregar campos a un formulario
Para agregar campos a un formulario, use el panel **Campos**. El panel **Campos** le permite buscar y filtrar y le ayuda a encontrar rápidamente campos. También incluye la opción de mostrar sólo los campos no usados. 

> [!div class="mx-imgBorder"] 
>    ![](media/FormDesignerFieldsPane.png "Fields pane")

### <a name="add-fields-to-a-form-using-drag-and-drop"></a>Agregar campos a un formulario mediante arrastrar y colocar
> [!NOTE]
> Cuando se agregan o mueven campos utilizando arrastrar y colocar tenga en cuenta que la vista previa de formularios es dinámica y puede representar columnas de varias secciones como apiladas. Para asegurarse de que el campo que se agrega o mueve está en la columna de la sección correcta, colóquelo o péguelo anclado a otro campo que ya esté en esa columna de sección.
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la barra de comandos, seleccione **Agregar campo**, o en el panel izquierdo, seleccione **Campos**.  El panel **Campos** está abierto de forma predeterminada cuando se abre el diseñador de formularios. 
3. En el panel **Campos**, busque, filtre o desplácese para encontrar el campo que desee agregar. Si no encuentra un campo, puede que esté ya en el formulario. Desactive **Mostrar solo los campos no usados** para ver todos los campos, incluidos los ya agregados al formulario. 
4. En el panel **Campos**, seleccione un campo y arrástrelo sobre la vista previa de formulario. Cuando arrastra el campo sobre la vista previa de formulario verá destinos de colocación en los que podrá agregar el campo. 
5. Coloque el campo en la ubicación que desea. Tenga en cuenta lo siguiente: 
    - Los campos se pueden colocar antes o después de cualquier componente o campo existente.
    - Los campos también se pueden colocar en el área vacía de una sección. En este caso, el campo se agregará en un espacio disponible para distribuir uniformemente campos y componentes a través de las columnas de sección.
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

## <a name="configure-fields-on-a-form"></a>Configurar campos en un formulario
Éstas son las propiedades disponibles para configurar un campo cuando crea o edita un formulario usando el diseñador de formularios.

## <a name="field-properties"></a>Propiedades de campo

|Área  |Nombre  |Descripción  |
|---------|---------|---------|
|**Opciones de visualización** | **Etiqueta de campo** | De forma predeterminada, la etiqueta se corresponderá con el nombre para mostrar del campo. Puede reemplazar ese nombre para el formulario proporcionando otra etiqueta aquí. <br /><br />Se requiere esta propiedad. |
|**Opciones de visualización** |  **Nombre del campo** | Nombre del campo. Esto procede de las propiedades de campo de la entidad y es de solo lectura. |
|**Opciones de visualización** | **Ocultar etiqueta** | Cuando se selecciona, la etiqueta del campo está oculta. |
|**Opciones de visualización** | **Campo de solo lectura** | Cuando se selecciona, el valor del campo no es editable. |
|**Opciones de visualización** | **Bloquear campo** |  Bloquee este campo para que no se pueden quitar. |
|**Opciones de visualización** | **Ocultar campo** | Cuando se selecciona, el campo está oculto de forma predeterminada y se puede mostrar con código. |
|**Opciones de visualización** | **Ocultar en teléfono** | El campo se puede ocultar para representar una versión condensada del formulario en pantallas de teléfono. |
|**Formato** | **Ancho de campo** |  Cuando la sección que contiene los campos tiene más de una columna puede establecer el campo para ocupar hasta el número de columnas que tiene la sección. |

## <a name="move-fields-on-a-form"></a>Mover campos de un formulario
Puede mover un campo en un formulario mediante arrastrar y colocar o cortar y pegar acciones. 

### <a name="move-fields-on-a-form-using-drag-and-drop"></a>Mover campos en un formulario mediante arrastrar y colocar
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En a vista previa de formulario, seleccione el campo que desea mover y arrástrelo y colóquelo. Cuando arrastra el campo sobre la vista previa de formulario verá destinos de colocación a los que podrá mover el campo. 
   Tenga en cuenta lo siguiente:
    - Los campos se pueden colocar antes o después de cualquier componente o campo existente.
    - Los campos también se pueden colocar en el área vacía de una sección. En este caso, el campo se agregará en un espacio disponible para distribuir uniformemente campos y componentes a través de las columnas de sección.
    - Si mantiene el puntero sobre un encabezado de pestaña cuando arrastra un campo cambiará la pestaña actualmente seleccionada, permitiendo que agregue el campo a una pestaña diferente.   
3. Repita el paso 2 anterior si desea mover más campos.
4. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

### <a name="move-fields-on-a-form-using-cut-and-paste"></a>Mover campos en un formulario mediante cortar y pegar
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formulario, seleccione el campo que desee mover.
3. En la barra de comandos, seleccione **Cortar**.
4. En la vista previa de formulario, seleccione otro componente, campo o sección existente. También puede cambiar a una pestaña diferente si es necesario.
5. En la barra de comandos, seleccione **Pegar** o seleccione el botón de contenido adicional, y después seleccione **Pegar delante**.      Tenga en cuenta lo siguiente:
     - Cuando selecciona **Pegar**, el campo movido se pega después del componente o campo existente. 
     - Cuando selecciona **Pegar delante**, el campo movido se pega delante del componente o campo existente.
     - Cuando seleccione una sección, el campo que se está moviendo se agrega en un espacio disponible para distribuir uniformemente componentes y campos a través de las columnas de sección. La acción **Pegar delante** no es aplicable y por tanto no está disponible en este caso.
6. Repita los pasos 2-5 anteriores si desea mover más campos.
7. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

## <a name="delete-fields-on-a-form"></a>Eliminar campos de un formulario
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formularios, seleccione el campo que desee eliminar del formulario. 
3. En la barra de comandos, seleccione **Eliminar**. 
4. Repita los pasos 2-3 si desea eliminar más campos.
5. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

     > [!NOTE]
     >   -  Si elimina un campo por error, en la barra de comandos seleccione **Deshacer** para revertir el formulario al estado anterior. 
     >   -  No puede eliminar un campo que esté bloqueado o sea obligatorio y no se encuentra presente en ninguna otra parte del formulario. 

## <a name="create-a-new-field-on-the-entity-when-editing-a-form"></a>Crear un nuevo campo de la entidad al editar un formulario 
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la barra de comandos, seleccione **Agregar campo**, o en el panel izquierdo, seleccione **Campos**. El panel **Campos** está abierto de forma predeterminada cuando se abre el diseñador de formularios. 
3. En el panel **Campos**, seleccione **+ Nuevo campo**.
4. En el diálogo **Nuevo campo**, proporcione **el Nombre para mostrar** y **Nombre** para el campo.
5. En el diálogo **Nuevo campo**, seleccione **Tipo de datos** y configure cualquier otra propiedad necesaria del campo.

     > [!NOTE]
     >   -  Algunos tipos de campos no están disponibles cuando crea un campo desde el diseñador de formularios. Si un tipo de campo que desea no está disponible, puede seguir los pasos que se describen en [Crear y editar campos para Common Data Service usando el portal de Power Apps](../common-data-service/create-edit-field-portal.md)

6. Seleccione **Hecho** para crear un nuevo campo de la entidad. El campo aparece en el panel **Campos**.
7. Si desea agregar el campo recién creado al formulario, siga los pasos indicados en la sección [**Agregar campos a un formulario**](add-move-or-delete-fields-on-form.md#add-fields-to-a-form).

     > [!NOTE]
     >  Cuando un campo se crea en la entidad, no está limitado al formulario actual y estará disponible para su uso en otros sitios.

### <a name="see-also"></a>Vea también
[Información general del diseñador de formularios controlado por modelos](form-designer-overview.md)  
[Crear, editar o configurar formularios usando el diseñador de formularios](create-and-edit-forms.md)  
[Agregar, configurar, mover o eliminar componentes de un formulario](add-move-configure-or-delete-components-on-form.md)  
[Agregar, configurar, mover o eliminar secciones de un formulario](add-move-or-delete-sections-on-form.md)  
[Agregar, configurar, mover o eliminar pestañas de un formulario](add-move-or-delete-tabs-on-form.md)  
[Configurar propiedades de encabezado en el diseñador de formularios](form-designer-header-properties.md)  
[Agregar y configurar un componente de subcuadrícula en un formulario](form-designer-add-configure-subgrid.md)  
[Agregar y configurar un componente de vista rápida en un formulario](form-designer-add-configure-quickview.md)  
[Configurar un componente de búsqueda en un formulario](form-designer-add-configure-lookup.md)  
[Use la vista de árbol del diseñador de formularios](using-tree-view-on-form.md)  
[Crear y editar campos](../common-data-service/create-edit-field-portal.md)  
