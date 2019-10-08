---
title: Funciones Left, Mid y Right| Microsoft Docs
description: Información de referencia de las funciones Left, Mid y Right de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 81220ab8df16dcea74dbdc9db48e692e379e1b4d
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992614"
ms.PowerAppsDecimalTransform: true
---
# <a name="left-mid-and-right-functions-in-powerapps"></a>Funciones Left, Mid y Right en PowerApps
Extrae la parte izquierda, central o derecha de una cadena de texto.

## <a name="description"></a>Descripción
Las funciones **Left**, **Mid** y **Right** devuelven una parte de una cadena.

* **Left**: devuelve los caracteres del principio de una cadena.
* **Mid**: devuelve los caracteres centrales de una cadena.
* **Right**: devuelve los caracteres del final de una cadena.

Si especifica una cadena como argumento, la función devuelve la parte que ha solicitado de la cadena. Si especifica una [tabla](../working-with-tables.md) de una columna que contiene cadenas, la función devuelve una tabla de una columna de las partes que solicitó de esas cadenas. Si especifica una tabla con varias columnas, puede convertirla en una tabla de una columna, como se describe en la sección sobre cómo [trabajar con tablas](../working-with-tables.md).

Si la posición inicial es negativa o sobrepasa el final de la cadena, **Mid** devuelve *blank*.  Puede comprobar la longitud de una cadena mediante la función **[Len](function-len.md)** . Si se solicitan más caracteres de los que contiene la cadena, la función devuelve tantos caracteres como sea posible.

## <a name="syntax"></a>Sintaxis
**Left**( *String*; *NumberOfCharacters* )<br>**Mid**( *String*; *StartingPosition*; *NumberOfCharacters* )<br>**Right**( *String*; *NumberOfCharacters* )

* *String*: requerido. La cadena hasta la cual se extrae el resultado o desde la que se extrae el resultado.
* *StartingPosition*: requerido (solo **Mid**).  La posición inicial.  El primer carácter de la cadena ocupa la posición 1.
* *NumberOfCharacters* : requerido (solo**izquierda** y **derecha** ).  El número de caracteres que se va a devolver.  Si se omite para la función **Mid** , la función devuelve la parte desde la posición inicial hasta el final de la cadena.

**Left**( *SingleColumnTable*; *NumberOfCharacters* )<br>**Mid**( *SingleColumnTable*; *StartingPosition*; *NumberOfCharacters* )<br>**Right**( *SingleColumnTable*; *NumberOfCharacters* )

* *SingleColumnTable*: requerido. Una tabla de una columna de cadenas de la cual se extraen los resultados.
* *StartingPosition*: requerido (solo **Mid**).  La posición inicial.  El primer carácter de la cadena ocupa la posición 1.
* *NumberOfCharacters* : requerido (solo**izquierda** y **derecha** ).  El número de caracteres que se va a devolver.  Si se omite para la función **Mid** , la función devuelve la parte desde la posición inicial hasta el final de la cadena.

## <a name="examples"></a>Ejemplos
### <a name="single-string"></a>Cadena única
En los ejemplos de esta sección se usa un control de entrada de texto como [origen de datos](../working-with-data-sources.md). El control se denomina **Author** y contiene la cadena "E". E. Cummings".

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Left( Author.Text; 5 )** |Extrae un máximo de cinco caracteres del principio de la cadena. |"E. E". |
| **Mid( Author.Text; 7; 4 )** |Extrae un máximo de cuatro caracteres de la cadena, empezando por el séptimo carácter. |"Cumm" |
| **MID (Author. Text, 7)** |Extrae todos los caracteres, empezando por el séptimo carácter, de la cadena. |"Cummings" |
| **Right( Author.Text; 5 )** |Extrae un máximo de cinco caracteres del final de la cadena. |"mings" |

### <a name="single-column-table"></a>Tabla de una sola columna
En cada ejemplo de esta sección se extraen cadenas de la [columna](../working-with-tables.md#columns) **Address** de este origen de datos, denominado **People**, y se devuelve una tabla de una columna que contiene los resultados:

![](media/function-left-mid-right/people-table.png)

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Left( ShowColumns(&nbsp;People;&nbsp;"Address"&nbsp;); 8 )** |Extrae los ocho primeros caracteres de cada cadena. |<style> img { max-width: none } </style> ![](media/function-left-mid-right/people-table-left.png) |
| **Mid( ShowColumns(&nbsp;People;&nbsp;"Address"&nbsp;); 5; 7 )** |Extrae los siete caracteres centrales de cada cadena, comenzando por el quinto carácter. |![](media/function-left-mid-right/people-table-mid.png) |
| **Right( ShowColumns(&nbsp;People;&nbsp;"Address"&nbsp;); 7 )** |Extrae los siete últimos caracteres de cada cadena. |![](media/function-left-mid-right/people-table-right.png) |

### <a name="step-by-step-example"></a>Ejemplo paso a paso
1. Importe o cree una [colección](../working-with-data-sources.md#collections) denominada **Inventory** y muéstrela en una galería, como se describe en el primer procedimiento en [Show images and text in a gallery](../show-images-text-gallery-sort-filter.md) (Mostrar imágenes y texto en una galería).
2. Establezca la propiedad **[Text](../controls/properties-core.md)** de la etiqueta inferior de la galería en esta función:
   
    **Right(ThisItem.ProductName; 3)**
   
    La etiqueta muestra los tres últimos caracteres de cada nombre de producto.

