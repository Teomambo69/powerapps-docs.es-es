---
title: Descripción general de PowerApps Component Framework | MicrosoftDocs
description: Use PowerApps component framework  para crear componentes de código para proporcionar una mejor experiencia para que los usuarios vean y trabajen con datos en formularios, vistas, y paneles.
keywords: Component Framework, componente, componentes de código, controles de PowerApps
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
ms.openlocfilehash: 03534f925750b7c99e6d53822aab766421854968
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753624"
---
# <a name="powerapps-component-framework-overview"></a>Información general sobre PowerApps component framework

PowerApps component framework permite a los desarrolladores profesionales y creadores de aplicaciones crear los componentes de código de aplicaciones basadas en modelo y aplicaciones de lienzo (vista previa experimental) para proporcionar una mejor experiencia de usuario para que los usuarios vean y ejecuten datos en formularios, vistas, y paneles. Por ejemplo:

- Reemplace un campo que muestre un valor de texto numérico con un componente de código `dial` o `slider`.
- Transforme una lista en una experiencia visual completamente diferente enlazada al conjunto de datos como un `Calendar` o `Map`.

> [!IMPORTANT]
> - PowerApps component framework está en vista previa piloto para aplicaciones de lienzo y en GA para aplicaciones basadas en modelo. Esto implica que todas las API que son compatibles con las aplicaciones basadas en modelo podrían no admitirse en aplicaciones de lienzo.
> - De forma predeterminada PowerApps component framework está habilitado para las aplicaciones basadas en modelo. Para habilitar esta característica para aplicaciones de lienzo, consulte [Disponibilidad para aplicaciones de lienzo](component-framework-for-canvas-apps.md).
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]
> - Las aplicaciones de lienzo sólo admiten el tipo *campo* de componentes de código, y no el tipo *conjunto de datos*.


Use PowerApps component framework para crear componentes de código que se pueden usar en toda la extensión de las capacidades de PowerApps. A diferencia de los recursos web HTML, los componentes de código se representan como parte del mismo contexto, se cargan al mismo tiempo que cualquier otro componente, proporcionando una experiencia integrada para los usuarios. Los programadores pueden empaquetar todos los archivos HTML, CSS y TypeScript o JavaScript en un archivo de paquete de solución única. Los componentes de código pueden ser reusados muchas veces en diferentes entidades y formularios.

Los componentes de código tienen acceso a un amplio conjunto de API de marcos que exponen capacidades como la administración del ciclo de vida de componentes, acceso a datos contextuales y metadatos, acceso sin problemas del servidor mediante la API web, métodos de formato de datos y utilidades, características de dispositivos como cámara, ubicación y micrófono junto con elementos UX fáciles de invocar como diálogos, búsquedas y generación de páginas completas.  

Los desarrolladores y creadores de aplicaciones pueden usar prácticas web modernas y también aprovechar el poder de bibliotecas externas para crear interacciones de usuario avanzadas. El marco controla automáticamente el ciclo de vida de componentes, mantiene la lógica empresarial de la aplicación y optimiza el rendimiento (sin IFrames asincrónicos). La definición, las dependencias, y configuraciones de componentes se pueden empaquetar en una [solución](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview) y mover a través de entornos y entregar a través de [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=dynamics-365).  

## <a name="related-topics"></a>Temas relacionados

[Qué son los componentes de código](custom-controls-overview.md)<br/>
[Disponibilidad para las aplicaciones de lienzo](component-framework-for-canvas-apps.md)<br/>
[Crear y generar un componente de código](create-custom-controls-using-pcf.md)<br/>
[PowerApps para desarrolladores](https://docs.microsoft.com/powerapps/#pivot=home&panel=developer)

