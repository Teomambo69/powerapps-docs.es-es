---
title: Desarrollo con Common Data Service | Microsoft Docs
description: Ofrece información sobre cómo puede usar Common Data Service para desarrollar aplicaciones y soluciones.
author: RobertBruckner
ms.service: powerapps
ms.topic: article
ms.date: 07/24/2018
ms.author: robruc
ms.openlocfilehash: 6e99fbe13d9b6e3acdd0cfdd08662676a321471c
ms.sourcegitcommit: abe4d4728db7f56088f618af5b820af78e7099c9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2018
ms.locfileid: "39332125"
---
# <a name="how-to-use-the-common-data-model"></a>Cómo usar Common Data Service

Con **Common Data Service (CDS)**, puede convertir los datos a formatos que representen conceptos y actividades de uso común, y que sean ampliamente utilizados y reconocidos, para que pueda consultar esos datos, reutilizarlos e interoperar con otras empresas y aplicaciones que también utilicen ese formato. De la misma forma que hay que saber el tamaño y la forma de una pila AA para que se pueda usar en todos los controles remotos, CDS define el tamaño y la forma de un *contacto* (por ejemplo), para que los desarrolladores de aplicaciones y los asociados comerciales sepan cómo utilizar esos datos y puedan crear sus aplicaciones (o interoperar) con agilidad y confianza. Y puesto que CDS es una definición de código abierto de entidades estándar, la comunidad de desarrolladores interesados puede entender fácilmente las definiciones de esquema y participar en ellas.

En la actualidad, CDS se usa en Common Data Service (CDS) for Apps, compatible con Dynamics y PowerApps, y las funcionalidades de preparación de datos de Power BI para crear archivos esquematizados en Azure Data Lake.

![Common Data Service con CDS for Apps](media/cdm-with-cds.png)

Puede usar CDS for Apps de las maneras siguientes:

-   **Almacenar y administrar de forma segura los datos en formato CDS**: puede usar CDS for Apps para almacenar y administrar de forma segura los datos en el formato CDS estandarizado. Al hacerlo, tiene acceso a esos datos y puede utilizarlos en aplicaciones de Microsoft y servicios tales como Dynamics, Power Apps, Flow o Power BI, o en sus propias aplicaciones personalizadas.

-   **Crear entidades personalizadas de CDS**: CDS es extensible, para que pueda crear las entidades que no se encuentran ya en CDS y son específicas de su organización, y rellenar las entidades con los datos existentes mediante **Power Query**. Esto le permite aprovechar las ventajas de CDS, así como adaptarlas a su negocio.

-   **Crear sus propios repositorios de datos**: puede crear repositorios de datos que cumplan con el esquema de **Common Data Service (CDS)** y conectarse a esos orígenes de datos mediante conectores de datos de Microsoft. Esto le permite compilar aplicaciones de línea de negocio personalizadas que utilicen o compartan los datos de CDS, independientemente de dónde se originen o almacenen los datos.

-   **Obtener y distribuir rápidamente información con Power BI**: puede usar servicios de preparación de datos avanzados de Power BI que acceden a los almacenes de datos de CDS (por ejemplo, los datos que ha incluido en CDS for Apps) para crear informes y paneles y, luego, crear aplicaciones de generación de informes que extraigan automáticamente los datos de CDS en forma de información personalizada para usuarios y grupos de la organización.

-   **Generar informes personalizados, pero para toda la organización en Power BI**: puede usar aplicaciones que generen automáticamente informes personalizados que puede insertar en áreas de trabajo de Power BI para los usuarios de la organización, y mucho más.

A medida que Microsoft extienda CDS, junto con muchos asociados y expertos en la materia, nuevos sectores, como el sanitario podrán beneficiarse de CDS y las plataformas compatibles.

## <a name="data-integration-and-power-query-online"></a>Integración de datos y Power Query Online

Las dos plataformas que actualmente admiten CDS ofrecen también experiencias de integración de datos a través de Power Query Online que permiten a los usuarios incorporar datos procedentes de diversos orígenes, transformarlos si es necesario y luego asignarlos a entidades de CDS estándar o crear entidades personalizadas. Power Query Online aprovecha la misma experiencia de preparación de datos visuales y de autoservicio que Power Query en Excel y Power BI Desktop, por lo que los usuarios existentes pueden progresar rápidamente.

![Mapa de datos con entidades en CDS](media/cdm-map-entities.png)

## <a name="common-data-service-for-apps"></a>Common Data Service for Apps

CDS for Apps le permite iniciar aplicaciones mediante CDS con la lógica de negocios, la seguridad y la integración incorporadas. La plataforma le permite:

-   **Aprovechar las aplicaciones empresariales empaquetadas**: muchas soluciones de Microsoft Dynamics y muchas aplicaciones de terceros se crean en CDS for Apps (o al menos lo utilizan). Cuando los datos están en CDS, puede aprovechar esas aplicaciones empaquetadas.

-   **Obtener acceso a las soluciones personalizadas**: existe un ecosistema de extensiones y aplicaciones completas, creadas por desarrolladores que entienden y trabajan con datos en el formato de CDS. Para obtener más información, vea [Introducción a las soluciones](https://docs.microsoft.com/powerapps/developer/common-data-service/introduction-solutions).

Sea cual sea su intención, CDS convierte los datos a un formato común para que se puedan usar, compartir y analizar con más facilidad.

**Recursos para CDS for Apps**

-   [CDS for Apps](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro)

-   [Agregar datos a una entidad en CDS for Apps mediante Power Query](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-cds-newentity-pq)

-   [Introducción a las soluciones](https://docs.microsoft.com/powerapps/developer/common-data-service/introduction-solutions)

-   [Build a model-driven app](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview) (Compilación de una aplicación controlada por modelos)

-   [Build a canvas app](https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started) (Compilación de una aplicación de lienzo)

-   [Crear un flujo que utilice CDS for Apps](https://docs.microsoft.com/flow/common-data-model-intro)

