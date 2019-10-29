---
title: Usar tipos de líquido para un portal | MicrosoftDocs
description: Obtenga información sobre los tipos de líquido disponibles en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: dd6da4788f6563c2026f57914c8156caedfadad3
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974952"
---
# <a name="available-liquid-types"></a>Tipos de Liquid disponibles

Los objetos Liquid pueden devolver uno de los siete tipos básicos: **cadena**, **número**, **booleano**, **matriz**, **Diccionario**, **DateTime**o **null**. Las variables líquidas se pueden inicializar mediante el uso de las etiquetas de **asignación** o de **captura** .

## <a name="string"></a>Cadena

Una cadena se declara ajustando el texto entre comillas simples o dobles.

```
{% assign string_a = Hello World! %}

{% assign string_b = 'Single quotes work too.' %}
```

Obtiene el número de caracteres de una cadena con la propiedad Size.

```
{{ string_a.size }} <!-- Output: 12 -->
```

## <a name="number"></a>Número

Los números pueden ser enteros o flotantes.

```
{% assign pi = 3.14 %}

{% if page.title.size > 100 %}

This page has a long title.

{% endif %}
```

## <a name="boolean"></a>Booleano

Un valor booleano es true o false.

```
{% assign x = true %}

{% assign y = false %}

{% if x %}

This will be rendered, because x is true.

{% endif %}
```

## <a name="array"></a>matriz

Una matriz contiene una lista de valores de cualquier tipo. Puede obtener acceso a un elemento determinado por índice (basado en cero) mediante \[ \], recorrer en iteración mediante la **etiqueta for**y obtener el número de elementos de la matriz mediante la propiedad Size.

```
{% for view in entitylist.views %}

{{ view.name }}

{% endfor %}

{{ entitylist.views[0] }}

{% if entitylist.views.size > 0 %}

This entity list has {{ entitylist.views.size }} views.

{% endif %}
```

## <a name="dictionary"></a>Diccionarios

Los diccionarios contienen una colección de valores a los que se puede tener acceso mediante una clave de cadena. Puede tener acceso a un elemento determinado por clave de cadena mediante \[ \], recorrer en iteración mediante la **etiqueta for**y obtener el número de elementos del diccionario mediante la propiedad Size.

```
{{ request.params[ID] }}

{% if request.params.size > 0 %}

The request parameters collection contains some items.

{% endif %}
```

## <a name="datetime"></a>DateTime

Un objeto DateTime representa una fecha y hora específicas.

```
{{ page.modifiedon | date: 'f' }}
```

## <a name="null"></a>Acepta

Null representa un valor vacío o que no existe. Las salidas que intenten devolver un valor NULL no representarán nada. Se tratará como falso en condiciones.

```
{% if request.params[ID] %}

This will render if the ID request parameter is NOT null.

{% endif %}
```

### <a name="see-also"></a>Vea también

[Almacenar contenido de origen mediante plantillas web](store-content-web-templates.md)  
[Descripción de los operadores Liquid](liquid-operators.md)  
[Instrucción](liquid-conditional-operators.md)  
[Objetos Liquid](liquid-objects.md)  
[Etiquetas líquidas](liquid-tags.md)  
[Filtros líquidos](liquid-filters.md)  