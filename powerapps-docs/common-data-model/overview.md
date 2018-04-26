---
title: Introducción a Common Data Service | Microsoft Docs
description: Obtenga información sobre cómo Common Data Service conecta Common Data Service for Apps con Common Data Service for Analytics.
documentationcenter: na
author: RobertBruckner
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.date: 03/14/2018
ms.author: jdaly
ms.openlocfilehash: ed7a1bfd7e3d3439cdcf2f20d1026c69a9abce4d
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="common-data-model-overview"></a>Introducción a Common Data Service

**Common Data Service** (CDS) es una definición de código abierto de entidades estándar que representan los conceptos y actividades más usados en una variedad de dominios de aplicación y empresariales. Common Data Service ofrece entidades empresariales *bien definidas, modulares y extensibles* como Account, Business Unit, Case, Contact, Lead, Opportunity y Product, así como interacciones y relaciones entre proveedores, trabajadores y clientes, como actividades y acuerdos de nivel de servicio. 

[Common Data Service for Apps](../maker/common-data-service/data-platform-intro.md) de Microsoft y Common Data Service for Analytics <!-- TODO add link when available  --> implementan Common Data Service. Estos servicios contienen datos que se ajustan a la definición de Common Data Service. Al compilarse sobre estos servicios, las aplicaciones empaquetadas y las soluciones analíticas pueden trabajar con formas de entidad bien definidas y compartir datos, con independencia de dónde procedan o se usen originalmente los datos. Las aplicaciones de línea de negocio personalizadas y las soluciones analíticas pueden aprovechar las mismas entidades para el uso compartido de datos y, por tanto, admitir necesidades y requisitos empresariales específicos. 

Microsoft y nuestros socios se comprometen a compilar nuestras aplicaciones sobre Common Data Service y a almacenar los datos empresariales en formato de CDS. Existe una *abundante y creciente colección de soluciones que funcionan de manera conjunta y eficaz cuando los datos se almacenan en formato de CDS*, lo que significa que se pueden implementar rápidamente nuevos procesos de negocio y obtener información sobre las operaciones empresariales sin fricción o complejidad. En el siguiente diagrama se muestran aplicaciones sobre Common Data Service que aprovechan las entidades de Common Data Service.

![Aplicaciones sobre Common Data Service que aprovechan las entidades de Common Data Service](media/cdm-overview.png)

Common Data Service simplifica los desafíos de la administración de datos mediante la unificación de los datos en un formato conocido con *coherencia estructural y semántica entre las aplicaciones e implementaciones*. Ayuda a integrar y *eliminar la ambigüedad de los datos* recopilados de procesos empresariales, interacciones digitales, telemetría de productos, interacciones de usuarios y así sucesivamente. 

Los datos almacenados en Common Data Service for Apps *se integran de forma sencilla y automática* con Common Data Service for Analytics para los clientes que usan ambos servicios. Puede empezar a partir de los datos empresariales y transaccionales que ya posee (por ejemplo, clientes potenciales, información de campañas, compras de clientes anteriores) y combinarlos con datos de otros orígenes (como blogs o telemetría de productos) para obtener una imagen unificada.

Common Data Service también es *extensible*: se pueden agregar campos a cualquiera de las entidades personalizables que se incluyen con CDS o se pueden crear entidades personalizadas propias. El estándar CDS define un lenguaje común para las entidades empresariales que abarca toda la gama de procesos de negocio en ventas, servicios, operaciones de marketing, finanzas, talento y comercio, y para las entidades de clientes, usuarios y productos en el núcleo de los procesos empresariales de una empresa. Common Data Service facilita la interoperabilidad de los datos que abarcan varios canales, implementaciones de servicios y proveedores.

Common Data Service proporciona una plataforma de desarrollo enriquecida y productiva a través de las características siguientes:

