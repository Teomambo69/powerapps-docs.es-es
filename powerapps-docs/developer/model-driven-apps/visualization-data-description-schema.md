---
title: Esquema de descripción de datos de visualización (aplicaciones basadas en modelos) | Microsoft Docs
description: A continuación, se ofrece el esquema para la cadena XML de descripción de datos para gráficos de visualización. Esto se puede usar para validar el contenido de la cadena XML de descripción de datos al crear un gráfico.
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
ms.openlocfilehash: 48bc0b00dbb5a2a75cb8bf5f87ca912db83e48f7
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753396"
---
# <a name="visualization-data-description-schema"></a>Esquema de descripción de los datos de visualización

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/visualization-data-description-schema -->

A continuación, se ofrece el esquema para la cadena XML de descripción de datos para gráficos de visualización. Esto se puede usar para validar el contenido de la cadena XML de descripción de datos al crear un gráfico. Para obtener más información, consulte [Descripción de los gráficos: representación de datos y gráficos subyacentes](understand-charts-underlying-data-chart-representation.md). [!INCLUDE[schema_download](../../includes/schema-download.md)] y ver el archivo `VisualizationDataDescription.xsd` en la carpeta.  
  
## <a name="schema"></a>Nombre del  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<xs:schema attributeFormDefault='unqualified'  
           elementFormDefault='qualified'  
           xmlns:xs='https://www.w3.org/2001/XMLSchema'>  
 <xs:element name='datadefinition'>  
  <xs:complexType>  
   <xs:sequence>  
    <xs:element name='fetchcollection'>  
     <xs:complexType>  
      <xs:sequence>  
       <xs:element maxOccurs='unbounded'  
                   name='fetch'>  
        <xs:annotation>  
         <!--FetchXML goes here-->  
        </xs:annotation>  
       </xs:element>  
      </xs:sequence>  
     </xs:complexType>  
    </xs:element>  
    <xs:element name='categorycollection'>  
     <xs:complexType>  
      <xs:sequence>  
       <xs:element name='category'  
                   type='CategoryType'  
                   minOccurs='1'  
                   maxOccurs='unbounded' />  
      </xs:sequence>  
     </xs:complexType>  
    </xs:element>  
   </xs:sequence>  
  </xs:complexType>  
 </xs:element>  
 <xs:complexType name ='CategoryType'>  
  <xs:sequence>  
   <xs:element minOccurs='1'  
               maxOccurs='unbounded'  
               name='measurecollection'>  
    <xs:complexType>  
     <xs:sequence>  
      <xs:element minOccurs='1'  
                  maxOccurs='unbounded'  
                  name='measure'>  
       <xs:complexType>  
        <xs:attribute name='alias'  
                      type='xs:string'  
                      use='required' />  
       </xs:complexType>  
      </xs:element>  
     </xs:sequence>  
    </xs:complexType>  
   </xs:element>  
  </xs:sequence>  
  <xs:attribute name='alias'  
                type='xs:string'  
                use='optional' />  
 </xs:complexType>  
</xs:schema>  
```  
### <a name="see-also"></a>Vea también  
 [Personalizar visualizaciones y paneles](customize-visualizations-dashboards.md)   
 [Descripción de los gráficos: representación de datos y gráficos subyacentes](understand-charts-underlying-data-chart-representation.md)   
 [Gráficos de muestra](sample-charts.md)   
 [Usar FetchXML para crear una consulta](../common-data-service/use-fetchxml-construct-query.md)