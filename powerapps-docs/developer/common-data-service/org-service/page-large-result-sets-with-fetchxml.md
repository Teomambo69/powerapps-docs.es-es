---
title: Paginar grandes conjuntos de resultados con FetchXML (Common Data Service para aplicaciones) | Documentos de Microsoft
description: Lea cómo puede paginar los resultados de una consulta FetchXML mediante la cookie de paginación.
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
# <a name="page-large-result-sets-with-fetchxml"></a>Páginar grandes conjuntos de resultados con FetchXML

Puede numerar los resultados de una consulta de FetchXML mediante la cookie de paginación. La cookie de paginación es una característica de rendimiento que hace que la paginación de la aplicación sea más rápida para conjuntos de datos muy extensos. Cuando consulte un conjunto de registros, el resultado contendrá un valor para la cookie de paginación. Para un mejor rendimiento, puede pasar ese valor cuando recupere el siguiente conjunto de registros.  
  
 FetchXML y <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> usan formatos diferentes para las cookies de paginación. Si convierte de un formato de consulta a otro sí mediante el mensaje <xref:Microsoft.Crm.Sdk.Messages.FetchXmlToQueryExpressionRequest> o el mensaje <xref:Microsoft.Crm.Sdk.Messages.QueryExpressionToFetchXmlRequest>, se omite el valor de la cookie de paginación. Además, si solicita páginas no consecutivas, se omite el valor de la cookie de paginación.  
  
 Cuando use la cookie de paginación con FetchXML, asegúrese de usar la codificación correcta. El siguiente ejemplo muestra la codificación correcta cuando se usa la cookie de paginación con FetchXML:  
  
```csharp  
strQueryXML = @"  
<fetch mapping='logical' paging-cookie='&lt;cookie page=&quot;1&quot;&gt;&lt;accountid last=&quot;{E062B974-7F8D-DC11-9048-0003FF27AC3B}&quot; first=&quot;{60B934EF-798D-DC11-9048-0003FF27AC3B}&quot;/&gt;&lt;/cookie&gt;' page='2' count='2'>  
 <entity name='account'>  
  <all-attributes/>  
 </entity>  
</fetch>";  
```  
  
## <a name="fetchxml-and-the-paging-cookie-example"></a>FetchXML y el ejemplo de cookie de paginación  
 El siguiente ejemplo muestra cómo usar la cookie de paginación con una consulta FetchXML. Para ver el código de ejemplo completo, consulte [Ejemplo: Usar FetchXML con una cookie de paginación](samples/use-fetchxml-paging-cookie.md).  
  
```csharp
// Define the fetch attributes.
// Set the number of records per page to retrieve.
int fetchCount = 3;
// Initialize the page number.
int pageNumber = 1;
// Initialize the number of records.
int recordCount = 0;
// Specify the current paging cookie. For retrieving the first page, 
// pagingCookie should be null.
string pagingCookie = null;

// Create the FetchXml string for retrieving all child accounts to a parent account.
// This fetch query is using 1 placeholder to specify the parent account id 
// for filtering out required accounts. Filter query is optional.
// Fetch query also includes optional order criteria that, in this case, is used 
// to order the results in ascending order on the name data column.
string fetchXml = string.Format(@"<fetch version='1.0' 
                                mapping='logical' 
                                output-format='xml-platform'>
                                <entity name='account'>
                                    <attribute name='name' />
                                    <attribute name='emailaddress1' />
                                    <order attribute='name' descending='false'/>
                                    <filter type='and'>
                            <condition attribute='parentaccountid' 
                                            operator='eq' value='{0}' uiname='' uitype='' />
                                    </filter>
                                </entity>
                            </fetch>",
                                _parentAccountId);

Console.WriteLine("Retrieving data in pages\n"); 
Console.WriteLine("#\tAccount Name\t\t\tEmail Address");

while (true)
{
    // Build fetchXml string with the placeholders.
    string xml = CreateXml(fetchXml, pagingCookie, pageNumber, fetchCount);

    // Excute the fetch query and get the xml result.
    RetrieveMultipleRequest fetchRequest1 = new RetrieveMultipleRequest
    {
        Query = new FetchExpression(xml)
    };

    EntityCollection returnCollection = ((RetrieveMultipleResponse)_service.Execute(fetchRequest1)).EntityCollection;
    
    foreach (var c in returnCollection.Entities)
    {
        System.Console.WriteLine("{0}.\t{1}\t\t{2}", ++recordCount, c.Attributes["name"], c.Attributes["emailaddress1"] );
    }                        
    
    // Check for morerecords, if it returns 1.
    if (returnCollection.MoreRecords)
    {
        Console.WriteLine("\n****************\nPage number {0}\n****************", pageNumber);
        Console.WriteLine("#\tAccount Name\t\t\tEmail Address");
        
        // Increment the page number to retrieve the next page.
        pageNumber++;

        // Set the paging cookie to the paging cookie returned from current results.                            
        pagingCookie = returnCollection.PagingCookie;
    }
    else
    {
        // If no more records in the result nodes, exit the loop.
        break;
    }
}
```
  
### <a name="see-also"></a>Vea también  
 [Ejemplo: Usar FetchXML con una cookie de paginación](samples/use-fetchxml-paging-cookie.md)   
 [Crear consultas con FetchXML](/dynamics365/customer-engagement/developer/org-service/build-queries-fetchxml)   
 [Fecha fiscal y operadores de consultas de fecha y hora más antiguo de en FetchXML](../use-fetchxml-fiscal-date-older-datetime-query-operators.md)   
 [Usar FetchXML](../use-fetchxml-construct-query.md)   
 [Conjuntos de resultados grandes de página con QueryExpression](page-large-result-sets-with-queryexpression.md)
