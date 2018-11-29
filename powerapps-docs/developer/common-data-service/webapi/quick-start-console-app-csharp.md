---
title: 'Tutorial: Ejemplo de web API (C#) (Common Data Service para aplicaciones) | Microsoft Docs'
description: 'Este ejemplo muestra cómo autenticarse con un servidor Common Data Service para aplicaciones y luego llamar a una operación básica de API Web, la función WhoAmI.'
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
# <a name="quick-start-web-api-sample-c"></a>Tutorial: Ejemplo de API Web (C#)

En este tutorial creará una aplicación de consola básica para conectarse al entorno de Common Data Service para aplicaciones usando la API web.

Se autenticará con OAuth2 y usará [HttpClient](/dotnet/api/system.net.http.httpclient) para enviar una solicitud `GET` a <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /> y la respuesta será un <xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" />. Se mostrará el valor de la propiedad `UserId`.

> [!NOTE]
> Este ejemplo de tutorial no incluye tratamiento de errores. Es un ejemplo mínimo de lo que necesita para conectarse y usar la API web.

## <a name="prerequisites"></a>Requisitos previos

 - Visual Studio (2017 recomendado)
 - Conexión a Internet
 - Una cuenta de usuario válida para la estancia de Common Data Service para aplicaciones
    - Su nombre de usuario
    - Su contraseña
 - Dirección URL a CDS del entorno de aplicaciones con el que quiere conectarse
 - Comprensión básica de lenguaje Visual C#

> [!NOTE]
> Para la autenticación mediante el uso de OAuth2 debe tener una aplicación registrada en Azure Active Directory. Este ejemplo de tutorial proporciona un valor de clientid del registro de la aplicación que puede usar con fin de ejecutar el código de instalación publicado por Microsoft. Para sus propias aplicaciones debe registrar sus aplicaciones. Más información: [Tutorial: Registrar una aplicación con Azure Active Directory](../walkthrough-register-app-azure-active-directory.md)

## <a name="create-visual-studio-project"></a>Crear proyecto en Visual Studio

1. Cree un nuevo proyecto de aplicación de consola (.NET Framework) mediante .NET Framework 4.6.2

    ![Inicie un proyecto de aplicación de consola](../media/quick-start-web-api-console-app-csharp-1.png)

    > [!NOTE]
    > Este captura de pantalla muestra el nombre `WebAPIQuickStart`, pero puede elegir el nombre del proyecto y la solución que desee. 

1. En el **Explorador de soluciones** haga clic con el botón secundario en el proyecto que ha creado y seleccione **Administrar paquetes de NuGet...** en el menú contextual.

    ![Agregar paquete de NuGet](../media/quick-start-web-api-console-app-csharp-2.png)

1. Busque el  el paquete de NuGet `Microsoft.IdentityModel.Clients.ActiveDirectory`.
1. Seleccione **Versión** 2.29.0 e instálelo.

    ![Instale el paquete NuGet Microsoft.IdentityModel.Clients.ActiveDirectory](../media/quick-start-web-api-console-app-csharp-3.png)

    > [!IMPORTANT]
    > **No instale la versión más reciente de este paquete de NuGet.**
    >
    > Este ejemplo depende de la capacidad de pasar las credenciales de usuario sin un diálogo de Azure distinto del inicio de sesión, algo no disponible en la versión 3.x de esta biblioteca.

    > [!NOTE]
    > Debe seleccionar **Acepto** en el diálogo **Aceptación de licencia**.

1. Busque el paquete de NuGet `Newtonsoft.Json` e instale la versión más reciente.

    ![Instale el paquete NuGet Microsoft.IdentityModel.Clients.ActiveDirectory](../media/quick-start-web-api-console-app-csharp-4.png)

## <a name="edit-programcs"></a>Edite Program.cs

1. Agregue estas instrucciones a la parte superior de `Program.cs`

    ```csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    using System.Net.Http.Headers;
    using System.Net.Http;
    using Newtonsoft.Json.Linq;
    ```

1. Reemplace el método `Main` con el siguiente:

    ```csharp
    static void Main(string[] args)
    {
        // Set these values:
        // e.g. https://yourorg.crm.dynamics.com
        string url = "<your environment url>";
        // e.g. you@yourorg.onmicrosoft.com
        string userName = "<your user name>";
        // e.g. y0urp455w0rd
        string password = "<your password>";

        // Azure Active Directory registered app clientid for Microsoft samples
        string clientId = "51f81489-12ee-4a9e-aaae-a2591f45987d";

        var userCredential = new UserCredential(userName, password);
        string apiVersion = "9.0";
        string webApiUrl = $"{url}/api/data/v{apiVersion}/";

        //Authenticate using IdentityModel.Clients.ActiveDirectory
        var authParameters = AuthenticationParameters.CreateFromResourceUrlAsync(new Uri(webApiUrl)).Result;
        var authContext = new AuthenticationContext(authParameters.Authority, false);
        var authResult = authContext.AcquireToken(url, clientId, userCredential);
        var authHeader = new AuthenticationHeaderValue("Bearer", authResult.AccessToken);

        using (var client = new HttpClient())
        {
            client.BaseAddress = new Uri(webApiUrl);
            client.DefaultRequestHeaders.Authorization = authHeader;

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
    ```

1. Edite los siguientes valores para agregar información para el entorno:

    ```csharp
    // e.g. https://yourorg.crm.dynamics.com
    string url = "<your environment url>";
    // e.g. you@yourorg.onmicrosoft.com
    string userName = "<your user name>";
    // e.g. y0urp455w0rd
    string password = "<your password>";
    ```

## <a name="run-the-program"></a>Ejecute el programa.

1. Pulse F5 para ejecutar el programa. Los resultados deberán tener un aspecto similar al siguiente:

    ```
    Your UserId is 969effb0-98ae-478c-b547-53a2968c2e75
    Press any key to exit.
    ```

### <a name="congratulations"></a>Enhorabuena.

Se ha conectado con éxito a la API web.

<!-- TODO: Include link to next steps topics -->