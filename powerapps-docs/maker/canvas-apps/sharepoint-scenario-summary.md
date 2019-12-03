---
title: Tutorial de principio a fin del escenario de integración de SharePoint Online | Microsoft Docs
description: Realice un tutorial de principio a fin para el escenario que se ha creado en esta serie de tutoriales.
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/12/2017
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d6ee64ddb2ae2f2a9c114a70970843627b92efb1
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74709704"
---
# <a name="walk-end-to-end-through-the-completed-sharepoint-online-integration-scenario"></a>Tutorial de principio a fin para el escenario de integración de SharePoint Online completado
> [!NOTE]
> Este artículo forma parte de una serie de tutoriales sobre el uso de Power Apps, Power Automatic y Power BI con SharePoint Online. Asegúrese de leer la [introducción a la serie](sharepoint-scenario-intro.md) para hacerse una idea general, así como para obtener descargas relacionadas.

Se ha tratado una cantidad enorme de datos en esta serie de tutoriales, desde la creación de aplicaciones de lienzo y flujos hasta la creación de informes y su inserción en SharePoint. Con suerte, habrá aprendido mucho y visto lo suficiente sobre cómo se integran estas tecnologías, para que pueda integrar aplicaciones de lienzo, flujos e informes en SharePoint según sus propias necesidades. Antes de terminar, se va a realizar un recorrido del escenario de principio a fin para ver cómo funcionan juntas todas las partes.

## <a name="step-1-add-a-project-to-the-project-requests-list"></a>Paso 1: Incorporación de un proyecto a la lista Project Requests
1. En la lista **Project Requests**, pulse o haga clic en **Todos los elementos** y en **Project Requests app**.
   
    ![Vista de Project Requests app](./media/sharepoint-scenario-summary/09-00-01-view-app.png)
2. Haga clic en **Abrir**, lo que abre la aplicación en una nueva pestaña de explorador.
   
    ![Abrir Project Requests app](./media/sharepoint-scenario-summary/09-00-02-open-app.png)
3. En la aplicación, pulse o haga clic en ![Icono Agregar elemento](./media/sharepoint-scenario-summary/icon-add-item.png) para crear un elemento.
4. Rellene el formulario con los siguientes valores:
   
   * **Title** = "Mobile devices for design team"

   * **Approved** = "Pending"

   * **Description** = "The design team will now use Contoso-supplied devices"

   * **EstimatedDays** = "30"

   * **ProjectType** = "New hardware"

   * **RequestDate** = "03/01/2017"

   * **Requestor** = "Emily Braun"
     
     ![Formulario de edición de solicitudes de proyecto](./media/sharepoint-scenario-summary/09-01-01-app-new.png)
5. Haga clic o pulse ![en Icono de marca de verificación](./media/sharepoint-scenario-summary/icon-check-mark.png)y cierre la pestaña de explorador.
6. Vuelva a la lista **Project Requests**, pulse o haga clic en **Project Requests app** y en **Todos los elementos**.
   
    ![Ver todos los elementos](./media/sharepoint-scenario-summary/09-01-01a-view-all.png)
7. Compruebe la nueva entrada en la lista.
   
    ![Lista de SharePoint con nueva entrada](./media/sharepoint-scenario-summary/09-01-02-list-new.png)

## <a name="step-2-approve-the-project"></a>Paso 2: Aprobación del proyecto
1. Cuando agrega el elemento en el paso 1, se debería ejecutar el flujo y enviar un correo electrónico de aprobación. Compruebe la bandeja de entrada de la cuenta de correo electrónico del aprobador.
   
    ![Correo electrónico de solicitud de aprobación](./media/sharepoint-scenario-summary/09-02-01-allan-email.png)
2. Haga clic en **Aprobar**. El flujo ejecuta otro proceso, y obtiene información similar a la siguiente directamente en el correo electrónico.
   
    ![Acción completada](./media/sharepoint-scenario-summary/09-02-01a-action-complete.png)
