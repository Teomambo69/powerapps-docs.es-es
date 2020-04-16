---
title: Comprobar un valor nulo (Common Data Service) | Microsoft Docs
description: Este ejemplo muestra cómo probar un valor null usando las clases FilterExpression y QueryByAttribute
ms.custom: ''
ms.date: 05/03/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1db91713c281edc5d7c41f72d0fc1740c76c6a2b
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155468"
---
# <a name="test-for-a-null-value"></a>Comprobar valores nulos

En el siguiente ejemplo de código se muestra cómo probar un valor nulo mediante las clases <xref:Microsoft.Xrm.Sdk.Query.FilterExpression> y <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute>.  
  
## <a name="example"></a>Ejemplo  
 Use este código para probar la igualdad mediante la clase <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>.  
  
```csharp  
FilterExpression null_filter = new FilterExpression(LogicalOperator.And);   
null_filter.FilterOperator = LogicalOperator.And;   
null_filter.AddCondition("leadid", ConditionOperator.Null);  
  
```  
  
## <a name="example"></a>Ejemplo  
 Use este código para probar la diferencia mediante la clase <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>.  
  
```csharp  
  
FilterExpression filter = new FilterExpression(LogicalOperator.And);   
filter.FilterOperator = LogicalOperator.And;   
filter.AddCondition("leadid", ConditionOperator.NotNull);  
```  
  
## <a name="example"></a>Ejemplo  
 Use este código para probar la igualdad mediante la clase <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute>.  
  
```csharp  
  
QueryByAttribute qba = new QueryByAttribute("account");   
qba.ColumnSet = new ColumnSet("name","address1_stateorprovince");   
qba.AddAttributeValue("donotfax", null);  
```  
  
### <a name="see-also"></a>Vea también  
 [Crear consultas con QueryExpression](build-queries-with-queryexpression.md)   
 [Páginar grandes conjuntos de resultados con FetchXML](page-large-result-sets-with-fetchxml.md)
