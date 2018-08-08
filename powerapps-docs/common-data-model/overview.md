---
title: Qué es Common Data Service| Microsoft Docs
description: Common Data Service es una colección estandarizada, modular y extensible de esquemas de datos publicados por Microsoft que están diseñados para facilitarle la compilación, el uso y el análisis de datos.
author: RobertBruckner
ms.service: powerapps
ms.topic: article
ms.date: 07/24/2018
ms.author: robruc
ms.openlocfilehash: 1469646301c273067ad035428f03c452ae223604
ms.sourcegitcommit: abe4d4728db7f56088f618af5b820af78e7099c9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2018
ms.locfileid: "39332003"
---
# <a name="what-is-the-common-data-model"></a>¿Qué es Common Data Service?

Si alguna vez ha experimenta dificultades con datos que son *prácticamente* los mismos o *deben* trabajar juntos, y luego ha dedicado un esfuerzo considerable a transformar campos y tablas para trabajar con el resto de sus datos, sabe que los elementos de datos comunes pueden ahorrar esfuerzo, agilizar el desarrollo futuro y permitir un análisis más rápido. Estas funcionalidades y otras son las que puede proporcionar Common Data Service (CDS).

**Common Data Service (CDS)** es una colección estandarizada, modular y extensible de esquemas de datos publicados por Microsoft que están diseñados para facilitarle la compilación, el uso y el análisis de datos. Esta colección de esquemas predefinidos, que consta de *entidades*, *atributos*, *metadatos semánticos* y *relaciones*, representa conceptos y actividades que se usan habitualmente, como cuenta y campaña, para simplificar la creación, la agregación y el análisis de datos. Más información: [repositorio de CDS en GitHub](https://aka.ms/cdmrepo)

![Common Data Model](media/cdm-entities.png)

Más información: [póster de CDS](https://aka.ms/cdmposter)

## <a name="why-use-the-common-data-model"></a>¿Por qué usar Common Data Service?

CDS simplifica el desarrollo de aplicaciones y administración de datos mediante la unificación de los datos en un formato conocido y la aplicación de coherencia estructural y semántica en varias aplicaciones e implementaciones. En otras palabras, cuando los datos se encuentran en CDS, puede usarlos en muchas aplicaciones diferentes, simplificar la creación o el uso de otras aplicaciones para usar los datos existentes y crear fácilmente informes para cada uno de ellos (o todos ellos). Además, los integradores de datos que traen datos desde diversos sistemas pueden centrarse en la llegada de los datos a CDS, en lugar de compilar un nuevo modelo para cada aplicación.

Imagine que tiene tres aplicaciones empresariales: una aplicación de materiales, una aplicación de fabricación y una aplicación de ventas. Muchas veces, cada una de las aplicaciones se crearía en forma independiente, con diferentes estructuras que representan una entidad, como *cuenta*, que son prácticamente iguales (pero no). Con CDS, podría compilar los datos en un formato normalizado (con las entidades, atributos y relaciones de CDS). Luego, cada una de esas tres aplicaciones podría usar los mismos datos como base. Por supuesto, cada aplicación podría tener sus propios datos y esquemas adicionales, basados en la funcionalidad de cada aplicación. Pero en cuanto a desarrollo, las aplicaciones y los informes podrían extraer los elementos de datos comunes rápidamente, sin problemas y con confianza.

¿Y qué hay de la necesidad de crear una cuarta aplicación? Los datos están listos (en el esquema de CDS), por lo que puede concentrar sus esfuerzos de desarrollo en la lógica de negocios, no en complicaciones de datos y transformaciones difíciles.

En otras palabras, CDS ofrece lo siguiente para los datos:

-   **Coherencia estructural y semántica** entre aplicaciones e implementaciones.

-   **Integración simplificada y eliminación de ambigüedades de los datos** que se recopilan de procesos, interacciones digitales, telemetría de productos, interacciones de usuarios, etcétera.

-   **Una forma unificada** en la que las integraciones de datos pueden **combinar datos de empresa existentes con otros orígenes** y usar esos datos holísticamente para desarrollar nuevas aplicaciones o extraer conclusiones.

-   **Posibilidad de extender el esquema y las entidades de CDS** para adaptar Common Data Service a la organización.

Puede usar CDS para crear repositorios de datos que coincidan con el esquema, así como para transformar los datos existentes al esquema de Common Data Service. En cualquier caso, la eficacia que obtiene de la estandarización puede acelerar y simplificar todo lo que haga después con los datos.

## <a name="who-uses-the-common-data-model"></a>¿Quién usa Common Data Service?

CDS se utiliza en diversos clientes, asociados y productos, todo ello con el mismo objetivo de unificar los datos de forma conocida con significado semántico.

-   **Creadores y desarrolladores de aplicaciones**: ya sea que estos usuarios utilicen plataformas basadas en código o una plataforma de poco o código o ninguno, como PowerApps, tienen que almacenar y administrar los datos de sus aplicaciones.

-   **Integradores de datos**: estos usuarios son responsables de incorporar datos procedentes de diversos sistemas para hacerlos accesibles para que las aplicaciones los usen.

Históricamente, el trabajo de compilación de una aplicación ha estado estrechamente ligado a la integración de datos, pero con CDS y las plataformas compatibles, ambas tareas pueden producirse por separado.

## <a name="common-data-model-in-action"></a>Common Data Service en acción

Microsoft y sus asociados usan CDS en sus propias aplicaciones y ofertas, y crean servicios y ofertas adicionales a partir de esquemas de CDS. Los ejemplos siguientes muestran cómo las organizaciones usan CDS:

-   **Common Data Service (CDS) for Apps**, compatible con Dynamics y PowerApps, almacena los datos de acuerdo a la definición de CDS. De hecho, muchas de las entidades empresariales originales que se incluyen en CDS provienen de ofertas de Dynamics tales como Dynamics 365 for Sales y Dynamics 365 for Marketing.

-   **Segmentos de mercado vertical** (por ejemplo, el sector sanitario) trabajan estrechamente con Microsoft para ampliar CDS a sus conceptos empresariales específicos, tales como *paciente* y *plan de atención médica*, por lo que pueden compartir datos y compilar servicios para que los asociados puedan intercambiar datos fácilmente, crear servicios y aplicaciones interoperables y crear análisis rápidos que sean fáciles de compartir.

## <a name="next-step"></a>Paso siguiente

[Cómo usar Common Data Service](use-common-data-model.md): describe CDS en detalle y se tratan casos de uso para crear otros datos en CDS o transformar los datos existentes en CDS.