---
title: Operaciones de la entidad con el servicio de organización (Common Data Service)| Microsoft Docs
description: Obtenga más información sobre la clase entidad que se usa para las operaciones de datos mediante el servicio de la organización de Common Data Service
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 810d13ca894e1152438b667e409a1989623be5b8
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156064"
---
# <a name="entity-operations-using-the-organization-service"></a>Operaciones de la entidad con el servicio de la organización

Al ejecutar con datos de Common Data Service mediante el servicio de la organización usará la clase <xref:Microsoft.Xrm.Sdk.Entity> con el estilo de enlace en tiempo e ejecución o con clases de entidad generadas mediante en el estilo de enalce en tiempo de compilación. Las tipos de entidad generadas heredan de la clase <xref:Microsoft.Xrm.Sdk.Entity>, por lo que de entender la clase <xref:Microsoft.Xrm.Sdk.Entity> es importante para cualquiera de los estilos.

Este tema describirá algunas de las propiedades y métodos más utilizados de la clase <xref:Microsoft.Xrm.Sdk.Entity>.

## <a name="entitylogicalname"></a>Entity.LogicalName

Al crear una instancia de una nueva instancia <xref:Microsoft.Xrm.Sdk.Entity> con el estilo de enlace en tiempo de ejecución, debe proporcionar un valor de cadena válido para especificar el tipo de entidad de que se trate. `LogicalName` se define en los metadatos de la entidad.

Cuando se usa el estilo de enlace en tiempo de compilación, el valor se establece por el constructor de la clase generada. Por ejemplo: `var account = new Entity("account");`

En el código, si desea más adelante recuperar el valor de cadena que describe el tipo de entidad, puede usar la propiedad <xref:Microsoft.Xrm.Sdk.Entity.LogicalName>. Esto resulta útil para las muchas API que necesitan un nombre lógico de entidad como parámetro.

## <a name="entityid"></a>Identificador de la entidad

Al crear instancias de una instancia de entidad, bien con el estilo de enlace en tiempo de ejecución o en tiempo de compliación, no tiene establecido un identificador único. Si crea una entidad, no debería establecerla, sino permitir que se pueda establecer por el sistema cuando se crea (guarda).

Si está recuperando una entidad, incluirá el valor de atributo de clave principal bien si lo solicita como si no. El nombre de atributo de clave principal es diferente para cada tipo de entidad. Por lo general, el nombre lógico del atributo de clave principal es la entidad `logicalname` + `id`. Por lo tanto para una entidad cuenta es `accountid` y para una entidad contacto es `contactid`.

Puede obtener o establecer el valor de la clave principal mediante el atributo de clave principal y también puede usar la propiedad <xref:Microsoft.Xrm.Sdk.Entity.Id> para obtener acceso al valor sin tener que recordar el nombre del atributo de clave principal.

## <a name="early-bound-access-to-attributes"></a>Acceso de enlace en tiempo de compilación a los atributos

Si usa el estilo de enlace en tiempo de compilación con las clases generadas, encontrará las propiedades escritas para cada atributo en la clase. Las propiedades de los atributos usan <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName> y se puede obtener acceso a ellos directamente en la instancia de entidad.
Por ejemplo: 


```csharp
//Using the early-bound Account entity class
var account = new Account();
// set attribute values
// string primary name
account.Name = "Contoso";
// Boolean (Two option)
account.CreditOnHold = false;
// DateTime
account.LastOnHoldTime = new DateTime(2017, 1, 1);
// Double
account.Address1_Latitude = 47.642311;
account.Address1_Longitude = -122.136841;
// Int
account.NumberOfEmployees = 500;
// Money
account.Revenue = new Money(new decimal(5000000.00));
// Picklist (Option set)
account.AccountCategoryCode = new OptionSetValue(1); //Preferred customer
```

## <a name="late-bound-access-to-attributes"></a>Acceso de enlace en tiempo de ejecución a los atributos

Los datos que contiene una entidad están en la propiedad <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.Attributes> . Esta propiedad es una <xref:Microsoft.Xrm.Sdk.AttributeCollection> que proporciona un conjunto completo de métodos para agregar a nuevos atributos, comprobar si ya existe un atributo o quitar atributos.

### <a name="discover-attribute-names-and-data-types"></a>Detección de nombres de atributo y tipos de datos

