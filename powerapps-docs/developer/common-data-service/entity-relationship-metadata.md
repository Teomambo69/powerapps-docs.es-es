---
title: Metadatos de relación entre entidades | Microsoft Docs
description: Obtener más información sobre los metadatos de relación de entidad usados en Common Data Service.
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
ms.openlocfilehash: d6d0f5aee398d83227f365ac5bb73ccea8068ed4
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "3126515"
---
# <a name="entity-relationship-metadata"></a>Metadatos de relaciones entre entidades

Al mirar el explorador de soluciones o a las tres colecciones de relaciones en `EntityMetadata`, es posible que piense que existen tres tipos de relaciones entre entidades. Realmente solo hay dos, como se muestra en la siguiente tabla.

|Tipo de relación|Descripción|
|--|--|
|Uno a varios<br />[OneToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.onetomanyrelationshipmetadata)|Una relación entre entidades en la que un registro de entidad para **Entidad principal** se puede asociar a muchos otros registros de **Entidad relacionada** debido a un campo de búsqueda en la entidad relacionada.<br />Al ver un registro de entidad principal puede ver una lista de los registros de entidad relacionados asociados a este.|
|Varios a varios<br />[ManyToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.manytomanyrelationshipmetadata)|Una relación de entidad que depende de una *Entidad relación* especial, a veces denominada una entidad de *intersección*, para que se puedan relacionar muchos registros de una entidad con muchos registros de otra entidad.<br />Para ver los registros de cualquier entidad en una relación de varios a varios puede ver una lista de los registros de la otra entidad relacionados con esta.|

La colección `EntityMetadata` `ManyToOneRelationships` contiene tipos [OneToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.onetomanyrelationshipmetadata). Las relaciones de uno a varios existen entre entidades y hacen referencia a cada entidad como *Entidad principal* o *Entidad relacionada*. La entidad relacionada, a veces denominada la *entidad secundaria*, tiene un atributo de búsqueda que permite almacenar una referencia en un registro desde la entidad principal, a veces denominada la *entidad principal*. Una relación de varios a uno es tan solo una relación de unos a varios desde la perspectiva de la entidad relacionada.

> [!NOTE]
> Aunque las entidades relacionadas a veces se denominen *entidades secundarias*, no se deben confundir con [Entidades secundarias](entity-metadata.md#child-entities), que se hace referencia a cómo la seguridad se aplica a las entidades relacionadas.

Más información: [Creación de relaciones entre entidades](../../maker/common-data-service/data-platform-entity-lookup.md)

## <a name="cascade-configuration"></a>Configuración en cascada

Cuando existe una relación entre entidades de uno a varios, hay comportamientos en cascada que se pueden configurar para preservar la integridad de los datos y automatizar los procesos de negocio. Más información: [Comportamiento en cascada de las relaciones entre entidades](configure-entity-relationship-cascading-behavior.md).

## <a name="create-a-hierarchy-of-entities"></a>Creación de una jerarquía de entidades

Dentro de una relación de uno a varios que se hace referencia a sí misma puede establecer una jerarquía configurando la propiedad `IsHierarchical` en `true`.

Con las aplicaciones basadas en modelos, esto habilita una experiencia que le permite ver e interactuar con la jerarquía. 

Para los desarrolladores, habilita nuevos tipos de consulta en función de la jerarquía mediante los operadores `Under` y `Not Under`.

Más información: [Guía para desarrolladores para Common Data Service: consulta y visualización de datos relacionados jerárquicamente](/dynamics365/customer-engagement/customize/query-visualize-hierarchical-data).

### <a name="see-also"></a>Vea también

[Entidades de Common Data Service](entities.md)
