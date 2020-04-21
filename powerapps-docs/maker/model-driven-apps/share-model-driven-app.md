---
title: Compartir una aplicación controlada por modelos con Power Apps | Microsoft Docs
description: Aprenda a compartir una aplicación basada en modelos
documentationcenter: ''
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/04/2020
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e1187757c90af2ec245ace51031f5e0345c92bd2
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/08/2020
ms.locfileid: "3238478"
---
# <a name="share-a-model-driven-app-with-power-apps"></a>Compartir una aplicación controlada por modelos con Power Apps

Las aplicaciones de [!INCLUDE [powerapps](../../includes/powerapps.md)] usan la seguridad basada en roles para compartir. El concepto básico en la seguridad basada en roles es que el rol de seguridad contiene privilegios que definen un conjunto de acciones que se pueden realizar en la aplicación. Todos los usuarios de la aplicación deben estar asignados a uno o más roles predefinidos o personalizados. O bien, también se pueden asignar roles a equipos. Cuando se asigna un usuario o un equipo a uno de estos roles, se concede a la persona o miembros del equipo el conjunto de privilegios asociados a este rol. 

## <a name="prerequisites"></a>Requisitos previos
Asegúrese de tener un [rol de seguridad](https://docs.microsoft.com/power-platform/admin/security-roles-privileges) con permisos iguales o mayores que el rol que está asignando a la aplicación y a otros usuarios. 

## <a name="create-a-security-role-for-your-app"></a>Crear un rol de seguridad para la aplicación
En general, las aplicaciones basadas en modelo contienen entidades personalizadas y otras configuraciones personalizadas. Es importante primero [crear un rol de seguridad](#create-a-security-role-for-your-app) con permiso para todos los componentes utilizados en la aplicación.  
> [!NOTE]
> Este paso se puede omitir si los roles existentes otorgan acceso a los datos en su aplicación. 

## <a name="preview-share-a-model-driven-app"></a>Vista previa: Compartir una aplicación basada en modelo 
Compartir una aplicación basada en modelo implica dos pasos principales. Primero, asocie uno o más roles de seguridad con la aplicación y luego asigne los roles de seguridad a los usuarios. 
1. Visite https://make.powerapps.com
2. Seleccione una aplicación basada en modelo y haga clic en **Compartir**.
3. Seleccione la aplicación y luego elija un rol de seguridad en la lista.
    > [!div class="mx-imgBorder"] 
    > ![](media/share-model-driven-app/share-app.png "Assign a role to the app")
4. Buscar un usuario
5. Seleccione el usuario y luego seleccione un rol en la lista.
    > [!div class="mx-imgBorder"] 
    > ![](media/share-model-driven-app/share-user.png "Assign a role to the user")
6. Haga clic en **Compartir**.

### <a name="share-the-link-to-your-app"></a>Compartir el vínculo a su aplicación
A diferencia cuando se comparten aplicaciones de lienzo, compartir aplicaciones basadas en modelo actualmente no envía un correos electrónicos con un vínculo a la aplicación.

Para obtener el vínculo directo a una aplicación:
1. Edite la aplicación y haga clic en la pestaña **Propiedades**.
2. Copie la **URL de interfaz unificada**.
3. Pegue la dirección URL de la aplicación en una ubicación para que los usuarios puedan acceder a ella, como publicándola en un sitio de SharePoint o enviándola por correo electrónico.


## <a name="create-or-configure-a-security-role"></a>Crear o configurar un rol de seguridad
El entorno de [!INCLUDE [powerapps](../../includes/powerapps.md)] incluye [roles de seguridad predefinidos](#about-predefined-security-roles) que reflejan tareas de usuario comunes con niveles de acceso definidos para que coincidan con el objetivo de seguridad recomendado de proporcionar acceso a la cantidad mínima de datos profesionales necesarios para usar la aplicación. Por ejemplo, si su aplicación se basa en una entidad personalizada, los privilegios de la entidad deben especificarse explícitamente antes de que los usuarios puedan trabajar en ella. Para hacerlo, puede realizar lo siguiente.
- Expandir un rol de seguridad predefinido existente, de modo que incluya privilegios en registros en función de la entidad personalizada. 
- Crear un rol de seguridad personalizado con el fin de administrar privilegios para los usuarios de la aplicación. 

Para obtener más información sobre los privilegios de acceso y de ámbito, consulte [Roles de seguridad](https://docs.microsoft.com/dynamics365/customer-engagement/admin/security-roles-privileges#security-roles).

### <a name="create-a-custom-security-role"></a>Crear un rol de seguridad personalizado
1. En el sitio [!INCLUDE [powerapps](../../includes/powerapps.md)] seleccione **Aplicaciones**, junto a la aplicación basada en modelo que desea compartir, seleccione **...** y luego seleccione **Compartir**.

2. Seleccione la aplicación y expanda la lista de roles de seguridad.

3. En la página **Todos los roles**, seleccione **Nuevo**.  

4. En el diseñador de roles de seguridad, seleccione las acciones, como leer, escribir o eliminar, y el ámbito para realizar dicha acción. El ámbito determina la profundidad o altura dentro de la jerarquía de entornos en la que el usuario puede realizar una acción determinada. En el cuadro **Nombre del rol**, introduzca *Técnicos de cuidado de mascotas*.

5. Seleccione la pestaña **Entidades personalizadas** y, a continuación, localice la entidad personalizada que desee. Para este ejemplo, se utiliza la entidad personalizada **Mascota**. 

6. En la fila **Mascota**, seleccione cada uno de los siguientes privilegios cuatro veces hasta que se seleccione el ámbito global de la organización ![Ámbito global de la organización](media/share-model-driven-app/organizational-scope-privilege.png): **Leer, Escribir, Anexar**

   > [!div class="mx-imgBorder"] 
   > ![Nuevo rol de seguridad](media/share-model-driven-app/custom-security-role.png)

7. Puesto que la aplicación de cuidado de mascotas también tiene una relación con la entidad Cuenta, seleccione la pestaña **Registros principales** y, en la fila **Cuenta** seleccione **Leer** cuatro veces hasta que se haya seleccionado el ámbito global de la organización ![Ámbito global de la organización](media/share-model-driven-app/organizational-scope-privilege.png). 

8. Seleccione la pestaña **Personalización** y luego en la lista de privilegios seleccione el privilegio **Leer** junto a **Aplicación basada en modelo** para seleccionar el ámbito de organización. ![Ámbito global de la organización](media/share-model-driven-app/organizational-scope-privilege.png).

    > [!div class="mx-imgBorder"] 
    > ![Seleccionar roles de seguridad para la aplicación](media/app-access-specific-use.png)

9. Seleccione **Guardar y cerrar**. 

10. En el diseñador de roles de seguridad, en el cuadro **Nombre del rol**, introduzca *Programadores del cuidado de mascotas*. 

11. Seleccione la pestaña **Entidades personalizadas** y, a continuación, localice la entidad **Mascota**. 

12. En la fila **Mascota**, seleccione cada uno de los siguientes privilegios cuatro veces hasta que se seleccione el ámbito global de la organización ![Ámbito global de la organización](media/share-model-driven-app/organizational-scope-privilege.png): **Crear, Leer, Escribir, Eliminar, Anexar, Anexar a, Asignar, Compartir**

13. Puesto que la aplicación de cuidado de mascotas también tiene una relación con la entidad Cuenta y los programadores deben poder crear y modificar registros de cuenta, seleccione la pestaña **Registros principales** y, en la fila **Cuenta** seleccione cada uno de los siguientes privilegios cuatro veces hasta que se haya seleccionado el ámbito global de la organización ![Ámbito global de la organización](media/share-model-driven-app/organizational-scope-privilege.png). 
    **Crear, Leer, Escribir, Eliminar, Anexar, Anexar a, Asignar, Compartir**

14. Seleccione **Guardar y cerrar**.

### <a name="assign-security-roles-to-users"></a>Asignar roles de seguridad a usuarios
Los roles de seguridad controlan el acceso del usuario a los datos a través de un conjunto de niveles de acceso y permisos. La combinación de niveles de acceso y permisos que se incluyen en un determinado rol de seguridad define los límites de visualización de datos para el usuario, así como las interacciones del usuario con estos.

#### <a name="assign-a-security-role-to-pet-grooming-technicians"></a>Asignar un rol de seguridad a los técnicos del cuidado de mascotas
1. En el cuadro de diálogo **Compartir esta aplicación**, en **Asignar usuarios al rol de seguridad**, seleccione **Usuarios de seguridad**.
2. En la lista que se muestra, seleccione los usuarios que sean cuidadores de mascotas y luego, en la barra de comandos, seleccione **Administrar roles**.

3. Haga clic en **Administrar roles de seguridad**.
    > [!div class="mx-imgBorder"] 
    > ![](media/share-model-driven-app/manage-roles.png "Manage roles")

4. En la página **Todos los roles**, seleccione **Usuario de Common Data Service**, luego haga clic en **Acciones** y luego en **Copiar rol**. 

> [!TIP]
> También puede crear una nueva función vacía en lugar de copiar una función existente. 

6. En el cuadro **Nombre de rol** proporcione un rol descriptivo como *Mi acceso a la aplicación personalizada*.  Haga clic en **Aceptar**.

7. En el diseñador de roles de seguridad, seleccione las acciones, como leer, escribir o eliminar, y los [niveles de acceso](https://docs.microsoft.com/power-platform/admin/security-roles-privileges#security-roles). Los niveles de acceso determinan la profundidad o altura dentro de la jerarquía de entornos en la que el usuario puede realizar una acción determinada. 

8. Seleccione la pestaña **Entidades personalizadas** y, a continuación, localice la entidad personalizada que utiliza en su aplicación. 

9.  En la fila de su entidad personalizada, establezca niveles de acceso para cada permiso.  

10. Repita para otras entidades utilizadas en su aplicación. 

11. Seleccione la pestaña **Personalización** y asegúrese de que el privilegio **Lectura** está establecido en **Aplicación basada en modelo** para que el nivel de acceso de la organización. ![Ámbito global de la organización](media/share-model-driven-app/organizational-scope-privilege.png) esté seleccionado.

    > [!IMPORTANT]
    > Los usuarios que tengan otorgados **Lectura**, **Creación** y **Escritura** para el privilegio **Aplicación basada en modelo** tendrán acceso a todas las aplicaciones del entorno, incluso cuando no forman parte de ningún rol que tenga acceso a la aplicación.
    > ![Crear y escribir con privilegio de aplicación basada en modelo](media/app-access-cds.png)

12. Seleccione **Guardar y cerrar**. 


## <a name="about-predefined-security-roles"></a>Acerca de los roles de seguridad predefinidos
Estos roles predefinidos están disponibles con un entorno de [!INCLUDE [powerapps](../../includes/powerapps.md)].


|Rol de seguridad  |*Privilegios  |Descripción |
|---------|---------|---------|
|Creador de entornos     |  Ninguno       | Puede crear nuevos recursos asociados a un entorno incluyendo aplicaciones, conexiones, API personalizadas, puertas de enlace y flujos usando Power Automate. Sin embargo, no tiene ningún privilegio para acceder a los datos en un entorno. Más información: [Información general de entornos](https://powerapps.microsoft.com/blog/powerapps-environments/)        |
|Administrador del sistema     |  Crear, Leer, Escribir, Eliminar, Personalizaciones, Roles de seguridad       | Tiene permiso completo para personalizar o administrar el entorno, incluida la creación, modificación y asignación de roles de seguridad. Puede ver todos los datos del entorno. Más información: [Privilegios necesarios para la personalización](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|Personalizador del sistema     | Crear (propio), Leer (propio), Escribir (propio), Eliminar (propio), Personalizaciones         | Tiene permiso completo para personalizar el entorno. No obstante, solo puede ver los registros de las entidades del entorno que cree. Más información: [Privilegios necesarios para la personalización](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|Usuario de Common Data Service     |  Leer, Crear (propio), Escribir (propio), eliminar (propio)       | Puede ejecutar una aplicación dentro del entorno y realizar las tareas comunes para los registros de su propiedad.        |
|Delegar     | Actúa en nombre de otro usuario        | Permite ejecutar código como otro usuario o la suplantación.  Se suele usar con otro rol de seguridad para permitir el acceso a los registros. Más información: [Suplantar a otro usuario](https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/impersonate-another-user)        |

*El privilegio es ámbito global salvo que se especifique lo contrario.

## <a name="use-azure-active-directory-groups-to-manage-access"></a>Utilizar grupos de Azure Active Directory para administrar acceso
Los administradores pueden usar los grupos de Azure Active Directory (Azure AD) de su organización para administrar los derechos de acceso para usuarios de Common Data Service con licencia. Ambos tipos de grupos de Azure AD (oficina y seguridad) se pueden usar para proteger los derechos de acceso de usuario a una aplicación. Más información: [Acerca de los equipos de grupo](/power-platform/admin/manage-teams#about-group-teams) 


### <a name="see-also"></a>Vea también
[Ejecutar una aplicación controlada por modelos en un dispositivo móvil](../../user/run-app-client-model-driven.md)

[Crear usuarios y asignar roles de seguridad](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)


