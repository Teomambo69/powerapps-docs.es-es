---
title: Funciones DateValue, TimeValue y DateTimeValue | Microsoft Docs
description: Información de referencia de las funciones FechaNumero, HoraNumero y FechaHoraNumero de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: b5087c648c2115c93e4cd122455830e2e40b61f8
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39015418"
---
# <a name="datevalue-timevalue-and-datetimevalue-functions-in-powerapps"></a>Funciones FechaNumero, HoraNumero y FechaHoraNumero en PowerApps
Convierte una fecha o una hora, o ambas, en un valor de fecha y hora.

## <a name="description"></a>Descripción
La función **FechaNumero** convierte una cadena de fecha (por ejemplo, "10/01/2014") en un valor de fecha y hora.

La función **HoraNumero** convierte una cadena de hora (por ejemplo, "12:15 p. m.") en un valor de fecha y hora.

La función **FechaHoraNumero** convierte una cadena de fecha y hora (por ejemplo, "10 de enero de 2013, 12:13 a. m.") en un valor de fecha y hora.

La función **FechaNumero** ignora cualquier información de hora en la cadena de fecha y la función **HoraNumero** ignora cualquier información de fecha en la cadena de hora.

De forma predeterminada, el idioma utilizado es el del usuario actual, pero puede invalidar esta opción para asegurarse de que las cadenas se interpreten correctamente. Por ejemplo, "10/1/1920" se interpreta como el 1 de octubre<sup></sup> en "inglés" y como 10 de enero<sup></sup> en "francés".

Las fechas deben estar en uno de estos formatos:

* MM/DD/AAAA
* DD/MM/AAAA
* DD Mes AAAA
* Mes DD, AAAA

Consulte las funciones **[Fecha](function-date-time.md)** y **[Hora](function-date-time.md)** para convertir a partir de componentes numéricos la fecha, mes y año, y la hora, minuto y segundo.

Consulte también [cómo trabajar con fechas y horas](../show-text-dates-times.md) para más información.

Para convertir números, consulte la función **[Valor](function-value.md)**.

## <a name="syntax"></a>Sintaxis
**FechaNumero**( *Cadena* [, *Idioma* ])<br>**FechaHoraNumero**( *Cadena* [, *Idioma* ])<br>**HoraNumero**( *Cadena* [, *Idioma* ])

* *Cadena*: requerido.  Una cadena de texto que contiene un valor de fecha, de hora, o una combinación de ambas.
* *Idioma*: opcional.  Una cadena de idioma, como la que devuelven los dos primeros caracteres de la función **[Idioma](function-language.md)**.  Si no se indica, se utilizará el idioma de cliente del usuario actual.  

## <a name="examples"></a>Ejemplos
### <a name="datevalue"></a>FechaNumero
Si escribió **10/11/2014** en un control de entrada de texto denominado **Startdate** y, después, estableció la propiedad **[Texto](../controls/properties-core.md)** de una etiqueta en esta función:

* **Texto(FechaNumero(Startdate.Text), DateTimeFormat.LongDate)**
  
    La etiqueta debería mostrar el **sábado, 11 de octubre de 2014**, si su equipo se ha configurado con la configuración regional **en**.
  
    > [!NOTE]
  > Puede utilizar varias opciones, excepto **FechaYHoraLargas**, con el parámetro **FormatoDeFechaYHora**. Para mostrar una lista de esas opciones, escriba el parámetro, seguido inmediatamente de un signo de exclamación, en el cuadro de función.
* **Texto(FechaNumero(Startdate.Text, "fr"), DateTimeFormat.LongDate)**
  
    La etiqueta mostrará ahora el **lunes 10 de noviembre de 2014**.

Si hizo lo mismo en el **20 de octubre de 2014**:

* **DateDiff(FechaNumero(Startdate.Text), Today())**
  
    Si su equipo se ha configurado con el idioma **en**, la etiqueta mostrará **9**, que indica el número de días entre el 11 de octubre y el 20 de octubre. La función **[DateDiff](function-dateadd-datediff.md)** también puede mostrar la diferencia en meses, trimestres o años.

### <a name="datetimevalue"></a>FechaHoraNumero
Si escribió **10/11/2014 1:50:24.765 p. m.** en un control de entrada de texto denominado **Start** y, después, estableció la propiedad **[Texto](../controls/properties-core.md)** de una etiqueta en esta función:

* **Texto(FechaHoraNumero(Start.Text), DateTimeFormat.LongDateTime)**
  
    La etiqueta debería mostrar el **sábado, 11 de octubre de 2014 1:50:24 p. m.**, si su equipo se ha configurado con la configuración regional "en".
  
    > [!NOTE]
  > Puede utilizar varias opciones, excepto **FechaYHoraLargas**, con el parámetro **FormatoDeFechaYHora**. Para mostrar una lista de esas opciones, escriba el parámetro, seguido inmediatamente de un signo de exclamación, en el cuadro de función.
* **Texto(FechaHoraNumero(Start.Text, "fr"), DateTimeFormat.LongDateTime)**
  
    La etiqueta mostrará ahora el **lunes 10 de noviembre de 2014 1:50:24 p. m**.
* **Texto(FechaHoraNumero(Start.Text), "dddd, mmmm dd, aaaa hh:mm:ss.fff a. m./p. m.")**
  
    La etiqueta debería mostrar el **sábado, 11 de octubre de 2014 01:50:24:765 p. m.**, si su equipo se ha configurado con la configuración regional **en**.
  
    Como alternativa, puede especificar **hh:mm:ss.f** o **hh:mm:ss.ff** para redondear la hora a la décima o centésima de segundo más cercana.

### <a name="timevalue"></a>HoraValor
Asigne el nombre **FinishedAt** a un control de entrada de texto y establezca la propiedad **[Texto](../controls/properties-core.md)** de una etiqueta en esta función:

**If(HoraNumero(FinishedAt.Text)<HoraNumero("5:00:00.000 p. m."), "You made it!", "Too late!")**

* Si escribe **4:59:59.999 PM** en el control **FinishedAt** la etiqueta mostrará el texto "You made it!"
* Si escribe **5:00:00.000 p. m.** en el control **FinishedAt**, la etiqueta mostrará el texto "Too late!"

