---
title: Consultar datos jerárquicos (Common Data Service) | Microsoft Docs
description: Lea cómo puede aprovechar los nuevos operadores de condición de consulta para consultar entidades con relaciones jerárquicas explícitas.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 61bcf12b58c3ce4438281adda0809dcda92c7cfa
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155360"
---
# <a name="query-hierarchical-data"></a>Consultar datos jerárquicos

Usted puede definir relaciones específicas de entidad de uno a varios que hacen referencia a sí mismas como jerárquicas. Puede escribir consultas que devuelven datos relacionados en estas jerarquías.  
  
Puede aprovechar los nuevos operadores de condición de consulta para consultar entidades con relaciones jerárquicas explícitas. Estos operadores sólo se aplican a la relación de entidad definida específicamente como relación jerárquica. Puede usar nuevos operadores de condición para recuperar estos datos jerárquicos cuando consulta utilizando <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> o <xref:Microsoft.Xrm.Sdk.Query.FetchExpression>.  
  
<a name="BKMK_ConditionOperators"></a>   
## <a name="condition-operators-for-hierarchical-data"></a>Operadores de condición para datos jerárquicos  
 Use los siguientes operadores para establecer condiciones para consultar datos jerárquicos.  
  
|FetchXML|ConditionOperator|Descripción|  
|--------------|-----------------------|-----------------|  
|`above`|`Above`|Devuelve todos los registros en la línea de ascendencia jerárquica del registro al que se hace referencia.|  
|`eq-or-above`|`AboveOrEqual`|Devuelve el registro al que se hace referencia y todos los registros sobre éste en la jerarquía.|  
|`under`|`Under`|Devuelve todos los registros secundarios por debajo del registro al que se hace referencia en la jerarquía.|  
|`eq-or-under`|`UnderOrEqual`|Devuelve el registro al que se hace referencia y todos los registros secundarios por debajo de éste en la jerarquía.|  
|`not-under`|`NotUnder`|Devuelve todos los registros que no están por debajo del registro al que se hace referencia en la jerarquía.|  
|`eq-owneduseroruserhierarchy`|`OwnedByMeOrMyReports`|Cuando se usan modelos de seguridad jerárquicos, es igual al usuario actual o la jerarquía de subordinados del usuario|  
|`eq-useroruserhierarchyandteams`|`OwnedByMeOrMyReportsAndTeams`|Cuando se usan modelos de seguridad jerárquicos, es igual al usuario actual y sus equipos o la jerarquía de subordinados del usuario y sus equipos|  
  
### <a name="recursion-limits-when-querying-hierarchical-data"></a>Límites de la recursión al consultar datos jerárquicos  
 Dado que la consulta de datos jerárquicos puede emplear muchos recursos, hay un límite predeterminado de 100 condiciones permitidas de recursiones para consultas jerárquicas utilizando los operadores de condición `Above`, `AboveOrEqual`, `Under`, `UnderOrEqual`, y `NotUnder`.  
  
 `OwnedByMeOrMyReports` y `OwnedByMeOrMyReportsAndTeams` son operadores de condición de seguridad jerárquica que dependen de la configuración de **Profundidad de jerarquía** que se encuentra en **Configuración** > **Seguridad** > **Seguridad de jerarquía**. El valor de este ajuste se almacena en el atributo `Organization.MaxDepthForHierarchicalSecurityModel`.  
  
<a name="BKMK_ChildCountAggregate"></a>   
## <a name="retrieve-the-number-of-hierarchically-related-child-records"></a>Recuperar el número de registros secundarios relacionados jerárquicamente  
 Use el atributo `rowaggregate` en una consulta basada en FetchXML para recuperar el número de registros secundarios relacionados jerárquicamente. Cuando este valor se establece en `CountChildren` un valor que incluye el número total de registros secundarios para el registro se incluye en la <xref:Microsoft.Xrm.Sdk.EntityCollection>. Por ejemplo, la siguiente consulta incluirá un valor de agregado de `AccountChildren` que representa el número de registros de cuentas secundarios en la relación jerárquica donde el parámetro `{0}` representa el `AccountId` del registro primario.  
  
```xml  
<fetch distinct='false' no-lock='false' mapping='logical'>  
  <entity name='account'>  
    <attribute name='name' />  
    <attribute name='accountid' />  
    <attribute name='accountid' rowaggregate='CountChildren' alias='AccountChildren'/>  
    <filter type='and'>  
      <condition attribute='accountid' operator='under' value='{0}' />  
    </filter>  
  </entity>  
</fetch>  
  
```  
  
> [!NOTE]
>  El valor agregado devuelto representa todos los registros secundarios, incluidos aquellos a los que el usuario no tenga acceso de lectura.  
  
 
