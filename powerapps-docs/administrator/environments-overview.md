---
title: Información general de los entornos | Microsoft Docs
description: Información sobre entornos en PowerApps y cómo utilizarlos
author: manasmams
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: manasma
ms.openlocfilehash: 4973265baf701851ac5c2e8bca9da541b246c068
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34167801"
---
# <a name="environments-overview"></a>Información general sobre los entornos
Un entorno es un espacio para almacenar, administrar y compartir los datos empresariales, las aplicaciones y los flujos de la organización. También sirven como contenedores para separar aplicaciones que pueden tener roles distintos, otros requisitos de seguridad o distintos públicos objetivos. Cómo se elige aprovechar los entornos depende de la organización y de las aplicaciones que se intenta compilar. Por ejemplo:

* Puede elegir solo compilar aplicaciones en un entorno único.
* Puede crear entornos separados que agrupen las versiones de prueba y producción de las aplicaciones.
* Puede crear entornos separados que correspondan a equipos o departamentos específicos de la empresa, donde cada uno contenga los datos y aplicaciones pertinentes para cada público.
* También puede crear entornos separados para las distintas ramas globales de la empresa.  

## <a name="environment-scope"></a>Ámbito del entorno
Cada entorno se crea bajo un inquilino de Azure AD y solo los usuarios dentro de ese inquilino pueden tener acceso a sus recursos. Un entorno también está enlazado a una ubicación geográfica, como Estados Unidos. Cuando crea una aplicación en un entorno, esa aplicación se enruta solo a centros de datos en esa ubicación geográfica. Cualquier elemento que cree en ese entorno (incluidas conexiones, puertas de enlace, flujos con Microsoft Flow, etc.) también están enlazados a la ubicación de su entorno.

Cada entorno puede tener una o ninguna base de datos de Common Data Service, lo que proporciona almacenamiento para las aplicaciones. La capacidad de crear una base de datos para el entorno dependerá de la licencia que compre para PowerApps y su permiso dentro de ese entorno. Para más información, consulte [Información sobre precios](pricing-billing-skus.md).

Cuando se crea una aplicación en un entorno, esa aplicación solo se puede conectar a los orígenes de datos que también están implementados en el mismo entorno, incluidas conexiones, puertas de enlace, flujos y bases de datos de Common Data Service.  Por ejemplo, consideremos un escenario en el que creó dos entornos llamados "Prueba" y "Desarrollo", y que creó una base de datos de Common Data Service en cada uno de los entornos. Si crea una aplicación en el entorno "Prueba", solo podrá conectarse a la base de datos de "Prueba": no se podrá conectar a la base de datos de "Desarrollo".

También hay un proceso para mover recursos entre los entornos. Para más información, consulte [Migrar recursos](environment-and-tenant-migration.md).

![](./media/environments-overview/Environments.png)

## <a name="environment-permissions"></a>Permisos de entorno
Los entornos tienen dos roles integrados que proporcionan acceso a los permisos dentro de un entorno:

* El rol Administrador de entorno puede realizar todas las acciones administrativas en un entorno, incluidas las siguientes:

    * Agregar o quitar un usuario o grupo de los roles Administrador de entorno o Creador de entorno.

    * Aprovisionar una base de datos de Common Data Service para el entorno.

    * Ver y administrar todos los recursos creados en un entorno.

    * Establecer directivas para la prevención de pérdida de datos. Para más información, consulte [Directivas para la prevención de pérdida de datos](prevent-data-loss.md).

    Después de crear la base de datos en el entorno, puede usar el rol Administrador del sistema en lugar del rol Administrador de entorno.

* El rol Creador de entorno puede crear recursos dentro de un entorno, incluidas aplicaciones, conexiones, conectores personalizados, puertas de enlace y flujos con Microsoft Flow.

Los creadores de entorno también pueden distribuir las aplicaciones que compilan en un entorno a otros usuarios de la organización, al compartir la aplicación con usuarios individuales, grupos de seguridad, o bien a todos los usuarios de la organización. Para más información, consulte [Compartir una aplicación en PowerApps](../maker/canvas-apps/share-app.md).

Los usuarios o grupos asignados a estos roles de entorno no tienen acceso automáticamente a la base de datos del entorno (si existe) y un propietario de base de datos debe darles acceso por separado. Para más información, consulte [Configurar seguridad de base de datos](database-security.md).

Un Administrador de entorno puede asignar usuarios o grupos de seguridad a cualquiera de estos dos roles desde el [centro de administración de PowerApps][1]. Para obtener más información, vea [Administer environments in PowerApps](environments-administration.md) (Administración de entornos en PowerApps).

![](./media/environments-overview/EnvironmentRoles.png)

## <a name="the-default-environment"></a>El entorno predeterminado
PowerApps crea automáticamente un entorno predeterminado único para cada inquilino, el que se comparte entre todos los usuarios de ese inquilino. Cada vez que un usuario nuevo se suscribe a PowerApps, se agrega automáticamente al rol Creador del entorno predeterminado. El entorno predeterminado se crea en la región más cercana a la región predeterminada del inquilino de AAD.

