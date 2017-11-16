---
title: "Inserción del informe de proyecto de Power BI en SharePoint Online | Microsoft Docs"
description: En esta tarea, se va a insertar el informe de Power BI en el mismo sitio de SharePoint Online que hospeda nuestras dos listas.
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
ms.openlocfilehash: 6574ad1c67c6fc42da3b1cd5940f163307829333
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="embed-the-power-bi-project-report-in-sharepoint-online"></a>Inserción del informe de proyecto de Power BI en SharePoint Online
**Nota**: Este artículo forma parte de una serie de tutoriales sobre el uso de PowerApps, Microsoft Flow y Power BI con SharePoint Online. Asegúrese de leer la [introducción a la serie](sharepoint-scenario-intro.md) para hacerse una idea general, así como para obtener descargas relacionadas.

La última tarea de este escenario consiste en insertar el informe de Power BI en el mismo sitio de SharePoint Online que hospeda nuestras dos listas. Power BI admite varios métodos de inserción y ha agregado recientemente la integración directamente en las páginas de SharePoint para vistas móviles y web.

Con este tipo de inserción, Power BI inserta el informe como un elemento web, proporciona un acceso adecuado a los usuarios y le permite desplazarse desde el informe insertado al informe de powerbi.com. En primer lugar, se va a generar un vínculo de inserción en Power BI. Posteriormente, se utilizará ese vínculo en una página que vamos a crear. Para más información sobre cómo insertar, consulte [Insertar el elemento web de informes en SharePoint Online](https://powerbi.microsoft.com/documentation/powerbi-service-embed-report-spo) (y, específicamente, la sección de requisitos).

## <a name="step-1-generate-an-embed-link"></a>Paso 1: Generación de un vínculo de inserción
1. Inicie sesión en Power BI y, en el panel de navegación izquierdo, haga clic o pulse en el nombre del informe.
   
    ![Ir al informe](./media/sharepoint-scenario-embed-report/08-01-01-reports.png)
2. Haga clic o pulse en **Insertar en SharePoint Online**.
   
    ![Insertar en SharePoint Online](./media/sharepoint-scenario-embed-report/08-01-02-embed-spo.png)
3. Copie el vínculo de inserción del cuadro de diálogo a un archivo y, a continuación, haga clic en **Cerrar**. Usaremos el vínculo después de haber creado una página de SharePoint.
   
    ![Vínculo de inserción para SharePoint](./media/sharepoint-scenario-embed-report/08-01-03-embed-url.png)

## <a name="step-2-embed-the-report"></a>Paso 2: Inserción del informe
1. Inicie sesión en SharePoint y, a continuación, haga clic o pulse en **Contenidos del sitio**.
   
    ![Contenidos del sitio de SharePoint](./media/sharepoint-scenario-embed-report/08-01-04-site-contents.png)
2. Podría incluir solamente un informe en la página principal del equipo, pero le mostraremos cómo crear también una página independiente para él. Haga clic o pulse en **Nueva** y, a continuación en **Página**.
   
    ![Nueva página de SharePoint](./media/sharepoint-scenario-embed-report/08-01-05-new-page.png)
3. Escriba un nombre para la página, como "Project Analysis".
4. Haga clic o pulse en el ![icono con el signo más](./media/sharepoint-scenario-embed-report/icon-plus.png) y , a continuación, en **Power BI**.
   
    ![Agregar elemento de página de Power BI](./media/sharepoint-scenario-embed-report/08-01-06-add-page-part.png)
5. Haga clic o pulse en **Agregar informe**.
   
    ![Agregar informe](./media/sharepoint-scenario-embed-report/08-01-07-add-report.png)
6. En el panel adecuado, copie la dirección URL en el cuadro **Vínculo del informe de Power BI**. Establezca **Mostrar panel de filtros** y **Mostrar el panel de navegación** en **Activado**.
   
    ![Configuración de informe](./media/sharepoint-scenario-embed-report/08-01-08-report-settings.png)
7. El informe ya se ha insertado en la página. Haga clic en **Publicar** para hacer que esté disponible para cualquier persona que pueda acceder al informe subyacente.
   
    ![Inserción de informe completada](./media/sharepoint-scenario-embed-report/08-01-09-report-complete.png)

## <a name="step-3-grant-access-to-the-report"></a>Paso 3: Concesión de acceso al informe.
Si usas grupos de Office 365, tal y como se recomienda, asegúrese de que los usuarios que necesitan acceder son miembros del área de trabajo del grupo en el servicio Power BI. Esto garantiza que los usuarios puedan ver el contenido de ese grupo. Para más información, consulte [Creación de grupos en Power BI](https://powerbi.microsoft.com/documentation/powerbi-service-create-a-group-in-power-bi).

Así concluye nuestro trabajo en Power BI para este escenario. Empezó extrayendo datos de nuestras listas de SharePoint en Power BI y ahora se ha cerrado el círculo con la inserción de un informe de Power BI de nuevo en SharePoint.

## <a name="next-steps"></a>Pasos siguientes
El siguiente paso en esta serie de tutoriales consiste en [ejecutar íntegramente el flujo de trabajo que hemos creado](sharepoint-scenario-summary.md).

