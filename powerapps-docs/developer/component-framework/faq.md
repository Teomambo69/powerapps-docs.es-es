---
title: Preguntas más frecuentes | MicrosoftDocs
description: Preguntas más frecuentes sobre el marco de componentes
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 9f940264-d7d5-4930-8052-1bd582445d37
ms.author: grhurl
author: ghurlman
ms.reviewer: nkrb
ms.openlocfilehash: e471cd617243b98635fa0db4a1487be4ddb1e5e9
ms.sourcegitcommit: 59f0b3adc56279b5673cbf04b4a55bd7678e1ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2020
ms.locfileid: "3091247"
---
# <a name="faqs"></a>P + F

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

### <a name="component-changes-are-not-reflected-after-the-updated-solution-import"></a>¿Los cambios en los componentes no se reflejan después de la importación de la solución actualizada?

Actualice la versión del componente (menor o revisión) en el archivo de manifiesto del componente (por ejemplo, 1.0.0 a 1.0.1). Cada actualización en el componente necesita un salto de versión del componente que se refleje en el servidor de Common Data Service.

> [!NOTE]
> - Se debe crear una nueva solución cada vez si desea tener un salto de versión principal. Incrementar el número de versión principal (por ejemplo, 1.0 a 2.0) no es compatible como actualización.
> - Solo se admiten tres secciones de versión (es decir, PRINCIPAL.MENOR.REVISIÓN). Estas secciones de número de versión deben estar entre 0 y 65536.

### <a name="what-are-the-things-to-be-considered-from-a-performance-perspective"></a>¿Cuáles son las cosas que deben considerarse desde una perspectiva de rendimiento?

1. Si desea acceder a una gran cantidad de elementos de datos, implemente métodoso [filtering](reference/filtering.md) y [paging](reference/paging.md) para limitar la cantidad de datos que se deben cargar.
2. Agrupe por lotes sus llamadas de red y realice todas las llamadas de red de forma asincrónica. Diseñe el componente de tal manera que toda la información requerida se proporcione con una sola llamada. 
3. Diseñe el componente de modo que el usuario tenga que realizar una acción (como hacer clic en un botón) para iniciar la carga de datos de un elemento específico en lugar de realizar la llamada para cada elemento de datos.
4. Asegúrese de limpiar los recursos utilizando la función [destroy](reference/control/destroy.md). Las llamadas de red abiertas, las conexiones y los controladores de eventos deben limpiarse para aumentar el rendimiento.

### <a name="where-can-i-find-some-good-examples-of-code-components"></a>¿Dónde puedo encontrar buenos ejemplos de componentes de código?

Muchos ejemplos excelentes de la comunidad están disponibles en los [Foros de la comunidad de Power Apps](https://powerusers.microsoft.com/t5/Power-Apps-Component-Framework/Community-content-sample-components-blogs-etc-Link-to-this-page/td-p/280710).

### <a name="how-to-use-rich-data-types-in-code-components-such-as-collections"></a>¿Cómo usar tipos de datos enriquecidos en componentes de código como Colecciones?

Actualmente no se admite esta característica. Sin embargo, hay una [función JSON](https://docs.microsoft.com/powerapps/maker/canvas-apps/functions/function-json) en aplicaciones de lienzo que permiten a los creadores de aplicaciones codificar sus datos.

1. Pase la colección a la función JSON.
2. Pase la representación de cadena de los datos de colección que se devuelven desde la función JSON a una de las propiedades de cadena del componente.
3. Utilice [JSON.parse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse) en el código de componente para convertirlo nuevamente en un Objeto JavaScript.

### <a name="how-can-i-define-multiple-components-in-a-single-manifest-file"></a>¿Cómo puedo definir varios componentes en un solo archivo de manifiesto?

No es posible definir varios componentes en un solo archivo de manifiesto. 

### <a name="how-can-i-define-behavior-properties"></a>¿Cómo puedo definir propiedades de comportamiento?

Esto no se admite en este momento. Actualmente, solo puede llamar a cuadros de diálogo utilizando el método [Navigation](reference/navigation.md) en aplicaciones basadas en modelo.

### <a name="how-can-i-call-other-components-from-within-another-component"></a>¿Cómo puedo llamar a otros componentes desde otro componente?

Esto no lo admite el marco de forma nativa. Puede usar una de las muchas bibliotecas de terceros para habilitar esta funcionalidad en sus componentes.

### <a name="can-i-bundle-font-resources"></a>¿Puedo agrupar recursos de fuentes?

Actualmente, el marco no admite recursos de fuente (archivos con extensión .ttf).

## <a name="related-topics"></a>Temas relacionados

[Referencia de la API de Power Apps component framework](reference/index.md)<br/>
[Información general sobre Power Apps component framework](overview.md)
