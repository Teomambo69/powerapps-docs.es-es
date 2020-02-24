---
title: Consideraciones sobre API para entidades virtuales (Common Data Service) | Microsoft Docs
description: Describe consideraciones sobre API para entidades virtuales
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: d329dade-16c5-46e9-8dec-4b8efb996dea
author: mayadumesh
ms.author: jdaly
manager: amyla
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: fed9bc722c09b157dfd1f62b6ea27d2603bcc969
ms.sourcegitcommit: 303d5aed44f2bbb406cabeb6b9c8474d738d9114
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "3005091"
---
# <a name="api-considerations-of-virtual-entities"></a>Consideraciones sobre API para entidades virtuales

Hay dos grandes categorías de cambios en el sistema de metadatos que están asociadas con la introducción de entidades virtuales en Common Data Service:

- Adición de un nuevo ensamblado, espacios de nombres, clases y otros tipos para admitir el desarrollo de proveedores de datos de entidad virtuales personalizados
- Cambios a la plataforma principal, incluidas algunas propiedades adicionales para admitir la asignación de origen de datos externos y modificación de comportamientos de propiedades de entidad y atributo existentes que reflejan las limitaciones de la implementación inicial de esta característica

## <a name="dynamics-365-data-sdk-assembly"></a>Ensamblado de SDK de datos de Dynamics 365

El ensamblado de SDK de datos de Dynamics 365, `Microsoft.Xrm.Sdk.Data.dll`, contiene tipos que le ayudarán en la creación de proveedores de datos de entidad virtuales personalizados. Consta de los siguientes espacios de nombres:

