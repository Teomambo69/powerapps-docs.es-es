---
title: Preparación de los datos de autoservicio con flujos de datos en PowerApps | MicrosoftDocs
description: Aprenda a usar flujos de datos en PowerApps para preparar los datos
ms.custom: ''
ms.date: 08/05/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ''
caps.latest.revision: ''
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 32fb0c402fce458f728b44c63e337fe07b36fd76
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754671"
---
<!--note from editor: I think "dataflows" should be lowercase based on this entry in the Microsoft style guide (scroll down to find dataflows): https://styleguides.azurewebsites.net/Styleguide/Read?id=2696&topicid=42299 -->



# <a name="self-service-data-prep-with-dataflows"></a>Preparación de los datos de autoservicio con flujos de datos
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

A medida que el volumen de datos sigue creciendo, también aumenta el reto de dar forma a los datos en información bien estructurada y procesable. Conviene que los datos estén listo para aplicaciones, cargas de trabajo de IA o análisis para poder convertir rápidamente volúmenes de datos en información procesable. Con la preparación de los datos de autoservicio en el portal de PowerApps, puede transformar y cargar los datos en Common Data Service o la cuenta de Azure Data Lake Storage Gen2 en solo unos clics.

Los flujos de datos se introdujeron para ayudar a las organizaciones a unificar datos de orígenes dispares y a prepararlos para el consumo. Puede crear fácilmente flujos de datos mediante herramientas familiares de autoservicio para ingerir, transformar, integrar, y mejorar los macrodatos. Cuando cree un flujo de datos, definirá las conexiones a un origen de datos, la lógica ETL (extraer, transformar, cargar), y el destino para cargar los datos resultantes. Una vez creados, puede configurar un programación de actualización de flujos de datos para indicar la frecuencia con la que debe ejecutarse. Además, el nuevo motor de cálculo basado en modelo hace que el proceso de preparación de datos sea más administrable, más determinista, y menos incómodo para los clientes de flujo de datos. Con los flujos de datos, las tarea que antes requerían una organización TI de datos para crear y supervisar (y muchas horas o días para completar) se ahora pueden administrar con solo unos pocos clics por individuos que ni siquiera son científicos de datos, como creadores de aplicación, analistas de negocios y creadores de informes.


Los flujos de datos almacenan datos en entidades. Una entidad es un conjunto de registros que se usa para almacenar datos, similar a cómo una tabla almacena los datos en una base de datos. Los clientes pueden definir un esquema de entidad personalizada o aprovechar las entidades estándar de Common Data Model.
Common Data Model es un lenguaje de datos compartido para uso de aplicaciones de negocios y analíticas. El sistema de metadatos Common Data Store habilita la coherencia de datos y sus significado a través de aplicaciones y de procesos de negocio, como PowerApps, Power BI, algunas aplicaciones de Dynamics 365 (aplicaciones basadas en modelo), y Azure, que almacenan datos de conformidad con el Common Data Store. Las entidades resultantes de un flujo de datos pueden a continuación almacenarse en uno de los siguientes:

-   **Common Data Service.** Le permite almacenar y administrar de forma segura los datos que usan las aplicaciones empresariales utilizando PowerApps y Microsoft Flow.

