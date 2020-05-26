---
title: Usar la clase QueryExpression (Common Data Service) | Microsoft Docs
description: Utilice la clase QueryExpression para crear consultas complejas para uso con el método IOrganizationService.QueryBase o el mensaje RetrieveMultipleRequest.
ms.custom: ''
ms.date: 04/17/2020
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
ms.openlocfilehash: 0b405e76323300522e01956ea3eacbe7b2596f50
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275784"
---
# <a name="use-the-queryexpression-class"></a>Usar la clase QueryExpression

En Common Data Service puede usar la clase <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> para construir consultas complejas para su uso con el <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> el método o el mensaje <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest>. Se pueden configurar los parámetros de la consulta en <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> con las clases <xref:Microsoft.Xrm.Sdk.Query.ConditionExpression>, <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> y <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>.  
  
 La clase <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> permite crear consultas complejas. La clase <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> está diseñada para ser una forma simple de búsqueda para las entidades en las que los atributos coinciden con los valores especificados.  
  
<a name="record_count"></a>   
## <a name="record-count"></a>Recuento de registros  
 Para averiguar cuántos registros devuelve la consulta, establezca la propiedad <xref:Microsoft.Xrm.Sdk.Query.PagingInfo.ReturnTotalRecordCount> en true antes de ejecutar la consulta. Al hacerlo, se establecerá <xref:Microsoft.Xrm.Sdk.EntityCollection.TotalRecordCount>. De lo contrario, esta valor será -1.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra cómo usar la clase <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>.  
  
```csharp  
//  Query using ConditionExpression and FilterExpression  
ConditionExpression condition1 = new ConditionExpression();  
condition1.AttributeName = "lastname";  
condition1.Operator = ConditionOperator.Equal;  
condition1.Values.Add("Brown");              
  
FilterExpression filter1 = new FilterExpression();  
filter1.Conditions.Add(condition1);  
  
QueryExpression query = new QueryExpression("contact");  
query.ColumnSet.AddColumns("firstname", "lastname");  
query.Criteria.AddFilter(filter1);  
  
EntityCollection result1 = _serviceProxy.RetrieveMultiple(query);  
Console.WriteLine();Console.WriteLine("Query using Query Expression with ConditionExpression and FilterExpression");  
Console.WriteLine("---------------------------------------");  
foreach (var a in result1.Entities)  
{  
    Console.WriteLine("Name: " + a.Attributes["firstname"] + " " + a.Attributes["lastname"]);  
}  
Console.WriteLine("---------------------------------------");  
```  
## <a name="use-sql-hints-in-a-query"></a>Usar sugerencias en una consulta SQL

La clase <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> contiene una propiedad denominada <xref:Microsoft.Xrm.Sdk.Query.QueryExpression.QueryHints>. Al establecer esta propiedad en uno de los valores de cadena admitidos que se muestran a continuación, puede proporcionar una pista para el texto SQL generado que afecta la ejecución de la consulta.

|Valor de QueryHint | Opción y consulta de SQL Query |
|---------|---------|
|OptimizeForUnknown | Optimizar para desconocido|
|ForceOrder | Forzar orden |
|Volver a compilar | Volver a compilar |
|DisableRowGoal | use hint(‘Disable_Optimizer_RowGoal’) |
|EnableOptimizerHotfixes | use hint('ENABLE_QUERY_OPTIMIZER_HOTFIXES') |
|LoopJoin | Combinación de bucle |
|MergeJoin | Combinación de mezcla |
|HashJoin | Combinación hash |
|NO_PERFORMANCE_SPOOL | NO_PERFORMANCE_SPOOL |
|MaxRecursion | Número MAXRECURSION |

Más información: [Sugerencias (Transact-SQL) - Consulta](https://docs.microsoft.com/sql/t-sql/queries/hints-transact-sql-query)

### <a name="see-also"></a>Vea también  
 [Generar consultas con QueryExpression](build-queries-with-queryexpression.md)   
 [Utilizar la clase ColumnSet](use-the-columnset-class.md)   
 [Uso de la clase ConditionExpression](use-conditionexpression-class.md)   
 [Usar la clase FilterExpression](use-filterexpression-class.md)   
 <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>