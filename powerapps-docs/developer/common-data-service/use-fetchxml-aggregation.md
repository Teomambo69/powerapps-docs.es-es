---
title: Utilizar el agregado FetchXML (Common Data Service) | Microsoft Docs
description: 'Más información sobre las características de agrupación y agregación que le permiten calcular la suma, media, mínimo, máximo y recuento.'
ms.custom: ''
ms.date: 06/18/2019
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

# <a name="use-fetchxml-aggregation"></a>Usar el agregado FetchXML

En Common Data Service, `FetchXML` incluye características de agrupación y agregación que le permiten calcular la suma, media, mínimo, máximo y recuento.  
  
 Se admiten las siguientes funciones de agregado:  
  
- sum  
- avg  
- min.  
- max  
- count(*)  
- count(*nombre de atributo*)
  
<a name="Aggregation"></a>

## <a name="about-aggregation"></a>Acerca de la agregación
 
Para crear un atributo de agregado, establezca la palabra clave `aggregate` en `true`. A continuación, especifique un *nombre de entidad*, un *nombre de atributo* y un *alias* (nombre de variable) válidos. También debe especificar el tipo de agregación que desea realizar.  
  
El siguiente ejemplo muestra un atributo de agregado sencillo en `FetchXML`.  
  
```xml  
<fetch distinct='false' mapping='logical' aggregate='true'>   
   <entity name='entity name'>   
      <attribute name='attribute name' aggregate='count' alias='alias name'/>   
   </entity>   
</fetch>
```  
  
El resultado de una consulta con un atributo de agregado es diferente de los resultados de una consulta estándar. Se usa el valor de alias como identificador de etiqueta para el resultado de agregado.  
  
El siguiente ejemplo muestra el formato de salida de una consulta de agregado.  
  
```xml
<resultset morerecords="0"'>   
   <result>  
      <alias>aggregate value</alias>  
   </result>  
</resultset>
```  
  
El siguiente ejemplo muestra los resultados de una consulta cuando la variable de alias se establece en `account_count`.  
  
```xml
<resultset morerecords="0"'>   
   <result>  
      <account_count>20</account_count>  
   </result>  
</resultset>
```  

<a name="Limitations"></a>

## <a name="limitations"></a>Limitaciones

Las consultas que devuelven valores agregados están limitadas a 50.000 registros. Este límite ayuda a mantener el rendimiento y confiabilidad del sistema. Si el criterio de filtra en su consulta incluye más de 50.000 registros se mostrará el error siguiente:

Código de error: `-2147164125`<br />
Código de error hexadecimal: `8004E023`<br />
Mensaje de error de plataforma: `AggregateQueryRecordLimit exceeded. Cannot perform this operation.`<br />
Mensaje de error al cliente: Se supera el límite de registros máximos. Reduzca el número de registros.<br />

Para evitar este error agregue filtros adecuados a la consulta para asegurarse de que no evaluará más de 50.000 registros. Después ejecute la consulta varias veces y combine los resultados.

> [!TIP]
> Si desea obtener un recuento total de registros sin filtro, use el mensaje `RetrieveTotalRecordCount` con la API web <xref href="Microsoft.Dynamics.CRM.RetrieveTotalRecordCount?text=RetrieveTotalRecordCount Function" /> o con una clase de mensaje servicio<xref:Microsoft.Crm.Sdk.Messages.RetrieveTotalRecordCountRequest> del servicio de la organización.
  
<a name="AVG"></a>

## <a name="avg"></a>Prom.

 El siguiente ejemplo muestra cómo usar el atributo `avg` `aggregate`.  
  
 ```csharp
// Fetch the average of estimatedvalue for all opportunities.  This is the equivalent of 
// SELECT AVG(estimatedvalue) AS estimatedvalue_avg ... in SQL.
string estimatedvalue_avg = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='estimatedvalue' alias='estimatedvalue_avg' aggregate='avg' /> 
    </entity> 
</fetch>";

EntityCollection estimatedvalue_avg_result = _serviceProxy.RetrieveMultiple(new FetchExpression(estimatedvalue_avg));

foreach (var c in estimatedvalue_avg_result.Entities)
{
    decimal aggregate1 = ((Money)((AliasedValue)c["estimatedvalue_avg"]).Value).Value;
    System.Console.WriteLine("Average estimated value: " + aggregate1);

}
```
  
