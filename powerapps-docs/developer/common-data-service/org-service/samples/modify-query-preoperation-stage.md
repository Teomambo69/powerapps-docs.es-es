---
title: 'Ejemplo: Modificar consulta en fase PreOperation (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo escribir un complemento que modifique una consulta definida en la fase PreOperation de una solicitud RetrieveMultiple.
ms.custom: ''
ms.date: 09/23/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a9e0cfa0a639d50a60fbc793ad87b35ed4faf8d8
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155712"
---
# <a name="sample-modify-query-in-preoperation-stage"></a>Ejemplo: Modificar consulta en fase PreOperation

Este ejemplo muestra cómo escribir un complemento que modifique una consulta definida en la fase `PreOperation` de una solicitud `RetrieveMultiple`.

El filtrado de datos en un complemento suele hacerse en la fase `PostOperation`. Los datos de <xref:Microsoft.Xrm.Sdk.EntityCollection.Entities> se pueden examinar y las entidades que no deben ser devueltas se quitan de la colección. Pero este patrón introduce problemas cuando el número de registros devuelto en una página no puede coincidir con los tamaños de paginación esperados.

El método descrito por este ejemplo es diferente. En lugar de filtrar entidades después de que han recuperado, este complemento aplicará los cambios a la consulta en la fase `PreOperation` antes de que se ejecute. 

Un punto clave mostrado por este ejemplo es que <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest.Query> puede ser uno de los tres de diferentes tipos que se deriven de <xref:Microsoft.Xrm.Sdk.Query.QueryBase>. Para dar cabida a consultas de cualquier tipo, el código de complemento debe detectar el tipo de consulta e implementar el tipo adecuado de filtro.

Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveMultipleAccountPreOperation).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

