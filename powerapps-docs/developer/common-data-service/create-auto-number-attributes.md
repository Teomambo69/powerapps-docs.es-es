---
title: Crear atributos de numeración automática (Common Data Service) | Microsoft Docs
description: 'Obtenga información sobre cómo crear un atributo de numeración automática del mismo modo que se crea un atributo de cadena mediante la clase StringAttributeMetadata excepto que en este caso se usa la nueva propiedad AutoNumberFormat. Utilice la propiedad AutoNumberFormat para definir un modelo que incluya números secuenciales y cadenas aleatorias mediante la composición de marcadores de posición, que indica la longitud y el tipo de valores que se generan.'
keywords: Atributos de numeración automática
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: MicroSri
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-auto-number-attributes"></a>Crear atributos de numeración automática

Con Common Data Service puede agregar un atributo de numeración automática para cualquier entidad. Actualmente, puede agregar el atributo mediante programación. No hay ninguna interfaz de usuario para agregar este tipo de atributo. El tema explica cómo puede crear mediante programación un atributo de numeración automática y establecer un valor de semilla para los elementos de la secuencia. Además, el tema muestra cómo establecer el número de secuencia del registro siguiente si necesita restablecer el valor de semilla en cualquier momento más adelante.
> [!NOTE]
>El establecimiento de un valor de semilla es opcional. No es necesario llamar a la semilla si no es necesario volver a sembrar el valor.


Puede crear un atributo de numeración automática del mismo modo que se crea un atributo de cadena mediante la clase **StringAttributeMetadata** excepto que en este caso se usa la nueva propiedad **AutoNumberFormat**. Utilice la propiedad **AutoNumberFormat** para definir un modelo que incluya números secuenciales y cadenas aleatorias mediante la composición de marcadores de posición, que indica la longitud y el tipo de valores que se generan. Las cadenas aleatorias le ayudan a evitar duplicados o colisiones, en especial cuando los clientes sin conexión intentan crear números automáticamente.

