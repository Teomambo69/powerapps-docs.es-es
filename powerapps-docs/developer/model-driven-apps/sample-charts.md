---
title: Gráficos de ejemplo (aplicaciones basadas en modelos) | Microsoft Docs
description: El tema contiene gráficos de ejemplo junto con las respectivas cadenas XML de presentación y descripción de los datos.
ms.custom: ''
ms.date: 01/17/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 34ca8223ecf08bda2ed38353684a0971ab289b19
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749598"
---
# <a name="sample-charts"></a>Gráficos de muestra

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/sample-charts -->

Este tema contiene gráficos de ejemplo junto con las respectivas cadenas XML de presentación y descripción de los datos. Puede especificar lo siguiente:  
  
-   La *cadena XML de descripción de los datos* para un gráfico usando el atributo `SavedQueryVisualization.DataDescription` o `UserQueryVisualization.DataDescription` para el gráfico propiedad de la organización o del usuario, respectivamente.  
  
-   La *cadena XML de descripción de presentación* para un gráfico usando el atributo `SavedQueryVisualization.PresentationDescription` o `UserQueryVisualization. PresentationDescription` para el gráfico propiedad de la organización o del usuario, respectivamente.  
  
<a name="ColumnChart"></a>   
## <a name="column-chart"></a>Gráfico de columnas  
 A continuación se muestra un gráfico de columnas que muestra la cuenta por sector. Modificamos la descripción de la presentación del gráfico predeterminado de cuenta por sector existente disponible en aplicaciones basadas en modelos para que la entidad `Account` lo cambie por un gráfico de columnas.  
  
 ![Gráfico de columnas de muestra: cuentas por sector](media/charts-accounts-by-industry.gif "Gráfico de columnas de muestra: cuentas por sector")  
  
### <a name="data-description"></a>Descripción de los datos  
 A continuación se muestra el contenido de la cadena XML de descripción de los datos para este gráfico.  
  
```xml  
<datadefinition>  
  <fetchcollection>  
    <fetch mapping="logical" aggregate="true">  
      <entity name="account">  
        <attribute groupby="true" alias="groupby_column" name="industrycode" />  
        <attribute alias="aggregate_column" name="name" aggregate="count" />  
      </entity>  
    </fetch>  
  </fetchcollection>  
  <categorycollection>  
    <category>  
      <measurecollection>  
        <measure alias="aggregate_column" />  
      </measurecollection>  
    </category>  
  </categorycollection>  
</datadefinition>  
  
```  
  
### <a name="presentation-description"></a>Descripción de presentación  
 A continuación se muestra el contenido de la cadena XML de descripción de presentación para este gráfico.  
  
```xml  
<Chart>  
  <Series>  
    <Series ChartType="Column" IsValueShownAsLabel="True" Color="149, 189, 66" BackGradientStyle="TopBottom" BackSecondaryColor="112, 142, 50" Font="{0}, 9.5px" LabelForeColor="59, 59, 59" CustomProperties="MinPixelPointWidth=5, PointWidth=0.75, MaxPixelPointWidth=40">  
      <SmartLabelStyle Enabled="True" />  
    </Series>  
  </Series>  
  <ChartAreas>  
    <ChartArea BorderColor="White" BorderDashStyle="Solid">  
      <AxisY IsLabelAutoFit="False" TitleForeColor="59, 59, 59" TitleFont="{0}, 10.5px" LineColor="165, 172, 181" IsReversed="False">  
        <MajorGrid LineColor="239, 242, 246" />  
        <LabelStyle Font="{0}, 10.5px" ForeColor="59, 59, 59" />  
      </AxisY>  
      <AxisX IsLabelAutoFit="True" TitleForeColor="59, 59, 59" TitleFont="{0}, 10.5px" LineColor="165, 172, 181" IsReversed="False">  
        <MajorGrid Enabled="False" />  
        <MajorTickMark Enabled="False" />  
        <LabelStyle Font="{0}, 10.5px" ForeColor="59, 59, 59" />  
      </AxisX>  
    </ChartArea>  
  </ChartAreas>  
  <Titles>  
    <Title Name="Chart Title" DockingOffset="-3" Font="{0}, 13px" ForeColor="59, 59, 59" Alignment="TopLeft"></Title>  
  </Titles>  
</Chart>  
```  
  
