---
title: "Integración de PowerApps, Microsoft Flow y Power BI con SharePoint Online (Introducción) | Microsoft Docs"
description: "Esta serie de tutoriales explora cómo crear una aplicación básica de administración de proyectos basada en listas de SharePoint y tres tecnologías claves que se integran con SharePoint Online: PowerApps, Microsoft Flow y Power BI."
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
ms.openlocfilehash: 98998b30eb4c407c6c2dcaa61c04c75d5b92e4f9
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="integrate-powerapps-microsoft-flow-and-power-bi-with-sharepoint-online"></a>Integración de PowerApps, Microsoft Flow y Power BI con SharePoint Online
¿Tiene SharePoint Online y desea mejorar la automatización y simplificación de los procesos empresariales? ¿Ha trabajado con PowerApps, Microsoft Flow o Power BI, pero no está seguro de cómo usarlos con SharePoint Online? Ha venido al lugar correcto. Esta serie de tutoriales explora cómo crear una aplicación básica de administración de proyectos basada en listas de SharePoint y tres tecnologías claves que se integran con SharePoint Online: PowerApps, Microsoft Flow y Power BI. Estas tecnologías funcionan de forma conjunta, lo que facilita el *análisis* de su negocio, la *actuación* sobre los resultados y la *automatización* de los flujos de trabajo. Cuando haya terminado con esta serie de tutoriales, tendrá un escenario estupendo similar al siguiente:

![Diagrama del escenario completo](./media/sharepoint-scenario-intro/composite-with-background.png)

## <a name="business-scenario"></a>Escenario empresarial
En esta serie de tutoriales, la empresa Contoso tiene un sitio de SharePoint Online donde administran el ciclo de vida de los proyectos, desde su solicitud, aprobación y desarrollo hasta la revisión final. Un *solicitante de proyecto* como, por ejemplo, un director de departamento, solicita un proyecto de TI mediante la adición de un elemento a una lista de SharePoint. Un *aprobador de proyecto* como, por ejemplo, un administrador de TI, revisa el proyecto y, a continuación, lo aprueba o lo rechaza. Si se aprueba, el proyecto se asigna a un *jefe de proyecto* y se agrega información adicional a una segunda lista en la misma aplicación. Un *analista de negocios* revisa los proyectos actuales y los ya finalizados mediante un informe de Power BI insertado en SharePoint.  Microsoft Flow se utiliza para enviar un correo electrónico de aprobación y para responder a las alertas de Power BI.

## <a name="getting-started-quickly"></a>Introducción rápida
El escenario que se presenta en esta serie de tutoriales es sencillo en comparación con una aplicación de análisis y gestión de proyectos con todas las prestaciones, pero aún así se tarda algún tiempo en completar todas las tareas. Si solo desea obtener una introducción rápida al uso de PowerApps, Microsoft Flow y Power BI con SharePoint, consulte los artículos siguientes:

* **PowerApps**: [Creación de una aplicación desde SharePoint mediante PowerApps](generate-app-from-sharepoint-list-interface.md) y [Generación de una aplicación para administrar datos en una lista de SharePoint](app-from-sharepoint.md)
* **Microsoft Flow**: [Espera de la aprobación en Microsoft Flow](https://flow.microsoft.com/documentation/wait-for-approvals)
* **Power BI**: [Insertar el elemento web de informes en SharePoint Online](https://powerbi.microsoft.com/documentation/powerbi-service-embed-report-spo)

Una vez que haya terminado, confiamos en que volverá para comprobar el escenario completo.

Incluso dentro del mismo escenario, puede centrarse en las tareas que más le interesen e ir completando el resto a medida que disponga de más tiempo. Después de configurar las listas de SharePoint en la tarea 1, puede trabajar en las tareas 2 a 5 en cualquier orden. Por último, las tareas 6 a 8 son secuenciales. Finalmente, hemos incluido dos aplicaciones terminadas y un informe de Power BI Desktop como parte del [paquete de descarga](https://aka.ms/o4ia0f) de este escenario. Puede examinar estos y obtener información incluso aunque no realice todos los pasos de cada tarea.

## <a name="prerequisites"></a>Requisitos previos
Para completar el escenario, necesita las siguientes suscripciones y herramientas de escritorio. La suscripción a Office 365 Business Premium incluye PowerApps y Microsoft Flow.

| **Suscripción o herramienta** | **Vínculo** |
| --- | --- |
| Suscripción a Office 365 Business Premium |[Suscripción de prueba](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) |
| PowerApps Studio |Use PowerApps Studio para web (no es preciso descargar nada) o [PowerApps Studio para Windows](https://aka.ms/powerappswin) |
| Suscripción a Power BI Pro |[Suscripción de prueba](https://powerbi.microsoft.com/get-started/) (haga clic en **PROBAR GRATIS**) |
| Power BI Desktop |[Descarga gratuita](https://powerbi.microsoft.com/get-started/) (haga clic en **DESCARGAR GRATIS**) |

Lo ideal es tener un conocimiento básico de cada tecnología, pero incluso si no es así, podrá completar el escenario descrito. Use el siguiente contenido para ponerse al día:

* [Introducción a SharePoint](https://support.office.com/article/Get-started-with-SharePoint-909ec2f0-05c8-4e92-8ad3-3f8b0b6cf261)
* [Aprendizaje guiado de PowerApps](https://powerapps.microsoft.com/guided-learning/)
* [Aprendizaje guiado de Microsoft Flow](https://flow.microsoft.com/guided-learning/)
* [Aprendizaje guiado de Power BI](https://powerbi.microsoft.com/guided-learning/)

## <a name="next-steps"></a>Pasos siguientes
El siguiente paso en esta serie de tutoriales es [configurar las listas de SharePoint Online](sharepoint-scenario-setup.md) que se usan en toda la serie.
