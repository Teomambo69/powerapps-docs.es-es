---
title: Ejemplos de operaciones de datos de la API web (Common Data Service) | Microsoft Docs
description: El SDK de Common Data Service proporciona una matriz de los ejemplos que demuestran cómo usar la API web en varias formas diferentes. Encuentre aquí las implementaciones en C# y JavaScript del ejemplo de operaciones básicas, datos de consulta, operaciones condicionales y funciones y acciones
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: cdcb02f5-3baa-4fb7-8fb3-6fe53c2d4271
caps.latest.revision: 11
author: JimDaly
ms.author: jdaly
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2a962298f8824aa26d83646806e1f5f1a3afa6e9
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154936"
---
# <a name="web-api-data-operations-samples"></a>Ejemplos de operaciones de datos de API web

Puede usar la API web de Common Data Service con una gran variedad de lenguajes o bibliotecas de programación. Esta guía proporciona una matriz de los ejemplos que demuestran cómo usar la API web en varias formas diferentes. Este tema introduce los ejemplos disponibles para cada grupo de operaciones y cómo realizar estas operaciones con otros lenguajes o bibliotecas.

<!-- TODO:
> [!NOTE]
> With the availability of the new [Xrm.WebApi](../clientapi/reference/xrm-webapi.md) client API methods, we are working on updating the client-side JavaScript samples to use the new client API methods. Check back soon.   -->
  
## <a name="web-api-sample-matrix"></a>Matriz de ejemplos de la API web

En la siguiente tabla se describen los ejemplos de la API web de Common Data Service y sus implementaciones específicas del lenguaje.  
  
|Descripción en lenguaje neutro|Implementación en C#|Implementación JavaScript del lado del cliente|  
|-----------------------------------|------------------------|--------------------------------------------|  
|[Ejemplos de API web](web-api-samples.md) (este tema)|[Ejemplos de la API web (C#)](web-api-samples-csharp.md)|[Ejemplos de la API web (JavaScript del lado del cliente)](web-api-samples-client-side-javascript.md)|  
<!-- TODO:
|[Web API Basic Operations Sample](web-api-basic-operations-sample.md)|[Web API Basic Operations Sample (C#)](samples/basic-operations-csharp.md)|Under construction. See [Xrm.WebApi](../clientapi/reference/xrm-webapi.md)|  
|[Web API Query Data Sample](web-api-query-data-sample.md)|[Web API Query Data Sample (C#)](samples/query-data-csharp.md)|Under construction. See [Xrm.WebApi](../clientapi/reference/xrm-webapi.md)|   
|[Web API Conditional Operations Sample](web-api-conditional-operations-sample.md)|[Web API Conditional Operations Sample (C#)](samples/conditional-operations-csharp.md)|Under construction. See [Xrm.WebApi](../clientapi/reference/xrm-webapi.md)|  
|[Web API Functions and Actions Sample](web-api-functions-actions-sample.md)|[Web API Functions and Actions Sample (C#)](samples/functions-actions-csharp.md)|Under construction. See [Xrm.WebApi](../clientapi/reference/xrm-webapi.md)|  -->
  
 Las siguientes tablas categorizan los temas de ejemplo por grupos de operaciones demostradas y por problemas de implementación.  
  
### <a name="groups-of-operations"></a>Grupos de operaciones
 
En la siguiente tabla se clasifican los ejemplos por grupos de operación demostrados.  
  
|Agrupar|Descripción|  
|-----------|-----------------|  
|[Ejemplo de operaciones básicas de la API web](web-api-basic-operations-sample.md)|Cómo realizar operaciones CRUD (Crear, Recuperar, Actualizar y Eliminar) y asociativas básicas.<br /><br /> Más información: <br /><br /> -   [Cree una entidad usando API web](create-entity-web-api.md)<br />-   [Recuperar una entidad usando API web](retrieve-entity-using-web-api.md)<br />-   [Actualizar y eliminar entidades mediante la API web](update-delete-entities-using-web-api.md)<br />-   [Asociar y anular la asociación de entidades mediante la API web](associate-disassociate-entities-using-web-api.md)|  
|[Ejemplo de datos de consulta de la API web](web-api-query-data-sample.md)|Cómo realizar solicitudes de consulta básicas.<br /><br /> Más información: <br /><br /> -   [Consultar datos utilizando la API web](query-data-web-api.md)<br />-   [Recuperar y ejecutar consultas predefinidas](retrieve-and-execute-predefined-queries.md)|  
|[Ejemplo de operaciones condicionales de la API web](web-api-conditional-operations-sample.md)|Cómo realizar determinadas categorías de operaciones que se basen condicionalmente en la versión del registro de entidad contenido en el servidor y/o mantenido actualmente por el cliente. Más información:[Realizar operaciones condicionales mediante la API web](perform-conditional-operations-using-web-api.md).|  
|[Ejemplo de funciones y acciones de la API web](web-api-functions-actions-sample.md)|Cómo usar funciones y acciones enlazadas y sin enlazar, incluidas acciones personalizadas.<br /><br /> Más información: <br /><br /> -   [Usar funciones de la API web](use-web-api-functions.md)<br />-   [Usar acciones de la API web](use-web-api-actions.md)|  
  
### <a name="language-or-library"></a>Lenguaje o biblioteca
 
La siguiente tabla muestra los temas que hacen referencia a los problemas comunes de implementación específicos bibliotecas o de lenguajes.  
  
|Lenguaje o biblioteca|Descripción|  
|-------------------------|-----------------|  
|[Ejemplos de la API web (C#)](web-api-samples-csharp.md)|Describe los elementos comunes que se usan en este grupo de ejemplos en C# que demuestren operaciones con clases .NET básicas y un mínimo de bibliotecas de código auxiliar.|  
|[Ejemplos de la API web (JavaScript del lado del cliente)](web-api-samples-client-side-javascript.md)|En construcción.|  
  
### <a name="see-also"></a>Vea también

[Usar la API web de Common Data Service](overview.md)<br />
[Ejemplo de operaciones básicas de la API web](web-api-basic-operations-sample.md)<br />
[Ejemplo de datos de consulta de la API web](web-api-query-data-sample.md)<br />
[Ejemplo de operaciones condicionales de la API web](web-api-conditional-operations-sample.md)<br />
[Ejemplo de funciones y acciones de la API web](web-api-functions-actions-sample.md)<br />
[Ejemplos de la API web (C#)](web-api-samples-csharp.md)<br />
