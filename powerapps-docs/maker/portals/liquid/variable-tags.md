---
title: Usar etiquetas de variable para un portal | MicrosoftDocs
description: Obtenga información sobre las etiquetas variables disponibles en el portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: fa375909ad3e909e70b3477d4e7ba0f24691fc0c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2707755"
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
