---
title: Usar etiquetas de variable para un portal | MicrosoftDocs
description: Obtenga información sobre las etiquetas variables disponibles en el portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="variable-tags"></a>Etiquetas variables

Las etiquetas variables se usan para crear nuevas variables de Liquid.

## <a name="assign"></a>asignar

Crea una nueva variable. Las asignaciones también pueden [filtros](liquid-filters.md) para modificar el valor.  

**Código**

```
{% assign is_valid = true %}

{% if is_valid %}

It is valid.

{% endif %}

{% assign name = dave bowman' | upcase %}

{{ name }}
```

**Salida**

```
It is valid.

DAVE BOWMAN
```

## <a name="capture"></a>capture

Captura el contenido en su bloque y lo asigna a una variable. Este contenido se puede representar más adelante utilizando etiquetas de salida.

**Código**

```
{% capture hello %}Hello, {{ user.fullname }}.{% endcapture %}

{{ hello }}

{{ hello }}
```

**Salida**

```
Hello, DAVE BOWMAN.

Hello, DAVE BOWMAN.
```

### <a name="see-also"></a>Vea también

[Etiquetas del flujo de control](control-flow-tags.md)<br>
[Etiquetas de iteración](iteration-tags.md)<br>
[Etiquetas de plantilla](template-tags.md)<br>
[Etiquetas de entidad de PowerApps common data service](portals-entity-tags.md)
