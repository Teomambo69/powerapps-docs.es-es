---
title: Conjuntos de resultados grandes de página con QueryExpression (Common Data Service) | Microsoft Docs
description: Use la característica de la cookie de paginación para crear la paginación en una aplicación más rápida para conjuntos de datos de gran tamaño. La característica está disponible con las consultas FetchXML y QueryExpression
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
ms.openlocfilehash: f518f8b47347399d3670b89f67db8978f591430c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749542"
---
# <a name="page-large-result-sets-with-queryexpression"></a>Conjuntos de resultados grandes de página con QueryExpression

En Common Data Service, puede usar la característica de la cookie de paginación para crear la paginación en una aplicación más rápida para conjuntos de datos de gran tamaño. La característica está disponible con las consultas FetchXML y <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>. Cuando se usa la característica de la cookie de paginación para consultar un conjunto de registros, el resultado contiene un valor para la cookie de la paginación. Para mejorar el rendimiento del sistema, puede pasar ese valor al recuperar el siguiente conjunto de registros.  
  
 <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> y FetchXML usan formatos diferentes para las cookies de paginación. Si convierte de un formato de consulta a otro sí mediante el mensaje <xref:Microsoft.Crm.Sdk.Messages.QueryExpressionToFetchXmlRequest> o el mensaje <xref:Microsoft.Crm.Sdk.Messages.FetchXmlToQueryExpressionRequest>, se omite el valor de la cookie de paginación. Además, si solicita páginas no consecutivas, se omite el valor de la cookie de paginación.  
  
<a name="QueryExpression"></a>   
## <a name="using-a-paging-cookie-with-queryexpression"></a>Mediante una cookie de la paginación con QueryExpression  
 El siguiente ejemplo muestra cómo usar la cookie de paginación con una expresión de consultas. Para ver el código de ejemplo completo, consulte [Ejemplo: Usar QueryExpression con una cookie de paginación](../org-service/samples/use-queryexpression-with-a-paging-cookie.md).  
  
```csharp
// Query using the paging cookie.
// Define the paging attributes.
// The number of records per page to retrieve.
int queryCount = 3;

// Initialize the page number.
int pageNumber = 1;

// Initialize the number of records.
int recordCount = 0;

// Define the condition expression for retrieving records.
ConditionExpression pagecondition = new ConditionExpression();
pagecondition.AttributeName = "parentaccountid";
pagecondition.Operator = ConditionOperator.Equal;
pagecondition.Values.Add(_parentAccountId);

// Define the order expression to retrieve the records.
OrderExpression order = new OrderExpression();
order.AttributeName = "name";
order.OrderType = OrderType.Ascending;

// Create the query expression and add condition.
QueryExpression pagequery = new QueryExpression();
pagequery.EntityName = "account";
pagequery.Criteria.AddCondition(pagecondition);
pagequery.Orders.Add(order);
pagequery.ColumnSet.AddColumns("name", "emailaddress1");                   

// Assign the pageinfo properties to the query expression.
pagequery.PageInfo = new PagingInfo();
pagequery.PageInfo.Count = queryCount;
pagequery.PageInfo.PageNumber = pageNumber;

// The current paging cookie. When retrieving the first page, 
// pagingCookie should be null.
pagequery.PageInfo.PagingCookie = null;
Console.WriteLine("Retrieving sample account records in pages...\n");
Console.WriteLine("#\tAccount Name\t\tEmail Address"); 

while (true)
{
    // Retrieve the page.
    EntityCollection results = _serviceProxy.RetrieveMultiple(pagequery);
    if (results.Entities != null)
    {
        // Retrieve all records from the result set.
        foreach (Account acct in results.Entities)
        {
            Console.WriteLine("{0}.\t{1}\t{2}", ++recordCount, acct.Name,
                               acct.EMailAddress1);
        }
    }

    // Check for more records, if it returns true.
    if (results.MoreRecords)
    {
        Console.WriteLine("\n****************\nPage number {0}\n****************", pagequery.PageInfo.PageNumber);
        Console.WriteLine("#\tAccount Name\t\tEmail Address");

        // Increment the page number to retrieve the next page.
        pagequery.PageInfo.PageNumber++;
        
        // Set the paging cookie to the paging cookie returned from current results.
        pagequery.PageInfo.PagingCookie = results.PagingCookie;
    }
    else
    {
        // If no more records are in the result nodes, exit the loop.
        break;
    }
}
```

### <a name="see-also"></a>Vea también  
 [Generar consultas con QueryExpression](build-queries-with-queryexpression.md)   
 [Ejemplo: usar QueryExpression con una cookie de paginación](samples/use-queryexpression-with-a-paging-cookie.md)   
 [Ejemplo: recuperar con relación uno a varios](/dynamics365/customer-engagement/developer/retrieve-with-one-to-many-relationship)   
 [Usar la clase QueryExpression](use-queryexpression-class.md)   
 [Paginar grandes conjuntos de resultados con FetchXML](page-large-result-sets-with-fetchxml.md)