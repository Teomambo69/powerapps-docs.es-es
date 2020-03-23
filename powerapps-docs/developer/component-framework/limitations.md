---
title: Limitaciones de Power Apps component framework | MicrosoftDocs
description: Limitaciones del uso de Power Apps component framework
author: nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
ms.openlocfilehash: 61567ce7d1dff080c1e953751796973105f66885
ms.sourcegitcommit: 59f0b3adc56279b5673cbf04b4a55bd7678e1ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2020
ms.locfileid: "3091239"
---
# <a name="limitations"></a>Limitaciones 

Con el lanzamiento de Power Apps component framework, ahora puede crear sus propios componentes de código para mejorar la experiencia de usuario en aplicaciones basadas en modelo. Aunque puede crear sus propios componentes, hay algunas limitaciones que restringen a los programadores a implementar algunas características en los componentes de código. A continuación se indican algunas de las limitaciones:

1. Las API dependientes de Common Data Service, incluida WebAPI junto algunas otras API, no están disponibles para esta vista previa piloto. Para la disponibilidad de API individual para esta versión de vista previa piloto, consulte [ Referencia de API de Power Apps component framework](reference/index.md).
2. Los componentes de código deben agrupar todo el código incluidas bibliotecas externas en la agrupación de código principal. Para ver un ejemplo de cómo la interfaz de línea de comandos de Power Apps puede ayudar a agrupar su contenido de biblioteca externa en una agrupación específica del componente, vea el ejemplo de [Componente de Flip angular](sample-controls/angular-flip-control.md).

   > [!NOTE]
   > Las bibliotecas compartidas a través de componentes utilizando nodos de biblioteca en el manifiesto del componente aún no se admiten. Estamos revisando esto y agregaremos esta capacidad en una versión futura.

## <a name="related-topics"></a>Temas relacionados

[Referencia de la API de Power Apps component framework](reference/index.md)<br/>
[Información general sobre Power Apps component framework](overview.md)
