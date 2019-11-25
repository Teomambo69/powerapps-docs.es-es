---
title: Establecer identidad de autenticación para un portal | MicrosoftDocs
description: Instrucciones para establecer la identidad de autenticación de un portal.
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756452"
---
# <a name="set-authentication-identity-for-a-portal"></a>Establecer identidad de autenticación para un portal

Los portales proporcionan funcionalidad de autenticación basada en la API de [Identidad ASP.NET](https://www.asp.net/identity). La identidad ASP.NET a su vez se basa en el marco [OWIN](https://www.asp.net/aspnet/overview/owin-and-katana) que también es un componente importante del sistema de autenticación. Los servicios proporcionados incluyen:

- Inicio de sesión de usuario local (nombre de usuario y contraseña)
- Inicio de sesión de usuario externo (proveedor social) a través de proveedores de identidad terceros
- Autenticación bifactorial con correo electrónico
- Confirmación de dirección de correo electrónico
- Recuperación de contraseña
- Registro de código de invitación para registrar registros de contacto pregenerados

> [!NOTE]
> El campo **Teléfono móvil confirmado** en el formulario Contacto del portal de la entidad Contacto actualmente no responde a ningún propósito. Este campo debe utilizarse solo al actualizar desde Adxstudio Portals.

## <a name="requirements"></a>Requisitos

Los portales requieren:

- Portales base
- Identidad de [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]
- Paquetes de la solución Flujos de trabajo de identidad de [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]

## <a name="authentication-overview"></a>Información general sobre autenticación

Los visitantes del portal que repiten tienen la opción de autenticarse mediante las credenciales de usuario local o las cuentas de un proveedor de identidad externo. Un nuevo visitante puede registrarse para una cuenta de usuario proporcionando un nombre de usuario y la contraseña o iniciando sesión mediante un proveedor externo. Los visitantes que reciben un código de invitación (enviado por el administrador de portal) tienen la opción de canjear el código en el proceso de suscribirse a una nueva cuenta de usuario.

**Valores relacionados de la ubicación:**

- `Authentication/Registration/Enabled`
- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/OpenRegistrationEnabled`
- `Authentication/Registration/InvitationEnabled`
- `Authentication/Registration/RememberMeEnabled`
- `Authentication/Registration/ResetPasswordEnabled`

### <a name="sign-in-by-using-a-local-identity-or-external-identity"></a>Iniciar sesión con una identidad local o una identidad externa

![Inicie sesión mediante cuenta local](../media/sign-in-local-account.png "Inicie sesión mediante cuenta local")  

### <a name="sign-up-by-using-a-local-identity-or-external-identity"></a>Suscripción con una identidad local o una identidad externa

![Registrarse para una nueva cuenta local](../media/register-new-local-account.png "Registrarse para una nueva cuenta local")  

### <a name="redeem-an-invitation-code-manually"></a>Canjee un código de invitación manualmente

![Registrarse con un código de invitación](../media/sign-up-invitation-code.png "Registrarse con un código de invitación")  

## <a name="forgot-password-or-password-reset"></a>Olvidó contraseña o reinicio de contraseña 

Los visitantes que repiten y que necesitan restablecer la contraseña (y que hayan especificado previamente una dirección de correo electrónico en su perfil de usuario) tienen la opción de solicitar el envío de un token de restablecimiento de contraseña a su cuenta de correo electrónico. Un token de restablecimiento permite que el propietario elija una nueva contraseña. Como alternativa, el token se puede abandonar dejando a los usuarios su contraseña original sin modificar.

**Valores relacionados de la ubicación:**

- `Authentication/Registration/ResetPasswordEnabled`
- `Authentication/Registration/ResetPasswordRequiresConfirmedEmail`

**Proceso relacionado:** Enviar restablecimiento de contraseña al contacto

1.  Personalizar el correo electrónico en el flujo de trabajo según sea necesario.
2.  Enviar un correo electrónico para llamar al proceso.
3.  Solicitar al visitante que compruebe el correo electrónico.
4.  El visitante recibe el correo electrónico de restablecimiento de contraseña con instrucciones.
5.  El visitante vuelve al formulario de restablecimiento.
6.  El restablecimiento de contraseña se ha completado..

## <a name="redeem-an-invitation"></a>Canjear una invitación

Canjear un código de invitación permite a un visitante que se registra asociarse a un registro de contacto existente que se preparó de antemano específicamente para ese visitante. Normalmente, los códigos de invitación son enviados por correo electrónico, pero puede usar un formulario de envío de código general para enviar los códigos a través de otros canales. Después de que se envíe un código de invitación válido, el proceso de registro de usuario normal (suscripción) se realiza para configurar la nueva cuenta de usuario.

**Valores relacionados de la ubicación:**

`Authentication/Registration/InvitationEnabled`

**Proceso relacionado:** Enviar invitación

El correo electrónico enviado por este flujo de trabajo se debe personalizar con la dirección URL a la página de invitación de canjeo en el portal: https://portal.contoso.com/register/?returnurl=%2f&invitation={Invitation Code(Invitation)}

1. Cree una invitación para un nuevo contacto.

    ![Cree una invitación para un nuevo contacto](../media/create-invitation.png "Cree una invitación para un nuevo contacto")  

2. Personalice y guarde la nueva invitación.

    ![Personalización de una nueva invitación](../media/customize-new-invitation.png "Personalización de una nueva invitación")  

3. Proceso: Enviar invitación
4. Personalice el correo electrónico de invitación.
5. El correo electrónico de invitación abre la página de canje.
6. El usuario se suscribe con el código de invitación enviado.

    ![Registrarse con un código de invitación](../media/sign-up-invitation-code.png "Registrarse con un código de invitación")  

## <a name="manage-user-accounts-through-profile-pages"></a>Administrar cuentas de usuario a través de páginas del perfil

Los usuarios autenticados administran sus cuentas de usuario a través de la barra de navegación **Seguridad** de la página del perfil. Los usuarios no está limitados a la cuenta local individual o a una sola cuenta externa elegida en el tiempo del registro del usuario. Los usuarios con una cuenta externa pueden crear una cuenta local aplicando un nombre de usuario y una contraseña. Los usuarios que comenzaron con una cuenta local pueden asociar múltiples identidades externas a su cuenta. La página del perfil también es donde se recuerda al usuario que confirme su dirección de correo electrónico solicitando el envío de un correo de confirmación a su cuenta de correo electrónico.

**Valores relacionados de la ubicación:**

- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/TwoFactorEnabled`

## <a name="set-or-change-a-password"></a>Establecer o cambiar una contraseña

Un usuario con una cuenta local existente puede aplicar una nueva contraseña suministrando la contraseña original. Un usuario sin una cuenta local puede elegir un nombre de usuario y una contraseña para configurar una nueva cuenta local. El nombre de usuario no se puede cambiar después de establecer.

**Valores relacionados de la ubicación:**

`Authentication/Registration/LocalLoginEnabled`

**Proceso relacionado:**
- Crear un nombre de usuario y una contraseña.
- Cambiar una contraseña existente.

## <a name="confirm-an-email-address"></a>Confirmar una dirección de correo electrónico

Cambiar una dirección de correo electrónico (o establecerla por primera vez) la coloca en estado sin confirmar. El usuario puede solicitar el envío de un correo electrónico de confirmación a la nueva dirección de correo electrónico; en el mensaje se incluyen instrucciones para completar el proceso de confirmación de correo electrónico.

**Proceso relacionado:** enviar una confirmación de correo electrónico a un contacto

1. Personalizar el correo electrónico en el flujo de trabajo según sea necesario. 
2. El usuario envía un nuevo correo electrónico, que se encuentra en un estado sin confirmar.
3. El usuario comprueba el correo electrónico para confirmación.
4. Proceso: Enviar confirmación de correo electrónico a contacto
5. Personalice el correo electrónico de confirmación.
6. El usuario hace clic en el vínculo de confirmación para completar el proceso de confirmación.

> [!NOTE]
> Asegúrese de que se ha especificado el correo electrónico principal del contacto porque el mensaje de confirmación se envía solo para el correo electrónico principal (emailaddress1) del contacto. La confirmación del correo electrónico no se enviará al correo electrónico secundario (emailaddress2) o correo electrónico alternativo (emailaddress3) del registro de contacto.

## <a name="enable-two-factor-authentication"></a>Habilitar autenticación bifactorial

La característica de autenticación en dos fases incrementa la seguridad de la cuenta de usuario solicitando prueba de propiedad de un correo electrónico confirmado además del inicio de sesión en la cuenta local o externa estándar. Un usuario que intenta iniciar sesión en una cuenta con autenticación bifactorial activada recibe un código de seguridad en el correo electrónico confirmado asociados a su cuenta. El código de seguridad se debe enviar para completar el proceso de inicio de sesión. Un usuario puede optar por recordar el explorador que ha pasado correctamente la verificación de modo que el código de seguridad no será necesario para inicios de sesión posteriores desde el mismo explorador. Cada cuenta de usuario habilita esta característica individualmente y requiere un correo electrónico confirmado.

> [!WARNING]
> Si crea y permite la configuración del sitio **Authentication/Registration/MobilePhoneEnabled** para habilitar la funcionalidad antigua, se producirá un error. Este valor de sitio no se proporciona de manera predefinida y no lo admiten los portales.

**Valores relacionados de la ubicación:**

- `Authentication/Registration/TwoFactorEnabled`
- `Authentication/Registration/RememberBrowserEnabled`

**Proceso relacionado:** enviar un correo electrónico con el código de dos fases a un contacto

1. Habilitar autenticación bifactorial.
2. Elija la opción para recibir el código de seguridad por correo electrónico.
3. Espere al correo electrónico que contiene el código de seguridad.
4. Proceso: Enviar código bifactorial de correo electrónico al contacto.
5. La autenticación bifactorial puede deshabilitarse.

## <a name="manage-external-accounts"></a>Administrar cuentas externas

Un usuario autenticado puede conectar (registrar) varias identidades externas a su cuenta de usuario, uno de cada uno de los proveedores de identidad configurados. Después de conectar las identidades, el usuario puede optar por iniciar sesión con cualquiera de las identidades conectadas. Las identidades existentes también se pueden desconectar mientras se mantenga una sola identidad externa o local.

**Valores relacionados de la ubicación:**

- `Authentication/Registration/ExternalLoginEnabled`

**Configuración del sitio del proveedor de identidad externo**

1.  Seleccione un proveedor para conectarse a su cuenta de usuario.

    ![Administrar cuentas externas](../media/manage-external-accounts.png "Administrar cuentas externas")  

2.  Inicie sesión con el proveedor que quiera usar para conectarse.

El proveedor está conectado. Igualmente, el proveedor puede desconectarse.

## <a name="enable-aspnet-identity-authentication"></a>Habilitar autenticación de identidad de ASP.NET

La siguiente información describe la configuración para habilitar y deshabilitar las diferentes características y comportamientos de autenticación:


|                        Nombre de configuración del sitio                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Descripción                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          Authentication/Registration/LocalLoginEnabled          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     Habilita o deshabilita el inicio de sesión de cuenta local basado en nombre del usuario (o correo electrónico) y contraseña. Valor predeterminado: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|          Authentication/Registration/LocalLoginByEmail          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               Habilita o deshabilita el inicio de sesión de cuenta local usando un campo de dirección de correo electrónico en lugar de un campo de nombre de usuario. Valor predeterminado: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|        Authentication/Registration/ExternalLoginEnabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Habilita o deshabilita el inicio de sesión y el registro de la cuenta externa. Valor predeterminado: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|          Authentication/Registration/RememberMeEnabled          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          Selecciona o desactiva la casilla ¿Recordarme? en el inicio de sesión local para permitir que las sesiones autenticadas persistan incluso al cerrarse el explorador web. Valor predeterminado: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|          Authentication/Registration/TwoFactorEnabled           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Habilita o deshabilita la opción para que los usuarios habiliten autenticación bifactorial. Los usuarios que tienen una dirección de correo electrónico confirmada pueden suscribirse a la seguridad adicional de la autenticación bifactorial. Valor predeterminado: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|       Authentication/Registration/RememberBrowserEnabled        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                Selecciona o desactiva una casilla ¿Recordarme? en la validación bifactorial (código de correo electrónico) para persistir la validación bifactorial del explorador actual. No se requerirá al usuario que pase la validación bifactorial para posteriores inicios de sesión mientras utilice el mismo explorador. Valor predeterminado: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|        Authentication/Registration/ResetPasswordEnabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         Habilita o deshabilita la característica de reinicio de contraseña. Valor predeterminado: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentication/Registration/ResetPasswordRequiresConfirmedEmail |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               Habilita o deshabilita el reinicio de la contraseña de las direcciones de correo electrónico confirmadas solo. Si están habilitada, las direcciones de correo electrónico sin confirmar no se pueden usar para enviar instrucciones de reinicio de contraseña. Valor predeterminado: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|   Authentication/Registration/TriggerLockoutOnFailedPassword    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          Habilita o deshabilita el registro de intentos de contraseña con error. Si está habilitada, las cuentas de usuario no serán bloqueadas. Valor predeterminado: "true".                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|             Authentication/Registration/IsDemoMode              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                          Habilita o deshabilita un indicador de modo de demostración que se usará solo en entornos de desarrollo o demostración. No habilite este valor en entornos de producción. El modo de demostración también requiere que el explorador web se ejecute localmente en el servidor de aplicaciones web. Cuando se habilita el modo de demostración, el código de reinicio de contraseña y el código bifactorial se muestran al usuario para el acceso rápido. Valor predeterminado: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|    Authentication/Registration/LoginButtonAuthenticationType    | Si un portal solo requiere un proveedor de identidad externo (para administrar toda la autenticación), esto permite al botón **Iniciar sesión** de la barra de navegación del encabezado vincularse directamente con la página de inicio de sesión de dicho proveedor de identidad externo (en lugar de vincularse al formulario de inicio de sesión local intermedio y la página de selección del proveedor de identidad). Sólo se puede seleccionar un único proveedor de identidad para esta acción. Especifique el valor de [AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx) del proveedor.<br>Para un perfil de configuración de inicio de sesión único mediante OpenIdConnect, como el uso de Azure Active Directory B2C, el usuario debe proporcionar la autoridad.<br>Para proveedores basados en OAuth2 los valores aceptados son: `Facebook, Google, Yahoo, [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)], LinkedIn, Yammer,` o `Twitter`<br>Para proveedores basados en WS-Federation, use el valor especificado para la configuración del sitio `Authentication/WsFederation/ADFS/AuthenticationType` y `Authentication/WsFederation/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]/\[provider\]/AuthenticationType`. Ejemplos: https://adfs.contoso.com/adfs/services/trust Facebook-0123456789, Google, Yahoo!, uri:[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)]LiveID. |
|                                                                 |                                                                                                                                                                                                                                                                                                  |

## <a name="enable-or-disable-user-registration"></a>Habilitar o deshabilitar registros de usuario

La siguiente información describe la configuración para habilitar y deshabilitar las opciones de registro de usuario (suscripción):

| Nombre de configuración del sitio                                   | Descripción                                                                                                                                                                             |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/Enabled                 | Habilita o deshabilita todos los formularios de registro de usuario. El registro debe estar habilitada para que los otros valores en esta sección surtan efecto. Valor predeterminado: true                                   |
| Authentication/Registration/OpenRegistrationEnabled | Habilita o deshabilita el formulario de registro de suscripción para crear nuevos usuarios locales. El formulario de suscripción permite que cualquier visitante anónimo al portal cree una cuenta de usuario nueva. Valor predeterminado: true |
| Authentication/Registration/InvitationEnabled       | Habilita o deshabilita el formulario de canje del código de invitación para registrar usuarios que posean códigos de invitación. Valor predeterminado: true                                                               |
|Authentication/Registration/CaptchaEnabled|Habilita o deshabilita captcha en la página de registro de usuarios. Valor predeterminado: false<br>**Nota**: esta configuración de sitio puede no estar disponible de forma predeterminada. Para habilitar captcha, debe crear la configuración del sitio y establecer su valor en verdadero. |
||

> [!NOTE]
> Asegúrese de que el correo electrónico principal está especificado para el usuario porque el registro se realiza usando el correo electrónico principal (emailaddress1) del usuario. El usuario no se puede registrar usando el correo electrónico secundario (emailaddress2) o correo electrónico alternativo (emailaddress3) del registro de contacto.

## <a name="user-credential-validation"></a>Validación de credenciales de usuario

La siguiente información describa la configuración para para ajustar parámetros de validación de nombre de usuario y contraseña. La validación se produce cuando el usuario se suscribe a una nueva cuenta local o modifica una contraseña.

| Nombre de configuración del sitio                                                       | Descripción                                                                                                                                                                                         |
|-------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/UserManager/PasswordValidator/EnforcePasswordPolicy      | Si la contraseña contiene caracteres de tres de las siguientes categorías:<br><ul><li>Letras mayúsculas de los idiomas europeos (A a z, con marca diacríticas, caracteres griegos y cirílicos)</li><li>Letras minúsculas de los idiomas europeos (A a z, s cerrada, con marca diacríticas, caracteres griegos y cirílicos)</li><li>Dígitos de Base 10 (de 0 a 9)</li><li>Caracteres no alfanuméricos (caracteres especiales) (por ejemplo, !, $, \#, %)</li></ul>Valor predeterminado: true. Consulte [Directiva de contraseñas](https://technet.microsoft.com/library/hh994562(v=ws.10).aspx) para obtener más información.                                                                                                           |  
| Authentication/UserManager/UserValidator/AllowOnlyAlphanumericUserNames | Si permite solo caracteres alfanuméricos para el nombre de usuario. Valor predeterminado: false. Para obtener más información consulte [UserValidator<TUser, TKey>.AllowOnlyAlphanumericUserNames](https://msdn.microsoft.com/library/dn613211.aspx).                                                          |  
| Authentication/UserManager/UserValidator/RequireUniqueEmail             | Si se necesita correo electrónico único para validar el usuario. Valor predeterminado: true. Para obtener más información consulte [UserValidator<TUser, TKey>.RequireUniqueEmail](https://msdn.microsoft.com/library/dn613213.aspx).                                                                   |  
| Authentication/UserManager/PasswordValidator/RequiredLength             | La longitud de contraseña mínima requerida. Opción predeterminada: 8. Para obtener más información consulte [PasswordValidator.RequiredLength](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredlength.aspx).                                       |  
| Authentication/UserManager/PasswordValidator/RequireNonLetterOrDigit    | Si la contraseña requiere un carácter que no sea letra o dígito. Valor predeterminado: false. Para obtener más información consulte [PasswordValidator.RequireNonLetterOrDigit](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirenonletterordigit.aspx). |  
| Authentication/UserManager/PasswordValidator/RequireDigit               | Si la contraseña requiere un dígito numérico ( de 0 a 9). Valor predeterminado: false. Para obtener más información consulte [PasswordValidator.RequireDigit](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredigit.aspx).                |  
| Authentication/UserManager/PasswordValidator/RequireLowercase           | Si la contraseña requiere una letra minúscula ( de la "a", a la "z"). Valor predeterminado: false. Para obtener más información consulte [PasswordValidator.RequireLowercase](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirelowercase.aspx).        |  
| Authentication/UserManager/PasswordValidator/RequireUppercase           | Si la contraseña requiere una letra mayúscula ( de la "a", a la "z"). Valor predeterminado: false. Para obtener más información consulte [PasswordValidator.RequireUppercase](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requireuppercase.aspx).       | 
|| 

## <a name="user-account-lockout-settings"></a>Configuración de bloqueo de cuenta del usuario

La siguiente información describe la configuración que define cuándo y cómo una cuenta pasa a estar bloqueada para autenticación. Cuando se detecta un determinado número de intentos de contraseña fallidos en un período de tiempo corto, la cuenta de usuario se bloquea por un período de tiempo. El usuario puede intentar de nuevo cuando transcurra el período de bloqueo.

| Nombre de configuración del sitio                                               | Descripción                                                                                                                                                                                                                                     |
|-----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/UserManager/UserLockoutEnabledByDefault          | Indica si el bloqueo del usuario está activado cuando se crean usuarios. Valor predeterminado: true. Para obtener más información consulte [UserManager<TUser, TKey>.UserLockoutEnabledByDefault](https://msdn.microsoft.com/library/dn613214.aspx).                                                                                                  |  
| Authentication/UserManager/DefaultAccountLockoutTimeSpan        | El periodo de tiempo predeterminado que un usuario está bloqueado después de llegar a Authentication/UserManager/MaxFailedAccessAttemptsBeforeLockout. Valor predeterminado: 24:00:00 (1 día). Para obtener más información consulte [UserManager<TUser, TKey>.DefaultAccountLockoutTimeSpan](https://msdn.microsoft.com/library/dn613201.aspx).                 |  
| Authentication/UserManager/MaxFailedAccessAttemptsBeforeLockout | El número máximo de intentos de acceso permitidos antes de que un usuario quede bloqueado (si está habilitado el bloqueo). Opción predeterminada: 5. Para obtener más información consulte [UserManager<TUser, TKey>.MaxFailedAccessAttemptsBeforeLockout](https://msdn.microsoft.com/library/dn613202.aspx).                                                                        |  
| Authentication/ApplicationCookie/ExpireTimeSpan                 | La cantidad predeterminada de tiempo para las que son válidas las sesiones de autenticación de cookie. Valor predeterminado: 24:00:00 (1 día). Para obtener más información consulte [CookieAuthenticationOptions.ExpireTimeSpan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx). |
||  

## <a name="cookie-authentication-site-settings"></a>Configuración del sitio de autenticación de cookies

Configuración para modificar el comportamiento predeterminado de la cookie de autenticación. Definido por la clase [CookieAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.aspx).

| Nombre de configuración del sitio   | Descripción       |
|----------------------|------------------------------------------------|
| Authentication/ApplicationCookie/AuthenticationType                      | El tipo de cookie de autenticación de la aplicación. Predeterminada: ApplicationCookie. Para obtener más información: [AuthenticationOptions::AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx).  |
| Authentication/ApplicationCookie/CookieName                              | Determina el nombre de cookie empleado para persistir la identidad. Predeterminada: .AspNet.Cookies. Para obtener más información: [CookieAuthenticationOptions::CookieName](https://msdn.microsoft.com/library/dn385537.aspx).  |
| Authentication/ApplicationCookie/CookieDomain                            | Determina el dominio empleado para crear la cookie. Para obtener más información: [CookieAuthenticationOptions::CookieDomain](https://msdn.microsoft.com/library/dn385536.aspx).  |
| Authentication/ApplicationCookie/CookiePath                              | Determina la ruta emplead apara crear la cookie. Predeterminada: /. Para obtener más información: [CookieAuthenticationOptions::CookiePath](https://msdn.microsoft.com/library/dn385539.aspx). |
| Authentication/ApplicationCookie/CookieHttpOnly                          | Determina si el explorador debe permitir que el javascript del cliente acceda a la cookie. Valor predeterminado: true. Para obtener más información: [CookieAuthenticationOptions::CookieHttpOnly](https://msdn.microsoft.com/library/dn385540.aspx).                     |
| Authentication/ApplicationCookie/CookieSecure                            | Determina si la cookie debe transmitirse solo en la solicitud HTTPS. Predeterminada: SameAsRequest. Para obtener más información: [CookieAuthenticationOptions::CookieSecure](https://msdn.microsoft.com/library/dn385538.aspx).  |
| Authentication/ApplicationCookie/ExpireTimeSpan                          | Controla el tiempo que la cookie de la aplicación seguirá siendo válida a partir del punto que se crea. Valor predeterminado: 14 días. Para obtener más información: [CookieAuthenticationOptions::ExpireTimeSpan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx).  |
| Authentication/ApplicationCookie/SlidingExpiration                       | SlidingExpiration se establece en True para indicar al middleware que vuelva a emitir una nueva cookie con una nueva hora de expiración cada vez que procesa una solicitud que sea más de la mitad de la ventana de expiración. Valor predeterminado: true. Para obtener más información: [CookieAuthenticationOptions::SlidingExpiration](https://msdn.microsoft.com/library/dn385548.aspx). |
| Authentication/ApplicationCookie/LoginPath                               | La propiedad LoginPath informa al middleware que debe cambiar un código de estado saliente 401 No autorizado por una redirección 302 en la ruta de inicio de sesión dada. Predeterminada: ~/signin. Para obtener más información: [CookieAuthenticationOptions::LoginPath](https://msdn.microsoft.com/library/dn385541.aspx).                                            |
| Authentication/ApplicationCookie/LogoutPath                              | Si el LogoutPath recibe el middleware, una solicitud a esa ruta se redirigirá en función del ReturnUrlParameter. Para obtener más información: [CookieAuthenticationOptions::LogoutPath](https://msdn.microsoft.com/library/dn385545.aspx).               |
| Authentication/ApplicationCookie/ReturnUrlParameter                      | El ReturnUrlParameter determina el nombre del parámetro de cadena de consulta que es anexado por el middleware cuando un código de estado 401 No autorizado se cambia a una redirección 302 en la ruta de inicio de sesión. Para obtener más información: [CookieAuthenticationOptions::ReturnUrlParameter](https://msdn.microsoft.com/library/dn385546.aspx).                           |
| Authentication/ApplicationCookie/SecurityStampValidator/ValidateInterval | El período de tiempo entre las validaciones de marca de seguridad. Por defecto: 30 minutos. Para obtener más información: [SecurityStampValidator::OnValidateIdentity](https://msdn.microsoft.com/library/microsoft.aspnet.identity.owin.securitystampvalidator.onvalidateidentity.aspx).                    |
| Authentication/TwoFactorCookie/AuthenticationType                        | El tipo de cookie de autenticación de dos factores. Predeterminada: TwoFactorCookie. Para obtener más información: [AuthenticationOptions::AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx).            |
| Authentication/TwoFactorCookie/ExpireTimeSpan                            | Controla el tiempo que la cookie de dos factores seguirá siendo válida a partir del punto que se crea. Por defecto: 5 minutos. Para obtener más información: [CookieAuthenticationOptions::ExpireTimeSpan](https://msdn.microsoft.com/library/dn385543.aspx).     |
|||

### <a name="see-also"></a>Vea también

[Configurar la autenticación del portal](configure-portal-authentication.md)  
[Configuración del proveedor OAuth2 para portales](configure-oauth2-settings.md)  
[Configuración de proveedor Open ID Connect para portales](configure-openid-settings.md)  
[Configuración de proveedor de WS-Federation para portales](configure-ws-federation-settings.md)  
[Configuración del proveedor SAML 2.0 para portales](configure-saml2-settings.md)  
