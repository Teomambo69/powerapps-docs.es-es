---
title: Funciones Acos, Acot, Asin, Atan, Atan2, Cos, Cot, Degrees, Pi, Radians, Sin y Tan | Microsoft Docs
description: Información de referencia de las funciones ABS y sqrt en Power Apps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/13/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8ff8b68dce51ce985c391de569e4be7a5a8fabb4
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74729997"
ms.PowerAppsDecimalTransform: true
---
# <a name="acos-acot-asin-atan-atan2-cos-cot-degrees-pi-radians-sin-and-tan-functions-in-power-apps"></a>Funciones ACOS, ACOT, Asin, atan, Atan2, cos, Cot, degrees, PI, radians, sin y tan en Power apps
Calcula valores trigonométricos.

## <a name="description"></a>Descripción
### <a name="primary-functions"></a>Funciones principales
La función **Cos** devuelve el coseno de su argumento, un ángulo especificado en radianes.

La función **Cot** devuelve la cotangente de su argumento, un ángulo especificado en radianes.

La función **Sin** devuelve el seno de su argumento, un ángulo especificado en radianes.

La función **Tan** devuelve la tangente de su argumento, un ángulo especificado en radianes.

### <a name="inverse-functions"></a>Funciones inversas
El **Acos** función devuelve el arcocoseno, o coseno inverso, de su argumento. El arcocoseno es el ángulo cuyo coseno es el argumento.  El ángulo devuelto se expresa en radianes en el intervalo de 0 (cero) a &pi;.

La función **Acot** devuelve el valor principal de la arcocotangente, o cotangente inversa, de su argumento.  El ángulo devuelto se expresa en radianes en el intervalo de 0 (cero) a &pi;.

La función **Asin** devuelve el arcoseno, o seno inverso, de su argumento. El arcoseno es el ángulo cuyo seno es el argumento.  El ángulo devuelto se expresa en radianes en el intervalo de -&pi;/2 a &pi;/2.

La función **Atan** devuelve la arcotangente, o tangente inversa, de su argumento. La arcotangente es el ángulo cuya tangente es el argumento. El ángulo devuelto se expresa en radianes en el intervalo de -&pi;/2 a &pi;/2.

