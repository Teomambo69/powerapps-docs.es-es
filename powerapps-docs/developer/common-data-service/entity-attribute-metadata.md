---
title: Metadatos de atributo | Microsoft Docs
description: Conozca el uso de metadatos de atributo en Common Data Service.
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

<!-- This topic was not migrated it was written for PowerApps 
Was Mike Carter
Overlap with https://docs.microsoft.com/dynamics365/customer-engagement/developer/introduction-entity-attributes

-->
# <a name="attribute-metadata"></a>Metadatos del atributo

Las entidades incluyen una colección de atributos que representan los datos que se pueden incluir en cada registro. Los programadores deben comprender los diferentes tipos de atributos y cómo trabajar con ellos. 

Más información: [Introducción a los atributos de entidad](/dynamics365/customer-engagement/developer/introduction-entity-attributes)

## <a name="attribute-names"></a>Nombres de atributo

Al igual que las entidades, cada atributo tiene un nombre único definido cuando se crea. Este nombre aparece de diversas formas:


|Nombre |Descripción  |
|---------|---------|
|`SchemaName`|Normalmente, una versión con estilo de mayúsculas y minúsculas Pascal del nombre lógico. Por ejemplo, `AccountNumber`|
|`LogicalName`|Un nombre todo en minúsculas. Por ejemplo, `accountnumber`|

Al crear un atributo personalizado, el nombre que elija estará antepuesto con el valor del prefijo de personalización del editor de soluciones asociado con la solución donde se creó el atributo.

No puede cambiar los nombres de un atributo después de haberlo creado.

Cada atributo también tiene dos propiedades que pueden mostrar valores localizados. Estos son los valores que se usan para referirse a los atributos en una aplicación.

|Nombre |Descripción  |
|---------|---------|
|`DisplayName`|Normalmente, es igual al nombre de esquema, pero puede incluir espacios. Por ejemplo **Número de cuenta**.|
|`Description`|Una breve frase que describe el atributo o que proporciona instrucciones al usuario. Por ejemplo, *Escriba un número o un código de identificación de la cuenta para buscar e identificar rápidamente la cuenta en las vistas del sistema.*<br />En aplicaciones basadas en modelos, esta información aparecerá cuando los usuarios pasen el ratón sobre el campo para este atributo en un formulario.|


Estos son los valores localizables que se usan para referirse a los atributos en una aplicación. Estos valores se puede cambiar en cualquier momento. Para agregar o editar valores localizados, consulte [Guía de personalización de Common Data Service: traducir texto de entidad y de campo personalizados a otros idiomas](/dynamics365/customer-engagement/customize/export-customized-entity-field-text-translation).

## <a name="attribute-types"></a>Tipos de atributos

La propiedad `AttributeTypeName` describe el tipo de un atributo. Esta propiedad contiene un valor de tipo `AttributeTypeDisplayName` que proporciona una etiqueta para cada uno de los diferentes tipos de atributos que existan. 

> [!NOTE]
> No se confunda con la propiedad `AttributeType`. Los valores en esta propiedad antigua están fundamental alineados con `AttributeTypeName`, pero muestra los atributos `ImageType` como `Virtual`. Debe remitirse a la propiedad `AttributeTypeName` en lugar de la propiedad `AttributeType`.

En la siguiente tabla:

- Estos tipos de agrupan por categoría para su comparación.
- Por cada valor `AttributeTypeDisplayName`, se incluye la correspondiente clase [AttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.attributemetadata) derivada del ensamblado .NET si está disponible. No hay una relación de 1:1 entre estos tipos y la etiqueta `AttributeTypeDisplayName`.
- Esos tipos de atributos que se pueden crear como atributos personalizados incluyen la etiqueta correspondiente que se muestra en la interfaz de usuario.


