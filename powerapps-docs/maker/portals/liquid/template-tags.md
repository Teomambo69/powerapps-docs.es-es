---
title: Usar etiquetas de plantilla para un portal | MicrosoftDocs
description: Más información sobre las etiquetas de plantilla disponibles en el portal
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 4475e9e2ccc474a6eeb3e7a2e959b360b3250aa8
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543288"
---
# <a name="template-tags"></a>Etiquetas de plantilla

Las etiquetas de plantilla controlan la salida de una plantilla de varias maneras y permiten la combinación de varias plantillas en una sola salida.

## <a name="include"></a>inclui

Incluye el contenido de una plantilla en otro, por nombre. En los portales de PowerApps, el origen de esta otra plantilla será normalmente una [plantilla Web](store-content-web-templates.md). Esto permite la reutilización de fragmentos de plantilla comunes en varios lugares.  

Cuando una plantilla se incluye en otra, la plantilla incluida tendrá acceso a las variables definidas en la plantilla primaria.

`{% include 'My Template' %}`

También es posible pasar cualquier número de parámetros con nombre a la etiqueta include. Estos se definirán como variables en la plantilla incluida.

`{% include 'My Template' a:x, b:y %}`

## <a name="block"></a>Sin

Se usa junto con extiende para proporcionar la herencia de la plantilla. Consulte extends for Usage.

## <a name="extends"></a>llegar

Se usa junto con la etiqueta de bloque, y proporciona herencia de plantillas. Esto permite que varias plantillas usen un diseño compartido, al tiempo que se invalidan áreas específicas del diseño primario.

En los portales de PowerApps, el nombre de la plantilla principal que se proporciona a la etiqueta normalmente hará referencia al nombre de una [plantilla Web](store-content-web-templates.md).  

Cuando se utiliza extends, debe ser el primer contenido de la plantilla y solo puede ir seguido de una o varias etiquetas de bloque.

Si no se invalida un bloque definido en la plantilla primaria, se representará su contenido en la plantilla primaria (si existe).

## <a name="comment"></a>comentario

Permite dejar código sin representar dentro de una plantilla Liquid. No se representará ningún contenido del bloque y no se ejecutará ningún código de líquido dentro de.

**Codifica**

`Hello{% comment %}, {{ user.fullname }}{% endcomment %}. My name is Charles.`

**Genere**

`Hello. My name is Charles.`

## <a name="raw"></a>Socket

Permite la salida de código líquido en una página sin que se analice y se ejecute.

**Genere**

`Hello, {{ user.fullname }}. My name is Charles.`

### <a name="see-also"></a>Vea también

[Etiquetas de flujo de control](control-flow-tags.md)<br>
[Etiquetas de iteración](iteration-tags.md)<br>
[Etiquetas de variables](variable-tags.md)<br>
[Etiquetas de entidad de Common Data Service de PowerApps](portals-entity-tags.md)
