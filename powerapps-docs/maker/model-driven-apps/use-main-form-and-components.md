---
title: Utilizar el formulario principal de la aplicación controlada por modelos y sus componentes en PowerApps | Microsoft Docs
description: Aprender a usar el formulario principal y sus componentes en las aplicaciones basadas en la interfaz unificada
keywords: Formularios principales; Customer Service; Centro de servicio al cliente; Dynamics 365
author: Mattp123
ms.author: matp
manager: kvivek
ms.date: 06/06/2018
ms.service: powerapps
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: 43bfface-4dc2-411d-99a1-83e934646989
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 610a4baf51a2affea142b496d016d732fa626d20
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755924"
---
# <a name="use-the-model-driven-app-main-form-and-its-components"></a>Utilizar el formulario principal de la aplicación controlada por modelos y sus componentes

Los formularios en las aplicaciones basadas en la interfaz unificada proporcionan una mejor experiencia de usuario para la productividad óptima de agentes y ayudan a mantener el contexto mientras se trabaja en registros relacionados. Puede ver los formularios en el explorador de soluciones. El tipo de formulario de los formularios nuevos es **Principal**.

En este tema se explica cómo editar un formulario principal y agregar, modificar o cambiar varios elementos del formulario.

## <a name="open-the-form-editor"></a>Abrir el editor de formularios

Para editar un formulario o agregar o cambiar elementos, use el editor de formularios. El editor de formularios permite editar los formularios para todas las aplicaciones basadas en la interfaz unificada.

Siga las instrucciones a continuación para acceder al editor de formularios. 

> [!NOTE]
> Si crea componentes de la solución nuevos en el proceso de edición del formulario, los nombres de los componentes usarán el prefijo de personalización del editor de soluciones de la solución predeterminada y estos componentes solo se incluirán en la solución predeterminada. Si desea que los nuevos componentes de la solución se incluyan en una solución no administrada específica, abra el editor de formularios a través de esa solución no administrada.


### <a name="access-the-form-editor-through-app-designer-in-powerapps"></a>Acceda al editor de formularios a través del diseñador de aplicaciones en PowerApps

