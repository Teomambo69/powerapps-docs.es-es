---
title: 'Inicio rápido: Ejemplo de API web (C#) (Common Data Service)| Microsoft Docs'
description: Este ejemplo muestra cómo autenticarse con un servidor Common Data Service y luego llamar a una operación básica de API Web, la función WhoAmI.
ms.custom: ''
ms.date: 02/02/2019
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
ms.reviewer: susikka
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 995fbc4e4d21549d59c5d1c135fd7448c8abedc0
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753688"
---
# <a name="quick-start-web-api-sample-c"></a>Tutorial: Ejemplo de API Web (C#)

En este tutorial creará una aplicación de consola básica para conectarse al entorno de Common Data Service usando la API web. 

Se autenticará y usará un <xref:System.Net.Http.HttpClient> para enviar una solicitud `GET` al <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /> y la respuesta será un <xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" />. Se mostrará el valor de propiedad `UserId`.

> [!NOTE]
> Esto es un ejemplo muy sencillo para mostrar cómo estar conectado con un mínimo de código. El siguiente [inicio rápido mejorado](enhanced-quick-start.md) se basará en este ejemplo para aplicar mejores patrones de diseño.

## <a name="prerequisites"></a>Requisitos previos

 - Visual Studio (2017 recomendada)
 - Conexión a Internet
 - Cuenta de usuario válida para una instancia de Common Data Service
    - Su nombre de usuario
    - Su contraseña
 - Dirección URL al entorno de Common Data Service con el que quiere conectarse
 - Comprensión básica de lenguaje Visual C#

> [!NOTE]
> Para la autenticación, debe tener una aplicación registrada en Azure Active Directory. Este ejemplo de tutorial proporciona un valor `clientid` de registro de la aplicación que puede usar con el fin de ejecutar el código de instalación publicado por Microsoft. Para sus propias aplicaciones debe registrar sus aplicaciones. Más información: [Tutorial: Registrar una aplicación con Azure Active Directory](../walkthrough-register-app-azure-active-directory.md).

## <a name="create-visual-studio-project"></a>Crear proyecto de Visual Studio

1. Crear un nuevo proyecto de aplicación de consola (.NET Framework) mediante **.NET Framework 4.6.2**

    ![Inicie un proyecto de aplicación de consola](../media/quick-start-web-api-console-app-csharp-1.png)

    > [!NOTE]
    > Este captura de pantalla muestra el nombre `WebAPIQuickStart`, pero puede elegir el nombre del proyecto y la solución que desee.

    > [!IMPORTANT]
    > **Problema conocido de Visual Studio 2015**
    > 
    > Cuando se ejecuta el proyecto/solución en VS 2015 en modo de depuración, es posible que no pueda conectarse. Esto ocurre independientemente de si está usando un marco de destino de 4.6.2 o más alto. Esto puede producirse porque el proceso de hospedaje de Visual Studio se compila con .NET 4.5, lo que significa de forma predeterminada que no es compatible con TLS 1.2. Puede deshabilitar el proceso de hospedaje de Visual Studio como solución. 
    >
    > Haga clic con el botón derecho del mouse en el nombre del proyecto en Visual Studio y luego haga clic en **Propiedades**. En la pestaña **Depuración** puede desactivar la opción **Habilitar proceso de hospedaje de Visual Studio**. 
    >
    > Esto afecta solo a la experiencia de depuración en VS 2015. Esto no afecta a los archivos binarios o ejecutables que se crean. El mismo problema no se produce en Visual Studio 2017.

1. En el **Explorador de soluciones** haga clic con el botón secundario en el proyecto que ha creado y seleccione **Administrar paquetes de NuGet...** en el menú contextual.

    ![Agregar paquete de NuGet](../media/quick-start-web-api-console-app-csharp-2.png)

1. Busque el paquete de `Microsoft.IdentityModel.Clients.ActiveDirectory` NuGet.
1. Seleccione **Versión** 2.29.0 e instálelo.

    ![Instale el paquete NuGet Microsoft.IdentityModel.Clients.ActiveDirectory](../media/quick-start-web-api-console-app-csharp-3.png)

    > [!IMPORTANT]
    > **No instale la versión más reciente de este paquete de NuGet.**
    >
    > Este ejemplo depende de la capacidad de pasar las credenciales de usuario sin un diálogo de Azure distinto del inicio de sesión, algo no disponible en la versión 3.x de esta biblioteca.

    > [!NOTE]
    > Debe seleccionar **Acepto** en el diálogo **Aceptación de licencia**.

1. Busque el paquete `Newtonsoft.Json` NuGet e instale la versión más reciente.

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
    Para obtener el valor `url`:

    1. En el sitio [https://make.powerapps.com](https://make.powerapps.com) con el entorno adecuado seleccionado, seleccione **Configuración** ![botón Configuración](media/settings-icon.png) y elija **Personalización avanzada**. A continuación, seleccione **Recursos de desarrollador**.
    1. En la página **Recursos de desarrollador**, busque el valor **Instancia de API web** y cópielo. 

        Debería tener aspecto similar a `https://yourorgname.api.crm.dynamics.com/api/data/v9.1/`. Pero para este ejemplo, debe cortar de la parte final (`/api/data/v9.1/`) para que solo sea `https://yourorgname.api.crm.dynamics.com`.

    Para las variables `userName` y `password`, use las mismas credenciales que usa para registrarse en el sitio [https://make.powerapps.com](https://make.powerapps.com).

## <a name="run-the-program"></a>Ejecute el programa.

1. Pulse F5 para ejecutar el programa. Los resultados deberán tener un aspecto similar al siguiente:

    ```
    Your UserId is 969effb0-98ae-478c-b547-53a2968c2e75
    Press any key to exit.
    ```

### <a name="congratulations"></a>Enhorabuena.

Se ha conectado con éxito a la API web.

El ejemplo de inicio rápido muestra un enfoque básico para crear un proyecto de Visual Studio sin ningún control de las excepciones o sin método para actualizar el token de acceso. 

Es suficiente para comprobar que puede conectarse, pero no constituye un buen patrón de generar una aplicación.

El tema del [inicio rápido mejorado](enhanced-quick-start.md) muestra cómo implementar los métodos de control de excepciones, el método de autenticación básica mediante una cadena de conexión, un método reutilizable para obtener acceso a los tokens y, además, presenta cómo crear métodos reutilizables para realizar operaciones de datos.

## <a name="next-steps"></a>Pasos siguientes

Aprenda a estructurar el código para crear mejores diseños.

> [!div class="nextstepaction"]
> [Inicio rápido mejorado](enhanced-quick-start.md)<br/>