En el estilo de enlace en tiempo de ejecución, debe conocer <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.LogicalName> del atributo y del tipo de datos. `LogicalName` es la versión en minúsculas de `SchemaName`. Puede detectar `LogicalName` y el tipo de los atributos de diversas formas:

- Vea la definición del atributo en las herramientas de personalización
- Para las entidades del sistema, puede consultar la [Referencia de entidad](../reference/about-entity-reference.md)
- Use una herramienta para examinar los metadatos en busca de entidades, como el Explorador de metadatos que se describe en [Exploración de los metadatos de su entorno](../browse-your-metadata.md).

Los tipos de atributo pueden ser los siguientes:

|Escriba|Descripción|
|--|--|
|<xref:Microsoft.Xrm.Sdk.EntityReference>|Un atributo de **búsqueda**. Un vínculo a otro registro.|
|<xref:Microsoft.Xrm.Sdk.BooleanManagedProperty>|Se usa solo para las entidades que pueden ser componentes de solución, como la [entidad WebResource](../reference/entities/webresource.md). Más información: [Usar propiedades administradas](../use-managed-properties.md)|
|<xref:Microsoft.Xrm.Sdk.Money>|Un atributo **Currency**.|
|<xref:Microsoft.Xrm.Sdk.OptionSetValue>|Un atributo **Option Set**. Los atributos **State** y **Status** también usan este tipo. |
|<xref:System.Boolean>|Un atributo **Option Set**.|
|<xref:System.Byte>[]|Un atributo de **Image**. Cada entidad puede tener una imagen y el atributo se llama `entityimage`. Una dirección URL para descargar la imagen que se puede encontrar en un atributo de complemento denominado `entityimage_url`. Más información [Atributos de imagen](../image-attributes.md) |
|<xref:System.DateTime>|Un atributo de **F¡fecha y hora** usa normalmente un valor UTC. Más información: [Comportamiento y formato del atributo de fecha y hora](../behavior-format-date-time-attribute.md).|
|<xref:System.Decimal>|Un atributo de **número decimal**.|
|<xref:System.Double>|Un atributo de **número de punto flotante**.|
|<xref:System.Guid>|Se usa normalmente como el identificador único para la entidad. |
|<xref:System.Int32>|Un atributo de **número entero**.|
|<xref:System.String>|Los atributos de **varias líneas de texto** y **una sola línea de texto** usan este tipo.|



Existen tres formas diferentes para interactuar con los atributos de la entidad con el estilo de enlace en tiempo de ejecución.
- Usar el indizador en la entidad
- Usar el indizador en la colección `Attributes`
- Usar los métodos de entidad proporcionados

### <a name="use-the-indexer-on-the-entity"></a>Usar el indizador en la entidad

En la mayoría de casos si se usa el estilo de enlace en tiempo de ejecución, puede interactuar con la colección mediante el indizador para obtener o establecer el valor de un atributo mediante `LogicalName` para el atributo. Por ejemplo, para establecer el atributo de nombre de una cuenta:

```csharp
//Use Entity class with entity logical name
var account = new Entity("account");
// set attribute values
// string primary name
account["name"] = "Contoso";
// Boolean (Two option)
account["creditonhold"] = false;
// DateTime
account["lastonholdtime"] = new DateTime(2017, 1, 1);
// Double
account["address1_latitude"] = 47.642311;
account["address1_longitude"] = -122.136841;
// Int
account["numberofemployees"] = 500;
// Money
account["revenue"] = new Money(new decimal(5000000.00));
// Picklist (Option set)
account["accountcategorycode"] = new OptionSetValue(1); //Preferred customer
```

### <a name="use-the-indexer-on-the-attributes-collection"></a>Usar el indizador en la colección de atributos

Al igual que en la entidad, también puede obtener acceso a un valor mediante el indizador en la colección de atributos.

```csharp
string accountName = account.Attributes["name"];
```

### <a name="use-the-entity-methods"></a>Use los métodos de entidad

También puede usar los métodos <xref:Microsoft.Xrm.Sdk.Entity> para obtener o establecer valores de atributo.

|Método|Descripción|
|--|--|
|<xref:Microsoft.Xrm.Sdk.Entity.GetAttributeValue``1(System.String)>|Usar esta opción para devolver un valor de atributo escrito|
|<xref:Microsoft.Xrm.Sdk.Entity.SetAttributeValue(System.String,System.Object)>|Usar esta opción para establecer un valor de atributo escrito|

