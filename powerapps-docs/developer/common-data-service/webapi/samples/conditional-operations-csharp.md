---
title: 'Ejemplo de operaciones condicionales de API web (C#) (Common Data Service para aplicaciones) | Microsoft Docs'
description: 'Este ejemplo muestra cómo realizar operaciones condicionales mediante la API web y C# de Common Data Service para aplicaciones'
ms.custom: ''
ms.date: 1/09/2019
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 48a6322c-51f3-4368-ae7b-748d0c771a82
caps.latest.revision: 17
author: KumarVivek
ms.author: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-conditional-operations-sample-c"></a>Ejemplo de operaciones condicionales de la API web (C#)

Este ejemplo muestra cómo realizar operaciones condicionales mediante la API web de de CDS for Apps y C#.  
  
> [!NOTE]
> Este ejemplo implementa las operaciones de Common Data Service para aplicaciones y la salida de la consola detalladas en el [Ejemplo de operaciones condicionales de API web](../web-api-conditional-operations-sample.md) y utiliza las construcciones comunes de C# que se describen en [Ejemplos de API web (C#)](../web-api-samples-csharp.md).  
  
<a name="bkmk_Prereqs"></a>

## <a name="prerequisites"></a>Requisitos previos

Los requisitos previos de todos los ejemplos en C# de la API web de CDS for Apps se detallan en la sección [Requisitos previos](../web-api-samples-csharp.md#bkmk_prerequisites) del tema primario [Ejemplos de operaciones básicas de la API web (C#)](../web-api-samples-csharp.md).  
  
<a name="bkmk_RunSample"></a>
 
## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

