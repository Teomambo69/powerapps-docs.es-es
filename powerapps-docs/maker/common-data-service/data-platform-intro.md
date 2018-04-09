---
title: Common Data Service for Apps | Microsoft Docs
description: Introducción a Common Data Service for Apps, las entidades y la lógica del lado servidor.
services: powerapps
documentationcenter: na
author: clwesene
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 3/21/2018
ms.author: clwesene
ms.openlocfilehash: 9a247ab22970538c56c8a1fb1578b197f9898f92
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="common-data-service-for-apps"></a>Common Data Service for Apps

Common Data Service permite almacenar y administrar de forma segura los datos que se usan en las aplicaciones que ha desarrollado o las de Microsoft y proveedores de aplicaciones. Los datos de Common Data Service se almacenan en un conjunto de entidades estándar y personalizadas. Una entidad es un conjunto de campos que se usan para almacenar datos, de forma similar a como lo hace tabla en una base de datos. Después de que se almacenan los datos puede usar Microsoft PowerApps para compilar aplicaciones completas con sus datos:

* Aproveche las entidades existentes o cree entidades personalizadas para proporcionar soporte al escenario y la aplicación.
* Cree PowerApps y flujos directamente con Common Data Service.
* Agregue campos personalizados y relaciones a entidades estándar donde se necesite información adicional.
* Cree campos calculados y consolidados para las entidades con el fin de proporcionar cálculos y análisis coherentes en todas las aplicaciones.
* Defina reglas de negocio para garantizar la calidad de datos dentro de las entidades, con independencia de qué aplicación obtenga acceso a los datos o los modifique.
* Cree flujos de trabajo y aproveche la integración con Microsoft Flow para controlar acciones y procesos de negocio adicionales sobre los datos.
* Incorpore entidades estándar y personalizadas a una aplicación que desarrolle, con la misma facilidad que lo haría con los datos de otros orígenes.
* Conéctese a los datos desde Microsoft Excel mediante los complementos de productividad de Common Data Service.
* Importe y sincronice los datos con facilidad mediante Power Query.
* Proteja los datos en su organización mediante la seguridad basada en roles en las entidades estándar y personalizadas.
* Proporcione compatibilidad global para los datos y aplicaciones aprovechando la traducción de los nombres de entidades y campos al lenguaje de los usuarios.

Cada entidad contiene un conjunto de registros que los usuarios pueden crear, leer, actualizar y eliminar en función de sus permisos. Puede crear relaciones entre entidades para que pueda buscar información en una entidad basada en un registro de otra entidad. Por ejemplo, puede crear una entidad personalizada que realice el seguimiento de los eventos a los que un cliente había asistido. Al agregar Cliente a una entidad personalizada como campo de búsqueda, se establece una relación entre las dos entidades que se pueden utilizar tanto en la aplicación como en la creación de informes.

Para más información sobre la compra de un plan para utilizar Common Data Service, consulte la [información sobre los precios](../../administrator/pricing-billing-skus.md).

## <a name="why-use-the-common-data-service-for-apps"></a>¿Por qué usar Common Data Service for Apps?
Las entidades de Common Data Service, tanto estándar como personalizadas, permiten una opción de almacenamiento seguro en la nube para los datos. Las entidades le permiten crear una definición centrada en la empresa de los datos para usarla en las aplicaciones. Si no está seguro de si las entidades son la mejor opción, tenga en cuenta estas ventajas:

* **Fáciles de administrar**: tanto los metadatos como los datos se almacenan en la nube. No tiene que preocuparse por los detalles de cómo se almacenan.
* **Fáciles de compartir**: puede compartir fácilmente datos con sus compañeros porque PowerApps administra los permisos.
* **Fáciles de proteger**: los datos se almacenan de forma segura para que los usuarios solo los puedan ver si se les concede acceso. La seguridad basada en roles le permite controlar el acceso a entidades de los diferentes usuarios dentro de la organización.
* **Metadatos completos**: los tipos de datos y las relaciones se usan directamente desde dentro de PowerApps. Por ejemplo, la definición de una dirección URL de tipo de campo presentará los datos como un hipervínculo dentro de la aplicación.
* **Lógica y validación**: defina campos calculados, reglas de negocio, flujos de trabajo y flujos de procesos de negocio para garantizar la calidad de los datos y controlar los procesos empresariales.
* **Herramientas de productividad**: las entidades están disponibles en los complementos para que Microsoft Excel aumente la productividad y garantice que se pueda tener acceso a los datos.