Por ejemplo:

```csharp
account.SetAttributeValue("name", "Account Name");
var accountName = account.GetAttributeValue<string>("name");
```



## <a name="entityformattedvalues"></a>Entity.FormattedValues

Cualquier valor de atributo de entidad que se puede presentar en la interfaz de usuario y no sea una cadena tendrá un valor de formato de cadena que se puede usar para mostrar el valor de la interfaz de usuario. Por ejemplo:

- Los valores de dinero tendrán un valor de cadena con el formato de la divisa y precisión adecuados.
- Los valores de fecha tendrán el formato establecido en función de cómo está configurado el sistema
- Los valores de OptionSet mostrarán la etiqueta localizada que representa el valor entero

> [!NOTE]
> Los valores con formato sólo se aplica a las entidades se han que se recuperado. Una vez que establezca el valor, no se calculará un nuevo valor de formato hasta que se guarde la entidad y se vuelva a recuperar. El valor darle con formato se genera en el servidor.

Puede obtener acceso a los valores con formato mediante la colección <xref:Microsoft.Xrm.Sdk.Entity.FormattedValues> con un indizador o con una un método <xref:Microsoft.Xrm.Sdk.Entity.GetFormattedAttributeValue(System.String)> de la entidad.

Por ejemplo, las dos alternativas siguientes recuperan el mismo valor de formato:

```csharp
var formattedRevenueString1 = account.FormattedValues["revenue"];
var formattedRevenueString2 = account.GetFormattedAttributeValue("revenue");
```

Más información: [Obtener acceso a valores con formato](entity-operations-query-data.md#access-formatted-values).

## <a name="entityrelatedentities"></a>Entity.RelatedEntities 

Cuando crea una entidad, también puede definir un conjunto de registros de entidad que se vayan a crear en la misma operación. Más información: [Creación de entidades relacionadas en una operación](entity-operations-create.md#create-related-entities-in-one-operation)

Cuando se recupera una entidad puede usar <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> estableciendo <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest.RelatedEntitiesQuery> con una consulta para incluir las entidades relacionadas en los resultados. Más información: [Recuperación con registros relacionados](entity-operations-retrieve.md#retrieve-with-related-records)

Si incluye entidades relacionadas en los resultados, también puede actualizar los valores de estas entidades relacionadas e incluirlos al actualizar la entidad. Más información: [Actualización de entidades relacionadas en una operación](entity-operations-update-delete.md#update-related-entities-in-one-operation)

## <a name="convert-to-an-entityreference"></a>Conversión a un EntityReference

Muchas propiedades de mensaje requieren únicamente un método <xref:Microsoft.Xrm.Sdk.EntityReference>. Use el <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.ToEntityReference> para convertir una entidad a una referencia de entidad.

## <a name="convert-to-an-entity-class"></a>Conversión a una clase de entidad

Si usa el estilo de enlace en tiempo de ejecución, deberá convertir la instancia <xref:Microsoft.Xrm.Sdk.Entity> al tipo de clase de entidad generada que está usando. Esto se puede hacer normalmente con una conversión, pero también puede usar el método <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.ToEntity``1> .

```csharp
Account account1 = (Account)retrievedEntity;
Account account2 = retrievedEntity.ToEntity<Account>();
```

> [!NOTE]
> Este método no se puede usar para convertir una instancia de entidad generada a otra clase generada o a <xref:Microsoft.Xrm.Sdk.Entity>. Solo se puede usar para convertir una instancia <xref:Microsoft.Xrm.Sdk.Entity> a un de las clases generadas que heredan de ella. Si la instancia <xref:Microsoft.Xrm.Sdk.Entity> no es en realidad una instancia de la clase generada este mensaje producirá un error.

## <a name="next-steps"></a>Pasos siguientes

Estos temas aportarán más información sobre cómo trabajar con las entidades de Common Data Service.

[Tutorial: ejemplo de servicio de organización (C#)](quick-start-org-service-console-app.md)
[Consultar datos](entity-operations-query-data.md)<br />
[Crear entidades](entity-operations-create.md)<br />
[Recuperar una entidad](entity-operations-retrieve.md)<br />
[Actualizar y eliminar entidades](entity-operations-update-delete.md)<br />
[Asociar y desasociar entidades](entity-operations-associate-disassociate.md)<br />
[Generación de clases para programación de enlace en tiempo de compilación](generate-early-bound-classes.md)<br />