---
title: Tutorial para agregar o editar componentes de aplicación controlada por modelos con Power Apps | MicrosoftDocs
description: Utilice el diseñador de aplicaciones de Power Apps para agregar o editar componentes.
keywords: ''
ms.date: 03/05/2020
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: be93b9d7-f1c2-4ee7-8d7c-0f5c34dfa5f7
ms.author: matp
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 17
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5f357bd55060258ca8545fae6ad4bb3c7621ab5c
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136497"
---
# <a name="tutorial-add-or-edit-model-driven-app-components-in-the-power-apps-app-designer"></a>Tutorial: Agregar o editar componentes de aplicación controlada por modelos en el diseñador de aplicaciones de Power Apps

En este tutorial aprenderá a agregar y quitar componentes de una aplicación controlada por modelos. 

Una aplicación controlada por modelos se compone de distintos componentes. Puede añadir dos tipos de componentes a una aplicación: artefactos y activos de la entidad. En el contexto del diseñador de la aplicación, las entidades, panel, y los flujos de proceso de negocio son artefactos de una aplicación. Los activos de entidad constan de formularios, vistas, gráficos y paneles.  
  
El diseñador de la aplicación hace referencia a metadatos existentes en la solución predeterminada. Puede usarlo para crear componentes como formularios, vistas, gráficos y paneles.  
  
## <a name="app-designer-layout"></a>Diseño del Diseñador de la aplicación  
 El diseñador de la aplicación tiene dos áreas principales. En la parte izquierda está el lienzo donde se agregan componentes de la aplicación.  
  
 > [!div class="mx-imgBorder"]
 > ![Lienzo del diseñador de la aplicación](../model-driven-apps/media/app-designer-canvas-pane.png "Lienzo del diseñador de la aplicación")

 En el lado derecho están las pestañas que usará para seleccionar componentes y establecer propiedades de componentes.  
 
 > [!div class="mx-imgBorder"]
 > ![Componentes del diseñador de aplicaciones](../model-driven-apps/media/app-designer-canvas-components-tab.png "Componentes del diseñador de aplicaciones")  
  
 En el lienzo, verá las áreas para el mapa del sitio, flujo de proceso de negocio, panel y entidades. Cuando selecciona un panel o un flujo de proceso de negocio o configura un mapa del sitio, el diseñador de la aplicación agrega automáticamente las entidades que se usan en estos componentes al lienzo. Después de que las entidades estén en su lugar, todo lo que necesita hacer es seleccionar cada entidad y agregar los activos de entidad necesarios, tales como formularios, vistas y gráficos.
 
 También puede usar **Buscar en el lienzo** para buscar componentes en el lienzo. Si selecciona **Buscar en el lienzo**, se abre una nueva pestaña de búsqueda a la derecha de las pestañas en el panel derecho.   
 
 > [!div class="mx-imgBorder"]
 > ![Opción de búsqueda en el lienzo](media/app-designer-search-tab.png "Buscar en el lienzo")

