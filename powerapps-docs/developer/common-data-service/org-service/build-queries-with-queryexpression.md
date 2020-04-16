---
title: Crear consultas con QueryExpression (Common Data Service) | Microsoft Docs
description: Obtenga información sobre cómo puede usar la clase QueryExpression para crear una consulta mediante programación que contenga los filtros y las condiciones de búsqueda de los datos que definen el ámbito de una búsqueda de base de datos.
ms.custom: ''
ms.date: 06/25/2019
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
ms.openlocfilehash: 107432081e08a662621521244f2dc5613824a28f
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156108"
---
# <a name="build-queries-with-queryexpression"></a>Crear consultas con QueryExpression

En Common Data Service, puede usar la clase <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> para crear una consulta mediante programación que contenga los filtros y las condiciones de búsqueda de los datos que definen el ámbito de una búsqueda de base de datos. Una expresión de consulta se usa para búsquedas de un solo objeto. Por ejemplo, puede crear una búsqueda que devuelva todas las cuentas que coinciden con determinados criterios de búsqueda. La clase <xref:Microsoft.Xrm.Sdk.Query.QueryBase> es la clase base para las expresiones de consulta. Hay tres clases derivadas: <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>, <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> y <xref:Microsoft.Xrm.Sdk.Query.FetchExpression>. La clase `QueryExpression` admite consultas complejas. La clase `QueryByAttribute` constituye un instrumento sencillo para buscar entidades en las que los atributos coinciden con los valores especificados. 

> [!NOTE]
> La tercera clase derividaa, `FetchExpression` se utiliza con FetchXML, el lenguaje de consultas propietario de Common Data Service, se puede usar para realizar algunas consultas mediante consultas basadas en XML. Más información: [Usar FetchXML para crear una consulta](../use-fetchxml-construct-query.md)
  
Las expresiones de consulta se usan en métodos que recuperan más de un registro, como el<xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> método, en mensajes que realizan una operación en un conjunto de resultados especificado por una expresión de consulta, como,<xref:Microsoft.Crm.Sdk.Messages.BulkDeleteRequest> y cuando el identificador de un registro específico no se conoce.  

> [!WARNING]
>  No se recuperan todos los atributos en una consulta debido al efecto negativo en el rendimiento. Este valor es "true" si la consulta se usa como parámetro de una solicitud de actualización. En una actualización, si están incluidos todos los atributos, se definen todos los valores de campo, incluso si no se cambian. Con frecuencia, esto activa las actualizaciones en cascada para los registros secundarios.

Para guardar una consulta y poder reutilizarla, puede convertirla en FetchXML usando <xref:Microsoft.Crm.Sdk.Messages.QueryExpressionToFetchXmlRequest> y guardarla como una consulta guardada. Más información: [Consultas guardadas](../saved-queries.md) 
 
## <a name="alternatives-to-queryexpression"></a>Alternativas a QueryExpression

Existen dos métodos adicionales para crear consultas para recuperar los registros de Common Data Service. 

- FetchXML, el lenguaje de consultas propietario de Common Data Service, se puede usar para realizar algunas consultas mediante consultas basadas en XML. Más información: [Usar FetchXML para crear una consulta](../use-fetchxml-construct-query.md). 
- Consulta integrada del lenguaje .NET (LINQ). Más información: [Crear consultas con LINQ (consulta integrada del lenguaje .NET)](build-queries-with-linq-net-language-integrated-query.md).  

<!-- This doesn't belong here. It should be in model driven app configuration -->
## <a name="configuration-for-quick-find"></a>Configuración de búsqueda rápida

En aplicaciones basadas en modelos hay una característica de búsqueda rápida. Si un usuario ofrece criterios de búsqueda para una búsqueda rápida que no es muy selectiva, el sistema lo detecta y se detiene la búsqueda. Esto permite un formulario más rápido de búsqueda rápida y puede suponer una gran diferencia de rendimiento. Esta es controlada por el atributo [QuickFindRecordLimitEnabled de entidad de la organización](/powerapps/developer/common-data-service/reference/entities/organization#BKMK_QuickFindRecordLimitEnabled) Cuando este valor de atributo `Boolean` es `true`, se impone un límite de consultas de búsqueda rápida.

## <a name="in-this-section"></a>En esta sección

[Usar la clase QueryByAttribute](use-querybyattribute-class.md)<br />
[Usar la clase QueryExpression](use-queryexpression-class.md)<br />
[Usar la clase ColumnSet](use-the-columnset-class.md)<br />
[Usar la clase ConditionExpression](use-conditionexpression-class.md)<br />
[Usar la clase FilterExpression](use-filterexpression-class.md)<br />
[Usar una combinación externa izquierda en QueryExpression para consultar los registros "no en"](use-left-outer-join-queryexpression-query-records-not-in.md)<br />
[Probar para un valor nulo](/dynamics365/customer-engagement/developer/test-null-value)<br />
[Paginar grandes conjuntos de resultados con QueryExpression y FetchXML](page-large-result-sets-with-queryexpression.md)<br />
[Ejemplo: Recuperar con relación de uno a varios](/dynamics365/customer-engagement/developer/org-service/sample-retrieve-with-one-to-many-relationship)<br />
[Ejemplo: Recuperar varios mediante consulta por atributo](/org-service/samples/retrieve-multiple-querybyattribute-class.md)<br />
[Ejemplo: Recuperar varios mediante consulta por expresión](/org-service/samples/retrieve-multiple-queryexpression-class.md)<br />
[Ejemplo: usar QueryExpression con una cookie de paginación](/dynamics365/customer-engagement/developer/org-service/sample-use-queryexpression-with-a-paging-cookie)  
  
## <a name="reference"></a>Referencia

<xref:Microsoft.Xrm.Sdk.Query.QueryBase><br />
<xref:Microsoft.Xrm.Sdk.Query.QueryExpression><br />
<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute><br />
<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*><br />
<xref:Microsoft.Xrm.Sdk.Query.ColumnSet><br />
<xref:Microsoft.Xrm.Sdk.Query.ConditionExpression><br />
<xref:Microsoft.Xrm.Sdk.Query.FilterExpression><br />
<xref:Microsoft.Xrm.Sdk.Query.PagingInfo.PagingCookie><br />
  
### <a name="see-also"></a>Vea también

[Ejemplo: convertir consultas entre Fetch y QueryExpression](/dynamics365/customer-engagement/developer/org-service/sample-convert-queries-fetch-queryexpression)
