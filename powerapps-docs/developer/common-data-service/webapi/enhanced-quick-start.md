---
title: Inicio rápido mejorado (Common Data Service) | Microsoft Docs
description: Crear un nuevo proyecto en Visual Studio para compilar una aplicación de consola que utilice la API web de Common Data Service
ms.custom: ''
ms.date: 02/02/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 08377156-32c7-492a-8e66-50a47a330dc6
caps.latest.revision: 14
author: brandonsimons
ms.author: jdaly
manager: ''
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="enhanced-quick-start"></a>Inicio rápido mejorado

En este tema se muestra cómo corregir el código en el tema [Inicio rápido](quick-start-console-app-csharp.md) agregando un <xref:System.Net.Http.HttpClient> reutilizable y métodos de gestión de errores. Complete los pasos en el tema [Inicio rápido](quick-start-console-app-csharp.md) para crear un nuevo proyecto de Visual Studio antes de comenzar con este tema.

## <a name="enable-passing-credentials-in-a-connection-string"></a>Habilitar la transferencia de credenciales en una cadena de conexión

Ubicar las credenciales de usuario dentro del código de la forma en que se hizo en el ejemplo de [Inicio rápido](quick-start-console-app-csharp.md) no es una práctica recomendada. 

La forma de recopilar credenciales de usuario dependen del tipo de cliente que esté creando. Para esta aplicación de consola estableceremos las credenciales en `App.config` porque es una forma cómoda de mover las credenciales fuera del código. También es el método usado en [Ejemplos de operaciones de datos de API web (C#)](web-api-samples-csharp.md), por lo que si se entiende este método, puede ver fácilmente cómo funcionan los diferentes ejemplos.

Para habilitar son necesarios tres pasos:

1. [Agregar la referencia a System.Configuration para el proyecto de Visual Studio](#1-add-reference-to-systemconfiguration-to-the-visual-studio-project)
1. [Editar el archivo de configuración de aplicación](#2-edit-the-application-configuration-file)
1. [Agregar la instrucción using a Program.cs](#3-add-using-statement-to-programcs)


### <a name="add-reference-to-systemconfiguration-to-the-visual-studio-project"></a>Agregar la referencia a System.Configuration para el proyecto de Visual Studio

1. En el **Explorador de soluciones**, haga clic con el botón secundario en **Referencias** y seleccione **Agregar referencia...**.
1. En el cuadro de diálogo **Administrador de referencias** busque `System.Configuration` y active la casilla para agregar esta referencia al proyecto.
1. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Administrador de referencias**.
  
### <a name="edit-the-application-configuration-file"></a>Editar el archivo de configuración de aplicación

En el **Explorador de soluciones**, abra el archivo **App.config**. Debería tener aspecto similar a éste:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.2" />
    </startup>
</configuration>
```

Edite el elemento `<configuration>` el elemento para agregar al nodo `connectionStrings` como se indica a continuación:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.2" />
    </startup>
  <connectionStrings>
    <!--Online using Office 365-->
    <add name="Connect"
         connectionString="Url=https://yourorg.api.crm.dynamics.com;Username=yourname@yourorg.onmicrosoft.com;Password=y0urp455w0rd; />
  </connectionStrings>
</configuration>
```
Esto crea una cadena de conexión a la que se puede hacer referencia por el nombre, en este caso `Connect`, de modo que puede definir más de una conexión si lo desea.

Edite los valores `Url`, `Username` y `Password` de la cadena de conexión en `connectionString` para que coincidan con lo que necesita para conectarse al entorno de Common Data Service.

### <a name="add-using-statement-to-programcs"></a>Agregar la instrucción using a Program.cs

En la parte superior del archivo Program.cs, agregue esta instrucción using:

```csharp
using System.Configuration;
```

## <a name="add-helper-code"></a>Agregar código auxiliar

En el ejemplo [Inicio rápido](quick-start-console-app-csharp.md), todo el código está dentro del archivo `program.cs`. Vamos a mover el código que se ocupa de la conexión y la creación de un <xref:System.Net.Http.HttpClient> en un archivo independiente de métodos auxiliares. 

Estas aplicaciones auxiliares también se usan en [SampleHelper.cs](https://github.com/Microsoft/PowerApps-Samples/blob/master/cds/webapi/C%23/SampleHelpers.cs) que se usa en [Ejemplos de operaciones de datos de API web (C#)](web-api-samples-csharp.md). Si entiende estas aplicaciones auxiliares, comprenderá cómo se usan en los ejemplos.

1. En el **Explorador de soluciones**, haga clic en el proyecto y seleccione **Agregar** > **Clase…** (o presione `Shift`+`Alt`+`C`) para abrir el diálogo **Agregar nuevo elemento**.
1. Especifique un nombre para la clase. Para seguir el patrón que se usa en [Ejemplos de operaciones de datos de API web (C#)](web-api-samples-csharp.md), denomínela `SampleHelpers.cs`. 

    > [!NOTE]
    > El nombre de la clase determinará cómo se hará referencia a esas propiedades y métodos auxiliares en `Program.cs`. Las instrucciones restantes esperarán el nombre sea `SampleHelpers`, por lo que debe recordar el nombre si utilizó otro diferente.

1. Agregue las siguientes instrucciones `using`:

    ```csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    using System;
    using System.Linq;
    using System.Net.Http;
    using System.Net.Http.Headers;
    using System.Threading.Tasks;
    ```

1. Agregue las propiedades y métodos siguientes a la clase `SampleHelper`:

    ```csharp
    //These sample application registration values are available for all online instances.
    //You can use these while running sample code, but you should get your own for your own apps
    public static string clientId = "51f81489-12ee-4a9e-aaae-a2591f45987d";
    public static string redirectUrl = "app://58145B91-0C36-4500-8554-080854F2AC97";

    /// <summary>
    /// Method used to get a value from the connection string
    /// </summary>
    /// <param name="connectionString"></param>
    /// <param name="parameter"></param>
    /// <returns>The value from the connection string that matches the parameter key value</returns>
    public static string GetParameterValueFromConnectionString(string connectionString, string parameter)
    {
      try
      {
        return connectionString.Split(';').Where(s => s.Trim().StartsWith(parameter)).FirstOrDefault().Split('=')[1];
      }
      catch (Exception)
      {
        return string.Empty;
      }
    }

    /// <summary>
    /// Returns an HttpClient configured with an OAuthMessageHandler
    /// </summary>
    /// <param name="connectionString">The connection string to use.</param>
    /// <param name="clientId">The client id to use when authenticating.</param>
    /// <param name="redirectUrl">The redirect Url to use when authenticating</param>
    /// <param name="version">The version of Web API to use. Defaults to version 9.1 </param>
    /// <returns>An HttpClient you can use to perform authenticated operations with the Web API</returns>
    public static HttpClient GetHttpClient(string connectionString, string clientId, string redirectUrl, string version = "v9.1")
    {
      string url = GetParameterValueFromConnectionString(connectionString, "Url");
      string username = GetParameterValueFromConnectionString(connectionString, "Username");
      string password = GetParameterValueFromConnectionString(connectionString, "Password");
      try
      {
        HttpMessageHandler messageHandler = new OAuthMessageHandler(url, clientId, redirectUrl, username, password,
                      new HttpClientHandler());

        HttpClient httpClient = new HttpClient(messageHandler)
        {
          BaseAddress = new Uri(string.Format("{0}/api/data/{1}/", url, version)),

          Timeout = new TimeSpan(0, 2, 0)  //2 minutes
        };

        return httpClient;
      }
      catch (Exception)
      {
        throw;
      }
    }

    /// <summary> Displays exception information to the console. </summary>
    /// <param name="ex">The exception to output</param>
    public static void DisplayException(Exception ex)
    {
      Console.WriteLine("The application terminated with an error.");
      Console.WriteLine(ex.Message);
      while (ex.InnerException != null)
      {
        Console.WriteLine("\t* {0}", ex.InnerException.Message);
        ex = ex.InnerException;
      }
    }
    ```

1. Agregue la clase `OAuthMessageHandler` en el espacio de nombres del archivo `SampleHelpers.cs`.

    > [!NOTE]
    > No agregue esto dentro la clase `SampleHelpers`.

    Esta clase garantiza que el token de acceso se actualice cada vez que se realiza la operación. Cada token de acceso caducará después de aproximadamente una hora. Esta clase implementa un <xref:System.Net.Http.DelegatingHandler> que funcionará con el contexto de autenticación de Azure Active Directory Authentication Library (ADAL) para llamar al método `AquireToken` cada vez que se realice una operación, de modo que no necesita explícitamente administrar la caducidad del token.

    ```csharp
    /// <summary>
    ///Custom HTTP message handler that uses OAuth authentication thru ADAL.
    /// </summary>
    class OAuthMessageHandler : DelegatingHandler
    {
      private AuthenticationHeaderValue authHeader;

      public OAuthMessageHandler(string serviceUrl, string clientId, string redirectUrl, string username, string password,
              HttpMessageHandler innerHandler)
          : base(innerHandler)
      {
        // Obtain the Azure Active Directory Authentication Library (ADAL) authentication context.
        AuthenticationParameters ap = AuthenticationParameters.CreateFromResourceUrlAsync(
                new Uri(serviceUrl + "/api/data/")).Result;
        AuthenticationContext authContext = new AuthenticationContext(ap.Authority, false);
        //Note that an Azure AD access token has finite lifetime, default expiration is 60 minutes.
        AuthenticationResult authResult;
        if (username != string.Empty && password != string.Empty)
        {

          UserCredential cred = new UserCredential(username, password);
          authResult = authContext.AcquireToken(serviceUrl, clientId, cred);
        }
        else
        {
          authResult = authContext.AcquireToken(serviceUrl, clientId, new Uri(redirectUrl), PromptBehavior.Auto);
        }

        authHeader = new AuthenticationHeaderValue("Bearer", authResult.AccessToken);
      }

      protected override Task<HttpResponseMessage> SendAsync(
                HttpRequestMessage request, System.Threading.CancellationToken cancellationToken)
      {
        request.Headers.Authorization = authHeader;
        return base.SendAsync(request, cancellationToken);
      }
    }
    ```

## <a name="update-programcs"></a>Actualizar Program.cs

Ahora que ha hecho los cambios según [Habilitar la transferencia de credenciales en una cadena de conexión](#enable-passing-credentials-in-a-connection-string) y [Agregar código auxiliar](#add-helper-code), puede actualizar el método `Main` en `Program.cs` para que solo contenga lo siguiente:

```csharp
static void Main(string[] args)
{
  try
  {
    //Get configuration data from App.config connectionStrings
    string connectionString = ConfigurationManager.ConnectionStrings["Connect"].ConnectionString;

    using (HttpClient client = SampleHelpers.GetHttpClient(connectionString, SampleHelpers.clientId, SampleHelpers.redirectUrl))
    {
      // Use the WhoAmI function
      var response = client.GetAsync("WhoAmI").Result;

      if (response.IsSuccessStatusCode)
      {
        //Get the response content and parse it.  
        JObject body = JObject.Parse(response.Content.ReadAsStringAsync().Result);
        Guid userId = (Guid)body["UserId"];
        Console.WriteLine("Your UserId is {0}", userId);
      }
      else
      {
        Console.WriteLine("The request failed with a status of '{0}'",
                    response.ReasonPhrase);
      }
      Console.WriteLine("Press any key to exit.");
      Console.ReadLine();
    }
  }
  catch (Exception ex)
  {
    SampleHelpers.DisplayException(ex);
    Console.WriteLine("Press any key to exit.");
    Console.ReadLine();
  }
}
```

Es menos código y ha agregado la gestión de errores y los medios para actualizar el token de acceso con cada uso de `HttpClient`.

Pulse F5 para ejecutar el programa. Al igual que en el ejemplo [Inicio rápido](quick-start-console-app-csharp.md), el resultado debería tener este aspecto:

    ```
    Your UserId is 969effb0-98ae-478c-b547-53a2968c2e75
    Press any key to exit.
    ```

## <a name="create-re-usable-methods"></a>Crear métodos que pueden reutilizarse

Pese a que hemos reducido la cantidad total de código en el método `main` de `Program.cs`, no va a escribir un programa solo para invocar una operación y no es realista escribir tanto código solo para hacer esto.

Esta sección muestra cómo puede cambiar esto:

  ```csharp
  var response = client.GetAsync("WhoAmI").Result;

  if (response.IsSuccessStatusCode)
  {
    //Get the response content and parse it.  
    JObject body = JObject.Parse(response.Content.ReadAsStringAsync().Result);
    Guid userId = (Guid)body["UserId"];
    Console.WriteLine("Your UserId is {0}", userId);
  }
  else
  {
    Console.WriteLine("The request failed with a status of '{0}'",
        response.ReasonPhrase);
  }
  ```
a esto:

  ```csharp
  WhoAmIResponse response = WhoAmI(client);
        Console.WriteLine("Your system user ID is: {0}", response.UserId);
  ```

Antes de comenzar, es conveniente ir a la referencia de la API web y revisar estos temas:
- <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /> 
- <xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" />

Observe cómo <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /> devuelve un <xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" /> y <xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" /> contienen tres propiedades de `GUID`: `BusinessUnitId`, `UserId` y `OrganizationId`;

El código que agregaremos es simplemente para hacer que estos elementos pasen a ser un método reutilizable que acepte `HttpClient` como parámetro.

> [!NOTE]
> La forma exacta de hacerlo depende de sus preferencias personales. Este diseño se proporciona porque es relativamente sencillo.

En el proyecto de Visual Studio lleve a cabo los pasos siguientes:

1. Edite la clase `Program` para crear una clase parcial.

    En la parte superior, cambie lo siguiente:

    `class Program`

    A esto:

    `partial class Program`

1. Cree una nueva clase llamada `ProgramMethods.cs`.

    En `ProgramMethods.cs`, cambie esto:

    `class ProgramMethods`

    A esto:

    `partial class Program`

    De esta forma, la clase `Program` en el archivo `ProgramMethods.cs` solo será una extensión de la clase original `Program` en el archivo `Program.cs`. 

1. Agregue las instrucciones using siguientes a la parte superior del archivo `ProgramMethods.cs`.

    ```csharp
    using Newtonsoft.Json.Linq;
    using System;
    using System.Net.Http;
    ```

1. Agregue el siguiente método a la clase `Program` en el archivo `ProgramMethods.cs`.

    ```csharp
    public static WhoAmIResponse WhoAmI(HttpClient client) {
      WhoAmIResponse returnValue = new WhoAmIResponse();
      //Send the WhoAmI request to the Web API using a GET request. 
      HttpResponseMessage response = client.GetAsync("WhoAmI",
              HttpCompletionOption.ResponseHeadersRead).Result;
      if (response.IsSuccessStatusCode)
      {
          //Get the response content and parse it.
          JObject body = JObject.Parse(response.Content.ReadAsStringAsync().Result);
          returnValue.BusinessUnitId = (Guid)body["BusinessUnitId"];
          returnValue.UserId = (Guid)body["UserId"];
          returnValue.OrganizationId = (Guid)body["OrganizationId"];
      }
      else
      {
          throw new Exception(string.Format("The WhoAmI request failed with a status of '{0}'",
                  response.ReasonPhrase));
      }
      return returnValue;
    }
    ```

1. Agregue la clase siguiente fuera de la clase `Program`, pero en el mismo espacio de nombres del archivo `ProgramMethods.cs`.

    ```csharp
    public class WhoAmIResponse
    {
        public Guid BusinessUnitId { get; set; } 
        public Guid UserId { get; set; }
        public Guid OrganizationId { get; set; }
    }
    ```

1. En el método `main` de `Program` en el archivo original `Program.cs`:

    Reemplace esto:

    ```csharp
    var response = client.GetAsync("WhoAmI").Result;

    if (response.IsSuccessStatusCode)
    {
      //Get the response content and parse it.  
      JObject body = JObject.Parse(response.Content.ReadAsStringAsync().Result);
      Guid userId = (Guid)body["UserId"];
      Console.WriteLine("Your UserId is {0}", userId);
    }
    else
    {
      Console.WriteLine("The request failed with a status of '{0}'",
                  response.ReasonPhrase);
    }
    ```
    Con esto:

    ```csharp
    WhoAmIResponse response = WhoAmI(client);
    Console.WriteLine("Your system user ID is: {0}", response.UserId);
    ```

1. Presione la F5 para ejecutar el ejemplo y debería obtener los mismos resultados que antes.


## <a name="troubleshooting"></a>Solución de problemas

Si tiene problemas al ejecutar estos ejemplos, puede descargar todos los ejemplos de PowerApps del repositorio de GitHub en [https://github.com/Microsoft/PowerApps-Samples](https://github.com/Microsoft/PowerApps-Samples).

Este ejemplo se basa en [SimpleWebApi](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/SimpleWebApi) que se encuentra en la carpeta `PowerApps-Samples-master\PowerApps-Samples-master\cds\webapi\C#\SimpleWebApi`.

Debe poder abrir el archivo `SimpleWebApi.sln` en Visual Studio y ejecutar el ejemplo. Debería funcionar con usted siempre que tenga credenciales válidas.

> [!IMPORTANT]
> Todos los ejemplos del repositorio de GitHub están configurados para usar un común App.config que se encuentra en `PowerApps-Samples-master\cds\App.config`. Cuando establece la cadena de conexión debe editar este archivo. Al hacerlo, puede trabajar con todos los ejemplos sin configurar sus credenciales de nuevo.

## <a name="create-a-template-project"></a>Crear un proyecto como plantilla

Antes de salir de este tema, considere guardar el proyecto como una plantilla del proyecto. A continuación, puede volver a usar esa plantilla para futuros proyectos de aprendizaje y ahorrarse tiempo y esfuerzos para configurar nuevos proyectos. Para ello, mientras el proyecto está abierto en Microsoft Visual Studio, en el menú **Archivo**, seleccione **Exportar plantilla**. Siga las instrucciones del [Asistente para exportar plantilla](https://docs.microsoft.com/visualstudio/ide/how-to-create-project-templates) para crear la plantilla.  
  
## <a name="next-steps"></a>Pasos siguientes

Use los siguientes recursos para obtener más información:

> [!div class="nextstepaction"]
> [Realizar operaciones mediante la API web](perform-operations-web-api.md)<br /><br />
> [Intente realizar los ejemplos de operaciones de datos de API web (C#)](web-api-samples-csharp.md)<br /><br />
> [Consulte los ejemplos de API web (C#) en GitHub](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23)

