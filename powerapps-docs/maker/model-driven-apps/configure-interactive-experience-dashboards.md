---
title: Configurar paneles de experiencia interactiva de aplicaciones controladas por modelos en PowerApps | Microsoft Docs
description: Aprenda a configurar paneles de experiencia interactiva en PowerApps
keywords: Paneles interactivos; Customer Service; Microsoft Dynamics 365; centro de servicio interactivo
author: Mattp123
ms.author: matp
manager: kvivek
ms.custom: ''
ms.date: 05/21/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: d1446a95-14bf-4b15-a905-72fce07f4c76
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="configure-model-driven-app-interactive-experience-dashboards"></a>Configurar paneles de experiencia interactiva de aplicaciones controladas por modelos

Los paneles de experiencia interactiva pueden convertirse en un área de trabajo integral para los usuarios de las aplicaciones, como representantes de servicio, para ver la información sobre la carga de trabajo y actuar. Son totalmente configurables, están basados en roles de seguridad y proporcionan la información de carga de trabajo a través de secuencias múltiples en tiempo real. Los usuarios de panel interactivo no necesitan navegar por la aplicación en busca de un registro específico; pueden actuar sobre él directamente desde el panel. 

 Los paneles de experiencia interactiva se ofrecen en dos formatos: de varias secuencias y de secuencia única. Además, los paneles de varias secuencias pueden ser paneles específicos de la página principal o de la entidad. Los paneles específicos de la entidad se configuran en una parte diferente de la interfaz de usuario y se precargan parcialmente con información de configuración específica de la entidad.  
  
 Los paneles de varias secuencias muestran datos en tiempo real sobre varias secuencias de datos. No hay un límite en el número de secuencias que puede configurar en el panel. Los datos de una secuencia se pueden basar únicamente en una entidad, pero cada secuencia se puede basar en otra entidad. En los paneles específicos de la entidad, todas las secuencias se basan en la misma entidad. Los datos fluyen desde distintas vistas o colas, por ejemplo, **Mis actividades**, **Mis casos**o **Casos de la cola bancarios**. 
  
 Los paneles de secuencia única muestran datos en tiempo real a lo largo de una secuencia basados en una vista o cola de la entidad. Las ventanas se colocan en la parte derecha de los paneles y se muestran siempre. Los paneles de secuencia única suelen ser útiles para los clientes potenciales o administradores del servicio de nivel 2, que supervisan menos casos, pero más complejos o remitidos a una instancia superior.  
  
 Los paneles de varias secuencias y de secuencia única contienen gráficos interactivos que proporcionan un recuento de registros relevantes, como casos por prioridad o por estado. Estos gráficos también actúan como filtros visuales. Los filtros visuales (gráficos interactivos) se basan en varias entidades y en los paneles de secuencia única, la entidad en la secuencia de datos define la entidad de filtro visual.   
  
 Los usuarios pueden aplicar filtrado adicional con filtros globales y filtros temporales. El filtro global trabaja en un nivel de campo en todos los gráficos, y también en secuencias y ventanas que se basan en la entidad de filtro (especifique la entidad de filtro al configurar los filtros visuales). 
  
> [!NOTE]
>  Los paneles interactivos son compatibles con soluciones y se pueden exportar y luego importar en otro entorno como solución. Sin embargo, las colas en las que se basan las secuencias y las ventanas no son compatibles con soluciones. Antes de importar la solución del panel en el sistema de destino, las colas tienen que crearse manualmente en el sistema de destino en **Configuración** > **Administración de servicios** > **Colas**. Después de crear las colas, importe la solución de panel en el sistema de destino, y a continuación edite las secuencias o las ventanas que se basan en las colas para asignar las colas recién creadas adecuadamente.  
  
 Las ilustraciones de este tema muestran paneles de varias secuencias y de secuencia única con el panel del encabezado. Debajo del encabezado se ven filtros visuales y secuencias. En el panel de secuencia única también se ven ventanas. Para cada tipo de panel, puede elegir entre varios diseños diferentes que también se muestran. El encabezado del panel contiene los siguientes controles e iconos que se pueden seleccionar, de izquierda a derecha: selector de paneles, actualizar, icono de filtro visual, icono de filtro global y filtro temporal.  
  
