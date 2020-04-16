---
title: Fecha fiscal y operadores de consultas de fecha y hora más antiguo en FetchXML (Common Data Service) | Microsoft Docs
description: Aprenda a usar operadores condicionales de fecha fiscal de FetchXML y cláusulas &quot;más antiguo de&quot; para los valores de fecha y hora
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
ms.openlocfilehash: 11fae9bca37f2a38d2918260adc7361b7088e1e5
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155184"
---
# <a name="fiscal-date-and-older-than-datetime-query-operators-in-fetchxml"></a>Fecha fiscal y operadores de consultas de fecha y hora más antiguo de en FetchXML

Una consulta FetchXML en Common Data Service puede usar valores de fecha fiscal especiales y cláusulas *más antiguo de* para valores de fecha y hora en consultas. Por ejemplo, una consulta FetchXML puede buscar todos los pedidos completados en el último mes fiscal o casos urgentes con alta gravedad que tengan más de 15 minutos.  
  
> [!NOTE]
>  Para todas las consultas de fechas fiscales, la consulta FetchXML usa la configuración del año fiscal de la organización.  
  
<a name="FiscalDate"></a>   
## <a name="using-fetchxml-fiscal-date-conditional-operators"></a>Utilizar operadores condicionales de fecha fiscal FetchXML  
 En el siguiente ejemplo se muestra una expresión FetchXML que busca todos los pedidos completados en el último período fiscal de acuerdo con la configuración del año fiscal de la organización. Por ejemplo, si la organización usa meses fiscales, la consulta devolverá los pedidos completados durante el último mes fiscal. Si la organización usa trimestres fiscales, la consulta devolverá los pedidos completados durante el último trimestre fiscal. Si la organización usa semestres fiscales, se obtendrán los pedidos completados durante el último semestre fiscal.  
  
```xml  
<fetch>  
 <entity name="order">  
  <attribute name="name"/>  
  <filter type="and">  
   <condition attribute="datefulfilled" operator="last-fiscal-period"/>  
  </filter>  
 </entity>  
</fetch>  
```  
  
 En el siguiente ejemplo se muestra una expresión FetchXML que busca todas las cuentas creadas durante el año fiscal 2013.  
  
```xml  
<fetch>  
 <entity name="account">  
  <attribute name="name"/>  
  <filter type="and">  
   <condition attribute="createdon" operator="in-fiscal-year" value="2013"/>  
  </filter>  
 </entity>  
</fetch>  
```  
  
 El siguiente ejemplo muestra una expresión FetchXML que busca todas las oportunidades con una fecha de cierre estimada en los tres años fiscales próximos, en función de la configuración del año fiscal de la organización. El valor de `x` se especifica en el atributo de valor de la etiqueta de la condición.  
  
```xml  
<fetch>  
 <entity name="opportunity">  
  <attribute name="name"/>  
  <filter type="and">  
   <condition attribute="estimatedclosedate" operator="next-x-fiscal-years" value="3"/>  
  </filter>  
 </entity>  
</fetch>  
```  
  
 En el siguiente ejemplo se muestra una expresión FetchXML que busca todos los pedidos completados en el tercer período de cualquier año fiscal de acuerdo con la configuración del año fiscal de la organización. El valor del período fiscal se especifica en el atributo de valor de la etiqueta de la condición. Si la organización usa meses fiscales, la consulta ofrecerá resultados a partir del mes número tres. Si la organización usa trimestres fiscales, la consulta ofrecerá resultados a partir del trimestre número tres. Si la organización usa semestres fiscales, no se mostrará ningún resultado; solo hay dos semestres, y el valor proporcionado está por lo tanto fuera de rango.  
  
```xml  
<fetch>  
 <entity name="order">  
  <attribute name="name"/>  
  <filter type="and">  
   <condition attribute="datefulfilled" operator="in-fiscal-period" value="3"/>  
  </filter>  
 </entity>  
</fetch>  
```  
  
 En el siguiente ejemplo se muestra una expresión FetchXML que busca todos los pedidos completados en el tercer período del año fiscal 2013 de acuerdo con la configuración del año fiscal de la organización. Si la organización usa meses fiscales, la consulta ofrecerá resultados a partir del mes número tres. Si la organización usa trimestres fiscales, la consulta ofrecerá resultados a partir del trimestre número tres. Si la organización usa semestres fiscales, no se mostrará ningún resultado; solo hay dos semestres, y el valor proporcionado está por lo tanto fuera de rango.  
  
