---
title: "Administración de entornos | Microsoft Docs"
description: "Administrar entornos en PowerApps, incluida la creación, cambio de nombre, eliminación y seguridad"
services: 
suite: powerapps
documentationcenter: na
author: jamesol-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/11/2017
ms.author: jamesol
ms.openlocfilehash: 1eeb79d0c109181ae75b86a78cecdb4babe058ab
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="environments-administration-in-powerapps"></a>Administración de entornos en PowerApps
En el [centro de administración de PowerApps][1], administre los entornos que ha creado y aquellos a los que se le ha agregado con el rol de administrador de entorno. Desde el centro de administración, puede realizar estas acciones administrativas:

* Crear entornos.
* Cambiar el nombre de entornos.
* Agregar o quitar un usuario o grupo del rol Administrador de entorno o Creador de entorno.
* Aprovisionar una base de datos de Common Data Service para el entorno.
* Establecer directivas para la prevención de pérdida de datos.
* Establecer directivas de seguridad de base de datos (abiertas o restringidas por los roles de base de datos).
* Los miembros del rol Administrador global del inquilino de Azure AD (incluye administradores globales de Office 365) también pueden administrar todos los entornos creados en su inquilino y establecer directivas para todo el inquilino.

## <a name="access-the-powerapps-admin-center"></a>Acceso al centro de administración de PowerApps
Para acceder al centro de administración de PowerApps:

* Vaya directamente a [admin.powerapps.com][1] o
* Vaya a [powerapps.com][2] y seleccione el icono de engranaje en el encabezado de navegación.
  
    ![](./media/environment-admin/powerapps-gear-dropdown.png)

Para administrar un entorno en el centro de administración de PowerApps, debe tener uno de estos roles:

* El rol Administrador de entorno para el entorno o
* El rol Administrador global del inquilino de Azure AD o de Office 365.

También necesita Plan 2 de PowerApps o de Flow para acceder al centro de administración. Para más información, consulte la [página de precios de PowerApps][3].

**Importante**: Los cambios realizados en el centro de administración de PowerApps afectan al [centro de administración de Flow][4] y viceversa.

## <a name="create-an-environment"></a>Creación de un entorno
En primer lugar, haga clic en **+ Nuevo entorno** para abrir un cuadro de diálogo y crear un entorno.

![](./media/environment-admin/new-environment-button.png)

A continuación, escriba la siguiente información:

| Propiedad | Descripción |
| --- | --- |
| Nombre del entorno |Escriba el nombre de su entorno. |
| Región |Elija la ubicación para hospedar el entorno. Se recomienda usar la ubicación más cercana a los usuarios. Por ejemplo, si los usuarios de la aplicación se encuentran en Londres, elija una ubicación de Europa. Si se encuentran en Nueva York, elija Estados Unidos. Consulte la lista de [regiones admitidas](regions-overview.md) para los entornos. |
| Crear una base de datos para este entorno |Active esta casilla para crear una base de datos de Common Data Service para este entorno. Se puede configurar la base de datos para que esté abierta a todos los usuarios del entorno o restringida a los roles de base de datos. Para más información, consulte [Configurar seguridad de base de datos](database-security.md). |

![](./media/environment-admin/new-environment-updated.png)

Por último, seleccione **Crear entorno**.

El nuevo entorno aparece en la tabla de entornos.

> [!NOTE]
> Cuando crea un entorno, se le agrega automáticamente al rol Administrador de entorno de dicho entorno.
> 
> 

## <a name="view-your-environments"></a>Visualización de los entornos
Cuando se abre el centro de administración, la pestaña Entornos aparece de forma predeterminada y muestra todos los entornos para los que es Administrador de entorno (como se ve a continuación):

![](./media/environment-admin/environment-list-updated.png)

Si es miembro del rol Administrador global del inquilino de Azure AD o de Office 365, todos los entornos que hayan creado los usuarios de su inquilino aparecen porque es automáticamente Administrador de entorno para todos ellos.

