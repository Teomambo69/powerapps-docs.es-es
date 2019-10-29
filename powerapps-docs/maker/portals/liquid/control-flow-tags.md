---
title: Usar etiquetas de flujo de control para un portal | MicrosoftDocs
description: Obtenga información sobre las etiquetas de flujo de control disponibles en el portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 77fcc7db0adf68cd6decbcc95e11d8e803761535
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975113"
---
# <a name="control-flow-tags"></a>Etiquetas de flujo de control

Las etiquetas de flujo de control determinan qué bloque de código se debe ejecutar y qué contenido se debe representar en función de las condiciones especificadas. Las condiciones se crean mediante los [operadores Liquid](liquid-operators.md)disponibles o simplemente se basan en [la veracidad o el falsehood de un valor determinado](liquid-conditional-operators.md).  

## <a name="if"></a>Cuando

Ejecuta un bloque de código si se cumple una condición determinada.

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% endif %}
```

## <a name="unless"></a>vaya

Como si, salvo que ejecuta un bloque de código si**no** se cumple una condición determinada.

```
{% unless page.title == 'Home' %}

This is not the Home page.

{% endunless %}
```

## <a name="elsifelse"></a>ELSIF/else

Agrega más condiciones a un bloque if o a menos que.

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% elsif user.fullname == 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endif %}
```

## <a name="casewhen"></a>caso/cuando

Una instrucción switch para comparar una variable con distintos valores y ejecutar un bloque de código diferente para cada valor.

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
[Etiquetas de variables](variable-tags.md)<br>
[Etiquetas de plantilla](template-tags.md)<br>
[Etiquetas de entidad de Common Data Service de PowerApps](portals-entity-tags.md)
