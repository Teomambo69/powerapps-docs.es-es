---
title: Definir y consultar datos jerárquicos con Common Data Service for Apps | MicrosoftDocs
description: Aprenda a definir y consultar datos relacionados jerárquicamente
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="define-and-query-hierarchically-related-data"></a>Definir y consultar datos relacionados jerárquicamente

Puede obtener información de negocio valiosa definiendo y consultando datos relacionados jerárquicamente. Las funciones de visualización y modelado jerárquico tienen varias ventajas:  
  
- Vea y explore información jerárquica compleja.  
- Vea indicadores clave de rendimiento (KPIs) en la vista contextual de una jerarquía.  
- Analice visualmente información clave en la web y las tabletas.  
  
Algunas entidades estándar ya tienen definidas jerarquías. Otras entidades, incluidas las entidades personalizadas, pueden habilitarse para una jerarquía y puede crear las visualizaciones para ellas. 

## <a name="define-hierarchical-data"></a>Definir datos jerárquicos

Con Common Data Service for Apps, las estructuras jerárquicas de datos son compatibles con relaciones de uno a varios (1:N) *que hacen referencia a sí mismas* de registros relacionados. 

> [!NOTE]
> *Que hacen referencia a sí mismas* significa que la entidad está relacionada consigo misma. Por ejemplo, la entidad Cuenta tiene un campo de búsqueda para asociarlo al registro de otra entidad Cuenta.

Cuando existe una relación de uno a varios (1:N) que hace referencia a sí misma, en la definición de la relación, existe la opción **Jerárquica** que se puede definir como **Sí**.

![Valor de jerárquica en la definición de una relación](media/self-referential-relationship-car-solution-explorer.png)

Para consultar los datos como jerarquía, debe habilitar como jerárquica una de las relaciones que hacen referencia a sí mismas de uno a varios (1: N) de la entidad. Esto solo se puede hacer usando el explorador de soluciones.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

Para activar la jerarquía:  
  
1. Mientras [visualiza relaciones de 1:N](create-edit-1n-relationships-solution-explorer.md#view-entity-relationships), seleccione la relación que hace referencia a sí misma que desee editar.
2. En **Definición de relación**, establezca **Jerárquica** en **Sí**.  
  
> [!NOTE]
> - Algunas de las relaciones (1:N) predefinidas no se pueden personalizar. Esto evitará que configure esas relaciones como jerárquicas.  
> - Puede especificar una relación jerárquica para las relaciones que hacen referencia a sí mismas del sistema. Esto incluye las relaciones 1:N que hacen referencia a sí mismas de tipo sistema, como la relación "contact_master_contact".  

> [!IMPORTANT]
> Puede tener varias relaciones que hacen referencia a sí mismas, pero únicamente una relación por entidad se puede definir como la relación jerárquica. Si intenta cambiar el valor una vez aplicado, recibirá una advertencia:
>
> - **Al deshabilitar:** Si desactiva la configuración de jerarquías para esta relación, todas las definiciones, procesos y vistas consolidadas que usen esta jerarquía dejarán de funcionar. ¿Desea continuar? 
> - **Al habilitar:** Si habilita la configuración de jerarquías para esta relación, todas las definiciones consolidadas que usen esta jerarquía existente dejarán de ser válidas. ¿Desea continuar?
>
> A menos que esté seguro de que no hay otras dependencias en la jerarquía existente, revise cualquier documentación sobre la implementación o consulte con otros personalizadores para saber cómo se usa la relación jerárquica existente antes de continuar.

<a name="BKMK_Querydata"></a> 
  
## <a name="query-hierarchical-data"></a>Consultar datos jerárquicos  

Sin una jerarquía definida, para recuperar datos jerárquicos deberá consultar de forma iterativa los registros relacionados. Con una jerarquía definida, podrá consultar los datos relacionados como una jerarquía en un paso. Puede consultar los registros usando la lógica de **Bajo** y **No menor que**. Los operadores jerárquicos **Bajo** y **No menor que** aparecen en Búsqueda avanzada y el editor de flujo de trabajo. Para obtener más información acerca de cómo utilizar estos operadores, consulte [Configurar pasos del flujo de trabajo](/flow/configure-workflow-steps#setting-conditions-for-workflow-actions). Para obtener más información sobre Búsqueda avanzada, consulte [Crear, editar o guardar la búsqueda de Búsqueda avanzada](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search)..  

> [!NOTE]
> Los desarrolladores también podrán utilizar estos operadores en código. Más información [Documentación para desarrolladores: Consultar datos jerárquicos](/dynamics365/customer-engagement/developer/org-service/query-hierarchical-data)
  
Los siguientes ejemplos muestran escenarios para consultar jerarquías:  
  
### <a name="query-account-hierarchy"></a>Consultar jerarquía de cuenta  
  
![Consultar cuentas en la jerarquía de cuentas](media/query-accounts.png)  
  
### <a name="query-account-hierarchy-including-related-activities"></a>Consultar jerarquía de cuenta, incluidas actividades relacionadas  
  
![Consultar actividades relacionadas de la cuenta](media/query-account-related-activities.png)  
  
###  <a name="query-account-hierarchy-including-related-opportunities"></a>Consultar jerarquía de cuenta, incluidas oportunidades relacionadas  
  
![Consultar oportunidades relacionadas de la cuenta](media/query-account-related-opportunities.png)  
  
## <a name="see-also"></a>Vea también 
[Crear y editar relaciones de entidad de 1: N (uno a varios) o N:1 (varios a uno)](create-edit-1n-relationships.md)<br />
[Creación y edición de relaciones entre entidades 1:N (uno a varios) o N:1 (varios a uno) con el explorador de soluciones](create-edit-1n-relationships-solution-explorer.md)<br />
[Visualizar datos jerárquicos con aplicaciones controladas por modelos](visualize-hierarchical-data.md)<br />
[Vídeo: Modelos de seguridad jerárquica](http://www.youtube.com/watch?v=kx5So32DrCo&index=10&list=PLC3591A8FE4ADBE07)<br />
[Vídeo: Visualización de la jerarquía](http://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)