### <a name="multi-stream-dashboard-standard-view"></a>Vista estándar del panel de varias secuencias  
 En el panel de varias secuencias, verá una fila de filtros visuales en la parte superior con las secuencias de datos por debajo de ellos.  
 
![Panel interactivo de varias secuencias](../model-driven-apps/media/interactive-dashboards-multi-stream.png) 
   
### <a name="multi-stream-dashboard-tile-view"></a>Vista de ventana del panel de varias secuencias  
 El mismo panel, solo en la vista de ventana.  
  
 ![Vista de ventana del panel de varias secuencias](../model-driven-apps/media/interactive-dashboards-multi-stream-tiles.png "Vista de ventana del panel de varias secuencias")  
  
### <a name="multi-stream-dashboard-layouts"></a>Diseños de paneles de varias secuencias  
 Para los paneles de varias secuencias, puede elegir entre cuatro diseños diferentes.  

 > [!div class="mx-imgBorder"] 
 > ![Diseños de paneles de varias secuencias](../model-driven-apps/media/interactive-dashboards-multi-stream-layout.png "Diseños de paneles de varias secuencias")  
  
### <a name="multi-stream-entity-specific-dashboard"></a>Panel específico de la entidad de varias secuencias  
 El panel específico de la entidad para la entidad `Case` aparece aquí.  
  
 ![Abrir panel de casos](../model-driven-apps/media/interactive-dashboard-cases-dashboard.PNG "Abrir panel de casos")  
  
### <a name="single-stream-dashboard"></a>Panel de secuencia única  
 El panel de secuencia única contiene la secuencia de datos a la izquierda y filtros visuales y las ventanas a la derecha.  
  
 ![Panel del centro de servicio interactivo de secuencia única](../model-driven-apps/media/interactive-dashboards-single-stream.png "Panel del centro de servicio interactivo de secuencia única")  
  
### <a name="single-stream-dashboard-layouts"></a>Diseños de paneles de secuencia única  
 Para los paneles de secuencia única, puede elegir entre cuatro diseños diferentes.  
 
 > [!div class="mx-imgBorder"] 
 > ![Diseños de paneles de secuencia única](../model-driven-apps/media/interactive-dashboards-single-stream-layout.png "Diseños de paneles de secuencia única")  
  
<a name="BKMK_Enable"></a>   
## <a name="configure-entities-fields-and-security-roles-for-the-interactive-dashboards"></a>Configurar entidades, campos, y los roles de seguridad para los paneles interactivos  
 Cuando configura paneles interactivos, la primera tarea es habilitar las entidades, campos, y los roles de seguridad para la experiencia activa.  
  
### <a name="entities-enabled-for-interactive-experience"></a>Entidades habilitadas para experiencia interactiva
 Todas las entidades compatibles con la interfaz unificada tienen habilitado el panel de la experiencia interactiva.
  
### <a name="configure-fields"></a>Configurar campos  
 Para que un campo aparezca en el filtro global y se incluya en la ordenación de secuencia de datos, debe establecer dos indicadores, tal como se muestra en el siguiente ejemplo para el campo **IsEscalated** de la entidad Caso.  

 > [!div class="mx-imgBorder"] 
 > ![Habilitar un campo para filtro global y ordenación](../model-driven-apps/media/global-filter-sort-8.png "Habilitar un campo para filtro global y ordenación")  
  
