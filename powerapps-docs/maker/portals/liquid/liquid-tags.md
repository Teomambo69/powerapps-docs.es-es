---
title: Usar etiquetas líquidas para un portal | MicrosoftDocs
description: Obtenga información sobre las etiquetas líquidas disponibles en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b04c6447911d1a884627bd2cbb4ad7b74b9c5ce5
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976562"
---
# <a name="available-liquid-tags"></a>Etiquetas de Liquid disponibles

Las etiquetas componen la lógica de programación que indica a las plantillas qué hacer. Las etiquetas se incluyen en {%%}.

```
{% if user.fullname == 'Dave Bowman' %} Hello, Dave. {% endif %}
```

## <a name="whitespace-control"></a>Control de espacio en blanco

Normalmente, Liquid representa todo lo que se encuentra fuera de los bloques de variables y etiquetas literalmente, con todos los espacios en blanco tal cual. En ocasiones no querrá el espacio en blanco adicional, pero todavía desea formatear la plantilla sin problemas, lo que requiere un espacio en blanco.

Puede indicar al motor que elimine todos los espacios en blanco iniciales o finales agregando un guión (-) a la etiqueta del bloque inicial o final.

**Codifica**

```
{% for i in (1..5) --%}

{{ i }}

{%-- endfor %}
```

**Genere**

```
12345
```
### <a name="see-also"></a>Vea también

[Tipos de líquido](liquid-types.md)  
[Objetos Liquid](liquid-objects.md)  
[Filtros líquidos](liquid-filters.md) 
