---
title: Usar la clase QueryExpression (Common Data Service) | Microsoft Docs
description: Utilice la clase QueryExpression para crear consultas complejas para uso con el método IOrganizationService.QueryBase o el mensaje RetrieveMultipleRequest.
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
ms.openlocfilehash: 79b8f500bb6448a0272df627e813cf518159c817
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155428"
---
# <a name="use-the-queryexpression-class"></a>Usar la clase QueryExpression

En Common Data Service puede usar la clase <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> para construir consultas complejas para su uso con el <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> el método o el mensaje <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest>. Se pueden configurar los parámetros de la consulta en <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> con las clases <xref:Microsoft.Xrm.Sdk.Query.ConditionExpression>, <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> y <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>.  
  
 La clase <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> permite crear consultas complejas. La clase <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> está diseñada para ser una forma simple de búsqueda para las entidades en las que los atributos coinciden con los valores especificados.  
  
 En la siguiente tabla se enumeran las propiedades que se definen para crear una expresión de consulta.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.EntityName>|Especifica que tipo de entidad se va a recuperar. Una expresión de consulta solo puede recuperar una colección de un tipo de entidad.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.ColumnSet>|Especifica el conjunto de atributos (columnas) que se va a recuperar.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.Criteria>|Especifica complejas expresiones de filtro condicionales y lógicas que filtran los resultados de la consulta.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.Distinct>|Especifica si los resultados de la consulta contienen registros duplicados.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.LinkEntities>|Especifica los vínculos entre varios tipos de entidad.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.Orders>|Especifica el orden en que los registros se devuelven desde la consulta.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.PageInfo>|Especifica el número de páginas y el número de registros por página devueltos por la consulta.|  
  
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
  
### <a name="see-also"></a>Vea también  
 [Generar consultas con QueryExpression](build-queries-with-queryexpression.md)   
 [Utilizar la clase ColumnSet](use-the-columnset-class.md)   
 [Uso de la clase ConditionExpression](use-conditionexpression-class.md)   
 [Usar la clase FilterExpression](use-filterexpression-class.md)   
 <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>