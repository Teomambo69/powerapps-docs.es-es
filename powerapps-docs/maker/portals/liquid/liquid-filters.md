---
title: Usar filtros Liquid para un portal | MicrosoftDocs
description: Obtenga información sobre los filtros Liquid disponibles en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 68a595ee72704cf81241ecfee19f90728fb95aeb
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975159"
---
# <a name="available-liquid-filters"></a>Filtros de Liquid disponibles

Los filtros Liquid se utilizan para modificar la salida de cadenas, números, variables y objetos. Se separan del valor al que se aplica un |.

`{{ 'hal 9000' | upcase }} <!-- Output: HAL 9000 -->`

Algunos filtros aceptan parámetros. Los filtros también se pueden combinar y se aplican en orden de izquierda a derecha.

```
{{ 2 | times: 2 | minus: 1 }} <!-- Output: 3 -->

{{ "Hello, " | append: user.firstname }} <!-- Output: Hello, Dave -->
```
En la sección siguiente se describen varios filtros. 

## <a name="array-filters"></a>Filtros de matriz

Los filtros de matriz se utilizan para trabajar con [matrices](liquid-types.md#array).  

### <a name="batch"></a>procesamiento

Divide una matriz en varias matrices de un tamaño determinado.

**Codifica**

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

**Genere**

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

Concatena dos matrices en una sola nueva.

Dado un solo elemento como parámetro, concat devuelve una nueva matriz que consta de la matriz original, con el elemento dado como el último elemento.

**Codifica**

```
Group #1: {{ group1 | join: ', ' }}

Group #2: {{ group2 | join: ', ' }}

Group #1 + Group #2: {{ group1 | concat: group2 | join: ', ' }}

Group #1 + Leslie: {{ group1 | concat: 'Leslie' | join: ', ' }}
```

**Genere**

```
Group #1: John, Pete, Hannah

Group #2: Joan, Bill

Group #1 + Group #2: John, Pete, Hannah, Joan, Bill

Group #1 + Leslie: John, Pete, Hannah, Leslie
```

### <a name="except"></a>CEPT

Seleccione todos los objetos de una matriz en los que un atributo determinado no tenga un valor determinado. (Este es el inverso de**donde**).

**Codifica**

```
{% assign redmond = entityview.records | except: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**Genere**

```
Jack Robinson
```

### <a name="first"></a>Lugar

Devuelve el primer elemento de una matriz.

en primer lugar, también se puede usar con una notación de puntos especial, en los casos en los que es necesario utilizar dentro de una etiqueta.

**Codifica**

```
{% assign words = This is a run of text | split:   %}

{{ words | first }}

{% if words.first == This %}

The first word is This.

{% endif %}
```

**Genere**

```
This

The first word is This.
```

### <a name="group_by"></a>group_by

Agrupar los elementos de una matriz por un atributo determinado.

**Codifica**

```
{% assign groups = entityview.records | group_by: 'address1_city' %}

{% for group in groups %}

{{ group.key }}:

{% for item in group.items %}

{{ item.fullname }}

{% endfor %}

{% endfor %}
```

**Genere**

```
Redmond:

John Smith

Dave Thomas

Jake Johnson

New York:

Jack Robinson
```

### <a name="join"></a>Vuelve

Combina los elementos de una matriz con el carácter que se pasa como parámetro. El resultado es una sola cadena.

**Codifica**

```
{% assign words = This is a run of text | split:   %}

{{ words | join: ,  }}
```

**Genere**

```
This, is, a, run, of, text
```

### <a name="last"></a>guardado

Devuelve el último elemento de una matriz.

Last también se puede usar con una notación de puntos especial, en los casos en los que es necesario utilizar dentro de una etiqueta.

**Codifica**

```
{% assign words = This is a run of text | split:   -%}

{{ words | last }}

{% if words.last == text -%}

The last word is text.

{% endif -%}
```

**Genere**

```
text

The last word is text.
```

### <a name="order_by"></a>ordenar\_por

Devuelve los elementos de una matriz ordenada por un atributo determinado de los elementos de la matriz.

Opcionalmente, puede proporcionar DESC como segundo parámetro para ordenar los elementos en orden descendente, en lugar de ascendente.

**Codifica**

```
{{ entityview.records | order_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'fullname', 'desc' | join: ', ' }}
```

**Genere**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="random"></a>aleatorio

Devuelve un único elemento seleccionado aleatoriamente de la matriz.

**Codifica**

```
{{ group1 | join: ', ' }}

{{ group1 | random }}
```

**Genere**

```
John, Pete, Hannah

Pete
```

### <a name="select"></a>No

Selecciona el valor de un atributo determinado para cada elemento de una matriz y devuelve estos valores como una matriz.

**Codifica**

```
{{ entityview.records | select: 'address1_city' | join: ', ' }}
```

**Genere**

```
Redmond, New York
```

### <a name="shuffle"></a>aleatoria

Aplicado a una matriz, devuelve una nueva matriz con los mismos elementos, en orden aleatorio.

**Codifica**

```
{{ group1 | join: ', ' }}

{{ group1 | shuffle | join: ', ' }}
```

**Genere**

```
John, Pete, Hannah

Hannah, John, Pete
```

### <a name="size"></a>Ajusta

Devuelve el número de elementos de una matriz.

el tamaño también se puede usar con una notación de puntos especial, en los casos en los que es necesario utilizar dentro de una etiqueta.

**Codifica**

```
{% assign words = This is a run of text | split:   -%}

{{ words | size }}

{% if words.size == 6 -%}

The text contains 6 words.

{% endif -%}
```

**Genere**

```
6

The text contains 6 words.
```

### <a name="skip"></a>skip

Omite un número determinado de elementos de una matriz y devuelve el resto.

**Codifica**

```
{% assign words = This is a run of text | split:   %}

{{ words | skip: 3 | join: ', ' }}
```

**Genere**

```
run, of, text
```

### <a name="take"></a>echar

Toma un número determinado de elementos de la matriz y devuelve los elementos tomados.

**Codifica**

```
{% assign words = This is a run of text | split:   %}

{{ words | take: 3 | join: ', ' }}
```
**Genere**

```

This, is, a
```

### <a name="then_by"></a>después\_por

Agrega una ordenación posterior adicional a una matriz ya ordenada por**orden\_por**.

Opcionalmente, puede proporcionar DESC como segundo parámetro para ordenar los elementos en orden descendente, en lugar de ascendente.

**Codifica**

```
{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname', 'desc' | join: ', ' }}
```

**Genere**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="where"></a>Mientras

Seleccione todos los objetos de una matriz donde un atributo determinado tiene un valor determinado.

**Codifica**

```
{% assign redmond = entityview.records | where: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**Genere**

```
John Smith

Dave Thomas

Jake Johnson
```


## <a name="date-filters"></a>Filtros de fecha

Los filtros de fecha se pueden usar para operaciones aritméticas de fecha o para convertir valores de fecha y hora en varios formatos.

### <a name="date"></a>Posteriormente

Da formato a un valor DateTime mediante una cadena de formato .NET.

[Cadenas con formato de fecha y hora estándar](https://docs.microsoft.com/en-us/dotnet/standard/base-types/standard-date-and-time-format-strings)  

[Cadenas con formato de fecha y hora personalizado](https://docs.microsoft.com/en-us/dotnet/standard/base-types/custom-date-and-time-format-strings)  

**Codifica**

```
{{ now | date: 'g' }}

{{ now | date: 'MMMM dd, yyyy' }}
```

**Genere**

```
5/7/2018 7:20 AM

May 07, 2018
```

### <a name="date_add_days"></a>fecha\_agregar\_días

Agrega el número especificado de días enteros y fraccionarios al valor de fecha y hora. El parámetro puede ser positivo o negativo.

**Codifica**

```
{{ now }}

{{ now | date_add_days: 1 }}

{{ now | date_add_days: -2.5 }}
```

**Genere**

```
5/7/2018 7:20:46 AM

5/8/2018 7:20:46 AM

5/4/2018 7:20:46 PM
```

### <a name="date_add_hours"></a>fecha\_agregar\_horas

Agrega el número especificado de horas enteras y fraccionarias al valor de fecha y hora. El parámetro puede ser positivo o negativo.

**Codifica**

```
{{ now }}

{{ now | date_add_hours: 1 }}

{{ now | date_add_hours: -2.5 }}
```

**Genere**

```
5/7/2018 7:20:46 AM

5/7/2018 8:20:46 AM

5/7/2018 4:50:46 AM
```

### <a name="date_add_minutes"></a>fecha\_agregar\_minutos

Agrega el número especificado de minutos enteros y fraccionarios al valor de fecha y hora. El parámetro puede ser positivo o negativo.

**Codifica**

```
{{ now }}

{{ now | date_add_minutes: 10 }}

{{ now | date_add_minutes: -2.5 }}
```


**Genere**

```
5/7/2018 7:20:46 AM

5/7/2018 7:30:46 AM

5/7/2018 7:18:16 AM
```

### <a name="date_add_months"></a>fecha\_agregar\_meses

Agrega el número especificado de meses completos al valor de fecha y hora. El parámetro puede ser positivo o negativo.

**Codifica**

```
{{ now }}

{{ now | date_add_months: 1 }}

{{ now | date_add_months: -2 }}
```

**Genere**

```
5/7/2018 7:20:46 AM

6/7/2018 7:20:46 AM

3/7/2018 7:20:46 AM
```

### <a name="date_add_seconds"></a>fecha\_agregar\_segundos

Agrega el número especificado de segundos enteros y fraccionarios al valor de fecha y hora. El parámetro puede ser positivo o negativo.

**Codifica**

```
{{ now }}

{{ now | date_add_seconds: 10 }}

{{ now | date_add_seconds: -1.25 }}
```

**Genere**

```
5/7/2018 7:20:46 AM

5/7/2018 7:20:56 AM

5/7/2018 7:20:45 AM
```

### <a name="date_add_years"></a>fecha\_agregar\_años

Suma el número especificado de años completos al valor de fecha y hora. El parámetro puede ser positivo o negativo.

**Codifica**

```
{{ now }}

{{ now | date_add_years: 1 }}

{{ now | date_add_years: -2 }}
```

**Genere**

```
5/7/2018 7:20:46 AM

5/7/2019 7:20:46 AM

5/7/2016 7:20:46 AM
```

### <a name="date_to_iso8601"></a>\_de fecha para\_iso8601

Da formato a un valor de fecha y hora según el estándar [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) . Resulta útil cuando se crean [*fuentes Atom*](http://tools.ietf.org/html/rfc4287)o el elemento&gt; de tiempo &lt;HTML5.  

**Codifica**

```
{{ now | date_to_iso8601 }}
```

**Genere**

```
2018-05-07T07:20:46Z
```

### <a name="date_to_rfc822"></a>\_de fecha para\_rfc822

Da formato a un valor de fecha y hora según el estándar [RFC 822](https://www.ietf.org/rfc/rfc0822.txt) . Resulta útil al crear [*fuentes RSS*](http://cyber.law.harvard.edu/rss/rss.html).  

**Codifica**

```
{{ now | date_to_rfc822 }}
```

**Genere**

```
Mon, 07 May 2018 07:20:46 Z
```


## <a name="entity-list-filters"></a>Filtros de la lista de entidades

Los filtros de la lista de entidades se usan para trabajar con determinados valores de atributos de [entitylist](liquid-objects.md#entitylist) y para ayudar a crear vistas de la lista de entidades.  

### <a name="current_sort"></a>orden de\_actual

Dada una expresión de ordenación, devuelve la dirección de ordenación actual para un atributo determinado.

**Codifica**

```
{{ 'name ASC, createdon DESC' | current_sort: 'createdon' }}
```

**Genere**

```
DESC
```

### <a name="metafilters"></a>metafiltros

Analiza un filtro [entitylist](liquid-objects.md#entitylist)\_valor JSON de definición en objetos de grupo de opciones de filtro.  

los metafiltros se pueden proporcionar opcionalmente con una consulta de filtro de atributo actual y un [entitylist](liquid-objects.md#entitylist)actual, lo que permite marcar los objetos de filtro devueltos como seleccionados o sin seleccionar.

**Codifica**

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

### <a name="reverse_sort"></a>orden de\_inverso

Dada una dirección de ordenación, devuelve la dirección de ordenación opuesta.

**Codifica**

```
<!-- Sort direction is not case-sensitive -->

{{ 'ASC' | reverse_sort }}

{{ 'desc' | reverse_sort }}
```

**Genere**

```
DESC

ASC
```


## <a name="math-filters"></a>Filtros matemáticos

Los filtros matemáticos le permiten realizar operaciones matemáticas en [números](liquid-types.md#number).  

Al igual que con todos los filtros, los filtros matemáticos se pueden encadenar y se aplican en orden de izquierda a derecha.

**Codifica**

```
{{ 10 | times: 2 | minus: 5 | divided_by: 3 }}
```

**Genere**

```
5
```

### <a name="ceil"></a>Ceil (

Redondea un valor al entero más próximo.

**Codifica**

```
{{ 4.6 | ceil }}

{{ 4.3 | ceil }}
```

**Genere**

```
5

5
```

### <a name="divided_by"></a>\_dividido por

Divide un número por otro número.

**Codifica**

```
{{ 10 | divided_by: 2 }}

{{ 10 | divided_by: 3 }}

{{ 10.0 | divided_by: 3 }}
```

**Genere**

```
5

3

3.333333
```

### <a name="floor"></a>palabra

Redondea un valor al entero más próximo.

**Codifica**

```
{{ 4.6 | floor }}

{{ 4.3 | floor }}
```

**Genere**

```
4

4
```

### <a name="minus"></a>DISMINUI

Resta un número de otro número.

**Codifica**

```
<!-- entityview.page = 11 -->

{{ entityview.page | minus: 1 }}

{{ 10 | minus: 1.1 }}

{{ 10.1 | minus: 1 }}
```

**Genere**

```
10

9

9.1
```

### <a name="modulo"></a>velocidad

Divide un número por otro número y devuelve el resto.

**Codifica**

```
{{ 12 | modulo: 5 }}
```

**Genere**

```
2
```

### <a name="plus"></a>signo más

Agrega un número a otro número.

**Codifica**

```
<!-- entityview.page = 11 -->

{{ entityview.page | plus: 1 }}

{{ 10 | plus: 1.1 }}

{{ 10.1 | plus: 1 }}
```

**Genere**

```
12

11

11.1
```

### <a name="round"></a>retorno

Redondea un valor al entero más próximo o al número especificado de decimales.

**Codifica**

```
{{ 4.6 | round }}

{{ 4.3 | round }}

{{ 4.5612 | round: 2 }}
```

**Genere**

```
5

4

4.56
```

### <a name="times"></a>Times

Multiplica un número por otro número.

**Codifica**

```
{{ 10 | times: 2 }}

{{ 10 | times: 2.2 }}

{{ 10.1 | times: 2 }}
```

**Genere**

```
20

20

20.2
```


## <a name="string-filters"></a>Filtros de cadena

Los filtros de cadena manipulan [cadenas](liquid-types.md#string).  

### <a name="append"></a>anexar

Anexa una cadena al final de otra cadena.

**Codifica**

```
{{ 'filename' | append: '.js' }}
```

**Genere**

```
filename.js
```

### <a name="capitalize"></a>**capitaliza**

pone en mayúscula la primera palabra de una cadena.

**Codifica**

```
{{ 'capitalize me' | capitalize }}
```

**Genere**

```
Capitalize Me
```

### <a name="downcase"></a>**downcase**

Convierte una cadena en minúsculas.

**Codifica**

```
{{ 'MIxed Case TExt' | downcase }}
```

**Genere**

```
mixed case text
```

### <a name="escape"></a>**salida**

HTML: escapa una cadena.

**Codifica**

```
{{ '<p>test</p>' | escape }}
```

**Genere**

```
&lt;p&gt;test&lt;/p&gt;
```

### <a name="newline_to_br"></a>**nueva línea\_a\_br**

Inserta una etiqueta HTML &lt;br/&gt; salto de línea en cada salto de línea de una cadena.

**Codifica**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | newline_to_br }}
```

**Genere**

```
A<br />

B<br />

C<br />
```

### <a name="prepend"></a>**pospone**

Antepone una cadena al principio de otra cadena.

**Codifica**

```
{{ 'Jane Johnson' | prepend: 'Dr. ' }}
```

**Genere**

```
Dr. Jane Johnson
```

### <a name="remove"></a>**retirar**

Quita todas las apariciones de una subcadena de una cadena.

**Codifica**

```
{{ 'Hello, Dave. How are you, Dave?' | remove: 'Dave' }}
```

**Genere**

```
Hello, . How are you, ?
```

### <a name="remove_first"></a>**quitar\_primero**

Quita la primera aparición de una subcadena de una cadena.

**Codifica**

```
{{ 'Hello, Dave. How are you, Dave?' | remove_first: 'Dave' }}
```

**Genere**

```
Hello, . How are you, Dave?
```

### <a name="replace"></a>**Reemplace**

Reemplaza todas las apariciones de una cadena por una subcadena.

**Codifica**

```
{{ 'Hello, Dave. How are you, Dave?' | replace: 'Dave', 'John' }}
```

**Genere**

```
Hello, John. How are you, John?
```

### <a name="replace_first"></a>**reemplazar\_primero**

Reemplaza la primera aparición de una cadena por una subcadena.

**Codifica**

```
{{ 'Hello, Dave. How are you, Dave?' | replace_first: 'Dave', 'John' }}
```

**Genere**

```
Hello, John. How are you, Dave?
```

### <a name="split"></a>**Divida**

El filtro dividido toma una subcadena como parámetro. La subcadena se utiliza como delimitador para dividir una cadena en una matriz.

**Codifica**

```
{% assign words = This is a demo of the split filter | split: ' ' %}

First word: {{ words.first }}

First word: {{ words[0] }}

Second word: {{ words[1] }}

Last word: {{ words.last }}

All words: {{ words | join: ', ' }}
```

**Genere**

```
First word: This

First word: This

Second word: is

Last word: filter

All words: This, is, a, demo, of, the, split, filter
```

### <a name="strip_html"></a>**quitar HTML\_**

Quita todas las etiquetas HTML de una cadena.

**Codifica**

```
<p>Hello</p>
```

**Genere**

```
Hello
```

### <a name="strip_newlines"></a>**franjas\_nuevas**

Quita los saltos de línea de una cadena.

**Codifica**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | strip_newlines }}
```

**Genere**

```
ABC
```

### <a name="text_to_html"></a>**\_de texto a\_HTML**

Da formato a una cadena de texto sin formato como HTML simple. Todo el texto estará codificado en HTML, los bloques de texto separados por una línea en blanco se ajustarán en el párrafo &lt;p&gt; etiquetas, los saltos de línea únicos se reemplazarán por &lt;br&gt;y las direcciones URL se convertirán en hipervínculos.

**Codifica**

```
{{ note.notetext | text_to_html }}
```

**Genere**

```
<p>This is the first paragraph of notetext. It contains a URL: <a href="http://example.com/" rel="nofollow">http://example.com</a></p>

<p>This is a second paragraph.</p>
```

### <a name="truncate"></a>**truncar**

Trunca una cadena hasta un número determinado de caracteres. Se anexan puntos suspensivos (...) a la cadena y se incluyen en el recuento de caracteres.

**Codifica**

```
{{ 'This is a long run of text.' | truncate: 10 }}
```

**Genere**

```
This is...
```

### <a name="truncate_words"></a>**truncar palabras\_**

Trunca una cadena hasta un número determinado de palabras. Se anexan puntos suspensivos (...) a la cadena truncada.

**Codifica**

```
{{ 'This is a long run of text.' | truncate_words: 3 }}
```

**Genere**

```
This is a...
```

### <a name="upcase"></a>**escenario de uso**

Convierte una cadena en mayúsculas.

**Codifica**

```
{{ 'MIxed Case TExt' | upcase }}
```

**Genere**

```
MIXED CASE TEXT
```

### <a name="url_escape"></a>**URL\_escape**

URI: escapa de una cadena para su inclusión en una dirección URL.

**Codifica**

```
{{ 'This & that//' | url_escape }}
```

**Genere**

```
This+%26+that%2F%2F
```

### <a name="xml_escape"></a>**escape de\_XML**

XML: escapa de una cadena para su inclusión en la salida XML.

**Codifica**

```
{{ '<p>test</p>' | xml_escape }}
```

**Genere**

```
&lt;p&gt;test&lt;/p&gt;
```


## <a name="type-filters"></a>Filtros de tipo

Los filtros de tipo permiten convertir valores de un tipo en otros tipos.

### <a name="boolean"></a>**booleano**

Intenta convertir un valor de cadena en un valor booleano. Si el valor ya es un valor booleano, se devolverá sin cambios. Si el valor no se puede convertir en un valor booleano, se devolverá null.

Este filtro también aceptará on, Enabled o Yes como true y OFF, Disabled y no como false.

**Codifica**

```
{{ true | boolean }}

{{ 'false' | boolean }}

{{ 'enabled' | boolean }}

{{ settings['something/enabled'] | boolean | default: false }}
```

**Genere**

```
true

false

true

false
```

### <a name="decimal"></a>**decimal**

Intenta convertir un valor de cadena en un número decimal. Si el valor ya es un número decimal, se devolverá sin cambios. Si el valor no se puede convertir en un número decimal, se devolverá null.

**Codifica**

```
{{ 10.1 | decimal }}

{{ '3.14' | decimal }}

{{ 'text' | decimal | default: 3.14 }}
```

**Genere**

```
10.1

3.14

3.14
```

### <a name="integer"></a>**entero**

Intenta convertir un valor de cadena en un entero. Si el valor ya es un entero, se devolverá sin cambios. Si el valor no se puede convertir en un entero, se devolverá null.

**Codifica**

```
{{ 10 | integer }}

{{ '10' | integer }}

{{ '10.1' | integer }}

{{ 'text' | integer | default: 2 }}
```

**Genere**

```
10

10


2
```

### <a name="string"></a>**String@**

Intenta convertir un valor en su representación de cadena. Si el valor ya es una cadena, se devolverá sin cambios. Si el valor es null, se devolverá null.



## <a name="url-filters"></a>Filtros de URL

Los filtros de dirección URL permiten crear o extraer partes de las direcciones URL.

### <a name="add_query"></a>**Agregar\_consulta**

Anexa un parámetro de cadena de consulta a una dirección URL. Si el parámetro ya existe en la dirección URL, se actualizará el valor del parámetro.

Si este filtro se aplica a una dirección URL absoluta completa, el resultado será una dirección URL absoluta actualizada. Si se aplica a una ruta de acceso, el resultado será una ruta de acceso actualizada.

**Codifica**

```
{{ 'http://example.com/path?page=1' | add_query: 'foo', 'bar' }}

{{ '/path?page=1' | add_query: 'page', 2 }}
```

**Genere**

```
http://example.com/path?page=1&foo=bar

/path?page=2
```

### <a name="base"></a>**básica**

Obtiene la dirección URL base de una dirección URL determinada.

**Codifica**

```
{{ 'http://example.com/path?foo=bar&page=2' | base }}
```

**Genere**

```
http://example.com
```

### <a name="host"></a>**organizar**

Obtiene la parte del host de una dirección URL.

**Codifica**

```
{{ 'http://example.com/path?foo=bar&page=2' | host }}
```

**Genere**

```
example.com
```

### <a name="path"></a>**camino**

Obtiene la parte de la ruta de acceso de una dirección URL.

**Codifica**

```
{{ 'http://example.com/path?foo=bar&page=2' | path }}

{{ '/path?foo=bar&page=2' | path }}
```

**Genere**

```
/path

/path
```

### <a name="path_and_query"></a>**\_de ruta de acceso y\_consulta**

Obtiene la ruta de acceso y la parte de la consulta de una dirección URL.

**Codifica**

```
{{ 'http://example.com/path?foo=bar&page=2' | path_and_query }}

{{ '/path?foo=bar&page=2' | path_and_query }}
```

**Genere**

```
/path?foo=bar&page=2

/path?foo=bar&page=2
```

### <a name="port"></a>**casilla**

Obtiene el número de puerto de una dirección URL.

**Codifica**

```
{{ 'http://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com:9000/path?foo=bar&page=2' | port }}
```

**Genere**

```
80

443

9000
```

### <a name="remove_query"></a>**quitar\_consulta**

Quita un parámetro de cadena de consulta de una dirección URL. Si el parámetro no existe en la dirección URL, la dirección URL se devolverá sin cambios.

Si este filtro se aplica a una dirección URL absoluta completa, el resultado será una dirección URL absoluta actualizada. Si se aplica a una ruta de acceso, el resultado será una ruta de acceso actualizada.

**Codifica**

```
{{ 'http://example.com/path?page=1' | remove_query: 'page' }}

{{ '/path?page=1' | remove_query: 'page' }}
```

**Genere**

```
http://example.com/path

/path
```

### <a name="scheme"></a>**regímenes**

Obtiene la parte del esquema de una dirección URL.

**Codifica**

```
{{ 'http://example.com/path?foo=bar&page=2' | scheme }}

{{ 'https://example.com/path?foo=bar&page=2' | scheme }}
```

**Genere**

```
http

https
```


## <a name="additional-filters"></a>Filtros adicionales

Estos filtros proporcionan una funcionalidad general útil.

### <a name="default"></a>**predeterminada**

Devuelve un valor predeterminado para cualquier variable sin ningún valor asignado (es decir, null).

**Codifica**

```
{{ snippets[Header] | default: 'My Website' }}
```

**Genere**

```
<!-- If a snippet with the name Header returns null -->

My Website
```

### <a name="file_size"></a>**tamaño de\_de archivo**

Aplicado a un valor numérico que representa un número de bytes, devuelve un tamaño de archivo con formato con una unidad de escala adecuada.

Opcionalmente, se puede pasar un parámetro de precisión para controlar el número de posiciones decimales en el resultado. La precisión predeterminada es 1.

**Codifica**

```
{{ 10000000 | file_size }}

{{ 2050 | file_size: 0 }}

{{ entity.notes.first.filesize | file_size: 2 }}
```

**Genere**

```
9.5 MB

2 KB

207.14 KB
```

### <a name="has_role"></a>**tiene rol de\_**

Aplicado a un [usuario](liquid-objects.md#user), devuelve true si el usuario pertenece al rol especificado. Devuelve false si no lo está.  

**Codifica**

```
{% assign is_admin = user | has_role: 'Administrators' %}

{% if is_admin %}

User is an administrator.

{% endif %}
```

### <a name="liquid"></a>**circula**

Representa una cadena como código de líquido. Este código tendrá acceso al contexto de ejecución de Liquid actual (variables, etc.).

> [!Note] 
> Este filtro debe usarse con precaución y, por lo general, solo debe aplicarse a los valores que están bajo el control exclusivo de los autores de contenido del portal, u otros usuarios que pueden ser de confianza para escribir código líquido.

**Codifica**

```
{{ page.adx_copy | liquid }}
```

### <a name="see-also"></a>Vea también

[Almacenar contenido de origen mediante plantillas web](store-content-web-templates.md)  
[Descripción de los operadores liquid](liquid-operators.md) 
[tipos de líquido](liquid-types.md)  
[Objetos Liquid](liquid-objects.md)  
[Etiquetas líquidas](liquid-tags.md)  
[Filtros líquidos](liquid-filters.md)  
