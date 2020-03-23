---
title: Descripción general de Power Apps component framework | MicrosoftDocs
description: Use Power Apps component framework  para crear componentes de código para proporcionar una mejor experiencia para que los usuarios vean y trabajen con datos en formularios, vistas, y paneles.
keywords: Component Framework, componente, componentes de código, controles de Power Apps
author: nkrb
manager: kvivek
ms.date: 09/05/2019
ms.service: powerapps
ms.custom:
- dyn365-a11y
- dyn365-developer
ms.topic: article
ms.assetid: 7923e36d-3640-49f7-9f2f-c97358a632db
ms.author: nabuthuk
ms.openlocfilehash: cc809d81b7b9adf7327aa9cb8f74515816022118
ms.sourcegitcommit: 59f0b3adc56279b5673cbf04b4a55bd7678e1ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2020
ms.locfileid: "3091235"
---
# <a name="power-apps-component-framework-overview"></a>Información general sobre Power Apps component framework

Power Apps component framework permite a los desarrolladores profesionales y creadores de aplicaciones crear componentes de código para aplicaciones basadas en modelo y aplicaciones de lienzo (versión preliminar pública) para proporcionar una experiencia de usuario mejorada para que los usuarios trabajen con datos en formularios, vistas y paneles. Por ejemplo:

- Reemplace un campo que muestre un valor de texto numérico con un componente de código `dial` o `slider`.
- Transforme una lista en una experiencia visual completamente diferente enlazada al conjunto de datos como un `Calendar` o `Map`.

> [!IMPORTANT]
> - PowerApps component framework está en una versión preliminar pública para aplicaciones de lienzo y generalmente está disponible para aplicaciones basadas en modelo. Esto implica que todas las API que son compatibles con las aplicaciones basadas en modelo podrían no admitirse en aplicaciones de lienzo.
> - De forma predeterminada Power Apps component framework está habilitado para las aplicaciones basadas en modelo. Para habilitar esta función para aplicaciones de lienzo, consulte [Componentes de código para aplicaciones de lienzo](component-framework-for-canvas-apps.md).
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]
> - Power Apps component framework solo funciona en Interfaz unificada y no en el cliente web. 
> - Power Apps component framework no funciona para instancias locales. 

## <a name="how-is-it-different-from-web-resources"></a>¿En qué se diferencia de los recursos web?

A diferencia de los recursos web HTML, los componentes de código se representan como parte del mismo contexto, se cargan al mismo tiempo que cualquier otro componente, proporcionando una experiencia integrada para los usuarios. 

Los desarrolladores pueden agrupar todos los archivos HTML, CSS y TypeScript en un único archivo del paquete de [soluciones](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview) y moverse entre entornos y se envían a través de [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=dynamics-365). 

Los componentes de código pueden ser reusados muchas veces en diferentes entidades y formularios. Use Power Apps component framework para crear componentes de código que se pueden usar en toda la extensión de las capacidades de Power Apps.

## <a name="advantages"></a>Ventajas 

- Acceda a un amplio conjunto de API de marco con funciones como la gestión del ciclo de vida de los componentes, los datos contextuales y los metadatos. 
- Acceso perfecto al servidor a través de la API web, los métodos de utilidades y formato de datos, las características del dispositivo como la cámara, la ubicación y el micrófono, junto con elementos de experiencia de usuario fáciles de invocar, como diálogos, búsquedas y representación de página completa.  
- Soporte para prácticas web modernas.
- Optimiza para el rendimiento.
- Se puede volver a utilizar
- Agrupe todos los archivos en un único archivo de solución.

## <a name="licensing"></a>Licencias

Los requisitos de licencia de Power Apps component framework se ajustan a los de los conectores y componentes existentes y se basan en el tipo de datos y conexiones utilizados en su aplicación. Más información: [Precios de Power Apps](https://powerapps.microsoft.com/pricing/). Para ajustarse a los requisitos de licencia, clasificaremos los componentes del código en dos tipos:

- Componentes de código que se conectan a servicios o datos externos directamente y no a través de conectores. Cuando estos componentes se usan en una aplicación, la aplicación se vuelve premium y los usuarios finales deben tener licencias de **Power Apps**.
- Componentes de código que no se conectan a servicios o datos externos. Cuando estos componentes se usan en una aplicación que usa características estándar, la aplicación sigue siendo estándar y los usuarios finales deben tener una licencia mínima para **Office 365**.

> [!NOTE]
> Si actualmente está utilizando componentes de código en aplicaciones basadas en modelo conectadas a Common Data Service, los usuarios finales requerirán licencias de **Power Apps**.

Con la disponibilidad general del marco de trabajo, los desarrolladores de componentes de código podrán clasificar los componentes como parte del manifiesto de componentes para que los creadores puedan ver qué componentes son premium.

## <a name="related-topics"></a>Temas relacionados

[Qué son los componentes de código](custom-controls-overview.md)<br/>
[Componentes de código para aplicaciones de lienzo](component-framework-for-canvas-apps.md)<br/>
[Crear y generar un componente de código](create-custom-controls-using-pcf.md)<br/>
[Power Apps para desarrolladores](https://docs.microsoft.com/powerapps/#pivot=home&panel=developer)

