---
title: Establecer la identidad de autenticación para un portal | MicrosoftDocs
description: Instrucciones para establecer la identidad de autenticación para un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 44b45a019b786da01dc686ecb69f068ce1d7eef8
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542669"
---
# <a name="set-authentication-identity-for-a-portal"></a>Establecimiento de la identidad de autenticación para un portal

Portales proporciona la funcionalidad de autenticación basada en la API de [ASP.net Identity](https://www.asp.net/identity) . A su vez, ASP.NET Identity se basa en el marco [OWIN](https://www.asp.net/aspnet/overview/owin-and-katana) , que también es un componente importante del sistema de autenticación. Los servicios proporcionados incluyen:

- Inicio de sesión de usuario (nombre de usuario/contraseña) local
- Inicio de sesión de usuario externo (proveedor social) a través de proveedores de identidades de terceros
- Autenticación en dos fases con correo electrónico
- Confirmación de la dirección de correo electrónico
- Recuperación de contraseñas
- Registro del código de invitación para registrar los registros de contacto pregenerados

> [!NOTE]
> El campo de **teléfono móvil confirmado** en el formulario de contacto del portal de la entidad Contact actualmente no sirve para ningún propósito. Este campo solo se debe usar al actualizar desde Adxstudio portales.

## <a name="requirements"></a>Requisitos

Los portales requieren:

- Base de portales
- Identidad de [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]
- paquetes de soluciones de [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] de flujos de trabajo de identidad

## <a name="authentication-overview"></a>Introducción a la autenticación

La devolución de visitantes del portal puede autenticarse mediante el uso de credenciales de usuario local o cuentas externas del proveedor de identidades. Un nuevo visitante puede registrarse para una nueva cuenta de usuario, ya sea proporcionando un nombre de usuario y una contraseña o iniciando sesión a través de un proveedor externo. Los visitantes a los que se envía un código de invitación (por el administrador del portal) tienen la opción de canjear el código en el proceso de registro de una nueva cuenta de usuario.

**Configuración del sitio relacionado:**

- `Authentication/Registration/Enabled`
- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/OpenRegistrationEnabled`
- `Authentication/Registration/InvitationEnabled`
- `Authentication/Registration/RememberMeEnabled`
- `Authentication/Registration/ResetPasswordEnabled`

### <a name="sign-in-by-using-a-local-identity-or-external-identity"></a>Inicio de sesión con una identidad local o externa

![Inicio de sesión con una cuenta local](../media/sign-in-local-account.png "Inicio de sesión con una cuenta local")  

### <a name="sign-up-by-using-a-local-identity-or-external-identity"></a>Registrarse con una identidad local o una identidad externa

![Registrarse para una nueva cuenta local](../media/register-new-local-account.png "Registrarse para una nueva cuenta local")  

### <a name="redeem-an-invitation-code-manually"></a>Canjear un código de invitación manualmente

![Registrarse con un código de invitación](../media/sign-up-invitation-code.png "Registrarse con un código de invitación")  

## <a name="forgot-password-or-password-reset"></a>Olvidó la contraseña o el restablecimiento de contraseña 

La devolución de visitantes que requieran un restablecimiento de contraseña (y haya especificado previamente una dirección de correo electrónico en su perfil de usuario) puede solicitar que se envíe un token de restablecimiento de contraseña a su cuenta de correo electrónico. Un token de restablecimiento permite a su propietario elegir una nueva contraseña. Como alternativa, se puede abandonar el token, sin modificar la contraseña original del usuario.

**Configuración del sitio relacionado:**

- `Authentication/Registration/ResetPasswordEnabled`
- `Authentication/Registration/ResetPasswordRequiresConfirmedEmail`

**Proceso relacionado:** Enviar un restablecimiento de contraseña a un contacto

1.  Personalice el correo electrónico en el flujo de trabajo según sea necesario.
2.  Envíe el correo electrónico para invocar el proceso.
3.  Se pedirá al visitante que compruebe el correo electrónico.
4.  El visitante recibe el correo electrónico de restablecimiento de contraseña con instrucciones.
5.  El visitante vuelve al formulario de restablecimiento.
6.  Se completó el restablecimiento de la contraseña.

## <a name="redeem-an-invitation"></a>Canjear una invitación

Canjear un código de invitación permite asociar un visitante de registro a un registro de contacto existente que se preparó de antemano para ese visitante. Normalmente, los códigos de invitación se envían por correo electrónico, pero puede usar un formulario de envío de código general para enviar códigos a través de otros canales. Después de enviar un código de invitación válido, se lleva a cabo el proceso de registro de usuarios (registro) normal para configurar la nueva cuenta de usuario.

**Configuración del sitio relacionado:**

`Authentication/Registration/InvitationEnabled`

**Proceso relacionado:** Enviar invitación

El correo electrónico enviado por este flujo de trabajo se debe personalizar mediante la dirección URL de la página canjear invitación en el portal: código de https://portal.contoso.com/register/?returnurl=%2f&invitation={Invitation (invitación)}

1. Cree una invitación para un nuevo contacto.

    ![Crear una invitación para un nuevo contacto](../media/create-invitation.png "Crear una invitación para un nuevo contacto")  

2. Personalizar y guardar la nueva invitación.

    ![Personalización de una nueva invitación](../media/customize-new-invitation.png "Personalización de una nueva invitación")  

3. Proceso: Enviar invitación
4. Personalice el correo electrónico de invitación.
5. El correo electrónico de invitación abre la página canje.
6. El usuario se registra mediante el código de invitación enviado.

    ![Registro con un código de invitación](../media/sign-up-invitation-code.png "Registrarse con un código de invitación")  

## <a name="manage-user-accounts-through-profile-pages"></a>Administrar cuentas de usuario a través de páginas de perfil

Los usuarios autenticados administran sus cuentas de usuario a través de la barra de navegación **seguridad** de la página de perfil. Los usuarios no se limitan a la cuenta local única o a una cuenta externa única que eligieron en el momento del registro. Los usuarios que tienen una cuenta externa pueden optar por crear una cuenta local aplicando un nombre de usuario y una contraseña. Los usuarios que iniciaron con una cuenta local pueden elegir asociar varias identidades externas a su cuenta. La página de perfil también es donde se recuerda al usuario que confirme su dirección de correo electrónico solicitando que se envíe un correo electrónico de confirmación a su cuenta de correo electrónico.

**Configuración del sitio relacionado:**

- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/TwoFactorEnabled`

## <a name="set-or-change-a-password"></a>Establecer o cambiar una contraseña

Un usuario que tenga una cuenta local existente puede aplicar una nueva contraseña proporcionando la contraseña original. Un usuario que no tiene una cuenta local puede elegir un nombre de usuario y una contraseña para configurar una nueva cuenta local. El nombre de usuario no se puede cambiar una vez establecido.

**Configuración del sitio relacionado:**

`Authentication/Registration/LocalLoginEnabled`

**Proceso relacionado:**
- Cree un nombre de usuario y una contraseña.
- Cambiar una contraseña existente.

## <a name="confirm-an-email-address"></a>Confirmar una dirección de correo electrónico

El cambio de una dirección de correo electrónico (o su configuración por primera vez) lo pone en un estado no confirmado. El usuario puede solicitar que se envíe un correo electrónico de confirmación a su nueva dirección de correo electrónico y el correo electrónico incluirá instrucciones al usuario para completar el proceso de confirmación de correo electrónico.

**Proceso relacionado:** Enviar una confirmación por correo electrónico a un contacto

1. Personalice el correo electrónico en el flujo de trabajo según sea necesario. 
2. El usuario envía un nuevo correo electrónico, que se encuentra en un estado no confirmado.
3. El usuario comprueba la confirmación del correo electrónico.
4. Proceso: enviar una confirmación por correo electrónico al contacto
5. Personalice el correo electrónico de confirmación.
6. El usuario hace clic en el vínculo de confirmación para completar el proceso de confirmación.

> [!NOTE]
> Asegúrese de que se especifica el correo electrónico principal para el contacto porque el correo electrónico de confirmación se envía solo al correo electrónico principal (emailaddress1) del contacto. El correo electrónico de confirmación no se envía al correo electrónico secundario (emailaddress2) ni al correo electrónico alternativo (emailaddress3) del registro de contacto.

## <a name="enable-two-factor-authentication"></a>Habilitar la autenticación en dos fases

La característica de autenticación en dos fases aumenta la seguridad de las cuentas de usuario al requerir la prueba de propiedad de un correo electrónico confirmado además del inicio de sesión de la cuenta local o externa estándar. Un usuario que intenta iniciar sesión en una cuenta que tiene habilitada la autenticación en dos fases se envía un código de seguridad al correo electrónico confirmado asociado a su cuenta. El código de seguridad debe enviarse para completar el proceso de inicio de sesión. Un usuario puede optar por recordar el explorador que ha superado correctamente la comprobación, de modo que el código de seguridad no será necesario para los inicios de sesión posteriores desde el mismo explorador. Cada cuenta de usuario habilita esta característica de forma individual y requiere un correo electrónico confirmado.

> [!WARNING]
> Si crea y habilita la configuración de sitio de **autenticación/registro/MobilePhoneEnabled** para habilitar la funcionalidad heredada, se producirá un error. Esta configuración de sitio no se proporciona de forma preestablecida y no es compatible con los portales.

**Configuración del sitio relacionado:**

- `Authentication/Registration/TwoFactorEnabled`
- `Authentication/Registration/RememberBrowserEnabled`

**Proceso relacionado:** Enviar código de dos factores de correo electrónico a un contacto

1. Habilitar la autenticación en dos fases.
2. Elija recibir el código de seguridad por correo electrónico.
3. Espere el correo electrónico que contiene el código de seguridad.
4. Proceso: envíe un código de dos factores por correo electrónico para ponerse en contacto con.
5. Se puede deshabilitar la autenticación en dos fases.

## <a name="manage-external-accounts"></a>Administrar cuentas externas

Un usuario autenticado puede conectarse (registrar) varias identidades externas a su cuenta de usuario, una de cada proveedor de identidades configurado. Una vez conectadas las identidades, el usuario puede elegir iniciar sesión con cualquiera de las identidades conectadas. Las identidades existentes también se pueden desconectar, siempre y cuando permanezca una única identidad externa o local.

**Configuración del sitio relacionado:**

- `Authentication/Registration/ExternalLoginEnabled`

**Configuración del sitio del proveedor de identidad externo**

1.  Seleccione un proveedor para conectarse a su cuenta de usuario.

    ![Administrar cuentas externas](../media/manage-external-accounts.png "Administrar cuentas externas")  

2.  Inicie sesión con el proveedor que desea conectar.

El proveedor ya está conectado. También se puede desconectar el proveedor.

## <a name="enable-aspnet-identity-authentication"></a>Habilitar la autenticación de identidad de ASP.NET

A continuación se describen los valores para habilitar y deshabilitar diversas características de autenticación y comportamientos:


|                        Nombre de la configuración del sitio                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Descripción                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          Autenticación/registro/LocalLoginEnabled          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     Habilita o deshabilita el inicio de sesión de cuenta local en función de un nombre de usuario (o correo electrónico) y una contraseña. Valor predeterminado: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|          Autenticación/registro/LocalLoginByEmail          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               Habilita o deshabilita el inicio de sesión de la cuenta local mediante un campo de dirección de correo electrónico en lugar de un campo de nombre de usuario. Valor predeterminado: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|        Autenticación/registro/ExternalLoginEnabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Habilita o deshabilita el registro y el inicio de sesión de la cuenta externa. Valor predeterminado: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|          Autenticación/registro/RememberMeEnabled          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          ¿Activa o desactiva un recordatorio? en la casilla del inicio de sesión local para permitir que las sesiones autenticadas se conserven incluso cuando se cierre el explorador Web. Valor predeterminado: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|          Autenticación/registro/TwoFactorEnabled           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Habilita o deshabilita la opción para que los usuarios habiliten la autenticación en dos fases. Los usuarios con una dirección de correo electrónico confirmada pueden optar por la seguridad agregada de la autenticación en dos fases. Valor predeterminado: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|       Autenticación/registro/RememberBrowserEnabled        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                ¿Selecciona o borra un explorador recordar? casilla en la validación de segundo factor (código de correo electrónico) para conservar la validación de segundo factor para el explorador actual. No será necesario que el usuario pase la validación del segundo factor para los inicios de sesión posteriores, siempre que se use el mismo explorador. Valor predeterminado: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|        Autenticación/registro/ResetPasswordEnabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         Habilita o deshabilita la característica de restablecimiento de contraseña. Valor predeterminado: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Autenticación/registro/ResetPasswordRequiresConfirmedEmail |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               Habilita o deshabilita el restablecimiento de contraseña solo para direcciones de correo electrónico confirmadas. Si está habilitada, las direcciones de correo electrónico no confirmadas no se pueden usar para enviar instrucciones de restablecimiento de contraseña. Valor predeterminado: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|   Autenticación/registro/TriggerLockoutOnFailedPassword    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          Habilita o deshabilita el registro de intentos de contraseña erróneos. Si está deshabilitada, las cuentas de usuario no se bloquearán. Valor predeterminado: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|             Autenticación/registro/IsDemoMode              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                          Habilita o deshabilita una marca de modo de demostración para usar solo en entornos de desarrollo o demostración. No habilite esta configuración en entornos de producción. El modo de demostración también requiere que el explorador Web se ejecute localmente en el servidor de aplicaciones Web. Cuando se habilita el modo de demostración, se muestra al usuario el código de restablecimiento de contraseña y el código de segundo factor para obtener un acceso rápido. Valor predeterminado: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|    Autenticación/registro/LoginButtonAuthenticationType    | Si un portal solo requiere un único proveedor de identidades externo (para controlar toda la autenticación), esto permite que el botón de **Inicio de sesión** de la barra de navegación del encabezado se vincule directamente a la página de inicio de sesión de ese proveedor de identidad externo (en su lugar, se vincula al Página de selección de proveedor de identidad y formulario de inicio de sesión local). Solo se puede seleccionar un proveedor de identidades para esta acción. Especifique el valor de [AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx) del proveedor.<br>Para una configuración de inicio de sesión único con OpenIdConnect, como el uso de Azure Active Directory B2C, el usuario debe proporcionar la autoridad.<br>En el caso de los proveedores basados en OAuth2, los valores aceptados son: `Facebook, Google, Yahoo, [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)], LinkedIn, Yammer,` o `Twitter`<br>Para los proveedores basados en WS-Federation, utilice el valor especificado para la configuración del sitio de `Authentication/WsFederation/ADFS/AuthenticationType` y `Authentication/WsFederation/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]/\[provider\]/AuthenticationType`. Ejemplos: https://adfs.contoso.com/adfs/services/trust , Facebook-0123456789, Google, Yahoo!, Uri:[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] LiveID. |
|                                                                 |                                                                                                                                                                                                                                                                                                  |

## <a name="enable-or-disable-user-registration"></a>Habilitar o deshabilitar el registro de usuario

A continuación se describen los valores para habilitar y deshabilitar las opciones de registro de usuario (suscripción):

| Nombre de la configuración del sitio                                   | Descripción                                                                                                                                                                             |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autenticación/registro/habilitado                 | Habilita o deshabilita todos los formularios de registro de usuario. El registro debe estar habilitado para que los demás valores de esta sección surtan efecto. Valor predeterminado: true                                   |
| Autenticación/registro/OpenRegistrationEnabled | Habilita o deshabilita el formulario de registro de inicio de sesión para crear nuevos usuarios locales. El formulario de registro permite a cualquier visitante anónimo en el portal crear una nueva cuenta de usuario. Valor predeterminado: true |
| Autenticación/registro/InvitationEnabled       | Habilita o deshabilita el formulario de canje de código de invitación para registrar a los usuarios que poseen códigos de invitación. Valor predeterminado: true                                                               |
|Autenticación/registro/CaptchaEnabled|Habilita o deshabilita CAPTCHA en la página de registro del usuario. Valor predeterminado: false<br>**Nota**: es posible que esta configuración de sitio no esté disponible de forma predeterminada. Para habilitar CAPTCHA, debe crear la configuración del sitio y establecer su valor en true. |
||

> [!NOTE]
> Asegúrese de que se especifica el correo electrónico principal para el usuario, ya que el registro se realiza mediante el correo electrónico principal (emailaddress1) del usuario. El usuario no se puede registrar mediante el correo electrónico secundario (emailaddress2) o el correo electrónico alternativo (emailaddress3) del registro de contacto.

## <a name="user-credential-validation"></a>Validación de credenciales de usuario

A continuación se describe la configuración para ajustar los parámetros de validación de nombre de usuario y contraseña. La validación se produce cuando los usuarios se suscriben a una nueva cuenta local o cambian una contraseña.

| Nombre de la configuración del sitio                                                       | Descripción                                                                                                                                                                                         |
|-------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/UserManager/PasswordValidator/EnforcePasswordPolicy      | Si la contraseña contiene caracteres de tres de las siguientes categorías:<br><ul><li>Letras mayúsculas de idiomas europeos (de la a a la Z, con marcas diacríticas, caracteres griegos y cirílico)</li><li>Letras minúsculas de los idiomas europeos (de la a a la z, nitidez-s, con marcas diacríticas, caracteres griegos y cirílico)</li><li>Dígitos de base 10 (de 0 a 9)</li><li>Caracteres no alfanuméricos (caracteres especiales) (por ejemplo,!, $, \#,%)</li></ul>Valor predeterminado: true. Para obtener más información: [Directiva de contraseñas](https://technet.microsoft.com/library/hh994562(v=ws.10).aspx).                                                                                                           |  
| Authentication/UserManager/UserValidator/AllowOnlyAlphanumericUserNames | Indica si se permiten solo caracteres alfanuméricos para el nombre de usuario. Valor predeterminado: false. Para obtener más información: [UserValidator < TUser, TKey >. AllowOnlyAlphanumericUserNames](https://msdn.microsoft.com/library/dn613211.aspx).                                                          |  
| Authentication/UserManager/UserValidator/RequireUniqueEmail             | Indica si se necesita una dirección de correo electrónico única para validar al usuario. Valor predeterminado: true. Para obtener más información: [UserValidator < TUser, TKey >. RequireUniqueEmail](https://msdn.microsoft.com/library/dn613213.aspx).                                                                   |  
| Authentication/UserManager/PasswordValidator/RequiredLength             | La longitud mínima de contraseña necesaria. Valor predeterminado: 8. Para obtener más información: [PasswordValidator. RequiredLength](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredlength.aspx).                                       |  
| Authentication/UserManager/PasswordValidator/RequireNonLetterOrDigit    | Si la contraseña requiere un carácter que no sea una letra o un dígito. Valor predeterminado: false. Para obtener más información: [PasswordValidator. RequireNonLetterOrDigit](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirenonletterordigit.aspx). |  
| Authentication/UserManager/PasswordValidator/RequireDigit               | Si la contraseña requiere un dígito numérico (de 0 a 9). Valor predeterminado: false. Para obtener más información: [PasswordValidator. RequireDigit](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredigit.aspx).                |  
| Authentication/UserManager/PasswordValidator/RequireLowercase           | Si la contraseña requiere una letra minúscula (de la a a la z). Valor predeterminado: false. Para obtener más información: [PasswordValidator. RequireLowercase](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirelowercase.aspx).        |  
| Authentication/UserManager/PasswordValidator/RequireUppercase           | Si la contraseña requiere una letra mayúscula (de la a a la Z). Valor predeterminado: false. Para obtener más información: [PasswordValidator. RequireUppercase](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requireuppercase.aspx).       | 
|| 

## <a name="user-account-lockout-settings"></a>Configuración de bloqueo de cuenta de usuario

A continuación se describen las opciones de configuración que definen cómo y cuándo se bloquea la autenticación de una cuenta. Cuando se detecta un número determinado de intentos de contraseña erróneos en un breve período de tiempo, la cuenta de usuario se bloquea durante un período de tiempo. El uso puede intentarlo de nuevo una vez transcurrido el período de bloqueo.

| Nombre de la configuración del sitio                                               | Descripción                                                                                                                                                                                                                                     |
|-----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autenticación/UserManager/UserLockoutEnabledByDefault          | Indica si el bloqueo de usuario está habilitado cuando se crean los usuarios. Valor predeterminado: true. Para obtener más información: [UserManager < TUser, TKey >. UserLockoutEnabledByDefault](https://msdn.microsoft.com/library/dn613214.aspx).                                                                                                  |  
| Autenticación/UserManager/DefaultAccountLockoutTimeSpan        | La cantidad de tiempo predeterminada que un usuario está bloqueado para después de que se alcance la autenticación/UserManager/MaxFailedAccessAttemptsBeforeLockout. Valor predeterminado: 24:00:00 (1 día). Para obtener más información: [UserManager < TUser, TKey >. DefaultAccountLockoutTimeSpan](https://msdn.microsoft.com/library/dn613201.aspx).                 |  
| Autenticación/UserManager/MaxFailedAccessAttemptsBeforeLockout | Número máximo de intentos de acceso permitidos antes de que un usuario esté bloqueado (si está habilitado el bloqueo). Valor predeterminado: 5. Para obtener más información: [UserManager < TUser, TKey >. MaxFailedAccessAttemptsBeforeLockout](https://msdn.microsoft.com/library/dn613202.aspx).                                                                        |  
| Autenticación/ApplicationCookie/ExpireTimeSpan                 | La cantidad de tiempo predeterminada que las sesiones de autenticación de cookies son válidas para. Valor predeterminado: 24:00:00 (1 día). Para obtener más información: [CookieAuthenticationOptions. ExpireTimeSpan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx). |
||  

## <a name="cookie-authentication-site-settings"></a>Configuración del sitio de autenticación de cookies

Configuración para modificar el comportamiento predeterminado de la cookie de autenticación. Definido por la clase [CookieAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.aspx) .

| Nombre de la configuración del sitio   | Descripción       |
|----------------------|------------------------------------------------|
| Autenticación/ApplicationCookie/AuthenticationType                      | El tipo de la cookie de autenticación de la aplicación. Valor predeterminado: ApplicationCookie. Para obtener más información: [AuthenticationOptions:: AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx).  |
| Autenticación/ApplicationCookie/CookieName predeterminado                              | Determina el nombre de la cookie que se usa para conservar la identidad. Valor predeterminado:. AspNet. cookies. Para obtener más información: [CookieAuthenticationOptions:: CookieName predeterminado](https://msdn.microsoft.com/library/dn385537.aspx).  |
| Autenticación/ApplicationCookie/CookieDomain                            | Determina el dominio que se usa para crear la cookie. Para obtener más información: [CookieAuthenticationOptions:: CookieDomain](https://msdn.microsoft.com/library/dn385536.aspx).  |
| Authentication/ApplicationCookie/CookiePath                              | Determina la ruta de acceso utilizada para crear la cookie. Valor predeterminado:/. Para obtener más información: [CookieAuthenticationOptions:: cookiePath](https://msdn.microsoft.com/library/dn385539.aspx). |
| Autenticación/ApplicationCookie/CookieHttpOnly                          | Determina si el explorador debe permitir el acceso de JavaScript del lado cliente a la cookie. Valor predeterminado: true. Para obtener más información: [CookieAuthenticationOptions:: CookieHttpOnly](https://msdn.microsoft.com/library/dn385540.aspx).                     |
| Autenticación/ApplicationCookie/CookieSecure                            | Determina si la cookie solo se debe transmitir en la solicitud HTTPS. Valor predeterminado: SameAsRequest. Para obtener más información: [CookieAuthenticationOptions:: CookieSecure](https://msdn.microsoft.com/library/dn385538.aspx).  |
| Autenticación/ApplicationCookie/ExpireTimeSpan                          | Controla la cantidad de tiempo que la cookie de aplicación seguirá siendo válida desde el punto en que se crea. Valor predeterminado: 14 días. Para obtener más información: [CookieAuthenticationOptions:: ExpireTimeSpan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx).  |
| Autenticación/ApplicationCookie/SlidingExpiration                       | La configuración de SlidingExpiration está establecida en true para indicar al middleware que vuelva a emitir una cookie nueva con una nueva hora de expiración cada vez que procese una solicitud que sea superior a la mitad de la ventana de expiración. Valor predeterminado: true. Para obtener más información: [CookieAuthenticationOptions:: slidingExpiration](https://msdn.microsoft.com/library/dn385548.aspx). |
| Autenticación/ApplicationCookie/LoginPath                               | La propiedad LoginPath informa al middleware de que debe cambiar un código de estado no autorizado 401 saliente a una redirección de 302 a la ruta de acceso de inicio de sesión determinada. Valor predeterminado: ~/signin. Para obtener más información: [CookieAuthenticationOptions:: LoginPath](https://msdn.microsoft.com/library/dn385541.aspx).                                            |
| Autenticación/ApplicationCookie/LogoutPath                              | Si se proporciona a LogoutPath el middleware, una solicitud a esa ruta de acceso se redirigirá en función de ReturnUrlParameter. Para obtener más información: [CookieAuthenticationOptions:: LogoutPath](https://msdn.microsoft.com/library/dn385545.aspx).               |
| Autenticación/ApplicationCookie/ReturnUrlParameter                      | ReturnUrlParameter determina el nombre del parámetro de cadena de consulta que el middleware anexa cuando se cambia un código de estado no autorizado 401 a una redirección de 302 a la ruta de acceso de inicio de sesión. Para obtener más información: [CookieAuthenticationOptions:: ReturnUrlParameter](https://msdn.microsoft.com/library/dn385546.aspx).                           |
| Authentication/ApplicationCookie/SecurityStampValidator/ValidateInterval | Período de tiempo entre las validaciones de marcas de seguridad. Valor predeterminado: 30 minutos. Para obtener más información: [SecurityStampValidator:: OnValidateIdentity](https://msdn.microsoft.com/library/microsoft.aspnet.identity.owin.securitystampvalidator.onvalidateidentity.aspx).                    |
| Autenticación/TwoFactorCookie/AuthenticationType                        | Tipo de la cookie de autenticación en dos fases. Valor predeterminado: TwoFactorCookie. Para obtener más información: [AuthenticationOptions:: AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx).            |
| Autenticación/TwoFactorCookie/ExpireTimeSpan                            | Controla la cantidad de tiempo que la cookie de dos factores seguirá siendo válida desde el punto en que se crea. Valor predeterminado: 5 minutos. Para obtener más información: [CookieAuthenticationOptions:: ExpireTimeSpan](https://msdn.microsoft.com/library/dn385543.aspx).     |
|||

### <a name="see-also"></a>Vea también

[Configurar la autenticación del portal](configure-portal-authentication.md)  
[Configuración del proveedor de OAuth2 para portales](configure-oauth2-settings.md)  
[Open ID Connect configuración del proveedor para portales](configure-openid-settings.md)  
[Configuración del proveedor de WS-Federation para portales](configure-ws-federation-settings.md)  
[Configuración del proveedor de SAML 2,0 para portales](configure-saml2-settings.md)  