### <a name="limitation-with-null-values-while-computing-average"></a>Limitación con valores nulos mientras se calcula el promedio

Los **valores** no se consideran cuando Common Data Service calcula el promedio de los datos. En su lugar, se usa cero (0).  
  
En el siguiente ejemplo, con los siguientes datos, el promedio de la Cuenta 1 (dos entradas) se mostrará como 250, mientras que el promedio de la Cuenta 2 (dos entradas) se mostrará como 125.  
  
|Tema|Cliente potencial|Valor estimado|  
|-----|------------------|---------------|  
|Oportunidad 1|Cuenta 1|nulo|  
|Oportunidad 2|Cuenta 1|250|  
|Oportunidad 3|Cuenta 2|0|  
|Oportunidad 4|Cuenta 2|250|  
  
<a name="count"></a>

## <a name="count"></a>Recuento

El siguiente ejemplo muestra cómo usar el atributo `count` `aggregate`.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      opportunity_count   Aggregate 2
// *****************************************************************************************************************
// Fetch the count of all opportunities.  This is the equivalent of
// SELECT COUNT(*) AS opportunity_count ... in SQL.
string opportunity_count = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='name' alias='opportunity_count' aggregate='count'/> 
    </entity> 
</fetch>";

EntityCollection opportunity_count_result = _serviceProxy.RetrieveMultiple(new FetchExpression(opportunity_count));

foreach (var c in opportunity_count_result.Entities)
{
    Int32 aggregate2 = (Int32)((AliasedValue)c["opportunity_count"]).Value;
    System.Console.WriteLine("Count of all opportunities: " + aggregate2); 

}
```
  
<a name="count_column"></a>

### <a name="countcolumn"></a>CountColumn

El siguiente ejemplo muestra cómo usar el atributo `countcolumn` `aggregate` para contar columnas.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      opportunity_colcount   Aggregate 3
// *****************************************************************************************************************
// Fetch the count of all opportunities.  This is the equivalent of 
// SELECT COUNT(name) AS opportunity_count ... in SQL.
string opportunity_colcount = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='name' alias='opportunity_colcount' aggregate='countcolumn'/> 
    </entity> 
</fetch>";

EntityCollection opportunity_colcount_result = _serviceProxy.RetrieveMultiple(new FetchExpression(opportunity_colcount));

foreach (var c in opportunity_colcount_result.Entities)
{
    Int32 aggregate3 = (Int32)((AliasedValue)c["opportunity_colcount"]).Value;
    System.Console.WriteLine("Column count of all opportunities: " + aggregate3);

}
```
  
<a name="count_distinct"></a>
 
### <a name="count-distinct-columns"></a>Varias columnas de recuento

El siguiente ejemplo muestra cómo usar el atributo `countcolumn` `aggregate` con el atributo `distinct` para contar varias columnas.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      opportunity_distcount   Aggregate 4
// *****************************************************************************************************************
// Fetch the count of distinct names for opportunities.  This is the equivalent of 
// SELECT COUNT(DISTINCT name) AS opportunity_count ... in SQL.
string opportunity_distcount = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='name' alias='opportunity_distcount' aggregate='countcolumn' distinct='true'/> 
    </entity> 
</fetch>";

EntityCollection opportunity_distcount_result = _serviceProxy.RetrieveMultiple(new FetchExpression(opportunity_distcount));

foreach (var c in opportunity_distcount_result.Entities)
{
    Int32 aggregate4 = (Int32)((AliasedValue)c["opportunity_distcount"]).Value;
    System.Console.WriteLine("Distinct name count of all opportunities: " + aggregate4);

}
```
  
<a name="max"></a>

## <a name="max"></a>Máx.

Los valores **Null** no se consideran cuando Common Data Service calcula el máximo de datos. En su lugar, se usa cero (0).  
  
El siguiente ejemplo muestra cómo usar el atributo `max` `aggregate`.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      estimatedvalue_max   Aggregate 5
// *****************************************************************************************************************
// Fetch the maximum estimatedvalue of all opportunities.  This is the equivalent of 
// SELECT MAX(estimatedvalue) AS estimatedvalue_max ... in SQL.
string estimatedvalue_max = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
        <attribute name='estimatedvalue' alias='estimatedvalue_max' aggregate='max' /> 
    </entity> 
</fetch>";

EntityCollection estimatedvalue_max_result = service.RetrieveMultiple(new FetchExpression(estimatedvalue_max));

foreach (var c in estimatedvalue_max_result.Entities)
{
    decimal aggregate5 = ((Money)((AliasedValue)c["estimatedvalue_max"]).Value).Value;
    Console.WriteLine("Max estimated value of all opportunities: " + aggregate5);

}
```
  
