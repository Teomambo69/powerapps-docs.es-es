---
title: Configure un componente de búsqueda en un formulario | MicrosoftDocs"
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
---

# <a name="configure-a-lookup-component-on-a-form"></a>Configurar un componente de búsqueda en un formulario  
Un campo de búsqueda se puede usar para vincular con un registro en otra entidad. Se utiliza un componente de búsqueda automáticamente cuando un campo de búsqueda se agrega a un formulario. Los fabricantes pueden configurar un componente de búsqueda con el diseñador de formularios.

## <a name="configure-a-lookup-component"></a>Configurar un componente de búsqueda
Éstas son las propiedades disponibles para configurar cuando utiliza un componente de búsqueda en un formulario usando el diseñador de formularios.


<!--from editor: "Drop-down" should only be an adjective. In the following table, is it a list? A menu? -->


|Área  |Nombre  |Descripción  |
|---------|---------|---------|
| **Opciones de visualización** | **Entidad** |  La entidad relacionada con la que el campo de búsqueda se conecta. |
| **Opciones de visualización** | **Vista predeterminada** |  La vista de la entidad seleccionada en la propiedad **Entidad** que se puede usar para obtener y mostrar la lista de registros que los usuarios de la aplicación pueden usar en el desplegable de búsqueda. |
| **Opciones de visualización** | **Permitir que los usuarios cambien la vista** |  Cuando está seleccionada, los usuarios de la aplicación pueden cambiar de la **Vista predeterminada** a otra vista de la entidad seleccionada en la propiedad **Entidad**. |
| **Opciones de visualización** | **Mostrar todas las vistas** |  Cuando está seleccionada, los usuarios de la aplicación pueden cambiar de la **Vista predeterminada** a todas las demás vistas de la entidad seleccionada en la propiedad **Entidad**. <br /><br />Esta propiedad sólo está disponible cuando se selecciona **Permitir que los usuarios cambien la vista**. |
| **Opciones de visualización** | **Vistas seleccionadas** |  Una lista de vistas de la entidad seleccionada en la propiedad **Entidad** a la que los usuarios de la aplicación pueden cambiar desde la **Vista predeterminada**. <br /><br />Esta propiedad sólo está disponible cuando se selecciona **Permitir que los usuarios cambien la vista** y se desactiva **Mostrar todas las vistas**. |

## <a name="see-also"></a>Vea también
[Información general del diseñador de formularios controlado por modelos](form-designer-overview.md)  
[Crear, editar o configurar formularios usando el diseñador de formularios](create-and-edit-forms.md)  
[Agregar, configurar, mover o eliminar campos de un formulario](add-move-or-delete-fields-on-form.md)  
[Agregar, configurar, mover o eliminar componentes de un formulario](add-move-configure-or-delete-components-on-form.md)  
[Agregar, configurar, mover o eliminar secciones de un formulario](add-move-or-delete-sections-on-form.md)  
[Agregar, configurar, mover o eliminar pestañas de un formulario](add-move-or-delete-tabs-on-form.md)  
[Configurar propiedades de encabezado en el diseñador de formularios](form-designer-header-properties.md)  
[Agregar y configurar un componente de subcuadrícula en un formulario](form-designer-add-configure-subgrid.md)  
[Agregar y configurar un componente de vista rápida en un formulario](form-designer-add-configure-quickview.md)  
[Use la vista de árbol del diseñador de formularios](using-tree-view-on-form.md)  
[Crear y editar campos](../common-data-service/create-edit-field-portal.md)  
