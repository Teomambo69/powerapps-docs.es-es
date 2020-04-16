---
title: Requisitos de licencia para entidades | Microsoft Docs
description: Una explicación de los requisitos de licencia para las entidades de Common Data Service.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/20/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0a6b950c35043ecf47f45373f758ce62953945e7
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156546"
---
# <a name="license-requirements-for-entities"></a>Requisitos de licencia para entidades

> [!IMPORTANT]
> Para obtener la información más reciente sobre los requisitos de licencia para entidades, consulte [Manual de licencias de Power Apps](https://go.microsoft.com/fwlink/p/?linkid=2085130).

Los creadores de aplicaciones pueden usar la mayoría de entidades disponibles en Common Data Service (incluidas las entidades personalizadas y las entidades que forman parte del modelo común de datos) para crear aplicaciones y flujos para los usuarios que tienen una licencia de Plan 1 de Power Apps o de Plan 1 de Power Automate. En algunos casos, las entidades contienen lógica de negocios compleja o están ligadas a aplicaciones de Dynamics 365 para las que es necesario que los usuarios tengan una licencia específica. 


|Entidad    |Descripción    |Requisito    |
|---------|---------|---------|
|Entidades con lógica de negocios compleja   | Estas son entidades que usan una lógica de negocios compleja de servidor. Por ejemplo, cualquier entidad que use un flujo de trabajo en tiempo real o un complemento de código.       |  [Plan de 2 Power Apps](https://powerapps.microsoft.com/pricing/) o [Plan 2 de Flow](https://flow.microsoft.com/pricing/)        |
|Entidades restringidas  |  Son entidades que no son estándar con Common Data Service pero se incluyen en la aplicación basadas en modelo disponible en Dynamics 365 (como Dynamics 365 Sales o Dynamics 365 Customer Service) o una solución de terceros. Por ejemplo, las entidades de artículo de conocimientos, de objetivo y de derecho.     |  [Un plan de Dynamics 365](https://dynamics.microsoft.com/pricing/)      | 


> [!NOTE]
> Las aplicaciones y los flujos que usan estas entidades requieren que la aplicación y el usuario del flujo tengan una licencia adecuada (no el creador o desarrollador de la aplicación o flujo).

## <a name="entities-with-complex-business-logic"></a>Entidades con lógica de negocios compleja
Las entidades que incluyen la siguiente lógica compleja de servidor requieren que los usuarios de una aplicación o flujo en el que se usen estas entidades tengan una licencia de Plan 2 de Power Apps o de Plan 2 de Power Automate:

* Complementos de código (para obtener más información, consulte [Desarrollo de complementos](/powerapps/developer/common-data-service/plug-ins))
* Flujos de trabajo en tiempo real (para obtener más información, consulte [Procesos de flujo de trabajo](/flow/workflow-processes))

    > [!NOTE]
    >  Solo los flujos de trabajo que se convierten a un flujo de trabajo en tiempo real se consideran en tiempo real y sincrónicos. Los flujos de trabajo que se ejecutan en segundo plano pueden usarse con el plan adecuado de Power Apps y no requieren licencias adicionales.

Para saber si ha agregado lógica de negocios compleja a las entidades, revise la lista de ensamblados de complementos y de flujos de trabajo configurados en el entorno. Para la lista de entidades que pueden contener lógica del lado del servidor después de instalar una aplicación basada en modelo en Dynamics 365 (como Dynamics 365 Sales o Dynamics 365 Customer Service), consulte [Entidades complejas que requieren licencias de Power Apps Plan 2](data-platform-complex-entities.md)  

### <a name="impacting-license-requirements-when-adding-complex-business-logic"></a>Elementos que afectan a los requisitos de licencia al agregar lógica de negocios compleja
Los creadores de aplicaciones pueden agregar complementos de código y flujos de trabajo en tiempo real a las entidades de Common Data Service, pero el hacerlo podría cambiar los requisitos de licencia para los usuarios de aplicaciones ya implementadas. Los creadores de aplicaciones deben ser prudentes al agregar lógica de negocios compleja a una entidad y primero deben comprobar qué aplicaciones usan la entidad y si los usuarios de esas aplicaciones tienen las licencias adecuadas.

## <a name="restricted-entities"></a>Entidades restringidas
Algunas entidades que están ligadas a la funcionalidad de las aplicaciones de Dynamics 365 requieren que los usuarios de la aplicación tengan la licencia correspondiente para esa aplicación si desean crear, actualizar, o eliminar registros dentro de las entidades. Para obtener una lista completa de las entidades restringidas, consulte [Entidades restringidas que requieren licencias de Dynamics 365](data-platform-restricted-entities.md).

## <a name="licensing-examples"></a>Ejemplos de licencias
Barb e Isaac van a crear aplicaciones en Power Apps mediante Common Data Service para almacenar los datos.

Barb va a crear dos aplicaciones de lienzo:

* La aplicación 1 &ndash; usa la entidad Cita junto con una entidad personalizada que almacena información relacionada
* La aplicación 2 &ndash; usa la entidad Cita junto con la entidad Incidente, que es una entidad restringida

Isaac va a crear dos aplicaciones controladas por modelos:

* La aplicación 3 &ndash; usa la entidad Cita junto con una entidad personalizada que almacena información relacionada
* La aplicación 4 &ndash; usa la entidad Cita junto con la entidad Incidente, que es una entidad restringida

Barb e Isaac necesitan las licencias siguientes:
* Barb necesita una licencia de Plan 1 de Power Apps para crear aplicaciones de lienzo usando Common Data Service. Si tuviera que crear una base de datos o una entidad personalizada, necesitaría una licencia de Plan 2 de Power Apps.

* Isaac necesita una licencia de Plan 2 de Power Apps para crear aplicaciones controladas por modelos.

Los usuarios de la aplicación necesitan las licencias siguientes:
* Los usuarios de la aplicación 1 sólo necesitan una licencia de Plan 1 o de Plan 2 de Power Apps, ya que la aplicación no tiene ninguna entidad con lógica de negocios compleja o entidades restringidas.

* Los usuarios de la aplicación 2 necesitan una licencia de Dynamics 365 Customer Service, Enterprise Edition (o un plan de Dynamics 365 o Dynamics 365 Customer Engagement) porque la aplicación incluye una entidad restringida.

* Los usuarios de la aplicación 3 necesitan una licencia de Plan 2 de Power Apps, ya que es una aplicación controlada por modelos.

* Los usuarios de la aplicación 4 necesitan una licencia de Dynamics 365 for Customer Service, Enterprise Edition (o un plan de Dynamics 365 Customer Engagement) porque la aplicación incluye una entidad restringida.

    El plan de Dynamics 365 for Customer Service incluye una licencia de Power Apps Plan 2, que permite a los usuarios ejecutar aplicaciones basadas en modelo.

Ahora, veamos lo que sucede cuando Isaac agrega un flujo de trabajo en tiempo real a la entidad personalizada que Barb e Isaac usan en sus aplicaciones.

Barb e Isaac necesitan las licencias siguientes:
* Barb sigue necesitando una licencia de Plan 1 de Power Apps para crear aplicaciones de lienzo usando Common Data Service.

* Isaac sigue necesitando una licencia de Plan 2 de Power Apps para crear aplicaciones controladas por modelos.

Los usuarios de la aplicación necesitan las licencias siguientes:
* Los usuarios de la aplicación 1 ahora necesitan una licencia de Plan 2 de Power Apps, ya que la aplicación contiene una entidad con un flujo de trabajo en tiempo real.

* Los usuarios de la aplicación 2 siguen necesitando una licencia de Dynamics 365 for Customer Service, Enterprise Edition (o un plan de Dynamics 365 Customer Engagement) porque la aplicación incluye una entidad restringida. 

* Los usuarios de la aplicación 3 siguen necesitando una licencia de Plan 2 de Power Apps, ya que es una aplicación basada en modelos.

* Los usuarios de la aplicación 4 siguen necesitando una licencia de Dynamics 365 for Customer Service, Enterprise Edition (o un plan de Dynamics 365 Customer Engagement) porque la aplicación incluye una entidad restringida.

    El plan de Dynamics 365 for Customer Service incluye una licencia de Power Apps Plan 2, que permite a los usuarios ejecutar aplicaciones basadas en modelo.

La única aplicación a la que afecta este cambio es la aplicación 1, que antes requería una licencia de Plan 1 de Power Apps, pero ahora requiere una licencia de Plan 2 de Power Apps, porque contiene una entidad con lógica de negocios compleja. 

## <a name="more-about-licensing"></a>Más información sobre las licencias
Para obtener más información acerca de las licencias de Power Apps y Dynamics 365, consulte [Información general de las licencias](../../administrator/pricing-billing-skus.md).
