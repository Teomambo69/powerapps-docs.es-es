---
title: Organizar su equipo para desarrollar soluciones (Common Data Service para aplicaciones) | Microsoft Docs
description: En este documento se enumeran algunas estrategias que se pueden usar cuando varios desarrolladores trabajan en la misma solución
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="organize-your-team-to-develop-solutions"></a>Organizar a su equipo para desarrollar soluciones

Cuando varios desarrolladores tienen que trabajar en la misma solución, puede que desee crear un entorno donde cada desarrollador pueda crear personalizaciones que no interferirán con el trabajo de otros desarrolladores. También es posible que necesite mover la solución de entornos de desarrollo a entornos de prueba y a entornos de prueba de aceptación de usuario (UAT).  
  
<a name="BKMK_StrategiesForTeamDev"></a>   
## <a name="strategies-for-team-development"></a>Estrategias de desarrollo de equipo  
 Algunas de las estrategias para administrar el desarrollo de equipo de las soluciones son las siguientes:  
  
-   [Única organización: una solución principal](organize-team-develop-solutions.md#BKMK_SingleOrgMasterSolution)  
  
-   [Única organización: soluciones de varios desarrolladores + solución principal](organize-team-develop-solutions.md#BKMK_SingleOrgMultipleDeveloper)  
  
-   [Una organización por cada desarrollador](organize-team-develop-solutions.md#BKMK_OneOrgPerDev)  
  
<a name="BKMK_SingleOrgMasterSolution"></a>   
### <a name="single-organization-one-master-solution"></a>Única organización: una solución principal  
 Varios programadores pueden trabajar en una sola organización; sin embargo, deben tener cuidado de trabajar en componentes independientes. Esto es más sencillo cuando se instala primero cualquier solución administrada de requisito previo (bibliotecas compartidas).  
  
<a name="BKMK_SingleOrgMultipleDeveloper"></a>   
### <a name="single-organization-multiple-developer-solutions--master-solution"></a>Única organización: varias soluciones de desarrollador + solución maestra  
 En una organización única, puede crear soluciones no administradas independientes para cada desarrollador. Cada solución contiene un conjunto de una solución maestra. Cada componente de la solución solo existe en una solución no administrada. Los desarrolladores no agregan componentes de la solución existentes a las soluciones no administradas asignadas a ellas. Esto proporciona una separación clara de componentes que se están modificando. No es necesario que se combinen los cambios porque la solución de cada desarrollador contiene una referencia a los componentes que se incluyen en la solución maestra.  
  
<a name="BKMK_OneOrgPerDev"></a>   
### <a name="one-organization-per-developer"></a>Una organización por desarrollador  

 Cada desarrollador puede trabajar en su propia organización. Para comprobar sus cambios en CDS para aplicaciones, deben exportar su solución como solución no administrada. La solución de la organización de cada desarrollador se importa a continuación a una solución maestra. Use la solución maestra para exportar la solución administrada.  
  
<a name="BKMK_DeployingSolutionsFromDevThroughToProduction"></a>   
## <a name="deploy-solutions-from-development-through-test-and-production-environments"></a>Implementar soluciones desde el desarrollo a través de los entornos de producción y prueba  
 En organizaciones de desarrollo, las soluciones se implementan en los diferentes entornos de prueba y de ensayo para análisis antes de que se implementan en un entorno de producción. En las notas del producto [Implementar soluciones de Microsoft Dynamics CRM 2011 y CRM Online desde desarrollo a través de entornos de prueba y producción](http://go.microsoft.com/fwlink/p/?LinkId=232288) se explora cómo implementar soluciones de Dynamics 365 en escenarios reales en entornos de prueba y producción de formas confiables y repetibles usando la automatización. El documento también resalta las restricciones específicas que existen cuando implementa y prueba las soluciones en CDS para aplicaciones.  
  
### <a name="see-also"></a>Vea también  
 [Planificación del desarrollo de soluciones](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Modularizar sus soluciones](organize-solutions.md)   
 [Notas del producto: Implementar soluciones de Dynamics 365 Customer Engagement y de CRM Online desde desarrollo a través de entornos de prueba y producción](http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=27824)