---
title: Implemente todos los tipos de consultas al filtrar resultados mediante PreOperation RetrieveMultiple | MicrosoftDocs
description: Para obtener el máximo rendimiento y resultados coherentes para todas las aplicaciones debe implementar el filtrado para todos los tipos de consultas que se pueden usar con complementos que se registran para la fase PreOperation de RetrieveMultiple
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: ryjones
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/23/2019
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="implement-all-types-of-queries-when-filtering-results-using-preoperation-retrievemultiple"></a>Implemente todos los tipos de consultas al filtrar resultados mediante PreOperation RetrieveMultiple

**Categoría**: Diseño, rendimiento, seguridad, compatibilidad

**Potencial de impacto**: medio

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

Las llamadas de RetrieveMultiple desde diferentes aplicaciones muestran resultados diferentes.

- Por ejemplo: las mismas vistas en aplicaciones heredadas muestran diferentes resultados en nuevas aplicaciones.

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

> [!NOTE]
> Los mensajes `Retrieve` y `RetrieveMultiple` suelen ser los mensajes más comunes. Los complementos para estos mensajes pueden afectar de forma significativa el rendimiento del sistema. Generalmente, debe evitar el uso de complementos para estos mensajes si los requisitos se pueden conseguir de algún otro modo. Más información: [Limitar el registro de complementos para los mensajes Retrieve y de RetrieveMultiple](limit-registration-plugins-retrieve-retrievemultiple.md)

Los complementos registrados en el mensaje `RetrieveMultiple` se proporcionan normalmente para filtrar los resultados devueltos por las consultas de una entidad. Hay dos estrategias para hacerlo con un complemento registrado en las fases `PostOperation` o `PreOperation`.

### <a name="postoperation-filtering"></a>Filtrado PostOperation

En la fase `PostOperation`, evalúe los registros devueltos en la propiedad <xref:Microsoft.Xrm.Sdk.IExecutionContext.OutputParameters> `BusinessEntityCollection` <xref:Microsoft.Xrm.Sdk.EntityCollection.Entities> y quite las entidades que no deben ser devueltas.

Este método cambia potencialmente el número de registros esperado devueltos en cada página de resultados y puede producir experiencias incoherentes cuando los datos se muestra en una aplicación.

### <a name="preoperation-filtering"></a>Filtrado PreOperation

En la fase `PreOperation`, evalúe la propiedad <xref:Microsoft.Xrm.Sdk.IExecutionContext.InputParameters> <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest.Query> y ajuste la consulta para filtrar qué se devolverá antes de que se ejecute.

Cuando se usa este método debe implementar el filtrado adecuado para los diferentes tipos posibles de consultas, sobre todo: <xref:Microsoft.Xrm.Sdk.Query.FetchExpression> y<xref:Microsoft.Xrm.Sdk.Query.QueryExpression>. Si implementa sólo uno de estos, distintas aplicaciones que usan el otro tipo de consulta no aplicarán los cambios.

Aunque los mensajes `QueryExpressionToFetchXml` y `FetchXmlToQueryExpression` proporcionan la capacidad de convertir un tipo de consulta en otro, debido al impacto de rendimiento de incluir llamadas adicionales en `RetrieveMultiple`, se recomienda no usar estos mensajes en este contexto. En su lugar, implemente el filtrado mediante la lógica equivalente en ambos. 

Hay un tercer tipo de consulta que también puede ser usado con `RetrieveMultiple`: <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute>. Este tipo de consulta no proporciona filtrado complejo y no es posible incluir una lógica de filtrado más compleja en un complemento. Afortunadamente, este tipo de consulta no se usa con frecuencia. Según la sensibilidad del filtrado que agrega, puede elegir rechazar consultas de este tipo lanzando una <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException>.

## <a name="example"></a>Ejemplo

Vea [Ejemplo: Modificar consulta en fase PreOperation](../../org-service/samples/modify-query-preoperation-stage.md) para un ejemplo de la estrategia que se recomienda.

## <a name="problematic-patterns"></a>Patrones problemáticos

Si se escribe un complemento para cambiar los registros devueltos en una aplicación específica que usa solo un tipo de consulta usado por esa aplicación, <xref:Microsoft.Xrm.Sdk.Query.FetchExpression> o<xref:Microsoft.Xrm.Sdk.Query.QueryExpression>, es posible que los resultados no sean coherentes en otras aplicaciones o si la aplicación cambia el tipo de consulta usado. Los complementos se deben escribir para proporcionar el mismo resultado sin importar la aplicación.

<a name='additional'></a>

## <a name="additional-information"></a>Información adicional

Cuando se usa API web, las solicitudes GET en una colección se convierten a <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> a menos que la consulta use FetchXml como se describe en [Recuperar y ejecutar consultas predefinidas](../../webapi/retrieve-and-execute-predefined-queries.md). En ese caso, las consultas usan <xref:Microsoft.Xrm.Sdk.Query.FetchExpression>.

El cliente web heredado para aplicaciones basadas en modelo está siendo reemplazado por la interfaz unificada. La interfaz unificada usa el FetchXml definido en las propiedades de [SavedQuery.FetchXml](../../reference/entities/savedquery.md#BKMK_FetchXml) o [UserQuery.FetchXml](../../reference/entities/userquery.md#BKMK_FetchXml). Para mejorar el rendimiento, la interfaz unificada no convierte los datos de FetchXml a una <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> antes de ejecutar estas consultas como hizo el cliente web heredado. Por tanto, las consultas que se modificaron en código de complemento para el cliente web heredado que utilizaba <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> no aplicarán los mismos cambios ahora que la consulta para admitir vistas se está pasando mediante <xref:Microsoft.Xrm.Sdk.Query.FetchExpression> a menos que el código de complemento se escriba para aplicar la misma lógica a consultas <xref:Microsoft.Xrm.Sdk.Query.FetchExpression>. 

<a name='seealso'></a>

### <a name="see-also"></a>Vea también

[Ejemplo: Modificar consulta en fase PreOperation](../../org-service/samples/modify-query-preoperation-stage.md)<br />
[Consulta de datos duplicados con el servicio de organización](../../org-service/entity-operations-query-data.md)<br />
[Usar FetchXML para crear una consulta](../../use-fetchxml-construct-query.md)<br />
[Crear consultas con QueryExpression](../../org-service/build-queries-with-queryexpression.md)<br />
[Limitar el registro de complementos para los mensajes Retrieve y de RetrieveMultiple](limit-registration-plugins-retrieve-retrievemultiple.md)<br />
[Comunidad de interfaz unificada](https://community.dynamics.com/365/unified-interface/)