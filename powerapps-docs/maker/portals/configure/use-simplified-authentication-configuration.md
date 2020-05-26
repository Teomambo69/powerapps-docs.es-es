---
title: Usar la autenticación simplificada y la configuración del proveedor de identidades (vista previa) | MicrosoftDocs
description: Aprenda a usar la configuración de portal rápida, fácil y simplificada para autenticación.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/05/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 6dc6fc21c32c044a49ff9364dbf0c3c95bcb04cf
ms.sourcegitcommit: 13a78a66408d39b4bc90a72613b0d303abc07b1b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2020
ms.locfileid: "3338239"
---
# <a name="simplified-authentication-and-identity-provider-configuration-preview"></a>Autenticación simplificada y configuración del proveedor de identidades (vista previa)

[Este tema es documentación preliminar y está sujeto a modificaciones.]

La configuración de la autenticación es una personalización principal en cualquier portal. La configuración del proveedor de identidades simplificada en los portales de Power Apps proporciona orientación dentro de la aplicación para la configuración del proveedor de identidades y resume las complejidades de la configuración. Los creadores y administradores pueden configurar fácilmente el portal para proveedores de identidades admitidos.

> [!NOTE]
> La característica de autenticación simplificada y la configuración del proveedor de identidades está en vista previa. Para obtener acceso a esta característica en vista previa, debe usar la [vista previa de Power Apps](https://make.preview.powerapps.com). Después de que esta característica en vista previa esté disponible con carácter general, podrá acceder a ella desde [Power Apps](https://make.powerapps.com). No puede activar o desactivar esta característica en vista previa para su portal. Para obtener más información sobre las características en vista previa (GB), vea [Descripción de las características experimentales y en vista previa de Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-experimental-preview). 

## <a name="overview"></a>Información general

Puede habilitar, deshabilitar y configurar proveedores de identidades del portal desde la [vista previa de Power Apps](https://make.preview.powerapps.com) mediante el uso de la configuración de autenticación de portal simplificada. Después de seleccionar un proveedor de identidades, puede seguir las indicaciones para introducir fácilmente la configuración del proveedor, en lugar de [configurar la autenticación manualmente](set-authentication-identity.md).

### <a name="authentication-settings"></a>Configuración de autenticación

Para comenzar a configurar un proveedor de identidades para su portal:

1. Vaya a la [vista previa de Power Apps](https://make.preview.powerapps.com).

1. Seleccione **Aplicaciones** en el panel de navegación izquierdo.

    ![Seleccione Aplicaciones](media/use-simplified-authentication-configuration/select-apps.png "Seleccionar Aplicaciones").

1. Seleccione su portal en la lista de aplicaciones disponibles.

1. Seleccione **Ajustes** en el menú superior. También puede seleccionar **Más comandos** (**...**) y luego seleccionar **Configuraciones**.

    ![Seleccione Configuración](media/use-simplified-authentication-configuration/select-settings.png "Seleccionar Configuración").

1. Desde la configuración del lado derecho de su área de trabajo, seleccione **Configuración de autenticación**.

    ![Configuración de autenticación](media/use-simplified-authentication-configuration/portal-settings-right-pane.png "Configuración de autenticación")

Verá una lista de proveedores de identidades que puede configurar.

![Proveedores de identidades](media/use-simplified-authentication-configuration/portal-authentication-settings.png "Proveedores de identidades")

> [!NOTE]
> Los portales de Power Apps admiten varios proveedores de identidades. Sin embargo, la característica de configuración de autenticación simplificada y proveedor de identidades actualmente solo admite los proveedores de identidades enumerados anteriormente.

#### <a name="authentication-settings-from-the-portal-details-page"></a>Configuración de autenticación en la página de detalles del portal

También puede ver los proveedores de identidades desde la página de detalles del portal.

1. Seleccione su portal en la lista de aplicaciones disponibles.

1. Seleccione **Detalles** en el menú superior. También puede seleccionar **Más comandos** (**...**) y luego seleccionar **Detalles**.

    ![Seleccione detalles](media/use-simplified-authentication-configuration/select-details.png "Seleccionar detalles").

La página de detalles muestra la sección **Proveedores de identidades**.

![Detalles del portal](media/use-simplified-authentication-configuration/portal-details.png "Detalles del portal")

> [!NOTE]
> Tras seleccionar **Ver todo** desde la página de detalles del portal, podrá ver la lista completa de proveedores de identidades.

## <a name="general-authentication-settings"></a>Configuración general de autenticación

Puede definir las siguientes configuraciones generales de autenticación seleccionando **Configuración de autenticación** en la página **Proveedores de identidades**.

![Configuración general de autenticación](media/use-simplified-authentication-configuration/general-authentication-settings.png "Configuración general de autenticación")

- **Inicio de sesión externo**: al establecer la opción como **Desactivado**, deshabilita y oculta el inicio de sesión y registro externos de cuenta.
<br>La autenticación externa la proporciona la API de identidad ASP.NET. En este caso, las credenciales de cuenta y la administración de contraseñas son controladas por proveedores de identidades externos, como Facebook, LinkedIn, Google, Twitter y Microsoft. Los usuarios se suscriben para acceder al portal seleccionando una identidad externa para registrarse en el portal. Una vez registrada, una identidad externa tiene acceso a las mismas características que una cuenta local. Vea [Administrar cuentas externas](set-authentication-identity.md#manage-external-accounts) para configuraciones del sitio relacionadas.

- **[Registro abierto](configure-portal-authentication.md#open-registration)**: cuando se establece como **Desactivado**, deshabilita y oculta el registro externo de cuenta.

También puede ir a la configuración general de autenticación desde la página de detalles del portal seleccionando **Configuración**en la esquina superior derecha de la sección **Proveedores de identidades**.

![Configuración general de autenticación desde la página de detalles](media/use-simplified-authentication-configuration/general-settings-from-details.png "Configuración general de autenticación desde la página de detalles")

### <a name="default-identity-provider"></a>Proveedor de identidades predeterminado

Puede establecer cualquier proveedor de identidades como predeterminado. Cuando un proveedor de identidades se establece como el predeterminado, a los usuarios que inician sesión en el portal no se les redirige a la página de inicio de sesión del portal. En su lugar, la experiencia de inicio de sesión siempre establece de manera predeterminada el inicio de sesión utilizando el proveedor seleccionado.

![Proveedor de identidades predeterminado](media/use-simplified-authentication-configuration/set-default.png "Proveedor de identidades predeterminado")

> [!IMPORTANT]
> Si establece un proveedor de identidades como el predeterminado, los usuarios no tendrán la opción de elegir ningún otro proveedor de identidades.

Después de establecer un proveedor de identidades como el predeterminado, puede seleccionar **Eliminar como predeterminado** para eliminarlo como el predeterminado. Si elimina un proveedor de identidades como predeterminado, a los usuarios se le redirigirá a la página de inicio de sesión del portal y podrán elegir entre los proveedores de identidades que ha habilitado.

> [!NOTE]
> Solo puede establecer un proveedor de identidades configurado como el predeterminado. La opción **Establecer como predeterminado** estará disponible después de configurar un proveedor de identidades.

## <a name="add-configure-or-delete-an-identity-provider"></a>Agregar, configurar o eliminar un proveedor de identidades

De manera predeterminada, se agregan varios proveedores de identidades que puede configurar. Puede agregar más proveedores de Azure Active Directory (Azure AD) B2C o bien, configurar los proveedores de Oauth 2.0 disponibles como LinkedIn y Microsoft.

> [!NOTE]
> - No puede cambiar la configuración de los proveedores de [Inicio de sesión local](configure-portal-authentication.md) y Azure Active Directory al usar esta interfaz.
> - Solo puede tener una instancia de cada tipo de proveedor de identidades para Oauth 2.0, como **Facebook**, **LinkedIn**, **Google**, **Twitter** y **Microsoft**.
> - Las actualizaciones de la configuración del proveedor de identidades pueden tardar unos minutos en reflejarse en el portal. Para aplicar sus cambios inmediatamente, puede [reiniciar el portal](../admin/admin-overview.md#open-power-apps-portals-admin-center).

### <a name="add-or-configure-a-provider"></a>Agregar o configurar un proveedor

Para agregar un proveedor de identidades, seleccione **Agregar proveedor** desde **Configuración de autenticación**.

![Agregar un proveedor desde la configuración](media/use-simplified-authentication-configuration/add-provider-from-settings.png "Agregar un proveedor desde la configuración")

También puede seleccionar **Agregar proveedor** en la página de detalles del portal.

![Agregar un proveedor desde la página de detalles](media/use-simplified-authentication-configuration/add-provider-from-details.png "Agregar un proveedor desde la página de detalles")

Puede seleccionar en la lista de proveedores disponibles, introducir un nombre y luego seleccionar **Siguiente** para configurar la configuración del proveedor.

![Agregar un nuevo proveedor](media/use-simplified-authentication-configuration/add-provider.png "Agregar un nuevo proveedor")

> [!NOTE]
> El **Nombre del proveedor** que introduce aquí se muestra en la página de inicio de sesión para los usuarios como el texto del botón que usan al seleccionar este proveedor.

Para configurar un proveedor, seleccione **Haga clic para configurar** (o seleccione **Más comandos** (**..**) y luego seleccione **Configurar**).

![Configurar un proveedor](media/use-simplified-authentication-configuration/configure-provider.png "Configurar un proveedor")

> [!NOTE]
> Puede usar **Agregar proveedor** o **Configurar** para agregar o configurar un proveedor por primera vez. Después de configurar un proveedor, puede editarlo. También puede seleccionar el hipervínculo del nombre del proveedor para abrir las opciones de configuración rápidamente.

Los pasos de configuración después de seleccionar **Siguiente** dependen del tipo de proveedor de identidades que seleccione. Por ejemplo, la configuración de Azure Active Directory B2C es diferente a la manera de configurar LinkedIn. Consulte las secciones específicas del proveedor más adelante en este artículo para configurar el proveedor que elija.

### <a name="edit-a-provider"></a>Editar un proveedor

Después de agregar y configurar un proveedor, puede ver el proveedor en el estado **Habilitado** en las páginas de detalles o configuración del portal.

Para editar un proveedor que haya configurado, selecciónelo, seleccione **Más comandos** (**...**) y luego seleccione **Editar configuración**.

![Editar un proveedor](media/use-simplified-authentication-configuration/edit-provider.png "Editar un proveedor")

Consulte las secciones específicas del proveedor más adelante en este artículo para editar la configuración del tipo de proveedor que ha seleccionado.

### <a name="delete-a-provider"></a>Eliminar un proveedor

Para eliminar un proveedor de identidades, seleccione **Más comandos** (**...**) y luego seleccione **Eliminar**.

![Eliminar un proveedor](media/use-simplified-authentication-configuration/delete-provider.png "Eliminar un proveedor")

Al eliminar un proveedor, se elimina su configuración de proveedor para el tipo de proveedor seleccionado, y el proveedor vuelve a estar disponible para la configuración.

> [!NOTE]
> Al eliminar un proveedor, solo se elimina la configuración del portal para el proveedor. Por ejemplo, si elimina el proveedor de LinkedIn, su aplicación de LinkedIn y la configuración de la aplicación permanecen intactas. Del mismo modo, si elimina un proveedor de Azure Active Directory B2C, solo se elimina la configuración del portal; la configuración del inquilino de Azure para este proveedor no cambiará.

## <a name="configure-the-azure-active-directory-b2c-provider"></a>Configurar el proveedor de Azure Active Directory B2C

### <a name="step-1---configure-the-azure-active-directory-b2c-application"></a>Paso 1: Configurar la aplicación Azure Active Directory B2C

![Configurar la aplicación Azure AD B2C](media/use-simplified-authentication-configuration/configure-ad-b2c-step1.png "Configurar la aplicación Azure AD B2C")

Para usar Azure AD B2C como proveedor de identidades:

1. [Cree y configure un inquilino de Azure AD B2C](https://docs.microsoft.com/azure/active-directory-b2c/tutorial-create-tenant).

1. [Registre una aplicación](https://docs.microsoft.com/azure/active-directory-b2c/tutorial-register-applications?tabs=applications#register-a-web-application) en su inquilino. Use la **URL de respuesta** proporcionada en el asistente durante la configuración de la aplicación.

    > [!NOTE]
    > Debe elegir  **Sí**  para el campo  **Permitir flujo implícito**  e introducir la dirección URL del portal en el campo  **URL de respuesta** .

1. [Creación de un flujo de usuario](https://docs.microsoft.com/azure/active-directory-b2c/tutorial-create-user-flows#create-a-sign-up-and-sign-in-user-flow). Opcionalmente, [cree un flujo de usuario de restablecimiento de contraseña](https://docs.microsoft.com/azure/active-directory-b2c/tutorial-create-user-flows#create-a-password-reset-user-flow).

1. [Configure la compatibilidad del token](https://docs.microsoft.com/azure/active-directory-b2c/configure-tokens#configure-token-compatibility) con una dirección URL de **Notificación de emisor (iss)** que incluya **tfp**. Más información: [Compatibilidad de tokens](https://docs.microsoft.com/azure/active-directory-b2c/tokens-overview#compatibility)

### <a name="step-2---configure-site-settings"></a>Paso 2: Configuración del sitio

Configure la siguiente configuración del sitio y la directiva de restablecimiento de contraseña para su proveedor de Azure AD B2C.

![Configuración del sitio](media/use-simplified-authentication-configuration/configure-ad-b2c-step2.png "Configuración del sitio")

- **Autoridad**: la URL del emisor definida en los metadatos del flujo de usuario de la directiva de registro e inicio de sesión.
<br> Para obtener la URL del emisor:

   1. Abra el flujo de usuario de registro e inicio de sesión que creó en el [paso 1](#step-1---configure-the-azure-active-directory-b2c-application). Para este paso, debe visitar el inquilino de Azure AD B2C en el [Azure Portal](https://portal.azure.com).
   1. Seleccione **Ejecutar flujo de usuario**, y en el cuadro de diálogo **Abrir**, seleccione la URL en la parte superior para abrir el documento de configuración. <br> La URL hace referencia a *Documento de configuración del proveedor de identidades de OpenID Connect*, también conocido como *Extremo de configuración de well-known de OpenID*.
   1. Copie la URL del **Emisor** desde el documento de configuración que se abre en un nuevo navegador.  

- **Id. de cliente**: introduzca el **Id. de aplicación** de la aplicación Azure AD B2C creada en el [paso 1](#step-1---configure-the-azure-active-directory-b2c-application).

- **URL de redireccionamiento**: escriba la dirección URL del portal. <br> Solo necesita cambiar el URI de redireccionamiento si usa un nombre de dominio personalizado.

#### <a name="password-reset-settings"></a>Configuración de restablecimiento de contraseña

- **Id. de directiva predeterminada**: introduzca el nombre del flujo de usuario de registro e inicio de sesión que creó en el [paso 1](#step-1---configure-the-azure-active-directory-b2c-application). El nombre tiene el prefijo *B2C_1*.

- **Id. de directiva de restablecimiento de contraseña**: introduzca el nombre del flujo de usuario de restablecimiento de contraseña que creó en el [paso 1](#step-1---configure-the-azure-active-directory-b2c-application). El nombre tiene el prefijo *B2C_1*.

- **Emisores válidos**: una lista delimitada por comas de direcciones URL de emisor para el flujo de usuario de registro e inicio de sesión y el flujo de usuario de restablecimiento de contraseña que creó en el [paso 1](#step-1---configure-the-azure-active-directory-b2c-application). 
<br> Para obtener las URL de emisor para el flujo de usuario de registro e inicio de sesión, y el flujo de usuario de restablecimiento de contraseña, abra cada flujo y luego siga los pasos de **Autoridad**, que se indican anteriormente en esta sección.

Para obtener más información sobre la configuración del sitio, consulte la [configuración del sitio relacionada](azure-ad-b2c.md#related-site-settings).

### <a name="step-3---configure-additional-settings"></a>Paso 3: Configuración adicional de las opciones configuración

Tiene la opción de configurar ajustes adicionales para el proveedor de identidades de Azure AD B2C.

![Configuración adicional de las opciones configuración](media/use-simplified-authentication-configuration/configure-ad-b2c-step3.png "Configuración adicional de las opciones configuración")

- **Asignación de notificaciones de registro**: lista de pares de nombre lógico y notificación que se usarán para asignar valores de notificación devueltos de Azure AD B2C creados durante el registro a atributos del registro de contacto. <br> Por ejemplo, si ha habilitado **Puesto (jobTitle)** y **Código postal (postalCode)** como **Atributos del usuario** en su flujo de usuario y desea actualizar los campos correspondientes de la entidad Contacto **Puesto (jobTitle)** y **Dirección 1: código postal (address1_postalcode)**, introduzca la asignación de notificaciones como: ```jobtitle=jobTitle,address1_postalcode=postalCode```.
- **Asignación de notificaciones de inicio de sesión**: lista de pares de nombre lógico y notificación que se usarán para asignar valores devueltos de Azure AD B2C después de iniciar sesión en los atributos del formulario de contacto. <br> Por ejemplo, si ha habilitado **Puesto (jobTitle)** y **Código postal (postalCode)** como **Notificaciones de aplicación** en su flujo de usuario y desea actualizar los campos correspondientes de la entidad Contacto **Puesto (jobTitle)** y **Dirección 1: código postal (address1_postalcode)**, introduzca la asignación de notificaciones como: ```jobtitle=jobTitle,address1_postalcode=postalCode```.
- **Cierre de sesión externo**: habilita o deshabilita el cierre de sesión federado. Si se establece en **Activado**, a los usuarios se les redirige a la experiencia de usuario de cierre de sesión federada al cerrar sesión del portal. Si se establece en **Desactivado**, los usuarios solo cierran sesión desde el portal.
- **Asignación de contacto con correo electrónico**: especifica si los contactos están asignados a un correo electrónico correspondiente. Si se establece en **Activado**, el valor se asocia a un registro de contacto único con una dirección de correo electrónico coincidente, y después asigna automáticamente el proveedor de identidades externo al contacto cuando el usuario inicia sesión correctamente.
- **Registro habilitado**: active o desactive el [registro abierto](configure-portal-authentication.md#open-registration) para su portal. Al establecer esta opción en **Desactivado**, se deshabilita y oculta el registro de cuenta externo.

Seleccione **Confirmar** para ver un resumen de su configuración y completar la configuración de la identidad.

Para obtener más información acerca de la asignación de notificaciones, consulte [Escenarios de asignación de notificaciones de Azure AD B2C](azure-ad-b2c.md#claims-mapping).

Para más información acerca de la configuración del proveedor de identidades de Azure AD B2C, consulte [Configuración del proveedor de Azure AD B2C para portales](azure-ad-b2c.md#customize-the--ad-b2c-user-interface).

## <a name="configure-the-facebook-provider"></a>Configure el proveedor de Facebook

![Configurar la aplicación Facebook](media/use-simplified-authentication-configuration/configure-facebook.png "Configurar la aplicación Facebook")

Para usar **Facebook** como proveedor de identidades, necesita [crear una aplicación en Facebook](https://developers.facebook.com) con una URL de redireccionamiento.

La aplicación Facebook utiliza la URL de redireccionamiento para redirigir a los usuarios al portal después de que la autenticación se realice correctamente. Si su portal usa un nombre de dominio personalizado, es posible que tenga una URL diferente a la que se proporciona aquí.

**Configuración del sitio del portal** para Facebook:

- **Id. de cliente**: un id. de aplicación único generado por Facebook para su aplicación.
- **Secreto de cliente**: el secreto de la aplicación para su aplicación Facebook.

Para definir las opciones de configuración adicionales de Facebook, consulte [configurar opciones adicionales para proveedores Oauth 2](#configure-additional-settings-for-oauth-2-providers).

Para obtener más información acerca de la configuración de proveedores Oauth, consulte [Configuración del proveedor OAuth2 para portales](configure-oauth2-settings.md).

## <a name="configure-the-linkedin-provider"></a>Configurar el proveedor de LinkedIn

![Configurar la aplicación LinkedIn](media/use-simplified-authentication-configuration/configure-linkedin.png "Configurar la aplicación LinkedIn")

Para usar **LinkedIn** como proveedor de identidades, necesita [crear una aplicación en LinkedIn](https://www.linkedin.com/developers/apps) con una URL de redireccionamiento.

La aplicación LinkedIn utiliza la URL de redireccionamiento para redirigir a los usuarios al portal después de que la autenticación se realice correctamente. Si su portal usa un nombre de dominio personalizado, es posible que tenga una URL diferente a la que se proporciona aquí.

**Configuración del sitio del portal** para LinkedIn:

- **Id. de cliente**: un Id. de aplicación único generado por LinkedIn para su aplicación.
- **Secreto de cliente**: el secreto de la aplicación para su aplicación LinkedIn.

Para configurar ajustes adicionales de LinkedIn, consulte [configurar opciones adicionales para proveedores Oauth 2](#configure-additional-settings-for-oauth-2-providers).

Para obtener más información acerca de la configuración de proveedores Oauth, consulte [Configuración del proveedor OAuth2 para portales](configure-oauth2-settings.md).

## <a name="configure-the-google-provider"></a>Configure el proveedor de Google

![Configurar la aplicación Google](media/use-simplified-authentication-configuration/configure-google.png "Configurar la aplicación Google")

Para usar **Google** como proveedor de identidades, necesita [crear una aplicación en Google](https://console.developers.google.com/) con una URL de redireccionamiento.

La aplicación Google utiliza la URL de redireccionamiento para redirigir a los usuarios al portal después de que la autenticación se realice correctamente. Si su portal usa un nombre de dominio personalizado, es posible que tenga una URL diferente a la que se proporciona aquí.

**Configuración del sitio del portal** para Google:

- **Id. de cliente**: un id. de aplicación único generado por Google para su aplicación.
- **Secreto de cliente**: el secreto de cliente generado por Google para su aplicación.

Para configurar ajustes adicionales de Google, consulte [configurar opciones adicionales para proveedores Oauth 2](#configure-additional-settings-for-oauth-2-providers).

Para obtener más información acerca de la configuración de proveedores Oauth, consulte [Configuración del proveedor OAuth2 para portales](configure-oauth2-settings.md).

## <a name="configure-the-twitter-provider"></a>Configure el proveedor de Twitter

![Configurar la aplicación Twitter](media/use-simplified-authentication-configuration/configure-twitter.png "Configurar la aplicación Twitter")

Para usar **Twitter** como proveedor de identidades, necesita [crear una aplicación en Twitter](https://developer.twitter.com/apps) con una URL de redireccionamiento.

La aplicación Twitter utiliza la URL de redireccionamiento para redirigir a los usuarios al portal después de que la autenticación se realice correctamente. Si su portal usa un nombre de dominio personalizado, es posible que tenga una URL diferente a la que se proporciona aquí.

**Configuración del sitio del portal** para Twitter:

- **Id. de cliente**: un id. de aplicación único generado por Twitter para su aplicación.
- **Secreto de cliente**: el secreto de cliente generado por Twitter para su aplicación.

Para establecer la **Configuración adicional** para Twitter, consulte [configurar opciones adicionales para proveedores Oauth 2](#configure-additional-settings-for-oauth-2-providers).

Para obtener más información acerca de la configuración de proveedores Oauth, consulte [Configuración del proveedor OAuth2 para portales](configure-oauth2-settings.md).

## <a name="configure-the-microsoft-provider"></a>Configurar el proveedor de Microsoft

![Configurar la aplicación de Microsoft](media/use-simplified-authentication-configuration/configure-microsoft.png "Configurar la aplicación de Microsoft")

Para usar **Microsoft** como proveedor de identidades, necesita [crear una aplicación en el portal de Azure](https://aka.ms/AppRegistrations) con una URL de redireccionamiento.

La aplicación de Microsoft utiliza la URL de redireccionamiento para redirigir a los usuarios al portal después de que la autenticación se realice correctamente. Si su portal usa un nombre de dominio personalizado, es posible que tenga una URL diferente a la que se proporciona aquí.

**Configuración del sitio del portal** para Microsoft:

- **Id. de cliente**: un id. de aplicación único generado por Microsoft para su aplicación.
- **Secreto de cliente**: el secreto de cliente generado por Microsoft para su aplicación.

Para establecer la **Configuración adicional** para Microsoft, consulte [configurar opciones adicionales para proveedores Oauth 2](#configure-additional-settings-for-oauth-2-providers).

Para obtener más información acerca de la configuración de proveedores Oauth, consulte [Configuración del proveedor OAuth2 para portales](configure-oauth2-settings.md).

## <a name="configure-additional-settings-for-oauth-2-providers"></a>Configurar ajustes adicionales para proveedores Oauth 2

La configuración adicional de autenticación de esta sección se aplica a los proveedores **Facebook**, **Twitter**, **Microsoft**, **LinkedIn** y **Google**.

![Configuración adicional de las opciones configuración](media/use-simplified-authentication-configuration/additional-oauth-settings.png "Configuración adicional de las opciones configuración")

- **Tipo de autenticación**: el tipo de middleware de autenticación OWIN: [AuthenticationOptions.AuthenticationType](https://docs.microsoft.com/previous-versions/aspnet/mt152183(v=vs.113)?redirectedfrom=MSDN). Por ejemplo, https://sts.windows.net/contoso.onmicrosoft.com/.
- **Modo de autenticación**: el modo de middleware de autenticación OWIN: [AuthenticationOptions.AuthenticationMode](https://docs.microsoft.com/previous-versions/aspnet/mt152179(v=vs.113)?redirectedfrom=MSDN).
- **Tiempo de espera de canal posterior**: valor de tiempo de espera en milisegundos para comunicaciones de canal posterior: [MicrosoftAccountAuthenticationOptions.BackchannelTimeout](https://docs.microsoft.com/previous-versions/aspnet/mt174421(v=vs.113)?redirectedfrom=MSDN).
- **Ruta de acceso de devolución de llamada**: la ruta de acceso de solicitud dentro de la ruta de acceso base de la aplicación donde se devolverá el agente de usuario: [MicrosoftAccountAuthenticationOptions.CallbackPath](https://docs.microsoft.com/previous-versions/aspnet/mt174433(v=vs.113)?redirectedfrom=MSDN).
- **Iniciar sesión como tipo de autenticación**: el nombre de otro middleware de autenticación que será responsable de emitir realmente una identidad de notificaciones de usuario: [MicrosoftAccountAuthenticationOptions.SignInAsAuthenticationType](https://docs.microsoft.com/previous-versions/aspnet/mt174430(v=vs.113)?redirectedfrom=MSDN).
- **Ámbito**: una lista de permisos separados por comas para solicitar: [MicrosoftAccountAuthenticationOptions.Scope](https://docs.microsoft.com/previous-versions/aspnet/mt174435(v=vs.113)?redirectedfrom=MSDN).
- **Registro habilitado**: habilita o deshabilita el requisito de registro para el proveedor de identidades existente. Cuando está deshabilitado, al usuario se le deniega el registro con un error si no existe ningún registro de contacto para el usuario. Si se habilita esta opción, el registro de usuario está permitido para un nuevo usuario solo si la configuración del sitio **Authentication/Registration/Enabled** se ha establecido en true.

Si desea obtener más información, consulte [Configuración de sitio OAuth2](configure-oauth2-settings.md#create-site-settings-by-using-oauth2).

### <a name="see-also"></a>Vea también

- [Establecer identidad de autenticación para un portal](set-authentication-identity.md)
- [Configuración del proveedor de Azure AD B2C](azure-ad-b2c.md)
- [Configuración del proveedor de OAuth2](configure-oauth2-settings.md)
