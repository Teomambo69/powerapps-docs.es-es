---
title: 'Código auxiliar de la API web: Clase de autenticación (Common Data Service para aplicaciones)| Microsoft Docs'
description: Clase de autenticación ayuda a establecer una conexión validada con un servicio web de Common Data Service para aplicaciones
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: a7b5931c-3142-4616-a331-1e07b4d8845d
caps.latest.revision: 11
author: brandonsimons
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-helper-code-authentication-class"></a>Código auxiliar de API web: Clase de autenticación

Utilice la clase `Authentication` para ayudar a establecer una conexión validada con un servicio web de Common Data Service para aplicaciones. Esta clase admite dos protocolos de autenticación: [Autenticación Windows](https://docs.microsoft.com/en-us/windows-server/security/windows-authentication/windows-authentication-overview) para Common Data Service para aplicaciones local o [OAuth 2.0](http://oauth.net/2/) para Common Data Service para aplicaciones (online) o implementaciones con conexión a Internet (IFD). Esta clase se basa en Microsoft Azure Active Directory Authentication Library ([ADAL](https://docs.microsoft.com/en-us/dotnet/api/microsoft.identitymodel.clients.activedirectory?view=azure-dotnet)) para controlar el protocolo OAuth.  
  
La clase `Authentication` se encuentra en el archivo Authentication.cs en la [Biblioteca de código auxiliar de la API web de CRM SDK](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode/). Está diseñada para funcionar conjuntamente con la jerarquía de clases auxiliares de `Configuration` para permitirle establecer una conexión segura con el servicio de Common Data Service para aplicaciones a través de un objeto de tipo System.Net.Http.[HttpMessageHandler](https://msdn.microsoft.com/library/hh138091\(v=vs.110\).aspx). Para obtener más información, consulte [Usar la biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md).  
  
## <a name="authentication-processing"></a>Procesamiento de autenticación
 
El mecanismo que la clase `Authentication` usa para autenticación con un servicio de Common Data Service para aplicaciones depende de la información que pasa en el constructor con el parámetro `Configuration`. Intenta crear un objeto derivado de HttpMessageHandlerque puede usar posteriormente para crear instancias de una instancia System.Net.Http.[HttpClient](https://msdn.microsoft.com/library/system.net.http.httpclient\(v=vs.110\).aspx) para ofrecer una sesión de comunicaciones segura y persistente con el servicio de Common Data Service para aplicaciones.  
  
 Primero se ejecuta un breve protocolo enlace de detección con el servicio especificado de Common Data Service para aplicaciones para determinar si se está usando la autenticación nativa de OAuth o de Windows.  
  
- Si se usa OAuth, se crea un objeto `OAuthMessageHandler` mediante la autoridad de autenticación que se detectó en el protocolo de enlace. Esta clase, derivada de System.Net.Http.[DelegatingHandler](/dotnet/api/system.net.http.delegatinghandler), actualiza el token de acceso de OAuth en cada solicitud, por lo que no es necesario administrar explícitamente la caducidad del token.  
  
- Si se usa la autenticación de Windows, y se proporcionan las credenciales de usuario, esas credenciales se usan para generar a un [HttpClientHandler](/dotnet/api/system.net.http.httpclienthandler).  
  
- Si se usa la autenticación de Windows, pero no se proporcionan las credenciales de usuario, se construye un HttpClientHandler usando credenciales de red predeterminadas.  
  
## <a name="class-hierarchy-and-members"></a>Jerarquía de clases e integrantes  
 La siguiente tabla muestra los integrantes públicos de la clase `Authentication`.  
<!-- TODO:  
|||  
|-|-|  
|![Common Data Service for Apps Web API Helper Library&#45;Authentication Class Diagram](../media/web-api-helper-library-authentication-class-diagram.png "Common Data Service for Apps Web API Helper Library-Authentication Class Diagram")|**Authentication class**<br /><br /> *Properties:*<br /><br /> `Authority` – the URL of the server that manages OAuth authentication.<br /><br /> `ClientHandler` – the [HttpMessageHandler](https://msdn.microsoft.com/library/hh138091\(v=vs.110\).aspx)-derived object that provides the network credentials or authorization access token for message requests.<br /><br /> `Context` – the [AuthenticationContext](https://msdn.microsoft.com/library/microsoft.identitymodel.clients.activedirectory.authenticationcontext.aspx) for an authentication event.<br /><br /> *Methods:*<br /><br /> `AquireToken` – For OAuth, returns an [AuthenticationResult](https://msdn.microsoft.com/library/microsoft.identitymodel.clients.activedirectory.authenticationresult.aspx),  containing the refresh and access tokens, for the current authentication context.<br /><br /> `Authentication` – Initializes an instance of this class using the `Configuration` parameter.<br /><br /> `DiscoverAuthority` – Discovers the authentication authority of the Common Data Service for Apps web service.<br /><br /> <br /><br /> **OAuthMessageHandler class**<br /><br /> This nested class sets the authorization header for each sent message for Common Data Service for Apps (online) and IFD deployments.|   -->
  
## <a name="usage"></a>Uso  
 Las clases `Configuration` y `Authentication` están diseñadas para usarse en tándem para establecer una conexión segura con el servicio de Common Data Service para aplicaciones de destino.  Primero cree un objeto de tipo `Configuration`, luego páselo como el único parámetro al constructor `Authentication`.  Después de la creación correcta, puede usar la propiedad `ClientHandler` para generar una conexión de cliente HTTP segura, autenticada y persistente al servicio de Common Data Service para aplicaciones.  
  
 Una forma común de realizar esta operación, que usan la mayoría de los ejemplos de C# de la API web, es usar la clase derivada `FileConfiguration` para leer información de conexión de los archivos de configuración aplicaciones correctamente creados, como se muestra en las siguientes líneas.  
  
```csharp  
  
FileConfiguration config = new FileConfiguration(null);  
Authentication auth = new Authentication(config);  
httpClient = new HttpClient(auth.ClientHandler, true);  
  
```  
  
 Para obtener más información acerca de este modo de uso, consulte la sección [configuración de la conexión FileConfiguration](web-api-helper-code-configuration-classes.md#bkmk_FileConfigconnectionsettings). Aunque la clase `Authentication` contiene otras propiedades y métodos públicos, éstos se proporcionan principalmente para admitir la creación de la propiedad `ClientHandler`, y la mayoría de aplicaciones cliente raramente accederían a ellos directamente.  
  
## <a name="class-listing"></a>Lista de clases  

El origen más actual para esta clase se encuentra en el paquete de NuGet de la [Biblioteca de código auxiliar de la API web del SDK de CRM](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode).  
  
```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;  
using System;  
using System.Net;  
using System.Net.Http;  
using System.Net.Http.Headers;  
using System.Security;  
using System.Threading.Tasks;  
  
namespace Microsoft.Crm.Sdk.Samples.HelperCode  
{  
    /// <summary>  
    /// Manages user authentication with the Dynamics CRM Web API (OData v4) services. This class uses Microsoft Azure  
    /// Active Directory Authentication Library (ADAL) to handle the OAuth 2.0 protocol.   
    /// </summary>  
    public class Authentication  
    {  
        private Configuration _config = null;  
        private HttpMessageHandler _clientHandler = null;  
        private AuthenticationContext _context = null;  
        private string _authority = null;  
  
        #region Constructors  
        /// <summary>  
        /// Base constructor.  
        /// </summary>  
        public Authentication() { }  
  
        /// <summary>  
        /// Establishes an authentication session for the service.  
        /// </summary>  
        /// <param name="config">A populated configuration object.</param>  
        public Authentication(Configuration config)  
            : base()  
        {  
            if (config == null)  
                throw new Exception("Configuration cannot be null.");  
  
            _config = config;  
  
            SetClientHandler();  
        }  
  
        /// <summary>  
        /// Custom constructor that allows adding an authority determined asynchronously before   
        /// instantiating the Authentication class.  
        /// </summary>  
        /// <remarks>For a WPF application, first call DiscoverAuthorityAsync(), and then call this  
        /// constructor passing in the authority value.</remarks>  
        /// <param name="config">A populated configuration object.</param>  
        /// <param name="authority">The URL of the authority.</param>  
        public Authentication(Configuration config, string authority)  
            : base()  
        {  
            if (config == null)  
                throw new Exception("Configuration cannot be null.");  
  
            _config = config;  
            Authority = authority;  
  
            SetClientHandler();  
        }  
        #endregion Constructors  
  
        #region Properties  
        /// <summary>  
        /// The authentication context.  
        /// </summary>  
        public AuthenticationContext Context  
        {  
            get  
            { return _context; }  
  
            set  
            { _context = value; }  
        }  
  
        /// <summary>  
        /// The HTTP client message handler.  
        /// </summary>  
        public HttpMessageHandler ClientHandler  
        {  
            get  
            { return _clientHandler; }  
  
            set  
            { _clientHandler = value; }  
        }  
  
        /// <summary>  
        /// The URL of the authority to be used for authentication.  
        /// </summary>  
        public string Authority  
        {  
            get  
            {  
                if (_authority == null)  
                    _authority = DiscoverAuthority(_config.ServiceUrl);  
  
                return _authority;  
            }  
  
            set { _authority = value; }  
        }  
        #endregion Properties  
  
        #region Methods  
        /// <summary>  
        /// Returns the authentication result for the configured authentication context.  
        /// </summary>  
        /// <returns>The refreshed access token.</returns>  
        /// <remarks>Refresh the access token before every service call to avoid having to manage token expiration.</remarks>  
        public AuthenticationResult AcquireToken()  
        {  
            if (_config != null && (!string.IsNullOrEmpty(_config.Username) && _config.Password != null))  
            {  
                UserCredential cred = new UserCredential(_config.Username, _config.Password);  
                return _context.AcquireToken(_config.ServiceUrl, _config.ClientId, cred);  
            }  
            return _context.AcquireToken(_config.ServiceUrl, _config.ClientId, new Uri(_config.RedirectUrl),  
                PromptBehavior.Auto);  
        }  
  
        /// <summary>  
        /// Returns the authentication result for the configured authentication context.  
        /// </summary>  
        /// <param name="username">The username of a CRM system user in the target organization. </param>  
        /// <param name="password">The password of a CRM system user in the target organization.</param>  
        /// <returns>The authentication result.</returns>  
        /// <remarks>Setting the username or password parameters to null results in the user being prompted to  
        /// enter log-on credentials. Refresh the access token before every service call to avoid having to manage  
        /// token expiration.</remarks>  
        public AuthenticationResult AcquireToken(string username, SecureString password)  
        {  
  
            try  
            {  
                if (!string.IsNullOrEmpty(username) && password != null)  
                {  
                    UserCredential cred = new UserCredential(username, password);  
                    return _context.AcquireToken(_config.ServiceUrl, _config.ClientId, cred);  
                }  
            }  
            catch (Exception e)  
            {  
                throw new Exception("Authentication failed. Verify the configuration values are correct.", e);  
            }  
            return null;  
        }  
  
        /// <summary>  
        /// Discover the authentication authority.  
        /// </summary>  
        /// <returns>The URL of the authentication authority on the specified endpoint address, or an empty string  
        /// if the authority cannot be discovered.</returns>  
         public static string DiscoverAuthority(string serviceUrl)  
        {  
            try  
            {  
                AuthenticationParameters ap = AuthenticationParameters.CreateFromResourceUrlAsync(  
                    new Uri(serviceUrl + "api/data/")).Result;  
  
                return ap.Authority;  
            }  
            catch (HttpRequestException e)  
            {  
                throw new Exception("An HTTP request exception occurred during authority discovery.", e);  
            }  
            catch (System.Exception e )  
            {  
                // This exception ocurrs when the service is not configured for OAuth.  
                if( e.HResult == -2146233088 )  
                {  
                    return String.Empty;  
                }  
                else  
                {  
                    throw e;  
                }  
            }  
        }  
  
        /// <summary>  
        /// Discover the authentication authority asynchronously.  
        /// </summary>  
        /// <param name="serviceUrl">The specified endpoint address</param>  
        /// <returns>The URL of the authentication authority on the specified endpoint address, or an empty string  
        /// if the authority cannot be discovered.</returns>  
        public static async Task<string> DiscoverAuthorityAsync(string serviceUrl)  
        {  
            try  
            {  
                AuthenticationParameters ap = await AuthenticationParameters.CreateFromResourceUrlAsync(  
                    new Uri(serviceUrl + "api/data/"));  
  
                return ap.Authority;  
            }  
            catch (HttpRequestException e)  
            {  
                throw new Exception("An HTTP request exception occurred during authority discovery.", e);  
            }  
            catch (Exception e)  
            {  
                // These exceptions ocurr when the service is not configured for OAuth.  
  
                // -2147024809 message: Invalid authenticate header format Parameter name: authenticateHeader  
                if (e.HResult == -2146233088 || e.HResult == -2147024809)  
                {  
                    return String.Empty;  
                }  
                else  
                {  
                    throw e;  
                }  
            }  
        }  
  
        /// <summary>  
        /// Sets the client message handler as appropriate for the type of authentication  
        /// in use on the web service endpoint.  
        /// </summary>  
        private void SetClientHandler()  
        {  
            // Check the Authority to determine if OAuth authentication is used.  
            if (String.IsNullOrEmpty(Authority))  
            {  
                if (_config.Username != String.Empty)  
                {  
                    _clientHandler = new HttpClientHandler()  
                    { Credentials = new NetworkCredential(_config.Username, _config.Password, _config.Domain) };  
                }  
                else  
                // No username is provided, so try to use the default domain credentials.  
                {  
                    _clientHandler = new HttpClientHandler()  
                    { UseDefaultCredentials = true };  
                }  
            }  
            else  
            {  
                _clientHandler = new OAuthMessageHandler(this, new HttpClientHandler());  
                _context = new AuthenticationContext(Authority, false);  
            }  
        }  
        #endregion Methods  
  
        /// <summary>  
        /// Custom HTTP client handler that adds the Authorization header to message requests. This  
        /// is required for IFD and Online deployments.  
        /// </summary>  
        class OAuthMessageHandler : DelegatingHandler  
        {  
            Authentication _auth = null;  
  
            public OAuthMessageHandler( Authentication auth, HttpMessageHandler innerHandler )  
                : base(innerHandler)  
            {  
                _auth = auth;  
            }  
  
            protected override Task<HttpResponseMessage> SendAsync(  
                HttpRequestMessage request, System.Threading.CancellationToken cancellationToken)  
            {  
                // It is a best practice to refresh the access token before every message request is sent. Doing so  
                // avoids having to check the expiration date/time of the token. This operation is quick.  
                request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", _auth.AcquireToken().AccessToken);  
  
                return base.SendAsync(request, cancellationToken);  
            }  
        }  
    }  
}  
```  
  
### <a name="see-also"></a>Vea también  

[Introducción a la API web (C#)](get-started-dynamics-365-web-api-csharp.md)<br />
[Iniciar un proyecto de la API web en Visual Studio (C#)](start-web-api-project-visual-studio-csharp.md)<br />
[Usar la biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md).<br />
[Código auxiliar: Clase de configuración](web-api-helper-code-configuration-classes.md)<br />
[Código auxiliar: clase CrmHttpResponseException](web-api-helper-code-crmhttpresponseexception-class.md)
