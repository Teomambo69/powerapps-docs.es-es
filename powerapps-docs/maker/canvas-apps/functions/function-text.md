---
title: Función Texto | Microsoft Docs
description: Información de referencia para la función Text en PowerApps, incluidos ejemplos y sintaxis
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 10/25/2016
ms.author: gregli
ms.openlocfilehash: fece9b928cdbfa955ada994e4cdd637eea3f7ac8
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37899718"
---
# <a name="text-function-in-powerapps"></a>Función Text en PowerApps
Da formato a un número o un valor de fecha y hora para mostrar como una cadena de texto.

## <a name="description"></a>Descripción
La función **Text** da formato a un número o a un valor de fecha y hora según uno de estos tipos de argumentos:

* Un formato predefinido de fecha y hora que especifica a través de la enumeración **DateTimeFormat**.  En el caso de fechas y horas, se prefiere este enfoque porque se ajusta automáticamente al idioma y la ubicación de cada usuario.
* Un formato personalizado, una cadena de texto que incluye marcadores de posición que describen cómo dar formato al número o al valor de fecha y hora. Los marcadores de posición definen cuántos dígitos se deben mostrar, si se deben usar separadores de agrupación y cómo mostrar el nombre de un mes. PowerApps admite un subconjunto de los marcadores de posición que admite Microsoft Excel.

Consulte [cómo trabajar con fechas y horas](../show-text-dates-times.md) para más información.

### <a name="predefined-datetime-formats"></a> Formatos predefinidos de fecha y hora

| Formato predefinido | Descripción |
| --- | --- |
| **DateTimeFormat.LongDate** |Año completo, mes, día del mes y día de la semana. Los nombres del mes y del día de la semana no se abrevian. |
| **DateTimeFormat.LongDateTime** |Año completo, mes, día del mes y día de la semana, además de la hora (reloj de 12 horas), minutos, segundos y designación a.m y p.m. Los nombres del mes y del día de la semana no se abrevian. |
| **DateTimeFormat.LongDateTime24** |Año completo, mes, día del mes y día de la semana, además de la hora (reloj de 24 horas), minutos y segundos. Los nombres del mes y del día de la semana no se abrevian. |
| **DateTimeFormat.LongTime** |Hora (reloj de 12 horas), minutos, segundos y designación a.m. y p.m. Igual que ShortTime. |
| **DateTimeFormat.LongTime24** |Hora (reloj de 24 horas), minutos y segundos. Igual que ShortTime24. |
| **DateTimeFormat.ShortDate** |Año de cuatro dígitos con mes de dos dígitos y día de la semana. |
| **DateTimeFormat.ShortDateTime** |Año de cuatro dígitos con mes de dos dígitos y día de la semana, además de la hora (reloj de 12 horas), minutos, segundos y designación a.m. y p.m. |
| **DateTimeFormat.ShortDateTime24** |Año de cuatro dígitos con mes de dos dígitos y día de la semana, además de la hora (reloj de 24 horas), minutos y segundos. |
| **DateTimeFormat.ShortTime** |Hora (reloj de 12 horas), minutos, segundos y designación a.m. y p.m.  Igual que LongTime. |
| **DateTimeFormat.ShortTime24** |Hora (reloj de 24 horas), minutos y segundos.  Igual que LongTime24. |
| **DateTimeFormat.UTC** |El valor de fecha y hora se convierte en UTC según la zona horaria del usuario actual y usa un formato basado en el estándar ISO 8601. |

### <a name="number-placeholders"></a>Marcadores de posición de número

