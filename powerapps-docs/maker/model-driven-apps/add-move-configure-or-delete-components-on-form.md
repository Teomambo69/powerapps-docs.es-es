---
title: Agregar, configurar, mover o eliminar componentes de un formulario | MicrosoftDocs
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
ms.openlocfilehash: a40b0b9e5fc64856be931a2407a451c8d27ef8ec
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2702387"
---
# <a name="add-configure-move-or-delete-components-on-a-form"></a>Agregar, configurar, mover o eliminar componentes de un formulario  
Gracias al diseñador de formularios, los fabrticantes pueden agregar y configurar fácilmente componentes populares, como [subcuadrícula](form-designer-add-configure-subgrid.md), [vista rápida](form-designer-add-configure-quickview.md), control de mando esférico, control deslizante lineal, etc.

## <a name="add-components-to-a-form"></a>Agregar componentes a un formulario
Para agregar componentes a un formulario, use el panel **Componentes**. El panel **Componentes** además le permite buscar buscar rápidamente componentes.  

> [!div class="mx-imgBorder"] 
> ![](media/FormDesignerComponentsPane.PNG "Components pane")

### <a name="add-components-to-a-form-using-drag-and-drop"></a>Agregar componentes a un formulario mediante arrastrar y colocar
> [!NOTE]
> Cuando se agregan o mueven componentes utilizando arrastrar y colocar tenga en cuenta que la vista previa de formularios es dinámica y puede representar columnas de varias secciones como apiladas. Para asegurarse de que el componente que se agrega o mueve está en la columna de la sección correcta, colóquelo o péguelo anclado a otro campo o componente que ya esté en esa columna de sección.
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la barra de comandos, seleccione **Agregar componente**, o en el panel izquierdo, seleccione **Componentes** para ver una lista de componentes disponibles. También puede mantener el mouse sobre un componente de la lista para ver una imagen de vista previa, la descripción, y otros detalles de ese componente.
3. En el panel **Componentes**, busque o desplácese para buscar el componente que desea agregar y a continuación selecciónelo.
4. Arrastre y coloque el componente sobre la vista previa de formularios. Cuando arrastra el componente sobre la vista previa de formulario verá destinos de colocación en los que podrá agregar el componente. 

   Tenga en cuenta lo siguiente: 
    - Los componentes se pueden colocar antes o después de cualquier componente o campo existente.
    - Los componentes también se pueden colocar en el área vacía de una sección. En este caso, el componente se agregará en un espacio disponible para distribuir uniformemente campos y componentes a través de las columnas de sección.
    - Si mantiene el puntero sobre un encabezado de sección cuando arrastra un componente cambiará la pestaña actualmente seleccionada, permitiendo que agregue el componente a una pestaña diferente.
    - Cuando quita el componente, en la mayoría de los casos, verá un diálogo para establecer las propiedades del componente. Asegúrese de que haya configurado todas las propiedades necesarias del componente. 
5. En el cuadro de diálogo para establecer las propiedades del componente, en **Mostrar el componente en**, las opciones **Web**, **Móvil** y **Tableta** se seleccionan de forma predeterminada para garantizar que se usa el componente cuando el formulario se muestra en la web, aplicación móvil, y aplicación de tableta. En función de sus requisitos puede borrar algunas de estas opciones para restringir el uso del componente. Seleccione **Listo**.
6. Repita los pasos 3-5 anteriores para agregar más componentes.
7. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

### <a name="add-components-for-a-field-on-the-form"></a>Agregue componentes a un campo en el formulario
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formulario, seleccione un campo existente.
3. En el panel de propiedad, en el área **Componentes**, seleccione **+ Componente**.
4. El diálogo **Agregar componente** muestra una lista de componentes que estén disponibles para el tipo de campo actual. Puede mantener el mouse sobre un componente de la lista para ver una imagen de vista previa, la descripción, y otros detalles de ese componente.
5. En el diálogo **Agregar componente**, busque o desplácese para buscar el componente que desea agregar y a continuación selecciónelo.
   En la mayoría de los casos, aparece un diálogo para poder establecer las propiedades del componente. Asegúrese de que haya configurado todas las propiedades necesarias del componente.
6. En el cuadro de diálogo para establecer las propiedades del componente, en **Mostrar el componente en**, las opciones **Web**, **Móvil** y **Tableta** se seleccionan de forma predeterminada para garantizar que se usa el componente cuando el formulario se muestra en la web, aplicación móvil, y aplicación de tableta. En función de sus requisitos puede borrar algunas de estas opciones para restringir el uso del componente. Seleccione **Listo**.
7. Repita los pasos 2-6 anteriores si desea agregar más componentes al mismo campo o a otro.
8. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios.

