---
title: Propiedades de subcuadrícula para formularios principales de aplicaciones controladas por modelos en PowerApps | MicrosoftDocs
description: Comprender las propiedades de subcuadrícula para formularios principales
Keywords: Formulario principal; propiedades de subcuadrícula; Dynamics 365
author: Mattp123
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.author: matp
manager: kvivek
ms.date: 06/07/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 82892cd3-3436-4677-b96b-f2ccd0a4f078
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="sub-grid-properties-for-model-driven-app-main-forms-overview"></a>Información general de propiedades de subcuadrícula para formularios principales de aplicaciones controladas por modelos

Puede configurar una subcuadrícula en un formulario para presentar una lista de registros o un gráfico. Seleccione **Solo mostrar gráfico** en la ficha **Mostrar** para mostrar un gráfico en lugar de una lista.  

Puede acceder a las **Propiedades de subcuadrícula** desde el sitio de PowerApps. 
1.  En el sitio de [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) seleccione **Controlado por modelos** (parte inferior izquierda del panel de navegación).  

     ![Modo de diseño controlado por modelos](media/model-driven-switch.png)

2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Formularios**. 

3.  En la lista de formularios, abra el formulario de tipo **Principal**. Luego en la pestaña **Insertar**, seleccione **Subcuadrícula** para ver propiedades de subcuadrícula.

    ![propiedades de subcuadrícula](media/sub-grid-properties.png)
  
