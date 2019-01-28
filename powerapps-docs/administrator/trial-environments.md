---
title: Entornos de prueba | Microsoft Docs
description: Obtenga acceso anticipado a las funcionalidades con el programa de versión preliminar de PowerApps
author: manasmams
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 01/09/2019
ms.author: manasma
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: bd05c4c1251058d464034de71d9b1c287e714190
ms.sourcegitcommit: 170deba334c922157bbb826c795bed3fa858b85e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2019
ms.locfileid: "54196203"
---
# <a name="about-trial-environments"></a>Acerca de los entornos de prueba

En la actualidad, puede crear dos tipos de entornos de Common Data Service (CDS) para aplicaciones: prueba o producción. Un entorno de prueba es útil para probar aplicaciones de Dynamics 365 for Customer Engagement sin costo alguno. Los entornos de prueba expiran después de 30 días.

Abra la página **Entornos** para ver los tipos de entorno que tiene y la fecha de caducidad próxima para los entornos de prueba:

> [!div class="mx-imgBorder"] 
> ![Entornos de PowerApps](media/powerapps-environments75b.png "PowerApps environments")

## <a name="convert-a-trial-environment-to-production"></a>Conversión de un entorno de prueba en producción

Mientras usa el entorno de prueba, si ha creado recursos que quiera conservar durante más de 30 días, convierta el entorno de prueba en un entorno de producción.

Para convertir en un entorno de producción, se deben cumplir estos criterios:

