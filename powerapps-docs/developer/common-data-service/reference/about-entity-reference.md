---
title: Acerca de referencia de entidades (Common Data Service) | Microsoft Docs
description: 'Utilice esta referencia para comprender las operaciones disponibles que se pueden realizar para entidades específicas, los atributos predeterminados de cada entidad y las relaciones entre entidades.'
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
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
# <a name="about-the-entity-reference"></a>Acerca de la referencia de entidades

Utilice esta referencia para comprender las operaciones disponibles que se pueden realizar para entidades específicas, los atributos predeterminados de cada entidad y las relaciones entre entidades.

> [!NOTE]
> Esta referencia incluye solo entidades donde:
>
> -  **IsPrivate** es igual a `false`
>    - Esto excluye entidades donde no existe ningún caso de uso externo.
> - **IsIntersect** es igual a `false`
>    - Esto excluye entidades que se usan para definir relaciones de varios a varios.
> - La entidad admite algún tipo de operación de modificación de datos directa.
>    - Esto excluye entidades con las que no puede trabajar directamente. 
>
> Para ver toda la información de metadatos de una entidad de su entorno, vea [Guía de desarrolladores de Common Data Service: Exploración de los metadatos de su organización](/dynamics365/customer-engagement/developer/browse-your-metadata).


## <a name="entity-properties"></a>Propiedades de entidad

En esta sección se incluyen las propiedades de entidad seleccionadas en lugar de todos ellas. Solo se incluyen las propiedades que se espera sean más útiles para los desarrolladores. Algunos valores de propiedades de las entidades se pueden cambiar.

## <a name="attributes"></a>Atributos
Los atributos aparecen en dos secciones separadas: **atributos que se pueden escribir** y **atributos de solo lectura**. La finalidad de esta separación es poner el foco en los atributos que un desarrollador puede establecer al crear o actualizar una instancia de entidad. Comprender estos atributos ayuda a un desarrollador a comprender lo que pueden hacer con la entidad aparte de simplemente recuperar los valores. 

Los atributos de la sección **Atributos que se pueden escribir** devuelven un valor true *ya sea* para la propiedad **IsValidForCreate** como para **IsValidForUpdate**, (normalmente para ambas). Si alguna de estas propiedades devuelve un valor false, esto se indica.

Los **atributos de solo lectura** siempre devuelven un valor false para las propiedades **IsValidForCreate** *e* **IsValidForUpdate**.

## <a name="relationships"></a>Relaciones

La clase [EntityMetada](/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata) incluye tres propiedades para representar relaciones:

