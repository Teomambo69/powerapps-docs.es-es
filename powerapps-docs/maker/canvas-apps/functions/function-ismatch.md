---
title: Funciones IsMatch, Match y MatchAll | Microsoft Docs
description: Información de referencia, incluida la sintaxis de las funciones IsMatch, Match y MatchAll en PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/15/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7141d3b9a2ba6bf18bffe1756d0d7de048606cad
ms.sourcegitcommit: f5013108140276b3d66a9dce13a061df89609d26
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "57798384"
---
# <a name="ismatch-match-and-matchall-functions-in-powerapps"></a>Funciones IsMatch, Match y MatchAll en PowerApps
Comprueba si una coincidencia o extrae las partes de una cadena de texto según un patrón.

## <a name="description"></a>Descripción
La función **IsMatch** comprueba si una cadena de texto coincide con un patrón que puede incluir caracteres normales, patrones predefinidos o una [expresión regular](#regular-expressions).  El **coincidencia** y **MatchAll** funciones devuelven lo coincidió, incluidos los subelementos coincidentes.  

Use **IsMatch** para validar que un usuario ha escrito en un control **[Entrada de texto](../controls/control-text-input.md)**. Por ejemplo, puede confirmar si el usuario ha escrito una dirección de correo electrónico válida antes de que el resultado se guarde en el origen de datos. Si la entrada no coincide con los criterios, agregue otros controles que pidan al usuario que corrija la entrada.

Use **coincide con** para extraer la primera cadena de texto que coincide con un patrón y **MatchAll** para extraer todas las cadenas de texto que coinciden. También puede extraer subelementos coincidentes para analizar cadenas complejas.   

**Coincide con** devuelve un registro de información para la primera coincidencia encontrada, y **MatchAll** devuelve una tabla de registros por cada coincidencia encontrada. El registro o registros contienen:

| Columna | Tipo | Descripción |
|----|----|----|
| *denominado sub&#8209;coinciden o sub&#8209;coincide con* | Text | Cada coincidencia de subdirectorio con nombre tendrá su propia columna. Crear una coincidencia de subdirectorio con nombre mediante **(?&lt; *nombre*&gt;**... **)** en la expresión regular. Si una coincidencia de subdirectorio con nombre tiene el mismo nombre que una de las columnas predefinidas (a continuación), la coincidencia subcarpetas tiene prioridad y se genera una advertencia. Para evitar esta advertencia, cambie el nombre de la coincidencia de subcarpetas. |
| **FullMatch** | Text | Todo el texto que ha coincidido con la cadena. |
| **StartMatch** | Número | La posición inicial de la coincidencia en la cadena de texto de entrada. El primer carácter de la cadena devuelve 1. | 
| **SubMatches** | Tabla de una columna de texto (columna **valor**) | La tabla de subelementos coincidentes con nombre y sin nombre en el orden en que aparecen en la expresión regular. Por lo general, subelementos coincidentes con nombre son más fáciles de trabajar con y se anima. Use la [ **ForAll** ](function-forall.md) función o [ **última**](function-first-last.md)( [ **FirstN**](function-first-last.md)() **...**  )) funciones para trabajar con una coincidencia secundarios individual. Si ninguna coincidencia secundarias se define en la expresión regular, esta tabla estará presente pero vacío. |

