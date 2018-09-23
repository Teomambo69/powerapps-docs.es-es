---
title: Requisitos de licencia para entidades | Microsoft Docs
description: Una descripción de los requisitos de licencia para las entidades en Common Data Service (CDS) for Apps.
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/01/2018
ms.author: clwesene
ms.openlocfilehash: 4350f7141adf0fbce3e74271d6aff48c18c857e2
ms.sourcegitcommit: 2bcc36916f0c591466eb3e007c2d30b99f2315c6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40009268"
---
# <a name="license-requirements-for-entities"></a>Requisitos de licencia para entidades
Los creadores de aplicaciones pueden usar la mayoría de las entidades disponibles en Common Data Service (CDS) for Apps (incluidas las entidades personalizadas y las que forman parte de Common Data Service) para crear aplicaciones y flujos para los usuarios que tengan una licencia del plan 1 de PowerApps o de Microsoft Flow. En algunos casos, las entidades contienen lógica de negocios compleja o están asociadas a aplicaciones de Dynamics 365 que requieren que los usuarios de la aplicación tengan una licencia específica. 


|Entidad    |Descripción    |Requisito    |
|---------|---------|---------|
|Entidades con lógica de negocios compleja   | Se trata de entidades que usan una lógica de negocios compleja del lado servidor. Por ejemplo, cualquier entidad que use un flujo de trabajo o un complemento de código en tiempo real.       |  [Plan 2 de PowerApps](https://powerapps.microsoft.com/pricing/) o [Plan 2 de Flow](https://flow.microsoft.com/pricing/)        |
|Entidades restringidas  |  Se trata de entidades que no son estándares en Common Data Service for Apps, pero se incluyen en una aplicación del plan Customer Engagement de Dynamics 365 o en una solución de terceros. Por ejemplo, el artículo de conocimientos, el objetivo y las entidades de derecho.     |  [Plan de Dynamics 365](https://dynamics.microsoft.com/pricing/)      | 


> [!NOTE]
> Las aplicaciones y los flujos que usan estas entidades requieren que el usuario de la aplicación y el flujo tenga la licencia apropiada, no el fabricante o el desarrollador de la aplicación o el flujo.

## <a name="entities-with-complex-business-logic"></a>Entidades con lógica de negocios compleja
Las entidades que incluyen la siguiente lógica compleja del lado servidor requieren que los usuarios de una aplicación o flujo en el que se usen estas entidades tengan una licencia del Plan 2 de PowerApps o del Plan 2 de Microsoft Flow:

* Complementos de código (para obtener más información, vea [Desarrollo de complementos](https://docs.microsoft.com/dynamics365/customer-engagement/developer/plugin-development)).
* Flujos de trabajo en tiempo real (para obtener más información, vea [Procesos de flujo de trabajo](https://docs.microsoft.com/dynamics365/customer-engagement/customize/workflow-processes)).

    > [!NOTE]
    >  Solo los flujos de trabajo que se convierten en un flujo de trabajo en tiempo real se consideran de tiempo real y sincrónicos. Los flujos de trabajo que se ejecutan en segundo plano se pueden seguir usando con el plan de PowerApps adecuado y no requieren licencias adicionales.

Para saber si ha agregado o no lógica de negocios compleja a las entidades, revise la lista de ensamblados de complementos y flujos de trabajo configurados en el entorno. Para consultar la lista de entidades que pueden contener una lógica del lado servidor después de instalar una aplicación de Dynamics 365, vea [Entidades complejas que requieren licencias del plan 2 de PowerApps](data-platform-complex-entities.md).  

### <a name="impacting-license-requirements-when-adding-complex-business-logic"></a>Requisitos de licencia con impacto al agregar lógica de negocios compleja
Los creadores de aplicaciones pueden agregar complementos de código y flujos de trabajo en tiempo real a entidades de CDS for Apps, pero al hacerlo se cambiarían los requisitos de licencia para los usuarios de las aplicaciones ya implementadas. Los creadores de aplicaciones deben tener cuidado al agregar lógica de negocios compleja a una entidad y primero deben comprobar qué aplicaciones usan la entidad y si los usuarios de esas aplicaciones tienen las licencias correspondientes.

## <a name="restricted-entities"></a>Entidades restringidas
Algunas entidades asociadas a la funcionalidad de las aplicaciones de Dynamics 365 requieren que los usuarios de la aplicación tengan la licencia correspondiente para ese producto si quieren crear, actualizar o eliminar registros dentro de las entidades. Para obtener una lista completa de las entidades restringidas, vea [Entidades restringidas que requieren licencias de Dynamics 365](data-platform-restricted-entities.md).

## <a name="licensing-examples"></a>Ejemplos de licencias
Isaac y Barb están creando aplicaciones en PowerApps con CDS for Apps para almacenar los datos.

Barb va a crear dos aplicaciones de lienzo:

* Aplicación 1 &ndash; se usa la entidad Contacto junto con una entidad personalizada que almacena información relacionada.
* Aplicación 2 &ndash; se usa la entidad Contacto junto con la entidad Incidente, que es una entidad restringida.

Isaac va a crear dos aplicaciones controladas por modelos:

* Aplicación 3 &ndash; se usa la entidad Contacto junto con una entidad personalizada que almacena información relacionada.
* Aplicación 4 &ndash; se usa la entidad Contacto junto con la entidad Incidente, que es una entidad restringida.

Isaac y Barb necesitan las licencias siguientes:
* Barb necesita una licencia del Plan 1 de PowerApps para crear aplicaciones de lienzo con CDS for Apps. Si tiene crear una base de datos o una entidad personalizada, necesitará una licencia del Plan 2 de PowerApps.

* Isaac necesita una licencia del Plan 2 de PowerApps para compilar aplicaciones controladas por modelos.

Los usuarios de la aplicación necesitan las licencias siguientes:
* Los usuarios de la Aplicación 1 solo necesitan una licencia del Plan 1 o 2 de PowerApps, puesto que la aplicación no contiene entidades con lógica de negocios compleja ni entidades restringidas.

* Los usuarios de la Aplicación 2 necesitan una licencia de Dynamics 365 for Customer Service, edición Enterprise (o un plan de Dynamics 365 o Dynamics 365 Customer Engagement), ya que la aplicación incluye una entidad restringida.

* Los usuarios de la Aplicación 3 necesitan una licencia del Plan 2 de PowerApps, ya que es una aplicación controlada por modelos.

* Los usuarios de la Aplicación 4 necesitan una licencia de Dynamics 365 for Customer Service, edición Enterprise (o un plan de Dynamics 365 o Dynamics 365 Customer Engagement), ya que la aplicación incluye una entidad restringida.

    El plan Dynamics 365 for Customer Service incluye una licencia del Plan 2 de PowerApps, que permite a los usuarios ejecutar aplicaciones controladas por modelos.

Ahora, veamos lo que sucede cuando Isaac agrega un flujo de trabajo en tiempo real a la entidad personalizada que él y Barb usan en las aplicaciones.

Isaac y Barb necesitan las licencias siguientes:
* Barb sigue necesitando una licencia del Plan 1 de PowerApps para crear aplicaciones de lienzo con CDS for Apps.

* Isaac sigue necesitando una licencia del Plan 2 de PowerApps para compilar aplicaciones controladas por modelos.

Los usuarios de la aplicación necesitan las licencias siguientes:
* Los usuarios de la Aplicación 1 ahora necesitan una licencia del Plan 2 de PowerApps, puesto que la aplicación contiene una entidad con un flujo de trabajo en tiempo real.

* Los usuarios de la Aplicación 2 siguen necesitando una licencia de Dynamics 365 for Customer Service, edición Enterprise (o un plan de Dynamics 365 o Dynamics 365 Customer Engagement), ya que la aplicación incluye una entidad restringida. 

* Los usuarios de la Aplicación 3 siguen necesitando una licencia del Plan 2 de PowerApps, ya que es una aplicación controlada por modelos.

* Los usuarios de la Aplicación 4 siguen necesitando una licencia de Dynamics 365 for Customer Service, edición Enterprise (o un plan de Dynamics 365 o Dynamics 365 Customer Engagement), ya que la aplicación incluye una entidad restringida.

    El plan Dynamics 365 for Customer Service incluye una licencia del Plan 2 de PowerApps, que permite a los usuarios ejecutar aplicaciones controladas por modelos.

La única aplicación que se ve afectada por este cambio es la Aplicación 1, que anteriormente requería una licencia del Plan 1 de PowerApps, pero que ahora requiere una licencia del Plan 2 de PowerApps, porque contiene una entidad con lógica de negocios compleja. 

## <a name="more-about-licensing"></a>Más información sobre la concesión de licencias
Para obtener más información sobre las licencias de PowerApps y Dynamics 365, vea [Introducción a las licencias](../../administrator/pricing-billing-skus.md).
