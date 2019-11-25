---
title: Limitaciones de PowerApps component framework | MicrosoftDocs
description: Limitaciones del uso de PowerApps component framework
author: nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
ms.openlocfilehash: aabcf4518e71648797c795a006c2d842f3e5ff01
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749630"
---
# <a name="limitations"></a>Limitaciones 

Con el lanzamiento de PowerApps component framework, ahora puede crear sus propios componentes de código para mejorar la experiencia de usuario en aplicaciones basadas en modelo. Aunque puede crear sus propios componentes, hay algunas limitaciones que restringen a los programadores a implementar algunas características en los componentes de código. A continuación se indican algunas de las limitaciones:

1. Solo se admite el tipo de componentes *campo* en la vista previa piloto para aplicaciones de lienzo y no el tipo de componentes *conjunto de datos*. 
2. Las API dependientes de Common Data Service, incluida WebAPI junto algunas otras API, no están disponibles para esta vista previa piloto. Para la disponibilidad de API individual para esta versión de vista previa piloto, consulte [ Referencia de API de PowerApps component framework](reference/index.md).
3. Los componentes de código deben agrupar todo el código incluidas bibliotecas externas en la agrupación de código principal. Para ver un ejemplo de cómo la interfaz de línea de comandos de PowerApps puede ayudar a agrupar su contenido de biblioteca externa en una agrupación específica del componente, vea el ejemplo de [Componente de Flip angular](sample-controls/angular-flip-control.md).

   > [!NOTE]
   > Las bibliotecas compartidas a través de componentes utilizando nodos de biblioteca en el manifiesto del componente aún no se admiten. Estamos revisando esto y agregaremos esta capacidad en una versión futura.
4. Aún no es posible definir varios componentes en un solo archivo de manifiesto.
5. Aún no se admite llamar a procesos y acciones. Solo puede llamar a cuadros de diálogo mediante el método [Navegación](reference/navigation.md).
6. Llamar a un componente desde otro componente de código aún no se admite.
7. No se admite actualmente el recurso de fuente (.tff).

## <a name="related-topics"></a>Temas relacionados

[Referencia de la API de PowerApps component framework](reference/index.md)<br/>
[Información general sobre PowerApps component framework](overview.md)
