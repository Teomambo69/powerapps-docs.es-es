---
title: Administración de entornos | Microsoft Docs
description: Administración de entornos en PowerApps, incluida la creación, el cambio de nombre, la eliminación y la seguridad
author: manasmams
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 07/30/2018
ms.author: manasma
ms.openlocfilehash: 02b25dd627e85b638a113c1c0aceee16d7df6275
ms.sourcegitcommit: 2e7b621066cdc3e7be329d5213ecfee0b4223641
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39349096"
---
# <a name="administer-environments-in-powerapps"></a>Administrar entornos en PowerApps
En el [Centro de administración de PowerApps][1], administre los entornos que ha creado y aquellos a los que se le ha agregado con el rol Administrador de entorno o Administrador del sistema. Desde el centro de administración, puede realizar estas acciones administrativas:

* Crear entornos.
* Cambiar el nombre de entornos.
* Agregar o quitar un usuario o grupo del rol Administrador de entorno o Creador de entorno.
* Aprovisionar una base de datos de Common Data Service para el entorno.
* Establecer directivas para la prevención de pérdida de datos.
* Establecer directivas de seguridad de base de datos (abiertas o restringidas por los roles de base de datos).
* Los miembros del rol Administrador global del inquilino de Azure AD (incluye administradores globales de Office 365) también pueden administrar todos los entornos creados en su inquilino y establecer directivas para todo el inquilino.

Para más información, consulte [Environments overview](environments-overview.md) (Información general de los entornos).

## <a name="access-the-powerapps-admin-center"></a>Acceso al centro de administración de PowerApps
Para acceder al centro de administración de PowerApps:

* Vaya directamente a [admin.powerapps.com][1], o bien

* Vaya a [powerapps.com][2] y seleccione el icono de engranaje en el encabezado de navegación.

    ![](./media/environment-admin/powerapps-gear-dropdown.png)

Para administrar un entorno en el centro de administración de PowerApps, debe tener uno de estos roles:

* El rol Administrador de entorno del entorno o el rol Administrador del sistema, O BIEN

* El rol Administrador global de su inquilino de Azure AD o de Office 365.

También necesita una licencia de Plan 2 de PowerApps o de Plan 2 de Microsoft Flow para acceder al centro de administración. Para más información, consulte la [página de precios de PowerApps][3].

> [!IMPORTANT]
> Los cambios que realice en el centro de administración de PowerApps afectan al [centro de administración de Microsoft Flow][4] y viceversa.

## <a name="create-an-environment"></a>Creación de un entorno
Para obtener instrucciones sobre cómo crear un entorno, vea [Create an environment](create-environment.md) (Creación de un entorno).

## <a name="view-your-environments"></a>Visualización de los entornos
Cuando se abre el centro de administración, la pestaña Entornos aparece de forma predeterminada y muestra todos los entornos para los que es Administrador de entorno (como se ve a continuación):

![](./media/environment-admin/environment-list-new.png)

Si es miembro del rol Administrador global del inquilino de Azure AD o de Office 365, todos los entornos que hayan creado los usuarios de su inquilino aparecen porque es automáticamente Administrador de entorno para todos ellos.

## <a name="rename-your-environment"></a>Cambio del nombre del entorno
1. Abra el [centro de administración de PowerApps][1], busque el entorno cuyo nombre vaya a cambiar en la lista y haga clic o pulse en él.

    ![](./media/environment-admin/environment-list-updated3.png)

2. Haga clic o pulse en **Detalles**.

    ![](./media/environment-admin/environment-rename-details-2.png)
3. En el cuadro de texto **Nombre**, escriba el nuevo nombre y haga clic en **Guardar**.

    ![](./media/environment-admin/environment-rename-2.png)

    Si ha creado la base de datos en el entorno, no verá esta opción. Puede cambiar el nombre del entorno desde el Centro de administración de Dynamics 365 si hace clic en el vínculo de la pestaña **Detalles**.

    ![](./media/environment-admin/Delete-D365AdminCenter.png)


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
2. Haga clic en la pestaña **Detalles**.
3. Seleccione **Crear mi base de datos**.

    ![](./media/environment-admin/Create-DB-From-Details.png)


Después de crear una base de datos, elija un modelo de seguridad. Para más información, consulte [Configurar seguridad de base de datos](database-security.md).

## <a name="manage-security-for-your-environments"></a>Administración de la seguridad para los entornos

### <a name="environment-permissions"></a>Permisos de entorno
En un entorno, todos los usuarios en el inquilino de Azure AD lo son también de dicho entorno. No obstante, para que puedan desempeñan un rol con más privilegios, se les debe agregar a un rol de entorno específico. Los entornos tienen dos roles integrados que proporcionan acceso a los permisos dentro de un entorno:

* El rol **Administrador de entorno** (o el rol **Administrador del sistema**) puede realizar todas las acciones administrativas en un entorno, incluidas las siguientes:
    * Agregar o quitar un usuario de los roles Administrador de entorno o Creador de entorno.

    * Aprovisionar una base de datos de Common Data Service para el entorno.

    * Ver y administrar todos los recursos creados en un entorno.

    * Establecer directivas para la prevención de pérdida de datos. Para más información, consulte [Directivas para la prevención de pérdida de datos](prevent-data-loss.md).

  > [!NOTE]
  > Si el entorno tiene la base de datos, debe asignar a los usuarios el rol **Administrador del sistema**, en lugar del rol **Administrador de entorno**.

* El rol **Creador de entorno** puede crear recursos dentro de un entorno, incluidas aplicaciones, conexiones, conectores personalizados, puertas de enlace y flujos con Microsoft Flow. Los creadores de entorno también pueden distribuir las aplicaciones que creen en un entorno a otros usuarios de su organización. Pueden compartir la aplicación con usuarios individuales, grupos de seguridad o todos los usuarios de la organización. Para más información, consulte [Compartir una aplicación en PowerApps](../maker/canvas-apps/share-app.md).

Para asignar un usuario o un grupo de seguridad a un rol de entorno, un Administrador de entorno puede realizar estos pasos en el [centro de administración de PowerApps][1]:

1. Seleccione el entorno en la tabla de entornos.

    ![](./media/environment-admin/choose-environment-updated.png)
2. Haga clic en la pestaña **Seguridad**.
3. Si no hay ninguna base de datos creada en el entorno:

    a. Seleccione el rol **Administrador de entorno** o **Creador de entorno**.

    ![](./media/environment-admin/choose-environment-role.png)

    b. Especifique los nombres de uno o varios usuarios o grupos de seguridad en Azure Active Directory o especifique que desea agregar toda la organización.

    ![](./media/environment-admin/enter-name.png)

    c. Seleccione **Guardar** para actualizar las asignaciones al rol de entorno.

4. Si se crea una base de datos en el entorno:

    a. Agregue el usuario al entorno y haga clic en el vínculo para asignarle un rol.

    ![](./media/database-security/security-adduser.png)

    b. Seleccione el usuario de la lista de usuarios en el entorno o instancia.

    ![](./media/environment-admin/D365-Select-User.png)

    c. Asigne el rol al usuario.

    ![](./media/environment-admin/D365-Assign-Role.png)

    d. Haga clic en **Aceptar** para actualizar las asignaciones al rol de entorno.


> [!NOTE]
> Los usuarios o grupos asignados a estos roles de entorno no tienen acceso automáticamente a la base de datos del entorno (si existe) y un propietario de base de datos debe darles acceso por separado. Para más información, consulte [Configurar seguridad de base de datos](database-security.md).  
>
>

### <a name="database-security"></a>Seguridad de base de datos
La capacidad de crear y modificar un esquema de base de datos y conectarse a los datos almacenados en una base de datos que está aprovisionada en su entorno se controla mediante los roles de usuario y los conjuntos de permisos de la base de datos. Puede administrar los roles de usuario y los conjuntos de permisos para la base de datos de su entorno desde las secciones **Roles de usuario** y **Conjuntos de permisos** de la pestaña **Seguridad**. Para más información, consulte [Configurar seguridad de base de datos](database-security.md).

![](./media/environment-admin/D365-Assign-Role.png)

## <a name="data-policies"></a>Directivas de datos
Los datos de una organización deben protegerse para que no se compartan con usuarios que no deberían tener acceso a ellos. Para protegerlos, puede crear y aplicar directivas que definen con qué servicios de consumidor y datos empresariales específicos del conector se pueden compartir. Las directivas que definen cómo se pueden compartir los datos se conocen como directivas de prevención de pérdida de datos (DLP). Puede administrar las directivas DLP para sus entornos en la sección **Directivas de datos** del [centro de administración de PowerApps][1].  Para más información, consulte [Directivas para la prevención de pérdida de datos](prevent-data-loss.md).

