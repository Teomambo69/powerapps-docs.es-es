---
title: Información sobre los componentes de las aplicaciones basadas en modelos en PowerApps | Microsoft Docs
description: Conozca los distintos componentes de una aplicación basada en modelos, como los datos, la interfaz de usuario, la lógica y la visualización.
Keywords: fields, attributes, model-driven app
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/27/2018
ms.service: crm-online
ms.topic: article
ms.openlocfilehash: 249f0d35ce9eb466303ef16658aa01198632875e
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39699021"
---
# <a name="understand-model-driven-app-components"></a>Información de componentes de aplicación basada en modelos
Una aplicación basada en modelos bien diseñada consta de varios componentes que el diseñador selecciona con el diseñador para crear la apariencia y funcionalidades de la aplicación terminada. Los componentes y las propiedades de componente que usan los diseñadores para crear una aplicación se convierten en los metadatos. 

Para entender cómo se relaciona cada uno de estos componentes con el diseño de aplicaciones, aquí se separan en las categorías *datos*, *interfaz de usuario*, *lógica* y *visualización*. 

## <a name="data"></a>Datos
Estos componentes determinan en qué datos se va a basar la aplicación.


|Componente  |Descripción  |Diseñador  |
|---------|---------|---------|
|Entidad     |Un elemento con propiedades del que se realiza el seguimiento, por ejemplo, un contacto o una cuenta. Existen muchas entidades estándar. Se puede personalizar una entidad estándar que no sea del sistema (entidad de producción) o crear una entidad personalizada desde cero.     | Diseñador de entidades de [!INCLUDE [powerapps](../../includes/powerapps.md)]        |
|Campo     | Una propiedad que está asociada a una entidad. Un campo se define por un tipo de datos, que determina el tipo de datos que se pueden escribir o seleccionar. Algunos ejemplos son texto, número, fecha y hora, moneda o búsqueda (crea una relación con otra entidad). Normalmente, los campos se usan con formularios, vistas y búsquedas.        | Diseñador de entidades de [!INCLUDE [powerapps](../../includes/powerapps.md)]   |
|Relación     | Las relaciones de entidad definen cómo se pueden relacionar las entidades entre sí. Los tipos de relaciones disponibles son 1:N (uno a varios), N:1 (varios a uno) y N:N (varios a varios). Por ejemplo, agregar un campo de búsqueda a una entidad crea una relación 1:N entre las dos entidades y le permite colocar ese campo de búsqueda en un formulario.   | Diseñador de entidades de [!INCLUDE [powerapps](../../includes/powerapps.md)]        |
|Campo de conjunto de opciones     | Se trata de un tipo de campo especial, que proporciona al usuario un conjunto de opciones predeterminadas. Cada opción tiene un valor numérico y una etiqueta. Cuando se agrega a un formulario, en este campo se muestra un control para que el usuario seleccione una opción.  Hay dos tipos de conjuntos de opciones; los conjuntos de opciones, donde el usuario solo puede seleccionar una opción, y los conjuntos de opciones de selección múltiple, que permiten más de una selección.  | Diseñador de conjuntos de opciones de [!INCLUDE [powerapps](../../includes/powerapps.md)]     |

Más información: [Definir datos para su aplicación basada en modelos](define-data-model-driven-app.md) 

## <a name="ui"></a>Interfaz de usuario
Estos componentes determinan cómo interactúan los usuarios con la aplicación. 

|Componente  |Descripción  |Diseñador  |
|---------|---------|---------|
|App     | Determina los elementos fundamentales de la aplicación, como los componentes, las propiedades, el tipo de cliente y la dirección URL de la aplicación.      | Diseñador de aplicaciones   |
|Mapa del sitio     | Especifica la navegación de la aplicación.        | Diseñador de mapa del sitio        |
|Formulario     | Un conjunto de campos de entrada de datos para una entidad determinada que coincide con los elementos de los que la organización realiza el seguimiento para la entidad. Por ejemplo, un conjunto de campos de entrada de datos donde los usuarios introducen la información pertinente para realizar el seguimiento de los pedidos anteriores de un cliente junto con las fechas específicas de la solicitud de los nuevos pedidos.        | Diseñador de formularios        |
|Ver     | Las vistas definen cómo se muestra una lista de registros para una entidad específica en la aplicación. Una vista define las columnas para mostrar, el ancho de cada columna, el comportamiento de ordenación y los filtros predeterminados.   |  Diseñador de vistas       |

