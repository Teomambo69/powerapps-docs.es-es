---
title: Integración de compatibilidad global en aplicaciones de lienzo | Microsoft Docs
description: Utilice PowerApps para compilar aplicaciones que se usen en todo el mundo.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ee2e2b854b56dadfd63b35a984e92db2ca515093
ms.sourcegitcommit: 8bad6bff1b3397b21654df4a9357dd0180fbcfe6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2019
ms.locfileid: "65046051"
---
# <a name="build-global-support-into-canvas-apps"></a>Integración de compatibilidad global en aplicaciones de lienzo
PowerApps es un producto global. Puede compilar y usar aplicaciones de lienzo en muchas regiones e idiomas diferentes.

Tanto al compilar como al ejecutar aplicaciones, el texto que PowerApps muestra se ha traducido a diversos idiomas.  Verá los elementos de menú, cuadros de diálogo, pestañas de la cinta y otros textos en su idioma nativo.  La escritura y presentación de fechas y números también se ha adaptado a su idioma y región concretos.  Por ejemplo, algunas regiones del mundo usan un **.** (punto o punto) como separador decimal mientras que otros usan un **,** (coma).  

Las aplicaciones que cree también pueden ser globales.  Use **[Idioma](functions/function-language.md)**, **[Texto](functions/function-text.md)**, **[Valor](functions/function-value.md)**, **[FechaNumero](functions/function-datevalue-timevalue.md)** y otras funciones para adaptar lo que se muestra y se utiliza como entrada en diferentes idiomas.   

## <a name="language-settings"></a>Configuración de idioma
Cuando se usa el paquete Studio nativo o un reproductor nativo, el sistema operativo host especifica el idioma.  En el caso de Windows, esto puede controlarse en "Todas las configuraciones", "Hora e idioma".  Windows también permite especificar los caracteres que se va a usar como separador decimal, invalidando la configuración de idioma.  

Cuando se trabaja con la Web, es el explorador el que proporciona el idioma.  La mayoría de los exploradores utilizan la configuración del sistema operativo de host de forma predeterminada, y algunos permiten establecer el idioma manualmente.

## <a name="authoring-environment"></a>Entorno de creación
El entorno de creación se adapta a la configuración de idioma del autor.  La aplicación se guarda de forma independiente del idioma, para que los autores con distintos idiomas puedan editar la misma aplicación.

### <a name="names-in-formulas"></a>Nombres en las fórmulas
La mayoría de los elementos de una fórmula están siempre en inglés:

* Nombres de función: **Si**, **vaya**, **recopilar**,...
* Nombres de propiedad de control: **Screen.Fill**, **Button.OnSelect**, **Textbox.Font**,...
* Nombres de enumeración: **Color.Aqua**, **DataSourceInfo.MaxValue**, **FontWeight.Bold**...
* Registros de señal: **Compass.Heading**, **ubicación. Latitude**, **App.ActiveScreen**, ...
* Operadores: **Elemento primario**, **en**, **exactIn**,...

A medida que se localiza la experiencia de creación, los controles y otros nombres de objetos se mostrarán en el idioma nativo del autor.  En español, algunos de los nombres de los controles aparecen como:

![](media/global-apps/insert-controls-es.png)

Al insertar uno de estos elementos en la aplicación, su nombre se usará en inglés de forma predeterminada.  Esto sirve para mantener la coherencia con los nombres de propiedad de los controles y el resto de la fórmula.  Por ejemplo, **Casilla** se inserta como **Checkbox1**.  

Después de insertar un control, puede cambiar el nombre por el que prefiera.  Mientras está seleccionado, el extremo izquierdo de la cinta de opciones "Contenido" muestra el nombre del control.  Al seleccionar este nombre, se despliega un cuadro de texto donde puede editarlo:

![](media/global-apps/control-rename.png)

Si lo desea, aquí se puede cambiar el nombre del control por **Casilla1**.  La línea roja ondulada, que en este caso muestra el explorador, se debe a que el nombre no es una palabra en español y no supone ningún problema.

Puede usar los nombres que desee como:

* Nombres del control
* Nombres de colección
* Nombres de variable de contexto

### <a name="formula-separators-and-chaining-operator"></a>Separadores de fórmulas y operador de encadenamiento
Algunos [separadores y operadores](functions/operators.md) cambiarán según el separador decimal del idioma del autor:

