---
title: Migrar proveedores de identidad a Azure AD B2C | MicrosoftDocs
description: Aprenda a migrar proveedores de identidad a Azure AD B2C.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: a57398d08e190140a3383aef29825f4c08e90363
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2708899"
---
# <a name="migrate-identity-providers-to-azure-ad-b2c"></a>Migrar proveedores de identidad a Azure AD B2C

El portal admite un sistema de seguridad configurable que permite a nuestros clientes admitir varios sistemas de autenticación. El portal incluye sus propias credenciales locales además de federación con proveedores de identidad externos mediante protocolos estándar como OIDC, SAML y WS-Federation. En el futuro, se recomienda usar solo el proveedor de identidad de Azure AD B2C para la autenticación y que se descarte a los demás proveedores de identidad. 

## <a name="marking-an-identity-provider-as-deprecate"></a>Marcar un proveedor de identidad como descartado

Puede configurar su portal para marcar a los demás proveedores de identidad como obsoletos y permitir que los usuarios migren a un proveedor de identidad de Azure AD B2C. 

La siguiente configuración de sitio se utiliza para controlar la obsolescencia de proveedores de identidad:

| Nombre  | Descripción  |
|--------|--------|
| Authentication/Registration/LocalLoginDeprecated | Un valor verdadero o falso. Si se establece en true, la cuenta local se marcará como obsoleta. El usuario del portal deberá migrar a una cuenta no obsoleta. De forma predeterminada, se establece como falso. |
| Authentication/[protocolo]/[proveedor]/Obsoleto  | Un valor verdadero o falso. Si se establece en true, la cuenta específica se marcará como obsoleta. El usuario del portal deberá migrar a una cuenta no obsoleta. De forma predeterminada, se establece como falso. |
|||

Cuando un usuario del portal intenta iniciar sesión y se marca al menos a un proveedor de identidad como obsoleto, la cuenta obsoleta se muestra en la página. En el siguiente ejemplo, una cuenta de Microsoft se marca como obsoleta.

![Ejemplo de cuenta en desuso](../media/gdpr-deprecate-account.png "Ejemplo de cuenta en desuso")

Puede cambiar el texto de la pantalla para proveedor de autenticación heredado usando el siguiente fragmento de contenido:

| Nombre                                               | Tipo | Value                         |
|----------------------------------------------------|------|-------------------------------|
| Account/Signin/SignInExternalDeprecatedFormHeading | Texto | Iniciar sesión con una cuenta heredada |
|||

> [!NOTE]
> No se muestran los proveedores de identidad obsoletos cuando un usuario registra o canjea una invitación a un portal.

## <a name="migrating-a-deprecated-identity-provider-to-a-new-identity-provider"></a>Migrar un proveedor de identidad obsoleto a un proveedor de identidad nuevo

Si un usuario de portal inicia sesión con un proveedor de identidad obsoleto, la pantalla de migración de cuentas muestra un mensaje para iniciar sesión con un proveedor de identidad no obsoleto. Cuando el usuario inicia sesión con el proveedor de identidad no obsoleto, la cuenta de usuario se asocia al nuevo proveedor.

![Ejemplo de migración de cuenta](../media/gdpr-account-migration.png "Ejemplo de migración de cuenta")

Puede cambiar el mensaje en la pantalla para migración de cuentas mediante los siguientes fragmentos de contenido:

| Nombre                                         | Tipo | Value                                                                                                                                                                                                                |
|----------------------------------------------|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Account/Conversion/PageTitle                 | Texto | Migración de cuenta                                                                                                                                                                                                    |
| Account/Conversion/PageCopy                  | HTML | Ha iniciado sesión con una cuenta que ya no se admite. Para seguir utilizando este portal, debe migrar a otra cuenta. Seleccione el botón siguiente para iniciar sesión con una cuenta admitida nueva o existente. |
| Account/Conversion/SignInExternalFormHeading | Texto | Iniciar sesión con una cuenta admitida.                                                                                                                                                                                     |
|||

El portal permite asociar varias identidades a un único registro de contacto. Cuando varios proveedores están obsoletos, un usuario de portal debe aceptar los términos y condiciones varias veces. Cada vez que un usuario inicia sesión con un proveedor de identidad obsoleto, se inicia el proceso de migración de cuenta para cada proveedor obsoleto y el registro de contacto se asocia al proveedor no obsoleto después de la migración de cuenta.

Por ejemplo: el portal admite cuentas de Microsoft (MSA), Google y Facebook como proveedores de identidad para la autenticación. Si marca Google y Facebook como proveedores obsoletos y un usuario del portal solo tiene Google y Facebook como proveedores de identidad para la autenticación, el usuario recibirá el mensaje de migración de cuenta al intentar iniciar sesión con alguno de estos dos proveedores. Cuando el usuario inicia sesión con MSA, MSA se agrega al registro de contacto del usuario. Ahora el usuario tiene solo MSA como el proveedor de identidad de autenticación admitido.

Cuando un usuario del portal selecciona un nuevo proveedor de identidad y la identidad ya está asociada a otro registro de contacto, aparece un mensaje de error. Puede configurar el mensaje de error con los siguientes fragmentos de contenido:

| Nombre                                                     | Tipo | Value                                                                                                                               |
|----------------------------------------------------------|------|-------------------------------------------------------------------------------------------------------------------------------------|
| Account/Signin/AccountConversionIdentityUsedErrorHeading | Texto | Error de conversión de cuenta                                                                                                            |
| Account/Signin/AccountConversionIdentityUsedErrorText    | HTML | Esta cuenta ya existe. Cierre el explorador, reinicie el proceso y seleccione otra cuenta en la página Migración de cuenta. |
|||

## <a name="disabling-local-login"></a>Deshabilitación del inicio de sesión local

Puede configurar un portal para deshabilitar el inicio de sesión local mediante la configuración de sitio `Authentication/Registration/LocalLoginDeprecated`. Si alguien intenta iniciar sesión con las credenciales locales, aparece la pantalla de migración de cuenta junto con las instrucciones para iniciar sesión con un proveedor de identidad no obsoleto. Cuando se migra la cuenta, las credenciales locales del usuario se deshabilitan.

> [!NOTE]
> Si marca el inicio de sesión local como obsoleto, el usuario no podrá registrarse para una cuenta nueva.

El campo siguiente se añade en el registro de contacto del portal para indicar si el inicio de sesión local está deshabilitada para un usuario:
- **Inicio de sesión local deshabilitado**: Indica que el contacto ya no puede iniciar sesión en el portal utilizando la cuenta local. De forma predeterminada, se establece en **No**. Este campo está establecido en **Sí** si se migra una cuenta de usuario a un proveedor de identidad no obsoleto y está deshabilitado el inicio de sesión local.

    ![Inicio de sesión local deshabilitado](../media/local-login-disabled.png "Inicio de sesión local deshabilitado")
