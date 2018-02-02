---
title: "Configuración de alertas de datos para el panel de Power BI | Microsoft Docs"
description: "En esta tarea, se va a agregar una alerta en Power BI que avise de si se está tardando demasiado en aprobar proyectos pendientes, y un flujo que responda cuando se produzca esa alerta."
services: 
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 06/12/2017
ms.author: mblythe
ms.openlocfilehash: fb750e6345c6aa576e378134ed98be92c234a86b
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="set-up-data-alerts-for-the-power-bi-dashboard"></a>Configurar alertas de datos para el panel de Power BI
> [!NOTE]
> Este artículo forma parte de una serie de tutoriales acerca del uso de PowerApps, Microsoft Flow y Power BI con SharePoint Online. Asegúrese de leer la [introducción a la serie](sharepoint-scenario-intro.md) para hacerse una idea general, así como para obtener descargas relacionadas.

En esta tarea, se va a agregar una alerta en Power BI que avise de si se está tardando demasiado en aprobar proyectos pendientes, y un flujo que responda cuando se produzca esa alerta. Para más información sobre las alertas, consulte [Alertas de datos en el servicio Power BI](https://powerbi.microsoft.com/documentation/powerbi-service-set-data-alerts).

## <a name="step-1-create-an-alert"></a>Paso 1: Creación de una alerta
1. En el servicio Power BI, abra el panel que creó en la última tarea.
2. En la tarjeta con un solo número, pulse o haga clic en el botón de puntos suspensivos (**…**).
   
    ![Tarjeta con máximo de días pendientes de aprobación](./media/sharepoint-scenario-alerts-flow/07-01-01-tile-ellipsis.png)
3. Haga clic o pulse ![en Icono de campana](./media/sharepoint-scenario-alerts-flow/icon-bell.png).
   
    ![Menú de icono](./media/sharepoint-scenario-alerts-flow/07-01-02-tile-bell.png)
4. En el panel derecho, pulse o haga clic en **Agregar regla de alertas**.
   
    ![Agregar regla de alertas](./media/sharepoint-scenario-alerts-flow/07-01-03-add-alert.png)
5. Observe las opciones disponibles para las alertas, como la frecuencia con la que se debe ejecutar una alerta. Escriba el valor 25 para **Umbral** y pulse o haga clic en **Guardar y cerrar**.
   
    ![Establecer el umbral de alerta y guardar](./media/sharepoint-scenario-alerts-flow/07-01-04-save-alert.png)

La alerta no se activará ahora mismo, aunque 56 esté por encima del umbral de 25. Se activará cuando se actualicen los datos, lo que se verá en el [recorrido de principio a fin del escenario](sharepoint-scenario-summary.md).

Cuando se activa la alerta, Power BI envía un mensaje de correo electrónico a su creador; en el paso siguiente, se verá cómo enviar correo adicional mediante Microsoft Flow.

## <a name="step-2-create-a-flow-that-responds-to-the-alert"></a>Paso 2: Creación de un flujo que responda a la alerta
1. Inicie sesión en flow.microsoft.com y pulse o haga clic en **Servicios** y en **Power BI**.
   
    ![Power BI en Microsoft Flow](./media/sharepoint-scenario-alerts-flow/07-01-05-power-bi.png)
2. Pulse o haga clic en **Enviar un correo electrónico al público cuando se desencadene una alerta de datos de Power BI**.
   
    ![Enviar un correo electrónico cuando se desencadene una alerta de datos de Power BI](./media/sharepoint-scenario-alerts-flow/07-01-06-alert-flow.png)
3. Pulse o haga clic en **Usar esta plantilla**.
4. Si aún no ha iniciado sesión, inicie sesión en Outlook y Power BI, y pulse o haga clic en **Continuar**.
   
    ![Iniciar sesión y continuar](./media/sharepoint-scenario-alerts-flow/07-01-08-continue.png)
5. En la lista desplegable **Id. de alerta**, seleccione **Alert for Max days pending approval** (Alerta para máximo de días pendientes de aprobación).
   
    ![Especificar una alerta como desencadenador](./media/sharepoint-scenario-alerts-flow/07-01-09-choose-alert.png)
6. En el cuadro **A**, escriba una dirección de correo electrónico válida.
   
    ![Especificar a quién se debe enviar el mensaje de correo electrónico](./media/sharepoint-scenario-alerts-flow/07-01-10-choose-email.png)
7. Pulse o haga clic en **Editar** para ver otros campos que se pueden actualizar.
   
    ![Editar correo electrónico de alerta](./media/sharepoint-scenario-alerts-flow/07-01-11-email-full.png)
8. En la parte superior derecha de la pantalla, haga clic en **Crear flujo** y en **Listo**.
   
    ![Botón Listo](./media/sharepoint-scenario-alerts-flow/07-01-12-done.png)

Se verá esta ejecución de flujo en el [recorrido de principio a fin del escenario](sharepoint-scenario-summary.md). Ahora se va a continuar con la última tarea de este escenario: insertar un informe de Power BI en SharePoint.

## <a name="next-steps"></a>Pasos siguientes
El siguiente paso en esta serie de tutoriales es [insertar el informe de proyecto de Power BI en SharePoint Online](sharepoint-scenario-embed-report.md).

