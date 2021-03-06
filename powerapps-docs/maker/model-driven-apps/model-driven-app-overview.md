---
title: Información general sobre cómo crear una aplicación controlada por modelos con Power Apps | Microsoft Docs
description: Instrucciones paso a paso para crear y configurar una entidad para usar con una aplicación de Power Apps.
documentationcenter: na
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 02/12/2020
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d29ec6ca429efb4a7c221b888c77f01841542a18
ms.sourcegitcommit: 6cffa70358fd2e388d64a01f906c8c196fbbdefb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "3069823"
---
# <a name="what-are-model-driven-apps-in-power-apps"></a>¿Qué son las aplicaciones controladas por modelos en Power Apps?

El diseño de una aplicación controlada por modelos es un enfoque centrado en los componentes para el desarrollo de la aplicación. Para el diseño de aplicaciones controladas por modelos no se requiere código y las aplicaciones que crea pueden ser simples o muy complejas.  A diferencia del desarrollo de aplicaciones de lienzo, donde el diseñador tiene control total sobre el diseño de la aplicación, con las aplicaciones controladas por modelos, la mayoría del diseño lo determina el usuario y viene determinado en gran medida por los componentes que agrega a la aplicación.

![Aplicación controlada por modelos de ejemplo](media/model-driven-app-overview/model-app-sample.png)

El diseño de las aplicaciones controladas por modelos proporciona las siguientes ventajas:
- Entornos de diseño enriquecidos no de código orientados a los componentes 
- Crear aplicaciones complejas que responden adecuadamente con una IU similar en una variedad de dispositivos de escritorio a móvil
- Amplia capacidad de diseño 
- Su aplicación se puede distribuir como una solución
 
## <a name="the-approach-to-model-driven-app-making"></a>Enfoque de la creación de aplicaciones controladas por modelos
Básicamente, la creación de una aplicación controlada por modelos consta de tres áreas de enfoque clave.

- Modelar datos profesionales 
- Definir procesos de negocio 
- Componer la aplicación

### <a name="modeling-business-data"></a>Modelar datos profesionales
Para modelar datos empresariales determine qué datos necesitará la aplicación y cómo se relacionarán los datos con otros datos. En el diseño controlado por modelos se usa una arquitectura controlada por metadatos para que los diseñadores puedan personalizar la aplicación sin escribir código. Metadatos significa "datos acerca de datos" y define la estructura de los datos almacenados en el sistema. [Tutorial: Crear una entidad personalizada que tenga componentes en Power Apps](../common-data-service/create-custom-entity.md)

### <a name="defining-business-processes"></a>Definir procesos de negocio
La definición y aplicación de procesos de negocio coherentes es un aspecto clave del diseño de aplicaciones controladas por modelos. Los procesos coherentes garantizan que los usuarios de la aplicación se centren en su trabajo y no en recordar realizar un conjunto de pasos manuales. Los procesos pueden ser simples o complejos y normalmente cambian con el tiempo. Para crear un proceso, en el área Controlado por modelos de PowerApps.com, seleccione ![Configuración](media/powerapps-gear.png) > **Personalizaciones avanzadas** > **Abrir explorador de soluciones**. A continuación, en el panel de navegación de la izquierda en el explorador de soluciones, seleccione **Procesos** y, a continuación, **Nuevo**. Más información: [Información general sobre flujos de proceso de negocio](/flow/business-process-flows-overview) y [Aplicar lógica de negocios con Common Data Service](../common-data-service/cds-processes.md). 

### <a name="composing-the-model-driven-app"></a>Componer la aplicación controlada por modelos
Después de modelar los datos y definir los procesos, cree la aplicación seleccionando y configurando los componentes que necesita usando el diseñador de aplicaciones.

![Diseñador de aplicaciones](media/model-driven-app-overview/app-designer.png)

## <a name="next-steps"></a>Pasos siguientes

[Crear la primera aplicación controlada por modelos](build-first-model-driven-app.md)

[Conocer los componentes de las aplicaciones basadas en modelos](model-driven-app-components.md)

