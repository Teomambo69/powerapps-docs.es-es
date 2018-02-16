---
title: "Descripción de las entidades | Microsoft Docs"
description: "Introducción a entidades, campos, relaciones y bases de datos."
services: powerapps
documentationcenter: na
author: clwesene
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/20/2017
ms.author: kfend
ms.openlocfilehash: da01fe6e89e64e07b5ce4eb0350bc2ac1f54ff30
ms.sourcegitcommit: e827813cd898ca9a1046b5952ea5e32ce2989a65
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="understand-entities-in-the-common-data-service"></a>Descripción de las entidades de Common Data Service

Common Data Service permite almacenar y administrar los datos de forma segura en un conjunto de entidades estándar y personalizadas. Una entidad es un conjunto de campos que se usan para almacenar datos, de forma similar a como lo hace tabla en una base de datos. Después de que se almacenan los datos puede usar Microsoft PowerApps para compilar aplicaciones completas con sus datos:

* Importe datos en entidades estándar o personalizadas.
* Cree entidades personalizadas para proporcionar soporte a un escenario y una aplicación.
* Agregue campos personalizados a entidades estándar donde se necesite información adicional.
* Incorpore entidades estándar y personalizadas a una aplicación que desarrolle, con la misma facilidad que lo haría con los datos de otros orígenes.
* Aproveche los complementos de productividad para acceder a los datos de Microsoft Excel y Outlook.
* Proteja los datos en su organización mediante la seguridad basada en roles en las entidades estándar y personalizadas.
* Incluya a listas desplegables de datos predefinidos, como el país, el saludo o la divisa.
* Proporcione compatibilidad global para sus datos y aplicaciones, para lo que debe sacar provecho de la traducción de los nombres de entidades y campos.

Cada entidad contiene un conjunto de registros que los usuarios pueden crear, leer, actualizar y eliminar. Puede crear relaciones entre entidades para que pueda buscar información en una entidad basada en un registro de otra entidad. Por ejemplo, puede crear una entidad personalizada que realice el seguimiento de los eventos a los que un cliente había asistido. Al agregar Cliente a una entidad personalizada como campo de búsqueda, se establece una relación entre las dos entidades que se pueden utilizar tanto en la aplicación como en la creación de informes.

Para más información sobre la compra de un plan para utilizar Common Data Service, consulte la [información sobre los precios](pricing-billing-skus.md).

## <a name="why-use-entities"></a>¿Por qué usar entidades?
Las entidades de Common Data Service, tanto estándar como personalizadas, permiten una opción de almacenamiento seguro en la nube para los datos. Las entidades le permiten crear una definición centrada en la empresa de los datos para usarla en las aplicaciones. Si no está seguro de si las entidades son la mejor opción, tenga en cuenta estas ventajas:

* **Fáciles de administrar**: tanto los metadatos como los datos se almacenan en la nube. No tiene que preocuparse por los detalles de cómo se almacenan.
* **Fáciles de compartir**: puede compartir fácilmente datos con sus compañeros porque PowerApps administra los permisos.
* **Fáciles de proteger**: los datos se almacenan de forma segura para que los usuarios solo los puedan ver si se les concede acceso. La seguridad basada en roles le permite controlar el acceso a entidades de los diferentes usuarios dentro de la organización.
* **Metadatos completos**: los tipos de datos y las relaciones se usan directamente desde dentro de PowerApps. Por ejemplo, la definición de una dirección URL de tipo de campo presentará los datos como un hipervínculo dentro de la aplicación.
* **Herramientas de productividad**: las entidades están disponibles en los complementos para que Microsoft Excel y Outlook aumenten la productividad y haya una garantía de que se puede acceder a los datos.
* **Listas desplegables**: se incluyen listas desplegables de una amplia variedad de listas estándar para proporcionar listas desplegables rápidas en las aplicaciones y entidades.

## <a name="standard-and-custom-entities"></a>Entidades estándar y personalizadas
Al desarrollar una aplicación, puede usar entidades estándar, entidades personalizadas o ambas. Si una entidad estándar puede servir para un fin determinado de su aplicación, es mejor utilizarla en lugar de desarrollar una entidad personalizada que haga lo mismo. Si una entidad estándar sirve para una finalidad con solo realizar unos pocos cambios, puede agregar campos para adaptarlos a sus necesidades.

