---
title: Ver datos con visualizaciones (gráficos) (aplicaciones basadas en modelos) | Microsoft Docs
description: Las visualizaciones le permiten ver gráficamente los datos profesionales. Una visualización se asocia a una entidad en Common Data Service. Puede adjuntar varias visualizaciones a una entidad, no obstante, solo se puede mostrar una visualización al mismo tiempo junto con una cuadrícula. Puede ver varias visualizaciones al mismo tiempo utilizando un panel.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4ede56a8ab217b81580c036e45309db214b273b4
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754553"
---
# <a name="view-data-with-visualizations-charts"></a>Ver los datos con visualizaciones (gráficos)

Las visualizaciones le permiten ver gráficamente los datos profesionales. Una visualización se asocia a una entidad en Common Data Service. Puede adjuntar varias visualizaciones a una entidad, no obstante, solo se puede mostrar una visualización al mismo tiempo junto con una cuadrícula. Puede ver varias visualizaciones al mismo tiempo utilizando un panel. Más información: [Analizar datos con paneles](analyze-data-with-dashboards.md)  
  
 Puede usar un gráfico o a un recurso web como visualización en Common Data Service. Para los gráficos, puede usar el diseñador de gráficos en aplicaciones basadas en modelos. Sin embargo, para usar un recurso web en una visualización, debe usar el SDK o importar una visualización XML personalizada en aplicaciones basadas en modelos.
  
<a name="VisualizationTypes"></a>   
## <a name="visualization-ownership"></a>Propiedad de la visualización  
 En aplicaciones basadas en modelos, existen dos tipos de propiedad de la visualización: que pertenece a la organización y que pertenece al usuario.  
  
- Una visualización que pertenece a una organización su propietario es una organización y no se puede asignar o compartir. La entidad `SavedQueryVisualization` representa la visualización que pertenece a la organización. Estas visualizaciones son entidades basadas en la solución de aplicaciones basadas en modelos. Cuando actualiza una visualización guardada de la consulta, debe publicar los cambios para que las actualizaciones estén disponibles en la organización mediante el mensaje <xref:Microsoft.Crm.Sdk.Messages.PublishAllXmlRequest>. Se hace referencia a esta entidad como un *Gráfico del sistema* en la aplicación web de aplicaciones basadas en modelos.  
  
- Una visualización que pertenece el usuario su propietario es un usuario individual, y se puede asignar y compartir con otros usuarios y equipos. La entidad `UserQueryVisualization` representa la visualización que pertenece al usuario. Se hace referencia a esta entidad como un *Gráfico de usuario* en la aplicación web de aplicaciones basadas en modelos y se muestra en **Mis gráficos** en la lista desplegable de gráfico.  
  
  Una visualización de consulta de usuario no está asociada a una consulta de usuario (vista), a pesar del nombre de entidad. El aspecto de la vista de esta entidad se usa solo para establecer los criterios de filtro.  
  
<a name="Charts"></a>   
## <a name="chart-visualizations"></a>Visualizaciones de gráfico  
 Los gráficos permiten ver los resúmenes de datos de la cuadrícula. Los gráficos se crean mediante las Controles de gráfico de Microsoft para Microsoft .NET Framework 3.5. Para obtener más información sobre Controles de gráfico de Microsoft, vea [Descargar: Controles de gráfico para .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=128852).  
  
 Estos gráficos se integran con las cuadrículas de la aplicación web. Cuando aplica un filtro (consulta) a los datos de una cuadrícula, el filtro se aplica al gráfico también y el gráfico se actualiza de modo correspondiente. De forma similar, cuando realiza operaciones de exploración en profundidad en un gráfico, los datos de cuadrícula se actualizan automáticamente.  
  
 Está disponible un gráfico asociado a una entidad para todas las vistas de la entidad. Un gráfico muestra los datos de acuerdo a la vista seleccionada (o mostrada) actualmente de una entidad. Un gráfico puede mostrar los datos de una consulta guardada (vista que pertenece a la organización) y una consulta de usuario (vista que pertenece al usuario).  
  
 Los gráficos muestran los datos solo de las consultas guardadas (vistas que pertenecen a la organización) que FetchXML usa (atributo `SavedQuery.FetchXml`) para filtrar los registros. Si una consulta guardada usa la API de consulta (atributo `SavedQuery.QueryAPI`) para filtrar los registros, no aparecerá el gráfico para esa consulta guardada. Esta limitación no es aplicable para las consultas de usuario (vistas que pertenecen al usuario) porque la entidad de consulta del usuario no usa el atributo `QueryAPI` para filtrar los registros.  
  
 Para obtener más información sobre cómo trabajar con gráficos, consulte [Descripción de los gráficos: representación de datos y gráficos subyacentes](understand-charts-underlying-data-chart-representation.md).  
  
