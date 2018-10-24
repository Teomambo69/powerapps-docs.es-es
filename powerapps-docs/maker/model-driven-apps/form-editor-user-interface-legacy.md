---
title: Información general de la interfaz de usuario del editor de formularios de aplicaciones controladas por modelos para PowerApps | Microsoft Docs
description: Información sobre la interfaz de usuario del editor de formularios para editar formularios en PowerApps
keywords: Formularios; Formulario principal; Aplicaciones de interfaz unificada; Dynamics 365 for Customer Engagement
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.assetid: 146f8035-4fcd-4572-8e71-4270cd150495
ms.openlocfilehash: a44987e7b8809dea46f164224974a21a2d9a5010
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39711466"
---
# <a name="overview-of-the-model-driven-app-form-editor-user-interface"></a>Información general de la interfaz de usuario del editor de formulario de aplicaciones controladas por modelos

El editor de formularios muestra los comandos en tres pestañas: **Archivo**, **Inicio** e **Insertar**.  

- [Pestaña Archivo](#file-tab)
- [Pestaña Inicio](#home-tab)
- [Pestaña Insertar](#insert-tab)
  
El editor de formularios se divide en tres áreas: **Navegación**, **Cuerpo** y **Explorador**.  

![Interfaz de usuario del editor de formularios](media/form-user-interface.png)
  
**Navegación**  
Use el área de navegación, a la izquierda, para controlar el acceso a entidades relacionadas o agregar vínculos a las URL que se mostrarán en el panel principal del formulario. Para editar la navegación, primero debe seleccionar el comando **Navegación** del grupo **Seleccionar** de la pestaña **Inicio**.

Los formularios principales proporcionan opciones de navegación en la barra de navegación. Sin embargo, use los mismos datos en el área de navegación para controlar qué opciones de exploración estarán disponibles. Más información: [Edición de la navegación](use-the-form-editor-legacy.md)  


**Cuerpo** <br>
Use el área de cuerpo, en el centro, para controlar el diseño del formulario. Puede seleccionar los elementos de formulario y arrastrarlos para colocarlos. Haga doble clic en un elemento para abrir las propiedades del elemento. 

De forma predeterminada, en los formularios de Caso, Contacto y Cuenta, la primera sección de la pestaña **Resumen** muestra el formulario de tarjeta de contacto o cuenta del tipo **Vista rápida**. Esta sección no está disponible de forma predeterminada en las entidades personalizadas. Pero puede insertar una nueva sección y un formulario de vista rápida en ella. El formulario de tarjeta muestra un máximo de cinco campos. Aparte de los campos, no es posible mostrar otros controles en el icono azul, aunque el formulario de vista rápida los contenga. 
 
>[!NOTE] 
> Para conservar el formato de tarjeta (como se muestra en la siguiente imagen), se recomienda no mover el formulario de vista rápida a cualquier otra sección del formulario.

![Formato de tarjeta](media/card-format.png)
   
Más información: [Crear y editar formularios de vista rápida](create-edit-quick-view-forms.md)  
 
-   Para agregar un campo, selecciónelo en el **Explorador de campos** y arrástrelo a una sección.  
  
    -   Para agregar un elemento que no sea un campo, seleccione el área dónde desea colocarlo y use el comando correspondiente de la pestaña **Insertar** para agregarlo.  
  
    -   Para quitar un elemento, selecciónelo y utilice el comando **Quitar** del grupo **Editar** de la pestaña **Inicio**.  
  
    -   Para editar el **encabezado** o el **pie de página** del formulario, primero debe seleccionar el comando correspondiente en el grupo **Seleccionar** de la pestaña **Inicio**.  
  
**Explorador**  
El contenido del área del explorador, a la derecha, depende del contexto.  
  
Al seleccionar **Cuerpo**, **Encabezado** o **Pie de página** en el grupo **Seleccionar** de la pestaña **Inicio**, verá el **Explorador de campos**. Use el **Explorador de campos** para arrastrar campos que desea mostrar en una sección del formulario o en el encabezado o pie de página. Puede incluir varias veces el mismo campo en un formulario. Use el botón **Nuevo campo** como acceso directo para crear un campo.  
  
Al seleccionar **Navegación** en el grupo **Seleccionar** de la pestaña **Inicio**, verá el **Explorador de relaciones**. Arrastre cualquiera de las relaciones en uno de los grupos del área de navegación. No se puede agregar la misma relación dos veces. Las relaciones están disponibles en función de cómo estén configuradas. Si configura una relación para que no se muestre, no aparecerá en el **Explorador de relaciones**. Para obtener información sobre cómo configurar las opciones de visualización predeterminadas para las relaciones, consulte el artículo sobre el [elemento de panel de navegación de una entidad principal](../common-data-service/create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity).
  
Puede usar los botones **Nueva 1:N** y **Nueva N:N** como método abreviado para agregar nuevas relaciones entre entidades.  

## <a name="file-tab"></a>Pestaña Archivo

Seleccione la pestaña **Archivo** para agregar o ver las opciones siguientes:

- **Nueva actividad**: agregue una nueva actividad.
- **Nuevo registro**: agregue un nuevo registro.
- **Herramientas**: use opciones como Importar datos, Detección de duplicados y el Asistente para eliminación en masa.
- **Opciones**: cambie la configuración de visualización predeterminada para personalizar la solución predeterminada y administre las plantillas de correo electrónico.
    - General
    - Sincronización
    - Actividades
    - Formatos
    - Plantillas de correo electrónico
    - Firmas de correo electrónico
    - Correo electrónico
    - Privacidad
    - Lenguajes
- Ayuda
- Cerrar


## <a name="home-tab"></a>Pestaña Inicio  
 La pestaña **Inicio** muestra los comandos de la tabla siguiente:

![Pestaña Inicio](media/home-tab.png)

|Grupo|Comando|Descripción|
|-----------|-------------|-----------------| 
|**Guardar**|**Guardar** **(Ctrl+S)**|Guarde el formulario.|
||**Guardar como**|Cree una copia de este formulario con otro nombre.|
||**Guardar y cerrar**|Guarde el formulario y cierre el editor de formularios.|
||**Publicar**|Publique el repositorio. Más información: Publicación de personalizaciones|
|**Editar**|**Cambiar propiedades**|Cambie las propiedades del elemento seleccionado en el cuerpo.<br /><br /> Consulte las secciones siguientes según el elemento seleccionado:<br /><br /> -   [Propiedades de la ficha](tab-properties-legacy.md)<br />-   [Propiedades de la sección](section-properties-legacy.md)<br />-   [Propiedades de campo común](common-field-properties-legacy.md)<br />-   [Propiedades de campo especial](special-field-properties-legacy.md)<br />-  [Propiedades de subcuadrícula](sub-grid-properties-legacy.md)<br />-   [Propiedades de control de vista rápida](quick-view-control-properties-legacy.md)|
||**Quitar**|Quite el elemento seleccionado.|
||**Deshacer** **(Ctrl+Z)**|Deshaga la acción anterior.|
||**Rehacer** **(Ctrl+Y)**|Rehaga la acción anterior.|
|**Seleccionar**|**Cuerpo**|Edite el cuerpo principal del formulario.|
||**Encabezado**|Edite el encabezado del formulario.|
||**Pie de página**|Edite el pie de página del formulario.|
||**Navegación**|Edite la navegación del formulario.<br /><br /> Más información: [Edición de la navegación](use-the-form-editor-legacy.md)
|**Formulario**|**Reglas de negocio**|Vea, edite o cree nuevas reglas de negocio con el Explorador de reglas de negocio. **Nota**: En los formularios interactivos solo se admiten los ámbitos "Entidad" y "Todos los formularios".<br /><br /> Más información: [Creación y edición de reglas de negocio](create-business-rules-recommendations-apply-logic-form.md)|
||**Propiedades del formulario**| Más información: [Propiedades del formulario](form-properties-legacy.md)|  
||**Versión preliminar**|Utilícelo para ver el aspecto del formulario después de publicarlo. También puede obtener una vista previa para probar los scripts asociados a partir de eventos.|         
||**Habilitar roles de seguridad**|Utilice este grupo para establecer los roles de seguridad que tendrán acceso a los formularios. Más información: [Control del acceso a los formularios](control-access-forms.md) **Importante:** Si crea un formulario, solo los roles de seguridad Administrador del sistema y Personalizador del sistema tendrán acceso al formulario. Debe asignar acceso a otros roles de seguridad antes de que los usuarios puedan utilizar el formulario.|  
||**Mostrar dependencias**|Vea qué componentes de la solución dependen de este formulario y cuáles son los que requiere este formulario. Más información: [Dependencias de la solución](../common-data-service/overview.md)|  
||**Propiedades administradas**|El comando Propiedades administradas tiene dos propiedades **Personalizable** y **Puede eliminarse**. Si establece el valor de estas propiedades en false, el formulario no podrá personalizarse ni eliminarse después de incluirlo en una solución. Exporte esa solución como una solución administrada e impórtela en otro entorno. Más información: [Propiedades administradas](../common-data-service/solutions-overview.md#managed-properties)| 
|**Actualizar**|**Combinar formularios**|Si es aplicable, esta opción permite combinar este formulario con uno de una versión anterior del formulario de Dynamics 365.|
  

## <a name="insert-tab"></a>Pestaña Insertar  
![Pestaña Insertar](media/insert-tab.png)
 
La pestaña Insertar muestra los comandos de la tabla siguiente:

|Grupo|Comando|Descripción|
|-----------|-------------|-----------------| 
||**Sección**|Agregue una sección a una pestaña seleccionada. Puede incluir una sección con entre una y cuatro columnas.<br /><br /> También puede insertar un panel de referencia en los formularios interactivos. El panel de referencia también se agrega como sección al formulario principal de experiencia interactiva. De forma predeterminada, se agrega la sección Panel de referencia a los formularios de entidad personalizada Caso, Cuenta y Contacto.<br /><br /> Más información: [Propiedades de la sección](section-properties-legacy.md)|  
|**3 Pestañas**|**Tres columnas**|Inserte una pestaña de tres columnas con anchos iguales.<br /><br /> Más información: [Propiedades de la ficha](tab-properties-legacy.md)|  
||**Tres columnas**|Inserte una pestaña de tres columnas con una columna central más amplia.|  
|**2 Pestañas**|**Dos columnas**|Inserte una pestaña de dos columnas con una columna derecha más amplia.|  
||**Dos columnas**|Inserte una pestaña de dos columnas con una columna izquierda más amplia.|  
||**Dos columnas**|Inserte una pestaña de dos columnas con anchos iguales.|  
|**1 Pestaña**|**Una columna**|Inserte una pestaña de una sola columna.|  
|**Control**|**Subcuadrícula**|Dé formato a una subcuadrícula e insértela en el formulario.<br /><br /> Más información: [Propiedades de subcuadrícula](sub-grid-properties-legacy.md)|  
||**Espaciador**|Inserte un espacio en blanco.|  
||**Formulario de vista rápida**|Inserte un formulario de vista rápida.<br /><br /> Más información: [Propiedades de control de vista rápida](quick-view-control-properties-legacy.md)|  
||**Recurso web**|Inserte un recurso web para insertar contenido de otras ubicaciones en una página.<br /><br /> Más información: [Propiedades de recurso web](web-resource-properties-legacy.md)|  
||**IFRAME**|Puede agregar un elemento IFRAME a un formulario para integrar el contenido de otro sitio web en un formulario.| 
||**Escala de tiempo**|Inserte un control de escala de tiempo en el formulario. Este control muestra la escala de tiempo de las actividades relacionadas con la entidad de un formulario.|  
||**Vínculo de navegación**|Con esta opción puede insertar un vínculo en la navegación de un formulario.|  
||**Temporizador**|Inserte un control de temporizador en un formulario de entidad para realizar el seguimiento del tiempo con respecto a un Acuerdo de Nivel de Servicio (SLA). Más información: [agregar un control de temporizador](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customer-service/add-timer-control-case-form-track-time-against-sla)|
||**Búsqueda en Knowledge Base**|Inserte un control de búsqueda que los usuarios puedan usar para buscar artículos de conocimientos. Más información: [Control de búsqueda de Knowledge Base](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customer-service/add-knowledge-base-search-control-forms)|  
||**Asistente de relaciones**|Con esta opción puede insertar un control del asistente de relaciones en el formulario.|

>[!Note] 
>Los siguientes componentes no se admiten en los formularios principales:<br> <ul> <li>Mapas de Bing <br><li>Yammer <br><li>Fuentes de actividades <br> </li> </ul>


## <a name="next-steps"></a>Pasos siguientes

[Utilizar el formulario principal y sus componentes](use-main-form-and-components.md)  
