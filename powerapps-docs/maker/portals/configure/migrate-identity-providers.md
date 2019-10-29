---
title: Migrar proveedores de identidades a Azure AD B2C | MicrosoftDocs
description: Obtenga información sobre cómo migrar proveedores de identidades a Azure AD B2C.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: a57398d08e190140a3383aef29825f4c08e90363
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978310"
---
# <a name="migrate-identity-providers-to-azure-ad-b2c"></a>Migrar proveedores de identidades a Azure AD B2C

El portal admite un sistema de seguridad configurable que permite que nuestros clientes admitan varios sistemas de autenticación. El portal incluye sus propias credenciales locales además de la Federación con proveedores de identidades externos mediante protocolos estándar como OIDC, SAML y WS-Federation. En el futuro, se recomienda usar solo Azure AD B2C proveedor de identidades para la autenticación y dejar en desuso otros proveedores de identidades. 

## <a name="marking-an-identity-provider-as-deprecate"></a>Marcar un proveedor de identidades como en desuso

Puede configurar el portal para marcar otros proveedores de identidades como desusados y permitir que los usuarios migren a Azure AD B2C proveedor de identidades. 

La siguiente configuración del sitio se utiliza para controlar la degradación de los proveedores de identidades:

| Nombre  | Descripción  |
|--------|--------|
| Autenticación/registro/LocalLoginDeprecated | Valor true o false. Si se establece en true, la cuenta local se marcará como desusada. El usuario del portal tendrá que migrar a una cuenta no desusada. De forma predeterminada, se establece en false. |
| Autenticación/[Protocolo]/[proveedor]/deprecated  | Valor true o false. Si se establece en true, la cuenta específica se marcará como desusada. El usuario del portal tendrá que migrar a una cuenta no desusada. De forma predeterminada, se establece en false. |
|||

Cuando un usuario del portal intenta iniciar sesión y ha marcado al menos un proveedor de identidades como desusado, se muestra la cuenta en desuso en la página. En el ejemplo siguiente, una cuenta de Microsoft se marca como desusada.

![Ejemplo de cuenta en desuso](../media/gdpr-deprecate-account.png "Ejemplo de cuenta en desuso")

El texto de la pantalla para el proveedor de autenticación heredado se puede cambiar mediante el siguiente fragmento de código de contenido:

| Nombre                                               | Tipo | Value                         |
|----------------------------------------------------|------|-------------------------------|
| Cuenta/inicio de sesión/SignInExternalDeprecatedFormHeading | Text | Iniciar sesión con una cuenta heredada |
|||

> [!NOTE]
> Los proveedores de identidad desusados no se muestran cuando un usuario registra o canjea una invitación para un portal.

## <a name="migrating-a-deprecated-identity-provider-to-a-new-identity-provider"></a>Migración de un proveedor de identidades en desuso a un nuevo proveedor de identidades

Si un usuario del portal inicia sesión con un proveedor de identidades en desuso, la pantalla migración de cuentas muestra un mensaje para iniciar sesión con un proveedor de identidades que no está en desuso. Cuando el usuario inicia sesión con el proveedor de identidades no en desuso, la cuenta de usuario se asocia con el nuevo proveedor.

![Ejemplo de migración de cuentas](../media/gdpr-account-migration.png "Ejemplo de migración de cuentas")

El mensaje en la pantalla para la migración de cuentas se puede cambiar mediante los siguientes fragmentos de código de contenido:

| Nombre                                         | Tipo | Value                                                                                                                                                                                                                |
|----------------------------------------------|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Account/Conversion/PageTitle                 | Text | Migración de cuentas                                                                                                                                                                                                    |
| Account/Conversion/PageCopy                  | HTML | Ha iniciado sesión con una cuenta que ya no se admite. Para seguir usando este portal, debe migrar a una cuenta diferente. Seleccione el botón siguiente para iniciar sesión con una cuenta admitida nueva o existente. |
| Account/Conversion/SignInExternalFormHeading | Text | Inicie sesión con una cuenta admitida.                                                                                                                                                                                     |
|||

El portal permite asociar varias identidades a un único registro de contacto. Cuando varios proveedores están en desuso, un usuario del portal debe dar su consentimiento a los términos y condiciones varias veces. Cada vez que un usuario inicia sesión con un proveedor de identidades en desuso, se inicia el proceso de migración de cuentas para cada proveedor en desuso y el registro de contacto se asocia al proveedor no en desuso después de la migración de la cuenta.

Por ejemplo: el portal admite cuenta de Microsoft (MSA), Google y Facebook como proveedores de identidades para la autenticación. Si marca Google y Facebook como proveedores en desuso y un usuario del portal solo tiene Google y Facebook como proveedores de identidades para la autenticación, el usuario recibirá el mensaje de migración de la cuenta cuando intente iniciar sesión con cualquiera de estos dos proveedores. Cuando el usuario inicia sesión con MSA, se agrega MSA al registro de contacto del usuario. El usuario ahora solo tiene MSA como proveedor de identidades de autenticación compatible.

Cuando un usuario del portal selecciona un nuevo proveedor de identidades y la identidad ya está asociada a otro registro de contacto, aparece un mensaje de error. Puede configurar el mensaje de error mediante los siguientes fragmentos de código de contenido:

| Nombre                                                     | Tipo | Value                                                                                                                               |
|----------------------------------------------------------|------|-------------------------------------------------------------------------------------------------------------------------------------|
| Cuenta/inicio de sesión/AccountConversionIdentityUsedErrorHeading | Text | Error de conversión de cuenta                                                                                                            |
| Cuenta/inicio de sesión/AccountConversionIdentityUsedErrorText    | HTML | Esta cuenta ya existe. Cierre el explorador, reinicie el proceso y seleccione otra cuenta en la página migración de cuentas. |
|||

## <a name="disabling-local-login"></a>Deshabilitar el inicio de sesión local

Puede configurar un portal para deshabilitar el inicio de sesión local mediante la configuración del sitio `Authentication/Registration/LocalLoginDeprecated`. Si alguien intenta iniciar sesión con las credenciales locales, aparecerá la pantalla migración de cuenta junto con la instrucción para iniciar sesión con un proveedor de identidades no en desuso. Cuando se migra la cuenta, se deshabilitan las credenciales locales para el usuario.

> [!NOTE]
> Si marca inicio de sesión local como desusado, el usuario no podrá registrarse para una cuenta nueva.

El siguiente campo se agrega en el registro del contacto del portal para indicar si el inicio de sesión local está deshabilitado para un usuario:
- **Inicio de sesión local deshabilitado**: indica que el contacto ya no puede iniciar sesión en el portal con la cuenta local. De forma predeterminada, se establece en **no**. Este campo se establece en **sí** si se migra la cuenta de un usuario a un proveedor de identidades que no está en desuso y el inicio de sesión local está deshabilitado.

    ![Inicio de sesión local deshabilitado](../media/local-login-disabled.png "Inicio de sesión local deshabilitado")
