---
title: Información general sobre el marco de componentes de PowerApps | Microsoft Docs
description: Use el marco de componentes de PowerApps para crear componentes de código con el fin de proporcionar experiencias mejoradas para que los usuarios puedan ver y trabajar con datos en formularios, vistas y paneles.
keywords: Marco de componentes, componentes de código, controles de PowerApps
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
ms.openlocfilehash: a9f157dfb3d0a7d29cebadee935c84826ae040d6
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025654"
---
# <a name="powerapps-component-framework-overview"></a>Información general sobre el marco de componentes de PowerApps

El marco de componentes de PowerApps permite a los desarrolladores profesionales y a los fabricantes de aplicaciones crear componentes de código para aplicaciones controladas por modelos y aplicaciones de lienzo (vista previa experimental) para proporcionar una experiencia de usuario mejorada para que los usuarios puedan ver y trabajar con datos en formularios, vistas, y paneles. Por ejemplo:

- Reemplace un campo que muestre un valor de texto numérico por un `dial` o `slider` componente de código.
- Transformar una lista en una experiencia visual totalmente diferente enlazada al conjunto de datos como un `Calendar` o `Map`.

> [!IMPORTANT]
> - El marco de componentes de PowerApps está en versión preliminar experimental para aplicaciones de canvas y en GA para aplicaciones controladas por modelos. Esto implica que todas las API que se admiten para aplicaciones controladas por modelos podrían no ser compatibles todavía con las aplicaciones de canvas.
> - De forma predeterminada, el marco de componentes de PowerApps está habilitado para aplicaciones controladas por modelos. Para habilitar esta característica para las aplicaciones de Canvas, consulte [disponibilidad de las aplicaciones de canvas](component-framework-for-canvas-apps.md).
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]
> - Las aplicaciones de lienzo solo admiten el tipo de *campo* de los componentes de código y no el tipo de *conjunto* de elementos.


Use el marco de componentes de PowerApps para crear componentes de código que pueden usarse en toda la amplitud de funcionalidades de PowerApps. A diferencia de los recursos web HTML, los componentes de código se representan como parte del mismo contexto, y se cargan al mismo tiempo que cualquier otro componente, lo que proporciona una experiencia sin problemas para los usuarios. Los desarrolladores pueden agrupar todos los archivos HTML, CSS y TypeScript o JavaScript en un único archivo de paquete de solución. Los componentes de código se pueden reutilizar muchas veces en diferentes entidades y formularios.

Los componentes de código tienen acceso a un amplio conjunto de API de marco de trabajo que exponen funcionalidades como la administración del ciclo de vida de los componentes, los datos contextuales y el acceso a metadatos, acceso de servidor sin problemas mediante API Web, métodos de formato de datos y utilidades, características de dispositivos Ubicación y micrófono, junto con elementos de la experiencia de usuario fáciles de invocar, como cuadros de diálogo, búsquedas y representación de página completa.  

Los desarrolladores y los responsables de aplicaciones pueden usar las prácticas web modernas y también aprovechar la eficacia de las bibliotecas externas para crear interacciones de usuario avanzadas. El marco de trabajo controla automáticamente el ciclo de vida de los componentes, conserva la lógica de negocios de la aplicación y optimiza el rendimiento (no más IFrame asincrónicos). La definición de componentes, las dependencias y las configuraciones se pueden empaquetar en una [solución](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview) y moverse entre entornos y se pueden enviar a través de [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=dynamics-365).  

## <a name="related-topics"></a>Temas relacionados

[Qué son los componentes de código](custom-controls-overview.md)<br/>
[Disponibilidad de las aplicaciones de Canvas](component-framework-for-canvas-apps.md)<br/>
[Crear y compilar un componente de código](create-custom-controls-using-pcf.md)<br/>
[PowerApps para desarrolladores](https://docs.microsoft.com/powerapps/#pivot=home&panel=developer)