1. Descargar o clonar el informe de [Muestras](https://github.com/Microsoft/PowerApps-Samples) para que tenga una copia local. Este ejemplo se encuentra en PowerApps-Samples-master\cds\orgsvc\C#\RetrieveMultipleAccountPreOperation.
1. Abra la solución de ejemplo en Visual Studio, vaya a las propiedades del proyecto y comprueba que el ensamblado se firmará durante la compilación. Presione la F6 para compilar el ensamblado del ejemplo (RetrieveMultipleAccountPreOperation.dll).
1. Ejecute la herramienta de registro de complementos y registre el ensamblado en el espacio aislado del servidor de Common Data Service y la base de datos para la fase `PreOperation` del mensaje `RetrieveMultiple` para la entidad `Account`. 
1. Mediante un aplicación o escribiendo código para recuperar cuentas para desencadenar el complemento. Consulte [Código para probar este ejemplo](#code-to-test-this-sample) a continuación para un ejemplo.
1. Cuando haya terminado con la prueba, cancele el registro del ensamblado y el paso.

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Cuando se ejecuta, el complemento se asegurará de que los registros de cuenta inactivo no se devolverán para los tipos de consulta más comunes: <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> y<xref:Microsoft.Xrm.Sdk.Query.FetchExpression>.

<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> es un tercer tipo de consulta que también puede ser usado. No admite consultas complejas y, por tanto, no se puede aplicar filtrado complejo mediante este método. Afortunadamente, este tipo de consulta no se usa con frecuencia. Es posible que convenga rechazar consultas de este tipo lanzando <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> en la fase `PreValidation`.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

1. Compruebe que los parámetros de entrada incluyen un parámetro denominado `Query`
1. Pruebe el tipo de consulta intentando convertirlo en uno de los tres tipos esperados.
1. Según el tipo de consulta, la consulta se modifica de la forma siguiente:

### <a name="fetchexpression"></a>FetchExpression

1. Analice el valor de <xref:Microsoft.Xrm.Sdk.Query.FetchExpression.Query> que contiene el FetchXml en <xref:System.Xml.Linq.XDocument>.
1. Compruebe que el atributo `attribute` del elemento `entity` especifica la entidad `account`.
1. Examine todos los elementos `filter` de la consulta para condiciones que prueben el atributo `statecode`.
1. Quite cualquier condición existente basada en dicho atributo.
1. Agregue un nuevo `filter` a la consulta que requiere que solo se devuelvan las cuentas donde `statecode` no es igual a 1 (inactivo).
1. Establezca la consulta modificada con el valor <xref:Microsoft.Xrm.Sdk.Query.FetchExpression.Query>

```csharp
if (fetchExpressionQuery != null)
{
    tracingService.Trace("Found FetchExpression Query");

    XDocument fetchXmlDoc = XDocument.Parse(fetchExpressionQuery.Query);
    //The required entity element
    var entityElement = fetchXmlDoc.Descendants("entity").FirstOrDefault();
    var entityName = entityElement.Attributes("name").FirstOrDefault().Value;

    //Only applying to the account entity
    if (entityName == "account")
    {
        tracingService.Trace("Query on Account confirmed");

        //Get all filter elements
        var filterElements = entityElement.Descendants("filter");

        //Find any existing statecode conditions
        var stateCodeConditions = from c in filterElements.Descendants("condition")
                                    where c.Attribute("attribute").Value.Equals("statecode")
                                    select c;

        if (stateCodeConditions.Count() > 0)
        {
            tracingService.Trace("Removing existing statecode filter conditions.");
        }
        //Remove statecode conditions
        stateCodeConditions.ToList().ForEach(x => x.Remove());


        //Add the condition you want in a new filter
        entityElement.Add(
            new XElement("filter",
                new XElement("condition",
                    new XAttribute("attribute", "statecode"),
                    new XAttribute("operator", "neq"), //not equal
                    new XAttribute("value", "1") //Inactive
                    )
                )
            );
    }


    fetchExpressionQuery.Query = fetchXmlDoc.ToString();

}
```

### <a name="queryexpression"></a>QueryExpression

1. Compruebe que <xref:Microsoft.Xrm.Sdk.Query.QueryExpression.EntityName> es la entidad `account`.
1. Recorra en bucle <xref:Microsoft.Xrm.Sdk.Query.QueryExpression.Criteria>.<xref:Microsoft.Xrm.Sdk.Query.FilterExpression.Filters> recopilación
1. Use el método `RemoveAttributeConditions` recursivo para buscar cualquier instancia de <xref:Microsoft.Xrm.Sdk.Query.ConditionExpression> que pruebe el atributo statecode y quítelo.
1. Agregar un nuevo <xref:Microsoft.Xrm.Sdk.Query.FilterExpression> a <xref:Microsoft.Xrm.Sdk.Query.QueryExpression.Criteria>.<xref:Microsoft.Xrm.Sdk.Query.FilterExpression.Filters>. Colección que requiere que solo se devuelvan las cuentas donde `statecode` no es igual a 1 (inactivo).

```csharp
if (queryExpressionQuery != null)
{
    tracingService.Trace("Found Query Expression Query");
    if (queryExpressionQuery.EntityName.Equals("account"))
    {
        tracingService.Trace("Query on Account confirmed");

        //Recursively remove any conditions referring to the statecode attribute
        foreach (FilterExpression fe in queryExpressionQuery.Criteria.Filters)
        {
            //Remove any existing criteria based on statecode attribute
            RemoveAttributeConditions(fe, "statecode", tracingService);
        }

        //Define the filter
        var stateCodeFilter = new FilterExpression();
        stateCodeFilter.AddCondition("statecode", ConditionOperator.NotEqual, 1);
        //Add it to the Criteria
        queryExpressionQuery.Criteria.AddFilter(stateCodeFilter);
    }

}
```

#### <a name="removeattributeconditions-method"></a>Método RemoveAttributeConditions

Método recursivo que quita las condiciones para un atributo específico con nombre

```csharp
/// <summary>
/// Removes any conditions using a specific named attribute
/// </summary>
/// <param name="filter">The filter that may have a condition using the attribute</param>
/// <param name="attributeName">The name of the attribute that should not be used in a condition</param>
/// <param name="tracingService">The tracing service to use</param>
private void RemoveAttributeConditions(FilterExpression filter, string attributeName, ITracingService tracingService)
{

    List<ConditionExpression> conditionsToRemove = new List<ConditionExpression>();

    foreach (ConditionExpression ce in filter.Conditions)
    {
        if (ce.AttributeName.Equals(attributeName))
        {
            conditionsToRemove.Add(ce);
        }
    }

    conditionsToRemove.ForEach(x =>
    {
        filter.Conditions.Remove(x);
        tracingService.Trace("Removed existing statecode filter conditions.");
    });

    foreach (FilterExpression fe in filter.Filters)
    {
        RemoveAttributeConditions(fe, attributeName, tracingService);
    }
}
```

### <a name="querybyattribute"></a>QueryByAttribute

Puesto que <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> no admite filtros complejos, escriba solo un mensaje al registro de seguimiento de complementos. 

Si no desea que este tipo de consulta se use en absoluto, podría lanzar una <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> para impedir la operación, pero esto se aplicaría mejor durante la fase `PreValidation`.

```csharp
if (queryByAttributeQuery != null)
{
    tracingService.Trace("Found Query By Attribute Query");
    //Query by attribute doesn't provide a complex query model that 
    // can be manipulated
}
```

## <a name="code-to-test-this-sample"></a>Código para probar este ejemplo

El siguiente código demuestra 5 formas distintas de realizar la misma consulta que activará el complemento. 

Especificando un criterio específico, en este caso el valor de atributo `address1_city`, que solo se corresponde con un registro activo, estas consultas devolverán solo ese registro.

A continuación, desactive ese registro y ejecute a este código una segunda vez. No se devolverán registros.

```csharp
try
{
    string account_city_value = "ValueForTesting";

    //QueryByAttribute
    var queryByAttribute = new QueryByAttribute("account")
    {
        TopCount = 1,
        ColumnSet = new ColumnSet("accountid", "name")
    };
    queryByAttribute.AddAttributeValue("address1_city", account_city_value);
    queryByAttribute.AddOrder("name", OrderType.Descending);

    //QueryExpression
    var queryExpression = new QueryExpression("account")
    { ColumnSet = new ColumnSet("accountid", "name"), TopCount = 1 };
    queryExpression.Orders.Add(new OrderExpression("name", OrderType.Descending));
    var qeFilter = new FilterExpression(LogicalOperator.And);
    qeFilter.AddCondition(new ConditionExpression("address1_city", ConditionOperator.Equal, account_city_value));
    queryExpression.Criteria = qeFilter;

    //Fetch
    var fetchXml = $@"<fetch mapping='logical' count='1'>
                <entity name='account'>  
                    <attribute name='accountid'/>
                    <attribute name='name'/>
                    <order attribute='name' descending='true' />
                    <filter>
                    <condition attribute='address1_city' operator='eq' value='{account_city_value}' />
                    </filter>
                </entity>  
            </fetch>";

    var fetchExpression = new FetchExpression(fetchXml);

    //Get results:
    var queryByAttributeResults = service.RetrieveMultiple(queryByAttribute);
    var queryExpressionResults = service.RetrieveMultiple(queryExpression);
    var fetchExpressionResults = service.RetrieveMultiple(fetchExpression);

    //WebAPI
    string WebAPIAccountName = string.Empty;

    Dictionary<string, List<string>> ODataHeaders = new Dictionary<string, List<string>>() {
    {"Accept", new List<string>(){"application/json" } },
    {"OData-MaxVersion", new List<string>(){ "4.0" } },
    {"OData-Version", new List<string>(){ "4.0" } }};


    HttpResponseMessage response = service.ExecuteCrmWebRequest(HttpMethod.Get,
        $"accounts?$select=accountid,name&$top=1&$orderby=name desc&$filter=address1_city eq '{account_city_value}'",
        string.Empty,
        ODataHeaders);
    if (response.IsSuccessStatusCode)
    {
        var results = response.Content.ReadAsStringAsync().Result;
        var jsonResults = JObject.Parse(results);
        var accounts = (JArray)jsonResults.GetValue("value");
        if (accounts.Count > 0)
        {
            var account = accounts.First();
            WebAPIAccountName = account.Value<string>("name");
        }

    }

    else
    {
        Console.WriteLine(response.ReasonPhrase);
    }

    //Using Fetch with Web API
    string FetchWebAPIAccountName = string.Empty;
    HttpResponseMessage fetchResponse = service.ExecuteCrmWebRequest(HttpMethod.Get,
    $"accounts?fetchXml=" + Uri.EscapeDataString(fetchXml),
    string.Empty,
    ODataHeaders);
    if (fetchResponse.IsSuccessStatusCode)
    {

        var results = fetchResponse.Content.ReadAsStringAsync().Result;
        var jsonResults = JObject.Parse(results);
        var accounts = (JArray)jsonResults.GetValue("value");
        if (accounts.Count > 0)
        {
            var account = accounts.First();
            FetchWebAPIAccountName = account.Value<string>("name");
        }
    }

    else
    {
        Console.WriteLine(fetchResponse.ReasonPhrase);
    }

    string no_records_message = "No records returned";

    Console.WriteLine("QueryByAttribute Account Returned: {0}", queryByAttributeResults.Entities.Count > 0 ?
        queryByAttributeResults.Entities[0]["name"] : no_records_message);
    Console.WriteLine("QueryExpression Account Returned: {0}", queryExpressionResults.Entities.Count > 0 ?
        queryExpressionResults.Entities[0]["name"] : no_records_message);
    Console.WriteLine("Fetch Account Returned: {0}", fetchExpressionResults.Entities.Count > 0 ?
        fetchExpressionResults.Entities[0]["name"] : no_records_message);
    Console.WriteLine("WebAPI Account Returned: {0}", WebAPIAccountName != string.Empty ?
        WebAPIAccountName : no_records_message);
    Console.WriteLine("WebAPI Fetch Account Returned: {0}", FetchWebAPIAccountName != string.Empty ?
        FetchWebAPIAccountName : no_records_message);

}
catch (Exception ex)
{

    throw ex;
}
```

### <a name="see-also"></a>Vea también

[Implemente todos los tipos de consultas al filtrar resultados mediante PreOperation RetrieveMultiple](../../best-practices/business-logic/implement-all-types-of-queries-when-filtering-preoperation-retrievemultiple.md)