-   **Azure Data Lake Storage Gen2.** Le permite colaborar con personas de la organización usando Power BI, Azure Data, y los servicios de IA o aplicaciones de línea de negocio a la medida que leen datos del lago. Los flujos de datos que cargan datos en una cuenta de Azure Data Lake Storage almacenan datos en [carpetas de Common Data Model](https://go.microsoft.com/fwlink/?linkid=2045304). Las **carpetas de Common Data Service** contienen datos y metadatos esquematizados en un formato estandarizado para facilitar el intercambio de datos y permitir una interoperabilidad completa entre los servicios que producen o consumen datos almacenados en la cuenta de Azure Data Lake Storage de una organización como capa de almacenamiento compartido.

Puede usar flujos de datos para preparar datos de un conjunto grande y creciente de orígenes de datos admitidos locales y basados en la nube incluidos Excel, la base de datos de Azure SQL, SharePoint, Azure Data Explorer, Salesforce, base de datos Oracle, etc.

Después de seleccionar el origen de datos, puede usar la experiencia sin código o con poco código de Power Query para transformar los datos y asignarlos a entidades estándar en Common Data Model o crear entidades personalizadas. Los usuarios avanzados pueden editar directamente el lenguaje M de un flujo de datos para personalizar completamente flujos de datos, similares a la experiencia de Power Query que millones de usuarios de Power BI Desktop y Excel conocen ya.

Una vez que ha creado y ha guardado un flujo de datos, tendrá que ejecutarlo en la nube.
Puede elegir desencadenar un flujo de datos para ejecutarse manualmente o programar la frecuencia para que el servicio de flujo de datos de Power Platform lo ejecute por usted. Cuando un flujo de datos completa una ejecución, sus datos están disponibles para usar. Para cargar los datos de flujo de datos en Common Data Service, el conector de Common Data Service se puede usar en PowerApps, Microsoft Flow, Excel, y el resto de aplicaciones que admiten el conector Common Data Service. Para obtener flujos de datos almacenados en la cuenta de Azure Data Lake Storage Gen2 de su organización, puede usar el conector de flujo de datos de Power Platform en Power BI Desktop o tener acceso a los archivos directamente en el lago.

## <a name="how-to-use-dataflows"></a>Cómo usar flujos de datos
La sección anterior proporcionó información general sobre la tecnología de flujos de datos. En esta sección, veremos cómo los flujos de datos se pueden usar en una organización.

> [!NOTE]
> Debe tener un plan PowerApps de pago para usar flujos de datos, pero no se le cobra por separado por usar flujos de datos. 

### <a name="load-data-to-common-data-service"></a>Cargar datos en Common Data Service
Los flujos de datos se pueden usar para rellenar entidades en [Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro) que se usan en aplicaciones PowerApps. Con solo unos clics puede integrar datos de orígenes online y locales.

<!--from editor: In the last sentence above, should it change to "...on-premises data sources." ? -->


### <a name="extend-the-common-data-model-for-your-business-needs"></a>Ampliar el Common Data Model para las necesidades de negocio
Para las organizaciones que desean ampliar y crear basándose en Common Data Model, los flujos de datos permiten a profesionales de inteligencia empresarial personalizar entidades estándar o para crear nuevas. Este método de autoservicio para personalizar el modelo de datos se puede usar posteriormente con flujos de datos para crear paneles Power BI que están adaptados a una organización.

### <a name="extend-your-capabilities-with-azure-data-and-ai-services"></a>Extender las funciones con servicios de Azure Data e IA
Puede configurar flujos de datos de Power Platform para almacenar datos de flujos de datos en la cuenta de Azure Data Lake Storage Gen2 de la organización. Cuando un entorno está conectado al lago de datos de la organización, los científicos y los programadores de datos pueden aprovechar productos eficaces de Azure como Azure Machine Learning, Azure Databricks, Azure Data Factory, etc.

Para obtener más información sobre integración de Azure Data Lake Storage Gen2 y flujos de datos, y cómo crear flujos de datos que residen en Azure Data Lake de la organización, consulte [Conectar Azure Data Lake Storage Gen2 para almacenamiento de flujo de datos](connect-azure-data-lake-storage-for-dataflow.md).

## <a name="summary-of-self-service-data-prep-for-big-data-in-powerapps"></a>Resumen de preparación de los datos de autoservicio para macrodatos en PowerApps
Hay varias situaciones y ejemplos donde los flujos de datos pueden permitirle para obtener mejor control —e información más rápida— de los datos profesionales. Otros usuarios de la organización pueden aprovechar los flujos de datos mediante Common Data Service, el conector de flujo de datos Power Platform de Power BI o acceso directo a la carpeta **Common Data Service** del flujo de datos en la cuenta de Azure Data Lake Storage Gen2 de la organización. Mediante un modelo de datos del estándar (esquema) definido por Common Data Model, las aplicaciones empresariales pueden depender del esquema de una entidad, y resumirse del modo en que los datos se crearon o cuál sea su origen. Cuando un flujo de datos completa una ejecución programada, los datos están listos para modelado y creación de aplicaciones, flujos o ideas de BI en un período muy corto, mientras que antes se tardaban meses, o más.

El formato estandarizado del Common Data Model permite que las personas en su organización crear aplicaciones que generan elementos visuales e informes rápidos fáciles, y automáticos. Entre estos se incluyen, entre otros:

-   Asignación de datos de diversos orígenes a entidades estándar en Common Data Model para unificar datos y aprovechar el esquema conocido para controlar aplicaciones listas para usar.

-   Crear sus propias entidades personalizadas para unificar datos en toda la organización.

-   Crear informes y paneles Power BI que aprovechen los datos de flujo de datos.

-   Crear integración con servicios de Azure Data e IA mediante la cuenta de Azure Data Lake Storage Gen2 de la organización.

## <a name="next-steps"></a>Pasos siguientes

Este artículo proporcionó una visión general de preparación de datos de autoservicio en el portal PowerApps, y las formas en que puede usarlos. Los temas siguientes dan más detalles sobre los escenarios de uso comunes para flujos de datos:

-   [Creación y uso de flujos de datos en PowerApps](https://go.microsoft.com/fwlink/?linkid=2100076)

-   [Agregar datos a una entidad en Common Data Service](https://go.microsoft.com/fwlink/?linkid=2100075)

-   [Conexión a Azure Data Lake Storage Gen2 para el almacenamiento del flujo de datos](https://go.microsoft.com/fwlink/?linkid=2099973)

-   [Uso de flujos de datos con orígenes de datos locales](https://go.microsoft.com/fwlink/?linkid=2100077)

Para obtener más información acerca de Power Query y actualización programada, puede leer estos artículos:

-   [Información general sobre consulta en Power BI Desktop](/power-bi/desktop-query-overview)

-   [Configurar la actualización programada](/power-bi/refresh-scheduled-refresh)

Para obtener más información sobre Common Data Model, puede leer el artículo de información general:

-   [Common Data Model - visión general](/powerapps/common-data-model/overview)