- **Definición de entidades estándar**: Common Data Service proporciona una definición de entidades que representan las más usadas en todas las aplicaciones de negocio y productividad. El repositorio de CDS público de GitHub [(https://github.com/Microsoft/CDM)](https://github.com/Microsoft/CDM) se ampliará continuamente con entidades principales que abarcan todo el panorama de procesos de negocio, modelos de datos de la industria verticales adicionales y orígenes multidisciplinares como encuestas, motores de búsqueda y telemetría de productos.
- **Integración de datos**: use Power Query como experiencia web integrada para importar y transformar visualmente los datos de los sistemas existentes y para combinar datos de orígenes en línea y locales sin código con o poca cantidad de código. Las habilidades de transformación de datos de Excel y Power BI se aplican sin problemas. Vea [Add data to an entity in the Common Data Service by using Power Query](../maker/common-data-service/data-platform-cds-newentity-pq.md) (Adición de datos a una entidad en Common Data Service mediante Power Query).
    
    Al importar datos a Common Data Service, se pueden asignar a entidades de Common Data Service estándar, o bien crear y asignar a entidades nuevas. Las plantillas estándar de asignación e integración de datos simplifican la conexión a orígenes de datos comunes, como Salesforce. Estas plantillas de asignación son totalmente personalizables y extensibles. En la captura de pantalla siguiente se muestra la importación de datos externos y la asignación a entidades estándar en Power Query. 
    
    ![Importación de datos externos y asignación a entidades estándar en Power Query ](media/cdm-mapping-entities.png)<br />

- **Extensibilidad**: las entidades se pueden ampliar sin que ello interrumpa el uso compartido de datos con otras aplicaciones.
- **Fiabilidad**: como se puede depender de entidades comunes, se pueden crear componentes reutilizables enlazados a las entidades. Common Data Service admite la extensibilidad y el control de versiones que protege la inversión en desarrollo.
- **Coherencia de entidades entre implementaciones**: las soluciones pueden conectar información de las plataformas de productividad con datos de aplicaciones empresariales. Por ejemplo, se puede conectar una cita de calendario o una tarea de Microsoft Outlook con una oportunidad de venta. 

[Common Data Service for Apps](../maker/common-data-service/data-platform-intro.md) implementa Common Data Service, que permite el desarrollo de aplicaciones empresariales para:

- **Aprovechar aplicaciones empresariales empaquetadas**: las aplicaciones de Dynamics 365 for Marketing, Sales, Service, Talent, Finance y Operations, así como aplicaciones de otros fabricantes aprovechan o se compilan sobre Common Data Service for Apps.
- **Personalizar aplicaciones y compilar extensiones nativas para las necesidades**: los desarrolladores y personalizadores distribuyen las soluciones de aplicación con un ciclo de vida de aplicación bien definido. Las soluciones son la forma de distribuir aplicaciones y extensiones. Vea [Introducción a las soluciones](../developer/common-data-service/introduction-solutions.md).
- **Compilar aplicaciones sin código o poca cantidad de código, controladas por modelos y de lienzo WYSIWYG con PowerApps**: use las mismas entidades compartidas que crean o usan las aplicaciones empaquetadas u otras aplicaciones de terceros, y cree aplicaciones independientes adicionales. Vea: 
    - [Build a model-driven app](../maker/model-driven-apps/model-driven-app-overview.md) (Compilación de una aplicación controlada por modelos)
    - [Build a canvas app](../maker/canvas-apps/getting-started.md) (Compilación de una aplicación de lienzo) 
- **Automatizar los procesos empresariales con Flow**: use un flujo de proceso de negocio para definir un conjunto de fases y pasos para lograr un resultado deseado. Vea [Create a flow that uses the Common Data Service](/flow/common-data-model-intro) (Creación de un flujo que use Common Data Service).
 
En la próxima versión preliminar pública de **Common Data Service for Analytics** <!-- TODO add link when available  --> también se implementa Common Data Service, para admitir análisis de datos empresariales en un formato estandarizado, incluidas:

- **Soluciones analíticas empaquetadas y personalizadas basadas en entidades de datos estándar**: las aplicaciones analíticas, como Sales Insights, que realiza el seguimiento del rendimiento de ventas histórico, proporcionan información coherente con independencia de dónde se usaran originalmente los datos; porque la experiencia de integración de datos asigna datos de otros orígenes (por ejemplo, Salesforce.com) a formas de entidad de Common Data Service. Esto simplifica la solución de análisis para centrarse en la semántica de los datos de entidades bien definidas, como clientes potenciales y oportunidades.
- **Integración de datos de Power Query sin código o con poco código**: se usa la experiencia integrada para crear, rellenar, transformar y enriquecer las entidades. 
- **Traer almacenamiento de Azure propio**: sacar partido de la pila de datos de Azure para que los datos estén disponibles para Common Data Service for Analytics. Las entidades se almacenan en el mismo formato de modelo de datos común, reconocido por las soluciones analíticas.