<a name="min"></a>
 
## <a name="min"></a>Minutos

Los valores **Null** no se consideran cuando Common Data Service calcula el mínimo de datos. En su lugar, se usa cero (0).  
  
El siguiente ejemplo muestra cómo usar el atributo `min``aggregate`.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      estimatedvalue_min   Aggregate 6
// *****************************************************************************************************************
// Fetch the minimum estimatedvalue of all opportunities.  This is the equivalent of 
// SELECT MIN(estimatedvalue) AS estimatedvalue_min ... in SQL.
string estimatedvalue_min = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='estimatedvalue' alias='estimatedvalue_min' aggregate='min' /> 
    </entity> 
</fetch>";

EntityCollection estimatedvalue_min_result = _serviceProxy.RetrieveMultiple(new FetchExpression(estimatedvalue_min));

foreach (var c in estimatedvalue_min_result.Entities)
{
    decimal aggregate6 = ((Money)((AliasedValue)c["estimatedvalue_min"]).Value).Value;
    System.Console.WriteLine("Minimum estimated value of all opportunities: " + aggregate6);

}
```
  
<a name="sum"></a>

## <a name="sum"></a>Suma

El siguiente ejemplo muestra cómo usar el atributo `sum``aggregate`.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      estimatedvalue_sum   Aggregate 7
// *****************************************************************************************************************
// Fetch the sum of estimatedvalue for all opportunities.  This is the equivalent of 
// SELECT SUM(estimatedvalue) AS estimatedvalue_sum ... in SQL.
string estimatedvalue_sum = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='estimatedvalue' alias='estimatedvalue_sum' aggregate='sum' /> 
    </entity> 
</fetch>";

EntityCollection estimatedvalue_sum_result = _serviceProxy.RetrieveMultiple(new FetchExpression(estimatedvalue_sum));

foreach (var c in estimatedvalue_sum_result.Entities)
{
    decimal aggregate7 = ((Money)((AliasedValue)c["estimatedvalue_sum"]).Value).Value;
    System.Console.WriteLine("Sum of estimated value of all opportunities: " + aggregate7);

}
```
  
<a name="mult_agg"></a>
 
## <a name="multiple-aggregates"></a>Varios agregados

El siguiente ejemplo muestra cómo usar varios atributos `aggregate` para establecer un mínimo y un máximo.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      estimatedvalue_avg, estimatedvalue_sum   Aggregate 8
// *****************************************************************************************************************
// Fetch multiple aggregate values within a single query.
string estimatedvalue_avg2 = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='opportunityid' alias='opportunity_count' aggregate='count'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_sum' aggregate='sum'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_avg' aggregate='avg'/> 
    </entity> 
</fetch>";

EntityCollection estimatedvalue_avg2_result = _serviceProxy.RetrieveMultiple(new FetchExpression(estimatedvalue_avg2));

