---
title: Tutorial para agregar o editar componentes de aplicaciones controladas por modelos con PowerApps | Microsoft Docs
description: Uso del Diseñador de aplicaciones de PowerApps para agregar o editar componentes
keywords: ''
ms.date: 03/30/2018
ms.service: crm-online
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
ms.openlocfilehash: 87fec3bff3ad21a5c0474b67f001cca5c902d609
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39710946"
---
# <a name="tutorial-add-or-edit-model-driven-app-components-in-the-powerapps-app-designer"></a>Tutorial: Adición o edición de componentes de aplicaciones controladas por modelos en el Diseñador de aplicaciones de PowerApps

En este tutorial aprenderá a agregar y quitar componentes de una aplicación controlada por modelos. 

Una aplicación controlada por modelos consta de varios componentes. Puede agregar dos tipos de componentes a una aplicación: artefactos y recursos de entidad. En el contexto del Diseñador de aplicaciones, las entidades, el panel y los flujos de proceso de negocio son los artefactos de una aplicación. Los recursos de entidad constan de formularios, vistas, gráficos y paneles.  
  
El Diseñador de aplicaciones hace referencia a los metadatos existentes de la solución predeterminada. Puede usarlo para crear componentes como formularios, vistas, gráficos y paneles.  
  
## <a name="app-designer-layout"></a>Diseño del Diseñador de aplicaciones  
 El Diseñador de aplicaciones tiene dos áreas principales. En el lado izquierdo se encuentra el lienzo, donde se agregan los componentes de aplicaciones.  
  
![Lienzo del Diseñador de aplicaciones](../model-driven-apps/media/app-designer-canvas-pane.png)

 En el lado derecho están las pestañas que se usarán para seleccionar los componentes y establecer las propiedades de componentes.  
  
 ![Componentes del Diseñador de aplicaciones](../model-driven-apps/media/app-designer-canvas-components-tab.png "Componentes del Diseñador de aplicaciones")  
  
 En el lienzo, podrá ver las áreas del mapa del sitio, del flujo de proceso de negocio, del panel y de las entidades. Al seleccionar un flujo de proceso de negocio o un panel, o al configurar un mapa del sitio, el Diseñador de aplicaciones agrega automáticamente las entidades que se usan en estos componentes al lienzo. Cuando las entidades estén en su sitio, basta con seleccionar cada una de ellas y agregarles los recursos de entidad necesarios, como formularios, vistas y gráficos.
 
 También puede usar **Buscar en el lienzo** para buscar componentes en el lienzo. Al seleccionar **Buscar en el lienzo**, se abrirá una nueva pestaña de búsqueda a la derecha de las pestañas del panel situado más a la derecha.   
  
 ![Opción Buscar en el lienzo](media/app-designer-search-tab.png "Buscar en el lienzo")

