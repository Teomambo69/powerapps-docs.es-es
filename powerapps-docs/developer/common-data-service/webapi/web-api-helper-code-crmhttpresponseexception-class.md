---
title: 'Código auxiliar de la API web: Clase CrmHttpResponseException (Common Data Service para aplicaciones)| Microsoft Docs'
description: Clase CrmHttpResponseException se usa para representan errores de estado HTTP generados durante las llamadas de API Web de Common Data Service para aplicaciones
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 8deb0bc5-6f4a-4ca7-a3a2-75c06dc7f967
caps.latest.revision: 11
author: brandonsimons
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-helper-code-crmhttpresponseexception-class"></a>Código auxiliar de API web: Clase CrmHttpResponseException

Utilice la clase `CrmHttpResponseException` para representar [errores de estado HTTP](https://msdn.microsoft.com/library/gg334391.aspx) generados durante las llamadas de API Web de Common Data Service para aplicaciones.  Esta clase se deriva de la clase de sistema estándar .NET [Exception](https://msdn.microsoft.com/library/system.exception.aspx) para integrarse fácilmente con sus mecanismos existentes de control de excepciones. Para obtener información más general, consulte [Control y lanzamiento de excepciones](https://docs.microsoft.com/en-us/dotnet/standard/exceptions/index).  
  
La clase `CrmHttpResponseException` se encuentra en el archivo Exceptions.cs en la [Biblioteca de código auxiliar de la API web de CRM](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode/).  Se usa extensivamente en las otras clases de biblioteca de código auxiliar y ejemplos web de la API web en C#. Para obtener más información, consulte [Usar la biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md).  
  
Esta clase usa funcionalidad de control de cadenas JSON desde la biblioteca [Json.NET](http://www.newtonsoft.com/json) de origen abierto.  
  
## <a name="class-members"></a>Integrantes de la clase  

La siguiente tabla muestra los integrantes públicos de la clase `CrmHttpResponseException`.  
  
<!-- TODO:
|||  
|-|-|  
|![Common Data Service for Apps Web API Helper Library&#45;CrmHttpResponseException Class Diagram](../media/web-api-helper-library-crm-exception-class-diagram.png "Common Data Service for Apps Web API Helper Library-CrmHttpResponseException Class Diagram")|**CrmHttpResponseException  class**<br /><br /> *Properties:*<br /><br /> `StackTrace` – the string representation of the immediate frames on the Common Data Service for Apps server’s call stack when the exception was thrown, if available.<br /><br /> *Methods*:<br /><br /> The constructors initialize an instance of this class, and require a [HttpContent](https://msdn.microsoft.com/library/hh193687\(v=vs.110\).aspx) parameter and an optional inner exception parameter.<br /><br /> `ExtractMessageFromContent` – this static method extracts the error message from the specified HTTP content parameter.|  
   -->
## <a name="usage"></a>Uso  

Normalmente, usted crea y genera un objeto `CrmHttpResponseException` al procesar un error de estado devuelto con un mensaje de respuesta HTTP. Por ejemplo, el siguiente código inicia un error de este tipo cuando la llamada a la función <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /> produce un error.  
  
```csharp  
response = await httpClient.GetAsync("WhoAmI", HttpCompletionOption.ResponseContentRead);  
if (!response.IsSuccessStatusCode)  
{   
    throw new CrmHttpResponseException(response.Content);   
}  
```  
  
 Puede recoger y procesar objetos `CrmHttpResponseException` lanzados de forma similar a otras excepciones .NET estándar.  
  
> [!IMPORTANT]
>  Si está usando el método HttpResponseMessage.[EnsureSuccessStatusCode](/dotnet/api/system.net.http.httpresponsemessage.ensuresuccessstatuscode) para convertir automáticamente errores de respuesta HTTP en objetos [HttpRequestException](/dotnet/api/system.net.http.httprequestexception) lanzados, este método impide el uso de la clase `CrmHttpResponseException`. Tenga en cuenta que si usa este método, gran parte de los detalles de respuesta, incluido el código de estado, no estarán disponibles durante control de excepciones.  
  
## <a name="class-listing"></a>Lista de clases

 El origen más actual para esta clase se encuentra en el paquete de NuGet de la [Biblioteca de código auxiliar de la API web del SDK de CRM](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode).  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Net.Http;  
using Newtonsoft.Json;  
using Newtonsoft.Json.Linq;  
  
namespace Microsoft.Crm.Sdk.Samples.HelperCode  
{  
    /// <summary>  
    /// Produces a populated exception from an error message in the content of an HTTP response.   
    /// </summary>  
    public class CrmHttpResponseException : System.Exception  
    {  
        #region Properties  
        private static string _stackTrace;  
  
        /// <summary>  
        /// Gets a string representation of the immediate frames on the call stack.  
        /// </summary>  
        public override string StackTrace  
        {  
            get { return _stackTrace; }  
        }  
        #endregion Properties  
  
        #region Constructors  
        /// <summary>  
        /// Initializes a new instance of the CrmHttpResponseException class.  
        /// </summary>  
        /// <param name="content">The populated HTTP content in Json format.</param>  
        public CrmHttpResponseException(HttpContent content)  
            : base(ExtractMessageFromContent(content)) { }  
  
        /// <summary>  
        /// Initializes a new instance of the CrmHttpResponseException class.  
        /// </summary>  
        /// <param name="content">The populated HTTP content in Json format.</param>  
        /// <param name="innerexception">The exception that is the cause of the current exception, or a null reference  
        /// if no inner exception is specified.</param>  
        public CrmHttpResponseException(HttpContent content, Exception innerexception)  
            : base(ExtractMessageFromContent(content), innerexception) { }  
  
        #endregion Constructors  
  
        #region Methods  
        /// <summary>  
        /// Extracts the CRM specific error message and stack trace from an HTTP content.   
        /// </summary>  
        /// <param name="content">The HTTP content in Json format.</param>  
        /// <returns>The error message.</returns>  
        private static string ExtractMessageFromContent(HttpContent content)  
        {  
            string message = String.Empty;  
            string downloadedContent = content.ReadAsStringAsync().Result;  
            if (content.Headers.ContentType.MediaType.Equals("text/plain"))  
            {  
                message = downloadedContent;  
            }  
            else if (content.Headers.ContentType.MediaType.Equals("application/json"))  
            {  
                JObject jcontent = (JObject)JsonConvert.DeserializeObject(downloadedContent);  
                IDictionary<string, JToken> d = jcontent;  
  
                // An error message is returned in the content under the 'error' key.   
                if (d.ContainsKey("error"))  
                {  
                    JObject error = (JObject)jcontent.Property("error").Value;  
                    message = (String)error.Property("message").Value;  
                }  
                else if (d.ContainsKey("Message"))  
                    message = (String)jcontent.Property("Message").Value;  
  
                if (d.ContainsKey("StackTrace"))  
                    _stackTrace = (String)jcontent.Property("StackTrace").Value;  
            }  
            else if (content.Headers.ContentType.MediaType.Equals("text/html"))  
            {  
                message = "HTML content that was returned is shown below.";  
                message += "\n\n" + downloadedContent;  
            }  
            else  
            {  
                message = String.Format("No handler is available for content in the {0} format.",    
                    content.Headers.ContentType.MediaType.ToString());  
            }  
            return message;  
            #endregion Methods  
        }  
    }  
}  
  
```  
  
### <a name="see-also"></a>Vea también

[Introducción a la API web (C#)](get-started-dynamics-365-web-api-csharp.md)<br />
[Iniciar un proyecto de la API web en Visual Studio (C#)](start-web-api-project-visual-studio-csharp.md)<br />
[Usar la biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md).<br />
[Código auxiliar: clase de autenticación](web-api-helper-code-authentication-class.md)<br />
[Código auxiliar: Clase de configuración](web-api-helper-code-configuration-classes.md)
