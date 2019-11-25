---
title: Usar funciones de la API web (Common Data Service)| Microsoft Docs
description: Las funciones son operaciones reutilizables que se utilizan con una solicitud GET para recuperar datos de Common Data Service
ms.custom: ''
ms.date: 09/05/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: c6de9c12-e8e3-4ed5-a6ed-18ade572065f
caps.latest.revision: 45
author: JimDaly
ms.author: jdaly
ms.reviewer: susikka
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 46d9db977c1db3dcd336ed6eda0f30228468a529
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749496"
---
# <a name="use-web-api-functions"></a>Usar funciones de la API web

Las acciones y funciones representan operaciones reutilizables que puede realizar mediante la API web. Existen dos tipos de funciones en la API web:  
  
**Funciones**  
Use una solicitud `GET` con las funciones que aparecen en <xref:Microsoft.Dynamics.CRM.FunctionIndex> para realizar operaciones que tienen efectos secundarios. Estas capacidades recuperan normalmente datos. Devuelven una colección o un tipo complejo. Cada una de estas funciones tiene un mensaje correspondiente en el servicio de la organización.  
  
**Funciones de consulta**  
Use las funciones enumeradas en <xref:Microsoft.Dynamics.CRM.QueryFunctionIndex> para evaluar propiedades y valores en la creación de una consulta. Cada una de estas funciones tiene un valor <xref:Microsoft.Xrm.Sdk.Query.ConditionOperator> correspondiente.  
  
<a name="bkmk_passParametersToFunctions"></a>

## <a name="passing-parameters-to-a-function"></a>Paso de parámetros a una función
  
Para las funciones que requieren parámetros, se recomienda pasar los valores mediante parámetros. Por ejemplo, cuando usa la <xref href="Microsoft.Dynamics.CRM.GetTimeZoneCodeByLocalizedName?text=GetTimeZoneCodeByLocalizedName Function" />, debe incluir los valores de parámetro `LocalizedStandardName` y `LocaleId`. Por tanto, puede usar la siguiente sintaxis en línea que se indica a continuación.  
  
```http
GET [Organization URI]/api/data/v9.0/GetTimeZoneCodeByLocalizedName(LocalizedStandardName='Pacific Standard Time',LocaleId=1033)  
```  
  
