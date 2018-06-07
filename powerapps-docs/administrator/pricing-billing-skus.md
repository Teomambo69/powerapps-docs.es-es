---
title: Introducción a las licencias | Microsoft Docs
description: Información general de administración de licencias en PowerApps.
author: jamesol-msft
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: jamesol
ms.openlocfilehash: 03aa8fc5254529a337f7bbdf40428ab4a1042a92
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34168122"
---
# <a name="licensing-overview"></a>Introducción a las licencias
Las licencias de PowerApps se conceden por usuario. Todos y cada uno de los usuarios que acceda al servicio para crear y ejecutar aplicaciones necesitan una licencia. Los clientes de Office 365 y Dynamics 365 pueden beneficiarse inmediatamente de las funcionalidades de PowerApps y Microsoft Flow que incluyen estas ofertas. Los clientes que desean crear aplicaciones y flujos que acceden a orígenes de datos de fuera de Office 365 y Dynamics 365, o que necesitan más funcionalidad, pueden comprar suscripciones independientes a PowerApps y Microsoft Flow. Hay diferencias importantes en la funcionalidad entre estos grupos de licencias.

## <a name="pricing"></a>Precios
Para obtener la información más reciente sobre los precios de cada licencia de PowerApps, consulte la [página de precios de PowerApps][2].
Para obtener la información más reciente sobre los precios de cada licencia de Microsoft Flow, consulte la [página de precios de Microsoft Flow][1].

## <a name="licenses"></a>Licencias
### <a name="powerapps-for-office-365-and-dynamics-365"></a>PowerApps para Office 365 y Dynamics 365
Las funcionalidades de PowerApps para Office 365 y Dynamics 365 permiten a los usuarios crear y ejecutar aplicaciones en el contexto de estos servicios. Estas aplicaciones también se puede extender para sacar provecho de los datos en servicios en la nube comunes, entre los que se incluyen Box.com, Facebook, etc. Los usuarios con acceso a PowerApps a través de Office 365 y Dynamics 365 no pueden crear o ejecutar aplicaciones en bases de datos de Microsoft Common Data Service. La siguiente lista de planes de Office 365 y Dynamics 365 incluyen funcionalidades de PowerApps.

|  | Planes incluidos |
| --- | --- |
| ¿Qué planes de Microsoft Office 365 incluye PowerApps? |Estos planes incluyen PowerApps para Office 365: <br><br>Office 365 Business Essentials <br>Office 365 Business Premium <br>Office 365 Education <br>Office 365 Education Plus <br>Office 365 Enterprise E1 <br>Office 365 Enterprise E3 <br>Office 365 Enterprise E5<br><br>*Office 365 Enterprise E2 incluye las mismas funcionalidades que Office 365 Enterprise E1, y Office 365 Enterprise E4 incluye las mismas funcionalidades que Office 365 Enterprise E3.*<br><br>Office 365 Enterprise F1 incluye PowerApps para Office 365 Enterprise F1. |
| ¿Qué planes y aplicaciones de Microsoft Dynamics 365 incluye PowerApps? |Estas aplicaciones incluyen PowerApps para Dynamics 365:<br><br>Dynamics 365 for Team Members Enterprise Edition <br>Dynamics 365 for Financials Business Edition <br>Dynamics 365 for Team Members Business Edition<br>Dynamics 365 for Talent <br><br>Estos planes incluyen Plan 2 de PowerApps:<br><br>Dynamics 365 Customer Engagement Plan Enterprise Edition<br>Dynamics 365 Plan Enterprise Edition <br>Dynamics 365 for Sales Enterprise Edition <br>Dynamics 365 for Customer Service Enterprise Edition<br>Dynamics 365 for Case Management Enterprise Edition <br>Dynamics 365 for Operations Enterprise Edition <br>Dynamics 365 for Field Service Enterprise Edition <br>Dynamics 365 for Project Service Automation Enterprise Edition<br>Solución Microsoft Relationship Sales <br><br>*PowerApps para Dynamics 365 también se incluye en las suscripciones de Dynamics CRM Online Enterprise, Professional, Basic y Essential.* |

### <a name="powerapps-for-office-365-enterprise-f1"></a>PowerApps para Office 365 Enterprise F1
PowerApps se incluye con Office 365 Enterprise F1, con lo que los usuarios pueden ejecutar aplicaciones y automatizar flujos de trabajo. Sin embargo, este plan no permite a los usuarios crear aplicaciones (tal y como se puede hacer con otros planes, como Office 365 E1, E3 y E5). Esta tabla contiene información específica acerca de lo que pueden hacer los usuarios con PowerApps para Office 365 Enterprise F1:

