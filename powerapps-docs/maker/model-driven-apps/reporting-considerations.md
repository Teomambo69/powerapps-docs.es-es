---
title: Consideraciones sobre los informes | MicrosoftDocs
ms.custom: ''
ms.date: 09/27/2019
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 for Customer Engagement (online)
- powerapps
ms.assetid: cb1bb002-8300-43bb-ab75-99e7a9c9c35d
caps.latest.revision: 11
author: Mattp123
ms.author: matp
manager: kvivek
tags:
- MigrationHO
search.audienceType:
- customizer
search.app:
- D365CE
ms.openlocfilehash: d3600ad3c1f0953ff3aef5786c62afebca43b4c4
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755067"
---
# <a name="reporting-considerations"></a>Consideraciones sobre informes

Las aplicaciones basadas en modelo tienen varias características que permiten que los clientes busquen datos profesionales que les ayudan a tomar decisiones e interactuar con sus clientes de forma más eficaz.  Las funciones que están disponibles incluyen vistas, gráficos, paneles e informes de SQL Server Reporting Services. También incluyen integración de Microsoft Excel que permite a los usuarios crear fácilmente informes de autoservicio utilizando las características de Power BI [PowerView](https://support.office.com/article/power-view-overview-and-learning-5380e429-3ee0-4be2-97b7-64d7930020b6), [PowerPivot](https://support.office.com/article/power-pivot-overview-and-learning-f9001958-7901-4caa-ad80-028a6d2432ed) y [PowerQuery](https://support.office.com/article/power-query-overview-and-learning-ed614c81-4b00-4291-bd3a-55d80767f81d). A medida que el volumen de datos contenidos en la base de datos de aplicaciones sigue creciendo, se hace cada vez más importante que pensar en la estrategia de BI y determinar los mecanismos más eficaces para generar informes y ver conjuntos de datos grandes.  
  
 En un entorno, la infraestructura de informes está compartida y separada de la base de datos. En esta arquitectura, aunque los clientes compartan los recursos necesarios ejecutar el informe, cada informe se ejecuta con la instancias individuales de la base de datos de los clientes.  Además, los usuarios pueden ejecutar tantos informes como necesiten siempre que deseen ejecutarlos para cumplir objetivos empresariales.  No ponemos restricciones de tiempo en informes.  
  
 Las capacidades de informes integradas en Common Data Service están diseñadas para permitir que los usuarios ejecuten informes en conjuntos de datos que abarcan períodos de tiempo más cortos. Considerando esto, observe los siguientes valores fijos:  
  
- Los informes y las consultas pueden ejecutarse durante hasta cinco minutos. Cuando se alcanza el período máximo, el informe agota el tiempo de espera y un mensaje se devuelve al usuario. En la duración de cinco minutos, se permite que informes y consultas abarquen conjuntos de datos grandes de más de 50.000 registros, lo que proporciona flexibilidad significativa para satisfacer la mayoría de las necesidades operativas de los informes.  
  
- Para mejorar la respuesta de la consulta, es recomendable que los informes detallados minimicen la visualización de un gran número de registros. Para ello, aplique el filtrado conveniente para reducir el número de registros que se devuelven. Al crear informes agregados o resumidos, las consultas deben impulsar la agregación a la consulta en lugar de recoger registros detallados para realizar agregación en el informe.  Esto se puede hacer mediante agregación Fetch XML. <!-- More information: [Use FetchXML aggregation](../developer/use-fetchxml-aggregation.md)  -->
  
- Para los gráficos y cuadrículas que se muestran en paneles, las aplicaciones permiten que los usuarios ejecuten consultas que tienen un conjunto de datos de menos de 50.000 filas. Si un usuario ejecuta una consulta de panel de ventas que abarca un conjunto de datos de 50.000 o más filas, devuelve el mensaje "Se ha superado el límite de registros máximos. Reducir el número de registros para sincronizar."  La configuración práctica del conjunto de datos ayuda a asegurar el rendimiento óptimo de la aplicación.  
 
  
<a name="BKMK_ReportTips"></a>   
## <a name="tips-and-solutions-for-reporting"></a>Consejos y soluciones para informes  
 Generalmente estos valores suelen ser adecuados para la mayoría de las necesidades de informes de las organizaciones. Para asegurarse de que los usuarios no excedan estos valores y para mejorar el rendimiento de consulta de informes en general, considere las recomendaciones siguientes.  
  
- Al crear informes o paneles personalizados, diséñelos para consultar conjuntos de datos más pequeños durante períodos de tiempo más cortos agregando un filtro de tiempo en el informe, como un mes o trimestre actual, para limitar los resultados.  
  
- Se recomienda que limite el número de entidades que son necesarias para devolver el resultado. Esto ayuda a reducir el tiempo necesario para la consulta y para devolver el conjunto de resultados.  
  
- Se recomienda reducir el número de registros que se muestra en los informes detallados. El filtrado conveniente se puede usar para reducir el número de registros devuelto por la consulta para reducir tiempos de espera.  
  
- Para informes agregados o resumidos, deben utilizarse consultas para impulsar la agregación a la base de datos y no recoger registros detallados y realizar agregación en el informe de SQL Server Reporting Services.  
  
- Cuando es adecuado para su negocio, los usuarios deben ejecutar informes y paneles predeterminados (predefinidos). Estos informes y paneles normalmente están diseñados para consultar conjuntos de datos de usuarios, por lo que en la mayoría de los casos no excederán el límite del conjunto de datos.  
  
  Si los usuarios deben ejecutar informes que exceden esta configuración, se recomienda revisar las siguientes opciones para obtener ayuda con necesidades de informes complejas. Ambas opciones descargan con eficacia las cargas de trabajo de informes desde Common Data Service a otro almacén de datos mediante una solución de integración de datos.  
  
- Los [Adaptadores](reporting-considerations.md#BKMK_ThirdPartyAdapt) se usan junto con SQL Server Integration Services (SSIS) para ampliar las funciones para la integración con los datos de aplicaciones.  
  
- Las [herramientas Extraer, transformar y cargar (ETL)](reporting-considerations.md#BKMK_ETL) proporcionan un nuevo conjunto de herramientas para crear análisis de los datos combinando varios orígenes de datos o extrayendo datos a la solución del almacén de datos si SSIS no está en uso. Las herramientas ETL proporcionan soluciones completas para conectar con Common Data Service para mover datos.  
  
> [!IMPORTANT]
>  Al usar estas herramientas, es recomendable que mueva o sincronice los datos en horas sin actividad de negocio.  
  
 Si es necesario, hay muchos asociados de Microsoft que pueden ayudarle a proporcionar una solución para las necesidades de informes específicas. como crear una copia sin conexión de los datos usados específicamente para ejecutar informes grandes.  Estos asociados conocen las herramientas de integración de datos disponibles. Más información: [Buscar un asociado de Dynamics 365](https://dynamics.microsoft.com/partners/find-a-partner/)  
  
<a name="BKMK_ThirdPartyAdapt"></a>   
## <a name="third-party-adapters-for-ssis"></a>Adaptadores de terceros para SSIS  
  
-   [Componente CozyRoc SSIS+ para Dynamics 365/CRM](https://www.cozyroc.com/ssis/dynamics-crm)  
  
-   [Kit de herramientas de integración de KingswaySoft SSIS para Dynamics 365](https://www.kingswaysoft.com/products/ssis-integration-toolkit-for-microsoft-dynamics-365)  
  
-   [Componentes de CData SSIS para Dynamics 365](https://www.cdata.com/ssis/components/)  
  
-   [Conector Team4 SSIS para Dynamics 365](https://www.team4.de/microsoft-dynamics-365-crm/)  
  
<!--    [PragmaticWorks TaskFactory SSIS Source/Destination for Dynamics CRM](https://pragmaticworks.com/Products/Task-Factory/Features/DynamicsCRMSource.aspx)  -->
  
<a name="BKMK_ETL"></a>   
## <a name="etl-tools"></a>Herramientas ETL  
  
-   [Integración con TIBCO Dynamics 365](https://www.tibco.com/solutions/microsoft-dynamics-365-integration)  <br />
  
<!--   [Productivity tools from Informatica](https://community.informatica.com/community/search.jspa?peopleEnabled=true&userID=&containerType=14&container=2002&spotlight=true&resultTypes=solution&q=dynamics+CRM)  -->
  
### <a name="see-also"></a>Vea también  
 [Extensión de creación de informes (con compatibilidad con SQL Server Data Tools)](https://www.microsoft.com/download/details.aspx?id=45013) <br />
  
 [Introducción a Microsoft Power Query para Excel](https://office.microsoft.com/en-ca/excel-help/introduction-to-microsoft-power-query-for-excel-HA104003940.aspx?CTT=5&origin=HA104003813)   <br />
 [Fuentes de OData y Power Query de Dynamics 365 for Customer Engagement: ¿Qué es el [registro?](https://community.dynamics.com/crm/b/survivingcrm/archive/2014/02/16/dynamics-crm-odata-feeds-and-power-query-what-s-the-record.aspx)   <br />
 

