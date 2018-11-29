---
title: Atributos de lista desplegable de selección múltiple (Common Data Service para aplicaciones) | Microsoft Docs
description: Obtenga información sobre los atributos de lista desplegable de selección múltiple que permiten almacenar varias opciones seleccionables en un único atributo.
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
# <a name="multi-select-picklist-attributes"></a>Atributos de lista desplegable de selección múltiple

Los personalizadores pueden definir un atributo que permite la selección de varias opciones. La clase <xref:Microsoft.Xrm.Sdk.Metadata.MultiSelectPicklistAttributeMetadata> define un tipo de atributo que se hereda de la clase <xref:Microsoft.Xrm.Sdk.Metadata.EnumAttributeMetadata>. Igual que la clase <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata>, este atributo incluye una propiedad <xref:Microsoft.Xrm.Sdk.Metadata.OptionSetMetadata> <xref:Microsoft.Xrm.Sdk.Metadata.OptionSetMetadata.Options> que contiene las opciones válidas para el atributo. La diferencia es que los valores que se obtienen o se establecen son de un tipo <xref:Microsoft.Xrm.Sdk.OptionSetValueCollection> que contiene una matriz de enteros que representan las opciones seleccionadas. Los valores con formato de este atributo son cadenas separadas por punto y coma que contienen las etiquetas de las opciones seleccionadas.

Con la API web, este atributo se define mediante <xref href="Microsoft.Dynamics.CRM.MultiSelectPicklistAttributeMetadata?text=MultiSelectPicklistAttributeMetadata EntityType" />.

Al igual que los atributos de lista desplegable, técnicamente no existe ningún límite en cuanto al número de opciones que se pueden definir. El factor de limitación que se debe aplicar son las consideraciones de facilidad de uso. Sin embargo, solo 150 opciones se pueden seleccionar para un único atributo. Asimismo, no se puede establecer un valor predeterminado.

## <a name="setting-multi-select-picklist-values"></a>Establecer los valores de la lista desplegable de selección múltiple

Con la API web, los valores se establecen al pasar una cadena que contiene valores numéricos separados por comas, tal como se muestra en el ejemplo siguiente:
### <a name="request"></a>Solicitud
```http
POST [organization uri]/api/data/v9.0/contacts HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0

{
    "@odata.type": "Microsoft.Dynamics.CRM.contact",
    "firstname": "Wayne",
    "lastname": "Yarborough",
    "sample_outdooractivities": "1, 9"
}
```
### <a name="response"></a>Respuesta
```http
HTTP/1.1 204 No Content
OData-Version: 4.0
OData-EntityId: [organization uri]/api/data/v9.0/contacts(0c67748a-b78d-e711-811c-000d3a75bdf1)
```

Cuando el servicio de organización usa los conjuntos, utilice <xref:Microsoft.Xrm.Sdk.OptionSetValueCollection> para establecer los valores de este atributo tal como se muestra en el siguiente ejemplo de C#:
```csharp
OptionSetValueCollection activities = new OptionSetValueCollection();
activities.Add(new OptionSetValue(1)); //Swimming
activities.Add(new OptionSetValue(9)); //Camping

Contact contact = new Contact();
contact["firstname"] = "Wayne";
contact["lastname"] = "Yarborough";
contact["sample_outdooractivities"] = activities;

_serviceProxy.Create(contact);
```

## <a name="query-data-from-multi-select-picklists"></a>Consultar datos desde listas desplegables de selección múltiple

Se han agregado dos nuevos operadores de condición para admitir la consulta de valores en conjuntos de opciones de selección múltiple: `ContainValues` y `DoesNotContainValues`, o los operadores FetchXml `contain-values` y `not-contain-values`. Con la API web, hay las funciones de consulta equivalentes `ContainValues` y `DoesNotContainValues`.

Otros operadores de condición existentes que se pueden usar con este tipo de atributo son: `Equal`, `NotEqual`, `NotNull`, `Null`, `In` y `NotIn`. 

> [!NOTE]
> Los operadores `ContainValues` y `DoesNotContainValues` dependen de que se aplique indización de texto completo en las tablas de la base de datos que almacenan varios valores. Hay cierta latencia después de crear nuevos registros y antes de que el índice de texto completo surta efecto. Puede que tenga que esperar unos segundos después de que se creen nuevos registros para que los filtros que usan estos operadores pueden evaluar los valores.