Vaya a [Microsoft CRM API Conditional Operations Sample (C#)](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23) y clone o descargue el repositorio de ejemplos, y extraiga el contenido del archivo en una carpeta de su equipo. Esta carpeta extraída debe contener los siguientes archivos:

|Archivo|Descripción|  
|----------|-----------------|  
|SampleProgram.cs|Contiene el código de origen para este ejemplo.|  
|App.config|El archivo de configuración de la aplicación, que contiene información de conexión con el servidor de CDS for Apps con marcadores. Este archivo se comparte con todos los ejemplos de API web en el repositorio. Si configura la información de la conexión para un ejemplo, puede ejecutar los otros ejemplos con la misma configuración.|  
|SampleHelper.cs|Contiene el código auxiliar para ayudar a realizar tareas comunes, como la configuración, la autenticación y la administración de errores de respuestas `HTTP`. <br/> Este archivo se comparte con todos los ejemplos de API web en el repositorio. Contiene métodos auxiliares para administrar excepciones y el token OAuth. Consulte el ejemplo simple de la API web para obtener más información sobre los métodos de este archivo.|
|SampleMethod.cs|Contiene todos los métodos que admiten el código de origen en el ejemplo. Las funciones que se usan en SampleProgram.cs se pueden definir en este archivo. |
|ConditionalOperations.sln<br /> ConditionalOperations.csproj<br /> Packages.config<br /> AssemblyInfo.cs|La solución de Visual Studio estándar 2017, proyecto, paquete NuGet, y archivos de información de ensamblado para este ejemplo.|  
  
1. Haga doble clic en el archivo ConditionalOperations.sln para abrir la solución en Visual Studio.  
  
1. Cree la solución (**Generar** > **Generar solución**). Debe descargar y actualizar automáticamente todos los paquetes NuGet necesarios.  
  
1. Edite el archivo App.Config en la solución para especificar la instancia del servidor de CDS for Apps con la que desee ejecutar este ejemplo.  
  
1. Ejecute el proyecto.  Todos los proyectos de ejemplo se configuran para ejecutarse en modo de depuración de forma predeterminada.  
  
     La salida del código de ejemplo se mostrará en una ventana de la consola.  
  
<a name="bkmk_CodeSample"></a>

## <a name="code-sample"></a>Código de ejemplo

 `SampleProgram.cs`  
  
```csharp  
using Newtonsoft.Json;
using Newtonsoft.Json.Linq;
using System;
using System.Collections.Generic;
using System.Configuration;
using System.Linq;
using System.Net;
using System.Net.Http;
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
              // <summary> Creates the CRM entity instance used by this sample. </summary>

               // Create a CRM account record.
               Console.WriteLine("\nCreate sample data");
               account.Add("name", "Contoso Ltd");
               account.Add("telephone1", "555-0000"); //Phone number value will increment with each update attempt
               account.Add("revenue", 5000000);
               account.Add("description", "Parent company of Contoso Pharmaceuticals, etc.");

               HttpRequestMessage request = new HttpRequestMessage(HttpMethod.Post, client.BaseAddress + "accounts");
               request.Content = new StringContent(account.ToString(), Encoding.UTF8, "application/json");

              HttpResponseMessage response = client.SendAsync(request, HttpCompletionOption.ResponseContentRead).Result;

                 if (response.IsSuccessStatusCode)
                  {
                    accountUri = response.Headers.GetValues("OData-EntityId").FirstOrDefault();
                    entityUri = accountUri;
                  }
                  else
                   {
                     throw new Exception(string.Format("Failed to create accounts", response.Content));
                   }

                //Retrieve the account record you created.
                 queryOptions = "?$select=name,revenue,telephone1,description";
                    //JObject entity = null;

                 HttpResponseMessage response1 = client.GetAsync(entityUri + queryOptions).Result;
                  if (response1.IsSuccessStatusCode) //200
                   {
                     account = JObject.Parse(response1.Content.ReadAsStringAsync().Result);
                     Console.WriteLine("Account entity created:");
                     Console.WriteLine(account.ToString(Newtonsoft.Json.Formatting.Indented));
                     initialAcctETagVal = account["@odata.etag"].ToString();
                   }

             #region Conditional GET

             Console.WriteLine("\n--Conditional GET section started--");
             // Attempt to retrieve using conditional GET with current ETag value.
             request = new HttpRequestMessage(HttpMethod.Get, accountUri + queryOptions);

             // Retrieve only if it doesn't match previously retrieved version.
             request.Headers.Add("If-None-Match", initialAcctETagVal);
             response = client.SendAsync(request, HttpCompletionOption.ResponseHeadersRead).Result;

              if (response.StatusCode == HttpStatusCode.NotModified)  // 304; expected.
                {
                  Console.WriteLine("Instance retrieved using ETag: {0}", initialAcctETagVal);
                  Console.WriteLine("Expected outcome: Entity was not modified so nothing was returned.");
                }

                else if (response.StatusCode == HttpStatusCode.OK)  // 200; not expected
                 {
                   Console.WriteLine("Instance retrieved using ETag: {0}", initialAcctETagVal);
                   account = JObject.Parse(response.Content.ReadAsStringAsync().Result);
                    Console.WriteLine(account.ToString(Formatting.Indented));
                 }

                else
                 {
                   throw new Exception(string.Format("Failed to retrieve", response.Content));
                  }

                // Modify the account instance by updating telephone1

                 string accountPhoneUri = string.Format("{0}/{1}", accountUri, "telephone1");
                 JObject phoneProperty = new JObject();
                 phoneProperty.Add("value", "555-0001");
                 request = new HttpRequestMessage(HttpMethod.Put, accountPhoneUri);
                 request.Content = new StringContent(phoneProperty.ToString(), Encoding.UTF8, "application/json");
                 response = client.SendAsync(request, HttpCompletionOption.ResponseContentRead).Result;
                 if (response.StatusCode == HttpStatusCode.NoContent)
                  {
                    Console.WriteLine("\nAccount telephone number updated.");
                  }
                 else
                  {
                   throw new Exception(string.Format("Failed to update the account telephone number", response.Content));
                  }

                 // Reattempt conditional GET with original ETag value.
                 request = new HttpRequestMessage(HttpMethod.Get, accountUri + queryOptions);
                 request.Headers.Add("If-None-Match", initialAcctETagVal);
                 response = client.SendAsync(request, HttpCompletionOption.ResponseHeadersRead).Result;

                 if (response.StatusCode == HttpStatusCode.OK) //200; expected
                  {
                    Console.WriteLine("Instance retrieved using ETag: {0}", initialAcctETagVal);
                  }
                 else if (response.StatusCode == HttpStatusCode.NotModified) // 304; not expected
                  {
                    Console.WriteLine("Unexpected status code: '{0}'.", (int)response.StatusCode);
                  }
                   else
                    { throw new Exception(string.Format("Failed to get original ETag value", response.Content)); }

                 // Retrieve and output current account state.
                 account = JObject.Parse(response.Content.ReadAsStringAsync().Result);
                 updatedAcctETagVal = account["@odata.etag"].ToString(); // Capture updated ETag
                  Console.WriteLine(account.ToString(Formatting.Indented));

                 #endregion Conditional GET

                 #region Optimistic concurrency on delete and update
                 Console.WriteLine("\n--Optimistic concurrency section started--");

                 // Attempt to delete original account (if matches original ETag value).
                 request = new HttpRequestMessage(HttpMethod.Delete, accountUri);
                 // If you replace "initialAcctETagVal" with "updatedAcctETagVal", 
                 // delete will succeed.
                 request.Headers.Add("If-Match", initialAcctETagVal); 
                 response = client.SendAsync(request, HttpCompletionOption.ResponseHeadersRead).Result;
                 // 412; Precondition failed error expected

              if (response.StatusCode == HttpStatusCode.PreconditionFailed) 
               {
                Console.WriteLine("Expected Error: The version of the existing record doesn't match the property provided.");
                Console.WriteLine("\tAccount not deleted using ETag '{0}', status code: '{1}'.",
                initialAcctETagVal, (int)response.StatusCode);
               }
               else if (response.IsSuccessStatusCode) // 200-299; not expected
                    {
                      Console.WriteLine("Account deleted!");
                    }

               else
                {
                 throw new Exception(string.Format("Failed to delete original count",response.Content));
                }

                 //Attempt to update account (if matches original ETag value).
                 JObject accountUpdate = new JObject();
                 accountUpdate.Add("telephone1", "555-0002");
                 accountUpdate.Add("revenue", 6000000);
                 request = new HttpRequestMessage(new HttpMethod("PATCH"), accountUri);
                 request.Content = new StringContent(accountUpdate.ToString(),
                 Encoding.UTF8, "application/json");
                 request.Headers.Add("If-Match", initialAcctETagVal);
                 response = client.SendAsync(request, HttpCompletionOption.ResponseHeadersRead).Result;

             if (response.StatusCode == HttpStatusCode.PreconditionFailed) // 412;
                    //Precondition failed error expected
              {
                Console.WriteLine("Expected Error: The version of the existing record doesn't match the property provided.");
                Console.WriteLine("\tAccount not updated using ETag '{0}', status code: '{1}'.",
                initialAcctETagVal, (int)response.StatusCode);
               }
             else if (response.StatusCode == HttpStatusCode.NoContent)  // 204; not expected
               {
                Console.WriteLine("Account updated using ETag: {0}, status code: '{1}'.",
                initialAcctETagVal, (int)response.StatusCode);
               }
             else
              {
                throw new Exception(string.Format("Failed to update account (if original ETag value matches)", response.Content));
              }

                  // Reattempt update if matches current ETag value.
                  accountUpdate["telephone1"] = "555-0003";
                  request = new HttpRequestMessage(new HttpMethod("PATCH"), accountUri);
                  request.Content = new StringContent(accountUpdate.ToString(),
                  Encoding.UTF8, "application/json");
                  request.Headers.Add("If-Match", updatedAcctETagVal);
                  response = client.SendAsync(request, HttpCompletionOption.ResponseHeadersRead).Result;

                 if (response.StatusCode == HttpStatusCode.NoContent) // 204; expected
                  {
                    Console.WriteLine("\nAccount successfully updated using ETag: {0}, status code: '{1}'.",
                    updatedAcctETagVal, (int)response.StatusCode);
                  }
                 else if (response.StatusCode == HttpStatusCode.PreconditionFailed) // 412; not expected
                  {
                    Console.WriteLine("Unexpected status code: '{0}'", (int)response.StatusCode);
                  }
                 else
                  {
                    throw new Exception(string.Format("Failed to update if matches current ETag value", response.Content));
                  }

                 // Retrieve and output current account state.
                 account = GetCurrentRecord(client,accountUri, queryOptions);
                 updatedAcctETagVal = account["@odata.etag"].ToString(); //Capture updated ETag
                 Console.WriteLine(account.ToString(Formatting.Indented));

                 #endregion Optimistic concurrency on delete and update

                 #region Controlling upsert operations
                 Console.WriteLine("\n--Controlling upsert operations section started--");
                 //Attempt to insert without update some properties for this account
                 accountUpdate = new JObject();
                 accountUpdate.Add("telephone1", "555-0004");
                 accountUpdate.Add("revenue", 7500000);

                 request = new HttpRequestMessage(new HttpMethod("PATCH"), accountUri);
                 request.Content = new StringContent(accountUpdate.ToString(),
                 Encoding.UTF8, "application/json");
                 
                 //Perform operation only if matching resource does not exist. 
                 request.Headers.Add("If-None-Match", "*");
                 response = client.SendAsync(request, HttpCompletionOption.ResponseHeadersRead).Result;

                 if (response.StatusCode == HttpStatusCode.PreconditionFailed) // 412; expected
                  {
                    Console.WriteLine("Expected Error: A record with matching key values already exists.");
                    Console.WriteLine("\tAccount not updated using ETag '{0}, status code: '{1}'.",
                    initialAcctETagVal, (int)response.StatusCode);
                  }
                 else if (response.StatusCode == HttpStatusCode.NoContent) // 204; unexpected
                  {
                    Console.WriteLine("Account updated using If-None-Match '*'");
                  }

                 else
                  {
                    throw new Exception(string.Format("Failed to perform operations", response.Content));
                  }

                 //Attempt to perform same update without creation. 
                 accountUpdate["telephone1"] = "555-0005";
                 request = new HttpRequestMessage(new HttpMethod("PATCH"), accountUri);
                 request.Content = new StringContent(accountUpdate.ToString(),
                 Encoding.UTF8, "application/json");
                 //Perform operation only if matching resource exists. 
                 request.Headers.Add("If-Match", "*");
                 response = client.SendAsync(request, HttpCompletionOption.ResponseHeadersRead).Result;

                 if (response.StatusCode == HttpStatusCode.NoContent)  // 204; expected
                  {
                    Console.WriteLine("Account updated using If-Match '*'");
                  }
                 else if (response.StatusCode == HttpStatusCode.PreconditionFailed) // 412; not expected
                  {
                    Console.WriteLine("Account not updated using If-Match '*', status code: '{0}'.",
                    (int)response.StatusCode);
                  }
                 else
                  {
                   throw new Exception(string.Format("Failed to perform operations", response.Content));
                  }

                //Retrieve and output current account state.
                 account = GetCurrentRecord(client,accountUri, queryOptions);
                 Console.WriteLine(account.ToString(Formatting.Indented));

                 // Delete the account record
                 HttpResponseMessage deleteResponse;
                 deleteResponse = client.DeleteAsync(accountUri).Result;
                 if (deleteResponse.IsSuccessStatusCode) // 200-299
                  {
                    Console.WriteLine("\nAccount was deleted.");
                  }
                 else if (deleteResponse.StatusCode == HttpStatusCode.NotFound)
                  // 404; entity record may have been deleted by another user.
                   {
                    Console.WriteLine("Account could not be found.");
                   }
                 else // Failed to delete
                   {
                        // Throw last failure.
                    throw new Exception(string.Format("Failed to delete account record", response.Content));
                   }

                // Attempt to update it
                 accountUpdate["telephone1"] = "555-0006";
                 request = new HttpRequestMessage(new HttpMethod("PATCH"), accountUri);
                 request.Content = new StringContent(accountUpdate.ToString(),
                 Encoding.UTF8, "application/json");

                 // Perform operation only if matching resource exists.
                 request.Headers.Add("If-Match", "*");
                 response = client.SendAsync(request, HttpCompletionOption.ResponseHeadersRead).Result;

                 if (response.StatusCode == HttpStatusCode.PreconditionFailed ||
                             response.StatusCode == HttpStatusCode.NotFound)  // 412 or 404; expected
                  {
                    Console.WriteLine("Expected Error: Account with Id = {0} does not exist.", account["accountid"]);
                    Console.WriteLine("Account not updated because it does not exist, status code: '{0}'.",
                    (int)response.StatusCode);
                  }
                  else if (response.StatusCode == HttpStatusCode.NoContent)  // 204; not expected                                                                       
                   {
                    Console.WriteLine("Account upserted using If-Match '*'");
                   }
                   else
                    {
                      throw new Exception(string.Format("Failed to perform operations", response.Content));
                    }

                    #endregion Controlling upsert operations
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

[Usar para la API web de Common Data Service para aplicaciones](../overview.md)<br />
[Realizar operaciones condicionales mediante la API web](../perform-conditional-operations-using-web-api.md)<br />
[Ejemplos de la API web](../web-api-samples.md)<br />
[Ejemplo de operaciones condicionales de la API web](../web-api-conditional-operations-sample.md)
[Ejemplo de operaciones básicas de la API web (C#)](basic-operations-csharp.md)<br />
[Ejemplo de datos de consulta API (C#)](query-data-csharp.md)<br />
[Ejemplo de funciones y acciones de la API web (C#)](functions-actions-csharp.md)