3. Compruebe la bandeja de entrada de la cuenta de correo electrónico del solicitante; debería ver un correo electrónico de aprobación.
   
    ![Correo electrónico de aprobación al solicitante](./media/sharepoint-scenario-summary/09-02-02-megan-email.png)
4. Compruebe la entrada actualizada en la lista.
   
    ![Lista de SharePoint con entrada actualizada](./media/sharepoint-scenario-summary/09-02-03-yes.png)

## <a name="step-3-assign-a-manager-to-the-project"></a>Paso 3: Asignación de un administrador al proyecto
1. En primer lugar, se va a echar un vistazo a la lista **Project Details** en SharePoint. El nuevo proyecto tiene el valor **Sin asignar** en la columna **PMAssigned**.
   
    ![Elemento de lista de SharePoint sin asignar](./media/sharepoint-scenario-summary/09-03-01-unassigned.png)
2. En el sitio de SharePoint, en el panel izquierdo, pulse o haga clic en **Project Management app**.
3. En la primera pantalla, pulse o haga clic en **Assign Manager**.
   
    ![Asignar administrador al proyecto](./media/sharepoint-scenario-summary/09-03-02-intro-screen.png)
4. En la pantalla **Assign Manager**, verá los dos proyectos sin asignar en la lista. Seleccione el proyecto **Mobile devices for design team**.
   
    ![Proyecto sin asignar seleccionado en la aplicación](./media/sharepoint-scenario-summary/09-03-03-selected.png)
5. En la entrada de texto **Manager**, escriba "Joni Sherman" y haga clic en **OK**.
   
    Se aplica el cambio a la lista y la galería se actualiza, de forma que solo se muestra el proyecto sin asignar restante.
   
    ![Administrador asignado a un proyecto](./media/sharepoint-scenario-summary/09-03-04-updated.png)
6. Cierre la aplicación y vuelva a la lista de SharePoint. Verá que la entrada del proyecto se ha actualizado con el nombre del administrador de proyecto.
   
    ![Elemento de lista de SharePoint asignado](./media/sharepoint-scenario-summary/09-03-05-assigned.png)

## <a name="step-4-add-time-estimates-for-the-project"></a>Paso 4: Incorporación de las estimaciones de tiempo para el proyecto
1. Pulse o haga clic en ![Icono Atrás](./media/sharepoint-scenario-summary/icon-back.png) para volver a la primera pantalla y en **Update Details**.
   
    ![Actualizar detalles del proyecto](./media/sharepoint-scenario-summary/09-04-00-intro-screen.png)
2. En la pantalla **View Projects**, escriba "Mobile" en el cuadro de búsqueda.
   
    ![Buscar en la aplicación](./media/sharepoint-scenario-summary/09-04-01-search-mobile.png)
3. Haga clic en ![Icono de flecha de detalles](./media/sharepoint-scenario-summary/icon-details-arrow.png) para el elemento **Mobile devices for design team**.
   
    ![Seleccionar el proyecto para actualizar](./media/sharepoint-scenario-summary/09-04-02-select-project.png)
4. En la pantalla **Update Details**, establezca los valores siguientes:
   
   * El campo **Status** = "Not started"

   * El campo **ProjectedStartDate** = "3/6/2017"

   * El campo **ProjectedEndDate** = "3/24/2017"

   * El campo **ProjectedDays** = "15"
     
     ![Actualizar detalles del proyecto](./media/sharepoint-scenario-summary/09-04-03-update.png)
5. Haga clic o pulse ![en Icono de marca de verificación](./media/sharepoint-scenario-summary/icon-check-mark.png) para aplicar el cambio a la lista de SharePoint.
6. Cierre la aplicación y vuelva a la lista. Verá que la entrada del proyecto se ha actualizado con los cambios de fecha y día.
   
   ![Detalles actualizados en la lista de SharePoint](./media/sharepoint-scenario-summary/09-04-04-updated-list.png)

