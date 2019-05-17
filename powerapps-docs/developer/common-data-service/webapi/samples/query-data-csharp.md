---
title: 'Ejemplo de datos de consulta de API web (C#) (Common Data Service) | Microsoft Docs'
description: 'Este ejemplo muestra cómo realizar solicitudes de consultas básicas mediante la API web y C# de Common Data Service'
ms.custom: ''
ms.date: 1/09/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 91183105-bc99-4e34-a1b3-1085e1a51f82
caps.latest.revision: 16
author: brandonsimons
ms.reviewer: susikka
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-query-data-sample-c"></a>Ejemplo de datos de consulta API (C#)

Este ejemplo muestra cómo realizar solicitudes de consultas básicas mediante la API web de Common Data Service con C#.  
  
> [!NOTE]
> Este ejemplo implementa las operaciones de Common Data Service y la salida de la consola detalladas en el [Ejemplo de consulta de datos en la API web](../web-api-query-data-sample.md) y utiliza las construcciones comunes de C# que se describen en [Ejemplos de API web (C#)](../web-api-samples-csharp.md).  
  
<a name="bkmk_prerequisites"></a>

## <a name="prerequisites"></a>Requisitos previos

Los requisitos previos de todos los ejemplos en C# de la API web de Common Data Service se detallan en la sección [Requisitos previos](../web-api-samples-csharp.md#bkmk_prerequisites) del tema primario [Ejemplos de operaciones básicas de la API web (C#)](../web-api-samples-csharp.md).  
  
<a name="bkmk_runSample"></a>

## <a name="hpw-to-run-this-sample"></a>Cómo ejecutar este ejemplo
  
