---
title: 'Comprender gráficos: datos subyacentes y representación de gráficos (aplicaciones basadas en modelos) | Microsoft Docs'
description: 'Los gráficos presentan los datos visualmente asignando valores de texto en dos ejes: el horizontal (x) y el vertical (y). El eje x se denomina eje de categoría y el eje y se denomina eje de serie.'
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
ms.openlocfilehash: a1e3e41e35d3d4a20e0234269ba66e2ec26942da
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754557"
---
# <a name="understand-charts-underlying-data-and-chart-representation"></a>Descripción de gráficos: representación gráfico y datos subyacentes

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/understand-charts-underlying-data-chart-representation -->

Los gráficos presentan los datos visualmente asignando valores de texto en dos ejes: el horizontal (x) y el vertical (y). El eje x se denomina eje de *categoría* y el eje y se denomina eje de *serie*. El eje de categoría puede mostrar valores numéricos y no numéricos, mientras el eje de series solo muestra valores numéricos.  
  
 Los gráficos de aplicaciones basadas en modelos se pueden clasificar en lo siguiente:  
  
- **Gráficos de una sola serie**: gráficos que muestran datos con un valor (y) de serie asignado a un valor de categoría (x).  
  
- **Gráficos de varias series**: gráficos que muestran datos con valores de varias series asignados a un valor de una categoría. Los gráficos de varias series incluyen gráficos de columnas apiladas, que muestran verticalmente la colaboración de cada serie a un total en las diferentes categorías, y gráficos de columna apiladas al 100%, que comparan el porcentaje que cada serie contribuye a un total en las diferentes categorías. Puede combinar varios tipos de gráficos compatibles en gráficos de varias series, por ejemplo, columna y línea, barra y línea, etc.  
  
> [!NOTE]
>  Los gráficos de varias categorías se pueden crear con la aplicación web o modificando las cadenas XML descritas aquí.  
  
 Durante la creación de un gráfico en aplicaciones basadas en modelos mediante el SDK, debe tener en cuenta los siguientes dos aspectos importantes:  
  
- **Datos subyacentes del gráfico**: especificados mediante la cadena XML *de descripción de los datos*.  
  
- **Visualización de datos (apariencia)**: especificados mediante la cadena XML *de la descripción de la visualización*.  
  
> [!NOTE]
> Controles de gráfico de Microsoft le permite crear varios tipos de gráficos como de columna, barras, áreas, líneas, circular, embudo, burbuja y radar. El diseñador de gráficos en aplicaciones basadas en modelos permite crear solo ciertos tipos de gráficos. Sin embargo, mediante el SDK, puede crear la mayoría de los tipos de gráficos compatibles con Controles de gráfico de Microsoft.  
  
## <a name="use-the-data-description-xml-string-to-specify-chart-data"></a>Use la cadena XML de descripción de datos para especificar datos del gráfico  
 La cadena XML de descripción de datos define los datos que se mostrarán en el gráfico. El contenido de la cadena XML se valida con el esquema de descripción de los datos de visualización. Para obtener más información acerca del esquema, consulte [Esquema de descripción de los datos de visualización](visualization-data-description-schema.md).  
  
 Puede especificar la cadena XML de descripción de datos mientras crea un gráfico mediante el atributo `SavedQueryVisualization.DataDescription` o el atributo `UserQueryVisualization.DataDescription` para el gráfico propiedad de la organización o propiedad del usuario respectivamente.  
  
 La cadena XML de descripción de datos contiene los siguientes dos elementos: `<FetchCollection>` y `<CategoryCollection>`.  
  
### <a name="the-fetchcollection-element"></a>El elemento \<FetchCollection 
 
 El elemento `<FetchCollection>` usa FetchXML para recuperar los datos para el gráfico. La consulta de FetchXML especifica la información acerca de los atributos de la entidad, las funciones agregadas y el grupo por cláusulas de los datos que se mostrarán en un gráfico. Todas las funciones agregadas FetchXML son compatibles con los gráficos. Para obtener más información acerca de las funciones agregadas FetchXML, consulte [Uso de agregación FetchXML](../common-data-service/use-fetchxml-aggregation.md).  
  
 La consulta de FetchXML permite filtrar los datos. Además, los filtros se aplican en gráficos a través de vistas. Por lo tanto, si ya se ha especificado una condición de filtrado en la consulta de FetchXML en el elemento `<FetchCollection>` y además se aplica un filtro a través de una vista, el gráfico mostrará los datos que se devuelven después de aplicar todos los filtros. Para obtener más información sobre cómo usar la consulta FetchXML para filtrar datos, consulte [Uso de FetchXML para crear una consulta](../common-data-service/use-fetchxml-construct-query.md).  
  
> [!NOTE]
>  Aunque la cadena XML de descripción de datos se valide de nuevo en el esquema de descripción de los datos de visualización, la consulta FetchXML del elemento `<FetchCollection>` no. La consulta FetchXML se valida en el esquema FetchXML. Para obtener más información, consulte [Esquema de FetchXML](../common-data-service/fetchxml-schema.md).  
  
 Si el gráfico es un gráfico de comparación, el elemento `<FetchCollection>` contendrá dos cláusulas de *agrupar por*.  
  
### <a name="the-categorycollection-element"></a>El elemento \<CategoryCollection>  
 El elemento `<CategoryCollection>` contiene información acerca de los ejes de categoría (horizontal) y de series (vertical) de un gráfico.  
  
