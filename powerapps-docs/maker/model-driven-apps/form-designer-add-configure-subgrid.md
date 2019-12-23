---
title: Agregar y configurar un componente de subcuadrícula en un formulario | MicrosoftDocs
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
ms.openlocfilehash: da158d718754e30a5979b680cd5640c8449a20b2
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2868486"
---
<!-- note from editor: I recommend removing the hyphen from "sub-grid" based on the style guide entry for sub: https://styleguides.azurewebsites.net/Styleguide/Read?id=2700&topicid=28872. I didn't change it here because I don't know how wide an impact that might have. -->


# <a name="add-and-configure-a-sub-grid-component-on-a-form"></a>Agregar y configurar un componente de subcuadrícula en un formulario  
Un formulario que muestra los detalles de un registro puede usar un componente de subcuadrícula para mostrar la lista de registros relacionados o no relacionadas en un formato tabular. Los fabricantes pueden agregar y configurar un componente de subcuadrícula con el diseñador de formularios.

## <a name="add-a-sub-grid-component"></a>Agregar un componente de subcuadrícula
Puede agregar un componente de subcuadrícula de la misma forma que agrega cualquier otro componente. Más información: [Agregar, configurar, mover o eliminar componentes de un formulario](add-move-configure-or-delete-components-on-form.md)

## <a name="configure-a-sub-grid-component"></a>Configurar un componente de subcuadrícula
Éstas son las propiedades disponibles para configurar cuando utiliza un componente de subcuadrícula en un formulario usando el diseñador de formularios.


|Área   |Nombre  |Descripción  |
|---------|---------|---------|
| **Opciones de visualización** | **Etiqueta** | Etiqueta localizable de la subcuadrícula visible para los usuarios. <br /><br />Se requiere esta propiedad.|
| **Opciones de visualización** |  **Nombre** |  Nombre único de la subcuadrícula que se usa al hacerle referencia en los scripts. El nombre solo puede contener caracteres alfanuméricos y de subrayado. <br /><br />Se requiere esta propiedad. |
| **Opciones de visualización** | **Ocultar en teléfono** |  La subcuadrícula se puede ocultar para representar una versión condensada del formulario en pantallas de teléfono. |
| **Opciones de visualización** | **Mostrar registros relacionados** |  Cuando se seleccionada, la subcuadrícula muestra solo los registros relacionados con el registro actual que se muestra en el formulario. <br /><br />La lista desplegable **Entidad** también se filtra para enumerar únicamente las entidades relacionadas con la entidad actual. |
| **Opciones de visualización** | **Entidad** |  La entidad cuyos registros desea mostrar en la subcuadrícula. <br /><br />Cuando se selecciona **Mostrar registros relacionados**, la lista de entidades se filtra para mostrar únicamente las entidades relacionadas con la entidad actual. Además del nombre de entidad, el nombre del campo de búsqueda también se muestra entre paréntesis. |
| **Opciones de visualización** | **Vista predeterminada** |  La vista de la entidad seleccionada en la propiedad **Entidad** que se usará para obtener y mostrar la lista de registros en la subcuadrícula. |
| **Opciones de visualización** | **Permitir que los usuarios cambien la vista** |  Cuando está seleccionada, los usuarios de la aplicación pueden cambiar de la **Vista predeterminada** a otra vista de la entidad seleccionada en la propiedad **Entidad**. |
| **Opciones de visualización** | **Mostrar todas las vistas** |  Cuando está seleccionada, los usuarios de la aplicación pueden cambiar de la **Vista predeterminada** a todas las demás vistas de la entidad seleccionada en la propiedad **Entidad**. <br /><br />Esta propiedad sólo está disponible cuando se selecciona **Permitir que los usuarios cambien la vista**. |
| **Opciones de visualización** | **Vistas seleccionadas** |  Una lista de vistas de la entidad seleccionada en la propiedad **Entidad** que los usuarios de la aplicación pueden cambiar de la **Vista predeterminada**. <br /><br />Esta propiedad sólo está disponible cuando se selecciona **Permitir que los usuarios cambien la vista** y se desactiva **Mostrar todas las vistas**. |

## <a name="see-also"></a>Vea también
[Información general del diseñador de formularios controlado por modelos](form-designer-overview.md)  
[Crear, editar o configurar formularios usando el diseñador de formularios](create-and-edit-forms.md)  
[Agregar, configurar, mover o eliminar campos de un formulario](add-move-or-delete-fields-on-form.md)  
[Agregar, configurar, mover o eliminar componentes de un formulario](add-move-configure-or-delete-components-on-form.md)  
[Agregar, configurar, mover o eliminar secciones de un formulario](add-move-or-delete-sections-on-form.md)  
[Agregar, configurar, mover o eliminar pestañas de un formulario](add-move-or-delete-tabs-on-form.md)  
[Configurar propiedades de encabezado en el diseñador de formularios](form-designer-header-properties.md)  
[Agregar y configurar un componente de vista rápida en un formulario](form-designer-add-configure-quickview.md)  
[Configurar un componente de búsqueda en un formulario](form-designer-add-configure-lookup.md)  
[Use la vista de árbol del diseñador de formularios](using-tree-view-on-form.md)  
[Crear y editar campos](../common-data-service/create-edit-field-portal.md)  
