---
title: Metadatos de relaciones de entidad | Microsoft Docs
description: Obtenga información sobre los metadatos de las relaciones de entidad que se usan en Common Data Service for Apps.
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
ms.date: 03/12/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ea59e1eea1c0a85c2de1f2d654c10ed687ffe858
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42863526"
---
# <a name="entity-relationship-metadata"></a>Metadatos de relaciones de entidad

Cuando se examina el Explorador de soluciones o las tres colecciones de relaciones en `EntityMetadata`, es posible que piense que hay tres tipos de relaciones de entidad. En realidad, hay solo dos, como se muestra en la tabla siguiente.

|Tipo de relación|Descripción|
|--|--|
|Uno a varios<br />[OneToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.onetomanyrelationshipmetadata)|Una relación de entidad en la que un registro de entidad para la **Entidad principal** se puede asociar a otros muchos registros **Entidad relacionada** debido a un campo de búsqueda en la entidad relacionada.<br />Al ver un registro de entidad principal se puede ver una lista de los registros de entidad relacionados que están asociados a ella.|
|Varios a varios<br />[ManyToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.manytomanyrelationshipmetadata)|Una relación de entidad que depende de una *Entidad de relación* especial, en ocasiones denominada entidad de *intersección*, para que varios registros de una entidad se puedan relacionar con varios registros de otra.<br />Al ver los registros de cualquier entidad en una relación varios a varios, se puede ver una lista de todos los registros de la otra entidad que están relacionada con ella.|

La colección `EntityMetadata` `ManyToOneRelationships` contiene tipos [OneToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.onetomanyrelationshipmetadata). Las relaciones uno a varios existen entre las entidades y hacen referencia a cada entidad como una *Entidad principal* o una *Entidad relacionada*. La entidad relacionada, que a veces se denomina la *entidad secundaria*, tiene un atributo de búsqueda que permite almacenar una referencia a un registro de la entidad principal, que en ocasiones se denomina *entidad principal*. Una relación varios a uno es simplemente una relación uno a varios vista desde la entidad relacionada.

> [!NOTE]
> Aunque las entidades relacionadas se denominan en ocasiones *entidades secundarias*, no se deben confundir con las [Entidades secundarias](entity-metadata.md#child-entities), que hacen referencia a cómo se aplica la seguridad a las entidades relacionadas.

Más información:
- [Crear y editar relaciones entre entidades (Guía de personalización de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/customize/create-edit-entity-relationships)
- [Personalizar metadatos de relaciones entre entidades (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)

## <a name="cascade-configuration"></a>Configuración en cascada

Cuando existe una relación de entidad de uno a varios, hay comportamientos en cascada que se pueden configurar para conservar la integridad de los datos y automatizar los procesos de negocio.

Más información:

- [Crear relaciones 1:N (uno a varios) o N:1 (uno a varios) (Guía de personalización de Dynamics 365 Customer Engagement) > Comportamiento de las relaciones](/dynamics365/customer-engagement/customize/create-and-edit-1n-relationships#relationship-behavior)
- [Comportamiento de relación entre entidades (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/entity-relationship-behavior)


## <a name="create-a-hierarchy-of-entities"></a>Crear una jerarquía de entidades

Dentro de una relación uno a varios que se hace referencia a sí misma, se puede establecer una jerarquía si se establece la propiedad `IsHierarchical` en `true`.

Con las aplicaciones controladas por modelos, esto permite ver e interactuar con la jerarquía. 

Para los desarrolladores, esto habilita nuevos tipos de consultas basadas en la jerarquía con los operadores `Under` y `Not Under`.

Más información: [Consultar y visualizar datos jerárquicos (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/customize/query-visualize-hierarchical-data)

### <a name="see-also"></a>Vea también

[Entidades de Common Data Service for Apps](entities.md)
