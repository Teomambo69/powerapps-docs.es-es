---
title: Crear consultas con LINQ (consulta integrada del lenguaje .NET) (Common Data Service) | Microsoft Docs
description: Lea cómo usar la consulta integrada del lenguaje .NET (LINQ) para escribir consultas en Common Data Service
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
# <a name="build-queries-with-linq-net-language-integrated-query"></a>Crear consultas con LINQ (consulta integrada del lenguaje .NET)

Puede usar la consulta integrada del lenguaje .NET (LINQ) para escribir consultas en Common Data Service. Puede utilizar la clase <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext> o una clase derivada creada por la herramienta CrmSvcUtil para escribir consultas de [LINQ](https://msdn.microsoft.com/library/bb397897.aspx) que accedan al extremo de SOAP (Organization.svc). La clase <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext> contiene un proveedor de consultas LINQ subyacente que convierte consultas de LINQ de sintaxis Visual C# o Visual Basic .NET a la API de consulta utilizada por Common Data Service.  
  
 Cuando utiliza clases de programación enlazadas en tiempo puede generar una clase derivada de la clase <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext> si especifica el nombre de la clase que utiliza el parámetro **servicecontextname** cuando se utiliza la herramienta de generación de código (CrmSvcUtil.exe). El uso de esta clase permite hacer referencia a un conjunto de entidades [IQueryable](https://msdn.microsoft.com/library/system.linq.iqueryable.aspx) mediante el patrón `<entity schema name>+Set`, por ejemplo **AccountSet** para hacer referencia a la colección de registros de entidades de `Account`. Todas las muestras de servicios web de Common Data Service usan **ServiceContext** como nombre para esta clase, pero es posible que su código utilice un nombre diferente. Más información: [Crear clases de entidad con enlace en tiempo de compilación con la herramienta de generación de código (CrmSvcUtil.exe)](/dynamics365/customer-engagement/developer/org-service/create-early-bound-entity-classes-code-generation-tool.md) 
  
## <a name="in-this-section"></a>En esta sección  
 [Usar LINQ para crear una consulta](use-linq-construct-query.md)  
  
 [Usar clase de entidad de enlace en tiempo de ejecución con una consulta LINQ](use-late-bound-entity-class-linq-query.md)  
  
 [Usar atributos de búsqueda de entidades con LINQ](order-results-entity-attributes-linq.md)  
  
 [Ordenar resultados mediante atributos de entidad con LINQ](/dynamics365/customer-engagement/developer/org-service/order-results-entity-attributes-linq)  
  
 [Paginar grandes conjuntos de resultados con LINQ](/dynamics365/customer-engagement/developer/org-service/page-large-result-sets-linq)  
  
 [Ejemplos de la consulta LINQ](/dynamics365/customer-engagement/developer/org-service/linq-query-examples)  
  
 [Ejemplo: Crear una consulta LINQ](/dynamics365/customer-engagement/developer/org-service/sample-create-linq-query)  
  
 [Ejemplo: Ejemplos de consulta LINQ](/dynamics365/customer-engagement/developer/org-service/sample-complex-linq-queries)  
  
 [Ejemplo: RetrieveMultiple con operadores de condición mediante LINQ](/dynamics365/customer-engagement/developer/org-service/sample-retrieve-multiple-with-condition-operators-using-linq)  
  
 [Ejemplo: Más ejemplos de consulta LINQ](/dynamics365/customer-engagement/developer/org-service/sample-more-linq-query-examples)  
  
 [Ejemplo: Usar LINQ con enlace en tiempo de ejecución](/dynamics365/customer-engagement/developer/org-service/sample-create-linq-query-late-binding)