* Common Data Service proporciona entidades estándar de forma predeterminada. Están diseñadas, de acuerdo con los procedimientos recomendados, para plasmar los conceptos más comunes de una organización, como contactos, cuentas y productos. Para obtener una lista completa de entidades, consulte [Entidades estándar](data-platform-intro.md#standard-entities).
* Puede ampliar la funcionalidad de entidades estándar mediante la creación de una o varias entidades personalizadas para almacenar información exclusiva de su organización. Para más información, consulte [Crear una entidad personalizada](data-platform-create-entity.md).

> [!NOTE]
> Si es posible, use entidades estándar (si es preciso, a los que se han agregado campos personalizados). Esto garantizará que en el futuro podrá beneficiarse de las nuevas características o aplicaciones que aprovechan estas entidades.


## <a name="fields"></a>Campos
Todos los campos tienen un nombre, un nombre para mostrar, un tipo de datos y una validación simple. Los tipos de datos incluyen, por ejemplo, **Texto**, **Fecha** o **Número**. La validación garantiza que los campos requeridos contienen datos y registros únicos si la entidad así lo requiere. Cada campo forma parte de una de estas tres categorías: campos del sistema, campos estándar o campos personalizados.

### <a name="system-fields"></a>Campos del sistema
Todas las entidades, ya sean estándar o personalizadas, se crean con un conjunto de campos de solo lectura que no se pueden cambiar, eliminar ni establecer para un valor. Para más información, consulte [Campos de título de registro y de sistema](data-platform-create-entity.md#system-fields-and-the-record-title-field). Estos son los campos más importantes del sistema:

* **Fecha del registro creada**: la fecha y hora en que se creó un registro.
* **Creado por**: el usuario que creó el registro.
* **Fecha del registro modificada**: la fecha y hora en que se modificó un registro por última vez.
* **Última modificación por**: el usuario que realizó la última modificación del registro.

### <a name="standard-fields"></a>Campos estándar
Cada entidad estándar contiene un conjunto de campos predeterminados que no se pueden cambiar ni eliminar. Para obtener una lista de las entidades y sus campos, y una lista de las listas desplegables, consulte [Entidades estándares](https://docs.microsoft.com/common-data-service/entity-reference/standard-entities).

### <a name="custom-fields"></a>Campos personalizados
Puede crear campos personalizados en una entidad estándar o en una entidad personalizada. Debe especificar el nombre, el nombre para mostrar y el tipo de datos de cada campo personalizado. Para obtener una lista completa de los tipos compatibles, consulte [Entity field data types](https://docs.microsoft.com/common-data-service/entity-reference/field-data-types) (Tipos de datos del campo Entidad).

## <a name="lookup-relationships"></a>Relaciones de búsqueda
Puede navegar entre los registros de las entidades si tienen una relación que se define como un campo del tipo de datos **Buscar**. Para crear una relación de búsqueda, agregue un campo del tipo de datos **Buscar** a una entidad y apunte a la entidad en la que desea buscar información. Para más información, consulte [Relaciones de entidad mediante un campo de búsqueda](data-platform-entity-lookup.md).

## <a name="standard-entities"></a>Entidades estándar
Para obtener una lista de las entidades y sus campos, y una lista de las enumeraciones, consulte [Entidades estándares](https://docs.microsoft.com/common-data-service/entity-reference/standard-entities).

| Grupo funcional | Descripción |
| --- | --- |
| Customer Service |Las entidades Customer Service administran los problemas de los clientes, incluido el seguimiento, el escalado y la documentación. |
| Foundation |Las entidades Foundation contienen información relevante para casi cualquier otro grupo de entidades. Este grupo contiene entidades como Address y Currency. |
| People, Organizations y Groups |Estas entidades abarcan un amplio conjunto de personas y organizaciones con las que puede interactuar, incluidos empleados, contratistas, donantes, voluntarios, seguidores, ex alumnos y familias. |
| Purchasing |Las entidades Purchasing permiten crear soluciones de compras. |
| Ventas |Las entidades Sales permiten crear soluciones de ventas integrales, desde seguimiento de clientes potenciales y oportunidades hasta seguimiento de contactos, aceptación y entrega de pedidos o envío de facturas. |

## <a name="get-started"></a>Introducción
Para probarlo, cree una aplicación mediante una entidad estándar, o bien [cree una entidad personalizada](data-platform-create-entity.md) y, después, [cree una aplicación que utilice dicha entidad](data-platform-create-app.md).

<!--TODO - Add Link for Standard entity app - Template? -->

## <a name="privacy-notice"></a>Aviso de privacidad
Con el modelo de datos común de Microsoft PowerApps, recopilamos y almacenamos los nombres de los campos y las entidades personalizadas en nuestros sistemas de diagnóstico.  Usamos esta información para mejorar el modelo de datos común para nuestros clientes. Los nombres de entidades y de campos creados nos servirán para comprender qué escenarios son habituales en toda la comunidad de Microsoft PowerApps y determinar las carencias en la cobertura de entidades estándar del servicio, por ejemplo, los esquemas relacionados con las organizaciones. Microsoft no accede a los datos de las tablas de base de datos asociadas a estas entidades ni los usa; tampoco los replica fuera de la región en que esté aprovisionada la base de datos. Sin embargo, tenga en cuenta que es posible que los nombres de campos y entidades personalizadas se repliquen entre regiones y se eliminen de acuerdo con nuestras directivas de retención de datos. Microsoft se compromete a respetar su privacidad, como se describe con más detalle en nuestro [Centro de confianza](https://www.microsoft.com/trustcenter/Privacy/default.aspx).