<a name="BarChart"></a>   
## <a name="bar-chart"></a>Gráfico de barras  
 A continuación se muestra un gráfico de barras que muestra los 10 clientes principales. Este es uno de los gráficos predeterminados disponibles en MDA para la entidad `Opportunity`.  
  
 ![Gráfico de barras de muestra: 10 clientes principales](media/charts-top-10-customers.gif "Gráfico de barras de muestra: 10 clientes principales")  
  
### <a name="data-description"></a>Descripción de los datos  
 A continuación se muestra el contenido de la cadena XML de descripción de los datos para este gráfico.  
  
```xml  
<datadefinition>  
  <fetchcollection>  
    <fetch mapping="logical" count="10" aggregate="true">  
      <entity name="opportunity">  
        <attribute name="estimatedvalue" aggregate="sum" alias="sum_estimatedvalue" />  
        <attribute name="customerid" groupby="true" alias="customerid" />  
        <order alias="sum_estimatedvalue" descending="true" />  
      </entity>  
    </fetch>  
  </fetchcollection>  
  <categorycollection>  
    <category>  
      <measurecollection>  
        <measure alias="sum_estimatedvalue" />  
      </measurecollection>  
    </category>  
  </categorycollection>  
</datadefinition>  
  
```  
  
### <a name="presentation-description"></a>Descripción de presentación  
 A continuación se muestra el contenido de la cadena XML de descripción de presentación para este gráfico.  
  
```xml  
<Chart>  
  <Series>  
    <Series ChartType="Bar" IsValueShownAsLabel="True" Color="149, 189, 66" BackGradientStyle="TopBottom" BackSecondaryColor="112, 142, 50" Font="{0}, 9.5px" LabelForeColor="59, 59, 59" CustomProperties="MinPixelPointWidth=5, PointWidth=0.75, MaxPixelPointWidth=40">  
      <SmartLabelStyle Enabled="True" />  
    </Series>  
  </Series>  
  <ChartAreas>  
    <ChartArea BorderColor="White" BorderDashStyle="Solid">  
      <AxisY IsLabelAutoFit="False" TitleForeColor="59, 59, 59" TitleFont="{0}, 10.5px" LineColor="165, 172, 181" IsReversed="False">  
        <MajorGrid LineColor="239, 242, 246" />  
        <LabelStyle Font="{0}, 10.5px" ForeColor="59, 59, 59" />  
      </AxisY>  
      <AxisX IsLabelAutoFit="False" TitleForeColor="59, 59, 59" TitleFont="{0}, 10.5px" LineColor="165, 172, 181" IsReversed="False">  
        <MajorGrid Enabled="False" />  
        <MajorTickMark Enabled="False" />  
        <LabelStyle Font="{0}, 10.5px" ForeColor="59, 59, 59" />  
      </AxisX>  
    </ChartArea>  
  </ChartAreas>  
  <Titles>  
    <Title DockingOffset="-3" Font="{0}, 13px" ForeColor="59, 59, 59" Alignment="TopLeft"></Title>  
  </Titles>  
</Chart>  
```  
  
<a name="AreaChart"></a>   
## <a name="area-chart"></a>Gráfico de área  
 A continuación se muestra un gráfico de áreas que muestra el número de registros generados entre un intervalo de fechas determinado.  
  
 ![Gráfico de áreas de ejemplo](media/charts-count-of-records-areachart.gif "Gráfico de áreas de ejemplo")  
  
### <a name="data-description"></a>Descripción de los datos  
 A continuación se muestra el contenido de la cadena XML de descripción de los datos para este gráfico.  
  
