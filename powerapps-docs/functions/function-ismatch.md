---
title: "Función IsMatch | Microsoft Docs"
description: "Información de referencia de la función IsMatch en PowerApps, que incluye la sintaxis"
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/05/2017
ms.author: gregli
ms.openlocfilehash: b15a394db060617aeae8324094a70aa8cadf6755
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="ismatch-function-in-powerapps"></a>Función IsMatch en PowerApps
Comprueba si una cadena de texto coincide con un patrón.

## <a name="description"></a>Descripción
La función **IsMatch** comprueba si una cadena de texto coincide con un patrón que puede incluir caracteres normales, patrones predefinidos o una [expresión regular](#regular-expressions).  

Use **IsMatch** para validar que un usuario ha escrito en un control **[Entrada de texto](../controls/control-text-input.md)**. Por ejemplo, puede confirmar si el usuario ha escrito una dirección de correo electrónico válida antes de que el resultado se guarde en el origen de datos. Si la entrada no coincide con los criterios, agregue otros controles que pidan al usuario que corrija la entrada.

De forma predeterminada, **IsMatch** distingue mayúsculas y minúsculas en la cadena de texto completo. Puede modificar este comportamiento especificando una o varias [**MatchOptions**](#match-options).

**IsMatch** devuelve *true* si la cadena de texto coincide con el patrón o *false* si no es así.

## <a name="patterns"></a>Patrones
La clave para usar **IsMatch** está en describir el patrón de coincidencia. El patrón en una cadena de texto se describe como una combinación de:

* Caracteres normales, como **"abc"** o **"123"**.
* Patrones predefinidos, como **Letter**, **MultipleDigits** o **Email**. (La enumeración **Match** define estos patrones).
* Códigos de expresiones regulares, como **"\d+\s+\d+"** o **"[a-z]+"**.

Combine estos elementos mediante el [operador de concatenación de cadenas **&**](operators.md). Por ejemplo, **"abc" & Digit & "\s+"** es un patrón válido que busca la coincidencia de los caracteres "a", "b" y "c", seguido de un dígito del 0 al 9, seguido de al menos un carácter de espacio en blanco.

### <a name="ordinary-characters"></a>Caracteres normales
El patrón más sencillo es una secuencia de caracteres normales que deben coincidir exactamente.

Por ejemplo, la cadena "Hello" coincide con el patrón **"Hello"** exactamente. Ni más ni menos. La cadena "hello!" no coincide con el patrón por el signo de exclamación del final y la "h" en minúscula. (Consulte [MatchOptions](#match-options) para ver formas de modificar este comportamiento).

En el lenguaje del patrón, algunos caracteres están reservados para fines especiales. Para usar estos caracteres, coloque delante una **\\** (barra diagonal inversa) para indicar que el carácter se debe usar literalmente o utilice uno de los patrones predefinidos. En esta tabla se enumeran los caracteres especiales:

| Carácter especial | Descripción |
| --- | --- |
| **.** |punto |
| **?** |signo de interrogación |
| **&#42;** |asterisco |
| **\+** |signo más |
| **( )** |paréntesis |
| **[ ]** |corchetes |
| **{ }** |llaves |
| **^** |símbolo de intercalación |
| **$** |signo de dólar |
| **&#124;** |barra vertical |
| **\\** |barra diagonal inversa |

Por ejemplo, puede buscar la coincidencia de "Hello?" mediante el patrón **"Hello\\?"** con una barra diagonal delante del signo de interrogación.

### <a name="predefined-patterns"></a>Patrones predefinidos
Los patrones predefinidos proporcionan una manera sencilla de buscar coincidencia con un carácter de un conjunto de caracteres o con una secuencia de varios caracteres. Use el [operador de concatenación de cadenas **&**](operators.md) para combinar sus propias cadenas de texto con miembros de la enumeración **Match**:

| Enumeración Match | Descripción | Expresión regular |
| --- | --- | --- |
| **Any** |Busca la coincidencia con cualquier carácter. |**.** |
| **Comma** |Busca la coincidencia con una coma. |**,** |
| **Digit** |Busca la coincidencia con un único dígito (del "0" al "9"). |**\\d** |
| **Email** |Busca la coincidencia con una dirección de correo electrónico que contiene un símbolo "arroba" ("@") y un nombre de dominio que contiene un punto (".") |**.+@.+\\.[^\\.]{2,}** |
| **Hyphen** |Busca la coincidencia con un guion. |**\\-** |
| **LeftParen** |Busca la coincidencia con un paréntesis izquierdo "(". |**\\(** |
| **Letter** |Busca la coincidencia con una letra. |**\\p{L}** |
| **MultipleDigits** |Busca la coincidencia con uno o varios dígitos. |**\\d+** |
| **MultipleLetters** |Busca la coincidencia con una o varias letras. |**\\p{L}+** |
| **MultipleNonSpaces** |Busca la coincidencia con uno o varios caracteres que no agregan espacios en blanco (espacio, tabulación, nueva línea). |**\\S+** |
| **MultipleSpaces** |Busca la coincidencia con uno o varios caracteres que agregan espacio en blanco (espacio, tabulación, nueva línea). |**\\s+** |
| **NonSpace** |Busca la coincidencia con un único carácter que no agrega espacios en blanco. |**\\S** |
| **OptionalDigits** |Busca la coincidencia con cero, uno o más dígitos. |**\\d** |
| **OptionalLetters** |Busca la coincidencia con cero, una o más letras. |**\\p{L}** |
| **OptionalNonSpaces** |Busca la coincidencia con cero, uno o más caracteres que no agregan espacio en blanco. |**\\S** |
| **OptionalSpaces** |Busca la coincidencia con cero, uno o más caracteres que agregan espacio en blanco. |**\\s** |
| **Period** |Busca la coincidencia con un punto ("."). |**\\.** |
| **RightParen** |Busca la coincidencia con un paréntesis derecho ")". |**\\)** |
| **Space** |Busca la coincidencia con un carácter que agrega espacio en blanco. |**\\s** |

Por ejemplo, el patrón **"A" & MultipleDigits** buscará la coincidencia con la letra "A" seguido de uno o varios dígitos.  

### <a name="regular-expressions"></a>Expresiones regulares
El patrón usado por **IsMatch** es una *expresión regular*. Los caracteres normales y los patrones predefinidos que se han descrito anteriormente ayudan a crear expresiones regulares.  

Las expresiones regulares son muy eficaces, están disponibles en muchos lenguajes de programación y se usan para multitud de propósitos. En este artículo no se pueden describir todos los aspectos de las expresiones regulares, pero existe una gran cantidad de información y tutoriales publicados en Internet que le pueden servir de ayuda.  

Las expresiones regulares tienen distintos dialectos y PowerApps emplea una variante del dialecto JavaScript. Para más información, consulte la [sintaxis de expresiones regulares](http://msdn.microsoft.com/library/1400241x.aspx).

En la tabla de enumeración **Match** anterior, cada enumeración se expande en una expresión regular y la cadena de texto de la columna "Regular Expression" define esa expresión.

## <a name="match-options"></a>Opciones de coincidencia
También puede modificar el comportamiento de **IsMatch** mediante la especificación de una o más opciones, que se pueden combinar con el operador de concatenación de cadenas (**&amp;**).  

De forma predeterminada, **IsMatch** busca una coincidencia completa de toda la cadena de texto.

| Enumeración MatchOptions | Descripción | Impacto en la expresión regular |
| --- | --- | --- |
| **BeginsWith** |El patrón debe coincidir desde el principio del texto. |Agrega un **^** al principio de la expresión regular. |
| **Complete** |Predeterminado.  El patrón debe coincidir con el texto entero, de principio a fin. |Agrega **^** al principio y **$** al final de la expresión regular. |
| **Contains** |El patrón debe aparecer en alguna parte del texto pero no tiene que ser al principio o al final. |No modifica la expresión regular. |
| **EndsWith** |El patrón debe coincidir con el final del texto. |Agrega **$** al final de la expresión regular. |
| **IgnoreCase** |Trata la búsqueda de coincidencias de letras sin distinción de mayúsculas y minúsculas. De forma predeterminada, la búsqueda de coincidencia distingue mayúsculas y minúsculas. |No modifica la expresión regular. |
| **Multiline** |Busca la coincidencia entre varias líneas. |No modifica la expresión regular. |

## <a name="syntax"></a>Sintaxis
**IsMatch**( *Texto*, *Pattern* [, *Options* ] )

* *Texto*: requerido.  La cadena de texto que se va a probar.
* *Pattern*: requerido.  El patrón que se va a probar, como una cadena de texto.  Concatene los patrones predefinidos que define la enumeración **Match** o proporcione una expresión regular.
* *Options*: valor opcional.  Una combinación de cadenas de texto de valores de enumeración **MatchOptions**.  De forma predeterminada, se usa **MatchOptions.Complete**.

## <a name="examples"></a>Ejemplos
### <a name="ordinary-characters"></a>Caracteres normales
Imagine que la aplicación contiene un control **Entrada de texto** denominado **TextInput1**.  El usuario escribe valores en este control para almacenarlos en una base de datos.   

El usuario escribe **Hello world** en **TextInput1**.

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **IsMatch( TextInput1.Text, "Hello world" )** |Comprueba si la entrada del usuario coincide exactamente con la cadena "Hello world". |**true** |
| **IsMatch( TextInput1.Text, "Good bye" )** |Comprueba si la entrada del usuario coincide exactamente con la cadena "Good bye". |**false** |
| **IsMatch( TextInput1.Text, "hello", Contains )** |Comprueba si la entrada del usuario contiene la palabra "hello" (con distinción de mayúsculas y minúsculas). |**false** |
| **IsMatch( TextInput1.Text, "hello", Contains & IgnoreCase )** |Comprueba si la entrada del usuario contiene la palabra "hello" (con distinción de mayúsculas y minúsculas). |**true** |

### <a name="predefined-patterns"></a>Patrones predefinidos
| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **IsMatch( "123-45-7890", Digit & Digit & Digit & Hyphen & Digit & Digit & Hyphen & Digit & Digit & Digit & Digit & Digit )** |Busca la coincidencia con un número de la Seguridad Social de Estados Unidos. |**true** |
| **IsMatch( "joan@contoso.com", Email )** |Busca la coincidencia con una dirección de correo electrónico. |**true** |
| **IsMatch( "123.456", MultipleDigits & Period & OptionalDigits )** |Busca la coincidencia con una secuencia de dígitos, un punto y luego cero o más dígitos. |**true** |
| **IsMatch( "123", MultipleDigits & Period & OptionalDigits )** |Busca la coincidencia con una secuencia de dígitos, un punto y luego cero o más dígitos. Un punto no aparece en el texto, así que no hay coincidencia con este patrón. |**false** |

### <a name="regular-expressions"></a>Expresiones regulares
| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **IsMatch( "986", "\d+" )** |Busca la coincidencia con un número entero mayor que cero. |**true** |
| **IsMatch( "1.02", "\d+(\.\d\d)?" )** |Busca la coincidencia con un importe de divisa positivo. Si la entrada contiene un separador decimal, la entrada también debe contener 2 caracteres numéricos después de la coma decimal. Por ejemplo, 3,00 es válido, pero no 3,1. |**true** |
| **IsMatch( "-4.95", "(-)?\d+(\.\d\d)?" )** |Busca la coincidencia con un importe de divisa negativo. Si la entrada contiene un separador decimal, la entrada también debe contener 2 caracteres numéricos después de la coma decimal. |**true** |
| **IsMatch( "111-11-1111", "\d{3}-\d{2}-\d{4}" )** |Busca la coincidencia con un número de la Seguridad Social de Estados Unidos.  Valida el formato, el tipo y la longitud del campo de entrada proporcionado. La cadena con la que se busca coincidencia debe estar formada por 3 caracteres numéricos seguidos de un guion, luego 2 caracteres numéricos seguidos de un guion y luego 4 caracteres numéricos. |**true** |
| **IsMatch( "111-111-111", "\d{3}-\d{2}-\d{4}" )** |Lo mismo que el ejemplo anterior, pero uno de los guiones está fuera de lugar en la entrada. |**false** |
| **IsMatch( "weakpassword", "(?!^[0-9]\*$)(?!^[a-zA-Z]\*$)([a-zA-Z0-9]{8,10})" )** |Valida una contraseña segura, que debe contener 8, 9 o 10 caracteres, además de al menos un dígito y al menos un carácter alfabético. La cadena no debe contener caracteres especiales. |**false** |
| **IsMatch( "http://microsoft.com", "(ht&#124;f)tp(s?)\:\/\/\[0-9a-zA-Z\]([-.\w]\*[0-9a-zA-Z])\*(:(0-9)\*)\*(\/?)([a-zA-Z0-9\-\.\?\,\'\/\\\+&amp;%\$#_]\*)?" )** |Valida una dirección URL http, https o ftp. |**true** |

