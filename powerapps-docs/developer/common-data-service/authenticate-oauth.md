---
title: Usar OAuth con Common Data Service (Common Data Service) | Microsoft Docs
description: Aprenda cómo autenticarse mediante OAuth con Common Data Service
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a0777bcb4f67a01a894600176bd68ec3793034c4
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753068"
---
# <a name="use-oauth-with-common-data-service"></a>Usar OAuth con Common Data Service

[OAuth 2.0](https://oauth.net/2/) es el protocolo estándar de la industria para autorizaciones. Después de que las personas proporcionan las credenciales para autenticarse, OAuth determina si están autorizadas para acceder a los recursos.

Las aplicaciones cliente deben admitir el uso de OAuth para el acceso a los datos mediante la API web. OAuth habilita la autenticación en dos fases (2FA) o autenticación basada en certificados para escenarios de aplicación entre servidores.

OAuth requiere un proveedor de identidad para la autenticación. Para Common Data Service el proveedor de identidad es Azure Active Directory (AAD). Para autenticarse con AAD usando una cuenta de trabajo o centro educativo de Microsoft, use Azure Active Directory Authentication Libraries (ADAL).

> [!NOTE]
> Este tema introducirá los conceptos comunes relacionados con la conexión con Common Data Service mediante OAuth con las bibliotecas de ADAL. Este contenido se centrará en la forma en que un programador puede conectarse a Common Data Service pero no en el funcionamiento interno de OAuth ni en las bibliotecas de ADAL. Si desea obtener más información sobre autencación, consulte la documentación de Azure Active Directory. [¿Qué es la autenticación?](/azure/active-directory/develop/authentication-scenarios) es un buen punto de inicio.
>
>Los ejemplos que proporcionamos se preconfiguran con los valores apropiados de registro para que pueda ejecutarlos sin generar su propio registro de la aplicación. Al publicar sus propias aplicaciones, debe usar sus propios valores de registro.

## <a name="app-registration"></a>Registro de aplicaciones

Al conectarse con OAuth primero debe registrar una aplicación en su inquilino de Azure AD. Cómo debe registrar la aplicación depende del tipo de aplicación que desee crear.

En todos los casos, comience con los pasos básicos para registrar una aplicación descrita en el tema de AAD: [Inicio rápido: Registrar una aplicación en el extremo Azure Active Directory v1.0](/azure/active-directory/develop/quickstart-v1-add-azure-ad-app). Para consultar instrucciones específicas de Common Data Service, consulte [Tutorial: Registrar una aplicación con Azure Active Directory > Crear un registro de la aplicación](walkthrough-register-app-azure-active-directory.md#create-an-application-registration).

Las opciones que deberá tomar en este paso dependen principalmente de la opción de tipo de aplicación.

### <a name="types-of-app-registration"></a>Tipos de registro de la aplicación

Cuando registra una aplicación con Azure AD una de las decisiones que debe tomar es el tipo de aplicación. Hay dos tipos de aplicación que puede registrar:

|Tipo de aplicación|Descripción|
|--|--|
|Aplicación web/API|**Cliente web**<br />Tipo de [aplicación cliente](/azure/active-directory/develop/developer-glossary#client-application) que ejecuta todos los códigos en un servidor web.<br /><br />**Cliente basado en usuario-agente**<br />Tipo de [aplicación cliente](/azure/active-directory/develop/developer-glossary#client-application) que descarga código desde un servidor web y se ejecuta en un agente de usuario (por ejemplo, explorador web), como una aplicación de una sola página (SPA). 
|
|Modo nativo de |Tipo de [aplicación cliente](/azure/active-directory/develop/developer-glossary#client-application) que está instalada nativamente en un dispositivo. |

Cuando selecciona **Aplicación web/API** debe proporcionar una **Dirección URL de inicio de sesión** que es la dirección URL a la que Azure AD enviará la respuesta de autenticación, incluido un símbolo (token) si la autenticación se realiza correctamente. Mientras desarrolla una aplicación, esta opción se establece normalmente en `https://localhost/appname:[port]` por lo que puede desarrollar y depuración su aplicación localmente. Al publicar la aplicación, necesita cambiar este valor en la dirección URL publicada de la aplicación.

Cuando selecciona **Nativo**, debe proporcionar el identificador uniforme de recursos URI de una redirección. Es un identificador único al que Azure AD redirigirá el agente de usuario en una solicitud de OAuth 2.0. Esto suele ser un valor con un formato similar al siguiente: `//app:<guid>`. 

### <a name="giving-access-to-common-data-service"></a>Conceder acceso a Common Data Service

Si su aplicación va a ser un cliente que permite al usuario autenticado realizar operaciones, debe configurar la aplicación para que tenga Access Dynamics 365 como permiso delegado de los usuarios de la organización.

Para ver los pasos específicos necesarios para hacerlo, consulte [Tutorial: Registrar una aplicación con Azure Active Directory > Aplicar permisos](walkthrough-register-app-azure-active-directory.md).

<!-- TODO Verify this -->
 Si su aplicación va a usar la autenticación entre servidores (S2S), este paso no es obligatorio. Esa configuración requiere un usuario del sistema específico y las operaciones se realizarán por la cuenta de ese usuario en lugar de cualquier usuario que tenga que ser autenticado.

### <a name="enable-implicit-flow"></a>Habilitar flujo implícito

Si está configurando una aplicación para una aplicación de una sola página (SPA) debe editar el manifiesto para establecer el valor `oauth2AllowImplicitFlow` en `true`. Más información: [Tutorial: Registrar y configurar una aplicación SPA con adal.js](walkthrough-registering-configuring-simplespa-application-adal-js.md)

### <a name="use-client-secrets--certificates"></a>Uso de Secretos y certificados del cliente

En los escenarios entre servidores, no aparecerá una cuenta de usuario interactiva para la autenticación. En estos casos, debe proporcionar algunos medios de confirmar que la aplicación es de confianza. Esto se realiza con secretos o certificados del cliente.

Para aplicaciones que se registran con el tipo de aplicación **Aplicación web/API**, puede configurar secretos. Estos se establecen utilizando el área **Teclas** de **Acceso de API** en **Configuración** para el registro de la aplicación. 

Para ambos tipos de aplicación, puede cargar un certificado.

Más información: [Conectar como aplicación](#connect-as-an-app)

## <a name="use-adal-libraries-to-connect"></a>Uso de bibliotecas de ADAL para conectar

Use una de las bibliotecas cliente de Azure Active Directory Authentication Libraries (ADAL) admitidas por Microsoft. [Bibliotecas de autenticación de Azure Active Directory > Bibliotecas cliente admitidas por Microsoft](/azure/active-directory/develop/active-directory-authentication-libraries#microsoft-supported-client-libraries).

Estas bibliotecas están disponibles para varias plataformas como se muestra en la tabla siguiente:

|Plataforma|Biblioteca|
|--|--|
|Cliente de .NET, Windows Store, UWP, Xamarin |ADAL .NET v3|
|Cliente de .NET, Windows Store, Windows Phone 8.1|ADAL .NET v2|
|JavaScript|ADAL.js|
|iOS, macOS|ADAL|
|Android|ADAL|
|Node.js|ADAL|
|Java|ADAL4J|
|Python|ADAL|

> [!NOTE]
> Actualmente, todos nuestros ejemplos usan las bibliotecas de cliente de .NET excepto para [Usar OAuth con uso compartido de recursos entre orígenes para conectar una aplicación de una sola página](oauth-cross-origin-resource-sharing-connect-single-page-application.md) que usa la biblioteca de JavaScript ADAL.js.

## <a name="adal-net-client-library-versions"></a>Versiones de biblioteca de cliente de ADAL .NET

Common Data Service admite autenticación de aplicaciones con el extremo de la API web mediante el protocolo de OAuth 2.0. Azure Active Directory Authentication Library (ADAL) es la interfaz de API recomendada al protocolo para sus aplicaciones .NET personalizadas. ADAL v2.x es compatible desde hace tiempo con nuestras API de SDK y de hecho muchos ejemplos de código de SDK usan esa versión de la biblioteca. Cuando ADAL v3 se publicó, se introdujo un cambio importante porque las credenciales de usuario podrían no pasar ya en llamadas ADAL API para mejorar la seguridad de la aplicación.

Para sus aplicaciones .NET personalizadas, use ADAL v2 o mayor para autenticación de la aplicación con el extremo de la API web. Cuando usa API de XrmTooling encontrados en el paquete [Microsoft.CrmSdk.XrmTooling.CoreAssembly](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CoreAssembly/) NuGet, la versión correcta de la biblioteca de ADAL se importará automáticamente en el proyecto de Visual Studio. Tenga en cuenta que la transición de ADAL v2 a ADAL v3 en las API XrmTooling se produjo en el paquete [v9.1.0.13](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CoreAssembly/9.1.0.13) NuGet. Consulte las notas de la versión del paquete para información detallada.  

Para ver un ejemplo de código usando la biblioteca ADAL v3 consulte: [Ejemplo de WhoAmI de ADAL v3](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/ADALV3WhoAmI/ADALV3WhoAmI).

## <a name="use-the-accesstoken-with-your-requests"></a>Use el AccessToken con sus solicitudes

El objetivo de usar las bibliotecas de ADAL es obtener un símbolo que pueda incluir con las solicitudes. Esto requiere solo unas líneas de código y solo unas cuantas líneas más para configurar un HttpClient para ejecutar una solicitud.

### <a name="simple-example"></a>Ejemplo sencillo:

A continuación se presenta la cantidad mínima de código necesaria para ejecutar una sola solicitud de web Api, pero no es el método recomendado. Esto es un ejemplo de ADAL v2 debido al uso de las credenciales de cliente:

```csharp
class SampleProgram
{
    private static string serviceUrl = "https://yourorg.crm.dynamics.com"; 
    private static string clientId = "51f81489-12ee-4a9e-aaae-a2591f45987d"; 
    private static string userName = "you@yourorg.onmicrosoft.com";
    private static string password = "yourpassword";

    static void Main(string[] args)
    {

        AuthenticationContext authContext = 
        new AuthenticationContext("https://login.microsoftonline.com/common", false);  
        UserCredential credential = new UserCredential(userName, password);
        AuthenticationResult result = authContext.AcquireToken(serviceUrl, clientId, credential);
        //The access token
        string accessToken = result.AccessToken;

        using (HttpClient client = new HttpClient()) {
        client.BaseAddress = new Uri(serviceUrl);
        client.Timeout = new TimeSpan(0, 2, 0);  //2 minutes  
        client.DefaultRequestHeaders.Add("OData-MaxVersion", "4.0");
        client.DefaultRequestHeaders.Add("OData-Version", "4.0");
        client.DefaultRequestHeaders.Accept.Add(
            new MediaTypeWithQualityHeaderValue("application/json"));
        HttpRequestMessage request = 
            new HttpRequestMessage(HttpMethod.Get, "/api/data/v9.0/WhoAmI");
        //Set the access token
        request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", accessToken);
        HttpResponseMessage response = client.SendAsync(request).Result;
        if (response.IsSuccessStatusCode)
        {
            //Get the response content and parse it.  
            JObject body = JObject.Parse(response.Content.ReadAsStringAsync().Result);
            Guid userId = (Guid)body["UserId"];
            Console.WriteLine("Your system user ID is: {0}", userId);
        }

    }
}
```

Este método sencillo no es un buen patrón que deba seguirse, porque el `AccessToken` expirará aproximadamente en una hora. Las bibliotecas de ADAL almacenarán en memoria caché el símbolo en su nombre y lo actualizarán cada vez que se llame al método `AcquireToken`.

### <a name="example-demonstrating-a-delegatinghandler"></a>Ejemplo que demuestra un DelegatingHandler

El método recomendado consiste en implementar una clase derivada de <xref:System.Net.Http.DelegatingHandler>, que se pasará al constructor del <xref:System.Net.Http.HttpClient>. Este controlador le permite invalidar el método <xref:System.Net.Http.HttpClient>.<xref:System.Net.Http.HttpClient.SendAsync*> para que ADAL llame al método `AcquireToken` con cada solicitud enviada por el cliente de http.

A continuación se presenta un ejemplo de una clase personalizada derivada de <xref:System.Net.Http.DelegatingHandler>.

```csharp
  /// <summary>  
  ///Custom HTTP message handler that uses OAuth authentication thru ADAL.  
  /// </summary>  
  class OAuthMessageHandler : DelegatingHandler
  {
    private UserCredential _credential;
    private AuthenticationContext _authContext = 
      new AuthenticationContext("https://login.microsoftonline.com/common", false);
    private string _clientId;
    private string _serviceUrl;

    public OAuthMessageHandler(string serviceUrl, string clientId, string userName, string password,
            HttpMessageHandler innerHandler)
        : base(innerHandler)
    {
      _credential = new UserCredential(userName, password);
      _clientId = clientId;
      _serviceUrl = serviceUrl;
    }

    protected override Task<HttpResponseMessage> SendAsync(
             HttpRequestMessage request, System.Threading.CancellationToken cancellationToken)
    {
      try
      {
        request.Headers.Authorization =
        new AuthenticationHeaderValue("Bearer", _authContext.AcquireToken(_serviceUrl, _clientId, _credential).AccessToken);
      }
      catch (Exception ex)
      {
        throw ex;
      }      
      return base.SendAsync(request, cancellationToken);
    }
  }
```

Mediante esta clase `OAuthMessageHandler`, el programa sencillo que se muestra arriba parecería esto, con alguna gestión de errores adicional incluida:

```csharp
class SampleProgram
{
    private static string serviceUrl = "https://yourorg.crm.dynamics.com"; 
    private static string clientId = "51f81489-12ee-4a9e-aaae-a2591f45987d"; 
    private static string userName = "you@yourorg.onmicrosoft.com";
    private static string password = "yourpassword";

    static void Main(string[] args)
    {
       HttpMessageHandler messageHandler;

      try
      {
        messageHandler = new OAuthMessageHandler(serviceUrl, clientId, userName, password,
                         new HttpClientHandler());
        //Create an HTTP client to send a request message to the CRM Web service.  
        using (HttpClient client = new HttpClient(messageHandler))
        {
          //Specify the Web API address of the service and the period of time each request   
          // has to execute.  
          client.BaseAddress = new Uri(serviceUrl);
          client.Timeout = new TimeSpan(0, 2, 0);  //2 minutes
          client.DefaultRequestHeaders.Add("OData-MaxVersion", "4.0");
          client.DefaultRequestHeaders.Add("OData-Version", "4.0");
          client.DefaultRequestHeaders.Accept.Add(
              new MediaTypeWithQualityHeaderValue("application/json"));

          //Send the WhoAmI request to the Web API using a GET request.   
          var response = client.GetAsync("api/data/v9.0/WhoAmI",
                  HttpCompletionOption.ResponseHeadersRead).Result;
          if (response.IsSuccessStatusCode)
          {
            //Get the response content and parse it.  
            JObject body = JObject.Parse(response.Content.ReadAsStringAsync().Result);
            Guid userId = (Guid)body["UserId"];
            Console.WriteLine("Your system user ID is: {0}", userId);
          }
          else
          {
            throw new Exception(response.ReasonPhrase);
          }
        }
      }
      catch (Exception ex)
      {
        DisplayException(ex);
      }
    }

    /// <summary> Displays exception information to the console. </summary>  
    /// <param name="ex">The exception to output</param>  
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
```

Aunque este ejemplo use <xref:System.Net.Http.HttpClient>.<xref:System.Net.Http.HttpClient.GetAsync*> en lugar del <xref:System.Net.Http.HttpClient.SendAsync*> reemplazado, solicitará todos los métodos de <xref:System.Net.Http.HttpClient> que envían una solicitud.

### <a name="discover-the-authority-at-run-time"></a>Detectar la autoridad en tiempo de ejecución

La URL de la autoridad de autenticación y la URL del recurso pueden determinarse de forma dinámica en tiempo de ejecución mediante el siguiente código de ADAL. Este es el método recomendado para usar en comparación con la URL ("https://login.microsoftonline.com/common") de autoridad conocida que se mostraba anteriormente en un fragmento de código.  
  
```csharp    
AuthenticationParameters ap = AuthenticationParameters.CreateFromResourceUrlAsync(  
                        new Uri("https://mydomain.crm.dynamics.com/api/data/")).Result;  
  
String authorityUrl = ap.Authority;  
String resourceUrl  = ap.Resource;  
```  
  
Para la API web, otra forma de obtener la URL de autoridad es enviar cualquier solicitud de mensaje al servicio web sin especifiar ningún token de acceso. Esto se conoce como *desafío del portador*. La respuesta se puede analizar para obtener la URL de autoridad.  
  
```csharp  
httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", "");  
```  

## <a name="connect-as-an-app"></a>Conectar como aplicación

Algunas aplicaciones que va a crear no están previstas para ser ejecutadas recíprocamente por un usuario. Por ejemplo, es posible que desee crear una aplicación cliente web que pueda realizar operaciones en datos de Common Data Service, o una aplicación de consola que realice una tarea programada de algún tipo. 

Aunque puede llegar a realizar estos escenarios usando las credenciales de un usuario normal, la cuenta de ese usuario necesitaría usar una licencia de pago. Este no es el enfoque recomendado.

En estos casos puede crear un usuario de aplicación especial que está vinculado a una aplicación registrada de Azure Active Directory y usar la clave secreta configurada para la aplicación o cargar un certificado [X.509](https://www.itu.int/rec/T-REC-X.509/en). Otro ventaja de este método es que no consume una licencia de pago.

### <a name="requirements-to-connect-as-an-app"></a>Requisitos para conectarse como aplicación

Para conectarse como una aplicación necesitará:
 - Una aplicación registrada
 - Un usuario de Common Data Service vinculado a la aplicación registrada
 - Conectarse usando la clave secreta de la aplicación o una huella digital del certificado

#### <a name="register-your-app"></a>Registrar su aplicación

Al registrar una aplicación repite muchos de los pasos descritos en [Tutorial: Registrar una aplicación con Azure Active Directory](walkthrough-register-app-azure-active-directory.md), con las excepciones siguientes:

 - No es necesario conceder el permiso **Acceso a Dynamics 365 como usuarios de la organización**.
 
    Esta aplicación estará enlazada a una cuenta de usuario específica.

 - Debe configurar un secreto para el registro de la aplicación O cargar un certificado de clave pública.

Mientras registra la aplicación, seleccione la sección **Claves** en la página **Configuración**.

Para agregar un certificado:
1. Seleccione **Cargar clave pública**.
2. Seleccione el archivo que le gustaría cargar. Debe ser uno de los siguientes tipos de archivo: .cer, .pem, .crt.

Para agregar una contraseña:

1. Agregue una descripción para la clave.
2. Seleccionar una duración.
3. Seleccione **Guardar**. 

  La columna situada más a la derecha incluirá el valor de clave, después de guardar los cambios de configuración. Asegúrese de copiar la clave para usarla en el código de aplicación cliente, ya que no se puede obtener acceso a ella una vez que sale de esta página.

#### <a name="common-data-service-user-account-bound-to-the-registered-app"></a>Cuenta de usuario de Common Data Service vinculada a la aplicación registrada


Lo primero que debe hacer es crear un rol de seguridad personalizado que definirá qué acceso y privilegios esta cuenta tendrá dentro de la organización de Common Data Service. Más información: [Creación o configuración de un rol de seguridad personalizado](/power-platform/admin/database-security#create-or-configure-a-custom-security-role)

Después de crear el rol de seguridad personalizado, debe crear la cuenta de usuario que lo usará.

<!-- Almost exactly the same intructions below can be found in powerapps-docs\developer\common-data-service\use-multi-tenant-server-server-authentication.md -->

#### <a name="manually-create-a-common-data-service-application-user"></a>Cree manualmente un usuario de la aplicación de Common Data Service  

 El procedimiento para crear este usuario es diferente de crear un usuario con licencia. Lleve a cabo los pasos siguientes:  
  
1. Vaya a **Configuración** > **Seguridad** > **Usuarios**  
  
2. En la lista desplegable de vistas, seleccione **Usuarios de la aplicación**.  
  
3. Haga clic en **Nuevo**. A continuación compruebe que está usando el formulario **Usuario de la aplicación**.  
  
    Si no ve los campos **Identificador de la aplicación**, **URI del Id. la aplicación** e **Id. del objeto de Azure AD** en el formulario, debe seleccionar el formulario **Usuario de la aplicación** de la lista:  
  
   ![Seleccionar formulario de usuario de la aplicación](media/select-application-user-form.PNG "Seleccionar formulario de usuario de la aplicación")  
  
4. Agregue los valores correspondientes a los campos:  
  
   |Campo|Value|  
   |-----------|-----------|
   |**Nombre de usuario**| Un nombre para el usuario|
   |**Id. de aplicación**|El valor del Id. de la aplicación para la aplicación registrada con Azure AD.|  
   |**Nombre completo**|Nombre de la aplicación.|  
   |**Correo electrónico principal**|La dirección de correo electrónico del usuario.|  
  
    Los campos **URI del Id. de la aplicación** e **Id. del objeto de Azure AD** están bloqueados y no puede establecer los valores para estos campos.  
  
    Cuando crea un este usuario los valores de estos campos se recuperarán de Azure AD en función del valor de **Identificador de la aplicación** al guardar el usuario.  
  
5. Asocie el usuario de la aplicación con el rol de seguridad personalizado que creó.

#### <a name="connect-using-the-application-secret"></a>Conectar con el secreto de la aplicación

Si se está conectando mediante un secreto configurado para la aplicación, usará la clase <xref:Microsoft.IdentityModel.Clients.ActiveDirectory.ClientCredential> que pasa el `clientId` y el `clientSecret` en vez de un <xref:Microsoft.IdentityModel.Clients.ActiveDirectory.UserCredential> con parámetros `userName` y `password`.
```csharp
string serviceUrl = "https://yourorg.crm.dynamics.com";
string clientId = "<your app id>";
string secret = "<your app secret>";

AuthenticationContext authContext = new AuthenticationContext("https://login.microsoftonline.com/common", false);
ClientCredential credential = new ClientCredential(clientId, secret);

AuthenticationResult result = authContext.AcquireToken(serviceUrl, credential);

string accessToken = result.AccessToken;
```
#### <a name="connect-using-a-certificate-thumbprint"></a>Conectar con una huella digital del certificado

Si se está conectando mediante un certificado y el <xref:Microsoft.Xrm.Tooling.Connector>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> puede usar código como el siguiente:

```csharp
string CertThumbPrintId = "DC6C689022C905EA5F812B51F1574ED10F256FF6";
string AppID = "545ce4df-95a6-4115-ac2f-e8e5546e79af";
string InstanceUri = "https://yourorg.crm.dynamics.com";

string ConnectionStr = $@"AuthType=Certificate;
                        SkipDiscovery=true;url={InstanceUri};
                        thumbprint={CertThumbPrintId};
                        ClientId={AppID};
                        RequireNewInstance=true";
using (CrmServiceClient svc = new CrmServiceClient(ConnectionStr))
{
    if (svc.IsReady)
    {
    //your code goes here
    }

}
```


### <a name="see-also"></a>Vea también

[Autenticación con servicios web Common Data Service](authentication.md)<br />
[Autenticación con las aplicaciones de .NET Framework](authenticate-dot-net-framework.md)
