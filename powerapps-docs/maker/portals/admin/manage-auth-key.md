---
title: Conexión de un portal a un entorno de Common Data Service | MicrosoftDocs
description: Obtenga información acerca de cómo conectar un portal a un entorno de Common Data Service y cómo renovar la clave de autenticación.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 31632f4de1834855c696baa1b4b651ed777c8abd
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977505"
---
# <a name="connect-to-a-common-data-service-environment-using-a-portal"></a>Conexión a un entorno de Common Data Service mediante un portal

Un portal se conecta a un entorno de Common Data Service mediante una aplicación Azure Active Directory. La aplicación se crea en el mismo inquilino donde se aprovisiona el portal. La aplicación se registra con el entorno de Common Data Service durante el proceso de aprovisionamiento del portal.

![Conexión de un portal con Common Data Service entorno]que(../media/connect-with-dynamics.png "conecta un portal con Common Data Service entorno")

Cada portal tiene asociada una aplicación Azure Active Directory independiente, tanto si está conectada al mismo entorno Common Data Service como si no. El proveedor de autenticación Azure Active Directory predeterminado creado para un portal usa la misma aplicación Azure Active Directory para autenticar el portal. La autorización se aplica mediante roles web asignados al usuario que accede al portal.

Puede ver la aplicación de portal asociada en Azure Active Directory. El nombre de esta aplicación será portales de Microsoft CRM y el identificador del portal se encuentra en el campo **URI de ID** . de aplicación en la aplicación Azure Active Directory. La persona que aprovisiona el portal es propietaria de esta aplicación. No debe eliminar o modificar esta aplicación, o podría interrumpir la funcionalidad del portal. Debe ser el propietario de la aplicación para administrar un portal desde el centro de administración de portales de PowerApps.

## <a name="authentication-key"></a>Clave de autenticación

Para que un portal se conecte a Common Data Service mediante una aplicación Azure Active Directory, requiere una clave de autenticación conectada a la aplicación Azure Active Directory. Esta clave se genera al aprovisionar un portal y la parte pública de esta clave se carga automáticamente en la aplicación Azure Active Directory.

> [!IMPORTANT]
> La clave de autenticación expirará en dos años. Debe renovarse cada dos años para asegurarse de que el portal seguirá conectándose al entorno de Common Data Service. Si no actualiza la clave, el portal dejará de funcionar.  

### <a name="authentication-key-details"></a>Detalles de la clave de autenticación

Los detalles de una clave de autenticación se muestran en el portal y el centro de administración de portales de PowerApps.

**Centro de administración de portales de PowerApps**

1. Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2. Seleccione **administrar clave de autenticación del portal**. La clave de autenticación se muestra junto con la fecha de expiración y la huella digital.

   > [!div class=mx-imgBorder]
   > ![Detalles de la clave de autenticación en el centro de administración portal de powerapps](../media/manage-auth-key.png "detalles de la clave de autenticación en el centro de administración portal de powerapps")

**Portal**

1. Inicie sesión en el portal como administrador.

2. Vaya a la dirección URL < portal_path >/_Services/about. Se muestra la fecha de expiración de la clave de autenticación. 

   > [!div class=mx-imgBorder]
   > Página de(../media/portal-services-page.png "servicio del portal") de ![páginas del servicio de portal]

> [!NOTE]
> Para ver la información de la clave de autenticación, debe iniciar sesión en el portal en la misma sesión del explorador y debe tener todos los permisos de acceso al sitio Web.

### <a name="authentication-key-expiration-notification"></a>Notificación de expiración de clave de autenticación

Antes de que expire la clave de autenticación, recibirá una notificación por correo electrónico, el centro de administración de portales de PowerApps y el portal.

**Email**

El correo electrónico se enviará a los usuarios que se hayan registrado para recibir notificaciones por correo electrónico de la organización conectada a su portal. Más información sobre cómo registrarse para recibir notificaciones por correo electrónico: [Administración de notificaciones por correo electrónico para administradores](https://docs.microsoft.com/dynamics365/customer-engagement/admin/manage-email-notifications)

Las notificaciones por correo electrónico se envían en los siguientes intervalos: 
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

También se le notificará después de que expire la clave cada día hasta una semana después de la expiración de la clave.

> [!NOTE]
> - Los intervalos se calculan en UTC a partir de la fecha de expiración de la clave.
> - No se garantiza que el correo electrónico esté exactamente en los intervalos indicados anteriormente. La notificación de correo electrónico se puede retrasar o perder. Asegúrese de comprobar también la fecha de expiración de la clave en línea.

**Centro de administración de portales de PowerApps**

En la parte superior de la página se muestra un mensaje sobre la expiración de la clave.

> [!div class=mx-imgBorder]
> ![Notificación de clave de autenticación en Powerapps portal de administración centro de administración](../media/portal-admin-center-auth-notif.png "notificación de clave de autenticación en powerapps Portals centro de administración")

**Portal**

Cuando navega a la dirección URL < portal_path >/_Services/about, se muestra una notificación sobre la expiración de la clave en la parte inferior de la página.

> [!NOTE]
> Debe iniciar sesión en el portal en la misma sesión del explorador y debe tener asignado el permiso de acceso a todos los sitios Web.

> [!div class=mx-imgBorder]
> ![Notificación de clave de autenticación en]la(../media/portal-service-page-auth-notif.png "notificación de clave de autenticación del portal en el portal")

## <a name="renew-portal-authentication-key"></a>Renovación de la clave de autenticación del portal

Debe renovar la clave cada dos años para asegurarse de que el portal puede conectarse al entorno de Common Data Service.

> [!NOTE]
> Para renovar la clave, debe tener permisos para administrar el portal.

1. Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2. Seleccione **administrar clave de autenticación del portal**. La clave de autenticación se muestra junto con la fecha de expiración y la huella digital.

    > [!div class=mx-imgBorder]
    > ![Administrar clave de autenticación del portal](../media/manage-portal-auth-key.png "administrar clave de autenticación del portal")

3. Seleccione **actualizar clave**.

4. Seleccione **Actualizar** en el mensaje. Se inicia el proceso de actualización y se muestra un mensaje.

> [!NOTE]
> - Aunque este proceso se ejecuta en segundo plano, el portal se reiniciará una vez.
> - Cuando se actualiza una clave, se actualiza durante dos años.
> - Este proceso tardará entre cinco y siete minutos.

### <a name="troubleshooting"></a>Solución de problemas

Si se produce un error en la actualización de la clave, se muestra un mensaje de error junto con la siguiente acción:

- **Vuelva a intentar la actualización**de la clave de autenticación. Esta acción le permite reiniciar el proceso de actualización de la clave de autenticación del portal. Si la actualización no se realiza varias veces, póngase en contacto con el soporte técnico de Microsoft.

    > [!div class=mx-imgBorder]
    > ![Reintentar]actualización de clave de autenticación del portal actualizar clave de(../media/retry-auth-key-update.png "autenticación del portal")