```xml
<datadefinition>  
      <fetchcollection>  
        <fetch mapping="logical" aggregate="true">  
          <entity name="incident">  
            <attribute name="createdon" groupby="true" alias="_CRMAutoGen_groupby_column_Num_0" dategrouping="day" />  
            <attribute name="incidentid" aggregate="count" alias="_CRMAutoGen_aggregate_column_Num_0" />  
          </entity>  
        </fetch>  
      </fetchcollection>  
      <categorycollection>  
        <category alias="_CRMAutoGen_groupby_column_Num_0">  
          <measurecollection>  
            <measure alias="_CRMAutoGen_aggregate_column_Num_0" />  
          </measurecollection>  
        </category>  
      </categorycollection>  
    </datadefinition>   
```  
  
### <a name="presentation-description"></a>Descripción de presentación  
 A continuación se muestra el contenido de la cadena XML de descripción de presentación para este gráfico.  
  
```xml
<Chart Palette="None" PaletteCustomColors="149,189,66; 197,56,52; 55,118,193; 117,82,160; 49,171,204; 255,136,35; 168,203,104; 209,98,96; 97,142,206; 142,116,178; 93,186,215; 255,155,83">  
      <Series>  
        <Series ChartType="StackedArea" Font="{0}, 9.5px" LabelForeColor="59, 59, 59" CustomProperties="PointWidth=0.75, MaxPixelPointWidth=40" />  
      </Series>  
      <ChartAreas>  
        <ChartArea BorderColor="White" BorderDashStyle="Solid">  
          <AxisY LabelAutoFitMinFontSize="8" TitleForeColor="59, 59, 59" TitleFont="{0}, 10.5px" LineColor="165, 172, 181" IntervalAutoMode="VariableCount">  
            <MajorGrid LineColor="239, 242, 246" />  
            <MajorTickMark LineColor="165, 172, 181" />  
            <LabelStyle Font="{0}, 10.5px" ForeColor="59, 59, 59" />  
          </AxisY>  
          <AxisX LabelAutoFitMinFontSize="8" TitleForeColor="59, 59, 59" TitleFont="{0}, 10.5px" LineColor="165, 172, 181" IntervalAutoMode="VariableCount">  
            <MajorTickMark LineColor="165, 172, 181" />  
            <MajorGrid LineColor="Transparent" />  
            <LabelStyle Font="{0}, 10.5px" ForeColor="59, 59, 59" />  
          </AxisX>  
        </ChartArea>  
      </ChartAreas>  
      <Titles>  
        <Title Alignment="TopLeft" DockingOffset="-3" Font="{0}, 13px" ForeColor="59, 59, 59" />  
      </Titles>  
      <Legends>  
        <Legend Alignment="Center" LegendStyle="Table" Docking="right" IsEquallySpacedItems="True" Font="{0}, 11px" ShadowColor="0, 0, 0, 0" ForeColor="59, 59, 59" />  
      </Legends>  
    </Chart>  
```  
  
<a name="LineChart"></a>   
## <a name="line-chart"></a>Gráfico de líneas  
 A continuación se muestra un gráfico de líneas que muestra el número de clientes potenciales generados en los cinco últimos meses. Este es uno de los gráficos predeterminados disponibles en MDA para la entidad `Lead`. 
  
![Gráfico de líneas de muestra: tasa de generación de clientes potenciales](media/lead-generation-rate-chart.png "Gráfico de líneas de muestra: tasa de generación de clientes potenciales") --> 
  
### <a name="data-description"></a>Descripción de los datos  
 A continuación se muestra el contenido de la cadena XML de descripción de los datos para este gráfico.  
  
```xml  
<datadefinition>  
  <fetchcollection>  
    <fetch mapping="logical" count="5" aggregate="true">  
      <entity name="lead">  
        <attribute name="leadid" aggregate="countcolumn" alias="count_leadid" />  
        <attribute name="createdon" groupby="true" dategrouping="month" usertimezone="false" alias="createdon" />  
        <order alias="createdon" descending="false" />  
      </entity>  
    </fetch>  
  </fetchcollection>  
  <categorycollection>  
    <category>  
      <measurecollection>  
        <measure alias="count_leadid" />  
      </measurecollection>  
    </category>  
  </categorycollection>  
</datadefinition>  
```  
  