foreach (var c in estimatedvalue_avg2_result.Entities)
{
    Int32 aggregate8a = (Int32)((AliasedValue)c["opportunity_count"]).Value;
    System.Console.WriteLine("Count of all opportunities: " + aggregate8a);
    decimal aggregate8b = ((Money)((AliasedValue)c["estimatedvalue_sum"]).Value).Value;
    System.Console.WriteLine("Sum of estimated value of all opportunities: " + aggregate8b);
    decimal aggregate8c = ((Money)((AliasedValue)c["estimatedvalue_avg"]).Value).Value;
    System.Console.WriteLine("Average of estimated value of all opportunities: " + aggregate8c);

}
```
  
<a name="groupby"></a>
 
## <a name="group-by"></a>Agrupar por

El siguiente ejemplo muestra cómo usar varios atributos `aggregate` y un atributo `groupby` vinculado.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      groupby1   Aggregate 9
// *****************************************************************************************************************
// Fetch a list of users with a count of all the opportunities they own using groupby.
string groupby1 = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='name' alias='opportunity_count' aggregate='countcolumn' /> 
       <attribute name='ownerid' alias='ownerid' groupby='true' /> 
    </entity> 
</fetch>";

EntityCollection groupby1_result = _serviceProxy.RetrieveMultiple(new FetchExpression(groupby1));

foreach (var c in groupby1_result.Entities)
{
    Int32 aggregate9a = (Int32)((AliasedValue)c["opportunity_count"]).Value;
    System.Console.WriteLine("Count of all opportunities: " + aggregate9a + "\n");
    string aggregate9b = ((EntityReference)((AliasedValue)c["ownerid"]).Value).Name;
    System.Console.WriteLine("Owner: " + aggregate9b);
    string aggregate9c = (string)((AliasedValue)c["ownerid_owneridyominame"]).Value;
    System.Console.WriteLine("Owner: " + aggregate9c);
    string aggregate9d = (string)((AliasedValue)c["ownerid_owneridyominame"]).Value;
    System.Console.WriteLine("Owner: " + aggregate9d);
}
```
  
Los ejemplos que aparecen a continuación muestran el grupo siguiente por ejemplos:  
  