Vaya a [Ejemplo de datos de consulta de la API web (C#)](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23), clone o descargue el repositorio de ejemplos y extraiga su contenido en una carpeta local. Esta carpeta debe contener los siguientes archivos:  
  
|Archivo|Objetivo/descripción|  
|----------|--------------------------|  
|SampleProgram.cs|Contiene el código de origen primario para este ejemplo.|  
|App.config|El archivo de configuración de la aplicación, que contiene información de conexión con el servidor de Common Data Service con marcadores. Este archivo se comparte con todos los ejemplos de API web en el repositorio. Si configura la información de la conexión para un ejemplo, puede ejecutar los otros ejemplos con la misma configuración.|  
|SampleHelper.cs|Contiene el código auxiliar para ayudar a realizar tareas comunes, como la configuración de la aplicaciones, la autenticación y la administración de errores de respuestas `HTTP`. <br/>Este archivo se comparte con todos los ejemplos de API web en el repositorio. Contiene métodos auxiliares para administrar excepciones y el token OAuth. Consulte el ejemplo simple de la API web para obtener más información sobre los métodos de este archivo.| 
|SampleMethod.cs|Contiene todos los métodos que admiten el código de origen en el ejemplo. Las funciones que se usan en SampleProgram.cs se pueden definir en este archivo.| 
|QueryData.sln <br />QueryData.csproj <br />Packages.config <br />AssemblyInfo.cs|El proyecto, la configuración del paquete NuGet, y los archivos de información de ensamblado de la solución Visual Studio 2017 estándar para este ejemplo.|  
  
A continuación, use el procedimiento siguiente para ejecutar este servicio.  
  
1. Busque y haga doble clic en el archivo de la solución, QueryData.sln, para cargar la solución en Visual Studio. Cree la solución **QueryData**.  Debe descargar e instalar automáticamente todos los paquetes NuGet necesarios que faltan o deben actualizarse.
1. Edite el archivo de configuración, App.config, para especificar información de conexión para el servidor de Common Data Service.  
1. Ejecute el proyecto **QueryData** desde Visual Studio.  Todas las soluciones de ejemplo se configuran para ejecutarse en modo de depuración de forma predeterminada.  
  
<a name="bkmk_codeListing"></a>
  
## <a name="code-listing"></a>Lista de código

Vaya a [Ejemplos](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23) para descargar el ejemplo completo.
  
 `SampleProgram.cs`  
  
```csharp  
  
using Newtonsoft.Json.Linq;
using System;
using System.Collections.Generic;
using System.Configuration;
using System.Linq;
using System.Net;
using System.Net.Http;
using System.Net.Http.Headers;
using System.Text;
using System.Threading.Tasks;

namespace PowerApps.Samples
{
  public partial class SampleProgram
   {
     static void Main(string[] args)
      {
        try
         {
           //Get configuration data from App.config connectionStrings
           string connectionString = ConfigurationManager.ConnectionStrings["Connect"].ConnectionString;

            using (HttpClient client = SampleHelpers.GetHttpClient(
                    connectionString,
                    SampleHelpers.clientId,
                    SampleHelpers.redirectUrl,"v9.0"))
             {
               string queryOptions;  //select, expand and filter clauses
                                          //Entity properties to select in a request and display.
               string[] contactProperties = { "fullname", "jobtitle", "annualincome" };
               string[] accountProperties = { "name" };
               string[] taskProperties = { "subject", "description" };
               CreateRequireRecords(client);
                   
#region Selecting specific properties
// Basic query: Query using $select against a contact entity to get the properties you want.
// For performance best practice, always use $select, otherwise all properties are returned.

      Console.WriteLine("-- Basic Query --");
      queryOptions = "?$select=" + String.Join(",", contactProperties);

 //Request formatted values be returned (in addition to standard unformatted values).
HttpResponseMessage response = client.GetAsync(contact1Uri + queryOptions, HttpCompletionOption.ResponseHeadersRead).Result;
    if (response.IsSuccessStatusCode) //200
      {
         contact1 = JObject.Parse(response.Content.ReadAsStringAsync().Result);
         Console.WriteLine("Contact basic info:\n\tFullname: {0}\n\tJobtitle: {1}\n\tAnnualincome: {2} (unformatted)",
         contact1["fullname"], contact1["jobtitle"], contact1["annualincome"]);
         Console.WriteLine("\tAnnualincome: {0} (formatted)\n",
         contact1["annualincome@OData.Community.Display.V1.FormattedValue"]);
      }
   else
      {
        throw new Exception(string.Format("Failed to retrtieve specific properties", response.Content));

      }
 #endregion Selecting specific properties

 #region Using query functions
   // Filter criteria:
   // Applying filters to get targeted data.
   // 1) Using standard query functions (e.g.: contains, endswith, startswith)
   // 2) Using  query functions (e.g.: LastXhours, Last7Days, Today, Between, In, ...)
   // 3) Using filter operators and logical operators (e.g.: eq, ne, gt, and, or, etc…)
   // 4) Set precedence using parenthesis (e.g.: ((criteria1) and (criteria2)) or (criteria3)
   // For more info, see: https://msdn.microsoft.com/en-us/library/gg334767.aspx#bkmk_filter

      Console.WriteLine("-- Filter Criteria --");
      JObject collection;

    //Filter 1: Using standard query functions to filter results.  In this operation, we 
    //will query for all contacts with fullname containing the string "(sample)".
      string filter = @"&$filter=contains(fullname,'(sample)')";
      queryOptions = "?$select=" + String.Join(",", contactProperties) + filter;
      response = client.GetAsync("contacts" + queryOptions, HttpCompletionOption.ResponseHeadersRead).Result;
       if (response.IsSuccessStatusCode) //200
        {
          collection = JObject.Parse(response.Content.ReadAsStringAsync().Result);
          DisplayFormattedEntities("Contacts filtered by fullname containing '(sample)':",collection, contactProperties);
        }
      else
        {
          throw new Exception(string.Format("Failed to retrieve Contacts with fullname containing the string (sample)", response.Content));
        }

//Filter 2: Using  query functions to filter results. In this operation, we will query
//for all contacts that were created in the last hour. For complete list of CRM query  
//functions, see: https://msdn.microsoft.com/en-us/library/mt607843.aspx

       filter = "&$filter=Microsoft.Dynamics.CRM.LastXHours(PropertyName='createdon',PropertyValue='1')";
       queryOptions = "?$select=" + String.Join(",", contactProperties) + filter;
       response = client.GetAsync("contacts" + queryOptions, HttpCompletionOption.ResponseHeadersRead).Result;
       if (response.IsSuccessStatusCode) //200
         {
           collection = JObject.Parse(response.Content.ReadAsStringAsync().Result);
            DisplayFormattedEntities("Contacts that were created within the last 1hr:",collection, contactProperties);
         }
       else
         {
            throw new Exception(string.Format("Failed to retrieve Contacts that were created within the last 1hr", response.Content));
         }

  //Filter 3: Using operators. Building on the previous operation, we further limit
  //the results by the contact's income. For more info on standard filter operators, 
  //https://msdn.microsoft.com/en-us/library/gg334767.aspx#bkmk_filter

     filter = "&$filter=contains(fullname,'(sample)') and annualincome gt 55000";
     queryOptions = "?$select=" + String.Join(",", contactProperties) + filter;
     response = client.GetAsync("contacts" + queryOptions, HttpCompletionOption.ResponseHeadersRead).Result;
     if (response.IsSuccessStatusCode) //200
      {
         collection = JObject.Parse(response.Content.ReadAsStringAsync().Result);
         DisplayFormattedEntities("Contacts filtered by fullname and annualincome (<$55,000):",collection, contactProperties);
       }
     else
       {
          throw new Exception(string.Format("Failed to retrieve Contacts filtered by fullname and annual income < $55,000", response.Content)); 
       }

    //Filter 4: Set precedence using parenthesis. Continue building on the previous 
    //operation, we further limit results by job title. Parenthesis and the order of 
    //filter statements can impact results returned.

      filter = "&$filter=contains(fullname,'(sample)') and(contains(jobtitle, 'senior')" +
                    " or contains(jobtitle,'specialist')) and annualincome gt 55000";
      queryOptions = "?$select=" + String.Join(",", contactProperties) + filter;
      response = client.GetAsync("contacts" + queryOptions, HttpCompletionOption.ResponseHeadersRead).Result;
      if (response.IsSuccessStatusCode) //200
       {
          collection = JObject.Parse(response.Content.ReadAsStringAsync().Result);
          DisplayFormattedEntities("Contacts filtered by fullname, annualincome and jobtitle " +
                            "(Senior or Specialist):", collection, contactProperties);
       }
      else
        {
          throw new Exception(string.Format("Failed to retrieve Contacts filtered by fullname, annual income and jobtitle" + "(Senior or Specialist)", response.Content));
        }
 #endregion Using query functions

  #region Ordering and aliases
   //Results can be ordered in descending or ascending order.
       Console.WriteLine("\n-- Order Results --");
       filter = @"&$filter=contains(fullname,'(sample)') &$orderby=jobtitle asc, annualincome desc";
       queryOptions = "?$select=" + String.Join(",", contactProperties) + filter;
        response = client.GetAsync("contacts" + queryOptions, HttpCompletionOption.ResponseHeadersRead).Result;
        if (response.IsSuccessStatusCode) //200
          {
             collection = JObject.Parse(response.Content.ReadAsStringAsync().Result);
             DisplayFormattedEntities("Contacts ordered by jobtitle (Ascending) and annualincome (descending):",
                            collection, contactProperties);
           }
        else
          { 
            throw new Exception(string.Format("Failed to retrieve Contacts oredered by jobtitle (Ascending) and annual income (descending)", response.Content)); 
          }

//Parameterized aliases can be used as parameters in a query. These parameters can be used 
 //in $filter and $orderby options. Using the previous operation as basis, parameterizing the 
//query will give us the same results. For more info, see: 
//https://msdn.microsoft.com/en-us/library/gg309638.aspx#bkmk_passParametersToFunctions

      Console.WriteLine("\n-- Parameterized Aliases --");
      filter = "&$filter=contains(@p1,'(sample)') &$orderby=@p2 asc, " +
                        "@p3 desc&@p1=fullname&@p2=jobtitle&@p3=annualincome";
      queryOptions = "?$select=" + String.Join(",", contactProperties) + filter;
      response = client.GetAsync("contacts" + queryOptions, HttpCompletionOption.ResponseHeadersRead).Result;
      if (response.IsSuccessStatusCode) //200
                    {
                        collection = JObject.Parse(response.Content.ReadAsStringAsync().Result);
                        DisplayFormattedEntities("Contacts list using parameterized aliases:",
                            collection, contactProperties);
                    }
       else
           { 
             throw new Exception(string.Format("Failed to retrieve Contacts list using parameterized aliases", response.Content)); 
           }
 #endregion Ordering and aliases

#region Limit results
//To limit records returned, use the $top query option.  Specifying a limit number for $top 
 //returns at most that number of results per request. Extra results are ignored.
 //For more information, see: https://msdn.microsoft.com/en-us/library/gg334767.aspx#bkmk_limits
    
      Console.WriteLine("\n-- Top Results --");
      filter = "&$filter=contains(fullname,'(sample)')&$top=5";
      queryOptions = "?$select=" + String.Join(",", contactProperties) + filter;
      response = client.GetAsync("contacts" + queryOptions, HttpCompletionOption.ResponseHeadersRead).Result;
      if (response.IsSuccessStatusCode) //200
                    {
                        collection = JObject.Parse(response.Content.ReadAsStringAsync().Result);
                        DisplayFormattedEntities("Contacts top 5 results:", collection, contactProperties);
                    }
       else
         { 
           throw new Exception(string.Format("Failed to retrieve Contacts top 5 results", response.Content));
          }

 //Result count - count the number of results matching the filter criteria.
 //Tip: Use count together with the "odata.maxpagesize" to calculate the number of pages in
 //the query.  Note: CRM has a max record limit of 5000 records per response.
                    
Console.WriteLine("\n-- Result Count --");
  string count;
   //  1) Get a count of a collection without the data.
    response = client.GetAsync("contacts/$count", HttpCompletionOption.ResponseHeadersRead).Result; // Count is returned in response body.
    if (response.IsSuccessStatusCode) //200
                    {
                        count = JValue.Parse(response.Content.ReadAsStringAsync().Result).ToString();
                        Console.WriteLine("The contacts collection has {0} contacts.", count);
                    }
    else
      { 
         throw new Exception(string.Format("Failed to retrieve The contacts collection has {0} contacts", response.Content)); 
     }

//  2) Get a count along with the data.
      filter = "&$filter=contains(jobtitle,'senior') or contains(jobtitle, 'manager')&$count=true";
      queryOptions = "?$select=" + String.Join(",", contactProperties) + filter;
      response = client.GetAsync("contacts" + queryOptions, HttpCompletionOption.ResponseHeadersRead).Result;
      if (response.IsSuccessStatusCode) //200
                    {
                        collection = JObject.Parse(response.Content.ReadAsStringAsync().Result);
                        count = collection["@odata.count"].ToString();
                        Console.WriteLine("{0} contacts have either 'Manager' or 'Senior' designation " +
                            "in their jobtitle.", count);
                        DisplayFormattedEntities("Manager or Senior:", collection, contactProperties);
                    }
        else
          {
             throw new Exception(string.Format("Failed to retrieve Contacts having either 'Manager' or 'Senior' designation " +
                              "in their jobtitle.", response.Content));
          }

 #region Expanding results
//The expand option retrieves related information.  
//To retrieve information on associated entities in the same request, use the $expand 
//query option on navigation properties. 
//  1) Expand using single-valued navigation properties (e.g.: via the 'primarycontactid')
//  2) Expand using partner property (e.g.: from contact to account via the 'account_primary_contact')
//  3) Expand using collection-valued navigation properties (e.g.: via the 'contact_customer_accounts')
//  4) Expand using multiple navigation property types in a single request.
// Note: Expansions can only go 1 level deep.
// Tip: For performance best practice, always use $select statement in an expand option.
                   
        Console.WriteLine("\n-- Expanding Results --");
        string expand;  //expansion portion of query

        //1) Expand using the 'primarycontactid' single-valued navigation property of account1.
        expand = "&$expand=primarycontactid($select=" + String.Join(",", contactProperties) + ")";
        queryOptions = "?$select=" + String.Join(",", accountProperties) + expand;
        response = client.GetAsync(account1Uri + queryOptions, HttpCompletionOption.ResponseHeadersRead).Result;
        if (response.IsSuccessStatusCode) //200
                    {
                        JObject account = JObject.Parse(response.Content.ReadAsStringAsync().Result);
                        Console.WriteLine("Account {0} has the following primary contact person:\n\t" +
                            "Fullname: {1} \n\tJobtitle: {2} \n\tAnnualincome: {3}",
                            account["name"],
                            account["primarycontactid"]["fullname"],
                            account["primarycontactid"]["jobtitle"],
                            account["primarycontactid"]["annualincome"]);
                    }
          else
           {
              throw new Exception(string.Format("Failed to retrieve Account {0} has the following primary contact person:\n\t" +
                              "Fullname: {1} \n\tJobtitle: {2} \n\tAnnualincome: {3}", response.Content));
          }

      //2) Expand using the 'account_primary_contact' partner property.
         expand = "&$expand=account_primary_contact($select=" + String.Join(",", accountProperties) + ")";
         queryOptions = "?$select=" + String.Join(",", contactProperties) + expand;
        response = client.GetAsync(contact1Uri + queryOptions, HttpCompletionOption.ResponseHeadersRead).Result;
         if (response.IsSuccessStatusCode) //200
                    {
                        JObject contact = JObject.Parse(response.Content.ReadAsStringAsync().Result);
                        string label = "Contact '" + contact["fullname"] +
                            "' is the primary contact for the following accounts:";
                        DisplayFormattedEntities(label, (JArray)contact["account_primary_contact"], accountProperties);
                    }
         else
          {
            throw new Exception(string.Format("Failed to retrieve Contact '" + "' is the primary contact for the following accounts ", response.Content));
          }

         //3) Expand using the collection-valued 'contact_customer_accounts' navigation property. 
          expand = "&$expand=contact_customer_accounts($select=" + String.Join(",", contactProperties) + ")";
          queryOptions = "?$select=" + String.Join(",", accountProperties) + expand;
          response = client.GetAsync(account1Uri + queryOptions, HttpCompletionOption.ResponseHeadersRead).Result;
          if (response.IsSuccessStatusCode) //200
            {
                JObject account = JObject.Parse(response.Content.ReadAsStringAsync().Result);
                string label = "Account '" + account["name"] + "' has the following contact customers:";
                        DisplayFormattedEntities(label, (JArray)account["contact_customer_accounts"], contactProperties);
              }
          else
            { 
               throw new Exception(string.Format("Failed to retrieve Account '" + "' has the following contact customers:", response.Content));
            }

    //4) Expand using multiple navigation property types in a single request, specifically:
    //   primarycontactid, contact_customer_accounts, and Account_Tasks.
        Console.WriteLine("\n-- Expanding multiple property types in one request -- ");
        expand = "&$expand=primarycontactid($select=" + String.Join(",", contactProperties) + ")," +
                        "contact_customer_accounts($select=" + String.Join(",", contactProperties) + ")," +
                        "Account_Tasks($select=" + String.Join(",", taskProperties) + ")";
        queryOptions = "?$select=" + String.Join(",", accountProperties) + expand;
        response = client.GetAsync(account1Uri + queryOptions, HttpCompletionOption.ResponseHeadersRead).Result;
        if (response.IsSuccessStatusCode) //200
                    {
                        JObject account = JObject.Parse(response.Content.ReadAsStringAsync().Result);
                        string label = "Account {0} has the following primary contact person:\n\t" +
                            "Fullname: {1} \n\tJobtitle: {2} \n\tAnnualincome: {3}";
                        Console.WriteLine(label, account["name"],
                            account["primarycontactid"]["fullname"],
                            account["primarycontactid"]["jobtitle"],
                            account["primarycontactid"]["annualincome"]);

                        //Output each collection separately.
                        label = "Account '" + account["name"] + "' has the following related contacts:";
                        DisplayFormattedEntities(label, (JArray)account["contact_customer_accounts"], contactProperties);
                        label = "Account '" + account["name"] + "' has the following tasks:";
                        DisplayFormattedEntities(label, (JArray)account["Account_Tasks"], taskProperties);
                    }
        else
          { throw new Exception(string.Format("Failed to retrieve", response.Content)); }
  #endregion Expanding results

  #region FetchXML queries
    //Use FetchXML to query for all contacts whose fullname contains '(sample)'.
    //Note: XML string must be URI encoded. For more information, see: 
     //https://msdn.microsoft.com/en-us/library/gg328117.aspx

                    Console.WriteLine("\n-- FetchXML -- ");
                    string fetchXmlQuery =
                        "<fetch mapping='logical' output-format='xml-platform' version='1.0' distinct='false'>" +
                          "<entity name ='contact'>" +
                            "<attribute name ='fullname' />" +
                            "<attribute name ='jobtitle' />" +
                            "<attribute name ='annualincome' />" +
                            "<order descending ='true' attribute='fullname' />" +
                            "<filter type ='and'>" +
                              "<condition value ='%(sample)%' attribute='fullname' operator='like' />" +
                            "</filter>" +
                          "</entity>" +
                        "</fetch>";
    //Must encode the FetchXML query because it's a part of the request (GET) string .
       response = client.GetAsync("contacts?fetchXml=" + WebUtility.UrlEncode(fetchXmlQuery), HttpCompletionOption.ResponseHeadersRead).Result;
        if (response.IsSuccessStatusCode) //200
                    {
                        collection = JObject.Parse(response.Content.ReadAsStringAsync().Result);
                        DisplayFormattedEntities("Contacts Fetched by fullname containing '(sample)':",
                            collection, contactProperties);
                    }
        else
         { 
            throw new Exception(string.Format("Failed to retrieve Contacts Fetched by fullname containing '(sample)'", response.Content)); 
       }
#endregion FetchXML queries

#region Using predefined queries
   //Use predefined queries of the following two types:
   //  1) Saved query (system view)
   //  2) User query (saved view)
   //For more info, see: https://msdn.microsoft.com/en-us/library/mt607533.aspx

   //1) Saved Query - retrieve "Active Accounts", run it, then display the results.
       Console.WriteLine("\n-- Saved Query -- ");
       filter = "&$filter=name eq 'Active Accounts'";
       queryOptions = "?$select=name,savedqueryid" + filter;
//Retrieve the saved query GUID then execute it.
       response = client.GetAsync("savedqueries" + queryOptions).Result;
       if (response.IsSuccessStatusCode) //200
                    {
                        JObject body = JObject.Parse(response.Content.ReadAsStringAsync().Result);
                        JObject activeAccount = (JObject)body["value"][0]; // Get the first matched.
                        string savedQueryId = activeAccount["savedqueryid"].ToString();
                        //Now execute the query and display the results.
          response = client.GetAsync("accounts?savedQuery=" + savedQueryId, HttpCompletionOption.ResponseHeadersRead).Result;
        if (response.IsSuccessStatusCode) //200
                        {
                            collection = JObject.Parse(response.Content.ReadAsStringAsync().Result);
                            DisplayFormattedEntities("Saved query (Active Accounts):", collection, accountProperties);
                        }
       else
        { throw new Exception(string.Format("Failed to retrieve the Saved query", response.Content));
           }
           }
       else
        { throw new Exception(string.Format("Failed to retrieve the Saved query GUID", response.Content));
           }

                    //2) Create a user query, then retrieve and execute it to display its results.
                    //For more info, see: https://msdn.microsoft.com/en-us/library/gg509053.aspx
                    Console.WriteLine("\n-- User Query -- ");

                    string userQueryRep = "{ " +
                      "\"name\": \"My User Query\", " +
                      "\"description\": \"User query to display contact info.\", " +
                      "\"querytype\": 0, " +
                      "\"returnedtypecode\": \"contact\", " +
                      "\"fetchxml\": " +
                      "\"<fetch mapping='logical' output-format='xml-platform' version='1.0' distinct='false'>" +
                        "<entity name ='contact'>" +
                          "<attribute name ='fullname' />" +
                          "<attribute name ='contactid' />" +
                          "<attribute name ='jobtitle' />" +
                          "<attribute name ='annualincome' />" +
                          "<order descending ='false' attribute='fullname' />" +
                          "<filter type ='and'>" +
                            "<condition value ='%(sample)%' attribute='fullname' operator='like' />" +
                            "<condition value ='%Manager%' attribute='jobtitle' operator='like' />" +
                            "<condition value ='55000' attribute='annualincome' operator='gt' />" +
                          "</filter>" +
                        "</entity>" +
                      "</fetch>\"" +
                      "}";

   //Create the user query on server.
 HttpRequestMessage request = new HttpRequestMessage(HttpMethod.Post, "userqueries");
                    request.Content = new StringContent(userQueryRep, Encoding.UTF8, "application/json");
   response = client.SendAsync(request, HttpCompletionOption.ResponseHeadersRead).Result;
    if (response.IsSuccessStatusCode) //200
                    {

                    }
     else { throw new Exception(string.Format("Failed to create user query", response.Content)); }

       //Retrieve this new user query.
          string userQueryId;
          filter = "&$filter=name eq 'My User Query'";
          queryOptions = "?$select=name,userqueryid," + filter;
         response = client.GetAsync("userqueries" + queryOptions, HttpCompletionOption.ResponseHeadersRead).Result;
         if (response.IsSuccessStatusCode) //200
                    {
                        JObject body = JObject.Parse(response.Content.ReadAsStringAsync().Result);
                        JObject userQuery = (JObject)body["value"][0]; //Use the first match.
                        userQueryId = userQuery["userqueryid"].ToString();
                        entityUris.Add(client.BaseAddress + "/userqueries(" + userQueryId + ")");
                    }
         else
          { 
            throw new Exception(string.Format("Failed to retrieve the new user query", response.Content)); 
          }

  //Finally, execute retrieved query and display results.
      response = client.GetAsync("contacts?userQuery=" + userQueryId, HttpCompletionOption.ResponseHeadersRead).Result;
       if (response.IsSuccessStatusCode) //200
                    {
                        collection = JObject.Parse(response.Content.ReadAsStringAsync().Result);
                        DisplayFormattedEntities("Saved user query:", collection, contactProperties);
                    }
       else
        { 
          throw new Exception(string.Format("Failed to execute retrieved query and display results", response.Content));
 }
                    #endregion Using predefined queries

                    DeleteRequiredRecords(client, prompt);
                }
            }
            catch (Exception ex)
            {
                SampleHelpers.DisplayException(ex);
                throw;
            }
            finally
            {
                Console.WriteLine("Press <Enter> to exit the program.");
                Console.ReadLine();
            }
        }
    }
}
```  
  
### <a name="see-also"></a>Vea también 
 
[Utilizar API Web de Common Data Service](../overview.md)<br />
[Consultar datos utilizando la API web](../query-data-web-api.md)<br />
[Ejemplos de la API web](../web-api-samples.md)<br />
[Ejemplo de datos de consulta de la API web](../web-api-query-data-sample.md)<br />
[Ejemplo de datos de consulta de la API web (JavaScript del lado del cliente)](query-data-client-side-javascript.md)<br />
[Ejemplo de operaciones básicas de la API web (C#)](basic-operations-csharp.md)<br />
[Ejemplo de operaciones condicionales de la API web (C#)](conditional-operations-csharp.md)<br />
[Ejemplo de funciones y acciones de la API web (C#)](functions-actions-csharp.md)