### <a name="presentation-description"></a>Descripción de presentación  
 A continuación se muestra el contenido de la cadena XML de descripción de presentación para este gráfico.  
  
```xml  
<Chart>  
  <Series>  
    <Series IsValueShownAsLabel="True" BorderWidth="3" ChartType="Line" Color="49, 171, 204" MarkerStyle="Square" MarkerSize="9" MarkerColor="37, 128, 153"></Series>  
  </Series>  
  <ChartAreas>  
    <ChartArea BorderColor="White">  
      <AxisY LabelAutoFitMinFontSize="8" TitleForeColor="59, 59, 59" TitleFont="{0}, 10.5px" LineColor="165, 172, 181">  
        <MajorGrid LineColor="239, 242, 230" />  
        <MajorTickMark LineColor="165, 172, 181" />  
        <LabelStyle Font="{0}, 10.5px" ForeColor="59, 59, 59" />  
      </AxisY>  
      <AxisX LabelAutoFitMinFontSize="8" TitleForeColor="59, 59, 59" TitleFont="{0}, 10.5px" LineColor="165, 172, 181">  
        <MajorGrid Enabled="False" />  
        <LabelStyle Font="{0}, 10.5px" ForeColor="59, 59, 59" />  
      </AxisX>  
    </ChartArea>  
  </ChartAreas>  
  <Titles>  
    <Title DockingOffset="-3" Font="{0}, 13px" ForeColor="59, 59, 59" Alignment="TopLeft"></Title>  
  </Titles>  
</Chart>  
```  
  
<a name="PieChart"></a>   
## <a name="pie-chart"></a>Gráfico circular  
 A continuación se muestra un gráfico circular que muestra la cantidad total de clientes potenciales y su importancia. Este es uno de los gráficos predeterminados disponibles en MDA para la entidad `Lead`.  
  
 ![Gráfico circular de muestra: clientes potenciales por nivel de interés](media/leads-by-source-chart.png "Gráfico circular de muestra: clientes potenciales por nivel de interés")  
  
### <a name="data-description"></a>Descripción de los datos  
 A continuación se muestra el contenido de la cadena XML de descripción de los datos para este gráfico.  
  
```xml  
<datadefinition>  
  <fetchcollection>  
    <fetch mapping="logical" aggregate="true">  
      <entity name="lead">  
        <attribute groupby="true" alias="groupby_column" name="leadqualitycode" />  
        <attribute alias="aggregate_column" name="fullname" aggregate="count" />  
      </entity>  
    </fetch>  
  </fetchcollection>  
  <categorycollection>  
    <category>  
      <measurecollection>  
        <measure alias="aggregate_column" />  
      </measurecollection>  
    </category>  
  </categorycollection>  
</datadefinition>  
  
```  
  
### <a name="presentation-description"></a>Descripción de presentación  
 A continuación se muestra el contenido de la cadena XML de descripción de presentación para este gráfico.  
  
```xml  
<Chart Palette="None" PaletteCustomColors="97,142,206; 209,98,96; 168,203,104; 142,116,178; 93,186,215; 255,155,83; 148,172,215; 217,148,147; 189,213,151; 173,158,196; 145,201,221; 255,180,138">  
  <Series>  
    <Series ShadowOffset="0" IsValueShownAsLabel="true" Font="{0}, 9.5px" LabelForeColor="59, 59, 59" CustomProperties="PieLabelStyle=Inside, PieDrawingStyle=Default" ChartType="pie">  
      <SmartLabelStyle Enabled="True" />  
    </Series>  
  </Series>  
  <ChartAreas>  
    <ChartArea>  
      <Area3DStyle Enable3D="false" />  
    </ChartArea>  
  </ChartAreas>  
  <Legends>  
    <Legend Alignment="Center" LegendStyle="Table" Docking="right" Font="{0}, 11px" ShadowColor="0, 0, 0, 0" ForeColor="59, 59, 59" />  
  </Legends>  
  <Titles>  
    <Title Alignment="TopLeft" DockingOffset="-3" Font="{0}, 13px" ForeColor="0, 0, 0"></Title>  
  </Titles>  
</Chart>  
```  
  