## <a name="rename-your-environment"></a>Cambio del nombre del entorno
1. Abra el [centro de administración de PowerApps][1], busque el entorno cuyo nombre vaya a cambiar en la lista y haga clic o pulse en él.
   
    ![](./media/environment-admin/environment-list-updated3.png)
2. Haga clic o pulse en **Detalles**.
   
    ![](./media/environment-admin/environment-rename-details-2.png)
3. En el cuadro de texto **Nombre**, escriba el nuevo nombre y haga clic en **Guardar**.
   
    ![](./media/environment-admin/environment-rename-2.png)

## <a name="delete-your-environment"></a>Eliminación del entorno
1. En el [centro de administración de PowerApps][1], haga clic o pulse en el entorno que desea eliminar.
   
    ![](./media/environment-admin/environment-list-updated3.png)
2. Haga clic o pulse en **Detalles**.
   
    ![](./media/environment-admin/environment-rename-details-2.png)
3. Haga clic o pulse en **Eliminar este entorno** para eliminarlo.
   
    ![](./media/environment-admin/delete-environment-2.png)

## <a name="create-a-common-data-service-database-for-an-environment"></a>Creación de una base de datos de Common Data Service para un entorno
Si un entorno carece de base de datos, un Administrador de entorno puede crear una en el [centro de administración de PowerApps][1] siguiendo estos pasos. Solo los usuarios con una licencia de Plan 2 de PowerApps pueden crear bases de datos de Common Data Service.

1. Seleccione un entorno en la tabla de entornos.
   
    ![](./media/environment-admin/choose-environment-updated.png)
2. Seleccione la pestaña **Base de datos**.
3. Seleccione **Crear mi base de datos**.
   
    ![](./media/environment-admin/database-tab.png)
   
    Cuando se haya aprovisionado la base de datos, aparece este mensaje de confirmación:
   
    ![](./media/environment-admin/database-tab-success.png)

Después de crear una base de datos, elija un modelo de seguridad. Para más información, consulte [Configurar seguridad de base de datos](database-security.md).

## <a name="manage-security-for-your-environments"></a>Administración de la seguridad para los entornos
### <a name="environment-permissions"></a>Permisos de entorno
En un entorno, todos los usuarios en el inquilino de Azure AD lo son también de dicho entorno. No obstante, para que puedan desempeñan un rol con más privilegios, se les debe agregar a un rol de entorno específico. Los entornos tienen dos roles integrados que proporcionan acceso a los permisos dentro de un entorno:

* El rol **Administrador de entorno** puede realizar todas las acciones administrativas en un entorno, incluidas las siguientes:
  
  o    Agregar o quitar un usuario o grupo del rol Administrador de entorno o Creador de entorno.
  
  o    Aprovisionar una base de datos de Common Data Service para el entorno.
  
  o    Ver y administrar todos los recursos creados dentro de un entorno.
  
  o    Establecer directivas de prevención de pérdida de datos. Para más información, consulte [Directivas para la prevención de pérdida de datos](prevent-data-loss.md).
* El rol **Creador de entorno** puede crear recursos dentro de un entorno, incluidas aplicaciones, conexiones, conectores personalizados, puertas de enlace y flujos con Microsoft Flow. Los creadores de entorno también pueden distribuir las aplicaciones que creen en un entorno a otros usuarios de su organización. Pueden compartir la aplicación con usuarios individuales, grupos de seguridad o todos los usuarios de la organización. Para más información, consulte [Compartir una aplicación en PowerApps](share-app.md).

Para asignar un usuario o un grupo de seguridad a un rol de entorno, un Administrador de entorno puede realizar estos pasos en el [centro de administración de PowerApps][1]:

1. Seleccione el entorno en la tabla de entornos.
   
    ![](./media/environment-admin/choose-environment-updated.png)
2. En la pestaña **Seguridad**, seleccione **Roles de entorno**.
3. Seleccione el rol **Administrador de entorno** o **Creador de entorno**.
   
    ![](./media/environment-admin/choose-environment-role.png)
4. Especifique los nombres de uno o varios usuarios o grupos de seguridad en Azure Active Directory o especifique que desea agregar toda la organización.
   
    ![](./media/environment-admin/enter-name.png)
