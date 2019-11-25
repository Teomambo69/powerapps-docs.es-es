---
title: Configurar ajustes del proveedor de SAML 2.0 para un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar las opciones del proveedor de SAML 2.0 para un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: af5b0ae8eddb68127c7271fccb4696a23fedfc60
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759664"
---
# <a name="configure-saml-20-provider-settings-for-portals"></a>Configurar el proveedor SAML 2.0 para portales

para proporcionar autenticación externa, se pueden agregar uno o varios proveedores de identidad (IdP) compatibles con [SAML 2.0](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html). En este documento se describe cómo configurar varios proveedores de identidad para integrarse con un portal que actúe como proveedor de servicios.  

## <a name="ad-fs-idp"></a>AD FS (IdP)

Configuración de un proveedore de identidad como [!include[](../../../includes/pn-active-dir-fed-svcs-ad-fs.md)].

### <a name="create-an-ad-fs-relying-party-trust"></a>Cree un usuario de confianza de AD FS

> [!Note]
> Consulte [Configurar AD FS mediante PowerShell,](#configure-ad-fs-by-using-powershell) a continuación, para obtener información sobre cómo realizar estos pasos en un script [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)].

Utilizando la herramienta de administración [!include[](../../../includes/pn-adfs-short.md)], vaya a **Servicio** > **Descripciones de notificaciones**.

1.  Seleccione **Agregar descripción de notificación**.
2.  Especificar la notificación:

    -  Nombre para mostrar:**Identificador persistente**

    -  Identificador de notificación:**urn:oasis:names:tc:SAML:2.0:nameid-format:persistent**

    -  **Habilitar** la casilla para: Publicar esta descripción de notificación en metadatos de federación como tipo de notificación que este servicio de federación puede aceptar

    -  **Habilitar** casilla para: Publicar esta descripción de notificación en metadatos de federación como tipo de notificación que este servicio de federación puede enviar

3.  Seleccione **Aceptar**.

Utilizando la herramienta de administración [!include[](../../../includes/pn-adfs-short.md)], seleccione **Relaciones de confianza** >**Usuarios de confianza**.

1. Seleccione **Agregar usuario de confianza**.
2. Bienvenida: Seleccione **Inicio**.
3. Seleccionar origen de datos: Seleccione **Especifique datos del usuario de confianza manualmente** y luego seleccione **Siguiente**.
4. Especificar nombre para mostrar: Escriba un nombre y luego seleccione **Siguiente**.
   Ejemplo: https://portal.contoso.com/
5. Elegir perfil: Seleccione **Perfil de AD FS 2.0** y luego seleccione **Siguiente**.
6. Configurar certificado: Seleccione **Siguiente**.
7. Configurar dirección URL: Seleccione la casilla **Habilitar compatibilidad para el protocolo SAML 2.0 WebSSO**.
   Dirección URL de servicio SAML 2.0 SSO: especifique https://portal.contoso.com/signin-saml2
   - Nota: [!include[](../../../includes/pn-adfs-short.md)] requiere que el portal se ejecute en HTTPS.

   > [!Note] 
   > El extremo resultante tiene los siguientes valores:  
   > - Tipo de extremo: **Extremos de consumo de aserción SAML**             
   > - Enlace:**POST**                                            
   > - Índice: n/d (0)                                              
   > - URL: **https://portal.contoso.com/signin-saml2**

8. Configuración de identidades: especifique https://portal.contoso.com/, seleccione **Agregar**y, a continuación seleccione **Siguiente**.
   Si corresponde, pueden agregarse más identidades para cada portal del usuario de confianza adicional. Los usuarios podrán autenticarse en cualquiera o todas las identidades disponibles.
9. Elegir reglas de autorización de emisión: Seleccione **Permitir a todos los usuarios el acceso a este usuario de confianza** y luego seleccione **Siguiente**.
10. Listo para agregar confianza: Seleccione **Siguiente**.
11. Seleccione **Cerrar**.

Agregue la notificación **Id. de nombre** al usuario de confianza:

**Transforme el nombre de cuenta de [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)]** a la solicitud **Id. de nombre** (Transformar una notificación entrante):

