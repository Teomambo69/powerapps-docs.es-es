---
title: Guía para desarrolladores de Common Data Service | Microsoft Docs
description: Descubra cómo los desarrolladores pueden agregar valor mediante Common Data Service.
author: JimDaly
manager: annbe
ms.service: powerapps
ms.topic: article
ms.date: 03/27/2019
ms.author: jdaly
ms.reviewer: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 41eb896c56809d1ceb289e86ee427f7a1b9f18db
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749818"
---
# <a name="common-data-service-developer-guide"></a>Manual para desarrolladores de Common Data Service

PowerApps proporciona a usuarios, empresas, fabricantes independientes de software (ISV) e integradores de sistemas (SI) una plataforma eficaz para crear aplicaciones de línea de negocio. **Common Data Service** es la plataforma subyacente de datos para PowerApps que contiene la funcionalidad básica como lógica del lado del servidor (complementos y flujos de trabajo), flujos de proceso de negocio, un modelo de seguridad bien avanzado, y una plataforma extensible para que los desarrolladores generen aplicaciones. 

Hay muchos aspectos referentes a cómo los desarrolladores pueden contribuir a crear aplicaciones que usan Common Data Service. Aunque sea posible crear una aplicación con un código mediante Common Data Service como el origen de datos, la mayoría de los proyectos utilizarán [aplicaciones basadas en modelos](/powerapps/maker/model-driven-apps/model-driven-app-overview) o [aplicaciones de lienzo](/powerapps/maker/canvas-apps/getting-started) para generar la experiencia que usan las personas. 

## <a name="working-with-model-driven-apps"></a>Trabajar con aplicaciones basadas en modelos

Las aplicaciones basadas en modelo se crean con Common Data Service y solo pueden conectarse a un entorno de Common Data Service. Todos los datos que definen una aplicación basada en modelos se almacenan en Common Data Service.

Las aplicaciones basadas en modelos comparten el método de distribución de personalizaciones y extensiones que usa Common Data Service utilizando [Soluciones](introduction-solutions.md).

Las aplicaciones basadas en modelos también tienen varios puntos para que los desarrolladores escriban código para ampliar. Para obtener información sobre lo que pueden hacer los desarrolladores con las aplicaciones basadas en modelos, consulte [Guía para desarrolladores sobre aplicaciones basadas en modelos](../model-driven-apps/overview.md).

Algunos ejemplos de aplicaciones basadas en modelo disponibles en Microsoft son [Dynamics 365 Customer Service](https://docs.microsoft.com/dynamics365/customer-service/help-hub), [Dynamics 365 Field Service](https://docs.microsoft.com/dynamics365/field-service/overview)y [Dynamics 365 Marketing](https://docs.microsoft.com/dynamics365/marketing/help-hub).

## <a name="understand-when-to-write-code"></a>Comprender cuándo hay que escribir código

Dado que Common Data Service incluye muchas funcionalidades para que los usuarios configuren la lógica empresarial personalizada sin escribir código, los escenarios más comunes para que los desarrolladores contribuyan tienen que ver con rellenar espacios donde puede que las características existentes no proporcionen la funcionalidad que necesita para cumplir requisitos. Afortunadamente, Common Data Service proporciona muchos puntos para que los desarrolladores amplíen la funcionalidad común con código.

Para un desarrollador que ayude en proyectos es importante entender lo que se puede hacer sin necesidad de escribir código. Debe familiarizarse con estas funcionalidades. Más información: [Qué es Common Data Service](../../maker/common-data-service/data-platform-intro.md) 

## <a name="content-for-on-premises-deployments"></a>Contenido para implementaciones locales

Common Data Service no está disponible para implementaciones locales en este momento. El contenido de este manual no incluye información sobre las opciones que solo están disponibles para implementaciones local o implementaciones con conexión a Internet (IFD). Para información relacionada con estas opciones, consulte la [está configurado de Dynamics 365 Customer Engagement (on-premises))](/dynamics365/customer-engagement/on-premises/developer/overview).

> [!div class="nextstepaction"]
> [Introducción](get-started-cds-developers.md)

### <a name="see-also"></a>Vea también

[PowerApps para desarrolladores](/powerapps/#pivot=home&panel=developer)<br/>
[Manual para desarrolladores de aplicaciones basadas en modelos](../model-driven-apps/overview.md)
