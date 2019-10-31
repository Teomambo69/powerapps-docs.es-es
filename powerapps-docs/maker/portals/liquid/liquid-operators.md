---
title: Usar operadores de Liquid para un portal | MicrosoftDocs
description: Obtenga información acerca de los operadores de Liquid disponibles en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="understand-liquid-operators"></a>Descripción de los operadores de Liquid

Liquid tiene acceso a todos los operadores lógicos y de comparación comunes. Estos pueden usarse en etiquetas como **si** y **a menos que**.

## <a name="basic-operators"></a>Operadores básicos

| ==    | Es igual a                          |
|-------|---------------------------------|
| !=    | No es igual a                  |
| &gt;  | Mayor que                    |
| &lt;  | Menor que                       |
| &gt;= | Mayor o igual que        |
| &lt;= | Menor o igual que           |
| o    | Condición A **o** condición B  |
| y   | Condición A **y** condición B |

## <a name="contains"></a>contiene

contains comprueba la presencia de una subcadena dentro de una cadena.

```
{% if page.title contains 'Product' %}

The title of this page contains the word Product.

{% endif %}
```

contains también puede comprobar la presencia de una cadena dentro de una matriz de cadenas.

## <a name="startswith"></a>startswith

contains comprueba si una cadena empieza con una subcadena determinada.

```
{% if page.title startswith 'Profile' %}

This is a profile page.

{% endif %}
```

## <a name="endswith"></a>endswith

endswith comprueba si una cadena termina con una subcadena determinada.

```
{% if page.title endswith 'Forum' %}

This is a forum page.

{% endif %}
```

### <a name="see-also"></a>Vea también

[Almacenar contenido de origen con plantillas web](store-content-web-templates.md)  
[Tipos Liquid](liquid-types.md)  
[Condicional](liquid-conditional-operators.md)  
[Objetos de Liquid](liquid-objects.md)  
[Etiquetas de Liquid](liquid-tags.md)  
[Filtros de Liquid](liquid-filters.md) 