- Tipo de notificación entrante:**Nombre de cuenta de [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)]**

- Tipo de notificación saliente: **Id. de nombre**

- Formato de Id. de nombre saliente: **Identificador persistente**

- Paso a través de todos los valores de notificaciones

### <a name="create-site-settings"></a>Crear configuraciones de sitio

Aplique la configuración del sitio del portal haciendo referencia al usuario de confianza de [!include[](../../../includes/pn-adfs-short.md)] anterior.

> [!Note]
> Una configuración [!include[](../../../includes/pn-adfs-short.md)] estándar (IdP) solo usa los siguientes parámetros (con valores de ejemplo): Authentication/SAML2/ADFS/MetadataAddress - <https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>  
> - Authentication/SAML2/ADFS/AuthenticationType - https://adfs.contoso.com/adfs/services/trust    
>   -   Use el valor del atributo **entityID** en el elemento raíz de los metadatos de federación (abra la **Dirección URL de MetadataAddress** en un explorador que sea el valor del ajuste de sitio anterior) 
> - Authentication/SAML2/ADFS/ServiceProviderRealm - https://portal.contoso.com/  
> - Authentication/SAML2/ADFS/AssertionConsumerServiceUrl - https://portal.contoso.com/signin-saml2  
>   Los **metadatos de federación** se pueden recuperar en **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** ejecutando el siguiente script en el servidor [!include[](../../../includes/pn-adfs-short.md)]: `Import-Module adfs`
>   `Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml`

Varios servicios de IdP pueden configurarse sustituyendo una etiqueta para la etiqueta [provider]. Cada etiqueta única forma un grupo de valores relacionados con un IdP. Ejemplos: ADFS, [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD, MyIdP


| Nombre de configuración del sitio                                             | Descripción                                                                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ExternalLoginEnabled              | Habilita o deshabilita el inicio de sesión y el registro de la cuenta externa. Valor predeterminado: true                                                                                                                                                                                                                                                                                                                                                            |
| Authentication/SAML2/[provider]/MetadataAddress             | Requerido. La dirección URL de metadatos de [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx) del servidor (STS) [!include[](../../../includes/pn-adfs-short.md)]. Comúnmente termina con la ruta de acceso:/FederationMetadata/2007-06/FederationMetadata.xml. Ejemplo: `https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml`. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx) |  
| Authentication/SAML2/[provider]/AuthenticationType          | Requerido. El tipo de middleware de autenticación OWIN. Especifique el valor del [atributo entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata) en la raíz del XML de metadatos de federación. Ejemplo: `https://adfs.contoso.com/adfs/services/trust`. [!include[](../../../includes/proc-more-information.md)] [AuthenticationOptions.AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)                                                            |  
| Authentication/SAML2/[provider]/ServiceProviderRealm<br>o <br>Authentication/SAML2/[provider]/Wtrealm                      | Requerido. El identificador del usuario de confianza [!include[](../../../includes/pn-adfs-short.md)]. Ejemplo: `https://portal.contoso.com/`. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx)                       |  
| Authentication/SAML2/[provider]/AssertionConsumerServiceUrl<br>o<br>Authentication/SAML2/[provider]/Wreply                       | Requerido. El extremo de aserción del consumidor SAML [!include[](../../../includes/pn-adfs-short.md)]. Ejemplo: https://portal.contoso.com/signin-saml2. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.Wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx)                                                                                                                                                                                                  |  
| Authentication/SAML2/[provider]/Caption                     | Recomendado. El texto que el usuario puede mostrar en una interfaz de usuario de inicio de sesión. Predeterminado: [provider]. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.Caption](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx)                |  
| Authentication/SAML2/[provider]/CallbackPath                | Una ruta limitada opcional en la que procesar la devolución de llamada de autenticación. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx)                                                                                                                                                                                                                      |  
| Authentication/SAML2/[provider]/BackchannelTimeout          | Valor de tiempo de espera para comunicaciones del canal posterior. Ejemplo: 00:05:00 (5 mins). [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx)                                                                                                                                                                                                                   |  
| Authentication/SAML2/[provider]/UseTokenLifetime            | Indica que la duración de la sesión de autenticación (por ejemplo, cookies) debe coincidir con la del token de autenticación. [WsFederationAuthenticationOptions.UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx).                                                                                                                                                                               |  
| Authentication/SAML2/[provider]/AuthenticationMode          | El modo de middleware de autenticación OWIN. [!include[](../../../includes/proc-more-information.md)] [AuthenticationOptions.AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)                                                                                                                                                                                                                                                                              |  
| Authentication/SAML2/[provider]/SignInAsAuthenticationType  | El AuthenticationType usado al crear el System.Security.Claims.ClaimsIdentity. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx)                                                                                                                                                                                                 |  
| Authentication/SAML2/[provider]/ValidAudiences              | Lista separada por comas de direcciones URL de la audiencia. [!include[](../../../includes/proc-more-information.md)] [TokenValidationParameters.AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)                                                                                                                                                                                                                                                                          |  
| Authentication/SAML2/[provider]/ClockSkew                   | El desplazamiento del reloj a aplicar al validar horas.                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentication/SAML2/[provider]/RequireExpirationTime       | Un valor que indica si los tokens deben tener un valor de expiración.                                                                                                                                                                                                                                                                                                                                                                      |
| Authentication/SAML2/[provider]/ValidateAudience            | Un booleano para controlar si el público se validará durante la validación de token.                                                                                                                                                                                                                                                                                                                                                         |