La función **Atan2** devuelve la arcotangente, o tangente inversa, de las coordenadas *x* e *y* especificadas como argumentos. La arcotangente es el ángulo desde el eje *x* a una línea que contiene el origen (0, 0) y un punto con las coordenadas (*x*, *y*). El ángulo se expresa en radianes entre -&pi; y &pi;, excluyendo -&pi;.  Un resultado positivo representa un ángulo con rotación levógira (hacia la izquierda) desde el eje *x*; un resultado negativo representa un ángulo con rotación dextrógira (hacia la derecha).  **Atan2(&nbsp;*a*;&nbsp;*b*&nbsp;)** es igual a **Atan(&nbsp;*b*/*a*&nbsp;)** , excepto que ***a*** puede ser igual a 0 (cero) con la función **Atan2**.

### <a name="helper-functions"></a>Funciones del asistente
La función **Degrees** convierte radianes en grados.  &pi; radianes equivalen a 180 grados.

La función **Pi** devuelve el número transcendente &pi;, que comienza 3,141592...

La función **Radians** convierte grados en radianes.  

### <a name="notes"></a>Notas
Si pasa un solo número a estas funciones, el valor que se devuelve es un resultado único.  Si pasa una [tabla](../working-with-tables.md) de una sola columna que contiene números, el valor que se muestra es una tabla de resultados de una sola columna, un resultado para cada registro en la tabla del argumento. Si tiene una tabla con varias columnas, puede convertirla en una tabla de una sola columna, como se describe en cómo [trabajar con tablas](../working-with-tables.md).  

Si algún argumento resultase en un valor no definido, el resultado es *blank*.  Esto puede ocurrir, por ejemplo, al utilizar las funciones inversas con argumentos que están fuera del intervalo.

## <a name="syntax"></a>Sintaxis
### <a name="primary-functions"></a>Funciones principales
**Cos**( *Radians* )<br>**Cot**( *Radians* )<br>**Sin**( *Radians* )<br>**Tan**( *Radians* )

* *Radians*: requerido. Ángulo sobre el cual operar.

**Cos**( *SingleColumnTable* )<br>**Cot**( *SingleColumnTable* )<br>**Sin**( *SingleColumnTable* )<br>**Tan**( *SingleColumnTable* )

* *SingleColumnTable*: requerido. Una tabla de ángulos de una sola columna sobre la que se va a actuar.

### <a name="inverse-functions"></a>Funciones inversas
**Acos**( *Number* )<br>**Acot**( *Number* )<br>**Asin**( *Number* )<br>**Atan**( *Number* )

* *Number*: requerido. El número sobre el cual operar.

**Acos**( *SingleColumnTable* )<br>**Acot**( *SingleColumnTable* )<br>**Asin**( *SingleColumnTable* )<br>**Atan**( *SingleColumnTable* )

* *SingleColumnTable*: requerido. Una tabla de números de una sola columna sobre la cual operar.

**Atan2**( *X*; *Y* )

* *X*: requerido.  coordenadas del eje *X*.
* *Y*: requerido.  coordenadas del eje *Y*.

### <a name="helper-functions"></a>Funciones del asistente
**Degrees**( *Radians* )

* *Radians*: requerido.  Ángulo en radianes para convertir en grados.

**Pi**()

**Radians**( *Degrees* )

* *Degrees*: requerido.  Ángulo en grados para convertir en radianes.

## <a name="examples"></a>Ejemplos
### <a name="single-number"></a>Número único

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Cos(&nbsp;1;047197&nbsp;)** |Devuelve el coseno de 1,047197 radianes o 60 grados. |0,5 |
| **Cot(&nbsp;Pi()/4&nbsp;)** |Devuelve la cotangente de 0,785398... radianes o 45 grados. |1 |
| **Sin(&nbsp;Pi()/2&nbsp;)** |Devuelve el seno de 1,570796 radianes o 90 grados. |1 |
| **Tan (&nbsp;Radians(60)&nbsp;)** |Devuelve la tangente de 1,047197 radianes o 60 grados. |1,732050... |
| **Acos(&nbsp;0;5&nbsp;)** |Devuelve el arcocoseno de 0,5 en radianes. |1,047197... |
| **Acot(&nbsp;1&nbsp;)** |Devuelve la arcocotangente de 1, en radianes. |0,785398... |
| **Asin(&nbsp;1&nbsp;)** |Devuelve el arcoseno de 1, en radianes. |1,570796... |
| **Atan (&nbsp;1,732050&nbsp;)** |Devuelve la arcotangente de 1,732050, en radianes. |1,047197... |
| **Atan2(&nbsp;5;&nbsp;3&nbsp;)** |Devuelve la arcotangente del ángulo del eje *x* de la línea que contiene el origen (0,0) y la coordenada (5,3), que es aproximadamente 31 grados. |0,540419... |
| **Atan2(&nbsp;4;&nbsp;4&nbsp;)** |Devuelve la arcotangente del ángulo del eje *x* de la línea que contiene el origen (0,0) y la coordenada (4,4), que es exactamente &pi;/4 radianes o 45 grados. |0,785398... |
| **Degrees (&nbsp;1,047197&nbsp;)** |Devuelve el número equivalente de grados de 1,047197 radianes. |60 |
| **Pi()** |El número trascendente &pi;. |3,141592... |
| **Radians (&nbsp;15&nbsp;)** |Devuelve el número equivalente de radianes para 15 grados. |0,261799... |

### <a name="single-column-table"></a>Tabla de una sola columna
Los ejemplos de esta sección usan un [origen de datos](../working-with-data-sources.md) denominado **ValueTable** que contiene los siguientes datos:  El último registro en la tabla es &pi;/2 radianes o 90 grados.

![](media/function-trig/values.png)

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Cos(&nbsp;ValueTable&nbsp;)** |Devuelve el coseno de cada número en la tabla. |<style> img { max-width: none } </style> ![](media/function-trig/values-cos.png) |
| **Cot(&nbsp;ValueTable&nbsp;)** |Devuelve la cotangente de cada número en la tabla. |<style> img { max-width: none } </style> ![](media/function-trig/values-cot.png) |
| **Sin(&nbsp;ValueTable&nbsp;)** |Devuelve el seno de cada número en la tabla. |<style> img { max-width: none } </style> ![](media/function-trig/values-sin.png) |
| **Tan(&nbsp;ValueTable&nbsp;)** |Devuelve la tangente de cada número en la tabla. |<style> img { max-width: none } </style> ![](media/function-trig/values-tan.png) |
| **Acos(&nbsp;ValueTable&nbsp;)** |Devuelve el arcocoseno de cada número en la tabla. |<style> img { max-width: none } </style> ![](media/function-trig/values-acos.png) |
| **Acot(&nbsp;ValueTable&nbsp;)** |Devuelve la arcocotangente de cada número en la tabla. |<style> img { max-width: none } </style> ![](media/function-trig/values-acot.png) |
| **Asin(&nbsp;ValueTable&nbsp;)** |Devuelve el arcoseno de cada número en la tabla. |<style> img { max-width: none } </style> ![](media/function-trig/values-asin.png) |
| **Atan(&nbsp;ValueTable&nbsp;)** |Devuelve la arcotangente de cada número en la tabla. |<style> img { max-width: none } </style> ![](media/function-trig/values-atan.png) |
| **Degrees(&nbsp;ValueTable&nbsp;)** |Devuelve el número equivalente de grados para cada número de la tabla, supone que son ángulos en radianes. |<style> img { max-width: none } </style> ![](media/function-trig/values-degrees.png) |
| **Radians(&nbsp;ValueTable&nbsp;)** |Devuelve el número equivalente de radianes para cada número de la tabla, supone que son ángulos en grados. |<style> img { max-width: none } </style> ![](media/function-trig/values-radians.png) |

