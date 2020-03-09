---
title: Función Texto | Microsoft Docs
description: Información de referencia para la función Text en Power Apps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/14/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9ebc28c72d1d25c4a6e85e25a14c8addaf457318
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78403260"
---
# <a name="text-function-in-power-apps"></a>Función de texto en Power apps
Convierte cualquier valor y da formato a un número o un valor de fecha y hora en una cadena de texto.

## <a name="description"></a>Descripción
La función **Text** da formato a un número o a un valor de fecha y hora según uno de estos tipos de argumentos:

* Un formato predefinido de fecha y hora que especifica a través de la enumeración **DateTimeFormat**. Para las fechas y horas, se prefiere este enfoque, ya que se ajusta automáticamente a la región y el idioma de cada usuario.
* Un formato personalizado, que consta de una cadena de marcadores de posición que definen, por ejemplo, si los números muestran un separador decimal y las fechas muestran el nombre completo del mes, el mes como una abreviatura o el mes como un número. Power apps admite un subconjunto de los marcadores de posición que Microsoft Excel hace. En esta cadena, el marcador de posición de idioma especifica el idioma en el que se van a interpretar los demás marcadores de posición. Si el formato personalizado incluye un punto, por ejemplo, el marcador de posición de formato de idioma especifica si el punto es un separador decimal (ja-JP) o un separador de miles (es-ES).

Consulte [cómo trabajar con fechas y horas](../show-text-dates-times.md) para más información.

La función **Text** también puede convertir cualquier tipo de datos en una representación de texto con un formato predeterminado. Úselo para pasar valores que no son de texto a funciones basadas en texto como [**Len**](function-len.md), [**right**](function-left-mid-right.md)y [**IsMatch**](function-ismatch.md).

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

