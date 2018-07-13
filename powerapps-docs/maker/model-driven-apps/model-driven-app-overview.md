---
title: Información general sobre la compilación de una aplicación controlada por modelos con PowerApps | Microsoft Docs
description: Instrucciones paso a paso para crear y configurar una entidad para usar con una aplicación de PowerApps.
documentationcenter: na
author: Mattp123
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/21/2018
ms.author: matp
ms.openlocfilehash: eceaf1886bf77b85d6d6b3faae3f32428223cb7e
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37899511"
---
# <a name="overview-of-building-a-model-driven-app"></a>Información general sobre la compilación de una aplicación controlada por modelos

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
La definición y aplicación de procesos de negocio coherentes son un aspecto clave del diseño de aplicaciones controladas por modelos. Los procesos coherentes ayudan a asegurar que los usuarios de la aplicación se centran en su trabajo y no en recordar que tienen que realizar un conjunto de pasos manuales. Los procesos pueden ser simples o complejos, y a menudo cambian con el tiempo. Para crear un proceso, haga clic en **Opciones avanzadas** para abrir el [Explorador de soluciones](#advanced-model-driven-app-making). Después, en el panel de navegación de la izquierda en el Explorador de soluciones, seleccione **Procesos** y, después, haga clic en **Nuevo**. Más información: [Trabajar con la lógica de negocios](#working-with-business-logic)  

### <a name="composing-the-model-driven-app"></a>Creación de la aplicación controlada por modelos
Después de modelar los datos y definir los procesos, para compilar la aplicación se seleccionan y configuran los componentes necesarios mediante el Diseñador de aplicaciones.

![Diseñador de aplicaciones](media/model-driven-app-overview/app-designer.png)

## <a name="model-driven-app-components-and-designers"></a>Componentes y diseñadores de aplicaciones controladas por modelos
Una aplicación controlada por modelos bien diseñada consta de varios componentes que el diseñador selecciona para crear la apariencia y funcionalidad de la aplicación terminada. Los componentes y las propiedades de componente que usan los diseñadores para crear una aplicación se convierten en los metadatos. Para entender cómo se relaciona cada uno de estos componentes con el diseño de aplicaciones, aquí se separan en las categorías *datos*, *interfaz de usuario*, *lógica* y *visualización*. 

### <a name="data"></a>Datos
Estos componentes determinan en qué datos se va a basar la aplicación.



|Componente  |Descripción  |Diseñador  |
|---------|---------|---------|
|Entidad     |Un elemento con propiedades del que se realiza el seguimiento, por ejemplo, un contacto o una cuenta. Existen muchas entidades estándar. Se puede personalizar una entidad estándar que no sea del sistema (entidad de producción) o crear una entidad personalizada desde cero.     | Diseñador de entidades de [!INCLUDE [powerapps](../../includes/powerapps.md)]        |
|Campo     | Una propiedad que está asociada a una entidad. Un campo se define por un tipo de datos, que determina el tipo de datos que se pueden escribir o seleccionar. Algunos ejemplos son texto, número, fecha y hora, moneda o búsqueda (crea una relación con otra entidad). Normalmente, los campos se usan con formularios, vistas y búsquedas.        | Diseñador de entidades de [!INCLUDE [powerapps](../../includes/powerapps.md)]   |
|Relación     | Las relaciones de entidad definen cómo se pueden relacionar las entidades entre sí. Los tipos de relaciones disponibles son 1:N (uno a varios), N:1 (varios a uno) y N:N (varios a varios). Por ejemplo, agregar un campo de búsqueda a una entidad crea una relación 1:N entre las dos entidades y le permite colocar ese campo de búsqueda en un formulario.   | Diseñador de entidades de [!INCLUDE [powerapps](../../includes/powerapps.md)]        |
|Campo de conjunto de opciones     | Se trata de un tipo de campo especial, que proporciona al usuario un conjunto de opciones predeterminadas. Cada opción tiene un valor numérico y una etiqueta. Cuando se agrega a un formulario, en este campo se muestra un control para que el usuario seleccione una opción.  Hay dos tipos de conjuntos de opciones; los conjuntos de opciones, donde el usuario solo puede seleccionar una opción, y los conjuntos de opciones de selección múltiple, que permiten más de una selección.  | Diseñador de conjuntos de opciones de [!INCLUDE [powerapps](../../includes/powerapps.md)]     |

### <a name="ui"></a>Interfaz de usuario
Estos componentes determinan cómo interactúan los usuarios con la aplicación. 

|Componente  |Descripción  |Diseñador  |
|---------|---------|---------|
|App     | Determina los elementos fundamentales de la aplicación, como los componentes, las propiedades, el tipo de cliente y la dirección URL de la aplicación.      | Diseñador de aplicaciones   |
|Mapa del sitio     | Especifica la navegación de la aplicación.        | Diseñador de mapa del sitio        |
|Formulario     | Un conjunto de campos de entrada de datos para una entidad determinada que coincide con los elementos de los que la organización realiza el seguimiento para la entidad. Por ejemplo, un conjunto de campos de entrada de datos donde los usuarios introducen la información pertinente para realizar el seguimiento de los pedidos anteriores de un cliente junto con las fechas específicas de la solicitud de los nuevos pedidos.        | Diseñador de formularios        |
|Ver     | Las vistas definen cómo se muestra una lista de registros para una entidad específica en la aplicación. Una vista define las columnas para mostrar, el ancho de cada columna, el comportamiento de ordenación y los filtros predeterminados.   |  Diseñador de vistas       |

![Diseñador de aplicaciones y diseñador de formularios](media/model-driven-app-overview/app-and-form-designers.png)

### <a name="logic"></a>Lógica
Determina los procesos de negocio, las reglas y la automatización que va a tener la aplicación. Los creadores de [!INCLUDE [powerapps](../../includes/powerapps.md)] usan un diseñador que es específico del tipo de proceso o regla. 


|Tipo de lógica  |Descripción  |Diseñador  |
|---------|---------|---------|
|Flujo de proceso de negocio     | Un proceso en línea que guía a los usuarios a través de un proceso de negocio estándar. Por ejemplo, se puede usar un flujo de proceso de negocio si quiere que todos los usuarios controlen las solicitudes de servicio de cliente del mismo modo, o bien para requerir que el personal obtenga la aprobación de una factura antes de enviar un pedido.        | Diseñador de flujos de proceso de negocio        |
|Flujo de trabajo     |  Los flujos de trabajo automatizan los procesos de negocio sin una interfaz de usuario. Los diseñadores usan los flujos de trabajo para iniciar la automatización que no requiere la intervención del usuario.       | Diseñador de flujos de trabajo        |
|Acciones    |  Las acciones son un tipo de proceso que permite invocar acciones manualmente, incluidas las acciones personalizadas, directamente desde un flujo de trabajo.       |  Diseñador de procesos       |
|Regla de negocio     | Se usa para aplicar la lógica de reglas o recomendaciones a un formulario, por ejemplo para establecer requisitos de campo, ocultar campos o validar datos. Los diseñadores de aplicaciones usan una interfaz sencilla para implementar y mantener reglas que cambian con rapidez y son de uso frecuente.         |  Diseñador de reglas de negocio       |
|Flujo     | Flow es un servicio basado en la nube que permite crear flujos de trabajo automatizados entre aplicaciones y servicios para obtener notificaciones, sincronizar archivos, recopilar datos y mucho más.        | Microsoft Flow        |

![Diseñadores de flujos de trabajo, acciones y flujos de proceso de negocio](media/model-driven-app-overview/designer-mash.png)

### <a name="visualizations"></a>Visualizaciones
Determina qué tipo de visualizaciones de datos e informes estarán disponibles para la aplicación.


|Componente  |Descripción  |Diseñador  |
|---------|---------|---------|
|Gráfico     | Una sola visualización gráfica que se puede mostrar dentro de una vista, en un formulario o se puede agregar a un panel.        | Diseñador de gráficos        |
|Panel     | Funciona como una paleta para una o más visualizaciones gráficas que proporcionan una visión general de los datos de negocio que requieren acción.        | Diseñador de paneles        |
|Embedded Power BI     | Agregue iconos y paneles de Embedded Power BI a la aplicación. Power BI es un servicio basado en la nube que proporciona información de inteligencia empresarial.        |  Combinación del diseñador de gráficos, el diseñador de paneles y Power BI       |

![Panel de ejemplo](media/model-driven-app-overview/dashboard-designer.png)

### <a name="advanced-model-driven-app-making"></a>Creación de aplicaciones controladas por modelos avanzadas
El Explorador de soluciones es una herramienta completa que se usa para la compilación de aplicaciones controladas por modelos avanzadas. En el Explorador de soluciones se puede navegar a través de una jerarquía formada por todos los componentes de aplicación mediante el panel de navegación del lado izquierdo de la herramienta.

![Explorador de soluciones](media/model-driven-app-overview/solutionexplorer-entitiescollapsed.png)

Para abrir el Explorador de soluciones, haga clic en **Basado en modelos** en el panel izquierdo de [!INCLUDE [powerapps](../../includes/powerapps.md)].

  ![Seleccionar Basado en modelos](media/model-driven-app-overview/app-type-picker-mod.png)

Después, haga clic en la pestaña **Opciones avanzadas**. 

## <a name="model-driven-app-development-resources"></a>Recursos de desarrollo de aplicaciones controladas por modelos
Para obtener más información sobre el desarrollo de aplicaciones controladas por modelos, vea estos temas.
### <a name="modeling-your-data"></a>Modelado de los datos
- [Diseñar aplicaciones empresariales personalizadas mediante el diseñador de aplicaciones](https://docs.microsoft.com/dynamics365/customer-engagement/customize/design-custom-business-apps-using-app-designer)
- [Crear y diseñar formularios](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-design-forms)
- [Comprender las vistas](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-views)  

### <a name="modeling-and-composing-your-app"></a>Modelado y composición de la aplicación
- [Crear o editar entidades](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-entities)
- [Crear y editar relaciones entre entidades](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-entity-relationships) 
- [Crear y editar campos](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-fields)
- [Crear y editar conjuntos de opciones globales](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-global-option-sets)

### <a name="working-with-business-logic"></a>Trabajar con lógica de negocios
- [Información general sobre flujos de proceso de negocio](https://docs.microsoft.com/dynamics365/customer-engagement/customize/business-process-flows-overview)
- [Procesos del flujo de trabajo](https://docs.microsoft.com/dynamics365/customer-engagement/customize/workflow-processes)
- [Información general sobre las acciones](https://docs.microsoft.com/dynamics365/customer-engagement/customize/actions)
- [Crear reglas de negocio y recomendaciones para aplicar lógica en un formulario](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-business-rules-recommendations-apply-logic-form)

### <a name="using-visualizations-in-your-app"></a>Uso de visualizaciones en la aplicación
- [Crear o editar un gráfico del sistema](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-system-chart)
- [Crear o editar paneles](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-dashboards)


### <a name="distributing-your-app"></a>Distribución de la aplicación
[Crear una solución](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-solution)

## <a name="next-steps"></a>Pasos siguientes
[Inicio rápido: Creación de una entidad personalizada](../common-data-service/data-platform-create-entity.md)

[Tutorial: Creación de una entidad personalizada que tiene componentes en PowerApps](../common-data-service/create-custom-entity.md)

