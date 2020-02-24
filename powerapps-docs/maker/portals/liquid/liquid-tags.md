---
title: Usar etiquetas de Liquid para un portal | MicrosoftDocs
description: Obtenga información acerca de las etiquetas de Liquid disponibles en un portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 3f85e4b86b305696f5b155c7e9e3b773f8ba2103
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2981117"
---
# <a name="available-liquid-tags"></a>Etiquetas de Liquid disponibles

Las etiquetas conforman la lógica de programación que indica a las plantillas qué deben hacer. Las etiquetas están envueltas en {% %}.

```
{% if user.fullname == 'Dave Bowman' %} Hello, Dave. {% endif %}
```

## <a name="whitespace-control"></a>Control de espacio en blanco

Normalmente Liquid representa todo lo que está fuera de la variable y bloques de etiqueta textualmente, con todo el espacio en blanco como se encuentra. En algunos casos no conviene el espacio en blanco adicional, pero sí dar formato a la plantilla limpiamente, lo que requiere espacio en blanco.

Puede indicar al motor que elimine todo el espacio en blanco inicial o final agregando un guión (-) a la etiqueta de bloque inicial o final.

**Código**

```
{% for i in (1..5) --%}

{{ i }}

{%-- endfor %}
```

**Salida**

```
12345
```
### <a name="see-also"></a>Vea también

[Tipos Liquid](liquid-types.md)  
[Objetos de Liquid](liquid-objects.md)  
[Filtros de Liquid](liquid-filters.md) 
