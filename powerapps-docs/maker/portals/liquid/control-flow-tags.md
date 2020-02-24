---
title: Usar etiquetas del flujo de control para un portal | MicrosoftDocs
description: Obtener información sobre las etiquetas del flujo de control disponibles en el portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 1cdc608253bef652445f0eb689435f0089629979
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977289"
---
# <a name="control-flow-tags"></a>Etiquetas del flujo de control

Las etiquetas del flujo de control determinan qué bloque de código se debe ejecutar y qué contenido se debe representar según las condiciones dadas. Las condiciones se crean mediante los [operadores de Liquid](liquid-operators.md) disponibles, o simplemente se basan en si [un valor determinado es verdadero o falso](liquid-conditional-operators.md).  

## <a name="if"></a>if

Ejecuta un bloque de código si se cumple una condición determinada.

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% endif %}
```

## <a name="unless"></a>unless

Al igual que if, ejecuta un bloque de código si **no** se cumple una condición determinada.

```
{% unless page.title == 'Home' %}

This is not the Home page.

{% endunless %}
```

## <a name="elsifelse"></a>elsif/else

Agrega más condiciones a un bloque if o unless.

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% elsif user.fullname == 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endif %}
```

## <a name="casewhen"></a>case/when

Una instrucción de cambio para comparar una variable con diferentes valores, y ejecutar otro bloque de código para cada valor.

```
{% case user.fullname %}

{% when 'Dave Bowman' %}

Hello, Dave.

{% when 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endcase %}
```

### <a name="see-also"></a>Vea también

[Etiquetas de iteración](iteration-tags.md)<br>
[Etiquetas variables](variable-tags.md)<br>
[Etiquetas de plantilla](template-tags.md)<br>
[Etiquetas de entidad de Power Apps common data service](portals-entity-tags.md)