<a name="FunnelChart"></a>   
## <a name="funnel-chart"></a>Gráfico de embudo  
 A continuación se muestra un gráfico de embudo que muestra la suma de los ingresos estimados en cada etapa de la canalización de ventas. Este es uno de los gráficos predeterminados disponibles en MDA para la entidad `Opportunity`.  
  
 ![Gráfico de embudo de muestra: canalización de ventas](media/charts-sales-pipeline-chart.png "Gráfico de embudo de muestra: canalización de ventas")  
  
### <a name="data-description"></a>Descripción de los datos  
 A continuación se muestra el contenido de la cadena XML de descripción de los datos para este gráfico.  
  
```xml  
<datadefinition>  
  <fetchcollection>  
    <fetch mapping="logical" count="10" aggregate="true">  
      <entity name="opportunity">  
        <attribute name="estimatedvalue" aggregate="sum" alias="sum_estimatedvalue" />  
        <attribute name="stepname" groupby="true" alias="stepname" />  
        <order alias="stepname" descending="false" />  
      </entity>  
    </fetch>  
  </fetchcollection>  
  <categorycollection>  
    <category>  
      <measurecollection>  
        <measure alias="sum_estimatedvalue" />  
      </measurecollection>  
    </category>  
  </categorycollection>  
</datadefinition>  
```  
  
### <a name="presentation-description"></a>Descripción de presentación  
 A continuación se muestra el contenido de la cadena XML de descripción de presentación para este gráfico.  
  
```xml  
<Chart Palette="None" PaletteCustomColors="55,118,193; 197,56,52; 149,189,66; 117,82,160; 49,171,204; 255,136,35; 97,142,206; 209,98,96; 168,203,104; 142,116,178; 93,186,215; 255,155,83">  
  <Series>  
    <Series ShadowOffset="0" IsValueShownAsLabel="true" Font="{0}, 9.5px" LabelForeColor="59, 59, 59" ChartType="Funnel" CustomProperties="FunnelLabelStyle=Outside, FunnelNeckHeight=0, FunnelPointGap=1, FunnelNeckWidth=5">  
      <SmartLabelStyle Enabled="True" />  
    </Series>  
  </Series>  
  <ChartAreas>  
    <ChartArea>  
      <Area3DStyle Enable3D="True" />  
    </ChartArea>  
  </ChartAreas>  
  <Legends>  
    <Legend Alignment="Center" LegendStyle="Table" Docking="right" Font="{0}, 11px" ShadowColor="0, 0, 0, 0" ForeColor="59, 59, 59" />  
  </Legends>  
  <Titles>  
    <Title Alignment="TopLeft" DockingOffset="-3" Font="Segeo UI, 13px" ForeColor="0, 0, 0"></Title>  
  </Titles>  
</Chart>  
```  
  
<a name="MultiSeriesChart"></a> 
  
## <a name="multi-series-chart"></a>Gráfico de varias series  

 A continuación se muestra un gráfico de varias series que muestra los ingresos estimados frente a los ingresos reales cerrados por mes. Puede usar el diseñador de gráficos en MDA o los métodos descritos en la documentación para desarrolladores para crear estos tipos de gráficos.  
  
 Un gráfico de varias series tiene varios elementos `<measurecollection>` en la descripción de los datos, cada uno asignado al elemento `<Series>` correspondiente en la cadena XML de descripción de presentación  
  
 Un gráfico de varias series tiene varios elementos `<Series>` en la descripción de presentación; el número de elementos `<Series>` es el mismo que el número de elementos `<measurecollection>` en la cadena XML de descripción de los datos.  
  
 ![Gráfico de varias series de muestra](media/estimated-actual-revenue-chart.gif "Gráfico de varias series de muestra")  
  
