---
title: Usar operadores condiciones de Liquid para un portal | MicrosoftDocs
description: Obtenga información acerca de los operadores condicionales de Liquid disponibles en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="available-liquid-conditional-operators"></a>Operadores condicionales de Liquid disponibles

Cuando se usa en instrucciones condicionales (**si**, **a menos que**), algunos valores de Liquid se tratan como true, y otros como false.

En Liquid, null y el valor booleano false se tratan como false; todo lo demás se trata como true. Cadenas vacías, matrices vacías, etc. se tratan como true. Por ejemplos:

```
{% assign empty_string =  %}
{% if empty_string %}
<p>This will render.</p>
{% endif %}
```
Puede comprobar cadenas y matrices vacías mediante el vacío de valor especial si es necesario.

```
{% unless page.title == empty %}
<h1>{{ page.title }}</h1>
{% endunless %}
```
También puede probar el tamaño de [Tipos Liquid](liquid-types.md)[Tipos Liquid](liquid-types.md), o [Tipos Liquid](liquid-types.md) con la propiedad especial size.

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

|                           | VERDADERO | FALSO |
|---------------------------|------|-------|
| VERDADERO                      | ×    |       |
| FALSO                     |      | ×     |
| Null                      |      | ×     |
| Cadena                    | ×    |       |
| cadena vacía              | ×    |       |
| 0                         | ×    |       |
| 1, 3.14                   | ×    |       |
| matriz o diccionario       | ×    |       |
| matriz o diccionario vacío | ×    |       |
| Objeto                    | ×    |       |

### <a name="see-also"></a>Vea también

[Almacenar contenido de origen con plantillas web](store-content-web-templates.md)  
[Descripción de los operadores de Liquid](liquid-operators.md)  
[Tipos Liquid](liquid-types.md)  
[Objetos de Liquid](liquid-objects.md)  
[Etiquetas de Liquid](liquid-tags.md)  
[Filtros de Liquid](liquid-filters.md)  
