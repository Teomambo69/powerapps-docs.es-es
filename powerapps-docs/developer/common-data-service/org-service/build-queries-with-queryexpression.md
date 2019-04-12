---
title: Crear consultas con QueryExpression (Common Data Service) | Microsoft Docs
description: Obtenga información sobre cómo puede usar la clase QueryExpression para crear una consulta mediante programación que contenga los filtros y las condiciones de búsqueda de los datos que definen el ámbito de una búsqueda de base de datos.
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
# <a name="build-queries-with-queryexpression"></a>Crear consultas con QueryExpression

En Common Data Service puede usar la clase <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> para crear una consulta mediante programación que contenga los filtros de datos y las condiciones de búsqueda de los datos que definen el ámbito de una búsqueda de base de datos. Una expresión de consulta se usa para búsquedas de un solo objeto. Por ejemplo, puede crear una búsqueda que devuelva todas las cuentas que coinciden con determinados criterios de búsqueda. La clase <xref:Microsoft.Xrm.Sdk.Query.QueryBase> es la clase base para las expresiones de consulta. Hay dos clases derivadas: <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> y <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute>. La clase `QueryExpression` admite consultas complejas. La clase `QueryByAttribute` constituye un instrumento sencillo para buscar entidades en las que los atributos coinciden con los valores especificados.  
  
 Las expresiones de consulta se usan en métodos que recuperan más de un registro, como el<xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> método, en mensajes que realizan una operación en un conjunto de resultados especificado por una expresión de consulta, como,<xref:Microsoft.Crm.Sdk.Messages.BulkDeleteRequest> y cuando el identificador de un registro específico no se conoce.  
  
 Además, hay un nuevo atributo en la entidad de la organización, `Organization.QuickFindRecordLimitEnabled`. Cuando este atributo `Boolean` es `true`, se impone un límite de consultas de búsqueda rápida. Si un usuario ofrece criterios de búsqueda para una búsqueda rápida que no es muy selectiva, el sistema lo detecta y se detiene la búsqueda. Esto permite un formulario más rápido de búsqueda rápida y puede suponer una gran diferencia de rendimiento.  
  
> [!WARNING]
>  No se recuperan todos los atributos en una consulta debido al efecto negativo en el rendimiento. Este valor es "true" si la consulta se usa como parámetro de una solicitud de actualización. En una actualización, si están incluidos todos los atributos, se definen todos los valores de campo, incluso si no se cambian. Con frecuencia, esto activa las actualizaciones en cascada para los registros secundarios.  
  
 Existen dos métodos adicionales para crear consultas para recuperar los registros de Common Data Service. FetchXML, el lenguaje de consultas propietario de Common Data Service, se puede usar para realizar algunas consultas mediante consultas basadas en XML. Para obtener más información, consulte [Crear consultas con FetchXML](/dynamics365/customer-engagement/developer/org-service/build-queries-fetchxml). También puede usar la consulta integrada del lenguaje .NET (LINQ) para escribir consultas. Más información: [Crear consultas con LINQ (consulta integrada del lenguaje .NET)](build-queries-with-linq-net-language-integrated-query.md).  
  
 Para guardar una consulta, puede convertirla en FetchXML usando <xref:Microsoft.Crm.Sdk.Messages.QueryExpressionToFetchXmlRequest> y guardarla como una vista guardada usando la entidad `userquery`.  
  
## <a name="in-this-section"></a>En esta sección  
 [Usar la clase QueryByAttribute](use-querybyattribute-class.md)  
  
 [Usar la clase QueryExpression](use-queryexpression-class.md)  
  
 [Usar la clase ColumnSet](use-the-columnset-class.md)  
  
 [Usar la clase ConditionExpression](use-conditionexpression-class.md)  
  
 [Usar la clase FilterExpression](use-filterexpression-class.md)  
  
 [Usar una combinación externa izquierda en QueryExpression para consultar los registros "no en"](use-left-outer-join-queryexpression-query-records-not-in.md)  
  
 [Probar para un valor nulo](/dynamics365/customer-engagement/developer/test-null-value)  
  
 [Paginar grandes conjuntos de resultados con QueryExpression y FetchXML](page-large-result-sets-with-queryexpression.md)  
  
 [Ejemplo: Recuperar con relación de uno a varios](/dynamics365/customer-engagement/developer/org-service/sample-retrieve-with-one-to-many-relationship)  
  
 [Ejemplo: Recuperar varios mediante consulta por atributo](/org-service/samples/retrieve-multiple-querybyattribute-class.md)  
  
 [Ejemplo: Recuperar varios mediante consulta por expresión](/org-service/samples/retrieve-multiple-queryexpression-class.md)  
  
 [Ejemplo: usar QueryExpression con una cookie de paginación](/dynamics365/customer-engagement/developer/org-service/sample-use-queryexpression-with-a-paging-cookie)  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.Xrm.Sdk.Query.QueryBase>  
  
 <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>  
  
 <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute>  
  
 <xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*>  
  
 <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>  
  
 <xref:Microsoft.Xrm.Sdk.Query.ConditionExpression>  
  
 <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>  
  
 <xref:Microsoft.Xrm.Sdk.Query.PagingInfo.PagingCookie>  
  
### <a name="see-also"></a>Vea también  
 [Ejemplo: convertir consultas entre Fetch y QueryExpression](/dynamics365/customer-engagement/developer/org-service/sample-convert-queries-fetch-queryexpression)
