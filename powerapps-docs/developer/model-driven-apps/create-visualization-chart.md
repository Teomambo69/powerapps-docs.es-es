---
title: Crear una visualización (gráfico) (aplicaciones basadas en modelos) | Microsoft Docs
description: Este tema muestra cómo crear una visualización del gráfico y una visualización del recurso web.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 9dbed5ee-21a4-ab86-fc4c-08c3838e42f2
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ef9bb60a64b4b7b88d252fcfbbc99e74307eb298
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275840"
---
# <a name="create-a-visualization-chart"></a>Crear una visualización (gráfico)

Para crear una visualización mediante programación, debe crear un registro para la [Entidad SavedQueryVisualization](../common-data-service/reference/entities/savedqueryvisualization.md) o la [Entidad UserQueryVisualization](../common-data-service/reference/entities/userqueryvisualization.md) para crear un gráfico propiedad de la organización o propiedad del usuario respectivamente. Este tema muestra cómo crear una visualización del gráfico y una visualización del recurso web.  
  
<a name="Before"></a>   

## <a name="before-you-create-a-visualization"></a>Antes de crear una visualización  

 Antes de crear una visualización, asegúrese de saber lo siguiente:  
  
- **Tipo de visualización**: si desea que las visualizaciones estén disponibles en la organización y no se desea administrar los niveles de acceso en un nivel más detallado, puede crear una visualización propiedad de la organización. Sin embargo, si le preocupan los privilegios de acceso y la seguridad de la visualización, considere la posibilidad de crear una visualización propiedad del usuario en la que tenga más control sobre quién puede obtener acceso a ella.  
  
    > [!NOTE]
    >  Las visualizaciones que pertenecen a la organización solo las pueden crear los usuarios que tengan el rol de administrador del sistema o personalizador del sistema.  
  
- **Entidad asociada**: las visualizaciones se asocian a entidades. Más información: [Entidades compatibles con visualizaciones](view-data-with-visualizations-charts.md#SupportedVisualizationEntities). Puede vincular un gráfico a una entidad admitida usando el atributo [SavedQueryVisualization.PrimaryEntityTypeCode](../common-data-service/reference/entities/savedqueryvisualization.md#BKMK_PrimaryEntityTypeCode) o [UserQueryVisualization.PrimaryEntityTypeCode](../common-data-service/reference/entities/userqueryvisualization.md#BKMK_PrimaryEntityTypeCode).  
  
<a name="CreateChart"></a>   

## <a name="create-a-chart-visualization"></a>Creación de una visualización de gráfico  

 Los gráficos requieren que se especifiquen sus datos subyacentes y el aspecto que tendrán los gráficos mediante cadenas XML de *descripción de datos* y *descripción de presentación*. Más información: [Especificar datos de gráficos](understand-charts-underlying-data-chart-representation.md) y [Gráficos de ejemplo](sample-charts.md).  
  
 Para obtener un ejemplo completo sobre cómo crear un gráfico de propiedad de la organización, vea [Ejemplo: Crear, recuperar, actualizar y eliminar (CRUD) un gráfico ](/dynamics365/customer-engagement/developer/customize-dev/sample-create-retrieve-update-delete-chart).  <!-- TODO need to replace the link with powerapps -->
  
### <a name="create-a-multi-series-chart"></a>Creación de un gráfico de varias series  

 Los gráficos de varias series asignan valores de eje (vertical) de varias series a un solo valor de eje (horizontal) de categorías. Solo se diferencia de los gráficos de una sola serie en que estos gráficos tienen varios elementos `<measurecollection>` y `<series>` correspondientes especificados en las cadenas XML. Cada elemento `<measurecollection>` contiene un elemento secundario `<measure>` que define un valor de eje (vertical) de series para el mismo valor (horizontal) de categorías. Más información: [Descripción de los gráficos: representación de datos y gráficos subyacentes](understand-charts-underlying-data-chart-representation.md).  
  
 Para obtener un gráfico de varias series de ejemplo y las correspondientes cadenas XML de descripción de datos y de presentación, consulte [Gráfico de varias series](sample-charts.md#multi-series-chart).
  
<a name="CreateWRVisualization"></a>   

## <a name="create-a-web-resource-visualization"></a>Creación de una visualización de recurso web  

 Las visualizaciones que contienen recursos web no requieren especificar las cadenas XML de descripción de datos y de presentación. El siguiente ejemplo muestra cómo crear una visualización propiedad de una organización que contiene un recurso web mediante el SDK.  
  
```csharp  
SavedQueryVisualization newWebResourceVisualization = new SavedQueryVisualization()  
{  
   Name = "Sample Dashboard Visualization",  
   Description = "Sample organization-owned visualization",  
                           PrimaryEntityTypeCode = Account.EntityLogicalName,  
   WebResourceId = new EntityReference(WebResource.EntityLogicalName, _webResourceId))  
  
};  
_orgOwnedVisualizationId = _serviceProxy.Create(newWebResourceVisualization);  
  
```  
  
 Si desea crear una visualización del recurso web mediante la aplicación web de Common Data Service, debe crear un archivo XML en el siguiente formato, y después usar **Importar gráfico** en la cinta de opciones para importar la visualización.  
  
```xml  
<visualization>  
  <name>Visualization_Name</name>  
  <description>Description</description>  
  <webresourcename>Name_Of_An_Existing_Web_Resource</webresourcename>  
  <primaryentitytypecode>Entity_Logical_Name</primaryentitytypecode>  
  <isdefault>Value: true or false</isdefault>  
</visualization>  
```  
  
 Por ejemplo, para crear una *Visualización de ejemplo* que muestra un recurso web existente llamado *new_TestWebResource*, la visualización debe estar asociada a la entidad *cuenta*, el código XML debería tener este aspecto.  
  
```xml  
<visualization>  
  <name>Sample Visualization</name>  
  <description>Sample Web Resource Visualization.</description>  
  <webresourcename>new_TestWebResource</webresourcename>  
  <primaryentitytypecode>account</primaryentitytypecode>  
  <isdefault>false</isdefault>  
</visualization>  
```  
  
### <a name="see-also"></a>Vea también  
 [Gráficos](view-data-with-visualizations-charts.md)   
 [Especificar datos del gráfico](understand-charts-underlying-data-chart-representation.md)   
 [Acciones en el gráfico](actions-visualizations-charts.md)   
 [Gráficos de muestra](sample-charts.md)   
 [Análisis y visualización de datos](customize-visualizations-dashboards.md)   
 [Ejemplo: Crear, recuperar, actualizar y eliminar (CRUD) un gráfico](/dynamics365/customer-engagement/developer/customize-dev/sample-create-retrieve-update-delete-chart)  <!-- TODO need to replace the link with powerapps -->