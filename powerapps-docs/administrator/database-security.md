---
title: Configuración de la seguridad del entorno | Microsoft Docs
description: En este tema se explica cómo configurar la seguridad del entorno.
author: manasmams
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 10/10/2018
ms.author: manasma
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: 3c8bdcb855b1e15cbebeb2a51fedf8aea7684286
ms.sourcegitcommit: c4369e5f31bb08716f1af1416f3f7510a4b926d5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2018
ms.locfileid: "49072528"
---
# <a name="configure-environment-security"></a>Configurar la seguridad del entorno
Common Data Service (CDS) for Apps usa un modelo de seguridad basado en rol que ayuda a proteger el acceso a la base de datos. En este tema se explica cómo crear los artefactos de seguridad necesarios para ayudarle proteger una aplicación. Estos roles de usuario controlan el acceso en tiempo de ejecución a los datos y son independientes de los roles de entorno que rigen los administradores de entorno y los creadores de entorno. Para obtener información general acerca de los entornos, consulte [Environments overview](environments-overview.md) (Introducción a los entornos).

## <a name="assign-security-roles-to-users"></a>Asignar roles de seguridad a los usuarios
Los roles de seguridad controlan el acceso de un usuario a los datos a través de un conjunto de permisos y niveles de acceso. La combinación de niveles de acceso y permisos que se incluyen en un rol de seguridad específico establece los límites en la vista de los datos del usuario y en las interacciones del usuario con esos datos.

Para asignar un usuario o un grupo de seguridad a un rol de entorno, un Administrador de entorno puede realizar estos pasos en el [centro de administración de PowerApps][1]:

1. Seleccione el entorno en la tabla de entornos.

    ![](./media/environment-admin/environment-list-new.png)

2. Haga clic en la pestaña **Seguridad**.

3. Compruebe si el usuario ya existe en el entorno. Para ello, seleccione la opción pertinente para **ver la lista de usuarios en el entorno**.
    
    ![](./media/database-security/security-viewuser.png)

4. Si el usuario no existe, puede agregarlo desde el centro de administración de PowerApps. Para ello, indique la dirección de correo electrónico del usuario en la organización y seleccione **Agregar usuario**.

    ![](./media/database-security/security-adduser.png)

    Espere unos minutos para ver si el usuario está disponible en la lista de usuarios del entorno.
  
5. Seleccione el usuario de la lista de usuarios en el entorno.

    ![](./media/environment-admin/D365-Select-User.png)

6. Asigne el rol al usuario.

    ![](./media/environment-admin/D365-Assign-Role.png)

    > [!NOTE]
    > Actualmente, solo se pueden asignar roles a los usuarios. La asignación de un rol a un grupo de seguridad está en nuestro trabajo pendiente.

7. Haga clic en **Aceptar** para actualizar las asignaciones al rol de entorno.

## <a name="predefined-security-roles"></a>Roles de seguridad predefinidos
En el entorno de PowerApps se incluyen los roles de seguridad predefinidos que reflejan las tareas comunes de usuario con niveles de acceso definidos para que coincidan con el objetivo de procedimiento recomendado de seguridad de proporcionar acceso a la cantidad mínima de datos empresariales necesarios para usar la aplicación.

