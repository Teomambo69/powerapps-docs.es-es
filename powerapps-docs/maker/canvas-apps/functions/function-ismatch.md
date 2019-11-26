---
title: Funciones IsMatch, Match y MatchAll | Microsoft Docs
description: Información de referencia de las funciones IsMatch, Match y MatchAll en PowerApps, incluida la sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/15/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ac6e5196de03a3c2d292696f1216c443f4c5b7e6
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992659"
ms.PowerAppsDecimalTransform: true
---
# <a name="ismatch-match-and-matchall-functions-in-powerapps"></a>Funciones IsMatch, Match y MatchAll en PowerApps
Comprueba si hay coincidencias o extrae partes de una cadena de texto basándose en un patrón.

## <a name="description"></a>Descripción
La función **IsMatch** comprueba si una cadena de texto coincide con un patrón que puede incluir caracteres normales, patrones predefinidos o una [expresión regular](#regular-expressions).  Las funciones **Match** y **MatchAll** devuelven lo que coincidía, incluidas las subcoincidencias.  

Use **IsMatch** para validar que un usuario ha escrito en un control **[Entrada de texto](../controls/control-text-input.md)** . Por ejemplo, puede confirmar si el usuario ha escrito una dirección de correo electrónico válida antes de que el resultado se guarde en el origen de datos. Si la entrada no coincide con los criterios, agregue otros controles que pidan al usuario que corrija la entrada.

Use **Match** para extraer la primera cadena de texto que coincida con un patrón y **MatchAll** para extraer todas las cadenas de texto que coincidan. También puede extraer coincidencias secundarias para analizar cadenas complejas.   

**Match** devuelve un registro de información para la primera coincidencia encontrada y **MatchAll** devuelve una tabla de registros para cada coincidencia encontrada. El registro o los registros contienen:

| Columna | Tipo | Descripción |
|----|----|----|
| *coincidencia secundaria&#8209;o sub&#8209;coincidencias* | Texto | Cada subcoincidencia con nombre tendrá su propia columna. Cree una subcoincidencia con nombre mediante **(?&lt;*nombre*&gt;** ... **)** en la expresión regular. Si una subcoincidencia con nombre tiene el mismo nombre que una de las columnas predefinidas (a continuación), la subcoincidencia tiene prioridad y se genera una advertencia. Para evitar esta advertencia, cambie el nombre de la subcoincidencia. |
| **FullMatch** | Texto | Toda la cadena de texto con la que se encontró una coincidencia. |
| **StartMatch** | Número | Posición inicial de la coincidencia dentro de la cadena de texto de entrada. El primer carácter de la cadena devuelve 1. | 
| **Subcoincidencias** | Tabla de texto de una sola columna ( **valor**de columna) | Tabla de subcoincidencias con nombre y sin nombre en el orden en que aparecen en la expresión regular. Por lo general, las subcoincidencias con nombre son más fáciles de trabajar con y se recomiendan. Use las funciones [**forall**](function-forall.md) o [**Last**](function-first-last.md)( [**firstn**](function-first-last.md)( **...** )) para trabajar con una subcoincidencia individual. Si no se definen subcoincidencias en la expresión regular, esta tabla estará presente pero vacía. |

Estas funciones admiten [**MatchOptions**](#match-options). De forma predeterminada: 
- Estas funciones realizan una coincidencia que distingue entre mayúsculas y minúsculas. Use **ignoreCase** para realizar coincidencias que no distinguen mayúsculas de minúsculas.    
- **IsMatch** coincide con toda la cadena de texto (**Complete** MatchOption), mientras que **Match** y **MatchAll** buscan una coincidencia en cualquier parte de la cadena de texto (**contiene** MatchOption). Use **Complete**, **Contains**, **BeginsWith**o **EndsWith** según corresponda para su escenario.

**IsMatch** devuelve *true* si la cadena de texto coincide con el patrón o *false* si no es así. **Match** devuelve un valor *en blanco* si no se encuentra ninguna coincidencia que se pueda probar con la función [**esblanco**](function-isblank-isempty.md) . **MatchAll** devuelve una tabla vacía si no se encuentra ninguna coincidencia que se pueda probar con la función [**IsEmpty**](function-isblank-isempty.md) .

Si usa **MatchAll** para dividir una cadena de texto, considere la posibilidad de usar la función **[Split](function-split.md)** , que es más fácil de usar y más rápida.

## <a name="patterns"></a>Patrones
La clave para usar estas funciones es describir el patrón que debe coincidir. El patrón en una cadena de texto se describe como una combinación de:

* Caracteres normales, como **"abc"** o **"123"** .
* Patrones predefinidos, como **Letter**, **MultipleDigits** o **Email**. (La enumeración **Match** define estos patrones).
* Códigos de expresión regular, como **"\d + \s + \d +"** o **"[a-z] +"** .

Combine estos elementos mediante el [operador de concatenación de cadenas **&** ](operators.md). Por ejemplo, **"abc" & Digit & "\s+"** es un patrón válido que busca la coincidencia de los caracteres "a", "b" y "c", seguido de un dígito del 0 al 9, seguido de al menos un carácter de espacio en blanco.

### <a name="ordinary-characters"></a>Caracteres normales
El patrón más sencillo es una secuencia de caracteres normales que deben coincidir exactamente.

Por ejemplo, cuando se usa con la función **IsMatch** , la cadena "Hello" coincide exactamente con el patrón **"Hello"** . Ni más ni menos. La cadena "hello!" no coincide con el patrón debido al signo de exclamación del final y porque el caso es incorrecto para la letra "h". (Consulte [MatchOptions](#match-options) para ver formas de modificar este comportamiento).

En el lenguaje del patrón, algunos caracteres están reservados para fines especiales. Para usar estos caracteres, anteponga al carácter un **\\** (barra diagonal inversa) para indicar que el carácter debe tomarse literalmente, o bien puede usar uno de los patrones predefinidos que se describen más adelante en este tema. En esta tabla se enumeran los caracteres especiales:

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
| **\|** |barra vertical |
| **\\** |barra diagonal inversa |

Por ejemplo, puede buscar la coincidencia de "Hello?" mediante el patrón **"Hello\\?"** con una barra diagonal delante del signo de interrogación.

### <a name="predefined-patterns"></a>Patrones predefinidos
Los patrones predefinidos proporcionan una manera sencilla de buscar coincidencias con uno de un juego de caracteres o con una secuencia de varios caracteres. Use el [operador de concatenación de cadenas **&** ](operators.md) para combinar sus propias cadenas de texto con miembros de la enumeración **Match** :

| Coincidencia de enumeración | Descripción | Expresión regular |
| --- | --- | --- |
| **Any** |Busca la coincidencia con cualquier carácter. |`.` |
| **Comma** |Busca la coincidencia con una coma. |`;` |
| **Digit** |Busca la coincidencia con un único dígito (del "0" al "9"). |`\d` |
| **Email** |Busca la coincidencia con una dirección de correo electrónico que contiene un símbolo "arroba" ("\@") y un nombre de dominio que contiene un punto (".") |`.+\@.+\\.[^\\.]{2;}` |
| **Hyphen** |Busca la coincidencia con un guion. |`\-` |
| **LeftParen** |Busca la coincidencia con un paréntesis izquierdo "(". |`\(` |
| **Letter** |Busca la coincidencia con una letra. |`\p{L}` |
| **MultipleDigits** |Coincide con uno o más dígitos. |`\d+` |
| **MultipleLetters** |Busca la coincidencia con una o varias letras. |`\p{L}+` |
| **MultipleNonSpaces** |Coincide con uno o más caracteres que no agregan espacios en blanco (no hay espacio, tabulación o nueva línea). |`\S+` |
| **MultipleSpaces** |Coincide con uno o varios caracteres que agregan espacios en blanco (espacio, tabulación o nueva línea). |`\s+` |
| **NonSpace** |Busca la coincidencia con un único carácter que no agrega espacios en blanco. |`\S` |
| **OptionalDigits** |Busca la coincidencia con cero, uno o más dígitos. |`\d*` |
| **OptionalLetters** |Busca la coincidencia con cero, una o más letras. |`\p{L}*` |
| **OptionalNonSpaces** |Busca la coincidencia con cero, uno o más caracteres que no agregan espacio en blanco. |`\S*` |
| **OptionalSpaces** |Busca la coincidencia con cero, uno o más caracteres que agregan espacio en blanco. |`\s*` |
| **Period** |Busca la coincidencia con un punto ("."). |`\.` |
| **RightParen** |Busca la coincidencia con un paréntesis derecho ")". |`\)` |
| **Space** |Busca la coincidencia con un carácter que agrega espacio en blanco. |`\s` |

Por ejemplo, el patrón **"A" & MultipleDigits** buscará la coincidencia con la letra "A" seguido de uno o varios dígitos.  

### <a name="regular-expressions"></a>Expresiones regulares
El patrón que usan estas funciones es una [expresión regular](https://en.wikipedia.org/wiki/Regular_expression). Los caracteres ordinarios y los patrones predefinidos que se describen anteriormente en este tema ayudan a crear expresiones regulares.  

Las expresiones regulares son muy eficaces, están disponibles en muchos lenguajes de programación y se usan para multitud de propósitos. También pueden parecerse a menudo como una secuencia aleatoria de signos de puntuación. En este artículo no se describen todos los aspectos de las expresiones regulares, pero hay una gran cantidad de información, tutoriales y herramientas disponibles en la Web.  

Las expresiones regulares se encuentran en distintos dialectos y PowerApps usa una variante del dialecto de JavaScript. Consulte [Sintaxis de expresiones regulares](https://msdn.microsoft.com/library/1400241x.aspx) para obtener una introducción a la sintaxis. Se admiten las subcoincidencias con nombre (que a veces se denominan grupos de captura con nombre):

- Subcoincidencias con nombre: **(?&lt;*nombre*&gt;...)**
- Referencias inversas con nombre: **\\k&lt;*nombre*&gt;**

En la tabla de enumeración **coincidir** anteriormente en este tema, cada enumeración aparece en la misma fila que la expresión regular correspondiente.

## <a name="match-options"></a>Opciones de coincidencia
Para modificar el comportamiento de estas funciones, puede especificar una o varias opciones, que se pueden combinar mediante el operador de concatenación de cadenas ( **&amp;** ).  

| Enumeración MatchOptions | Descripción | Impacto en una expresión regular |
| --- | --- | --- |
| **BeginsWith** |El patrón debe coincidir desde el principio del texto. |Agrega un **^** al principio de la expresión regular. |
| **Complete** |Valor predeterminado para **IsMatch**. El patrón debe coincidir con toda la cadena de texto, de principio a fin. |Agrega un **^** al inicio y una **$** al final de la expresión regular. |
| **Contains** |Valor predeterminado para **Match** y **MatchAll**. El patrón debe aparecer en alguna parte del texto pero no tiene que ser al principio o al final. |No modifica la expresión regular. |
| **EndsWith** |El patrón debe coincidir con el final de la cadena de texto. |Agrega **$** al final de la expresión regular. |
| **IgnoreCase** |Trata las letras mayúsculas y minúsculas como idénticas. De forma predeterminada, la búsqueda de coincidencia distingue mayúsculas y minúsculas. |No modifica la expresión regular. Esta opción es equivalente al modificador "i" estándar de las expresiones regulares.  |
| **Multiline** |Busca la coincidencia entre varias líneas. |No modifica la expresión regular. Esta opción es equivalente al modificador estándar "m" de las expresiones regulares. |

El uso de **MatchAll** es equivalente a usar el modificador estándar "g" para las expresiones regulares.

## <a name="syntax"></a>Sintaxis
**IsMatch**( *Text*; *Pattern* [; *Options* ] )

* *Text*: requerido. La cadena de texto que se va a probar.
* *Pattern*: requerido. Patrón que se va a probar como una cadena de texto. Concatene los patrones predefinidos que define la enumeración **Match** o proporcione una expresión regular. *Pattern* debe ser una fórmula constante sin variables, orígenes de datos u otras referencias dinámicas que cambian a medida que se ejecuta la aplicación.
* *Options*: valor opcional. Una combinación de cadena de texto de valores de enumeración **MatchOptions** . De forma predeterminada, se usa **MatchOptions.Complete**.

**Match**( *texto*; *patrón* [; *Opciones* ])

* *Text*: requerido. Cadena de texto que debe coincidir.
* *Pattern*: requerido. Patrón que debe coincidir como una cadena de texto. Concatene los patrones predefinidos que define la enumeración **Match** o proporcione una expresión regular. *Pattern* debe ser una fórmula constante sin variables, orígenes de datos u otras referencias dinámicas que cambian a medida que se ejecuta la aplicación.
* *Options*: valor opcional. Una combinación de cadena de texto de valores de enumeración **MatchOptions** . De forma predeterminada, se usa **MatchOptions. Contains** .

**MatchAll**( *texto*; *patrón* [; *Opciones* ])

* *Text*: requerido. Cadena de texto que debe coincidir.
* *Pattern*: requerido. Patrón que debe coincidir como una cadena de texto. Concatene los patrones predefinidos que define la enumeración **Match** o proporcione una expresión regular. *Pattern* debe ser una fórmula constante sin variables, orígenes de datos u otras referencias dinámicas que cambian a medida que se ejecuta la aplicación.
* *Options*: valor opcional. Una combinación de cadena de texto de valores de enumeración **MatchOptions** . De forma predeterminada, se usa **MatchOptions. Contains** .

## <a name="ismatch-examples"></a>Ejemplos de IsMatch
### <a name="ordinary-characters"></a>Caracteres normales
Imagine que la aplicación contiene un control **Entrada de texto** denominado **TextInput1**. El usuario escribe valores en este control para almacenarlos en una base de datos.   

El usuario escribe **Hello world** en **TextInput1**.

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| `IsMatch( TextInput1.Text; "Hello world" )` |Comprueba si la entrada del usuario coincide exactamente con la cadena "Hello World". |**true** |
| `IsMatch( TextInput1.Text; "Good bye" )` |Comprueba si la entrada del usuario coincide exactamente con la cadena "Good Bye". |**false** |
| `IsMatch( TextInput1.Text; "hello"; Contains )` |Comprueba si la entrada del usuario contiene la palabra "Hello" (con distinción de mayúsculas y minúsculas). |**false** |
| `IsMatch( TextInput1.Text; "hello"; Contains & IgnoreCase )` |Comprueba si la entrada del usuario contiene la palabra "hello" (con distinción de mayúsculas y minúsculas). |**true** |

### <a name="predefined-patterns"></a>Patrones predefinidos

|                                                            Fórmula                                                            |                                                                Descripción                                                                |  Resultado   |
|-------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| `IsMatch( "123-45-7890"; Digit & Digit & Digit & Hyphen & Digit & Digit & Hyphen & Digit & Digit & Digit & Digit )` |                                              Busca la coincidencia con un número de la Seguridad Social de Estados Unidos.                                               | **true**  |
|                                           `IsMatch( "joan@contoso.com"; Email )`                                            |                                                         Busca la coincidencia con una dirección de correo electrónico.                                                          | **true**  |
|                              `IsMatch( "123.456"; MultipleDigits & Period & OptionalDigits )`                               |                                   Busca la coincidencia con una secuencia de dígitos, un punto y luego cero o más dígitos.                                   | **true**  |
|                                `IsMatch( "123"; MultipleDigits & Period & OptionalDigits )`                                 | Busca la coincidencia con una secuencia de dígitos, un punto y luego cero o más dígitos. No aparece un punto en el texto para que coincida, por lo que no coincide con este patrón. | **false** |

### <a name="regular-expressions"></a>Expresiones regulares

|                                                                              Fórmula                                                                              |                                                                                                                                  Descripción                                                                                                                                   |  Resultado   |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
|                                                                    `IsMatch( "986"; "\d+" )`                                                                   |                                                                                                                    Coincide con un entero mayor que cero.                                                                                                                     | **true**  |
|                                                               `IsMatch( "1.02"; "\d+(\.\d\d)?" )`                                                              |                                        Busca la coincidencia con un importe de divisa positivo. Si la entrada contiene un separador decimal, la entrada también debe contener dos caracteres numéricos después del separador decimal. Por ejemplo, 3,00 es válido, pero no 3,1.                                         | **true**  |
|                                                            `IsMatch( "-4.95"; "(-)?\d+(\.\d\d)?" )`                                                             |                                                        Busca la coincidencia con un importe de divisa negativo. Si la entrada contiene un separador decimal, la entrada también debe contener dos caracteres numéricos después del separador decimal.                                                        | **true**  |
|                                                         `IsMatch( "111-11-1111"; "\d{3}-\d{2}-\d{4}" )`                                                        | Busca la coincidencia con un número de la Seguridad Social de Estados Unidos. Valida el formato, el tipo y la longitud del campo de entrada proporcionado. La cadena que debe coincidir debe constar de tres caracteres numéricos seguidos de un guion, dos caracteres numéricos seguidos de un guión y, a continuación, cuatro caracteres numéricos. | **true**  |
|                                                         `IsMatch( "111-111-111"; "\d{3}-\d{2}-\d{4}" )`                                                         |                                                                                               Lo mismo que el ejemplo anterior, pero uno de los guiones está fuera de lugar en la entrada.                                                                                               | **false** |
|                                         `IsMatch( "AStrongPasswordNot"; "(?!^[0-9]\*$)(?!^[a-zA-Z]\*$)([a-zA-Z0-9]{8,10})" )`                                        |                                        Valida una contraseña segura, que debe contener ocho, nueve o 10 caracteres, además de al menos un dígito y al menos un carácter alfabético. La cadena no debe contener caracteres especiales.                                        | **false** |
| `IsMatch( "<https://microsoft.com>"; "(ht&#124;f)tp(s?)\:\/\/\[0-9a-zA-Z\]([-.\w]\*[0-9a-zA-Z])\*(:(0-9)\*)\*(\/?)([a-zA-Z0-9\-\.\?\,\'\/\\\+&%\$#_]\*)?" )` |                                                                                                                     Valida una dirección URL http, https o ftp.                                                                                                                      | **true**  |

## <a name="match-and-matchall-examples"></a>Ejemplos de Match y MatchAll

| Fórmula | Descripción | Resultado |
|--------|------------|-----------|
| `Match( "Bob Jones <bob.jones@contoso.com>"; "<(?<email>" & Match.Email & ")>"` | Extrae solo la parte de correo electrónico de la información de contacto.  | {<br>correo electrónico:&nbsp;"bob.jones@contoso.com",<br>FullMatch:&nbsp;"&lt;bob.jones@contoso.com>",<br>Subcoincidencias:&nbsp;[&nbsp;"bob.jones@contoso.com"&nbsp;],<br>StartMatch: 11<br>}  
| `Match( "Bob Jones <InvalidEmailAddress>"; "<(?<email>" & Match.Email & ")>"` | Extrae solo la parte de correo electrónico de la información de contacto. No se encuentra ninguna dirección válida (no hay @ Sign), por lo que la función devuelve *Blank*. | *blank* |  
| `Match( Language(); "(<language>\w{2})(?:-(?<script>\w{4}))?(?:-(?<region>\w{2}))?" )` | Extrae las partes de idioma, script y región de la etiqueta de idioma que devuelve la función **[Language](function-language.md)** . Estos resultados reflejan el Estados Unidos; Consulte la documentación de la función de [ **lenguaje** ](function-language.md) para obtener más ejemplos.  El operador **(?:** agrupa los caracteres sin crear otra subcoincidencia. | {<br>lenguaje: "en",<br>script: *en blanco*, <br>región: "EE. UU.",<br>FullMatch: "en-US", <br>Subcoincidencias: ["en", "", "EE. UU."], <br>StartMatch: 1<br>} 
| `Match( "PT2H1M39S"; "PT(?:<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" )` | Extrae las horas, los minutos y los segundos de un valor de duración ISO 8601. Los números extraídos siguen en una cadena de texto; Utilice la función [**Value**](function-value.md) para convertirlo en un número antes de que se realicen operaciones matemáticas en él.  | {<br> horas: "2",<br>minutos: "1",<br>segundos: "39",<br>FullMatch: "PT2H1M39S",<br>Subcoincidencias:&nbsp;[&nbsp;"2",&nbsp;"1",&nbsp;"39"&nbsp;],<br>StartMatch: 1<br>} |

Vamos a profundizar en el último ejemplo. Si desea convertir esta cadena en un valor de fecha y hora mediante la función **[Time](function-date-time.md)** , debe pasar individualmente las coincidencias con nombre. Para ello, puede usar la función **[with](function-with.md)** que funciona en el registro que **coincide con** las devoluciones:

``` powerapps-comma
With( 
    Match( "PT2H1M39S"; "PT(?:(?<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" ); 
    Time( Value( hours ); Value( minutes ); Value( seconds ) )
)
```

En estos ejemplos, agregue un control [botón](../controls/control-button.md) , establezca su propiedad **alseleccionar** en esta fórmula y, a continuación, seleccione el botón:

``` powerapps-comma
Set( pangram; "The quick brown fox jumps over the lazy dog." )
```
 
| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| `Match( pangram; "THE"; IgnoreCase )` | Busque todas las coincidencias de "THE" en la cadena de texto que contiene la variable **pangram** . La cadena contiene dos coincidencias, pero solo se devuelve la primera porque está usando **Match** y not **MatchAll**. La columna submatches está vacía porque no se definió ninguna subcoincidencia.  | {<br>FullMatch: "The",<br>Subcoincidencias: [&nbsp;],<br>StartMatch: 32<br>} |
| `MatchAll( pangram; "the" )` | Busque todas las coincidencias de "The" en la cadena de texto que contiene la variable **pangram** . La prueba distingue entre mayúsculas y minúsculas, por lo que solo se encuentra la segunda instancia de "The". La columna submatches está vacía porque no se definió ninguna subcoincidencia.  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-the-one.png) |
| `MatchAll( pangram; "the"; IgnoreCase )` | Busque todas las coincidencias de "The" en la cadena de texto que contiene la variable **pangram** . En este caso, la prueba no distingue entre mayúsculas y minúsculas, por lo que se encuentran ambas instancias de la palabra. La columna submatches está vacía porque no se definió ninguna subcoincidencia.  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-the-two.png) |
| `MatchAll( pangram; "\b\wo\w\b" )` | Busca todas las palabras de tres letras con una "o" en el centro. Tenga en cuenta que "Brown" se excluye porque no es una palabra de tres letras y, por lo tanto, no coincide con "\b" (límite de palabras).  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-fox-dog.png) |
| `Match( pangram; "\b\wo\w\b\s\*(?<between>\w.+\w)\s\*\b\wo\w\b" )` | Coincide con todos los caracteres entre "Fox" y "Dog". | {<br>entre:&nbsp;"salta&nbsp;sobre&nbsp;el&nbsp;Lazy",<br>FullMatch:&nbsp;"Fox&nbsp;salta&nbsp;sobre&nbsp;el&nbsp;perro diferido&nbsp;",<br>Subcoincidencias: ["salta sobre el Lazy"],<br>StartMatch: 17<br> } |

Para ver los resultados de **MatchAll** en una galería:

1. En una pantalla vacía, inserte un control **[Galería](../controls/control-gallery.md)** vertical en blanco.

2. Establezca la propiedad **Items** de la galería en **MatchAll (pangram, "\w +")** o **MatchAll (pangram, MultipleLetters)** .

    ![](media/function-ismatch/pangram-gallery1.png)

3. Seleccione "agregar un elemento de la pestaña insertar" en el centro del control Galería para seleccionar la plantilla de la galería. 

5. Agregue un control **[etiqueta](../controls/control-text-box.md)** a la plantilla de la galería.  

4. Establezca la propiedad **Text** de la etiqueta en **ThisItem. FullMatch**.  
 
    La galería se rellena con cada palabra en el texto de ejemplo.  Cambie el tamaño de la plantilla de la galería y del control de etiqueta para ver todas las palabras de una pantalla.

    ![](media/function-ismatch/pangram-gallery2.png)
