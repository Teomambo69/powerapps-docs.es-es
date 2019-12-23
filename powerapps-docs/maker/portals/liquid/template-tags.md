---
title: Usar etiquetas de plantilla para un portal | MicrosoftDocs
description: Obtenga información sobre las etiquetas de plantilla disponibles en el portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 951b4055aa47a6fba31df5473bd517ed67c8f17d
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2873241"
---
# <a name="template-tags"></a>Etiquetas de plantilla

Las etiquetas de plantilla controlan el resultado de una plantilla de varias formas, y permiten combinar varias plantillas en una sola.

## <a name="include"></a>include

Incluye el contenido de una plantilla en otra, por nombre. En los portales de Power Apps, el origen de esta otra plantilla será normalmente una [plantilla web](store-content-web-templates.md). Esto permite la reutilización de fragmentos comunes de plantilla en varios lugares.  

Cuando una plantilla se incluye en otra, la plantilla incluida tendrá acceso a las variables definidas en la plantilla primaria.

`{% include 'My Template' %}`

También es posible pasar cualquier número de parámetros con nombre a la etiqueta include. Estos a continuación se definirán como variables de la plantilla incluida.

`{% include 'My Template' a:x, b:y %}`

## <a name="block"></a>block

Usado junto con extends para proporcionar herencia de plantilla. Vea extends para uso.

## <a name="extends"></a>extends

Usado junto con la etiqueta block para proporcionar herencia de plantilla. Esto permite que varias plantillas usen un diseño compartido, al tiempo que reemplazan áreas específicas del diseño primario.

En los portales de Power Apps, el nombre de la plantilla primaria suministrado a la etiqueta normalmente hará referencia al nombre de una [plantilla web](store-content-web-templates.md).  

Cuando se utiliza extends, debe ser el primer contenido de la plantilla, y solo puede ir seguido de una o más etiquetas block.

Si un bloque definido en la plantilla principal no se reemplaza, su contenido en la plantilla primaria (si lo hay) se representarán.

## <a name="comment"></a>comentario

Permite dejar código no representado dentro una plantilla de Liquid. No se representará ningún contenido dentro del bloque y no se ejecutará ningún código de Liquid dentro.

**Código**

`Hello{% comment %}, {{ user.fullname }}{% endcomment %}. My name is Charles.`

**Salida**

`Hello. My name is Charles.`

## <a name="raw"></a>raw

Permite el resultado de código de Liquid en una página sin analizarlo ni ejecutarlo.

**Salida**

`Hello, {{ user.fullname }}. My name is Charles.`

## <a name="substitution"></a>sustitución

Cuando el usuario ha habilitado el almacenamiento en caché del encabezado y pie de página, y desea evitar el almacenamiento en caché de los resultados de cierta sección, puede usar esta etiqueta. Esta etiqueta proporciona el bloque de contenido en el encabezado o pie de página donde el resultado del bloque de contenido envuelto no se almacena en caché. Esto es útil en escenarios en los que el usuario usa un objeto que se puede actualizar con frecuencia, como solicitud, página, idioma y fecha. Por ejemplo, consulte los escenarios de actualización del código fuente de la plantilla web de encabezado y pie de página cuando [el almacenamiento en caché del encabezado y pie de página esté habilitado](../configure/enable-header-footer-output-caching.md).

### <a name="see-also"></a>Vea también

[Etiquetas del flujo de control](control-flow-tags.md)<br>
[Etiquetas de iteración](iteration-tags.md)<br>
[Etiquetas variables](variable-tags.md)<br>
[Etiquetas de entidad de Power Apps common data service](portals-entity-tags.md)
