---
title: Usar etiquetas de iteración para un portal | MicrosoftDocs
description: Más información sobre las etiquetas de iteración disponibles en el portal
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 600ddb0ac6e016acf057e592ac638b4e07ddf8ba
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976516"
---
# <a name="iteration-tags"></a>Etiquetas de iteración

Las etiquetas de iteración se usan para ejecutar o representar un bloque de código de forma repetida.

## <a name="for"></a>para

Ejecuta un bloque de código de forma repetida. Normalmente se usa para iterar por los elementos de una matriz o un diccionario.

En el bloque de etiquetas for, el [objeto forloop](liquid-objects.md#forloop) está disponible.  

**Codifica**

```
{% for child_page in page.children %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Genere**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

### <a name="parameters"></a>Parámetros

Estos parámetros de para se pueden usar solos o en combinación.

**ilimitado**

Sale del bucle después de un número determinado de elementos.

**Codifica**

```
{% for child_page in page.children limit:2 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Genere**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>
```

**posición**

Inicia el bucle en el índice especificado.

**Codifica**

```
{% for child_page in page.children offset:1 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Genere**

```
<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

**variedad**

Define un intervalo de números que se van a recorrer.

**Codifica**

```
{% assign n = 4 %}

{% for i in (2..n) %}

{{ i }}

{% endfor %}

{% for i in (10..14) %}

{{ i }}

{% endfor }}
```

**Genere**

```
2 3 4

10 11 12 14
```

**invertido**

Recorre en iteración el bucle en orden inverso, empezando por el último elemento.

**Codifica**

```
{% for child_page in page.children reversed %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Genere**

```
<a href=/parent/child3/>Child 3</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child1/>Child 1</a>
```

## <a name="cycle"></a>interrumpa

Recorre en bucle un grupo de cadenas y las envía en el orden en que se pasaron como parámetros. Cada ciclo de tiempo se llama, la siguiente cadena que se pasó como parámetro es output.

**Codifica**

```
{% for item in items %}

<div class={% cycle 'red', 'green', 'blue' %}> {{ item }} </div>

{% end %}
```

**Genere**

```
<div class=red> Item one </div>

<div class=green> Item two </div>

<div class=blue> Item three </div>

<div class=red> Item four </div>

<div class=green> Item five</div>
```

## <a name="tablerow"></a>TableRow

Genera una tabla HTML. Se debe incluir en una &lt;de apertura de tabla&gt; y cierre de &lt;/Table&gt; etiquetas HTML.

Dentro del bloque de etiquetas TableRow, [tablerowloop](liquid-objects.md#tablerowloop) está disponible.  

**Codifica**

```
<table>

{% tablerow child_page in page.children %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Genere**

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

Estos parámetros de tablerowcan se usan solos o en combinación.

**Genere**

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

**Codifica**

```
<table>

{% tablerow child_page in page.children cols:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

Determina el número de filas que debe tener la tabla generada.

**columnas**

**ilimitado**

Sale del bucle después de un número determinado de elementos.

**Codifica**

```
<table>

{% tablerow child_page in page.children limit:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Genere**

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

Inicia el bucle en el índice especificado.

**Codifica**

```
<table>

{% tablerow child_page in page.children offset:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Genere**

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

**variedad**

Define un intervalo de números que se van a recorrer.

**Codifica**

```
<table>

{% tablerow i in (1..3) %}

{{ i }}

{% endtablerow %}

</table>
```

### <a name="see-also"></a>Vea también

[Etiquetas de flujo de Control](control-flow-tags.md)
[etiquetas de variable](variable-tags.md)
[etiquetas de plantilla](template-tags.md)
etiquetas de [entidad de Common Data Service de PowerApps](portals-entity-tags.md)
