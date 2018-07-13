---
title: Creación de un informe de Power BI para analizar proyectos | Microsoft Docs
description: En esta tarea, vamos a crear un informe de Power BI basado en dos listas de SharePoint.
documentationcenter: na
author: mgblythe
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 01/10/2018
ms.author: mblythe
ms.openlocfilehash: 7ab372f8e8a03da35752614905017e24672480b3
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37897717"
---
# <a name="create-a-power-bi-report-to-analyze-projects"></a>Creación de un informe de Power BI para analizar proyectos
> [!NOTE]
> Este artículo forma parte de una serie de tutoriales acerca del uso de PowerApps, Microsoft Flow y Power BI con SharePoint Online. Asegúrese de leer la [introducción a la serie](sharepoint-scenario-intro.md) para hacerse una idea general, así como para obtener descargas relacionadas.

En esta tarea, vamos a crear un informe de Power BI basado en las dos listas de SharePoint. Trasladaremos los datos de las listas a Power BI Desktop y los limpiaremos un poco, realizaremos algunas operaciones básicas de modelado de datos y crearemos un conjunto de objetos visuales que nos proporcionarán cierta información acerca de los datos.

> [!TIP]
> El [paquete de descarga](https://aka.ms/o4ia0f) de este escenario incluye una versión terminada de este informe: project-analysis.pbix.

## <a name="quick-review-of-power-bi-desktop"></a>Repaso rápido de Power BI Desktop
Antes de profundizar en la creación de informes, revisemos Power BI Desktop. Es una herramienta eficaz, con gran cantidad de características, por lo que nos centraremos en proporcionar información general de las áreas que se van a utilizar en esta tarea. En Power BI Desktop hay tres áreas de trabajo o *vistas* principales: vista **Informe**, vista **Datos** y vista **Relaciones**. Power BI Desktop también incluye el **Editor de consultas**, que se abre en una ventana independiente.

La siguiente pantalla muestra los iconos de las tres vistas a la izquierda de Power BI Desktop: **Informe**, **Datos** y **Relaciones**, de arriba a abajo. La barra amarilla de la izquierda indica la vista activa; en este caso, se muestra la vista **Informe**. Para cambiar de vista, seleccione cualquiera de los tres iconos.

![Vistas de Power BI Desktop](./media/sharepoint-scenario-build-report/05-00-00-tabs.png)

La vista **Informe** tiene cinco áreas principales:

1. La cinta de opciones, que muestra tareas comunes asociadas a informes y visualizaciones.
2. La vista **Informe**, o lienzo, donde las visualizaciones se crean y se organizan.
3. El área de la pestaña **Páginas** de la parte inferior, que permite seleccionar o agregar una página del informe.
4. El panel **Visualizaciones**, donde se cambian las visualizaciones, se personalizan los colores o ejes, se aplican filtros, se arrastran los campos, etc.
5. El panel **Campos**, en el que los elementos de consulta y los filtros se pueden arrastrar a la vista **Informe**, o bien al área **Filtros** del panel **Visualizaciones**.

![Paneles, vistas y pestañas de Power BI Desktop](./media/sharepoint-scenario-build-report/05-00-01-report.png)

La vista **Datos** tiene tres áreas principales:

1. La cinta de opciones, que tiene la pestaña **Modelado** seleccionada a continuación. En esta pestaña, se crean tablas y columnas calculadas, y se realizan otros cambios en el modelo de datos.
2. El panel central, que muestra los datos de la tabla seleccionada.
3. El panel **Campos**, donde se controla cómo se muestran los campos en los informes.

![Vista de datos de Power BI Desktop](./media/sharepoint-scenario-build-report/05-00-02-data.png)

En esta tarea no se usa la vista **Relaciones**, pero se puede consultar más adelante, después de que trasladar los datos de lista a Power BI Desktop.

En el **Editor de consultas**, se crean consultas y se transforman datos y, posteriormente, el modelo de datos refinados se carga en Power BI Desktop. El **Editor de consultas** tiene cuatro áreas principales:

1. La cinta de opciones, que tiene muchas opciones para dar forma y transformar los datos que se proporcionan.
2. El panel izquierdo, en el que se enumeran las consultas que se pueden seleccionar, visualizar y dar forma.
3. El panel central, en el que se muestran los datos de la consulta seleccionada y están disponibles para darles forma.
4. La ventana **Configuración de la consulta**, que enumera las propiedades de la consulta y los pasos de transformación de datos que se han aplicado.

![Editor de consultas de Power BI Desktop](./media/sharepoint-scenario-build-report/05-00-03-query.png)

## <a name="step-1-get-data-into-power-bi-desktop"></a>Paso 1: Obtención de datos en Power BI Desktop
En este paso, en primer lugar se conectará a las dos listas. Luego limpiará los datos, para lo que debe eliminar las columnas que no sean necesarias para el análisis de datos. También cambiará los tipos de datos de algunas de las columnas restantes para que los cálculos se realicen correctamente. Para más información acerca de cómo obtener y limpiar datos en Power BI Desktop, consulte la sección [Obtención de datos](https://powerbi.microsoft.com/guided-learning/powerbi-learning-1-1-overview-of-power-bi-desktop) del curso de aprendizaje guiado.

### <a name="connect-to-sharepoint-lists"></a>Conexión a listas de SharePoint
1. En Power BI Desktop, en la pestaña **Inicio**, haga clic o pulse en **Obtener datos** y luego en **Más...**
   
    ![Obtener datos](./media/sharepoint-scenario-build-report/05-01-01-get-data.png)
2. En el cuadro de diálogo **Obtener datos**, haga clic o pulse en **Lista de SharePoint Online** y, luego, en **Conectar**.
   
    ![Conectarse a lista de SharePoint](./media/sharepoint-scenario-build-report/05-01-02-sharepoint-list.png)
3. Escriba la dirección URL del sitio de SharePoint y, después, haga clic en **Aceptar** o pulse en él.
   
    ![Dirección URL de lista de SharePoint](./media/sharepoint-scenario-build-report/05-01-03-sharepoint-url.png)
4. Si aparece el siguiente cuadro de diálogo, asegúrese de que ha iniciado sesión con las credenciales correctas y haga clic o pulse en **Conectar**.
   
    ![Credenciales de lista de SharePoint](./media/sharepoint-scenario-build-report/05-01-04-credentials.png)
5. Seleccione **Project Details** y **Project Requests**, y haga clic o pulse en **Editar**.
   
    ![Seleccionar listas de SharePoint](./media/sharepoint-scenario-build-report/05-01-05-list-navigator.png)
   
    Las listas se muestran como tablas en el Editor de consultas.
   
    ![Tablas en el Editor de consultas](./media/sharepoint-scenario-build-report/05-01-06-query-editor.png)

### <a name="remove-unnecessary-columns-from-the-tables"></a>Eliminación de columnas innecesarias de las tablas
1. En el panel de navegación izquierdo, haga clic o pulse en **Project Details**.
2. En el panel central, seleccione la columna **FileSystemObjectType** y, después, haga clic o pulse **Quitar columnas**.
   
    ![Quitar columnas](./media/sharepoint-scenario-build-report/05-01-07-remove-column.png)
3. Quitar las dos columnas después de la columna **Id**: **ServerRedirectedEmbedURL** y **ContentTypeId**. 
   > [!TIP]
   > Utilice la tecla Máyus para seleccionar ambas columnas y, después, haga clic o pulse **Quitar columnas**.
4. Quite todas las columnas a la derecha de la columna **PMAssigned** (un total de 22 columnas). La tabla debe coincidir con la de la siguiente imagen:
   
    ![Tabla Project Details en el Editor de consultas](./media/sharepoint-scenario-build-report/05-01-08-table-details.png)
5. Repita el proceso que acaba de realizar, ahora para **Project Requests**: quite **FileSystemObjectType**, **ServerRedirectedEmbedURL**,  **ContentTypeId** y todas las columnas a la derecha de la columna **Approved** (un total de 22). La tabla debe coincidir con la de la siguiente imagen:
   
    ![ Tabla Project Requests en el Editor de consultas](./media/sharepoint-scenario-build-report/05-01-09-table-requests.png)

### <a name="change-the-data-type-on-project-details-columns"></a>Cambiar el tipo de datos en las columnas de Project Details
1. Seleccione la columna **ProjectedDays**, haga clic o pulse **Tipo de datos: cualquiera** y , luego, **Número entero**.
   
    ![Cambiar el tipo de datos a número entero](./media/sharepoint-scenario-build-report/05-01-10-datatype-number.png)
2. Repita el paso anterior en la columna **ActualDays**.
3. Seleccione la columna **ApprovedDate**, haga clic o pulse **Tipo de datos: cualquiera** y, luego, **Fecha**.
   
    ![ Cambiar el tipo de datos a fecha](./media/sharepoint-scenario-build-report/05-01-11-datatype-date.png)

4. Repita el paso anterior en las columnas **ProjectedStartDate** y **ProjectedEndDate**.

### <a name="change-the-data-type-on-project-requests-columns"></a>Cambio del tipo de datos en las columnas de Project Requests

1. Seleccione la columna **EstimatedDays**, haga clic o pulse **Tipo de datos: cualquiera** y , luego, **Número entero**.

2. Seleccione la columna **RequestDate**, haga clic o pulse **Tipo de datos: cualquiera** y, luego, **Fecha**.

### <a name="apply-and-save-changes"></a>Aplicación y guardado de cambios

1. En la pestaña **Inicio**, haga clic en **Cerrar y aplicar** para cerrar el Editor de consultas y vuelva a la ventana principal de Power BI Desktop.
   
    ![Cerrar y aplicar cambios](./media/sharepoint-scenario-build-report/05-01-12-close-apply.png)

2. Haga clic o pulse en **Archivo** y , luego, en **Guardar** y guarde el proyecto con el nombre project-analysis.pbix.

## <a name="step-2-improve-the-data-model"></a>Paso 2: Mejora del modelo de datos
Ahora que los datos de las listas de SharePoint se encuentran en Power BI Desktop, pasaremos al modelado de datos. El modelado de datos puede ser un proceso lento, pero le mostraremos sucintamente varias cosas interesantes que puede hacer para sacar el máximo partido a los datos de las listas en Power BI Desktop:

* Cambiar las relaciones entre dos tablas cualesquiera
* Agregar una tabla de fechas para poder realizar cálculos basados en los días laborables
* Agregar columnas calculadas para calcular los intervalos de tiempo entre los hitos del proyecto
* Agregar medidas para calcular la varianza en los días previstos frentes a los días reales de un proyecto

Una vez completados estos pasos, se pueden crear visualizaciones que saquen provecho de las mejoras en nuestro modelo. Para más información acerca del modelado de datos en Power BI Desktop, consulte la sección [Modelado](https://powerbi.microsoft.com/guided-learning/powerbi-learning-2-1-intro-modeling-data) del curso de aprendizaje guiado.

### <a name="change-table-relationships"></a>Cambiar las relaciones entre tablas
Cuando Power BI Desktop introdujo las listas, creó una relación entre ellas basada en la columna **Id** de ambas tablas. En realidad, la relación se establecería entre la columna **Id** de la tabla **Project Requests** y la columna **RequestId** de la tabla **Project Details**. Vamos a solucionar ese problema:

1. Haga clic o pulse el icono de la **vista Datos**.
   
    ![Vista Datos](./media/sharepoint-scenario-build-report/05-02-01-data-view.png)

2. En la pestaña **Modelado**, haga clic o pulse **Administrar relaciones**. Permaneceremos en esta pestaña de la vista **Datos** para todos los pasos del modelado de datos.
   
    ![Administrar relaciones](./media/sharepoint-scenario-build-report/05-02-02-manage-relationships.png)

3. Asegúrese de que está seleccionada la relación existente, haga clic o pulse **Eliminar** y, después, otra vez **Eliminar** para confirmar.
   
    ![Eliminar relación](./media/sharepoint-scenario-build-report/05-02-03-delete-relationship.png)

4. Haga clic en **Nuevo** para crear otra relación.

5. En el cuadro de dialogo **Crear relación**:
   
   1. Para la primera tabla, seleccione **Project Requests**y la columna **Id**.
   
   2. Para la segunda tabla, seleccione **Project Details**y la columna **RequestId**.
   
   3. La pantalla debe ser como la de siguiente imagen. Cuando esté listo, haga clic o pulse en **Aceptar** y, después, en **Cerrar**.
      
       ![Crear relación](./media/sharepoint-scenario-build-report/05-02-04-create-relationship.png)

### <a name="add-a-date-table-to-make-date-based-calculations-easier"></a>Adición de una tabla de fechas para facilitar los cálculos de fecha
1. Haga clic o pulse **Nueva tabla**.
   
    ![Nueva tabla](./media/sharepoint-scenario-build-report/05-02-05-modeling-table.png)
2. Escriba esta fórmula en la barra de fórmulas: **Dates = CALENDARAUTO()**.
   
    ![Barra de fórmulas con Dates = CALENDARAUTO()](./media/sharepoint-scenario-build-report/05-02-06-formula-bar.png)
   
    Esta fórmula crea una tabla denominada **Dates** con una sola columna de fecha. La tabla cubre todas las fechas de la otra tabla y se actualiza automáticamente si se agregan fechas adicionales (es decir, si se actualizan los datos).
   
    Tanto esta fórmula como las restantes de esta sección usan expresiones de análisis de datos (DAX), un lenguaje de fórmulas de Power BI y otras tecnologías. Para más información, consulte [Aspectos básicos de DAX en Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-quickstart-learn-dax-basics).
3. Presione Entrar para crear la tabla **Dates**.
   
    ![Tabla Dates](./media/sharepoint-scenario-build-report/05-02-07-date-table.png)

### <a name="add-a-calculated-column-to-the-dates-table"></a>Adición de una calculada a la tabla Dates
1. Aún en la tabla de fechas, haga clic o pulse en **Nueva columna**.
   
    ![Nueva columna](./media/sharepoint-scenario-build-report/05-02-00-modeling-column.png)
2. Escriba esta fórmula en la barra de fórmulas: **IsWeekDay = SWITCH(WEEKDAY(Dates[Date]), 1,0,7,0,1)**.
   
    Esta fórmula determina si una fecha de la columna **Date** es un día laborable. Si la fecha es un día laborable, la columna **IsWeekDay** obtiene el valor 1; de lo contrario, obtiene el valor 0.
3. Presione Entrar para agregar la columna **IsWeekDay** a la tabla **Dates**.
   
    ![Agregar columna IsWeekDay](./media/sharepoint-scenario-build-report/05-02-08-column-isweekday.png)

### <a name="add-a-calculated-column-to-the-project-details-table"></a>Adición de una columna calculada a la tabla Project Details
1. En el panel derecho, haga clic o pulse en la tabla **Project Details** y , después, en **Nueva columna**.
   
    ![Nueva columna](./media/sharepoint-scenario-build-report/05-02-00-modeling-column.png)
2. Escriba esta fórmula en la barra de fórmulas:
   
    ```
    ApprovedStartDiff = CALCULATE(SUM(Dates[IsWeekday]),
   
       DATESBETWEEN(Dates[Date],
   
          'Project Details'[ApprovedDate],
   
          'Project Details'[ProjectedStartDate]
   
      )
   
    )
    ```
   
    Esta fórmula calcula la diferencia, en días, entre el momento en que se aprobó un proyecto y cuando está previsto que se inicie. Usa la columna **IsWeekday** de la tabla **Dates**, por lo solo cuentan los días laborables.
3. Presione Entrar para agregar la columna **ApprovedStartDiff** a la tabla **Project Details**.
   
    ![Agregar columna ApprovedStartDiff](./media/sharepoint-scenario-build-report/05-02-09-column-approvedstartdiff.png)

### <a name="add-a-calculated-column-to-the-project-requests-table"></a>Adición de una columna calculada a la tabla Project Requests
1. En el panel derecho, haga clic o pulse en la tabla **Project Requests** y , después, en **Nueva columna**.
   
    ![Nueva columna](./media/sharepoint-scenario-build-report/05-02-00-modeling-column.png)
2. Escriba esta fórmula en la barra de fórmulas:
   
    ```
    RequestDateAge = CALCULATE(SUM(Dates[IsWeekday]),
   
       DATESBETWEEN(Dates[Date],
   
          'Project Requests'[RequestDate],
   
          NOW()
   
       )
   
    )
    ```
   
    Esta fórmula calcula la diferencia, en días, entre la fecha en que se solicitó un proyecto y la fecha de hoy [AHORA()]. Una vez más, la fórmula solo cuenta los días laborables. Esta columna se utiliza para buscar el proyecto que más tiempo lleva pendiente.
3. Presione Entrar para agregar la columna **RequestDateAge** a la tabla **Project Requests**.
   
    ![Agregar columna RequestDateAge](./media/sharepoint-scenario-build-report/05-02-10-column-requestdateage.png)

### <a name="add-a-measure-to-the-project-details-table"></a>Adición de una medida a la tabla Project Details
1. En el panel derecho, haga clic o pulse en la tabla **Project Details** y , después, en **Nueva medida**.
   
    ![Nueva medida](./media/sharepoint-scenario-build-report/05-02-00-modeling-measure.png)
2. Escriba esta fórmula en la barra de fórmulas:
   
    ```
    VarProjectedActual = DIVIDE(
   
        SUM('Project Details'[ActualDays]) - SUM('Project Details'[ProjectedDays]),
   
        SUM('Project Details'[ProjectedDays])
   
    )
    ```
   
    Esta fórmula calcula la varianza entre días reales y previstos de un proyecto. Se agrega como una medida, en lugar de como una columna calculada, por lo que devuelve los resultados correctos, independientemente de cómo se filtren o se agreguen los datos en un informe.
3. Presione Entrar para agregar la medida **VarProjectedActual** a la tabla **Project Details**.
   
    ![Agregar medida VarProjectedActual](./media/sharepoint-scenario-build-report/05-02-11-measure-varprojectedactual.png)

### <a name="add-a-measure-to-the-project-requests-table"></a>Adición de una medida a la tabla Project Requests
1. En el panel derecho, haga clic o pulse en la tabla **Project Requests** y , después, en **Nueva medida**.
   
    ![Nueva medida](./media/sharepoint-scenario-build-report/05-02-00-modeling-measure.png)
2. Escriba esta fórmula en la barra de fórmulas:
   
    ```
    MaxDaysPending = MAXX(
   
        FILTER('Project Requests', 'Project Requests'[Approved]="Pending"),
   
        'Project Requests'[RequestDateAge]
   
    )
    ```
   
    Esta fórmula busca el proyecto más tiempo lleva pendiente, en función de la columna calculada que se ha definido antes.
3. Presione Entrar para agregar la medida **MaxDaysPending** a la tabla **Project Requests**.
   
    ![Agregar medida MaxDaysPending](./media/sharepoint-scenario-build-report/05-02-12-measure-maxdayspending.png)

## <a name="step-3-create-report-visualizations"></a>Paso 3: Creación de visualizaciones de informes
Ahora estamos en el paso en el que mucha gente piensa cuando piensan en el análisis de datos: la creación de visualizaciones para poder buscar patrones en los datos. En este paso, crearemos cuatro visualizaciones:

* Un gráfico de columnas que muestra los días previstos frente a días reales de los proyectos
* Un gráfico de columnas que muestra la varianza de cada proyecto
* Una tarjeta que muestra el proyecto que lleva más tiempo pendiente
* Una tabla que muestra el tiempo transcurrido entre la aprobación del proyecto y la fecha de inicio previsto

Una vez que hemos creado estas visualizaciones de informes en Power BI Desktop, publicaremos los datos e informes para el servicio Power BI, con el fin de que podamos crear y compartir paneles. Para más información acerca de la creación de informes en Power BI Desktop, consulte la sección [Visualizaciones](https://powerbi.microsoft.com/guided-learning/powerbi-learning-3-1-intro-visualizations) del curso de aprendizaje guiado.

### <a name="create-a-bar-chart-to-show-projected-versus-actual"></a>Creación de un gráfico de barras que muestre las fechas previstas frente a las reales
1. Haga clic o pulse el icono de la **vista Informe**. Permaneceremos en esta vista durante el resto de nuestro tiempo en Power BI Desktop.
   
    ![Vista Informe](./media/sharepoint-scenario-build-report/05-03-01-report-view.png)
2. En el panel **Visualizaciones** panel de la derecha, haga clic o pulse **Gráfico de columnas agrupadas**.
   
    ![Visualizaciones: gráfico de columnas agrupadas](./media/sharepoint-scenario-build-report/05-03-00-visuals-column.png)
3. Arrastre **PMAssigned** y **Title** de **Project Details**, en el panel **Campos**, a **Eje**, en el panel **Visualizaciones**.
   
    ![Eje en el panel Visualizaciones](./media/sharepoint-scenario-build-report/05-03-00-axis.png)
4. Arrastre **ActualDays** y **ProjectedDays** de **Project Details**, en el panel **Campos**, a **Valores**, en el panel **Visualizaciones**.
   
    ![Valores en el panel Visualizaciones](./media/sharepoint-scenario-build-report/05-03-03-value-projected.png)
5. Ahora la visualización debería parecerse a la siguiente imagen.
   
    ![ProjectedDays y ActualDays por PMAssigned](./media/sharepoint-scenario-build-report/05-03-04-chart-projected.png)
6. Arrastre **Status** desde el panel **Campos** de **Project Details** hasta el área **Filtros** del panel **Visualizaciones** y seleccione la casilla **Completado**.
   
   ![Filtrar por columna Status](./media/sharepoint-scenario-build-report/05-03-05-filters-projected.png)
   
   El gráfico ahora está filtrado y muestra solo los proyectos completos, lo que tiene sentido porque se comparan días previstos con días reales.
7. Haga clic en las flechas de la esquina superior izquierda del gráfico para subir y bajar por la jerarquía de los jefes de proyecto y proyectos. En la siguiente imagen, verá cómo se exploran proyectos en profundidad.
   
   ![Explorar en profundidad un gráfico de columnas](./media/sharepoint-scenario-build-report/05-03-06-chart-projected-drill.png)

### <a name="create-a-bar-chart-to-show-variance-from-projected"></a>Creación de un gráfico de barras que muestre la varianza a partir de las fechas previstas
1. Haga clic o pulse en el lienzo fuera de la visualización que acaba de crear.
2. En el panel **Visualizaciones** panel de la derecha, haga clic o pulse **Gráfico de columnas agrupadas**.
   
    ![Visualizaciones: gráfico de columnas agrupadas](./media/sharepoint-scenario-build-report/05-03-00-visuals-column.png)
3. Arrastre **PMAssigned** y **Title** de **Project Details**, en el panel **Campos**, a **Eje**, en el panel **Visualizaciones**.
   
    ![Eje en el panel Visualizaciones](./media/sharepoint-scenario-build-report/05-03-00-axis.png)
4. Arrastre **VarProjectedActual** de **Project Details**, en el panel **Campos**, a **Valores**, en el panel **Visualizaciones**.
   
    ![Valores en el panel Visualizaciones](./media/sharepoint-scenario-build-report/05-03-07a-value-variance.png)
5. Arrastre **Status** desde el panel **Campos** de **Project Details** hasta el área **Filtros** del panel **Visualizaciones** y seleccione la casilla **Completado**.
   
    ![Filtrar por columna Status](./media/sharepoint-scenario-build-report/05-03-07b-filters-variance.png)
   
    Ahora la visualización debería parecerse a la siguiente imagen.
   
    ![VarProjectedActual por PMAssigned](./media/sharepoint-scenario-build-report/05-03-08-chart-variance.png)
   
    En este gráfico se puede ver la variabilidad que hay para los proyectos que ejecutó Irvin Sayers frente a los que ejecutó Joni Sherman. Explore en profundidad para ver la variabilidad por proyecto y si el número de días previstos era superior o inferior al de días reales.
   
    ![VarProjectedActual por Title](./media/sharepoint-scenario-build-report/05-03-09-chart-variance-drill.png)
6. Para poder crear más visualizaciones, mueva las que ha creado y cámbielas de tamaño para que quepan en paralelo.
   
    ![Ajustar gráficos en paralelo](./media/sharepoint-scenario-build-report/05-03-10-two-charts.png)

### <a name="create-a-card-that-shows-the-longest-pending-project"></a>Creación de una tarjeta que muestre el proyecto que lleva más tiempo pendiente
1. Haga clic o pulse en el lienzo fuera de la visualización que acaba de crear.
2. En el panel **Visualizaciones** de la derecha, haga clic o pulse **Tarjeta**.
   
    ![Visualizaciones: tarjeta](./media/sharepoint-scenario-build-report/05-03-11-visuals-card.png)
3. Arrastre **MaxDaysPending** de **Project Requests**, en el panel **Campos**, a **Campos** en el panel **Visualizaciones**.
   
    ![Campos en el panel Visualizaciones](./media/sharepoint-scenario-build-report/05-03-12-value-max.png)
4. Haga clic o pulse en **Formato** (rodillo de pintura) y, después, en **Borde**, a **Activar**.
   
    ![Copiar formato: borde](./media/sharepoint-scenario-build-report/05-03-13a-format.png)
5. En **Título**, seleccione **Activar** y agregue el título "Max days pending approval".
   
    ![Agregar un título](./media/sharepoint-scenario-build-report/05-03-13b-title.png)
   
    Ahora la visualización debería parecerse a la siguiente imagen.
   
    ![ Max days pending approval](./media/sharepoint-scenario-build-report/05-03-14-chart-max.png)
   
    Después de publicar este informe, vamos a usar este icono para desencadenar una alerta si el valor máximo de un proyecto pendiente llega a un umbral determinado.

### <a name="create-a-table-that-shows-the-time-between-project-approval-and-projected-start-date"></a>Creación de una tabla que muestre el tiempo transcurrido entre la aprobación del proyecto y la fecha de inicio previsto
1. Haga clic o pulse en el lienzo fuera de la visualización que acaba de crear.
2. En el panel **Visualizaciones** de la derecha, haga clic o pulse en **Tabla**.
   
    ![Visualizaciones: tabla](./media/sharepoint-scenario-build-report/05-03-15-visuals-table.png)
3. Arrastre **PMAssigned**, **Title** y **ApprovedStartDiff** de **Project Details**, en el panel **Campos**, a **Valores**, en el panel **Visualizaciones**.
   
    ![Valores en el panel Visualizaciones](./media/sharepoint-scenario-build-report/05-03-16-value-diff.png)
4. Arrastre **ProjectedStartDate** de **Project Details**, en el panel **Campos**, al área **Filtros** del panel **Visualizaciones** y seleccione todas las fechas, excepto **(En blanco)**.
   
    ![Filtrar por ProjectedStartDate](./media/sharepoint-scenario-build-report/05-03-17-filters-diff.png)
5. Ajuste el tamaño de las columnas de la tabla para que pueda ver todos los datos y ordénelos por **ApprovedStartDiff**, de forma descendente. Ahora la visualización debería parecerse a la siguiente imagen.
   
    ![Tabla con los valores de ApprovedStartDiff](./media/sharepoint-scenario-build-report/05-03-18-chart-diff.png)
6. En el área **Valores**, haga clic en la flecha hacia abajo (o púlsela) de **ApprovedStartDiff** y haga clic o pulse **Promedio**. Ahora se puede ver el tiempo medio que transcurre entre la aprobación de un proyecto y la fecha de inicio proyectada.
   
    ![Calcular media](./media/sharepoint-scenario-build-report/05-03-20a-average-menu.png)
7. Vuelva a hacer clic o a pulsar la flecha hacia abajo de **ApprovedStartDiff**, haga clic o pulse **Formato condicional** y, después, haga clic o pulse **Escalas de color de fondo**.
   
   ![Formato condicional](./media/sharepoint-scenario-build-report/05-03-20b-conditional-menu.png)
8. Establezca los colores de los campos **Mínimo** y **Máximo** como se muestra a continuación y haga clic o pulse **Aceptar**.
   
   ![Opciones de formato condicional](./media/sharepoint-scenario-build-report/05-03-21-conditional-dialog.png)
   
   Ahora la visualización debería parecerse a la siguiente imagen.
   
   ![Formato condicional completado](./media/sharepoint-scenario-build-report/05-03-22-chart-diff-completed.png)
   
   Como puede ver, los proyectos que ejecuta Irvin Sayers tienden a comenzar mucho más tarde que su aprobación. Puede que haya factores que no tengan nada que ver con el administrador asignado, pero merece la pena examinar este factor.

Esto nos lleva al final de la sección del informe y deberíamos tener un informe completo basado en los datos importados de SharePoint y limpiados y modelados en Power BI Desktop. Si todo ha salido según el plan, el informe debe ser similar al de la siguiente imagen.

![Informe completado](./media/sharepoint-scenario-build-report/05-03-23-report-completed.png)

## <a name="next-steps"></a>Pasos siguientes
El siguiente paso en esta serie de tutoriales es [publicar el informe de proyecto de Power BI y crear un panel](sharepoint-scenario-publish-report.md).

