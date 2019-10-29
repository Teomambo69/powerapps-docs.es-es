---
title: Configurar los valores del proveedor de OAuth2 para un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar los valores del proveedor de OAuth2 para un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 25a26e6298fa3257f3db6d04ffd2937e8e71d3a1
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978540"
---
# <a name="configure-oauth2-provider-settings-for-portals"></a>Configurar los valores del proveedor de OAuth2 para portales

Los proveedores de identidades externas basados en OAuth 2,0 implican el registro de una "aplicación" con un servicio de terceros para obtener un par "ID. de cliente" y "secreto de cliente". A menudo, esta aplicación requiere la especificación de una dirección URL de redireccionamiento que permite al proveedor de identidades devolver a los usuarios al portal (usuario de confianza). El ID. de cliente y el secreto de cliente se configuran como configuración del sitio del portal para establecer una conexión segura entre el usuario de confianza y el proveedor de identidades. La configuración se basa en las propiedades de las clases [[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]AccountAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.aspx), [TwitterAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.twitter.twitterauthenticationoptions.aspx), [FacebookAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.facebook.facebookauthenticationoptions.aspx)y [GoogleOAuth2AuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.google.googleoauth2authenticationoptions.aspx) .  

Los proveedores admitidos son:

- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] cuenta
- Twitter
- Facebook
- Google
- LinkedIn
- Yahoo

## <a name="create-oauth-applications"></a>Creación de aplicaciones de OAuth

En general, si un proveedor de OAuth usa la configuración de la aplicación que requiere un valor de URI de redireccionamiento, especifique <http://portal.contoso.com/or> http://portal.contoso.com/signin-\ [proveedor\] en función de cómo el proveedor realice la validación del URI de redirección (algunos proveedores requieren que se especifique la ruta de acceso completa de la dirección URL junto con el nombre de dominio). Sustituya el nombre del proveedor en lugar de \[proveedor\] en el URI de redirección.

### <a name="google"></a>Google