### <a name="configure-global-filter-fields"></a>Configurar campos de filtro global  
 Para que un campo aparezca en el filtro global, es necesario configurar el indicador **Aparece en el filtro global en la experiencia interactiva** para este campo. Los campos que configure aparecerán en el control flotante de filtro global cuando se haga clic en el icono de filtro global en el encabezado del panel. En la ventana de control flotante, los representantes de servicio pueden seleccionar los campos que desean filtrar globalmente, en gráficos, y también en secuencias y ventanas que se basan en la entidad de filtro. Para obtener más información acerca de la entidad de filtro vea la sección "Configurar paneles interactivos de varias secuencias" más adelante en este tema.  
  
 La ventana de control flotante de filtro global se muestra aquí:  
  
 ![Agregar dos campos de filtro global](../model-driven-apps/media/interactive-dashboards-global-filter-two-fields.png "Agregar dos campos de filtro global")  
  
> [!NOTE]
>  Cuando se configura un filtro visual (gráfico interactivo) basándose en los campos como prioridad o estado, una práctica recomendada también es permitir que estos campos (prioridad, estado) aparezcan en el filtro global.  
  
El siguiente procedimiento proporciona los pasos para establecer el indicador de filtro global:
  
1. Abra el [explorador de soluciones](advanced-navigation.md#solution-explorer).  
  
2. En **Componentes**, expanda **Entidades** y, a continuación, expanda la entidad que desea. Si no se muestra la entidad que desea, seleccione **Agregar existentes** para agregarla.  
  
3.  En el panel de navegación, seleccione **Campos** y en la cuadrícula, haga doble clic en el campo que desee habilitar.  
  
4.  En la pestaña **General**, seleccione la casilla **Aparece en el filtro global en la experiencia interactiva**. Seleccione **Guardar y cerrar**.  
  
5.  Seleccione **Publicar** para que los cambios surtan efecto.  
  
6.  Seleccione **Preparar personalizaciones de cliente**.  
  
### <a name="configure-sortable-fields"></a>Configurar campos que se pueden ordenar  
 Para que un campo se use para ordenar datos de secuencia, debe establecer el indicador **Se puede ordenar en el panel de experiencia interactiva** para este campo. Los campos que configure para ordenar aparecerán en la lista desplegable en el cuadro de diálogo de control flotante **Editar propiedad** cuando el usuario selecciona **Más (...)** en el encabezado de secuencia. El siguiente ejemplo muestra el cuadro de diálogo de control flotante con la lista de campos disponibles para ordenar, en la lista desplegable **Ordenar por**. La ordenación predeterminada siempre se establece en el campo **Fecha de modificación**.  
  
 ![Ordenar por lista desplegable](../model-driven-apps/media/interactive-dashboard-sortable-fields-dropdown.png "Ordenar por lista desplegable")  
  
El siguiente procedimiento proporciona los pasos para establecer el indicador de ordenación:
  
1. Abra el [explorador de soluciones](advanced-navigation.md#solution-explorer).   
2. En **Componentes**, expanda **Entidades** y, a continuación, expanda la entidad que desea. Si no se muestra la entidad estándar que desea, seleccione **Agregar existentes** para agregarla.  
  
3.  En el panel de navegación, seleccione **Campos** y en la cuadrícula, haga doble clic en el campo que desee habilitar.  
  
4.  En la pestaña **General**, seleccione la casilla **Se puede ordenar en el panel de experiencia interactiva**. Seleccione **Guardar y cerrar**.  
  
5.  Seleccione **Publicar** para que los cambios surtan efecto.  
  
6.  Seleccione **Preparar personalizaciones de cliente**.  
  
### <a name="enable-security-roles"></a>Habilitar roles de seguridad  
 Seleccione y habilite roles de seguridad que podrán ver los paneles interactivos.  
  
El siguiente procedimiento proporciona los pasos para habilitar los roles de seguridad para la experiencia interactiva:
  
1. Abra el [explorador de soluciones](advanced-navigation.md#solution-explorer).  
  
2. En **Componentes**, seleccione **Paneles**.  
  
4.  En la cuadrícula, seleccione el panel interactivo que desea y seleccione **Habilitar roles de seguridad** en la barra de tareas.  
  
5.  En el diálogo **Asignar roles de seguridad**, seleccione la opción **Mostrar solo a estos roles de seguridad determinados** y seleccione los roles que desea habilitar. Seleccione **Aceptar**.  
  
6.  Seleccione **Publicar** para que los cambios surtan efecto.  
  
7.  Seleccione **Preparar personalizaciones de cliente**.  
  
 ![Habilitar roles de seguridad](../model-driven-apps/media/interactive-dashboards-enable-security-roles.png "Habilitar roles de seguridad")  
  
 ![Asignar roles de seguridad](../model-driven-apps/media/interactive-dashboards-assign-security-roles.png "Asignar roles de seguridad")  
  
<a name="BKMK_Configure"></a>   
## <a name="configure-interactive-experience-dashboards"></a>Configurar paneles de experiencia interactiva  
 En la siguiente sección se describe cómo configurar los diferentes tipos de paneles interactivos.  
  
### <a name="configure-a-multi-stream-interactive-dashboard-using-the-4-column-layout"></a>Configure un panel interactivo de varias secuencias utilizando el diseño de 4 columnas  
 
1.  Iniciar sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

2.  Seleccione **Controlado por modelo** (parte inferior izquierda).  
  
3.  Seleccione **Datos** > **Entidades** > seleccione la entidad que desee. 

4.  Seleccione la pestaña **Paneles** y, a continuación, en la barra de herramientas seleccione **Agregar panel**.  
  
5.  Elija el diseño, 2, 3 o 4 de ancho de las columnas.  
  
6.  Cuando se abre el formulario del panel, rellene la información de filtro en la parte superior del formulario, como se indica aquí.  
 
 > [!div class="mx-imgBorder"] 
 > ![Agregar filtros visuales](../model-driven-apps/media/interactive-dashboards-add-visual-filters.png "Agregar filtros visuales")  
  
   - **Entidad de filtro**: Los filtros visuales (interactivos gráficos) y los atributos de filtro global se basan en esta entidad.  
      
    - **Vista de entidad**: Los filtros visuales (gráficos interactivos) se basan en esta vista.  
      
    - **Filtrar por**: El campo al que se aplica el filtro temporal.  
      
    - **Plazo de tiempo**: El valor predeterminado del filtro temporal para el campo **Filtrar por**.  
      
 Una vez especificada la información de filtrado, comience a agregar componentes para los gráficos y las secuencias de datos. Para agregar un componente, simplemente seleccione el elemento del centro del gráfico o la secuencia y, cuando aparezca el cuadro de diálogo, especifique la información necesaria, como se muestra en las siguientes ilustraciones.  
  
 Agregue el gráfico de anillos **Casos por prioridad**.
  
 > [!div class="mx-imgBorder"] 
 > ![Agregar un componente de gráfico de anillos.](../model-driven-apps/media/interactive-dashboards-add-chart-circle.png "Agregar un componente de gráfico de anillos.")  
  
 Algunos gráficos, como los gráficos de barras o los gráficos circulares, se generan mostrando los datos almacenados en el sistema. Los gráficos de anillos y gráficos de etiqueta cargan se cargan como imágenes estáticas y no aparecen en la vista previa de los datos reales.  
  
> [!NOTE]
>  Los gráficos configurados para los filtros visuales pueden usar los campos de la entidad **Filtro** y también entidades relacionadas. Cuando se usan los gráficos basados en campos de entidad relacionados, los representantes del servicio al cliente pueden filtrar gráficos con estos campos de entidad relacionados. Los campos que se basan en la entidad relacionada tienen normalmente el siguiente formato en la ventana de configuración de gráficos: "nombre del campo (nombre de la entidad)", como el campo **Modificado por (delegado)**. Para crear gráficos de varias entidades, debe agregar campos de una entidad relacionada a cualquiera de las vistas y luego usar estos campos mientras crea gráficos.  
 
 > [!div class="mx-imgBorder"] 
 > ![Crear gráficos para filtros visuales](../model-driven-apps/media/interactive-dashboard-visual-charts-x-y-axes.PNG "Crear gráficos para filtros visuales")  
  
 A continuación, hay que configurar las secuencias. Al igual que ocurre al agregar componentes en los gráficos, seleccione el elemento dentro del panel de secuencia. Cuando aparezca el cuadro de diálogo, seleccione **Vista** o **Cola** en función del elemento que desea que use la secuencia. Introduzca la información requerida tal y como se muestra en las ilustraciones siguientes.  
  
> [!NOTE]
>  La opción **Cola** está disponible en el cuadro de diálogo solo para entidades habilitadas para cola. En el caso de los paneles de entidad, si la entidad no está habilitada para cola, no verá la opción **Cola** en el cuadro de diálogo. Solo puede usar la opción **Vista** en la secuencia de paneles para las entidades que no están habilitadas para cola.  
  
 Configure la secuencia para los **Elementos disponibles para trabajar en ellos** como se muestra aquí:  
  
 ![Agregar una secuencia de mis casos activos.](../model-driven-apps/media/interactive-dashboards-add-stream-case.png "Agregar una secuencia de mis casos activos.")  
  
 El siguiente ejemplo es un ejemplo del panel de gráficos, de izquierda a derecha: gráfico de anillos, gráfico de etiqueta y gráfico de barras:  
 
 > [!div class="mx-imgBorder"] 
 > ![Todos los gráficos interactivos](../model-driven-apps/media/interactive-dashboards-add-all-charts.png "Todos los gráficos interactivos")  
  
 Esta ilustración es un ejemplo del panel de secuencia con varias secuencias:  
 
 > [!div class="mx-imgBorder"] 
 > ![Agregar todas las secuencias](../model-driven-apps/media/interactive-dashboards-add-all-streams.png "Agregar todas las secuencias")  
  
 Después de completar la configuración del panel, guárdelo y publique las personalizaciones para que los cambios surtan efecto. Además, asegúrese de seleccionar **Preparar personalizaciones de cliente**.  
  
#### <a name="edit-or-delete-individual-streams-of-an-existing-dashboard"></a>Editar o eliminar secuencias individuales de un panel existente  
  
1. Iniciar sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).   
  
2. Seleccione **Controlado por modelo** (parte inferior izquierda), **Datos** > **Entidades** > seleccione la entidad que desee. Seleccione la ficha **Paneles**.  
  
     O bien  
   
   Abra el [explorador de soluciones](advanced-navigation.md#solution-explorer) y, a continuación, en **Componentes** seleccione **Paneles**.
  
3.  En la cuadrícula, seleccione el nombre del panel interactivo que desea editar para abrirlo.  
  
4.  Seleccione la secuencia que desea editar para seleccionarla y luego seleccione **Editar componente**.  
  
5.  En función de si desea agregar una vista o una cola a la secuencia, seleccione los detalles de la vista o la cola para la secuencia y, a continuación seleccione **Establecer**.  
  
6.  Seleccione **Guardar**.  
  
 También puede eliminar una secuencia individual de un panel. Para ello, seleccione la secuencia y, en la barra de comandos, seleccione **Eliminar**.  
  
### <a name="configure-an-entity-specific-dashboard"></a>Configurar un panel específico de la entidad  
 Un panel específico de la entidad es un panel de varias secuencias. La configuración de este panel es similar a configurar un panel de varias secuencias de la página principal, pero se realiza en un lugar distinto de la interfaz de usuario y hay otras diferencias de menor importancia. Por ejemplo, en lugar de seleccionar una entidad, algunos campos del panel específico de la entidad se preestablecen en la entidad para la que está creando el panel.  
  
1.  Iniciar sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

2.  Seleccione **Controlado por modelo** (parte inferior izquierda).  
  
3.  Seleccione **Datos** > **Entidades** > seleccione la entidad que desee. 

4.  Seleccione la pestaña **Paneles** y, a continuación, en la barra de herramientas seleccione **Agregar panel**.  
  
5.  Elija el diseño, 2, 3 o 4 de ancho de las columnas.    
  
6.  Cuando se abre el formulario del panel, la **Entidad de filtro** se preestablece en la entidad para la que está creando el panel. La lista desplegable **Vista de entidad** contiene las vistas disponibles para la entidad. Seleccione la vista y rellene el resto de la información necesaria en la página.  
  
 El resto de instalación es muy similar a la instalación del panel de varias secuencias de página principal que se describe en la sección anterior.  
  
### <a name="configure-a-single-stream-dashboard"></a>Configurar un panel de secuencia única  
 La configuración de un panel de secuencia única es similar a la del panel de varias secuencias. Todos los pasos de navegación de la interfaz de usuario son los mismos que para el panel de varias secuencias. Puede elegir un diseño que incluya ventanas o el diseño que no las incluye. Si se incluyen ventanas, siempre se muestran en el panel. Para configurar una ventana, seleccione el icono del centro de la ventana. Cuando se abre la ventana **Agregar ventana**, complete los datos necesarios. La ilustración siguiente es un ejemplo de configuración de ventanas.  
  
 ![Agregar una ventana al panel de secuencia única](../model-driven-apps/media/interactive-dashboard-add-tile-single-stream.png "Agregar una ventana al panel de secuencia única")  
  
<a name="BKMK_ConfigureColors"></a>   
## <a name="configure-dashboard-colors"></a>Configurar los colores del panel  
 Para todos los campos del tipo **Conjunto de opciones** y **Dos opciones**, como **Tipo de caso**, **Se ha remitido a una instancia superior** o **Prioridad** de la entidad `Case`, puede configurar un color determinado que aparecerá en los gráficos y secuencias para valores de campos específicos. Por ejemplo, los casos prioritarios se pueden mostrar en rojo, los casos de prioridad media en azul, y los casos de prioridad baja en verde en los gráficos interactivos. En las secuencias, habrá una barra vertical fina de color junto a la descripción del elemento de trabajo.  
  
> [!NOTE]
>  La codificación de color no está disponible para los gráficos de etiqueta y los gráficos de anillos. Estos gráficos aparecen en el panel en tonos de blanco, gris, y negro.  
  
1.  Abra el [explorador de soluciones](advanced-navigation.md#solution-explorer).  
2.  En **Componentes**, expanda **Entidades** y, a continuación, expanda la entidad que desea. Si no se muestra la entidad que desea, seleccione **Agregar existentes** para agregarla.  
  
3.  En el panel de navegación, seleccione **Campos**. En la cuadrícula, haga doble clic en el campo para el que desea configurar el color.  
  
4.  En la pestaña **General**, en la subárea **Tipo**, seleccione **Sí** y, a continuación, seleccione **Editar**.  
  
5.  Cuando aparezca el diálogo **Modificar valor de lista**, establezca el nuevo valor en el cuadro de texto **Color**. Seleccione **Aceptar**.  
  
     Seleccione **Guardar y cerrar**.  
  
7.  Seleccione **Publicar** para que los cambios surtan efecto.  
  
En el siguiente ejemplo, modificamos el color para el campo **Se ha remitido a una instancia superior**. Use el botón **Editar** para abrir el cuadro de diálogo **Modificar valor de lista**:  
 
 > [!div class="mx-imgBorder"] 
 > ![Cambiar color en el panel](../model-driven-apps/media/interactive-dashboards-change-color-edit-button.PNG "Cambiar color en el panel")  
  
Cuando se abra el cuadro de diálogo **Modificar valor de lista**, elija el color como se muestra aquí:  
  
 ![Modificar el color del panel](../model-driven-apps/media/interactive-dashboards-modify-color-value.png "Modificar el color del panel")  
  
### <a name="next-steps"></a>Pasos siguientes  
 
[Crear o editar paneles](create-edit-dashboards.md)
 

