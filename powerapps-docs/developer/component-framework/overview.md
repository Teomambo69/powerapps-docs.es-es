---
title: Descripción general de Power Apps Component Framework | MicrosoftDocs
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
ms.openlocfilehash: c86182fe14617f971b8ca2183bdb4627b8e8c5b9
ms.sourcegitcommit: 64d816a759c5cc6343928d56a673812c3ea066c2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/06/2019
ms.locfileid: "2895078"
---
# <a name="power-apps-component-framework-overview"></a>Información general sobre Power Apps component framework

Power Apps component framework permite a los desarrolladores profesionales y creadores de aplicaciones crear los componentes de código de aplicaciones basadas en modelo y aplicaciones de lienzo (vista previa experimental) para proporcionar una mejor experiencia de usuario para que los usuarios vean y ejecuten datos en formularios, vistas, y paneles. Por ejemplo:

- Reemplace un campo que muestre un valor de texto numérico con un componente de código `dial` o `slider`.
- Transforme una lista en una experiencia visual completamente diferente enlazada al conjunto de datos como un `Calendar` o `Map`.

> [!IMPORTANT]
> - Power Apps component framework está en vista previa piloto para aplicaciones de lienzo y en GA para aplicaciones basadas en modelo. Esto implica que todas las API que son compatibles con las aplicaciones basadas en modelo podrían no admitirse en aplicaciones de lienzo.
> - De forma predeterminada Power Apps component framework está habilitado para las aplicaciones basadas en modelo. Para habilitar esta función para aplicaciones de lienzo, consulte [Componentes de código para aplicaciones de lienzo](component-framework-for-canvas-apps.md).
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]
> - Las aplicaciones de lienzo sólo admiten el tipo *campo* de componentes de código, y no el tipo *conjunto de datos*.

## <a name="how-its-different-from-webresources"></a>Diferencias con los recursos web

 A diferencia de los recursos web HTML, los componentes de código se representan como parte del mismo contexto, se cargan al mismo tiempo que cualquier otro componente, proporcionando una experiencia integrada para los usuarios. Los desarrolladores pueden agrupar todo el HTML, CSS y archivos TypeScript o JavaScript en un solo archivo de paquete de [solución](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview) y movido a través de entornos y que se puede enviar a través de [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=dynamics-365). Los componentes de código pueden ser reusados muchas veces en diferentes entidades y formularios. Use Power Apps component framework para crear componentes de código que se pueden usar en toda la extensión de las capacidades de Power Apps.

## <a name="advantages"></a>Ventajas 

- Acceda a un amplio conjunto de API de marco con funciones como la gestión del ciclo de vida de los componentes, los datos contextuales y los metadatos. 
- Acceso perfecto al servidor a través de la API web, los métodos de utilidades y formato de datos, las características del dispositivo como la cámara, la ubicación y el micrófono, junto con elementos de experiencia de usuario fáciles de invocar, como diálogos, búsquedas y representación de página completa.  
- Soporte para prácticas web modernas.
- Optimiza para el rendimiento.
- Se puede volver a utilizar
- Agrupe todos los archivos en un único archivo de solución.

## <a name="related-topics"></a>Temas relacionados

[Qué son los componentes de código](custom-controls-overview.md)<br/>
[Componentes de código para aplicaciones de lienzo](component-framework-for-canvas-apps.md)<br/>
[Crear y generar un componente de código](create-custom-controls-using-pcf.md)<br/>
[Power Apps para desarrolladores](https://docs.microsoft.com/powerapps/#pivot=home&panel=developer)