1.  Inicie sesión en [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

2.  En el panel de navegación de la izquierda seleccione **Aplicaciones**, seleccione la aplicación que desee y, en la barra de herramientas, seleccione **Editar**.  

3. En el lienzo del diseñador de aplicaciones, selecciones la flecha hacia abajo ![Flecha abajo para diseñador de aplicaciones](media/down-arrow-app-designer.png) junto a una entidad para ver los formularios disponibles para esa entidad. 

4. Seleccione el botón para abrir el diseñador ![abrir diseñador](media/site-map-designer.png)correspondiente al formulario que se va a editar.

   ![Editor de formularios en el diseñador de aplicaciones](media/app-designer-forms.png)
 
5. En el diseñador de formularios, realice los cambios y seleccione **Guardar** para guardar los cambios y **Publicar** para publicarlos para su uso en la aplicación. 

> [!NOTE]
> Si se han realizado otros cambios en la aplicación, publíquelos utilizando la opción de publicación de nivel de aplicación. Consulte [Validar y publicar una aplicación mediante el diseñador de aplicaciones](validate-app.md) para obtener más información.

> [!NOTE]
> El formulario principal del cliente web también es compatible con el Centro de servicio al cliente y está disponible para editar con el diseñador de aplicaciones.


### <a name="access-the-form-editor-through-the-default-solution"></a>Acceso al editor de formularios a través de la solución predeterminada

1.  Inicie sesión en [PowerApps](https:///?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Formularios**.  

3. En la lista de formularios, abra el formulario de tipo **Principal**.

### <a name="access-the-form-editor-for-an-unmanaged-solution"></a>Acceso al editor de formularios de una solución no administrada

1. Abra [soluciones](advanced-navigation.md#solutions).
2. Haga doble clic en la solución no administrada que desea utilizar. El tipo de solución, administrada o no administrada, se muestra en la columna **Tipo de paquete**.
3. En la lista de componentes, busque la entidad con el formulario que desea editar. Si la entidad no está presente, deberá agregarla.

#### <a name="add-an-entity-to-an-unmanaged-solution"></a>Agregar una entidad para una solución no administrada

1. Con la solución no administrada abierta en el explorador de soluciones, seleccione el nodo **Entidades** y, en la barra de herramientas situada encima de la lista, seleccione **Agregar existente**.

     > [!div class="mx-imgBorder"] 
     > ![Agregar entidad existente](media/add-existing-entity.png)

2. En el cuadro de diálogo **Seleccionar componentes de la solución**, con el selector **Tipo de componente** definido en **Entidad**, seleccione la entidad que desee agregar y seleccione **Aceptar**.

3. Si aparece el cuadro de diálogo **Faltan componentes necesarios**, puede seleccionar **No, no incluir los componentes necesarios** si no se piensa exportar esta solución no administrada a otra organización. Si no desea incluir los componentes necesarios que faltan en este momento, puede agregarlos más adelante. Recibirá una notificación de nuevo si exporta esta solución en el futuro.

4. En el explorador de soluciones, expanda la entidad con el formulario que desee editar y seleccione **Formularios**.

5. En la lista de formularios, abra el formulario de tipo **Principal**.

#### <a name="publish-the-changes-for-use-in-the-app"></a>Publicar los cambios para su uso en la aplicación

Determinadas personalizaciones que realizan cambios en la interfaz de usuario requieren que se publiquen antes de que los usuarios puedan usarlas en la aplicación. Para publicar la personalización, en la barra de herramientas del explorador de soluciones, seleccione **Publicar todas las personalizaciones**.

## <a name="form-editor-user-interface"></a>Interfaz de usuario del editor de formularios

Para conocer en detalle la interfaz de usuario del editor de formularios, consulte [Información general de la interfaz de usuario del editor de formularios](form-editor-user-interface-legacy.md).

## <a name="form-properties"></a>Propiedades del formulario

Para conocer en detalle las propiedades del formulario, consulte [Propiedades del formulario](form-properties-legacy.md).

## <a name="visibility-options"></a>Opciones de visibilidad  
 Varios tipos de elementos de formulario tienen la opción para mostrarse u ocultarse de forma predeterminada. Pestañas, secciones y campos proporcionan esta opción. Con scripts de formulario o reglas de negocio, la visibilidad de estos elementos se puede controlar para crear un formulario dinámico para proporcionar una interfaz de usuario que se adapte a las condiciones del formulario. 
  
> [!NOTE]
>  Ocultar elementos de formulario no es una forma recomendada para imponer la seguridad. Existen varias formas en que los usuarios pueden ver todos los elementos y datos en el formulario cuando los elementos están ocultos. Para obtener más información, consulte [Mostrar u ocultar elementos de formulario](visibility-options-legacy.md). 
  
## <a name="tab-properties"></a>Propiedades de las pestañas  

En el cuerpo de un formulario, las pestañas proporcionan separación horizontal. Las pestañas tienen una etiqueta que puede mostrarse. Si se muestra la etiqueta, las pestañas se pueden expandir o contraer para mostrar u ocultar su contenido eligiendo la etiqueta. Para conocer en detalle las propiedades de la pestaña, consulte [Propiedades de la pestaña](tab-properties-legacy.md).


## <a name="section-properties"></a>Propiedades de las secciones  

Una sección en un formulario ocupa el espacio disponible en una columna de la ficha. Las secciones tienen una etiqueta que se puede mostrarse y una línea se puede mostrar debajo de la etiqueta. Para conocer en detalle las propiedades de la sección, consulte [Propiedades de la sección](section-properties-legacy.md).
  
## <a name="timeline"></a>Escala de tiempo  
 La línea de tiempo muestra actividades relacionadas para una entidad específica.  
  
 Se admiten los siguientes tipos de actividades: tarea, cita, llamada de teléfono, correo electrónico, actividad social, actividad personalizada.  
  
 La escala de tiempo también muestra notas y publicaciones del sistema y del usuario. Muestra las actividades que tienen el campo **Referente a** definido como la entidad que está visualizando. Para notas, el campo **Referente a** no se muestra al usuario; Es implícito cuando se creó desde la escala de tiempo.  
  
 Cada actividad que aparece en la escala de tiempo tendrá las mismas acciones rápidas que están disponibles en la barra de comandos de la actividad.  

## <a name="common-field-properties"></a>Propiedades comunes de los campos  

Para conocer en detalle las propiedades de campos comunes, consulte [Propiedades de campos comunes](common-field-properties-legacy.md). 
  
## <a name="special-field-properties"></a>Propiedades de campos especiales  
 Las propiedades de todos los campos aparecen en [Propiedades comunes de los campos](common-field-properties-legacy.md), pero algunos campos tienen propiedades adicionales. Para obtener más información, consulte [Propiedades de campos especiales](special-field-properties-legacy.md).

  
## <a name="sub-grid-properties"></a>Propiedades de subcuadrícula  

Puede configurar una subcuadrícula en un formulario para presentar una lista de registros o un gráfico. Para conocer en detalle las propiedades de la subcuadrícula, consulte [Propiedades de la subcuadrícula](sub-grid-properties-legacy.md).

## <a name="quick-view-control-properties"></a>Propiedades del control de vista rápida  

Un control de vista rápida sobre un formulario muestra datos de un registro seleccionado en una búsqueda en el formulario. Para explorar las propiedades del control de vista rápida, consulte [Propiedades del control de vista rápida](quick-view-control-properties-legacy.md).
  
## <a name="web-resource-properties"></a>Propiedades de recurso web  

Puede agregar o editar recursos web en un formulario para aumentar su atractivo o utilidad para los usuarios de la aplicación. Los recursos web habilitados para formularios son imágenes, archivos HTML o controles de Silverlight. Conocer en detalle las propiedades de recursos web. Vaya a [Propiedades de recursos web](web-resource-properties-legacy.md). 
  
## <a name="iframe-properties"></a>Propiedades de IFRAME  

Puede agregar los iFrame a un formulario para integrar contenido de otro sitio web en un formulario. Para conocer más sobre las propiedades de IFRAME, consulte [Propiedades de IFRAME](iframe-properties-legacy.md). 
  
## <a name="edit-navigation"></a> Editar la navegación  
 La navegación en el formulario permite que los usuarios vean listas de registros relacionados. Cada relación de entidad tiene propiedades para controlar si se debe mostrar. Más información: [Elemento del panel de navegación para una entidad principal](../common-data-service/create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity)
  
 Las relaciones de entidad configuradas para mostrarse se pueden reemplazar en el editor de formularios.  
  
 Para ver instrucciones paso a paso, consulte [Agregar navegación del formulario para las entidades relacionadas](add-edit-form-navigation-related-entities.md).
  
 Para habilitar la edición de la navegación debe seleccionar primero **Navegación** en el grupo **Seleccionar** de la ficha **Inicio**.  
  
 En el **Explorador de relaciones** puede filtrar por las relaciones 1: N (uno a varios) o N:N (varios a varios), o ver todas las relaciones disponibles. La opción **Mostrar únicamente la casilla de verificación sin usar de relaciones** está deshabilitada y seleccionada. Cada una de las relaciones se puede agregar una vez.  
  
 Para agregar una relación desde el **Explorador de relaciones** haga doble clic y se agregará debajo de la relación actualmente seleccionada en el área de navegación. Haga doble clic en una relación en el área de navegación y podrá cambiar la etiqueta en la pestaña **Visualización**. En la pestaña **Nombre**, puede obtener información sobre la relación. Use el botón **Editar** para abrir la definición de la entidad.  
  
 Hay cinco grupos en el área de navegación. Puede arrastrarlos para cambiar su ubicación y hacer doble clic encima para cambiar la etiqueta, pero no puede quitarlos. Estos grupos solo se mostrarán cuando contengan algo. Si no desea que un grupo aparezca, no le agregue ningún elemento.  
  
## <a name="configure-event-handlers"></a>Configurar controladores de eventos  

Un controlador de eventos se compone de una referencia a un recurso web de JavaScript y a una función definida dentro de ese recurso web que se ejecutará cuando se produzca el evento. Para obtener más información sobre la configuración de controladores de eventos, consulte [Configurar controladores de eventos](configure-event-handlers-legacy.md). 
  
## <a name="next-steps"></a>Pasos siguientes  
 [Crear y diseñar formularios](create-design-forms.md)   
 [Crear y editar formularios de creación rápida](create-edit-quick-view-forms.md)   
 [Crear y editar formularios de vista rápida](create-edit-quick-view-forms.md)
