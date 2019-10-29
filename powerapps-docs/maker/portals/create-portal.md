---
title: Creación de un portal en PowerApps | Microsoft Docs
description: Instrucciones para crear un portal en PowerApps.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 92ba08e47d3f0d657330ac3fcc6885626ff4a9e5
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975343"
---
# <a name="create-a-common-data-service-starter-portal"></a>Creación de un portal de inicio de Common Data Service

Con la capacidad de crear un portal en PowerApps, puede crear un sitio web para los usuarios externos e internos que les permitan interactuar con los datos almacenados en Common Data Service.

Estas son algunas ventajas de la creación de un portal:

- Dado que los datos se almacenan en Common Data Service, no es necesario crear una conexión desde PowerApps como se hace con orígenes de datos como SharePoint, aplicaciones controladas por modelos en Dynamics 365 o Salesforce. Solo necesita especificar las entidades que desea mostrar o administrar en el portal.

- Puede diseñar el portal a través de los portales WYSIWYG de portal de Azure agregando y configurando los componentes en las páginas Web.

Puede crear un portal en un entorno nuevo o en el entorno existente.

Si decide crear el portal en un entorno nuevo mediante el vínculo **crear nuevo entorno** , los requisitos previos necesarios del portal, como entidades, datos y una plantilla de portal de inicio, se instalan al crear el entorno. En este método, el portal se aprovisiona en unos minutos.

Si opta por crear el portal en un entorno existente sin requisitos previos del portal, los requisitos previos se instalarán primero y, a continuación, se creará el portal. En este método, el aprovisionamiento del portal puede tardar algún tiempo y se le notificará cuando se aprovisione el portal.

Puede crear un portal de inicio de Common Data Service o un portal de Dynamics 365 en PowerApps basado en el entorno seleccionado.

Más información sobre cómo trabajar con entornos: [trabajar con entornos y Microsoft PowerApps](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-environments)

Más información sobre las plantillas de portal disponibles: [plantillas de portal](portal-templates.md)

Para crear un portal:

1.  Inicie sesión en [PowerApps](http://web.powerapps.com).  

2.  En **crear su propia aplicación**, seleccione **portal en blanco**.

3.  Si el entorno seleccionado no contiene los requisitos previos del portal, se muestra un mensaje en el **portal desde la ventana en blanco** que le sugiere seleccionar otro entorno o crear uno nuevo.

    > [!div class=mx-imgBorder]
    > ![crear nuevo mensaje de entorno](media/create-portal-message.png "crear nuevo") mensaje de entorno

4.  Si decide continuar con el entorno actual, escriba la información necesaria en la ventana como se indica en los pasos siguientes. Si decide crear un nuevo entorno, consulte [crear nuevo entorno](#create-new-environment).

5.  En el portal, en la ventana **en blanco** , escriba un nombre para el portal y la dirección del sitio web y seleccione un idioma en la lista desplegable. Cuando haya terminado, seleccione **crear**.

    > [!div class=mx-imgBorder]
    > ![crear nuevo portal](media/create-new-portal.png "crear nuevo portal")  

Después de seleccionar **crear**, el portal comenzará el aprovisionamiento y el estado de aprovisionamiento se mostrará a través de [notificaciones](#portal-provisioning-notifications).

Si ha creado el portal en el entorno que no tiene instalados los requisitos previos del portal, el estado de aprovisionamiento también se muestra en la cuadrícula:

> [!div class=mx-imgBorder]
> ![](media/provision-progress-notif.png "Notificación de cuadrícula") de notificación de cuadrícula

Una vez que el portal se ha aprovisionado correctamente, el estado se actualiza y el portal se muestra en la cuadrícula:

> [!div class=mx-imgBorder]
> (media/recent-apps.png "Portal") ![aprovisionado del portal]aprovisionado

Para editar el portal en PowerApps Portals Studio, consulte [edición de un portal](manage-existing-portals.md#edit).

> [!NOTE]
> - Puede crear un máximo de cinco portales en un inquilino. Sin embargo, solo puede haber un portal de cada tipo creado en un entorno.
> - Si no tiene privilegios suficientes para aprovisionar un portal, se muestra un error. Debe tener el rol de administrador del sistema en Common Data Service para crear un portal. También debe tener el **modo de acceso** establecido en **lectura-escritura** en **información de licencia de acceso de cliente (cal)** en el registro de usuario.
> - Si ha adquirido un complemento de portal anterior y desea aprovisionar un portal mediante el complemento, debe ir a la página del centro de administración de **Dynamics 365** . Más información: [aprovisionamiento de un portal](https://docs.microsoft.com/en-gb/dynamics365/customer-engagement/portals/provision-portal)
> - Si ha aprovisionado un portal mediante el complemento de portal anterior, puede personalizarlo y administrarlo desde [make.powerapps.com](https://make.powerapps.com).
> - El aprovisionamiento de portales desde [make.powerapps.com](https://make.powerapps.com) no usa los complementos más antiguos del portal. Además, estos portales no aparecen en la pestaña **aplicaciones** de la página **centro de administración de Dynamics 365** .
> - No se puede crear un portal de inicio de Common Data Service desde la página del **centro de administración de Dynamics 365** .
> - Los portales de PowerApps no están disponibles en la región de Francia.

## <a name="create-new-environment"></a>Crear nuevo entorno

Siga estos pasos cuando cree un entorno con la opción proporcionada en el **portal desde la ventana en blanco** .

1.  En el panel **nuevo entorno** , escriba un nombre para el entorno y, a continuación, seleccione una región y un tipo de entorno en las listas desplegables. No se puede cambiar la región una vez creado el entorno. Cuando haya terminado, seleccione **crear entorno**.

    > [!div class=mx-imgBorder]
    > ![crear nuevo entorno](media/create-new-environment.png "crear nuevo entorno")  

2.  Una vez creado el entorno, recibirá un mensaje de confirmación en el cuadro de diálogo y se le pedirá que cree una base de datos. Seleccione **crear base de datos** para habilitar el acceso a Common Data Service.

    > [!NOTE]
    > Es posible que el mensaje para crear una base de datos no se muestre automáticamente. En este caso, debe ir al nuevo entorno y volver a seleccionar el icono **del portal en blanco** .

    > [!div class=mx-imgBorder]
    > ![nuevo entorno creado](media/new-environment-created.png "nuevo entorno creado")  

3.  Seleccione la moneda y el idioma de los datos almacenados en la base de datos. No se puede cambiar la moneda ni el lenguaje una vez creada la base de datos. Cuando haya terminado, seleccione **crear mi base de datos**. La base de datos se crea con el portal de inicio que le permite empezar a trabajar rápidamente con el contenido de ejemplo una vez aprovisionado el portal.

    > [!NOTE]
    > La opción **incluir portal de inicio** solo está disponible cuando se crea un entorno mediante la opción proporcionada en el **portal desde la ventana en blanco** . Esta opción no está disponible cuando se crea un entorno desde el centro de administración de PowerApps.

    > [!div class=mx-imgBorder]
    > ![crear nueva base de datos](media/create-new-database.png "crear nueva base") de datos 

    La creación de la base de datos puede tardar varios minutos en Common Data Service. Una vez creada la base de datos, el nuevo entorno se selecciona en la lista de entornos de la Página principal de PowerApps y se crea la aplicación de administración del portal. Esta aplicación no es el portal real sino una aplicación complementaria controlada por modelos que le permite realizar actividades de configuración avanzada. Ahora puede continuar con la creación del portal para diseñar el sitio web externo.

    > [!div class=mx-imgBorder]
    > (media/portal-mgmt-app.png "aplicación") de administración del portal de la ![aplicación administración del portal]

4. Después de crear el entorno y la base de datos, en **crear su propia aplicación**, seleccione **portal en blanco**. 

    > [!NOTE]
    > Si se crea la base de datos y sigue obteniendo el mensaje de creación de base de datos, debe actualizar la Página principal de PowerApps antes de seleccionar el icono **de portal en blanco** .


## <a name="portal-provisioning-notifications"></a>Notificaciones de aprovisionamiento del portal

Después de seleccionar **crear**, el portal comenzará el aprovisionamiento y el estado de aprovisionamiento se mostrará a través de notificaciones.

**Notificación como un sistema**

La siguiente notificación se muestra al seleccionar **crear** para aprovisionar el portal.

> [!div class=mx-imgBorder]
> (media/toast-notif.png "Notificación del sistema") de ![notificaciones del sistema] 

**Notificaciones en el panel notificaciones**

Una vez que se haya realizado correctamente la solicitud de aprovisionamiento, se mostrarán las siguientes notificaciones en el panel de **notificaciones** .

Notificación que se muestra para el aprovisionamiento en curso

> [!div class=mx-imgBorder]
> ![](media/pane-notif.png "Notificación del panel") de notificación del panel 

Notificación que se muestra para el aprovisionamiento completado correctamente

> [!div class=mx-imgBorder]
> (media/provision-complete-notif.png "Notificación de éxito de aprovisionamiento") de notificación de ![éxito]de aprovisionamiento 

Si se produce un error en el aprovisionamiento del portal, las notificaciones se muestran de manera similar.
  
**Notificaciones por correo electrónico**

Una vez que la solicitud de aprovisionamiento se haya realizado correctamente, se enviará una notificación por correo electrónico de confirmación al usuario que crea el portal. Además, se envía un correo electrónico al usuario una vez completado el aprovisionamiento del portal.

## <a name="disable-portal-creation-in-a-tenant"></a>Deshabilitar la creación del portal en un inquilino

Como administrador global, si desea deshabilitar la creación del portal en un inquilino por usuarios que no son administradores, puede hacerlo habilitando la configuración de `disablePortalsCreationByNonAdminUsers` nivel de inquilino a través de PowerShell. Para ejecutar los cmdlets de PowerShell, primero debe instalar los módulos necesarios. Para obtener información sobre la instalación de los módulos de PowerShell necesarios, vea [instalación](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-powershell#installation).

Después de instalar los módulos, ejecute el siguiente comando en una ventana de PowerShell (ejecute PowerShell como administrador).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $true }
```

Los usuarios tienen uno de los siguientes roles de Azure:

- Administrador global
- Administrador de servicios de Dynamics 365
- Administrador de servicios de plataforma de energía

Los usuarios que no tengan ninguno de los roles de Azure mencionados anteriormente se consideran no administradores.

Cuando la creación del portal esté deshabilitada en un inquilino, los usuarios que no sean administradores verán un error como se indica a continuación:

> [!div class=mx-imgBorder]
> Error de creación de portal de ![errores](media/portal-create-blocked-error.png "de creación de") portal bloqueada