<a name="ChartTypes"></a>   
### <a name="chart-types-in-microsoft-chart-controls"></a>Tipos de gráficos en Microsoft Chart Controls  
 Los controles de gráfico de Microsoft se usan para crear gráficos en aplicaciones basadas en modelos. Controles de gráfico de Microsoft permite crear diferentes tipos de gráfico como columnas, barras, áreas, apilados, líneas, burbujas y circulares.  
  
 Se admiten los siguientes tipos de gráficos predefinidos en Common Data Service: *Columna*, *Área*, *Barra*, *Línea*, *Circular* y *Embudo*. Sin embargo, puede ampliar la funcionalidad mediante la creación de otros tipos de gráficos de Controles de gráfico de Microsoft compatibles como de varias series, apilados y 100% apilada (comparación) especificando el contenido adecuado en la descripción de datos y en las cadenas XML de descripción de presentación para un gráfico. Más información: [Especificar datos del gráfico](understand-charts-underlying-data-chart-representation.md)  
  
<a name="WebResources"></a>   
## <a name="web-resource-visualizations"></a>Visualizaciones de recurso web  
 Los recursos web son archivos virtuales que se almacenan en la base de datos de aplicaciones basadas en modelos y se pueden recuperar mediante una dirección URL única. Puede mostrar un recurso web existente como una visualización y mostrarlo en el área **Gráficos** de aplicaciones basadas en modelos junto con otros gráficos de una entidad. Para obtener más información acerca de los recursos web, consulte [Recursos web para aplicaciones basadas en modelos](web-resources.md).  
  
 Puede usar los siguientes tipos de recursos web en una visualización: [Recursos de web Webpage (HTML)](webpage-html-web-resources.md) y [Recursos web de imagen (JPG, PNG, GIF, ICO)](image-web-resources.md). Para obtener más información sobre cómo crear una visualización con un recurso web, consulte [Crear una visualización de recursos web](create-visualization-chart.md#create-a-web-resource-visualization).  
  
<a name="SupportedVisualizationEntities"></a>   
## <a name="entities-supported-for-visualizations"></a>Entidades admitidas para las visualizaciones  
 Puede crear y adjuntar visualizaciones a aquellas entidades de Common Data Service que admitan la nueva interfaz de cinta de opciones. Esto se debe a que todos los controles gráficos solamente están presentes en la interfaz de la cinta de opciones de Common Data Service. También se admiten las entidades personalizadas para las visualizaciones. Puede desactivar el soporte técnico de visualización para las entidades personalizadas si lo desea. Sin embargo, no puede deshabilitar el soporte de visualización para las entidades predeterminadas.  
  
 A continuación se enumeran las entidades predeterminadas que se admiten para las visualizaciones.  
  
 Cuenta  
ActivityPointer  
Cita  
BulkOperation  
Campaña  
CampaignActivity  
CampaignResponse  
Competidor  
Conexión  
Contacto  
Contrato  
Enviar por correo electrónico  
Derecho  
EntitlementChannel  
EntitlementTemplateChannel  
Fax  
Objetivo  
GoalRollupQuery  
Incidente  
Factura  
InvoiceDetail  
KbArticle  
Cliente potencial  
Carta  
Enumerar  
Buzón  
Métrica  
Oportunidad  
Producto de oportunidad  
PhoneCall  
Puesto  
Nivel de precios  
Producto  
ProductAssociation  
ProductSubstitute  
QueueItem  
Oferta  
QuoteDetail  
RecurringAppointmentMaster  
Informe  
SalesLiterature  
Pedido de venta  
SalesOrderDetail  
Service  
ServiceAppointment  
SLAKPIInstance  
Actividad social  
Perfil social  
SystemUser  
Tarea  
Equipo  
Zona de ventas  
UoMSchedule  
  
### <a name="see-also"></a>Vea también  
 [Crear y analizar datos](customize-visualizations-dashboards.md)   
 [Especificar datos del gráfico](understand-charts-underlying-data-chart-representation.md)   
 [Acciones en el gráfico](actions-visualizations-charts.md)   
 [Crear un gráfico](create-visualization-chart.md)   
 [Gráficos de muestra](sample-charts.md)   
 [Entidad SavedQueryVisualization](../common-data-service/reference/entities/savedqueryvisualization.md)   
 [Entidad UserQueryVisualization](../common-data-service/reference/entities/userqueryvisualization.md) [Descarga: Controles de gráfico para el paquete de idioma de .NET Framework](https://www.microsoft.com/downloads/details.aspx?FamilyId=581FF4E3-749F-4454-A5E3-DE4C463143BD&displaylang=en)   
 [Descarga: Complemento Controles de gráfico para Visual Studio](https://www.microsoft.com/downloads/details.aspx?FamilyId=1D69CE13-E1E5-4315-825C-F14D33A303E9&displaylang=en)   
 [Descarga: Documentación de Controles de gráfico para .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=128301)   
 [Ejemplos de entorno de Controles de gráfico de Microsoft](https://code.msdn.microsoft.com/mschart)   
 [Foro de Controles de gráfico](https://go.microsoft.com/fwlink/p/?LinkId=128713)
