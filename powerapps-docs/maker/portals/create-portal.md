---
title: Crear un portal en PowerApps | Microsoft Doc
description: Instrucciones para crear un portal en PowerApps.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 10/02/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="create-a-common-data-service-starter-portal"></a>Crear un portal de inicio de Common Data Service

[!include[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Con la capacidad de crear un portal en PowerApps, puede crear una página web para usuarios externos e internos habilitándolos para interactuar con los datos almacenados en Common Data Service.

Estas son algunas ventajas de crear un portal:

- Puesto que los datos se almacenan en Common Data Service, no necesita crear una conexión de PowerApps como lo hace con orígenes de datos como SharePoint, aplicaciones basadas en modelo de Dynamics 365 o Salesforce. Debe especificar únicamente las entidades que desea mostrar o administrar en el portal.

- Puede diseñar el portal a través del diseñador de portal WYSIWYG agregando y configurando componentes en las páginas web.

Puede crear un portal en un nuevo entorno o en su entorno existente.

Si elige crear el portal en un nuevo entorno mediante el vínculo **Crear nuevo entorno**, los requisitos previos del portal necesarios como entidades, datos, y una plantilla de portal de inicio se instalan cuando se crea el entorno. En este método, el portal se aprovisiona en unos minutos.

Si elige crear el portal en un entorno existente sin requisitos previos de portal, los requisitos previos se instalan primero y después el portal se crea. En este método, el aprovisionamiento del portal puede tardar un tiempo y se le notificará cuando se aprovisione el portal.

Puede crear el portal de inicio de Common Data Service o portales de Dynamics 365 en PowerApps en función del entorno seleccionado.

Más información sobre cómo trabajar con entornos: [Trabajar con entornos y Microsoft PowerApps](https://docs.microsoft.com/en-us/powerapps/maker/canvas-apps/working-with-environments)

Más información sobre las plantillas de portal disponibles: [Plantillas de portal](portal-templates.md)

Para crear un portal:

1.  Inicie sesión en [PowerApps](http://web.powerapps.com).  

2.  En **Crear sus propias aplicaciones**, seleccione **Portal en blanco (vista previa)**.

3.  Si el entorno seleccionado no contiene requisitos previos de portal, se muestra un mensaje en la ventana **Portal en blanco (vista previa)** que le recomienda que seleccione otro entorno o cree uno.

    > [!div class=mx-imgBorder]
    > ![crear nuevo mensaje de entorno](media/create-portal-message.png "Crear nuevo mensaje de entorno")

4.  Si elige continuar con el entorno actual, especifique la información necesaria en la ventana como se menciona en los pasos siguientes. Si elige crear un nuevo entorno, consulte [Crear nuevo entorno](#create-new-environment).

5.  En la ventana **Portal en blanco (vista previa)**, escriba un nombre para el portal y la dirección de la página web, y seleccione un idioma de la lista desplegable. Cuando esté listo, seleccione **Crear**.

    > [!div class=mx-imgBorder]
    > ![crear nuevo portal](media/create-new-portal.png "Crear nuevo portal")  

Tras seleccionar **Crear**, el portal comenzará a aprovisionarse y el estado de aprovisionamiento se mostrará a través de [notificaciones](#portal-provisioning-notifications).

Si ha creado su portal en el entorno que no tiene requisitos previos de portal instalados, el estado de aprovisionamiento también se muestra en la cuadrícula:

> [!div class=mx-imgBorder]
> ![Notificación de cuadrícula](media/provision-progress-notif.png "Notificación de cuadrícula")

Después de que el portal se aprovisione correctamente, el estado se actualiza y el portal se muestra en la cuadrícula:

> [!div class=mx-imgBorder]
> ![Portal aprovisionado](media/recent-apps.png "Portal aprovisionado")

Para editar el portal en diseñador de portal, consulte [Editar un portal](manage-existing-portals.md#edit).

> [!NOTE]
> - Puede crearse un máximo de cinco portales en un inquilino. Sin embargo, solo puede haber un portal de cada tipo creado en un entorno.
> - Si no tiene suficientes privilegios para aprovisionar un portal, se muestra un error. Para ello, debe tener el rol Administrador del sistema o al menos Personalizador del sistema en Common Data Service para crear un portal. También debe tener el **Modo de acceso** establecido como **Lectura-Escritura** en **Información de licencia de acceso de cliente (CAL)** en el registro de usuario.

## <a name="create-new-environment"></a>Crear nuevo entorno

Siga estos pasos al crear un entorno mediante la opción proporcionada en la ventana **Portal en blanco (vista previa)**.

1.  En el panel **Nuevo entorno**, escriba un nombre para el entorno, y luego seleccione una región y un tipo de entorno de las listas desplegables. No puede cambiar la región una vez que se crea el entorno. Cuando esté listo, seleccione **Crear entorno**.

    > [!div class=mx-imgBorder]
    > ![crear nuevo entorno](media/create-new-environment.png "Crear nuevo entorno")  

2.  Cuando se crea el entorno, recibirá un mensaje de confirmación en el cuadro de diálogo, y se le pedirá que cree una base de datos. Seleccione **Crear base de datos** para permitir el acceso a Common Data Service.

    > [!NOTE]
    > El mensaje para crear una base de datos puede no mostrarse automáticamente. En este caso, debe ir al nuevo entorno y seleccionar la ventana **Portal en blanco** otra vez.

    > [!div class=mx-imgBorder]
    > ![nuevo entorno creado](media/new-environment-created.png "Nuevo entorno creado")  

3.  Seleccione la divisa y el idioma de los datos almacenados en la base de datos. No puede cambiar la divisa ni el idioma una vez que se cree la base de datos. Cuando esté listo, seleccione **Crear mi base de datos**. La base de datos se crea con el portal de inicio que le permite comenzar rápidamente con el contenido de ejemplo cuando se aprovisione el portal.

    > [!NOTE]
    > La opción **Incluir portal de inicio** solo está disponible cuando cree un entorno mediante la opción proporcionada en la ventana **Portal en blanco (vista previa)**. Esta opción no está disponible cuando cree un entorno desde el Centro de administración de PowerApps.

    > [!div class=mx-imgBorder]
    > ![crear nueva base de datos](media/create-new-database.png "Crear nueva base de datos") 

    Puede que tarde varios minutos en crear la base de datos en Common Data Service. Una vez que se cree la base de datos, el nuevo entorno se selecciona en la lista de entornos en la página principal de PowerApps y se crea la aplicación Administración del portal. Esta aplicación no es el portal real sino una aplicación complementaria basada en modelo que permite realizar actividades de administración avanzada. Ahora puede continuar creando el portal para diseñar la página web externa.

    > [!div class=mx-imgBorder]
    > ![[aplicación de administración del portal](media/portal-mgmt-app.png "[Aplicación de administración del portal")

4. Después de crear el entorno y la base de datos, en **Crear su propia aplicación**, seleccione **Portal en blanco (vista previa)**. 

    > [!NOTE]
    > Si se crea la base de datos y sigue recibiendo el mensaje de crear base de datos, debe actualizar la página principal de PowerApps antes de seleccionar la ventana **Portal en blanco (vista previa)**.


## <a name="portal-provisioning-notifications"></a>Notificaciones de aprovisionamiento del portal

Tras seleccionar **Crear**, el portal comenzará a aprovisionarse y el estado de aprovisionamiento se mostrará a través de notificaciones.

**Notificación del sistema**

Se muestra la notificación siguiente cuando se selecciona **Crear** para aprovisionar el portal.

> [!div class=mx-imgBorder]
> ![Notificación del sistema](media/toast-notif.png "Notificación del sistema") 

**Notificaciones en el panel Notificaciones**

Una vez que la solicitud de aprovisionamiento se realiza correctamente, las notificaciones siguientes se muestran en el panel **Notificación**.

Notificación mostrada para aprovisionamiento en curso

> [!div class=mx-imgBorder]
> ![Notificación de panel](media/pane-notif.png "Notificación de panel") 

Notificación mostrada para aprovisionamiento completado correctamente

> [!div class=mx-imgBorder]
> ![Notificación de aprovisionamiento correcto](media/provision-complete-notif.png "Notificación de aprovisionamiento correcto") 

Si el aprovisionamiento del portal produce un error, las notificaciones se muestran de forma similar.
  
## <a name="disable-portal-creation-in-a-tenant"></a>Deshabilitar creación de portal en un inquilino

Como administrador global, si desea deshabilitar la creación de portal en un inquilino por no administradores, puede hacerlo habilitando el valor del nivel de inquilino de `disablePortalsCreationByNonAdminUsers` con PowerShell. Para ejecutar los cmdlets de PowerShell, debe instalar los componentes necesarios. Para obtener información sobre instalar módulos necesarios de PowerShell, consulte [Instalación](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-powershell#installation).

Después de instalar los módulos, ejecute el comando siguiente en una ventana de PowerShell (ejecute PowerShell como administrador).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $true }
```

El administrador son los usuarios que tienen uno de los roles de Azure siguientes:

- Administrador global de 
- Administrador de servicio de Dynamics 365
- Administrador de servicios de Power Platform

Los usuarios que no tienen los roles de Azure mencionados se consideran no administradores.

Cuando la creación de portal se deshabilita en un inquilino, los usuarios no administradores verán un error de la siguiente manera:

> [!div class=mx-imgBorder]
> ![Error de bloqueo de creación de portal](media/portal-create-blocked-error.png "Error de bloqueo de creación de portal")

