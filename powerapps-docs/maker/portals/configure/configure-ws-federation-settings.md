---
title: Configuración del proveedor de WS-Federation para un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar la configuración del proveedor de WS-Federation para un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: c37bf02a0b1f76f7cb4c20ef838d6cf0583b019d
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978126"
---
# <a name="configure-ws-federation-provider-settings-for-portals"></a>Configuración del proveedor de WS-Federation para portales

Se puede Agregar un solo servidor de servicios de Federación de [!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)] (u otro servicio de token de seguridad compatible con [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx)) como proveedor de identidades. Además, se puede configurar un solo espacio de nombres de [ACS[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]](https://azure.microsoft.com/documentation/articles/active-directory-dotnet-how-to-use-access-control/) como un conjunto de proveedores de identidades individuales. La configuración de AD FS y ACS se basa en las propiedades de la clase [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.aspx) .

## <a name="create-an-ad-fs-relying-party-trust"></a>Crear un AD FS relación de confianza para usuario autenticado

Con la herramienta de administración de AD FS, vaya a **relaciones de confianza** &gt; confianzas para usuario **autenticado**.

1.  Seleccione **Agregar relación de confianza para usuario autenticado**.
2.  Bienvenido: seleccione **iniciar**.
3.  Seleccionar origen de datos: seleccione **escribir manualmente los datos sobre el usuario de confianza**y, después, seleccione **siguiente**.
4.  Especificar nombre para mostrar: escriba un **nombre**y, a continuación, seleccione **siguiente**.
    Ejemplo: https://portal.contoso.com/
5.  Elija perfil: seleccione **AD FS perfil 2,0**y, a continuación, seleccione **siguiente**.
6.  Configurar certificado: seleccione **siguiente**.
7.  Configurar dirección URL: Active la casilla **Habilitar compatibilidad para el protocolo de WS-Federation pasivo** .

Dirección URL del Protocolo de WS-Federation Passive del usuario de confianza: escriba https://portal.contoso.com/signin-federation

-   Nota: AD FS requiere que el portal se ejecute en **https**.

    > [!Note]
    > El punto de conexión resultante tiene la siguiente configuración: tipo de punto de conexión: **WS-Federation**
    > -   Enlace: **post**
    > -   Índice: n/a (0)
    > -   URL: **https://portal.contoso.com/signin-federation**

8.  Configurar identidades: especifique https://portal.contoso.com/, seleccione **Agregar**y, a continuación, seleccione **siguiente**.
    Si es aplicable, se pueden agregar más identidades para cada portal de usuarios de confianza adicional. Los usuarios podrán autenticarse en cualquiera de las identidades disponibles o en todas ellas.
9.  Elegir reglas de autorización de emisión: seleccione **permitir que todos los usuarios accedan a este usuario de confianza**y, después, seleccione **siguiente**.
10.  Listo para agregar confianza: seleccione **siguiente**.
11.  Haga clic en **Cerrar**.

Agregue la petición de **identificador de nombre** a la relación de confianza para usuario autenticado:

**Transformar [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] nombre de cuenta** en la demanda de **ID. de nombre** (transformar una demanda entrante):
- Tipo de notificaciones entrantes: nombre de cuenta de Windows
- Tipo de notificaciones salientes: ID. de nombre
- Formato de ID. de nombre saliente: no especificado
- Pasar a través todos los valores de notificaciones

### <a name="create-ad-fs-site-settings"></a>Crear AD FS configuración del sitio

Aplique la configuración del sitio del portal que hace referencia a la AD FS relación de confianza para usuario autenticado.

> [!Note]
> Una configuración de AD FS estándar (STS) solo usa la siguiente configuración (con valores de ejemplo):
> - Autenticación/WsFederation/ADFS/MetadataAddress- https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml
> - Autenticación/WsFederation/ADFS/AuthenticationType- http://adfs.contoso.com/adfs/services/trust
>   - Utilice el valor del atributo **entityID** en el elemento raíz de los metadatos de Federación (Abra la **dirección URL de MetadataAddress** en un explorador que sea el valor de la configuración del sitio anterior).
> - Autenticación/WsFederation/ADFS/Wtrealm- https://portal.contoso.com/
> - Autenticación/WsFederation/ADFS/Wreply- https://portal.contoso.com/signin-federation

Los **metadatos de WS-Federation** se pueden recuperar en **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** ejecutando el siguiente script en el servidor de AD FS:

```
Import-Module adfs
Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml
```


|                      Nombre de la configuración del sitio                      |                                                                                                                                                                                                                                                 Descripción                                                                                                                                                                                                                                                 |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      Autenticación/registro/ExternalLoginEnabled       |                                                                                                                                                                                                                Habilita o deshabilita el registro y el inicio de sesión de la cuenta externa. Valor predeterminado: true                                                                                                                                                                                                                 |
|      Autenticación/WsFederation/ADFS/MetadataAddress       | Obligatorio. La dirección URL de metadatos de [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx) del servidor de AD FS (STS). Normalmente, finaliza con la ruta de acceso:/FederationMetadata/2007-06/FederationMetadata. Xml. Ejemplo:<https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>. Para obtener más información: [WsFederationAuthenticationOptions. MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx). |
|     Autenticación/WsFederation/ADFS/AuthenticationType     |            Obligatorio. Tipo de middleware de autenticación OWIN. Especifique el valor del atributo [entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata) en la raíz del XML de metadatos de Federación. Ejemplo: http://adfs.contoso.com/adfs/services/trust. Para obtener más información: [AuthenticationOptions. AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx).             |
|          Autenticación/WsFederation/ADFS/Wtrealm           |                                                                                                              Obligatorio. Identificador del usuario de confianza AD FS. Ejemplo: `https://portal.contoso.com/`. Para obtener más información: [WsFederationAuthenticationOptions. Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx).                                                                                                               |
|           Autenticación/WsFederation/ADFS/Wreply           |                                                                                                     Obligatorio. El punto de conexión pasivo de AD FS WS-Federation. Ejemplo: https://portal.contoso.com/signin-federation. Para obtener más información: [WsFederationAuthenticationOptions. Wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx).                                                                                                     |
|          Autenticación/WsFederation/ADFS/Caption           |                                                                                                           Recomendar. Texto que el usuario puede mostrar en una interfaz de usuario de inicio de sesión. Valor predeterminado: ADFS. Para obtener más información: [WsFederationAuthenticationOptions. Caption](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx).                                                                                                            |
|        Autenticación/WsFederation/ADFS/CallbackPath        |                                                                                                             Una ruta de acceso restringida opcional en la que se va a procesar la devolución de llamada de autenticación. Para obtener más información: [WsFederationAuthenticationOptions. CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx).                                                                                                              |
|       Autenticación/WsFederation/ADFS/SignOutWreply        |                                                                                                                               El valor de "wreply" usado durante el cierre de sesión. Para obtener más información: [WsFederationAuthenticationOptions. SignOutWreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signoutwreply.aspx).                                                                                                                               |
|     Autenticación/WsFederation/ADFS/BackchannelTimeout     |                                                                                                         Valor de tiempo de espera para las comunicaciones de canal posterior. Ejemplo: 00:05:00 (5 minutos). Para obtener más información: [WsFederationAuthenticationOptions. BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx).                                                                                                         |
| Autenticación/WsFederation/ADFS/RefreshOnIssuerKeyNotFound |                                                                                  Determina si se debe intentar una actualización de metadatos después de un SecurityTokenSignatureKeyNotFoundException. Para obtener más información: [WsFederationAuthenticationOptions. RefreshOnIssuerKeyNotFound](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.refreshonissuerkeynotfound.aspx).                                                                                  |
|      Autenticación/WsFederation/ADFS/UseTokenLifetime      |                                                                                                   Indica que la duración de la sesión de autenticación (por ejemplo, cookies) debe coincidir con la del token de autenticación. [WsFederationAuthenticationOptions. UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx).                                                                                                   |
|     Autenticación/WsFederation/ADFS/AuthenticationMode     |                                                                                                                                            El modo de middleware de autenticación OWIN. Para obtener más información: [AuthenticationOptions. AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx).                                                                                                                                             |
| Autenticación/WsFederation/ADFS/SignInAsAuthenticationType |                                                                                            AuthenticationType que se usa al crear System. Security. Claims. ClaimsIdentity. Para obtener más información: [WsFederationAuthenticationOptions. SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx).                                                                                            |
|       Autenticación/WsFederation/ADFS/ValidAudiences       |                                                                                                                                         Lista de direcciones URL de audiencia separadas por comas. Para obtener más información: [TokenValidationParameters. AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx).                                                                                                                                          |
|        Autenticación/WsFederation/ADFS/ValidIssuers        |                                                                                                                                              Lista separada por comas de direcciones URL de emisor. Para obtener más información: [TokenValidationParameters. ValidIssuers](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx).                                                                                                                                               |
|         Autenticación/WsFederation/ADFS/ClockSkew          |                                                                                                                                                                                                                               El sesgo de reloj que se aplica al validar los tiempos.                                                                                                                                                                                                                                |
|       Autenticación/WsFederation/ADFS/NameClaimType        |                                                                                                                                                                                                                     El tipo de demanda que usa ClaimsIdentity para almacenar la demanda de nombre.                                                                                                                                                                                                                      |
|       Autenticación/WsFederation/ADFS/RoleClaimType        |                                                                                                                                                                                                                     El tipo de demanda que usa ClaimsIdentity para almacenar la demanda de rol.                                                                                                                                                                                                                      |
|   Autenticación/WsFederation/ADFS/RequireExpirationTime    |                                                                                                                                                                                                                     Valor que indica si los tokens deben tener un valor de ' expiración '.                                                                                                                                                                                                                      |
|    Autenticación/WsFederation/ADFS/RequireSignedTokens     |                                                                                                                                                                       Un valor que indica si un System. IdentityModel. tokens. SecurityToken xmlns =<http://ddue.schemas.microsoft.com/authoring/2003/5> puede ser válido si no está firmado.                                                                                                                                                                       |
|      Autenticación/WsFederation/ADFS/SaveSigninToken       |                                                                                                                                                                                                               Valor booleano que se va a controlar si el token original se guarda cuando se crea una sesión.                                                                                                                                                                                                                |
|       Autenticación/WsFederation/ADFS/ValidateActor        |                                                                                                                                                                                                   Un valor que indica si se debe validar System. IdentityModel. tokens. JwtSecurityToken. actor.                                                                                                                                                                                                    |
|      Autenticación/WsFederation/ADFS/ValidateAudience      |                                                                                                                                                                                                               Valor booleano que se va a utilizar para controlar si la audiencia se valida durante la validación de tokens.                                                                                                                                                                                                               |
|       Autenticación/WsFederation/ADFS/ValidateIssuer       |                                                                                                                                                                                                                Valor booleano que se va a utilizar para controlar si el emisor se validará durante la validación del token.                                                                                                                                                                                                                |
|      Autenticación/WsFederation/ADFS/ValidateLifetime      |                                                                                                                                                                                                               Valor booleano que se va a utilizar para controlar si se validará la duración durante la validación de tokens.                                                                                                                                                                                                               |
|  Autenticación/WsFederation/ADFS/ValidateIssuerSigningKey  |                                                                                                                                                         Valor booleano que controla si se llama a la validación de System. IdentityModel. tokens. SecurityKey que firmó el securityToken xmlns =<http://ddue.schemas.microsoft.com/authoring/2003/5>.                                                                                                                                                          |
|            Autenticación/WsFederation/ADFS/WHr             |                                                                                                                                       Especifica un parámetro "WHr" en la dirección URL de redireccionamiento del proveedor de identidades. Para obtener más información: [wsFederation](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation).                                                                                                                                       |

## <a name="ws-federation-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>Configuración de WS-Federation para [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]

La sección anterior que describe AD FS se puede aplicar también a [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] ([[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ad](https://msdn.microsoft.com/library/azure/mt168838.aspx)), ya que [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ad se comporta como un servicio de token de seguridad compatible con [WS-Federation](https://docs.microsoft.com/azure/active-directory/develop/active-directory-developers-guide) estándar. Para empezar, inicie sesión en el [portal de administración de[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) y cree o seleccione un directorio existente. Cuando un directorio esté disponible, siga las instrucciones para [Agregar una aplicación](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) al directorio.

1.  En el menú **aplicaciones** del directorio, seleccione **Agregar**.
2.  Elija **Agregar una aplicación que mi organización está desarrollando**.
3.  Especifique un **nombre** personalizado para la aplicación y, a continuación, elija la **aplicación Web de tipo y/o la API Web**.
4.  Para la **dirección URL de inicio de sesión** y el **URI de ID**. de aplicación, especifique la dirección URL del portal para ambos campos https://portal.contoso.com/.
    - Esto corresponde al valor de configuración del sitio de **Wtrealm** .
5.  En este momento, se crea una nueva aplicación. Vaya a la sección **configurar** en el menú.
6.  En la sección **Inicio de sesión único** , actualice la primera entrada de **dirección URL de respuesta** para incluir una ruta de acceso en la dirección URL http://portal.contoso.com/signin-azure-ad.
    - Esto corresponde al valor de configuración del sitio de **Wreply** .
7.  Seleccione **Guardar** en el pie de página.
8.  En el menú de pie de página, seleccione **Ver extremos** y anote el campo de **documento de metadatos de Federación** .

    - Esto corresponde al valor de configuración del sitio de **MetadataAddress** .
    - Pegue esta dirección URL en una ventana del explorador para ver el XML de metadatos de Federación y anote el atributo **entityID** del elemento raíz.
    - Esto corresponde al valor de configuración del sitio de **AuthenticationType** .

> [!Note]
> Una configuración de [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] estándar de AD solo usa la configuración siguiente (con valores de ejemplo):
> - Autenticación/WsFederation/ADFS/MetadataAddress- https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml
> - Autenticación/WsFederation/ADFS/AuthenticationType- https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/
>   - Utilice el valor del atributo **entityID** en el elemento raíz de los metadatos de Federación (Abra la **dirección URL de MetadataAddress** en un explorador que sea el valor de la configuración del sitio anterior).
> - Autenticación/WsFederation/ADFS/Wtrealm- https://portal.contoso.com/
> - Autenticación/WsFederation/ADFS/Wreply- https://portal.contoso.com/signin-azure-ad

### <a name="see-also"></a>Vea también

[Configurar la autenticación del portal](configure-portal-authentication.md)  
[Establecimiento de la identidad de autenticación para un portal](set-authentication-identity.md)  
[Configuración del proveedor de OAuth2 para portales](configure-oauth2-settings.md)  
[Open ID Connect configuración del proveedor para portales](configure-openid-settings.md)  
[Configuración del proveedor de SAML 2,0 para portales](configure-saml2-settings.md)  
