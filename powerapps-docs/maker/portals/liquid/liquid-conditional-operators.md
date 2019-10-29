---
title: Usar operadores condicionales Liquid para un portal | MicrosoftDocs
description: Obtenga información sobre los operadores condicionales de Liquid disponibles en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: def132ebc0f8ef93121b10b221479a2452a1d4fb
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975021"
---
# <a name="available-liquid-conditional-operators"></a>Operadores condicionales de Liquid disponibles

Cuando se usa en instrucciones condicionales (**si**,**a menos que**), algunos valores de líquido se tratarán como true y otros se tratarán como false.

En Liquid, NULL y el valor booleano false se tratan como false; todo lo demás se trata como true. Las cadenas vacías, las matrices vacías, etc. se tratan como true. Por ejemplo,

```
{% assign empty_string =  %}
{% if empty_string %}
<p>This will render.</p>
{% endif %}
```
Puede comprobar si hay cadenas vacías y matrices mediante el valor especial vacío si es necesario.

```
{% unless page.title == empty %}
<h1>{{ page.title }}</h1>
{% endunless %}
```
También puede probar el tamaño de los [tipos de líquido](liquid-types.md), los [tipos de líquido](liquid-types.md)o los [tipos de líquido](liquid-types.md) mediante la propiedad de tamaño especial.

```
{% if page.children.size > 0 %}
<ul>
{% for child in page.children %}
<li>{{ child.title }}</li>
{% endfor %}
</ul>
{% endif %}
```

## <a name="summary"></a>Resumen

|                           | True | Es |
|---------------------------|------|-------|
| True                      | 800x600    |       |
| Es                     |      | 800x600     |
| Acepta                      |      | 800x600     |
| Cadena                    | 800x600    |       |
| Cadena vacía              | 800x600    |       |
| 0                         | 800x600    |       |
| 1, 3,14                   | 800x600    |       |
| matriz o Diccionario       | 800x600    |       |
| matriz o Diccionario vacíos | 800x600    |       |
| Objeto                    | 800x600    |       |

### <a name="see-also"></a>Vea también

[Almacenar contenido de origen mediante plantillas web](store-content-web-templates.md)  
[Descripción de los operadores Liquid](liquid-operators.md)  
[Tipos de líquido](liquid-types.md)  
[Objetos Liquid](liquid-objects.md)  
[Etiquetas líquidas](liquid-tags.md)  
[Filtros líquidos](liquid-filters.md)  