```xml  
<fetch>  
 <entity name="order">  
  <attribute name="name"/>  
  <filter type="and">  
   <condition attribute="datefulfilled" operator="in-fiscal-period-and-year">  
    <value>3</value>  
    <value>2013</value>  
   </condition>  
  </filter>  
 </entity>  
</fetch>  
```  
  
 El siguiente ejemplo muestra una expresión de agregación FetchXML que suma la cantidad total de pedidos completados y agrupa el resultado por semestre y año fiscal.  
  
```xml  
<fetch aggregate="true">  
 <entity name="order">  
  <attribute name="totalamount" aggregate="sum" alias="total"/>  
  <attribute name="datefulfilled" groupby="true" dategrouping="fiscal-period"/>  
 </entity>  
</fetch>  
```  
  
<a name="OlderThan"></a>   
## <a name="using-older-than-clauses-for-date-and-time-values"></a>Uso de cláusulas "más antiguo de" para valores de fecha y hora  
 El siguiente ejemplo muestra un FetchXML que busca incidentes que tienen más de 30 minutos.  
  
```xml  
<fetch>  
  <entity name="incident">  
    <attribute name="title" />  
    <attribute name="ticketnumber" />  
    <attribute name="createdon" />  
    <attribute name="incidentid" />  
    <filter type="and">  
      <condition attribute="createdon" operator="olderthan-x-minutes" value="30" />  
    </filter>  
  </entity>  
</fetch>  
```  
  
 Use la siguiente sintaxis para especificar varias cláusulas *más antiguo de* en una expresión FetchXML.  
  
 Más antiguo de X minutos  
 ```xml  
<condition attribute="<AttributeName>" operator="olderthan-x-minutes" value="<VALUE>" />  
```  
  
> [!NOTE]
>  Esta cláusula no es compatible para los atributos de fecha y hora con el comportamiento de `DateOnly` . Más información: [Operadores de consulta de fecha y hora no admitidos en el comportamiento DateOnly](/dynamics365/customer-engagement/developer/behavior-format-date-time-attribute#date-and-time-query-operators-not-supported-for-dateonly-behavior)
  
 Más antiguo de X horas  
 ```xml  
<condition attribute="<AttributeName>" operator="olderthan-x-hours" value="<VALUE>" />  
```  
  
> [!NOTE]
>  Esta cláusula no es compatible para los atributos de fecha y hora con el comportamiento de `DateOnly` . Más información: [Operadores de consulta de fecha y hora no admitidos en el comportamiento DateOnly](/dynamics365/customer-engagement/developer/behavior-format-date-time-attribute#date-and-time-query-operators-not-supported-for-dateonly-behavior)  
  
 Más antiguo de X días  
 ```xml  
<condition attribute="<AttributeName>" operator="olderthan-x-days" value="<VALUE>" />  
```  
  
 Más antiguo de X semanas  
 ```xml  
<condition attribute="<AttributeName>" operator="olderthan-x-weeks" value="<VALUE>" />  
```  
  
 Más antiguo de X meses  
 ```xml  
<condition attribute="<AttributeName>" operator="olderthan-x-months" value="<VALUE>" />  
```  
  
 Más antiguo de X años  
 ```xml  
<condition attribute="<AttributeName>" operator="olderthan-x-years" value="<VALUE>" />  
```

### <a name="see-also"></a>Vea también  
 [Crear consultas para recuperar datos](/dynamics365/customer-engagement/developer/org-service/retrieve-data-queries-sdk-assemblies)   
 [Crear consultas con FetchXML](/dynamics365/customer-engagement/developer/org-service/build-queries-fetchxml)   
 [Use una combinación externa izquierda en FetchXML para consultar los registros "no en"](/dynamics365/customer-engagement/developer/use-left-outer-join-fetchxml-query-records-not-in)
