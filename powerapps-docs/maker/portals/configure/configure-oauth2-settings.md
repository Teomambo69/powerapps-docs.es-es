---
title: Configurar ajustes del proveedor de OAuth2 para un portal en | MicrosoftDocs
description: Instrucciones para agregar y configurar las opciones del proveedor de OAuth2 para un portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/17/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 6065c842831aa9aa0c225d12470a4469fe51146d
ms.sourcegitcommit: 4349eefb1fd788f5e27d91319bc878ee9aba7a75
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2020
ms.locfileid: "3012700"
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

## <a name="google-people-api-settings"></a>Configuración de API de Google People

> [!NOTE]
> [API Google+](https://developers.google.com/people/legacy) ha quedado obsoleta. Recomendamos encarecidamente que migre a [API Google People](https://developers.google.com/people).

Siga estos pasos para configurar su portal Power Apps con [autenticación Oauth 2.0 de Google] para autenticación del usuario.

1. Abra [Google Developers Console](https://console.developers.google.com/).  
1. Cree un proyecto de API o abra un proyecto existente.
1. Seleccione **HABILITAR APIS Y SERVICIOS** desde el panel de API y Servicios.
1. Busque y habilite la API **API de Google People**.
1. Dentro de **API de Google**, seleccione **Credenciales** en la parte izquierda.

    > [!NOTE]
    > Si ya ha configurado la pantalla de consentimiento con el dominio de nivel superior de los portales, puede omitir los pasos 6 a 14 y pasar directamente al paso 15. Sin embargo, vaya al paso 11 antes de pasar al paso 15 si su pantalla de consentimiento está configurada pero no está agregado el dominio de nivel superior de los portales.

1. Seleccione **CONFIGURAR PANTALLA DE CONSENTIMIENTO**.
1. Seleccione el tipo de usuario **Externo**.
1. Seleccione **Crear**.
1. Escriba **Nombre de la aplicación** y cargue una imagen para el logotipo, si es necesario.
1. Seleccione el **Correo electrónico de soporte** adecuado.
1. Escriba **powerappsportals.com** como dominio de nivel superior en **Dominios autorizados**. Utilice **microsoftcrmportals.com** si no tiene [actualizado su nombre de dominio del portal Power Apps](../admin/update-portal-domain.md). También puede escribir un [nombre de dominio personalizado](../admin/add-custom-domain.md) si lo ha configurado. 
1. Proporcione vínculos para la página principal, la política de privacidad y los términos del servicio, según sea necesario. 
1. Seleccione **Guardar**.
1. Seleccione **Credenciales** desde el menú de navegación izquierdo.
1. Seleccione **Id. de cliente Oauth ID** desde el menú desplegable **Crear credenciales**.
1. Seleccione el tipo de aplicación como **Aplicación web**.
1. Escriba **Nombre** para el Id. de cliente Oauth.
1. Escriba su dirección URL del portal Power Apps en la lista **Orígenes de JavaScript autorizados**.
1. Escriba **URI de redireccionamiento autorizado** como dirección URL del portal Power Apps, seguido por **/signin-google**. Por ejemplo, si la dirección URL del portal es https://contoso.powerappsportals.com, el campo de las URI de redireccionamiento autorizado debería ser https://contoso.powerappsportals.com/signin-google.
1. Seleccione **Crear**.
1. Copie **Id. del cliente** y **secreto de cliente** desde el cuadro de diálogo **Cliente Oauth** y configure [Configuración del sitio OAuth2](https://docs.microsoft.com/powerapps/maker/portals/configure/configure-oauth2-settings#create-site-settings-by-using-oauth2) en los portales Power Apps.

## <a name="facebook-app-settings"></a>Configuración de la aplicación Facebook

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

### <a name="cc-microsoft-application-settings"></a>Configuración de aplicación de [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]

1. Abra Centro para desarrolladores de cuentas de [[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] ](https://account.live.com/developers/applications/index)  
2. Seleccione **Crear aplicación** y especifique un **Nombre de aplicación**.
3. Seleccione **Acepto** para aceptar los términos y condiciones.
4. Vaya a **Configuración** &gt;**Configuración de API** y, a continuación, establezca la dirección URL de redireccionamiento como https://portal.contoso.com/signin-microsoft. 

## <a name="twitter-apps-settings"></a>Configuración de aplicaciones en Twitter

1. Abra [Administración de aplicaciones de Twitter](https://apps.twitter.com/). 
2. Seleccione **Crear nueva aplicación**.

    - Especifique el **Nombre** y **Descripción** de la aplicación.
    - Establezca la dirección URL del sitio web como https://portal.contoso.com.
    - Establezca la dirección URL de devolución de llamada como https://portal.contoso.com o https://portal.contoso.com/signin-twitter.

3. Seleccione **Cree su aplicación de Twitter**.

## <a name="linkedin-app-settings"></a>Configuración de aplicaciones en LinkedIn

1. Abra [Red para desarrolladores de LinkedIn](https://www.linkedin.com/secure/developer).  
2. Seleccione **Agregar nueva aplicación**.

    - Especifique **Nombre de aplicación**, **Descripción**, etc.
    - Establezca la dirección URL del sitio web como https://portal.contoso.com.
    - Establezca Ámbito de contrato de usuario/predeterminado de OAuth: r\_basicprofie y r\_emailaddress
    - Establezca la dirección URL de redireccionamiento de OAuth 2.0: https://portal.contoso.com/signin-linkedin.

3. Seleccione **Agregar aplicación**.

## <a name="yahoo-ydn-app-settings"></a>Yahoo! Configuración de aplicaciones en YDN

> [!NOTE]
> Debido a los continuos problemas de compatibilidad entre el extremo del proveedor actualizado de Yahoo YDN OAuth y los portales de Power Apps, los usuarios no pueden autenticarse temporalmente con el proveedor de identidades de Yahoo.

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
