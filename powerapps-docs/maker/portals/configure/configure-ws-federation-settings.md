---
title: Configurar ajustes del proveedor de WS-Federation para un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar las opciones del proveedor de WS-Federation para un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 2a668f501a54472da0335344997c049794794783
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759620"
---
# <a name="configure-ws-federation-provider-settings-for-portals"></a>Configurar valores de proveedor de WS-Federation para portales

Un solo servidor de Federation Services [!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)] se puede agregar (u otro servicio de token de seguridad, o STS, compatible con [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx)), como proveedor de identidad. Además, un solo espacio de nombres [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ACS](https://azure.microsoft.com/documentation/articles/active-directory-dotnet-how-to-use-access-control/) se puede configurar como un conjunto de proveedores de identidad individuales. Los valores de AD FS y ACS se basan en las propiedades de la clase [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.aspx).

## <a name="create-an-ad-fs-relying-party-trust"></a>Cree un usuario de confianza de AD FS

Utilizando la herramienta de administración de AD FS, vaya a **Relaciones de confianza** &gt; **Usuarios de confianza**.

1.  Seleccione **Agregar usuario de confianza**.
2.  Bienvenida: Seleccione **Inicio**.
3.  Seleccionar origen de datos: Seleccione **Especifique datos del usuario de confianza manualmente** y luego seleccione **Siguiente**.
4.  Especificar nombre para mostrar: Escriba un **nombre** y luego seleccione **Siguiente**.
    Ejemplo: https://portal.contoso.com/
5.  Elegir perfil: Seleccione **Perfil de AD FS 2.0** y luego seleccione **Siguiente**.
6.  Configurar certificado: Seleccione **Siguiente**.
7.  Configurar dirección URL: Seleccione la casilla **Habilitar compatibilidad para el protocolo WS-Federation Passive**.

Dirección URL del protocolo WS-Federation Passive del usuario de confianza: escriba https://portal.contoso.com/signin-federation

-   Nota: AD FS requiere que el portal se ejecute en **HTTPS**.

    > [!Note]
    > La extremo resultante tiene los siguientes valores: Tipo de extremo: **WS-Federation**
    > -   Enlace:**POST**
    > -   Índice: n/d (0)
    > -   Dirección URL: **https://portal.contoso.com/signin-federation**

8.  Configuración de identidades: especifique https://portal.contoso.com/, seleccione **Agregar**y, a continuación seleccione **Siguiente**.
    Si corresponde, más identidades pueden agregarse para cada portal del usuario de confianza adicional. Los usuarios podrán autenticarse en cualquiera o todas las identidades disponibles.
9.  Elegir reglas de autorización de emisión: Seleccione **Permitir a todos los usuarios el acceso a este usuario de confianza** y luego seleccione **Siguiente**.
10.  Listo para agregar confianza: Seleccione **Siguiente**.
11.  Seleccione **Cerrar**.

Agregue la notificación **Id. de nombre** al usuario de confianza:

**Transforme el nombre de cuenta de [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)]** a la solicitud **Id. de nombre** (Transformar una notificación entrante):
- Tipo de notificación entrante: Nombre de cuenta de Windows
- Tipo de notificación saliente: Id. de nombre
- Formato de Id. de nombre saliente: Sin especificar
- Paso a través de todos los valores de notificaciones

### <a name="create-ad-fs-site-settings"></a>Crear configuraciones de sitio de AD FS

Aplique la configuración del sitio del portal haciendo referencia al usuario de confianza de AD FS anterior.

> [!Note]
> Una configuración de AD FS (STS) estándar sólo usa los siguientes valores (con valores de ejemplo):
> - Authentication/WsFederation/ADFS/MetadataAddress: https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType: https://adfs.contoso.com/adfs/services/trust
>   - Use el valor del atributo **entityID** en el elemento raíz de los metadatos de federación (abra la **Dirección URL de MetadataAddress** en un explorador que sea el valor del ajuste de sitio anterior)
> - Authentication/WsFederation/ADFS/Wtrealm: https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/Wreply: https://portal.contoso.com/signin-federation

Los **metadatos de WS-Federation** se pueden recuperar en **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** ejecutando el siguiente script en el servidor de AD FS:

```
Import-Module adfs
Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml
```


