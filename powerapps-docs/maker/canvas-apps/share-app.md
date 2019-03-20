---
title: Compartir una aplicación de lienzo | Microsoft Docs
description: Compartir la aplicación de lienzo proporcionando a otros usuarios permiso para ejecutarla o modificarla
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 11/28/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 57a63ddf829e2a6c1062cad34e0f3c608d69afad
ms.sourcegitcommit: a06e3137e3cb36414f0d61825bbc687487ea6f8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2019
ms.locfileid: "57804226"
---
# <a name="share-a-canvas-app-in-powerapps"></a>Compartir una aplicación de lienzo en PowerApps

Después de compilar una aplicación que responde a una necesidad empresarial, especifique qué usuarios de su organización pueden ejecutarla y cuáles pueden modificarla e incluso volver a compartirla. Especifique cada usuario por nombre, o indique un grupo de seguridad en Azure Active Directory. Si todos los usuarios se beneficiarán de la aplicación, especifique que toda la organización puede ejecutarla.

> [!IMPORTANT]
> Para que una aplicación compartida funcione según lo esperado, también debe administrar los permisos para los orígenes de datos en los que se basa la aplicación, como [Common Data Service for Apps](#common-data-service-for-apps) o [Excel](share-app-data.md). Es posible que también deba compartir [otros recursos](share-app-resources.md) de los que depende la aplicación, como flujos, puertas de enlace o conexiones.

## <a name="prerequisites"></a>Requisitos previos

Para poder compartir una aplicación, debe guardarla en la nube, no de forma local, y después publicarla.

- Asigne a la aplicación un nombre descriptivo y una descripción clara, para que los usuarios sepan qué hace la aplicación y puedan encontrarla fácilmente en una lista. En el menú **Archivo** en PowerApps Studio, seleccione **Configuración de la aplicación**, especifique un nombre y después escriba o pegue una descripción.

- Siempre que realice cambios, debe guardar y volver a publicar la aplicación si desea que otros usuarios puedan verlos.

## <a name="share-an-app"></a>Compartir una aplicación

1. [Inicie sesión](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) en PowerApps y después seleccione **Aplicaciones** cerca del borde izquierdo.

    ![Mostrar la lista de aplicaciones](./media/share-app/file-apps.png)

1. Seleccione la aplicación que desea compartir seleccionando su icono.

    ![Seleccione una aplicación](./media/share-app/select-app.png)

1. En el encabezado, seleccione **Share**.

    ![Abrir la pantalla Compartir](./media/share-app/banner-share.png)

1. Especifique por nombre o alias de los usuarios o grupos de seguridad en Azure Active Directory con el que desea compartir la aplicación.

    - Para permitir que toda la organización ejecutar la aplicación (pero no modificarla ni compartirla), escriba **todo el mundo** en el panel de uso compartido.
    - Puede compartir una aplicación con una lista de alias, los nombres descriptivos o una combinación de ellos (por ejemplo, **Jane Doe &lt; jane.doe@contoso.com>**) si los elementos están separados por puntos y coma. Si hay más de una persona tiene el mismo nombre pero distintos alias, la primera persona se agregará a la lista. Información sobre herramientas aparece si un nombre o alias ya tiene permiso o no se puede resolver. 
    
    ![Especifique los usuarios y los copropietarios](./media/share-app/share-everyone.png)

    > [!NOTE]
    > No se puede compartir una aplicación con un grupo de distribución de su organización o con un usuario o grupo fuera de su organización.

1. Si desea permitir que aquellos con quienes comparte la aplicación para editar y compartirlo (además de ejecutarlo), seleccione el **copropietario** casilla de verificación.

    No puede conceder **copropietario** permiso para una seguridad del grupo si se [creó la aplicación desde dentro de una solución](add-app-solution.md).
    
    > [!NOTE]
    > Independientemente de los permisos, no habrá dos personas pueden editar una aplicación al mismo tiempo. Si una persona abre la aplicación para su edición, otras personas pueden ejecutarla, pero no editarlo.

1. Si la aplicación se conecta a los datos para el que los usuarios necesitan permisos de acceso, debe especificarlos.

    Por ejemplo, la aplicación puede conectarse a una entidad en una base de datos de aplicaciones de CDS. Cuando se comparte una aplicación, el panel de uso compartido le pide que administrar la seguridad de esa entidad.

    ![Establecer permisos](./media/share-app/set-permissions.png)

    Para obtener más información acerca de cómo administrar la seguridad de una entidad, vea [administrar permisos de entidad](share-app.md#manage-entity-permissions) más adelante en este tema.

1. Si desea ayudar a las personas a encontrar la aplicación, seleccione la **enviar una invitación por correo electrónico a los nuevos usuarios** casilla de verificación.

1. En la parte inferior del panel recurso compartido, seleccione **compartir**.

    Todos los usuarios con quienes ha compartido la aplicación pueden ejecutarla en PowerApps Mobile en un dispositivo móvil o en AppSource [Dynamics 365](https://home.dynamics.com) en un explorador. Pueden editar y compartir la aplicación en los copropietarios [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

    Si envía una invitación por correo electrónico, todos los usuarios con quienes ha compartido la aplicación pueden ejecutar mediante la selección de un vínculo de la invitación.

    - Si un usuario selecciona el vínculo en un dispositivo móvil, la aplicación se abre en PowerApps Mobile.
    - Si un usuario selecciona el vínculo en un equipo de escritorio, la aplicación se abre en un explorador.

    Los copropietarios que reciben una invitación obtención otro vínculo que abre la aplicación para su edición en PowerApps Studio.

Puede cambiar los permisos para un usuario o un grupo de seguridad, seleccione su nombre y, a continuación, realizar cualquiera de estos pasos:

- Para permitir que los copropietarios ejecutar la aplicación, pero ya no edición o compartirlo, desactive la **copropietario** casilla de verificación.
- Para dejar de compartir la aplicación con ese usuario o grupo, seleccione el icono de eliminación (x).

## <a name="security-group-considerations"></a>Consideraciones de grupo de seguridad

- Si comparte una aplicación con un grupo de seguridad, los miembros de ese grupo y cualquiera que se una a él tendrán los permisos que especifique para dicho grupo. Cualquier persona que abandone el grupo perderá esos permisos a menos que pertenezca a un grupo diferente que tenga acceso o le otorgue permisos como usuario individual.
- Todos los miembros de un grupo de seguridad tienen los mismos permisos para una aplicación que el grupo general. Sin embargo, puede especificar mayores permisos para uno o varios miembros de ese grupo para permitirles mayor acceso. Por ejemplo, puede otorgar permisos de grupo de seguridad A ejecutar una aplicación, pero también puede asignar el usuario B, que pertenece a ese grupo, **copropietario** permiso. Todos los miembros del grupo de seguridad pueden ejecutar la aplicación, pero solo el usuario B puede modificarla. Si asigna a un grupo de seguridad **copropietario** permiso y el usuario B permiso para ejecutar la aplicación, ese usuario puede seguir editando la aplicación.

## <a name="manage-entity-permissions"></a>Administrar permisos de entidad

### <a name="common-data-service-for-apps"></a>Common Data Service for Apps

Si crea una aplicación basada en CDS for Apps, debe asegurarse de que los usuarios con quién se comparte la aplicación tienen los permisos adecuados para la entidad o entidades en el que se basa la aplicación. En concreto, los usuarios deben pertenecer a un rol de seguridad que puede realizar tareas como crear, leer, escribir y eliminar los registros relevantes. En muchos casos, desea crear uno o varios roles de seguridad personalizado con los permisos exactos que los usuarios necesitan para ejecutar la aplicación. A continuación, puede asignar un rol a cada usuario según corresponda.

> [!NOTE]
> Cuando se redactó este documento, puede asignar roles de seguridad a usuarios individuales, pero no a los grupos de seguridad.

#### <a name="prerequisite"></a>Requisito previo

Para llevar a cabo los dos procedimientos siguientes, debe tener permisos de **administrador del sistema** en una base de datos de CDS for Apps.

#### <a name="create-a-security-role"></a>Crear un rol de seguridad

1. En el panel para compartir, seleccione **establecer permisos** en **permisos datos**y, a continuación, seleccione el **Roles de seguridad** vínculo.

    ![Abrir roles de seguridad](media/share-app/security-roles.png)

1. En **Todos los roles**, seleccione **Nuevo** y después escriba o pegue el nombre del rol que va a crear.

    ![Crear un rol de seguridad](media/share-app/new-role.png)

1. Seleccione una o más pestañas para buscar las entidades que usa su aplicación y después seleccione los permisos que quiera conceder al rol de seguridad.

    Por ejemplo, este gráfico muestra que el **principales registros** ficha contiene el **cuentas** entidad y los usuarios a los que se asignó este rol de seguridad puede crear, leer, escribir y eliminar registros en esa entidad .

    ![Especificar permisos](media/share-app/grant-access.png)

1. Haga clic en **Guardar y cerrar**.

#### <a name="assign-a-user-to-a-role"></a>Asignar un usuario a un rol

1. En el panel para compartir, seleccione **establecer permisos** en **permisos datos**y, a continuación, seleccione el **usuarios** vínculo.

    ![Vínculo Usuarios](media/share-app/open-users.png)

1. En la esquina superior derecha, escriba o pegue el nombre del usuario al que quiera asignar a la función y después seleccione el icono de búsqueda.

    ![Búsqueda de usuarios](media/share-app/search-users.png)

1. En los resultados de búsqueda, desplace el cursor hasta el resultado que quiera y seleccione la casilla que aparece.

1. En el banner superior, seleccione **Administrar roles**.

1. En el cuadro de diálogo que aparece, seleccione las casillas de verificación para **usuario de Common Data Service** y el rol que necesita el usuario para la aplicación, y, a continuación, seleccione **Aceptar.**

    ![Asignar un usuario a un rol](media/share-app/assign-users.png)

### <a name="common-data-service-previous-version"></a>Common Data Service (versión anterior)

Cuando se comparte una aplicación que se basa en una versión anterior de Common Data Service, debe compartir el permiso de tiempo de ejecución para el servicio por separado. Si no tiene permiso para hacerlo, consulte al administrador de entorno.