| **Funcionalidades** | **PowerApps para Office 365 Enterprise F1** |
| --- | --- |
| **Crear y ejecutar aplicaciones** | |
| Ejecutar aplicaciones |Sí |
| Crear aplicaciones |No |
| Compartir aplicaciones |No |
| **Capacidad** | |
| El flujo se ejecuta por mes (por usuario) |750 |
| Almacenamiento de datos en Common Data Service (por usuario) |- |
| Almacenamiento de archivos en Common Data Service (por usuario) |- |
| **Conectividad** | |
| Conectarse a Office 365, Dynamics 365 y orígenes de datos similares |Sí |
| Conectar con Azure SQL Server, Dropbox, Twitter y muchos otros servicios basados en la nube |Sí |
| Conectarse a Salesforce, DB2 y muchos otros orígenes de datos a través de conectores premium |No |
| Acceder a los datos locales mediante el uso de una puerta de enlace |No |
| Crear conectores personalizados para administrar los datos en sus propios sistemas |No |
| **Common Data Service** | |
| Crear y ejecutar aplicaciones en Common Data Service |No |
| Modelar los datos en Common Data Service |No |
| Crear una base de datos de Common Data Service |No |
| **Administración** | |
| Admite directivas de datos establecidas por el administrador de Office 365 |Sí |
| Agregar colaboradores como creadores de entornos y administradores |No |
| Agregar colaboradores a los roles de base de datos |No |
| Establecer directivas de datos para entornos |No |

### <a name="powerapps-standalone-plan-1-and-plan-2"></a>PowerApps independiente, plan 1 y plan 2
Los planes de la versión independiente y con todas las características de PowerApps proporcionan a los usuarios la capacidad de crear y ejecutar aplicaciones en varios orígenes de datos que van más allá de Office 365 y Dynamics 365, como Salesforce y orígenes de datos locales, así como Common Data Service de Microsoft. Estas suscripciones también incluyen características que no están disponibles en los planes de Office 365 y Dynamics 365.

* Las suscripciones del plan 2 de Microsoft PowerApps son para los usuarios y administradores que necesitan funcionalidades totales de creación y ejecución. Estos usuarios tienen acceso a funcionalidades de administración importantes como ver el uso y establecer las directivas. Los usuarios del plan 2 de PowerApps pueden modelar los datos de Common Data Service.
* Las suscripciones del plan 1 de Microsoft PowerApps son para los usuarios que principalmente ejecutan aplicaciones. Estos usuarios también pueden crear aplicaciones y los flujos, pero no pueden modelar los datos de Common Data Service o ni realizar tareas de administración.

### <a name="powerapps-plan-2-free-trial"></a>Evaluación gratuita del plan 2 de PowerApps
PowerApps no ofrece una cuenta gratuita, pero los usuarios puede probar el plan 2 de PowerApps de forma gratuita durante 90 días. Durante el periodo de evaluación, los usuarios tienen acceso a todas las características del plan 2 de PowerApps. Para obtener información acerca de cómo suscribirse, consulte [Suscripción de autoservicio para PowerApps][3].

Cuando el período de evaluación expira, los usuarios tienen estas opciones:

* Los usuarios que tienen acceso a PowerApps o Microsoft Flow a través de Office 365 o Dynamics 365 también pueden acceder a PowerApps o Microsoft Flow.  Sin embargo, los usuarios perderán el acceso a las características que son exclusivas del plan 2, como se describe en la [página de precios de PowerApps][2].
* Los usuarios que no tienen acceso a través de Office 365 o Dynamics 365 pueden solicitar una ampliación del periodo de evaluación o adquirir un plan independiente. Para más información, consulte [Compra de PowerApps para la organización][4].

> [!NOTE]
>   Para comprar PowerApps para una organización, es preciso ser administrador general o de facturación de Office 365 de un inquilino, o bien debe crear un inquilino.
> 
> 

### <a name="powerapps-community-plan"></a>Plan de la comunidad de PowerApps
Si desea desarrollar habilidades y obtener información sobre PowerApps, Microsoft Flow y Common Data Service, el Plan de la comunidad de PowerApps es el plan adecuado para usted. El Plan de la comunidad de PowerApps le ofrece un entorno de desarrollo gratuito para uso individual para aprender utilizando la funcionalidad completa de PowerApps. Acuda [aquí][5] para el Plan de la comunidad de PowerApps.

## <a name="powerapps-includes-flow"></a>PowerApps incluye Flow
Las licencias de PowerApps siempre incluyen funcionalidades de Microsoft Flow.  Además de que se incluirse en PowerApps, Microsoft Flow también está disponible como servicio independiente. Para más información acerca de las funcionalidades específicas de Microsoft Flow que incluye cada licencia de PowerApps, consulte la [página de precios de PowerApps][2].

