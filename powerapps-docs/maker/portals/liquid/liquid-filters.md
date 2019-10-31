---
title: Usar filtros de Liquid para un portal | MicrosoftDocs
description: Obtenga información acerca de los filtros de Liquid disponibles en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="available-liquid-filters"></a>Filtros de Liquid disponibles

Los filtros de Liquid se usan para modificar el resultado de cadenas, números, variables y objetos. Están separados del valor al que se aplican mediante una |.

`{{ 'hal 9000' | upcase }} <!-- Output: HAL 9000 -->`

Algunos filtros aceptan parámetros. Los filtros también se pueden combinar, y se aplican en orden de izquierda a derecha.

```
{{ 2 | times: 2 | minus: 1 }} <!-- Output: 3 -->

{{ "Hello, " | append: user.firstname }} <!-- Output: Hello, Dave -->
```
La sección a continuación describe los diferentes filtros. 

## <a name="array-filters"></a>Filtros de matriz

Los filtros de matriz se usan para trabajar con [matrices](liquid-types.md#array).  

### <a name="batch"></a>batch

Divide una matriz en matrices múltiples de un determinado tamaño.

**Código**

```
{% assign batches = entityview.records | batch: 2 %}

{% for batch in batches %}

<ul>

{% for item in batch %}

<li>{{ item.fullname }}</li>

{% endfor %}

</ul>

{% endfor %}
```

**Salida**

```
<ul>

<li>John Smith</li>

<li>Dave Thomas</li>

</ul>

<ul>

<li>Jake Johnson</li>

<li>Jack Robinson</li>

</ul>
```

### <a name="concat"></a>concat

Concatena dos matrices en un matriz nueva y única.

Dado un solo elemento como parámetro, concat devuelve una nueva matriz que consiste en la matriz original, con el elemento dado como último elemento.

**Código**

```
Group #1: {{ group1 | join: ', ' }}

Group #2: {{ group2 | join: ', ' }}

Group #1 + Group #2: {{ group1 | concat: group2 | join: ', ' }}

Group #1 + Leslie: {{ group1 | concat: 'Leslie' | join: ', ' }}
```

**Salida**

```
Group #1: John, Pete, Hannah

Group #2: Joan, Bill

Group #1 + Group #2: John, Pete, Hannah, Joan, Bill

Group #1 + Leslie: John, Pete, Hannah, Leslie
```

### <a name="except"></a>except

Seleccione todos los objetos de una matriz en la que un atributo determinado no tiene un valor determinado. (Es lo contrario de**where**).

**Código**

```
{% assign redmond = entityview.records | except: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**Salida**

```
Jack Robinson
```

### <a name="first"></a>primero

Devuelve el primer elemento de una matriz.

first también se puede usar con la notación de punto especial, en casos en los que sea necesario usarla dentro de una etiqueta.

**Código**

```
{% assign words = This is a run of text | split:   %}

{{ words | first }}

{% if words.first == This %}

The first word is This.

{% endif %}
```

**Salida**

```
This

The first word is This.
```

### <a name="group_by"></a>group_by

Agrupa los elementos en una matriz por un atributo determinado.

**Código**

```
{% assign groups = entityview.records | group_by: 'address1_city' %}

{% for group in groups %}

{{ group.key }}:

{% for item in group.items %}

{{ item.fullname }}

{% endfor %}

{% endfor %}
```

**Salida**

```
Redmond:

John Smith

Dave Thomas

Jake Johnson

New York:

Jack Robinson
```

### <a name="join"></a>join

Combina los elementos de una matriz con el carácter pasado como parámetro. El resultado es una sola cadena.

**Código**

```
{% assign words = This is a run of text | split:   %}

{{ words | join: ,  }}
```

**Salida**

```
This, is, a, run, of, text
```

### <a name="last"></a>Último

Devuelve el último elemento de una matriz.

last también se puede usar con la notación de punto especial, en casos en los que sea necesario usarla dentro de una etiqueta.

**Código**

```
{% assign words = This is a run of text | split:   -%}

{{ words | last }}

{% if words.last == text -%}

The last word is text.

{% endif -%}
```

**Salida**

```
text

The last word is text.
```

### <a name="order_by"></a>order\_by

Devuelve los elementos de una matriz ordenada por atributo dado de los elementos de la matriz.

De manera opcional, puede proporcionar desc como segundo parámetro para ordenar los elementos en orden descendente, en lugar de ascendente.

**Código**

```
{{ entityview.records | order_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'fullname', 'desc' | join: ', ' }}
```

**Salida**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="random"></a>random

Devuelve un solo elemento seleccionado aleatoriamente de la matriz.

**Código**

```
{{ group1 | join: ', ' }}

{{ group1 | random }}
```

**Salida**

```
John, Pete, Hannah

Pete
```

### <a name="select"></a>select

Selecciona el valor de un atributo determinado para cada elemento de una matriz, y devuelve estos valores como matriz.

**Código**

```
{{ entityview.records | select: 'address1_city' | join: ', ' }}
```

**Salida**

```
Redmond, New York
```

### <a name="shuffle"></a>shuffle

Aplicado a una matriz, devuelve una nueva matriz con los mismos elementos, en orden aleatorizado.

**Código**

```
{{ group1 | join: ', ' }}

{{ group1 | shuffle | join: ', ' }}
```

**Output**

```
John, Pete, Hannah

Hannah, John, Pete
```

### <a name="size"></a>size

Devuelve el número de elementos de una matriz.

size también se puede usar con la notación de punto especial, en casos en los que sea necesario usarla dentro de una etiqueta.

**Código**

```
{% assign words = This is a run of text | split:   -%}

{{ words | size }}

{% if words.size == 6 -%}

The text contains 6 words.

{% endif -%}
```

**Salida**

```
6

The text contains 6 words.
```

### <a name="skip"></a>skip

Omite un número determinado de elementos de una matriz, y devuelve el resto.

**Código**

```
{% assign words = This is a run of text | split:   %}

{{ words | skip: 3 | join: ', ' }}
```

**Salida**

```
run, of, text
```

### <a name="take"></a>take

Toma un número determinado de elementos de la matriz, devolviendo los elementos tomados.

**Código**

```
{% assign words = This is a run of text | split:   %}

{{ words | take: 3 | join: ', ' }}
```
**Salida**

```

This, is, a
```

### <a name="then_by"></a>then\_by

Agrega orden posterior adicional a una matriz ya ordenada mediante**order\_by**.

De manera opcional, puede proporcionar desc como segundo parámetro para ordenar los elementos en orden descendente, en lugar de ascendente.

**Código**

```
{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname', 'desc' | join: ', ' }}
```

**Salida**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="where"></a>donde

Seleccione todos los objetos de una matriz en la que un atributo determinado tiene un valor determinado.

**Código**

```
{% assign redmond = entityview.records | where: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**Salida**

```
John Smith

Dave Thomas

Jake Johnson
```


## <a name="date-filters"></a>Filtros por fecha

Los filtros por fecha se pueden usar para la aritmética de fecha o para convertir valores de fecha y hora en distintos formatos.

### <a name="date"></a>fecha

Aplica formato a un valor de fecha y hora con una cadena de formato .NET.

[Cadenas de formato estándar de fecha y hora](https://docs.microsoft.com/en-us/dotnet/standard/base-types/standard-date-and-time-format-strings)  

[Cadenas de formato personalizado de fecha y hora](https://docs.microsoft.com/en-us/dotnet/standard/base-types/custom-date-and-time-format-strings)  

**Código**

```
{{ now | date: 'g' }}

{{ now | date: 'MMMM dd, yyyy' }}
```

**Salida**

```
5/7/2018 7:20 AM

May 07, 2018
```

### <a name="date_add_days"></a>date\_add\_days

Agrega un número especificado de días enteros y fraccionarios al valor de fecha y hora. El parámetro pueden ser positivo o negativo.

**Código**

```
{{ now }}

{{ now | date_add_days: 1 }}

{{ now | date_add_days: -2.5 }}
```

**Salida**

```
5/7/2018 7:20:46 AM

5/8/2018 7:20:46 AM

5/4/2018 7:20:46 PM
```

### <a name="date_add_hours"></a>date\_add\_hours

Agrega un número especificado de horas enteras y fraccionarias al valor de fecha y hora. El parámetro pueden ser positivo o negativo.

**Código**

```
{{ now }}

{{ now | date_add_hours: 1 }}

{{ now | date_add_hours: -2.5 }}
```

**Salida**

```
5/7/2018 7:20:46 AM

5/7/2018 8:20:46 AM

5/7/2018 4:50:46 AM
```

### <a name="date_add_minutes"></a>date\_add\_minutes

Agrega un número especificado de minutos enteros y fraccionarios al valor de fecha y hora. El parámetro pueden ser positivo o negativo.

**Código**

```
{{ now }}

{{ now | date_add_minutes: 10 }}

{{ now | date_add_minutes: -2.5 }}
```


**Salida**

```
5/7/2018 7:20:46 AM

5/7/2018 7:30:46 AM

5/7/2018 7:18:16 AM
```

### <a name="date_add_months"></a>date\_add\_months

Agrega un número especificado de meses enteros al valor de fecha y hora. El parámetro pueden ser positivo o negativo.

**Código**

```
{{ now }}

{{ now | date_add_months: 1 }}

{{ now | date_add_months: -2 }}
```

**Salida**

```
5/7/2018 7:20:46 AM

6/7/2018 7:20:46 AM

3/7/2018 7:20:46 AM
```

### <a name="date_add_seconds"></a>date\_add\_seconds

Agrega un número especificado de segundos enteros y fraccionarios al valor de fecha y hora. El parámetro pueden ser positivo o negativo.

**Código**

```
{{ now }}

{{ now | date_add_seconds: 10 }}

{{ now | date_add_seconds: -1.25 }}
```

**Salida**

```
5/7/2018 7:20:46 AM

5/7/2018 7:20:56 AM

5/7/2018 7:20:45 AM
```

### <a name="date_add_years"></a>date\_add\_years

Agrega un número especificado de años enteros al valor de fecha y hora. El parámetro pueden ser positivo o negativo.

**Código**

```
{{ now }}

{{ now | date_add_years: 1 }}

{{ now | date_add_years: -2 }}
```

**Salida**

```
5/7/2018 7:20:46 AM

5/7/2019 7:20:46 AM

5/7/2016 7:20:46 AM
```

### <a name="date_to_iso8601"></a>date\_to\_iso8601

Aplica formato a un valor de fecha y hora de acuerdo con la norma [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601). Útil para crear fuentes [*Atom*](http://tools.ietf.org/html/rfc4287) o el elemento HTML5 &lt;&gt;.  

**Código**

```
{{ now | date_to_iso8601 }}
```

**Salida**

```
2018-05-07T07:20:46Z
```

### <a name="date_to_rfc822"></a>date\_to\_rfc822

Aplica formato a un valor de fecha y hora de acuerdo con la norma [RFC 822](https://www.ietf.org/rfc/rfc0822.txt). Útil para crear fuentes [*RSS*](http://cyber.law.harvard.edu/rss/rss.html).  

**Código**

```
{{ now | date_to_rfc822 }}
```

**Salida**

```
Mon, 07 May 2018 07:20:46 Z
```


## <a name="entity-list-filters"></a>Filtros de lista de entidades

Los filtros de lista de entidades se usan para trabajar con determinados valores de atributo [entitylist](liquid-objects.md#entitylist) y para ayudar a crear vistas de lista de entidades.  

### <a name="current_sort"></a>current\_sort

Dada una expresión de ordenación, devuelve la dirección de ordenación actual para un atributo determinado.

**Código**

```
{{ 'name ASC, createdon DESC' | current_sort: 'createdon' }}
```

**Salida**

```
DESC
```

### <a name="metafilters"></a>metafilters

Analiza un valor JSON de [entitylist](liquid-objects.md#entitylist) filtro\_definición en objetos de grupo de opciones de filtro.  

metafilters se puede ofrecer opcionalmente con una consulta de filtro de atributos actual y una [entitylist](liquid-objects.md#entitylist) actual, lo que permite que los objetos de filtro devueltos se marquen como seleccionados o no seleccionados.

**Código**

```
{% assign filters = entitylist | metafilters: params.mf, entityview %}
{% if filters.size > 0 %}
  <ul id=entitylist-filters>
    {% for filter in filters %}
      <li class=entitylist-filter-option-group>
        {% if filter.selection_mode == 'Single' %}
          {% assign type = 'radio' %}
        {% else %}
          {% assign type = 'checkbox' %}
        {% endif %}
        <h4 class=entitylist-filter-option-group-label
          data-filter-id={{ filter.id | h }}>
          {{ filter.label | h }}
        </h4>
        <ul>
          {% for option in filter.options %}
            <li class=entitylist-filter-option>
              {% if option.type == 'text' %}
                <div class=input-group entitylist-filter-option-text>
                  <span class=input-group-addon>
                    <span class=fa fa-filter aria-hidden=true></span>
                  </span>
                  <input class=form-control
                    type=text
                    name={{ filter.id | h }}
                    value={{ option.text | h }} />
                </div>
              {% else %}
                <div class={{ type | h }}>
                  <label>
                    <input
                      type={{ type | h }}
                      name={{ filter.id | h }}
                      value={{ option.id | h }}
                      {% if option.checked %}
                        checked=checked
                        data-checked=true{% endif %}
                      />
                    {{ option.label | h }}
                  </label>
                </div>
              {% endif %}
            </li>
          {% endfor %}
        </ul>
      </li>
    {% endfor %}
  </ul>
  <button class=btn btn-default data-serialized-query=mf data-target=#entitylist-filters>Apply Filters</button>
{% endif %}
```

### <a name="reverse_sort"></a>reverse\_sort

Dada una dirección de ordenación, devuelve la dirección de ordenación opuesta.

**Código**

```
<!-- Sort direction is not case-sensitive -->

{{ 'ASC' | reverse_sort }}

{{ 'desc' | reverse_sort }}
```

**Salida**

```
DESC

ASC
```


## <a name="math-filters"></a>Filtros de matemáticas

Los filtros de matemáticas permiten realizar operaciones matemáticas en [números](liquid-types.md#number).  

Como con todos los filtros, los filtros de matemáticas también se pueden encadenar y se aplican en orden de izquierda a derecha.

**Código**

```
{{ 10 | times: 2 | minus: 5 | divided_by: 3 }}
```

**Salida**

```
5
```

### <a name="ceil"></a>ceil

Redondea al alza un valor hasta el entero más cercano.

**Código**

```
{{ 4.6 | ceil }}

{{ 4.3 | ceil }}
```

**Salida**

```
5

5
```

### <a name="divided_by"></a>divided\_by

Divide un número por otro número.

**Código**

```
{{ 10 | divided_by: 2 }}

{{ 10 | divided_by: 3 }}

{{ 10.0 | divided_by: 3 }}
```

**Salida**

```
5

3

3.333333
```

### <a name="floor"></a>floor

Redondea a la baja un valor hasta el entero más cercano.

**Código**

```
{{ 4.6 | floor }}

{{ 4.3 | floor }}
```

**Salida**

```
4

4
```

### <a name="minus"></a>minus

Resta un número de otro número.

**Código**

```
<!-- entityview.page = 11 -->

{{ entityview.page | minus: 1 }}

{{ 10 | minus: 1.1 }}

{{ 10.1 | minus: 1 }}
```

**Salida**

```
10

9

9.1
```

### <a name="modulo"></a>modulo

Divide un número por otro número y devuelve el resto.

**Código**

```
{{ 12 | modulo: 5 }}
```

**Salida**

```
2
```

### <a name="plus"></a>plus

Suma un número a otro número.

**Código**

```
<!-- entityview.page = 11 -->

{{ entityview.page | plus: 1 }}

{{ 10 | plus: 1.1 }}

{{ 10.1 | plus: 1 }}
```

**Salida**

```
12

11

11.1
```

### <a name="round"></a>round

Redondea un valor al entero más próximo o el número especificado de decimales.

**Código**

```
{{ 4.6 | round }}

{{ 4.3 | round }}

{{ 4.5612 | round: 2 }}
```

**Salida**

```
5

4

4.56
```

### <a name="times"></a>times

Multiplica un número por otro número.

**Código**

```
{{ 10 | times: 2 }}

{{ 10 | times: 2.2 }}

{{ 10.1 | times: 2 }}
```

**Salida**

```
20

20

20.2
```


## <a name="string-filters"></a>Filtros de cadena

Los filtros de cadena manipulan [cadenas](liquid-types.md#string).  

### <a name="append"></a>append

Anexa una cadena al final de otra cadena.

**Código**

```
{{ 'filename' | append: '.js' }}
```

**Salida**

```
filename.js
```

### <a name="capitalize"></a>**capitalize**

pone en mayúscula la primera palabra en una cadena.

**Código**

```
{{ 'capitalize me' | capitalize }}
```

**Salida**

```
Capitalize Me
```

### <a name="downcase"></a>**downcase**

Convierte una cadena en minúscula.

**Código**

```
{{ 'MIxed Case TExt' | downcase }}
```

**Salida**

```
mixed case text
```

### <a name="escape"></a>**escape**

Inserta caracteres de escape HTML en una cadena.

**Código**

```
{{ '<p>test</p>' | escape }}
```

**Salida**

```
&lt;p&gt;test&lt;/p&gt;
```

### <a name="newline_to_br"></a>**newline\_to\_br**

Inserta una etiqueta HTML de salto de línea &lt;br /&gt; en cada salto de línea de una cadena.

**Código**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | newline_to_br }}
```

**Salida**

```
A<br />

B<br />

C<br />
```

### <a name="prepend"></a>**prepend**

Antepone una cadena al principio de otra cadena.

**Código**

```
{{ 'Jane Johnson' | prepend: 'Dr. ' }}
```

**Salida**

```
Dr. Jane Johnson
```

### <a name="remove"></a>**remove**

Elimina todas las instancias de una subcadena de una cadena.

**Código**

```
{{ 'Hello, Dave. How are you, Dave?' | remove: 'Dave' }}
```

**Salida**

```
Hello, . How are you, ?
```

### <a name="remove_first"></a>**remove\_first**

Elimina la primera instancia de una subcadena de una cadena.

**Código**

```
{{ 'Hello, Dave. How are you, Dave?' | remove_first: 'Dave' }}
```

**Salida**

```
Hello, . How are you, Dave?
```

### <a name="replace"></a>**replace**

Reemplaza todas las instancias de una cadena con una subcadena.

**Código**

```
{{ 'Hello, Dave. How are you, Dave?' | replace: 'Dave', 'John' }}
```

**Salida**

```
Hello, John. How are you, John?
```

### <a name="replace_first"></a>**replace\_first**

Reemplaza la primera instancia de una cadena con una subcadena.

**Código**

```
{{ 'Hello, Dave. How are you, Dave?' | replace_first: 'Dave', 'John' }}
```

**Salida**

```
Hello, John. How are you, Dave?
```

### <a name="split"></a>**split**

El filtro split adopta una subcadena como parámetro. La subcadena se usa como delimitador para dividir una cadena en una matriz.

**Código**

```
{% assign words = This is a demo of the split filter | split: ' ' %}

First word: {{ words.first }}

First word: {{ words[0] }}

Second word: {{ words[1] }}

Last word: {{ words.last }}

All words: {{ words | join: ', ' }}
```

**Salida**

```
First word: This

First word: This

Second word: is

Last word: filter

All words: This, is, a, demo, of, the, split, filter
```

### <a name="strip_html"></a>**strip\_html**

Quita todas las etiquetas HTML de una cadena.

**Código**

```
<p>Hello</p>
```

**Salida**

```
Hello
```

### <a name="strip_newlines"></a>**strip\_newlines**

Quita las saltos de línea de una cadena.

**Código**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | strip_newlines }}
```

**Salida**

```
ABC
```

### <a name="text_to_html"></a>**text\_to\_html**

Da formato a una cadena de texto sin formato como HTML simple. Todo el texto se codificará como HTML, bloques de texto separados por una línea en blanco se incluirán entre etiquetas de párrafo &lt;p&gt;, los saltos de línea individuales se sustituirán con &lt;br&gt;, y las direcciones URL se convertirán en hipervínculos.

**Código**

```
{{ note.notetext | text_to_html }}
```

**Salida**

```
<p>This is the first paragraph of notetext. It contains a URL: <a href="http://example.com/" rel="nofollow">http://example.com</a></p>

<p>This is a second paragraph.</p>
```

### <a name="truncate"></a>**truncate**

Trunca una cadena hasta un número de caracteres determinado. Un punto suspensivo (...) se anexa a la cadena y se incluye en el número de caracteres.

**Código**

```
{{ 'This is a long run of text.' | truncate: 10 }}
```

**Salida**

```
This is...
```

### <a name="truncate_words"></a>**truncate\_words**

Trunca una cadena hasta un número de palabras determinado. Se anexan puntos suspensivos (...) a la cadena truncada.

**Código**

```
{{ 'This is a long run of text.' | truncate_words: 3 }}
```

**Salida**

```
This is a...
```

### <a name="upcase"></a>**upcase**

Convierte una cadena en mayúscula.

**Código**

```
{{ 'MIxed Case TExt' | upcase }}
```

**Salida**

```
MIXED CASE TEXT
```

### <a name="url_escape"></a>**url\_escape**

Se insertan caracteres de escape URI en una cadena para su inclusión en una dirección URL.

**Código**

```
{{ 'This & that//' | url_escape }}
```

**Salida**

```
This+%26+that%2F%2F
```

### <a name="xml_escape"></a>**xml\_escape**

Se insertan caracteres de escape XML en una cadena para su inclusión en salida XML.

**Código**

```
{{ '<p>test</p>' | xml_escape }}
```

**Salida**

```
&lt;p&gt;test&lt;/p&gt;
```


## <a name="type-filters"></a>Filtros de tipo

Los filtros de tipo permiten la conversión de valores de un tipo a otro.

### <a name="boolean"></a>**boolean**

Intenta convertir un valor de cadena en booleano. Si el valor ya es booleano, se devolverá sin cambios. Si el valor no se puede convertir en booleano, se devolverá null.

Este filtro también acepta on, habilitado, o sí como true, y off, deshabilitado y no como false.

**Código**

```
{{ true | boolean }}

{{ 'false' | boolean }}

{{ 'enabled' | boolean }}

{{ settings['something/enabled'] | boolean | default: false }}
```

**Salida**

```
true

false

true

false
```

### <a name="decimal"></a>**decimal**

Intenta convertir un valor de cadena en número decimal. Si el valor ya es un número decimal, se devolverá sin cambios. Si el valor no se puede convertir en un número decimal, se devolverá null.

**Código**

```
{{ 10.1 | decimal }}

{{ '3.14' | decimal }}

{{ 'text' | decimal | default: 3.14 }}
```

**Salida**

```
10.1

3.14

3.14
```

### <a name="integer"></a>**integer**

Intenta convertir un valor de cadena en un entero. Si el valor ya es un entero, se devolverá sin cambios. Si el valor no se puede convertir en un entero, se devolverá null.

**Código**

```
{{ 10 | integer }}

{{ '10' | integer }}

{{ '10.1' | integer }}

{{ 'text' | integer | default: 2 }}
```

**Salida**

```
10

10


2
```

### <a name="string"></a>**string**

Intenta convertir un valor en su representación de cadena. Si el valor ya es una cadena, se devolverá sin cambios. Si el valor es null, se devolverá null.



## <a name="url-filters"></a>Filtros de dirección URL

Los filtros de dirección URL permiten crear o extraer partes de direcciones URL.

### <a name="add_query"></a>**add\_query**

Anexar un parámetro de cadena de consulta a una dirección URL. Si el parámetro ya existe en la dirección URL, el valor del parámetro se actualizará.

Si este filtro se aplica a una dirección URL absoluta completa, una dirección URL absoluta actualizada será el resultado. Si se aplica a una ruta, una ruta actualizada será el resultado.

**Código**

```
{{ 'http://example.com/path?page=1' | add_query: 'foo', 'bar' }}

{{ '/path?page=1' | add_query: 'page', 2 }}
```

**Salida**

```
http://example.com/path?page=1&foo=bar

/path?page=2
```

### <a name="base"></a>**base**

Obtiene la dirección URL de una dirección URL determinada.

**Código**

```
{{ 'http://example.com/path?foo=bar&page=2' | base }}
```

**Salida**

```
http://example.com
```

### <a name="host"></a>**host**

Obtiene la parte de host de una dirección URL.

**Código**

```
{{ 'http://example.com/path?foo=bar&page=2' | host }}
```

**Salida**

```
example.com
```

### <a name="path"></a>**path**

Obtiene la parte de ruta de una dirección URL.

**Código**

```
{{ 'http://example.com/path?foo=bar&page=2' | path }}

{{ '/path?foo=bar&page=2' | path }}
```

**Salida**

```
/path

/path
```

### <a name="path_and_query"></a>**path\_and\_query**

Obtiene la parte de ruta y consulta de una dirección URL.

**Código**

```
{{ 'http://example.com/path?foo=bar&page=2' | path_and_query }}

{{ '/path?foo=bar&page=2' | path_and_query }}
```

**Salida**

```
/path?foo=bar&page=2

/path?foo=bar&page=2
```

### <a name="port"></a>**port**

Obtiene el número de puerto una dirección URL.

**Código**

```
{{ 'http://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com:9000/path?foo=bar&page=2' | port }}
```

**Salida**

```
80

443

9000
```

### <a name="remove_query"></a>**remove\_query**

Quita un parámetro de cadena de consulta de una dirección URL. Si el parámetro no existe en la dirección URL, la dirección URL se devuelve sin cambios.

Si este filtro se aplica a una dirección URL absoluta completa, una dirección URL absoluta actualizada será el resultado. Si se aplica a una ruta, una ruta actualizada será el resultado.

**Código**

```
{{ 'http://example.com/path?page=1' | remove_query: 'page' }}

{{ '/path?page=1' | remove_query: 'page' }}
```

**Salida**

```
http://example.com/path

/path
```

### <a name="scheme"></a>**scheme**

Obtiene la parte de esquema de una dirección URL.

**Código**

```
{{ 'http://example.com/path?foo=bar&page=2' | scheme }}

{{ 'https://example.com/path?foo=bar&page=2' | scheme }}
```

**Salida**

```
http

https
```


## <a name="additional-filters"></a>Filtros adicionales

Estos filtros proporcionan funcionalidad general útil.

### <a name="default"></a>**default**

Devuelve un valor predeterminado para cualquier variable sin valor asignado (es decir, null).

**Código**

```
{{ snippets[Header] | default: 'My Website' }}
```

**Salida**

```
<!-- If a snippet with the name Header returns null -->

My Website
```

### <a name="file_size"></a>**file\_size**

Aplicado un valor de número que representa varios bytes, devuelve un tamaño de archivo con formato con una unidad de escala adecuada.

Opcionalmente, puede pasarse un parámetro de precisión para controlar el número de decimales en el resultado. La precisión predeterminada es 1.

**Código**

```
{{ 10000000 | file_size }}

{{ 2050 | file_size: 0 }}

{{ entity.notes.first.filesize | file_size: 2 }}
```

**Salida**

```
9.5 MB

2 KB

207.14 KB
```

### <a name="has_role"></a>**has\_role**

Si se aplica a un [usuario](liquid-objects.md#user), devuelve true si el usuario pertenece al rol determinado. Devuelve false si no.  

**Código**

```
{% assign is_admin = user | has_role: 'Administrators' %}

{% if is_admin %}

User is an administrator.

{% endif %}
```

### <a name="liquid"></a>**liquid**

Representa una cadena como código de Liquid. Este código tendrá acceso al contexto de ejecución de Liquid actual (variables, etc.).

> [!Note] 
> Este filtro se debe usar con precaución y debe aplicarse normalmente sólo a los valores que están bajo el control exclusivo de los autores del contenido del portal, u otros usuarios en los que se puede confiar para escribir código de Liquid.

**Código**

```
{{ page.adx_copy | liquid }}
```

### <a name="see-also"></a>Vea también

[Almacenar contenido de origen con plantillas web](store-content-web-templates.md)  
[Comprender operadores de Liquid](liquid-operators.md) 
[Tipos de Liquid](liquid-types.md)  
[Objetos de Liquid](liquid-objects.md)  
[Etiquetas de Liquid](liquid-tags.md)  
[Filtros de Liquid](liquid-filters.md)  
