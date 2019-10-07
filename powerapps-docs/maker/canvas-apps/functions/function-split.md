---
title: Función Split | Microsoft Docs
description: Información de referencia de la función Split de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm tapanm
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 72f92477cc8c942ee0274267c5bcb13094681873
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984138"
---
# <a name="split-function-in-powerapps"></a>Función Split en PowerApps
Divide una cadena de texto en una tabla de subcadenas.

## <a name="description"></a>Descripción
La función **Split** divide una cadena de texto en una tabla de subcadenas.  Se usa para dividir listas delimitada por comas, fechas que usan una barra diagonal entre sus distintas partes y en otras situaciones en las que se utiliza un delimitador bien definido.  

Para dividir la cadena de texto se usa una cadena de separación.  El separador puede ser cero, uno o varios caracteres que coinciden en conjunto con la cadena de texto.  Si se usa una longitud cero o una cadena *blank*, cada carácter se divide individualmente.  Los caracteres separadores coincidentes no se devuelven en el resultado.  Si no se encuentra ninguna coincidencia en el separador, toda la cadena de texto se devuelve como un único resultado.

Utilice la función **[concat](function-concatenate.md)** para recombinar la cadena sin los separadores. 
 
Utilice la función **[MatchAll](function-ismatch.md)** para dividir una cadena mediante una expresión regular.

En los ejemplos se muestra cómo se puede usar la **división** con la **[primera](function-first-last.md)** y la **[última](function-first-last.md)** función para extraer una única subcadena delimitada.  La función **[Match](function-ismatch.md)** suele ser una opción más concisa y eficaz para los usuarios familiarizados con las expresiones regulares.

## <a name="syntax"></a>Sintaxis
**Split**(*Texto*, *Separador*)

* *Text*: se requiere.  Texto que se divide.
* *Separador*: se requiere.  Separador que se usa para dividir la cadena.  Puede ser cero, uno o varios caracteres.

## <a name="examples"></a>Ejemplos

### <a name="basic-usage"></a>Uso básico

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| `Split( "Apples, Oranges, Bananas", "," )` |Divide las diferentes frutas, tomando como base la coma, que es el separador.  La división la realiza solo la coma, no el espacio posterior a ella, lo que da lugar a que haya un espacio delante de "&nbsp;Oranges" y "&nbsp;Bananas". |<style> img { max-width: none; } </style> ![](media/function-split/fruit1.png) |
| `TrimEnds( Split( "Apples, Oranges, Bananas", "," ) )` |Igual que el ejemplo anterior, pero en este caso la función [**TrimEnds** quita el espacio](function-trim.md), por lo que se usa solo la tabla de una columna que ha generado **Split**. También podríamos haber usado el separador **",&nbsp;"** que incluye el espacio después de la coma, pero es posible que no hubiera funcionado correctamente en caso de dos espacios, o ninguno. |<style> img { max-width: none; } </style> ![](media/function-split/fruit2.png) |
| `Split( "08/28/17", "/" )` |Divide la fecha, y se usa una barra diagonal como separador. |<style> img { max-width: none; } </style> ![](media/function-split/date.png) |

### <a name="different-delimiters"></a>Distintos delimitadores

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| `Split( "Hello, World", "," )` |Divide las palabras, y se usa una coma como separador.  El segundo resultado comienza con un espacio, ya que era el carácter inmediatamente posterior a la coma. |<style> img { max-width: none; } </style> ![](media/function-split/comma.png) |
| `Split( "Hello, World", "o" )` |Divide la cadena, y usa el carácter "o" como separador. |<style> img { max-width: none; } </style> ![](media/function-split/o.png) |
| `Split( "Hello, World", "l" )` |Divide la cadena, y usa el carácter individual "l" como separador. Puesto que no había ningún carácter entre los dos **l** de **Hello**, se ha devuelto un valor *blank*. |<style> img { max-width: none; } </style> ![](media/function-split/l.png) |
| `Split( "Hello, World", "ll" )` |Divide la cadena, y usa el carácter doble "ll" como separador. |<style> img { max-width: none; } </style> ![](media/function-split/ll.png) |
| `Split( "Hello, World", "%" )` |Divide la cadena, y usa el signo de porcentaje como separador. Como dicho separador no aparece en la cadena, se devuelve toda la cadena como un resultado. |<style> img { max-width: none; } </style> ![](media/function-split/percent.png) |
| `Split( "Hello, World", "" )` |Divide la cadena, y usa una cadena vacía como separador (cero caracteres). De esta forma la cadena se divide en cada carácter. |<style> img { max-width: none; } </style> ![](media/function-split/none.png) |

### <a name="substring-extraction"></a>Extracción de subcadenas

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| `First( Split( Last( Split( "Bob Jones <bob.jones@contoso.com>", "<" ) ).Result, ">" ) ).Result` | Divide la cadena en función de un delimitador de apertura (<) y extrae la cadena a la derecha del delimitador con el **último**.  A continuación, la fórmula divide el resultado según el delimitador de cierre (>) y extrae la cadena que está a la izquierda del delimitador con la **derecha**. | "bob.jones@contoso.com" |
| `Match( "Bob Jones <bob.jones@contoso.com>", "<(?<email>.+)>" ).email` | Realiza la misma extracción basada en delimitadores que en el último ejemplo, pero usa en su lugar la función **Match** y una expresión regular. | "bob.jones@contoso.com" |

