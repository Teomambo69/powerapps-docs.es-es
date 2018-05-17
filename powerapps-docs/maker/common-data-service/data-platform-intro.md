---
title: ¿Qué es Common Data Service for Apps? | Microsoft Docs
description: Introducción a Common Data Service (CDS) for Apps, las entidades y la lógica del lado servidor.
author: SKjerland
manager: kfile
ms.service: powerapps
ms.topic: overview
ms.component: cds
ms.date: 05/01/2018
ms.author: sharik
ms.openlocfilehash: fb0a7640e0a8b6da6664925528965d3fe6b8c82e
ms.sourcegitcommit: fe556abcfd6bdfeb5fdeea8f07b185b4b502d02f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="what-is-common-data-service-for-apps"></a>¿Qué es Common Data Service for Apps?
Common Data Service (CDS) for Apps permite almacenar y administrar de forma segura los datos que usan las aplicaciones empresariales. Los datos de CDS for Apps se almacenan en un conjunto de entidades. Una *entidad* es un conjunto de campos que se usan para almacenar datos, de forma similar a como lo hace una tabla en una base de datos. CDS for Apps incluye un conjunto básico de entidades estándar que cubre los escenarios típicos, pero también se pueden crear entidades personalizadas específicas para la organización y rellenarlas con datos con Power Query. Después, los creadores de aplicaciones pueden usar PowerApps para crear aplicaciones completas con estos datos.

Para obtener información sobre la compra de un plan para usar CDS for Apps, vea la [información sobre precios](../../administrator/pricing-billing-skus.md).

## <a name="why-use-common-data-service-for-apps"></a>¿Por qué usar Common Data Service for Apps?
Las entidades estándar y personalizadas de CDS for Apps proporcionan una opción de almacenamiento seguro en la nube para los datos. Las entidades permiten crear una definición centrada en la empresa de los datos de la organización para usarla en las aplicaciones. Si no está seguro de si las entidades son la mejor opción, tenga en cuenta estas ventajas:

* **Fáciles de administrar**: tanto los metadatos como los datos se almacenan en la nube. No tiene que preocuparse por los detalles de cómo se almacenan.
* **Fáciles de compartir**: se pueden compartir fácilmente datos con los compañeros&mdash; PowerApps administra los permisos.
* **Fáciles de proteger**: los datos se almacenan de forma segura para que los usuarios solo los puedan ver si se les concede acceso. La seguridad basada en roles le permite controlar el acceso a entidades de los diferentes usuarios dentro de la organización.
* **Metadatos completos**: los tipos de datos y las relaciones se usan directamente desde dentro de PowerApps. Por ejemplo, la definición de una dirección URL de tipo de campo presentará los datos como un hipervínculo dentro de la aplicación.
* **Lógica y validación**: defina campos calculados, reglas de negocio, flujos de trabajo y flujos de procesos de negocio para garantizar la calidad de los datos y controlar los procesos empresariales.
* **Herramientas de productividad**: las entidades están disponibles en los complementos para que Microsoft Excel aumente la productividad y garantice la accesibilidad a los datos.

## <a name="interacting-with-entities"></a>Interactuar con las entidades
Al desarrollar una aplicación, puede usar entidades estándar, entidades personalizadas o ambas. CDS for Apps proporciona entidades estándar de forma predeterminada. Están diseñadas, de acuerdo con los procedimientos recomendados, para plasmar los conceptos y escenarios más comunes de una organización.

![Captura de pantalla en la que se muestra una lista de entidades.](./media/data-platform-cds-intro/entitylist.png "Lista de entidades")

Para obtener una lista completa de entidades, vea [Entity reference](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/reference/about-entity-reference) (Referencia de entidades).

Puede ampliar la funcionalidad de entidades estándar mediante la creación de una o varias entidades personalizadas para almacenar información exclusiva de su organización. Para más información, consulte [Crear una entidad personalizada](create-custom-entity.md).

## <a name="logic-and-validation"></a>Lógica y validación
Las entidades de CDS for Apps pueden aprovechar la lógica enriquecida del lado servidor y la validación para garantizar la calidad de los datos y reducir el código repetitivo en cada aplicación que crea y usa los datos de la entidad.

* Las **reglas de negocio** validan los datos en varios campos y entidades, y proporcionan mensajes de advertencia y error, con independencia de la aplicación que se use para crear los datos. Para obtener más información, vea [Create a business rule](./data-platform-create-business-rule.md) (Creación de una regla de negocio)
* **Los flujos de proceso de negocio** guían a los usuarios para asegurarse de que escriben los datos de forma coherente y cada vez se siguen los mismos pasos. En la actualidad, los flujos de proceso de negocio solo se admiten para aplicaciones controladas por modelos. Para obtener más información, vea [Información general sobre flujos de proceso de negocio](/dynamics365/customer-engagement/customize/business-process-flows-overview).
* **Los flujos de trabajo** permiten automatizar los procesos de negocio sin la interacción del usuario. Para obtener más información, vea [Información general sobre flujos de trabajo](/dynamics365/customer-engagement/customize/workflow-processes).
* **La lógica de negocios con código** admite escenarios de desarrollador avanzados para ampliar la aplicación directamente mediante código. Para obtener más información, vea [Apply business logic with code](../../developer/common-data-service/apply-business-logic-with-code.md) (Aplicación de lógica de negocios con código).

## <a name="developer-capabilities"></a>Funciones para desarrolladores
Además de las características disponibles a través del portal de [PowerApps](https://web.powerapps.com), CDS for Apps también incluye características para desarrolladores con acceso mediante programación a los metadatos y datos para crear entidades y lógica de negocios, así como para interactuar con los datos. Para obtener más información, vea [Common Data Service for Apps Developer Overview](../../developer/common-data-service/overview.md) (Introducción para desarrolladores de Common Data Service for Apps).

## <a name="next-steps"></a>Pasos siguientes
Para empezar a usar CDS for Apps:
* [Creación de una aplicación desde cero mediante una base de datos de Common Data Service](../canvas-apps/data-platform-create-app-scratch.md).
* [Creación de una entidad personalizada](create-custom-entity.md) y, después, [creación de una aplicación que use esa entidad](../canvas-apps/data-platform-create-app.md).
* [Uso de Power Query](./data-platform-cds-newentity-pq.md) para conectarse a un origen de datos en línea o local, e importar los datos directamente a CDS for Apps.

## <a name="privacy-notice"></a>Aviso de privacidad
Con el modelo de datos común de Microsoft PowerApps, Microsoft recopila y almacena los nombres de los campos y las entidades personalizadas en nuestros sistemas de diagnóstico. Usamos esta información para mejorar el modelo de datos común para nuestros clientes. Los nombres de entidades y de campos que los creadores de aplicaciones crean nos servirán para comprender qué escenarios son habituales en toda la comunidad de Microsoft PowerApps y determinar las carencias en la cobertura de entidades estándar del servicio, por ejemplo, los esquemas relacionados con las organizaciones. Microsoft no accede a los datos de las tablas de base de datos asociadas a estas entidades ni los usa; tampoco los replica fuera de la región en que esté aprovisionada la base de datos. Sin embargo, tenga en cuenta que es posible que los nombres de campos y entidades personalizadas se repliquen entre regiones y se eliminen de acuerdo con nuestras directivas de retención de datos. Microsoft se compromete a respetar su privacidad, como se describe con más detalle en nuestro [Centro de confianza](https://www.microsoft.com/trustcenter/Privacy/default.aspx).
