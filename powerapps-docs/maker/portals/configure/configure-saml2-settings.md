---
title: Configuración del proveedor de SAML 2,0 para un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar la configuración del proveedor de SAML 2,0 para un portal.
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
ms.locfileid: "73542738"
---
# <a name="configure-saml-20-provider-settings-for-portals"></a>Configuración del proveedor de SAML 2,0 para portales

Para proporcionar autenticación externa, puede agregar uno o varios proveedores de identidades compatibles con [SAML 2,0](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html)(IDP). En este documento se describe cómo configurar varios proveedores de identidades para que se integren con un portal que actúa como proveedor de servicios.  

## <a name="ad-fs-idp"></a>AD FS (IdP)

Configuración de un proveedor de identidades como [!include[](../../../includes/pn-active-dir-fed-svcs-ad-fs.md)].

### <a name="create-an-ad-fs-relying-party-trust"></a>Crear un AD FS relación de confianza para usuario autenticado

> [!Note]
> Para más información sobre cómo realizar estos pasos en un script de [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)], consulte [configuración de AD FS mediante PowerShell](#configure-ad-fs-by-using-powershell).

Con la herramienta de administración de [!include[](../../../includes/pn-adfs-short.md)], vaya a **Service** > **descripciones de notificaciones**.

1.  Seleccione **Agregar Descripción de notificaciones**.
2.  Especifique la demanda:

    -  Nombre para mostrar: **identificador persistente**

    -  Identificador de notificación: **urn: oasis: names: TC: SAML: 2.0: NameID-Format: persistent**

    -  **Habilitar** casilla para: publicar esta descripción de notificaciones en los metadatos de Federación como un tipo de demanda que este servicio de Federación puede aceptar

    -  **Habilitar** casilla para: publicar esta descripción de notificaciones en los metadatos de Federación como un tipo de demanda que este servicio de Federación puede enviar

3.  Seleccione **Aceptar**.

Mediante la herramienta de administración de [!include[](../../../includes/pn-adfs-short.md)], seleccione **relaciones de confianza** >confianzas para usuario **autenticado**.

1. Seleccione **Agregar relación de confianza para usuario autenticado**.
2. Bienvenido: seleccione **iniciar**.
3. Seleccionar origen de datos: seleccione **escribir manualmente los datos sobre el usuario de confianza**y, después, seleccione **siguiente**.
4. Especificar nombre para mostrar: escriba un nombre y, a continuación, seleccione **siguiente**.
   Ejemplo: https://portal.contoso.com/
5. Elija perfil: seleccione **AD FS perfil 2,0**y, a continuación, seleccione **siguiente**.
6. Configurar certificado: seleccione **siguiente**.
7. Configurar dirección URL: Active la casilla **Habilitar la compatibilidad con el protocolo SAML 2,0 webs** .
   Dirección URL del servicio SSO de SAML 2,0 de usuario de confianza: escriba https://portal.contoso.com/signin-saml2
   - Nota: [!include[](../../../includes/pn-adfs-short.md)] requiere que el portal se ejecute en HTTPS.

   > [!Note] 
   > El punto de conexión resultante tiene la siguiente configuración: 
   > - Tipo de punto de conexión: **usar extremos de aserción de SAML**             
   > - Enlace: **post**                                            
   > - Índice: n/a (0)                                              
   > - URL: **https://portal.contoso.com/signin-saml2**

8. Configurar identidades: especifique https://portal.contoso.com/, seleccione **Agregar**y, a continuación, seleccione **siguiente**.
   Si es aplicable, puede agregar más identidades para cada portal de usuarios de confianza adicional. Los usuarios podrán autenticarse en cualquiera de las identidades disponibles o en todas ellas.
9. Elegir reglas de autorización de emisión: seleccione **permitir que todos los usuarios accedan a este usuario de confianza**y, después, seleccione **siguiente**.
10. Listo para agregar confianza: seleccione **siguiente**.
11. Haga clic en **Cerrar**.

Agregue la petición de **identificador de nombre** a la relación de confianza para usuario autenticado:

**Transformar[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] nombre de cuenta** en la demanda de **ID. de nombre** (transformar una demanda entrante):

- Tipo de notificaciones entrantes: **[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] nombre de cuenta**

- Tipo de notificaciones salientes: **ID. de nombre**

- Formato de ID. de nombre saliente: **identificador persistente**

- Pasar a través todos los valores de notificaciones

### <a name="create-site-settings"></a>Crear configuración del sitio

Aplique la configuración del sitio del portal que hace referencia a la [!include[](../../../includes/pn-adfs-short.md)] relación de confianza para usuario autenticado.

> [!Note]
> Una configuración de [!include[](../../../includes/pn-adfs-short.md)] estándar (IdP) solo usa la configuración siguiente (con valores de ejemplo): Authentication/SAML2/ADFS/MetadataAddress-<https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>  
> - Autenticación/SAML2/ADFS/AuthenticationType- https://adfs.contoso.com/adfs/services/trust    
>   -   Utilice el valor del atributo **entityID** en el elemento raíz de los metadatos de Federación (Abra la **dirección URL de MetadataAddress** en un explorador que sea el valor de la configuración del sitio anterior). 
> - Autenticación/SAML2/ADFS/ServiceProviderRealm- https://portal.contoso.com/  
> - Autenticación/SAML2/ADFS/AssertionConsumerServiceUrl- https://portal.contoso.com/signin-saml2  
>   Los **metadatos de Federación** se pueden recuperar en **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** ejecutando el siguiente script en el servidor de [!include[](../../../includes/pn-adfs-short.md)]: `Import-Module adfs`
>   `Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml`

Se pueden configurar varios servicios IdP sustituyendo una etiqueta por la etiqueta [Provider]. Cada etiqueta única forma un grupo de opciones de configuración relacionadas con un IdP. Ejemplos: ADFS, [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD, MyIdP


| Nombre de la configuración del sitio                                             | Descripción                                                                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autenticación/registro/ExternalLoginEnabled              | Habilita o deshabilita el registro y el inicio de sesión de la cuenta externa. Valor predeterminado: true                                                                                                                                                                                                                                                                                                                                                            |
| Authentication/SAML2/[Provider]/MetadataAddress             | Obligatorio. La dirección URL de metadatos de [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx) del servidor de [!include[](../../../includes/pn-adfs-short.md)] (STS). Normalmente finaliza con la ruta de acceso:/FederationMetadata/2007-06/FederationMetadata. Xml. Ejemplo: `https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml`. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions. MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx) |  
| Authentication/SAML2/[Provider]/AuthenticationType          | Obligatorio. Tipo de middleware de autenticación OWIN. Especifique el valor del atributo [entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata) en la raíz del XML de metadatos de Federación. Ejemplo: `https://adfs.contoso.com/adfs/services/trust`. [!include[](../../../includes/proc-more-information.md)] [AuthenticationOptions. AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)                                                            |  
| Authentication/SAML2/[Provider]/ServiceProviderRealm<br>O bien <br>Authentication/SAML2/[Provider]/Wtrealm                      | Obligatorio. Identificador del usuario de confianza [!include[](../../../includes/pn-adfs-short.md)]. Ejemplo: `https://portal.contoso.com/`. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions. Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx)                       |  
| Authentication/SAML2/[Provider]/AssertionConsumerServiceUrl<br>O bien<br>Authentication/SAML2/[Provider]/Wreply                       | Obligatorio. [!include[](../../../includes/pn-adfs-short.md)] extremo de aserción de consumidor SAML. Ejemplo: https://portal.contoso.com/signin-saml2. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions. Wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx)                                                                                                                                                                                                  |  
| Authentication/SAML2/[Provider]/Caption                     | Recomendar. Texto que el usuario puede mostrar en una interfaz de usuario de inicio de sesión. Valor predeterminado: [Provider]. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions. Caption](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx)                |  
| Authentication/SAML2/[Provider]/CallbackPath                | Una ruta de acceso restringida opcional en la que se va a procesar la devolución de llamada de autenticación. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions. CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx)                                                                                                                                                                                                                      |  
| Authentication/SAML2/[Provider]/BackchannelTimeout          | Valor de tiempo de espera para las comunicaciones de canal de reserva. Ejemplo: 00:05:00 (5 minutos). [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions. BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx)                                                                                                                                                                                                                   |  
| Authentication/SAML2/[Provider]/UseTokenLifetime            | Indica que la duración de la sesión de autenticación (por ejemplo, cookies) debe coincidir con la del token de autenticación. [WsFederationAuthenticationOptions. UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx).                                                                                                                                                                               |  
| Authentication/SAML2/[Provider]/AuthenticationMode          | El modo de middleware de autenticación OWIN. [!include[](../../../includes/proc-more-information.md)] [AuthenticationOptions. AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)                                                                                                                                                                                                                                                                              |  
| Authentication/SAML2/[Provider]/SignInAsAuthenticationType  | AuthenticationType que se usa al crear System. Security. Claims. ClaimsIdentity. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions. SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx)                                                                                                                                                                                                 |  
| Authentication/SAML2/[Provider]/ValidAudiences              | Lista de direcciones URL de audiencia separadas por comas. [!include[](../../../includes/proc-more-information.md)] [TokenValidationParameters. AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)                                                                                                                                                                                                                                                                          |  
| Authentication/SAML2/[Provider]/ClockSkew                   | El sesgo de reloj que se aplica al validar los tiempos.                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentication/SAML2/[Provider]/RequireExpirationTime       | Valor que indica si los tokens deben tener un valor de expiración.                                                                                                                                                                                                                                                                                                                                                                      |
| Authentication/SAML2/[Provider]/ValidateAudience            | Un valor booleano que controla si la audiencia se validará durante la validación del token.                                                                                                                                                                                                                                                                                                                                                         |