|Ficha|Propiedad|Descripción|  
|---------|--------------|-----------------|  
|**Presentación**|**Nombre**|**Requerido**: nombre único de la subcuadrícula que se usa al hacerle referencia en los scripts. El nombre solo puede contener caracteres alfanuméricos y de subrayado.|  
||**Etiqueta**|**Requerido**: etiqueta localizable de la subcuadrícula visible para los usuarios.|  
||**Mostrar etiqueta en el formulario**|Si la etiqueta debería mostrarse en el formulario. Es necesario si habilita **Mostrar cuadro de búsqueda**. También puede elegir el color del encabezado del panel.|  
||**Registros**|Elija entre dos opciones:<br /><br /> - **Solo los registros relacionados**: la subcuadrícula solo mostrará los registros relacionados con el registro actual.<br />- **Todos los tipos de registros**: la subcuadrícula mostrará los registros filtrados solo por la vista predeterminada o, si está habilitado el selector de la vista, todas las vistas que el usuario elija.<br /><br /> La opción que elija afectará al comportamiento de control de visualización de lista. Más información: [Mostrar comportamiento de la lista](#show-list-behavior) |  
||**Entidad**|En función de la opción que elija para **Registros**, esta lista mostrará una de las opciones:<br /><br /> - **Solo los registros relacionados**: una lista de entidades relacionadas con esta entidad con el nombre del campo de búsqueda en la entidad que define la relación entre paréntesis.<br />- **Todos los tipos de registros**: una lista de todas las entidades.|  
||**Vista predeterminada**|Seleccione la vista que se aplicará de forma predeterminada. Si no habilita otras vistas mediante la propiedad **Selector de vista**. Esta será la única vista.<br /><br /> Use el botón **Editar** para abrir la vista predeterminada para editar. Use el botón **Nuevo** para crear una vista nueva para usar para esta subcuadrícula.|  
||**Mostrar cuadro de búsqueda**|Muestra el cuadro de búsqueda. Cuando se selecciona esta opción se requiere la opción **Mostrar etiqueta en el formulario**.|  
||**Mostrar índice**|Solo los formularios que utilizan los [formularios clásicos](main-form-presentations.md#classic-forms) admiten la opción de mostrar índice.<br /><br /> Seleccione esta casilla si desea que esté disponible el índice alfabético con la lista. Esto le permite pasar a registros que comiencen con una letra o número determinado.|  
||**Selector de vista**|Tiene tres opciones:<br /><br /> - **Desactivado**: solo se puede usar la vista predeterminada.<br />- **Mostrar todas las vistas**: permite a los usuarios seleccionar cualquier vista.<br />- **Mostrar las vistas seleccionadas**: use la tecla Ctrl con el cursor para seleccionar las vistas disponibles que desee mostrar.|  
||**Gráfico predeterminado**|Seleccione el gráfico para mostrar si **Solo mostrar gráfico** está seleccionado.|  
||**Solo mostrar gráfico**|En lugar de una lista de registros, se mostrará un gráfico.|  
||**Mostrar selección de gráfico**|Si se selecciona **Solo mostrar gráfico**, permite a las personas seleccionar distintos gráficos.|  
||**Disponibilidad**|Especifique si la sección debe estar disponible en el teléfono.|
|**Formato**|**Diseño**|**Seleccione el número de columnas que ocupa el control**.<br /><br /> Cuando la sección que contiene la subcuadrícula tiene más de una columna, puede establecer que el campo ocupe hasta el número de columnas que tiene la sección.|  
||**Diseño de filas**|**Número de filas** determinará cuántos registros se muestran en una página de una subcuadrícula.<br /><br /> Si se selecciona **Expandir automáticamente para usar el espacio disponible**, el formulario permitirá espacio para dos registros y expandirá el espacio a medida que el número de registros aumente. Si el número excede **Número de filas**, los usuarios pueden navegar a páginas adicionales para ver los registros.<br /><br /> Si **Expandir automáticamente para usar el espacio disponible** no está seleccionado, el formulario proporcionará espacio para el número de registros definidos en **Número de filas** y las personas podrán navegar a páginas adicionales para ver registros adicionales.|  
|**Controles**|**Controles**|Elija para agregar controles y seleccione el botón de radio para que tenerlos para web, teléfono o tableta.|
  
 En formularios que utilizan la [presentación clásica](main-form-presentations.md#classic-forms), las acciones realizadas en una subcuadrícula están disponibles en la cinta de opciones. Los desarrolladores pueden personalizar el comportamiento de estas acciones o agregar acciones adicionales personalizando la cinta de opciones.  
  
 En formularios que utilizan los [formularios actualizados](main-form-presentations.md#updated-forms), las acciones para las subcuadrículas se colocan cerca de la subcuadrícula, para que sea más fácil acceder a ellas. Sin embargo, la barra de comandos no permite agregar acciones personalizadas. Los desarrolladores pueden editar la cinta de opciones para modificar las acciones para las tres acciones restantes: mostrar la lista, agregar registro y eliminar registro.  
  

## <a name="show-list-behavior"></a>Mostrar comportamiento de la lista  
 Al mostrar una lista en formularios con los [formularios actualizados](main-form-presentations.md#updated-forms), cada subcuadrícula incluye el botón **Abrir vista** ![Botón Abrir vista](media/crm-itpro-cust-openview.PNG "Botón Abrir vista") en la esquina superior derecha cuando la entidad también aparece como una de las entidades incluidas en el área de navegación del editor de formularios. Al elegir este botón se abrirá la vista. El comportamiento cambiará en función de la opción elegida para la propiedad **Registros**.  
  
 Al seleccionar **Solo los registros relacionados**, la vista se abrirá usando una de las vistas asociadas en la misma ventana. Para volver al formulario, use el botón Atrás o elija el valor del nombre principal del registro actual en la barra de navegación.  
  
 Al seleccionar **Todos los tipos de registros**, la vista se abrirá en una nueva ventana.  

## <a name="add-record-behavior"></a>Agregar comportamiento del registro  
 Al mostrar una lista en formularios con los [formularios actualizados](main-form-presentations.md#updated-forms), cada subcuadrícula incluye el botón **Agregar registro** ![Botón Agregar](media/crm-itpro-cust-subgridadd.PNG "Botón Agregar") en su lado superior derecho. Al elegir este botón podrá agregar un registro. Este comportamiento cambiará en función de la opción elegida para la propiedad **Registros** y si la búsqueda es para los registros de actividad.  
  
 Al seleccionar **Solo los registros relacionados** el comportamiento predeterminado es el comportamiento para agregar los registros existentes. Los usuarios ven una búsqueda en línea para buscar un registro existente primero. Esto ayuda a evitar la creación de registros duplicados.  Si no puede encontrar un registro de existente, puede seleccionar la opción **Nuevo**. Cuando se cree un nuevo registro, las asignaciones de campos definidas en la relación se aplicarán. Más información: [Asignar campos de entidades](../common-data-service/map-entity-fields.md)   
  
 Al seleccionar **Todos los tipos de registros** el comportamiento predeterminado es agregar un nuevo registro. El formulario de creación rápida se mostrará si la entidad de destino tiene uno. De lo contrario, aparecerá el formulario principal de la entidad predeterminada.  
  
 Si la subcuadrícula muestra actividades, las personas deberán elegir primero el tipo de actividad y después ver el comportamiento de "agregar registro nuevo".  
  
## <a name="delete-record-behavior"></a>Eliminar comportamiento del registro  
 Cuando selecciona un registro en una subcuadrícula, el botón **Eliminar** ![Icono Eliminar sublista](media/crm-itpro-cust-subgriddelete.PNG "Icono Eliminar sublista") aparece en la parte derecha de la fila. El comportamiento de esta acción de eliminación es diferente según el tipo de relación con la entidad actual.  
  
 Cuando la subcuadrícula usa una relación 1:N (uno a varios), el comportamiento de eliminación de registro normal es mostrar un diálogo de confirmación antes de eliminar el registro.  
  
 Cuando la subcuadrícula usa una relación N:N (varios a varios), el registro de la entidad de relación (o intersección) relacionado con dos registros se elimina sin una confirmación y el registro no se mostrará más en la subcuadrícula. No obstante, el registro que se mostraba no se elimina.  

## <a name="next-steps"></a>Pasos siguientes

[Utilizar el formulario Principal y sus componentes](use-main-form-and-components.md)