## <a name="resource-capacity-is-included-with-each-license"></a>Todas las licencias incluyen la capacidad de los recursos
Las licencias por usuario anteriores incluyen la capacidad de los recursos que se usa cuando se ejecuta una aplicación o un flujo. Dichos recursos incluyen el almacenamiento de datos, el almacenamiento de archivos y las ejecuciones de flujo. Las funcionalidades que se incluyen en las licencias por usuario se agrupan en el nivel de inquilino y cuando se agota la capacidad del inquilino, los clientes pueden adquirir capacidad adicional mediante licencias de complementos. La capacidad máxima de Common Data Service es 10 GB por base de datos y 5 TB para el almacenamiento de archivo por entorno. Si compra capacidad adicional y la capacidad disponible (con la combinación de licencias y complementos) es mayor que la capacidad máxima, puede usar la cantidad total en varios entornos. Para conocer la capacidad que incluye cada licencia de PowerApps, consulte la [página de precios de PowerApps][2].

## <a name="powerapps-licensing-examples"></a>Ejemplos de licencias PowerApps
Veamos un ejemplo. ABC Inc. tiene 1.000 empleados, de los que 700 tienen una licencia de Office 365 Enterprise 3. Al principio, un usuario avanzado crea una aplicación de línea de negocio que simplifica cómo se realiza el seguimiento de los pedidos de los clientes. Más adelante, el departamento de recursos humanos trabaja con el de TI para implementar una aplicación que informe del tiempo no trabajado y de las ausencias, y dicha aplicación se basa en Common Data Service.

### <a name="order-tracking-app"></a>Aplicación de seguimiento de pedidos
ABC Inc. comienza por desarrollar una aplicación para sus usuarios con licencia de Office 365. La aplicación reúne los datos de los clientes y de configuración de los productos almacenados en listas de Office 365 SharePoint con documentos de pedido de cliente, que se almacenan en Box.com. Dado que esta aplicación solo accede a los datos almacenados en Office 365 y a un servicio en la nube común cubierto por un conector estándar, las licencias de Office 365 que ya se posee cubren tanto la creación como el uso de esta aplicación.

**Licencias requeridas**: las 700 licencias de Office 365 Enterprise 3 que ya posee son suficientes.

### <a name="time-and-absence-app"></a>Aplicación de tiempo y de ausencias
En función de la rapidez y facilidad con que se haya iniciado la aplicación de seguimiento de pedidos, el grupo de recursos humanos de ABC da de alta la ayuda de TI para crear una aplicación que informe de las ausencias y del tiempo en toda la empresa.  Todos los empleados tendrán que usar esta aplicación para notificar sus horas laborales, vacaciones y días de baja por enfermedad.

Para esta aplicación, el departamento de TI selecciona Common Data Service como el sistema en el que se van a almacenar los datos de tiempo y de ausencia. Common Data Service proporciona las funcionalidades de seguridad y directiva de datos que requiere el departamento de TI para obtener información relacionada con los empleados. Asignan dos empleados de TI al proyecto para crear la base de datos y modelar los datos de la aplicación de tiempo y ausencia en Common Data Service. Estos empleados también son los responsables del seguimiento del uso de la aplicación y del establecimiento de la directiva que se aplica a los datos.

**Licencias requeridas**:

* Plan 2 de PowerApps, 10 licencias: los 10 administradores de TI que configurarán los entornos para que la empresa pruebe e implemente su aplicación, modele los datos en Common Data Service y establezca directivas de seguridad necesitarán que el plan 2 de PowerApps realice estas funciones.
* Plan 1 de PowerApps, 990 licencias:  será preciso que los 700 usuarios de Office 365 tengan una licencia del plan 1 de PowerApps, ya que esta aplicación utiliza datos almacenados fuera de  Office 365 (es decir, en Common Data Service). Los 290 usuarios restantes, que tienen licencia de Office 365 o del plan 2 de PowerApps, necesitarán que esta licencia tenga derechos para ejecutar la aplicación.

<!--Reference links in article-->
[1]: https://flow.microsoft.com/pricing/
[2]: https://powerapps.microsoft.com/pricing
[3]: https://powerapps.microsoft.com/tutorials/signup-for-powerapps/#try-powerapps-plan-2-for-free
[4]: https://powerapps.microsoft.com/tutorials/signup-for-powerapps-admin/
[5]: https://powerapps.microsoft.com/tutorials/dev-community-plan/
