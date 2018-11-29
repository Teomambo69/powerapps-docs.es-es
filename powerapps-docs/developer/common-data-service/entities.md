---
title: Entidades de Common Data Service para aplicaciones | Microsoft Docs
description: Conozca las entidades disponibles en Common Data Service para aplicaciones.
services: ''
suite: powerapps
documentationcenter: na
author: mayadumesh
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/31/2018
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
<!-- 
Was Mike Carter
This topic was not migrated it was written for PowerApps 

Overlap with content in https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/introduction-entities

-->

# <a name="common-data-service-for-apps-entities"></a>Entidades de Common Data Service para aplicaciones

Proporcionar almacenamiento para los datos es la función más importante de Common Data Service para aplicaciones. Common Data Service incluye un conjunto básico de entidades que proporcionan la estructura para los datos que utilizan las aplicaciones empresariales. 

Puede ver el conjunto básico de entidades en [Common Data Service para aplicaciones](reference/about-entity-reference.md).

## <a name="modify-entities"></a>Modificar entidades

Puede modificar los metadatos de la entidad de varias formas diferentes.

### <a name="use-designers"></a>Utilizar diseñadores

Hay varias formas de editar metadatos de entidad mediante un diseñadores.


|Diseñador  |Descripción  |
|---------|---------|
|powerapps.com|El enfoque más fácil y común para modificar el esquema es usar el sitio [powerapps.com](https://web.powerapps.com/) para editar el Common Data Service asociado a un entorno. Los cambios que se aplican aquí se realizan en el contexto de una solución no administrada y predeterminada de Common Data Service. <!-- TODO: Add link to topic that describes this -->|
|Explorador de soluciones predeterminadas de Common Data Service|Hay algún otro diseñador disponible en el sitio [powerapps.com](https://web.powerapps.com/) al editar Common Data Service. En la esquina inferior izquierda, el botón **Avanzado** abrirá el explorador de soluciones para la solución predeterminada de Common Data Service. |
|Explorador de soluciones para la solución |Si va a distribuir una solución, debe crear alguna nuevas entidades, atributos o relaciones en el contexto de la solución no administrada que usará para desarrollar su solución. <br /> Más información: [Crear un editor de soluciones y una solución](introduction-solutions.md#create-a-solution-publisher-and-solution)|
|Desde el editor de formularios|Al editar una aplicación basada en modelos para una entidad, puede hacer clic en el botón **Nuevo campo** en **Explorador de campos**. Si crea un campo de búsqueda, creará una nueva relación entre entidades para admitirlo.|

### <a name="import-a-solution"></a>Importación de soluciones

Las soluciones pueden contener metadatos de la entidad y otros componentes personalizados. Importar una solución administrada o no administrada aparecen en el inquilino de Common Data Service para aplicaciones incluirá esas entidades o extenderá las entidades existentes con los nuevos metadatos de la entidad que contienen.

### <a name="from-a-data-source-using-power-query"></a>Desde un origen de datos mediante Power Query

Puede crear entidades y rellenarlas con datos mediante Power Query. Más información: [Agregar datos a una entidad en Common Data Service mediante Power Query](../../maker/common-data-service/data-platform-cds-newentity-pq.md).

### <a name="use-metadata-services"></a>Usar servicios de metadatos

Los servicios web expuestos en CDS for Apps incluyen funcionalidades para crear, leer, escribir y eliminar metadatos de entidades. Estos servicios se utilizan con más frecuencia para leer los metadatos porque esos datos pueden informar al código en tiempo de ejecución sobre cómo se ha personalizado el entorno. Más información: [Servicios de metadatos](metadata-services.md)

## <a name="entity-metadata"></a>Metadatos de la entidad

El modelo de datos se define como los metadatos que están almacenados en Common Data Service. Estos datos sobre el esquema se conocen como *Metadatos de la entidad*. 

- La [clase EntityMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata) define esto con el servicio de la organización. 
- El [tipo de entidad EntityMetadata](/dynamics365/customer-engagement/web-api/entitymetadata) define esta opción para la API web. 

Los metadatos de la entidad incluyen la información siguiente:


|Datos  |Descripción  |
|---------|---------|
|Propiedades de entidad|Cada entidad tiene casi 100 propiedades que describen cómo se identifica y lo que se puede hacer con él.  Más información: [Metadatos de entidad](entity-metadata.md).|
|Atributos|La propiedad de la entidad `Attributes` es una colección de atributos. Cada atributo tiene más 50 propiedades para describir cómo se identifica, el tipo de datos que contiene, cómo se formatea y lo que se puede hacer con él. Más información: [Metadatos del atributo](entity-attribute-metadata.md)|
|Relaciones|Tres de las propiedades de la entidad son colecciones de relaciones entre entidades. Estas colecciones contienen varios tipos de relaciones: varios a varios, varios a uno y uno a varios. Más información: [Metadatos de las relaciones entre entidades](entity-relationship-metadata.md)|
|Privilegios|Una de las propiedades de una entidad es una colección de entre 0 y 8 privilegios que identifica los tipos de operaciones de datos que se pueden realizar en esa entidad con un identificador único asociado a cada uno. Estas operaciones incluyen: *Anexar*, *Anexar a*, *Asignar*, *Crear*, *Eliminar*, *Leer*, *Compartir* y *Escribir*.|
|Claves|De forma predeterminada, cada entidad tiene un único atributo GUID (identificador único global) y la propiedad `Keys`es una colección vacía. Puede agregar las claves alternativas a una entidad. Más información: [Claves de entidad](entity-metadata.md#entity-keys)|

> [!TIP]
> Desarrollar y comprender los metadatos de la entidad en el sistema le pueden ayudar a entender cómo funciona Common Data Service. Muchas de las propiedades también controlan qué pueden hacer las entidades en aplicaciones basadas en modelos. Los diseñadores disponibles para editar metadatos no pueden mostrar todos los detalles encontrados en los metadatos. Puede instalar una aplicación basada en modelos llamada Explorador de metadatos que le permitirá ver todas las entidades y propiedades de metadatos ocultas que se encuentran en el sistema. Más información: [Examinar los metadatos para su organización](/dynamics365/customer-engagement/developer/browse-your-metadata)

### <a name="see-also"></a>Vea también

[Información general para desarrolladores de Common Data Service para aplicaciones](overview.md)