| Separador decimal del idioma del autor | Separador decimal de PowerApps | Separador de lista de PowerApps | Operador de encadenamiento de PowerApps |
| --- | --- | --- | --- |
| **.** (punto o punto) |**.** (punto o punto) |**,** (coma) |**;**  (punto y coma) |
| **,** (coma) |**,** (coma) |**;**  (punto y coma) |**;;**  (doble punto y coma) |

El cambio en el separador de lista de PowerApps es coherente con lo que ocurre con el separador de lista de Excel.  Esto afectará a lo siguiente:

* Argumentos en llamadas a funciones.
* Campos de un [registro](working-with-tables.md#elements-of-a-table).
* Registros de una [tabla de valores](working-with-tables.md#inline-syntax).

Por ejemplo, considere la siguiente fórmula expresada en un idioma y región que usa el punto como separador decimal, como Japón o en el Reino Unido:

![Fórmula de PowerApps si el valor de punto de slider1 mayor comas punto 12 59 paréntesis de apertura notificar abrir paréntesis "Valid"! Navigate puntos y comas "NextScreen" nUno paréntesis de cierre de paréntesis de apertura de paréntesis de cierre correcto de comas comas notificar abrir paréntesis "No válida, inténtelo de nuevo" error de comas Cerrar paréntesis de cierre de paréntesis](media/global-apps/operators-dot.png)

Ahora puede ver esta misma fórmula en un idioma y región donde se usa una coma para el separador decimal, como Francia o España:

![Fórmula de PowerApps si el valor de punto de slider1 mayor que 12 comas 59 puntos y coma de paréntesis de apertura notificar abrir paréntesis "Valid"! doble punto y coma Navigate abrir paréntesis "NextScreen" coma nUno paréntesis de cierre de paréntesis de cierre correcto de punto y coma coma notificar abrir paréntesis "No válida, inténtelo de nuevo" cerrar el error de punto y coma paréntesis de cierre de paréntesis](media/global-apps/operators-comma.png)

El resaltado muestra los operadores que cambian entre las dos versiones.  Tenga en cuenta que el operador de selección de propiedad **.** (punto o punto) en **Slider1.Value** es siempre el mismo, independientemente de cuál sea el separador decimal.

La fórmula no cambia internamente; lo que cambia es cómo se muestra y cómo la edita el autor.  Dos autores diferentes que usen dos idiomas distintos pueden ver y editar la misma fórmula, y cada uno verá los separadores y operadores correspondientes a su idioma.

## <a name="creating-a-global-app"></a>Creación de una aplicación global
La aplicación que cree puede adaptarse a distintos idiomas y proporcionar una experiencia de usuario óptima a usuarios de todo el mundo.

### <a name="language-function"></a>Función Language
La función **[Language](functions/function-language.md)** devuelve la etiqueta de idioma del usuario actual.  Por ejemplo, esta función devuelve **"en-GB"** para los usuarios de Gran Bretaña y **"de-DE"** para los usuarios de Alemania.  

Entre otras cosas, puede usar **Language** para mostrar texto traducido a los usuarios.  La aplicación puede incluir una tabla de valores traducidos en la aplicación:

![](media/global-apps/loc-table.png)

Y, a continuación, utilizar una fórmula como la siguiente para extraer las cadenas traducidas de la tabla:

**LookUp( Table1, TextID = "Hello" && (LanguageTag = Left( Language(), 2 ) || IsBlank( LanguageTag ))).LocalizedText**  

Tenga en cuenta que las cadenas traducidas a otros idiomas podrían ocupar más espacio que las que están en su idioma.  En muchos casos, las etiquetas y otros elementos que muestran las cadenas en la interfaz de usuario necesitarán ser más anchos para dar cabida a esas cadenas.

Para más información, consulte la documentación de la función **[Language](functions/function-language.md)**.

### <a name="formatting-numbers-dates-and-times"></a>Formato de números, fechas y horas
Los números, las fechas y las horas se escriben con diferentes formatos en las distintas partes del mundo.  El significado de las comas, los decimales y el orden del día, mes y año varían de una ubicación a otra.   

La función **[Text](functions/function-text.md)** da formato a números y fechas utilizando la configuración de idioma del usuario.

**Text** requiere una cadena de formato para saber cómo desea dar formato al número o fecha.  Esta cadena de formato puede ser de dos formas:

* **Una enumeración independiente de la configuración regional.**  Por ejemplo, **Text( Now(), DateTimeFormat.LongDate )**.  Esta fórmula dará formato a la fecha actual con el formato correspondiente al idioma.  Esta es la mejor manera de especificar la cadena de formato.
* **Una cadena de formato personalizado.**  Por ejemplo, **Text( Now(), "[$-en-US]dddd, mmmm dd, yyyy" )** muestra el mismo texto que la enumeración cuando se utiliza en el idioma "en-US".  La ventaja de la cadena de formato personalizado es que puede especificar exactamente lo que desea.

"[$-en-US]" al principio de la cadena de formato personalizado indica a **Text** en qué idioma debe interpretar la cadena de formato personalizado.  Esto se inserta automáticamente y su valor predeterminado es el idioma de creación.  Normalmente no necesitará cambiarlo.  Resulta útil cuando los autores de distintos idiomas están modificando la misma aplicación.

El tercer argumento de **Text** especifica el idioma que se usará para el resultado de la función.  El valor predeterminado es el idioma configurado para el usuario actual.

Para más información, consulte la documentación de la función **[Text](functions/function-text.md)**.      

### <a name="reading-numbers-dates-and-times"></a>Lectura de números, fechas y horas
Hay cuatro funciones para leer los números, las fechas y las horas proporcionados por el usuario:

* **[Valor](functions/function-value.md)**: Convierte a un número en una cadena de texto en un valor numérico.
* **[DateValue](functions/function-datevalue-timevalue.md)**: Convierte un valor de fecha en una cadena de texto en un valor de fecha y hora.  Se omiten las horas especificadas en la cadena de texto.
* **[TimeValue](functions/function-datevalue-timevalue.md)**: Convierte un valor de tiempo en una cadena de texto en un valor de fecha y hora.  Se omiten las fechas especificadas en la cadena de texto.
* **[DateTimeValue](functions/function-datevalue-timevalue.md)**: Convierte un valor de fecha y hora en una cadena de texto en un valor de fecha y hora.  

Si usó Excel, todas estas funciones se combinan en la función única **Value**.  Se desglosan aquí porque PowerApps tiene tipos distintos de valores de fecha, hora y números.

Todas estas funciones tienen los mismos argumentos:

* *Cadena, se requiere*: Una cadena del usuario. Por ejemplo, una cadena escribe en un control de **entrada de texto** y lee el control con la propiedad **Text**.
* *Language, opcional*: El idioma en que se va a interpretar la *cadena*.  De forma predeterminada, es el idioma configurado para el usuario.

Por ejemplo:

* **Value( "12,345.678", "en-US" )** o **Value( "12,345.678" )** cuando "en-US" es el idioma del usuario, devuelve el número **12345.678**, listo para usarlo en cálculos.
* **FechaNumero( "1/2/01", "es-ES" )** o **FechaNumero( "1/2/01" )** cuando "es-ES" es el idioma del usuario, devuelve el valor de fecha y hora **February 1, 2001 at midnight**.
* **HoraNumero( "11:43:02", "fr-FR" )** o **FechaNumero( "11:43:02" )** cuando "fr-FR" es el idioma del usuario, devuelve el valor de fecha y hora **January 1, 1970 at 11:43:02**.
* **FechaHoraNumero( "11:43:02 1/2/01", "de-DE" )** o **FechaNumero( "11:43:02" )** cuando "de-DE" es el idioma del usuario, devuelve el valor de fecha y hora **February 1, 2001 at 11:43:02**.

Para más información, consulte la documentación de las funciones **[Value](functions/function-value.md)** y **[FechaNumero, HoraNumero y FechaHoraNumero](functions/function-datevalue-timevalue.md)**, y cómo [trabajar con fechas y horas](show-text-dates-times.md).

### <a name="calendar-and-clock-information"></a>Información sobre Calendar y Clock
Las funciones **[Calendar](functions/function-clock-calendar.md)** y **[Clock](functions/function-clock-calendar.md)** proporcionan información sobre el calendario y el reloj en el idioma del usuario actual.  

Entre otras cosas, use estas funciones para proporcionar un control **Dropdown** con una lista de opciones.  

Para más información, consulte la documentación de las funciones **[Calendar](functions/function-clock-calendar.md)** y **[Clock](functions/function-clock-calendar.md)**.
