---
title: Crear, editar o configurar formularios usando el diseñador de formularios controlado por modelos | MicrosoftDocs
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
ms.openlocfilehash: c357649ba68e6bce1b9df51d9601507c337afd31
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752518"
---
# <a name="create-edit-or-configure-forms-using-the-form-designer"></a>Crear, editar o configurar formularios usando el diseñador de formularios 
Use el nuevo diseñador de formularios para crear, editar o configurar formularios para aplicaciones controladas por formularios. 

> [!IMPORTANT]
> El nuevo diseñador de formularios controlado por modelos actualmente no permite editar los formularios de tarjeta. Más información: [Tipos de formularios](types-forms.md)

## <a name="create-a-form"></a>Crear un formulario 
1. Inicie sesión en [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). 
2. En el panel de navegación izquierdo, expanda **Datos**, y seleccione **Entidades**. 
3. Seleccione una endidad como la entidad de contable y luego seleccione la pestaña **Formularios**. 
4. Seleccione **Agregar formulario** y, a continuación, seleccione una de las opciones siguientes
    - **Formulario principal**  
    El contenido del nuevo formulario se rellena mediante la definición de formulario principal existente. Si existen varios formularios principales, el formulario superior de la lista del orden de formularios se usa para completar el nuevo formulario. 
    - **Formulario de creación rápida**
    - **Formulario de vista rápida**
5. Cuando termine de realizar cambios en el formulario, seleccione **Guardar** para guardar el formulario, o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios de la aplicación.  

## <a name="edit-a-form"></a>Editar un formulario 
1. Inicie sesión en [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). 
2. En el panel de navegación izquierdo, expanda **Datos**, y seleccione **Entidades**. 
3. Seleccione una endidad como la entidad de contable y luego seleccione la pestaña **Formularios**.
4. Seleccione el nombre del formulario que desea editar.  
    - También puede seleccionar la fila de un formulario y, en la barra de comandos, seleccionar **Editar formulario**
    - Otra alternativa consiste en seleccionar **...** junto al nombre del formulario y, en el menú, seleccionar **Editar formulario**. 
5. Cuando termine de realizar cambios en el formulario, seleccione **Guardar** para guardar el formulario, o seleccione **Publicar** si desea guardar y hacer que los cambios sean visibles para los usuarios de la aplicación. 

## <a name="configure-a-form"></a>Configurar un formulario
Éstas son las propiedades disponibles para configurar un formulario cuando crea o edita un formulario usando el diseñador de formularios.

|Nombre  |Descripción  |
|---------|---------|
|**Título**  | Escriba un nombre que tenga significado para otros creadores y usuarios de la aplicación. Este nombre se muestra los usuarios de la aplicación. Si los usuarios tienen acceso a varios formularios para una entidad, usarán este nombre para diferenciar entre los formularios disponibles. <br /><br />Se requiere esta propiedad. |
|**Descripción** |  Escriba una descripción que explique las diferencias del formulario respecto de otros formularios principales. Esta descripción se muestra solo a los creadores en la lista de formularios de una entidad en el explorador de soluciones. |
|**Ancho máx.** | Establezca el ancho máximo (en píxeles) para limitar el ancho del formulario. El valor predeterminado es 1900. <br /><br />Se requiere esta propiedad. |
|**Mostrar imagen** | Mostrar la **Imagen principal** de la entidad si tiene una establecida. Este valor permitirá mostrar el campo de imagen en el encabezado del formulario. <br /><br /> Consulte Habilitar o deshabilitar opciones de entidad para obtener más información acerca de las opciones de la entidad. |

## <a name="see-also"></a>Vea también
[Información general del diseñador de formularios controlado por modelos](form-designer-overview.md)  
[Agregar, configurar, mover o eliminar campos de un formulario](add-move-or-delete-fields-on-form.md)  
[Agregar, configurar, mover o eliminar componentes de un formulario](add-move-configure-or-delete-components-on-form.md)  
[Agregar, configurar, mover o eliminar secciones de un formulario](add-move-or-delete-sections-on-form.md)  
[Agregar, configurar, mover o eliminar pestañas de un formulario](add-move-or-delete-tabs-on-form.md)  
[Configurar propiedades de encabezado en el diseñador de formularios](form-designer-header-properties.md)  
[Agregar y configurar un componente de subcuadrícula en un formulario](form-designer-add-configure-subgrid.md)  
[Agregar y configurar un componente de vista rápida en un formulario](form-designer-add-configure-quickview.md)  
[Configurar un componente de búsqueda en un formulario](form-designer-add-configure-lookup.md)  
[Use la vista de árbol del diseñador de formularios](using-tree-view-on-form.md)  
[Crear y editar campos](../common-data-service/create-edit-field-portal.md)  