### <a name="data-description"></a>Descripción de los datos  
 A continuación se muestra el contenido de la cadena XML de descripción de los datos para este gráfico.  
  
```xml  
<datadefinition>  
  <fetchcollection>  
    <fetch mapping="logical" aggregate="true">  
      <entity name="opportunity">  
        <attribute name="estimatedvalue" aggregate="sum" alias="estvalue" />  
        <attribute name="actualvalue" aggregate="sum" alias="actvalue" />  
        <attribute name="actualclosedate" groupby="true" alias="actclosedate" dategrouping="month" />  
      </entity>  
    </fetch>  
  </fetchcollection>  
  <categorycollection>  
    <category>  
      <measurecollection>  
        <measure alias="estvalue" />  
      </measurecollection>  
      <measurecollection>  
        <measure alias="actvalue" />  
      </measurecollection>  
    </category>  
  </categorycollection>  
</datadefinition>  
  
```  
  
### <a name="presentation-description"></a>Descripción de presentación  
 A continuación se muestra el contenido de la cadena XML de descripción de presentación para este gráfico.  
  
```xml  
<Chart Palette="BrightPastel">  
  <Series>  
    <Series _Template_="All" Color="112, 162, 213" BorderColor="164, 164, 164" BorderDashStyle="Solid" BorderWidth="1" ShadowColor="128, 128, 128, 128" ShadowOffset="1" IsValueShownAsLabel="true" Font="{0}, 6.75pt, GdiCharSet=0" BackGradientStyle="TopBottom" BackSecondaryColor="0, 102, 153" LabelForeColor="100, 100, 100" ChartType="Column">  
      <SmartLabelStyle Enabled="True" />  
      <Points />  
    </Series>  
    <Series _Template_="All" Color="204,0,0" BorderColor="204,0,0" BorderDashStyle="Solid" BorderWidth="1" ShadowColor="128, 128, 128, 128" ShadowOffset="1" IsValueShownAsLabel="true" Font="{0}, 6.75pt, GdiCharSet=0" BackSecondaryColor="0, 102, 153" LabelForeColor="100, 100, 100" ChartType="Column">  
      <SmartLabelStyle Enabled="True" />  
      <Points />  
    </Series>  
  </Series>  
  <ChartAreas>  
    <ChartArea _Template_="All" BackColor="White" BorderColor="26, 59, 105" BorderWidth="0" BorderDashStyle="Solid">  
      <AxisY LineColor="204, 204, 204" TitleFont="{0}, 8pt, GdiCharSet=0" TitleForeColor="100, 100, 100" LabelAutoFitMaxFontSize="7" LabelAutoFitMinFontSize="7">  
        <MajorTickMark LineColor="Gray" />  
        <MajorGrid Enabled="false" />  
        <LabelStyle Font="{0}, 6.75pt, GdiCharSet=0" ForeColor="100, 100, 100" />  
      </AxisY>  
      <AxisX LineColor="204, 204, 204" TitleFont="{0}, 8pt, GdiCharSet=0" TitleForeColor="100, 100, 100" LabelAutoFitMaxFontSize="7" LabelAutoFitMinFontSize="7">  
        <MajorTickMark LineColor="Gray" />  
        <MajorGrid Enabled="false" />  
        <LabelStyle Font="{0}, 6.75pt, GdiCharSet=0" ForeColor="100, 100, 100" />  
      </AxisX>  
      <Area3DStyle LightStyle="Realistic" IsClustered="True" />  
    </ChartArea>  
  </ChartAreas>  
  <Legends>  
    <Legend _Template_="All" Alignment="Center" LegendStyle="Table" Docking="Bottom" IsEquallySpacedItems="True" BackColor="White" BorderColor="228, 228, 228" BorderWidth="0" Font="{0}, 8pt, GdiCharSet=0" ShadowColor="0, 0, 0, 0" ForeColor="100, 100, 100"></Legend>  
  </Legends>  
  <Titles>  
    <Title _Template_="All" Font="{0}, 9pt, style=Bold, GdiCharSet=0" ForeColor="100, 100, 100"></Title>  
  </Titles>  
  <BorderSkin PageColor="Control" BackColor="CornflowerBlue" BackSecondaryColor="CornflowerBlue" />  
</Chart>  
  
```  
  