|Espacio de nombres|Descripción|
|---------|---------|
|<xref:Microsoft.Xrm.Sdk.Data>|Espacio de nombres base que contiene algunos tipos comunes, como la enumeración **AllowedQueryOptions**|
|<xref:Microsoft.Xrm.Sdk.Data.CodeGen>|Contiene clases e interfaces que admiten reflexión dinámica, correspondencia de tipos y generación de código.  Utilizado principalmente por el motor del proveedor interno.|
|<xref:Microsoft.Xrm.Sdk.Data.Converters>|Un conjunto de clases para convertir a tipos XRM estándar a sus correspondientes tipos fundamentales de .NET|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions>|Un conjunto de clases de excepciones que representan errores que se pueden producir durante la resolución del valor de ejecución.  Todos se derivan de Microsoft.Xrm.Sdk.SdkExceptionBase.|
|<xref:Microsoft.Xrm.Sdk.Data.Expressions>|Clases para ayudar en la implementación de las transformaciones de consultas admitidas como FILTER, JOIN y ORDER.|
|<xref:Microsoft.Xrm.Sdk.Data.Infra>|Algunas clases diferentes que admiten el procesamiento de consultas central.|
|<xref:Microsoft.Xrm.Sdk.Data.Mappings>|Clases e interfaces que crean la asignación de tipos de metadatos de entidades virtuales a tipos externos.|
|Microsoft.Xrm.Sdk.Data.Visitors|Clases que implementan el [patrón de visitantes](https://en.wikipedia.org/wiki/Visitor_pattern) para realizar operaciones específicas en el parámetro **QueryExpression** que se pasa al proveedor de datos durante las solicitudes **RetrieveMultiple**. Proporciona compatibilidad específica tanto para consulta genérica como para procesamiento basado en LINQ. Estas clases se derivan de Microsoft.Xrm.Sdk.Query.QueryExpressionVisitorBase.|

Este ensamblado se distribuye como paquete de NuGet: [Microsoft.CrmSdk.Data](https://www.nuget.org/packages/Microsoft.CrmSdk.Data/)

## <a name="changes-to-the-core-platform"></a>Cambios en la plataforma principal

Los siguientes cambios a los tipos de referencia de Common Data Service estándar se introdujeron para poder admitir entidades virtuales.

### <a name="new-entities"></a>Nuevas entidades

Common Data Service expone orígenes y proveedores de datos de entidad virtuales como las siguientes nuevas entidades: [EntityDataProvider](../reference/entities/entitydataprovider.md) y [EntityDataSource](../reference/entities/entitydatasource.md). 

### <a name="new-metadata-properties"></a>Nuevas propiedades de metadatos

Se agregaron cuatro nuevas propiedades a la clase <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>:

|Propiedad|Descripción|
|--|--|
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.DataProviderId>|GUID que identifica el proveedor de datos de entidad virtual asociado.|
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.DataSourceId>|GUID que identifica el origen de datos de entidad virtual asociado.|
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ExternalName>|Nombre de este tipo en el origen de datos externos|
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ExternalCollectionName>|Nombre plural para este tipo, que se usa en la interfaz de usuario y para admitir el acceso a OData|

Se agregaron dos nuevas propiedades a la clase <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>:

|Propiedad|Descripción|
|--|--|
|<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.ExternalName>|Nombre del tipo en el origen de datos externos|
|<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.IsDataSourceSecret>|Indica si el campo contiene información confidencial|

La propiedad `ExternalName` también se agregó a las clases <xref:Microsoft.Xrm.Sdk.Metadata.OptionMetadata> y <xref:Microsoft.Xrm.Sdk.Metadata.OptionSetMetadata>. Estos nombres externos ayudan en la asignación de orígenes de datos externos, especificando el nombre del tipo asociado en el origen de datos externos. Estas propiedades solo se usan para entidades virtuales; para un tipo de entidad personalizada estándar o integrada, estos nombres externos deben ser `null`.


### <a name="virtual-entity-creation"></a>Creación de una entidad virtual

El método para crear mediante programación un tipo de entidad virtual difiere ligeramente de la creación de un tipo de entidad personalizada estándar en que:

- Si el proveedor de datos asociados (y, opcionalmente, el origen de datos) se conoce en el momento de la creación, entonces se debe especificar.
- Si no se conoce el proveedor de datos para este tipo, entonces, como mínimo, <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.DataProviderId> se establece en `7015A531-CC0D-4537-B5F2-C882A1EB65AD` y <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.DataSourceId> se establece en `null`. Antes de que las instancias de este tipo se usen en tiempo de ejecución, se deben asignar valores adecuados a estas propiedades.

Dos nuevas entidades, [EntityDataProvider](../reference/entities/entitydataprovider.md) y opcionalmente [EntityDataSource](../reference/entities/entitydatasource.md) se crearán al registrar un complemento y sus respectivos ID, `entitydataproviderid` y `entitydatasourceid`, representan estos GUID necesarios. (De lo contrario, los desarrolladores rara vez necesitan obtener acceso a estos tipos personalizados directamente). Tenga en cuenta que DataSource contiene la propiedad `entitydataproviderid` que debe coincidir con el tipo DataProvider correspondiente o se iniciará un excepción de tiempo de ejecución.

> [!WARNING]
> Las entidades (no virtuales) estándar deben tener los valores de sus entidades asociadas `DataProviderId` y `DataSourceId` establecidos en los valores predeterminados (`null`); de lo contrario se producirá una excepción de tiempo de ejecución.  Una vez creado, no puede convertir un tipo no virtual en un tipo virtual, ni viceversa. 

### <a name="entity-metadata-property-behavior-changes"></a>Cambios de comportamiento de las propiedades de metadatos de entidades

La tabla siguiente muestra cómo se modifica el comportamiento de las [propiedades de EntityMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata?view=dynamics-general-ce-9#properties) estándar cuando se aplican a entidades virtuales. Algunas propiedades no son válidas para entidades virtuales, mientras que otras están limitadas en el ámbito o el valor.

|**Propiedad de metadatos**|**¿Se aplica?**|**Notas**|
|---------------------|------------|---------|
|ActivityTypeMask|_no válido_|Siempre 0|
|Atributos|válido||
|AutoCreateAccessTeams|_no válido_|Siempre false|
|AutoRouteToOwnerQueue|_no válido_|Siempre false, no se admiten las colas.|
|CanBeInManyToMany|válido||
|CanBePrimaryEntityInRelationship|válido||
|CanBeRelatedEntityInRelationship|válido||
|CanChangeHierarchicalRelationship|_no válido_|Siempre false, no se admiten relaciones jerárquicas.|
|CanChangeTrackingBeEnabled|_no válido_|Siempre false, no se admiten valores de auditoría y seguimiento de cambios.|
|CanCreateAttributes|válido||
|CanCreateCharts|_no válido_|Siempre false|
|CanCreateForms|válido||
|CanCreateViews|válido||
|CanEnableSyncToExternalSearchIndex|_no válido_|Siempre false|
|CanModifyAdditionalSettings|válido||
|CanTriggerWorkflow|_no válido_|Siempre false, no se pueden desencadenar flujos de trabajo.
|ChangeTrackingEnabled|_no válido_|Siempre false|
|CollectionSchemaName|válido||
|DaysSinceRecordLastModified|_no válido_|Siempre nulo o 0|
|Descripción|válido||
|DisplayCollectionName|válido||
|DisplayName|válido||
|EnforceStateTransitions|_no válido_|No se admiten StateCode y Status.|
|EntityColor|válido||
|EntityHelpUrl|válido||
|EntityHelpUrlEnabled|válido||
|EntitySetName|válido||
|ExtensionData|_no válido_|Propiedad obsoleta|
|HasChanged|válido||
|IconLargeName|válido||
|IconMediumName|válido||
|IconSmallName|válido||
|IntroducedVersion|válido||
|IsActivity|_no válido_|Siempre false, no se admiten actividades.|
|IsActivityParty|_no válido_|Siempre false|
|IsAIRUpdated|_no válido_|Obsoleto|
|IsAuditEnabled|_no válido_|Siempre false, no se admite la auditoría.|
|IsAvailableOffline|_no válido_|Siempre false, no se admite el uso sin conexión.|
|IsBusinessProcessEnabled|_no válido_|Siempre false, no se admiten procesos de negocio.|
|IsChildEntity|_no válido_|Siempre false, todas las entidades virtuales son propiedad de la organización.|
|IsConnectionsEnabled|válido|<!-- TODO: Connection support is still TBD for Potassium -->|
|IsCustomEntity|válido||
|IsCustomizable|válido||
|IsDocumentManagementEnabled|válido||
|IsDocumentRecommendationsEnabled|_no válido_|Siempre false, no se admite esta característica nueva.|
|IsDuplicateDetectionEnabled|_no válido_|Siempre false, pero la detección de duplicados se puede realizar en el origen de datos.|
|IsEnabledForCharts|_limitado_|Solo para cláusulas de Fetch admitidas.|
|IsEnabledForTrace|válido||
|IsImportable|válido|<!--TODO: May have limitations. -->|
|IsInteractionCentricEnabled|válido||
|IsIntersect|válido||
|IsKnowledgeManagementEnabled|_no válido_|Siempre false, no se admite la integración de la administración del conocimiento.|
|IsMailMergeEnabled|válido||
|IsManaged|válido||
|IsMappable|válido||
|IsOfflineInMobileClient|_no válido_|Siempre false, los valores de la entidad virtual no se almacenan en caché para su uso sin conexión.|
|IsOneNoteIntegrationEnabled|válido||
|IsOptimisticConcurrencyEnabled|_no válido_|Siempre false, la simultaneidad se debe implementar en el origen de datos.|
|IsPrivate|válido||
|IsQuickCreateEnabled|válido||
|IsReadOnlyInMobileClient|válido||
|IsRenameable|válido||
|IsSLAEnabled|_no válido_|Siempre false|
|IsStateModelAware|_no válido_|<!-- TODO: TBD? -->|
|IsValidForAdvancedFind|válido||
|IsValidForQueue|válido||
|IsVisibleInMobile|válido||
|IsVisibleInMobileClient|válido||
|Claves|_no válido_|No se admiten claves alternativas.|
|LogicalCollectionName|válido||
|LogicalName|válido||
|ManyToManyRelationships|válido||
|ManyToOneRelationships|válido| No se admite entre dos entidades virtuales. |
|MetadataId|válido||
|MobileOfflineFilters|_no válido_|Siempre false, no se admite el uso sin conexión.|
|CódigoDeTipoDeObjeto|válido||
|OneToManyRelationships|válido||
|OwnershipType|_no válido_|Siempre **OrganizationOwned**|
|PrimaryIdAttribute|válido||
|PrimaryImageAttribute|válido||
|PrimaryNameAttribute|válido||
|Privilegios|_no válido_|<!-- TODO: TBD? -->|
|RecurrenceBaseEntityLogicalName|_no válido_||
|ReportViewName|_no válido_||
|SchemaName|válido||
|SyncToExternalSearchIndex|_no válido_||

<!-- TODO: Add links to reference properties in first column. -->


### <a name="attribute-metadata-property-behavior-changes"></a>Cambios de comportamiento de las propiedades de metadatos de atributos

La tabla siguiente explica cómo se modifica el comportamiento de las [propiedades de AttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.attributemetadata?view=dynamics-general-ce-9#properties) estándar cuando se aplican a entidades virtuales. Algunas propiedades no son válidas para entidades virtuales, mientras que otras están limitadas en el ámbito o el valor.

|**Propiedad de metadatos**|**¿Se aplica?**|**Notas**|
|---------------------|------------|---------|
|ColumnNumber|_no válido_||
|DeprecatedVersion|válido||
|Descripción|válido||
|DisplayName|válido||
|EntityLogicalName|válido||
|ExtensionData|_no válido_|<!-- TODO: TBD? -->|
|HasChanged|válido||
|InheritsFrom|válido||
|IntroducedVersion|válido||
|IsAuditEnabled|_no válido_|Siempre false, no se admite la auditoría.|
|IsCustomAttribute|válido||
|IsCustomizable|válido||
|IsFilterable|válido||
|IsGlobalFilterEnabled|válido||
|IsLogical|válido||
|IsManaged|válido||
|IsPrimaryId|válido||
|IsPrimaryName|válido||
|IsRenameable|válido||
|IsSearchable|válido||
|IsSecured|_no válido_|Siempre false, no se admite la seguridad de nivel de campo.|
|IsSortableEnabled|válido||
|IsValidForAdvancedFind|válido||
|IsValidForCreate|válido||
|IsValidForRead|válido||
|IsValidForUpdate|válido||
|LinkedAttributeId|válido||
|LogicalName|válido||
|MetadataId|válido||
|RequiredLevel|válido||
|SchemaName|válido||
|SourceType|_no válido_|Siempre 0, no se admiten valores calculados o de resumen.|

### <a name="see-also"></a>Vea también

[Introducción a las entidades virtuales](get-started-ve.md)<br />
[Proveedores de datos de entidad virtual personalizados](custom-ve-data-providers.md)<br />
[Ejemplo: Complemento de proveedor de datos de entidad virtual genérico](sample-generic-ve-plugin.md)