## <a name="configure-components-on-a-form"></a>Configure los componentes en un formulario
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formulario, seleccione un campo existente.
3. En el panel de propiedad, en el área **Componentes**, seleccione el componente que desee configurar.
4. Es posible que vea un diálogo para establecer las propiedades del componente. Cambie las propiedades del componente según sea necesario y seleccione **Hecho**.
5. Repita los pasos 2-4 para configurar más componentes del mismo campo o de otro.
6. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios.

## <a name="move-components-on-a-form"></a>Mover componentes de un formulario
Puede mover componentes en un formulario mediante arrastrar y colocar o cortar y pegar acciones. 

### <a name="move-components-on-a-form-using-drag-and-drop"></a>Mover componentes en un formulario mediante arrastrar y colocar
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En a vista previa de formulario, seleccione el componente que desea mover y arrástrelo y colóquelo. Cuando arrastra el componente sobre la vista previa de formulario aparecerán destinos de colocación en los que podrá mover el componente.     

   Tenga en cuenta lo siguiente: 
    - Los componentes se pueden colocar antes o después de cualquier componente o campo existente.
    - Los componentes también se pueden colocar en el área vacía de una sección. En este caso, el componente se agregará en un espacio disponible para distribuir uniformemente componentes y campos a través de las columnas de sección.
    - Si mantiene el puntero sobre un encabezado de sección cuando arrastra un componente cambiará la pestaña actualmente seleccionada, permitiendo que agregue el componente a una pestaña diferente.   
4. Repita los pasos 2-3 anteriores para mover más componentes.
5. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

### <a name="move-components-on-a-form-using-cut-and-paste"></a>Mover componentes en un formulario mediante cortar y pegar
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formulario, seleccione el componente que desee mover.
3. En la barra de comandos, seleccione **Cortar**.
4. En la vista previa de formulario, seleccione otro componente, campo o sección existente. Puede cambiar a una pestaña diferente si es necesario.
5. En la barra de comandos, seleccione **Pegar** o seleccione el botón de contenido adicional, y después seleccione **Pegar delante**.     

   Tenga en cuenta lo siguiente:
    - Cuando selecciona **Pegar**, el componente movido se pega después del componente o campo existente. 
    - Cuando selecciona **Pegar delante**, el componente movido se pega delante del componente o campo existente.
    - Cuando seleccione una sección, el componente que se está moviendo se agrega en un espacio disponible para distribuir uniformemente componentes y campos a través de las columnas de sección. La acción **Pegar delante** no es aplicable y por tanto no está disponible en este caso.
6. Repita los pasos 2-5 anteriores si desea mover más componentes.
7. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

## <a name="delete-components-on-a-form"></a>Eliminar componentes de un formulario
1. Abra el diseñador de formularios para crear o editar un formulario. Más información: [Crear un formulario](create-and-edit-forms.md#create-a-form) o [Editar un formulario](create-and-edit-forms.md#edit-a-form)
2. En la vista previa de formularios, seleccione el componente que desea eliminar del formulario y, en la barra de comandos, seleccione **Eliminar**. 
3. Repita el paso 2 anterior si desea eliminar más componentes.
4. En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios. 

     > [!NOTE]
     >   -  Si elimina un componente por error, en la barra de comandos seleccione **Deshacer** para revertir el formulario al estado anterior. 
     >   -  No puede eliminar un componente que esté bloqueado ni usar un campo obligatorio que no se encuentra presente en ninguna otra parte del formulario. 

### <a name="see-also"></a>Vea también
[Información general del diseñador de formularios controlado por modelos](form-designer-overview.md)  
[Crear, editar o configurar formularios usando el diseñador de formularios](create-and-edit-forms.md)  
[Agregar, configurar, mover o eliminar campos de un formulario](add-move-or-delete-fields-on-form.md)  
[Agregar, configurar, mover o eliminar secciones de un formulario](add-move-or-delete-sections-on-form.md)  
[Agregar, configurar, mover o eliminar pestañas de un formulario](add-move-or-delete-tabs-on-form.md)  
[Configurar propiedades de encabezado en el diseñador de formularios](form-designer-header-properties.md)  
[Agregar y configurar un componente de subcuadrícula en un formulario](form-designer-add-configure-subgrid.md)  
[Agregar y configurar un componente de vista rápida en un formulario](form-designer-add-configure-quickview.md)  
[Configurar un componente de búsqueda en un formulario](form-designer-add-configure-lookup.md)  
[Use la vista de árbol del diseñador de formularios](using-tree-view-on-form.md)  
[Crear y editar campos](../common-data-service/create-edit-field-portal.md)  
