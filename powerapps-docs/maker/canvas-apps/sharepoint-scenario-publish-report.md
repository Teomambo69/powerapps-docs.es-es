---
title: Publicación del informe de proyecto de Power BI y creación de un panel | Microsoft Docs
description: En esta tarea, vamos a publicar nuestro conjunto de datos y el informe en el servicio Power BI. A continuación, se creará un panel basado en este informe.
author: mgblythe
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/30/2018
ms.author: mblythe
ms.openlocfilehash: 988c072f6abb33e8606826fd105bc2e7f2c2c452
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39018753"
---
# <a name="publish-the-power-bi-project-report-and-create-a-dashboard"></a>Publicación del informe de proyecto de Power BI y creación de un panel
> [!NOTE]
> Este artículo forma parte de una serie de tutoriales acerca del uso de PowerApps, Microsoft Flow y Power BI con SharePoint Online. Asegúrese de leer la [introducción a la serie](sharepoint-scenario-intro.md) para hacerse una idea general, así como para obtener descargas relacionadas.

En esta tarea, vamos a publicar nuestro conjunto de datos y el informe en el servicio Power BI. A continuación, se creará un panel basado en este informe. Muchas veces, un informe tiene un gran número de visualizaciones y solo se usa un subconjunto en un panel. En este caso, vamos a agregar cuatro visualizaciones al panel.

## <a name="step-1-publish-the-dataset-and-report"></a>Paso 1: Publicación del conjunto de datos y el informe
1. En Power BI Desktop, en la pestaña **Inicio**, haga clic o pulse en **Publicar**.
   
    ![Publicar el conjunto de datos y el informe](./media/sharepoint-scenario-publish-report/06-01-01-publish.png)
2. Si aún no ha iniciado sesión en el servicio Power BI, especifique una cuenta y, a continuación, haga clic o pulse en **Iniciar sesión**.
   
    ![Iniciar sesión en la cuenta](./media/sharepoint-scenario-publish-report/06-01-02-account.png)
3. Escriba una contraseña y, a continuación, haga clic o pulse en **Iniciar sesión**.
   
    ![Escribir contraseña de la cuenta](./media/sharepoint-scenario-publish-report/06-01-03-password.png)
4. Elija un destino para el informe y, a continuación, haga clic o pulse en **Seleccionar**. Se recomienda la publicación en un área de trabajo del grupo para simplificar el acceso al informe en SharePoint. En este caso, vamos a publicar en el área de trabajo del grupo denominada **Project Management**. Para obtener más información, consulte [Colaboración en un área de trabajo de aplicación de Power BI](https://docs.microsoft.com/power-bi/service-collaborate-power-bi-workspace).
   
    ![Área de trabajo de destino](./media/sharepoint-scenario-publish-report/06-01-04-workspace.png)
5. Una vez finalizada la publicación, haga clic o pulse en **Abrir 'project-analysis.pbx' en Power BI**.
   
    ![Publicación finalizada correctamente](./media/sharepoint-scenario-publish-report/06-01-05-open-report.png)
6. El servicio Power BI carga el informe en un explorador. Haga clic o pulse en el menú situado en la esquina superior izquierda **(a)** para ver el panel de navegación izquierdo.
   
    ![Informe del servicio Power BI](./media/sharepoint-scenario-publish-report/06-01-06-service-report.png)
   
    Puede ver que, cuando se hizo la publicación, Power BI Desktop cargó un conjunto de datos **(d)** y un informe **(c)**. Va a crear paneles en el servicio, no en Power BI Desktop, y esta área de trabajo aún no tiene ningún panel **(b)**. Vamos a crear uno a continuación.

## <a name="step-2-configure-credentials-for-refresh"></a>Paso 2: Configuración de las credenciales para la actualización
1. En el servicio, haga clic o pulse en el ![icono de engranaje](./media/sharepoint-scenario-publish-report/icon-gear.png) en la esquina superior derecha. Después, haga clic o pulse en **Configuración**.
2. Haga clic o pulse en **Conjuntos de datos** y, después, en **project-analysis**.
   
    ![conjunto de datos project-analysis](./media/sharepoint-scenario-publish-report/06-01-07-dataset.png)
3. Expanda **Credenciales de origen de datos** y, a continuación, haga clic o pulse en **Editar credenciales**.
   
    ![Editar credenciales de origen de datos](./media/sharepoint-scenario-publish-report/06-01-08-credentials.png)
4. Seleccione **OAuth2** como método de autenticación y, a continuación, haga clic o pulse en **Iniciar sesión**.
   
    ![Iniciar sesión en SharePoint](./media/sharepoint-scenario-publish-report/06-01-09-sign-in.png)
5. Seleccione o inicie sesión en una cuenta que tenga permisos para las listas de SharePoint.
   
    ![Sesión iniciada en Office 365](./media/sharepoint-scenario-publish-report/06-01-10-account.png)
   
    Cuando se complete el proceso, obtendrá el siguiente mensaje en el servicio.
   
    ![Origen de datos actualizado](./media/sharepoint-scenario-publish-report/06-01-11-updated.png)

## <a name="step-3-create-a-dashboard"></a>Paso 3: Creación de un panel

1. Para volver al informe, en **INFORMES**, haga clic o pulse en **project-analysis**.

1. Haga clic o pulse en el gráfico de la esquina superior izquierda y, después, haga clic o pulse en ![el icono de anclar](./media/sharepoint-scenario-publish-report/icon-pin.png).
   
    ![Gráfico anclado](./media/sharepoint-scenario-publish-report/06-01-12-pin-projected.png)
2. Escriba un nombre para el panel al que desea anclarlo y, a continuación, haga clic o pulse en **Anclar**.
   
    ![Gráfico anclado al nuevo panel](./media/sharepoint-scenario-publish-report/06-01-13-pin-new.png)
3. Haga clic o pulse en el gráfico de la esquina superior derecha y, después, haga clic o pulse en ![el icono de anclar](./media/sharepoint-scenario-publish-report/icon-pin.png).
   
    ![Gráfico anclado](./media/sharepoint-scenario-publish-report/06-01-14-pin-variance.png)
4. Seleccione el panel existente, después, haga clic o pulse en **Anclar**.
   
    ![Gráfico anclado al panel existente](./media/sharepoint-scenario-publish-report/06-01-15-pin-existing.png)

5. Repita el proceso de anclaje con los otros dos objetos visuales.

6. En el panel de navegación izquierdo, haga clic o pulse en el nombre del panel.
   
    ![Nuevo panel de navegación del sitio](./media/sharepoint-scenario-publish-report/06-01-16-dashboard-menu.png)

7. Revise el panel. Si hace clic en un icono, volverá al informe.
   
    ![Panel terminado](./media/sharepoint-scenario-publish-report/06-01-17-dashboard-completed.png)

Así concluye la mayor parte del trabajo en Power BI. Si esta fue su primera experiencia de creación de informes y paneles, ¡enhorabuena! Si ya era un experto, esperamos que haya podido efectuar todos los pasos con rapidez. Ahora agregaremos alertas para asegurarnos de que sabe cuándo el panel necesita atención.

## <a name="next-steps"></a>Pasos siguientes
El siguiente paso en esta serie de tutoriales es [configurar alertas de datos para el informe de proyecto de Power BI](sharepoint-scenario-alerts-flow.md).

