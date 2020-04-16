---
title: Paginar grandes conjuntos de resultados con LINQ (Common Data Service) | Microsoft Docs
description: Lea cómo puede paginar los resultados de una consulta de gran tamaño de Language-Integrated Query (LINQ) de .NET usando los operadores Take y Skip
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
ms.openlocfilehash: 324f2e275dd9ec2b2d8aceaafe0a076488ca4bb7
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156000"
---
# <a name="page-large-result-sets-with-linq"></a>Páginar grandes conjuntos de resultados con LINQ

En Common Data Service puede paginar los resultados de una consulta de gran tamaño de Language-Integrated Query (LINQ) de .NET usando los operadores `Take` y `Skip`. El operador `Take` recupera un número determinado de resultados y el operador `Skip` omite un número determinado de resultados.  
  
## <a name="linq-paging-example"></a>Ejemplo de paginación LINQ  

En el siguiente ejemplo se muestra cómo paginar los resultados de una consulta LINQ con los operadores `Take` y `Skip`:  
  
```csharp
int pageSize = 5;

var accountsByPage = (from a in svcContext.AccountSet
                      select new Account
                      {
                       Name = a.Name,
                      });
System.Console.WriteLine("Skip 10 accounts, then Take 5 accounts");
System.Console.WriteLine("======================================");
foreach (var a in accountsByPage.Skip(2 * pageSize).Take(pageSize))
{
 System.Console.WriteLine(a.Name);
}

```
  
### <a name="see-also"></a>Vea también  
 [Crear consultas con LINQ (consulta integrada del lenguaje .NET)](build-queries-with-linq-net-language-integrated-query.md)   
 [Ejemplos de la consulta LINQ](linq-query-examples.md)