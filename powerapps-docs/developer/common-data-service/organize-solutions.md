---
title: Organizar sus soluciones (Common Data Service) | Microsoft Docs
description: En este documento se enumeran algunas estrategias para organizar sus soluciones
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: c24c701848f2a68d7a8ec9473dc521f6444f447d
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155412"
---
# <a name="organize-your-solutions"></a>Organizar sus soluciones

Antes de crear soluciones, dedique un tiempo de planificar con antelación. Por ejemplo, piense cuántas soluciones desea lanzar y si las soluciones compartirán componentes.  
  
 Además, determine cuántas organizaciones de Common Data Service necesitará para desarrollar su línea de soluciones. Puede usar una sola organización para la mayoría de las estrategias descritas en este tema. Sin embargo, si decide tener solo una organización y más adelante se da cuenta de que necesita más, puede ser desafiante cambiar las soluciones si los usuarios ya las han instalado. Si bien el uso de varias organizaciones puede introducir una mayor complejidad, puede brindar más flexibilidad.  
  
<a name="BKMK_OptionsToModularize"></a>   
## <a name="strategies-to-organize-your-solutions"></a>Estrategias para organizar sus soluciones  
 A continuación se muestran algunas estrategias para crear soluciones enumerados en orden, de las más sencilla a la más compleja:  
  
-   [Soluciones sin personalizar](organize-solutions.md#BKMK_NoCustomSolution)  
  
-   [Solución única](organize-solutions.md#BKMK_SingleSolution)  
  
-   [Varias soluciones](organize-solutions.md#BKMK_MultipleSolutions)  
  
-   [Varias soluciones con componentes compartidos](organize-solutions.md#BKMK_MultipleSolutionsSharedComponents)  
  
-   [Bibliotecas de la solución](organize-solutions.md#BKMK_SolutionLibraries)  
  
<a name="BKMK_NoCustomSolution"></a> 
  
### <a name="no-custom-solutions"></a>Soluciones sin personalizar  
 No es necesario que cree soluciones. Puede personalizar Common Data Service directamente con la solución predeterminada.  
  
 Aún puede exportar la solución predeterminada como una solución no administrada para transportarla entre las organizaciones.  
  
> [!TIP]
>  Si cambia el prefijo de personalización del editor de forma predeterminada a un valor que coincida con un editor que puede crear en el futuro, las nuevas personalizaciones que cree incluirán este prefijo de personalización en el nombre. De esta manera, si usa soluciones, puede agregar las personalizaciones que creó en la solución predeterminada una solución no administrada para que tengan nombres coherentes.  
  
<a name="BKMK_SingleSolution"></a>   
### <a name="single-solution"></a>Solución única  
 Al crear una solución, establece un conjunto de trabajo de personalizaciones. Esto facilita la búsqueda de los artículos que ha personalizado.  
  
 Se recomienda la utilización de este enfoque solo cuando desee crear una sola solución administrada. Si en el futuro considera que tiene que dividir la solución, tenga presente que puede usar varias soluciones.  
  
<a name="BKMK_MultipleSolutions"></a>   
### <a name="multiple-solutions"></a>Varias soluciones  
 Si tiene dos soluciones no relacionadas que no comparten componentes, el enfoque más directo consiste en crear dos soluciones no administradas.  
  
> [!NOTE]
>  En las soluciones, es muy común editar las cintas de opciones de la aplicación o el mapa del sitio. Si ambas soluciones modifican estos componentes de la solución, son componentes compartidos. Consulte la siguiente sección para ver cómo ejecutar los componentes compartidos.  
  
<a name="BKMK_MultipleSolutionsSharedComponents"></a>   
### <a name="multiple-solutions-with-shared-components"></a>Varias soluciones con componentes compartidos  
 Puede tener varias soluciones que comparten componentes. Es posible que tenga un determinado conjunto de funcionalidades comunes con varias soluciones y que esa funcionalidad común sea compatible con cualquier otra funcionalidad exclusiva para cada solución. Por ejemplo, puede tener un conjunto de complementos de utilidad que usa cada solución si bien cada una de las soluciones separadas no comparten otros componentes.  
  
 En este caso, cada solución se pueden desarrollar en una sola organización. Algunos componentes se pueden incluir en más de una solución siempre que los cambios que se les hayan realizado sean compatibles con todas las otras funciones que las usan. Es importante que todas las soluciones compartan el mismo editor de soluciones. Si el editor de soluciones no es idéntico, las organizaciones no podrán instalar más de una de sus soluciones.  
  
<a name="BKMK_SolutionLibraries"></a> 
  
### <a name="solution-libraries"></a>Bibliotecas de la solución  
 Para un ISV con varias soluciones o una implementación empresarial de gran tamaño, es posible que muchos componentes de la solución deban compartirse. Las mejores formas para que las soluciones compartan componentes es a través de las bibliotecas de la solución. Cree una biblioteca de la solución mediante la creación de una solución no administrada en una organización independiente y a continuación, empaquete esos componentes en una solución administrada. Instale la solución administrada en otra organización y deje que los desarrolladores relacionen estos componentes compartidos.  
  
 Common Data Service Solutions Framework le permite crear niveles de soluciones que dependen uno del otro. Normalmente, puede crear una biblioteca de soluciones que represente una solución "básica". Otras soluciones pueden generarse sobre esta solución base. Esto permite una separación más ordenada de los componentes. Los equipos de desarrollo que trabajan en las bibliotecas de la solución y los que trabajen en soluciones dependientes pueden desarrollar a diferentes ritmos. Las soluciones dependientes deben ser crearse después de que se instalen las bibliotecas de la solución.  
  
 Esto requiere la creación de una solución de requisito previo que los clientes se deben instalar antes de instalar una solución dependiente. Los desarrolladores que trabajen en las bibliotecas de la solución pueden seguir trabajando en ellas y actualizarlas siempre que no interrumpan ninguna de las soluciones dependientes que los necesiten.  
  
### <a name="see-also"></a>Vea también  
 [Organizar a su equipo para desarrollar soluciones](organize-team-develop-solutions.md)   
 [Planificación del desarrollo de soluciones](/dynamics365/customer-engagement/developer/plan-solution-development)
