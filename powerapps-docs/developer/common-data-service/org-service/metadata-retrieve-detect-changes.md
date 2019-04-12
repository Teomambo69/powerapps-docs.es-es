---
title: Recuperar metadatos y detectar cambios en metadatos (Common Data Service) | Microsoft Docs
description: Las clases del espacio de nombres Query y las clases RetrieveMetadataChangesRequest y RetrieveMetadataChangesResponse permiten crear consultas eficaces de metadatos y capturar los cambios que se producen según suceden en el tiempo.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="retrieve-and-detect-changes-to-metadata"></a>Recuperar y detectar cambios en metadatos

Las clases del espacio de nombres <xref:Microsoft.Xrm.Sdk.Metadata.Query> y las clases <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest> y <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse> permiten crear consultas eficaces de metadatos y capturar los cambios que se producen según suceden en el tiempo.  
  
 Todos los ejemplos de código a los que se hace referencia en este documento se encuentran en [Ejemplo: consultar metadatos y detectar cambios](/dynamics365/customer-engagement/developer/org-service/sample-query-metadata-detect-changes).  
  
 El artículo técnico [Consulta de metadatos con JavaScript](https://msdn.microsoft.com/library/jj919080.aspx) proporciona una biblioteca de JavaScript para usar objetos y mensajes en el código de cliente.  
  
<a name="BKMK_MetadataStrategies"></a> 
  
## <a name="strategies-for-using-metadata"></a>Estrategias para usar metadatos  

 Los metadatos permiten crear aplicaciones que se adaptan a medida que cambia el modelo de datos de Common Data Service. Los metadatos son importantes para los siguientes tipos de aplicaciones:  
  
-   Interfaz de usuario para aplicaciones cliente  
  
-   Herramientas de integración que tienen que asignar datos de Dynamics 365 a sistemas externos  
  
-   Herramientas de desarrollo  
  
 Mediante las clases del espacio de nombres <xref:Microsoft.Xrm.Sdk.Metadata.Query> puede implementar los diseños que existirán en algún punto entre una consulta ligera y una memoria caché de metadatos persistente.  
  
### <a name="lightweight-query"></a>Consulta ligera
  
 Un ejemplo de una consulta ligera es cuando tiene una interfaz de usuario de recurso web personalizado que proporciona un control de selección para mostrar las opciones actuales en un atributo de conjunto de opciones de Dynamics 365 (lista desplegable). No conviene configurar de forma rígida estas opciones porque habrá que actualizar dicho código si las opciones disponibles cambian en algún momento. En su lugar, se puede crear una consulta solo para recuperar esos valores y etiquetas de opciones desde los metadatos.  
  
 No tiene que almacenar en memoria caché estos datos porque puede usar las clases de <xref:Microsoft.Xrm.Sdk.Metadata.Query> para recuperarlos directamente de la memoria caché de aplicación de Dynamics 365.  
  
### <a name="persistent-metadata-cache"></a>Memoria caché de metadatos persistente
  
 Si tiene una aplicación que debe poder trabajar mientras está desconectada de Dynamics 365 Server o que es sensible a un ancho de banda de red limitado entre el cliente y el servidor, por ejemplo una aplicación móvil, le conviene implementar una memoria caché de metadatos persistente.  
  
 Con una caché de metadatos persistente, la aplicación tendrá que consultar todos los metadatos necesarios la primera vez que se conecta. A continuación, tendrá que guardar esos datos en la aplicación. La siguiente vez que la aplicación se conecta al servidor, se puede recuperar únicamente la diferencia desde la última consulta, lo que supondrá menor cantidad de datos que transferir; a continuación, se combinan los cambios en la memoria caché de metadatos cuando la aplicación se carga.  
  
 La frecuencia con la que debe sondear los cambios de metadatos depende de la volatilidad que se espera en los metadatos de la aplicación y cuánto tiempo la aplicación continuará ejecutándose. No hay ningún evento disponible que se pueda usar para detectar cuándo se producen cambios en los metadatos. Hay un límite del número de días que se guardan los cambios en los metadatos eliminados y una solicitud de los cambios que tienen lugar después de ese límite necesitará una reiniciación completa de la memoria caché de metadatos. Para obtener más información, consulte [Caducidad de los metadatos eliminados](/dynamics365/customer-engagement/developer/retrieve-detect-changes-metadata#BKMK_DeletedMetadataExpiration).  
  
 Cuando no hay cambios, la consulta responde con rapidez y no habrá datos que transferir. Sin embargo, si hay cambios, especialmente si hay elementos eliminados en los metadatos que tienen que eliminarse de la memoria caché, es de esperar que la solicitud requiera un tiempo adicional para finalizar. Más información: [Rendimiento cuando se recuperan metadatos eliminados](/dynamics365/customer-engagement/developer/retrieve-detect-changes-metadata#BKMK_PerformanceRetrievingDeletedMetadata)  
  
<a name="BKMK_RetrieveJusttheMetadataYouNeed"></a>
   
## <a name="retrieve-only-the-metadata-you-need"></a>Recuperar solo los metadatos que se necesitan  

 Con frecuencia los metadatos se recuperan o sincronizan cuando una aplicación se inicia y afecta al tiempo que la aplicación necesita para cargarse. Esto es especialmente así con aplicaciones móviles que recuperan metadatos por primera vez. Recuperar solo los metadatos que se necesitan es muy importante para crear una aplicación que rinda correctamente.  
  
 La clase <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression> proporciona una estructura coherente con la clase <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> que se usa para crear consultas complejas para recuperar datos de entidad. A diferencia de las clases <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllEntitiesRequest>, <xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityRequest>, <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAttributeRequest> o <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRelationshipRequest>, <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest> contiene un parámetro `Query` que acepta una instancia de <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression> que puede usar para especificar criterios específicos de los datos que se devuelven además de las propiedades que se desean. Puede usar <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest> para devolver el conjunto completo de metadatos que se obtienen mediante <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllEntitiesRequest>, o solo una etiqueta para un atributo específico.  
  
### <a name="specify-your-filter-criteria"></a>Especificar los criterios de filtro  

 La propiedad <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression>.<xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Criteria> acepta un <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataFilterExpression> que contiene una colección de objetos <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataConditionExpression> que permite definir las condiciones para filtrar las propiedades de entidad según su valor. Estas condiciones usan un <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataConditionOperator> que permite los operadores siguientes:  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataConditionOperator>.Equals  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataConditionOperator>.NotEquals  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataConditionOperator>.In  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataConditionOperator>.NotIn  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataConditionOperator>.GreaterThan  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataConditionOperator>.LessThan  
  
 <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataFilterExpression> también incluye <xref:Microsoft.Xrm.Sdk.Query.LogicalOperator> que representa si se aplica la lógica `And` o `Or` al evaluar las condiciones.  
  
 No todas las propiedades se pueden usar como criterios de filtro. Solo las propiedades que representan tipos de datos simples, enumeraciones o tipos <xref:Microsoft.Xrm.Sdk.BooleanManagedProperty> o <xref:Microsoft.Xrm.Sdk.Metadata.AttributeRequiredLevelManagedProperty> se pueden usar en <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataFilterExpression>. Cuando se especifica <xref:Microsoft.Xrm.Sdk.BooleanManagedProperty> o <xref:Microsoft.Xrm.Sdk.Metadata.AttributeRequiredLevelManagedProperty>, solo se evalúa la propiedad `Value`.  
  
 En la siguiente tabla se enumeran las propiedades <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata> que no se pueden usar en <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataFilterExpression>:  
  
|||||  
|-|-|-|-|  
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.Attributes>|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.Description>|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.DisplayCollectionName>|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.DisplayName>|  
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ManyToManyRelationships>|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ManyToOneRelationships>|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.OneToManyRelationships>|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.Privileges>|  
  
 El siguiente ejemplo muestra una <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataFilterExpression> que devolverá un conjunto de entidades que no se cruzan y son propiedad del usuario no incluidas en una lista de entidades que se excluyen:  
  
 ```csharp
   // An array SchemaName values for non-intersect, user-owned entities that should not be returned.
     String[] excludedEntities = {
"WorkflowLog",
"Template",
"CustomerOpportunityRole",
"Import",
"UserQueryVisualization",
"UserEntityInstanceData",
"ImportLog",
"RecurrenceRule",
"QuoteClose",
"UserForm",
"SharePointDocumentLocation",
"Queue",
"DuplicateRule",
"OpportunityClose",
"Workflow",
"RecurringAppointmentMaster",
"CustomerRelationship",
"Annotation",
"SharePointSite",
"ImportData",
"ImportFile",
"OrderClose",
"Contract",
"BulkOperation",
"CampaignResponse",
"Connection",
"Report",
"CampaignActivity",
"UserEntityUISettings",
"IncidentResolution",
"GoalRollupQuery",
"MailMergeTemplate",
"Campaign",
"PostFollow",
"ImportMap",
"Goal",
"AsyncOperation",
"ProcessSession",
"UserQuery",
"ActivityPointer",
"List",
"ServiceAppointment"};

     //A filter expression to limit entities returned to non-intersect, user-owned entities not found in the list of excluded entities.
     MetadataFilterExpression EntityFilter = new MetadataFilterExpression(LogicalOperator.And);
     EntityFilter.Conditions.Add(new MetadataConditionExpression("IsIntersect", MetadataConditionOperator.Equals, false));
     EntityFilter.Conditions.Add(new MetadataConditionExpression("OwnershipType", MetadataConditionOperator.Equals, OwnershipTypes.UserOwned));
     EntityFilter.Conditions.Add(new MetadataConditionExpression("SchemaName", MetadataConditionOperator.NotIn, excludedEntities));
     MetadataConditionExpression isVisibileInMobileTrue = new MetadataConditionExpression("IsVisibleInMobile", MetadataConditionOperator.Equals, true);
     EntityFilter.Conditions.Add(isVisibileInMobileTrue);
```
  
### <a name="specify-the-properties-you-want"></a>Especificar las propiedades que se desean
  
 La propiedad <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Properties> acepta una <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataPropertiesExpression>. Puede establecer <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataPropertiesExpression>.<xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataPropertiesExpression.AllProperties> en `true` si desea devolver todas las propiedades o puede proporcionar una colección de cadenas a <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataPropertiesExpression>.<xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataPropertiesExpression.PropertyNames> para definir las propiedades que desea incluir en los resultados.  
  
 Los objetos con establecimiento inflexible de tipos devueltos incluirán todas las propiedades, pero solo las que se hayan solicitado tendrán datos. El resto de las propiedades serán nulas, con las pocas excepciones siguientes: cada elemento de metadatos incluirá los valores <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.MetadataId>, `LogicalName` y <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.HasChanged> si existen para ese elemento. No tiene que especificarlos en las <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Properties> que solicita.  
  
 Si no está usando código administrado y está analizando realmente la `responseXML` devuelta de XMLHttpRequest, obtendrá elementos para cada propiedad pero solo las que se solicitan contendrán datos. El XML siguiente muestra el XML de los metadatos de entidad de contacto que se devolverán cuando `IsVisibleInMobile` sea la única propiedad solicitada.  
  
```xml  
<a:EntityMetadata>  
 <c:MetadataId>608861bc-50a4-4c5f-a02c-21fe1943e2cf</c:MetadataId>  
 <c:HasChanged i:nil="true"/>  
 <c:ActivityTypeMask i:nil="true"/>  
 <c:Attributes i:nil="true"/>  
 <c:AutoRouteToOwnerQueue i:nil="true"/>  
 <c:CanBeInManyToMany i:nil="true"/>  
 <c:CanBePrimaryEntityInRelationship i:nil="true"/>  
 <c:CanBeRelatedEntityInRelationship i:nil="true"/>  
 <c:CanCreateAttributes i:nil="true"/>  
 <c:CanCreateCharts i:nil="true"/>  
 <c:CanCreateForms i:nil="true"/>  
 <c:CanCreateViews i:nil="true"/>  
 <c:CanModifyAdditionalSettings i:nil="true"/>  
 <c:CanTriggerWorkflow i:nil="true"/>  
 <c:Description i:nil="true"/>  
 <c:DisplayCollectionName i:nil="true"/>  
 <c:DisplayName i:nil="true"/>  
 <c:IconLargeName i:nil="true"/>  
 <c:IconMediumName i:nil="true"/>  
 <c:IconSmallName i:nil="true"/>  
 <c:IsActivity i:nil="true"/>  
 <c:IsActivityParty i:nil="true"/>  
 <c:IsAuditEnabled i:nil="true"/>  
 <c:IsAvailableOffline i:nil="true"/>  
 <c:IsChildEntity i:nil="true"/>  
 <c:IsConnectionsEnabled i:nil="true"/>  
 <c:IsCustomEntity i:nil="true"/>  
 <c:IsCustomizable i:nil="true"/>  
 <c:IsDocumentManagementEnabled i:nil="true"/>  
 <c:IsDuplicateDetectionEnabled i:nil="true"/>  
 <c:IsEnabledForCharts i:nil="true"/>  
 <c:IsImportable i:nil="true"/>  
 <c:IsIntersect i:nil="true"/>  
 <c:IsMailMergeEnabled i:nil="true"/>  
 <c:IsManaged i:nil="true"/>  
 <c:IsMappable i:nil="true"/>  
 <c:IsReadingPaneEnabled i:nil="true"/>  
 <c:IsRenameable i:nil="true"/>  
 <c:IsValidForAdvancedFind i:nil="true"/>  
 <c:IsValidForQueue i:nil="true"/>  
 <c:IsVisibleInMobile>  
  <a:CanBeChanged>false</a:CanBeChanged>  
  <a:ManagedPropertyLogicalName>canmodifymobilevisibility</a:ManagedPropertyLogicalName>  
  <a:Value>false</a:Value>  
 </c:IsVisibleInMobile>  
 <c:LogicalName>contact</c:LogicalName>  
 <c:ManyToManyRelationships i:nil="true"/>  
 <c:ManyToOneRelationships i:nil="true"/>  
 <c:ObjectTypeCode i:nil="true"/>  
 <c:OneToManyRelationships i:nil="true"/>  
 <c:OwnershipType i:nil="true"/>  
 <c:PrimaryIdAttribute i:nil="true"/>  
 <c:PrimaryNameAttribute i:nil="true"/>  
 <c:Privileges i:nil="true"/>  
 <c:RecurrenceBaseEntityLogicalName i:nil="true"/>  
 <c:ReportViewName i:nil="true"/>  
 <c:SchemaName i:nil="true"/>  
</a:EntityMetadata>  
  
```  
  
 En una versión futura se logrará más eficacia no devolviendo elementos con valores null para propiedades que no se solicitaron. Si escribe código para analizar este XML, debe contar con que el XML devuelto para la misma consulta se podría reducir al XML siguiente únicamente.  
  
```xml  
<a:EntityMetadata>  
 <c:MetadataId>608861bc-50a4-4c5f-a02c-21fe1943e2cf</c:MetadataId>  
 <c:IsVisibleInMobile>  
  <a:CanBeChanged>false</a:CanBeChanged>  
  <a:ManagedPropertyLogicalName>canmodifymobilevisibility</a:ManagedPropertyLogicalName>  
  <a:Value>false</a:Value>  
 </c:IsVisibleInMobile>  
 <c:LogicalName>contact</c:LogicalName>  
</a:EntityMetadata>  
```  
  
 Los metadatos se devuelven en una estructura jerárquica igual que cuando se usa <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllEntitiesRequest>. Para obtener acceso a un atributo o relación específicos, debe crear una consulta que devuelva la entidad de la que forman parte. Si desea recuperar datos sobre un atributo específico, debe incluir la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.Attributes> en su <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression>.<xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Properties>. Para que las relaciones entre entidades se devuelvan, debe incluir una o varias de las siguientes propiedades <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>: <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ManyToManyRelationships>, <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ManyToOneRelationships> o <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.OneToManyRelationships>.  
  
 El siguiente ejemplo devolverá la propiedad `Attributes` para las entidades solicitadas:  
  
```csharp
//A properties expression to limit the properties to be included with entities
MetadataPropertiesExpression EntityProperties = new MetadataPropertiesExpression()
{
 AllProperties = false
};
EntityProperties.PropertyNames.AddRange(new string[] { "Attributes" });
```

### <a name="retrieve-attribute-metadata"></a>Recuperar metadatos de atributo 
 
 La propiedad <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression>.<xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression.AttributeQuery> acepta un <xref:Microsoft.Xrm.Sdk.Metadata.Query.AttributeQueryExpression> que define <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Criteria> y <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Properties> para que los atributos se devuelvan para las entidades que coincidan con <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression><xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Criteria> y <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Properties>.  
  
 En la siguiente tabla se enumeran las propiedades <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> que no se pueden usar en <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataFilterExpression>  
  
|||  
|-|-|  
|<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.Description>|<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.DisplayName>|  
|<xref:Microsoft.Xrm.Sdk.Metadata.EnumAttributeMetadata.OptionSet>|<xref:Microsoft.Xrm.Sdk.Metadata.LookupAttributeMetadata.Targets>|  
  
 En el siguiente ejemplo se limitarán los atributos devueltos a los que tengan `OptionSet` y se devolverán únicamente las propiedades <xref:Microsoft.Xrm.Sdk.Metadata.EnumAttributeMetadata.OptionSet> y <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.AttributeType> para esos atributos:  
  
```csharp
//A condition expresson to return optionset attributes
MetadataConditionExpression[] optionsetAttributeTypes = new MetadataConditionExpression[] { 
new MetadataConditionExpression("AttributeType", MetadataConditionOperator.Equals, AttributeTypeCode.Picklist),
new MetadataConditionExpression("AttributeType", MetadataConditionOperator.Equals, AttributeTypeCode.State),
new MetadataConditionExpression("AttributeType", MetadataConditionOperator.Equals, AttributeTypeCode.Status),
new MetadataConditionExpression("AttributeType", MetadataConditionOperator.Equals, AttributeTypeCode.Boolean)
};

//A filter expression to apply the optionsetAttributeTypes condition expression
MetadataFilterExpression AttributeFilter = new MetadataFilterExpression(LogicalOperator.Or);
AttributeFilter.Conditions.AddRange(optionsetAttributeTypes);

//A Properties expression to limit the properties to be included with attributes
MetadataPropertiesExpression AttributeProperties = new MetadataPropertiesExpression() { AllProperties = false };
AttributeProperties.PropertyNames.Add("OptionSet");
AttributeProperties.PropertyNames.Add("AttributeType");
```
  
### <a name="retrieve-relationship-metadata"></a>Recuperar metadatos de relaciones
  
 La propiedad <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression>.<xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression.RelationshipQuery> acepta un <xref:Microsoft.Xrm.Sdk.Metadata.Query.RelationshipQueryExpression> para especificar la relación entre entidades <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Criteria> y <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Properties> que desea para las entidades que coinciden con <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression><xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Criteria> y <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Properties>.  
  
 Use la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.RelationshipMetadataBase.RelationshipType> en sus criterios para especificar si desea devolver relaciones ManyToMany o OneToMany.  
  
 En la siguiente tabla se enumeran las propiedades de relaciones que no se pueden usar en MetadataFilterExpression:  
  
||  
|-|  
|<xref:Microsoft.Xrm.Sdk.Metadata.OneToManyRelationshipMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.OneToManyRelationshipMetadata.AssociatedMenuConfiguration>|  
|<xref:Microsoft.Xrm.Sdk.Metadata.OneToManyRelationshipMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.OneToManyRelationshipMetadata.CascadeConfiguration>|  
|<xref:Microsoft.Xrm.Sdk.Metadata.ManyToManyRelationshipMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.ManyToManyRelationshipMetadata.Entity1AssociatedMenuConfiguration>|  
|<xref:Microsoft.Xrm.Sdk.Metadata.ManyToManyRelationshipMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.ManyToManyRelationshipMetadata.Entity2AssociatedMenuConfiguration>|  
  
### <a name="retrieve-labels"></a>Recuperar etiquetas
  
 Finalmente, la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression>.<xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression.LabelQuery> acepta un <xref:Microsoft.Xrm.Sdk.Metadata.Query.LabelQueryExpression> que le permite especificar un valor entero o varios valores enteros `LCID` para determinar qué etiquetas localizadas devolver. Los valores de identificadores de configuración regional válidos pueden encontrarse en el [gráfico de identificadores de configuración regional (LCID)](http://go.microsoft.com/fwlink/?LinkId=122128). Si una organización tiene muchos paquetes de idioma instalados, se devolverán las etiquetas para todos los idiomas a menos que se especifique <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression.LabelQuery>.  
  
 En el siguiente ejemplo se define <xref:Microsoft.Xrm.Sdk.Metadata.Query.LabelQueryExpression> que limita las etiquetas a las que representan el idioma preferido de los usuarios únicamente.  
  
```csharp

private Guid _userId;
private int _languageCode;
```

```csharp

_userId = ((WhoAmIResponse)_service.Execute(new WhoAmIRequest())).UserId;
_languageCode = RetrieveUserUILanguageCode(_userId);
```

```csharp

protected int RetrieveUserUILanguageCode(Guid userId)
{
 QueryExpression userSettingsQuery = new QueryExpression("usersettings");
 userSettingsQuery.ColumnSet.AddColumns("uilanguageid", "systemuserid");
 userSettingsQuery.Criteria.AddCondition("systemuserid", ConditionOperator.Equal, userId);
 EntityCollection userSettings = _service.RetrieveMultiple(userSettingsQuery);
 if (userSettings.Entities.Count > 0)
 {
  return (int)userSettings.Entities[0]["uilanguageid"];
 }
 return 0;
}
```

```csharp

//A label query expression to limit the labels returned to only those for the user's preferred language
LabelQueryExpression labelQuery = new LabelQueryExpression();
labelQuery.FilterLanguages.Add(_languageCode);
```
  
<a name="BKMK_RetrievingNeworChangedMetadata"></a> 
  
## <a name="retrieve-new-or-changed-metadata"></a>Recuperar metadatos nuevos o modificados

 La clase <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse> devuelve <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadataCollection> con establecimiento inflexible de tipos que contiene los datos solicitados. La clase <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse> también proporciona un valor <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse.ServerVersionStamp> que se puede pasar a la propiedad <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest>.<xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.ClientVersionStamp> en solicitudes posteriores. Cuando un valor está incluido para la propiedad <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.ClientVersionStamp>, solo se devolverán los datos coincidentes con <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression> y que han cambiado desde que se recuperó `ClientVersionStamp`. La única excepción a esto es cuando su <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression>.<xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Properties> incluye <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.Privileges>. Los privilegios se devuelven siempre con independencia de <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.ClientVersionStamp>. De esta manera, la aplicación puede determinar si se han realizado cambios importantes que interesen desde la última vez que se consultaron los metadatos. Después, puede combinar los metadatos nuevos o modificados en la memoria caché de metadatos persistente de manera que la aplicación evite problemas de rendimiento descargando metadatos que no se necesitan.  
  
 La propiedad <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.HasChanged> proporciona una forma de detectar qué elementos secundarios de un elemento de metadatos han cambiado. Dado que todos los metadatos se devuelven como parte del elemento de metadatos contenedor, cuando la etiqueta de <xref:Microsoft.Xrm.Sdk.Metadata.OptionMetadata> cambia, se devuelven las propiedades <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>, <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> y <xref:Microsoft.Xrm.Sdk.Metadata.OptionSetMetadata> contenedoras. Sin embargo, la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.HasChanged> será falsa para los elementos de metadatos contenedores. Solo la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.OptionMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.HasChanged> se establecerá en true.  
  
 En el siguiente ejemplo se realiza una solicitud inicial definiendo <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression> y ejecutando una solicitud con <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.ClientVersionStamp> establecido en null.  
  
```csharp
//An entity query expression to combine the filter expressions and property expressions for the query.
EntityQueryExpression entityQueryExpression = new EntityQueryExpression()
{

 Criteria = EntityFilter,
 Properties = EntityProperties,
 AttributeQuery = new AttributeQueryExpression()
 {
  Criteria = AttributeFilter,
  Properties = AttributeProperties
 },
 LabelQuery = labelQuery

};

//Retrieve the metadata for the query without a ClientVersionStamp
RetrieveMetadataChangesResponse initialRequest = getMetadataChanges(entityQueryExpression, null, DeletedMetadataFilters.OptionSet);

```

```csharp
protected RetrieveMetadataChangesResponse getMetadataChanges(
 EntityQueryExpression entityQueryExpression,
 String clientVersionStamp,
 DeletedMetadataFilters deletedMetadataFilter)
{
 RetrieveMetadataChangesRequest retrieveMetadataChangesRequest = new RetrieveMetadataChangesRequest()
 {
  Query = entityQueryExpression,
  ClientVersionStamp = clientVersionStamp,
  DeletedMetadataFilters = deletedMetadataFilter
 };

 return (RetrieveMetadataChangesResponse)_service.Execute(retrieveMetadataChangesRequest);

}
```

<a name="BKMK_RetrieveInformationaboutDeletedMetadata"></a>
   
## <a name="retrieve-information-about-deleted-metadata"></a>Recuperar información sobre metadatos eliminados  

 La propiedad <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse>.<xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse.DeletedMetadata> devolverá un <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataCollection> cuando las propiedades <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.ClientVersionStamp> y <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.DeletedMetadataFilters> se establezcan en <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest>. <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataCollection> contiene los valores <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.MetadataId> de cualquier objeto <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>, <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> o <xref:Microsoft.Xrm.Sdk.Metadata.RelationshipMetadataBase> que se haya eliminado del sistema en un límite de tiempo. Para obtener más información, consulte [Caducidad de los metadatos eliminados](/dynamics365/customer-engagement/developer/retrieve-detect-changes-metadata#BKMK_DeletedMetadataExpiration).  
  
 Use la enumeración <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataFilters> con <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest>.<xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.DeletedMetadataFilters> para limitar la información a aquellos tipos de metadatos que le interesan. La enumeración <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataFilters> proporciona las siguientes opciones:  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataFilters>.Entity (predeterminado)  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataFilters>.Attribute  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataFilters>.Relationship  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataFilters>.Label  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataFilters>.OptionSet  
  
 También usará la enumeración <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataFilters> como clave para <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse>.<xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse.DeletedMetadata> para filtrar los valores `GUID` encontrados en la propiedad <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse>.<xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse.DeletedMetadata> .  
  
 Cuando diseñe una memoria caché de metadatos, le conviene usar <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.MetadataId> para cada elemento de modo que pueda identificar los elementos eliminados de los metadatos y quitarlos.  
  
<a name="BKMK_DeletedMetadataExpiration"></a>
   
### <a name="deleted-metadata-expiration"></a>Caducidad de los metadatos eliminados  

 Todo elemento de metadatos que se elimina recibe un seguimiento durante un período de tiempo limitado especificado por el valor `Organization.ExpireSubscriptionsInDays`. De manera predeterminada, el valor es 90 días. Si el valor <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest>.<xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.ClientVersionStamp> indica que la última consulta de metadatos se realizó antes de la fecha de vencimiento, el servicio producirá un error `ExpiredVersionStamp` (0x80044352). Cuando se recuperan datos para actualizar una memoria caché de metadatos existente, debe intentar capturar este error y estar preparado para reiniciar la memoria caché con los resultados de una segunda solicitud pasada sin <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.ClientVersionStamp>. El error `ExpiredVersionStamp` también se genera cuando los cambios en el servidor, como cambios en el valor `ExpireSubscriptionsInDays`, afectan exactamente al seguimiento de los metadatos eliminados.  
  
 En el siguiente ejemplo se pasa <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.ClientVersionStamp> y recoge el `ExpiredVersionStamp`. Si se captura el error, la memoria caché se reinicializa pasando una nueva solicitud con <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.ClientVersionStamp> establecido en `null`.  
  
```csharp

protected String updateOptionLabelList(EntityQueryExpression entityQueryExpression, String clientVersionStamp)
{
 //Retrieve metadata changes and add them to the cache
 RetrieveMetadataChangesResponse updateResponse;
 try
 {
  updateResponse = getMetadataChanges(entityQueryExpression, clientVersionStamp, DeletedMetadataFilters.OptionSet);
  addOptionLabelsToCache(updateResponse.EntityMetadata, true);
  removeOptionLabelsFromCache(updateResponse.DeletedMetadata, true);

 }
 catch (FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault> ex)
 {
  // Check for ErrorCodes.ExpiredVersionStamp (0x80044352)
  // Will occur when the timestamp exceeds the Organization.ExpireSubscriptionsInDays value, which is 90 by default.
  if (ex.Detail.ErrorCode == unchecked((int)0x80044352))
  {
   //reinitialize cache
   _optionLabelList.Clear();

   updateResponse = getMetadataChanges(entityQueryExpression, null, DeletedMetadataFilters.OptionSet);
   //Add them to the cache and display the changes
   addOptionLabelsToCache(updateResponse.EntityMetadata, true);

  }
  else
  {
   throw ex;
  }

 }
 return updateResponse.ServerVersionStamp;
}
```

  
<a name="BKMK_PerformanceRetrievingDeletedMetadata"></a>
   
### <a name="performance-when-retrieving-deleted-metadata"></a>Rendimiento cuando se recuperan metadatos eliminados 
 
 Cuando se elimina un elemento de metadatos, se guarda en la base de datos y no en la memoria caché de metadatos de Dynamics 365. Aunque los metadatos eliminados se limiten únicamente a <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.MetadataId> y al tipo del elemento de metadatos, el acceso a la base de datos es una operación que requerirá más recursos del servidor que una simple consulta de los cambios.  
  
### <a name="see-also"></a>Vea también  
 [Escribir aplicaciones y extensiones de servidor](/dynamics365/customer-engagement/developer/extend-dynamics-365-server)   
 [Uso sin conexión de servicios de Dynamics 365](/dynamics365/customer-engagement/developer/org-service/offline-use-services)   
 [Ejemplo: consultar metadatos y detectar cambios](/dynamics365/customer-engagement/developer/org-service/sample-query-metadata-detect-changes)   
 [Ampliar el modelo de metadatos de Dynamics 365](/dynamics365/customer-engagement/developer/org-service/use-organization-service-metadata)   
 [Personalizar metadatos de entidad](/dynamics365/customer-engagement/developer/customize-entity-metadata)   
 [Personalizar metadatos de atributos de entidad](/dynamics365/customer-engagement/developer/customize-entity-attribute-metadata)   
 [Personalizar metadatos de relación de entidad](/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)   
 [Consulta de metadatos con JavaScript](https://msdn.microsoft.com/library/jj919080.aspx)