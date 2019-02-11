---
title: Introducción a las licencias | Microsoft Docs
description: Información general de administración de licencias en PowerApps.
author: jamesol-msft
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 02/05/2019
ms.author: jamesol
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: 323c88f7d1e6ab9a476334f5888dcbaa6ef5ba74
ms.sourcegitcommit: 1da1338ba84db210f8517d6d15747f01398a9341
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2019
ms.locfileid: "55760618"
---
# <a name="licensing-overview"></a>Introducción a las licencias

## <a name="about-powerapps-licenses"></a>Sobre las licencias de PowerApps

- Las licencias de PowerApps se conceden por usuario. 
- Las licencias de usuario se asignan según el nombre de usuario; cada usuario necesita una licencia independiente para ejecutar aplicaciones. 
- Las licencias de PowerApps no limitan la creación de aplicaciones.
- PowerApps está disponible con dos planes independientes: PowerApps Plan 1 y PowerApps Plan 2. 
- PowerApps Plan 1 proporciona acceso a Common Data Service para aplicaciones para almacenar y administrar datos. Los usuarios pueden ejecutar aplicaciones de lienzo basadas en Common Data Service para aplicaciones, usar conectores premium, y acceder a datos de aplicaciones personalizadas o a datos locales. 
- PowerApps Plan 2 permite a los usuarios ejecutar aplicaciones controladas por modelos con complementos de código y flujos de trabajo en tiempo real. Para obtener información detallada, visite la [página de precios de PowerApps](https://powerapps.microsoft.com/pricing/).  
- Además de los planes independientes, las funcionalidades de PowerApps también se incluyen en determinados planes de Office 365 y Dynamics 365, lo que permite a los clientes extender y personalizar Office 365 y Dynamics 365 con las funcionalidades de PowerApps y Microsoft Flow que incluyen estas ofertas. Las aplicaciones y los planes exclusivos de Dynamics 365 incluyen una licencia completa de PowerApps P2. Obtenga más información [aquí](#powerapps-for-dynamics-365).

Hay diferencias importantes de funcionalidad entre estos grupos de licencias que se describen con más detalle a continuación.

## <a name="pricing"></a>Precios
Para obtener la información más reciente sobre los precios de cada licencia de PowerApps (Plan 1 y Plan 2), consulte la [página de precios de PowerApps](https://powerapps.microsoft.com/pricing/). Para obtener la información más reciente sobre los precios de cada licencia de Microsoft Flow, consulte la [página de precios de Microsoft Flow](https://preview.flow.microsoft.com/pricing/).

## <a name="licenses"></a>Licencias
### <a name="powerapps-for-office-365"></a>PowerApps para Office 365
Las funcionalidades de PowerApps para Office 365 permiten a los usuarios extender y personalizar la experiencia de Office con PowerApps y Microsoft Flow.  Los usuarios pueden crear aplicaciones de lienzo basadas en datos de Office 365. Estas aplicaciones de productividad también pueden utilizar datos fuera de Office 365 conectándose a servicios comunes, como Box.com, Facebook y muchos más mediante conectores estándar.  


|**Funcionalidades**  |**PowerApps para Office 365**  |
|---------|---------|
|Crear, ejecutar y compartir aplicaciones     |Sí<sup>1</sup>         |
|Ejecutar aplicaciones de lienzo en el contexto de Office 365     |Sí         |
|Conectarse a datos de Office 365      | Sí        |
|Conectarse a servicios en la nube mediante conectores estándar     |  Sí       |
|Ejecutar aplicaciones en un explorador o un dispositivo móvil con PowerApps para iOS y Android     |  Sí       |
|Ejecutar aplicaciones de lienzo sin conexión     | Sí        |
|Compatibilidad con directivas de datos establecidas por el administrador de Office 365     |  Sí       |
|Ejecuciones de Flow por usuario/mes (se incluye Flow para Office 365)     |  2000       |
|Acceder a datos locales o usar conectores premium o personalizados     |  -       |
|Administración y almacenamiento de datos en Common Data Service para aplicaciones     |   -      |

<sup>1</sup>Para PowerApps para Office 365 Enterprise F1, consulte la sección siguiente.

#### <a name="the-following-office-365-plans-include-powerapps-for-office-365"></a>Los siguientes planes de Office 365 incluyen PowerApps para Office 365.

|     | Planes incluidos |
| --- | --- |
|| ¿Qué planes de Microsoft Office 365 incluye PowerApps? |Estos planes incluyen PowerApps para Office 365:<br/><br/>Office 365 Business Essentials<br/>Office 365 Business Premium<br/>Office 365 A1 para profesores<br/>Office 365 A1 para estudiantes<br/>Office 365 A1 Plus para profesores<br/>Office 365 A1 Plus para estudiantes<br/>Office 365 A3 para profesores<br/>Office 365 A3 para estudiantes<br/>Office 365 A3 para Student Use Benefit<br/>Office 365 A5 para Student Use Benefit<br/>Office 365 A5<br/>Office 365 A5 para profesores<br/>Office 365 A5 para estudiantes<br/>Office 365 Education E3 para profesores<br/>Office 365 Education E3 para estudiantes<br/>Office 365 Education for Homeschool para profesores<br/>Office 365 Education for Homeschool para estudiantes<br/>Office 365 Enterprise E1<br/>Office 365 Enterprise E2<br/>Office 365 Enterprise E3<br/>Office 365 Enterprise E3 Developer<br/>Office 365 Enterprise E3 sin ProPlus<br/>Office 365 Enterprise E5<br/>Office 365 Enterprise F1 incluye PowerApps para Office 365 Enterprise F1.|

### <a name="powerapps-for-office-365-enterprise-f1"></a>PowerApps para Office 365 Enterprise F1
PowerApps se incluye con Office 365 Enterprise F1, con lo que los usuarios pueden ejecutar aplicaciones y automatizar flujos de trabajo. Sin embargo, este plan no permite a los usuarios crear aplicaciones (tal y como se puede hacer con otros planes de Office mencionados anteriormente). Esta tabla contiene información específica acerca de lo que pueden hacer los usuarios con PowerApps para Office 365 Enterprise F1:

| **Funcionalidad** | **PowerApps para Office 365 Enterprise F1** |
| --- | --- |
| Ejecutar aplicaciones |Sí |
| Ejecuciones de Flow por usuario/mes (se incluye Flow para Office 365) |750 |
|Ejecutar aplicaciones de lienzo en el contexto de Office 365| Sí|
|Conectarse a datos de Office 365 | Sí|
|Conectarse a servicios en la nube mediante conectores estándar|Sí|
|Ejecutar aplicaciones en un explorador o un dispositivo móvil con PowerApps para iOS y Android|Sí|
|Ejecutar aplicaciones de lienzo sin conexión|Sí|
|Compatibilidad con directivas de datos establecidas por el administrador de Office 365|Sí|
|Crear y compartir aplicaciones|-|
|Acceder a datos locales o usar conectores premium o personalizados| - |
|Administración y almacenamiento de datos en Common Data Service para aplicaciones|-|

### <a name="powerapps-standalone-plan-1-and-plan-2"></a>PowerApps independiente, plan 1 y plan 2
Los planes de PowerApps independientes proporcionan a los usuarios la capacidad de crear y ejecutar aplicaciones en varios orígenes de datos que van más allá de Office 365, como Salesforce y orígenes de datos locales y personalizados. Estos planes también incluyen acceso a Common Data Service para aplicaciones para almacenar y administrar datos. Obtenga más información sobre Common Data Service para aplicaciones [aquí](../maker/common-data-service/data-platform-intro.md).  

- Las suscripciones de Microsoft PowerApps Plan 1 son para los usuarios que necesitan ejecutar aplicaciones de lienzo y acceder a datos locales, datos de aplicaciones personalizadas y servicios en la nube mediante conectores premium.
- Las suscripciones Microsoft PowerApps Plan 2 son para los usuarios y administradores que necesitan acceder a más funcionalidades. Estos usuarios pueden ejecutar aplicaciones controladas por modelos que pueden incluir complementos de código personalizado y flujos de trabajo en tiempo real. Estos usuarios tienen acceso a funcionalidades de administración importantes como ver el uso y establecer las directivas. 

### <a name="powerapps-plan-2-free-trial"></a>Evaluación gratuita del plan 2 de PowerApps
Los usuarios pueden probar PowerApps Plan 2 de forma gratuita durante 30 días. Durante el periodo de evaluación, los usuarios tienen acceso a todas las características del plan 2 de PowerApps. Para obtener información sobre cómo suscribirse, consulte [Suscripción de autoservicio para PowerApps](../maker/signup-for-powerapps.md). 

Cuando el período de evaluación expira, los usuarios tienen estas opciones:

- Los usuarios que tienen acceso a PowerApps o Microsoft Flow a través de planes o aplicaciones de Office 365 o Dynamics 365 pueden seguir accediendo a PowerApps o Microsoft Flow. Sin embargo, los usuarios perderán el acceso a las características que son exclusivas del plan 2, como se describe en la página de precios de PowerApps. Las aplicaciones y los planes exclusivos de Dynamics 365 incluyen PowerApps Plan 2.
- Los usuarios que no tienen acceso a través de Office 365 o Dynamics 365 (aplicaciones y planes exclusivos) pueden solicitar una extensión del periodo de evaluación o adquirir un plan independiente. Para obtener más información, consulte [Compra de PowerApps para la organización](signup-for-powerapps-admin.md).

> [!NOTE]
>  Para comprar PowerApps para una organización, es preciso ser administrador general o de facturación de Office 365 de un inquilino, o bien debe crear un inquilino.

### <a name="powerapps-community-plan"></a>Plan de la comunidad de PowerApps
Si desea desarrollar habilidades y obtener información sobre PowerApps, Microsoft Flow y Common Data Service, el Plan de la comunidad de PowerApps es el plan adecuado para usted. El Plan de la comunidad de PowerApps le ofrece un entorno de desarrollo gratuito para uso individual para aprender utilizando la funcionalidad completa de PowerApps. Visite esta [página](https://go.microsoft.com/fwlink/p/?LinkId=866544) para ver el Plan de la comunidad de PowerApps.

## <a name="resource-capacity-is-included-with-each-license"></a>Todas las licencias incluyen la capacidad de los recursos
Las licencias por usuario incluyen la capacidad de los recursos que se usa cuando se ejecuta una aplicación o un flujo. Dichos recursos incluyen el almacenamiento de datos y las ejecuciones de flujo. Las funcionalidades que se incluyen en las licencias por usuario se agrupan en el nivel de inquilino y cuando se agota la capacidad del inquilino, los clientes pueden adquirir capacidad adicional mediante licencias de complementos. Para obtener información detallada, consulte la [página de precios de PowerApps](https://powerapps.microsoft.com/pricing).

> [!NOTE]
> Hemos quitado la capacidad máxima de 10 GB por instancia (base de datos) de Common Data Service. Puede adquirir hasta 30 TB de capacidad que se usarán en las instancias del inquilino.

### <a name="powerapps-for-dynamics-365"></a>PowerApps para Dynamics 365

PowerApps es la plataforma para personalizar y extender aplicaciones de Dynamics 365 en el contexto de los derechos de uso de Dynamics 365.

Las aplicaciones exclusivas de Dynamics 365 puede personalizarse mediante las funcionalidades de PowerApps y Microsoft Flow. Los planes empresariales y las aplicaciones empresariales de Dynamics 365 también incluyen PowerApps Plan 2, que ofrece la capacidad de crear y ejecutar aplicaciones personalizadas independientes. 

#### <a name="powerapps-included-in-select-dynamics-365-apps-and-plans"></a>Funcionalidades de PowerApps incluidas en las aplicaciones y los planes exclusivos de Dynamics 365

Las aplicaciones y los planes empresariales exclusivos de Dynamics 365 incluyen PowerApps Plan 2, que ofrece personalizaciones más avanzadas, así como la capacidad de crear y ejecutar aplicaciones personalizadas independientes. 

| **Funcionalidad** | **Aplicaciones de Dynamics 365 exclusivas<br/> (Professional, Team Member, Talent Attract y Onboard)** |**Planes y aplicaciones empresariales de Dynamics 365** |
| --- | --- | --- |
| Personalizar y extender aplicaciones y flujos de trabajo en el contexto de los derechos de uso de aplicaciones de Dynamics 365 |Sí | Sí|
| Crear y ejecutar aplicaciones con entidades personalizadas | Sí (se pueden agregar hasta 15 entidades personalizadas por aplicación; las personalizaciones se deben asignar a los derechos de uso o al contexto de las aplicaciones)| Sí|
| Acceder a entidades restringidas de Dynamics 365 en el contexto de los derechos de uso de aplicaciones de Dynamics 365| Crear, leer, actualizar y eliminar| Crear, leer, actualizar y eliminar|
|Acceder a API de aplicaciones de Dynamics 365| Sí<sup>1</sup> |Sí|
|Ejecutar PowerApps de forma independiente (aplicaciones de lienzo y controladas por modelos)|-|Sí|
|Capacidad de Flow incluida (agrupados en inquilinos)|2000 ejecuciones de Flow por usuario/mes|15 000 ejecuciones de Flow por usuario/mes (se incluye Flow Plan 2)|

<sup>1</sup>La licencia de Team Member no proporciona acceso a las API de aplicaciones de Dynamics 365.

Descargue la [guía de licencias de Dynamics 365](https://go.microsoft.com/fwlink/p/?LinkId=866544) para obtener más información sobre los derechos de uso de las aplicaciones y los planes específicos de Dynamics 365.

#### <a name="these-dynamics-365-apps-can-be-customized-using-powerapps-and-microsoft-flow-capabilities"></a>Estas aplicaciones de Dynamics 365 pueden personalizarse mediante las funcionalidades de PowerApps y Microsoft Flow.

Dynamics 365 for Sales Professional<br/>
Dynamics 365 for Customer Service Professional<br/>
Dynamics 365 for Talent: Captación<br/>
Dynamics 365 for Talent: Incorporación<br/>
Dynamics 365 Team Member

#### <a name="these-dynamics-365-apps-and-plans-include-powerapps-p2"></a>Estos planes y aplicaciones de Dynamics 365 incluyen PowerApps P2.

Dynamics 365 Business Central<br/>
Dynamics 365 for Sales Enterprise<br/>
Dynamics 365 for Customer Service<br/>
Dynamics 365 for Field Service<br/>
Dynamics 365 for Project Service Automation<br/>
Dynamics 365 for Talent<br/>
Dynamics 365 for Retail <br/>
Plan Dynamics 365 Customer Engagement Plan<br/>
Plan Unified Dynamics 365 Operations<br/>
Plan de Dynamics 365


## <a name="powerapps-licensing-examples"></a>Ejemplos de licencias PowerApps
Veamos un ejemplo. ABC Inc. tiene 1.000 empleados, de los que 700 tienen una licencia de Office 365 Enterprise 3. Al principio, un usuario avanzado crea una aplicación de línea de negocio que simplifica cómo se realiza el seguimiento de los pedidos de los clientes. Más adelante, el departamento de recursos humanos trabaja con el de TI para implementar una aplicación que informe del tiempo no trabajado y de las ausencias, y dicha aplicación se basa en Common Data Service.

### <a name="order-tracking-app"></a>Aplicación de seguimiento de pedidos
ABC Inc. comienza por desarrollar una aplicación para sus usuarios con licencia de Office 365. La aplicación reúne los datos de los clientes y de configuración de los productos almacenados en listas de Office 365 SharePoint con documentos de pedido de cliente, que se almacenan en Box.com. Dado que esta aplicación solo accede a los datos almacenados en Office 365 y a un servicio en la nube común cubierto por un conector estándar, las licencias de Office 365 que ya se posee cubren tanto la creación como el uso de esta aplicación.

**Licencias requeridas**:  las 700 licencias de Office 365 Enterprise 3 que ya posee son suficientes.

### <a name="time-and-absence-app"></a>Aplicación de tiempo y de ausencias
En función de la rapidez y facilidad con que se haya iniciado la aplicación de seguimiento de pedidos, el grupo de recursos humanos de ABC da de alta la ayuda de TI para crear una aplicación que informe de las ausencias y del tiempo en toda la empresa. Todos los empleados tendrán que usar esta aplicación para notificar sus horas laborales, vacaciones y días de baja por enfermedad.

Para esta aplicación, el departamento de TI selecciona Common Data Service como el sistema en el que se van a almacenar los datos de tiempo y de ausencia. Common Data Service proporciona las funcionalidades de seguridad y directiva de datos que requiere el departamento de TI para obtener información relacionada con los empleados. Asignan dos empleados de TI al proyecto para crear la base de datos y modelar los datos de la aplicación de tiempo y ausencia en Common Data Service. Estos empleados también son los responsables del seguimiento del uso de la aplicación y del establecimiento de la directiva que se aplica a los datos.

**Licencias requeridas**:

- **PowerApps Plan 2. 10 licencias**. los 10 administradores de TI que configurarán los entornos para que la empresa pruebe e implemente su aplicación, y establezca directivas de seguridad de datos que necesitará PowerApps Plan 2 para realizar estas funciones.
- **PowerApps Plan 1. 990 licencias**: será preciso que los 700 usuarios de Office 365 tengan una licencia PowerApps Plan 1, ya que esta aplicación utiliza datos almacenados fuera de Office 365 (es decir, en Common Data Service). Los 290 usuarios restantes, que no tienen licencia de Office 365 o de PowerApps Plan 2, necesitarán esta licencia para ejecutar la aplicación.


