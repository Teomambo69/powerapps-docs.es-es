---
title: Conocer los componentes de las aplicaciones controladas por modelos en PowerApps | MicrosoftDocs
description: 'Comprender los distintos componentes de una aplicación controlada por modelos, como datos, IU, lógica y visualización.'
Keywords: 'campos, atributos, aplicación basada en modelos'
author: Mattp123
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.author: matp
manager: kvivek
ms.date: 06/27/2018
ms.service: powerapps
ms.topic: article
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="understand-model-driven-app-components"></a>Conocer los componentes de las aplicaciones basadas en modelos
Una aplicación controlada por modelos bien diseñada se compone de varios componentes que selecciona usando el diseñador para crear la apariencia y funcionalidades de la aplicación terminada. Los componentes y propiedades de componentes que los diseñadores usan para crear una aplicación son los metadatos. 

Para conocer cómo cada uno de estos componentes se relaciona con el diseño de la aplicación, se separan aquí en las categorías de *datos*, *IU*, *lógica* y *visualización*. 

## <a name="data"></a>Datos
Estos componentes determinan en qué datos se basará la aplicación.


|Componente  |Descripción  |Diseñador  |
|---------|---------|---------|
|Entidad     |Un artículo con propiedades de las que se realiza un seguimiento, como un contacto o una cuenta. Hay disponibles muchas entidades estándar. Puede personalizar una entidad estándar que no sea del sistema (entidad de producción) o crear una entidad personalizada desde cero.     | Diseñador de entidades de [!INCLUDE [powerapps](../../includes/powerapps.md)]        |
|Campo     | Propiedad que está asociada a una entidad. Un campo está definido por un tipo de datos, que determina el tipo de datos que se pueden introducir o seleccionar. Por ejemplo: texto, número, fecha y hora, divisa o búsqueda (crea una relación con otra entidad). Los campos suelen usarse con formularios, vistas y búsquedas.        | Diseñador de entidades de [!INCLUDE [powerapps](../../includes/powerapps.md)]   |
|Relación     | Las relaciones de entidades definen cómo se pueden relacionar las entidades entre ellas. Existen los tipos de relaciones: 1: N (uno a varios), N: 1 (varios a uno) y N:N (varios a varios). Por ejemplo, al agregar un campo de búsqueda a una entidad se crea una nueva relación de 1:N entre las dos entidades y le permite colocar ese campo de búsqueda en un formulario.   | Diseñador de entidades de [!INCLUDE [powerapps](../../includes/powerapps.md)]        |
|Campo Conjunto de opciones     | Este es un tipo especial de campo, que proporciona al usuario un conjunto de opciones predeterminadas. Cada opción tiene un valor y una etiqueta del número. Cuando se agrega a un formulario, este campo muestra un control para que el usuario pueda seleccionar una opción.  Hay dos tipos de conjuntos de opciones; conjuntos de opciones, donde el usuario solo puede seleccionar una opción y conjuntos de opciones de selección múltiple, que permiten más de una selección.  | Diseñador de conjunto de opciones de [!INCLUDE [powerapps](../../includes/powerapps.md)]     |

Más información: [Definir datos para su aplicación controlada por modelos](define-data-model-driven-app.md) 

## <a name="ui"></a>IU
Estos componentes determinan cómo interactúan los usuarios con la aplicación. 

|Componente  |Descripción  |Diseñador  |
|---------|---------|---------|
|Aplicación     | Determina aspectos básicos de la aplicación como componentes, propiedades, tipo de cliente y dirección URL.      | Diseñador de aplicaciones   |
|Mapa del sitio     | Especifica la navegación para su aplicación.        | Diseñador del mapa del sitio        |
|Formulario     | Conjunto de campos de entrada de datos de una entidad dada que coincide con los elementos de los que su organización realiza un seguimiento para la entidad. Por ejemplo, un conjunto de campos de entrada de datos que realizan un seguimiento de los pedidos anteriores de un cliente junto con las fechas de nuevo pedido específicas solicitadas.        | Diseñador de formularios        |
|Vista     | Las vistas definen cómo se muestra una lista de registros para una entidad específica en la aplicación. Una vista define las columnas para mostrar, el ancho de cada columna, el comportamiento de ordenación y los filtros predeterminados.   |  Diseñador de vistas       |

