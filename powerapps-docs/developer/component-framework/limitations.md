---
title: Limitaciones del marco de componentes de PowerApps | MicrosoftDocs
description: Limitaciones del uso del marco de componentes de PowerApps
author: nkrb
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
---

# <a name="limitations-of-powerapps-component-framework"></a>Limitaciones del marco de componentes de PowerApps

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Con el lanzamiento del marco de componentes de PowerApps, ahora puede crear sus propios componentes personalizados para mejorar la experiencia de usuario en aplicaciones basadas en modelo. Aunque puede crear sus propios componentes, hay algunas limitaciones que restringen a los programadores a implementar algunas características en los componentes personalizados. A continuación se indican algunas de las limitaciones:

## <a name="support-for-external-libraries"></a>Compatibilidad con bibliotecas externas

Para la vista previa pública, los componentes deben agrupar todo el contenido de bibliotecas externas en la agrupación de código principal. Para ver un ejemplo de cómo la interfaz de línea de comandos de PowerApps puede ayudar a agrupar su contenido de biblioteca externa en una agrupación específica del componente, vea el ejemplo de [Componente de Flip angular](sample-controls/angular-flip-control.md).

> [!NOTE]
> Las bibliotecas compartidas a través de componentes utilizando nodos de biblioteca en el manifiesto del componente no se admiten para vista previa pública. Estamos revisando esto y agregaremos esta capacidad en una versión futura.

## <a name="related-topics"></a>Temas relacionados

[Referencia de la API de marco de componentes de PowerApps](reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](overview.md)