Cuando se crea un atributo de numeración automática, los valores de la propiedad **StringAttributeMetadata.FormatName** o de la propiedad **StringAttributeMetadata.Format** deben ser de texto. Puesto que estos son los valores predeterminados, normalmente no será necesario definir esta propiedad. No se puede crear un atributo de numeración automática que utiliza cualquier otro tipo de formato especial como Email, Phone, TextArea, Url o cualquier otro [formato existente](https://msdn.microsoft.com/library/microsoft.xrm.sdk.metadata.stringformatname.aspx).

SQL genera el segmento secuencial y, por tanto, SQL garantiza la exclusividad.

> [!NOTE]
>Puede modificar un atributo de texto de formato existente para que sea un formato de numeración automática.

Cuando se agrega el atributo de numeración automática como un campo a un formulario, el campo del atributo de numeración automática se comporta como de solo lectura en el formulario, y los usuarios finales no pueden editar el campo. El valor solo se establece después de guardar la entidad. Puede ver el atributo de numeración automática como el valor de cualquier otro campo en las vistas, las cuadrículas, etc.

### <a name="examples"></a>Ejemplos
Los siguientes ejemplos muestran cómo crear un nuevo atributo de numeración automática llamado **new\_SerialNumber** para una entidad personalizada llamada **new\_Widget** que tengan un valor similar a este: **WID-00001-AB7LSFG-20170913070240**.
Mediante el servicio de la organización con las clases **CreateAttributeRequest** y **StringAttributeMetadata** de ensamblados de SDK:

```csharp
CreateAttributeRequest widgetSerialNumberAttributeRequest = new CreateAttributeRequest
            {
                EntityName = "newWidget",
                Attribute = new StringAttributeMetadata
                {
                    //Define the format of the attribute
                    AutoNumberFormat = "WID-{SEQNUM:5}-{RANDSTRING:6}-{DATETIMEUTC:yyyyMMddhhmmss}",
                    LogicalName = "new_serialnumber",
                    SchemaName = "new_SerialNumber",
                    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
                    MaxLength = 100, // The MaxLength defined for the string attribute must be greater than the length of the AutoNumberFormat value, that is, it should be able to fit in the generated value.
                    DisplayName = new Label("Serial Number", 1033),
                    Description = new Label("Serial Number of the widget.", 1033)
                }
            };
            _serviceProxy.Execute(widgetSerialNumberAttributeRequest);
```

## <a name="use-web-api"></a>Usar la API web

Puede crear y actualizar definiciones de entidad mediante la API web.

Más información: [Crear y actualizar definiciones de entidad mediante la API web > Crear atributos](https://msdn.microsoft.com/library/mt593078.aspx#Anchor_3).

#### <a name="request"></a>Solicitud
```http
POST [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='new_widget')/Attributes HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0

{
 "AttributeType": "String",
 "AttributeTypeName": {
  "Value": "StringType"
 },
 "Description": {
  "@odata.type": "Microsoft.Dynamics.CRM.Label",
  "LocalizedLabels": [
   {
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",
    "Label": "Serial Number of the widget.",
    "LanguageCode": 1033
   }
  ]
 },
 "DisplayName": {
  "@odata.type": "Microsoft.Dynamics.CRM.Label",
  "LocalizedLabels": [
   {
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",
    "Label": "Serial Number",
    "LanguageCode": 1033
   }
  ]
 },
 "RequiredLevel": {
  "Value": "None",
  "CanBeChanged": true,
  "ManagedPropertyLogicalName": "canmodifyrequirementlevelsettings"
 },
 "SchemaName": "new_SerialNumber",
 "AutoNumberFormat": "WID-{SEQNUM:5}-{RANDSTRING:6}-{DATETIMEUTC:yyyyMMddhhmmss}",
 "@odata.type": "Microsoft.Dynamics.CRM.StringAttributeMetadata",
 "FormatName": {
  "Value": "Text"
 },
 "MaxLength": 100
}
```

#### <a name="response"></a>Respuesta

```http
HTTP/1.1 204 No Content
OData-Version: 4.0
OData-EntityId: [Organization URI]/api/data/v9.0/EntityDefinitions(402fa40f-287c-e511-80d2-00155d2a68d2)/Attributes(f01bef16-287c-e511-80d2-00155d2a68d2)
```

## <a name="autonumberformat-options"></a>Opciones de AutoNumberFormat

Estos ejemplos muestran cómo puede configurar la propiedad **AutoNumberFormat** para obtener resultados diferentes:

|**Valor de AutoNumberFormat**|**Valor de ejemplo**|
|:----------|:----------|
|`CAR-{SEQNUM:3}-{RANDSTRING:6}`|`CAR-123-AB7LSF`|
|`CNR-{RANDSTRING:4}-{SEQNUM:4}`|`CNR-WXYZ-1000`|
|`{SEQNUM:6}-#-{RANDSTRING:3}`  |`123456-#-R3V`|
|`KA-{SEQNUM:4}`                |`KA-0001`|
|`{SEQNUM:10}`                  |`1234567890`|
|`QUO-{SEQNUM:3}#{RANDSTRING:3}#{RANDSTRING:5}`|      `QUO-123#ABC#PQ2ST`|
|`QUO-{SEQNUM:7}{RANDSTRING:5}` |`QUO-0001000P9G3R`|
|`CAS-{SEQNUM:6}-{RANDSTRING:6}-{DATETIMEUTC:yyyyMMddhhmmss}`|`CAS-002000-S1P0H0-20170913091544`|
|`CAS-{SEQNUM:6}-{DATETIMEUTC:yyyyMMddhh}-{RANDSTRING:6}`|`CAS-002002-2017091309-HTZOUR`|
|`CAS-{SEQNUM:6}-{DATETIMEUTC:yyyyMM}-{RANDSTRING:6}-{DATETIMEUTC:hhmmss}`|`CAS-002000-201709-Z8M2Z6-110901`|

Los marcadores de posición de cadena aleatoria son opcionales. Puede incluir más de un marcador de posición de cadena aleatoria. Utilice cualquiera de los marcadores de posición de valor de formato para de fecha y hora [Cadenas con formato de fecha y hora estándar](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings).

### <a name="string-length"></a>Longitud de cadena

En la tabla se muestra el valor de la longitud de cadena para los marcadores de posición aleatorios y secuenciales.

<table>
  <tr>
    <th>Marcador de posición</th>
    <th>Longitud de cadena</th>
    <th>Escenario de salida</th>
  </tr>
  <tr>
    <td><code>{RANDSTRING:MIN_LENGTH}</code></td>
    <td>El valor de <b>MIN_LENGTH</b> está entre 1 y 6.</td>
     <td>Cuando se guarda la entidad, el atributo de numeración automática genera la cadena aleatoria con la longitud definida si el valor está entre 1 y 6. Si usa un valor <b>MIN_LENGTH</b> de 7 o más, obtendrá un error de argumento no válido.</td>
  </tr>
  <tr>
    <td><code>{SEQNUM:MIN_LENGTH}</code></td>
    <td>El valor mínimo de <b>MIN_LENGTH</b> es 1. El número sigue aumentando más allá de la longitud mínima.</td>
    <td>Cuando se guarda la entidad, el atributo de numeración automática funciona bien y sigue funcionando correctamente para valores mayores de <b>MIN_LENGTH</b>.</td></table>

Para marcadores de posición de valores secuenciales, **MIN_LENGTH** es una longitud mínima. Si establece el valor en 2, el valor inicial será 01 y el valor de la entidad número 100 será 100. El número seguirá aumentando más allá de la longitud mínima. El valor en la configuración de la longitud de los valores secuenciales sirve para establecer una longitud coherente para el valor generado automáticamente agregando 0 adicionales al valor inicial. Esto no limitará el valor absoluto. Los marcadores de posición de valores aleatorios siempre serán la misma longitud.

Como los valores secuenciales pueden ser mayores que la longitud mínima asignada, no debería ajustar la propiedad **StringAttributeMetadata.MaxLength** para que coincida con la longitud del valor con formato. Esto no es de gran utilidad porque podría producir un error en el futuro si el valor supera el valor de **MaxLength**. Asegúrese de que queda suficiente espacio para un intervalo realista de valores de la secuencia.

> [!NOTE]
> No se necesita ninguna validación de los valores de marcador de posición cuando se crea el atributo. El error aparece solo cuando intenta guardar una instancia de entidad que utiliza un valor de **AutoNumberFormat** configurado incorrectamente.
> Por ejemplo, si especifica la longitud de la cadena aleatoria como mayor de 6, la primera persona en crear una nueva instancia de entidad obtendrá un error **Argumento no válido** al intentar guardar por primera vez la entidad que contiene el nuevo atributo de numeración automática.

## <a name="update-auto-number-attributes"></a>Actualizar atributos de numeración automática

Si crea un atributo de numeración automática con una configuración incorrecta o si desea modificar un atributo de numeración automática existente, puede actualizar el valor **AutoNumberFormat** del atributo.

El siguiente fragmento de código explica cómo recuperar, modificar y actualizar el atributo de numeración automática.

Para modificar un atributo de numeración automática existente, debe recuperar el atributo mediante la clase **RetrieveAttributeRequest**.

```csharp
// Create the retrieve request
RetrieveAttributeRequest attributeRequest = new RetrieveAttributeRequest
            {
                EntityLogicalName = entityName.ToLower(),
                LogicalName = "new_serialnumber",
                RetrieveAsIfPublished = true
            };
// Retrieve attribute response
RetrieveAttributeResponse attributeResponse = (RetrieveAttributeResponse)_serviceProxy.Execute(attributeRequest);
```

Después de recuperar el atributo de numeración automática, debe modificar y actualizar el atributo.

```csharp            
//Modify the retrieved auto-number attribute
AttributeMetadata retrievedAttributeMetadata = attributeResponse.AttributeMetadata;
retrievedAttributeMetadata.AutoNumberFormat = "CAR-{RANDSTRING:5}{SEQNUM:6}"; //Modify the existing attribute by writing the format as per your requirement 

// Update the auto-number attribute            
UpdateAttributeRequest updateRequest = new UpdateAttributeRequest
                        {
                            Attribute = retrievedAttributeMetadata,
                            EntityName = "newWidget",
                        };
// Execute the request
_serviceProxy.Execute(updateRequest);
```

## <a name="set-a-seed-value"></a>Establecer un valor de semilla

De forma predeterminada, todos los valores de la secuencia de numeración automática comienzan con 1000 y utilizan 0 como prefijo según la longitud. De este modo, la longitud del valor siempre es el misma. Si desea cambiar el valor inicial, debe cambiar el valor de semilla inicial mediante la API que se indica a continuación para establecer el número siguiente que se usará para el segmento de la secuencia.

Por ejemplo, cuando la longitud del número de secuencia es 5, es posible que desee comenzar con un valor inicial de 10000 en lugar del valor predeterminado de 00001. Si desea elegir un valor inicial diferente después de crear el atributo de numeración automática, utilice el mensaje **SetAutoNumberSeed**. Utilice la clase **SetAutoNumberSeedRequest** cuando use los ensamblados de SDK y la acción **SetAutoNumberSeed** cuando use la API de web.

El mensaje **AutoNumberSeed** tiene los siguientes parámetros:


|**Nombre**|**Tipo**|**Descripción**|
|:----------|:----------|:----------|
|EntityName|cadena|El nombre lógico de la entidad que contiene el atributo en el que desea establecer el valor de semilla.|
|AttributeName|cadena|El nombre lógico del atributo en el que desea establecer el valor de semilla.|
|Value|int|El siguiente valor de numeración automática del atributo.|

> [!NOTE]
> Establecer el valor de inicialización sólo cambia el **valor numérico actual** para el atributo especificado en el entorno actual. No implica un **valor de inicio** común para el atributo. El valor de inicialización no se incluye en una solución cuando se instala en diferentes entornos. Para establecer el número de inicio después de una importación de solución, use el mensaje **SetAutoNumberSeed** en el entorno de destino.

### <a name="examples"></a>Ejemplos
Los siguientes ejemplos establecen el valor de semilla en 10000 para un atributo de numeración automática llamado **new\_SerialNumber** para una entidad personalizada llamada **new\_Widget**.

Usando el servicio de organización con la clase **SetAutoNumberSeedRequest** de ensamblados de SDK:
```csharp
//Define the seed 
SetAutoNumberSeedRequest req = new SetAutoNumberSeedRequest();
req.EntityName = "newWidget";
req.AttributeName = "newSerialnumber";
req.Value = 10000;
_serviceProxy.Execute(req);
```
Con la acción **SetAutoNumberSeed** de la API web.

Más información: [Use las acciones de API de web > Acciones sin enlazar](https://msdn.microsoft.com/library/mt607600.aspx#bkmk_unboundActions)

#### <a name="request"></a>Solicitud

```http
POST [Organization URI]/api/data/v9.0/SetAutoNumberSeed HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0

{
 "EntityName": "new_Widget",
 "AttributeName": "new_Serialnumber",
 "Value": 10000
} 
```

#### <a name="response"></a>Respuesta

```json
HTTP/1.1 204 No Content
OData-Version: 4.0
```
## <a name="community-tools"></a>Herramientas de la Comunidad

### <a name="auto-number-manager"></a>Auto Number Manager

**[Auto Number Manager](https://www.xrmtoolbox.com/plugins/Rappen.XrmToolBox.AutoNumManager/)** para XrmToolBox es una herramienta impulsada por la comunidad para Common Data Service que proporciona una interfaz de usuario para configurar, actualizar y quitar el formato de numeración automática en atributos nuevos y existentes.
Consulte el tema [Herramientas del desarrollador](developer-tools.md) para ver las herramientas desarrolladas por la comunidad y [anm.xrmtoolbox.com](http://anm.xrmtoolbox.com) para obtener más información sobre Auto Number Manager.

> [!NOTE]
> Las herramientas de la Comunidad no son un producto de Common Data Service y no se amplía el soporte para las herramientas de comunidad. Si tiene alguna duda relacionada con la herramienta, póngase en contacto con el Editor. Más información: [XrmToolBox](https://www.xrmtoolbox.com). 


### <a name="see-also"></a>Vea también
[Modelos de datos y metadatos en Dynamics 365](/dynamics365/customer-engagement/developer/metadata-data-models)  
[Personalizar metadatos de entidad](customize-entity-metadata.md) 