![](./media/environment-admin/data-policies.png)

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes
### <a name="how-many-environments-and-databases-can-i-create"></a>¿Cuántos entornos y cuántas bases de datos puedo crear?
Puede crear hasta dos entornos de prueba y dos entornos de producción, en función de sus licencias. Para obtener más información, consulte [este vínculo](environments-overview.md#creating-an-environment). Cada usuario puede aprovisionar dos bases de datos en dos entornos de prueba y dos entornos de producción, en función de sus licencias. 

### <a name="which-license-includes-common-data-service"></a>¿Qué licencia incluye Common Data Service?
Plan 2 de PowerApps.  Consulte la [página de precios de PowerApps][3] para más información sobre todos los planes que incluyen esta licencia.

### <a name="while-trying-to-create-a-new-environment-i-am-getting-an-error-how-should-i-resolve-it"></a>Al intentar crear un entorno, obtengo un error. ¿Cómo puedo resolver esto?
Si obtiene el mensaje de error "El plan no es compatible con el tipo de entorno seleccionado o se alcanzó el límite de ese tipo de entorno." , puede que se deba a uno de estos dos motivos:

1. Ya ha usado la cuota de creación de un tipo de entorno específico. Supongamos que estaba creando un entorno de prueba y ha recibido este mensaje de error. Significa que ya ha aprovisionado dos entornos de prueba. Puede ver todos los entornos en el [centro de administración de PowerApps][1].
Si lo prefiere, puede eliminar un entorno existente de ese tipo específico y crear otro nuevo. Asegúrese de no perder los datos, las aplicaciones, los flujos y otros recursos que quiera conservar.

2. No tiene ninguna cuota de creación de ese tipo de entorno específico. Compruebe qué tipo de entorno puede crear [aquí](environments-overview.md#creating-an-environment).

Si recibe cualquier otro mensaje de error o tiene alguna pregunta más, póngase en contacto con nosotros [aquí][5].

### <a name="while-trying-to-create-a-database-in-an-environment-i-am-getting-an-error-how-should-i-resolve-it"></a>Al intentar crear una base de datos en un entorno, obtengo un error. ¿Cómo puedo resolver esto?
En los escenarios siguientes, puede que obtenga un error al intentar crear una base de datos:

1. **Entorno predeterminado**: actualmente, la creación de una base de datos no es compatible con el entorno predeterminados del inquilino. 

2. **Entorno para un uso individual**: puede obtener un entorno para su uso individual registrándose en el plan de comunidad de PowerApps. Si aún no ha creado la base de datos, no podrá aprovisionar ninguna base de datos en el entorno para su uso individual. 

3. **Entorno en una región diferente de la principal de su inquilino de AAD**: actualmente, solo puede aprovisionar una base de datos en los entornos creados en la región principal de su inquilino de Azure Active Directory. La capacidad de aprovisionar una base de datos en otras regiones estará disponible próximamente. Por lo tanto, asegúrese de que la región y la ubicación predeterminada del inquilino coincidan para poder crear una base de datos en ella.

4. **Creación de bases de datos no admitida en algunas regiones**: en determinadas regiones, aún no se pueden crear bases de datos. Por ejemplo, los países de Sudamérica. Así pues, si la ubicación principal de su inquilino está en Sudamérica, por el momento no podrá aprovisionar una base de datos en ningún entorno. 
    
Estamos trabajando para admitir todos los casos mencionados anteriormente.
Si recibe cualquier otro mensaje de error o tiene alguna pregunta más, póngase en contacto con nosotros [aquí][5].

### <a name="when-will-my-trial-environment-expire"></a>¿Cuándo expirará el entorno de prueba?   
Los entornos de prueba expiran una vez transcurridos 30 días de su creación. Si no quiere que su entorno expire, podrá convertirlo en un entorno de producción. Esta funcionalidad estará disponible pronto, pero, mientras tanto, no expirará ningún entorno de prueba.

### <a name="does-my-current-database-created-with-previous-version-of-the-common-data-service-also-gets-counted-in-the-quota"></a>¿Mi base de datos actual creada con una versión anterior de Common Data Service también se contabiliza en la cuota?
Si tenía una base de datos creada con una versión anterior de Common Data Service, también se contabilizará en la cuota de su entorno de producción. Si crea una base de datos en un entorno anterior al 15 de marzo de 2018, se contabilizará en el entorno de producción.

### <a name="can-i-rename-an-environment"></a>¿Puedo cambiar el nombre de un entorno?
Sí, esta funcionalidad está disponible en el centro de administración de PowerApps. Para más información, consulte [Administración de entornos en PowerApps](environments-administration.md#rename-your-environment).

### <a name="can-i-delete-an-environment"></a>¿Puedo eliminar un entorno?
Sí, esta funcionalidad está disponible en el centro de administración de PowerApps. Para más información, consulte [Administración de entornos en PowerApps](environments-administration.md#delete-your-environment).
Tenga en cuenta que, actualmente, no puede eliminar un entorno de producción que contenga una base de datos que use la última versión de Common Data Service. Esta opción estará disponible próximamente.

### <a name="as-an-environment-admin-can-i-view-and-manage-all-resources-apps-flows-apis-etc-for-an-environment"></a>Como Administrador de entorno, ¿puedo ver y administrar todos los recursos (aplicaciones, flujos, API, etc.) para un entorno?
Sí, la capacidad para ver las aplicaciones y los flujos de un entorno está disponible en el centro de administración de PowerApps. Para más información, consulte [Visualización de una instancia de PowerApps creada en su organización](admin-view-apps.md).



<!--Reference links in article-->
[1]: https://admin.powerapps.com
[2]: https://web.powerapps.com
[3]: https://powerapps.microsoft.com/pricing/
[4]: https://admin.flow.microsoft.com
[5]: https://go.microsoft.com/fwlink/p/?linkid=871628