![Diseñador de aplicaciones y diseñador de formularios](media/model-driven-app-overview/app-and-form-designers.png)

## <a name="logic"></a>Lógica
Determina los procesos de negocio, reglas y automatización que la aplicación tendrá. Los creadores de [!INCLUDE [powerapps](../../includes/powerapps.md)] usan un diseñador que es específico al tipo de proceso o de regla. 


|Tipo de lógica  |Descripción  |Diseñador  |
|---------|---------|---------|
|Flujo de proceso de negocio     | Proceso en línea que guía a los usuarios a través de un proceso de negocio estándar. Por ejemplo, use un proceso de negocio si desea que todo el mundo administre las solicitudes de servicio al cliente de la misma forma, o para requerir que el personal obtenga aprobación para una factura antes de enviar un pedido.        | Diseñador de flujos de proceso de negocio        |
|Flujo de trabajo     |  Los flujos de trabajo automatizan los procesos de negocio sin una interfaz de usuario. Los diseñadores usan flujos de trabajo para iniciar tareas de automatización que no requieren ninguna interacción del usuario.       | Diseñador de flujos de trabajo        |
|Acciones    |  Las acciones son un tipo de proceso que le permiten invocar acciones manualmente, incluidas acciones personalizadas, directamente desde un flujo de trabajo.       |  Diseñador de procesos       |
|Regla de negocio     | Se usa para aplicar lógica de reglas o de recomendación a un formulario, por ejemplo, para establecer los requisitos de campo, ocultar campos o validar datos. Los diseñadores de aplicaciones usan una interfaz básica para implementar y mantener reglas de evolución rápida y de uso general.         |  Diseñador de reglas de negocio       |
|Flujo     | Un flujo es un servicio basado en la nube que le permite crear flujos de trabajo automáticos entre aplicaciones y servicios para obtener notificaciones, sincronizar archivos, recopilar datos, etc.        | Microsoft Flow        |

![Diseñadores de flujos de trabajo, acciones y flujos de proceso de negocio](media/model-driven-app-overview/designer-mash.png)

Más información: [Aplicar lógica de negocios a su aplicación controlada por modelos](guide-staff-through-common-tasks-processes.md)

## <a name="visualizations"></a>Visualizaciones
Determina qué tipo de visualizaciones y de creación de informes tendrá disponible la aplicación.


|Componente  |Descripción  |Diseñador  |
|---------|---------|---------|
|Gráfico     | Una única visualización gráfica que puede mostrarse en una vista, en un formulario o bien agregar a un panel.        | Diseñador de gráficos        |
|Panel     | Funciona como una preferencia para una o varias visualizaciones gráficas que proporcionan una visión general de los datos profesionales en los que se puede actuar.        | Diseñador de paneles        |
|Power BI incrustado     | Agregue ventanas y paneles de Power BI incrustado a la aplicación. Power BI es un servicio basado en la nube que ofrece información detallada de inteligencia empresarial.        |  Combinación de diseñador de gráficos, diseñador de paneles y Power BI       |

![Panel de ejemplo](media/model-driven-app-overview/dashboard-designer.png)

## <a name="advanced-model-driven-app-making"></a>Creación avanzada de aplicaciones controladas por modelos
El explorador de soluciones es una herramienta completa que se usa para la creación avanzada de aplicaciones controladas por modelos. En el explorador de soluciones puede navegar por una jerarquía formada por todos los componentes de las aplicaciones usando el panel de navegación que hay a la izquierda de la herramienta.

![Explorador de soluciones](media/model-driven-app-overview/solutionexplorer-entitiescollapsed.png)

Para abrir el explorador de soluciones, seleccione **Controlado por modelos** en el panel izquierdo de [!INCLUDE [powerapps](../../includes/powerapps.md)].

  ![Seleccione Controlado por modelos](media/model-driven-app-overview/app-type-picker-mod.png)

A continuación, seleccione la pestaña **Avanzada**.

Más información: [Creación y personalización avanzadas de aplicaciones](advanced-navigation.md)

## <a name="related-topics"></a>Temas relacionados

[Validar y publicar una aplicación controlada por modelos](validate-app.md)

[Compartir su aplicación controlada por modelos](share-model-driven-app.md)