|Rol de seguridad  |*Privilegios de la base de datos  |Descripción |
|---------|---------|---------|
|Administrador del sistema     |  Crear, Leer, Escribir, Eliminar, Personalizaciones, Roles de seguridad       | Tiene permiso completo para personalizar o administrar el entorno, incluida la creación, modificación y asignación de roles de seguridad. Puede ver todos los datos en el entorno. Más información: [Privilegios necesarios para la personalización](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|Personalizador del sistema     | Crear (propio), Lectura (propio), Escritura (propio), Eliminar (propio), Personalizaciones         | Tiene permiso total para personalizar el entorno. Pero solo puede ver los registros de las entidades de entorno que crea. Más información: [Privilegios necesarios para la personalización](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|Creador de entorno     |  Ninguno       | Puede crear recursos asociados a un entorno, incluidas aplicaciones, conexiones, API personalizadas, puertas de enlace y flujos con Microsoft Flow. Pero no tiene privilegios para tener acceso a los datos dentro de un entorno. Más información: [Environments overview](https://powerapps.microsoft.com/blog/powerapps-environments/) (Información general de los entornos).        |
|Usuario de Common Data Service     |  Lectura (propio), Crear (propio), Escritura (propio), Eliminar (propio)       | Puede ejecutar una aplicación en el entorno y realizar tareas comunes para los registros que le pertenecen.        |
|Delegado     | Actuar en nombre de otro usuario        | Permite que el código se ejecute como otro usuario o lo suplante.  Se usa normalmente con otro rol de seguridad para permitir el acceso a los registros. Más información: [Suplantar a otro usuario](https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/impersonate-another-user)        |

*El privilegio es de ámbito global, a menos que se especifique lo contrario.

- El rol Creador de entorno no solo puede crear recursos dentro de un entorno, sino también distribuir las aplicaciones que cree en un entorno a otros usuarios de la organización. Pueden compartir la aplicación con usuarios individuales. Para más información, consulte [Compartir una aplicación en PowerApps](../maker/canvas-apps/share-app.md).

- A los usuarios que crean aplicaciones que se conectan a la base de datos y que tienen que crear o actualizar entidades y roles de seguridad, también se les debe asignar el rol Personalizador del sistema, junto con el rol Creador de entorno, dado que este último no tiene privilegios en la base de datos.

## <a name="create-or-configure-a-custom-security-role"></a>Crear o configurar un rol de seguridad personalizado
Si la aplicación usa una entidad personalizada, sus privilegios se deben conceder explícitamente en un rol de seguridad para que se pueda usar.  Puede agregar estos privilegios en un rol de seguridad existente o crear uno personalizado. Hay un conjunto de privilegios mínimos que son necesarios para usar el nuevo rol de seguridad: vea [Privilegios mínimos para ejecutar aplicaciones](#minimum-privileges-to-run-app).

> [!TIP]
> Si quiere crear un rol de seguridad personalizado con los privilegios mínimos necesarios para ejecutar una aplicación, vea la sección siguiente: [Privilegios mínimos para ejecutar aplicaciones](#minimum-privileges-to-run-app).

Es posible que el entorno mantenga los registros que pueden usar varias aplicaciones, y es posible que necesite varios roles de seguridad para acceder a los datos con diferentes privilegios. P. ej.:
- Es posible que algunos de los usuarios (Tipo A) solo necesiten leer, actualizar y adjuntar otros registros para que su rol de seguridad tenga privilegios de lectura, escritura y anexar.
- Es posible que otros usuarios necesiten todos los privilegios que tienen los usuarios de Tipo A, además de la capacidad de crear, anexar, eliminar y compartir, de modo que su rol de seguridad tendrá privilegios para crear, leer, escribir, anexar, eliminar, asignar, anexar a y compartir.

Para obtener más información sobre los privilegios de acceso y ámbito, vea [Roles de seguridad](https://docs.microsoft.com/dynamics365/customer-engagement/admin/security-roles-privileges#security-roles).

1. En el [Centro de administración de PowerApps][1], seleccione el entorno en el que quiera actualizar un rol de seguridad.

    ![](./media/environment-admin/choose-environment-updated.png)

2. Haga clic en el vínculo de la pestaña **Detalles** para administrar el entorno en el Centro de administración de Dynamics 365.

3. Seleccione la instancia (con el mismo nombre del entorno) y haga clic en Abrir

    ![](./media/database-security/glados-instance-list.png)

4. En el encabezado, haga clic en **Configuración** y seleccione **Seguridad**

    ![](./media/database-security/dyn365-settings-security.png)

5. Seleccione **Roles de seguridad**.

    ![](./media/database-security/dyn365-securityroles.png)

6. Haga clic en **Nuevo**.

7. Desde el Diseñador de roles de seguridad se seleccionan las acciones, como lectura, escritura o eliminación, y el ámbito para realizar esa acción.

8. Haga clic en la pestaña y busque la entidad, p. ej. la pestaña **Entidades personalizadas**, para establecer permisos en una entidad personalizada.

9. Seleccione los privilegios **Leer, escribir, anexar**

10. Haga clic en **Guardar y cerrar**.

## <a name="minimum-privileges-to-run-app"></a>Privilegios mínimos para ejecutar aplicaciones
Cuando se crea un rol de seguridad personalizado, es necesario incluir en él un conjunto de privilegios mínimos para que un usuario ejecute una aplicación. Se ha creado una solución que se puede importar y que proporciona un rol de seguridad con los privilegios mínimos necesarios.  

Comience por descargar la solución desde el Centro de descarga: [CDS for Apps minimum privilege security role](http://download.microsoft.com/download/6/5/5/6552A30E-05F4-45F0-AEE3-9BB01E13118A/MinprivilegeSecRole_1_0_0_0.zip) (Rol de seguridad con privilegios mínimos CDS para aplicaciones).

Luego siga las instrucciones para importar la solución: [Importar, actualizar y exportar soluciones](../maker/common-data-service/import-update-export-solutions.md).

Al importar la solución, se crea el rol **min prv apps use**, que puede copiar (vea: [Crear un rol de seguridad por Copiar rol](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/create-edit-security-role#create-a-security-role-by-copy-role)). Cuando termine el copiado del rol, vaya a cada pestaña (Registros principales, Administración empresarial, Personalización, etc.) y establezca los privilegios adecuados. 

> [!IMPORTANT]
> Debe probar la solución en un entorno de desarrollo antes de importar en un entorno de producción. 

<!--Reference links in article-->
[1]: https://admin.powerapps.com
