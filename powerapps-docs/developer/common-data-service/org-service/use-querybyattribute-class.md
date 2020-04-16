---
title: Usar la clase QueryByAttribute (Common Data Service) | Microsoft Docs
description: Ouede usar la clase QueryByAttribute para crear consultas que prueben un conjunto de atributos con un conjunto de valores
ms.custom: ''
ms.date: 05/03/2019
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
ms.openlocfilehash: a4eefba47dcda493086090f5d5cbde9416ea18f7
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155432"
---
# <a name="use-the-querybyattribute-class"></a>Usar la clase QueryByAttribute

Puede usar la clase <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> para crear consultas que prueben un conjunto de atributos con un conjunto de valores. Use esta clase con el método de <xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> o de <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest>. .
  
 La siguiente tabla enumera las propiedades que puede definir para crear una expresión de consulta mediante la clase <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute>.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute.EntityName>|Especifica qué tipo de entidad se va a recuperar. Una expresión de consulta solo puede recuperar una colección de un tipo de entidad. También puede utilizar el constructor <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> para pasar este valor.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute.ColumnSet>|Especifica el conjunto de atributos (columnas) que se va a recuperar.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute.Attributes>|Especifica el conjunto de atributos seleccionados en la consulta.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute.Values>|Especifica los valores de atributo a buscar cuando se ejecuta la consulta.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute.Orders>|Especifica el orden en que los registros se devuelven desde la consulta.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute.PageInfo>|Especifica el número de páginas y el número de registros por página devueltos por la consulta.|  
  
 El siguiente ejemplo del código muestra cómo usar la clase de `QueryByAttribute`.  
  
```csharp  
//  Create query using querybyattribute      
QueryByAttribute querybyexpression = new QueryByAttribute("account");      
querybyexpression.ColumnSet = new ColumnSet("name", "address1_city", "emailaddress1");  
  
//  Attribute to query      
querybyexpression.Attributes.AddRange("address1_city");  
  
//  Value of queried attribute to return      
querybyexpression.Values.AddRange("Detroit");      
  
//  Query passed to the service proxy      
EntityCollection retrieved = _serviceProxy.RetrieveMultiple(querybyexpression);     
  
//  Iterate through returned collection      
foreach (var c in retrieved.Entities)      
{  
      System.Console.WriteLine("Name: " + c.Attributes["name"]);  
      System.Console.WriteLine("Address: " + c.Attributes["address1_city"]);        
      System.Console.WriteLine("E-mail: " + c.Attributes["emailaddress1"]);      
}  
  
```  
  
### <a name="see-also"></a>Vea también  
 [Crear consultas con QueryExpression](build-queries-with-queryexpression.md)   
 <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute>