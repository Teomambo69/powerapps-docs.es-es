---
title: Tutorial para compartir una aplicación controlada por modelos con PowerApps | Microsoft Docs
description: En este tutorial, obtendrá información sobre cómo compartir una aplicación controlada por modelos.
documentationcenter: ''
author: Mattp123
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/21/2018
ms.author: matp
ms.openlocfilehash: 134ae4dfb5fe111c4c40e96efa1e79a3993c4a46
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37899764"
---
# <a name="tutorial-share-a-model-driven-app-with-powerapps"></a>Tutorial: Compartir una aplicación controlada por modelos con PowerApps

Las aplicaciones de [!INCLUDE [powerapps](../../includes/powerapps.md)] usan la seguridad basada en roles para su uso compartido. El concepto fundamental en la seguridad basada en roles es que un rol de seguridad contiene los privilegios que definen un conjunto de acciones que se pueden realizar dentro de la aplicación. Todos los usuarios de la aplicación deben estar asignados a uno o más roles predefinidos o personalizados. O bien, los roles se pueden asignar a equipos. Cuando un usuario o equipo se asigna a uno de estos roles, se concede al usuario o los miembros del equipo el conjunto de privilegios asociados a ese rol. 

En este tutorial realizará las tareas para compartir una aplicación controlada por modelos para que otros usuarios puedan usarla. Obtendrá información sobre cómo:
- Crear un rol de seguridad personalizado
- Asignar usuarios al rol de seguridad personalizado
- Asignar el rol de seguridad a una aplicación

## <a name="prerequisites"></a>Requisitos previos
Para compartir una aplicación debe tener el rol Administrador de entorno de [!INCLUDE [powerapps](../../includes/powerapps.md)] o el rol Administrador del sistema. 

## <a name="sign-in-to-powerapps"></a>Inicio de sesión en PowerApps
Inicie sesión en [PowerApps](https://powerapps.microsoft.com/). Si todavía no tiene una cuenta de [!INCLUDE [powerapps](../../includes/powerapps.md)], haga clic en el vínculo **Inicio gratuito**.

## <a name="share-an-app"></a>Compartir una aplicación 
En el tutorial se sigue a la empresa Contoso, que tiene un negocio de peluquería para mascotas para perros y gatos. Ya se ha creado y publicado una aplicación que contiene una entidad personalizada para el seguimiento de la empresa de peluquería para mascotas. Ahora, la aplicación debe compartirse para que el personal de la empresa pueda usarla. Para compartir la aplicación, un administrador o el creador de la aplicación asigna uno o varios roles de seguridad a los usuarios y la aplicación. 

## <a name="create-or-configure-a-security-role"></a>Crear o configurar un rol de seguridad
En el entorno de [!INCLUDE [powerapps](../../includes/powerapps.md)] se incluyen [roles de seguridad predefinidos](#about-predefined-security-roles) que reflejan las tareas comunes de usuario con niveles de acceso definidos para que coincidan con el objetivo de procedimiento recomendado de seguridad de proporcionar acceso a la cantidad mínima de datos de negocio necesarios para usar la aplicación. Recuerde que la aplicación de peluquería para mascotas de Contoso se basa en una entidad personalizada. Como la entidad es personalizada, se deben especificar los privilegios de forma explícita antes de que los usuarios puedan trabajar en ella. Para ello, se puede realizar una de las acciones siguientes:
- Expandir un rol de seguridad predefinido existente para que incluya los privilegios en registros en función de la entidad personalizada. 
- Crear un rol de seguridad personalizado con el fin de administrar privilegios para los usuarios de la aplicación. 

Como el entorno en el que se van a mantener los registros de peluquería para mascotas también se usa para otras aplicaciones que ejecuta la empresa Contoso, se creará un rol de seguridad personalizado específico para la aplicación de peluquería para mascotas. Además, se necesitan dos conjuntos diferentes de privilegios de acceso.
- Los técnicos de peluquería para mascotas solo necesitan leer, actualizar y adjuntar otros registros, por lo que su rol de seguridad tendrá privilegios de lectura, escritura y anexar. 
- Los programadores de peluquería para mascotas necesitan todos los privilegios que tienen los técnicos, además de la capacidad de crear, anexar, eliminar y compartir, de modo que su rol de seguridad tendrá privilegios para crear, leer, escribir, anexar, eliminar, asignar, anexar a y compartir.

Para obtener más información sobre los privilegios de acceso y ámbito, vea [Roles de seguridad](https://docs.microsoft.com/dynamics365/customer-engagement/admin/security-roles-privileges#security-roles).

## <a name="create-a-custom-security-role"></a>Crear un rol de seguridad personalizado
1. En el sitio de [!INCLUDE [powerapps](../../includes/powerapps.md)], seleccione **Basado en modelos** > **Aplicaciones** > **...**> **Vínculo Compartir**.
2. Desde el cuadro de diálogo **Compartir esta aplicación**, en **Crear un rol de seguridad**, haga clic en **Configuración de seguridad**.
3. En la página **Configuración**, haga clic en **Nuevo**.  

4. Desde el Diseñador de roles de seguridad se seleccionan las acciones, como lectura, escritura o eliminación, y el ámbito para realizar esa acción. El ámbito determina la profundidad o altura dentro de la jerarquía de entornos a la que el usuario puede realizar una acción concreta. En el cuadro **Nombre del rol** escriba *Técnicos de peluquería para mascotas*.
5. Haga clic en la pestaña **Entidades personalizadas** y, después, busque la entidad personalizada que quiere. En este ejemplo, se usará la entidad personalizada denominada **Mascota**. 
6. En la fila **Mascota**, seleccione cuatro veces cada uno de los privilegios siguientes hasta que se seleccione ![Ámbito global de organización](media/share-model-driven-app/organizational-scope-privilege.png): **Leer, Escribir, Anexar**
   ![Nuevo rol de seguridad](media/share-model-driven-app/custom-security-role.png)
7. Como la aplicación de peluquería para mascotas también tiene una relación con la entidad de cuenta, haga clic en la pestaña **Registros principales** y, en la fila **Cuenta**, seleccione cuatro veces **Lectura** hasta que se seleccione ![Ámbito global de la organización](media/share-model-driven-app/organizational-scope-privilege.png). 
8. Haga clic en **Guardar y cerrar**. 
9. En el Diseñador de roles de seguridad, en el cuadro **Nombre de rol**, escriba *Programadores de peluquería para mascotas*. 
10. Haga clic en la pestaña **Entidades personalizadas** y, después, busque la entidad **Mascota**. 
11. En la fila **Mascota**, seleccione cuatro veces cada uno de los privilegios siguientes hasta que se seleccione ![Ámbito global de la organización](media/share-model-driven-app/organizational-scope-privilege.png): **Crear, Leer, Escribir, Eliminar Anexar, Anexar a, Asignar, Compartir**.
12. Como la aplicación de peluquería para mascotas también tiene una relación con la entidad de cuenta y los programadores deben poder crear y modificar registros de cuenta, haga clic en la pestaña **Registros principales** y, en la fila **Cuenta**, seleccione cuatro veces cada uno de los privilegios siguientes hasta que se seleccione ![Ámbito global de la organización](media/share-model-driven-app/organizational-scope-privilege.png). 
    **Crear, Leer, Escribir, Eliminar, Anexar, Anexar a, Asignar, Compartir**
13. Haga clic en **Guardar y cerrar**.

## <a name="assign-security-roles-to-users"></a>Asignar roles de seguridad a los usuarios
Los roles de seguridad controlan el acceso de un usuario a los datos a través de un conjunto de permisos y niveles de acceso. La combinación de niveles de acceso y permisos que se incluyen en un rol de seguridad específico establece los límites en la vista de los datos del usuario y en las interacciones del usuario con esos datos.

> [!IMPORTANT]
> Para usar una aplicación controlada por modelos, todos los usuarios de la aplicación en el entorno deben tener al menos el rol de seguridad de usuario de Common Data Service, independientemente de los roles de seguridad adicionales que asigne. En la mayoría de los casos, el rol de seguridad de usuario de Common Data Service proporciona suficientes privilegios para llevar a cabo las tareas básicas necesarias para usar una aplicación.
> Tenga en cuenta que los usuarios que tienen el rol de seguridad de usuario de Common Data Service también tienen acceso de lectura y escritura a todos los registros de entidad estándar de cuenta, contacto y conexión, independientemente de quién sea el propietario. Si no quiere que los usuarios de la aplicación tengan privilegios para estos registros, cree un rol de seguridad personalizado. La manera más sencilla es copiar el rol de seguridad de usuario de Common Data Service y quitar los privilegios adecuados. Más información: [Copia de roles de seguridad](https://docs.microsoft.com/dynamics365/customer-engagement/admin/copy-security-role)

### <a name="assign-a-security-role-to-pet-grooming-technicians"></a>Asignar un rol de seguridad a los técnicos de peluquería para mascotas
1. Desde el cuadro de diálogo **Compartir esta aplicación**, en **Assign users to the security role** (Asignar usuarios al rol de seguridad), haga clic en **Usuarios de seguridad**.
2. En la lista que aparece, seleccione los cuidadores de mascotas.
3. Haga clic en **Administrar roles**.

    ![Administrar roles](media/share-model-driven-app/select-users-for-security-roles.png)

4. En el cuadro de diálogo **Administrar roles de usuario**, seleccione el rol de seguridad **Técnicos de peluquería para mascotas** que creó anteriormente y, después, haga clic en **Aceptar**.

### <a name="assign-a-security-role-to-pet-grooming-schedulers"></a>Asignar un rol de seguridad a los programadores de peluquería para mascotas
1. Desde el cuadro de diálogo **Compartir esta aplicación**, en **Assign users to a security role** (Asignar usuarios a un rol de seguridad), haga clic en **Usuarios de seguridad**.
2. En la lista que aparece, seleccione los programadores de peluquería para mascotas.
3. Haga clic en **Administrar roles**.
4. En el cuadro de diálogo **Administrar roles de usuario**, seleccione el rol de seguridad **Programadores de peluquería para mascotas** que creó anteriormente y, después, haga clic en **Aceptar**.


## <a name="add-security-roles-to-the-app"></a>Agregar roles de seguridad a la aplicación
Después, será necesario asignar uno o varios roles de seguridad a la aplicación. Los usuarios tendrán acceso a las aplicaciones en función de los roles de seguridad que tengan asignados.
1. Desde el cuadro de diálogo **Compartir esta aplicación**, en **Add the security role to your app** (Agregar el rol de seguridad a la aplicación), haga clic en **Mis aplicaciones**.
2. En la esquina inferior derecha del icono de aplicación de la aplicación de peluquería para mascotas de Contoso, haga clic en **Más opciones (...)**  y, después, seleccione **Administrar roles**.

    ![Administrar los roles de la aplicación](media/share-model-driven-app/manage-roles.png)

4. En la sección **Roles**, puede elegir si quiere dar acceso a la aplicación a todos los roles de seguridad o a los roles seleccionados. Seleccione los roles **Programadores de peluquería para mascotas** y **Técnicos de peluquería para mascotas** que creó anteriormente.

    ![Seleccionar roles de seguridad para la aplicación](media/share-model-driven-app/app-security-roles.png)

5. Seleccione **Guardar**.
 
## <a name="share-the-link-to-your-app"></a>Compartir el vínculo a la aplicación
1. Desde el cuadro de diálogo **Compartir esta aplicación**, en **Share the link to your app directly with users** (Compartir el vínculo a la aplicación directamente con los usuarios), copie la dirección URL que se muestra.
 
2. Haga clic en **Cerrar**.
3. Pegue la URL de la aplicación en una ubicación a la que los usuarios puedan tener acceso, por ejemplo publicándola en un sitio de SharePoint o enviándola por correo electrónico.

![Compartir el vínculo](media/share-model-driven-app/share-model-driven-URL.PNG)

También puede encontrar la dirección URL de la aplicación en la pestaña **Propiedades** del diseñador de la aplicación. 
    
![Copiar la dirección URL de la aplicación](media/share-model-driven-app/app-designer-copy-web-url.png)

## <a name="about-predefined-security-roles"></a>Acerca de los roles de seguridad predefinidos
Estos roles predefinidos están disponibles con un entorno de [!INCLUDE [powerapps](../../includes/powerapps.md)].


|Rol de seguridad  |*Privilegios  |Descripción |
|---------|---------|---------|
|Creador de entorno     |  Ninguno       | Puede crear recursos asociados a un entorno, incluidas aplicaciones, conexiones, API personalizadas, puertas de enlace y flujos con Microsoft Flow. Pero no tiene privilegios para tener acceso a los datos dentro de un entorno. Más información: [Environments overview](https://powerapps.microsoft.com/blog/powerapps-environments/) (Información general de los entornos).        |
|Administrador del sistema     |  Crear, Leer, Escribir, Eliminar, Personalizaciones, Roles de seguridad       | Tiene permiso completo para personalizar o administrar el entorno, incluida la creación, modificación y asignación de roles de seguridad. Puede ver todos los datos en el entorno. Más información: [Privilegios necesarios para la personalización](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|Personalizador del sistema     | Crear (propio), Lectura (propio), Escritura (propio), Eliminar (propio), Personalizaciones         | Tiene permiso total para personalizar el entorno. Pero solo puede ver los registros de las entidades de entorno que crea. Más información: [Privilegios necesarios para la personalización](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|Usuario de Common Data Service     |  Lectura, Crear (propio), Escritura (propio), Eliminar (propio)       | Puede ejecutar una aplicación en el entorno y realizar tareas comunes para los registros que le pertenecen.        |
|Delegado     | Actuar en nombre de otro usuario        | Permite que el código se ejecute como otro usuario o lo suplante.  Se usa normalmente con otro rol de seguridad para permitir el acceso a los registros. Más información: [Suplantar a otro usuario](https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/impersonate-another-user)        |

*El privilegio es de ámbito global, a menos que se especifique lo contrario.

## <a name="next-steps"></a>Pasos siguientes
[Inicio rápido: Ejecución de una aplicación controlada por modelos en un dispositivo móvil](../../user/run-app-client-model-driven.md)



