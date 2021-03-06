---
title: Agregar y configurar un componente de vista rápida en un formulario | MicrosoftDocs
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
ms.openlocfilehash: 758a7d2ce925526e5c0e7062f1e5134ac519e9eb
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2868267"
---
# <a name="add-and-configure-a-quick-view-component-on-a-form"></a>Agregar y configurar un componente de vista rápida en un formulario  
Un formulario principal que muestra los detalles de un registro puede usar un componente de vista rápida para mostrar detalles de solo lectura de un registro relacionado (consulta). Los datos mostrados por el componente de vista rápida están definidos por el formulario de vista rápida de la entidad relacionada. Cuando no hay ningún registro relacionado, como una consulta, el componente de vista rápida se oculta automáticamente.

## <a name="add-a-quick-view-component"></a>Agregar un componente de vista rápida
Puede agregar un componente de vista rápida de la misma forma que agrega cualquier otro componente. Más información: [Agregar, configurar, mover o eliminar componentes de un formulario](add-move-configure-or-delete-components-on-form.md)

## <a name="configure-a-quick-view-component"></a>Configurar un componente de vista rápida
Éstas son las propiedades disponibles para configurar cuando utiliza un componente de vista rápida en un formulario usando el diseñador de formularios.


<!--note from editor: "Drop-down" should be used only as an adjective. In the following table, is it a list? A menu? (It's used three times in line 44.) --> 


|Área   |Nombre  |Descripción  |
|---------|---------|---------|
|**Opciones de visualización** | **Etiqueta** | Etiqueta localizable de la vista rápida visible para los usuarios. <br /><br /> Se requiere esta propiedad. |
| **Opciones de visualización** | **Nombre** |  El nombre único de la vista rápida que se usa al hacerle referencia en los scripts. El nombre solo puede contener caracteres alfanuméricos y de subrayado. <br /> <br />Se requiere esta propiedad. |
| **Opciones de visualización**  | **Ocultar etiqueta** |  Cuando se selecciona, la etiqueta de la vista rápida está oculta. |
| **Opciones de visualización**  | **Formularios de vista rápida** |  Una lista de formularios de vista rápida que se muestran a los usuarios de la aplicación. <br /><br />Para configurar la lista de formularios de vista rápida <br /><br /> Seleccione **Seleccionar formularios…** y en el desplegable **Búsqueda** seleccione un campo de búsqueda donde desea mostrar un formulario de vista rápida. <br /><br />Según el campo de búsqueda que seleccione en el desplegable **Búsqueda**, verá desplegables que le permitan seleccionar formularios de vista rápida para una o varias entidades. |

## <a name="see-also"></a>Vea también
[Información general del diseñador de formularios controlado por modelos](form-designer-overview.md)  
[Crear, editar o configurar formularios usando el diseñador de formularios](create-and-edit-forms.md)  
[Agregar, configurar, mover o eliminar campos de un formulario](add-move-or-delete-fields-on-form.md)  
[Agregar, configurar, mover o eliminar componentes de un formulario](add-move-configure-or-delete-components-on-form.md)  
[Agregar, configurar, mover o eliminar secciones de un formulario](add-move-or-delete-sections-on-form.md)  
[Agregar, configurar, mover o eliminar pestañas de un formulario](add-move-or-delete-tabs-on-form.md)  
[Configurar propiedades de encabezado en el diseñador de formularios](form-designer-header-properties.md)  
[Agregar y configurar un componente de subcuadrícula en un formulario](form-designer-add-configure-subgrid.md)  
[Configurar un componente de búsqueda en un formulario](form-designer-add-configure-lookup.md)  
[Use la vista de árbol del diseñador de formularios](using-tree-view-on-form.md)  
[Crear y editar campos](../common-data-service/create-edit-field-portal.md)  