Los siguientes ejemplos muestran el uso de `ContainValues` y `not-contain-values` con `FetchXML` en el siguiente conjunto de datos con un atributo de lista desplegable de selección múltiple denominado `sample_outdooractivities` en la entidad `contact`.

### <a name="multi-select-picklist-sampleoutdooractivities-options"></a>Opciones de la lista desplegable de selección múltiple `sample_outdooractivities`:

|Value|Etiqueta|
|-----|-----|
|1|Natación|
|2|Excursionismo|
|3|Montañismo|
|4|Pesca|
|5|Caza|
|6|En ejecución|
|7|Remo|
|8|Esquí|
|9|Acampada|

### <a name="contact-entity-values"></a>Valores de la entidad Contact

|`fullname`| `sample_outdooractivities` |
|--------|-------------------|
|Wayne Yarborough|1,9|
|Monte Orton|2|
|Randal Maple|4|
|Hiram Mundy|2,3,8,9|
|Barbara Weber|1,4,7|
|Georgette Sullivan|4,5,9|
|Verna Kennedy|2,4,9|
|Marvin Bracken|1,2,8,9|

### <a name="example-code-using-web-api"></a>Código de ejemplo con la API web
En el ejemplo siguiente, se muestra el uso de la función de consulta `ContainsValues` para devolver todos los contactos a los que les gusta el excursionismo. Tenga en cuenta que el texto de las opciones se devuelve como anotaciones debido a la preferencia `odata.include-annotations="OData.Community.Display.V1.FormattedValue"` aplicada.

#### <a name="request"></a>Solicitud
```http
GET [organization uri]/api/data/v9.0/contacts?$select=fullname,sample_outdooractivities&$filter=Microsoft.Dynamics.CRM.ContainValues(PropertyName='sample_outdooractivities',PropertyValues=%5B'2'%5D) HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Prefer: odata.include-annotations="OData.Community.Display.V1.FormattedValue"
```
#### <a name="response"></a>Respuesta
```http
HTTP/1.1 200 OK
Content-Type: application/json; odata.metadata=minimal
OData-Version: 4.0
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"
Content-Length: 1092

{
    "@odata.context": "[organization uri]/api/data/v9.0/$metadata#contacts(fullname,sample_outdooractivities)",
    "value": [{
        "@odata.etag": "W/\"529811\"",
        "fullname": "Monte Orton",
        "sample_outdooractivities@OData.Community.Display.V1.FormattedValue": "Hiking",
        "sample_outdooractivities": "2",
        "contactid": "cdbcc48e-0b8d-e711-811c-000d3a75bdf1"
    }, {
        "@odata.etag": "W/\"529823\"",
        "fullname": "Hiram Mundy",
        "sample_outdooractivities@OData.Community.Display.V1.FormattedValue": "Hiking; Mountain Climbing; Skiing; Camping",
        "sample_outdooractivities": "2,3,8,9",
        "contactid": "d7bcc48e-0b8d-e711-811c-000d3a75bdf1"
    }, {
        "@odata.etag": "W/\"529838\"",
        "fullname": "Verna Kennedy",
        "sample_outdooractivities@OData.Community.Display.V1.FormattedValue": "Hiking; Fishing; Camping",
        "sample_outdooractivities": "2,4,9",
        "contactid": "e6bcc48e-0b8d-e711-811c-000d3a75bdf1"
    }, {
        "@odata.etag": "W/\"529843\"",
        "fullname": "Marvin Bracken",
        "sample_outdooractivities@OData.Community.Display.V1.FormattedValue": "Swimming; Hiking; Skiing; Camping",
        "sample_outdooractivities": "1,2,8,9",
        "contactid": "ebbcc48e-0b8d-e711-811c-000d3a75bdf1"
    }]
}
```
En el ejemplo siguiente, se muestra el uso del operador `not-contain-values` en la siguiente consulta `FetchXml` con la API web.

```xml
<fetch distinct='false' no-lock='false' mapping='logical'>
    <entity name='contact'>
        <attribute name='fullname' />
        <attribute name='sample_outdooractivities' />
            <filter type='and'>
                <condition attribute='sample_outdooractivities' operator='not-contain-values'>
                    <value>2</value>
                </condition>
            </filter>
    </entity>
</fetch>
```