-   Cada subelemento de `<Category>` tiene un elemento secundario llamado `<MeasureCollection>` que se asigna al elemento `<Series>` en el XML de descripción de la presentación. Un único gráfico de serie dispone de un solo elemento secundario `<MeasureCollection>`, mientras que un gráfico de varias series tendrá varios elementos secundarios `<MeasureCollection>`, cada uno asignado al elemento `<Series>` correspondiente en el XML de descripción de la presentación.  
  
-   Cada elemento secundario de `<MeasureCollection>` tiene un elemento denominado `<Measure>` que se corresponde al valor del eje de serie (vertical), correspondiente a cada valor del eje de categorías (horizontal).  
  
### <a name="example"></a>Ejemplo  
 A continuación se facilita una cadena XML de descripción de datos de ejemplo:  
  
```xml  
<datadefinition>  
  <fetchcollection>  
    <fetch mapping="logical" count="10">  
      <entity name="opportunity">  
        <attribute name="estimatedvalue" />  
        <order attribute="estimatedvalue" descending="true" />  
      </entity>  
    </fetch>  
  </fetchcollection>  
  <categorycollection>  
    <category>  
      <measurecollection>  
        <measure alias="estimatedvalue" />  
      </measurecollection>  
    </category>  
  </categorycollection></datadefinition>  
```  
  
 Para obtener más cadenas XML de descripción de los datos de ejemplo, consulte [Gráficos de muestra](sample-charts.md).  
  
## <a name="use-the-presentation-description-xml-string-to-specify-data-representation"></a>Use la cadena XML de descripción de presentación para especificar la representación de datos  
 La cadena XML de la descripción de la presentación contiene información acerca de la apariencia del gráfico, como el título del gráfico, el color del gráfico, el tipo de gráfico (barra, columna, línea, etc.). No hay ninguna definición de esquema para esta cadena XML. Sin embargo, XML es una serialización de la clase [Gráfico](https://msdn.microsoft.com/library/system.web.ui.datavisualization.charting.chart.aspx) en Controles de gráfico de Microsoft. Más información: [Controles de gráfico](https://go.microsoft.com/fwlink/p/?LinkId=128301)  
  
 Puede especificar la cadena XML de descripción de presentación mientras crea un gráfico mediante el atributo `SavedQueryVisualization.PresentationDescription` o el atributo `UserQueryVisualization.PresentationDescription` para el gráfico propiedad de la organización o propiedad del usuario respectivamente.  
  
### <a name="example"></a>Ejemplo  
 A continuación se facilita una cadena XML de descripción de la presentación de muestra:  
  
```xml  
<Chart Palette="BrightPastel">  
  <Series>  
    <Series _Template_="All" Color="153, 204, 255" BorderColor="164, 164, 164" BorderDashStyle="Solid" BorderWidth="1" ShadowColor="128, 128, 128, 128" ShadowOffset="1" IsValueShownAsLabel="true" Font="{0}, 6.75pt" BackGradientStyle="TopBottom" BackSecondaryColor="0, 102, 153" LabelForeColor="100, 100, 100" ChartType="Column">  
      <SmartLabelStyle Enabled="True" />  
      <Points />  
    </Series>  
  </Series>  
  <ChartAreas>  
    <ChartArea _Template_="All" BackColor="White" BorderColor="26, 59, 105" BorderWidth="0" BorderDashStyle="Solid">      <AxisY LineColor="204, 204, 204" TitleFont="{0}, 8pt, GdiCharSet=0" TitleForeColor="100, 100, 100" LabelAutoFitMaxFontSize="7" LabelAutoFitMinFontSize="7">  
        <MajorTickMark LineColor="Gray" />  
        <MajorGrid Enabled="false" />  
        <LabelStyle Font="{0}, 6.75pt, GdiCharSet=0" ForeColor="100, 100, 100" />  
      </AxisY>  
      <AxisX LineColor="204, 204, 204" TitleFont="{0}, 8pt, GdiCharSet=0" TitleForeColor="100, 100, 100" LabelAutoFitMaxFontSize="7" LabelAutoFitMinFontSize="7">        <MajorTickMark LineColor="Gray" />        <MajorGrid Enabled="false" />  
        <LabelStyle Font="{0}, 6.75pt, GdiCharSet=0" ForeColor="100, 100, 100" />  
      </AxisX>  
    </ChartArea>  
  </ChartAreas>  
  <Titles>  
    <Title _Template_="All" Font="{0}, 9pt, style=Bold, GdiCharSet=0" ForeColor="100, 100, 100"></Title>  
  </Titles>  
  <BorderSkin PageColor="Control" BackColor="CornflowerBlue" BackSecondaryColor="CornflowerBlue" />  
</Chart>  
```  
  
 Para obtener más cadenas XML de descripción de los datos de ejemplo, consulte [Gráficos de muestra](sample-charts.md).  
  
### <a name="see-also"></a>Vea también  
 [Visualizaciones (gráficos)](view-data-with-visualizations-charts.md)   
 [Acciones en visualizaciones (gráficos)](actions-visualizations-charts.md)   
 [Crear un gráfico](create-visualization-chart.md)   
 [Usar FetchXML para crear una consulta](../common-data-service/use-fetchxml-construct-query.md)   
 [Esquema de FetchXML](../common-data-service/fetchxml-schema.md) [Esquema de descripción de datos de visualización](visualization-data-description-schema.md)   
 [Gráficos de muestra](sample-charts.md)   
 [Clase de gráfico (Controles de gráficos de Microsoft)](https://msdn.microsoft.com/library/system.web.ui.datavisualization.charting.chart.aspx)