### <a name="idp-initiated-sign-in"></a>Inicio de sesión iniciado por IdP

[!include[](../../../includes/pn-adfs-short.md)] admite el perfil [inicio de seseión único iniciado por IdP (SSO)](https://technet.microsoft.com/library/jj127245.aspx) de la [especificación](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline) SAML 2.0. Para que el portal (proveedor de servicios) responda correctamente a la solicitud de SAML iniciada por el IdP, el parámetro [RelayState](https://blogs.technet.com/b/askds/archive/2012/09/27/ad-fs-2-0-relaystate.aspx) se debe codificar correctamente.  

El valor de cadena básico que se codificará en el parámetro SAML RelayState debe estar en formato **ReturnUrl=/content/sub-content/**, donde **/content/sub-content/** es la ruta a la página web a la que quiere ir en el portal (proveedor de servicios). La ruta se puede reemplazar por cualquier página web válida en el portal. El valor de cadena se codifica y se incluye en una cadena contenedora de formato **RPID=&lt;URL encoded RPID&gt;&RelayState&lt;=URL encoded RelayState&gt;**. Esta cadena completa se codifica una vez y se agrega a otro contenedor del formato **<https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=&lt;URL> encoded RPID/RelayState&gt;**.

Por ejemplo, dada la ruta de proveedor de servicio **/content/sub-content/** y el identificador de usuario de confianza **https://portal.contoso.com/**, construya la dirección URL con los pasos:

Codifique el valor ReturnUrl=/content/sub-content/

-   para obtener ReturnUrl%3D%2Fcontent%2Fsub-content%2F

<!-- -->

-   Codifique el valor https://portal.contoso.com/

<!-- -->

-   para obtener https%3A%2F%2Fportal.contoso.com%2F

<!-- -->

-   Codifique el valor RPID=https%3A%2F%2Fportal.contoso.com%2F&RelayState=ReturnUrl%3D%2Fcontent%2Fsub-content%2F

<!-- -->

-   para obtener RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F

<!-- -->

-   Anteponga la ruta SSO iniciada por IdP AD FS para obtener la dirección URL final

<!-- -->

-   https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F

El siguiente script de [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] puede usarse para crear la dirección URL (guardar en un archivo llamado Get-IdPInitiatedUrl.ps1).

```
<#

.SYNOPSIS 

Constructs an IdP-initiated SSO URL to access a portal page on the service provider.

.PARAMETER path

The path to the portal page.

.PARAMETER rpid

The relying party identifier.

.PARAMETER adfsPath

The AD FS IdP initiated SSO page.

.EXAMPLE

PS C:\\> .\\Get-IdPInitiatedUrl.ps1 -path "/content/sub-content/" -rpid "https://portal.contoso.com/" -adfsPath "https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx"

#>

param

(

[parameter(mandatory=$true,position=0)]

$path,

[parameter(mandatory=$true,position=1)]

$rpid,

[parameter(position=2)]

$adfsPath = https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx

)

$state = ReturnUrl=$path

$encodedPath = [uri]::EscapeDataString($state)

$encodedRpid = [uri]::EscapeDataString($rpid)

$encodedPathRpid = [uri]::EscapeDataString("RPID=$encodedRpid&RelayState=$encodedPath")

$idpInitiatedUrl = {0}?RelayState={1} -f $adfsPath, $encodedPathRpid

Write-Output $idpInitiatedUrl
```

## <a name="saml-20-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>Configuración de SAML 2.0 para [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]

La sección anterior que describe [!include[](../../../includes/pn-adfs-short.md)] también puede ser aplicada a [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD](https://msdn.microsoft.com/library/azure/mt168838.aspx), dado que [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD se comporta como un IdP compatible con [SAML 2.0](https://msdn.microsoft.com/library/azure/dn195591.aspx)&ndash;estándar. Para empezar, inicie sesión en el [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] Portal de administración](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) y cree o seleccione un directorio existente. Cuando un directorio está disponible siga las instrucciones para [agregar una aplicación](https://msdn.microsoft.com/library/azure/dn132599.aspx) al directorio.  

1.  En el menú **Aplicaciones** del directorio, seleccione **Agregar**.
2.  Elija **Agregue una aplicación que mi organización está desarrollando**.
3.  Especifique un nombre personalizado para la aplicación y luego elija el tipo de **aplicación web y/o API web**.
4.  Para la **Dirección URL de inicio de sesión** y la **URI de Id. de la aplicación**, especifique la dirección URL del portal para los dos campos https://portal.contoso.com/.
    Esto corresponde al valor de la configuración del sitio **ServiceProviderRealm** (Wtrealm).
5. En este punto, se crea una nueva aplicación. Vaya a la sección **Configurar** en el menú.

    En la sección **inicio de sesión único**, actualice la primera entrada **Dirección URL de respuesta** para incluir una ruta en la dirección URL https://portal.contoso.com/signin-azure-ad.

    Esto corresponde al valor del parámetro del sitio **AssertionConsumerServiceUrl** (Wreply).

6. En el menú de pie de página, seleccione **Ver extremos** y escriba el campo **Documento de metadatos de federación**.

Esto corresponde al valor del parámetro del sitio **MetadataAddress**.

-   Pegue esta dirección URL en una ventana del explorador para ver el XML de metadatos de federación y anote el atributo **entityID** del elemento raíz.
-   Esto corresponde al valor del parámetro del sitio**AuthenticationType**.

> [!Note]
> Una configuración AD [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] estándar solo usa los siguientes parámetros (con valores de ejemplo): Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/MetadataAddress - <https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml> 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AuthenticationType - <https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/>  
> - Use el valor del atributo**entityID** en el elemento raíz de los metadatos de federación (abra la**Dirección URL de MetadataAddress** en un explorador que sea del valor del ajuste de sitio anterior) 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/ServiceProviderRealm - <https://portal.contoso.com/>  
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AssertionConsumerServiceUrl - <https://portal.contoso.com/signin-azure-ad>                                                                                   |

## <a name="shibboleth-identity-provider-3"></a>Proveedor de identidad Shibboleth 3

Use las directrices siguientes para configurar correctamente [Proveedor de identidad Shibboleth](https://wiki.shibboleth.net/confluence/display/IDP30/Home) como servicio de IdP. Lo siguiente asume que el IdP se hospeda en el dominio https://idp.contoso.com.  

La dirección URL de metadatos de federación es https://idp.contoso.com/idp/shibboleth

-   El IdP se debe configurar para generar o servir como identificador persistente. Siga las instrucciones para habilitar [Generación de identificador persistente](https://wiki.shibboleth.net/confluence/display/IDP30/NameIDGenerationConfiguration).  

-   Los metadatos de federación de IdP (&lt;IDPSSODescriptor&gt;) deben configurarse para incluir un [enlace de redirección SSO](https://shibboleth.net/about/advanced.html). [Ejemplo](https://wiki.shibboleth.net/confluence/display/SHIB2/MetadataExample).  

```
<SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-Redirect"

Location=https://idp.contoso.com/idp/profile/SAML2/Redirect/SSO/>
```

Configure los proveedores de servicios (usuarios de confianza) configurando [metadata-providers.xml](https://wiki.shibboleth.net/confluence/display/IDP30/MetadataConfiguration).  

-   Cada metadato de federación de proveedor de servicios (&lt;SPSSODescriptor&gt;) debe incluir un enlace de publicación de servicio de consumidor de aserción. Una opción consiste en utilizar un [FilesystemMetadataProvider](https://wiki.shibboleth.net/confluence/display/IDP30/FilesystemMetadataProvider) y hacer referencia a un archivo de configuración que contenga:  

```
<AssertionConsumerService index=1 isDefault=true

Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST"

Location=https://portal.contoso.com/signin-saml2/>
```

El atributo Ubicación corresponde al valor**AssertionConsumerServiceUrl** (Wreply).

-   Los metadatos de federación de proveedor de servicios deben especificar un atributo **entityID** para el EntityDescriptor que corresponda a la configuración **AuthenticationType**.

**&lt;EntityDescriptor entityID=<https://portal.local.contoso.com/&gt>;...**

> [!Note] 
> Una configuración Shibboleth estándar sólo usa los siguientes valores (con valores de ejemplo):   
> Authentication/SAML2/Shibboleth/MetadataAddress - https://idp.contoso.com/idp/shibboleth   
> -   Authentication/SAML2/Shibboleth/AuthenticationType - https://idp.contoso.com/idp/shibboleth 
> -   Use el valor del atributo **entityID** en el elemento raíz de los metadatos de federación (abra la **Dirección URL de MetadataAddress** en un explorador que sea el valor del ajuste de sitio anterior)  
> -   Authentication/SAML2/Shibboleth/ServiceProviderRealm - https://portal.contoso.com/ 
> -   Authentication/SAML2/Shibboleth/AssertionConsumerServiceUrl - https://portal.contoso.com/signin-saml2 

### <a name="idp-initiated-sign-in"></a>Inicio de sesión iniciado por IdP

Shibboleth admite el perfil [SSO iniciado por IdP](https://wiki.shibboleth.net/confluence/display/SHIB2/IdPUnsolicitedSSO) de la [especificación](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline) SAML 2.0. Para que el portal (proveedor de servicios) responda correctamente a la solicitud de SAML iniciada por el IdP, el parámetro RelayState se debe codificar correctamente.  

El valor de cadena básico que se codificará en el parámetro SAML RelayState debe estar en formato **ReturnUrl=/content/sub-content/**, donde **/content/sub-content/** es la ruta a la página web a la que quiere ir en el portal (proveedor de servicios). La ruta se puede reemplazar por cualquier página web válida en el portal. La dirección URL completa de SSO iniciado por IdP debe estar en el formato <https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=&lt;URL> Id. del proveedor codificado como dirección URL&gt;&target=&lt;ruta de retorno codificada como dirección URL&gt;.

Por ejemplo, dada la ruta de proveedor de servicio **/content/sub-content/** y el identificador de usuario de confianza **https://portal.contoso.com/**, la dirección URL definitiva es https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=https%3A%2F%2Fportal.contoso.com%2F&target=ReturnUrl%3D%2Fcontent%2Fsub-content%2F

El siguiente script de [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] puede usarse para crear la dirección URL (guardar en un archivo llamado Get-ShibbolethIdPInitiatedUrl.ps1).

```
<# 

.SYNOPSIS

Constructs an IdP initiated SSO URL to access a portal page on the service provider.

.PARAMETER path

The path to the portal page.

.PARAMETER providerId

The relying party identifier.

.PARAMETER shibbolethPath

The Shibboleth IdP-initiated SSO page.

.EXAMPLE

PS C:\\> .\\Get-ShibbolethIdPInitiatedUrl.ps1 -path "/content/sub-content/" -providerId "https://portal.contoso.com/" -shibbolethPath "https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO"

#>

param

(

[parameter(mandatory=$true,position=0)]

$path,

[parameter(mandatory=$true,position=1)]

$providerId,

[parameter(position=2)]

$shibbolethPath = https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO

)

$state = ReturnUrl=$path

$encodedPath = [uri]::EscapeDataString($state)

$encodedRpid = [uri]::EscapeDataString($providerId)

$idpInitiatedUrl = {0}?providerId={1}&target={2} -f $shibbolethPath, $encodedRpid, $encodedPath

Write-Output $idpInitiatedUrl
```

## <a name="configure-ad-fs-by-using-powershell"></a>Configurar AD FS mediante PowerShell

El proceso para agregar un usuario de confianza en [!include[](../../../includes/pn-adfs-short.md)] también se puede realizar ejecutando el siguiente script [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] en el servidor de [!include[](../../../includes/pn-adfs-short.md)] (guarde el contenido en un archivo llamado Add-AdxPortalRelyingPartyTrustForSaml.ps1). Después de ejecutar el script, continúe con la configuración del sitio del portal.

```
<# 

.SYNOPSIS

Adds a SAML 2.0 relying party trust entry for a website.

.PARAMETER domain

The domain name of the portal.

.EXAMPLE

PS C:\\> .\\Add-AdxPortalRelyingPartyTrustForSaml.ps1 -domain portal.contoso.com

#>

param

(

[parameter(Mandatory=$true,Position=0)]

$domain,

[parameter(Position=1)]

$callbackPath = /signin-saml2

)

$VerbosePreference = Continue

$ErrorActionPreference = Stop

Import-Module adfs

Function Add-CrmRelyingPartyTrust

{

param (

[parameter(Mandatory=$true,Position=0)]

$name

)

$identifier = https://{0}/ -f $name

$samlEndpoint = New-ADFSSamlEndpoint -Binding POST -Protocol SAMLAssertionConsumer -Uri (https://{0}{1} -f $name, $callbackPath)

$identityProviderValue = Get-ADFSProperties | % { $_.Identifier.AbsoluteUri }

$issuanceTransformRules = @'

@RuleTemplate = MapClaims

@RuleName = Transform [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] Account Name to Name ID claim

c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname"]

=> issue(Type = "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier", Issuer = c.Issuer, OriginalIssuer = c.OriginalIssuer, Value = c.Value, ValueType = c.ValueType, Properties["https://schemas.xmlsoap.org/ws/2005/05/identity/claimproperties/format"] = "urn:oasis:names:tc:SAML:2.0:nameid-format:persistent");

@RuleTemplate = LdapClaims

@RuleName = Send LDAP Claims

c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname", Issuer == "AD AUTHORITY"]

=> issue(store = "[!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)]", types = ("https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname", "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname", "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"), query = ";givenName,sn,mail;{{0}}", param = c.Value);

'@ -f $identityProviderValue

$issuanceAuthorizationRules = @'

@RuleTemplate = AllowAllAuthzRule

=> issue(Type = https://schemas.microsoft.com/authorization/claims/permit, Value = true);

'@

Add-ADFSRelyingPartyTrust -Name $name -Identifier $identifier -SamlEndpoint $samlEndpoint -IssuanceTransformRules $issuanceTransformRules -IssuanceAuthorizationRules $issuanceAuthorizationRules

}

# add the 'Identity Provider' claim description if it is missing

if (-not (Get-ADFSClaimDescription | ? { $_.Name -eq Persistent Identifier })) {

Add-ADFSClaimDescription -name "Persistent Identifier" -ClaimType "urn:oasis:names:tc:SAML:2.0:nameid-format:persistent" -IsOffered:$true -IsAccepted:$true

}

# add the portal relying party trust

Add-CrmRelyingPartyTrust $domain
```

### <a name="see-also"></a>Vea también

[Configurar la autenticación del portal](configure-portal-authentication.md)  
[Establecer identidad de autenticación para un portal](set-authentication-identity.md)  
[Configuración del proveedor OAuth2 para portales](configure-oauth2-settings.md)  
[Configuración de proveedor Open ID Connect para portales](configure-openid-settings.md)  
[Configuración de proveedor de WS-Federation para portales](configure-ws-federation-settings.md)  
