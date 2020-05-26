---
title: Información general de la interfaz de usuario del editor de formularios de aplicaciones controladas por modelos para Power Apps | MicrosoftDocs
description: Conozca la interfaz de usuario del editor de formularios para editar formularios en Power Apps
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.assetid: 146f8035-4fcd-4572-8e71-4270cd150495
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 85850ce83fa7431e1f881f18ae95c59b320c9dd1
ms.sourcegitcommit: c6906775005aec98973b1f5c3dbe5924aff6d26e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "3341199"
---
# <a name="overview-of-the-model-driven-app-form-editor-user-interface"></a>Información general de la interfaz de usuario del editor de formularios de aplicaciones controladas por modelos

El editor de formularios muestra comandos en tres pestañas: **Archivo**, **Inicio** e **Insertar**.  

- [Pestaña Archivo](#file-tab)
- [Pestaña Inicio](#home-tab)
- [Insertar la ficha](#insert-tab)
  
El editor de formularios se divide en tres áreas: **navegación**, **cuerpo** y **explorador**.  

> [!div class="mx-imgBorder"] 
> ![Interfaz de usuario del editor de formularios](media/form-user-interface.png)
  
**Navegación**  
Ubicada en la parte izquierda, use el área de navegación para controlar el acceso a las entidades relacionadas o agregar vínculos a las direcciones URL que deben mostrarse en el panel principal del formulario. Para modificar la navegación debe seleccionar primero el comando **Navegación** en el grupo **Seleccionar** de la ficha **Inicio**.

Los formularios principales proporcionan opciones de navegación a través de la barra de navegación, pero usan los mismos datos en el área de navegación para controlar las opciones de navegación que están disponibles. Más información: [Editar navegación](use-the-form-editor-legacy.md)  


**Cuerpo** <br>
Ubicada en el centro, use el área del cuerpo para controlar el diseño del formulario. Puede seleccionar y arrastrar elementos de formulario para colocarlos. Al hacer doble clic en un elemento se abrirán las propiedades del elemento. 

De manera predeterminada, para los formularios principales de Caso, Contacto y Cuenta, la primera sección en la pestaña **Resumen** muestra el formulario de cuenta o tarjeta de contacto del tipo **Vista rápida**. Para las entidades personalizadas, esta sección no está disponible de forma predeterminada. Puede insertar una sección nueva y un formulario de vista rápida en ella. El formulario de tarjeta muestra un máximo de cinco campos. Con la excepción de los campos, no es posible mostrar otros controles en la ventana Azul aunque el formulario de vista rápida lo contenga. 
 
>[!NOTE] 
> Para mantener el formato de tarjeta (como se muestra en la siguiente imagen), se recomienda no mover el formulario de vista rápida a ninguna otra sección del formulario.

> [!div class="mx-imgBorder"] 
> ![Formato de tarjeta](media/card-format.png)
   
Más información: [Crear y editar formularios de vista rápida](create-edit-quick-view-forms.md)  
 
-   Para agregar un campo, selecciónelo en el **Explorador de campos** y arrástrelo a una sección.  
  
    -   Para agregar un elemento que no sea un campo, seleccione la ubicación donde desee colocarlo y use el comando adecuado de la ficha **Insertar** para agregarlo.  
  
    -   Para quitar un elemento, selecciónelo y use el comando **Quitar** del grupo **Editar** de la ficha **Inicio**.  
  
    -   Para editar las opciones de **Encabezado** o **Pie de página** del formulario debe seleccionar primero el comando correspondiente en el grupo **Seleccionar** de la ficha **Inicio**.  
  
**Explorador**  
Ubicada en el lado derecho, el área del explorador incluye contenido dependiente del contexto.  
  
Al seleccionar **Cuerpo**, **Encabezado** o **Pie de página** en el grupo **Seleccionar** de la ficha **Inicio**, verá el **Explorador de campos**. Use el **Explorador de campos** para arrastrar los campos que desee mostrar en una sección del formulario o en el encabezado o pie de página. Puede incluir el mismo campo varias veces en un formulario. Use el botón **Nuevo campo** como acceso directo para crear un nuevo campo.  
  
Al seleccionar **Navegación** en el grupo **Seleccionar** de la ficha **Inicio**, verá el **Explorador de relaciones**. Arrastre las relaciones a uno de los grupos dentro del área de navegación. No puede agregar la misma relación dos veces. Las relaciones están disponibles en función de su configuración. Si configura una relación para que no se muestre, no aparecerá en el **Explorador de relaciones**. Para obtener información acerca de cómo configurar las opciones de visualización predeterminadas para las relaciones, consulte [Elemento del panel de navegación para una entidad principal](../common-data-service/create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity).
  
Puede usar los botones **Nueva 1:N** y **Nueva N:N** como acceso directo para agregar nuevas relaciones entre entidades.  

## <a name="file-tab"></a>Pestaña Archivo

Seleccione la pestaña **Archivo** para agregar o ver las siguientes opciones:

- **Nueva actividad** agrega una nueva actividad
- **Nuevo registro** agrega nuevo registro
- **Herramientas** utiliza opciones como Importar datos, Detección de duplicados y Asistente para eliminación en masa
- **Opciones** Cambie la configuración de visualización predeterminada para personalizar la solución predeterminada y administre las plantillas de correo
    - General
    - Sincronización
    - Actividades
    - Formatos
    - Plantillas de correo electrónico
    - Firmas de correo electrónico
    - Correo electrónico
    - Privacidad
    - Idiomas
- Ayuda
- Cerrar


## <a name="home-tab"></a>Pestaña Inicio  
 La pestaña **Inicio** muestra los comandos de la tabla siguiente:

> [!div class="mx-imgBorder"] 
> ![home-tab](media/home-tab.png)

|Agrupar|Comando|Descripción|
|-----------|-------------|-----------------| 
|**Guardar**|**Guardar**  **(Ctrl+S)**|Guarde el formulario.|
||**Guardar como**|Crear una copia de este formulario con otro nombre.|
||**Guardar y cerrar**|Guardar el formulario y cerrar el editor de formularios.|
||**Publicar**|Publicar el formulario. Más información: Publicación de personalizaciones|
|**Editar**|**Cambiar propiedades**|Cambiar las propiedades del elemento seleccionado en el cuerpo.<br /><br /> Consulte las siguientes secciones en función del elemento seleccionado:<br /><br /> -   [Propiedades de la ficha](tab-properties-legacy.md)<br />-   [Propiedades de las secciones](section-properties-legacy.md)<br />-   [Propiedades comunes de los campos](common-field-properties-legacy.md)<br />-   [Propiedades de campos especiales](special-field-properties-legacy.md)<br />-  [Propiedades de subcuadrícula](sub-grid-properties-legacy.md)<br />-   [Propiedades del control de vista rápida](quick-view-control-properties-legacy.md)|
||**Quitar**|Quite el elemento seleccionado.|
||**Deshacer** **(Ctrl+Z)**|Deshaga la acción anterior.|
||**Rehacer** **(Ctrl+Y)**|Rehacer la acción anterior.|
|**Seleccionar**|**Cuerpo**|Editar el cuerpo principal del formulario.|
||**Encabezado**|Editar el encabezado del formulario.|
||**Pie de página**|Edite el pie de página del formulario.|
||**Navegación**|Edite la navegación del formulario.<br /><br /> Más información: [Editar navegación](use-the-form-editor-legacy.md)
|**Formulario**|**Reglas de negocio**|Ver, editar o crear nuevas reglas de negocio con el explorador de reglas de negocio. **Nota:** Para los formularios interactivos, solo se admite el ámbito de "Entidad" y "Todos los formularios".<br /><br /> Más información: [Crear y editar reglas de negocio](create-business-rules-recommendations-apply-logic-form.md)|
||**Propiedades del formulario**| Más información: [Propiedades de formularios](form-properties-legacy.md)|  
||**Vista previa**|Utilice esta para ver el aspecto del formulario después de que se ha publicado. También puede obtener una vista previa para probar secuencias asociadas desde eventos.|         
||**Habilitar roles de seguridad**|Use esta opción para establecer los roles de seguridad que tendrán acceso a los formularios. Más información: [Controlar el acceso a los formularios](control-access-forms.md) **Importante**: si crea un nuevo formulario, solo los roles de seguridad de administrador del sistema y de personalizador del sistema tendrán acceso al formulario. Debe asignar el acceso a otros roles de seguridad para que los usuarios puedan usarlo.|  
||**Mostrar dependencias**|Vea los componentes de la solución que dependen de este formulario y los componentes de la solución necesarios para este formulario. |  
||**Propiedades administradas**|El comando de propiedades administradas tiene dos propiedades **Personalizable** y **Puede eliminarse**. Si se configuran estas propiedades como falso, el formulario no se podrá personalizar y no se podrá eliminar una vez que se haya incluido en una solución, exportado la solución como una solución administrada e importado la solución administrada en otro entorno. Más información: [Propiedades administradas](/power-platform/alm/managed-properties-alm)| 
|**Actualizar**|**Combinar formularios**|Si procede, esta opción permite combinar este formulario con un formulario de una versión anterior del formulario de Dynamics 365|
  

## <a name="insert-tab"></a>Insertar la ficha  
> [!div class="mx-imgBorder"] 
> ![insert-tab](media/insert-tab.png)
 
La pestaña Insertar muestra los comandos en la tabla siguiente:

|Grupo|Comando|Descripción|
|-----------|-------------|-----------------| 
||**Sección**|Agregue una sección a una pestaña seleccionada. Puede incluir una sección con una a cuatro columnas.<br /><br /> También puede insertar un panel de referencia en los formularios interactivos. El panel de referencia también se agrega como sección al formulario Principal: experiencia interactiva. De forma predeterminada la sección Panel de referencia se agrega los formularios de caso, cuenta, contacto y entidad personalizada.<br /><br /> Más información: [Propiedades de sección](section-properties-legacy.md)|  
|**3 Pestañas**|**Tres columnas**|Inserte una pestaña de tres columnas del mismo ancho.<br /><br /> Más información: [Propiedades de pestaña](tab-properties-legacy.md)|  
||**Tres columnas**|Inserte una pestaña de tres columnas con la columna central más ancha.|  
|**2 Pestañas**|**Dos columnas**|Insertar una pestaña de dos columnas con la columna derecha más ancha.|  
||**Dos columnas**|Insertar una pestaña de dos columnas con la columna izquierda más ancha.|  
||**Dos columnas**|Insertar una pestaña de dos columnas del mismo ancho.|  
|**1 Pestaña**|**Una columna**|Insertar una pestaña de una columna.|  
|**Control**|**Subcuadrícula**|Dé formato a una subcuadrícula e insértela en el formulario.<br /><br /> Más información: [Propiedades de subcuadrícula](sub-grid-properties-legacy.md)|  
||**Separador**|Inserte un espacio vacío.|  
||**Formulario de vista rápida**|Insertar un formulario de vista rápida.<br /><br /> Más información: [Propiedades de control de vista rápida](quick-view-control-properties-legacy.md)|  
||**Recurso de web**|Inserte un recurso web para incrustar contenido de otras ubicaciones en una página.<br /><br /> Más información: [Propiedades de recursos web](web-resource-properties-legacy.md)|  
||**IFRAME**|Puede agregar un IFRAME a un formulario para integrar contenido de otro sitio web en un formulario.| 
||**Escala de tiempo**|Inserte un control de escala de tiempo en el formulario. Este control muestra la escala de tiempo de actividades relacionadas con la entidad en un formulario.|  
||**Vínculo de navegación**|Con esta opción, puede insertar un vínculo en una navegación del formulario.|  
||**Temporizador**|Inserte un control de temporizador en un formulario de entidad para realizar un seguimiento del tiempo con un SLA. Más información: [Agregar un control de temporizador](https://docs.microsoft.com/dynamics365/customer-engagement/customer-service/add-timer-control-case-form-track-time-against-sla)|
||**Busque en Knowledge Base**|Inserte un control de búsqueda que los usuarios pueden usar para buscar en los artículos de conocimientos. Más información: [Control de búsqueda de Knowledge Base](https://docs.microsoft.com/dynamics365/customer-engagement/customer-service/add-knowledge-base-search-control-forms)|  
||**Asistente de relaciones**|Con esta opción, puede insertan un control del asistente de relaciones en el formulario.|

>[!Note] 
>No se admiten los componentes siguientes en los formularios principales:<br> <ul> <li>Mapas de Bing <br><li>Yammer <br><li>Fuentes de actividades <br> </li> </ul>


## <a name="next-steps"></a>Pasos siguientes

[Utilizar el formulario Principal y sus componentes](use-main-form-and-components.md)  
