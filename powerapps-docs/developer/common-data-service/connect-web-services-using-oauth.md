---
title: Conectarse a los servicios web de Common Data Service para aplicaciones usando OAuth(Common Data Service para aplicaciones) | Microsoft Docs
description: Obtenga información sobre cómo conectar con los servicios web de Dynamics 365 Customer Engagement usando OAuth y cómo la API ADAL administra la autenticación OAuth 2.0 con el proveedor de identidad del servicio de web de Dynamics 365.
ms.custom: ''
ms.date: 01/25/2019
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
---
# <a name="connect-to-web-services-using-oauth"></a>Conexión con los servicios web mediante OAuth

OAuth es el método de autenticación admitido por la API web de Common Data Service para aplicaciones y es uno de dos métodos de autenticación para el servicio de la organización; el otro es la autenticación de Azure Active Directory. Un beneficio de usar OAuth es que la aplicación puede admitir autenticación de varios factores. Puede usar autenticación OAuth cuando la aplicación se conecte con el servicio de la organización o el servicio de detección.  
  
 Las llamadas de métodos a los servicios web deben autorizarse con el proveedor de identidad de ese extremo de servicio. La autorización es aprobada cuando un símbolo de acceso válido de OAuth 2.0 (usuario), emitido por Azure Active Directory, se proporciona en los encabezados de las solicitudes del mensaje.  
  
 La API de autenticación recomendada para uso con la API web de CDS for Apps es [Azure Active Directory Authentication Library (ADAL)](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-libraries/), que está disponible para una gran variedad de plataformas y de lenguajes de programación. La API ADAL administra la autenticación OAuth 2.0 con el proveedor de identidad de servicio web de CDS for Apps. Para obtener más detalles del protocolo OAuth real usado, consulte [Uso de OAuth para autenticarse con el servicio de CRM](http://blogs.msdn.com/b/crm/archive/2013/12/12/use-oauth-to-authenticate-with-the-crm-service.aspx).  
 
> [!NOTE]
> Debe usar las bibliotecas ADAL 2.0. Todas las herramientas, conjuntos y herramientas de Dynamics 365 Customer Engagement requieren los modelos admitidos por ADAL 2.0.
> Las bibliotecas ADAL 3.0 requieren una pantalla de inicio de sesión para capturar la información de la cuenta de usuario y no permiten pasar esta información de la cuenta de manera automatizada como requiere Dynamics 365 Customer Engagement. 

Para poder usar la autenticación OAuth para conectarse con los servicios web de CDS for Apps, la aplicación primero se debe registrar con Azure Active Directory. Azure Active Directory se usa para comprobar que la aplicación está autorizada a acceder a los datos profesionales almacenados en un inquilino de CDS for Apps.  
  
## <a name="authenticate-using-adal"></a>Autenticar usando ADAL  
 La autenticación del servicio web OAuth básica mediante ADAL se realiza con sólo unas líneas de código.  
  
```csharp  
// TODO Substitute your correct CRM root service address,   
string resource = "https://mydomain.crm.dynamics.com";  
  
// TODO Substitute your app registration values that can be obtained after you  
// register the app in Active Directory on the Microsoft Azure portal.  
string clientId = "e5cf0024-a66a-4f16-85ce-99ba97a24bb2";  
string redirectUrl = "http://localhost/SdkSample";  
  
// Authenticate the registered application with Azure Active Directory.  
AuthenticationContext authContext =   
    new AuthenticationContext("https://login.windows.net/common", false);  
AuthenticationResult result = authContext.AcquireToken(resource, clientId, new Uri(redirectUrl));  
```  
  
 El contexto de autenticación se devuelve mediante un proveedor de autoridad conocido. Cuando no se conoce el inquilino de Azure Active Directory asociado con la instancia de CDS for Apps a la que está llamando, puede usar una cadena constante de ` https://login.microsoftonline.com`, que es la URL de la autoridad para un escenario de múltiples inquilinos. Un método alternativo para detectar dinámicamente la autoridad en tiempo de ejecución se describe más adelante en este tema.  
  
 La línea de código siguiente obtiene el resultado de autenticación que contiene el símbolo de acceso que busca. Puede enviar solicitudes de mensaje al servicio web con este símbolo.  
  
 Algunos elementos de interés más en este código son los valores de cadena usados. La variable de recursos contiene la dirección de raíz de seguridad de la capa de transporte (TLS) o capa de sockets seguros (SSL), incluido el dominio (organización), de su servidor de CDS for Apps. Las variables `clientId` y `redirectUrl` contienen información de registro de la aplicación que es el resultado de registrar la aplicación con Azure Active Directory. Para obtener más información sobre el registro de aplicaciones, consulte [Tutorial: Registrar una aplicación de Dynamics 365 con Azure Active Directory](/dynamics365/customer-engagement/developer/walkthrough-register-dynamics-365-app-azure-active-directory).  
  
## <a name="use-the-access-token-in-message-requests"></a>Use el símbolo de acceso en solicitudes de mensajes  
 Según la API de CDS for Apps que use, hay dos métodos diferentes para enviar una solicitud de mensaje a los servicios web. Para la API web, normalmente enviaría una solicitud de mensaje HTTP. Para el servicio de la organización, enviaría una solicitud de mensaje con el proxy del cliente web.  
  
### <a name="http-message-request"></a>Solicitud de mensaje HTTP  
 Una vez que tenga el token de acceso, debe establecer el encabezado de autorización de la solicitud del mensaje que está enviando al servicio web al valor del token de acceso y especificar el tipo de token de `Bearer`. Para obtener más información sobre el encabezado de autorización, vea la sección 14.8 del [Protocolo HTTP/1.1](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html). El siguiente código demuestra cómo se hace esto utilizando la clase `System.Net.Http.HttpClient`.  
  
```csharp  
using (HttpClient httpClient = new HttpClient())  
{  
    httpClient.Timeout = new TimeSpan(0, 2, 0);  // 2 minutes  
    httpClient.DefaultRequestHeaders.Authorization =   
        new AuthenticationHeaderValue("Bearer", result.AccessToken);  
```  
  
### <a name="web-client-requests"></a>Solicitudes del cliente web

Establezca simplemente el valor de propiedad <xref:Microsoft.Xrm.Sdk.WebServiceClient.WebProxyClient`1.HeaderToken> con el símbolo de acceso al usar <xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient> o <xref:Microsoft.Xrm.Sdk.WebServiceClient.DiscoveryWebProxyClient> del servicio de organización.  
  
## <a name="refresh-the-access-token"></a>Actualizar el símbolo de acceso

Se recomienda actualizar el símbolo de acceso antes de cada llamada a un método del servicio web de CDS for Apps. Para actualizar el símbolo de acceso, que ADAL almacena en la memoria caché, llame simplemente al método `AcquireToken` de nuevo utilizando el mismo contexto.  
  
```csharp    
AuthenticationResult result = authContext.AcquireToken(resource, clientId, new Uri(redirectUrl));  
```  
  
Luego, de nuevo establezca el encabezado de autorización con `result.AccessToken` al usar la API web, o <xref:Microsoft.Xrm.Sdk.WebServiceClient.WebProxyClient`1.HeaderToken> al usar el servicio de organización.  
  
```csharp    
httpClient.DefaultRequestHeaders.Authorization =   
    new AuthenticationHeaderValue("Bearer", result.AccessToken);  
```  
  
## <a name="discover-the-authority-at-run-time"></a>Detectar la autoridad en tiempo de ejecución

La URL de la autoridad de autenticación y la URL del recurso pueden determinarse de forma dinámica en tiempo de ejecución mediante el siguiente código de ADAL. Este es el método recomendado para usar en comparación con la URL de autoridad conocida que se mostraba anteriormente en un fragmento de código.  
  
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
  
### <a name="see-also"></a>Vea también  
 [Tutorial: Registrar una aplicación de Dynamics 365 con Azure Active Directory](/dynamics365/customer-engagement/developer/walkthrough-register-dynamics-365-app-azure-active-directory)   
 [Documentación de autenticación multifactor](https://azure.microsoft.com/en-us/documentation/services/multi-factor-authentication/)   
 [OAuth 2.0](http://oauth.net/2/)