## <a name="open-an-app"></a>Abra una aplicación
1. Inicie sesión en [Power Apps](https://make.powerapps.com/). 

2. Seleccione una aplicación basada en modelos ya existente o seleccione **Aplicación basada en modelo desde cero**. Para obtener información acerca de cómo crear una aplicación, consulte [Creación o edición de una aplicación controlada por modelos usando el diseñador de aplicaciones](create-edit-app.md#create-an-app).

## <a name="add-an-artifact-entity-dashboard-or-business-process-flow"></a>Agregar un artefacto (entidad, panel, o flujo de proceso de negocio)  
 Cuando se agrega un panel o un flujo de proceso de negocio a una aplicación, las entidades que usan se agregan automáticamente a la aplicación. Cuando agrega una entidad, las ventanas de los activos se agregan automáticamente. Hay dos formas de agregar artefactos al lienzo del diseñador: mediante el botón **Agregar** ![Botón Agregar en el diseñador](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "Agregar botón en el diseñador") en la barra de comandos o con las ventanas de la pestaña **Componentes**.  
  
 Estos son los pasos para agregar un panel a la aplicación. Use los mismos pasos para agregar un proceso de flujo de negocio o una entidad.  
  
1.  En el lienzo del diseñador de la aplicación, selecciones la ventana **Paneles**.  
  
     En el lienzo del diseñador de la aplicación, el panel derecho muestra los paneles que se encuentran disponibles en la solución predeterminada.  
  
    > [!TIP]
    >  Como alternativa, puede realizar una de las acciones siguientes:  
    >   
    > - Seleccione **Agregar** ![Botón Agregar en el diseñador](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "Agregar botón en el diseñador") y, a continuación, seleccione **Paneles**.  
    > - En la pestaña **Componentes**, en **Artefactos**, seleccione **Paneles**.  
  
2.  En el cuadro **Buscar**, escriba algunas palabras clave para el nombre del panel que busca.  
  
     La lista del panel se filtrará para que aparezcan los resultados que coincidan con las palabras claves.  
  
3.  Si desea que los usuarios sólo usen paneles seleccionados, active la casilla para los paneles que desee agregar. Se puede elegir entre los siguientes tipos de paneles:
    - **Paneles clásicos** aparecen en la aplicación web y la aplicación Interfaz unificada.
    - **Paneles interactivos** solo aparecen en la aplicación Interfaz unificada. Si ha seleccionado el tipo de cliente de la aplicación como aplicaciones web, la opción **Paneles interactivos** no se mostrará.

     Esos paneles se agregarán a la ventana **Panel** en el lienzo del diseñador de la aplicación. La ventana **Panel** también muestra el número de paneles agregados a la aplicación. Si no selecciona un panel, **Todos** aparecerán en vez del recuento de paneles y estarán disponibles todos los paneles para los usuarios cuando usen la aplicación.  
  
     Todas las entidades que utiliza el panel también se agregan al área **Vista de la entidad**. Por ejemplo, si agrega el panel Administrador de servicio de atención al cliente, las entidades Caso, Derechos y Cola se agregan al área Vista de entidad. Para cada entidad, también se agregan las ventanas de sus activos. Puede usar estas ventanas para agregar formularios, vistas y gráficos. Más información:[Agregar o editar componentes en el diseñador de aplicaciones de Power Apps](add-edit-app-components.md#bkmk_AddEntityAssets)   
  
    > [!div class="mx-imgBorder"]
    > ![Agregar la entidad al lienzo del diseñador de aplicaciones](../model-driven-apps/media/add-entity-app-designer-canvas.png "Agregar una entidad al lienzo del diseñador de aplicaciones")  
  
4.  Si el panel que desea no existe en la solución predeterminada, cree un panel seleccionando **Crear nuevo** en la pestaña **Componentes** en el lado derecho del lienzo.  
  
     > [!div class="mx-imgBorder"]
     > ![Crear nuevo vínculo en la pestaña Componentes del diseñador de aplicaciones](../model-driven-apps/media/app-designer-components-tab-create-new.png "Crear nuevo vínculo en la pestaña Componentes del diseñador de aplicaciones")  
  
     Se abrirá el diseñador de paneles. Más información: [Crear y editar paneles](create-edit-dashboards.md)  
  
    > [!NOTE]
    > - Cuando se agrega un flujo de proceso de negocio o una entidad, la opción **Crear nuevo** abre el diseñador correspondiente. Para obtener más información sobre cómo crear flujos de proceso de negocio o entidades, consulte [Crear un flujo de proceso de negocio](/flow/create-business-process-flow) y [Crear una entidad personalizada](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-create-entity).  
      
  
5.  Cuando haya terminado de agregar artefactos, en la barra de comandos, seleccione **Guardar**.  
  
<a name="bkmk_AddEntityAssets"></a>   
## <a name="add-entity-assets-forms-views-charts-or-dashboards"></a>Agregar activos de la entidad (formularios, vistas, gráficos o paneles)  
 Con los artefactos en su lugar, ahora puede comenzar a agregar activos de la entidad como formularios, vistas, gráficos y paneles a la aplicación.
Además, si está usando al cliente interfaz unificada, también puede agregar activos de panel de entidad a la aplicación.  
  
 En esta sección se describen los pasos para agregar un formulario a la aplicación. Use los mismos pasos para agregar una vista o un gráfico a la aplicación.  
  
1.  En el lienzo del diseñador de la aplicación, seleccione la ventana **Formularios** de la entidad a la que desee agregar un formulario.  
  
     En el lienzo del diseñador de la aplicación, la fila completa para la entidad está seleccionada. En el lado derecho verá todos los formularios existentes para la entidad seleccionada.  
  
    > [!NOTE]
    >  Como alternativa, puede realizar una de las acciones siguientes:  
    >   
    > - Seleccione **Agregar** ![Botón Agregar en el diseñador](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "Agregar botón en el diseñador") y, a continuación, seleccione **Formularios**.  
    > - En la pestaña **Componentes**, en **Activos de la entidad**, seleccione **Formularios**.  
  
    > [!TIP]
    >  Para todas las entidades seleccionadas para la aplicación, un botón **Más opciones** (**...**) aparece en la lista **Seleccionar entidades** en la pestaña **Componentes**. Para agregar todos los activos para la entidad seleccionada, seleccione **Más opciones** (**...**) y seleccione **Agregar todos los activos**.  
  
2.  Si desea que los usuarios de la aplicación sólo usen formularios seleccionados, active las casillas para los formularios que desee agregar. Los formularios definen cómo los usuarios verán e interactuarán con los datos en la aplicación. 
 
     La ventana del formulario de la entidad seleccionada mostrará el número de formularios agregados.  
  
     ![Ventana del formulario para la entidad Caso](../model-driven-apps/media/add-forms-entity.png "Ventana del formulario para la entidad Caso")  
  
     Por ejemplo, si no selecciona ningún formulario para una entidad, todos los formularios de la entidad se mostrarán a los usuarios finales mientras utilizan la aplicación. Este comportamiento es similar para los gráficos y vistas también, si no se selecciona ninguna vista o gráfico. Esto ayuda a crear aplicaciones rápidamente cuando necesita trabajar con todos los componentes disponibles; no es necesario seleccionar cada componente durante el diseño de la aplicación.  

     Si no se selecciona ningún panel o flujo de procesos de negocio, todos los paneles y los flujos de procesos negocio estarán disponibles para los usuarios mientras utilizan la aplicación.
  
    > [!NOTE]
    > Para que la aplicación se ejecute, cada entidad que agrega debe tener al menos un formulario activo. Si ha seleccionado múltiples formularios, el primer formulario activo que aparece en la solución predeterminada se usará cuando los usuarios ejecuten la aplicación.  
  
3.  Si desea agregar un nuevo formulario que no esté disponible en la lista, seleccione **Crear nuevo**.  
  
     En la lista desplegable, seleccione el tipo de formulario que desea crear.  
  
    > [!NOTE]
    >  La lista desplegable solo está disponible cuando está agregando formularios. No está disponible para las vistas y gráficos.  
  
     Se abre el diseñador de formularios. Más información: [Crear y diseñar formularios](create-design-forms.md)  
  
     Cuando agrega una vista o un gráfico, la opción **Crear nuevo** abre el diseñador correspondiente. Más información: [Comprender las vistas](create-edit-views.md) y [Creación o edición de un gráfico del sistema](create-edit-system-chart.md)  
  
    > [!NOTE]
    >  Cuando agrega una vista, puede hacer referencia solo a las vistas públicas que se muestran en el nodo **Vistas** en el explorador de soluciones.  
  
4. Seleccione la flecha abajo ![Icono desplegable](../model-driven-apps/media/drop-down-icon.png "flecha abajo") flecha abajo para expandir la ventana y ver una lista de formularios que se han agregado.  
  
     ![Ventana del formulario expandida en el diseñador de aplicaciones](../model-driven-apps/media/app-designer-expanded-form-tile.png "Ventana del formulario expandida en el diseñador de aplicaciones")  
  
5.  Repita estos pasos para agregar vistas y los gráficos de la entidad a la aplicación.  
  
6.  Seleccione **Guardar**.  
  
## <a name="edit-or-remove-artifacts"></a>Editar o quitar artefactos  
  
- Para editar un panel o flujo de proceso de negocio, seleccione la flecha abajo ![Icono desplegable](../model-driven-apps/media/drop-down-icon.png "flecha abajo") para expandir la ventana y, a continuación, elija el botón Diseñador del mapa de sitio ![botón Abrir diseñador del mapa de sitio](../model-driven-apps/media/dynamics365-open-designer.PNG "Botón Abrir diseñador del mapa del sitio") correspondientes al panel o flujo del proceso de negocio que desea editar.  
  
     El diseñador para el artefacto seleccionado se abre.  
  
- Para quitar un panel o flujo de proceso de negocio, seleccione la flecha abajo ![Icono desplegable](../model-driven-apps/media/drop-down-icon.png "flecha abajo") para expandir la ventana y, después, seleccione el panel o el flujo de proceso de negocio que desea quitar. En la barra de comandos, seleccione **Quitar**.  

    Otra forma de quitar un panel o flujo de proceso de negocio es desactivando la casilla correspondiente en la pestaña **componentes**.
  
- Para editar o quitar una entidad, seleccione la ventana de la entidad y, luego, en la barra de comandos, seleccione **Editar** o **Quitar**. Cuando edita una entidad, el explorador de soluciones se abre, donde puede realizar cambios a la entidad.  
  
     Como alternativa, para quitar un componente, seleccione el panel, el flujo de proceso de negocio o la ventana de la entidad. En la pestaña **Componentes**, desactive las casillas de los artefactos que desea quitar del diseñador.  
  
    > [!NOTE]
    >  Cuando realice cambios a una entidad&mdash;como cambiar un nombre para mostrar o una descripción de la entidad&mdash;, los cambios no aparecerán en el diseñador de la aplicación a menos que los cambios se publiquen en el explorador de soluciones.  
  
## <a name="edit-or-remove-entity-assets"></a>Editar o quitar activos de la entidad  

### <a name="edit-entity-assets"></a>Editar activos de la entidad
  
1. Seleccione la flecha abajo ![Icono desplegable](../model-driven-apps/media/drop-down-icon.png "flecha abajo") para expandir la ventana de formularios, vistas, gráficos o paneles.  
  
2. Seleccione el formulario, vista, gráfico o panel que desea editar.  
  
3. En la barra de comandos, seleccione **Editar**.

   o

   Seleccione el botón diseñador del mapa de sitio ![botón Abrir diseñador del mapa de sitio](../model-driven-apps/media/dynamics365-open-designer.PNG "Botón Abrir diseñador del mapa del sitio") correspondiente en el formulario, la vista, el gráfico o el panel.  

### <a name="remove-entity-assets"></a>Quitar activos de la entidad  

1. Seleccione la flecha abajo ![Icono desplegable](../model-driven-apps/media/drop-down-icon.png "flecha abajo") para expandir la ventana de formularios, vistas, gráficos o paneles.  
  
2. Seleccione el formulario, vista, gráfico o panel que desea editar.

3. En la barra de comandos, seleccione **Quitar**. 

También puede seleccionar la ventana de los formularios, vistas, gráficos o paneles y, después, en la pestaña **componentes**, desactivar las casillas de los activos que quiere quitar del diseñador.  
  
## <a name="next-steps"></a>Pasos siguientes  
 [Crear un mapa del sitio para una aplicación](create-site-map-app.md) </br>  
 [Validar y publicar una aplicación](validate-app.md)
