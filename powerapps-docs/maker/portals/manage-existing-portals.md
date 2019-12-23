---
title: Administrar portales existentes en Power Apps | Microsoft Docs
description: Instrucciones para la administración de un portal en Power Apps.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 0921e39c93b5f63a3f9a0ea038fd97389ea2b968
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2883935"
---
# <a name="manage-existing-portals-in-power-apps"></a>Administrar portales existentes en Power Apps

Cuando haya creado un portal, está visible en la sección **Aplicaciones recientes** en la página principal de Power Apps.

> [!div class=mx-imgBorder]
> ![aplicaciones recientes](media/recent-apps.png "Aplicaciones recientes")  

Para administrar una aplicación, seleccione **Más comandos** (**…**) para el portal y elija una acción en el menú contextual.

> [!div class=mx-imgBorder]
> ![opciones de aplicaciones de portal](media/portal-app-options.png "Opciones de aplicaciones de portal")  

## <a name="edit"></a>Editar

Abre [portales de Power Apps Studio](portal-designer-anatomy.md) para editar el contenido y componentes del portal.  

> [!div class=mx-imgBorder]
> ![creador de portal](media/portal-maker.png "Creador de portal")  

## <a name="browse"></a>Examinar

Abre el portal para explorar la página web. Esto ayuda a ver el portal como lo verán los clientes.

> [!div class=mx-imgBorder]
> ![sitio web del portal](media/portal-website.png "Sitio web del portal")  

Como alternativa, también puede abrir el portal para explorar la página web seleccionando **Explorar sitio web** en [portales de Power Apps Studio](portal-designer-anatomy.md) para ver los cambios que ha realizado a la página web. La página web se abre en una nueva pestaña con la dirección URL de la página web.

## <a name="share"></a>Compartir

Comparta el portal con usuarios internos o externos. Siga los pasos a los que se hace referencia en el panel **Compartir este portal**.

> [!div class=mx-imgBorder]
> ![compartir portal](media/share-portal.png "Compartir portal")  

### <a name="share-with-internal-users"></a>Compartir con usuarios internos

Para compartir el portal con usuarios internos primero debe crear un rol de seguridad y después asignar usuarios al rol de seguridad para que pueden usar el portal.

> [!NOTE]
> Como usuario en Common Data Service, si no tiene permisos apropiados en las entidades de portal, pueden aparecer errores como “No tiene acceso para ver soluciones en este entorno”. p "No tiene acceso para ver sitios web en este entorno." Se recomienda encontrarse en un rol de seguridad de Administrador del sistema en la base de datos de Common Data Service correspondiente.

#### <a name="step-1-create-a-security-role"></a>Paso 1: Crear un rol de seguridad

1.  En el panel **Compartir este portal**, en **Crear un rol de seguridad**, seleccione **Roles de seguridad**. Una lista de todos los roles de seguridad configurados se muestra.

2.  En la barra de herramientas Acciones, seleccione **Nuevo**.

3.  En la ventana **Nuevo rol de seguridad**, escriba el nombre del rol.

4.  Establezca privilegios para todas las entidades que se usan en el portal.

5.  Cuando termine de configurar el rol de seguridad, en la barra de herramientas, seleccione **Guardar y cerrar**.

Para obtener información sobre roles de seguridad y privilegios, consulte: [Roles de seguridad y privilegios](https://docs.microsoft.com/power-platform/admin/security-roles-privileges).

#### <a name="step-2-assign-users-to-the-security-role"></a>Paso 2: Asigne usuarios al rol de seguridad

1.  En el panel **Compartir este portal**, en **Asignar usuarios al rol de seguridad**, seleccione **Usuarios**. A continuación, aparecerá una lista de todos los usuarios.

2.  Seleccione el usuario al que desea asignar un rol de seguridad.

3.  Seleccione **Administrar roles**.

    > [!NOTE]
    > Si no puede ver el botón **Administrar roles** en la barra de comandos, debe cambiar el cliente estableciendo forceUCI a 0 en la dirección URL. Por ejemplo, https://&lt;org\_url&gt;/main.aspx?pagetype=entitylist&etn=systemuser&forceUCI=0

4.  En el cuadro de diálogo **Administrar roles de usuario**, seleccione el rol de seguridad que creó antes y seleccione **Aceptar**.

### <a name="share-with-external-users"></a>Compartir con usuarios externos

Su portal debe funcionar de manera anónima y debe ser accesible por los usuarios externos. Si desea probar capacidades avanzadas para administrar roles y permisos para usuarios externos, consulte [Configurar un contacto para uso en un portal](configure/configure-contacts.md), [Invitar contactos en los portales](configure/invite-contacts.md), [Crear roles web para portales](configure/create-web-roles.md), [Asignar permisos de entidad](configure/assign-entity-permissions.md).  

## <a name="settings"></a>Configuración

Muestra la configuración de portal y permite cambiar el nombre del portal. Puede realizar acciones avanzadas como administrar el portal a través del centro de administración de portales de Power Apps y trabajar con la configuración del sitio. La configuración proporciona vínculos con el Centro de administración de los portales de Power Apps y Configuración del sitio. Más información: [Administración avanzada de portal](admin/admin-overview.md) y [Configuración del sitio](configure/configure-site-settings.md).  

> [!div class=mx-imgBorder]
> ![configuración del portal](media/portal-settings.png "Configuración del portal")  

## <a name="delete"></a>Eliminar

Elimina el portal y recursos hospedados. Cuando se elimina un portal, su dirección URL deja de estar accesible. La eliminación de un portal no afecta a ninguna configuración de portal o soluciones presentes en el entorno, y permanecerán como se encuentran.
Deberá eliminar las configuraciones de portal manualmente para quitar totalmente las configuraciones de portal del entorno. Para ello, use la aplicación Administración del portal, y elimine el registro correspondiente de la página web para el portal.

> [!NOTE]
> Si no tiene suficientes privilegios para eliminar un portal, se muestra un error. Debe tener el rol de administrador del sistema para eliminar un portal. Además, debe ser el propietario de la aplicación de portal en Azure Active Directory. El usuario que creó el portal es de forma predeterminada el propietario y puede eliminar un portal. Para obtener información para agregarse a usted mismo como propietario, consulte [Agregarse a sí mismo como propietario de la aplicación Azure AD](admin/admin-overview.md#add-yourself-as-an-owner-of-the-azure-ad-application).

## <a name="details"></a>Detalles

Muestra detalles como propietario del portal, fecha y hora cuando se creó y se modificó por última vez, y la dirección URL del portal.

> [!div class=mx-imgBorder]
> ![detalles del portal](media/portal-details.png "Detalles del portal")  

