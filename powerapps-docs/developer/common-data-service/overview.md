---
title: Guía para desarrolladores de Common Data Service | Microsoft Docs
description: Descubra cómo los desarrolladores pueden agregar valor mediante Common Data Service.
author: JimDaly
manager: annbe
ms.service: powerapps
ms.topic: article
ms.date: 03/27/2019
ms.author: jdaly
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a6b160057ca43b8a4e6a9b0e906994fbf2d46051
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155376"
---
# <a name="common-data-service-developer-guide"></a>Manual para desarrolladores de Common Data Service

Power Apps proporciona a usuarios, empresas, fabricantes independientes de software (ISV) e integradores de sistemas (SI) una plataforma eficaz para crear aplicaciones de línea de negocio. **Common Data Service** es la plataforma subyacente de datos para Power Apps que contiene la funcionalidad básica como lógica del lado del servidor (complementos y flujos de trabajo), flujos de proceso de negocio, un modelo de seguridad bien avanzado, y una plataforma extensible para que los desarrolladores generen aplicaciones. 

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

Common Data Service no está disponible para implementaciones locales en este momento. El contenido de este manual no incluye información sobre las opciones que solo están disponibles para implementaciones local o implementaciones con conexión a Internet (IFD). Para información relacionada con estas opciones, la [Guía de desarrolladores para Dynamics 365 Customer Engagement (on-premises)](/dynamics365/customerengagement/on-premises/developer/overview).

> [!div class="nextstepaction"]
> [Introducción](get-started-cds-developers.md)

### <a name="see-also"></a>Vea también

[Power Apps para desarrolladores](/powerapps/#pivot=home&panel=developer)<br/>
[Manual para desarrolladores de aplicaciones basadas en modelos](../model-driven-apps/overview.md)