| Marcador | Descripción |
| --- | --- |
| **0** (*cero*) |Muestra ceros no significativos si un número tiene menos dígitos que ceros en el formato. Por ejemplo, use el formato **#.00** si desea mostrar **8.9** como **8.90**. |
| **#** |Sigue las mismas reglas que **0** (cero). Sin embargo, **Text** no muestra ceros adicionales cuando el número tiene menos dígitos en cualquier lado del decimal que símbolos # en el formato. Por ejemplo, se muestra **8.9** si el formato personalizado es **#.##** y el número al que debe darse formato es **8.9**. |
| **.** (*punto*) |Muestra el punto decimal de un número. Depende del idioma del formato personalizado; vea [aplicaciones globales](#global-apps) para obtener más detalles. |
| **,** (*coma*) |Muestra el separador de agrupación de un número; a menudo, se usa para los miles. **Text** separa los grupos con comas si el formato contiene una coma encerrada entre signos numéricos ( **#** ) o ceros. Depende del idioma del formato personalizado; vea [aplicaciones globales](#global-apps) para obtener más detalles. |

Si un número tiene más dígitos a la derecha del separador decimal que marcadores de posición en el formato, el número se redondea a tantas cifras decimales como marcadores de posición existen. Si hay más dígitos a la izquierda del separador decimal que marcadores de posición, se muestran los dígitos adicionales. Si el formato solo consta de signos numéricos (#) a la izquierda del separador decimal, los números menores que 1 comienzan con un separador decimal (por ejemplo **.47**).

### <a name="date-and-time-placeholders"></a>Marcadores de posición de fecha y hora

|   Marcador    |   Descripción                                                  |
|------------------|----------------------------------------------------------------|
|  **m**   |   Muestra el mes como número sin cero inicial.               |
|  **mm**  |   Muestra el mes como número con cero inicial cuando corresponda. |
|  **mmm** |   Muestra el mes abreviado (**Ene** a **Dic**).          |
|                                                                                                   **mmmm**                                                                                                   |                                                                          Muestra el nombre completo del mes (**Enero** a **Diciembre**).                                                                           |
|                                                                                                    **d**                                                                                                     |                                                                                Muestra el día como número sin cero inicial.                                                                                 |
|                                                                                                    **dd**                                                                                                    |                                                                         Muestra el día como número con cero inicial cuando corresponda.                                                                          |
|                                                                                                   **ddd**                                                                                                    |                                                                              Muestra el día abreviado (**Dom** a **Sáb**).                                                                              |
|                                                                                                   **dddd**                                                                                                   |                                                                            Muestra el nombre completo del día (**Domingo** a **Sábado**).                                                                            |
|                                                                                                    **yy**                                                                                                    |                                                                                      Muestra el año como número de dos dígitos.                                                                                       |
|                                                                                                   **yyyy**                                                                                                   |                                                                                      Muestra el año como número de cuatro dígitos.                                                                                      |
|                                                                                                    **h**                                                                                                     |                                                                                Muestra la hora como número sin cero inicial.                                                                                |
|   **hh** | Muestra la hora como número con cero inicial cuando corresponda. Si el formato contiene **AM** o **PM**, la hora se muestra según el reloj de 12 horas. De lo contrario, la hora se muestra según el reloj de 24 horas. | 
|  **m**   |   Muestra el minuto como número sin cero inicial.<br><br>Este marcador de posición debe aparecer inmediatamente después del código **h** o **HH** o inmediatamente antes del código **SS** ; de lo contrario, **Text** devuelve el mes en lugar de los minutos.  |    
| **mm**   | Muestra el minuto como número con cero inicial cuando corresponda.<br><br>Este marcador de posición debe aparecer inmediatamente después del marcador de posición **h** o **HH** o inmediatamente antes del marcador de posición **SS** . De lo contrario, **Text** devuelve el mes en lugar de los minutos. |                                                                                                                   
| **s**   |  Muestra el segundo como número sin cero inicial.  |
| **ss**  | Muestra el segundo como número con cero inicial cuando corresponda.                                                                        |
|                                                                                                    **f**                                                                                                     |                                                                                         Muestra las fracciones de segundos.                                                                                          |
|                                                                                    **AM/PM**, **a/p**                                                                                    |               Muestra la hora según un reloj de 12 horas. El **texto** devuelve "AM" o "a" para las horas desde medianoche hasta mediodía y "PM" o "p" para las horas desde el mediodía hasta la medianoche.                |

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
| **&** |Ampersand |
| **~** |Tilde |
| **}** |Llave de cierre |
| **>** |Signo de mayor que |
| &nbsp; |Carácter de espacio |

## <a name="global-apps"></a>Aplicaciones globales
La función **Text** es globalmente compatible. Para una amplia variedad de idiomas, sabe cómo escribir correctamente fechas, horas, monedas y números. Para ello, necesita dos tipos de información:

* **El idioma del formato personalizado:** Para los responsables, ¿cómo se debe interpretar un formato personalizado? Los caracteres separadores ( **.** y **,** ) tienen significados distintos en diferentes idiomas. Si especifica un formato personalizado, puede incluir un marcador de posición de idioma o tomar el valor predeterminado, que refleja el idioma en el que está establecido el dispositivo. Incluso más fácilmente, puede usar uno de los [formatos de fecha y hora predefinidos](#predefined-datetime-formats), que son independientes del lenguaje.
* **El idioma del resultado:** Para los usuarios, ¿en qué idioma debe aparecer el resultado de la función? Los nombres de los meses y los días de la semana deben estar en el idioma adecuado para el usuario de la aplicación, que se puede especificar agregando un tercer argumento opcional a la función de **texto** . 

En ambos casos, se especifica el idioma mediante una [etiqueta de idioma](function-language.md#language-tags). Para ver la lista de idiomas admitidos, escriba **texto (1234, "")** en la barra de fórmulas o en la pestaña **Opciones avanzadas** del panel derecho y, a continuación, desplácese por la lista de configuraciones regionales sugeridas para el tercer argumento.

### <a name="language-placeholder"></a>Marcador de posición de idioma
Para especificar el idioma del formato personalizado, use:

| Marcador | Descripción |
| --- | --- |
| **[$-*LanguageTag*]** |*LanguageTag* es una etiqueta de idioma que la función **Language** muestra. Puede especificar solo el idioma (por ejemplo, **[$-en]** para inglés), o también puede especificar la región (por ejemplo, **[$-en-GB]** para especificar más Gran Bretaña). |

El marcador de posición de idioma puede aparecer en cualquier parte del formato personalizado, pero solo una vez.

Si especifica un formato personalizado sin un marcador de posición de idioma y el formato es ambiguo desde un punto de vista global, se insertará automáticamente la etiqueta de idioma del idioma actual.  

**[$-en-US]** se presupone si este marcador de posición no está presente cuando se ejecuta la aplicación. 

> [!NOTE]
> En una versión futura, la sintaxis de este marcador de posición puede cambiar para evitar la confusión con un marcador de posición similar, pero distinto, que Excel admite.

### <a name="result-language-tag"></a>Etiqueta de idioma del resultado
El resultado de **texto** incluye cadenas traducidas para meses, días de la semana y designaciones AM/PM, así como el grupo y los separadores decimales adecuados.

De manera predeterminada, la función **Text** usa el idioma del usuario que ejecuta la aplicación. La función **Language** muestra la etiqueta de idioma correspondiente al usuario actual. Puede invalidar este valor predeterminado si proporciona una etiqueta de idioma para el tercer argumento a **texto**.

## <a name="syntax"></a>Sintaxis
**Text**( *NumberOrDateTime*, *DateTimeFormatEnum* [, *ResultLanguageTag* ])

* *NumberOrDateTime* : requerido. El número o el valor de fecha y hora al que se dará formato.
* *DateTimeFormat*: requerido.  Miembro de la enumeración **DateTimeFormat**.
* *ResultLanguageTag*: opcional. La etiqueta de idioma que se usará para el texto de resultado. De manera predeterminada, se usa el idioma del usuario actual.

**Text**( *NumberOrDateTime*, *CustomFormat* [, *ResultLanguageTag* ])

* *Number*: requerido. El número o el valor de fecha y hora al que se dará formato.
* *CustomFormat*: requerido. Uno o más marcadores de posición entre comillas dobles.
* *ResultLanguageTag*: opcional. La etiqueta de idioma que se usará para el texto de resultado. De manera predeterminada, se usa el idioma del usuario actual.

**Texto**( *AnyValue* )

* *AnyValue* : requerido. Valor que se va a convertir en una representación de texto. Se utiliza un formato predeterminado.

## <a name="examples"></a>Ejemplos:
A menos que se especifique lo contrario, el usuario que ejecuta estas fórmulas se encuentra en el Estados Unidos y ha seleccionado inglés como idioma.  La función **Language** muestra "en-US".

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
| **Texto (1448318857 * 1000, "MMM. DD, AAAA (HH: mm: SS AM/PM) ")** | Muestra un valor de fecha y hora de UNIX en formato legible si multiplica el valor de origen por 1.000. | "Nov 23, 2015 (02:47:37 PM)" |

### <a name="global-apps"></a>Aplicaciones globales

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Text (1234567.89, "[$-fr-FR] # # # #, # # &euro;", "fr-FR")** | Muestra un espacio como separador de agrupación, la coma como separador decimal y **&euro;** como símbolo de divisa. |"1&nbsp;234&nbsp;567, 89 &euro;" |
| **Texto (1234567, 89; "[$-fr-FR] # # # #, # # &euro;")** | Si los datos de origen siguen el francés personalizado de usar una coma como separador decimal, debe cambiar la configuración regional a francés y separar los argumentos con un punto y coma en lugar de una coma para obtener el mismo resultado que el anterior. |"1&nbsp;234&nbsp;567, 89 &euro;" |
| **Text( Date(2016,1,31), "dddd mmmm d" )** |Muestra el día de la semana, el mes y el día del mes en el idioma del usuario actual. Como ninguno de los marcadores de posición depende del idioma, no es necesario tener una etiqueta de idioma de texto de formato. |"Sábado&nbsp;enero&nbsp;31" |
| **Text( Date(2016,1,31), "dddd mmmm d", "es-ES" )** |Muestra el día de la semana, el mes y el día del mes en el idioma "es-ES". |"Domingo&nbsp;enero&nbsp;31" |

### <a name="converting-values-to-text"></a>Convertir valores en texto

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Texto (&nbsp;1234567,89&nbsp;)** | Convierte un número en una cadena. No hay separadores de miles ni control sobre el número de dígitos antes o después del separador decimal; para obtener más control, proporcione marcadores de posición de número como segundo argumento. | "1234567,89" |
| **Text (&nbsp;Fechahoranumero (&nbsp;"01/04/2003"&nbsp;)&nbsp;)** | Convierte un valor de fecha y hora en una cadena de texto. Para controlar la conversión, proporcione un miembro de la enumeración DateTimeFormat o una cadena de formato personalizado. | "1/4/2003 12:00 AM" |
| **Text (&nbsp;true&nbsp;)** | Convierte un valor booleano en una cadena. | reales |
| **Texto (&nbsp;GUID ()&nbsp;)** | Convierte un valor GUID generado en una cadena.  | "f8b10550-0f12-4f08-9aa3-bb10958bc3ff" |
| **Left (&nbsp;texto (&nbsp;GUID ()&nbsp;),&nbsp;4&nbsp;)** | Devuelve los cuatro primeros caracteres de un GUID generado. | "2d9c" | 