### <a name="idp-initiated-sign-in"></a>Inicio de sesión iniciado por IdP

[!include[](../../../includes/pn-adfs-short.md)] admite el perfil de [Inicio de sesión único (SSO) iniciado por IDP](https://technet.microsoft.com/library/jj127245.aspx) de la [especificación](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline)SAML 2,0. Para que el portal (proveedor de servicios) responda correctamente a la solicitud SAML iniciada por el IdP, el parámetro [RelayState](https://blogs.technet.com/b/askds/archive/2012/09/27/ad-fs-2-0-relaystate.aspx) debe estar codificado correctamente.  

El valor de cadena básico que se va a codificar en el parámetro RelayState de SAML debe tener el formato **ReturnUrl =/Content/sub-Content/** , donde **/Content/sub-Content/** es la ruta de acceso a la página web a la que desea ir en el portal (proveedor de servicios). La ruta de acceso se puede reemplazar por cualquier página web válida en el portal. El valor de cadena se codifica y se coloca en una cadena de contenedor con el formato **RPID =&lt;URL codificada RPID&gt;& RelayState =&lt;&gt;con codificación URL RelayState** . Toda la cadena se codifica de nuevo y se agrega a otro contenedor del formato **<https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=&lt;URL> RPID/&gt;RelayState codificado** .

Por ejemplo, dada la ruta de acceso del proveedor de servicios **/Content/sub-Content/** y el identificador del usuario de confianza **https://portal.contoso.com/** , construya la dirección URL con los pasos siguientes:

Codifique el valor ReturnUrl =/Content/sub-Content/

-   para obtener ReturnUrl% 3D% 2Fcontent% 2Fsub-Content% 2F

<!-- -->

-   Codifique el valor https://portal.contoso.com/

<!-- -->

-   para obtener https %3 A %2 F %2 F portal. contoso. com% 2F

<!-- -->

-   Codifique el valor RPID = https %3 A %2 F %2 F portal. contoso. com% 2F & RelayState = ReturnUrl% 3D% 2Fcontent% 2Fsub-Content% 2F

<!-- -->

-   para obtener RPID %3 D https %2 5 3A %2 5 2F %2 5 2Fportal. contoso. com% 252F% 26RelayState% 3DReturnUrl% 253D% 252Fcontent% 252Fsub-Content% 252F

<!-- -->

-   Anteponga el AD FS ruta de acceso de SSO iniciada por IdP para obtener la dirección URL final

<!-- -->

-   https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F

El siguiente script de [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] se puede usar para construir la dirección URL (guardar en un archivo denominado Get-IdPInitiatedUrl. PS1).

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

## <a name="saml-20-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>Configuración de SAML 2,0 para [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]

La sección anterior que describe [!include[](../../../includes/pn-adfs-short.md)] se puede aplicar también a [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ad](https://msdn.microsoft.com/library/azure/mt168838.aspx), ya que [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ad se comporta como un IDP estándar compatible con [SAML 2,0](https://msdn.microsoft.com/library/azure/dn195591.aspx)&ndash;. Para empezar, inicie sesión en el [portal de administración de[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) y cree o seleccione un directorio existente. Cuando un directorio esté disponible, siga las instrucciones para [Agregar una aplicación](https://msdn.microsoft.com/library/azure/dn132599.aspx) al directorio.  

1.  En el menú**aplicaciones** del directorio, seleccione **Agregar**.
2.  Elija **Agregar una aplicación que mi organización está desarrollando**.
3.  Especifique un nombre personalizado para la aplicación y, a continuación, elija la **aplicación Web de tipo y/o la API Web**.
4.  Para la **dirección URL de inicio de sesión** y el**URI de ID**. de aplicación, especifique la dirección URL del portal para ambos campos https://portal.contoso.com/.
    Esto corresponde al valor de configuración del sitio de **ServiceProviderRealm** (Wtrealm).
5. En este momento, se crea una nueva aplicación. Vaya a la sección **configurar** en el menú.

    En la sección **Inicio de sesión único** , actualice la primera entrada de **dirección URL de respuesta** para incluir una ruta de acceso en la dirección URL https://portal.contoso.com/signin-azure-ad.

    Esto corresponde al valor de configuración del sitio de **AssertionConsumerServiceUrl** (Wreply).

6. En el menú de pie de página, seleccione **Ver extremos** y anote el campo de **documento de metadatos de Federación** .

Esto corresponde al valor de configuración del sitio de **MetadataAddress** .

-   Pegue esta dirección URL en una ventana del explorador para ver el XML de metadatos de Federación y anote el atributo **entityID** del elemento raíz.
-   Esto corresponde al valor de configuración del sitio de**AuthenticationType** .

> [!Note]
> Una configuración de [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] estándar de AD solo usa la configuración siguiente (con valores de ejemplo): Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/MetadataAddress-<https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml> 
> - Autenticación/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AuthenticationType-<https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/>  
> - Utilice el valor del atributo**entityID** en el elemento raíz de los metadatos de Federación (Abra la**dirección URL de MetadataAddress** en un explorador que sea el valor de la configuración del sitio anterior). 
> - Autenticación/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/ServiceProviderRealm-<https://portal.contoso.com/>  
> - Autenticación/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AssertionConsumerServiceUrl-<https://portal.contoso.com/signin-azure-ad>                                                                                   |

## <a name="shibboleth-identity-provider-3"></a>Proveedor de identidades de Shibboleth 3

Use las siguientes directrices para configurar correctamente el [proveedor de identidades de Shibboleth](https://wiki.shibboleth.net/confluence/display/IDP30/Home) como un servicio IDP. A continuación se da por supuesto que el IdP se hospeda en el https://idp.contoso.comde dominio.  

La dirección URL de metadatos de Federación es https://idp.contoso.com/idp/shibboleth

-   El IdP debe estar configurado para generar o servir un identificador persistente. Siga las instrucciones para habilitar la [generación de identificadores persistentes](https://wiki.shibboleth.net/confluence/display/IDP30/NameIDGenerationConfiguration).  

-   Los metadatos de Federación de IdP (&lt;IDPSSODescriptor&gt;) deben configurarse para incluir un [enlace de redirección de SSO](https://shibboleth.net/about/advanced.html). [Ejemplo](https://wiki.shibboleth.net/confluence/display/SHIB2/MetadataExample).  

```
<SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-Redirect"

Location=https://idp.contoso.com/idp/profile/SAML2/Redirect/SSO/>
```

Configure los proveedores de servicios (usuarios de confianza) mediante la configuración de [Metadata-Providers. XML](https://wiki.shibboleth.net/confluence/display/IDP30/MetadataConfiguration).  

-   Cada uno de los metadatos de Federación del proveedor de servicios (&lt;SPSSODescriptor&gt;) debe incluir un enlace posterior al servicio de consumidor de aserciones. Una opción consiste en usar [FilesystemMetadataProvider](https://wiki.shibboleth.net/confluence/display/IDP30/FilesystemMetadataProvider) y hacer referencia a un archivo de configuración que contenga:  

```
<AssertionConsumerService index=1 isDefault=true

Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST"

Location=https://portal.contoso.com/signin-saml2/>
```

El atributo de ubicación corresponde al valor de**AssertionConsumerServiceUrl** (Wreply).

-   Los metadatos de Federación del proveedor de servicios deben especificar un atributo **entityID** para el EntityDescriptor que se corresponda con la configuración de **AuthenticationType** .

**&lt;EntityDescriptor entityID =<https://portal.local.contoso.com/&gt>;...**

> [!Note] 
> Una configuración de Shibboleth estándar solo usa la siguiente configuración (con valores de ejemplo):   
> Authentication/SAML2/Shibboleth/MetadataAddress- https://idp.contoso.com/idp/shibboleth   
> -   Autenticación/SAML2/Shibboleth/AuthenticationType- https://idp.contoso.com/idp/shibboleth 
> -   Utilice el valor del atributo **entityID** en el elemento raíz de los metadatos de Federación (Abra la **dirección URL de MetadataAddress** en un explorador que sea el valor de la configuración del sitio anterior).  
> -   Authentication/SAML2/Shibboleth/ServiceProviderRealm- https://portal.contoso.com/ 
> -   Authentication/SAML2/Shibboleth/AssertionConsumerServiceUrl- https://portal.contoso.com/signin-saml2 

### <a name="idp-initiated-sign-in"></a>Inicio de sesión iniciado por IdP

Shibboleth admite el perfil [SSO Iniciado por IDP](https://wiki.shibboleth.net/confluence/display/SHIB2/IdPUnsolicitedSSO) de la [especificación](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline)SAML 2,0. Para que el portal (proveedor de servicios) responda correctamente a la solicitud SAML iniciada por el IdP, el parámetro RelayState se debe codificar correctamente.  

El valor de cadena básico que se va a codificar en el parámetro RelayState de SAML debe tener el formato **ReturnUrl =/Content/sub-Content/** , donde **/Content/sub-Content/** es la ruta de acceso a la página web a la que desea ir en el portal (proveedor de servicios). La ruta de acceso se puede reemplazar por cualquier página web válida en el portal. La dirección URL de inicio de sesión único iniciada por IdP debe tener el formato <https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=&lt;URL> ID. de proveedor codificado&gt;& destino =&lt;ruta de acceso de devolución codificada URL&gt;.

Por ejemplo, dada la ruta de acceso del proveedor de servicios **/Content/sub-Content/** y el identificador del usuario de confianza **https://portal.contoso.com/** , la dirección URL final se https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=https%3A%2F%2Fportal.contoso.com%2F&target=ReturnUrl%3D%2Fcontent%2Fsub-content%2F

El siguiente script de [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] se puede usar para construir la dirección URL (guardar en un archivo denominado Get-ShibbolethIdPInitiatedUrl. PS1).

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

## <a name="configure-ad-fs-by-using-powershell"></a>Configuración de AD FS mediante PowerShell

El proceso de agregar una relación de confianza para usuario autenticado en [!include[](../../../includes/pn-adfs-short.md)] también puede realizarse mediante la ejecución del siguiente script de [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] en el servidor de [!include[](../../../includes/pn-adfs-short.md)] (guarde el contenido en un archivo denominado Add-AdxPortalRelyingPartyTrustForSaml. PS1). Después de ejecutar el script, continúe con la configuración del sitio del portal.

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
[Establecimiento de la identidad de autenticación para un portal](set-authentication-identity.md)  
[Configuración del proveedor de OAuth2 para portales](configure-oauth2-settings.md)  
[Open ID Connect configuración del proveedor para portales](configure-openid-settings.md)  
[Configuración del proveedor de WS-Federation para portales](configure-ws-federation-settings.md)  