|Categoría|AttributeTypeDisplayName/<br />Tipo de AttributeMetadata|Can Create/<br />Etiqueta|Descripción  |
|---------|---------|---------|---------|
|Categorización|`BooleanType`<br />[BooleanAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.booleanattributemetadata)|Sí<br />**Dos opciones**|Contiene el valor de opción seleccionado de las dos opciones que indican normalmente un valor verdadero o falso.<br />Más información: [Conjuntos de opciones](#option-sets)|
|Categorización|`EntityNameType`<br />[EntityNameAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.entitynameattributemetadata)|No|Contiene un valor de opción que se corresponde con una entidad del sistema. Solo para uso interno.|
|Categorización|`MultiSelectPicklistType`<br />[MultiSelectPicklistAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.multiselectpicklistattributemetadata)|Sí<br />**Conjunto de opciones multiselección**|Contiene los valores de opción seleccionados donde se pueden seleccionar varias opciones.<br />Más información: <br />[Conjuntos de opciones](#option-sets)<br />[Atributos de lista desplegable de selección múltiple](/dynamics365/customer-engagement/developer/multi-select-picklist)|
|Categorización|`PicklistType`<br />[PicklistAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.picklistattributemetadata)|Sí<br />**Conjunto de opciones**|Contiene el valor de opción seleccionado donde se puede seleccionar una opción.<br />Más información: [Conjuntos de opciones](#option-sets)|
|Categorización|`StateType`<br />[StateAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.stateattributemetadata)|No|Contiene el valor de opción que describe el estado de un registro de entidades.<br />Más información: [Conjuntos de opciones](#option-sets)|
|Categorización|`StatusType`<br />[StatusAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.statusattributemetadata)|No|Contiene el valor de opción que describe el motivo del estado de un registro de entidades.<br />Más información: [Conjuntos de opciones](#option-sets)|
|Recogida|`CalendarRulesType`|No|Contiene una colección de registros de entidad `CalendarRules`.<br />No hay atributos reales que usen est tipo. Cuando se genera un proxy, la herramienta de generación de código creará los dos atributos simulados que no están presentes en los metadatos. Estos atributos representan una vista de registros de reglas de calendario asociados en una relación de uno a varios al registro de entidades.|
|Recogida|`PartyListType`|No|Contiene una colección de registros de entidad `ActivityParty`.<br />Más información: [Entidad ActivityParty](#activityparty-entity).|
|Fecha y hora|`DateTimeType`<br />[DateTimeAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.datetimeattributemetadata)|Sí<br />**Fecha y hora**|Contiene un valor de fecha y hora.<br />Todos los atributos de fecha y hora admiten valores de hasta 1/1/1753 12:00.|
|Imagen|`ImageType`<br />[ImageAttributeMetadata]()|Sí<br />**Imagen**|Contiene datos para admitir la recuperación de datos de imagen para un registro de entidades.<br />Más información: [Imágenes de entidad](entity-metadata.md#entity-images)|
|Propiedad administrada|`ManagedPropertyType`<br />[ManagedPropertyAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.imageattributemetadata)|No|Contiene datos que describen si el componente de la solución almacenado en el registro de la entidad se puede personalizar cuando está incluido en una solución administrada.<br />Más información: [Propiedades administradas](introduction-solutions.md#managed-properties)|
|Cantidad|`BigIntType`<br />[BigIntAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.bigintattributemetadata)|No|Contiene un valor `BigInt`. Solo para uso interno.|
|Cantidad|`DecimalType`<br />[DecimalAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.decimalattributemetadata)|Sí<br />**Número decimal**|Contiene un valor `Decimal`. La propiedad `Precision` establece el nivel de precisión.|
|Cantidad|`DoubleType`<br />[DoubleAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.doubleattributemetadata)|Sí<br />**Número de punto flotante**|Contiene un valor `Double`. La propiedad `Precision` establece el nivel de precisión.|
|Cantidad|`IntegerType`<br />[IntegerAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.integerattributemetadata)|Sí<br />**Número entero**|Contiene un valor `Int`.|
|<a name='money_type'></a>Cantidad|`MoneyType`<br />[MoneyAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.moneyattributemetadata)|Sí<br />**Divisa**|Contiene un valor `Decimal`. La propiedad `PrecisionSource` determina dónde se establece el nivel de precisión.<br />0 : La propiedad `Precision`<br />1 : El atributo `Organization.PricingDecimalPrecision`<br />2 : El atributo `TransactionCurrency.CurrencyPrecision` en el registro de entidad|
|Referencia|`CustomerType`<br />[LookupAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.lookupattributemetadata)|Sí<br />**Cliente**|Contiene una referencia a una cuenta o al registro de entidad de contacto.|
|Referencia|`LookupType`<br />[LookupAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.lookupattributemetadata)|Sí<br />**Búsqueda**|Contiene una referencia a un registro de entidad. Los nombres lógicos de los registros válidos se almacenan normalmente en la propiedad `Targets` del atributo.|
|Referencia|`OwnerType`<br />[LookupAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.lookupattributemetadata)|No|Contiene una referencia a un registro de entidad de usuario o equipo.|
|String|`MemoType`<br />[MemoAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.memoattributemetadata)|Sí<br />**Varias líneas de texto**|Contiene un valor de cadena pensado para mostrarse en un cuadro de texto de varias líneas.|
|String|`StringType`<br />[StringAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.stringattributemetadata)|Sí<br />**Línea de texto única**|Contiene un valor de cadena pensado para mostrarse en un cuadro de texto de una línea.|
|Identificador único|`UniqueidentifierType`<br />[UniqueIdentifierAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.uniqueidentifierattributemetadata)|No|Contiene un valor de identificador único de GUID.|
|Virtual|`VirtualType`|No|Estos atributos no se pueden usar en código y pueden ser ignorados por lo general.|


## <a name="supported-operations-and-form-usage-for-attributes"></a>Operaciones admitidas y el uso de formulario para los atributos

Cada atributo incluye las propiedades booleanas que describen las clases de operaciones en las que puede participar y cómo puede estar en un formulario.

|Propiedad|Descripción|
|--|--|
|`IsRequiredForForm`|Si el atributo se debe incluir como un campo en un formulario.|
|`IsValidForCreate`|Si el valor de atributo se puede establecer en una operación de crear.|
|`IsValidForForm`|Si el atributo se puede incluir como un campo en un formulario.|
|`IsValidForRead`|Si el valor del atributo se puede recuperar.|
|`IsValidForUpdate`|Si el valor de atributo se puede establecer en una operación de actualizar.|

Si intenta establecer un valor en una operación de crear o actualizar para un atributo que no sea válido para esa operación, el valor se omitirá.
Si intenta recuperar un atributo que no sea válido para la lectura, se devolverá un valor null.


## <a name="attribute-requirement-level"></a>Nivel de requisito de atributo

La propiedad `RequiredLevel` es una propiedad booleana administrada que describe si es necesario un valor de atributo.

Esta propiedad puede tener los valores siguientes establecidos:

|Nombre|Value|UI Label|Descripción|
|--|--|--|--|
|`None`|0|**Opcional**|No se especifican requisitos.|
|`SystemRequired`|1|**Necesario para el sistema**|Es necesario que el atributo tenga un valor.|
|`ApplicationRequired`|2|**Requerido por la empresa**|La empresa requiere que el atributo tenga un valor.|
|`Recommended`|3|**Recomendado por la empresa**|Se recomienda que el atributo tenga un valor.|

Common Data Service solo aplica la opción `SystemRequired` para los atributos creados por el sistema. Los atributos personalizados no se pueden configurar para que utilicen la opción `SystemRequired`. 

Las aplicaciones basadas en modelos aplicarán la opción `ApplicationRequired` y utilizarán una presentación diferente para la opción `Recommended`. Los autores de clientes personalizados pueden usar esta información para requerir una validación similar u opciones de presentación.

Como se trata de una propiedad administrada, como editor de una solución administrada puede decidir si los consumidores de la solución pueden modificar esos valores de atributos en la solución.

Más información: [Propiedades administradas](introduction-solutions.md#managed-properties)


## <a name="rollup-and-calculated-attributes"></a>Consolidar y calcular atributos

Los atributos calculados y consolidados liberan al usuario de tener que realizar cálculos manualmente y le permiten centrarse en su trabajo. Los administradores del sistema pueden definir un campo para que contenga el valor de muchos cálculos comunes sin necesidad de trabajar con un desarrollador. Los programadores también pueden aprovechar las capacidades de la plataforma para realizar estos cálculos en vez de en su propio código.

Más información: 
- [Guía de personalización Common Data Service: definir campos consolidados que agreguen valores](/dynamics365/customer-engagement/customize/define-rollup-fields)
- [Guía de personalización Common Data Service: atributos calculados y consolidados](/dynamics365/customer-engagement/customize/define-calculated-fields)
- [Atributos calculados y consolidados](/dynamics365/customer-engagement/developer/calculated-rollup-attributes)

## <a name="attribute-format"></a>Formato de atributos

Los valores de formato para atributos controla cómo se muestra en aplicaciones basadas en modelos. El desarrollador de aplicaciones personalizadas puede usar esta información para crear experiencias similares.

### <a name="integer-formats"></a>Formatos de entero

Use la propiedad `Format` con atributos de enteros para mostrar las experiencias alternativas de usuario para este tipo.

|Opción|Descripción|
|--|--|
|`None`|Muestra un cuadro de texto para editar un valor numérico|
|`Duration`|Muestra una lista desplegable que contiene intervalos de tiempo. El usuario puede seleccionar un valor de la lista o escribir un valor entero que represente el número de minutos.|
|`TimeZone`|Muestra una lista desplegable que contiene una lista de zonas horarias.|
|`Language`|Muestra una lista desplegable con los idiomas que se hayan habilitado para la organización. Si no se ha activado ningún otro idioma, el idioma base será la única opción. El valor guardado es el valor del LCID del idioma.|

### <a name="string-formats"></a>Formatos de cadena

Use la propiedad `FormatName` mediante atributos de cadena para definir valores desde la [clase StringFormatName](/dotnet/api/microsoft.xrm.sdk.metadata.stringformatname) para controlar cómo es el formato del atributo.

|Nombre|Descripción|
|--|--|
|`Email`|El campo de formulario validará el valor de texto como dirección de correo electrónico y creará un vínculo mailto en el campo.|
|`PhoneNumber`|El campo de formulario contendrá un vínculo para iniciar una llamada de teléfono mediante Skype.|
|`PhoneticGuide`|Solo para uso interno.|
|`Text`|El formulario mostrará un cuadro de texto.|
|`TextArea`|El formulario mostrará un campo de área de texto.|
|`TickerSymbol`|El formulario mostrará un vínculo que se abrirá para mostrar la cotización del valor bursátil correspondiente al símbolo.|
|`URL`|El formulario mostrará un vínculo para abrir la dirección URL.|
|`VersionNumber`|Solo para uso interno.|

### <a name="date-and-time-formats"></a>Formatos de fecha y hora

La propiedad `DateTimeBehavior` controla el comportamiento de los atributos de fecha y hora.
Hay tres opciones:

|Opción|Descripción breve|
|--|--|
|`UserLocal`|Almacena el valor de fecha y hora como valor UTC en el sistema.|
|`DateOnly`|Almacena el valor de fecha real con el valor de hora como 12:00 AM (00:00:00) en el sistema.|
|`TimeZoneIndependent`|Almacena los valores reales de fecha y hora en el sistema independientemente de la zona horaria del usuario.|

Use la propiedad `Format` para controlar cómo se muestra el valor en una aplicación basada en modelos independientemente de `DateTimeBehavior`.

|Opción|Descripción|
|--|--|
|DateAndTime|Mostrar la fecha y hora completas|
|DateOnly|Mostrar solo la fecha.|

Más información: [Comportamiento y formato del atributo de fecha y hora](/dynamics365/customer-engagement/developer/behavior-format-date-time-attribute).

## <a name="auto-number-attributes"></a>Atributos de numeración automática

Puede agregar un atributo de numeración automática para cualquier entidad. Actualmente, puede agregar el atributo mediante programación. No hay ninguna interfaz de usuario para agregar este tipo de atributo.
Más información: [Crear atributos de numeración automática](/dynamics365/customer-engagement/developer/create-auto-number-attributes)

## <a name="option-sets"></a>Conjuntos de opciones

Los atributos que muestran un conjunto de opciones pueden hacer referencia a un conjunto de opciones definidas por el atributo o pueden hacer referencia a una serie de opciones que se pueden compartir con más de un atributo. Esto resulta particularmente útil cuando los valores de un atributo también se aplican a otros atributos. Al hacer referencia a un conjunto de opciones común, las opciones se pueden mantener en un solo lugar. Los conjuntos de opciones que se pueden compartir son los conjuntos de la opción *global*. Los definidos en el atributo son conjuntos de opciones *local*.

### <a name="retrieve-options-data"></a>Recuperar datos de las opciones
El servicio de la organización proporciona clases de solicitud que puede usar para recuperar las opciones usadas por un atributo.

#### <a name="use-the-organization-service-to-retrieve-options"></a>Usar el servicio de la organización para recupera opciones

Cada uno de los atributos con opciones heredan de [EnumAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.enumattributemetadata) e incluyen [Propiedad de OptionSet](/dotnet/api/microsoft.xrm.sdk.metadata.enumattributemetadata.optionset). Esta propiedad contiene [OptionSetMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.optionsetmetadata) que incluye las opciones en la [propiedad Options](/dotnet/api/microsoft.xrm.sdk.metadata.optionsetmetadata.options). 

Con el servicio de organización puede usar los siguientes mensajes para recuperar información sobre optionsets:

|Clase Request|Descripción|
|--|--|
|[RetrieveAllOptionSetsRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrievealloptionsetsrequest) |Recupera datos sobre todos los optionsets *global*|
|[RetrieveAttributeRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrieveattributerequest) |Recupera datos sobre un atributo incluidas las optionsets *local*|
|[RetrieveMetadataChangesRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrievemetadatachangesrequest) |Recupera los metadatos en función de una consulta que puede incluir optionsets *local*<br />Más información: [Recuperar y detectar cambios en los metadatos](/dynamics365/customer-engagement/developer/retrieve-detect-changes-metadata).|
|[RetrieveOptionSetRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrieveoptionsetrequest) |Recupera datos sobre un conjunto de opciones *global*.|

Más información: 
- [Ejemplo: volcar metadatos de lista desplegable de atributo a un archivo](/dynamics365/customer-engagement/developer/org-service/sample-dump-attribute-picklist-metadata-file)
- [Guía para desarrolladores de Common Data Service: personalizar conjuntos de opciones global](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets)

#### <a name="use-the-web-api-to-retrieve-options"></a>Usar la API web para recuperar opciones

La API web proporciona un estilo RESTful para consultar valores de opción. Puede recuperar opciones locales o globales si recupera los atributos dentro de una entidad. El siguiente ejemplo devuelve [OptionSetMetadata](/dynamics365/customer-engagement/web-api/optionsetmetadata) para las opciones incluidas en [Account](reference/entities/account.md)[Propiedad AccountCategoryCode](reference/entities/account.md#BKMK_AccountCategoryCode).

`GET <organization url>/api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes(LogicalName='accountcategorycode')/Microsoft.Dynamics.CRM.PicklistAttributeMetadata?$select=LogicalName&$expand=OptionSet`

Con la API web también puede usar la función [RetrieveMetadataChanges](/dynamics365/customer-engagement/web-api/retrievemetadatachanges).

Más información: [Consultar metadatos mediante la API web > Consulta de los atributos EntityMetadata](/dynamics365/customer-engagement/developer/webapi/query-metadata-web-api#querying-entitymetadata-attributes)



## <a name="attribute-mapping"></a>Asignación de atributo

Al crear un nuevo registro de entidades en el contexto del registro de entidades existente, puede automáticamente transferir algunos valores de registro desde el registro de entidades existente como valores predeterminados para el nuevo registro de entidades. Esto simplifica la entrada de datos para las personas que usan aplicaciones basadas en modelos. Los usuarios de la aplicación ven los valores asignados y los pueden editar antes de guardar la entidad.

Para los programadores que crean clientes personalizados, se puede conseguir el mismo comportamiento si se utiliza el mensaje `InitializeFrom` (servicio de la organización [Clase InitializeFromRequest](/dotnet/api/microsoft.crm.sdk.messages.initializefromrequest) o la API web [función InitializeFrom](/dynamics365/customer-engagement/web-api/initializefrom)) para recopilar los datos de la entidad con los valores predeterminados configurados establecidos.

Más información 
- [Guía de personalización de Common Data Service: asignar campos de entidad](/dynamics365/customer-engagement/customize/map-entity-fields#BKMK_mappingEntityFields)
- [Guía para desarrolladores de Common Data Service: personalizar asignaciones de entidades y atributos](/dynamics365/customer-engagement/developer/customize-entity-attribute-mappings)

### <a name="see-also"></a>Vea también

[Entidades Common Data Service](entities.md)
