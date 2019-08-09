---
title: Descripción general de PowerApps Component Framework | MicrosoftDocs
description: 'Use el marco de componentes de PowerApps para crear componentes personalizados para proporcionar una mejor experiencia para que los usuarios vean y trabajen con datos en formularios, vistas, y paneles.'
keywords: 'Marco de componentes, componentes personalizados, controles de PowerApps'
author: nkrb
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.custom:
  - dyn365-a11y
  - dyn365-developer
ms.topic: article
ms.assetid: 7923e36d-3640-49f7-9f2f-c97358a632db
ms.author: nabuthuk
---

# <a name="powerapps-component-framework-overview"></a>Descripción general de PowerApps Component Framework

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Use el marco de componentes de PowerApps para crear componentes personalizados en aplicaciones basadas en modelo para proporcionar una mejor experiencia para que los usuarios vean y trabajen con datos en formularios, vistas, y paneles. Por ejemplo:

- Reemplace un campo que muestre un valor de texto numérico con un componente `dial` o `slider`.
- Transforme una lista en una experiencia visual completamente diferente enlazada al conjunto de datos como un `Calendar` o `Map`.

> [!IMPORTANT]
> - El marco de componentes de PowerApps es una característica de vista previa.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)] 


El marco de componentes de PowerApps permite a los desarrolladores profesionales crear componentes personalizados que se pueden usar en toda la extensión de las capacidades de PowerApps. Los componentes personalizados tienen acceso a un amplio conjunto de API de marcos que exponen capacidades como la administración del ciclo de vida de componentes, acceso a datos contextuales y metadatos, acceso sin problemas del servidor mediante la API web, métodos de formato de datos y utilidades, características de dispositivos como cámara, ubicación y micrófono junto con elementos UX fáciles de invocar como diálogos, búsquedas, generación de páginas completas, etc.  

> [!NOTE]
> Los componentes personalizados se admiten solo en la Interfaz unificada para [aplicaciones basadas en modelo](/powerapps/maker/model-driven-apps/model-driven-app-overview) versión 9.1.0.3842 o posterior

Los programadores de componentes pueden usar prácticas web modernas y también aprovechar el poder de bibliotecas externas para crear interacciones de usuario avanzadas. El marco controla automáticamente el ciclo de vida de componentes, mantiene la lógica empresarial de la aplicación y optimiza el rendimiento (sin iframes asincrónicos). Los componentes creados mediante este marco son totalmente configurables y pueden ser reusados en varias superficies en aplicaciones basadas en modelo como formularios, paneles, cuadrículas, etc. La definición de componentes, dependencias y configuraciones se pueden agrupar en una [solución](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview) y mover a través de entornos y se pueden enviar mediante [origen de aplicación](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=dynamics-365).  

## <a name="related-topics"></a>Temas relacionados

[Qué son componentes personalizados](custom-controls-overview.md)<br/>
[Crear e implementar los componentes personalizados](create-custom-controls-using-pcf.md)<br/>
[PowerApps para desarrolladores](https://docs.microsoft.com/powerapps/#pivot=home&panel=developer)