## <a name="step-5-review-report-data-for-existing-projects"></a>Paso 5: Revisión de datos de informe para proyectos existentes
1. En SharePoint Online, pulse o haga clic en **Contenidos del sitio** y en **Páginas del sitio**.
2. Abra la página **Project Analysis** que se creó antes.
   
    ![Informe de análisis de proyecto insertado](./media/sharepoint-scenario-summary/09-05-01-report-complete.png)
3. Revise la visualización de varianza.
   
    ![Gráfico que muestra la varianza](./media/sharepoint-scenario-summary/09-05-02-chart-variance.png)
   
    Como se señaló cuando se creó esta visualización, hay mucha más varianza en los proyectos ejecutados por Irvin Sayers que en los de Joni Sherman.
4. Explore en profundidad la visualización y verá que gran parte de la varianza procede de dos proyectos que tardaron mucho más tiempo del previsto.
   
    ![Gráfico que muestra detalles de la varianza](./media/sharepoint-scenario-summary/09-05-03-chart-variance-drill.png)
5. Revise la tabla que muestra cuánto tiempo tardan los proyectos en pasar de la aprobación a la fecha de inicio proyectada.
   
    ![Tabla que muestra las diferencias en la fecha de inicio](./media/sharepoint-scenario-summary/09-05-04-chart-diff-completed.png)
   
    Como se señaló cuando se creó esta visualización, los proyectos que se asignaron a Irvin Sayers tardan más en iniciarse y dos de ellos están tardando mucho más que el resto.

## <a name="step-6-respond-to-pending-project-delays"></a>Paso 6: Respuesta a retrasos en proyectos pendientes
1. En el servicio Power BI, pulse o haga clic en el conjunto de datos **project-analysis** y después en **ACTUALIZAR AHORA**. La actualización desencadena la alerta que se configuró para proyectos pendientes.
   
    ![Actualizar conjunto de datos ahora](./media/sharepoint-scenario-summary/09-06-01-refresh.png)
2. Una vez completada la actualización, el **Centro de notificaciones** en la parte superior derecha muestra un nuevo icono de notificación.
   
    ![Centro de notificaciones de Power BI](./media/sharepoint-scenario-summary/09-06-02-alert.png)
   
    Esto puede tardar un tiempo, así que vuelva a consultarlo si no lo ve de inmediato.
3. Abra el Centro de notificaciones para ver los detalles de la alerta que se ha activado.
   
    ![Notificación para alerta de datos](./media/sharepoint-scenario-summary/09-06-03-notification.png)
4. Compruebe la bandeja de entrada de la persona que creó la alerta (Megan Bowen, en este caso).
   
    ![Correo electrónico de alerta de Power BI](./media/sharepoint-scenario-summary/09-06-04-email-powerbi.png)
5. Compruebe la bandeja de entrada de la persona que agregó en el flujo de alertas de datos (Allan DeYoung, en este caso).
   
    ![Correo electrónico de alerta de Power Automatic](./media/sharepoint-scenario-summary/09-06-05-email-flow.png)
6. Ahora que tiene información sobre los proyectos pendientes, puede regresar y aprobar los que tenga esperando.

Con esto, ha llegado a la conclusión de este tutorial de principio a fin y de esta serie de tutoriales. Puede continuar su viaje en los siguientes sitios:

* [Power apps](https://www.powerapps.com/)
* [Automatización de la energía](https://flow.microsoft.com)
* [Power BI](https://www.powerbi.com)
* [Comunidad de usuarios avanzados](https://powerusers.microsoft.com/)
* [SharePoint](https://sharepoint.microsoft.com)
* [Comunidad tecnológica de Microsoft](https://techcommunity.microsoft.com/)

Proporcione su opinión sobre esta serie, sugerencias para adiciones o ideas para contenidos adicionales que le ayuden a trabajar con las tecnologías tratadas.