|                      Nombre de configuración del sitio                      |                                                                                                                                                                                                                                                 Descripción                                                                                                                                                                                                                                                 |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      Authentication/Registration/ExternalLoginEnabled       |                                                                                                                                                                                                                Habilita o deshabilita el inicio de sesión y el registro de la cuenta externa. Valor predeterminado: true                                                                                                                                                                                                                 |
|      Authentication/WsFederation/ADFS/MetadataAddress       | Requerido. La [dirección URL de metadatos de WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx) del servidor de AD FS (STS). Comúnmente termina con la ruta de acceso:/FederationMetadata/2007-06/FederationMetadata.xml . Ejemplo:<https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>. Para obtener más información: [WsFederationAuthenticationOptions.MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx). |
|     Authentication/WsFederation/ADFS/AuthenticationType     |            Requerido. El tipo de middleware de autenticación OWIN. Especifique el valor del [atributo entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata) en la raíz del XML de metadatos de federación. Ejemplo: https://adfs.contoso.com/adfs/services/trust. Para obtener más información: [AuthenticationOptions.AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx).             |
|          Authentication/WsFederation/ADFS/Wtrealm           |                                                                                                              Requerido. El identificador del usuario de confianza de AD FS. Ejemplo: `https://portal.contoso.com/`. Para obtener más información: [WsFederationAuthenticationOptions.Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx).                                                                                                               |
|           Authentication/WsFederation/ADFS/Wreply           |                                                                                                     Requerido. El extremo de AD FS WS-Federation Passive. Ejemplo: https://portal.contoso.com/signin-federation. Para obtener más información: [WsFederationAuthenticationOptions.Wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx).                                                                                                     |
|          Authentication/WsFederation/ADFS/Caption           |                                                                                                           Recomendado. El texto que el usuario puede mostrar en una interfaz de usuario de inicio de sesión. Predeterminado: ADFS. Para obtener más información: [WsFederationAuthenticationOptions.Caption](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx).                                                                                                            |
|        Authentication/WsFederation/ADFS/CallbackPath        |                                                                                                             Una ruta limitada opcional en la que procesar la devolución de llamada de autenticación. Para obtener más información: [WsFederationAuthenticationOptions.CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx).                                                                                                              |
|       Authentication/WsFederation/ADFS/SignOutWreply        |                                                                                                                               El valor 'wreply'usado durante el cierre de sesión. Para obtener más información: [WsFederationAuthenticationOptions.SignOutWreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signoutwreply.aspx).                                                                                                                               |
|     Authentication/WsFederation/ADFS/BackchannelTimeout     |                                                                                                         Valor de tiempo de espera para comunicaciones del canal posterior. Ejemplo: 00:05:00 (5 mins). Para obtener más información: [WsFederationAuthenticationOptions.BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx).                                                                                                         |
| Authentication/WsFederation/ADFS/RefreshOnIssuerKeyNotFound |                                                                                  Determina si una actualización de metadatos debe intentarse después de una SecurityTokenSignatureKeyNotFoundException. Para obtener más información: [WsFederationAuthenticationOptions.RefreshOnIssuerKeyNotFound](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.refreshonissuerkeynotfound.aspx).                                                                                  |
|      Authentication/WsFederation/ADFS/UseTokenLifetime      |                                                                                                   Indica que la duración de la sesión de autenticación (por ejemplo, cookies) debe coincidir con la del token de autenticación. [WsFederationAuthenticationOptions.UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx).                                                                                                   |
|     Authentication/WsFederation/ADFS/AuthenticationMode     |                                                                                                                                            El modo de middleware de autenticación OWIN. Para obtener más información: [AuthenticationOptions.AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx).                                                                                                                                             |
| Authentication/WsFederation/ADFS/SignInAsAuthenticationType |                                                                                            El AuthenticationType usado al crear el System.Security.Claims.ClaimsIdentity. Para obtener más información: [WsFederationAuthenticationOptions.SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx).                                                                                            |
|       Authentication/WsFederation/ADFS/ValidAudiences       |                                                                                                                                         Lista separada por comas de direcciones URL de la audiencia. Para obtener más información: [TokenValidationParameters.AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx).                                                                                                                                          |
|        Authentication/WsFederation/ADFS/ValidIssuers        |                                                                                                                                              Lista separada por comas de direcciones URL del emisor. Para obtener más información: [TokenValidationParameters.ValidIssuers](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx).                                                                                                                                               |
|         Authentication/WsFederation/ADFS/ClockSkew          |                                                                                                                                                                                                                               El desplazamiento del reloj a aplicar al validar horas.                                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/NameClaimType        |                                                                                                                                                                                                                     El tipo de notificación usado por ClaimsIdentity para almacenar la notificación de nombre.                                                                                                                                                                                                                      |
|       Authentication/WsFederation/ADFS/RoleClaimType        |                                                                                                                                                                                                                     El tipo de notificación usado por ClaimsIdentity para almacenar la notificación de rol.                                                                                                                                                                                                                      |
|   Authentication/WsFederation/ADFS/RequireExpirationTime    |                                                                                                                                                                                                                     Un valor que indica si los tokens deben tener un valor de 'expiración'.                                                                                                                                                                                                                      |
|    Authentication/WsFederation/ADFS/RequireSignedTokens     |                                                                                                                                                                       Un valor que indica si un System.IdentityModel.Tokens.SecurityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5> puede ser válido si no está firmado.                                                                                                                                                                       |
|      Authentication/WsFederation/ADFS/SaveSigninToken       |                                                                                                                                                                                                               Un booleano para controlar si el token original se guarda cuando se crea una sesión.                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/ValidateActor        |                                                                                                                                                                                                   Un valor que indica si el System.IdentityModel.Tokens.JwtSecurityToken.Actor debe validarse.                                                                                                                                                                                                    |
|      Authentication/WsFederation/ADFS/ValidateAudience      |                                                                                                                                                                                                               Un booleano para controlar si el público se validará durante la validación de token.                                                                                                                                                                                                               |
|       Authentication/WsFederation/ADFS/ValidateIssuer       |                                                                                                                                                                                                                Un booleano para controlar si el emisor se validará durante la validación de token.                                                                                                                                                                                                                |
|      Authentication/WsFederation/ADFS/ValidateLifetime      |                                                                                                                                                                                                               Un booleano para controlar si la duración se validará durante la validación de token.                                                                                                                                                                                                               |
|  Authentication/WsFederation/ADFS/ValidateIssuerSigningKey  |                                                                                                                                                         Un valor booleano que controla si se llama a la validación de System.IdentityModel.Tokens.SecurityKey que firmó el securityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5>.                                                                                                                                                          |
|            Authentication/WsFederation/ADFS/Whr             |                                                                                                                                       Especifica un parámetro "whr" en la dirección URL de redirección del proveedor de identidad. Para obtener más información: [wsFederation](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation).                                                                                                                                       |

