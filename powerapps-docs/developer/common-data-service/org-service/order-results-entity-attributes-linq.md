---
title: Ordenar resultados mediante atributos de entidad con LINQ (Common Data Service) | Microsoft Docs
description: Lea cómo puede usar los atributos de búsqueda o de OptionSet (lista desplegable) para ordenar los resultados de una consulta LINQ.
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
ms.openlocfilehash: e665e66b4ec138532dd5476561b6cc0c7becc330
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156028"
---
# <a name="order-results-using-entity-attributes-with-linq"></a>Ordenar resultados mediante atributos de entidad con LINQ

En Common Data Service (Common Data Service) para aplicaciones, puede usar los atributos de búsqueda o de OptionSet (lista desplegable) para ordenar los resultados de una consulta LINQ. Este tema muestra varios ejemplos de este tipo de consulta.  
  
## <a name="using-a-lookup-value-to-order-by"></a>Uso de un valor de búsqueda para ordenar  

El siguiente ejemplo muestra el uso del atributo de búsqueda `PrimaryContactId` en una cláusula `Order By`.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
 var query_orderbylookup = from a in svcContext.AccountSet
                           where a.Address1_Name == "Contoso Pharmaceuticals"
                           orderby a.PrimaryContactId
                           select new
                           {
                            a.Name,
                            a.Address1_City
                           };
 foreach (var a in query_orderbylookup)
 {
  System.Console.WriteLine(a.Name + " " + a.Address1_City);
 }
}

```
  
## <a name="using-a-picklist-to-order-by"></a>Uso de una lista desplegable para ordenar  

El siguiente ejemplo muestra el uso de un valor de búsqueda para ordenar.  
  
```csharp

using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
 var query_orderbypicklist = from c in svcContext.ContactSet
                             where c.LastName != "Parker" &&
                             c.AccountRoleCode != null
                             orderby c.AccountRoleCode, c.FirstName
                             select new
                             {
                              AccountRole = c.FormattedValues["accountrolecode"],
                              c.FirstName,
                              c.LastName
                             };
 foreach (var c in query_orderbypicklist)
 {
  System.Console.WriteLine(c.AccountRole + " " +
   c.FirstName + " " + c.LastName);
 }
}
```
  
### <a name="see-also"></a>Vea también  
 [Crear consultas con LINQ (consulta integrada del lenguaje .NET)](build-queries-with-linq-net-language-integrated-query.md)   
 [Paginar grandes conjuntos de resultados con LINQ](page-large-result-sets-linq.md)