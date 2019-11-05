---
title: Administración de portales existentes en PowerApps | Microsoft Docs
description: Instrucciones para administrar un portal en PowerApps.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 82fbc5d8cafa6af13af63eaff106ea028830bd01
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541925"
---
# <a name="manage-existing-portals-in-powerapps"></a>Administración de portales existentes en PowerApps

Una vez que haya creado un portal, estará visible en la sección **aplicaciones recientes** de la Página principal de PowerApps.

> [!div class=mx-imgBorder]
> ![aplicaciones recientes](media/recent-apps.png "Aplicaciones recientes")  

Para administrar una aplicación, seleccione **más comandos** ( **...** ) para el portal y elija una acción en el menú contextual.

> [!div class=mx-imgBorder]
> ![Opciones de aplicación del portal](media/portal-app-options.png "Opciones de aplicación del portal")  

## <a name="edit"></a>Editar

Abre [PowerApps Portals Studio](portal-designer-anatomy.md) para editar el contenido y los componentes del portal.  

> [!div class=mx-imgBorder]
> ![Creador de portal](media/portal-maker.png "Creador de portal")  

## <a name="browse"></a>Examina

Abre el portal para examinar el sitio Web. Esto le ayuda a ver el portal tal y como será el aspecto de los clientes.

> [!div class=mx-imgBorder]
> ![sitio web del portal](media/portal-website.png "Sitio web del portal")  

Como alternativa, también puede abrir el portal para examinar el sitio web seleccionando **examinar sitio web** en [PowerApps portales Studio](portal-designer-anatomy.md) para ver los cambios que ha realizado en el sitio Web. El sitio web se abre en una nueva pestaña con la dirección URL del sitio Web.

## <a name="share"></a>Compartir

Comparta su portal con usuarios internos o externos. Siga los pasos mencionados en el panel **compartir este portal** .

> [!div class=mx-imgBorder]
> ![compartir portal](media/share-portal.png "Compartir portal")  

### <a name="share-with-internal-users"></a>Compartir con usuarios internos

Para compartir el portal con usuarios internos, primero debe crear un rol de seguridad y, a continuación, asignar usuarios al rol de seguridad para que puedan usar el portal.

> [!NOTE]
> Como usuario en Common Data Service, si no tiene los privilegios adecuados en las entidades del portal, es posible que vea errores como "no tiene acceso para ver soluciones en este entorno". o "no tiene acceso para ver el sitio web en este entorno". Se recomienda que esté en un rol de seguridad Administrador del sistema en la base de datos de Common Data Service correspondiente.

#### <a name="step-1-create-a-security-role"></a>Paso 1: creación de un rol de seguridad

1.  En el panel **compartir este portal** , en **crear un rol de seguridad**, seleccione **roles de seguridad**. Se muestra una lista de todos los roles de seguridad configurados.

2.  En la barra de herramientas acciones, seleccione **nuevo**.

3.  En la ventana **nuevo rol de seguridad** , escriba el nombre del rol.

4.  Establezca los privilegios para todas las entidades usadas en el portal.

5.  Cuando haya terminado de configurar el rol de seguridad, en la barra de herramientas, seleccione **Guardar y cerrar**.

Para obtener información sobre los roles de seguridad y los privilegios, consulte [roles y privilegios de seguridad](https://docs.microsoft.com/power-platform/admin/security-roles-privileges).

#### <a name="step-2-assign-users-to-the-security-role"></a>Paso 2: asignación de usuarios al rol de seguridad

1.  En el panel **compartir este portal** , en **asignar usuarios al rol de seguridad**, seleccione **usuarios**. Se muestra una lista de todos los usuarios.

2.  Seleccione el usuario al que desea asignar un rol de seguridad.

3.  Haga clic en **Administrar roles**.

    > [!NOTE]
    > Si no puede ver el botón **administrar roles** en la barra de comandos, debe cambiar el cliente estableciendo forceUCI en 0 en la dirección URL. Por ejemplo, https://&lt;org\_URL&gt;/Main.aspx? pageType = entitylist & ETN = systemuser & forceUCI = 0

4.  En el cuadro de diálogo **administrar roles de usuario** , seleccione el rol de seguridad que creó anteriormente y, a continuación, haga clic en **Aceptar**.

### <a name="share-with-external-users"></a>Compartir con usuarios externos

El portal debe funcionar de forma anónima y los usuarios externos deben tener acceso a él. Si desea probar las funcionalidades avanzadas para administrar roles y permisos para usuarios externos, vea [configurar un contacto para usarlo en un portal](configure/configure-contacts.md), [invitar a los contactos a los](configure/invite-contacts.md)portales, [crear roles web para portales](configure/create-web-roles.md), [asignar permisos de entidad. ](configure/assign-entity-permissions.md).  

## <a name="settings"></a>Configuración

Muestra la configuración del portal y permite cambiar el nombre del portal. También puede realizar acciones avanzadas, como administrar el portal a través del centro de administración de portales de PowerApps y trabajar con la configuración del sitio. La configuración proporciona vínculos a la configuración del sitio y el centro de administración de portales de PowerApps. Más información: [Administración avanzada del portal](admin/admin-overview.md) y [configuración del sitio](configure/configure-site-settings.md).  

> [!div class=mx-imgBorder]
> ![configuración del portal](media/portal-settings.png "Configuración del portal")  

## <a name="delete"></a>Elimínelos

Elimina el portal y los recursos hospedados. Cuando se elimina un portal, no se puede tener acceso a su dirección URL. La eliminación de un portal no afecta a las configuraciones del portal ni a las soluciones presentes en el entorno y permanecerán tal cual.
Debe eliminar las configuraciones del portal manualmente para quitar completamente las configuraciones de portal del entorno. Para ello, use la aplicación de administración del portal y elimine el registro del sitio web correspondiente para el portal.

> [!NOTE]
> Si no tiene privilegios suficientes para eliminar un portal, se muestra un error. Debe tener el rol de administrador del sistema para eliminar un portal. Además, debe ser el propietario de la aplicación de portal en Azure Active Directory. El usuario que crea el portal es, de forma predeterminada, el propietario y puede eliminar un portal. Para obtener información sobre cómo agregarse como propietario, vea [agregarse como propietario de la aplicación Azure ad](admin/admin-overview.md#add-yourself-as-an-owner-of-the-azure-ad-application).

## <a name="details"></a>Detalles

Muestra detalles como el propietario del portal, la fecha y hora en que se creó, se modificó por última vez y la dirección URL del portal.

> [!div class=mx-imgBorder]
> ![detalles del portal](media/portal-details.png "Detalles del portal")  