![Diseñador de aplicaciones y diseñador de formularios](media/model-driven-app-overview/app-and-form-designers.png)

## <a name="logic"></a>Lógica
Determina los procesos de negocio, las reglas y la automatización que va a tener la aplicación. Los creadores de [!INCLUDE [powerapps](../../includes/powerapps.md)] usan un diseñador que es específico del tipo de proceso o regla. 


|Tipo de lógica  |Descripción  |Diseñador  |
|---------|---------|---------|
|Flujo de proceso de negocio     | Un proceso en línea que guía a los usuarios a través de un proceso de negocio estándar. Por ejemplo, se puede usar un flujo de proceso de negocio si quiere que todos los usuarios controlen las solicitudes de servicio de cliente del mismo modo, o bien para requerir que el personal obtenga la aprobación de una factura antes de enviar un pedido.        | Diseñador de flujos de proceso de negocio        |
|Flujo de trabajo     |  Los flujos de trabajo automatizan los procesos de negocio sin una interfaz de usuario. Los diseñadores usan los flujos de trabajo para iniciar la automatización que no requiere la intervención del usuario.       | Diseñador de flujos de trabajo        |
|Acciones    |  Las acciones son un tipo de proceso que permite invocar acciones manualmente, incluidas las acciones personalizadas, directamente desde un flujo de trabajo.       |  Diseñador de procesos       |
|Regla de negocio     | Se usa para aplicar la lógica de reglas o recomendaciones a un formulario, por ejemplo para establecer requisitos de campo, ocultar campos o validar datos. Los diseñadores de aplicaciones usan una interfaz sencilla para implementar y mantener reglas que cambian con rapidez y son de uso frecuente.         |  Diseñador de reglas de negocio       |
|Flujo     | Flow es un servicio basado en la nube que permite crear flujos de trabajo automatizados entre aplicaciones y servicios para obtener notificaciones, sincronizar archivos, recopilar datos y mucho más.        | Microsoft Flow        |

![Diseñadores de flujos de trabajo, acciones y flujos de proceso de negocio](media/model-driven-app-overview/designer-mash.png)

Más información: [Aplicar lógica de negocios a su aplicación basada en modelos](guide-staff-through-common-tasks-processes.md)

## <a name="visualizations"></a>Visualizaciones
Determina qué tipo de visualizaciones de datos e informes estarán disponibles para la aplicación.


|Componente  |Descripción  |Diseñador  |
|---------|---------|---------|
|Gráfico     | Una sola visualización gráfica que se puede mostrar dentro de una vista, en un formulario o se puede agregar a un panel.        | Diseñador de gráficos        |
|Panel     | Funciona como una paleta para una o más visualizaciones gráficas que proporcionan una visión general de los datos de negocio que requieren acción.        | Diseñador de paneles        |
|Embedded Power BI     | Agregue iconos y paneles de Embedded Power BI a la aplicación. Power BI es un servicio basado en la nube que proporciona información de inteligencia empresarial.        |  Combinación del diseñador de gráficos, el diseñador de paneles y Power BI       |

![Panel de ejemplo](media/model-driven-app-overview/dashboard-designer.png)

## <a name="advanced-model-driven-app-making"></a>Creación de aplicaciones controladas por modelos avanzadas
El Explorador de soluciones es una herramienta completa que se usa para la compilación de aplicaciones controladas por modelos avanzadas. En el Explorador de soluciones se puede navegar a través de una jerarquía formada por todos los componentes de aplicación mediante el panel de navegación del lado izquierdo de la herramienta.

![Explorador de soluciones](media/model-driven-app-overview/solutionexplorer-entitiescollapsed.png)

Para abrir el Explorador de soluciones, haga clic en **Basado en modelos** en el panel izquierdo de [!INCLUDE [powerapps](../../includes/powerapps.md)].

  ![Seleccionar Basado en modelos](media/model-driven-app-overview/app-type-picker-mod.png)

Después, haga clic en la pestaña **Opciones avanzadas**.

Más información: [Creación y personalización avanzadas de aplicaciones](advanced-navigation.md)

## <a name="related-topics"></a>Temas relacionados

[Validar y publicar una aplicación basada en modelos](validate-app.md)

[Compartir su aplicación basada en modelos](share-model-driven-app.md)