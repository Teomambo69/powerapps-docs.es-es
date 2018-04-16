---
title: Entidades de Common Data Service for Apps | Microsoft Docs
description: Obtenga información sobre las entidades disponibles en Common Data Service for Apps.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/19/2018
ms.author: jdaly
ms.openlocfilehash: 98f2360e29af7cb0bdf5caf041dfa13b933e6323
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="common-data-service-for-apps-entities"></a>Entidades de Common Data Service for Apps

Proporcionar almacenamiento para los datos es la función más importante de Common Data Service for Apps. Common Data Service incluye un conjunto básico de entidades que proporcionan estructura para los datos usados por las aplicaciones empresariales. 

Puede ver el conjunto básico de las entidades en la [referencia de entidades de Common Data Service for Apps](reference/about-entity-reference.md).

## <a name="modify-entities"></a>Modificar entidades

Puede modificar los metadatos de entidad mediante varios métodos diferentes.

### <a name="use-designers"></a>Usar diseñadores

Hay varias maneras de modificar los metadatos de entidad mediante diseñadores.


|Diseñador  |Descripción  |
|---------|---------|
|powerapps.com|El enfoque más sencillo y común para modificar el esquema consiste en usar el sitio [powerapps.com](https://web.powerapps.com/) para modificar el Common Data Service asociado a un entorno. Los cambios que se aplican aquí se ejecutan en el contexto de una solución predeterminada de Common Data Service no administrada. <!-- TODO: Add link to topic that describes this -->|
|Explorador de soluciones predeterminado de Common Data Service|Hay otro diseñador disponible en el sitio [powerapps.com](https://web.powerapps.com/) cuando se modifica Common Data Service. En la esquina inferior izquierda, el botón **Opciones avanzadas** abre el Explorador de soluciones por la solución predeterminada de Common Data Service. |
|Explorador de soluciones para la solución |Si se va a distribuir una solución, las entidades, atributos o relaciones se deben crear en el contexto de la solución no administrada que se va a usar para desarrollar la solución. <br /> Más información: [Crear un editor de soluciones y una solución](introduction-solutions.md#create-a-solution-publisher-and-solution)|
|Desde el editor de formularios|Al modificar un formulario de aplicación controlada por modelos para una entidad, puede hacer clic en el botón **Nuevo campo** del **Explorador de campos**. Si se crea un campo de búsqueda, se creará una relación de entidad para admitirlo.|

### <a name="import-a-solution"></a>Importar una solución

Una solución puede contener metadatos de entidad y otros componentes personalizados. La importación de una solución administrada o no administrada al inquilino de Common Data Service incluirá esas entidades o ampliará las existentes con los nuevos metadatos de entidad que contienen.

### <a name="from-a-data-source-using-power-query"></a>Desde un origen de datos con Power Query

Se pueden crear entidades y rellenarlas con datos mediante Power Query. Más información: [Add data to an entity in the Common Data Service by using Power Query](../../maker/common-data-service/data-platform-cds-newentity-pq.md) (Adición de datos a una entidad en Common Data Service mediante Power Query)

### <a name="use-metadata-services"></a>Usar servicios de metadatos

Los servicios web expuestos en Common Data Service incluyen funciones para crear, leer, escribir y eliminar metadatos de entidad. Estos servicios se suelen usar para leer los metadatos porque esos datos pueden informar al código en tiempo de ejecución sobre cómo se ha personalizado el entorno.

Más información: [Servicios de metadatos](use-web-services.md#metadata-services)

## <a name="entity-metadata"></a>Metadatos de entidad

El modelo de datos se define como metadatos que se almacenan en Common Data Service. Estos datos sobre el esquema se conocen como *metadatos de entidad*. 

- La [clase EntityMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata) define esto con el servicio de organización. 
- [EntityMetadata EntityType](/dynamics365/customer-engagement/web-api/entitymetadata) define esto para la API web. 

Los metadatos de entidad incluyen la información siguiente:


|Datos  |Descripción  |
|---------|---------|
|Propiedades de entidad|Cada entidad tiene casi 100 propiedades que describen cómo se identifica y qué se puede hacer con ella.  Más información: [Metadatos de entidad](entity-metadata.md)|
|Atributos|La propiedad `Attributes` de la entidad es una colección de atributos. Cada atributo tiene aproximadamente 50 propiedades para describir cómo se identifica, el tipo de datos que contiene, cómo se le da formato y qué se puede hacer con él. Más información: [Metadatos de atributo](entity-attribute-metadata.md)|
|Relaciones|Tres de las propiedades de entidad son colecciones de relaciones entre entidades. Estas colecciones contienen distintos tipos de relaciones: varios a varios, varios a uno y uno a varios. Más información: [Entity Relationships Metadata](entity-relationship-metadata.md) (Metadatos de las relaciones de entidad)|
|Privilegios|Una de las propiedades de entidad es una colección de entre cero y ocho privilegios que identifican los tipos de operaciones de datos que se pueden realizar en esa entidad con un identificador único asociado a cada una de ellas. Estas operaciones incluyen: *Append*, *AppendTo*, *Assign*, *Create*, *Delete*, *Read*, *Share* y *Write*.|
|Claves|De forma predeterminada, cada entidad tiene un único atributo GUID (identificador único global) y la propiedad `Keys` es una colección vacía. Se pueden agregar claves alternativas a una entidad. Más información: [Claves de entidad](entity-metadata.md#entity-keys)|

> [!TIP]
> Desarrollar un entendimiento de los metadatos de entidad en el sistema puede ayudar a entender cómo funciona Common Data Service. Muchas de las propiedades también controlan lo que pueden hacer las entidades en las aplicaciones controladas por modelos. En los diseñadores disponibles para modificar los metadatos no se pueden mostrar todos los detalles encontrados en los metadatos. Se puede instalar una aplicación controlada por modelos denominada Explorador de metadatos que permite ver todas las entidades ocultas y las propiedades de metadatos que se encuentran en el sistema. Más información: [Exploración de los metadatos de su organización (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/browse-your-metadata)

### <a name="see-also"></a>Vea también

[Common Data Service for Apps Developer Overview](overview.md) (Introducción para desarrolladores de Common Data Service for Apps)


