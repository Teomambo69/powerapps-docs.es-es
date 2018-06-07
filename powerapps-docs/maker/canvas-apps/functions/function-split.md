---
title: Función Split | Microsoft Docs
description: Información de referencia de la función Split de PowerApps, con sintaxis y ejemplos
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 08/28/2017
ms.author: gregli
ms.openlocfilehash: 3cb894d044a1e6ac02234bc1fa4c5b9239959015
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "31830679"
---
# <a name="split-function-in-powerapps"></a>Función Split en PowerApps
Divide una cadena de texto en una tabla de subcadenas.

## <a name="description"></a>Descripción
La función **Split** divide una cadena de texto en una tabla de subcadenas.  Se usa para dividir listas delimitada por comas, fechas que usan una barra diagonal entre sus distintas partes y en otras situaciones en las que se utiliza un delimitador bien definido.  

Para dividir la cadena de texto se usa una cadena de separación.  El separador puede ser cero, uno o varios caracteres que coinciden en conjunto con la cadena de texto.  Si se usa una longitud cero o una cadena *en blanco*, cada carácter se divide individualmente.  Los caracteres separadores coincidentes no se devuelven en el resultado.  Si no se encuentra ninguna coincidencia en el separador, toda la cadena de texto se devuelve como un único resultado.

Use la función **[Concat](function-concatenate.md)** función para volver a combinar la cadena (sin los separadores).  

## <a name="syntax"></a>Sintaxis
**Split**(*Texto*, *Separador*)

* *Text*: se requiere.  Texto que se divide.
* *Separador*: se requiere.  Separador que se usa para dividir la cadena.  Puede ser cero, uno o varios caracteres.

## <a name="examples"></a>Ejemplos
| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Split( "Apples,&nbsp;Oranges,&nbsp;Bananas", "," )** |Divide las diferentes frutas, tomando como base la coma, que es el separador.  La división la realiza solo la coma, no el espacio posterior a ella, lo que da lugar a que haya un espacio delante de "&nbsp;Oranges" y "&nbsp;Bananas". |<style> img { max-width: none; } </style> ![](media/function-split/fruit1.png) |
| **TrimEnds( Split( "Apples,&nbsp;Oranges,&nbsp;Bananas", "," ) )** |Igual que el ejemplo anterior, pero en este caso la función [**TrimEnds** quita el espacio](function-trim.md), por lo que se usa solo la tabla de una columna que ha generado **Split**. También podríamos haber usado el separador **",&nbsp;"** que incluye el espacio después de la coma, pero es posible que no hubiera funcionado correctamente en caso de dos espacios, o ninguno. |<style> img { max-width: none; } </style> ![](media/function-split/fruit2.png) |
| **Split( "08/28/17", "/" )** |Divide la fecha, y se usa una barra diagonal como separador. |<style> img { max-width: none; } </style> ![](media/function-split/date.png) |
| **Split( "Hello,&nbsp;World", "," )** |Divide las palabras, y se usa una coma como separador.  El segundo resultado comienza con un espacio, ya que era el carácter inmediatamente posterior a la coma. |<style> img { max-width: none; } </style> ![](media/function-split/comma.png) |
| **Split( "Hello,&nbsp;World", "o" )** |Divide la cadena, y usa el carácter "o" como separador. |<style> img { max-width: none; } </style> ![](media/function-split/o.png) |
| **Split( "Hello,&nbsp;World", "l" )** |Divide la cadena, y usa el carácter individual "l" como separador. Puesto que no había ningún carácter entre los dos **l** de **Hello**, se ha devuelto un valor *en blanco*. |<style> img { max-width: none; } </style> ![](media/function-split/l.png) |
| **Split( "Hello,&nbsp;World", "ll" )** |Divide la cadena, y usa el carácter doble "ll" como separador. |<style> img { max-width: none; } </style> ![](media/function-split/ll.png) |
| **Split( "Hello,&nbsp;World", "%" )** |Divide la cadena, y usa el signo de porcentaje como separador. Como dicho separador no aparece en la cadena, se devuelve toda la cadena como un resultado. |<style> img { max-width: none; } </style> ![](media/function-split/percent.png) |
| **Split( "Hello,&nbsp;World", "" )** |Divide la cadena, y usa una cadena vacía como separador (cero caracteres). De esta forma la cadena se divide en cada carácter. |<style> img { max-width: none; } </style> ![](media/function-split/none.png) |

