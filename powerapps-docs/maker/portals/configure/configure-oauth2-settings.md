---
title: Configurar ajustes del proveedor de OAuth2 para un portal en | MicrosoftDocs
description: Instrucciones para agregar y configurar las opciones del proveedor de OAuth2 para un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: be576425067079549d3174e6d6306814a6ddb13a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755463"
---
# <a name="configure-oauth2-provider-settings-for-portals"></a>Configurar el proveedor OAuth2 para portales

Los proveedores de identidad externos basados en OAuth 2.0 registran una "aplicación" con un servicio de terceros para obtener un par "Id. de cliente" y "secreto de cliente". A menudo, esta aplicación requiere especificar una dirección URL de redirección que permite que el proveedor de identidad envíe los usuarios de vuelta al portal (usuario de confianza). El Id. del cliente y el secreto de cliente están configurados como valores del sitio del portal para establecer una conexión de seguridad del usuario de confianza al proveedor de identidad. Los valores se basan en las propiedades de las clases [[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]AccountAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.aspx), [TwitterAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.twitter.twitterauthenticationoptions.aspx), [FacebookAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.facebook.facebookauthenticationoptions.aspx) y [GoogleOAuth2AuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.google.googleoauth2authenticationoptions.aspx).  

Los proveedores admitidos son:

- Cuenta de [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]
- Twitter
- Facebook
- Google
- LinkedIn
- Yahoo

## <a name="create-oauth-applications"></a>Crear aplicaciones OAuth

Normalmente si un proveedor de OAuth usa una configuración de aplicación que requiere un valor de URI de redirección, especifique <https://portal.contoso.com/or> https://portal.contoso.com/signin-\[proveedor]\] en función de cómo el proveedor realiza validación de URI de re direccionamiento (algunos proveedores requieren que se especifique la ruta de acceso completa de la dirección URL junto al nombre de dominio). Sustituya el nombre del proveedor en lugar de \[provider\] en la URI de redirección.

### <a name="google"></a>Google