- [Agrupar por con entidad vinculada](use-fetchxml-aggregation.md#groupby_linked)
- [Agrupar por año](use-fetchxml-aggregation.md#groupby_year)
- [Agrupar por trimestre](use-fetchxml-aggregation.md#groupby_quarter)
- [Agrupar por mes](use-fetchxml-aggregation.md#groupby_month)
- [Agrupar por semana](use-fetchxml-aggregation.md#groupby_week)  
- [Agrupar por día](use-fetchxml-aggregation.md#groupby_day)  
- [Agrupar varios por](use-fetchxml-aggregation.md#Multiple_GroupBy)  
  
<a name="groupby_linked"></a>

### <a name="group-by-with-linked-entity"></a>Agrupar por con entidad vinculada

El siguiente ejemplo muestra cómo usar el atributo `sum``aggregate` para sumar valores de entidad vinculados.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      groupby2   Aggregate 10
// *****************************************************************************************************************
// Fetch the number of opportunities each manager's direct reports 
// own using a groupby within a link-entity.
string groupby2 = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='name' alias='opportunity_count' aggregate='countcolumn' /> 
       <link-entity name='systemuser' from='systemuserid' to='ownerid'>
           <attribute name='parentsystemuserid' alias='managerid' groupby='true' />
       </link-entity> 
    </entity> 
</fetch>";

EntityCollection groupby2_result = _serviceProxy.RetrieveMultiple(new FetchExpression(groupby2));

foreach (var c in groupby2_result.Entities)
{

      int? aggregate10a = (int?)((AliasedValue)c["opportunity_count"]).Value;
      System.Console.WriteLine("Count of all opportunities: " + aggregate10a + "\n");
}
```
  
<a name="groupby_year"></a>

### <a name="group-by-year"></a>Agrupar por año

Agrupar por, para fechas, usa el valor de día, semana, mes, trimestre o año. El siguiente ejemplo muestra cómo usar el atributo `aggregate` y el atributo `groupby` para agrupar los resultados por año.  
  
 ```csharp

// *****************************************************************************************************************
//                FetchXML      byyear   Aggregate 11           
// *****************************************************************************************************************
// Fetch aggregate information about the opportunities that have 
// been won by year.
string byyear = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='opportunityid' alias='opportunity_count' aggregate='count'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_sum' aggregate='sum'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_avg' aggregate='avg'/> 
       <attribute name='actualclosedate' groupby='true' dategrouping='year' alias='year' />
       <filter type='and'>
           <condition attribute='statecode' operator='eq' value='Won' />
       </filter>
    </entity> 
</fetch>";

EntityCollection byyear_result = _serviceProxy.RetrieveMultiple(new FetchExpression(byyear));

foreach (var c in byyear_result.Entities)
{
    Int32 aggregate11 = (Int32)((AliasedValue)c["year"]).Value;
    System.Console.WriteLine("Year: " + aggregate11);                      
    Int32 aggregate11a = (Int32)((AliasedValue)c["opportunity_count"]).Value;
    System.Console.WriteLine("Count of all opportunities: " + aggregate11a);
    decimal aggregate11b = ((Money)((AliasedValue)c["estimatedvalue_sum"]).Value).Value;
    System.Console.WriteLine("Sum of estimated value of all opportunities: " + aggregate11b);
    decimal aggregate11c = ((Money)((AliasedValue)c["estimatedvalue_avg"]).Value).Value;
    System.Console.WriteLine("Average of estimated value of all opportunities: " + aggregate11c);
    System.Console.WriteLine("----------------------------------------------");
}
```
  
<a name="groupby_quarter"></a>
 
### <a name="group-by-quarter"></a>Agrupar por trimestre

El siguiente ejemplo muestra cómo usar el atributo `aggregate` y el atributo `groupby` para agrupar los resultados por trimestre.  
  
 ```csharp
 // *****************************************************************************************************************
 //                FetchXML      byquarter   Aggregate 12           
 // *****************************************************************************************************************
// Fetch aggregate information about the opportunities that have 
 // been won by quarter.(returns 1-4)
 string byquarter = @" 
 <fetch distinct='false' mapping='logical' aggregate='true'> 
     <entity name='opportunity'> 
        <attribute name='opportunityid' alias='opportunity_count' aggregate='count'/> 
        <attribute name='estimatedvalue' alias='estimatedvalue_sum' aggregate='sum'/> 
        <attribute name='estimatedvalue' alias='estimatedvalue_avg' aggregate='avg'/> 
        <attribute name='actualclosedate' groupby='true' dategrouping='quarter' alias='quarter' />
        <filter type='and'>
            <condition attribute='statecode' operator='eq' value='Won' />
        </filter>
     </entity> 
 </fetch>";

 EntityCollection byquarter_result = _serviceProxy.RetrieveMultiple(new FetchExpression(byquarter));

 foreach (var c in byquarter_result.Entities)
 {
     Int32 aggregate12 = (Int32)((AliasedValue)c["quarter"]).Value;
     System.Console.WriteLine("Quarter: " + aggregate12);
     Int32 aggregate12a = (Int32)((AliasedValue)c["opportunity_count"]).Value;
     System.Console.WriteLine("Count of all opportunities: " + aggregate12a);
     decimal aggregate12b = ((Money)((AliasedValue)c["estimatedvalue_sum"]).Value).Value;
     System.Console.WriteLine("Sum of estimated value of all opportunities: " + aggregate12b);
     decimal aggregate12c = ((Money)((AliasedValue)c["estimatedvalue_avg"]).Value).Value;
     System.Console.WriteLine("Average of estimated value of all opportunities: " + aggregate12c);
     System.Console.WriteLine("----------------------------------------------");
 }
```
  
<a name="groupby_month"></a>

### <a name="group-by-month"></a>Agrupar por mes

El siguiente ejemplo muestra cómo usar el atributo `aggregate` y el atributo `groupby` para agrupar los resultados por mes.  
  
```csharp
// *****************************************************************************************************************
//                FetchXML      bymonth   Aggregate 13           
// *****************************************************************************************************************
// Fetch aggregate information about the opportunities that have 
// been won by month. (returns 1-12)
string bymonth = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='opportunityid' alias='opportunity_count' aggregate='count'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_sum' aggregate='sum'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_avg' aggregate='avg'/> 
       <attribute name='actualclosedate' groupby='true' dategrouping='month' alias='month' />
       <filter type='and'>
           <condition attribute='statecode' operator='eq' value='Won' />
       </filter>
    </entity> 
</fetch>";

EntityCollection bymonth_result = _serviceProxy.RetrieveMultiple(new FetchExpression(bymonth));

foreach (var c in bymonth_result.Entities)
{
    Int32 aggregate13 = (Int32)((AliasedValue)c["month"]).Value;
    System.Console.WriteLine("Month: " + aggregate13);
    Int32 aggregate13a = (Int32)((AliasedValue)c["opportunity_count"]).Value;
    System.Console.WriteLine("Count of all opportunities: " + aggregate13a);
    decimal aggregate13b = ((Money)((AliasedValue)c["estimatedvalue_sum"]).Value).Value;
    System.Console.WriteLine("Sum of estimated value of all opportunities: " + aggregate13b);
    decimal aggregate13c = ((Money)((AliasedValue)c["estimatedvalue_avg"]).Value).Value;
    System.Console.WriteLine("Average of estimated value of all opportunities: " + aggregate13c);
    System.Console.WriteLine("----------------------------------------------");
}
``` 

<a name="groupby_week"></a>

### <a name="group-by-week"></a>Agrupar por semana

El siguiente ejemplo muestra cómo usar el atributo `aggregate` y el atributo `groupby` para agrupar los resultados por semana.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      byweek   Aggregate 14           
// *****************************************************************************************************************
// Fetch aggregate information about the opportunities that have 
// been won by week. (Returns 1-52)
string byweek = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='opportunityid' alias='opportunity_count' aggregate='count'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_sum' aggregate='sum'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_avg' aggregate='avg'/> 
       <attribute name='actualclosedate' groupby='true' dategrouping='week' alias='week' />
       <filter type='and'>
           <condition attribute='statecode' operator='eq' value='Won' />
       </filter>
    </entity> 
</fetch>";

EntityCollection byweek_result = _serviceProxy.RetrieveMultiple(new FetchExpression(byweek));

foreach (var c in byweek_result.Entities)
{
    Int32 aggregate14 = (Int32)((AliasedValue)c["week"]).Value;
    System.Console.WriteLine("Week: " + aggregate14);
    Int32 aggregate14a = (Int32)((AliasedValue)c["opportunity_count"]).Value;
    System.Console.WriteLine("Count of all opportunities: " + aggregate14a);
    decimal aggregate14b = ((Money)((AliasedValue)c["estimatedvalue_sum"]).Value).Value;
    System.Console.WriteLine("Sum of estimated value of all opportunities: " + aggregate14b);
    decimal aggregate14c = ((Money)((AliasedValue)c["estimatedvalue_avg"]).Value).Value;
    System.Console.WriteLine("Average of estimated value of all opportunities: " + aggregate14c);
    System.Console.WriteLine("----------------------------------------------");
}
```
  
<a name="groupby_day"></a>

### <a name="group-by-day"></a>Agrupar por día

 El siguiente ejemplo muestra cómo usar el atributo `aggregate` y el atributo `groupby` para agrupar los resultados por día.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      byday   Aggregate 15           
// *****************************************************************************************************************
// Fetch aggregate information about the opportunities that have 
// been won by day. (Returns 1-31)
string byday = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='opportunityid' alias='opportunity_count' aggregate='count'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_sum' aggregate='sum'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_avg' aggregate='avg'/> 
       <attribute name='actualclosedate' groupby='true' dategrouping='day' alias='day' />
       <filter type='and'>
           <condition attribute='statecode' operator='eq' value='Won' />
       </filter>
    </entity> 
</fetch>";

EntityCollection byday_result = _serviceProxy.RetrieveMultiple(new FetchExpression(byday));

foreach (var c in byday_result.Entities)
{
    Int32 aggregate15 = (Int32)((AliasedValue)c["day"]).Value;
    System.Console.WriteLine("Day: " + aggregate15);
    Int32 aggregate15a = (Int32)((AliasedValue)c["opportunity_count"]).Value;
    System.Console.WriteLine("Count of all opportunities: " + aggregate15a);
    decimal aggregate15b = ((Money)((AliasedValue)c["estimatedvalue_sum"]).Value).Value;
    System.Console.WriteLine("Sum of estimated value of all opportunities: " + aggregate15b);
    decimal aggregate15c = ((Money)((AliasedValue)c["estimatedvalue_avg"]).Value).Value;
    System.Console.WriteLine("Average of estimated value of all opportunities: " + aggregate15c);
    System.Console.WriteLine("----------------------------------------------");
}
```
  
<a name="Multiple_GroupBy"></a>
 
### <a name="multiple-group-by"></a>Agrupar varios por

El siguiente ejemplo muestra cómo usar el atributo `aggregate` y varias cláusulas `groupby`.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      byyrqtr   Aggregate 16           
// *****************************************************************************************************************
// Fetch aggregate information about the opportunities that have 
// been won by year and quarter.
string byyrqtr = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='opportunityid' alias='opportunity_count' aggregate='count'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_sum' aggregate='sum'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_avg' aggregate='avg'/> 
       <attribute name='actualclosedate' groupby='true' dategrouping='quarter' alias='quarter' />
       <attribute name='actualclosedate' groupby='true' dategrouping='year' alias='year' />
       <filter type='and'>
           <condition attribute='statecode' operator='eq' value='Won' />
       </filter>
    </entity> 
</fetch>";

EntityCollection byyrqtr_result = _serviceProxy.RetrieveMultiple(new FetchExpression(byyrqtr));

foreach (var c in byyrqtr_result.Entities)
{
    Int32 aggregate16d = (Int32)((AliasedValue)c["year"]).Value;
    System.Console.WriteLine("Year: " + aggregate16d);
    Int32 aggregate16 = (Int32)((AliasedValue)c["quarter"]).Value;
    System.Console.WriteLine("Quarter: " + aggregate16);
    Int32 aggregate16a = (Int32)((AliasedValue)c["opportunity_count"]).Value;
    System.Console.WriteLine("Count of all opportunities: " + aggregate16a);
    decimal aggregate16b = ((Money)((AliasedValue)c["estimatedvalue_sum"]).Value).Value;
    System.Console.WriteLine("Sum of estimated value of all opportunities: " + aggregate16b);
    decimal aggregate16c = ((Money)((AliasedValue)c["estimatedvalue_avg"]).Value).Value;
    System.Console.WriteLine("Average of estimated value of all opportunities: " + aggregate16c);
    System.Console.WriteLine("----------------------------------------------");
}
```
  
<a name="orderby_aggregate"></a>

## <a name="order-by"></a>Ordenar por

El siguiente ejemplo muestra cómo usar el atributo `aggregate` y varias cláusulas `orderby`.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      byyrqtr2   Aggregate 17           
// *****************************************************************************************************************
// Specify the result order for the previous sample.  Order by year, then quarter.
string byyrqtr2 = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='opportunityid' alias='opportunity_count' aggregate='count'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_sum' aggregate='sum'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_avg' aggregate='avg'/> 
       <attribute name='actualclosedate' groupby='true' dategrouping='quarter' alias='quarter' />
       <attribute name='actualclosedate' groupby='true' dategrouping='year' alias='year' />
       <order alias='year' descending='false' />
       <order alias='quarter' descending='false' />
       <filter type='and'>
           <condition attribute='statecode' operator='eq' value='Won' />
       </filter>
    </entity> 
</fetch>";

EntityCollection byyrqtr2_result = _serviceProxy.RetrieveMultiple(new FetchExpression(byyrqtr2));

foreach (var c in byyrqtr2_result.Entities)
{
    Int32 aggregate17 = (Int32)((AliasedValue)c["quarter"]).Value;
    System.Console.WriteLine("Quarter: " + aggregate17);
    Int32 aggregate17d = (Int32)((AliasedValue)c["year"]).Value;
    System.Console.WriteLine("Year: " + aggregate17d);
    Int32 aggregate17a = (Int32)((AliasedValue)c["opportunity_count"]).Value;
    System.Console.WriteLine("Count of all opportunities: " + aggregate17a);
    decimal aggregate17b = ((Money)((AliasedValue)c["estimatedvalue_sum"]).Value).Value;
    System.Console.WriteLine("Sum of estimated value of all opportunities: " + aggregate17b);
    decimal aggregate17c = ((Money)((AliasedValue)c["estimatedvalue_avg"]).Value).Value;
    System.Console.WriteLine("Average of estimated value of all opportunities: " + aggregate17c);
    System.Console.WriteLine("----------------------------------------------");
}
```
  
### <a name="see-also"></a>Vea también

[Paginar grandes conjuntos de resultados con FetchXML](org-service/page-large-result-sets-with-fetchxml.md)<br />
[Esquema de Fetch XML](fetchxml-schema.md)<br />
<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*><br />
<xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest><br />
<xref:Microsoft.Xrm.Sdk.Query.FetchExpression>