#### <a name="request"></a>Solicitud
```http
GET [organization uri]/api/data/v9.0/contacts?fetchXml=%253Cfetch%2520distinct%253D'false'%2520no-lock%253D'false'%2520mapping%253D'logical'%253E%253Centity%2520name%253D'contact'%253E%253Cattribute%2520name%253D'fullname'%2520%252F%253E%253Cattribute%2520name%253D'sample_outdooractivities'%2520%252F%253E%253Cfilter%2520type%253D'and'%253E%253Ccondition%2520attribute%253D'sample_outdooractivities'%2520operator%253D'not-contain-values'%253E%253Cvalue%253E2%253C%252Fvalue%253E%253C%252Fcondition%253E%253C%252Ffilter%253E%253C%252Fentity%253E%253C%252Ffetch%253E HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Prefer: odata.include-annotations="OData.Community.Display.V1.FormattedValue"
```
#### <a name="response"></a>Respuesta
```http
HTTP/1.1 200 OK
Content-Type: application/json; odata.metadata=minimal
OData-Version: 4.0
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"

{
    "@odata.context": "[organization uri]/api/data/v9.0/$metadata#contacts(fullname,sample_outdooractivities,contactid)",
    "value": [{
        "@odata.etag": "W/\"529806\"",
        "fullname": "Wayne Yarborough",
        "sample_outdooractivities@OData.Community.Display.V1.FormattedValue": "Swimming; Camping",
        "sample_outdooractivities": "1,9",
        "contactid": "c8bcc48e-0b8d-e711-811c-000d3a75bdf1"
    }, {
        "@odata.etag": "W/\"529816\"",
        "fullname": "Randal Maple",
        "sample_outdooractivities@OData.Community.Display.V1.FormattedValue": "Fishing",
        "sample_outdooractivities": "4",
        "contactid": "d2bcc48e-0b8d-e711-811c-000d3a75bdf1"
    }, {
        "@odata.etag": "W/\"529828\"",
        "fullname": "Barbara Weber",
        "sample_outdooractivities@OData.Community.Display.V1.FormattedValue": "Swimming; Fishing; Boating",
        "sample_outdooractivities": "1,4,7",
        "contactid": "dcbcc48e-0b8d-e711-811c-000d3a75bdf1"
    }, {
        "@odata.etag": "W/\"529833\"",
        "fullname": "Georgette Sullivan",
        "sample_outdooractivities@OData.Community.Display.V1.FormattedValue": "Fishing; Hunting; Camping",
        "sample_outdooractivities": "4,5,9",
        "contactid": "e1bcc48e-0b8d-e711-811c-000d3a75bdf1"
    }]
}
```

### <a name="example-code-using-queryexpression-and-fetchexpression"></a>Código de ejemplo con QueryExpression y FetchExpression

En el ejemplo de C# siguiente, se muestra el uso del operador `ContainsValues` con `QueryExpression` y de `not-contain-values` con `FetchExpression` mediante `RetrieveMultiple` y el servicio de la organización.

