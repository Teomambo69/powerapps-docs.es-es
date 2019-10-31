---
title: Usar etiquetas de iteración para un portal | MicrosoftDocs
description: Obtenga información sobre las etiquetas de iteración disponibles en el portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="iteration-tags"></a>Etiquetas de iteración

Las etiquetas de iteración se usan para ejecutar/representar un bloque de código repetidamente.

## <a name="for"></a>para

Ejecuta un bloque de código repetidamente. Suele utilizarse para iterar los elementos en una matriz o un diccionario.

En el bloque de etiquetas, el [objeto forloop](liquid-objects.md#forloop) está disponible.  

**Código**

```
{% for child_page in page.children %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Salida**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

### <a name="parameters"></a>Parámetros

Estos parámetros de for pueden utilizarse solos o en combinación.

**limit**

Sale del bucle después de un número determinado de elementos.

**Código**

```
{% for child_page in page.children limit:2 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Salida**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>
```

**offset**

Inicia el bucle en un índice determinado.

**Código**

```
{% for child_page in page.children offset:1 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Salida**

```
<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

**range**

Define un intervalo de números para recorrer en bucle.

**Código**

```
{% assign n = 4 %}

{% for i in (2..n) %}

{{ i }}

{% endfor %}

{% for i in (10..14) %}

{{ i }}

{% endfor }}
```

**Salida**

```
2 3 4

10 11 12 14
```

**reversed**

Itera a través del bucle en orden inverso, empezando por el último elemento.

**Código**

```
{% for child_page in page.children reversed %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Salida**

```
<a href=/parent/child3/>Child 3</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child1/>Child 1</a>
```

## <a name="cycle"></a>cycle

Recorre en bucle un grupo de cadenas y los extrae en el orden en que se pasaron como parámetros. Cada vez que se llamada a un ciclo, se extrae la siguiente cadena que se pasó como parámetro.

**Código**

```
{% for item in items %}

<div class={% cycle 'red', 'green', 'blue' %}> {{ item }} </div>

{% end %}
```

**Salida**

```
<div class=red> Item one </div>

<div class=green> Item two </div>

<div class=blue> Item three </div>

<div class=red> Item four </div>

<div class=green> Item five</div>
```

## <a name="tablerow"></a>tablerow

Genera una tabla HTML. Debe ir entre etiquetas HTML &lt;table&gt; de apertura y &lt;/table&gt; de cierre.

En el bloque de etiquetas tablerow, el [tablerowloop](liquid-objects.md#tablerowloop) está disponible.  

**Código**

```
<table>

{% tablerow child_page in page.children %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Salida**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 1

</td>

<td class=col2>

Child Page 2

</td>

<td class=col3>

Child Page 3

</td>

<td class=col4>

Child Page 4

</td>

</tr>

</table>
```

### <a name="parameters"></a>Parámetros

Estos parámetros de tablerow pueden utilizarse solos o en combinación.

**Salida**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 1

</td>

<td class=col2>

Child Page 2

</td>

</tr>

<tr class=row2>

<td class=col3>

Child Page 3

</td>

<td class=col4>

Child Page 4

</td>

</tr>

</table>
```

**Código**

```
<table>

{% tablerow child_page in page.children cols:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

Dicta el número de filas que debe tener la tabla generada.

**cols**

**limit**

Sale del bucle después de un número determinado de elementos.

**Código**

```
<table>

{% tablerow child_page in page.children limit:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Salida**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 1

</td>

<td class=col2>

Child Page 2

</td>

</tr>

</table>

offset
```

Inicia el bucle en un índice determinado.

**Código**

```
<table>

{% tablerow child_page in page.children offset:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Salida**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 3

</td>

<td class=col2>

Child Page 4

</td>

</tr>

</table>
```

**range**

Define un intervalo de números para recorrer en bucle.

**Código**

```
<table>

{% tablerow i in (1..3) %}

{{ i }}

{% endtablerow %}

</table>
```

### <a name="see-also"></a>Vea también

[Etiquetas de flujo de control](control-flow-tags.md)
[Etiquetas de variable](variable-tags.md)
[Etiquetas de plantilla](template-tags.md)
[Etiquetas de entidad de PowerApps Common Data Service](portals-entity-tags.md)
