---
title: Agregar, configurar, mover o eliminar pestañas en un formulario usando el diseñador de formularios | MicrosoftDocs
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
ms.openlocfilehash: 0799fd352a17bb398f3f42444b9312fd90756caa
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2860674"
---
# <a name="add-configure-move-or-delete-tabs-on-a-form"></a>Agregar, configurar, mover o eliminar pestañas de un formulario  
Agregar, mover o eliminar pestañas en un formulario usando el diseñador de formularios.

## <a name="add-tabs-to-a-form"></a>Agregar pestañas a un formulario
Para agregar pestañas a un formulario, use el panel **Componentes**.  

> [!div class="mx-imgBorder"] 
> ![](media/FormDesignerComponentsLayout.png "Layout components")
   
  > [!NOTE]
  >  Solo se pueden agregar pestañas a los formularios principales. Más información: [Tipos de formularios](types-forms.md)

### <a name="add-tabs-to-a-form-using-drag-and-drop"></a>Agregar pestañas a un formulario mediante arrastrar y colocar
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la barra de comandos, seleccione **Agregar componente**, o en el panel izquierdo, seleccione **Componentes**. 
3. En el panel **Componente**, seleccione un componente de pestaña y arrástrelo y colóquelo sobre la vista previa de formulario.     Cuando arrastra la pestaña sobre la vista previa de formulario verá destinos de colocación en los que podrá agregar la pestaña. Tenga en cuenta lo siguiente: 
    - Las pestañas se pueden colocar antes o después de cualquier pestaña existente manteniendo el cursor sobre los encabezados de la pestaña.
    - Las pestañas también se pueden colocar antes o después de la pestaña actual manteniendo el cursor sobre el borde izquierdo o derecho de la pestaña actual.
4. Repita el paso 3 anterior si desea agregar más pestañas.
5. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

### <a name="add-tabs-to-a-form-using-selection"></a>Agregar pestañas a un formulario utilizando selección 
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formulario, seleccione otra pestaña o el formulario. Tenga en cuenta lo siguiente:
    - Cuando selecciona una pestaña existente, la nueva pestaña se agregará después de la pestaña existente. 
    - Cuando se selecciona el formulario, la nueva pestaña se agregará como la última pestaña del formulario. 
3. En la barra de comandos, seleccione **Agregar componente**, o en el panel izquierdo, seleccione **Componentes**.  
4. En el panel **Componentes**, seleccione un componente de pestaña para agregarlo al formulario. Como alternativa, seleccione **...** junto al componente de pestaña que desee y, a continuación seleccione **Agregar a formulario**. 
5. Repita los pasos 2-4 anteriores si desea agregar más pestañas.
6. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

## <a name="configure-tabs-on-a-form"></a>Configurar las pestañas en un formulario
Éstas son las propiedades disponibles para configurar una pestaña cuando crea o edita un formulario usando el diseñador de formularios.

|Área   |Nombre  |Descripción  |
|---------|---------|---------|
|**Opciones de visualización** | **Etiqueta de pestaña** | Etiqueta localizable de la pestaña visible para los usuarios. <br /><br />Se requiere esta propiedad. |
| **Opciones de visualización** |  **Nombre**  |  El nombre único de la pestaña que se usa al hacerle referencia en los scripts. El nombre solo puede contener caracteres alfanuméricos y de subrayado. <br /><br />Se requiere esta propiedad. |
| **Opciones de visualización** |  **Expandir esta ficha de forma predeterminada** |  El estado de la ficha puede alternar entre expandida o contraída usando scripts de formulario o cuando los usuarios seleccionan la etiqueta. Elija el estado predeterminado para la pestaña. |
| **Opciones de visualización** | **Ocultar pestaña** | Cuando se selecciona, la pestaña está oculta de forma predeterminada y se puede mostrar con código. |
| **Opciones de visualización** | **Ocultar en teléfono** |  La pestaña se puede ocultar para representar una versión condensada de este formulario en pantallas de teléfono. |
| **Formato** | **Diseño** |  Las pestañas pueden tener hasta tres columnas. Use las opciones para establecer el número de pestañas y qué porcentaje del ancho total deben ocupar. |

## <a name="move-tabs-on-a-form"></a>Mover pestañas en un formulario
Puede mover pestañas en un formulario mediante arrastrar y colocar o cortar y pegar acciones. 

### <a name="move-tabs-on-a-form-using-drag-and-drop"></a>Mover pestañas en un formulario mediante arrastrar y colocar
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En a vista previa de formulario, seleccione el encabezado de la pestaña que desea mover y arrástrelo y colóquelo. Cuando arrastra la pestaña sobre la vista previa de formulario verá destinos de colocación en los que podrá mover la pestaña. Tenga en cuenta lo siguiente:
    - Las pestañas se pueden colocar antes o después de cualquier pestaña existente manteniendo el cursor sobre los encabezados de la pestaña.
    - Las pestañas también se pueden colocar antes o después de la pestaña actual manteniendo el cursor sobre el borde izquierdo o derecho de la pestaña actual.
3. Repita el paso 2 si desea mover más pestañas.
4. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

### <a name="move-tabs-on-a-form-using-cut-and-paste"></a>Mover pestañas en un formulario mediante cortar y pegar
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formulario, seleccione la pestaña que desee mover.
3. En la barra de comandos, seleccione **Cortar**.
4. En la vista previa de formulario, seleccione otra pestaña o el formulario.
5. En la barra de comandos, seleccione **Pegar** o seleccione el botón de contenido adicional, y después seleccione **Pegar delante**.      Tenga en cuenta lo siguiente: 
    - Cuando selecciona **Pegar**, la pestaña movida se pega después de la pestaña existente. 
    - Cuando selecciona **Pegar delante**, la pestaña movida se pega delante de la pestaña existente.
    - Cuando se selecciona el formulario, la pestaña movida se agregará como la última pestaña del formulario. La acción **Pegar delante** no es aplicable y por tanto no está disponible en este caso.
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
[Crear, editar o configurar formularios usando el diseñador de formularios](create-and-edit-forms.md)  
[Agregar, configurar, mover o eliminar campos de un formulario](add-move-or-delete-fields-on-form.md)  
[Agregar, configurar, mover o eliminar componentes de un formulario](add-move-configure-or-delete-components-on-form.md)  
[Agregar, configurar, mover o eliminar secciones de un formulario](add-move-or-delete-sections-on-form.md)  
[Configurar propiedades de encabezado en el diseñador de formularios](form-designer-header-properties.md)  
[Agregar y configurar un componente de subcuadrícula en un formulario](form-designer-add-configure-subgrid.md)  
[Agregar y configurar un componente de vista rápida en un formulario](form-designer-add-configure-quickview.md)  
[Configurar un componente de búsqueda en un formulario](form-designer-add-configure-lookup.md)  
[Use la vista de árbol del diseñador de formularios](using-tree-view-on-form.md)  
[Crear y editar campos](../common-data-service/create-edit-field-portal.md)  
