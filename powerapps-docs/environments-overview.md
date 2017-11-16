---
title: "Información general de los entornos | Microsoft Docs"
description: "Qué son los entornos y cómo se usan"
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
ms.date: 11/01/2016
ms.author: jamesol
ms.openlocfilehash: 425376f218b01a9edab4dae90555b33cd1d26a80
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="environments-overview"></a>Información general sobre los entornos
Los entornos son un concepto nuevo en PowerApps. En palabras simples, un entorno es un espacio para almacenar, administrar y compartir flujos, aplicaciones y datos empresariales de la organización. También sirven como contenedores para separar aplicaciones que pueden tener roles distintos, otros requisitos de seguridad o distintos públicos objetivos. Cómo se elige aprovechar los entornos depende de la organización y de las aplicaciones que se intenta compilar. Por ejemplo:

1. Puede elegir solo compilar aplicaciones en un entorno único.
2. Puede crear entornos separados que agrupen las versiones de prueba y producción de las aplicaciones.
3. Puede crear entornos separados que correspondan a equipos o departamentos específicos de la empresa, donde cada uno contenga los datos y aplicaciones pertinentes para cada público.
4. También puede crear entornos separados para las distintas ramas globales de la empresa.  

## <a name="environment-scope"></a>Ámbito del entorno
Cada entorno se crea bajo un inquilino de Azure AD y solo los usuarios dentro de ese inquilino pueden tener acceso a sus recursos. Un entorno también está enlazado a una ubicación geográfica, como Estados Unidos. Cuando crea una aplicación en un entorno, esa aplicación se enruta solo a centros de datos en esa ubicación geográfica. Cualquier elemento que cree en ese entorno (incluidas conexiones, puertas de enlace, flujos con Microsoft Flow, etc.) también están enlazados a la ubicación de su entorno.

Cada entorno puede tener una o ninguna base de datos de Common Data Service, lo que proporciona almacenamiento para las aplicaciones. La capacidad de crear una base de datos para el entorno dependerá de la licencia que compre para PowerApps y su permiso dentro de ese entorno. Para más información, consulte [Información sobre precios](pricing-billing-skus.md).

Cuando se crea una aplicación en un entorno, esa aplicación solo se puede conectar a los orígenes de datos que también están implementados en el mismo entorno, incluidas conexiones, puertas de enlace, flujos y bases de datos de Common Data Service.  Por ejemplo, consideremos un escenario en el que creó dos entornos llamados "Prueba" y "Desarrollo", y que creó una base de datos de Common Data Service en cada uno de los entornos. Si crea una aplicación en el entorno "Prueba", solo podrá conectarse a la base de datos de "Prueba": no se podrá conectar a la base de datos de "Desarrollo".

También hay un proceso para mover recursos entre los entornos. Para más información, consulte [Migrar recursos](environment-and-tenant-migration.md).

![](./media/environments-overview/Environments.png)

## <a name="environment-permissions"></a>Permisos de entorno
Los entornos tienen dos roles integrados que proporcionan acceso a los permisos dentro de un entorno:

* El rol Administrador de entorno puede realizar todas las acciones administrativas en un entorno, incluidas las siguientes:
  
  o    Agregar o quitar un usuario o grupo del rol Administrador de entorno o Creador de entorno
  
  o    Aprovisionar una base de datos de Common Data Service para el entorno
  
  o    Ver y administrar todos los recursos creados dentro de un entorno
  
  o    Establecer directivas para la prevención de pérdida de datos Para más información, consulte [Directivas para la prevención de pérdida de datos](prevent-data-loss.md).
* El rol Creador de entorno puede crear recursos dentro de un entorno, incluidas aplicaciones, conexiones, conectores personalizados, puertas de enlace y flujos con Microsoft Flow.

Los creadores de entorno también pueden distribuir las aplicaciones que compilan en un entorno a otros usuarios de la organización, al compartir la aplicación con usuarios individuales, grupos de seguridad, o bien a todos los usuarios de la organización. Para más información, consulte [Compartir una aplicación en PowerApps](share-app.md).

Los usuarios o grupos asignados a estos roles de entorno no tienen acceso automáticamente a la base de datos del entorno (si existe) y un propietario de base de datos debe darles acceso por separado. Para más información, consulte [Configurar seguridad de base de datos](database-security.md).