**Un plan de PowerApps adecuado**. Un plan que permita crear entornos de producción, por ejemplo, Plan 2 de PowerApps. Vea [Elegir los planes correctos para el equipo](https://powerapps.microsoft.com/pricing/) para obtener información sobre los planes de PowerApps que incluyen entornos de producción. Vea [Cómo identifico mi plan](#how-do-i-identify-my-plans) para determinar el plan de PowerApps.
**Cuota de producción disponible**. Hay un número fijo de entornos de producción que se pueden crear con el plan. Por ejemplo, con el Plan 2 de PowerApps, se pueden crear dos entornos de producción. Si ya ha creado dos entornos de producción, no podrá crear más hasta que elimine uno de los existentes. Para más información, vea [Creación de un entorno](environments-overview.md#creating-an-environment).

Siga estos pasos para convertir un entorno de prueba en un entorno de producción:

1. Vaya a [https://admin.powerapps.com/environments](https://admin.powerapps.com/environments) e inicie sesión como administrador.
 
2. Abra la página **Entornos** y seleccione el entorno de prueba que quiera convertir en entorno de producción:

    > [!div class="mx-imgBorder"] 
    > ![Selección del entorno de prueba](media/powerapps-environments75b-select-trial.png "Select trial environment")

3. En la pestaña **Detalles**, haga clic en **Convertir**:

    > [!div class="mx-imgBorder"] 
    > ![Haga clic en Convertir](media/powerapps-trial-select-convert.png "Select Convert")

4. Haga clic en **Confirmar**:

    > [!div class="mx-imgBorder"] 
    > ![Haga clic en Confirmar](media/powerapps-trial-select-confirm.png "Select Confirm")

Si el entorno tiene una base de datos, es posible que tarde varias horas en convertirse en un entorno de producción. Puede supervisar el progreso a través de la notificación en la pestaña **Detalles**:

  > [!div class="mx-imgBorder"] 
  > ![Conversión iniciada](media/powerapps-trial-conversion-started.png "Conversion started")

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes

### <a name="who-can-convert-a-trial-environment-to-a-production-environment"></a>¿Quién puede convertir un entorno de prueba en un entorno de producción?

Es preciso cumplir los criterios siguientes para convertir un entorno de prueba en un entorno de producción:

**Tener un plan de PowerApps adecuado**. Necesita un plan que permita crear entornos de producción, por ejemplo, Plan 2 de PowerApps. Vea [Elegir los planes correctos para el equipo](https://powerapps.microsoft.com/pricing/) para obtener información sobre los planes de PowerApps que incluyen entornos de producción. Vea [Cómo identifico mi plan](#how-do-i-identify-my-plans) para determinar el plan de PowerApps.
**Tener cuota de producción disponible**. Hay un número fijo de entornos de producción que se pueden crear con el plan. Por ejemplo, con el Plan 2 de PowerApps, se pueden crear dos entornos de producción. Si ya ha creado dos, no podrá crear más hasta que elimine uno de los existentes.

### <a name="what-if-i-dont-have-available-quota-for-production-environments"></a>¿Qué ocurre si no tengo cuota disponible para entornos de producción?

Póngase en contacto con su administrador global de Office 365 o el administrador de inquilinos de Azure Active Directory (Azure AD) para que:
- Le asigne el Plan 2 de PowerApps. 
- Busque otro usuario que tenga cuota de entornos de producción disponible.

También puede comprar un plan de PowerApps.

### <a name="can-every-office-365-global-admin-or-azure-ad-tenant-admin-convert-a-trial-environment-to-a-production-environment"></a>¿Todos los administradores globales de Office 365 o los administradores de inquilinos de Azure AD pueden convertir un entorno de prueba en uno de producción?

No. Los administradores globales y los administradores de inquilinos de Azure AD deben tener cuota disponible para entornos de producción para poder convertir un entorno de prueba en uno de producción.

### <a name="is-there-a-way-to-recover-a-deleted-trial-environment"></a>¿Hay alguna manera de recuperar un entorno de prueba eliminado?

No podemos garantizar la recuperación de un entorno de prueba eliminado, pero haremos todo lo posible para recuperarlo, en un plazo de siete días tras la eliminación. No se puede recuperar la base de datos del entorno, pero se pueden recuperar las aplicaciones (creadas con PowerApps) y los flujos.

### <a name="how-can-i-retain-my-data-and-resources-if-i-dont-have-a-way-to-convert-the-trial-environment-to-a-production-environment"></a>¿Cómo puedo conservar mis datos y recursos si no consigo convertir el entorno de prueba en un entorno de producción?

Puede exportar los recursos y datos a otro entorno. Si quiere conservarlos durante más tiempo, se recomienda crear un entorno de producción o un entorno individual (con el Plan de la comunidad de PowerApps) y exportar los recursos a ese entorno. 

Estas son algunas instrucciones para la exportación de recursos.

|Tipo de recurso en el entorno  |¿Cómo se puede exportar?  |
|---------|---------|
|Aplicaciones (de lienzo y basadas en modelos) y flujos     |Puede usar el [empaquetado](environment-and-tenant-migration.md) para exportar aplicaciones y flujos desde un entorno.         |
|Datos en la base de datos (entorno de Common Data Service (CDS) para aplicaciones)     |Tiene varias opciones:<br/><ul><li>[Exportar a Excel](../user/export-data-excel.md) y guardar los datos. Puede [importar los datos](../user/import-data.md) a otro entorno.</li><br/><li>Puede usar [servicios de integración de datos](data-integrator.md) y API para exportar datos a otro entorno.</li></ul> |

Los entornos de prueba que no han tenido ninguna actividad en las bases de datos del entorno durante 30 días se eliminan.

### <a name="how-can-i-create-a-production-or-an-individual-environment"></a>¿Cómo se puede crear un entorno de producción o un entorno individual?

Debe tener un plan de PowerApps que proporcione la creación del entorno de producción. Para más información, vea [Creación de un entorno](environments-overview.md#creating-an-environment).

Puede crear un entorno individual si se registra para obtener el [Plan de la comunidad de PowerApps](https://powerapps.microsoft.com/communityplan/). Tenga en cuenta que existen restricciones sobre el uso compartido de aplicaciones en entornos individuales; estos entornos están diseñados únicamente para uso personal.

### <a name="how-do-i-identify-my-plans"></a>¿Cómo identifico mi plan?

Para determinar el plan, haga clic en el icono de **engranaje** en la esquina superior derecha del sitio de PowerApps y, después, seleccione **Planes**.

> [!div class="mx-imgBorder"] 
> ![Selección de Planes](media/powerapps-plans.png "Select Plans")

### <a name="see-also"></a>Vea también
[Administración de entornos en PowerApps](environments-administration.md)<br/>
[Información general sobre los entornos](environments-overview.md)<br/>
[Elegir los planes correctos para el equipo](https://powerapps.microsoft.com/pricing/)<br/>
[Introducción a las licencias](pricing-billing-skus.md)<br/>