Estas funciones admiten [ **MatchOptions**](#match-options). De forma predeterminada: 
- Estas funciones realizan a una coincidencia entre mayúsculas y minúsculas. Use **IgnoreCase** a realizar coincidencias de mayúsculas y minúsculas.    
- **IsMatch** coincide con la cadena de texto completo (**completar** MatchOption), mientras que **coinciden** y **MatchAll** buscar una coincidencia en cualquier parte de la cadena de texto ( **Contiene** MatchOption). Use **completar**, **Contains**, **BeginsWith**, o **EndsWith** según corresponda para su escenario.

**IsMatch** devuelve *true* si la cadena de texto coincide con el patrón o *false* si no es así. **Coincide con** devuelve *en blanco* si se encuentra ninguna coincidencia que se pueden probar con el [ **IsBlank** ](function-isblank-isempty.md) función. **MatchAll** devuelve una tabla vacía si se encuentra ninguna coincidencia que se pueden probar con el [ **IsEmpty** ](function-isblank-isempty.md) función.

Si usas **MatchAll** para dividir una cadena de texto, considere el uso de la **[división](function-split.md)** función, que es más fácil de usar y más rápido.

## <a name="patterns"></a>Patrones
La clave para usar estas funciones es describir el patrón de coincidencia. El patrón en una cadena de texto se describe como una combinación de:

* Caracteres normales, como **"abc"** o **"123"**.
* Patrones predefinidos, como **Letter**, **MultipleDigits** o **Email**. (La enumeración **Match** define estos patrones).
* Códigos de expresiones regulares, como **"\d+\s+\d+"** o **"[a-z] +"**.

Combine estos elementos mediante el uso de la [operador de concatenación de cadenas **&** ](operators.md). Por ejemplo, **"abc" & Digit & "\s+"** es un patrón válido que busca la coincidencia de los caracteres "a", "b" y "c", seguido de un dígito del 0 al 9, seguido de al menos un carácter de espacio en blanco.

### <a name="ordinary-characters"></a>Caracteres normales
El patrón más sencillo es una secuencia de caracteres normales que deben coincidir exactamente.

Por ejemplo, cuando se usa con el **IsMatch** función, la cadena "Hello" coincide con el patrón **"Hello"** exactamente. Ni más ni menos. La cadena "hello!" no coincide con el patrón a causa de exclamación en el extremo y dado que el caso es incorrecto para la letra "h". (Consulte [MatchOptions](#match-options) para ver formas de modificar este comportamiento).

En el lenguaje del patrón, algunos caracteres están reservados para fines especiales. Para utilizar estos caracteres, delante del carácter con un **\\** (barra diagonal inversa) para indicar que el carácter se debe tomar literalmente o utilice uno de los patrones predefinidos que se describe más adelante en este tema. En esta tabla se enumeran los caracteres especiales:

| Carácter especial | Descripción |
| --- | --- |
| **.** |punto |
| **?** |signo de interrogación |
| **&#42;** |asterisco |
| **\+** |signo más |
| **( )** |Paréntesis |
| **[ ]** |corchetes |
| **{ }** |llaves |
| **^** |símbolo de intercalación |
| **$** |signo de dólar |
| **\|** |barra vertical |
| **\\** |barra diagonal inversa |

Por ejemplo, puede buscar la coincidencia de "Hello?" mediante el patrón **"Hello\\?"** con una barra diagonal delante del signo de interrogación.

### <a name="predefined-patterns"></a>Patrones predefinidos
Patrones predefinidos proporcionan una manera sencilla para que coincida con uno de un juego de caracteres o una secuencia de varios caracteres. Use la [operador de concatenación de cadenas **&** ](operators.md) para combinar sus propias cadenas de texto con los miembros de la **coincidencia** enum:

| Enumeración de coincidencia | Descripción | Expresión regular |
| --- | --- | --- |
| **Any** |Busca la coincidencia con cualquier carácter. |`.` |
| **Comma** |Busca la coincidencia con una coma. |`,` |
| **Digit** |Busca la coincidencia con un único dígito (del "0" al "9"). |`\d` |
| **Email** |Busca la coincidencia con una dirección de correo electrónico que contiene un símbolo "arroba" ("\@") y un nombre de dominio que contiene un punto (".") |`.+\@.+\\.[^\\.]{2,}` |
| **Hyphen** |Busca la coincidencia con un guion. |`\-` |
| **LeftParen** |Busca la coincidencia con un paréntesis izquierdo "(". |`\(` |
| **Letter** |Busca la coincidencia con una letra. |`\p{L}` |
| **MultipleDigits** |Coincide con uno o más dígitos. |`\d+` |
| **MultipleLetters** |Busca la coincidencia con una o varias letras. |`\p{L}+` |
| **MultipleNonSpaces** |Coincide con uno o varios caracteres que no agregan espacios en blanco (no espacio, pestaña o nueva línea). |`\S+` |
| **MultipleSpaces** |Coincide con uno o varios caracteres que agregan espacio en blanco (espacio, la ficha o nueva línea). |`\s+` |
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
El patrón que usan estas funciones es un [expresión regular](https://en.wikipedia.org/wiki/Regular_expression). Los caracteres normales y los patrones predefinidos que se describieron anteriormente en esta Ayuda tema crean expresiones regulares.  

Las expresiones regulares son muy eficaces, están disponibles en muchos lenguajes de programación y se usan para multitud de propósitos. También suelen puede consultar como una secuencia aleatoria de signos de puntuación. En este artículo no describe todos los aspectos de las expresiones regulares, pero una gran cantidad de información, tutoriales, y las herramientas están disponibles en la web.  

Las expresiones regulares tienen distintos dialectos y PowerApps emplea una variante del dialecto JavaScript. Consulte [sintaxis de expresiones regulares](http://msdn.microsoft.com/library/1400241x.aspx) para obtener una introducción a la sintaxis. Se admiten las coincidencias de subdirectorio con nombre (a veces denominadas grupos de captura con nombre):

- Denominado subelementos coincidentes: **(?&lt; *nombre* &gt; ...)**
- Con el nombre de las referencias inversas:  **\\k&lt;*nombre*&gt;**

En el **coincidencia** enum tabla anteriormente en este tema, cada enumeración aparece en la misma fila que la expresión regular correspondiente.

## <a name="match-options"></a>Opciones de coincidencia
Puede modificar el comportamiento de estas funciones mediante la especificación de una o más opciones, que se pueden combinar mediante el operador de concatenación de cadenas (**&amp;**).  

| Enumeración MatchOptions | Descripción | Impacto en una expresión regular |
| --- | --- | --- |
| **BeginsWith** |El patrón debe coincidir desde el principio del texto. |Agrega un **^** al principio de la expresión regular. |
| **Complete** |El valor predeterminado para **IsMatch**. El patrón debe coincidir con toda la cadena de texto, de principio a fin. |Agrega un **^** al principio y un **$** al final de la expresión regular. |
| **Contains** |El valor predeterminado para **coincidencia** y **MatchAll**. El patrón debe aparecer en alguna parte del texto pero no tiene que ser al principio o al final. |No modifica la expresión regular. |
| **EndsWith** |El patrón debe coincidir con el final de la cadena de texto. |Agrega **$** al final de la expresión regular. |
| **IgnoreCase** |Trata de mayúsculas y minúsculas porque son idénticos. De forma predeterminada, la búsqueda de coincidencia distingue mayúsculas y minúsculas. |No modifica la expresión regular. Esta opción es el equivalente del modificador estándar "i" para las expresiones regulares de.  |
| **Multiline** |Busca la coincidencia entre varias líneas. |No modifica la expresión regular. Esta opción es el equivalente del modificador estándar "m" para las expresiones regulares de. |

Uso de **MatchAll** equivale a usar el modificador estándar "g" para las expresiones regulares.

## <a name="syntax"></a>Sintaxis
**IsMatch**( *Text*, *Pattern* [, *Options* ] )

* *Text*: requerido. La cadena de texto que se va a probar.
* *Pattern*: requerido. El modelo de prueba como una cadena de texto. Concatene los patrones predefinidos que la **coincidencia** define enum, o proporcionar una expresión regular. *Patrón* debe ser una constante fórmula sin las variables, los orígenes de datos u otro dinámico hace referencia a ese cambio cuando se ejecuta la aplicación.
* *Options*: valor opcional. Una combinación de cadenas de texto **MatchOptions** los valores de enumeración. De forma predeterminada, se usa **MatchOptions.Complete**.

**Coincidencia**( *texto*, *patrón* [, *opciones* ])

* *Text*: requerido. Para que coincida con la cadena de texto.
* *Pattern*: requerido. El patrón de coincidencia como una cadena de texto. Concatene los patrones predefinidos que la **coincidencia** define enum, o proporcionar una expresión regular. *Patrón* debe ser una constante fórmula sin las variables, los orígenes de datos u otro dinámico hace referencia a ese cambio cuando se ejecuta la aplicación.
* *Options*: valor opcional. Una combinación de cadenas de texto **MatchOptions** los valores de enumeración. De forma predeterminada, **MatchOptions.Contains** se utiliza.

**MatchAll**( *texto*, *patrón* [, *opciones* ])

* *Text*: requerido. Para que coincida con la cadena de texto.
* *Pattern*: requerido. El patrón de coincidencia como una cadena de texto. Concatene los patrones predefinidos que la **coincidencia** define enum, o proporcionar una expresión regular. *Patrón* debe ser una constante fórmula sin las variables, los orígenes de datos u otro dinámico hace referencia a ese cambio cuando se ejecuta la aplicación.
* *Options*: valor opcional. Una combinación de cadenas de texto **MatchOptions** los valores de enumeración. De forma predeterminada, **MatchOptions.Contains** se utiliza.

## <a name="ismatch-examples"></a>IsMatch ejemplos
### <a name="ordinary-characters"></a>Caracteres normales
Imagine que la aplicación contiene un control **Entrada de texto** denominado **TextInput1**. El usuario escribe valores en este control para almacenarlos en una base de datos.   

El usuario escribe **Hello world** en **TextInput1**.

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| `IsMatch( TextInput1.Text, "Hello world" )` |Las pruebas si la entrada del usuario coincide exactamente, la cadena "Hello world". |**true** |
| `IsMatch( TextInput1.Text, "Good bye" )` |Las pruebas si la entrada del usuario coincide exactamente, la cadena "Good bye". |**false** |
| `IsMatch( TextInput1.Text, "hello", Contains )` |Comprueba si la entrada del usuario contiene la palabra "hello" (distingue mayúsculas de minúsculas). |**false** |
| `IsMatch( TextInput1.Text, "hello", Contains & IgnoreCase )` |Comprueba si la entrada del usuario contiene la palabra "hello" (con distinción de mayúsculas y minúsculas). |**true** |

### <a name="predefined-patterns"></a>Patrones predefinidos

|                                                            Fórmula                                                            |                                                                Descripción                                                                |  Resultado   |
|-------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| `IsMatch( "123-45-7890", Digit & Digit & Digit & Hyphen & Digit & Digit & Hyphen & Digit & Digit & Digit & Digit )` |                                              Busca la coincidencia con un número de la Seguridad Social de Estados Unidos.                                               | **true**  |
|                                           `IsMatch( "joan@contoso.com", Email )`                                            |                                                         Busca la coincidencia con una dirección de correo electrónico.                                                          | **true**  |
|                              `IsMatch( "123.456", MultipleDigits & Period & OptionalDigits )`                               |                                   Busca la coincidencia con una secuencia de dígitos, un punto y luego cero o más dígitos.                                   | **true**  |
|                                `IsMatch( "123", MultipleDigits & Period & OptionalDigits )`                                 | Busca la coincidencia con una secuencia de dígitos, un punto y luego cero o más dígitos. Un punto no aparece en el texto para que coincida, por lo que no hay coincidencia con este patrón. | **false** |

### <a name="regular-expressions"></a>Expresiones regulares

|                                                                              Fórmula                                                                              |                                                                                                                                  Descripción                                                                                                                                   |  Resultado   |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
|                                                                    `IsMatch( "986", "\d+" )`                                                                   |                                                                                                                    Coincide con un número entero mayor que cero.                                                                                                                     | **true**  |
|                                                               `IsMatch( "1.02", "\d+(\.\d\d)?" )`                                                              |                                        Busca la coincidencia con un importe de divisa positivo. Si la entrada contiene un separador decimal, la entrada también debe contener dos caracteres numéricos después del separador decimal. Por ejemplo, 3,00 es válido, pero no 3,1.                                         | **true**  |
|                                                            `IsMatch( "-4.95", "(-)?\d+(\.\d\d)?" )`                                                             |                                                        Busca la coincidencia con un importe de divisa negativo. Si la entrada contiene un separador decimal, la entrada también debe contener dos caracteres numéricos después del separador decimal.                                                        | **true**  |
|                                                         `IsMatch( "111-11-1111", "\d{3}-\d{2}-\d{4}" )`                                                        | Busca la coincidencia con un número de la Seguridad Social de Estados Unidos. Valida el formato, el tipo y la longitud del campo de entrada proporcionado. Cadena con la que debe constar de tres caracteres numéricos seguidos de un guión, dos caracteres numéricos seguidos por un guión y, a continuación, cuatro caracteres numéricos. | **true**  |
|                                                         `IsMatch( "111-111-111", "\d{3}-\d{2}-\d{4}" )`                                                         |                                                                                               Lo mismo que el ejemplo anterior, pero uno de los guiones está fuera de lugar en la entrada.                                                                                               | **false** |
|                                         `IsMatch( "AStrongPasswordNot", "(?!^[0-9]\*$)(?!^[a-zA-Z]\*$)([a-zA-Z0-9]{8,10})" )`                                        |                                        Valida una contraseña segura, que debe contener ocho, 9 o 10 caracteres, además de al menos un dígito y al menos un carácter alfabético. La cadena no debe contener caracteres especiales.                                        | **false** |
| `IsMatch( "<http://microsoft.com>", "(ht&#124;f)tp(s?)\:\/\/\[0-9a-zA-Z\]([-.\w]\*[0-9a-zA-Z])\*(:(0-9)\*)\*(\/?)([a-zA-Z0-9\-\.\?\,\'\/\\\+&%\$#_]\*)?" )` |                                                                                                                     Valida una dirección URL http, https o ftp.                                                                                                                      | **true**  |

## <a name="match-and-matchall-examples"></a>Ejemplos de coincidencia y MatchAll

| Fórmula | Descripción | Resultado |
|--------|------------|-----------|
| `Match( "Bob Jones <bob.jones@contoso.com>", "<(?<email>" & Match.Email & ")>"` | Extrae solo la parte de correo electrónico de la información de contacto.  | {<br>correo electrónico:&nbsp;"bob.jones@contoso.com",<br>FullMatch:&nbsp;"&lt;bob.jones@contoso.com>",<br>Subcoincidencias:&nbsp;[&nbsp;"bob.jones@contoso.com"&nbsp;],<br>StartMatch: 11<br>}  
| `Match( "Bob Jones <InvalidEmailAddress>", "<(?<email>" & Match.Email & ")>"` | Extrae solo la parte de correo electrónico de la información de contacto. No se encuentra ninguna dirección legal (hay no signo @), por lo que la función devuelve *en blanco*. | *blank* |  
| `Match( Language(), "(<language>\w{2})(?:-(?<script>\w{4}))?(?:-(?<region>\w{2}))?" )` | Extrae las partes de idioma, script y región del lenguaje que etiqueta el **[lenguaje](function-language.md)** función devuelve. Estos resultados reflejan los Estados Unidos. Consulte la [ **lenguaje** documentación sobre la función](function-language.md) para obtener más ejemplos.  El **(?:** operador grupos de caracteres sin crear otra coincidencia secundarias. | {<br>idioma: "es-es",<br>secuencia de comandos: *en blanco*, <br>Región: "NOSOTROS",<br>FullMatch: "en-US", <br>Subcoincidencias: ["es-es", "", "US"], <br>StartMatch: 1<br>} 
| `Match( "PT2H1M39S", "PT(?:(<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" )` | Extrae las horas, minutos y segundos de un valor de duración ISO 8601. Los números extraídos aún están en una cadena de texto; Utilice la [ **valor** ](function-value.md) función para convertirlo en un número antes de que se realizan operaciones matemáticas en él.  | {<br> horas: "2",<br>minutos: "1",<br>segundos: "39",<br>FullMatch: "PT2H1M39S",<br>Subcoincidencias:&nbsp;[&nbsp;"2",&nbsp;"1",&nbsp;"será 39"&nbsp;],<br>StartMatch: 1<br>} |

Vamos a profundizar en ese último ejemplo. Si desea convertir esta cadena en un valor de fecha y hora mediante el **[tiempo](function-date-time.md)** función, debe pasar en las coincidencias de subdirectorio con nombre individualmente. Para ello, puede usar el **[ForAll](function-forall.md)** función operan en el primer registro que **MatchAll** devuelve:

``` powerapps-dot
First( 
    ForAll( 
        MatchAll( "PT2H1M39S", "PT(?:(?<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" ), 
        Time( Value( hours ), Value( minutes ), Value( seconds ) )
    )
).Value
```

Para estos ejemplos, agregue un [botón](../controls/control-button.md) , establezca su **OnSelect** propiedad a esta fórmula y, a continuación, seleccione el botón:

``` powerapps-dot
Set( pangram, "The quick brown fox jumps over the lazy dog." )
```
 
| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| `Match( pangram, "THE", IgnoreCase )` | Buscar todas las coincidencias de "THE" en el texto de cadena que el **pangram** contiene la variable. La cadena contiene dos coincidencias, pero no se devuelve solo la primera porque usa **coincidencia** y no **MatchAll**. La columna de subcoincidencias está vacía porque se han definido ninguna coincidencia secundarias.  | {<br>FullMatch: "The",<br>Subcoincidencias: [&nbsp;],<br>StartMatch: 32<br>} |
| `MatchAll( pangram, "the" )` | Buscar todas las coincidencias de "the" en la cadena de texto que el **pangram** contiene la variable. La prueba distingue mayúsculas de minúsculas, por lo que solo que se encuentra la segunda instancia de "the". La columna de subcoincidencias está vacía porque se han definido ninguna coincidencia secundarias.  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-the-one.png) |
| `MatchAll( pangram, "the", IgnoreCase )` | Buscar todas las coincidencias de "the" en la cadena de texto que el **pangram** contiene la variable. En este caso, la prueba es distingue entre mayúsculas y minúsculas, por lo que se encuentran las dos instancias de la palabra. La columna de subcoincidencias está vacía porque se han definido ninguna coincidencia secundarias.  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-the-two.png) |
| `MatchAll( pangram, "\b\wo\w\b" )` | Busca todas las palabras de tres letras con una "o" en la parte central. Tenga en cuenta que "brown" se excluyó porque no es una palabra de tres letras y, por lo tanto, no coincide con "\b" (límite de palabras).  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-fox-dog.png) |
| `Match( pangram, "\b\wo\w\b\s\*(?<between>\w.+\w)\s\*\b\wo\w\b" )` | Coincide con todos los caracteres entre "zorro" y "dog". | {<br>entre:&nbsp;"salta&nbsp;sobre&nbsp;el&nbsp;diferida",<br>FullMatch:&nbsp;"fox&nbsp;salta&nbsp;sobre&nbsp;el&nbsp;diferida&nbsp;perro",<br>Subcoincidencias: ["salta la diferida"],<br>StartMatch: 17<br> } |

Para ver los resultados de **MatchAll** en una galería:

1. En una pantalla vacía, inserte un valor en blanco vertical **[galería](../controls/control-gallery.md)** control.

2. La galería **elementos** propiedad **MatchAll (pangram, "\w+")** o **MatchAll (pangram, MultipleLetters)**.

    ![](media/function-ismatch/pangram-gallery1.png)

3. Seleccione "Agregar un elemento desde la pestaña Insertar" en el centro del control de galería para seleccionar la plantilla de la galería. 

5. Agregar un **[etiqueta](../controls/control-text-box.md)** control a la plantilla de la galería.  

4. Establezca la etiqueta **texto** propiedad **ThisItem.FullMatch**.  
 
    La galería se rellena con cada palabra en el texto de ejemplo.  Cambiar el tamaño de plantilla de la galería y el control de etiqueta para ver todas las palabras en una pantalla.

    ![](media/function-ismatch/pangram-gallery2.png)