5. Seleccione **Guardar** para actualizar las asignaciones al rol de entorno.

Para quitar todos los permisos de un usuario o grupo, haga clic o pulse en el icono **x** de ese usuario o grupo.

> [!NOTE]
> Los usuarios o grupos asignados a estos roles de entorno no tienen acceso automáticamente a la base de datos del entorno (si existe) y un propietario de base de datos debe darles acceso por separado. Para más información, consulte [Configurar seguridad de base de datos](database-security.md).  
> 
> 

### <a name="database-security"></a>Seguridad de base de datos
La capacidad de crear y modificar un esquema de base de datos y conectarse a los datos almacenados en una base de datos que está aprovisionada en su entorno se controla mediante los roles de usuario y los conjuntos de permisos de la base de datos. Puede administrar los roles de usuario y los conjuntos de permisos para la base de datos de su entorno desde las secciones **Roles de usuario** y **Conjuntos de permisos** de la pestaña **Seguridad**. Para más información, consulte [Configurar seguridad de base de datos](database-security.md).

![](./media/environment-admin/database-security.png)

> [!NOTE]
> Los Administradores de entorno no tienen acceso para crear y administrar roles de usuario ni conjuntos de permisos para la base de datos de un entorno. Esta capacidad se limita a los miembros del rol de usuario **Propietario de la base de datos**.  
> 
> 

## <a name="data-policies"></a>Directivas de datos
Los datos de una organización deben protegerse para que no se compartan con usuarios que no deberían tener acceso a ellos. Para protegerlos, puede crear y aplicar directivas que definen con qué servicios de consumidor y datos empresariales específicos del conector se pueden compartir. Las directivas que definen cómo se pueden compartir los datos se conocen como directivas de prevención de pérdida de datos (DLP). Puede administrar las directivas DLP para sus entornos en la sección **Directivas de datos** del [centro de administración de PowerApps][1].  Para más información, consulte [Directivas para la prevención de pérdida de datos](prevent-data-loss.md).

![](./media/environment-admin/data-policies.png)

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes
### <a name="how-many-environments-can-i-create"></a>¿Cuántos entornos puedo crear?
Cada usuario puede crear un máximo de dos entornos.

### <a name="how-many-databases-can-i-provision"></a>¿Cuántas bases de datos puedo aprovisionar?
Cada usuario puede aprovisionar hasta dos bases de datos.

### <a name="can-i-rename-an-environment"></a>¿Puedo cambiar el nombre de un entorno?
Sí, esta funcionalidad está disponible en el centro de administración de PowerApps. Para más información, consulte [Administración de entornos en PowerApps](environments-administration.md#rename-your-environment).

### <a name="can-i-delete-an-environment"></a>¿Puedo eliminar un entorno?
Sí, esta funcionalidad está disponible en el centro de administración de PowerApps. Para más información, consulte [Administración de entornos en PowerApps](environments-administration.md#delete-your-environment).

### <a name="as-an-environment-admin-can-i-view-and-manage-all-resources-apps-flows-apis-etc-for-an-environment"></a>Como Administrador de entorno, ¿puedo ver y administrar todos los recursos (aplicaciones, flujos, API, etc.) para un entorno?
Sí, la capacidad para ver las aplicaciones y los flujos de un entorno está disponible en el centro de administración de PowerApps. Para más información, consulte [Visualización de una instancia de PowerApps creada en su organización](admin-view-apps.md).

### <a name="which-license-includes-common-data-service"></a>¿Qué licencia incluye Common Data Service?
Plan 2 de PowerApps.  Consulte la [página de precios de PowerApps][3] para más información sobre todos los planes que incluyen esta licencia.

### <a name="can-the-common-data-service-be-used-outside-of-an-environment"></a>¿Se puede usar Common Data Service fuera de un entorno?
No. Common Data Service requiere un entorno.

<!--Reference links in article-->
[1]: https://admin.powerapps.com
[2]: https://web.powerapps.com
[3]: https://powerapps.microsoft.com/pricing/
[4]: https://admin.flow.microsoft.com
