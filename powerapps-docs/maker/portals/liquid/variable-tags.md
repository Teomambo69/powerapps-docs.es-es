---
title: Usar etiquetas de variables para un portal | MicrosoftDocs
description: Más información sobre las etiquetas de variables disponibles en el portal
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: fa375909ad3e909e70b3477d4e7ba0f24691fc0c
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974423"
---
# <a name="variable-tags"></a>Etiquetas variables

Las etiquetas de variables se usan para crear nuevas variables líquidas.

## <a name="assign"></a>quitar

Crea una nueva variable. Las asignaciones también pueden utilizar [filtros](liquid-filters.md) para modificar el valor.  

**Codifica**

```
{% assign is_valid = true %}

{% if is_valid %}

It is valid.

{% endif %}

{% assign name = dave bowman' | upcase %}

{{ name }}
```

**Genere**

```
It is valid.

DAVE BOWMAN
```

## <a name="capture"></a>grabar

Captura el contenido dentro de su bloque y lo asigna a una variable. Este contenido puede representarse posteriormente mediante el uso de etiquetas de salida.

**Codifica**

```
{% capture hello %}Hello, {{ user.fullname }}.{% endcapture %}

{{ hello }}

{{ hello }}
```

**Genere**

```
Hello, DAVE BOWMAN.

Hello, DAVE BOWMAN.
```

### <a name="see-also"></a>Vea también

[Etiquetas de flujo de control](control-flow-tags.md)<br>
[Etiquetas de iteración](iteration-tags.md)<br>
[Etiquetas de plantilla](template-tags.md)<br>
[Etiquetas de entidad de Common Data Service de PowerApps](portals-entity-tags.md)