| Marcador de posición | Descripción |
| --- | --- |
| **0** (*cero*) |Muestra ceros no significativos si un número tiene menos dígitos que ceros en el formato. Por ejemplo, use el formato **#.00** si desea mostrar **8.9** como **8.90**. |
| **#** |Sigue las mismas reglas que **0** (cero). Sin embargo, **Text** no muestra ceros adicionales cuando el número tiene menos dígitos en cualquier lado del decimal que símbolos # en el formato. Por ejemplo, se muestra **8.9** si el formato personalizado es **#.##** y el número al que debe darse formato es **8.9**. |
| **.** (*punto*) |Muestra el punto decimal de un número.  Depende del idioma del formato personalizado; consulte las [aplicaciones globales](#global-apps) para más detalles. |
| **,** (*coma*) |Muestra el separador de agrupación de un número; a menudo, se usa para los miles. **Text** separa los grupos con comas si el formato contiene una coma encerrada entre signos numéricos (**#**) o ceros.  Depende del idioma del formato personalizado; consulte las [aplicaciones globales](#global-apps) para más detalles. |

Si un número tiene más dígitos a la derecha del separador decimal que marcadores de posición en el formato, el número se redondea a tantas cifras decimales como marcadores de posición existen. Si hay más dígitos a la izquierda del separador decimal que marcadores de posición, se muestran los dígitos adicionales. Si el formato solo consta de signos numéricos (#) a la izquierda del separador decimal, los números menores que 1 comienzan con un separador decimal (por ejemplo **.47**).

### <a name="date-and-time-placeholders"></a>Marcadores de posición de fecha y hora

|                                                                                                 Marcador de posición                                                                                                  |                                                                                                     Descripción                                                                                                     |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                                    **m**                                                                                                     |                                                                               Muestra el mes como número sin cero inicial.                                                                                |
|                                                                                                    **mm**                                                                                                    |                                                                        Muestra el mes como número con cero inicial cuando corresponda.                                                                         |
|                                                                                                   **mmm**                                                                                                    |                                                                             Muestra el mes abreviado (**Ene** a **Dic**).                                                                             |
|                                                                                                   **mmmm**                                                                                                   |                                                                          Muestra el nombre completo del mes (**Enero** a **Diciembre**).                                                                           |
|                                                                                                    **d**                                                                                                     |                                                                                Muestra el día como número sin cero inicial.                                                                                 |
|                                                                                                    **dd**                                                                                                    |                                                                         Muestra el día como número con cero inicial cuando corresponda.                                                                          |
|                                                                                                   **ddd**                                                                                                    |                                                                              Muestra el día abreviado (**Dom** a **Sáb**).                                                                              |
|                                                                                                   **dddd**                                                                                                   |                                                                            Muestra el nombre completo del día (**Domingo** a **Sábado**).                                                                            |
|                                                                                                    **yy**                                                                                                    |                                                                                      Muestra el año como número de dos dígitos.                                                                                       |
|                                                                                                   **yyyy**                                                                                                   |                                                                                      Muestra el año como número de cuatro dígitos.                                                                                      |
|                                                                                                    **h**                                                                                                     |                                                                                Muestra la hora como número sin cero inicial.                                                                                |
|                                                                                                    **hh**                                                                                                    | Muestra la hora como número con cero inicial cuando corresponda. Si el formato contiene **AM** o **PM**, la hora se muestra según el reloj de 12 horas. De lo contrario, la hora se muestra según el reloj de 24 horas. |
|                                                                                                    **m**                                                                                                     |                                                                         Muestra el minuto como número sin cero inicial.  > [!NOTE]                                                                          |
|            > El código **m** o **mm** debe aparecer inmediatamente después del código **h** o **hh** o inmediatamente antes del código **ss**; de lo contrario, **Text** muestra el mes en lugar de los minutos.            |                                                                                                                                                                                                                     |
|                                                                                                    **mm**                                                                                                    |                                                                   Muestra el minuto como número con cero inicial cuando corresponda. > [!NOTE]                                                                   |
| > El marcador de posición **m** o **mm** debe aparecer inmediatamente después del marcador de posición **h** o **hh** o inmediatamente antes del marcador de posición **ss**. De lo contrario, **Text** muestra el mes en lugar de los minutos. |                                                                                                                                                                                                                     |
|                                                                                                    **s**                                                                                                     |                                                                               Muestra el segundo como número sin cero inicial.                                                                               |
|                                                                                                    **ss**                                                                                                    |                                                                        Muestra el segundo como número con cero inicial cuando corresponda.                                                                        |
|                                                                                                    **f**                                                                                                     |                                                                                         Muestra las fracciones de segundos.                                                                                          |
|                                                                                    **AM/PM**, **am/pm**, **A/P**, **a/p**                                                                                    |               Muestra la hora según un reloj de 12 horas. **Text** muestra "AM", "am", "A" o "a" para las horas que van entre la medianoche hasta el mediodía y "PM", "pm", "P" o "p" para las horas que van desde el mediodía hasta la medianoche.                |

### <a name="literal-placeholders"></a>Marcadores de posición literales
Puede incluir cualquiera de estos caracteres en su cadena de formato.  Aparecerán en el resultado de **Text** tal cual. Los caracteres adicionales están reservados para marcadores de posición futuros, por lo que no debe usarlos.

| Carácter | Descripción |
| --- | --- |
| Cualquier símbolo de moneda |Signo de dólar, signo de centavo, signo de euro, etc. |
| **+** |Signo más |
| **(** |Paréntesis de apertura |
| **:** |Dos puntos |
| **^** |Acento circunflejo (símbolo de intercalación) |
| **'** |Apóstrofo |
| **{** |Llave de apertura |
| **<** |Signo de menor que |
| **=** |Signo igual |
| **-** |Signo menos |
| **/** |Barra diagonal |
| **)** |Paréntesis de cierre |
| **&** |Y comercial |
| **~** |Tilde de la ñ |
| **}** |Llave de cierre |
| **>** |Signo de mayor que |
| &nbsp; |Carácter de espacio |

## <a name="global-apps"></a>Aplicaciones globales
La función **Text** es globalmente compatible.  Para una amplia variedad de idiomas, sabe cómo escribir correctamente fechas, horas, monedas y números.  Para ello, necesita dos tipos de información:

* **El idioma del formato personalizado:** para los autores, ¿cómo se debe interpretar un formato personalizado?  Los caracteres separadores (**.** y **,**) tienen significados distintos en diferentes idiomas.  Esto se controla con un marcador de posición especial que incluye una etiqueta de idioma.  Incluso más sencillo, los [formatos predefinidos de fecha y hora](#predefined-datetime-formats) son independientes del idioma.
* **El idioma del resultado:** para los usuarios, ¿qué idioma se debe usar en el resultado de la función?  Los nombres de los meses y días de la semana deben estar en el idioma correspondiente al usuario de la aplicación.  Esto se controla con un tercer argumento opcional de la función **Text**. 

En ambos casos, el idioma se proporciona con una [etiqueta de idioma](function-language.md#language-tags).  Para ver la lista de idiomas compatibles, escriba **Text( 1234, "", )** en la barra de fórmulas o en la vista avanzada y desplácese por la lista de configuraciones regionales sugeridas para el tercer argumento.

#### <a name="custom-format-language-placeholder"></a>Marcador de posición de formato personalizado
Para especificar el idioma del formato personalizado, use:

| Marcador de posición | Descripción |
| --- | --- |
| **[$-*LanguageTag*]** |*LanguageTag* es una etiqueta de idioma que la función **Language** muestra.  Puede tener el formato del idioma, como **[$-en]** para inglés, o también puede incluir la región, como **[$-en-GB]** para especificar, además, Gran Bretaña. |

El marcador de posición de idioma puede aparecer en cualquier parte del formato personalizado, pero solo una vez.

Cuando escriba una fórmula, si no proporciona un marcador de posición de idioma y la cadena de formato es ambigua en términos globales, la herramienta de creación insertará automáticamente la etiqueta de idioma correspondiente al idioma actual.  

**[$-en-US]** es el valor que se presume si este marcador de posición no está presente cuando se ejecuta la aplicación. 

> [!NOTE]
> En una versión futura, la sintaxis de este marcador de posición puede cambiar para evitar que se confunda con un marcador de posición similar, pero distinto, compatible con Excel.

#### <a name="result-language-tag"></a>Etiqueta de idioma del resultado
En el resultado de la función **Text** aparecen cadenas traducidas para mes, día de la semana y designaciones a.m. o p.m., además de separadores decimales y grupo adecuados.

De manera predeterminada, la función **Text** usa el idioma del usuario que ejecuta la aplicación.  La función **Language** muestra la etiqueta de idioma correspondiente al usuario actual.  Puede reemplazar este valor predeterminado si suministra una etiqueta de idioma para el tercer argumento opcional de **Text**.

## <a name="syntax"></a>Sintaxis
**Text**( *Number*, *DateTimeFormatEnum* [, *ResultLanguageTag* ] )

* *Number*: requerido. El número o el valor de fecha y hora al que se dará formato.
* *DateTimeFormat*: requerido.  Miembro de la enumeración **DateTimeFormat**.
* *ResultLanguageTag*: opcional.  La etiqueta de idioma que se usará para el texto de resultado.  De manera predeterminada, se usa el idioma del usuario actual.

**Text**( *Number*, *CustomFormat* [, *ResultLanguageTag* ] )

* *Number*: requerido. El número o el valor de fecha y hora al que se dará formato.
* *CustomFormat*: requerido. Uno o más marcadores de posición entre comillas dobles.
* *ResultLanguageTag*: opcional.  La etiqueta de idioma que se usará para el texto de resultado.  De manera predeterminada, se usa el idioma del usuario actual.

## <a name="examples"></a>Ejemplos
El usuario que ejecuta estas fórmulas se encuentra en Estados Unidos y seleccionó inglés como idioma.  La función **Language** muestra "en-US".

### <a name="number"></a>Número

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Text(&nbsp;1234.59,&nbsp;"####.#"&nbsp;)** |Da formato al número con un decimal. |"1234.6" |
| **Text(&nbsp;8.9,&nbsp;"#.000"&nbsp;)** |Rellena la parte decimal del número con ceros finales, si es necesario. |"8.900" |
| **Text(&nbsp;0.631,&nbsp;"0.#"&nbsp;)** |Rellena la parte entera del número con ceros iniciales, si es necesario. |"0.6" |
| **Text(&nbsp;12,&nbsp;"#.0#"&nbsp;)**<br>**Text(&nbsp;1234.568,&nbsp;"#.0#"&nbsp;)** |Rellena la parte decimal del número con ceros para una cifra decimal e incluye una segunda cifra decimal, si se suministra. |"12.0"<br>"1234.57" |
| **Text(&nbsp;12000,&nbsp;"$ #,###"&nbsp;)**<br>**Text(&nbsp;1200000,&nbsp;"$&nbsp;#,###"&nbsp;)** |Coloca un separador de miles cada tres dígitos e incluye un símbolo de moneda. |"$&nbsp;12,000"<br>"$&nbsp;1,200,000" |

### <a name="datetime"></a>Fecha y hora
* A las **2:37:47 PM** del **Monday, November 23, 2015**
* Zona horaria del Pacífico de Estados Unidos (UTC-8)

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Text( Now(), DateTimeFormat.LongDate )** |Da formato como una cadena de fecha larga, en el idioma y la configuración local del usuario actual. |"Monday, November 23, 2015" |
| **Text( Now(), DateTimeFormat.LongDateTime )** |Da formato como una cadena de fecha y hora larga, en el idioma y la configuración local del usuario actual, con un reloj de 12 horas. |"Monday, November 23, 2015 2:37:47 PM" |
| **Text( Now(), DateTimeFormat.LongTime24 )** |Da formato como una cadena de hora larga, con un reloj de 24 horas. |"14:37:47" |
| **Text( Now(), DateTimeFormat.ShortDate )** |Da formato como una cadena de fecha corta, en el idioma y la configuración local del usuario actual. |"11/23/2015" |
| **Text( Now(), "d-mmm-yy" )** |Da formato con caracteres de marcador de posición: <ul><li>**d** para un día del mes de solo un dígito o de dos dígitos<li>**-** como carácter literal copiado en el resultado<li>**mmm** para una abreviatura de tres letras del mes<li>**-** como otro carácter literal copiado en el resultado<li>**yy** para una abreviatura de dos dígitos del año</ul> |"23-Nov-15" |

### <a name="global-apps"></a>Aplicaciones globales

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Text( 1234567.89, "[$-en-US]$ #,###" )** |Interpreta **,** como un separador de agrupación puesto cada tres caracteres y **$** como el símbolo de moneda. Como no se mostrarán decimales, el valor se redondea hacia arriba al próximo número entero. En este caso, la etiqueta **[$-en-US]** es opcional, dado que se trata del valor predeterminado. |"$ 1,234,568" |
| **Text( 1234567.89, "[$-es-ES]&euro; #,###" )** |Interpreta **,** como un separador decimal y **&euro;** como el símbolo de moneda.  Debido a que la etiqueta **[$-fr-FR]** solo determina cómo se interpretará la cadena de formato, el resultado usará los caracteres de la etiqueta de idioma "en-US" predeterminada: **.** (punto) como separador decimal y **$** como símbolo de moneda. |"$ 1234567.89" |
| **Text( 1234567.89, "[$-es-ES]&euro; #,###", "es-ES" )** |Interpreta **,** como separador decimal.  La etiqueta de idioma del resultado se estableció en "fr-FR", lo que hará que **,** (coma) se use como separador decimal y **&euro;**, como símbolo de moneda. |"&euro; 1234567,89" |
| **Text( Date(2016,1,31), "dddd mmmm d" )** |Muestra el día de la semana, el mes y el día del mes en el idioma del usuario actual. Como ninguno de los marcadores de posición depende del idioma, no es necesario tener una etiqueta de idioma de texto de formato. |"Saturday January 31" |
| **Text( Date(2016,1,31), "dddd mmmm d", "es-ES" )** |Muestra el día de la semana, el mes y el día del mes en el idioma "es-ES". |"domingo enero 31" |