Un Administrador de entorno puede asignar usuarios o grupos de seguridad a cualquiera de estos dos roles desde el [centro de administración de PowerApps][1]. Para más información, consulte [Administración de entorno](environments-administration.md).

![](./media/environments-overview/EnvironmentRoles.png)

## <a name="the-default-environment"></a>El entorno predeterminado
PowerApps crea automáticamente un entorno predeterminado único para cada inquilino, el que se comparte entre todos los usuarios de ese inquilino. Cada vez que un usuario nuevo se suscribe a PowerApps, se agrega automáticamente al rol Creador del entorno predeterminado. El entorno predeterminado se crea en la región más cercana a la región predeterminada del inquilino de AAD.

> [!NOTE]
> Ningún usuario se agregará automáticamente al rol Administrador de entorno del entorno predeterminado. Para más información, consulte [Administración de entorno](environments-administration.md).
> 
> 

El nombre del entorno predeterminado tiene el siguiente formato: "{nombre del inquilino de Azure AD} (valor predeterminado)"

![](./media/environments-overview/DefaultEnvironment.png)

## <a name="choosing-an-environment"></a>Elección de un entorno
Con la introducción de los entornos, ahora verá una experiencia nueva cuando ingrese a [https://web.powerapps.com](https://web.powerapps.com).  Las aplicaciones, conexiones y otros elementos visibles en el sitio ahora se filtrarán según el entorno actual seleccionado.  El entorno actual se especifica en el selector de entornos que se encuentra cerca del borde derecho del encabezado. Para elegir un entorno distinto, pulse o haga clic en el selector y verá una lista de los entornos disponibles. Pulse o haga clic en el entorno que desea ingresar.

El selector mostrará un entorno si usted cumple con una de las siguientes condiciones:

1. Es miembro del rol Administrador de entorno del entorno.
2. Es miembro del rol Creador de entorno del entorno.
3. No es administrador ni creador de entorno del entorno en cuestión, pero tiene acceso de "colaborador" al menos a una aplicación dentro del entorno. Para más información, consulte cómo [compartir una aplicación](share-app.md). **Nota**: En este caso, no podrá crear aplicaciones en este entorno. Solo podrá modificar las aplicaciones existentes que se compartieron con usted.

![](./media/environments-overview/EnvironmentPicker.png)

## <a name="creating-an-environment"></a>Creación de un entorno
### <a name="who-can-create-environments"></a>¿Quién puede crear entornos?
La licencia determina si se pueden crear entornos.

| Licencia | Se permite crear entornos |
| --- | --- |
| PowerApps P2 |√ |
| Versión de prueba de PowerApps P2 |√ |
| PowerApps P1 |x |
| Versión de prueba de PowerApps P1 |x |
| Planes de Dynamics 365 |x |
| Planes de Office 365 |x |
| Planes de equipos y aplicaciones de Dynamics 365 |x |

Cada usuario puede crear un máximo de dos entornos.

### <a name="where-can-environments-be-created"></a>¿Dónde se pueden crear entornos?
Podrá crear entornos nuevos desde [PowerApps.com][2] y desde el [centro de administración de PowerApps][1]. Si crea un entorno, se le agregará automáticamente al rol Administrador de entorno de dicho entorno. No hay límite para el número de entornos en los que puede participar como miembro del rol Administrador de entorno o Creador de entorno. Para más información, consulte [Administración de entorno](environments-administration.md).

![](./media/environments-overview/CreateEnvironmentDialog.png)

## <a name="what-will-change-for-powerapps-preview-users"></a>¿Qué cambiará para los usuarios de PowerApps versión preliminar?
Cualquier usuario que haya participado en la versión preliminar de PowerApps verá algunos cambios en su experiencia debido a la introducción de los entornos.  La tabla siguiente muestra qué pueden esperar los usuarios en Estados Unidos y fuera de Estados Unidos:

| Usuario | Qué sucede |
| --- | --- |
| Usuario de la versión preliminar que creó una base de datos de Common Data Service |Verá un entorno llamado "Entorno de {su nombre}" que contiene la base de datos de Common Data Service que creó en la versión preliminar y cualquier aplicación que haya compilado en ella.  Se le agregará al rol Creador de entorno y Administrador de entorno de este entorno y como Propietario de base de datos de la base de datos en cuestión. Cuando PowerApps esté disponible al público general, actualizaremos los metadatos de Common Data Service. El impacto de este cambio significa que podrá seguir usando las entidades y aplicaciones que ya compiló en la base de datos de Common Data Service que creó en la versión preliminar; sin embargo, no podrá crear campos o entidades en dicha base de datos. Pronto publicaremos instrucciones sobre cómo puede crear un entorno con una base de datos que contenga los metadatos actualizados y migrar las aplicaciones a ese entorno.<br>**Nota**: Si cualquiera de las aplicaciones que compiló en la base de datos de Common Data Service en versión preliminar también usa un conector personalizado como origen de datos, se interrumpirá temporalmente en este entorno porque todos los conectores personalizados se migrarán al entorno predeterminado. Deberá volver a crear el conector personalizado en este entorno para reparar las aplicaciones afectadas. |
| Usuario de versión preliminar en Estados Unidos |Los siguientes recursos que creó durante el período de versión preliminar de PowerApps estarán disponibles en el entorno predeterminado de su inquilino:<br>- Todas las aplicaciones que creó (excepto las que estén conectadas a una base de datos de Common Data Service de la versión preliminar).<br>- Todas las conexiones y los conectores personalizados que creó.<br>- Todas las puertas de enlace de datos locales que instaló. |
| Usuario de versión preliminar fuera de Estados Unidos |Además del entorno predeterminado, también verá un entorno llamado "{Inquilino de Azure AD} (de la versión preliminar)" que contiene los recursos siguientes que creó durante el período de versión preliminar de PowerApps:<br>- Todas las aplicaciones que creó (excepto las que estén conectadas a una base de datos de Common Data Service de la versión preliminar).<br>- Todas las conexiones y los conectores personalizados que creó.<br>- Todas las puertas de enlace de datos locales que instaló.<br>Se le agregará al rol Creador de entorno de este entorno. |

Un *usuario de versión preliminar* es un usuario que usó Microsoft PowerApps antes de su lanzamiento a disponibilidad general.

Dos semanas después de que PowerApps ingrese a su disponibilidad general, los entornos que contienen contenido de la versión preliminar se marcarán como de solo lectura (a excepción del entorno predeterminad); todas las aplicaciones y flujos existentes seguirán funcionando en estos entornos, pero no podrá crear aplicaciones ni flujos. Se recomienda encarecidamente que los usuarios de estos entornos migren su contenido al entorno predeterminado o a otro entorno personalizado. Consulte el siguiente blog (que se publicará esta semana) para obtener más información sobre el proceso de migración: consulte el [blog sobre anuncios de características de Common Data Service][3].

### <a name="example-environments-for-a-preview-user-in-us"></a>Entornos de ejemplo para un usuario de versión preliminar en Estados Unidos
![](./media/environments-overview/USuser1.png)

### <a name="example-environments-for-a-preview-user-not-in-us"></a>Entornos de ejemplo para un usuario de versión preliminar fuera de Estados Unidos
![](./media/environments-overview/non-USuser1.png)

## <a name="managing-environments-for-your-organization"></a>Administración de entornos de la organización
Con la introducción de los entornos, también lanzamos el Centro de administración de PowerApps, donde puede administrar todos los entornos que creó o en los que se le agregó al rol Administrador de entorno. En el Centro de administración, puede realizar todas las acciones administrativas en un entorno, incluidas las siguientes:

* Agregar o quitar un usuario o grupo del rol Administrador de entorno o Creador de entorno.  Para más información, consulte [Administración de entorno](environments-administration.md).
* Aprovisionar una base de datos de Common Data Service para el entorno. Para más información, consulte [Crear una base de datos de Common Data Service](create-database.md).
* Establecer directivas para la prevención de pérdida de datos. Para más información, consulte [Directivas para la prevención de pérdida de datos](prevent-data-loss.md).
* Establecer directivas de seguridad de base de datos (abiertas o restringidas por los roles de base de datos). Para más información, consulte [Configurar seguridad de base de datos](database-security.md).
* Los miembros del rol Administrador global del inquilino de Azure AD (incluye administradores globales de Office 365) también administra todos los entornos creados en su inquilino y establece directivas para todo el inquilino desde el Centro de administración de PowerApps.

<!--Reference links in article-->
[1]: https://admin.powerapps.com
[2]: https://web.powerapps.com
[3]: https://aka.ms/cdspreviewtoga