Sin embargo, hay un problema pendiente con el uso de valores de DateTimeOffset con la sintaxis en línea, como se explica en el artículo siguiente: [DateTimeOffset como parámetro de consulta #204.](https://github.com/OData/WebApi/issues/204).  
  
Por lo tanto, se recomienda pasar los valores como parámetros como se muestra en el siguiente código de ejemplo. Si usa esta recomendación, puede evitar el problema pendiente que se aplica a `DateTimeOffset`.  
  
```http
GET [Organization URI]/api/data/v9.0/GetTimeZoneCodeByLocalizedName(LocalizedStandardName=@p1,LocaleId=@p2)?@p1='Pacific Standard Time'&@p2=1033  
```  
  
Los alias de parámetros también permiten reusar valores de parámetro para reducir la longitud total de la URL cuando el valor de parámetro se utiliza varias veces.  
  
<a name="bkmk_passCrmEntityReference"></a>

## <a name="pass-reference-to-an-entity-to-a-function"></a>Pasar referencia a una entidad para una función

Determinadas funciones requerirán el pase de una referencia a una entidad existente. Por ejemplo, las siguientes funciones tienen un parámetro que requiere un <xref href="Microsoft.Dynamics.CRM.crmbaseentity?text=crmbaseentity EntityType" />:  
  
||||  
|-|-|-|  
|<xref href="Microsoft.Dynamics.CRM.CalculateRollupField?text=CalculateRollupField Function" />|<xref href="Microsoft.Dynamics.CRM.IncrementKnowledgeArticleViewCount?text=IncrementKnowledgeArticleViewCount Function" />|<xref href="Microsoft.Dynamics.CRM.InitializeFrom?text=InitializeFrom Function" />|  
|<xref href="Microsoft.Dynamics.CRM.IsValidStateTransition?text=IsValidStateTransition Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveDuplicates?text=RetrieveDuplicates Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveLocLabels?text=RetrieveLocLabels Function" />|  
|<xref href="Microsoft.Dynamics.CRM.RetrievePrincipalAccess?text=RetrievePrincipalAccess Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveRecordWall?text=RetrieveRecordWall Function" />|<xref href="Microsoft.Dynamics.CRM.ValidateRecurrenceRule?text=ValidateRecurrenceRule Function" />|  
  
Al pasar una referencia a una entidad existente, use la anotación `@odata.id` para el URI para la entidad. Por ejemplo, si usa <xref href="Microsoft.Dynamics.CRM.RetrievePrincipalAccess?text=RetrievePrincipalAccess Function" />, puede usar el siguiente URI para especificar el acceso de recuperación a un contacto específico:  
  
```http
GET [Organization URI]/api/data/v9.0/systemusers(af9b3cf6-f654-4cd9-97a6-cf9526662797)/Microsoft.Dynamics.CRM.RetrievePrincipalAccess(Target=@tid)?@tid={'@odata.id':'contacts(9f3162f6-804a-e611-80d1-00155d4333fa)'}
```  
  
La anotación `@odata.id` puede ser el URI completo, pero un URI relativo también funciona.  
  
<a name="bkmk_boundAndUnboundFunctions"></a>
 
## <a name="bound-and-unbound-functions"></a>Funciones enlazadas y sin enlazar

Únicamente las funciones que se encuentran en <xref:Microsoft.Dynamics.CRM.FunctionIndex> pueden estar enlazadas. Las funciones de consulta nunca están enlazadas.  
  
<a name="bkmk_boundFunctions"></a>

### <a name="bound-functions"></a>Funciones enlazadas

En el [Documento de metadatos CSDL](web-api-types-operations.md#bkmk_csdl), cuando un elemento `Function` representa una función enlazada, tiene un atributo `IsBound` con el valor `true`. El primer elemento `Parameter` definido en la función representa la entidad a la que está enlazada la función. Cuando el atributo `Type` del parámetro es una colección, la función está enlazada a una colección de entidades. Por ejemplo, lo siguiente es la definición de la <xref href="Microsoft.Dynamics.CRM.CalculateTotalTimeIncident?text=CalculateTotalTimeIncident Function" /> y <xref href="Microsoft.Dynamics.CRM.CalculateTotalTimeIncidentResponse?text=CalculateTotalTimeIncidentResponse ComplexType" /> en CSDL.  
  
```xml
<ComplexType Name="CalculateTotalTimeIncidentResponse">  
  <Property Name="TotalTime" Type="Edm.Int64" Nullable="false" />  
</ComplexType>  
<Function Name="CalculateTotalTimeIncident" IsBound="true">  
  <Parameter Name="entity" Type="mscrm.incident" Nullable="false" />  
  <ReturnType Type="mscrm.CalculateTotalTimeIncidentResponse" Nullable="false" />  
</Function>  
```  
  
Esta función enlazada es equivalente a la <xref:Microsoft.Crm.Sdk.Messages.CalculateTotalTimeIncidentRequest> usada por el servicio de organización. En API web esta función está enlazada a <xref href="Microsoft.Dynamics.CRM.incident?text=incident EntityType" />, que representa a la propiedad <xref:Microsoft.Crm.Sdk.Messages.CalculateTotalTimeIncidentRequest>.<xref:Microsoft.Crm.Sdk.Messages.CalculateTotalTimeIncidentRequest.IncidentId> . En lugar de devolver una <xref:Microsoft.Crm.Sdk.Messages.CalculateTotalTimeIncidentResponse>, esta función devuelve un <xref href="Microsoft.Dynamics.CRM.CalculateTotalTimeIncidentResponse?text=CalculateTotalTimeIncidentResponse ComplexType" />. Cuando una función devuelve un tipo complejo, su definición aparece directamente por encima de la definición de la función en CSDL.  
  
Para invocar a una función sin enlazar, anexe el nombre completo de la función a la URL e incluya cualquier parámetro con nombre entre paréntesis tras el nombre de la función. El nombre completo de la función incluye el espacio de nombres `Microsoft.Dynamics.CRM`. Las funciones que no está enlazadas no deben usar el nombre completo.  
  
> [!IMPORTANT]
>  Una función enlazada debe llamarse mediante un URI para establecer el primer valor de parámetro. No puede establecerlo como un valor de parámetro con nombre.  
  
La siguiente ilustración muestra un ejemplo utilizando la <xref href="Microsoft.Dynamics.CRM.CalculateTotalTimeIncident?text=CalculateTotalTimeIncident Function" />, que está enlazada a la entidad de `incident`.  
  
 **Solicitud**

```http
GET [Organization URI]/api/data/v9.0/incidents(90427858-7a77-e511-80d4-00155d2a68d1)/Microsoft.Dynamics.CRM.CalculateTotalTimeIncident() HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Respuesta**
 
```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
  "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.CalculateTotalTimeIncidentResponse","TotalTime":30  
}  
```  
  
<a name="bkmk_unboundFunctions"></a>
 
### <a name="unbound-functions"></a>Funciones sin enlazar

La <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /> no está enlazado a una entidad. Se define en CSDL sin un atributo `IsBound`.  
  
```xml
<ComplexType Name="WhoAmIResponse">  
  <Property Name="BusinessUnitId" Type="Edm.Guid" Nullable="false" />  
  <Property Name="UserId" Type="Edm.Guid" Nullable="false" />  
  <Property Name="OrganizationId" Type="Edm.Guid" Nullable="false" />  
</ComplexType>  
<Function Name="WhoAmI">  
  <ReturnType Type="mscrm.WhoAmIResponse" Nullable="false" />  
</Function>  
```  
  
Esta función corresponde a la <xref:Microsoft.Crm.Sdk.Messages.WhoAmIRequest> y devuelve un <xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" /> que corresponde al <xref:Microsoft.Crm.Sdk.Messages.WhoAmIResponse> usado por el servicio de la organización. Esta función no tiene ningún parámetro.  
  
Al invocar una función sin enlazar, use únicamente el nombre de función que se muestra en el siguiente ejemplo.  
  
 **Solicitud**

```http
GET [Organization URI]/api/data/v9.0/WhoAmI() HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Respuesta**

```http
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
{  
 "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.WhoAmIResponse",  
 "BusinessUnitId": "ded5a64f-f06d-e511-80d0-00155db07cb1",  
 "UserId": "d96e9f55-f06d-e511-80d0-00155db07cb1",  
 "OrganizationId": "4faf1f34-f06d-e511-80d0-00155db07cb1"  
}  
```  
  
<a name="bkmk_composeQueryWithFunctions"></a>

## <a name="compose-a-query-with-functions"></a>Crear una consulta con funciones

Hay dos formas de utilizar las funciones para controlar los datos devueltos con consultas. Algunas funciones permiten el control de las columnas o condiciones que devuelven y se usan funciones de consulta para evaluar condiciones en una consulta.  
  
<a name="bkmk_composableFunctions"></a>
  
### <a name="composable-functions"></a>Funciones que admiten composición

Algunas funciones que figuran en <xref:Microsoft.Dynamics.CRM.FunctionIndex> devolverán una colección de entidades. Un subconjunto de estas funciones *admite composición*, lo que significa que puede incluir una opción adicional de consulta del sistema `$select` o `$filter` para controlar qué columnas se devuelven en los resultados. Estas funciones tienen un atributo `IsComposable` en CSDL. Cada una de estas funciones tiene un mensaje de acompañamiento manual en el servicio de la organización que acepta un parámetro de tipo <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> o <xref:Microsoft.Xrm.Sdk.Query.QueryBase>. Las opciones de consulta del sistema OData ofrecen la misma funcionalidad, por lo que estas funciones no tienen los mismos parámetros que sus mensajes de acompañamiento en el servicio de la organización. La siguiente tabla muestra una lista de esas funciones que admiten composición de esta versión.  
  
||||  
|-|-|-|  
|<xref href="Microsoft.Dynamics.CRM.GetDefaultPriceLevel?text=GetDefaultPriceLevel Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveAllChildUsersSystemUser?text=RetrieveAllChildUsersSystemUser Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveBusinessHierarchyBusinessUnit?text=RetrieveBusinessHierarchyBusinessUnit Function" />|  
|<xref href="Microsoft.Dynamics.CRM.RetrieveByGroupResource?text=RetrieveByGroupResource Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveByResourceResourceGroup?text=RetrieveByResourceResourceGroup Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveMembersBulkOperation?text=RetrieveMembersBulkOperation Function" />|  
|<xref href="Microsoft.Dynamics.CRM.RetrieveParentGroupsResourceGroup?text=RetrieveParentGroupsResourceGroup Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveSubGroupsResourceGroup?text=RetrieveSubGroupsResourceGroup Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveUnpublishedMultiple?text=RetrieveUnpublishedMultiple Function" />|  
|<xref href="Microsoft.Dynamics.CRM.SearchByBodyKbArticle?text=SearchByBodyKbArticle Function" />|<xref href="Microsoft.Dynamics.CRM.SearchByKeywordsKbArticle?text=SearchByKeywordsKbArticle Function" />|<xref href="Microsoft.Dynamics.CRM.SearchByTitleKbArticle?text=SearchByTitleKbArticle Function" />|  
  
<a name="bkmk_queryevaluationFunctions"></a>
  
### <a name="query-functions"></a>Funciones de consulta

Las funciones enumeradas en <xref:Microsoft.Dynamics.CRM.QueryFunctionIndex> se proporcionan para ser utilizadas para crear una consulta. Estas funciones se pueden usar de forma similar a las [Funciones de consulta integradas](query-data-web-api.md#bkmk_buildInQueryFunctions), aunque hay algunas diferencias importantes.  
  
Debe usar el nombre completo de la función e incluir los nombres de los parámetros. En el siguiente ejemplo se muestra cómo usar la <xref href="Microsoft.Dynamics.CRM.LastXHours?text=LastXHours Function" /> para devolver todas las entidades de cuenta modificadas durante las últimas 12 horas.  
  
```http
GET [Organization URI]/api/data/v9.0/accounts?$select=name,accountnumber&$filter=Microsoft.Dynamics.CRM.LastXHours(PropertyName=@p1,PropertyValue=@p2)&@p1='modifiedon'&@p2=12  
```  

#### <a name="limitations-of-query-functions"></a>Limitaciones de las funciones de consulta

Una de las limitaciones de funciones de consulta es que no puede usar el operador `not` para negar funciones de consulta.

Por ejemplo, la consulta siguiente utilizando <xref href="Microsoft.Dynamics.CRM.EqualUserId?text=EqualUserId Function" /> producirá el error: `Not operator along with the Custom Named Condition operators is not allowed`.

```http
GET [Organization URI]/api/data/v9.1/systemusers?$select=fullname,systemuserid&$filter=not Microsoft.Dynamics.CRM.EqualUserId(PropertyName=@p1)&@p1='systemuserid'
```
Varias funciones de consulta tienen una función de consulta negada complementaria. Por ejemplo, puede usar la <xref href="Microsoft.Dynamics.CRM.NotEqualUserId?text=NotEqualUserId Function" />. La consulta siguiente devolverá los resultados esperados:

```http
GET [Organization URI]/api/data/v9.1/systemusers?$select=fullname,systemuserid&$filter=Microsoft.Dynamics.CRM.NotEqualUserId(PropertyName=@p1)&@p1='systemuserid'
```

Otras funciones de consulta se pueden negar de distintas formas. Por ejemplo, en lugar de intentar negar la <xref href="Microsoft.Dynamics.CRM.Last7Days?text=Last7Days Function" /> de este modo (el que producirá el mismo error que se indicó anteriormente):

```http
GET [Organization URI]/api/data/v9.1/accounts?$select=name&$filter=not Microsoft.Dynamics.CRM.Last7Days(PropertyName=@p1)&@p1='createdon'
```
Utilice la <xref href="Microsoft.Dynamics.CRM.OlderThanXDays?text=OlderThanXDays Function" /> de este modo:

```http
GET [Organization URI]/api/data/v9.1/accounts?$select=name&$filter=Microsoft.Dynamics.CRM.OlderThanXDays(PropertyName=@p1,PropertyValue=@p2)&@p1='createdon'&@p2=7
```

### <a name="see-also"></a>Vea también

[Ejemplo de funciones y acciones de la API web (C#)](samples/functions-actions-csharp.md)<br />
[Ejemplo de funciones y acciones de la API web (JavaScript del lado del cliente)](samples/functions-actions-client-side-javascript.md)<br />
[Realizar operaciones mediante la API web](perform-operations-web-api.md)<br />
[Componer solicitudes HTTP y administrar errores](compose-http-requests-handle-errors.md)<br />
[Consultar datos utilizando la API web](query-data-web-api.md)<br />
[Cree una entidad usando API web](create-entity-web-api.md)<br />
[Recuperar una entidad usando API web](retrieve-entity-using-web-api.md)<br />
[Actualizar y eliminar entidades mediante la API web](update-delete-entities-using-web-api.md)<br />
[Asociar y anular la asociación de entidades mediante la API web](associate-disassociate-entities-using-web-api.md)<br />
[Usar acciones de la API web](use-web-api-actions.md)<br />
[Ejecute las operaciones por lotes mediante API web](execute-batch-operations-using-web-api.md)<br />
[Suplantar a otro usuario utilizando la API web](impersonate-another-user-web-api.md)<br />
[Realizar operaciones condicionales mediante la API web](perform-conditional-operations-using-web-api.md)
