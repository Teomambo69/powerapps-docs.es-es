---
title: Usar tipos de Liquid para un portal | MicrosoftDocs
description: Obtenga información acerca de los tipos de Liquid disponibles en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: dd6da4788f6563c2026f57914c8156caedfadad3
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2708107"
---
# <a name="available-liquid-types"></a>Tipos de Liquid disponibles

Los objetos de Liquid pueden devolver uno de estos siete tipos básicos: **Cadena**, **Número**, **Booleano**, **Matriz**, **Diccionario**, **Fecha y hora** y **Nulo**. Las variables de Liquid pueden inicializarse mediante las etiquetas **assign** o **capture**.

## <a name="string"></a>Cadena

Una cadena se declarada incluyendo texto entre comillas sencillas o dobles.

```
{% assign string_a = Hello World! %}

{% assign string_b = 'Single quotes work too.' %}
```

Obtenga el número de caracteres de una cadena con la propiedad size.

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

## <a name="boolean"></a>Boolean

Un booleano es true o false.

```
{% assign x = true %}

{% assign y = false %}

{% if x %}

This will be rendered, because x is true.

{% endif %}
```

## <a name="array"></a>Matriz

Una matriz alberga una lista de valores de cualquier tipo. Puede obtener acceso a un elemento dado por índice (basado en cero) utilizando \[ \], iterarlo utilizando la **etiqueta for**, y obtener el número de elementos en la matriz mediante la propiedad size.

```
{% for view in entitylist.views %}

{{ view.name }}

{% endfor %}

{{ entitylist.views[0] }}

{% if entitylist.views.size > 0 %}

This entity list has {{ entitylist.views.size }} views.

{% endif %}
```

## <a name="dictionary"></a>Diccionario

Los diccionarios albergan una colección de valores a los que se pueden acceder con una clave de cadena. Puede obtener acceso a un elemento dado por clave de cadena utilizando \[ \], iterarlo utilizando la **etiqueta for**, y obtener el número de elementos en el diccionario mediante la propiedad size.

```
{{ request.params[ID] }}

{% if request.params.size > 0 %}

The request parameters collection contains some items.

{% endif %}
```

## <a name="datetime"></a>DateTime

Un objeto de fecha y hora representa una fecha y una hora específicas.

```
{{ page.modifiedon | date: 'f' }}
```

## <a name="null"></a>Null

Nulo representa un valor vacío o inexistente. Los resultados que intentan devolver un valor nulo no representarán nada. Se tratarán como false en las condiciones.

```
{% if request.params[ID] %}

This will render if the ID request parameter is NOT null.

{% endif %}
```

### <a name="see-also"></a>Vea también

[Almacenar contenido de origen con plantillas web](store-content-web-templates.md)  
[Descripción de los operadores de Liquid](liquid-operators.md)  
[Condicional](liquid-conditional-operators.md)  
[Objetos de Liquid](liquid-objects.md)  
[Etiquetas de Liquid](liquid-tags.md)  
[Filtros de Liquid](liquid-filters.md)  