## <a name="open-an-app"></a>Abrir una aplicación
1. Inicie sesión en [PowerApps](https://web.powerapps.com/). 

2. Seleccione **Basado en modelos** > **Aplicaciones** y, a continuación, elija una aplicación o seleccione **Crear una aplicación**. Para obtener información sobre cómo crear una aplicación, consulte [Tutorial: Create a model-driven app by using the app designer](create-edit-app.md#create-an-app) (Tutorial: Creación de una aplicación controlada por modelos con el Diseñador de aplicaciones).

## <a name="add-an-artifact-entity-dashboard-or-business-process-flow"></a>Adición de un artefacto (entidad, panel o flujo de proceso de negocio)  
 Cuando se agrega un flujo de proceso de negocio o un panel a una aplicación, se insertan automáticamente en la aplicación las entidades que usan. Cuando se agrega una entidad, se insertan automáticamente los iconos de sus recursos. Hay dos maneras de agregar artefactos al lienzo del diseñador: usando el botón **Agregar**  ![botón Agregar del diseñador](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "botón Agregar del diseñador") de la barra de comandos o mediante los iconos de la pestaña **Componentes**.  
  
 Estos son los pasos para agregar un panel a la aplicación. Siga los mismos pasos para agregar un flujo de proceso de negocio o una entidad.  
  
1.  En el lienzo del Diseñador de aplicaciones, seleccione el icono de **Paneles**.  
  
     En el lienzo del Diseñador de aplicaciones, el panel derecho muestra los paneles que están disponibles en la solución predeterminada.  
  
    > [!TIP]
    >  También puede realizar uno de los siguientes pasos:  
    >   
    > - Seleccione **Agregar** ![botón Agregar del diseñador](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "botón Agregar del diseñador") y, a continuación, elija **Paneles**.  
    > - En la pestaña **Componentes**, que se encuentra en **Artefactos**, seleccione **Paneles**.  
  
2.  En el cuadro de **búsqueda**, escriba algunas palabras clave del nombre del panel que busca.  
  
     La lista de paneles se filtrará para mostrar los resultados que coincidan con las palabras clave.  
  
3.  Si desea que los usuarios usen solamente los paneles seleccionados, active la casilla de verificación de los paneles que desea agregar. Puede seleccionar los paneles de los siguientes tipos:
    - **Paneles clásicos**: aparecen en la aplicación web y la aplicación de interfaz unificada.
    - **Paneles interactivos**: solo aparecen en la aplicación de interfaz unificada. Si ha seleccionado el tipo de cliente en la aplicación como aplicación web, no se mostrarán los **paneles interactivos**.

     Estos paneles se agregarán al icono de **Panel** del lienzo del Diseñador de aplicaciones. El icono de **Panel** también muestra un recuento del número de paneles agregados a la aplicación. Si no selecciona un panel, se mostrará **Todos** en lugar del recuento de paneles, y todos los paneles estarán disponibles para los usuarios cuando usen la aplicación.  
  
     Todas las entidades que usa el panel también se agregan al área **Vista de entidad**. Por ejemplo, si agrega el panel de Customer Service Manager, las entidades Caso, Derecho y Cola se agregan al área Vista de entidad. También se agregan los iconos de sus recursos en cada entidad. Puede usar estos iconos para agregar formularios, vistas y gráficos. Más información: [Adición o edición de componentes en el Diseñador de aplicaciones de PowerApps](add-edit-app-components.md#bkmk_AddEntityAssets)   
  
    ![Adición de una entidad al lienzo del Diseñador de aplicaciones](../model-driven-apps/media/add-entity-app-designer-canvas.png "Adición de una entidad al lienzo del Diseñador de aplicaciones")  
  
4.  Si el panel que quiere no se encuentra en la solución predeterminada, cree uno seleccionando **Crear nuevo** en la pestaña **Componentes** a la derecha del lienzo.  
  
     ![Vínculo Crear nuevo en la pestaña Componentes del Diseñador de aplicaciones](../model-driven-apps/media/app-designer-components-tab-create-new.png "Vínculo Crear nuevo en la pestaña Componentes del Diseñador de aplicaciones")  
  
     Se abrirá el Diseñador de paneles. Más información: [Creación y edición de paneles](create-edit-dashboards.md)  
  
    > [!NOTE]
    > - Cuando se agrega un flujo de proceso de negocio o una entidad, la opción **Crear nuevo** abre el diseñador correspondiente. Para obtener más información sobre la creación de flujos de proceso de negocio o entidades, consulte el artículo sobre cómo [crear un flujo de proceso de negocio](/flow/create-business-process-flow) y el de cómo [crear una entidad personalizada](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-create-entity).  
      
  
5.  Cuando haya terminado de agregar artefactos, en la barra de comandos, seleccione **Guardar**.  
  
<a name="bkmk_AddEntityAssets"></a>   
## <a name="add-entity-assets-forms-views-charts-or-dashboards"></a>Adición de recursos de entidad (formularios, vistas, gráficos o paneles)  
 Con los artefactos agregados, puede empezar a insertar recursos de entidad, como formularios, vistas, gráficos y paneles en la aplicación.
Además, si usa el cliente de interfaz unificada, también podrá agregar recursos de panel de entidad a la aplicación.  
  
 En esta sección se describen los pasos para agregar un formulario a la aplicación. Utilice los mismos pasos para agregar una vista o un gráfico a la aplicación.  
  
1.  En el lienzo del Diseñador de aplicaciones, seleccione el icono de **Formularios** de la entidad a la que quiera agregar un formulario.  
  
     En el lienzo del Diseñador de aplicaciones, se selecciona toda la fila de la entidad. En el lado derecho, verá todos los formularios existentes de la entidad seleccionada.  
  
    > [!NOTE]
    >  También puede realizar uno de los siguientes pasos:  
    >   
    > - Seleccione el botón **Agregar** ![Botón Agregar del diseñador](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "Botón Agregar del diseñador") y, a continuación, elija **Formularios**.  
    > - En la pestaña **Componentes**, en **Activos de la entidad**, seleccione **Formularios**.  
  
    > [!TIP]
    >  Se muestra un botón **Más opciones** (**...** ) en la lista **Seleccionar entidades** de la pestaña **Componentes** en todas las entidades seleccionadas para la aplicación. Para agregar todos los recursos de la entidad seleccionada, seleccione **Más opciones** (**...** ) y, a continuación, elija **Agregar todos los activos**.  
  
2.  Si desea que los usuarios de la aplicación solo usen los formularios seleccionados, active las casillas de los formularios que quiere agregar. Los formularios definen cómo los usuarios verán los datos de la aplicación e interactuarán con ellos. 
 
     El icono del formulario de la entidad seleccionada mostrará el número de formularios agregados.  
  
     ![Icono de formulario de la entidad Caso](../model-driven-apps/media/add-forms-entity.png "Icono de formulario de la entidad Caso")  
  
     Por ejemplo, si no selecciona ningún formulario de una entidad, todos los formularios de esa entidad se mostrarán a los usuarios finales mientras usan la aplicación. Este comportamiento es similar también en las vistas y los gráficos si no se selecciona ninguna vista o ningún gráfico. Esta acción ayuda a crear aplicaciones rápidamente cuando necesite trabajar con todos los componentes disponibles; no hace falta seleccionar cada componente durante el diseño de las aplicaciones.  

     Si no hay paneles o flujos de procesos de negocio seleccionados, todos los paneles y flujos de proceso de negocio estarán disponibles para los usuarios mientras usan la aplicación.
  
    > [!NOTE]
    > Para que la aplicación se ejecute, cada entidad que agregue debe tener al menos un formulario activo. Si ha seleccionado varios, se usará el primer formulario activo que aparece en la solución predeterminada cuando los usuarios ejecuten la aplicación.  
  
3.  Si desea agregar un nuevo formulario que no está disponible en la lista, seleccione **Crear nuevo**.  
  
     En la lista desplegable, elija el tipo de formulario que desea crear.  
  
    > [!NOTE]
    >  La lista desplegable solo está disponible cuando va a agregar formularios. No está disponible para las vistas ni los gráficos.  
  
     Se abrirá el Diseñador de formularios. Más información: [Creación y diseño de formularios](create-design-forms.md)  
  
     Cuando se agrega una vista o un gráfico, la opción **Crear nuevo** abre el diseñador correspondiente. Más información: [Información sobre las vistas](create-edit-views.md) y [Creación o edición de un gráfico del sistema](create-edit-system-chart.md)  
  
    > [!NOTE]
    >  Cuando vaya a agregar una vista, puede hacer referencia solo a las vistas públicas que aparecen en el nodo **Vistas** del Explorador de soluciones.  
  
4. Seleccione la flecha abajo ![Icono de flecha abajo](../model-driven-apps/media/drop-down-icon.png "Icono de flecha abajo") para expandir el icono y ver una lista de los formularios que se han agregado.  
  
     ![Icono del Formulario expandido del Diseñador de aplicaciones](../model-driven-apps/media/app-designer-expanded-form-tile.png "Icono del Formulario expandido del Diseñador de aplicaciones")  
  
5.  Repita estos pasos para agregar gráficos y vistas de entidad a la aplicación.  
  
6.  Seleccione **Guardar**.  
  
## <a name="edit-or-remove-artifacts"></a>Edición o eliminación de artefactos  
  
- Para editar un panel o un flujo de proceso de negocio, seleccione la flecha abajo ![Icono de flecha abajo](../model-driven-apps/media/drop-down-icon.png "Icono de flecha abajo") para expandir el icono y, a continuación, elija el botón del Diseñador del mapa del sitio ![Botón para abrir el Diseñador del mapa del sitio botón](../model-driven-apps/media/dynamics365-open-designer.PNG "Botón para abrir el Diseñador del mapa del sitio botón") correspondiente al panel o al flujo del proceso de negocio que desea editar.  
  
     Se abrirá el diseñador del artefacto seleccionado.  
  
- Para quitar un panel o un flujo de proceso de negocio, seleccione la flecha abajo ![Icono de flecha abajo](../model-driven-apps/media/drop-down-icon.png "Icono de flecha abajo") para expandir el icono y, a continuación, elija el flujo de negocio o el panel que desea quitar. En la barra de comandos, seleccione **Quitar**.  

    Otra manera de quitar un flujo de proceso de negocio o un panel es desactivando la casilla correspondiente en la pestaña **Componentes**.
  
- Para editar o quitar una entidad, seleccione el icono de entidad y, a continuación, en la barra de comandos, elija **Editar** o **Quitar**. Al editar una entidad, se abre el Explorador de soluciones, donde puede realizar cambios en la entidad.  
  
     Otra manera de quitar un componente consiste en seleccionar el panel, el flujo de proceso de negocio o el icono de entidad. En la pestaña **Componentes**, desactive las casillas de verificación de los artefactos que desea quitar del diseñador.  
  
    > [!NOTE]
    >  Cuando realice cambios en una entidad, &mdash;como cambiar el nombre para mostrar o la descripción&mdash;, los cambios no se reflejan en el Diseñador de aplicaciones, a menos que se publiquen los cambios en el Explorador de soluciones.  
  
## <a name="edit-or-remove-entity-assets"></a>Edición o eliminación de recursos de entidad  

### <a name="edit-entity-assets"></a>Edición de recursos de entidad
  
1. Seleccione la flecha abajo ![Icono de flecha abajo](../model-driven-apps/media/drop-down-icon.png "Icono de flecha abajo") para expandir el icono de formularios, vistas, gráficos o paneles.  
  
2. Seleccione el formulario, la vista, el gráfico o el panel que desea editar.  
  
3. En la barra de comandos, seleccione **Editar**.

   O bien

   Seleccione el botón del Diseñador del mapa del sitio ![Botón para abrir el Diseñador del mapa del sitio](../model-driven-apps/media/dynamics365-open-designer.PNG "Botón para abrir el Diseñador del mapa del sitio") correspondiente al formulario, la vista, el gráfico o el panel.  

### <a name="remove-entity-assets"></a>Eliminación de recursos de entidad  

1. Seleccione la flecha abajo ![Icono de flecha abajo](../model-driven-apps/media/drop-down-icon.png "Icono de flecha abajo") para expandir el icono de formularios, vistas, gráficos o paneles.  
  
2. Seleccione el formulario, la vista, el gráfico o el panel que desea editar.

3. En la barra de comandos, seleccione **Quitar**. 

También puede seleccionar los formularios, las vistas, los gráficos o el icono de paneles y, a continuación, en la pestaña **Componentes**, desactive las casillas de los recursos que desea quitar del diseñador.  
  
## <a name="next-steps"></a>Pasos siguientes  
 [Crear un mapa del sitio para una aplicación](create-site-map-app.md) </br>  
 [Validar y publicar una aplicación](validate-app.md)