Al desarrollar una aplicación, puede usar entidades estándar, entidades personalizadas o ambas. Si una entidad estándar puede servir para un fin determinado de su aplicación, es mejor utilizarla en lugar de desarrollar una entidad personalizada que haga lo mismo. Si una entidad estándar sirve para una finalidad con solo realizar unos pocos cambios, puede agregar campos para adaptarlos a sus necesidades.

* Common Data Service proporciona entidades estándar de forma predeterminada. Están diseñadas, de acuerdo con los procedimientos recomendados, para plasmar los conceptos más comunes de una organización, como contactos, cuentas y productos. Para obtener una lista completa de entidades, consulte [Entidades estándar](data-platform-intro.md#standard-entities).
* Puede ampliar la funcionalidad de entidades estándar mediante la creación de una o varias entidades personalizadas para almacenar información exclusiva de su organización. Para más información, consulte [Crear una entidad personalizada](create-custom-entity.md).

> [!NOTE]
> Si es posible, use entidades estándar (si es preciso, a los que se han agregado campos personalizados). Esto garantizará que en el futuro podrá beneficiarse de las nuevas características o aplicaciones que aprovechan estas entidades.

## <a name="interacting-with-entities"></a>Interactuar con las entidades

Cuando se usa una entidad estándar o se crea una entidad personalizada, existen varios elementos disponibles dentro de cada una y se pueden realizar diferentes acciones. Las características que se tienen que usar se determinarán en función de lo simple o avanzado que sea el escenario de negocio. Para ver las entidades disponibles dentro del entorno, inicie sesión en [PowerApps](https://web.powerapps.com), haga clic en Datos y después en Entidades en el menú de la izquierda.

### <a name="system-fields"></a>Campos del sistema
Todas las entidades, ya sean estándar o personalizadas, se crean con un conjunto de campos de solo lectura que no se pueden cambiar, eliminar ni establecer para un valor. Estos son los campos más importantes del sistema:

* Cada **campo** permite definir una parte de la información que se va a recopilar y el formato o el tipo de datos que le gustaría mostrar. Los campos son similares a las columnas de las bases de datos o Excel.
* Las **claves** alternativas permiten la búsqueda eficaz y precisa y la interacción con los registros de la entidad cuando no se usa el identificador estándar. Esto es especialmente importante cuando se usa una clave empresarial o se realiza la integración con un sistema externo.
* Cada entidad puede tener varias **relaciones** con otras entidades para admitir búsquedas y consultas entre entidades. Se pueden crear relaciones para admitir relaciones varios a uno, uno a varios y varios a varios.
* **Las vistas** permiten presentar cada entidad de varias formas, incluidos qué campos se muestran, para filtrar y ordenar los datos. Estas presentaciones se guardan como vistas y se pueden usar en otras aplicaciones; por ejemplo, es posible que solo quiera ver Cuentas activas dentro de la aplicación, por lo que usaría una vista con un filtro previo para mostrar solo las cuentas activas para evitar repetir el filtro en cada aplicación que lo usa.
* Se pueden usar **reglas de negocio** para validar los datos que se crean y actualizan en las entidades para garantizar la calidad de los datos. Cada regla de negocio puede validar los datos en varios campos y entidades, y mostrar mensajes de advertencia y error, independientemente de la aplicación que se use para crear los datos.
* **Los datos** almacenados en Common Data Service están disponibles a través del portal de PowerApps, PowerApps, Microsoft Excel y las API web para desarrolladores.

## <a name="logic-and-validation"></a>Lógica y validación

Las entidades de Common Data Service pueden aprovechar la lógica enriquecida y del lado de servidor, y la validación para garantizar la calidad de los datos y reducir el código repetitivo en las aplicaciones que crean y usan los datos de la entidad.

* Las **reglas de negocio** pueden validar los datos en varios campos y entidades, y mostrar mensajes de advertencia y error, independientemente de la aplicación que se use para crear los datos. Para obtener más información, vea [Create a business rule](./data-platform-create-business-rule.md) (Creación de una regla de negocio)
* **Los flujos de proceso de negocio** guían a los usuarios para asegurarse de que los datos se escriben de forma coherente y cada vez se siguen los mismos pasos. En la actualidad, los flujos de proceso de negocio solo se admiten para aplicaciones controladas por modelos. Para obtener más información, vea [Información general sobre flujos de proceso de negocio](/dynamics365/customer-engagement/customize/business-process-flows-overview).
* **Los flujos de trabajo** permiten automatizar los procesos de negocio sin interacción del usuario. Para obtener más información, vea [Información general sobre flujos de trabajo](/dynamics365/customer-engagement/customize/workflow-processes).
* **La lógica de negocios con código** admite escenarios de desarrollador más avanzados en los que ampliar la aplicación directamente mediante código. Para obtener más información, vea [Apply business logic with code](../../developer/common-data-service/apply-business-logic-with-code.md) (Aplicación de lógica de negocios con código).

## <a name="getting-data-into-the-common-data-service"></a>Enviar datos a Common Data Service

Hay varias maneras de empezar a enviar datos a Common Data Service:

* Cree una PowerApp o un flujo para empezar a crear los datos.
* Use Power Query para conectarse a un origen de datos en línea o local, e importarlos directamente a Commmon Data Service. Power Query también permite crear las entidades durante la importación en función del esquema del origen, así como realizar transformaciones en los datos durante la importación. Para obtener más información, vea: [Add data to an entity in the Common Data Service by using Power Query](./data-platform-cds-newentity-pq.md) (Adición de datos a una entidad en Common Data Service mediante Power Query)

## <a name="developer-capabilities"></a>Funciones para desarrolladores

Además de las características disponibles a través del portal de [PowerApps](https://web.powerapps.com), Common Data Service también incluye características para desarrolladores para tener acceso mediante programación a los metadatos y datos para crear entidades y lógica de negocios, así como para interactuar con los datos. Para obtener más información, vea [Common Data Service for Apps Developer Overview](../../developer/common-data-service/overview.md) (Introducción para desarrolladores de Common Data Service for Apps).

## <a name="get-started"></a>Introducción
Para probarlo, cree una aplicación mediante una entidad estándar, o bien [cree una entidad personalizada](create-custom-entity.md) y, después, [cree una aplicación que utilice dicha entidad](../canvas-apps/data-platform-create-app.md).

## <a name="privacy-notice"></a>Aviso de privacidad
Con el modelo de datos común de Microsoft PowerApps, recopilamos y almacenamos los nombres de los campos y las entidades personalizadas en nuestros sistemas de diagnóstico.  Usamos esta información para mejorar el modelo de datos común para nuestros clientes. Los nombres de entidades y de campos creados nos servirán para comprender qué escenarios son habituales en toda la comunidad de Microsoft PowerApps y determinar las carencias en la cobertura de entidades estándar del servicio, por ejemplo, los esquemas relacionados con las organizaciones. Microsoft no accede a los datos de las tablas de base de datos asociadas a estas entidades ni los usa; tampoco los replica fuera de la región en que esté aprovisionada la base de datos. Sin embargo, tenga en cuenta que es posible que los nombres de campos y entidades personalizadas se repliquen entre regiones y se eliminen de acuerdo con nuestras directivas de retención de datos. Microsoft se compromete a respetar su privacidad, como se describe con más detalle en nuestro [Centro de confianza](https://www.microsoft.com/trustcenter/Privacy/default.aspx).