[Instrucciones de credenciales de la API de Google OAuth2](https://developers.google.com/accounts/docs/OpenIDConnect#appsetup)  

1. Abra la [consola de desarrolladores de Google](https://console.developers.google.com/)  
2. Crear un proyecto de API o abrir un proyecto existente
3. Vaya a**api & auth** &gt;**API**y, en **API de redes sociales**, seleccione**Google + API**y, a continuación, seleccione**Habilitar API** .
4. Vaya a la **pantalla de consentimiento**de**api & auth** &gt;.
    - Especifique una**dirección de correo electrónico**.
    - Especifique un**nombre de producto**personalizado.
    - Seleccione**Guardar**.
5. Vaya a**api & auth** &gt;**credenciales** y cree un nuevo ID. de cliente.
   - Tipo de aplicación:**aplicación web**
   - Orígenes de [!INCLUDE[pn-javascript](../../../includes/pn-javascript.md)] autorizados: http://portal.contoso.com
   - URI de redirección autorizados: http://portal.contoso.com/signin-google 
   - Seleccione **crear ID**. de cliente.

### <a name="facebook-app-settings"></a>Configuración de la aplicación Facebook

1. Abrir el panel de la [aplicación de desarrolladores de Facebook](https://developers.facebook.com/apps)  
2. Seleccione **Agregar una nueva aplicación**.
3. Seleccione **sitio web**.
4. Seleccione **omitir y crear ID. de aplicación**.
    - Especifique un **nombre para mostrar**.
    - Elija una **categoría**.
    - Seleccione **crear ID**. de aplicación.

5. En el panel de la nueva aplicación, vaya a **configuración** &gt;**Basic** (pestaña) y agregue los detalles siguientes:
    - Dominios de aplicación (opcional): portal.contoso.com 
    - Correo electrónico de contacto: *&lt;dirección de correo electrónico de su elección&gt;* 
    - Seleccione **Agregar plataforma**y, a continuación, seleccione **sitio web**. 
    - Dirección URL del sitio: http://portal.contoso.com/ o http://portal.contoso.com/signin-facebook

6. Seleccione **Guardar cambios**.
7. Vaya a **estado & revisar** &gt; pestaña **Estado** .
8. Seleccione **sí** cuando se le pregunte si desea que la aplicación y todas sus características estén disponibles para el público general. Debe haber rellenado los datos válidos en el paso 5 anterior para habilitar esta configuración.

### <a name="includecc-microsoftincludescc-microsoftmd-application-settings"></a>[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] configuración de la aplicación

1. Abrir el [Centro para desarrolladores de cuentas[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]](https://account.live.com/developers/applications/index)  
2. Seleccione **crear aplicación** y especifique un **nombre de aplicación**.
3. Seleccione **acepto para aceptar los** términos y condiciones.
4. Vaya a **configuración** &gt;**configuración de API**y, a continuación, establezca la dirección URL de redireccionamiento como http://portal.contoso.com/signin-microsoft 

### <a name="twitter-apps-settings"></a>Configuración de aplicaciones de Twitter

1. Abra [Administración de aplicaciones de Twitter](https://apps.twitter.com/). 
2. Seleccione **crear nueva aplicación**.

    - Especifique un **nombre** y una **Descripción** para la aplicación.
    - Establezca la dirección URL del sitio web como http://portal.contoso.com.
    - Establezca la dirección URL de devolución de llamada como http://portal.contoso.com o http://portal.contoso.com/signin-twitter.

3. Seleccione **crear la aplicación de Twitter**.

### <a name="linkedin-app-settings"></a>Configuración de la aplicación LinkedIn

1. Abra [LinkedIn Developer Network](https://www.linkedin.com/secure/developer).  
2. Seleccione **Agregar nueva aplicación**.

    - Especifique un **nombre de aplicación**, una **Descripción**, etc.
    - Establezca la dirección URL del sitio web como http://portal.contoso.com.
    - Establecer contrato de usuario de OAuth/ámbito predeterminado: r\_basicprofie y r\_EmailAddress
    - Establezca la dirección URL de redireccionamiento de OAuth 2,0: http://portal.contoso.com/signin-linkedin.

3. Seleccione **Agregar aplicación**.

### <a name="yahoo-ydn-app-settings"></a>Yahoo! Configuración de la aplicación YDN

1. Abra [Yahoo! Developer Network](https://developer.yahoo.com/apps).
2. Seleccione **crear una aplicación**.
    
    - Especifique un **nombre de aplicación**.
    - Tipo de aplicación: **aplicación web**.
    - Dominio de devolución de llamada: portal.contoso.com

3. Seleccione **crear aplicación**.

## <a name="create-site-settings-by-using-oauth2"></a>Crear la configuración del sitio mediante OAuth2

El panel de la aplicación para cada proveedor mostrará el identificador de cliente (identificador de aplicación, clave de consumidor) y el secreto de cliente (secreto de aplicación, secreto de consumidor) de cada aplicación. Use estos dos valores para establecer la configuración del sitio del portal.

>[!Note]
> Una configuración de OAuth2 estándar solo requiere la siguiente configuración (con Facebook como ejemplo):
> - `Authentication/OpenAuth/Facebook/ClientId`
> - `Authentication/OpenAuth/Facebook/ClientSecret`

Sustituya la etiqueta `[provider]` en el nombre de la configuración del sitio por un nombre de proveedor de identidades específico: Facebook, Google, Yahoo,[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)], LinkedIn o Twitter.

|**Nombre de la configuración del sitio**                                           |**Description**                                                                                                                                                                                                                                                                                                                                      |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autenticación/registro/ExternalLoginEnabled                | Habilita o deshabilita el registro y el inicio de sesión de la cuenta externa. Valor predeterminado: true                                                                                                                                                                                                                                                                         |
| Proveedor de autenticación/OpenAuth/\[\]/ClientId                   | Obligatorio. Valor de ID. de cliente de la aplicación de proveedor. También se le puede denominar identificador de aplicación o clave de consumidor.  Los nombres de configuración siguientes se permiten por compatibilidad con versiones anteriores: Authentication/OpenAuth/Twitter/ConsumerKey <ul><li>Autenticación/OpenAuth/Facebook/AppId</li><li>Authentication/OpenAuth/LinkedIn/ConsumerKey</li> |
| Proveedor de autenticación/OpenAuth/\[\]/ClientSecret               | Obligatorio. Valor de secreto de cliente de la aplicación de proveedor. También se le puede denominar secreto de aplicación o secreto de consumidor.  Los nombres de configuración siguientes se permiten por compatibilidad con versiones anteriores: Authentication/OpenAuth/Twitter/ConsumerSecret <ul><li>Autenticación/OpenAuth/Facebook/AppSecret</li><li>Authentication/OpenAuth/LinkedIn/ConsumerSecret</li> |
| Proveedor de autenticación/OpenAuth/\[\]/AuthenticationType         | Tipo de middleware de autenticación OWIN. Ejemplo: Yahoo. [authenticationoptions. AuthenticationType](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx).                                                                                                                                |  
| Proveedor de autenticación/OpenAuth/\[\]/Scope                      | Lista separada por comas de los permisos que se van a solicitar. [microsoftaccountauthenticationoptions. Scope](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.scope.aspx).                                                                                                                |  
| Proveedor de autenticación/OpenAuth/\[\]/Caption                    | Texto que el usuario puede mostrar en una interfaz de usuario de inicio de sesión. [microsoftaccountauthenticationoptions. Caption](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.caption.aspx).                                                                                              |  
| Proveedor de autenticación/OpenAuth/\[\]/BackchannelTimeout         | Valor de tiempo de espera en milisegundos para las comunicaciones de canal posterior. [microsoftaccountauthenticationoptions. backchanneltimeout](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.backchanneltimeout.aspx).                                                                         |  
| Proveedor de autenticación/OpenAuth/\[\]/CallbackPath               | La ruta de acceso de la solicitud dentro de la ruta de acceso base de la aplicación donde se devolverá el agente de usuario. [microsoftaccountauthenticationoptions. callbackpath](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.callbackpath.aspx).                                                         |  
| Proveedor de autenticación/OpenAuth/\[\]/SignInAsAuthenticationType | El nombre de otro middleware de autenticación que será responsable de la emisión real de un**userClaimsIdentity**. [microsoftaccountauthenticationoptions. signinasauthenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.signinasauthenticationtype.aspx). |  
| Proveedor de autenticación/OpenAuth/\[\]/AuthenticationMode         | El modo de middleware de autenticación OWIN. [Security. authenticationoptions. AuthenticationMode](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx).                                                                                                                                       |  

### <a name="see-also"></a>Vea también

[Configurar la autenticación del portal](configure-portal-authentication.md)  
[Establecimiento de la identidad de autenticación para un portal](set-authentication-identity.md)  
[Abra la configuración del proveedor de Connect Connect para portales](configure-openid-settings.md)   
[Configuración del proveedor de WS-Federation para portales](configure-ws-federation-settings.md)  
[Configuración del proveedor de SAML 2,0 para portales](configure-saml2-settings.md)