> [!NOTE]
> Ningún usuario se agregará automáticamente al rol Administrador de entorno del entorno predeterminado. Para obtener más información, vea [Administer environments in PowerApps](environments-administration.md) (Administración de entornos en PowerApps).
>
>

El nombre del entorno predeterminado tiene el siguiente formato: "{nombre del inquilino de Azure AD} (valor predeterminado)"

![](./media/environments-overview/DefaultEnvironment.png)

## <a name="production-and-trial-environments"></a>Entornos de prueba y producción
Puede crear entornos para un propósito diferente. Un entorno de prueba permite probar el entorno y la base de datos con la experiencia de Common Data Service. Caduca después de un período de tiempo concreto. Para obtener más información, vea [Administer environments in PowerApps](environments-administration.md) (Administración de entornos en PowerApps).

## <a name="choosing-an-environment"></a>Elección de un entorno
Con la introducción de los entornos, ahora verá una experiencia nueva cuando ingrese en [https://web.powerapps.com](https://web.powerapps.com).  Las aplicaciones, conexiones y otros elementos visibles en el sitio ahora se filtrarán según el entorno actual seleccionado.  El entorno actual se especifica en el selector de entornos que se encuentra cerca del borde derecho del encabezado. Para elegir un entorno distinto, pulse o haga clic en el selector y verá una lista de los entornos disponibles. Pulse o haga clic en el entorno que desea ingresar.

El selector mostrará un entorno si usted cumple con una de las siguientes condiciones:

* Es miembro del rol Administrador de entorno del entorno.
* Es miembro del rol Creador de entorno del entorno.
* No es administrador ni creador de entorno del entorno en cuestión, pero tiene acceso de "colaborador" al menos a una aplicación dentro del entorno. Para más información, consulte cómo [compartir una aplicación](../maker/canvas-apps/share-app.md). En este caso, no podrá crear aplicaciones en este entorno. Solo podrá modificar las aplicaciones existentes que se compartieron con usted.

![](./media/environments-overview/EnvironmentPicker.png)

## <a name="creating-an-environment"></a>Creación de un entorno
### <a name="who-can-create-environments"></a>¿Quién puede crear entornos?
La licencia determina si se pueden crear entornos.

| Licencia | Se permite crear entornos |
| --- | --- |
| PowerApps P2 |√ (Dos entornos de producción y dos de prueba)|
| Versión de prueba de PowerApps P2 |√ (Dos entornos de prueba)|
| PowerApps P1 |x |
| Versión de prueba de PowerApps P1 |x |
| Planes de Dynamics 365 |x |
| Planes de Office 365 |x |
| Planes de equipos y aplicaciones de Dynamics 365 |x |


### <a name="where-can-environments-be-created"></a>¿Dónde se pueden crear entornos?
Podrá crear entornos nuevos desde [PowerApps.com][2] y desde el [centro de administración de PowerApps][1]. Si crea un entorno, se le agregará automáticamente al rol Administrador de entorno para ese entorno. No hay límite para el número de entornos en los que se puede participar como miembro del rol Administrador de entorno o Creador de entorno. Para obtener más información sobre los entornos, vea [Administer environments in PowerApps](environments-administration.md) (Administración de entornos en PowerApps). Para obtener instrucciones sobre cómo crear un entorno, vea [Create an environment](create-environment.md) (Creación de un entorno).

![](./media/environments-overview/CreateEnvironmentDialog-New.png)


## <a name="managing-environments-for-your-organization"></a>Administración de entornos de la organización
En el Centro de administración de PowerApps, se pueden administrar todos los entornos que se han creado o a los que se le ha agregado con el rol Administrador de entorno. En el Centro de administración, puede realizar todas las acciones administrativas en un entorno, incluidas las siguientes:

* Agregar o quitar un usuario o grupo del rol Administrador de entorno o Creador de entorno.  Para obtener más información, vea [Administer environments in PowerApps](environments-administration.md) (Administración de entornos en PowerApps).
* Aprovisionar una base de datos de Common Data Service para el entorno. Para más información, consulte [Crear una base de datos de Common Data Service](create-database.md).
* Establecer directivas para la prevención de pérdida de datos. Para más información, consulte [Directivas para la prevención de pérdida de datos](prevent-data-loss.md).
* Establecer directivas de seguridad de base de datos (abiertas o restringidas por los roles de base de datos). Para más información, consulte [Configurar seguridad de base de datos](database-security.md).
* Los miembros del rol Administrador global del inquilino de Azure AD (incluye administradores globales de Office 365) también administra todos los entornos creados en su inquilino y establece directivas para todo el inquilino desde el Centro de administración de PowerApps.

<!--Reference links in article-->
[1]: https://admin.powerapps.com
[2]: https://web.powerapps.com
[3]: https://aka.ms/cdspreviewtoga