## <a name="ws-federation-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>Configuración de WS-Federation para [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]

La sección anterior que describe AD FS también puede ser aplicada a [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] ([[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD](https://msdn.microsoft.com/library/azure/mt168838.aspx)) dado que [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD se comporta como un servicio de token de seguridad compatible con [WS-Federation](https://docs.microsoft.com/azure/active-directory/develop/active-directory-developers-guide). Para empezar, inicie sesión en el Portal de administración de [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) y cree o seleccione un directorio existente. Cuando un directorio está disponible siga las instrucciones para [agregar una aplicación](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) al directorio.

1.  En el menú **Aplicaciones** del directorio, seleccione **Agregar**.
2.  Elija **Agregue una aplicación que mi organización está desarrollando**.
3.  Especifique un **nombre** personalizado para la aplicación y luego elija el tipo **aplicación web y/o API web**.
4.  Para la **Dirección URL de inicio de sesión** y la **URI de Id. de la aplicación**, especifique la dirección URL del portal para ambos campos https://portal.contoso.com/.
    - Esto corresponde al valor del parámetro del sitio **Wtrealm**.
5.  En este punto, se crea una nueva aplicación. Vaya a la sección **Configurar** en el menú.
6.  En la sección **inicio de sesión único**, actualice la primera entrada **Dirección URL de respuesta** para incluir una ruta en la dirección URL https://portal.contoso.com/signin-azure-ad.
    - Esto corresponde al valor del parámetro del sitio **Wreply**.
7.  Seleccione **Guardar** en el pie de página.
8.  En el menú de pie de página, seleccione **Ver extremos** y escriba el campo **Documento de metadatos de federación**.

    - Esto corresponde al valor del parámetro del sitio **MetadataAddress**.
    - Pegue esta dirección URL en una ventana del explorador para ver el XML de metadatos de federación y anote el atributo **entityID** del elemento raíz.
    - Esto corresponde al valor del parámetro del sitio **AuthenticationType**.

> [!Note]
> Una configuración de [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD estándar sólo usa los siguientes valores (con valores de ejemplo):
> - Authentication/WsFederation/ADFS/MetadataAddress: https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType: https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/
>   - Use el valor del atributo **entityID** en el elemento raíz de los metadatos de federación (abra la **Dirección URL de MetadataAddress** en un explorador que sea el valor del ajuste de sitio anterior)
> - Authentication/WsFederation/ADFS/Wtrealm: https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/Wreply: https://portal.contoso.com/signin-azure-ad

### <a name="see-also"></a>Vea también

[Configurar la autenticación del portal](configure-portal-authentication.md)  
[Establecer identidad de autenticación para un portal](set-authentication-identity.md)  
[Configuración del proveedor OAuth2 para portales](configure-oauth2-settings.md)  
[Configuración de proveedor Open ID Connect para portales](configure-openid-settings.md)  
[Configuración del proveedor SAML 2.0 para portales](configure-saml2-settings.md)  
