---
title: 'Ejemplos de operaciones de datos de API web (C#) (Common Data Service para aplicaciones) | Microsoft Docs'
description: 'En este tema se proporciona una descripción de distintos ejemplos de API web que están implementados mediante C#'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 66e26684-819e-45f7-bec4-c250be4d6fed
caps.latest.revision: 14
author: brandonsimons
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-data-operations-samples-c"></a>Ejemplos de operaciones de datos de API web (C#)

En este tema se proporciona información sobre los ejemplos de la API web implementada con C#. Si bien cada ejemplo se centra en un aspecto distinto de la API web de Common Data Service para aplicaciones, comparten características y estructura similares.  
  
> [!NOTE]
>  Este método de implementación usa creación de objetos de bajo nivel y llamadas de mensajes HTTP explícitas. Este método permite el control y demostración de las propiedades de objetos de bajo nivel que controlan el comportamiento de API web. Está diseñado para ayudarle a entender el funcionamiento interno pero no representa necesariamente un enfoque que proporcione la mejor experiencia de productividad para el desarrollador.  
>   
>  En cambio, las bibliotecas de alto nivel, como la [Biblioteca de OData](https://msdn.microsoft.com/library/hh525392\(v=vs.103\).aspx), resumen gran parte de esta lógica de cliente de bajo nivel.  La [Plantilla de OData T4](https://blogs.msdn.microsoft.com/odatateam/2012/07/02/trying-out-the-prerelease-odata-client-t4-template/) puede usarse opcionalmente conjuntamente con la biblioteca de OData para generar automáticamente clases de entidad de cliente.  

<a name="bkmk_prerequisites"></a>
   
## <a name="prerequisites"></a>Requisitos previos

A continuación se enumeran los requisitos para crear y ejecutar los ejemplos en C# de API web de Common Data Service para aplicaciones:  
  
-   Una versión Microsoft Visual Studio de 2015 o posterior.  Una versión gratuita, [Visual Studio Community](https://www.visualstudio.com/products/visual-studio-community-vs.aspx), está disponible para descarga [aquí](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx).  
  
-   Una conexión a internet para descargar y actualizar los paquetes NuGet a los que se hace referencia.  
  
-   Obtenga acceso a Common Data Service para aplicaciones con privilegios para realizar operaciones CRUD.  
  
<!-- TODO:
-   In order to run samples against CDS for Apps, you must register your application with Azure Active Directory to obtain a client ID and redirect URL. For more information, see [Walkthrough: Register a Common Data Service for Apps app with Azure Active Directory](../walkthrough-register-app-azure-active-directory.md).   -->

> [!NOTE]
> Estos ejemplos requieren la versión 2.x del ensamblado [Microsoft.IdentityModel.Client.ActiveDirectory](https://docs.microsoft.com/en-us/dotnet/api/microsoft.identitymodel.clients.activedirectory?view=azure-dotnet) para una autenticación basada en OAuth.
  
<a name="bkmk_webApiSamplesListing"></a>

## <a name="web-api-samples-listing-c"></a>Lista de ejemplos de la API web (C#)

En la siguiente tabla se muestran los ejemplos implementados en C#.  Cada ejemplo se describe en forma más general en un tema de grupo de ejemplo correspondiente que se centra en la solicitud HTTP y en mensajes de respuesta, como se detalla en el tema [Web API Samples](web-api-samples.md).  
  
|Muestra|Grupo de ejemplo|Descripción|  
|------------|------------------|-----------------|  
|[Ejemplo de operaciones básicas de la API web (C#)](samples/basic-operations-csharp.md)|[Ejemplo de operaciones básicas de la API web](web-api-basic-operations-sample.md)|Demuestra cómo crear, recuperar, actualizar, eliminar, asocie y anular la asociación de registros de entidad de Common Data Service para aplicaciones.|  
|[Ejemplo de datos de consulta API (C#)](samples/query-data-csharp.md)|[Ejemplo de datos de consulta de la API web](web-api-query-data-sample.md)|Demuestra cómo usar sintaxis y funciones de consulta de OData v4 así como funciones de consulta de Common Data Service para aplicaciones. Incluye ejemplos de trabajo con consultas predefinidas y uso de FetchXML para realizar consultas.|  
|[Ejemplo de operaciones condicionales de la API web (C#)](samples/conditional-operations-csharp.md)|[Ejemplo de operaciones condicionales de la API web](web-api-conditional-operations-sample.md)|Demuestra cómo realizar operaciones condicionales que usted especifica con criterios de ETag.|  
|[Ejemplo de funciones y acciones de la API web (C#)](samples/functions-actions-csharp.md)|[Ejemplo de funciones y acciones de la API web](web-api-functions-actions-sample.md)|Demuestra cómo usar funciones y acciones enlazadas y sin enlazar, incluidas acciones personalizadas.|  
  
<a name="bkmk_howDownloadRun"></a>

## <a name="how-to-download-and-run-the-samples"></a>Cómo descargar y ejecutar los ejemplos
  
El código de origen para cada ejemplo está disponible en [Galería de código de MSDN](https://code.msdn.microsoft.com/site/search?f%5b0%5d.type=user&f%5b0%5d.value=microsoft%20dynamics%20crm%20sdk%20documentation%20team). El vínculo para descargar cada ejemplo se incluye en el tema de ejemplo. La descarga de ejemplos es un archivo .zip comprimido que contiene archivos de la solución Visual Studio 2015 para el ejemplo. Para obtener más información, consulte la sección **Ejecutar este ejemplo** en cada tema de ejemplo.  
  
<a name="bkmk_commonElements"></a>

## <a name="common-elements-found-in-each-sample"></a>Elementos comunes que se encuentran en cada ejemplo

La mayoría de los ejemplos tienen una estructura similar y contienen métodos y recursos comunes, normalmente para proporcionar la infraestructura básica para un programa en C# de la API web.  
  
Muchos de estos elementos comunes también están presentes al crear una nueva solución que tendrá acceso a la API web de CDS para aplicaciones. Para obtener más información, consulte [iniciar un projecto API web en Visual Studio (C#)](start-web-api-project-visual-studio-csharp.md).  
  
### <a name="utilized-libraries-and-frameworks"></a>Bibliotecas y marcos de trabajo usados
 
Esta implementación en C# depende del siguiente código auxiliar para la comunicación HTTP, la configuración de aplicaciones, la autenticación, el tratamiento de errores, y la serialización de JSON.  
  
-   Las clases de mensajería estándar HTTP de .NET Framework que se contienen en el [Espacio de nombres System.Net.Http](/dotnet/api/system.net.http), en particular [HttpClient](/dotnet/api/system.net.http.httpclient), [HttpRequestMessage](/dotnet/api/system.net.http.httprequestmessage), y [HttpResponseMessage](/dotnet/api/system.net.http.httpresponsemessage), se usan para mensajería HTTP.  
  
-   La biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones se usa para leer el archivo de configuración de la aplicación, para autenticarse en el servidor de CDS para aplicaciones, y ayudar en el tratamiento de errores de operaciones.  Para obtener más información, consulte [Usar la biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md).  
  
-   La biblioteca [Json.NET](http://www.newtonsoft.com/json) de Newtonsoft admite el formato de datos JSON.  
  
#### <a name="jsonnet-library"></a>Biblioteca de Json.NET

Dado que C# y la mayoría de los otros lenguajes administrados no admiten nativamente el formato de datos de JSON, la mejor opción actual es usar una biblioteca para esta funcionalidad. Para obtener más información, consulte [Introducción a la notación de objetos de JavaScript (JSON) en JavaScript y .NET](https://msdn.microsoft.com/library/bb299886.aspx). Json.NET es una opción popular para proyectos de Microsoft .NET. Proporciona un marco de trabajo sólido, de alto rendimiento y código abierto (con [licencia MIT](https://opensource.org/licenses/MIT)) para serializar, convertir, analizar, consultar y dar formato a datos JSON. Para obtener más información, vea la [Documentación de Json.NET](http://www.newtonsoft.com/json/help/html/Introduction.htm).  
  
En los ejemplos de C#, esta biblioteca se usa principalmente para serializar datos entre objetos .NET y los cuerpos de mensajes HTTP. Aunque la biblioteca proporciona varios métodos para realizar esta tarea, el enfoque usado por los ejemplos es crear instancias [JObject](http://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm) individuales para representar instancias de entidad de Common Data Service para aplicaciones.  Por ejemplo, el siguiente código crea la variable `contact1` que representa una instancia <xref href="Microsoft.Dynamics.CRM.contact?text=contact EntityType" /> de Common Data Service para aplicaciones, después suministra valores para un conjunto seleccionado de propiedades para este tipo.  
  
```csharp  
  
JObject contact1 = new JObject();  
contact1.Add("firstname", "Peter");  
contact1.Add("lastname", "Cambel");  
contact1.Add("annualincome", 80000);  
contact1["jobtitle"] = "Junior Developer";  
  
```  
  
 El uso de la notación entre llaves en la última instrucción es equivalente al método [Add](http://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_Linq_JObject_Add.htm). Esta creación de instancias también podría conseguirse mediante el uso del método estático [Parse](http://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_Linq_JObject_Parse.htm):  
  
```csharp  
  
JObject contact1 = JObject.Parse(@"{firstname: 'Peter', lastname: 'Cambel', "  
+ @"annualincome: 80000, jobtitle: 'Junior Developer'}");  
  
```  
  
 Puesto que `JObject` representa un tipo JSON general, su uso evita mucha comprobación de tipos en tiempo de ejecución.  Por ejemplo, aunque la declaración siguiente es sintácticamente válida, potencialmente producirá los errores en tiempo de ejecución porque el <xref href="Microsoft.Dynamics.CRM.contact?text=contact EntityType" /> no contiene una propiedad `age`.  
  
 `contact1.Add("age", 37);    //Possible error--no age property exists in contact!`  
  
 Una vez que se ha inicializado la variable de entidad, puede enviarse en el cuerpo de un mensaje, con ayuda de varias clases System.Net.Http, por ejemplo:  
  
```csharp  
  
HttpRequestMessage request = new HttpRequestMessage(HttpMethod.Post, "contacts");  
request.Content = new StringContent(contact1.ToString(), Encoding.UTF8, "application/json");  
HttpResponseMessage response = await httpClient.SendAsync(request1);  
  
```  
  
 También puede crear instancias JObject deserializando instancias de entidad durante operaciones de recuperación, por ejemplo:  
  
```csharp  
  
//contact2Uri contains a reference to an existing CRM contact instance.  
string queryOptions = "?$select=fullname,annualincome,jobtitle,description";  
HttpResponseMessage response = await httpClient.GetAsync(contact2Uri + queryOptions);  
JObject contact2 = JsonConvert.DeserializeObject<JObject>(await response.Content.ReadAsStringAsync());  
  
```  
  
### <a name="response-success-and-error-handling"></a>Tratamiento de errores y aciertos de respuesta

En general, los ejemplos adoptan un enfoque directo procesar respuestas HTTP. Si la solicitud se realiza correctamente, la información sobre la operación se envía normalmente a la consola. Si la respuesta también contiene una carga útil de JSON o encabezados útiles, esta información se procesa si se ha realizado correctamente. Y, por último, si se creó una entidad de Common Data Service para aplicaciones, la colección `entityUris` se actualizará con el URI de ese recurso. El método [DeleteRequiredRecords](#bkmk_deleteRequiredRecords) usa esta colección para eliminar opcionalmente los datos creados por el ejemplo desde el servidor de Common Data Service para aplicaciones.  
  
Si se produce error en la solicitud, el programa envía un mensaje contextual sobre la operación que ha producido error y, a continuación inicia una excepción personalizada de tipo `CrmHttpResponseException`. El controlador de excepciones genera más información sobre la excepción y después controla los pases a un bloque `finally` que incluye lógica de limpieza, una vez más incluyendo una llamada a `DeleteRequiredRecords`. El siguiente código demuestra este método de tratamiento de errores en una solicitud POST para crear un registro.  
  
```csharp  
  
if (response.StatusCode == HttpStatusCode.NoContent)  //204  
{  
Console.WriteLine("POST succeeded, entity created!");  
//optionally process response message headers or body here, for example:  
entityUri = response.Headers.GetValues("OData-EntityId").FirstOrDefault();  
entityUris.Add(entityUri);  
}  
else  
{  
Console.WriteLine("Operation failed: {0}", response.ReasonPhrase);  
throw new CrmHttpResponseException(response.Content);  
}  
  
```  
  
 [HttpStatusCode](https://msdn.microsoft.com/library/hh435235.aspx).NoContent es equivalente a un código de estado HTTP 204, “Sin contenido”. Aquí, este código de estado indica que la solicitud POST se realizó correctamente. Para obtener más información, consulte [Componer solicitudes HTTP y administrar errores](https://msdn.microsoft.com/en-us/library/gg334391.aspx).  
  
### <a name="characteristics-and-methods"></a>Características y métodos
  
La mayoría de los ejemplos tienen el mismo patrón arquitectónico general, con las siguientes características:  
  
- Todo el código de ejemplo correspondiente en C# se contiene en el archivo de origen primario denominado `Program.cs`, que contiene una sola clase con el mismo nombre que el proyecto de ejemplo.  
  
- Las clases de ejemplo, así como la [Biblioteca de código auxiliar de API web de Common Data Service para aplicaciones](use-microsoft-dynamics-365-web-api-helper-library-csharp.md), se contienen en el espacio de nombres `Microsoft.Crm.Sdk.Samples`.  
  
- Los ejemplos se comentan generosamente: se proporcionan resúmenes en los niveles de clase y método, y la mayoría de las instrucciones individuales clave tienen comentarios asociados en la misma línea o en una sola.  Los archivos complementarios, como el archivo de configuración de la aplicación `App.config`, también contienen a menudo comentarios importantes.  
  
- La clase de ejemplo principal normalmente se estructura para contener el siguiente conjunto de métodos comunes: [Principal](#bkmk_main), [ConnectToCRM](#bkmk_connectToCrm), [CreateRequiredRecords](#bkmk_createRequiredRecords), [RunAsync](#bkmk_runAsync), [DisplayException](#bkmk_displayException), y [DeleteRequiredRecords](#bkmk_deleteRequiredRecords).  
  
<a name="bkmk_main"></a>
   
#### <a name="main-method"></a>Método principal

Por definición, este método comienza la ejecución del ejemplo.  Contiene sólo el flujo de control de alto nivel y la lógica de control de excepciones, a menudo exactamente como el siguiente código:  
  
```csharp  
  
static void Main(string[] args)  
{  
FunctionsAndActions app = new FunctionsAndActions();  
try  
{  
//Read configuration file and connect to specified CRM server.  
app.ConnectToCRM(args);  
app.CreateRequiredRecords();  
Task.WaitAll(Task.Run(async () => await app.RunAsync()));  
}  
catch (System.Exception ex) { DisplayException(ex);  
}  
finally  
{  
if (app.httpClient != null)  
{  
app.DeleteRequiredRecords(true);  
app.httpClient.Dispose();  
}  
Console.WriteLine("Press <Enter> to exit the program.");  
Console.ReadLine();  
}  
}  
  
```  
  
<a name="bkmk_connectToCrm"></a>

#### <a name="connecttocrm-method"></a>Método ConnectToCRM
 
Este método llama a las bibliotecas de código auxiliar para leer el archivo de configuración de la aplicación y después establece una conexión con el servidor especificado de Common Data Service para aplicaciones. El resultado de estos pasos es la inicialización de una propiedad de clase [HttpClient](https://msdn.microsoft.com/en-us/library/system.net.http.httpclient\(v=vs.110\).aspx) que se usa en todo el programa para enviar solicitudes web y recibir respuestas.  Tenga en cuenta que las propiedades siguientes se establecen en este objeto:  
  
```csharp  
  
//Define the Web API address, the max period of execute time, the Odata  
// version, and the expected response payload format.  
httpClient.BaseAddress = new Uri(config.ServiceUrl + "api/data/v8.1/");  
httpClient.Timeout = new TimeSpan(0, 2, 0);  // 2 minute timeout  
httpClient.DefaultRequestHeaders.Add("OData-MaxVersion", "4.0");  
httpClient.DefaultRequestHeaders.Add("OData-Version", "4.0");  
httpClient.DefaultRequestHeaders.Accept.Add(new MediaTypeWithQualityHeaderValue("application/json"));  
  
```  
  
 Para obtener más información sobre la aplicación del ejemplo de configuración y autenticación, consulte [Usar la biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md).  
  
<a name="bkmk_createRequiredRecords"></a>

#### <a name="createrequiredrecords-method"></a>Método CreateRequiredRecords
 
Este método crea e inicializa los registros de entidad requeridos por el ejemplo, solo cuando estas operaciones no son de interés principal en el ejemplo.  Por ejemplo, el [Ejemplo de operaciones básicas de la API web (C#)](samples/basic-operations-csharp.md) no contiene este método porque la creación de registros es un aspecto principal del ejemplo.  
  
<a name="bkmk_runAsync"></a>

#### <a name="runasync-method"></a>Método RunAsync

Este método asincrónico contiene el código de origen correspondiente o, para programas más largos, métodos de llamada que agrupan el código de ejemplo correspondiente. El código contenido se explica por comentarios incrustados y comentario situado en la sección **Comentarios** de cada tema de ejemplo correspondiente.  
  
<a name="bkmk_displayException"></a>
  
#### <a name="displayexception-method"></a>Método DisplayException

Este método auxiliar muestra información de excepciones, incluidas las excepciones internas, a la consola estándar.  
  
<a name="bkmk_deleteRequiredRecords"></a>
  
#### <a name="deleterequiredrecords-method"></a>Método DeleteRequiredRecords

Este método complementario elimina opcionalmente registros de ejemplo y otros recursos del servidor de Common Data Service para aplicaciones creados en el programa y, en particular, por el método [CreateRequiredRecords](#bkmk_createRequiredRecords). Consulta al usuario para la comprobación de esta operación, después itera a través de la colección `entityUris` e intenta eliminar cada elemento con un mensaje HTTP DELETE.  
  
### <a name="see-also"></a>Vea también  

[Usar para la API web de Common Data Service for Apps](overview.md)<br />
[Ejemplos de la API web](web-api-samples.md)<br />
[Ejemplos de la API web (JavaScript del lado del cliente)](web-api-samples-client-side-javascript.md)<br />
[Ejemplo de operaciones básicas de la API web (C#)](samples/basic-operations-csharp.md)<br />
[Ejemplo de datos de consulta API (C#)](samples/query-data-csharp.md)<br />
[Ejemplo de operaciones condicionales de la API web (C#)](samples/conditional-operations-csharp.md)<br />
[Ejemplo de funciones y acciones de la API web (C#)](samples/functions-actions-csharp.md)
