---
title: Información general sobre la compilación de una aplicación controlada por modelos con PowerApps | Microsoft Docs
description: Instrucciones paso a paso para crear y configurar una entidad para usar con una aplicación de PowerApps.
documentationcenter: na
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 08/09/2018
ms.author: matp
ms.openlocfilehash: f6434e6a9248586c05fa0b56b8934d910af3087a
ms.sourcegitcommit: 2a61989be5880fede31510c5dab1593a6f42a741
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "39723855"
---
# <a name="what-are-model-driven-apps-in-powerapps"></a>¿Qué son las aplicaciones controladas por modelos en PowerApps?

El diseño de aplicaciones controladas por modelos es un enfoque de componentes centrado en el desarrollo de aplicaciones. El diseño de aplicaciones controladas por modelos no requiere código y las aplicaciones que se creen pueden ser simples o muy complejas.  A diferencia del desarrollo de aplicaciones de lienzo en el que el diseñador tiene el control completo sobre el diseño de la aplicación, con las aplicaciones controladas por modelos gran parte del diseño se determina automáticamente y se diseña en gran medida por los componentes que se agregan a la aplicación. 

![Aplicación controlada por modelos de ejemplo](media/model-driven-app-overview/model-app-sample.png)

El diseño de aplicaciones controladas por modelos proporciona las ventajas siguientes:
- Entornos de diseño sin código centrados en componentes enriquecidos. 
- Crear aplicaciones complejas con capacidad de respuesta con una interfaz de usuario similar en una variedad de dispositivos, de escritorio y móviles.
- Capacidad de diseño similar a la que ofrece la plataforma Dynamics 365 Customer Engagement. 
- La aplicación se puede distribuir como una solución.
 
## <a name="the-approach-to-model-driven-app-making"></a>El enfoque a la creación de aplicaciones controladas por modelos
En un nivel fundamental, la creación de aplicaciones controladas por modelos consta de tres áreas de enfoque clave.

- Modelado de datos de negocio 
- Definición de procesos de negocio 
- Composición de la aplicación

### <a name="modeling-business-data"></a>Modelado de datos de negocio
Para modelar los datos de negocio, se determina qué datos va a necesitar la aplicación y cómo se relacionan esos datos con otros. En el diseño controlado por modelos se usa una arquitectura controlada por metadatos para que los diseñadores puedan personalizar la aplicación sin tener que escribir código. Los metadatos significan "datos sobre datos" y definen la estructura de los datos almacenados en el sistema. [Tutorial: Creación de una entidad personalizada que tiene componentes en PowerApps](../common-data-service/create-custom-entity.md)

### <a name="defining-business-processes"></a>Definición de procesos de negocio
La definición y aplicación de procesos de negocio coherentes son un aspecto clave del diseño de aplicaciones controladas por modelos. Los procesos coherentes ayudan a asegurar que los usuarios de la aplicación se centran en su trabajo y no en recordar que tienen que realizar un conjunto de pasos manuales. Los procesos pueden ser simples o complejos, y a menudo cambian con el tiempo. Para crear un proceso, en el área de aplicaciones controladas por modelos de PowerApps, seleccione ![Configuración](media/powerapps-gear.png) > **Personalizaciones avanzadas** > **Abrir el Explorador de soluciones**. Después, en el panel de navegación de la izquierda en el Explorador de soluciones, seleccione **Procesos** y, después, haga clic en **Nuevo**. Más información: [Información general sobre flujos de proceso de negocio](/flow/business-process-flows-overview) y [Aplicación de lógica de negocios con Common Data Service for Apps](../common-data-service/cds-processes.md). 

### <a name="composing-the-model-driven-app"></a>Creación de la aplicación controlada por modelos
Después de modelar los datos y definir los procesos, para compilar la aplicación se seleccionan y configuran los componentes necesarios mediante el Diseñador de aplicaciones.

![Diseñador de aplicaciones](media/model-driven-app-overview/app-designer.png)

## <a name="next-steps"></a>Pasos siguientes

[Crear la primera aplicación controlada por modelos](build-first-model-driven-app.md)

[Información de componentes de aplicación controlados por modelos](model-driven-app-components.md)

