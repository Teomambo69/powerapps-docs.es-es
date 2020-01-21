---
title: Preguntas más frecuentes | Documentos de Microsoft
description: Preguntas más frecuentes en portales de Power Apps.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 12/27/2019
ms.author: shjais
ms.reviewer: tapanm
ms.openlocfilehash: 35f68ef861ac8908e1eb9227df6768b7a2c2c9f3
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934126"
---
# <a name="power-apps-portals-faq"></a>Preguntas más frecuentes sobre portales de Power Apps

Hemos recopilado una lista de preguntas frecuentes con respuestas breves para que obtenga la información que necesita con rapidez.

## <a name="general"></a>General

### <a name="when-is-an-add-on-portal-in-suspended-state"></a>¿Cuándo está un portal de complementos en estado suspendido?

Portal [aprovisionado mediante un plan de complementos del portal](provision-portal-add-on.md) adquirido antes de que se suspenda al final de la expiración. Este periodo de expiración es de 30 días para portales de prueba, mientras que puede variar para un portal de complementos en producción con una licencia comprada. El portal de prueba suspendido se elimina después de 7 días, mientras que el periodo de suspensión puede variar para el portal de producción. Para obtener más detalles, lea el [ciclo de vida del portal](./admin/portal-lifecycle.md#considerations-for-add-on-portals) para portales de complementos.

### <a name="how-do-i-redirect-a-user-to-a-default-page-after-signing-in"></a>¿Cómo redirijo un usuario a una página predeterminada después de firmar?

Puede configurar un portal para redirigir un usuario a una página predeterminada una vez inicie sesión. Para lograr esta funcionalidad, puede incluir un código JavaScript en la plantilla web principal.

Por ejemplo, si desea redirigir a todos los usuarios a la página de los foros después de iniciar sesión, puede incluir un código JavaScript en la plantilla web principal de la siguiente manera:

```xml
{% if user %}
//if any user logs in
<script>
  window.location.href='./forums/'
</script>
{% else %}
//Home web page code, if you don't want to display the page when the user is being redirected
{% endif %}
//Home web page code, if you want to display the page when the user is being redirected
```

Para obtener más información sobre cómo trabajar con plantillas líquidas, consulte [Trabajar con plantillas líquidas](liquid/liquid-overview.md).

### <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>Recibo un error de que sólo un portal pueda ser creado.

Actualmente, puede crear solo un portal de cada tipo en un entorno por idioma. Si intenta crear más de un portal, verá un mensaje de error como el siguiente:

> [!div class=mx-imgBorder]
> ![Error de portales máximos creados](media/portal-max-error.png "Error de portales máximos creados")

Para crear más portales, debe crear un nuevo entorno mediante el vínculo **crear nuevo entorno** en el mensaje de error. Para obtener más información sobre crear un portal, consulte [Crear un portal](create-portal.md).

### <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>Recibo un error de que no puedo eliminar mi portal.

Si no tiene suficientes privilegios para eliminar un portal, verá un error como el siguiente:

> [!div class=mx-imgBorder]
> ![Error de eliminar portal](media/portal-delete-error.png "Error de eliminar portal")

Para obtener información sobre eliminar un portal y los privilegios necesarios, vea [Eliminar un portal](manage-existing-portals.md#delete).

### <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>Recibo un error de que no puedo crear un portal.

Si no tiene suficientes privilegios para crear un portal en un entorno, verá un error como el siguiente:

> [!div class=mx-imgBorder]
> ![Error de crear portal](media/portal-create-error.png "Error de crear portal")

Para obtener información sobre crear un portal y los privilegios necesarios, vea [Crear un portal](create-portal.md).

### <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>Recibo el mensaje: “Sus datos no están listos”.

Algunas veces la creación de la base de datos puede tardar un tiempo y el estado correcto puede no reflejarse en la página principal. En este caso verá el mensaje siguiente:

> [!div class=mx-imgBorder]
> ![Datos no preparados](media/data-not-ready.png "Datos no preparados")

Si sigue recibiendo el mensaje de crear base de datos o los datos no están listos, puede intentar actualizar la página principal de Power Apps antes de seleccionar la ventana **Portal en blanco**.

### <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>Recibo un error de que no tengo los permisos necesarios para crear aplicaciones de Azure Active Directory.

Al crear un portal, el portal como nueva aplicación se registra en Azure Active Directory asociado al inquilino. Si no tiene suficientes privilegios para registrar una aplicación con el inquilino de Azure Active Directory, verá un error como el siguiente:

> [!div class=mx-imgBorder]
> ![Error de Azure Active Directory](media/azure-ad-error.png "Error de Azure Active Directory")

Para crear y registrar aplicaciones en Azure Active Directory, debe ponerse en contacto con el administrador de inquilinos para activar la configuración **Registros de aplicación** para su inquilino. Para obtener información, consulte [Permisos requeridos](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions).

### <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>Recibo un error de que la creación del portal es bloqueada en este inquilino por el administrador global

Si la creación del portal está bloqueada en un inquilino por el administrador global, verá un error como el siguiente:

> [!div class=mx-imgBorder]
> ![Error de bloqueo de creación de portal](media/portal-create-blocked-error.png "Error de bloqueo de creación de portal")

Debe ponerse en contacto con el administrador global para habilitar la creación de portales por no administradores.

Si usted es un administrador global, debe deshabilitar el valor del nivel de inquilino de `disablePortalsCreationByNonAdminUsers` con PowerShell. Ejecute el siguiente comando en una ventana de PowerShell (ejecute PowerShell como administrador).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

Más información: [Deshabilitar creación de portal en un inquilino](create-portal.md#disable-portal-creation-in-a-tenant)

### <a name="im-getting-an-error-that-i-dont-have-appropriate-license-to-access-this-website"></a>Estoy obteniendo un error de que no tengo licencia adecuada para obtener acceso a este sitio web.

Los usuarios internos de una organización que usan portales para tener acceso a páginas autenticadas requieren que haya licencias asignadas al entorno al que esté conectado un portal. Puede leer más acerca de los derechos de usuario para los portales para usuarios internos [aquí](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-clarify-the-use-rights-to-portals-for-internal-users). Cuando un entorno no tiene licencias asignadas, los usuarios internos recibirán un error como el siguiente:

> [!div class=mx-imgBorder]
> ![Error de inicio de sesión en portal](media/portal-login-error.png "Error de inicio de sesión en portal")

## <a name="licensing-and-provisioning"></a>Licencias y aprovisionamiento

### <a name="how-do-i-get-a-portal-subscription"></a>¿Cómo obtengo una suscripción al portal?

[Portales de Power Apps](overview.md) están disponibles ahora completamente independientes en Power Apps. Ya no tiene que adquirir una licencia para aprovisionar un portal. El acceso del usuario al portal requiere una licencia según el tipo de persona. Lea más detalles en [Preguntas más frecuentes sobre licencias de portales de Power Apps](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-power-apps-portals-licensing).

### <a name="how-do-i-change-the-audience-and-type-of-a-portal-after-it-is-provisioned"></a>¿Cómo cambio el público y el tipo de portal después de que se aprovisiona?

Una vez que haya proporcionado un portal, se deshabilita la opción de cambiar el público del portal.

Sin embargo, puede cambiar el público y el tipo de portal después de que sea aprovisionado mediante los pasos en [Cambie la instancia, la audiencia, o el tipo de portal de Dynamics 365](admin/change-dynamics-instance.md).

> [!NOTE]
> - Se recomienda restablecer y aprovisionar su portal nuevamente para cambiar la audiencia, el tipo de portal, la organización, etc. Más información: [Restaurar un portal](admin/reset-portal.md)
> - Cambiar la instancia de Dynamics 365 solo ser aplica a los portales aprovisionados con los complementos de portal más antiguos.

### <a name="how-do-i-change-the-base-url-of-a-portal-after-it-is-provisioned"></a>¿Cómo puedo cambiar la dirección URL base de un portal después de que se aprovisione?

Puede cambiar la dirección URL base de un portal después de que sea aprovisionado mediante los pasos en [Cambiar la dirección URL base de un portal](admin/change-base-url.md).

### <a name="how-do-i-delete-a-portal-completely-after-it-is-provisioned"></a>¿Cómo elimino un portal completamente después de que esté aprovisionado?

Los portales constan de los componentes siguientes:

- **Host del sitio web del portal**: el host del sitio web del portal es el código de portal que forma el verdadero sitio web.

- **Soluciones de portal**: las soluciones que están instaladas en el entorno de Common Data Service y que contienen las entidades de metadatos para cualquier portal.

Para eliminar un portal completamente se requiere eliminar el host del sitio web del portal así como desinstalar soluciones del entorno de Common Data Service.

Para restaurar el host de portal, siga los pasos en [Restaure un portal](admin/reset-portal.md). Es importante observar que el restablecimiento del host de un portal no afecta a la configuración realizada en su entorno de Common Data Service.

Para eliminar soluciones de portal, tendrá que eliminar soluciones de la interfaz de usuario del explorador de soluciones de Dynamics 365. El pedido en el que las soluciones de portal se deben desinstalar aparece en [Desinstalar soluciones de portal](https://community.dynamics.com/365/b/dynamics365portalssupport/archive/2017/02/27/portal-troubleshooting-part-three-uninstalling-portal-solutions).

## <a name="common-data-service-environment-lifecycle"></a>Ciclo de vida del entorno de Common Data Service

### <a name="we-recently-moved-our-common-data-service-environment-from-one-geolocation-or-tenant-to-another-how-do-we-handle-portals-connected-to-our-organization"></a>Movimos recientemente nuestro entorno de Common Data Service desde una geolocalización o inquilino a otros. ¿Cómo manejamos los portales conectados a nuestra organización?

Cuando mueva su entorno de Common Data Service desde una geolocalización o el inquilino a otro, los portales asociados con la organización no se desplazarán automáticamente. Además, ya que su organización se ha movido, el portal asociada a la organización no funcionará y lanzará un error en inicio.

Para asociar el portal de nuevo para las organizaciones relevantes:

1. Restaure el portal existente hospedado desde la geolocalización o inquilinos existentes mediante los pasos en [Restaure un portal](admin/reset-portal.md). Esto eliminará los recursos de portal asociados y la dirección URL de portal no será accesible después de que la operación se complete.

2. Una vez que se restablece el portal existente, vaya al nuevo inquilino (o a la nueva geolocalización de inquilino existente) y aprovisione allí un portal disponible.

### <a name="after-restoring-a-common-data-service-environment-from-an-old-backup-the-portal-connected-to-the-organization-is-not-working-how-do-we-fix-it"></a>Después de restaurar un entorno de Common Data Service desde una antigua copia de seguridad, el portal conectado a la organización no está funcionando. ¿Cómo lo corregimos?

Cuando se restaura un entorno de Common Data Service a partir de una copia de seguridad, varios cambios realizados en su organización pueden interrumpir la conexión del portal con la organización. Para solucionar ese problema:

- Si el identificador de la organización es el mismo después de la operación de restauración y las soluciones de portal también están disponibles:

1. Abra [Centro de administración de Portales de Power Apps](admin/admin-overview.md).
2. Vaya a la pestaña **Detalles del portal**.
3. En la lista desplegable **Estado de portal** , elija **Desconectado**.
4. Seleccione **Actualizar**. 
5. Una vez completada la operación de actualización, establezca la lista desplegable **Estado de portal** en **Activador** y después seleccione **Actualizar**.

  Su portal se reiniciará y se creará de nuevo una conexión con la organización.

- Si el identificador de la organización es diferente después de la operación de restauración o las soluciones de portal se eliminen de la organización:

  - En este caso, es mejor restaurar el portal mediante los pasos en [Restaure un portal](admin/reset-portal.md) y después reaprovisionarlo.

### <a name="we-recently-changed-the-url-of-our-common-data-service-environment-and-our-portal-stopped-working-how-do-we-fix-it"></a>Cambiamos recientemente la dirección URL del entorno de Common Data Service y nuestro portal ha dejado de funcionar. ¿Cómo lo corregimos?

Cuando cambia la dirección URL de su entorno de Common Data Service, el portal dejarán de funcionar porque ya no puede identificar la dirección URL del entorno de Common Data Service. Para solucionar ese problema:

1. Abra [Centro de administración de Portales de Power Apps](admin/admin-overview.md).
2. Vaya a **Acciones de portal** > **Actualizar dirección URL de Dynamics 365**.
3. Siga las instrucciones del asistente.

Su portal se reiniciará y volverá a funcionar.

## <a name="debugging-and-fixing-problems"></a>Depuración y solución de problemas

### <a name="when-accessing-my-portal-i-see-a-generic-error-page-how-can-i-see-the-actual-error"></a>Al acceder a mi portal, veo una página de errores genérica. ¿Cómo puedo ver el error real?

Siempre que un error de servidor aparezca mientras intenta generar un portal, una página de errores genérica se muestra a los usuarios finales junto con la marca de tiempo y el id. de actividad de error. Los administradores de portal pueden configurar el portal para obtener los detalles reales de los errores, que son útiles para depurar y solucionar problemas. Para ver el error real:

- **Deshabilite la página de errores personalizada en el portal**: esto apagará la página de errores personalizada y le permitirá ver los campos del seguimiento de la pila completa cuando navegue por esa página. Puede deshabilitar el error personalizado mediante los pasos en [Deshabilitar error personalizado](admin/view-portal-error-log.md#disable-custom-error).

Se recomienda hacerlo solo cuando está desarrollando un portal. Una vez que el portal sea visible para los usuarios, debe habilitar los errores personalizados de nuevo. Más información: [Ver registros de error del portal](admin/view-portal-error-log.md)

- **Activar registro de diagnóstico**: esto permite que se obtengan todos los errores de portal en una cuenta de almacenamiento Azure Blob. Puede habilitar el registro de diagnóstico siguiendo los pasos en [Acceder a los registros de error del portal](admin/view-portal-error-log.md#access-portal-error-logs).

Al habilitar el registro de diagnóstico puede buscar los errores determinados que los usuarios destaquen mediante el Id. de actividad que se muestra en la página de errores genérica. El Id. de actividad se registra junto con los detalles del error y es muy útil para encontrar el problema real.

## <a name="portal-administration-and-management"></a>Administración y gestión del portal

### <a name="how-do-i-use-a-custom-login-provider-on-my-portal"></a>¿Cómo uso un proveedor de inicio de sesión personalizado en mi portal?

Los portales admiten cualquier proveedor de inicio de sesión personalizado que proporcione compatibilidad para protocolos de autenticación estándar. Admitimos los protocolos OpenIdConnect, SAML2, y WS-Federation para cualquier IDP personalizado. OAuth2 solo es compatible para un conjunto fijo de IDP conocido. Para obtener más información sobre cómo configurar una configuración IDP, consulte [Configurar autenticación del portal](configure/configure-portal-authentication.md).

### <a name="how-do-i-get-new-portal-releases-in-my-sandbox-portal-first-before-it-gets-applied-to-production"></a>¿Cómo obtengo nuevos lanzamientos de Portal en mi portal de espacio aislado antes de que se aplique a producción?

Cualquier lanzamiento de portal se realiza en dos pasos: actualización anticipada y disponibilidad general (GA). Durante la fase de actualización anticipada, solo actualizamos los portales marcados para la actualización anticipada. Para obtener un nuevo lanzamiento de portal en el entorno de espacio aislado (desarrollo o prueba), puede activar en el portal la actualización anticipada. Para obtener información sobre cómo habilitar un portal para actualización anticipada, consulte [Actualizar un portal](https://docs.microsoft.com/dynamics365/customer-engagement/portals/upgrade-portal).

### <a name="how-do-i-use-a-custom-domain-name-for-my-portal"></a>¿Cómo uso un nombre de dominio personalizado para mi portal?

Puede permitir que el portal use un nombre de dominio personalizado en lugar del nombre de dominio `microsoftcrmportals.com` estándar. Más información: [Vincular su portal con un dominio personalizado](admin/add-custom-domain.md).

## <a name="portal-checker"></a>Comprobador del portal

### <a name="portal-does-not-load-and-displays-a-generic-error-page-server-error-in--application"></a>El portal no se carga y muestra una página de errores genérica (error de servidor en la aplicación ”/”) 

Este problema se puede producir por una variedad de razones como cuando un portal no se puede conectar al entorno de Common Data Service subyacente, el entorno de Common Data Service no existe o su dirección URL ha cambiado, cuando la solicitud al entorno de Common Data Service ha agotado el tiempo de espera, etc. Al ejecutar la herramienta del comprobador del portal, esta intentará determinar la razón exacta y le señalará la mitigación correcta. 

A continuación se proporciona una lista de las razones más frecuentes y de los pasos de mitigación correspondientes:

#### <a name="url-of-the-connected-common-data-service-environment-has-changed"></a>La dirección URL del entorno Common Data Service conectado ha cambiado 

Esto ocurre cuando un usuario cambia la dirección URL del entorno de Common Data Service después de que el portal se aprovisione con la organización. Para corregir este problema, actualice la dirección URL de Microsoft Dynamics 365:

1. Abra [Centro de administración de Portales de Power Apps](admin/admin-overview.md).
2. Vaya a **Acciones de portal** > **Actualizar dirección URL de Dynamics 365**. Una vez que esta acción se ejecute correctamente, se actualizará la dirección URL del entorno de Common Data Service y el portal empezará a trabajar.

#### <a name="common-data-service-environment-connected-to-your-portal-is-in-administration-mode"></a>El entorno de Common Data Service conectado a su portal está en modo de administración.

Este problema se produce cuando el entorno de Common Data Service se pone en modo de administración ya sea cuando se cambia la organización de la producción al modo de espacio aislado o manualmente mediante un administrador de la organización.

Si esta es la causa, puede deshabilitar el modo de administración realizando las acciones que figuran [aquí](https://docs.microsoft.com/dynamics365/admin/manage-sandbox-instances#administration-mode). Una vez que se haya deshabilitado el modo de administración, el portal funcionará correctamente.

#### <a name="authentication-connection-between-common-data-service-environment-and-portal-is-broken"></a>La conexión de autenticación entre el entorno de Common Data Service y el portal está rota.

Este problema ocurre cuando la conexión de autenticación entre la organización de Dynamics 365 y el portal se rompe porque el entorno de Common Data Service se ha restablecido a partir de una copia de seguridad o se ha eliminado y vuelto a crear a partir de una copia de seguridad. Para solucionar ese problema:

1. Abra [Centro de administración de Portales de Power Apps](admin/admin-overview.md).
2. En la pestaña **Detalles del portal** , seleccione **Desactivar** en la lista **Estado del portal**.
3. Seleccione **Actualizar**.
4. Seleccione **Activar**, en la lista **Estado del portal**.
5. Seleccione **Actualizar**. El portal se reinicia y podrá crear una conexión de autenticación.

Sin embargo, en determinadas situaciones especialmente si el identificador de la organización ha cambiado después de la operación de restauración (o si se ha reaprovisionado la organización), estos pasos de la mitigación no funcionarán. En estas situaciones, puede reinicializar y reaprovisionar el portal con la misma instancia. Para obtener información sobre cómo restaurar un portal, consulte [Restablecer un portal](admin/reset-portal.md).

#### <a name="request-to-common-data-service-environment-has-timed-out"></a>La solicitud al entorno de Common Data Service ha agotado el tiempo de espera

Este problema por lo general es un problema transitorio que puede ocurrir si las solicitudes de API al entorno de Common Data Service han agotado el tiempo de espera. Este problema se mitigará automáticamente una vez que las solicitudes de API empiecen a funcionar. Para mitigar este problema, también puede intentar reiniciar el portal:

1. Abra [Centro de administración de Portales de Power Apps](admin/admin-overview.md).
2. Vaya a **Acciones del portal** > **Reiniciar**.

Si no funciona reiniciar el portal y el problema se produce durante un tiempo considerable, póngase en contacto con el Soporte técnico de Microsoft para obtener asistencia.

#### <a name="website-binding-not-found"></a>No se encuentra el enlace de sitio web

Este problema se produce cuando los registros de enlace de la página web para el portal se eliminan del entorno subyacente de Common Data Service y el portal no puede crear el enlace automáticamente. Para solucionar ese problema:

1. Abra la aplicación [Administración del portal](configure/configure-portal.md).
2. Vaya a **Portales** > **Enlaces a sitios web**.
3. Elimine todos los registros de enlace de la página web que señalan a su portal. El campo **Nombre de sitio** ayuda a identificar los registros de enlace de la página web de su portal.
4. Tras eliminar todos los registros de enlace de la página web, reinicie el portal.

Una vez que complete los pasos mencionados, el portal se reiniciará y reconstruirá el registro de enlace de la página web automáticamente.

Sin embargo, hay situaciones en las que el portal no podrá volver a crear el registro de enlace de la página web automáticamente cuando el GUID del registro de la página web disponible en su instancia sea diferente del que se ha creado durante la instalación predeterminada del portal. En este caso, lleve a cabo los pasos siguientes:

1. Elimine todos los registros de enlace de la página web que pertenezcan a su portal.
2. Cree un registro de enlace de la página web manualmente con los siguientes valores:
  - **Nombre**: Puede ser cualquier cadena
  - **Página web**: Seleccione el registro de la página web que desea que se genere en el portal
  - **Nombre de sitio**: Escriba el nombre de host del portal, por ejemplo, Dirección URL de portal sin https:// al principio. Si el portal usa un nombre de dominio personalizado, use aquí el nombre de dominio personalizado.
  - Deje el resto de los campos en blanco.
3. Una vez que se haya vuelto a crear el registro de enlace de la página web, reinicie el portal desde el centro de administración de portales de Power Apps.

#### <a name="an-unexpected-error-has-occurred-while-trying-to-connect-to-your-common-data-service-environment"></a>Se produjo un error inesperado al intentar conectarse a su entorno de Common Data Service

Esta situación puede surgir debido a algún problema inesperado. Para mitigar este caso, puede intentar restablecer o reaprovisionar el portal. Para obtener información sobre cómo restaurar un portal, consulte [Restablecer un portal](admin/reset-portal.md).

Si el reinicio y el reaprovisionamiento del portal no solucionan este problema, póngase en contacto con el equipo de soporte técnico de Microsoft para obtener asistencia.

### <a name="portal-is-not-displaying-updated-data-from-common-data-service-environment"></a>El portal no muestran los datos actualizados del entorno de Common Data Service

Todos los datos visualizados en el portal se generan en la memoria caché de portal. Esta caché se actualiza siempre que los datos del entorno de Common Data Service se actualizan. Sin embargo, este proceso es asincrónico y puede tardar hasta 15 minutos. Si los cambios se realizan en la entidad de metadatos del portal, por ejemplo, páginas web, archivos web, fragmentos de contenido, valor del sitio, etc., se aconseja borrar manualmente la caché o reiniciar el portal desde el centro de administración de portales de Power Apps. Para obtener información sobre cómo borrar la caché, consulte [Borrar la memoria caché del servidor para un portal](admin/clear-server-side-cache.md). 

Sin embargo, si ve datos antiguos durante mucho tiempo en entidades de metados que no son del portal, puede deberse a la variedad de problemas que aparecen a continuación:

#### <a name="entities-not-enabled-for-cache-invalidation"></a>Algunas entidades no tienen habilitada la invalidación de caché

Si ve datos obsoletos solo para determinadas entidades y no para todo, esto puede ser debido a que los metadatos de seguimiento de los cambios no están habilitados en esa entidad específica.

Si ejecuta la herramienta de comprobación del portal (realización propia de diagnóstico), esta mostrará el código de tipo de todas las entidades a las que se hace referencia en el portal en formularios de entidades o en listas de entidades y no están habilitados para el seguimiento de cambios. Examine los metadatos mediante los pasos a los que se hace referencia en [Exploración de los metadatos de su organización](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/browse-your-metadata)

Si tiene problemas de datos obsoletos en una de estas entidades, puede habilitar el seguimiento de cambios mediante el centro de administración de los portales de Power Apps. UI o API de Dynamics 365. Más información: [Habilitar el seguimiento de cambios de una entidad](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/use-change-tracking-synchronize-data-external-systems#enable-change-tracking-for-an-entity)

#### <a name="organization-not-enabled-for-change-tracking"></a>Organización no habilitada para el seguimiento de cambios

Aparte de que cada entidad está habilitada para el seguimiento de cambios, las organizaciones en su conjunto también tienen que ser habilitadas para el seguimiento de cambios. Una organización está habilitada para el seguimiento de cambios cuando se envía una solicitud de aprovisionamiento de portal. No obstante, esto puede interrumpirse si se restaura una organización desde una antigua base de datos o reiniciar. Para solucionar ese problema:

1. Abra [Centro de administración de Portales de Power Apps](admin/admin-overview.md).
2. En la pestaña **Detalles del portal** , seleccione **Desactivar** en la lista **Estado del portal**.
3. Seleccione **Actualizar**.
4. Seleccione **Activar**, en la lista **Estado del portal**.
5. Seleccione **Actualizar**. El portal se reinicia y podrá crear una conexión de autenticación.

### <a name="performance-best-practices"></a>Prácticas recomendadas de rendimiento

Los problemas de rendimiento en portales se pueden producir por una variedad de problemas de configuración. Todas las plantillas de portal listas para usar se prueban en diversas condiciones y configuraciones de carga que pueden afectar al rendimiento del portal. Abajo tiene la lista de configuraciones de portal comunes que pueden llevar a tener problemas de rendimiento en el portal.

La herramienta de comprobador del portal (autodiagnóstico) también señalará estos problemas consultando la configuración de portal.

#### <a name="web-page-tracking-enabled"></a>Seguimiento de páginas web habilitado

Habilitar una página web de portal para el seguimiento de páginas puede llevar a generar problemas de rendimiento en el portal. Esta funcionalidad se ha eliminado desde el lanzamiento de enero de 2018 de los portales de Dynamics 365. Más información: [Capacidades de los portales para Dynamics 365: Características obsoletas](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/)

La herramienta del comprobador del portal mostrará una lista de todas las páginas web (página raíz y de contenido) que están habilitadas para el seguimiento de páginas. Estas páginas deben ser deshabilitadas siguiendo estos pasos:

1. Abra la aplicación [Administración del portal](configure/configure-portal.md).
2. Vaya a Búsqueda avanzada.
3. Busque todas las páginas web donde el campo **Habilitar el seguimiento (obsoleto)** esté habilitado (valor establecido en Sí).
4. Edite masivamente todas las páginas y establezca este campo en **No**.

Como alternativa, también puede ir a cada página que figura en el resultado del comprobador del portal y establecer el valor del campo **Habilitar el seguimiento (obsoleto)** en **No**. Es importante comprender que si se encuentra en la solución de portales de Dynamics 365, versión 9.x, este campo no aparecerá en el formulario y es posible que deba agregarlo al formulario primero. 

#### <a name="web-file-tracking-enabled"></a>Seguimiento de archivos web habilitado

Habilitar un archivo web de portal para el seguimiento de páginas puede llevar a generar problemas de rendimiento en el portal. Esta funcionalidad se ha eliminado desde el lanzamiento de enero de 2018 de los portales de Dynamics 365. Más información: [Capacidades de los portales para Dynamics 365: Características obsoletas](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/)

La herramienta del comprobador del portal mostrará una lista de todos los archivos web que están habilitados para el seguimiento de páginas. Estos archivos deben ser deshabilitados siguiendo estos pasos:

1. Abra la aplicación [Administración del portal](configure/configure-portal.md).
2. Vaya a Búsqueda avanzada.
3. Busque todos los archivos web donde el campo **Habilitar el seguimiento (obsoleto)** esté habilitado (valor establecido en Sí).
4. Edite masivamente todos los registros y establezca este campo en **No**.

Como alternativa, también puede ir a cada archivo que figura en el resultado del comprobador del portal y establecer el valor del campo **Habilitar el seguimiento (obsoleto)** en **No**. Es importante comprender que si se encuentra en la solución de portal versión 9.x, este campo no aparecerá en el formulario y es posible que deba agregarlo al formulario primero. 

#### <a name="login-tracking-enabled"></a>El seguimiento de inicio de sesión está habilitado

Habilitar el seguimiento del inicio de sesión de un portal puede llevar a generar problemas de rendimiento en el portal. Esta funcionalidad se ha eliminado desde el lanzamiento de enero de 2018 de los portales de Dynamics 365. Más información: [Capacidades de los portales para Dynamics 365: Características obsoletas](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/)

La herramienta del comprobador del portal comprobará si el seguimiento de inicio de sesión está habilitado para el portal y mostrará una comprobación fallada si está habilitado. El seguimiento de inicio de sesión debe ser deshabilitado siguiendo estos pasos:

1.  Abra la aplicación [Administración del portal](configure/configure-portal.md).
2.  Vaya a **Portales** > **Configuraciones de sitios**.
3.  Busque la configuración del sitio llamada `Authentication/LoginTrackingEnabled`.
4.  Cambie el valor de este sitio en **Falso** o elimine el valor del sitio.
5.  Reinicie el portal. 

#### <a name="header-output-cache-is-disabled"></a>La caché de resultados de encabezado está deshabilitada.

Al deshabilitar la caché de resultados de encabezado en el portal pueden producirse problemas en el portal durante situaciones de mucha carga. Más información acerca de esta funcionalidad se encuentran en: [Habilitar el almacenamiento en caché de resultados del encabezado y el pie de página en un portal](configure/enable-header-footer-output-caching.md)

La herramienta del comprobador del portal comprobará si la caché de resultados del encabezado está deshabilitada en el portal y mostrará una comprobación fallada si está deshabilitada. Para habilitarla:

1.  Abra la aplicación [Administración del portal](configure/configure-portal.md).
2.  Vaya a **Portales** > **Configuraciones de sitios**.
3.  Busque la configuración del sitio llamada `Header/OutputCache/Enabled`.
4.  Si la configuración del sitio está disponible, cambie el valor de la configuración del sitio a **Verdadero**. Si el valor del sitio no está disponible, cree un nuevo valor de sitio con este nombre y establezca su valor en **Verdadero**.
5.  Reinicie el portal. 

#### <a name="footer-output-cache-is-disabled"></a>La caché de resultados de pie de página está deshabilitada.

Al deshabilitar la caché de resultados de pie de página en el portal pueden producirse problemas en el portal durante situaciones de mucha carga. Más información acerca de esta funcionalidad se encuentran en: [Habilitar el almacenamiento en caché de resultados del encabezado y el pie de página en un portal](configure/enable-header-footer-output-caching.md)

La herramienta del comprobador del portal comprobará si la caché de resultados del pie de página está deshabilitada en el portal y mostrará una comprobación fallada si está deshabilitada. Para habilitarla:

1.  Abra la aplicación [Administración del portal](configure/configure-portal.md).
2.  Vaya a **Portales** > **Configuraciones de sitios**.
3.  Busque la configuración del sitio llamada `Footer/OutputCache/Enabled`.
4.  Si la configuración del sitio está disponible, cambie el valor de la configuración del sitio a **Verdadero**. Si el valor del sitio no está disponible, cree un nuevo valor de sitio con este nombre y establezca su valor en **Verdadero**.
5.  Reinicie el portal. 

#### <a name="large-number-of-web-file-records"></a>Hay muchos registros de archivo web

Un portal usa la entidad de archivo web para almacenar todos los archivos estáticos que desee usar en el portal. El caso de uso principal de esta entidad es almacenar el contenido estático de la página web como CSS, JavaScript, archivos de imagen, etc. Sin embargo, tener muchos archivos de este tipo puede producir lentitud durante el inicio del portal.

La herramienta del comprobador del portal comprobará la existencia de este escenario y le proporcionará una indicación si tiene más de 500 archivos web activos en el portal. Si todos estos archivos representan contenido estático como CSS, JavaScript, archivos de imagen, etc., puede actuar de la siguiente manera para mitigar este problema.

- Use un servidor de archivos externo como el almacenamiento blob de Azure o CDN para almacenar estos archivos y haga referencia a estos archivos en las páginas adecuadas dentro de la página o en la plantilla subyacente.

- Si no puede mover los archivos fuera, asegúrese de que todos los archivos no se carguen junto con la página principal. Un archivo web se carga con la página principal si la página principal del archivo se establece en la página principal. Para evitar este escenario, puede realizar los siguientes pasos:

  1. Cree una página web ficticia sin contenido y una plantilla en blanco. Esta página se usará para crear una ruta directa a los archivos web. 
  2. Para todos los archivos web que no son necesarios en la página principal, cambie la página principal a esta página web ficticia. Una vez que haya terminado, la ruta de acceso completa al archivo web sería `Portal URL/{dummy_webpage}/{web file}`
  3. Haga referencia a su archivo web directamente en el HTML de la plantilla de página o en la plantilla web de la página donde quiera usarlo. Esto cargará el archivo a petición en la página. 

#### <a name="loading-static-resources-cssjs-asynchronously"></a>Carga de recursos estáticos (css/js) de forma asincrónica

Cuando trabaje en la implementación de portales, es importante comprender que administra completamente el HTML de la página, lo que significa que las prácticas estándar de desarrollo de web deben seguirse para asegurarse de que el rendimiento del lado cliente de la página web no queda afectado. 

Una de las causas más comunes de problemas de rendimiento en páginas web es cargar muchos recursos estáticos (css/js) de forma sincrónica en la carga de la página. La carga de forma sincrónica de un gran número de archivos de css/js puede llevar a un tiempo de procesamiento del lado de cliente largo para sus páginas web. 

En el caso de los portales, siempre que asocie un archivo web directamente a la página principal, se crea una dependencia en el código HTML generado que significa que el archivo web se carga siempre con la página principal. Si este archivo web es un archivo de css/js, sería cargará de forma sincrónica y puede retrasar el tiempo de procesamiento del lado de cliente. 

Para evitar este escenario, puede realizar los siguientes pasos: 

1. Si un archivo web no es necesario en la página principal, asegúrese de que su página principal no está definida como página principal y reuse el mecanismo descrito más arriba para cargarlo a petición.
2. Mientras carga un archivo de JavaScript a petición en cualquier página, use el atributo HTML `<async>` o`<defer>` para cargar el archivo de forma asincrónica.
3. Mientras carga un archivo CSS a petición, puede usar el atributo HTML `<preload>` (https://www.w3.org/TR/preload/) o estrategia basada en JavaScript ya que la precarga no se admite en todos los exploradores aún.

#### <a name="entity-form-lookup-configuration"></a>Configuración de búsqueda de formulario de entidad 

Habilitar una búsqueda para representarse en modo desplegable en formularios de entidad o formularios web puede consumir muchos recursos si la cantidad de registros que se muestran en el menú desplegable supera los 200 y se cambian con frecuencia. Esta opción solo debe usarse para búsquedas estáticas, como la lista de países y la lista de estados, que tienen un número limitado de registros.

Si esta opción está habilitada para búsquedas que pueden tener un gran número de registros, se ralentizará el tiempo de carga de la página web en la que está disponible el formulario de entidad. Si esta página es utilizada por muchos usuarios y se carga muchas veces, puede ralentizar todo el sitio web y los recursos del sitio web se utilizarán para representar esta página. Para estas situaciones, se debe usar la experiencia de búsqueda completa o se debe crear un control HTML personalizado que invoque un extremo AJAX (creado usando plantillas web) para obtener la apariencia deseada.

#### <a name="number-of-web-roles"></a>Número de roles web

Los roles web se utilizan en portales para habilitar el control de acceso basado en roles. Por lo general, el número de roles web en un portal es limitado, ya que también se limitaría el número de diferentes combinaciones de permisos. Si el número de roles web supera los 100 en su portal, puede causar problemas de rendimiento que pueden afectar a todas las páginas de su portal.

### <a name="an-active-home-site-marker-is-not-available-for-this-portal"></a>No hay ningún marcador de sitio Principal activo disponible para este portal

Este problema ocurre cuando el marcador del sitio **Principal** no está disponible en la configuración de su portal. Para solucionar ese problema:

1.  Abra la aplicación [Administración del portal](configure/configure-portal.md).
2.  En el panel de navegación izquierdo, seleccione **Marcadores de sitio**.
3.  Cree un nuevo marcador de sitio con los siguientes valores: 
  - **Nombre**: Principal
  - **Sitio web**: seleccione el sitio web del host de su portal.
  - **Página**: seleccione el registro de la página web que se establece como la página principal de su portal.

### <a name="the-home-site-marker-is-not-pointing-to-any-webpage"></a>El marcador de sitio Principal no apunta a ninguna página web

Este problema ocurre cuando el marcador del sitio **Principal** está disponible pero no apunta a ninguna página web. Para solucionar ese problema:

1.  Abra la aplicación [Administración del portal](configure/configure-portal.md).
2.  En el panel de navegación izquierdo, seleccione **Marcadores de sitio**.
3.  Encuentra el registro del marcador del sitio **Principal**.
4.  Actualice el campo **Página** campo para apuntar a una página de inicio activa de su portal.

### <a name="the-home-site-marker-is-pointing-to-a-deactivated-web-page"></a>El marcador de sitio Inicio apunta a una página web desactivada

Este problema ocurre cuando el marcador del sitio **Principal** está disponible pero apunta a una página web desactivada. Para solucionar ese problema:

1.  Abra la aplicación [Administración del portal](configure/configure-portal.md).
2.  En el panel de navegación izquierdo, seleccione **Marcadores de sitio**.
3.  Encuentra el registro del marcador del sitio **Principal**.
4.  Actualice el campo **Página** campo para apuntar a una página de inicio activa de su portal.

### <a name="the-home-site-marker-is-not-pointing-to-home-page-of-the-portal"></a>El marcador de sitio Inicio no apunta a la página principal del portal

Este problema ocurre cuando el marcador del sitio **Principal** está disponible pero apunta a una página web que no es una página principal de su portal. Para solucionar ese problema:

1.  Abra la aplicación [Administración del portal](configure/configure-portal.md).
2.  En el panel de navegación izquierdo, seleccione **Marcadores de sitio**.
3.  Encuentra el registro del marcador del sitio **Principal**.
4.  Actualice el campo **Página** campo para apuntar a una página de inicio activa de su portal.

### <a name="an-active-profile-site-marker-is-not-available-for-this-portal"></a>No hay ningún marcador de sitio Perfil activo disponible para este portal.

Este problema ocurre cuando el marcador del sitio **Perfil** no está disponible en la configuración de su portal. Para solucionar ese problema:

1.  Abra la aplicación [Administración del portal](configure/configure-portal.md).
2.  En el panel de navegación izquierdo, seleccione **Marcadores de sitio**.
3.  Cree un nuevo marcador de sitio con los siguientes valores: 
  - **Nombre**: Perfil
  - **Sitio web**: seleccione el sitio web del host de su portal.
  - **Página**: seleccione el registro de la página web que se establece como la página del perfil de su portal.

### <a name="the-profile-site-marker-is-not-pointing-to-any-webpage"></a>El marcador de sitio Perfil no apunta a ninguna página web.

Este problema ocurre cuando el marcador del sitio **Perfil** está disponible pero no apunta a ninguna página web. Para solucionar ese problema:

1.  Abra la aplicación [Administración del portal](configure/configure-portal.md).
2.  En el panel de navegación izquierdo, seleccione **Marcadores de sitio**.
3.  Encuentra el registro del marcador del sitio **Perfil**.
4.  Actualice el campo **Página** campo para apuntar a una página de perfil activa de su portal.

### <a name="the-profile-site-marker-is-pointing-to-a-deactivated-web-page"></a>El marcador de sitio Perfil apunta a una página web desactivada.

Este problema ocurre cuando el marcador del sitio **Perfil** está disponible pero apunta a una página web desactivada. Para solucionar ese problema:

1.  Abra la aplicación [Administración del portal](configure/configure-portal.md).
2.  En el panel de navegación izquierdo, seleccione **Marcadores de sitio**.
3.  Encuentra el registro del marcador del sitio **Perfil**.
4.  Actualice el campo **Página** campo para apuntar a una página de perfil activa de su portal.

### <a name="an-active-page-not-found-site-marker-is-not-available-for-this-portal"></a>No hay ningún marcador de sitio Página no encontrada activo disponible para este portal

Este problema ocurre cuando el marcador del sitio **Página no encontrada** no está disponible en la configuración de su portal. Para solucionar ese problema:

1.  Abra la aplicación [Administración del portal](configure/configure-portal.md).
2.  En el panel de navegación izquierdo, seleccione **Marcadores de sitio**.
3.  Cree un nuevo marcador de sitio con los siguientes valores: 
  - **Nombre**: Página no encontrada
  - **Sitio web**: seleccione el sitio web del host de su portal.
  - **Página**: seleccione el registro de la página web que se establece como la página Página no encontrada de su portal.

### <a name="the-page-not-found-site-marker-is-not-pointing-to-any-webpage"></a>El marcador de sitio Página no encontrada no apunta a ninguna página web.

Este problema ocurre cuando el marcador del sitio **Página no encontrada** está disponible pero no apunta a ninguna página web. Para solucionar ese problema:

1.  Abra la aplicación [Administración del portal](configure/configure-portal.md).
2.  En el panel de navegación izquierdo, seleccione **Marcadores de sitio**.
3.  Encuentre el registro del marcador del sitio **Página no encontrada**.
4.  Actualice el campo **Página** campo para apuntar a una página Página no encontrada activa de su portal.

### <a name="the-page-not-found-site-marker-is-pointing-to-a-deactivated-web-page"></a>El marcador de sitio Página no encontrada apunta a una página web desactivada

Este problema ocurre cuando el marcador del sitio **Página no encontrada** está disponible pero apunta a página web desactivada. Para solucionar ese problema:

1.  Abra la aplicación [Administración del portal](configure/configure-portal.md).
2.  En el panel de navegación izquierdo, seleccione **Marcadores de sitio**.
3.  Encuentre el registro del marcador del sitio **Página no encontrada**.
4.  Actualice el campo **Página** campo para apuntar a una página Página no encontrada activa de su portal.

### <a name="an-active-access-denied-site-marker-is-not-available-for-this-portal"></a>No hay ningún marcador de sitio Acceso denegado activo disponible para este portal

Este problema ocurre cuando el marcador del sitio **Acceso denegado** no está disponible en la configuración de su portal. Para solucionar ese problema:

1.  Abra la aplicación [Administración del portal](configure/configure-portal.md).
2.  En el panel de navegación izquierdo, seleccione **Marcadores de sitio**.
3.  Cree un nuevo marcador de sitio con los siguientes valores: 
  - **Nombre**: Acceso denegado
  - **Sitio web**: seleccione el sitio web del host de su portal.
  - **Página**: seleccione el registro de la página web que se establece como la página Acceso denegado de su portal.

### <a name="the-access-denied-site-marker-is-not-pointing-to-any-webpage"></a>El marcador de sitio Acceso denegado no apunta a ninguna página web.

Este problema ocurre cuando el marcador del sitio **Acceso denegado** está disponible pero no apunta a ninguna página web. Para solucionar ese problema:

1.  Abra la aplicación [Administración del portal](configure/configure-portal.md).
2.  En el panel de navegación izquierdo, seleccione **Marcadores de sitio**.
3.  Encuentra el registro del marcador del sitio **Acceso denegado**.
4.  Actualice el campo **Página** campo para apuntar a una página Acceso denegado de su portal.

### <a name="the-access-denied-site-marker-is-pointing-to-a-deactivated-web-page"></a>El marcador de sitio Acceso denegado apunta a una página web desactivada.

Este problema ocurre cuando el marcador del sitio **Acceso denegado** está disponible, pero apunta a una página web desactivada (la página raíz o página de contenido se pueden desactivar). Para solucionar ese problema:

1.  Abra la aplicación [Administración del portal](configure/configure-portal.md).
2.  En el panel de navegación izquierdo, seleccione **Marcadores de sitio**.
3.  Encuentra el registro del marcador del sitio **Acceso denegado**.
4.  Actualice el campo **Página** campo para apuntar a una página Acceso denegado de su portal.

### <a name="profile-web-form-is-not-available-for-contact-entity"></a>El formulario web de perfil no está disponible para la entidad de contacto

La página Perfil es una de las páginas comunes utilizadas en su portal para todos los problemas relacionados con el perfil. Esta página muestra un formulario que los usuarios pueden usar para actualizar su perfil. El formulario utilizado en esta página proviene del formulario principal **Página web Perfil** disponible en la entidad Contacto. Este formulario se crea en su entorno de Common Data Service cuando se aprovisiona el portal. Este error se muestra cuando el formulario web **Perfil** se elimina o deshabilita en su portal. Este formulario es obligatorio y eliminar o deshabilitar este formulario puede hacer fallar todo el sitio web y que aparezca un error de tiempo de ejecución en el portal. Este es un estado irreparable y requiere que el portal se reinstale en el entorno.

### <a name="published-state-is-not-available-for-this-website"></a>El estado Publicado no está disponible para este sitio web

Para solucionar el problema, asegúrese de que la entidad de estado de publicación **Publicado** esté disponible y activa.

### <a name="published-state-is-not-visible"></a>El estado Publicado no es visible

Para solucionar el problema, asegúrese de que la entidad de estado de publicación **Publicado** tiene la casilla de verificación **isVisible** seleccionada.

### <a name="list-of-entities-with-search-result-having-invalid-url"></a>Lista de entidades con resultados de búsqueda que tienen una dirección URL no válida

Para solucionar este problema, asegúrese de que la entidad tiene el permiso de seguridad adecuado.

### <a name="list-of-entities-with-cms-security-check-failed"></a>Lista de entidades con errores en la comprobación de seguridad de CMS

Para solucionar este problema, asegúrese de que la entidad tiene la página de búsqueda adecuada.

### <a name="web-file-is-not-active"></a>El archivo web no está activo.

Para solucionar este problema, asegúrese de que el archivo web se encuentra en estado activo.

### <a name="the-partial-url-of-web-file-is-misconfigured"></a>La dirección URL parcial del archivo web está mal configurada

Para solucionar este problema, asegúrese de que la dirección URL parcial es el nombre de archivo y que tiene Inicio como página raíz.

### <a name="web-file-doesnt-have-a-file-attachment"></a>El archivo web no contiene datos adjuntos

Para solucionar este problema, agregue el archivo CSS correspondiente a la sección de notas del archivo web.

### <a name="file-attachment-doesnt-have-content"></a>Los datos adjuntos no tienen contenido

Para solucionar este problema, agregue el archivo CSS con todo el contenido a la sección de notas del archivo web.

### <a name="mime-type-of-file-is-not-textcss"></a>El tipo MIME del archivo no es text/css

Para solucionar este problema, asegúrese de que no hay complementos ni flujos que reemplacen el tipo MIME de los archivos CSS.