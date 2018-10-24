---
title: Definición y consulta de datos jerárquicos con Common Data Service para aplicaciones | Microsoft Docs
description: Obtenga información sobre cómo realizar consultas a datos relacionados jerárquicamente y definirlos.
ms.custom: ''
ms.date: 06/02/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 0cf62817-5ff5-40bb-ad17-e1f6b0921720
caps.latest.revision: 42
ms.author: matp
manager: kvivek
ms.openlocfilehash: 4dad7da635156350d104d68108ac4acfbb991862
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39698814"
---
# <a name="define-and-query-hierarchically-related-data"></a>Definición y consulta de datos relacionados jerárquicamente

Puede obtener valiosas perspectivas de negocio mediante la definición y la consulta de datos relacionados jerárquicamente. Las funcionalidades de modelado y visualización jerárquicos ofrecen una serie de ventajas:  
  
- Ver y explorar información jerárquica compleja.  
- Ver indicadores clave de rendimiento (KPI) en la vista contextual de una jerarquía.  
- Analizar visualmente la información clave en la Web y las tabletas.  
  
Algunas entidades estándar ya tienen jerarquías definidas. Otras entidades, incluidas las entidades personalizadas, pueden habilitarse para una jerarquía y puede crear las visualizaciones para ellas. 

## <a name="define-hierarchical-data"></a>Definición de datos jerárquicos

Con Common Data Service para aplicaciones, las estructuras de datos jerárquicas son compatibles con las relaciones de *autorreferencia* uno a varios (1:N) de los registros relacionados. 

> [!NOTE]
> *Autorreferencia* significa que la entidad está relacionada consigo misma. Por ejemplo, la entidad de cuenta tiene un campo de búsqueda para asociarlo con otro registro de entidad de cuenta.

Cuando existe una relación uno a varios (1:N) de autorreferencia, en la definición de la relación está disponible la opción **Jerárquica** para establecerla en **Sí**.

![Configuración jerárquica en la definición de la relación](media/self-referential-relationship-car-solution-explorer.png)

Para consultar los datos como una jerarquía, debe establecer una de las relaciones de autorreferencia uno a varios (1:N) de la entidad como jerárquica. Esto solo se puede hacer usando el Explorador de soluciones.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

Para activar la jerarquía:  
  
1. Mientras [visualiza relaciones 1:N](create-edit-1n-relationships-solution-explorer.md#view-entity-relationships), seleccione la relación de autorreferencia que desea editar.
2. En la **Definición de relación**, establezca **Jerárquica** en **Sí**.  
  
> [!NOTE]
> - No se pueden personalizar algunas de las relaciones sencillas (1:N). Esto impedirá establecer esas relaciones como jerárquicas.  
> - Puede especificar una relación jerárquica para las relaciones de autorreferencia del sistema. Esto incluye las relaciones 1:N de autorreferencia del tipo de sistema, como la relación "contact_master_contact".  

> [!IMPORTANT]
> Puede tener varias relaciones de autorreferencia, pero solo una relación por cada entidad puede definirse como la relación jerárquica. Si intenta cambiar la configuración una vez aplicada, obtendrá una advertencia:
>
> - **Al deshabilitar:** si desactiva la configuración de la jerarquía para esta relación, todas las definiciones consolidadas, los procesos y las vistas que usan esta jerarquía no funcionarán. ¿Quiere continuar? 
> - **Al habilitar:** si habilita la configuración de la jerarquía para esta relación, todas las definiciones consolidadas que usan la jerarquía existente dejarán de ser válidas. ¿Quiere continuar?
>
> A menos que esté seguro de que no hay ninguna otra dependencia en la jerarquía existente, debe revisar cualquier documentación sobre la implementación o consultar a otros personalizadores para saber cómo se utiliza la relación jerárquica existente antes de continuar.

<a name="BKMK_Querydata"></a> 
  
## <a name="query-hierarchical-data"></a>Datos jerárquicos de consulta  

Sin una jerarquía definida, para recuperar los datos jerárquicos, debe consultar de forma iterativa los registros relacionados. Con una jerarquía definida, puede consultar los datos relacionados como una jerarquía en un solo paso. Puede consultar los registros con la lógica **En** y **No en**. Los operadores jerárquicos **En** y **No en** se exponen en el editor de flujo de trabajo y en la búsqueda avanzada. Para más información sobre cómo usar estos operadores, vea [Configurar pasos de flujo de trabajo](/flow/configure-workflow-steps#setting-conditions-for-workflow-actions). Para más información sobre la búsqueda avanzada, vea [Crear, editar o guardar búsquedas avanzadas](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search).  

> [!NOTE]
> Los desarrolladores también pueden usar estos operadores en el código. Más información: [Documentación para desarrolladores: Consultar datos jerárquicos](/dynamics365/customer-engagement/developer/org-service/query-hierarchical-data)
  
Los ejemplos siguientes ilustran escenarios para consultar las jerarquías:  
  
### <a name="query-account-hierarchy"></a>Consultar jerarquía de cuenta  
  
![Consultar cuentas de la jerarquía de cuenta](media/query-accounts.png)  
  
### <a name="query-account-hierarchy-including-related-activities"></a>Consultar jerarquía de cuenta, incluidas las actividades relacionadas  
  
![Consultar actividades relacionadas con la cuenta](media/query-account-related-activities.png)  
  
###  <a name="query-account-hierarchy-including-related-opportunities"></a>Consultar jerarquía de cuenta, incluidas las oportunidades relacionadas  
  
![Consultar oportunidades relacionadas con la cuenta](media/query-account-related-opportunities.png)  
  
## <a name="see-also"></a>Vea también 
[Crear y editar relaciones entre entidades de uno a varios o varios a uno](create-edit-1n-relationships.md)<br />
[Creación y edición de relaciones entre entidades 1:N (uno a varios) o N:1 (varios a uno) con el Explorador de soluciones](create-edit-1n-relationships-solution-explorer.md)<br />
[Visualizar datos jerárquicos con aplicaciones basadas en modelos](visualize-hierarchical-data.md)<br />
[Vídeo: Modelado de seguridad jerárquico](http://www.youtube.com/watch?v=kx5So32DrCo&index=10&list=PLC3591A8FE4ADBE07)<br />
[Vídeo: Visualización de la jerarquía](http://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)