```csharp
//Retrieve contacts who like hiking
//Using Query Expression
int[] hikingValue = new int[] { 2 };
ConditionExpression condition = new ConditionExpression("sample_outdooractivities", ConditionOperator.ContainValues, hikingValue);

FilterExpression filter = new FilterExpression();
filter.AddCondition(condition);

QueryExpression likesHikingQuery = new QueryExpression(Contact.EntityLogicalName);
likesHikingQuery.ColumnSet.AddColumns("fullname", "sample_outdooractivities");
likesHikingQuery.Criteria.AddFilter(filter);

EntityCollection hikers = _serviceProxy.RetrieveMultiple(likesHikingQuery);

Console.WriteLine("\nContacts who like Hiking");
Console.WriteLine("=========================");
foreach (Contact contact in hikers.Entities)
{
    string values = (contact["sample_outdooractivities"] == null) ? "null" : contact.FormattedValues["sample_outdooractivities"];
    Console.WriteLine("{0} {1}", contact.FullName, values);
}

    /*OUTPUT:
    Contacts who like Hiking
    =========================
    Monte Orton Hiking
    Hiram Mundy Hiking; Mountain Climbing; Skiing; Camping
    Verna Kennedy Hiking; Fishing; Camping
    Marvin Bracken Swimming; Hiking; Skiing; Camping
    */

//Retrieving contacts who do not like hiking:
//Using Fetch Expression
string fetchXml = @"<fetch distinct='false' no-lock='false' mapping='logical'>
                     <entity name='contact'>
                      <attribute name='fullname' />
                      <attribute name='sample_outdooractivities' />
                       <filter type='and'>
                        <condition attribute='sample_outdooractivities' operator='not-contain-values'>
                         <value>2</value>
                        </condition>
                       </filter>
                      </entity>
                     </fetch>";
FetchExpression doesNotLikeHiking = new FetchExpression(fetchXml);

EntityCollection nonHikers = _serviceProxy.RetrieveMultiple(doesNotLikeHiking);

Console.WriteLine("\nContacts who do not like Hiking");
Console.WriteLine("===============================");
foreach (Contact contact in nonHikers.Entities)
{
    string values = (contact["sample_outdooractivities"] == null) ? "null" : contact.FormattedValues["sample_outdooractivities"];
    Console.WriteLine("{0} {1}", contact.FullName, values);
}

    /* OUTPUT
    Contacts who do not like Hiking
    ===============================
    Wayne Yarborough Swimming; Camping
    Randal Maple Fishing
    Barbara Weber Swimming; Fishing; Boating
    Georgette Sullivan Fishing; Hunting; Camping 
    */
```


## <a name="create-a-multi-select-picklist-with-code"></a>Crear a una lista desplegable de selección múltiple con código

La forma más sencilla de crear a una lista desplegable de selección múltiple es usar el editor de atributos de las herramientas de personalización. Más información [Crear y editar campos](/dynamics365/customer-engagement/customize/create-edit-fields)

Pero si necesita automatizar la creación de este tipo de atributo, puede usar código C# como el siguiente con el servicio de la organización que crea una lista desplegable de selección múltiple para permitir opciones de actividades al aire libre para la entidad `contact`. Más información [Crear atributos](/dynamics365/customer-engagement/developer/org-service/work-attribute-metadata.md#create-attributes)

```csharp
    private const int _languageCode = 1033; //English

    MultiSelectPicklistAttributeMetadata outDoorActivitiesAttribute = new MultiSelectPicklistAttributeMetadata()
    {
    SchemaName = "sample_OutdoorActivities",
    LogicalName = "sample_outdooractivities",
    DisplayName = new Label("Outdoor activities", _languageCode),
    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
    Description = new Label("Outdoor activities that the contact likes.", _languageCode),
    OptionSet = new OptionSetMetadata()
        {
            IsGlobal = false,
            OptionSetType = OptionSetType.Picklist,
            Options = {
                new OptionMetadata(new Label("Swimming",_languageCode),1),
                new OptionMetadata(new Label("Hiking",_languageCode),2),
                new OptionMetadata(new Label("Mountain Climbing",_languageCode),3),
                new OptionMetadata(new Label("Fishing",_languageCode),4),
                new OptionMetadata(new Label("Hunting",_languageCode),5),
                new OptionMetadata(new Label("Running",_languageCode),6),
                new OptionMetadata(new Label("Boating",_languageCode),7),
                new OptionMetadata(new Label("Skiing",_languageCode),8),
                new OptionMetadata(new Label("Camping",_languageCode),9)}
        }
    };

    CreateAttributeRequest createAttributeRequest = new CreateAttributeRequest
    {
        EntityName = Contact.EntityLogicalName,
        Attribute = outDoorActivitiesAttribute
    };
```

### <a name="see-also"></a>Vea también
[Introducción a los atributos de entidad](/dynamics365/customer-engagement/developer/introduction-entity-attributes)<br />
[Cree una entidad usando API web](webapi/create-entity-web-api.md)<br />
[Consultar datos utilizando la API web](webapi/query-data-web-api.md)<br />
[Trabajar con metadatos de atributos](/dynamics365/customer-engagement/developer/org-service/work-attribute-metadata)<br />
[Ejemplo: Trabajar con metadatos de atributos](/dynamics365/customer-engagement/developer/org-service/sample-work-attribute-metadata)<br />
[Programación en tiempo de ejecución y en tiempo de compilación con el servicio de la organización](org-service/early-bound-programming.md)
