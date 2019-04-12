---
title: Usar la clase ConditionExpression (Common Data Service) | Microsoft Docs
description: 'Conozca cómo puede utilizar la clase ConditionExpression para comparar un atributo con un valor o conjunto de valores utilizando un operador, como &quot;igual a&quot; o &quot;mayor que&quot;.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-the-conditionexpression-class"></a>Usar la clase ConditionExpression

En Common Data Service, puede usar la clase de <xref:Microsoft.Xrm.Sdk.Query.ConditionExpression> para comparar un atributo con un valor o un conjunto de valores al usar un operador, como "igual a" o "mayor que". La clase de `ConditionExpression` le permite pasar expresiones de condición como parámetros a otras clases, como <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> y <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>.  
  
 La siguiente tabla enumera las propiedades que puede definir para crear una condición que usa la clase de `ConditionExpression`.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|<xref:Microsoft.Xrm.Sdk.Query.ConditionExpression.AttributeName>|Especifica el nombre lógico del atributo en la expresión de condición.|  
|<xref:Microsoft.Xrm.Sdk.Query.ConditionExpression.Operator>|Especifica el operador de la condición. Esto se configura mediante la enumeración de <xref:Microsoft.Xrm.Sdk.Query.ConditionOperator>.|  
|<xref:Microsoft.Xrm.Sdk.Query.ConditionExpression.Values>|Especifica los valores del atributo.|  
  
 Al usar el método de <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.AddCondition(Microsoft.Xrm.Sdk.Query.ConditionExpression)> (o el constructor para <xref:Microsoft.Xrm.Sdk.Query.ConditionExpression>), es importante comprender si la matriz se agrega como varios valores o como una matriz.  
  
 El siguiente ejemplo del código muestra dos resultados diferentes en función de cómo se usa la matriz.  
  
```csharp  
string[] values = new string[] { "Value1", "Value2" };  
ConditionExpression c = new ConditionExpression("name", ConditionOperator.In, values);  
Console.WriteLine(c.Values.Count); //This will output 2   
string[] values = new string[] { "Value1", "Value2" }object value = values;  
ConditionExpression c = new ConditionExpression("name", ConditionOperator.In, value);  
Console.WriteLine(c.Values.Count); //This will output 1  
  
```  
  
 En algunos casos, es necesario convertir a `object[]` o `object`, en función del comportamiento deseado.  
  
 Al crear una condición que compare un valor de atributo con una enumeración, como un código de estado, debe usar el método de `ToString` para convertir el valor de una cadena.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo del código muestra cómo usar la clase de `ConditionExpression`.  
  
```csharp  
  
//  Query using ConditionExpression    
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
Console.WriteLine();    
Console.WriteLine("Query using Query Expression with ConditionExpression and FilterExpression");    
Console.WriteLine("---------------------------------------");    
foreach (var a in result1.Entities)    
{  
      Console.WriteLine("Name: " + a.Attributes["firstname"] + " " + a.Attributes["lastname"]);    
}    
Console.WriteLine("---------------------------------------");  
```  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo del código muestra cómo usar la clase de `ConditionExpression` a fin de realizar una prueba para el estado inactivo.  
  
```csharp  
  
ConditionExpression condition3 = new ConditionExpression();  
condition3.AttributeName = "statecode";  
condition3.Operator = ConditionOperator.Equal;  
condition3.Values.Add(AccountState.Active);  
  
```  
  
### <a name="see-also"></a>Vea también  
 [Crear consultas](build-queries-with-queryexpression.md)   
 [Crear consultas con QueryExpression](build-queries-with-queryexpression.md)   
 [Usar la clase FilterExpression](use-filterexpression-class.md)   
 <xref:Microsoft.Xrm.Sdk.Query.ConditionExpression>