|Propiedad| Escriba  |Descripción  |
|---------|---------|---------|
|[OneToManyRelationships](/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata.onetomanyrelationships#Microsoft_Xrm_Sdk_Metadata_EntityMetadata_OneToManyRelationships)|[OneToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.onetomanyrelationshipmetadata)[]|Obtiene la matriz de relaciones de uno a varios para la entidad.|
|[EntityMetadata.ManyToOneRelationships](/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata.manytoonerelationships#Microsoft_Xrm_Sdk_Metadata_EntityMetadata_ManyToOneRelationships)|[OneToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.onetomanyrelationshipmetadata)[]|Obtiene la matriz de relaciones de varios a uno para la entidad.|
|[EntityMetadata.ManyToManyRelationships](/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata.manytomanyrelationships#Microsoft_Xrm_Sdk_Metadata_EntityMetadata_ManyToManyRelationships)|[ManyToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.manytomanyrelationshipmetadata)[]|Obtiene la matriz de relaciones de varios a varios para la entidad.|

> [!NOTE]
> Es importante tener en cuenta que mientras cada entidad muestra las relaciones que se aplican a ella, cada relación está compartida por las dos entidades. Las relaciones existen *entre* las entidades. Mientras las relaciones de uno a varios existen, las relaciones de *varios a uno* son simplemente una vista de una relación de uno a varios desde la entidad de referencia.

### <a name="one-to-many-relationships"></a>Relaciones de uno a varios
Con el fin de representar que no hay ninguna relación de *varios a uno* real con un mínimo de confusión, los detalles de cada relación solo se documentan una vez. Cada una de las relaciones de uno a varios aparece con la entidad de referencia e incluye detalles de la relación seleccionada y un vínculo a la relación de *varios a uno* correspondiente. Cada relación de *varios a uno* que se muestra solo incluye un vínculo a la correspondiente relación de uno a varios.

Para cada relación de uno a varios las propiedades siguientes se incluyen:

|Propiedad|Descripción|
|---------|---------|
|`ReferencingEntity`|Nombre lógico de la entidad relacionada.|
|`ReferencingAttribute`|El nombre lógico del atributo de la entidad relacionada que contiene una referencia a la clave principal de la entidad principal.|
|`IsHierarchical`|Si la relación representa una relación jerárquica como que se hace referencia a sí misma.|
|`IsCustomizable`|Si las propiedades de la relación se pueden cambiar.|
|`ReferencedEntityNavigationPropertyName`|El nombre de la propiedad de navegación valorada como colección de la API web para esta relación.<br />Más información:[Propiedades de navegación de la guía del desarrollador de Common Data Service](/dynamics365/customer-engagement/developer/webapi/web-api-types-operations#navigation-properties)|
|`AssociatedMenuConfiguration`|Datos usados por aplicaciones basadas en modelos para controlar si y cómo se puede acceder a los datos de la entidad relacionada en la interfaz de usuario de la entidad principal.|
|`CascadeConfiguration`|Datos que describen qué operaciones realizadas en la entidad principal se ejecutarán en cascada sobre las entidades relacionadas.<br />Más información: [Configuración en cascada](../entity-relationship-metadata.md#cascade-configuration)|


### <a name="many-to-many-relationships"></a>Relaciones de varios a varios
Cada relación de varios a varios incluye [Entity1LogicalName](/dotnet/api/microsoft.xrm.sdk.metadata.manytomanyrelationshipmetadata.entity1logicalname) y [Entity2LogicalName](/dotnet/api/microsoft.xrm.sdk.metadata.manytomanyrelationshipmetadata.entity2logicalname). Para esta documentación, los detalles de las relaciones solo se incluyen en el tema de *Entity1*. Cada relación de varios a varios donde la entidad es *Entity2*, solo incluye un vínculo a los detalles que se encuentran en el tema de *Entity1*.

Para cada relación de varios a varios las propiedades siguientes se incluyen:

|Propiedad|Descripción|
|---------|---------|
|`IntersectEntityName`|El nombre lógico de la entidad de intersección que admite esta relación de varios a varios|
|`Entity1LogicalName`|El nombre lógico de la primera entidad de la relación.|
|`Entity1IntersectAttribute`|El nombre lógico del atributo de la entidad de intersección que incluye una referencia a la clave principal de la primera entidad.|
|`Entity1NavigationPropertyName`|El nombre de la propiedad de navegación valorada como colección de la API web para esta relación.<br />Más información: [Propiedades de navegación de la guía del desarrollador de Common Data Service](/dynamics365/customer-engagement/developer/webapi/web-api-types-operations#navigation-properties)|
|`Entity1AssociatedMenuConfiguration`|Datos usados por aplicaciones basadas en modelos para controlar si y cómo se puede acceder a los primeros datos de la entidad relacionada en la interfaz de usuario de la segunda entidad.|
|`Entity2LogicalName`|El nombre lógico de la segunda entidad de la relación.|
|`Entity2IntersectAttribute`|El nombre lógico del atributo de la entidad de intersección que incluye una referencia a la clave principal de la segunda entidad.|
|`Entity2NavigationPropertyName`|Suele ser el mismo valor que el `Entity1NavigationPropertyName`|
|`Entity2AssociatedMenuConfiguration`|Datos usados por aplicaciones basadas en modelos para controlar si y cómo se puede acceder a los segundos datos de la entidad relacionada en la interfaz de usuario de la primera entidad.|
|`IsCustomizable`|Si las propiedades de la relación se pueden cambiar.|

