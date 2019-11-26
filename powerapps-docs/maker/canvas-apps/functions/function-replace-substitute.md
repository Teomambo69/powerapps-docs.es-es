---
title: Funciones Reemplazar y Substitute | Microsoft Docs
description: Información de referencia para las funciones Replace y Substitute en PowerApps, incluida la sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/02/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ff0e016f6ab1ad4f66651ccd3cfa2711f1d85a38
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992387"
ms.PowerAppsDecimalTransform: true
---
# <a name="replace-and-substitute-functions-in-powerapps"></a>Funciones Replace y Substitute en PowerApps
Reemplace una parte de una cadena de texto por otra cadena.

## <a name="description"></a>Descripción
La función **Replace** identifica el texto que se debe reemplazar según la posición inicial y la longitud.  

La función **Substitute** identifica el texto que se debe reemplazar buscando una cadena coincidente. Si se encuentra más de una coincidencia, puede reemplazar todas ellas o especificar una para reemplazar.

Si pasa una única cadena, el valor devuelto es la cadena modificada. Si pasa una [tabla](../working-with-tables.md) de una sola columna que contiene cadenas, el valor devuelto es la tabla de una sola columna con cadenas modificadas. Si tiene una tabla con varias columnas, puede convertirla en una tabla de una sola columna, como se describe en cómo [trabajar con tablas](../working-with-tables.md).

## <a name="syntax"></a>Sintaxis
**Replace**( *String*; *StartingPosition*; *NumberOfCharacters*; *NewString* )

* *String*: requerido. La cadena en la que se va a actuar.
* *StartingPosition*: requerido. La posición del carácter en la que se va a iniciar el reemplazo. El primer carácter de *String* está en la posición 1.
* *NumberOfCharacters*: requerido. El número de caracteres que se van a reemplazar en *String*.
* *NewString*: requerido. La cadena de reemplazo. El número de caracteres de este argumento puede diferir del argumento *NumberOfCharacters*.

**Substitute**( *String*; *OldString*; *NewString* [; *InstanceNumber* ] )

* *String*: requerido. La cadena en la que se va a actuar.
* *OldString*: requerido. La cadena que se va a reemplazar.
* *NewString*: requerido. La cadena de reemplazo. *OldString* y *NewString* pueden tener longitudes distintas.
* *InstanceNumber*: opcional. Use este argumento para especificar la instancia de *OldString* que se va a reemplazar si *String* contiene más de una instancia. Si no especifica este argumento, se reemplazarán todas las instancias.

**Replace**( *SingleColumnTable*; *StartingPosition*; *NumberOfCharacters*; *NewString* )

* *SingleColumnTable*: requerido. Una tabla de números de una sola columna sobre la que se va a actuar.
* *StartingPosition*: requerido. La posición del carácter en la que se va a iniciar el reemplazo.  El primer carácter de cada cadena de la tabla se encuentra en la posición 1.
* *NumberOfCharacters*: requerido. El número de caracteres que se van a reemplazar en cada cadena.
* *NewString*: requerido.  La cadena de reemplazo. El número de caracteres de este argumento puede diferir del argumento *NumberOfCharacters*.

**Substitute**( *SingleColumnTable*; *OldString*; *NewString* [; *InstanceNumber* ] )

* *SingleColumnTable*: requerido. Una tabla de números de una sola columna sobre la que se va a actuar.
* *OldString*: requerido.  La cadena que se va a reemplazar.
* *NewString*: requerido.  La cadena de reemplazo. *OldString* y *NewString* pueden tener longitudes distintas.
* *InstanceNumber*: opcional. Use este argumento para especificar la instancia de *OldString* que se va a reemplazar si *String* contiene más de una instancia. Si no especifica este argumento, se reemplazarán todas las instancias.

## <a name="examples"></a>Ejemplos

| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| **Replace ("abcdefghijk",&nbsp;6,&nbsp;5,&nbsp;"*")** | Reemplaza cinco caracteres de "abcdefghijk" por un único carácter "*", empezando por el sexto carácter ("f"). | "ABCDE * k" |
| **Replace (&nbsp;"2019",&nbsp;3,&nbsp;2,&nbsp;"20"&nbsp;)** | Reemplaza los dos últimos caracteres de "2019" por "20". | "2020" |
| **Replace (&nbsp;"123456",&nbsp;1,&nbsp;3,&nbsp;"_"&nbsp;)** | Reemplaza los tres primeros caracteres de "123456" por un único carácter "_". | "_456" | 
| **Substitute (&nbsp;"ventas&nbsp;datos",&nbsp;"ventas",&nbsp;"costo"&nbsp;)** | Sustituye la cadena "cost" por "sales". | "Datos de costo" | 
| **Substitute ("Quarter&nbsp;1,&nbsp;2018", "1", "2", 1)** | Sustituye solo la primera instancia de "1" por "2" porque el cuarto argumento (*InstanceNumber*) se proporciona con un 1. |  "Trimestre 2, 2018" |
| **Substitute ("Quarter&nbsp;1,&nbsp;2011", "1", "2", 3)** | Sustituye solo la tercera instancia de "1" por "2" porque el cuarto argumento (*InstanceNumber*) se proporciona con un 3. | "Trimestre 1, 2012" |
| **Substitute ("Quarter&nbsp;1,&nbsp;2011", "1", "2")** | Sustituye todas las instancias de "1" por "2" porque no se proporciona el cuarto argumento (*InstanceNumber*). | "Trimestre 2, 2022" |
| **Replace (<br>[&nbsp;"Quarter&nbsp;1,&nbsp;2018";<br>"Quarter&nbsp;2,&nbsp;2011";<br>"Quarter&nbsp;4,&nbsp;2019"];<br>9; 1; "3")** | Reemplaza el noveno carácter de cada registro de la tabla de una sola columna por "3". | [&nbsp;"Quarter&nbsp;3,&nbsp;2018",<br>"Quarter&nbsp;3,&nbsp;2011",<br>"Quarter&nbsp;3,&nbsp;2019"&nbsp;] |
| **Substitute (<br>[&nbsp;"Trim&nbsp;1,&nbsp;2018";<br>"Quarter&nbsp;1,&nbsp;2011";<br>"Q1,&nbsp;2019"&nbsp;];<br>"1"; "3"; 1)** | Dado que el cuarto argumento (*InstanceNumber*) se proporciona con un valor de 1, sustituye solo la primera instancia de "1" en cada registro de la tabla de una sola columna con "3". | [&nbsp;"Trim&nbsp;3,&nbsp;2018",<br>"Quarter&nbsp;3,&nbsp;2011",<br>"T3,&nbsp;2019"&nbsp;] |
| **Substitute (<br>[&nbsp;"Trim&nbsp;1,&nbsp;2018";<br>"Quarter&nbsp;1,&nbsp;2011";<br>"Q1,&nbsp;2019"&nbsp;];<br>"1"; "3")** | Dado que no se proporciona el cuarto argumento (*InstanceNumber*), sustituye todas las instancias de "1" en cada registro de la tabla de una sola columna con "3". | [&nbsp;"Trim&nbsp;3,&nbsp;2038",<br>"Quarter&nbsp;3,&nbsp;2033",<br>"T3,&nbsp;2039"&nbsp;] |  
 


