---
title: 'Ejemplo de inicio rápido: Recuperar entornos de Common Data Service mediante la API de administración en línea| MicrosoftDocs'
description: En el ejemplo de C# se muestra cómo autenticarse en la API de Online Management y recuperar todos los entornos de Common Data Service del inquilino de Office 365.
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: conceptual
ms.assetid: 63600a55-a1f0-491f-83f6-b3252566d27e
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
- developer
search.app:
- PowerApps
ms.openlocfilehash: 8b900ff8a1d4eae9664289cdcb96e53a453579ad
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749704"
---
# <a name="quick-start-sample-retrieve-common-data-service-environements-using-online-management-api"></a>Ejemplo de inicio rápido: Recuperar entornos de Common Data Service mediante la API de administración en línea 

En el ejemplo de C# se muestra cómo autenticarse en la API de Online Management y recuperar todos los entornos de Common Data Service del inquilino de Office 365.

En este ejemplo se usa el [código auxiliar](sample-authentication-helper.md) de la autenticación para poder autenticarse fácilmente en la API de Online Management mediante el protocolo OAuth 2.0 y poder pasar el token de acceso en la cabecera que quiera.

## <a name="what-this-sample-does"></a>¿Qué hace este ejemplo?

Este ejemplo realiza las siguientes tareas:

1. Utiliza el método **ConnectToAPI** para conectarse a la API de Online Management.

    a. Llama al método **DiscoverAuthority** en el código auxiliar de autenticación y los pasa la dirección URL del servicio para recopilar información de autoridad.

    b. Usa una instancia HttpClient para conectarse al servicio de la API de Online Management.

    c. Especifica la dirección base del servicio de API y el período de tiempo de ejecución máximo.
1. Utiliza el método **RetrieveInstancesAsync** para ejecutar una solicitud de HTTP para recuperar todas las instancias de Customer Engagement del inquilino de Office 365, y después muestra la respuesta.

## <a name="run-this-sample"></a>Ejecute este ejemplo
Para poder ejecutar este ejemplo, asegúrese de que tiene:
- Uno de los roles de administrador del inquilino de Office 365. Consulte [Roles de administración de Office 365](get-started-online-management-api.md#office-365-admin-roles)
- Visual Studio 2015 o posterior; es necesario tener una conexión a Internet para descargar o restaurar los ensamblados del paquete de NuGet.
- .NET Framework 4.6.2

Para ejecutar el ejemplo:
1. [Descargue](https://code.msdn.microsoft.com/Sample-Retrieve-Customer-94e4076d) el ejemplo y extráigalo.
2. Haga doble clic en el archivo de solución de Visual Studio (.sln) en la carpeta de C# en la ubicación extraída para abrir la solución en Visual Studio.
3. En el archivo **Programs.cs**, especifique otra dirección URL del servicio si la región no es Norte América. Para obtener una lista de los valores de direcciones URL de servicio en todas las regiones del mundo, consulte [Dirección URL de servicio](get-started-online-management-api.md#service-url).
    ```csharp
    //TODO: Change this value if your Office 365 tenant is in a different region than North America

    private static string _serviceUrl = "https://admin.services.crm.dynamics.com";
    ```
4. En el archivo **HelperCode** > **AuthenticationHelper.cs**, actualice los valores de `_clientId` y `_redirectURL` de forma adecuada.

    ```csharp
    // TODO: Substitute your app registration values here.
    // These values are obtained on registering your application with the 
    // Azure Active Directory.
    private static string _clientId = "<GUID>";    //e.g. "e5cf0024-a66a-4f16-85ce-99ba97a24bb2"
    private static string _redirectUrl = "<Url>";  //e.g. "app://e5cf0024-a66a-4f16-85ce-99ba97a24bb2"
    ```
5. Para guardar los cambios e iniciar la depuración, presione F5 o seleccione **Depuración** > **Iniciar depuración**.

## <a name="code-sample-listing"></a>Listado del código de ejemplo 

Este es el código de ejemplo completo:

```csharp
using Microsoft.Crm.Sdk.Samples.HelperCode;
using System;
using System.Net.Http;
using System.Threading.Tasks;


namespace Microsoft.Crm.Sdk.Samples
{
    /// <summary>
    /// This sample retrieves Customer Engagement instances
    /// in your Office 365 tenant.
    /// </summary>    

    class RetrieveInstances
    {
        private HttpClient httpClient;

        //TODO: Change this value if your Office 365 tenant is in a different region than North America
        private static string _serviceUrl = "https://admin.services.crm.dynamics.com";

        private void ConnectToAPI()
        {
            Console.WriteLine("Connecting to the Online Management API service...");

            // Discover authority for the Online Management API service
            var authority = Authentication.DiscoverAuthority(_serviceUrl);

            // Authenticate to the Online Management API service by 
            // passing in the discovered authority 
            Authentication auth = new Authentication(authority.Result.ToString());            

            // Use an HttpClient object to connect to Online Management API service.           
            httpClient = new HttpClient(auth.ClientHandler, true);

            // Specify the API service base address and the max period of execution time 
            httpClient.BaseAddress = new Uri(_serviceUrl);
            httpClient.Timeout = new TimeSpan(0, 2, 0);            
        }

        public async Task RetrieveInstancesAsync()
        {
            HttpRequestMessage myRequest = new HttpRequestMessage(HttpMethod.Get, "/api/v1.1/instances");
            HttpResponseMessage myResponse = await httpClient.SendAsync(myRequest);

            if (myResponse.IsSuccessStatusCode)
            {
                var result = myResponse.Content.ReadAsStringAsync().Result;
                Console.WriteLine("Your instances retrieved from Office 365 tenant: \n{0}", result);
            }
            else
            {
                Console.WriteLine("The request failed with a status of '{0}'",
                       myResponse.ReasonPhrase);
            }
        }

        static public void Main(string[] args)
        {
            RetrieveInstances app = new RetrieveInstances();
            try
            {
                // Connect to the Online Management API. 
                app.ConnectToAPI();

                // Run your request
                Task.WaitAll(Task.Run(async () => await app.RetrieveInstancesAsync()));
            }
            catch (System.Exception ex) { DisplayException(ex); }
            finally
            {
                if (app.httpClient != null)
                { app.httpClient.Dispose(); }
                Console.WriteLine("Press <Enter> to exit the program.");
                Console.ReadLine();
            }
        }

        /// <summary> Helper method to display exceptions </summary> 
        private static void DisplayException(Exception ex)
        {
            Console.WriteLine("The application terminated with an error.");
            Console.WriteLine(ex.Message);
            while (ex.InnerException != null)
            {
                Console.WriteLine("\t* {0}", ex.InnerException.Message);
                ex = ex.InnerException;
            }
        }
    }
}
```

### <a name="related-topics"></a>Temas relacionados  

[Introducción a la API de Online Management](get-started-online-management-api.md)

[Operaciones compatibles con la API Online Management](operations-supported.md)

[Referencia de la API de Online Management](/rest/api/admin.services.crm.dynamics.com)
