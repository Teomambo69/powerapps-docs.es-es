---
title: Limitaciones del marco de componentes de PowerApps | MicrosoftDocs
description: Limitaciones del uso del marco de componentes de PowerApps
author: nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
ms.openlocfilehash: aabcf4518e71648797c795a006c2d842f3e5ff01
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346748"
---
# <a name="limitations"></a>Límite 

Con el lanzamiento de la plataforma de componentes de PowerApps, ahora puede crear sus propios componentes de código para mejorar la experiencia del usuario en aplicaciones basadas en modelos y aplicaciones de lienzo. Aunque puede crear sus propios componentes, existen algunas limitaciones que restringen a los desarrolladores que implementan algunas características en los componentes de código. A continuación se muestran algunas de las limitaciones:

1. Solo se admite *el tipo de componente de los componentes* en la versión preliminar experimental de las aplicaciones de lienzo y no los componentes de tipo de *conjunto* de elementos. 
2. Common Data Service API dependientes, incluido WebAPI junto con otras API, no están disponibles para esta versión preliminar experimental. Para obtener la disponibilidad de API individual para esta versión preliminar experimental, consulte referencia de la [API del marco de componentes de PowerApps](reference/index.md).
3. Los componentes de código deben agrupar todo el código incluido el contenido de la biblioteca externa en el paquete de código principal. Para ver un ejemplo de cómo la interfaz de la línea de comandos de PowerApps puede ayudarle a agrupar el contenido de la biblioteca externa en un paquete específico del componente, consulte ejemplo de [componente de volteo angular](sample-controls/angular-flip-control.md) .

   > [!NOTE]
   > Todavía no se admiten las bibliotecas compartidas entre componentes que usan nodos de biblioteca en el manifiesto del componente. Estamos revisando esto y se agregará esta funcionalidad en futuras versiones.
4. Todavía no se admite la definición de varios componentes en un único archivo de manifiesto.
5. Todavía no se admite la llamada a procesos y acciones. Solo puede llamar a cuadros de diálogo mediante el método de [navegación](reference/navigation.md) .
6. Todavía no se admite la llamada a un componente desde otro componente de código.
7. Actualmente no se admite el recurso de fuente (. TFF).

## <a name="related-topics"></a>Temas relacionados

[Referencia de la API del marco de componentes de PowerApps](reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](overview.md)
