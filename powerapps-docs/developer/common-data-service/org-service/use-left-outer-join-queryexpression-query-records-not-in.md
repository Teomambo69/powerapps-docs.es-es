---
title: Usar una combinación externa izquierda en QueryExpression para consultar los registros &quot;no en&quot; (Common Data Service) | Microsoft Docs
description: Lea cómo usar una combinación externa izquierda mediante la clase QueryExpression para realizar una consulta que aplique un filtro a la tabla combinada y cree una consulta para buscar registros &quot;no incluidos en&quot; un conjunto
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: 009621e7e749255d64eae851629e5d7f0bd61e79
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749836"
---
# <a name="use-a-left-outer-join-in-queryexpression-to-query-for-records-not-in"></a>Usar una combinación externa izquierda en QueryExpression para consultar los registros "no en"

Puede usar una combinación externa izquierda mediante el uso de la clase <xref:Microsoft.Crm.Sdk.Messages.SearchByKeywordsKbArticleRequest.QueryExpression> para realizar una consulta que filtra la tabla combinada, por ejemplo, para buscar todos los contactos que no tuvieron ninguna actividad de campaña en los últimos dos meses. Otro uso común de este tipo de una consulta es buscar los registros que "no están en" un conjunto, como en estos casos:  
  
- Buscar todos los clientes potenciales que no tienen ninguna tarea  
  
- Buscar todas las cuentas que no tienen ningún contacto  
  
- Buscar todos los clientes potenciales que tienen una o varias tareas  
  
  Una combinación externa izquierda devuelve todas las filas que satisfacen la combinación de la primera entrada con la segunda entrada. También devuelve las filas de la primera entrada que no tenían ninguna fila coincidente en la segunda entrada. Las filas no coincidentes en la segunda entrada se devuelven como valores nulos.  
  
  Para realizar una combinación externa izquierda en `QueryExpression`, puede usar el atributo `entityname` como un operador de condición. El atributo `entityname` es válido en condiciones, filtros y filtros anidados.  
  
## <a name="find-all-leads-that-have-no-tasks-using-an-alias"></a>Buscar todos los clientes potenciales que no tienen tareas, mediante el uso de un alias  

El siguiente ejemplo muestra cómo crear esta consulta:  
  
```csharp
QueryExpression qx = new QueryExpression("lead");  
qx.ColumnSet.AddColumn("subject");  
  
LinkEntity link = qx.AddLink("task", "leadid", "regardingobjectid", JoinOperator.LeftOuter);  
link.Columns.AddColumn("subject");  
link.EntityAlias = "tsk";  
  
qx.Criteria = new FilterExpression();  
qx.Criteria.AddCondition("tsk", "activityid", ConditionOperator.Null);
```  
  
Esto equivale al código SQL siguiente.  
  
```sql
SELECT lead.FullName  
FROM Leads as lead  
LEFT OUTER JOIN Tasks as ab  
ON (lead.leadId  =  ab.RegardingObjectId)  
WHERE ab.RegardingObjectId is null
```  
  
### <a name="see-also"></a>Vea también  
 [Crear consultas con QueryExpression](build-queries-with-queryexpression.md)   
 [Comprobar un valor nulo](/dynamics365/customer-engagement/developer/test-null-value)   
 [Usar la clase QueryExpression](use-queryexpression-class.md)   
 [Usar la clase QueryByAttribute](use-querybyattribute-class.md)