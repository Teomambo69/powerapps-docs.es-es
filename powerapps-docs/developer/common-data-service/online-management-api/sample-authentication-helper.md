---
title: 'Ejemplo: aplicación auxiliar de autenticación para usar la API de Online Management para Dynamics 365 for Customer Engagement | MicrosoftDocs'
description: Código auxiliar para autenticarse en la API de Online Management.
ms.date: 11/27/2017
ms.service: crm-online
ms.topic: conceptual
applies_to: Dynamics 365 for Customer Engagement (online)
ms.assetid: a96fff7c-814e-4fa1-98b6-7a2875ee0234
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
- developer
search.app:
- D365CE
ms.openlocfilehash: 9ae7d883b31afc0e23f83ebf7157c2ec2ebf72b9
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115736"
---
# <a name="sample-authentication-helper-for-the-online-management-api"></a>Ejemplo: Código auxiliar de autenticación para la API de Online Management 

Este ejemplo de código auxiliar proporciona los siguientes métodos para poder autenticarse fácilmente en la API de Online Management mediante el protocolo OAuth 2.0 y poder pasar el token de acceso en la cabecera de sus mensajes.

## <a name="discoverauthority-method"></a>Método de DiscoverAuthority
Este método crea un desafío de Azure AD para descubrir la información de la autoridad basada en la dirección URL de servicio de la API. Para obtener una lista de direcciones URL de servicio de la API de Online Management, consulte [Direcciones URL de servicio](get-started-online-management-api.md#service-url) 

## <a name="acquiretoken-method"></a>Método de AcquireToken
Este método usa el token de acceso basado en el recursos descubierto y el id. de cliente y la URL de redirección de la aplicación que registró en Azure AD. Tenga en cuenta que estamos usando el recurso en lugar de la dirección URL de servicio de la API, ya que son diferentes.


## <a name="sendasync-method"></a>Método SendAsync

Este es un controlador de HTTP personalizado que agrega el encabezado de **Autorización** y **Aceptar-idioma** a las solicitudes de mensaje en la aplicación cliente.

## <a name="code-sample-listing"></a>Listado del código de ejemplo 

Aquí está el código de ejemplo completo de la aplicación auxiliar de autenticación:

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System;
using System.Net.Http;
using System.Net.Http.Headers;
using System.Threading.Tasks;

namespace Microsoft.Crm.Sdk.Samples.HelperCode
{
    /// <summary>
    /// Manages authentication to the Online Management API service.
    /// Uses Microsoft Azure Active Directory Authentication Library (ADAL) 
    /// to handle the OAuth 2.0 protocol. 
    /// </summary>
    public class Authentication
    {
        private HttpMessageHandler _clientHandler = null;
        private AuthenticationContext _authContext = null;
        private string _authority = null;        
        private string _serviceUrl = null;

        // Static variable to hold the Resource. This will be discovered
        // and then used later for acquiring access token
        private static string _resource = null;        

        // TODO: Substitute your app registration values here.
        // These values are obtained on registering your application with the 
        // Azure Active Directory.
        private static string _clientId = "<GUID>";     //e.g. "e5cf0024-a66a-4f16-85ce-99ba97a24bb2"
        private static string _redirectUrl = "<Url>";  //e.g. "app://s7cf7712-b773-4f16-92b3-34cs97a25cc7"

        #region Constructors
        /// <summary>
        /// Base constructor.
        /// </summary>
        public Authentication() { }

        /// <summary>
        /// Custom constructor that allows adding an authority determined asynchronously before 
        /// instantiating the Authentication class.
        /// </summary>                
        /// <param name="authority">The URL of the authority.</param>
        public Authentication(string authority)
            : base()
        {
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
            { return _authContext; }

            set
            { _authContext = value; }
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
                {
                    var authority = DiscoverAuthority(_serviceUrl.ToString());
                    _authority = authority.Result.ToString();
                }


                return _authority;
            }

            set { _authority = value; }
        }
        #endregion Properties

        #region Methods
        /// <summary>
        /// Discover the authentication authority asynchronously.
        /// </summary>
        /// <param name="serviceUrl">The specified endpoint address</param>
        /// <returns>The URL of the authentication authority on the specified endpoint address, or an empty string
        /// if the authority cannot be discovered.</returns>
        public static async Task<string> DiscoverAuthority(string _serviceUrl)
        {
            try
            {
                AuthenticationParameters ap = await AuthenticationParameters.CreateFromResourceUrlAsync(
                    new Uri(_serviceUrl + "/api/aad/challenge"));
                _resource = ap.Resource;
                return ap.Authority;
            }
            catch (HttpRequestException e)
            {
                throw new Exception("An HTTP request exception occurred during authority discovery.", e);
            }
            catch (Exception e)
            {
                throw e;
            }
        }

        /// <summary>
        /// Returns the authentication result for the configured authentication context.
        /// </summary>
        /// <returns>The refreshed access token.</returns>
        /// <remarks>Refresh the access token before every service call to avoid having to manage token expiration.</remarks>
        public AuthenticationResult AcquireToken()
        {
            return _authContext.AcquireToken(_resource, _clientId, new Uri(_redirectUrl),
                PromptBehavior.Always);
        }

        /// <summary>
        /// Sets the client message handler.
        /// </summary>
        private void SetClientHandler()
        {
            _clientHandler = new OAuthMessageHandler(this, new HttpClientHandler());
            _authContext = new AuthenticationContext(Authority, false);
        }

        #endregion Methods

        /// <summary>
        /// Custom HTTP client handler that adds the "Authorization" and "Accept-Language" headers to message requests.
        /// </summary>
        class OAuthMessageHandler : DelegatingHandler
        {
            Authentication _auth = null;

            public OAuthMessageHandler(Authentication auth, HttpMessageHandler innerHandler)
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

                // Set the "Accept-Language" header
                request.Headers.Add("Accept-Language", "en-US");

                return base.SendAsync(request, cancellationToken);
            }
        }
    }
}
```

### <a name="related-topics"></a>Temas relacionados  

[Introducción a la API de Online Management](get-started-online-management-api.md)

[Operaciones compatibles con la API Online Management](operations-supported.md)

[Referencia de la API de Online Management](/rest/api/admin.services.crm.dynamics.com)
