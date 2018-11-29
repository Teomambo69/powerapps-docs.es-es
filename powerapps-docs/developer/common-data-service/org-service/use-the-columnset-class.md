---
title: Usar la clase ColumnSet (Common Data Service para aplicaciones) | Microsoft Docs
description: <Description>
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
# <a name="use-the-columnset-class"></a>Use la clase ColumnSet

En Common Data Service para aplicaciones, puede usar la clase <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> para especificar qué atributos se devuelven de una consulta definida mediante las clases <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> y <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute>. También es un parámetro para el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*> y se usa como propiedad en varias clases de solicitudes de mensaje que devuelven datos en una <xref:Microsoft.Xrm.Sdk.EntityCollection>.

> [!NOTE]
> La clase <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> tiene una propiedad <xref:Microsoft.Xrm.Sdk.Query.ColumnSet.AllColumns> que especifica que todas las columnas de la entidad deben ser devueltas. Como práctica recomendada del rendimiento, no debería utilizarla para código de producción. Más información: [No recuperar la entidad todas las columnas mediante API de consulta](/dynamics365/customer-engagement/guidance/data/retrieve-specific-columns-entity-via-query-apis)

El siguiente ejemplo de código muestra cómo usar la clase `ColumnSet` para especificar qué atributos se devolverán de una expresión de consulta.  
  
```csharp  
QueryExpression contactquery = new QueryExpression   
{  
   EntityName="contact",  
   ColumnSet = new ColumnSet("firstname", "lastname", "contactid")   
};  
```  
  
### <a name="see-also"></a>Vea también  

[Usar la clase QueryExpression](use-queryexpression-class.md)<br />
[Crear consultas con QueryExpression](build-queries-with-queryexpression.md)<br />
[Usar la clase ConditionExpression](use-conditionexpression-class.md)<br />Clase de  
<xref:Microsoft.Xrm.Sdk.Query.QueryExpression> <br />
Clase de <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> <br />