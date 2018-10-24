---
title: Metadatos de atributo | Microsoft Docs
description: Obtenga información sobre el uso de metadatos de atributo en Common Data Service for Apps.
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
ms.openlocfilehash: f6fcf3ba1e8e9773df65ac566a9d5c798f4d13a9
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42859170"
---
# <a name="attribute-metadata"></a>Metadatos de atributo

Las entidades incluyen una colección de atributos que representan los datos que se pueden incluir en cada registro. Los desarrolladores deben comprender los distintos tipos de atributos y cómo trabajar con ellos. 

Más información: [Introducción a los atributos de entidad (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/introduction-entity-attributes)

## <a name="attribute-names"></a>Nombres de atributo

Como las entidades, cada atributo tiene un nombre único que se define cuando se crea. Este nombre se presenta de varias maneras:


|Nombre |Descripción  |
|---------|---------|
|`SchemaName`|Normalmente, una versión del nombre lógico con mayúsculas y minúsculas como en Pascal. Por ejemplo, `AccountNumber`.|
|`LogicalName`|Nombre en minúsculas. Por ejemplo, `accountnumber`.|

Cuando se crea un atributo personalizado, el nombre que se elija se anexará al principio con el valor de prefijo de personalización del editor de soluciones asociado a la solución en la que se creó el atributo.

No se pueden cambiar los nombres de un atributo después de crearlo.

Cada atributo también tiene dos propiedades que pueden mostrar valores traducidos. Estos son los valores que se usan para hacer referencia a los atributos de una aplicación.

|Nombre |Descripción  |
|---------|---------|
|`DisplayName`|Normalmente, el mismo que el nombre de esquema, pero puede incluir espacios. Por ejemplo, **Número de cuenta**.|
|`Description`|Una frase corta que describe el atributo o proporciona instrucciones al usuario. Por ejemplo, *Escriba un número de identificador o código de la cuenta para buscar e identificar rápidamente la cuenta en las vistas del sistema.*<br />En las aplicaciones controladas por modelos, esta información se mostrará cuando los usuarios mantengan el puntero sobre el campo para este atributo en un formulario.|


Estos son los valores localizables que se usan para hacer referencia a los atributos de una aplicación. Estos valores se pueden cambiar en cualquier momento. Para agregar o editar valores traducidos vea [Traducir texto de entidades y campos personalizados a otros idiomas (Guía de personalización de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/customize/export-customized-entity-field-text-translation).

## <a name="attribute-types"></a>Tipos de atributo

La propiedad `AttributeTypeName` describe el tipo de un atributo. Esta propiedad contiene un valor de tipo `AttributeTypeDisplayName` que proporciona una etiqueta para cada uno de los distintos tipos de atributos que existen. 

> [!NOTE]
> No se debe confundir con la propiedad `AttributeType`. Los valores de esta propiedad anterior se alinean principalmente con `AttributeTypeName` salvo que muestre los atributos `ImageType` como `Virtual`. Se debe hacer referencia a la propiedad `AttributeTypeName` en lugar de la propiedad `AttributeType`.

En la tabla siguiente:

- Estos tipos se agrupan por categoría para la comparación.
- Para cada valor `AttributeTypeDisplayName`, se incluye la clase derivada [AttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.attributemetadata) de ensamblado .NET correspondiente cuando sea posible. No hay una relación 1:1 entre estos tipos y la etiqueta `AttributeTypeDisplayName`.
- Los tipos de atributo que se pueden crear como atributos personalizados incluyen la etiqueta correspondiente que se muestra en la interfaz de usuario.


|Categoría|Tipo AttributeTypeDisplayName/<br />AttributeMetadata|Puede crear/<br />Etiquetas|Descripción  |
|---------|---------|---------|---------|
|Categorización|`BooleanType`<br />[BooleanAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.booleanattributemetadata)|Sí<br />**Dos opciones**|Contiene el valor de opción seleccionado de dos opciones que suelen indicar un valor true o false.<br />Más información: [Conjuntos de opciones](#option-sets)|
|Categorización|`EntityNameType`<br />[EntityNameAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.entitynameattributemetadata)|No|Contiene un valor de opción que corresponde a una entidad en el sistema. Solo para uso interno.|
|Categorización|`MultiSelectPicklistType`<br />[MultiSelectPicklistAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.multiselectpicklistattributemetadata)|Sí<br />**Conjunto de opciones de selección múltiple**|Contiene varios valores de opción seleccionados, donde se pueden seleccionar varias opciones.<br />Más información: <br />[Conjuntos de opciones](#option-sets)<br />[Atributos de lista desplegable de selección múltiple (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/multi-select-picklist)|
|Categorización|`PicklistType`<br />[PicklistAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.picklistattributemetadata)|Sí<br />**Conjunto de opciones**|Contiene el valor de opción seleccionado donde se puede seleccionar una opción.<br />Más información: [Conjuntos de opciones](#option-sets)|
|Categorización|`StateType`<br />[StateAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.stateattributemetadata)|No|Contiene el valor de opción que describe el estado de un registro de entidad.<br />Más información: [Conjuntos de opciones](#option-sets)|
|Categorización|`StatusType`<br />[StatusAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.statusattributemetadata)|No|Contiene el valor de opción que describe la razón del estado de un registro de entidad.<br />Más información: [Conjuntos de opciones](#option-sets)|
|Colección|`CalendarRulesType`|No|Contiene una colección de registros de entidad `CalendarRules`.<br />No hay ningún atributo que use este tipo. Al generar un proxy, la herramienta de generación de código creará dos atributos simulados que no están presentes en los metadatos. Estos atributos representan una vista de los registros de reglas de calendario asociados en una relación de uno a varios con el registro de entidad.|
|Colección|`PartyListType`|No|Contiene una colección de registros de entidad `ActivityParty`.<br />Más información: [Entidad ActivityParty](#activityparty-entity)|
|Fecha y hora|`DateTimeType`<br />[DateTimeAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.datetimeattributemetadata)|Sí<br />**Fecha y hora**|Contiene un valor de fecha y hora.<br />Todos los atributos de fecha y hora admiten valores tan antiguos como las 12:00 a. m. del 1/1/1753.|
|Imagen|`ImageType`<br />[ImageAttributeMetadata]()|Sí<br />**Imagen**|Contiene datos para admitir la recuperación de datos de imagen para un registro de entidad.<br />Más información: [Imágenes de entidad](entity-metadata.md#entity-images)|
|Propiedad administrada|`ManagedPropertyType`<br />[ManagedPropertyAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.imageattributemetadata)|No|Contiene datos que describen si se puede personalizar el componente de solución almacenado en el registro de entidad cuando se incluye en una solución administrada.<br />Más información: [Propiedades administradas](introduction-solutions.md#managed-properties)|
|Cantidad|`BigIntType`<br />[BigIntAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.bigintattributemetadata)|No|Contiene un valor `BigInt`. Solo para uso interno.|
|Cantidad|`DecimalType`<br />[DecimalAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.decimalattributemetadata)|Sí<br />**Número decimal**|Contiene un valor `Decimal`. La propiedad `Precision` establece el nivel de precisión.|
|Cantidad|`DoubleType`<br />[DoubleAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.doubleattributemetadata)|Sí<br />**Número de punto flotante**|Contiene un valor `Double`. La propiedad `Precision` establece el nivel de precisión.|
|Cantidad|`IntegerType`<br />[IntegerAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.integerattributemetadata)|Sí<br />**Número entero**|Contiene un valor `Int`.|
|Cantidad|`MoneyType`<br />[MoneyAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.moneyattributemetadata)|Sí<br />**Moneda**|Contiene un valor `Decimal`. La propiedad `PrecisionSource` determina dónde se establece el nivel de precisión.<br />0: la propiedad `Precision`<br />1: el atributo `Organization.PricingDecimalPrecision`<br />2: el `TransactionCurrency.CurrencyPrecision` atributo en el registro de entidad|
|Referencia|`CustomerType`<br />[LookupAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.lookupattributemetadata)|Sí<br />**Customer**|Contiene una referencia a una cuenta o a un registro de entidad Contact.|
|Referencia|`LookupType`<br />[LookupAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.lookupattributemetadata)|Sí<br />**Búsqueda**|Contiene una referencia a un registro de entidad. Los nombres lógicos de los registros válidos se almacenan normalmente en la propiedad `Targets` del atributo.|
|Referencia|`OwnerType`<br />[LookupAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.lookupattributemetadata)|No|Contiene una referencia a un registro de entidad de usuario o equipo.|
|Cadena|`MemoType`<br />[MemoAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.memoattributemetadata)|Sí<br />**Varias líneas de texto**|Contiene un valor de cadena diseñado para mostrarse en un cuadro de texto de varias líneas.|
|Cadena|`StringType`<br />[StringAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.stringattributemetadata)|Sí<br />**Una línea de texto**|Contiene un valor de cadena diseñado para mostrarse en un cuadro de texto de una línea.|
|Identificador único|`UniqueidentifierType`<br />[UniqueIdentifierAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.uniqueidentifierattributemetadata)|No|Contiene un valor de identificador único GUID.|
|Virtual|`VirtualType`|No|Estos atributos no se pueden usar en el código y por lo general se pueden ignorar.|


## <a name="supported-operations-and-form-usage-for-attributes"></a>Operaciones admitidas y uso de formularios para los atributos

Cada atributo incluye propiedades booleanas que describen los tipos de operaciones en las que puede participar y cómo puede estar en un formulario.

|Propiedad|Descripción|
|--|--|
|`IsRequiredForForm`|Si el atributo se debe incluir como un campo en un formulario.|
|`IsValidForCreate`|Si el valor del atributo se puede establecer en una operación de creación.|
|`IsValidForForm`|Si el atributo se puede incluir como un campo en un formulario.|
|`IsValidForRead`|Si se puede recuperar el valor del atributo.|
|`IsValidForUpdate`|Si el valor del atributo se puede establecer en una operación de actualización.|

Si se intenta establecer un valor en una operación de creación o actualización para un atributo que no es válido para esa operación, el valor se omitirá.
Si se intenta recuperar un atributo que no es válido para la lectura, se devolverá un valor NULL.


## <a name="attribute-requirement-level"></a>Nivel de requisitos de atributo

La propiedad `RequiredLevel` es una propiedad administrada booleana que describe si un valor de atributo es obligatorio.

En esta propiedad se pueden establecer los valores siguientes:

|Nombre|Valor|Etiqueta de la interfaz de usuario|Descripción|
|--|--|--|--|
|`None`|0|**Opcional**|No se especificó ningún requisito.|
|`SystemRequired`|1|**Requerido por el sistema**|El atributo debe tener un valor.|
|`ApplicationRequired`|2|**Requerido por la empresa**|La empresa requiere que el atributo tenga un valor.|
|`Recommended`|3|**Recomendado por la empresa**|Se recomienda que el atributo tenga un valor.|

Common Data Service for Apps solo aplica la opción `SystemRequired` a los atributos creados por el sistema. Los atributos personalizados no se pueden establecer para que usen la opción `SystemRequired`. 

Las aplicaciones controladas por modelos aplicarán la opción `ApplicationRequired` y usarán otra presentación para la opción `Recommended`. Los creadores de clientes personalizados pueden usar esta información para requerir opciones de validación o presentación similares.

Dado que se trata de una propiedad administrada, como editor de una solución administrada puede decidir si los consumidores de la solución pueden cambiar esta configuración en los atributos de la solución.

Más información: [Propiedades administradas](introduction-solutions.md#managed-properties)


## <a name="rollup-and-calculated-attributes"></a>Atributos consolidados y calculados

Los atributos calculados y consolidados liberan al usuario de tener que realizar cálculos de forma manual y se centre en su trabajo. Los administradores del sistema pueden definir un campo para que contenga el valor de muchos cálculos comunes sin tener que trabajar con un desarrollador. Los desarrolladores también pueden aprovechar las funciones de la plataforma para realizar estos cálculos en lugar de hacerlo dentro de su propio código.

Más información: 
- [Definir campos consolidados que agregan valores (Guía de personalización de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/customize/define-rollup-fields)
- [Definir campos calculados (Guía de personalización de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/customize/define-calculated-fields)
- [Atributos calculados y consolidados (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/calculated-rollup-attributes)

## <a name="attribute-format"></a>Formato del atributo

Los valores de formato para los atributos controlan cómo se muestran en las aplicaciones controladas por modelos. El desarrollador de aplicaciones personalizadas puede usar esta información para crear una experiencia similar.

### <a name="integer-formats"></a>Formatos enteros

Use la propiedad `Format` con atributos de enteros para mostrar las experiencias de usuario alternativas para este tipo.

|Opción|Descripción|
|--|--|
|`None`|Muestra un cuadro de texto para editar un valor numérico|
|`Duration`|Muestra una lista desplegable que contiene intervalos de tiempo. Un usuario puede seleccionar un valor de la lista o escribir un valor entero que represente el número de minutos.|
|`TimeZone`|Muestra una lista desplegable que contiene una lista de zonas horarias.|
|`Language`|Muestra una lista desplegable que contiene una lista de los idiomas que se han habilitado para la organización. Si no se han habilitado otros idiomas, el idioma base será la única opción. El valor guardado es el valor LCID del idioma.|

### <a name="string-formats"></a>Formato de cadena

Use la propiedad `FormatName` con atributos de cadena para establecer valores de la [clase StringFormatName](/dotnet/api/microsoft.xrm.sdk.metadata.stringformatname) para controlar cómo se da formato al atributo de cadena.

|Nombre|Descripción|
|--|--|
|`Email`|El campo de formulario validará el valor de texto como una dirección de correo electrónico y creará un vínculo mailto en el campo.|
|`PhoneNumber`|El campo de formulario contiene un vínculo para iniciar una llamada telefónica mediante Skype.|
|`PhoneticGuide`|Solo para uso interno.|
|`Text`|El formulario mostrará un cuadro de texto.|
|`TextArea`|El formulario mostrará un campo de área de texto.|
|`TickerSymbol`|El formulario mostrará un vínculo que se abrirá para mostrar una cotización para el símbolo de cotización bursátil.|
|`URL`|El formulario mostrará un vínculo para abrir la dirección URL.|
|`VersionNumber`|Solo para uso interno.|

### <a name="date-and-time-formats"></a>Formatos de fecha y hora

La propiedad `DateTimeBehavior` controla el comportamiento de los atributos de fecha y hora.
Hay tres opciones:

|Opción|Descripción breve|
|--|--|
|`UserLocal`|Almacena el valor de fecha y hora como valor UTC en el sistema.|
|`DateOnly`|Almacena el valor de fecha real con el valor de hora como las 12:00 a. m. (00:00:00) en el sistema.|
|`TimeZoneIndependent`|Almacena los valores de fecha y hora reales en el sistema, independientemente de la zona horaria del usuario.|

Use la propiedad `Format` para controlar cómo se mostrará el valor en una aplicación controlada por modelos con independencia del valor de `DateTimeBehavior`.

|Opción|Descripción|
|--|--|
|DateAndTime|Mostrar la fecha y hora completas|
|DateOnly|Mostrar solo la fecha.|

Más información: [Comportamiento y formato del atributo de fecha y hora (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/behavior-format-date-time-attribute)

## <a name="auto-number-attributes"></a>Atributos de numeración automática

Puede agregar un atributo de numeración automática para una entidad. Actualmente, el atributo no se puede agregar mediante programación. No hay ninguna interfaz de usuario para agregar este tipo de atributo.
Más información: [Crear atributos de numeración automática (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/create-auto-number-attributes)

## <a name="option-sets"></a>Conjuntos de opciones

Los atributos que muestran un conjunto de opciones pueden hacer referencia a un conjunto de opciones definido por el atributo o a un conjunto de opciones independiente que se puede compartir por más de un atributo. Esto es especialmente útil cuando los valores de un atributo también se aplican a otros atributos. Al hacer referencia a un conjunto de opciones común, las opciones se pueden mantener en un solo lugar. Los conjuntos de opciones que se pueden compartir son conjuntos de opciones *globales*. Los que se definen dentro del atributo son conjuntos de opciones *locales*.

### <a name="retrieve-options-data"></a>Recuperar datos de opciones
El servicio de organización proporciona clases de solicitud que se pueden usar para recuperar las opciones usadas por un atributo.

#### <a name="use-the-organization-service-to-retrieve-options"></a>Usar el servicio de organización para recuperar las opciones

Cada uno de los atributos con opciones heredan de [EnumAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.enumattributemetadata) e incluyen una [propiedad OptionSet](/dotnet/api/microsoft.xrm.sdk.metadata.enumattributemetadata.optionset). Esta propiedad contiene los [OptionSetMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.optionsetmetadata) que incluyen las opciones de la [propiedad Options](/dotnet/api/microsoft.xrm.sdk.metadata.optionsetmetadata.options). 

Con el servicio de organización, se pueden usar los mensajes siguientes para recuperar información sobre los conjuntos de opciones:

|Clase de solicitud|Descripción|
|--|--|
|[RetrieveAllOptionSetsRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrievealloptionsetsrequest) |Recupera datos sobre todos los conjuntos de opciones *globales*.|
|[RetrieveAttributeRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrieveattributerequest) |Recupera datos sobre un atributo, incluido cualquier conjunto de opciones *local*.|
|[RetrieveMetadataChangesRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrievemetadatachangesrequest) |Recupera los metadatos en función de una consulta que puede incluir conjuntos de opciones *locales*.<br />Más información: [Recuperar y detectar cambios en metadatos](/dynamics365/customer-engagement/developer/retrieve-detect-changes-metadata).|
|[RetrieveOptionSetRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrieveoptionsetrequest) |Recupera datos sobre un conjunto de opciones *global*.|

Más información: 
- [Ejemplo: volcar metadatos de lista desplegable de atributos a un archivo](/dynamics365/customer-engagement/developer/org-service/sample-dump-attribute-picklist-metadata-file)
- [Personalizar conjuntos de opciones globales (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets)

#### <a name="use-the-web-api-to-retrieve-options"></a>Usar la API web para recuperar las opciones

La API web proporciona un estilo de RESTful para consultar valores de opción. Se pueden recuperar opciones locales o globales mediante la recuperación de los atributos dentro de una entidad. En el ejemplo siguiente se devuelven los [OptionSetMetadata](/dynamics365/customer-engagement/web-api/optionsetmetadata) para las opciones incluidas en la [propiedad Account](reference/entities/account.md).[AccountCategoryCode](reference/entities/account.md#BKMK_AccountCategoryCode).

`GET <organization url>/api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes(LogicalName='accountcategorycode')/Microsoft.Dynamics.CRM.PicklistAttributeMetadata?$select=LogicalName&$expand=OptionSet`

Con la API web también se puede usar la [función RetrieveMetadataChanges](/dynamics365/customer-engagement/web-api/retrievemetadatachanges).

Más información: [Consultar metadatos con la API web (Guía para desarrolladores de Dynamics 365 Customer Engagement) > Consultar atributos EntityMetadata](/dynamics365/customer-engagement/developer/webapi/query-metadata-web-api#querying-entitymetadata-attributes)



## <a name="attribute-mapping"></a>Asignación de atributos

Cuando se crea un registro de entidad en el contexto de un registro de entidad existente, se pueden transferir automáticamente determinados valores del registro de entidad existente como valores predeterminados para el nuevo registro de entidad. Esto optimiza la entrada de datos para los usuarios de aplicaciones controladas por modelos. Los usuarios de la aplicación ven los valores asignados y los pueden modificar antes de guardar la entidad.

Para los desarrolladores que crean clientes personalizados, se puede lograr el mismo comportamiento mediante el uso del mensaje `InitializeFrom` (la [clase InitializeFromRequest](/dotnet/api/microsoft.crm.sdk.messages.initializefromrequest) del servicio de organización o la [función InitializeFrom](/dynamics365/customer-engagement/web-api/initializefrom) de la API web) para obtener los datos de entidad con el conjunto de valores predeterminado configurado.

Más información 
- [Asignar campos de entidad (Guía de personalización de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/customize/map-entity-fields#BKMK_mappingEntityFields)
- [Personalizar asignaciones de entidad y atributo (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/customize-entity-attribute-mappings)

### <a name="see-also"></a>Vea también

[Entidades de Common Data Service for Apps](entities.md)
