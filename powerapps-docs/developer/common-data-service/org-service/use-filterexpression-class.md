---
title: Usar la clase FilterExpression (Common Data Service) | Microsoft Docs
description: Conozca cómo puede utilizar la clase FilterExpression para crear una consulta que exprese múltiples condiciones
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
ms.openlocfilehash: ba077e5bf9c1f1f464e8cc71594d30684efc0824
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749838"
---
# <a name="use-the-filterexpression-class"></a>Usar la clase FilterExpression

En Common Data Service y , puede usar la clase <xref:Microsoft.Xrm.Sdk.Query.FilterExpression> para crear una consulta que exprese varias condiciones. Por ejemplo, puede crear una expresión de consulta que sea equivalente a una instrucción SQL como `([FirstName] = 'Joe' OR [FirstName] = 'John') AND [City] = 'Redmond'`.  
  
 La tabla siguiente enumera las propiedades de la clase <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>.  
  
|||  
|-|-|  
|Propiedad|Descripción|  
|<xref:Microsoft.Xrm.Sdk.Query.FilterExpression.Conditions>|Obtiene o establece expresiones de condición que incluyen atributos, operadores de condición y valores de atributos.|  
|<xref:Microsoft.Xrm.Sdk.Query.FilterExpression.FilterOperator>|Obtiene o establece operadores de filtros lógicos `AND/OR`. Esto se configura mediante la enumeración <xref:Microsoft.Xrm.Sdk.Query.LogicalOperator>.|  
|<xref:Microsoft.Xrm.Sdk.Query.FilterExpression.Filters>|Obtiene o establece una jerarquía de expresiones de filtro condicionales y lógicas que filtran los resultados de la consulta.|  
|<xref:Microsoft.Xrm.Sdk.Query.FilterExpression.IsQuickFindFilter>|Obtiene o establece un valor que indica si expresión forma parte de una consulta de búsqueda rápida.|  
  
 La clase <xref:Microsoft.Xrm.Sdk.Query.FilterExpression> también incluye varios métodos auxiliares que facilitan la creación de consultas. La propiedad <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>.<xref:Microsoft.Xrm.Sdk.Query.ConditionExpression> el método agrega una <xref:Microsoft.Xrm.Sdk.Query.ConditionExpression> a la propiedad <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.Conditions> para la <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>, reduciendo la cantidad de código necesario para construir la expresión de condición. La propiedad <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.AddFilter*>.<xref:Microsoft.Xrm.Sdk.Query.LogicalOperator> el método añade un nuevo filtro a la propiedad <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.Filters> de la clase <xref:Microsoft.Xrm.Sdk.Query.FilterExpression> .  
  
<a name="example"></a>   

## <a name="filter-expression-example"></a>Ejemplo de expresión de filtro  

 El siguiente ejemplo del código muestra cómo usar la clase de <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>.  
  
```csharp  
QueryExpression query = new QueryExpression("contact");   
query.ColumnSet.AddColumns("firstname", "lastname", "address1_city");   
  
query.Criteria = new FilterExpression();   
query.Criteria.AddCondition("address1_city", ConditionOperator.Equal, "Redmond");   
  
FilterExpression childFilter = query.Criteria.AddFilter(LogicalOperator.Or);   
childFilter.AddCondition("lastname", ConditionOperator.Equal, "Tharpe");   
childFilter.AddCondition("lastname", ConditionOperator.Equal, "Brown");   
  
// Pass query to service proxy   
EntityCollection results = _serviceProxy.RetrieveMultiple(query);   
Console.WriteLine();   
Console.WriteLine("Query using QE with multiple conditions and filters");   
Console.WriteLine("---------------------------------------");   
  
// Print results   
foreach (var a in results.Entities)   
{   
Console.WriteLine("Name: {0} {1}", a.GetAttributeValue<string>("firstname"), a.GetAttributeValue<string>("lastname"));   
Console.WriteLine("City: {0}", a.GetAttributeValue<string>("address1_city"));   
}   
Console.WriteLine("---------------------------------------");  
```  
  
<a name="quickfindfilter"></a> 
  
## <a name="about-the-isquickfindfilter-property"></a>Acerca de la propiedad IsQuickFindFilter  

 Puede usar el método <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>.<xref:Microsoft.Xrm.Sdk.Query.FilterExpression.IsQuickFindFilter> propiedad, que es análoga a la `isquickfindfields` atributo que existe en el nodo `filter` Fetch XML. Cuando se guarda una consulta de Fetch, se almacena en la propiedad `IsQuickFind` de las entidades `SavedQuery` y `UserQuery`. La propiedad <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.IsQuickFindFilter> se agregó para proporcionar coherencia entre las consultas FetchXML y las expresiones de consulta.  
  
 Las siguientes reglas se aplican a la propiedad <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.IsQuickFindFilter>:  
  
-   Este campo solo se puede establecer en `true` para las expresiones de filtro con un operador lógico de tipo <xref:Microsoft.Xrm.Sdk.Query.LogicalOperator>.`Or`. Si se establece en expresiones con un operador lógico de tipo <xref:Microsoft.Xrm.Sdk.Query.LogicalOperator>.`And`, la propiedad <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.IsQuickFindFilter> se omite.  
  
-   Solo se puede establecer una expresión de filtro en una jerarquía de expresiones de filtro con <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.IsQuickFindFilter> = **true**. Si se encuentra más de una, se genera una excepción.  
  
-   Si una expresión de filtro tiene la propiedad <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.IsQuickFindFilter> establecida en **true**, no puede tener ninguna propiedad de expresión de filtro secundaria, solo puede tener propiedades <xref:Microsoft.Xrm.Sdk.Query.ConditionExpression>. Si se agrega una expresión de filtro secundaria, se genera una excepción.  
  
-   Todas las expresiones de condición relacionadas con una expresión de filtro con la propiedad <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.IsQuickFindFilter> establecida en **true** deben ser condiciones con un solo valor no nulo. Es decir, teniendo en cuenta que una condición está compuesta por atributo, operador y valor, solo se admiten las condiciones cuya propiedad de valor sea un solo valor que no es **null**. Además, los únicos operadores de condición admitidos en estas expresiones de condición son los que funcionan con un solo valor que no es nulo. Si se detecta un valor **null** o varios valores, se genera una excepción.  
  
### <a name="see-also"></a>Vea también  

 [Generar consultas con QueryExpression](build-queries-with-queryexpression.md)   
 [Usar una combinación externa izquierda en QueryExpression para consultar los registros "no en"](use-left-outer-join-queryexpression-query-records-not-in.md)   
 [Uso de la clase ConditionExpression](use-conditionexpression-class.md)   
 <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>