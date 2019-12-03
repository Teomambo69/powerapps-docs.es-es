---
title: Integración de Power Apps, Power Automatic y Power BI con SharePoint Online (Introducción) | Microsoft Docs
description: 'En esta serie de tutoriales se explica cómo crear una aplicación de lienzo básica para la administración de proyectos basada en listas de SharePoint y tres tecnologías clave que se integran con SharePoint Online: Power Apps, Power Automatic y Power BI.'
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/19/2017
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0e768b017dc4f21b803cdbd6cf7fab220fb0f23c
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74674693"
---
# <a name="integrate-power-apps-power-automate-and-power-bi-with-sharepoint-online"></a>Integre Power Apps, Power Automatic y Power BI con SharePoint Online
¿Tiene SharePoint Online y desea mejorar la automatización y simplificación de los procesos empresariales? ¿Ha trabajado con Power Apps, Power Automatic o Power BI, pero no está seguro de cómo usarlas con SharePoint Online? Ha venido al lugar correcto. En esta serie de tutoriales se explica cómo crear una aplicación de lienzo básica para la administración de proyectos basada en listas de SharePoint y tres tecnologías clave que se integran con SharePoint Online: Power Apps, Power Automatic y Power BI. Estas tecnologías funcionan de forma conjunta, lo que facilita el *análisis* de su negocio, la *actuación* sobre los resultados y la *automatización* de los flujos de trabajo. Cuando haya terminado con esta serie de tutoriales, tendrá un escenario estupendo similar al siguiente:

![Diagrama del escenario completo](./media/sharepoint-scenario-intro/composite-with-background.png)

## <a name="business-scenario"></a>Escenario empresarial
En esta serie de tutoriales, la empresa Contoso tiene un sitio de SharePoint Online donde administran el ciclo de vida de los proyectos, desde su solicitud, aprobación y desarrollo hasta la revisión final. Un *solicitante de proyecto* como, por ejemplo, un director de departamento, solicita un proyecto de TI mediante la adición de un elemento a una lista de SharePoint. Un *aprobador de proyecto* como, por ejemplo, un administrador de TI, revisa el proyecto y, a continuación, lo aprueba o lo rechaza. Si se aprueba, el proyecto se asigna a un *jefe de proyecto* y se agrega información adicional a una segunda lista en la misma aplicación. Un *analista de negocios* revisa los proyectos actuales y los ya finalizados mediante un informe de Power BI insertado en SharePoint.  Power Automatic se usa para enviar correo electrónico de aprobación y responder a Power BI alertas.

## <a name="getting-started-quickly"></a>Introducción rápida
El escenario que se presenta en esta serie de tutoriales es sencillo en comparación con una aplicación de análisis y gestión de proyectos con todas las prestaciones, pero aún así se tarda algún tiempo en completar todas las tareas. Si solo desea una introducción rápida al uso de Power Apps, Power Automatic y Power BI con SharePoint, consulte los artículos siguientes:

* **PowerApps**: [Creación de una aplicación desde SharePoint mediante PowerApps](app-from-sharepoint.md#generate-an-app-from-within-sharepoint-online) y [Generación de una aplicación para administrar datos en una lista de SharePoint](app-from-sharepoint.md)
* **Power Automatic**: [espera de aprobación en Power Automatic](https://docs.microsoft.com/flow/wait-for-approvals)
* **Power BI**: [Insertar el elemento web de informes en SharePoint Online](https://docs.microsoft.com/power-bi/service-embed-report-spo)

Una vez que haya terminado, confiamos en que volverá para comprobar el escenario completo.

Incluso dentro del mismo escenario, puede centrarse en las tareas que más le interesen e ir completando el resto a medida que disponga de más tiempo. Después de configurar las listas de SharePoint en la tarea 1, puede trabajar en las tareas 2 a 5 en cualquier orden. Por último, las tareas 6 a 8 son secuenciales. Finalmente, hemos incluido dos aplicaciones terminadas y un informe de Power BI Desktop como parte del [paquete de descarga](https://aka.ms/o4ia0f) de este escenario. Puede examinar estos y obtener información incluso aunque no realice todos los pasos de cada tarea.

## <a name="prerequisites"></a>Requisitos previos
Para completar el escenario, necesita las siguientes suscripciones y herramientas de escritorio. La suscripción a Office 365 Business Premium incluye Power apps y Power Automatic.

| **Suscripción o herramienta** | **Vínculo** |
| --- | --- |
| Suscripción a Office 365 Business Premium |[Suscripción de prueba](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) |
| Suscripción a Power BI Pro |[Suscripción de prueba](https://powerbi.microsoft.com/get-started/) (haga clic en **PROBAR GRATIS**) |
| Power BI Desktop |[Descarga gratuita](https://powerbi.microsoft.com/get-started/) (haga clic en **DESCARGAR GRATIS**) |

Lo ideal es tener un conocimiento básico de cada tecnología, pero incluso si no es así, podrá completar el escenario descrito. Use el siguiente contenido para ponerse al día:

* [Introducción a SharePoint](https://support.office.com/article/Get-started-with-SharePoint-909ec2f0-05c8-4e92-8ad3-3f8b0b6cf261)
* [Aprendizaje guiado de Power apps](../../guided-learning/index.md)
* [Alimentación automatizada de aprendizaje guiado](https://docs.microsoft.com/flow/guided-learning/)
* [Aprendizaje guiado de Power BI](https://docs.microsoft.com/power-bi/guided-learning/)

## <a name="next-steps"></a>Pasos siguientes
El siguiente paso en esta serie de tutoriales es [configurar las listas de SharePoint Online](sharepoint-scenario-setup.md) que se usan en toda la serie.

