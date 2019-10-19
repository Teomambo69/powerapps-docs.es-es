---
title: Seguimiento del progreso con paneles y gráficos en aplicaciones controladas por modelos | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/4/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
- D365CE
ms.openlocfilehash: e9d046c49a2a91aaf5c65094d446ae09f41572f9
ms.sourcegitcommit: 4c35aedde46380d5438687ae6f61a3b0cc7e7e2f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/05/2019
ms.locfileid: "71969084"
---
# <a name="track-your-progress-with-dashboards-and-charts"></a>Realizar un seguimiento del progreso con gráficos y paneles

Los paneles toman una colección de datos de la aplicación y proporcionan información para mostrar indicadores clave de rendimiento (KPI) y otros datos importantes en gráficos y gráficos interactivos fáciles de leer. Los paneles están disponibles para todos los tipos de registros.

> [!div class="mx-imgBorder"]
> ![](media/Dashboard.png "Panel") del panel 

-  Para ver un diseño de panel diferente, seleccione la flecha hacia abajo situada junto al nombre del panel y, a continuación, seleccione el diseño que desee.
-  Para elegir un panel predeterminado, abra el panel que desee y, a continuación, seleccione **establecer como predeterminado** en la parte superior de la pantalla.

   > [!div class="mx-imgBorder"]
   > ![Agregar o cambiar]el panel(media/add_dashboard.png "Agregar o cambiar") el panel 

## <a name="create-a-new-dashboard"></a>Crear un nuevo panel

1. Para crear un nuevo panel, seleccione **crear un panel de Dynamics 365**. 

   > [!div class="mx-imgBorder"]
   > ![Agregar un nuevo panel](media/new_dashboard.png "Agregar un nuevo panel")
   
2. Elija un diseño de panel y seleccione **crear**.  

   > [!div class="mx-imgBorder"]
   > ![Creación de un panel](media/create_dashboard.png "creación de un panel")
 
3. Escriba un nombre para el panel. 
4. Agregue lo que desee a cada área del panel. Por ejemplo, vamos a agregar un gráfico. 

   > [!div class="mx-imgBorder"]
   > ![Agregar un]gráfico(media/add_chart.png "Agregar un gráfico")
 
 5. Seleccione el **tipo de registro** para el gráfico.
 6. Seleccione una **vista** en la que se mostrarán los datos del gráfico.
 7. Elija el gráfico y, a continuación, seleccione **Agregar**.
 8. Siga agregando componentes al panel y, cuando haya terminado, seleccione **Guardar**. 
 
El panel que ha creado aparecerá en el menú desplegable de los paneles disponibles.

## <a name="use-charts"></a>Usar gráficos 

Los gráficos proporcionan una vista rápida de cómo se realiza el seguimiento de los objetivos. También son interactivas, por lo que puede hacer clic o pulsar en un área de un gráfico para obtener más información.

-   Mantenga el mouse sobre el gráfico para ver una información sobre herramientas que proporciona información rápida sobre esa área del gráfico.
-   Haga clic en el área de un gráfico para ver una vista de cuadrícula con más detalles sobre los datos del gráfico.
-   Para expandir un gráfico, haga clic en el botón **expandir gráfico expandir**![vista]del gráfico expandir vista(media/expandviewbutton.png "del gráfico.")
-   Para ver los registros del gráfico o actualizar el gráfico, seleccione ![más comandos](media/MoreButton.png "más") comandos y, a continuación, elija una acción: **Actualizar** o **Ver registros**.
     
     > [!div class="mx-imgBorder"]
     > ![Vista de gráficos en]la(media/ViewOfCharts.png "vista de powerapps de gráficos en powerapps")  
       

**Cambiar la vista del gráfico**
 
Al cambiar la vista de gráfico, se muestra un desglose diferente de los datos, como oportunidades abiertas en un período de tiempo concreto. Puede cambiar una vista de gráfico seleccionando el selector de vistas en la página de cuadrícula.

Por ejemplo, seleccione "todas las oportunidades" y, a continuación, seleccione una vista diferente, y se actualizarán tanto el gráfico como la cuadrícula.

> [!div class="mx-imgBorder"]
> ![Cambiar una vista de gráfico en powerapps](media/ChangeChartView.png "cambiar una vista de gráfico en powerapps")

## <a name="known-issues"></a>Problemas conocidos  
En el diseñador de gráficos, no se admite la adición de un order by en determinados campos calculados y se producirá un error.  Los campos calculados que lo hacen es usar otros campos calculados, un campo de entidad relacionado o un campo local en la entidad.



