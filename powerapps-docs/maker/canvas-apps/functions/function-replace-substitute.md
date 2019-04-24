---
title: Funciones Replace y Substitute | Microsoft Docs
description: Información de referencia para las funciones Replace y Substitute en PowerApps, incluida la sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/02/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fca1953402c87ca13bc3560b827cde03a47a8e92
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61551615"
---
# <a name="replace-and-substitute-functions-in-powerapps"></a>Funciones Replace y Substitute en PowerApps
Reemplace una parte de una cadena de texto por otra cadena.

## <a name="description"></a>Descripción
La función **Replace** identifica el texto que se debe reemplazar según la posición inicial y la longitud.  

La función **Substitute** identifica el texto que se debe reemplazar buscando una cadena coincidente. Si se encuentra más de una coincidencia, puede reemplazar todos ellos o especificar uno para reemplazar.

Si pasa una única cadena, el valor devuelto es la cadena modificada. Si pasa una [tabla](../working-with-tables.md) de una sola columna que contiene cadenas, el valor devuelto es la tabla de una sola columna con cadenas modificadas. Si tiene una tabla con varias columnas, puede convertirla en una tabla de una sola columna, como se describe en cómo [trabajar con tablas](../working-with-tables.md).

## <a name="syntax"></a>Sintaxis
**Replace**( *String*, *StartingPosition*, *NumberOfCharacters*, *NewString* )

* *String*: requerido. La cadena en la que se va a actuar.
* *StartingPosition*: requerido. La posición del carácter en la que se va a iniciar el reemplazo. El primer carácter de *String* está en la posición 1.
* *NumberOfCharacters*: requerido. El número de caracteres que se van a reemplazar en *String*.
* *NewString*: requerido. La cadena de reemplazo. El número de caracteres de este argumento puede diferir del argumento *NumberOfCharacters*.

**Substitute**( *String*, *OldString*, *NewString* [, *InstanceNumber* ] )

* *String*: requerido. La cadena en la que se va a actuar.
* *OldString*: requerido. La cadena que se va a reemplazar.
* *NewString*: requerido. La cadena de reemplazo. *OldString* y *NewString* pueden tener longitudes distintas.
* *InstanceNumber*: opcional. Utilice este argumento para especificar qué instancia de *OldString* reemplazar si *cadena* contiene más de una instancia. Si no especifica este argumento, se reemplazará todas las instancias.

**Replace**( *SingleColumnTable*, *StartingPosition*, *NumberOfCharacters*, *NewString* )

* *SingleColumnTable*: requerido. Una tabla de números de una sola columna sobre la que se va a actuar.
* *StartingPosition*: requerido. La posición del carácter en la que se va a iniciar el reemplazo.  El primer carácter de cada cadena de la tabla se encuentra en la posición 1.
* *NumberOfCharacters*: requerido. El número de caracteres que se van a reemplazar en cada cadena.
* *NewString*: requerido.  La cadena de reemplazo. El número de caracteres de este argumento puede diferir del argumento *NumberOfCharacters*.

**Substitute**( *SingleColumnTable*, *OldString*, *NewString* [, *InstanceNumber* ] )

* *SingleColumnTable*: requerido. Una tabla de números de una sola columna sobre la que se va a actuar.
* *OldString*: requerido.  La cadena que se va a reemplazar.
* *NewString*: requerido.  La cadena de reemplazo. *OldString* y *NewString* pueden tener longitudes distintas.
* *InstanceNumber*: opcional. Utilice este argumento para especificar qué instancia de *OldString* reemplazar si *cadena* contiene más de una instancia. Si no especifica este argumento, se reemplazará todas las instancias.

## <a name="examples"></a>Ejemplos

| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| **Reemplazar ("abcdefghijk",&nbsp;6,&nbsp;5,&nbsp;"*")** | Reemplaza los cinco caracteres de "abcdefghijk" con un solo "*" caracteres, empezando por el sexto carácter ("f"). | "abcde * k" |
| **Reemplazar (&nbsp;"2019,"&nbsp;3,&nbsp;2,&nbsp;"20"&nbsp;)** | Reemplaza los dos últimos caracteres de "2019" con "20". | "2020" |
| **Reemplazar (&nbsp;"123456",&nbsp;1,&nbsp;3,&nbsp;"_"&nbsp;)** | Reemplaza los tres primeros caracteres de "123456" con un carácter único "_". | "_456" | 
| **SUBSTITUTE (&nbsp;"ventas&nbsp;datos",&nbsp;"Ventas",&nbsp;"Costo"&nbsp;)** | Sustituye la cadena "Costo" para "Ventas". | "Datos de costo" | 
| **SUBSTITUTE ("trimestre&nbsp;1,&nbsp;2018", "1", "2", 1)** | Sustituye solo la primera instancia de "1" con "2" porque el cuarto argumento (*InstanceNumber*) se proporciona con un 1. |  "Trimestre 2, 2018" |
| **SUBSTITUTE ("trimestre&nbsp;1,&nbsp;2011", "1", "2", (3).** | Sustituye solo la tercera instancia de "1" con "2" porque el cuarto argumento (*InstanceNumber*) se proporciona con un 3. | "Trimestre 1, 2012" |
| **SUBSTITUTE ("trimestre&nbsp;1,&nbsp;2011", "1", "2")** | Sustituye todas las instancias de "1" con "2" porque el cuarto argumento (*InstanceNumber*) no se proporciona. | "Trimestre 2, 2022" |
| **Reemplazar (<br>[&nbsp;"trimestre&nbsp;1,&nbsp;2018",<br>"trimestre&nbsp;2,&nbsp;2011"<br>"trimestre&nbsp;4,&nbsp;2019"],<br>9, 1, "3")** | Reemplaza la novena en cada registro de la tabla de una sola columna con "3". | [&nbsp;"Trimestre&nbsp;3,&nbsp;2018",<br>"Trimestre&nbsp;3,&nbsp;2011",<br>"Trimestre&nbsp;3,&nbsp;2019"&nbsp;] |
| **SUBSTITUTE ( <br>[&nbsp;"Qtr&nbsp;1,&nbsp;2018",<br>"trimestre&nbsp;1,&nbsp;2011"<br>"Q1,&nbsp;2019"&nbsp;],<br>"1 ","", 1) 3** | Dado que el cuarto argumento (*InstanceNumber*) se proporciona con un valor de 1, sustituye solo la primera instancia de "1" en cada registro de la tabla de una sola columna con "3". | [&nbsp;"Qtr&nbsp;3,&nbsp;2018",<br>"Trimestre&nbsp;3,&nbsp;2011",<br>"Q3,&nbsp;2019"&nbsp;] |
| **SUBSTITUTE ( <br>[&nbsp;"Qtr&nbsp;1,&nbsp;2018",<br>"trimestre&nbsp;1,&nbsp;2011"<br>"Q1,&nbsp;2019"&nbsp;],<br>"1 ","3")** | Dado que el cuarto argumento (*InstanceNumber*) no se proporciona, sustituye todas las instancias de "1" en cada registro de la tabla de una sola columna con "3". | [&nbsp;"Qtr&nbsp;3,&nbsp;2038",<br>"Trimestre&nbsp;3,&nbsp;2033",<br>"Q3,&nbsp;2039"&nbsp;] |  
 


