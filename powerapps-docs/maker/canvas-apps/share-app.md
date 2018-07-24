---
title: Uso compartido de una aplicación | Microsoft Docs
description: Comparta su aplicación proporcionando a otros usuarios permiso para ejecutarla o modificarla
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 07/11/2018
ms.author: anneta
ms.openlocfilehash: 197eb5223c0945a7cb80d8b187aaf44c871e798c
ms.sourcegitcommit: 79a58f1b6880cbc512b64cde71a4d532cebe5bed
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/18/2018
ms.locfileid: "39137031"
---
# <a name="share-an-app-in-powerapps"></a>Compartir una aplicación en PowerApps

Después de compilar una aplicación que responde a una necesidad empresarial, especifique qué usuarios de su organización pueden ejecutar la aplicación y cuáles pueden modificarla e incluso volverla a compartir. Especifique cada usuario por nombre, o indique un grupo de seguridad en Azure Active Directory. Si todos los usuarios se beneficiarán de la aplicación, especifique que toda la organización puede ejecutarla.

> [!IMPORTANT]
> Para que una aplicación compartida funcione según lo esperado, también debe administrar los permisos para los orígenes de datos en los que se basa la aplicación, como [Common Data Service for Apps](#common-data-service-for-apps) o [Excel](share-app-data.md). Es posible que también deba compartir [otros recursos](share-app-resources.md) de los que depende la aplicación, como flujos, puertas de enlace o conexiones.

## <a name="prerequisites"></a>Requisitos previos

Para poder compartir una aplicación, debe guardarla en la nube, no de forma local, y después publicarla.

- Asigne a la aplicación un nombre descriptivo y una descripción clara, para que los usuarios sepan qué hace la aplicación y puedan encontrarla fácilmente en una lista. En el menú **Archivo** en PowerApps Studio, seleccione **Configuración de la aplicación**, especifique un nombre y después escriba o pegue una descripción.

- Siempre que realice cambios, debe guardar y volver a publicar la aplicación si desea que otros usuarios puedan verlos.

## <a name="share-an-app"></a>Compartir una aplicación

1. [Inicie sesión](https://web.powerapps.com) en PowerApps y después seleccione **Aplicaciones** cerca del borde izquierdo.

    ![Mostrar la lista de aplicaciones](./media/share-app/file-apps.png)

1. Seleccione los puntos suspensivos (...) de la aplicación que quiera compartir y después seleccione **Compartir**.

    ![Abrir la pantalla Compartir](./media/share-app/ellipsis-share.png)

1. Especifique con qué usuarios o grupos de seguridad de Azure Active Directory desea compartir la aplicación.

    > [!NOTE]
    > No puede compartir aplicaciones con un grupo de distribución de su organización o con usuarios o grupos de fuera de su organización.

    ![Especificar usuarios](./media/share-app/share-list.png)

    También se puede compartir la aplicación con toda la organización para que la puedan ejecutar, pero no podrán modificarla ni compartirla.

1. (opcional) Para ayudar a los usuarios a encontrar la aplicación, seleccione la casilla para enviarles una invitación por correo electrónico.

    La invitación contiene un vínculo que los usuarios pueden seleccionar para ejecutar la aplicación.

    - Si un usuario selecciona el vínculo en un equipo de escritorio, la aplicación se abre en [Dynamics 365](http://home.dynamics.com).
    - Si el usuario selecciona el vínculo en un dispositivo móvil, la aplicación se abre en PowerApps Mobile.

    Si concede a los usuarios permiso para modificar la aplicación, el mensaje también contiene un vínculo independiente para abrir la aplicación para su edición en PowerApps Studio.

    Independientemente de si se envía una invitación, los usuarios pueden ejecutar la aplicación desde AppSource en [Dynamics 365](http://home.dynamics.com). Los usuarios que tienen el permiso **Puede editar** también pueden editar la aplicación desde [PowerApps](http://web.powerapps.com).

1. Especifique el permiso para cada usuario o grupo de seguridad y después seleccione **Guardar**.

    - **Puede usar**: los usuarios pueden ejecutar la aplicación pero no compartirla.
    - **Puede editar**: los usuarios pueden ejecutar la aplicación, modificarla y compartir la versión personalizada con otros usuarios.

        ![Especificar permisos](./media/share-app/edit-use.png)

    Para cambiar los permisos para un usuario o un grupo de seguridad, seleccione la flecha hacia abajo situada junto al permiso que ya tiene el usuario o grupo y después especifique un permiso diferente.

    Para quitar todos los permisos de un usuario o grupo, seleccione el icono **x** de ese usuario o grupo.

## <a name="security-group-considerations"></a>Consideraciones de grupo de seguridad

- Si comparte una aplicación con un grupo de seguridad, los miembros de ese grupo y cualquiera que se una a él tendrán los permisos que especifique para dicho grupo. Cualquier persona que abandone el grupo perderá esos permisos a menos que pertenezca a un grupo diferente que tenga acceso o le otorgue permisos como usuario individual.
- Todos los miembros de un grupo de seguridad tienen los mismos permisos para una aplicación que el grupo general. Sin embargo, puede especificar mayores permisos para uno o varios miembros de ese grupo para permitirles mayor acceso. Por ejemplo, puede asignar al Grupo de seguridad A el permiso **Puede usar**, pero también asignar al Usuario B, que pertenece a ese grupo, el permiso **Puede editar**. Todos los miembros del grupo de seguridad pueden ejecutar la aplicación, pero solo el usuario B puede modificarla. Si se asigna al Grupo de seguridad A el permiso **Puede editar** y al Usuario B el permiso **Puede usar**, ese usuario puede seguir editando la aplicación.

## <a name="manage-entity-permissions"></a>Administrar permisos de entidad

### <a name="common-data-service-for-apps"></a>Common Data Service for Apps

Si crea una aplicación basada en Common Data Service for Apps, debe asegurarse de que los usuarios que vayan a ejecutarla tienen los permisos adecuados para las entidades en las que se basa la aplicación. En concreto, los usuarios deben pertenecer a un rol de seguridad que pueda realizar tareas como crear, leer, escribir o eliminar los registros relevantes. Si tiene permisos de **Administrador del sistema** o **personalizador del sistema** para la base de datos en este entorno, puede crear un rol personalizado y después agregarle usuarios.

#### <a name="create-a-security-role"></a>Crear un rol de seguridad

1. [Inicie sesión en PowerApps](https://web.powerapps.com) y asegúrese de que se encuentra en el mismo entorno que la aplicación que desea compartir.

1. En la esquina superior derecha, seleccione el icono de engranaje y después seleccione **Personalizaciones avanzadas**.

    ![Abrir el panel de personalizaciones avanzadas](media/share-app/advanced-customizations.png)

1. Seleccione el vínculo **Roles de seguridad**.

    ![Abrir roles de seguridad](media/share-app/security-roles.png)

1. En **Todos los roles**, seleccione **Nuevo** y después escriba o pegue el nombre del rol que va a crear.

    ![Crear un rol de seguridad](media/share-app/new-role.png)

1. Seleccione una o más pestañas para buscar las entidades que usa su aplicación y después seleccione los permisos que quiera conceder al rol de seguridad.

    Por ejemplo, en este gráfico se muestra que un rol de seguridad puede crear, leer, escribir y eliminar registros en la entidad Cuenta, que aparece en la pestaña **Registros principales**.

    ![Especificar permisos](media/share-app/grant-access.png)

1. Haga clic en **Guardar y cerrar**.

#### <a name="assign-a-user-to-a-role"></a>Asignar un usuario a un rol

1. Abra el panel **Personalizaciones avanzadas** como se describe el procedimiento anterior y después seleccione el vínculo **Usuarios**.

    ![Vínculo Usuarios](media/share-app/open-users.png)

1. En la esquina superior derecha, escriba o pegue el nombre del usuario al que quiera asignar a la función y después seleccione el icono de búsqueda.

    ![Búsqueda de usuarios](media/share-app/search-users.png)

1. En los resultados de búsqueda, desplace el cursor hasta el resultado que quiera y seleccione la casilla que aparece.

1. En el banner superior, seleccione **Administrar roles**.

1. En el cuadro de diálogo que aparece, seleccione las casillas para **Usuario de Common Data Service** y los roles que los usuarios necesitan para la aplicación y después seleccione **Aceptar.**

    ![Asignar un usuario a un rol](media/share-app/assign-users.png)

### <a name="common-data-service-previous-version"></a>Common Data Service (versión anterior)

Cuando comparta una aplicación basada en una versión anterior de Common Data Service, debe compartir el permiso de tiempo de ejecución para el servicio por separado. Si no tiene permiso para hacerlo, póngase en contacto con su administrador de entorno.