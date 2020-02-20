---
title: Seguimiento del progreso con paneles y gráficos en aplicaciones basadas en modelos | Microsoft Docs
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
ms.openlocfilehash: 70c6f97c2617c9d6084c3aa8a0861793a0c059d5
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74726168"
---
# <a name="track-your-progress-with-dashboards-and-charts"></a>Realizar un seguimiento del progreso con gráficos y paneles

Los paneles toman una colección de datos de la aplicación y proporcionan información para mostrar indicadores clave de rendimiento (KPI) y otros datos importantes en gráficos interactivos fáciles de leer. Los paneles están disponibles para todo tipo de registros.

> [!div class="mx-imgBorder"]
> ![Panel](media/Dashboard.png "Panel") 

-  Para ver un diseño de panel diferente, seleccione la flecha abajo situada junto al nombre del panel y, después, seleccione el diseño que quiera.
-  Para elegir un panel predeterminado, abra el panel que quiera y, después, seleccione **Establecer como predeterminado** en la parte superior de la pantalla.

   > [!div class="mx-imgBorder"]
   > ![Adición o cambio de un panel](media/add_dashboard.png "Adición o cambio de un panel") 

## <a name="create-a-new-dashboard"></a>Creación de un nuevo panel

1. Para crear un panel, seleccione **Crear un panel de Dynamics 365**. 

   > [!div class="mx-imgBorder"]
   > ![Adición de un panel nuevo](media/new_dashboard.png "Adición de un panel nuevo")
   
2. Elija un diseño de panel y seleccione **Crear**.  

   > [!div class="mx-imgBorder"]
   > ![Creación de un panel](media/create_dashboard.png "Crear un panel")
 
3. Escriba un nombre para el panel. 
4. Agregue lo que quiera a cada área del panel. Vamos a agregar un gráfico, por ejemplo. 

   > [!div class="mx-imgBorder"]
   > ![Adición de un gráfico](media/add_chart.png "Agregar un gráfico")
 
 5. Seleccione el **Tipo de registro** del gráfico.
 6. Seleccione una **Vista** que vayan a mostrar los datos del gráfico.
 7. Elija el gráfico y, después, seleccione **Agregar**.
 8. Siga agregando componentes al panel y, cuando haya terminado, seleccione **Guardar**. 
 
El panel que ha creado aparecerá en el menú desplegable de los paneles disponibles.

## <a name="use-charts"></a>Uso de gráficos 

Los gráficos proporcionan una vista rápida de cómo se lleva un seguimiento de los objetivos. También son interactivas, de modo que se puede hacer clic o pulsar en un área de un gráfico para obtener más información.

-   Mantenga el puntero sobre el gráfico para ver una información emergente que dé información rápida sobre esa área del gráfico.
-   Haga clic en el área de un gráfico para ver una vista de cuadrícula con más detalles sobre los datos contenidos en el gráfico.
-   Para expandir un gráfico, seleccione el botón **Expandir gráfico** ![Vista Expandir gráfico](media/expandviewbutton.png "Vista Expandir gráfico").
-   Para ver registros del gráfico o actualizar el gráfico, seleccione ![Más comandos](media/MoreButton.png "Más comandos") y, después, elija una acción: **Actualizar** o **Ver registros**.
     
     > [!div class="mx-imgBorder"]
     > ![Vista de gráficos en Power Apps](media/ViewOfCharts.png "Vista de gráficos en Power Apps")  
       

**Cambio de la vista de gráfico**
 
Cuando se cambia de vista de gráfico, se muestra un desglose de los datos distinto, como, por ejemplo, las oportunidades abiertas durante un período de tiempo concreto. Para cambiar una vista de gráfico, hay que seleccionar el selector Vista de la página Cuadrícula.

Por ejemplo, seleccione "Todas las oportunidades" y, después, seleccione una vista diferente, y se actualizarán tanto el gráfico como la cuadrícula.

> [!div class="mx-imgBorder"]
> ![Cambiar una vista de gráfico en Power Apps](media/ChangeChartView.png "Cambio de una vista de gráfico en Power Apps")

## <a name="known-issues"></a>Problemas conocidos  
En el diseñador de gráficos no se puede agregar una opción Ordenar por en algunos campos calculados, y se producirá un error.  Los campos calculados en los que esto sucede usan otros campos calculados, un campo de entidad relacionado o un campo local en la entidad.



