---
title: Tipos y operaciones de API web (Common Data Service para aplicaciones) | Microsoft Docs
description: 'Este tema describe lo que está disponible para utilizarlo a través de la API web e introducirá temas importantes y cómo puede encontrar la información que necesita usando la documentación generada desde los documentos de servicio y de metadatos y la documentación de los tipos, funciones y acciones de entidad del sistema.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: d80cfb87-d4f1-4c75-bcc8-4f54d1351e26
caps.latest.revision: 27
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-types-and-operations"></a>Tipos y operaciones de API web

Para usar la API web necesita encontrar información sobre qué hay disponible para usar. El servicio se describe a través los documentos de servicio y de metadatos a los que puede obtener acceso. Este tema introducirá conceptos importantes y describirá cómo puede encontrar la información que necesita usando la documentación generada desde los documentos de servicio y de metadatos y la documentación de los tipos, funciones y acciones de entidad del sistema.  
  
<a name="bkmk_terminology"></a>
  
## <a name="terminology"></a>Terminología 

La API web se implementa mediante el estándar OData v4 que usa un conjunto específico de términos con los que necesita estar familiarizado. *Entity Data Model (EDM)* es el modelo de datos abstracto que se usa para describir los datos expuestos por un servicio OData. La tabla siguiente es una lista de términos seleccionados definidos en [OData Versión 4.0 Parte 1: Protocol Plus Errata 02](http://docs.oasis-open.org/odata/odata/v4.0/errata02/os/complete/part1-protocol/odata-v4.0-errata02-os-part1-protocol-complete.html) que debe comprender.  
  
|Término|Definición|  
|----------|----------------|  
|*Tipos de entidad*|Tipo estructurados con nombre con una clave. Definen las propiedades y las relaciones con nombre de una entidad. Los tipos de entidad pueden obtenerse mediante herencia individual de otros tipos de entidad.|  
|*Entidades*|Instancias de tipos de entidad (por ejemplo, cuenta, oportunidad).|  
|*Conjuntos de entidad*|Colecciones con nombre de entidades (por ejemplo, cuentas es un conjunto de entidades que contiene entidades de cuentas). Una clave de entidad identifica de manera única la entidad en un conjunto de entidades|  
|*Tipos complejos*|Tipos estructurados con nombre sin clave que constan de un conjunto de propiedades. Los tipos complejos suelen utilizarse como valores de propiedad en entidades de modelo, o como parámetros o valores devueltos para operaciones.|  
|*Tipos de enumeración* o *tipos de Enum*|Tipos primitivos con nombre cuyos valores son constantes con nombre con valores enteros subyacentes.|  
|*Funciones*|Operaciones que no tienen efectos secundarios y pueden admitir creación adicional, por ejemplo, con operaciones adicionales de filtro, funciones o una acción|  
|*Acciones*|Operaciones que permiten efectos secundarios, como modificación de datos y no se pueden crear aún más para evitar comportamiento no determinista|  
  
<a name="bkmk_servicedocs"></a>
  
## <a name="service-documents"></a>Documentos de servicio

Hay dos documentos de servicio a los que puede hacer referencia para obtener más información sobre la API web.  
  
<a name="bkmk_serviceDocument"></a>

### <a name="service-document"></a>Documento de servicio

La consulta siguiente, escrita en el campo de dirección del explorador, devuelve el *documento de servicio*, una lista completa de todos los conjuntos de entidades que están disponibles para su organización. Tenga en cuenta que *[URI de la organización]* representa la dirección URL de la organización.  
  
```  
  
[Organization URI]/api/data/v9.0  
  
```  
  
 Los conjuntos de entidades se devuelven con el formato de una matriz JSON. Cada elemento de la matriz tiene tres propiedades que figuran en esta tabla.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|`name`|Este es el nombre del conjunto de entidades. Estos datos proceden de la propiedad <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `EntitySetName` para la entidad.|  
|`kind`|Para la API web únicamente se muestran conjuntos de entidades.|  
|`url`|Este valor es el mismo que la propiedad nombre y representa la parte de la ruta de recursos para recuperar los datos de la entidad.|  
  
 Esta información se puede recuperar mediante una solicitud `GET` y puede resultar útil para obtener una lista de todos los conjuntos de entidades disponibles mediante el servicio.  
  
<a name="bkmk_csdl"></a>

### <a name="csdl-metadata-document"></a>Documento de metadatos CSDL $
 
Una solicitud `GET` a la siguiente URL devolverá un documento Common Schema Definition Language (CSDL) bastante grande (más de 3,5 MB) o un *documento de metadatos* que describe los datos y las operaciones expuestos por el servicio.  
  
```http  
GET [Organization URI]/api/data/v9.0/$metadata  
```  
  
Este documento puede usarse como origen de datos para generar clases que proporcionarán objetos con establecimiento inflexible de tipos para el servicio. Pero si no está usando clases generadas, en su lugar puede revisar la documentación generada desde esta información. La [Referencia de la API web](/dynamics365/customer-engagement/web-api/about) utiliza información principalmente de este documento que se ha tomado desde un sistema con soluciones adicionales comunes instaladas.  
  
Puede obtener más información sobre este documento en [OData Version 4.0 Part 3: Common Schema Definition Language (CSDL) Plus Errata 02](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part3-csdl.html).  
  
> [!TIP]
>  Antes de leer el resto de este tema, descargue el `$metadata` para la organización y eche un vistazo a cómo se incluyen los tipos, las funciones, y las acciones descritos en el `$metadata` y la documentación de apoyo.  
>   
>  Puede ver o descargar el documento desde el explorador entrando en la dirección URL.  

<a name="bkmk_metannot"></a>

### <a name="metadata-annotations"></a>Anotaciones de metadatos

El documento de metadatos incluye varios tipos de elementos `Annotation` que proporcionan información adicional sobre los elementos de metadatos y la funcionalidad del servicio.  A partir de v9.x, estas anotaciones no se incluyen con el documento de metadatos de forma predeterminada, a menos que se solicite explícitamente. Estas anotaciones aumentan el tamaño del documento metadatos y no siempre son necesarias.  
  
 Para incluir anotaciones tiene dos opciones cuando se solicita el documento de metadatos:  
  
-   Anexar un parámetro de cadena de consulta `?annotations=true` a una dirección URL.  
  
-   Agregar el encabezado `Prefer: odata.include-annotations="*"` a la solicitud.  
  
Cada elemento `Annotation` incluye un atributo `Term` que describe el tipo de anotaciones. La definición de todas las anotaciones posibles usadas por OData v4 se encuentran en [OData vocabularios versión 4.0](http://docs.oasis-open.org/odata/odata-vocabularies/v4.0/csprd01/odata-vocabularies-v4.0-csprd01.html). La tabla siguiente proporciona algunos ejemplos que se usan en la API web.  
  
|Término|Descripción|  
|----------|-----------------|  
|`Org.OData.Core.V1.Description`|Descripción de un entitytype o de la propiedad.|  
|`Org.OData.Core.V1.Permissions`|Una lista de los permisos disponibles para una propiedad cuando los permisos están restringidos.  Normalmente aparecerá para propiedades con solo un único elemento secundario `<EnumMember>Org.OData.Core.V1.PermissionType/Read</EnumMember>` para indicar que la propiedad es de solo lectura.|  
|`Org.OData.Core.V1.Computed`|Si se calcula la propiedad. Estos son normalmente de solo lectura.|  
|`OData.Community.Keys.V1.AlternateKeys`|Contiene una colección de elementos que describen cualquier clave alternativa definida para una entidad. Más información:[Claves alternativas](#bkmk_alternateKeys)|  
|`Org.OData.Capabilities.V1.IndexableByKey`|Si un entityset admite valores clave según convenciones OData URL.|  
|`Org.OData.Capabilities.V1.SkipSupported`|Si se admite un entityset `$skip`.|  
|`Org.OData.Capabilities.V1.SearchRestrictions`|Qué tipos de restricciones en las expresiones `$search` se aplican a un entityset.|  
|`Org.OData.Capabilities.V1.CountRestrictions`|Qué tipos de restricciones en el sufijo de ruta `/$count` y en la opción del sistema de consulta $count = true.|  
|`Org.OData.Capabilities.V1.NavigationRestrictions`|Qué tipos de restricciones en explorar propiedades de acuerdo con convenciones URL de OData.|  
|`Org.OData.Capabilities.V1.ChangeTracking`|El cambio capacidades de esta entidad o servicio de seguimiento.|  
|`Org.OData.Capabilities.V1.ConformanceLevel`|El nivel de conformidad logrado por este servicio.|  
|`Org.OData.Capabilities.V1.FilterFunctions`|Una lista de funciones y operadores que se admiten en `$filter`.|  
|`Org.OData.Core.V1.DereferenceableIDs`|Si el ID de entidad son direcciones URL que buscan la entidad identificada.|  
|`Org.OData.Core.V1.ConventionalIDs`|Si ID de entidad sigue las convenciones de la dirección URL de OData.|  
|`Org.OData.Capabilities.V1.AsynchronousRequestsSupported`|Si el servicio admite la preferencia de solicitud asincrónica.|  
|`Org.OData.Capabilities.V1.BatchContinueOnErrorSupported`|Si el servicio admite la preferencia de continuar con error.  Esta configuración admite las solicitudes `$batch`.|  
|`Org.OData.Capabilities.V1.CrossJoinSupported`|Si se admiten combinaciones cruzadas de los conjuntos de entidades en este contenedor.|  
|`Org.OData.Capabilities.V1.SupportedFormats`|Los tipos de medios de formatos admitidos, incluidos los parámetros de formato.|  
  
<a name="bkmk_entityTypes"></a>

## <a name="entity-types"></a>Tipos de entidad

La <xref:Microsoft.Dynamics.CRM.EntityTypeIndex> muestra cada uno de los tipos de entidades del sistema expuestos a través de la API web que almacena datos empresariales. Un tipo de entidad es un tipo estructurado con nombre con una clave. Define las propiedades y las relaciones con nombre de una entidad. Los tipos de entidad pueden obtenerse mediante herencia individual de otros tipos de entidad. <xref:Microsoft.Dynamics.CRM.MetadataEntityTypeIndex> enumera cada uno de los tipos de entidad usados para administrar metadatos del sistema. Ambos son tipos de entidad pero la manera de trabajar con ellos es diferente. Consultar [Usar la API Web con los metadatos de Common Data Service para aplicaciones](use-web-api-metadata.md) para obtener información sobre el uso de las entidades del modelo. Cada tipo de entidad se incluye en un elemento `EntityType` en el `$metadata`. A continuación se presenta la definición del <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> de `$metadata` con las propiedades y las propiedades de navegación quitadas.  
  
```xml  
<EntityType Name="account" BaseType="mscrm.crmbaseentity">  
  <Key>  
    <PropertyRef Name="accountid" />  
  </Key>  
  <!--Properties and navigation properties removed for brevity-->  
  <Annotation Term="Org.OData.Core.V1.Description" String="Business that represents a customer or potential customer. The company that is billed in business transactions." />  
</EntityType>  
```  
  
Cada página de referencia de `EntityType` en la documentación del SDK usa información de `$metadata` o de metadatos para mostrar la siguiente información cuando está disponible.  
  
|Información|Descripción|  
|-----------------|-----------------|  
|**Descripción**|Una descripción de la entidad.<br /><br /> La información de la propiedad <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `Description` se incluye en el elemento `EntityType` usando el elemento `Annotation` con el valor del atributo `Term` de Org.OData.Core.V1.Description.|  
|**Recopilación URL**|La dirección URL para obtener acceso a la colección de cada tipo.<br /><br /> La información de la propiedad <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `EntitySetName` se incluye utilizando el elemento `$metadata` `EntityContainer`. El atributo `Name` de cada elemento `EntitySet` controla cómo se accede a los datos mediante la dirección URL.|  
|**Tipo base**|Éste es el tipo de entidad del que se hereda el tipo de entidad.<br /><br /> El atributo `BaseType` del elemento `EntityType` contiene el nombre del tipo de entidad. Este nombre se prefija con el alias del espacio de nombres de Microsoft.Dynamics.CRM: mscrm. Más información:[Herencia de tipo](web-api-types-operations.md#bkmk_typeInheritance)|  
|**Nombre para mostrar**|Esta información no se encuentra en el `$metadata`, se recupera de la propiedad <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `DisplayName`.|  
|**Clave principal**|El valor de propiedad que contiene el identificador único para referirse a una instancia de una entidad.<br /><br /> El valor de la propiedad <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `PrimaryIdAttribute` se incluye en el elemento `EntityType` `Key`. Cada entidad puede tener solo una clave principal.<br /><br /> Las claves alternativas no se muestran aquí. Más información:[Claves alternativas](web-api-types-operations.md#bkmk_alternateKeys)|  
|**Atributo principal**|Muchas entidades requieren que se configure un valor de atributo principal, por lo que esto se incluye por comodidad.<br /><br /> Esta información no se encuentra en el `$metadata`, se recupera de la propiedad <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `PrimaryNameAttribute` de metadatos.|  
|**Propiedades**|Consultar [Propiedades](web-api-types-operations.md#bkmk_properties).|  
|**Propiedades de navegación de un solo valor**|Consultar [Propiedades de navegación de un solo valor](web-api-types-operations.md#bkmk_singleValuedNavigationProperties).|  
|**Propiedades de navegación valoradas como colección**|Consultar [Propiedades de navegación valoradas como colección](web-api-types-operations.md#bkmk_collectionvaluedNavProperties).|  
|**Operaciones enlazadas al tipo de entidad**|Cuando una operación está enlazada a un tipo de entidad específico, se muestra por comodidad.|  
|**Operaciones que utilizan el tipo de entidad**|Esta lista muestra cualquier operación que pueda usar el tipo de entidad. Esto se obtiene recogiendo referencias a todas las operaciones que hagan referencia al tipo actual en los parámetros o como valor de devolución.|  
|**Tipos de entidad que se heredan del tipo de entidad.**|Esta lista incluye cualquier tipo de entidad que se hereda directamente del tipo de entidad. Para obtener más información, vea [Herencia de tipo](web-api-types-operations.md#bkmk_typeInheritance).|  
  
<a name="bkmk_changeentitysetname"></a>
 
### <a name="change-the-name-of-an-entity-set"></a>Cambiar el nombre de un conjunto de entidades
 
De manera predeterminada, el nombre del conjunto de entidades coincide con el valor de la propiedad <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `LogicalCollectionName` (<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>`LogicalCollectionName`). Si tiene una entidad personalizada a la que desea dirigirse con otro nombre de conjunto de entidades, puede actualizar el valor de propiedad <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `EntitySetName` (<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.`EntitySetName`) para usar otro nombre.  
  
<a name="bkmk_alternateKeys"></a>

### <a name="alternate-keys"></a>Claves alternativas

Aunque Common Data Service para aplicaciones permite crear claves alternativas, solo la clave principal se encontrará en las entidades predeterminadas.  
  
 Ninguna de las entidades del sistema tienen claves alternativas definidas. Si define claves alternativas para una entidad, se incluirán en el elemento `$metadata` `EntityType` como una `Annotation` como la siguiente:  
  
```  
<Annotation Term="OData.Community.Keys.V1.AlternateKeys">  
  <Collection>  
    <Record Type="OData.Community.Keys.V1.AlternateKey">  
      <PropertyValue Property="Key">  
        <Collection>  
          <Record Type="OData.Community.Keys.V1.PropertyRef">  
            <PropertyValue Property="Alias" String="key name" />  
            <PropertyValue Property="Name" PropertyPath="key name" />  
          </Record>  
        </Collection>  
      </PropertyValue>  
    </Record>  
  </Collection>  
</Annotation>  
```  
  
La información sobre claves alternativas también se puede recuperar de los metadatos mediante la propiedad de navegación valorada como colección <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `Keys` utilizando la API web o la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.`Keys` con el servicio de organización.  
  
<a name="bkmk_typeInheritance"></a>
 
### <a name="type-inheritance"></a>Herencia de tipo

La herencia permite compartir propiedades comunes y clasificar tipos de entidades en grupos. Todos los tipos de entidad de la API web se heredan de dos de los siguientes tipos de entidad. Todos los tipos de entidad de negocios se heredan del <xref href="Microsoft.Dynamics.CRM.crmbaseentity?text=crmbaseentity EntityType" /> y todas las entidades de modelo se heredan del <xref href="Microsoft.Dynamics.CRM.crmmodelbaseentity?text=crmmodelbaseentity EntityType" />.  
  
|Entidad base|Descripción|  
|-----------------|-----------------|  
|<xref href="Microsoft.Dynamics.CRM.crmbaseentity?text=crmbaseentity EntityType" />|Todas las entidades de negocios se heredan de esta entidad. No tiene propiedades. Sirve solo como entidad base abstracta.|  
|<xref href="Microsoft.Dynamics.CRM.activitypointer?text=activitypointer EntityType" />|Todas las entidades de actividad se heredan de esta entidad. Define el conjunto común de propiedades y de propiedades de navegación para las entidades de actividad.|  
|<xref href="Microsoft.Dynamics.CRM.principal?text=principal EntityType" />|El <xref href="Microsoft.Dynamics.CRM.systemuser?text=systemuser EntityType" /> y el <xref href="Microsoft.Dynamics.CRM.team?text=team EntityType" /> heredan una propiedad ownerid común de esta entidad.|  
|<xref href="Microsoft.Dynamics.CRM.crmmodelbaseentity?text=crmmodelbaseentity EntityType" />|Solo <xref href="Microsoft.Dynamics.CRM.MetadataBase?text=MetadataBase EntityType" /> se hereda directamente desde esta entidad. No tiene propiedades. Sirve solo como entidad base abstracta.|  
|<xref href="Microsoft.Dynamics.CRM.MetadataBase?text=MetadataBase EntityType" />)|Todas las entidades de metadatos se heredan de esta entidad. Proporciona las propiedades `MetadataId` y `HasChanged` para todas las entidades de metadatos.|  
|<xref href="Microsoft.Dynamics.CRM.AttributeMetadata?text=AttributeMetadata EntityType" />|Todas las entidades de modelo que representan diferentes tipos de atributos se heredan de esta entidad.|  
|<xref href="Microsoft.Dynamics.CRM.EnumAttributeMetadata?text=EnumAttributeMetadata EntityType" />|Las entidades de modelo que representan atributos que incluyen un conjunto de opciones se heredan de esta entidad.|  
|<xref href="Microsoft.Dynamics.CRM.OptionSetMetadataBase?text=OptionSetMetadataBase EntityType" />|Este tipo de entidad de modelo proporciona un conjunto común de propiedades usadas por los tipos de entidad de modelo <xref href="Microsoft.Dynamics.CRM.BooleanOptionSetMetadata?text=BooleanOptionSetMetadata EntityType" /> y <xref href="Microsoft.Dynamics.CRM.OptionSetMetadata?text=OptionSetMetadata EntityType" /> que se heredan de él.|  
|<xref href="Microsoft.Dynamics.CRM.RelationshipMetadataBase?text=RelationshipMetadataBase EntityType" />|Este tipo de entidad proporciona un conjunto común de propiedades usadas por los tipos de entidad de modelo <xref href="Microsoft.Dynamics.CRM.ManyToManyRelationshipMetadata?text=ManyToManyRelationshipMetadata EntityType" /> y <xref href="Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata?text=OneToManyRelationshipMetadata EntityType" /> que se heredan de él.|  
  
<a name="bkmk_properties"></a>
 
## <a name="properties"></a>Propiedades

Cada tipo de entidad puede tener propiedades declaradas que correspondan a atributos. En el contenido de <xref:Microsoft.Dynamics.CRM.EntityTypeIndex> y <xref:Microsoft.Dynamics.CRM.MetadataEntityTypeIndex>, las propiedades que se heredan de un tipo de entidad base se combinan en la lista de propiedades declaradas para cada tipo de entidad. La llamada a la herencia se realiza en la descripción para cada propiedad.  
  
En los elementos `$metadata` `EntityType` cada propiedad se incluye en un elemento `Property` con un valor de atributo de `Name` que corresponde a las propiedades que establecerá en código. El valor del atributo `Type` especifica el tipo de datos de la propiedad. Las propiedades de los tipos de entidad de negocios usan normalmente tipos primitivos OData.  
  
El siguiente es un ejemplo de la propiedad <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> `name` definida en el `$metadata`.  
  
```  
<Property Name="name" Type="Edm.String" Unicode="false">  
  <Annotation Term="Org.OData.Core.V1.Description" String="Type the company or business name." />  
</Property>  
```  
  
La descripción de la propiedad está disponible en un elemento `Annotation` con la propiedad del atributo `Term` de Org.OData.Core.V1.Description. Esta descripción se toma del valor de la propiedad <xref href="Microsoft.Dynamics.CRM.AttributeMetadata?text=AttributeMetadata EntityType" /> `Description`. No todas las propiedades tienen una descripción.  
  
Cada propiedad se puede calcular. Esto significa que el valor puede establecerlo el sistema. Esto se especifica en un elemento `Annotation` con el valor de atributo `Term` de Org.OData.Core.V1.Computed.  
  
Cada propiedad también pueden tener limitaciones sobre si se puede actualizar. Esto se define en un elemento `Annotation` con un valor de atributo `Term` de Org.OData.Core.V1.Permissions. El único conjunto de opciones para esto es Org.OData.Core.V1.PermissionType/Read, lo que indica que la propiedad es de solo lectura.  
  
<a name="bkmk_primitives"></a>

### <a name="primitive-types"></a>Tipos primitivos
 
OData admite una gran variedad de tipos de datos pero Common Data Service para aplicaciones no los usa todos. En la siguiente tabla se describe cómo se asignan los tipos de servicio de organización de CDS para aplicaciones a tipos primitivos OData.  
  
|Tipo de servicio de organización|Tipo de la API web|Descripción|  
|-------------------------------|------------------|-----------------|  
|BigInt|Edm.Int64|Entero de 64 bits firmado|  
|Boolean|Edm.Booleano|Lógica de valor binario|  
|CalendarRules|Propiedades de navegación de un solo valor|Propiedades de navegación de un solo valor específicas del <xref href="Microsoft.Dynamics.CRM.calendarrule?text=calendarrule EntityType" />.|  
|Cliente|Propiedades de navegación de un solo valor|El cliente de una entidad con este tipo de propiedad puede ser una propiedad de navegación de un solo valor establecida en un tipo de entidad cuenta o contacto mediante las respectivas propiedades de navegación de un solo valor. Cuando se establece una de las respectivas propiedades de la colección de un solo valor, se desactiva la otra.|  
|DateTime|Edm.DateTimeOffset|Fecha y hora con un desplazamiento de zona horaria, no hay segundos bisiestos <br />No hay ningún tipo de fecha y hora en OData.|  
|Decimal|Edm.Decimal|Valores numéricos con precisión y escala fijas|  
|Double|Edm.Double|Número de coma flotante binaryIEEE 754 binary64 (15-17 dígitos decimales)|  
|EntityName|Edm.String|Secuencia de caracteres UTF-8|  
|Imagen|Edm.Binary|Datos binarios|  
|Entero|Edm.Int32|Entero de 32 bits firmado|  
|Búsqueda|Propiedad de navegación de un solo valor|Una referencia a una entidad específica|  
|ManagedProperty|No disponible|Solo para uso interno.|  
|Memorando|Edm.String|Secuencia de caracteres UTF-8|  
|Dinero|Edm.Decimal|Valores numéricos con precisión y escala fijas|  
|Propietario|Propiedad de navegación de un solo valor|Una referencia al <xref href="Microsoft.Dynamics.CRM.principal?text=principal EntityType" />. Los tipos de entidad systemuser y equipo heredan su propiedad ownerid del tipo de entidad principal.|  
<!-- TODO:
|PartyList|Collection-valued navigation property to the `activityparty` entity type.|The activitypartyparticipationtypemask property contains a value to represent the role of the participant. See [Activity Party Types](../activityparty-entity.md#ActivityPartyTypes) for more information.|   -->
|Picklist|Edm.Int32|Signed 32-bit integer|  
|State|Edm.Int32|Signed 32-bit integer|  
|Status|Edm.Int32|Signed 32-bit integer|  
|String|Edm.String|Sequence of UTF-8 characters|  
|Uniqueidentifier|Edm.Guid|16-byte (128-bit) unique identifier|  
  
<a name="bkmk_lookupProperties"></a>
 
### <a name="lookup-properties"></a>Propiedades de búsqueda

Para la mayoría de las propiedades de navegación de un solo valor encontrará una propiedad calculada de sólo lectura que use la convención de nomenclatura siguiente: `_<name>_value` donde `<name>` coincide con el nombre de la propiedad de navegación de un solo valor. La excepción a este patrón es cuando un atributo de búsqueda de la entidad puede aceptar varios tipos de referencias de entidad. Un ejemplo común es cómo el atributo `customerid` de la entidad `incident` se puede establecer en una referencia que sea una entidad `contact` o `account`. En las <xref href="Microsoft.Dynamics.CRM.incident?text=incident EntityType" /> [Propiedades de navegación de valor único](/dynamics365/customer-engagement/web-api/incident?view=dynamics-ce-odata-9#Single-valued_navigation_properties) encontrará  `customerid_account` y `customerid_contact` como propiedades de navegación de un solo valor aparte para reflejar el cliente asociado a una oportunidad. Si establece una de estas propiedades de navegación de un solo valor, la otra se establecerá como nula porque ambas están enlazadas al atributo `customerid`. En las [<xref href="Microsoft.Dynamics.CRM.incident?text=incident EntityType" /> [Propiedades](/dynamics365/customer-engagement/web-api/incident?view=dynamics-ce-odata-9#Properties) encontrará una propiedad de búsqueda `_customerid_value` que contiene el mismo valor que está establecido para cualquiera de las propiedades de navegación de un solo valor que contenga un valor.  
  
Generalmente, debe evitar el uso de propiedades de búsqueda y usar las propiedades de navegación de un solo valor correspondientes en su lugar. Estas propiedades se han incluido porque pueden ser útiles para determinados escenarios de integración. Estas propiedades son de solo lectura y calculadas porque simplemente reflejarán los cambios aplicados mediante la correspondiente propiedad de navegación de un solo valor.  
  
Al incluir propiedades de búsqueda en una consulta, puede solicitar la inclusión de anotaciones que proporcionen más información sobre los datos que se establecen para estos atributos subyacentes que no están representados por una propiedad de navegación de un solo valor. Más información:[Recuperar datos sobre propiedades de búsqueda](query-data-web-api.md#bkmk_lookupProperty)  
  
<a name="bkmk_navprops"></a>

## <a name="navigation-properties"></a>Propiedades de navegación

En OData, las propiedades de navegación le permiten tener acceso a datos relacionados con la entidad actual. Cuando recupera una entidad puede optar por expandir las propiedades de navegación para incluir los datos relacionados. Hay dos tipos de propiedades de navegación: de un solo valor y valoradas como colección.  
  
<a name="bkmk_singleValuedNavigationProperties"></a>
 
### <a name="single-valued-navigation-properties"></a>Propiedades de navegación de un solo valor

Estas propiedades corresponden a atributos de búsqueda que admiten relaciones de varios a uno y permiten establecer una referencia a otra entidad. En el elemento `$metadata` `EntityType`, están definidos como un elemento `NavigationProperty` con en el atributo `Type` establecido como un tipo único. El siguiente es un ejemplo de la propiedad de navegación de un solo valor <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> `createdby` en el `$metadata`:  
  
```xml  
<NavigationProperty Name="createdby" Type="mscrm.systemuser" Nullable="false" Partner="lk_accountbase_createdby">  
 <ReferentialConstraint Property="_createdby_value" ReferencedProperty="systemuserid" />  
</NavigationProperty>  
```  
  
Cada propiedad de navegación que representa una propiedad de navegación de un solo valor tendrá su correspondiente propiedad de navegación valorada como colección indicada por el valor del atributo `Partner`. Cada propiedad de navegación de un solo valor también tiene un elemento `ReferentialConstraint` con el valor de atributo `Property` que representa la propiedad de búsqueda de sólo lectura calculada que puede usarse para recuperar el correspondiente valor GUID de la entidad relacionada. Más información:[Propiedades de búsqueda](web-api-types-operations.md#bkmk_lookupProperties)  
  
<a name="bkmk_collectionvaluedNavProperties"></a>

### <a name="collection-valued-navigation-properties"></a>Propiedades de navegación valoradas como colección

Estas propiedades corresponden a relaciones de uno a varios o de varios a varios. En el elemento `$metadata` `EntityType`, se definen como un elemento `NavigationProperty` con en el atributo `Type` establecido como una colección de un tipo. Lo siguiente representa la propiedad de navegación valorada como colección de <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> `Account_Tasks` que representa una relación de uno a varios:  
  
```xml  
<NavigationProperty Name="Account_Tasks" Type="Collection(mscrm.task)" Partner="regardingobjectid_account_task" />  
```  
  
Cuando la propiedad de navegación valorada como colección representa una relación de varios a varios, el nombre de la propiedad de navegación y el nombre del asociado serán iguales. Lo siguiente representa la propiedad de navegación valorada como colección de <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> `accountleads_association` que representa una relación de varios a varios:  
  
```xml  
<NavigationProperty Name="accountleads_association" Type="Collection(mscrm.lead)" Partner="accountleads_association" />  
```  
  
La diferencia entre relaciones de uno a varios y relaciones de varios a varios no es importante al usar la API web. La forma desasociar las entidades es la misma independientemente del tipo de relación. Aunque las relaciones de varios a varios siguen usando entidades de intersección en segundo plano, solo algunas entidades de intersección especiales del sistema se incluyen en la <xref:Microsoft.Dynamics.CRM.EntityTypeIndex>. Por ejemplo,<xref href="Microsoft.Dynamics.CRM.campaignactivityitem?text=campaignactivityitem EntityType" /> es técnicamente una entidad de intersección, pero se incluye porque tiene más propiedades que una entidad de intersección ordinaria.  
  
Un entidad de intersección ordinaria solo tiene las cuatro propiedades básicas requeridas para mantener la relación de varios a varios. Cuando crea una relación personalizada de varios a varios entre entidades, un entidad de intersección ordinario se creará para ayudar en la relación. Puesto que debe usar propiedades de navegación para realizar operaciones relacionadas con relaciones de varios a varios, las entidades de intersección ordinarias no se documentan pero continúan estando disponibles mediante la API web. Estos tipos de entidad de intersección son accesibles mediante un nombre establecido de entidad que use la convención de nomenclatura siguiente: *\<intersect entity logical name>*+’collection’. Por ejemplo, puede recuperar información del tipo de entidad de intersección contactleads mediante `[Organization URI]/api/data/v9.0/contactleadscollection`. Debe usar solo estas entidades de intersección ordinarias en situaciones donde desee aplicar seguimiento de cambios.  
  
<a name="bkmk_actions"></a>

## <a name="actions"></a>Acciones

Las *acciones* son operaciones que permiten efectos secundarios, como modificación de datos y no se pueden crear aún más para evitar comportamiento no determinista.  
  
 El tema <xref:Microsoft.Dynamics.CRM.ActionIndex> enumera todas las acciones del sistema disponibles. Más infomación: [Usar acciones web API](use-web-api-actions.md).  
  
<a name="bkmk_functions"></a>
 
## <a name="functions"></a>Funciones

Las *funciones* son operaciones que no tienen efectos secundarios y pueden admitir creación adicional, por ejemplo, con operaciones adicionales de filtro, funciones o una acción  
  
 Existen dos tipos de funciones definidas en la API web:  
  
-   La <xref:Microsoft.Dynamics.CRM.FunctionIndex> enumera todas las funciones del sistema disponibles.  
  
-   El tema <xref:Microsoft.Dynamics.CRM.QueryFunctionIndex> enumera las funciones que se proporcionan para usar como criterios en una consulta.  
  
 Más información:[Usar funciones web API](use-web-api-functions.md).  
  
<a name="bkmk_complexTypes"></a>
 
## <a name="complex-types"></a>Tipos complejos

Los *tipos complejos* son tipos estructurados con nombre sin clave que constan de un conjunto de propiedades. Los tipos complejos suelen utilizarse como valores de propiedad en entidades de modelo, o como parámetros o valores devueltos para operaciones.  
  
<xref:Microsoft.Dynamics.CRM.ComplexTypeIndex> incluye todos los tipos complejos del sistema. Los *tipos complejos* son tipos estructurados con nombre sin clave que constan de un conjunto de propiedades. Suelen utilizarse como valores de propiedad en entidades de modelo, o como parámetros o valores devueltos para operaciones. El siguiente es el <xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" /> del $metadata.  
  
```xml  
<ComplexType Name="WhoAmIResponse">  
  <Property Name="BusinessUnitId" Type="Edm.Guid" Nullable="false" />  
  <Property Name="UserId" Type="Edm.Guid" Nullable="false" />  
  <Property Name="OrganizationId" Type="Edm.Guid" Nullable="false" />  
</ComplexType>  
```  
  
<a name="bkmk_EnumTypes"></a>
 
## <a name="enumeration-types"></a>Tipos de enumeración
 
Los *tipos de enumeración* o *EnumTypes* son tipos primitivos con nombre cuyos valores son constantes con nombre con valores de entero subyacentes.  
  
<xref:Microsoft.Dynamics.CRM.EnumTypeIndex> incluye todos los tipos de enumeración del sistema. Los *tipos de enumeración* son tipos primitivos con nombre cuyos valores son constantes con nombre con valores enteros subyacentes. El siguiente es el <xref href="Microsoft.Dynamics.CRM.AccessRights?text=AccessRights EnumType" /> del $metadata.  
  
```  
<EnumType Name="AccessRights">  
  <Member Name="None" Value="0" />  
  <Member Name="ReadAccess" Value="1" />  
  <Member Name="WriteAccess" Value="2" />  
  <Member Name="AppendAccess" Value="4" />  
  <Member Name="AppendToAccess" Value="16" />  
  <Member Name="CreateAccess" Value="32" />  
  <Member Name="DeleteAccess" Value="65536" />  
  <Member Name="ShareAccess" Value="262144" />  
  <Member Name="AssignAccess" Value="524288" />  
</EnumType>  
```  
  
### <a name="see-also"></a>Vea también  

[Usar para la API web de Common Data Service for Apps](overview.md)<br />
[Autentique Common Data Service para aplicaciones con la API web](authenticate-web-api.md)<br />
[Realizar operaciones mediante la API web](perform-operations-web-api.md)