[Instrucciones de credenciales de la API Google OAuth2](https://developers.google.com/accounts/docs/OpenIDConnect#appsetup)  

1. Abra [Google Developers Console](https://console.developers.google.com/)  
2. Cree un proyecto de API o abra un proyecto existente
3. Vaya a **API y autenticación** &gt;**API** y en **API de medios sociales**, seleccione **Google+ API** y luego seleccione **Habilitar API**
4. Vaya a **API y autenticación** &gt;**Pantalla de consentimiento**.
    - Especifique una **Dirección de correo electrónico**.
    - Especifique un **Nombre de producto** personalizado.
    - Seleccione **Guardar**.
5. Vaya a **API y autenticación** &gt;**Credenciales** y cree un nuevo identificador de cliente.
   - Tipo de aplicación: **Aplicación web**
   - Orígenes de [!INCLUDE[pn-javascript](../../../includes/pn-javascript.md)] autorizados: https://portal.contoso.com
   - URI de redirección autorizados: https://portal.contoso.com/signin-google 
   - Seleccione **Crear Id. de cliente**.

### <a name="facebook-app-settings"></a>Configuración de la aplicación Facebook

1. Abra [Facebook Developers App Dashboard](https://developers.facebook.com/apps)  
2. Seleccione **Agregar nueva aplicación**.
3. Seleccione **Sitio web**.
4. Seleccione **Omitir y crear Id. de aplicación**.
    - Especifique un **Nombre para mostrar**.
    - Elija una **Categoría**.
    - Seleccione **Crear id. de aplicación**.

5. Mientras está en el panel para la nueva aplicación, vaya a**Configuración** &gt;**Básica** (pestaña) y agregue los siguientes detalles:
    - Dominios de aplicación (opcional): portal.contoso.com 
    - Correo electrónico de contacto: *&lt;dirección de correo electrónico que prefiera&gt;* 
    - Seleccione **Agregar plataforma** y seleccione un **Sitio web**. 
    - Dirección URL: https://portal.contoso.com/ o https://portal.contoso.com/signin-facebook

6. Seleccione **Guardar cambios**.
7. Vaya a **Estado y revisión** &gt; **Estado** (pestaña).
8. Seleccione **Sí** cuando se le solicita para configurar la aplicación y todas las características a disposición del público general. Debe haber completado los datos válidos en el paso 5 anterior para habilitar este valor.

### <a name="includecc-microsoftincludescc-microsoftmd-application-settings"></a>Configuración de aplicación de [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]

1. Abra Centro para desarrolladores de cuentas de [[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] ](https://account.live.com/developers/applications/index)  
2. Seleccione **Crear aplicación** y especifique un **Nombre de aplicación**.
3. Seleccione **Acepto** para aceptar los términos y condiciones.
4. Vaya a **Configuración** &gt;**Configuración de API** y, a continuación, establezca la dirección URL de redireccionamiento como https://portal.contoso.com/signin-microsoft. 

### <a name="twitter-apps-settings"></a>Configuración de aplicaciones en Twitter

1. Abra [Administración de aplicaciones de Twitter](https://apps.twitter.com/). 
2. Seleccione **Crear nueva aplicación**.

    - Especifique el **Nombre** y **Descripción** de la aplicación.
    - Establezca la dirección URL del sitio web como https://portal.contoso.com.
    - Establezca la dirección URL de devolución de llamada como https://portal.contoso.com o https://portal.contoso.com/signin-twitter.

3. Seleccione **Cree su aplicación de Twitter**.

### <a name="linkedin-app-settings"></a>Configuración de aplicaciones en LinkedIn

1. Abra [Red para desarrolladores de LinkedIn](https://www.linkedin.com/secure/developer).  
2. Seleccione **Agregar nueva aplicación**.

    - Especifique **Nombre de aplicación**, **Descripción**, etc.
    - Establezca la dirección URL del sitio web como https://portal.contoso.com.
    - Establezca Ámbito de contrato de usuario/predeterminado de OAuth: r\_basicprofie y r\_emailaddress
    - Establezca la dirección URL de redireccionamiento de OAuth 2.0: https://portal.contoso.com/signin-linkedin.

3. Seleccione **Agregar aplicación**.

### <a name="yahoo-ydn-app-settings"></a>Yahoo! Configuración de aplicaciones en YDN

1. Abra [Red para desarrolladores de Yahoo!](https://developer.yahoo.com/apps).
2. Seleccione **Crear una aplicación**.
    
    - Especifique un **Nombre de aplicación**.
    - Tipo de aplicación: **Aplicación web**.
    - Dominio de devolución de llamada: portal.contoso.com

3. Seleccione **Crear aplicación**.

## <a name="create-site-settings-by-using-oauth2"></a>Crear valores del sitio mediante OAuth2

El panel de la aplicación para cada proveedor mostrará el Id. de cliente (Id. de la aplicación, clave de consumidor) y el secreto de cliente (secreto de la aplicación, secreto de consumidor) para cada aplicación. Use estos dos valores para establecer la configuración del sitio del portal.

>[!Note]
> Una configuración de OAuth2 estándar requiere solo los siguientes valores (con Facebook como ejemplo):
> - `Authentication/OpenAuth/Facebook/ClientId`
> - `Authentication/OpenAuth/Facebook/ClientSecret`

Sustituya la etiqueta `[provider]` en el nombre del valor de sitio con un nombre de proveedor de identidad específico: Facebook, Google, Yahoo, [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)], LinkedIn o Twitter.

|**Nombre de configuración del sitio**                                           |**Descripción**                                                                                                                                                                                                                                                                                                                                      |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ExternalLoginEnabled                | Habilita o deshabilita el inicio de sesión y el registro de la cuenta externa. Valor predeterminado: true                                                                                                                                                                                                                                                                         |
| Authentication/OpenAuth/\[provider\]/ClientId                   | Requerido. El valor de Id. de cliente de la aplicación del proveedor. También puede denominarse Id. de la aplicación o Clave de consumidor.  Los nombres de configuración siguientes se permiten por compatibilidad:  Authentication/OpenAuth/Twitter/ConsumerKey <ul><li>Authentication/OpenAuth/Facebook/AppId</li><li>Authentication/OpenAuth/LinkedIn/ConsumerKey</li> |
| Authentication/OpenAuth/\[provider\]/ClientSecret               | Requerido. El valor de secreto de cliente de la aplicación del proveedor. También puede denominarse Secreto de la aplicación o Secreto de consumidor.  Los nombres de configuración siguientes se permiten por compatibilidad:  Authentication/OpenAuth/Twitter/ConsumerSecret <ul><li>Authentication/OpenAuth/Facebook/AppSecret</li><li>Authentication/OpenAuth/LinkedIn/ConsumerSecret</li> |
| Authentication/OpenAuth/\[provider\]/AuthenticationType         | El tipo de middleware de autenticación OWIN. Ejemplo: yahoo. [authenticationoptions.authenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx).                                                                                                                                |  
| Authentication/OpenAuth/\[provider\]/Scope                      | Una lista separada por comas de permisos para solicitar. [microsoftaccountauthenticationoptions.scope](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.scope.aspx).                                                                                                                |  
| Authentication/OpenAuth/\[provider\]/Caption                    | El texto que el usuario puede mostrar en una interfaz de usuario de inicio de sesión. [microsoftaccountauthenticationoptions.caption](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.caption.aspx).                                                                                              |  
| Authentication/OpenAuth/\[provider\]/BackchannelTimeout         | Valor de tiempo de espera en milisegundos para comunicaciones de canal posterior. [microsoftaccountauthenticationoptions.backchanneltimeout](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.backchanneltimeout.aspx).                                                                         |  
| Authentication/OpenAuth/\[provider\]/CallbackPath               | Se devolverá la ruta de solicitud en la ruta de acceso base de la aplicación donde el agente de usuario. [microsoftaccountauthenticationoptions.callbackpath](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.callbackpath.aspx).                                                         |  
| Authentication/OpenAuth/\[provider\]/SignInAsAuthenticationType | El nombre de otro software intermedio de autenticación que será responsable de emitir realmente un**userClaimsIdentity**. [microsoftaccountauthenticationoptions.signinasauthenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.signinasauthenticationtype.aspx). |  
| Authentication/OpenAuth/\[provider\]/AuthenticationMode         | El modo de middleware de autenticación OWIN. [security.authenticationoptions.authenticationmode](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx).                                                                                                                                       |  

### <a name="see-also"></a>Vea también

[Configurar la autenticación del portal](configure-portal-authentication.md)  
[Establecer identidad de autenticación para un portal](set-authentication-identity.md)  
[Configuración de proveedor Open ID Connect para portales](configure-openid-settings.md)   
[Configuración de proveedor de WS-Federation para portales](configure-ws-federation-settings.md)  
[Configuración del proveedor SAML 2.0 para portales](configure-saml2-settings.md)
