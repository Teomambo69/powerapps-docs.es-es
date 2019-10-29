---
title: Usar operadores Liquid para un portal | MicrosoftDocs
description: Obtenga información sobre los operadores Liquid disponibles en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 4a27a5364a4ae12fecc3a72dbb52115e415dcdb8
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976539"
---
# <a name="understand-liquid-operators"></a>Descripción de los operadores de Liquid

Liquid tiene acceso a todos los operadores lógicos y de comparación comunes. Se pueden usar en etiquetas como **If** y **a menos que**.

## <a name="basic-operators"></a>Operadores básicos

| ==    | es igual a                          |
|-------|---------------------------------|
| !=    | No es igual a                  |
| &gt;  | Más de                    |
| &lt;  | Menos de                       |
| &gt;= | Mayor o igual que        |
| &lt;= | Menor o igual que           |
| O bien    | Condición A **o** condición B  |
| etc   | Condición A **y** condición B |

## <a name="contains"></a>Tuviera

contiene pruebas para la presencia de una subcadena en una cadena.

```
{% if page.title contains 'Product' %}

The title of this page contains the word Product.

{% endif %}
```

Contains también puede probar la presencia de una cadena en una matriz de cadenas.

## <a name="startswith"></a>StartsWith

StartsWith comprueba si una cadena comienza con una subcadena determinada.

```
{% if page.title startswith 'Profile' %}

This is a profile page.

{% endif %}
```

## <a name="endswith"></a>EndsWith

EndsWith comprueba si una cadena termina con una subcadena determinada.

```
{% if page.title endswith 'Forum' %}

This is a forum page.

{% endif %}
```

### <a name="see-also"></a>Vea también

[Almacenar contenido de origen mediante plantillas web](store-content-web-templates.md)  
[Tipos de líquido](liquid-types.md)  
[Instrucción](liquid-conditional-operators.md)  
[Objetos Liquid](liquid-objects.md)  
[Etiquetas líquidas](liquid-tags.md)  
[Filtros líquidos](liquid-filters.md) 