<a name="ComparisonChart"></a>   
## <a name="comparison-chart-stacked-chart"></a>Gráfico de comparación (gráfico apilado)  
 A continuación se muestra un gráfico de comparación que muestra el número de actividades por tipo y prioridad. Puede usar el diseñador de gráficos en MDA o los métodos descritos en la documentación para desarrolladores para crear estos tipos de gráficos.  
  
 Un gráfico de comparación tiene dos cláusulas `groupby` en la cadena XML de descripción de los datos.  
  
 ![Gráfico de comparación de muestra](media/charts-activities-by-type-and-priority-comparison-chart.gif "Gráfico de comparación de muestra")  
  
### <a name="data-description"></a>Descripción de los datos  
 A continuación se muestra el contenido de la cadena XML de descripción de los datos para este gráfico.  
  
```xml  
<datadefinition>  
  <fetchcollection>  
    <fetch mapping="logical" aggregate="true">  
      <entity name="activitypointer">  
        <attribute alias="aggregate_column" name="subject" aggregate="count" />  
        <attribute groupby="true" alias="groupby_column" name="activitytypecode" />  
        <attribute groupby="true" alias="groupby_priority" name="prioritycode" />  
      </entity>  
    </fetch>  
  </fetchcollection>  
  <categorycollection>  
    <category>  
      <measurecollection>  
        <measure alias="aggregate_column" />  
      </measurecollection>  
    </category>  
  </categorycollection>  
</datadefinition>  
  
```  
  
### <a name="presentation-description"></a>Descripción de presentación  
 A continuación se muestra el contenido de la cadena XML de descripción de presentación para este gráfico.  
  
```xml  
<Chart Palette="None" PaletteCustomColors="41,88,145; 147, 42, 39; 112,142,50; 88,62,120; 37,128,153; 194,103,28; 74,107,155; 155,77,73; 126,153,79; 107,88,134; 71,140,162; 199,118,64; 112,131,162;164,112,111; 143,161,115;131,120,148;111,152,167; 195,137,106">  
  <Series>  
    <Series Name="Series1" ChartType="StackedColumn" ChartArea="ChartArea1" IsValueShownAsLabel="True" Font="{0}, 9.5px" LabelForeColor="59, 59, 59" CustomProperties="MinPixelPointWidth=5, PointWidth=0.75, PixelPointWidth=26, MaxPixelPointWidth=40"></Series>  
  </Series>  
  <ChartAreas>  
    <ChartArea BorderColor="Transparent" BorderDashStyle="Solid" Name="ChartArea1">  
      <AxisY TitleForeColor="59, 59, 59" TitleFont="{0}, 10.5px" LineColor="165, 172, 181" IntervalAutoMode="VariableCount">  
        <MajorGrid LineColor="239, 242, 246" />  
        <MajorTickMark LineColor="165, 172, 181" />  
        <LabelStyle Font="{0}, 10.5px" ForeColor="59, 59, 59" />  
      </AxisY>  
      <AxisX TitleForeColor="59, 59, 59" TitleFont="{0}, 10.5px" LineColor="165, 172, 181" IntervalAutoMode="VariableCount">  
        <MajorGrid LineColor="Transparent" />  
        <MajorTickMark LineDashStyle="NotSet" />  
        <LabelStyle Font="{0}, 10.5px" ForeColor="59, 59, 59" />  
      </AxisX>  
    </ChartArea>  
  </ChartAreas>  
  <Legends>  
    <Legend Alignment="Center" LegendStyle="Table" Docking="Bottom" IsEquallySpacedItems="True" Font="{0}, 11px" ShadowColor="0, 0, 0, 0" ForeColor="59,59,59"></Legend>  
  </Legends>  
  <Titles>  
    <Title Alignment="TopLeft" Name="Title1" DockingOffset="-3" Font="{0}, 13px" ForeColor="59, 59, 59"></Title>  
  </Titles>  
</Chart>  
  
```  
  
