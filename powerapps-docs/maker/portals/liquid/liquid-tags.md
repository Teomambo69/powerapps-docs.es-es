---
title: Usar etiquetas de Liquid para un portal | MicrosoftDocs
description: Obtenga información acerca de las etiquetas de Liquid disponibles en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
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
