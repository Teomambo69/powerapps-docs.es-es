---
title: Datos de consulta con el servicio de la organización (Common Data Service para aplicaciones) | Microsoft Docs
description: Presenta las distintas formas para consultar datos con los ensamblados SDK de CDS for Apps.
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
# <a name="query-data-using-the-organization-service"></a>Consulta de datos duplicados con el servicio de organización

Los ensamblados SDK para el servicio de la organización proporcionan varios estilos de consulta de datos. Cada uno ofrece diferentes ventajas.

|Estilo|Ventajas|
|--|--|
|[FetchExpression](#use-fetchxml-with-fetchexpression)|Use el leguaje de consultas exclusivo de FetchXML para crear consultas complejas que devuelvan agregados como la suma de un valor para todos los registros devueltos. También se pueden realizar operaciones "agrupar por" con FetchXML. Puede incluir datos de entidades vinculadas.|
|[QueryExpression](#use-queryexpression)|Tiene un modelo de objetos con establecimiento inflexible de tipos para generar consultas complejas. Admite todas las características de FetchXML excepto agregados y agrupaciones. Puede incluir datos de entidades vinculadas.|
|[QueryByAttribute](#use-querybyattribute)|Un modelo de objetos más sencillo que `QueryExpression`. Use `QueryByAttribute` para consultas donde está probando si todos los criterios de valores de atributo de la consulta son una coincidencia. Solo puede devolver datos desde la entidad.|
|[LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq)|Usar <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.QueryProvider>. para crear consultas mediante la sintaxis popular de LINQ. Todas las consultas LINQ se convierten en <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> de forma que las funcionalidades se limitan a las disponibles para `QueryExpression` <br /> En este tema se centrará en los estilos de las consultas disponibles mediante las clases de ensamblados SDK. Más información: [Crear consultas con LINQ (consulta integrada del lenguaje .NET)](build-queries-with-linq-net-language-integrated-query.md)|


<xref:Microsoft.Xrm.Sdk.Query.FetchExpression>, <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> y <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> se obtienen de la clase abstracta <xref:Microsoft.Xrm.Sdk.Query.QueryBase>. Hay dos formas para obtener los resultados de una consulta definida mediante estos tipos:

- Puede pasar una instancia de cualquiera de estas clases como el parámetro `query` a <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> .
- Puede establecer la propiedad <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest.Query> de la clase <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> y usar el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> .

> [!NOTE]
> El método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> se prefiere por lo general. No hay funcionalidades especiales que requieren el uso de la clase <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest>.

Ambos métodos devolverán una <xref:Microsoft.Xrm.Sdk.EntityCollection> que contiene los resultados de la consulta en la colección <xref:Microsoft.Xrm.Sdk.EntityCollection.Entities>, así como las propiedades para administrar consultas adicionales para recibir resultados paginados. 

> [!NOTE]
> Para asegurar un máximo rendimiento, cada solicitud de consulta puede devolver un máximo de 5000 registros de entidad. Para devolver conjuntos de resultados más grandes debe solicitar páginas adicionales.

### <a name="null-attribute-values-are-not-returned"></a>Los valores de atributo NULL no se devuelven

Cuando un atributo contiene un valor nulo o si el atributo no se incluye en los atributos de FetchXml o <xref:Microsoft.Xrm.Sdk.Entity>, la colección <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>.<xref:Microsoft.Xrm.Sdk.Entity.Attributes> no incluirá el atributo. No una clave para tener acceso ni un valor para devolver. La ausencia del atributo indica que el valor es NULL. Cuando se usa el estilo de enlace en tiempo de compilación, las propiedades de clase de entidad generadas administrarán esto y devolverán un valor NULL.

Cuando se usa el estilo de enlace en tiempo de ejecución, si intenta obtener acceso al valor con un indizador en las colecciones <xref:Microsoft.Xrm.Sdk.Entity.Attributes> o <xref:Microsoft.Xrm.Sdk.Entity.FormattedValues> recibirá un <xref:System.Collections.Generic.KeyNotFoundException> con el mensaje `The given key was not present in the dictionary`.

Para evitar esto al usar el estilo de enlace en tiempo de ejecución, puede usar dos estrategias:

1. Para un atributo que pueda ser NULL, use el método <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.Contains(System.String)> para comprobar si el atributo es NULL antes de intentar tener acceso al mismo con un indizador. Por ejemplo:

    `Money revenue = (entity.Contains("revenue")? entity["revenue"] : null);`

1. Usar <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.GetAttributeValue``1(System.String)>. para acceder al valor. Por ejemplo:

    `Money revenue = entity.GetAttributeValue<Money>();`

  > [!NOTE]
  > Si el tipo indicado con <xref:Microsoft.Xrm.Sdk.Entity.GetAttributeValue``1(System.String)> es un tipo de valor que no puede ser NULL, como <xref:System.Boolean> o <xref:System.DateTime>, el valor devuelto será el valor predeterminado, como `false` o `1/1/0001 12:00:00 AM` en lugar de NULL.




## <a name="use-fetchxml-with-fetchexpression"></a>Usar FetchXML con FetchExpression

FetchXml es un lenguaje exclusivo de consultas basado en XML que se puede usar con consultas de ensamblado SDK mediante <xref:Microsoft.Xrm.Sdk.Query.FetchExpression> y por la API web mediante la cadena de consulta `fetchXml`. Más información: [API web: recuperar y ejecutar consultas predefinidas > Usar FetchXML personalizado](../webapi/retrieve-and-execute-predefined-queries.md#use-custom-fetchxml)

El siguiente ejemplo muestra una consulta sencilla para devolver hasta 50 entidades de cuenta coincidentes donde el valor `address1_city` equivale a `Redmond`, solicitado por `name`.

```csharp
string fetchXml = @"
<fetch top='50' >
  <entity name='account' >
    <attribute name='name' />
    <filter>
      <condition 
        attribute='address1_city' 
        operator='eq' 
        value='Redmond' />
    </filter>
    <order attribute='name' />
  </entity>
</fetch>";

var query = new FetchExpression(fetchXml);

EntityCollection results = svc.RetrieveMultiple(query);

results.Entities.ToList().ForEach(x => {
  Console.WriteLine(x.Attributes["name"]);
});
```

> [!IMPORTANT]
> Para recuperar registros de entidad solo debe solicitar los valores de atributo que necesite estableciendo los atributos específicos mediante los elementos `attribute` en lugar de usar el elemento `all-attributes` para devolver todos los atributos.


Más información:
- [Usar FetchXML para crear una consulta](../use-fetchxml-construct-query.md)
- [Esquema FetchXML](../fetchxml-schema.md)
- [Páginar grandes conjuntos de resultados con FetchXML](page-large-result-sets-with-fetchxml.md)
- [Usar el agregado FetchXML](../use-fetchxml-aggregation.md)
- [Fecha fiscal y operadores de consultas de fecha y hora más antiguo de en FetchXML](../use-fetchxml-fiscal-date-older-datetime-query-operators.md)
- [Use una combinación externa izquierda en FetchXML para consultar los registros "no en"](../use-fetchxml-left-outer-join-query-records-not-in.md)
- [Ejemplo: uso de agregación en FetchXML](samples/use-aggregation-fetchxml.md)
- [Ejemplo: usar FetchXML con una cookie de paginación](samples/use-fetchxml-paging-cookie.md)

## <a name="use-queryexpression"></a>Usar QueryExpression

La clase <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> proporciona un conjunto de objetos con establecimiento inflexible de tipos que se optimiza para la manipulación en tiempo de ejecución de consultas.

El siguiente ejemplo muestra una consulta sencilla para devolver hasta 50 entidades de cuenta coincidentes donde el valor `address1_city` equivale a `Redmond`, solicitado por `name`.

```csharp
var query = new QueryExpression("account")
{
  ColumnSet = new ColumnSet("name"),
  Criteria = new FilterExpression(LogicalOperator.And),
  TopCount = 50
};
query.Criteria.AddCondition("address1_city", ConditionOperator.Equal, "Redmond");
query.AddOrder("name", OrderType.Ascending);

EntityCollection results = svc.RetrieveMultiple(query);

results.Entities.ToList().ForEach(x =>
{
  Console.WriteLine(x.Attributes["name"]);
});
```

> [!IMPORTANT]
> Cuando se recuperan los registros de la entidad debe solicitar solo los valores de atributo que necesita estableciendo los atributos específicos mediante el constructor de la clase <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>. Aunque el constructor de la clase <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> proporcione una sobrecarga que acepte un parámetro booleano `allColumns`, no debería utilizar este código de producción.


Más información:
- [Crear consultas con QueryExpression](build-queries-with-queryexpression.md)
- [Conjuntos de resultados grandes de página con QueryExpression](page-large-result-sets-with-queryexpression.md)
- [Usar la clase QueryExpression](use-queryexpression-class.md)
- [Usar la clase ConditionExpression](use-conditionexpression-class.md)
- [Use la clase ColumnSet](use-the-columnset-class.md)
- [Usar la clase FilterExpression](use-filterexpression-class.md)
- [Ejemplo: Recuperación múltiple con la clase de QueryExpression](samples/retrieve-multiple-queryexpression-class.md)
- [Ejemplo: usar QueryExpression con una cookie de paginación](samples/use-queryexpression-with-a-paging-cookie.md)

## <a name="use-querybyattribute"></a>Usar QueryByAttribute

La clase <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> proporciona un conjunto de objetos con establecimiento inflexible de tipos que se optimiza para consultas comunes y sencillas de una entidad. A diferencia de FetchXML y `QueryExpression`, `QueryByAttribute` puede devolver solo los datos desde la entidad. No habilita recuperar datos de las entidades relacionadas o criterios de consulta complejos.

El siguiente ejemplo muestra una consulta sencilla para devolver hasta 50 entidades de cuenta coincidentes donde el valor `address1_city` equivale a `Redmond`, solicitado por `name`.

```csharp
var query = new QueryByAttribute("account")
{
  TopCount = 50,
  ColumnSet = new ColumnSet("name")
};
query.AddAttributeValue("address1_city", "Redmond");
query.AddOrder("name", OrderType.Ascending);

EntityCollection results = svc.RetrieveMultiple(query);

results.Entities.ToList().ForEach(x =>
{
  Console.WriteLine(x.Attributes["name"]);
});
```

Más información:
- [Usar la clase QueryByAttribute](use-querybyattribute-class.md)
- [Ejemplo: recuperar varios con la clase QueryByAttribute](samples/retrieve-multiple-querybyattribute-class.md)


## <a name="access-formatted-values"></a>Acceder a valores con formato

Independientemente del método que se use para consultar entidades, los datos se devuelven como <xref:Microsoft.Xrm.Sdk.EntityCollection><xref:Microsoft.Xrm.Sdk.EntityCollection.Entities>. Puede obtener acceso a los valores de los datos del atributo mediante la colección <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.Attributes> . Pero estos valores pueden ser de un tipo distinto al de cadena que necesitará manipular para obtener valores de cadena que puede mostrar en la aplicación.

Puede obtener acceso a los valores de cadena que usa la configuración de los entornos para dar formato mediante los valores en la colección <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.FormattedValues> .

El siguiente ejemplo muestra cómo acceder a los valores de cadena con formato para los siguientes atributos de la cuenta:

|Nombre lógico del atributo|Escriba|
|--|--|
|`primarycontactid`|<xref:Microsoft.Xrm.Sdk.EntityReference>|
|`createdon`|<xref:System.DateTime>|
|`revenue`|<xref:Microsoft.Xrm.Sdk.Money>|
|`statecode`|<xref:Microsoft.Xrm.Sdk.OptionSetValue>|

```csharp
var query = new QueryByAttribute("account")
{
TopCount = 50,
ColumnSet = new ColumnSet("name", "primarycontactid", "createdon", "revenue", "statecode")
};
query.AddAttributeValue("address1_city", "Redmond");
query.AddOrder("name", OrderType.Ascending);

EntityCollection results = svc.RetrieveMultiple(query);

results.Entities.ToList().ForEach(x =>
{
Console.WriteLine(@"
name:{0}
primary contact: {1}
created on: {2}
revenue: {3}
status: {4}",
  x.Attributes["name"],
  (x.Contains("primarycontactid")? x.FormattedValues["primarycontactid"]:string.Empty),
  x.FormattedValues["createdon"],
  (x.Contains("revenue") ? x.FormattedValues["revenue"] : string.Empty),
  x.FormattedValues["statecode"]
  );
});
```

> [!NOTE]
> Los atributos que contienen los valores NULL no se devuelven en la consulta `Attributes` o las colecciones `FormattedValues`. Si un atributo puede contener un valor nulo debe comprobarlo mediante el método <xref:Microsoft.Xrm.Sdk.Entity.Contains*> antes de intentar acceder al valor.

Los resultados con formato aparecerán como sigue:

```
name:A Datum (sample)
  primary contact: Rene Valdes (sample)
  created on: 2/28/2018 11:04 AM
  revenue: $10,000.000
  status: Active

name:City Power & Light (sample)
  primary contact: Scott Konersmann (sample)
  created on: 2/28/2018 11:04 AM
  revenue: $100,000.000
  status: Active

name:Contoso Pharmaceuticals (sample)
  primary contact: Robert Lyon (sample)
  created on: 2/28/2018 11:04 AM
  revenue: $60,000.000
  status: Active
```


## <a name="convert-queries-between-fetchxml-and-queryexpression"></a>Convertir consultas entre FetchXml y QueryExpression

Puede convertir consultas <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> a consultas FetchXml y FetchXml a QueryExpression mediante las clase <xref:Microsoft.Crm.Sdk.Messages.QueryExpressionToFetchXmlRequest> y <xref:Microsoft.Crm.Sdk.Messages.FetchXmlToQueryExpressionRequest>.

La entidad [SavedQuery](../reference/entities/savedquery.md)almacena las vistas del sistema para una entidad y la entidad [UserQuery](../reference/entities/userquery.md) almacena consultas guardadas de usuario. Otras entidades también pueden almacenar una consulta como una cadena de FetchXml. Estos métodos permiten convertir una cadena FetchXml a <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> de forma que se puede manipular mediante el modelo de objetos y luego convertirla de nuevo a FetchXml para que se pueda guardar como cadena.


Más información: [Ejemplo: convertir consultas entre Fetch y QueryExpression](samples/convert-queries-fetch-queryexpression.md)