<a name="StackedChart"></a>   

## <a name="comparison-chart-100-stacked-chart"></a>Gráfico de comparación (gráfico 100% apilado)  

 A continuación se muestra un gráfico de comparación que muestra el número de casos abierto en cualquier fecha, agrupados por prioridad. Puede usar el diseñador de gráficos en MDA o los métodos disponibles en servicios web para crear estos tipos de gráficos.  
  
 Un gráfico de comparación tiene dos cláusulas `groupby` en la cadena XML de descripción de los datos.  
  
 ![Gráfico apilado Sample100%](media/charts-numberofcases-anydate-bypriority-100stackedchart.gif "Gráfico apilado Sample100%")  
  
### <a name="data-description"></a>Descripción de los datos  
 A continuación se muestra el contenido de la cadena XML de descripción de los datos para este gráfico.  
  
```xml  
<datadefinition>  
      <fetchcollection>  
        <fetch mapping="logical" aggregate="true">  
          <entity name="incident">  
            <order alias="groupby_column" descending="false" />  
            <attribute alias="aggregate_column" name="incidentid" aggregate="count" />  
            <attribute groupby="true" alias="groupby_column" dategrouping="day" name="createdon" />  
            <attribute groupby="true" alias="groupby_priority" name="prioritycode" />  
          </entity>  
        </fetch>  
      </fetchcollection>  
      <categorycollection>  
        <category>  
          <measurecollection>  
            <measure alias="aggregate_column" />  
          </measurecollection>  
        </category>  
      </categorycollection>  
    </datadefinition>  
  
```  
  
### <a name="presentation-description"></a>Descripción de presentación  
 A continuación se muestra el contenido de la cadena XML de descripción de presentación para este gráfico.  
  
```xml  
<Chart Palette="None" PaletteCustomColors="149,189,66; 197,56,52; 55,118,193; 117,82,160; 49,171,204; 255,136,35; 168,203,104; 209,98,96; 97,142,206; 142,116,178; 93,186,215; 255,155,83">  
      <Series>  
        <Series ChartType="StackedBar100" Font="{0}, 9.5px" LabelForeColor="59, 59, 59" CustomProperties="PointWidth=0.75, MaxPixelPointWidth=40">  
          <SmartLabelStyle Enabled="True" />  
        </Series>  
      </Series>  
      <ChartAreas>  
        <ChartArea BorderColor="White" BorderDashStyle="Solid">  
          <AxisY LabelAutoFitMinFontSize="8" TitleForeColor="59, 59, 59" TitleFont="{0}, 10.5px" LineColor="165, 172, 181" IntervalAutoMode="VariableCount">  
            <MajorGrid LineColor="239, 242, 246" />  
            <MajorTickMark LineColor="165, 172, 181" />  
            <LabelStyle Font="{0}, 10.5px" ForeColor="59, 59, 59" />  
          </AxisY>  
          <AxisX LabelAutoFitMinFontSize="8" TitleForeColor="59, 59, 59" TitleFont="{0}, 10.5px" LineColor="165, 172, 181" IntervalAutoMode="VariableCount">  
            <MajorGrid Enabled="False" />  
            <MajorTickMark Enabled="False" />  
            <LabelStyle Font="{0}, 10.5px" ForeColor="59, 59, 59" />  
          </AxisX>  
        </ChartArea>  
      </ChartAreas>  
      <Titles>  
        <Title Alignment="TopLeft" DockingOffset="-3" Font="{0}, 13px" ForeColor="0, 0, 0" />  
      </Titles>  
    </Chart>  
```  
  
### <a name="see-also"></a>Vea también  
 [Análisis y la visualización de datos](customize-visualizations-dashboards.md)   
 [Esquema de descripción de los datos de visualización](visualization-data-description-schema.md)   
 [Crear un gráfico](create-visualization-chart.md)   
 [Ver los datos con visualizaciones (gráficos)](view-data-with-visualizations-charts.md)   
 

