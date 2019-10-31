---
title: Conectarse a un portal de una organización en línea de Dynamics 365 | MicrosoftDocs
description: Aprenda a conectarse a un portal de una organización en línea de Dynamics 365 y cómo renovar la clave de autenticación.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="connect-to-a-dynamics-365-online-organization-using-a-portal"></a>Conectarse a una organización en línea de Dynamics 365 utilizando un portal

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

Un portal se conecta a una organización en línea Dynamics 365 con una aplicación de Azure Active Directory. La aplicación se crea en el mismo inquilino donde está aprovisionado el portal. La aplicación se registra con la organización de Dynamics 365 durante el proceso de aprovisionamiento del portal.

![Conecte un portal con una organización de Dynamics 365](../media/connect-with-dynamics.png "conecte un portal con una organización de Dynamics 365")

Cada portal tiene una aplicación de Azure Active Directory independiente asociada, esté o no conectado a la misma organización de Dynamics 365. El proveedor de autenticación de Azure Active Directory predeterminado creado para un portal utiliza la misma aplicación de Azure Active Directory para autenticar el portal. La autorización se aplica mediante roles asignados al usuario que accede al portal.

Puede ver la aplicación de portal asociada en Azure Active Directory. El nombre de esta aplicación será Microsoft CRM Portal y el ID de portal está en el campo **URI de identificador de aplicación** de la aplicación de Azure Active Directory. La persona que aprovisiona el portal es propietaria de la aplicación. No debería eliminar o modificar esta aplicación, o podría romper la funcionalidad del portal. Debe ser propietario de la aplicación para administrar un portal desde el centro de administración de portal.

## <a name="authentication-key"></a>Clave de autenticación

Para que un portal se conecte con Dynamics 365 mediante una aplicación de Azure Active Directory, requiere una clave de autenticación con conexión con la aplicación de Azure Active Directory. Esta clave se genera al proporcionar un portal y la parte pública de esta clave se carga automáticamente en la aplicación de Azure Active Directory.

> [!IMPORTANT]
> La clave de autenticación expirará en dos años. Debe renovarse cada dos años para asegurarse de que su portal continúe conectándose a la organización de Dynamics 365. Si no actualiza la clave, el portal dejará de funcionar.  

### <a name="authentication-key-details"></a>Detalles clave de autenticación

Los detalles de una clave de autenticación se muestran en el centro de administración del portal y el portal.

**Centro de administración del portal**

1. Abra [Centro de administración de Portales de PowerApps](admin-overview.md).

2. Seleccione **Administración de la clave de autenticación del portal**. La clave de autenticación se muestra junto con su fecha de expiración y la huella.

   > [!div class=mx-imgBorder]
   > ![Detalles de clave de autenticación en el centro de administración del portal](../media/manage-auth-key.png "Detalles de clave de autenticación en el centro de administración del portal")

**Portal**

1. Inicie sesión en el portal como administrador.

2. Desplácese a la dirección URL <ruta_portal>/_services/about. Se muestra la fecha de finalización de la clave de autenticación. 

   > [!div class=mx-imgBorder]
   > ![Página de servicio de portal](../media/portal-services-page.png "página de servicio de Portal")

> [!NOTE]
> Para ver información de la clave de autenticación, debe iniciar sesión en el portal de en la misma sesión del explorador y debe tener permiso de acceso a todo el sitio Web.

### <a name="authentication-key-expiration-notification"></a>Notificación de la caducidad de claves de autenticación

Antes de que la clave de autenticación caduque, recibirá una notificación por correo electrónico, el centro de administración del Portal y el portal.

**Correo electrónico**

Se enviará un correo electrónico a las personas que se han registrado para recibir una notificación por correo electrónico para la organización conectada a su portal. Para obtener más información sobre cómo registrarse para recibir una notificación por correo electrónico: [administrar notificaciones por correo electrónico para administradores](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/manage-email-notifications)

Se envían notificaciones por correo electrónico en los siguientes intervalos: 
- 90 días 
- 60 días 
- 30 días 
- 15 días 
- 7 días 
- 6 días 
- 5 días 
- 4 días 
- 3 días 
- 2 días 
- 1 día 
- 12 horas 
- 6 horas 
- 3 horas

También recibirá una notificación cuando la clave expire, cada día, hasta que haya pasado 1 semana desde la expiración de la clave.

> [!NOTE]
> - Los intervalos se calculan en UTC a partir de la fecha de expiración de la clave.
> - No se garantiza que el correo electrónico se envíe exactamente en los intervalos indicados más arriba. La notificación por correo electrónico puede retrasarse o perderse. Asegúrese de comprobar también la fecha de expiración de la clave en línea.

**Centro de administración del portal**

Se muestra un mensaje sobre la expiración de la clave en la parte superior de la página.

> [!div class=mx-imgBorder]
> ![Notificación de clave de autenticación en el centro de administración del portal](../media/portal-admin-center-auth-notif.png "Notificación de clave de autenticación en el centro de administración del portal")

**Portal**

Cuando vaya a la dirección URL <ruta_portal>/_services/about, se muestra una notificación sobre la expiración de la clave en la parte inferior de la página.

> [!NOTE]
> Debe iniciar sesión en su portal de en la misma sesión del explorador y debe tener asignado permiso de acceso a todo el sitio Web.

> [!div class=mx-imgBorder]
> ![Notificación de clave de autenticación en el portal](../media/portal-service-page-auth-notif.png "Notificación de clave de autenticación en el portal")

## <a name="renew-portal-authentication-key"></a>Renovación de la clave de autenticación del portal

Debe renovar la clave cada dos años para asegurarse de que su portal pueda conectarse a la organización de Dynamics 365.

> [!NOTE]
> Para renovar la clave, debe tener permisos para administrar su portal.

1. Abra [Centro de administración de Portales de PowerApps](admin-overview.md).

2. Seleccione **Administración de la clave de autenticación del portal**. La clave de autenticación se muestra junto con su fecha de expiración y la huella.

    > [!div class=mx-imgBorder]
    > ![Administrar la clave de autenticación del portal](../media/manage-portal-auth-key.png "Administrar la clave de autenticación del portal")

3. Seleccione **Clave de actualización**.

4. Seleccione **Actualizar** en el mensaje. Se inicia el proceso de actualización, y se muestra un mensaje.

> [!NOTE]
> - Mientras este proceso se ejecuta en segundo plano, el portal se reiniciará una vez.
> - Cuando actualiza una clave, esta se actualiza para dos años.
> - Este proceso tardará entre cinco y siete minutos.

### <a name="troubleshooting"></a>Solución de problemas

Si se produce un error en la actualización de clave, se muestra un mensaje de error junto con la acción siguiente:

- **Reintentar la actualización de la clave de autenticación**. Esta acción le permite reiniciar el proceso de actualización de la clave de autenticación del portal. Si la actualización da un error varias veces, póngase en contacto con el soporte técnico de Microsoft.

    > [!div class=mx-imgBorder]
    > ![Reintentar la actualización de clave de autenticación del portal](../media/retry-auth-key-update.png "Reintentar la actualización de clave de autenticación del portal")