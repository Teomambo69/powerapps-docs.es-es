---
title: Funciones DateValue, TimeValue y DateTimeValue | Microsoft Docs
description: Información de referencia, sintaxis y ejemplos de las funciones DateValue, TimeValue y Fechahoranumero en Power apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/08/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2fc1a91b4468926ee98351f79d7ce2e84133aa46
ms.sourcegitcommit: 7d3caf698d367a56af9e16c43af8005adb9f87cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987235"
---
# <a name="datevalue-timevalue-and-datetimevalue-functions-in-power-apps"></a>Funciones DateValue, TimeValue y Fechahoranumero en Power apps

Convierte la fecha, la hora o ambas de una *cadena* en un valor de *fecha y hora* .

## <a name="description"></a>Descripción

- La función **dateValue** convierte una *cadena de fecha* (por ejemplo, "10/01/2014") en un valor de *fecha y hora* .

- **TimeValue** (función) convierte una *cadena de hora* (por ejemplo, "12:15 PM") en un valor de *fecha y hora* .

- La función **fechahoranumero** convierte una *cadena de fecha y hora* (por ejemplo, "10 de enero de 2013 12:13") en un valor de *fecha y hora* .

La función **dateValue** omite cualquier información de hora en la cadena de fecha y la función **timeValue** omite cualquier información de fecha en la cadena de tiempo.

> [!NOTE]
> Las funciones DateValue, TimeValue y Fechahoranumero usan de forma predeterminada el idioma de la configuración del usuario actual. Puede invalidarlo para asegurarse de que las cadenas se interpreten correctamente. Por ejemplo, "10/1/1920" se interpreta como el 1 de octubre en "*en*" y como el *10<sup>de</sup> enero* en "*fr*". *<sup>st</sup>*

Las fechas deben estar en uno de estos formatos:

- MM/DD/AAAA o MM-DD-AAAA
- DD/MM/AAAA o DD-MM-AAAA
- AAAA/MM/DD o AAAA-MM-DD
- MM/DD/AA o MM-DD-AA
- DD/MM/AA o DD-MM-AA
- DD Mes AAAA
- Mes DD, AAAA

Para convertir de los componentes numéricos de fecha, mes y año, lea [fecha](function-date-time.md). <br>
Para convertir de componentes de hora, minuto y segundo numéricos, [hora](function-date-time.md)de lectura.

Para obtener más información, lea:

- [Trabajar con fecha y hora](../show-text-dates-times.md).
- [Tipos de datos, fecha y hora](data-types.md#date-time-and-datetime).

## <a name="syntax"></a>Sintaxis

**DateValue**( *String* [, *Language* ])<br>
**DateTimeValue**( *String* [, *Language* ])<br>
**TimeValue**( *String* [, *Language* ])

* *String*: requerido. Una cadena de texto que contiene un valor de fecha, de hora, o una combinación de ambas.
* *Idioma*: opcional. Una cadena de idioma, como la devolverían los dos primeros caracteres de la función [Language](function-language.md) .  Si no se proporciona, se usa el idioma de la configuración del usuario actual.  

## <a name="examples"></a>Ejemplos

### <a name="datevalue"></a>DateValue

Si escribe **10/11/2014** en un control de entrada de texto denominado **startDate**y, a continuación, establece la propiedad [Text](../controls/properties-core.md) de una etiqueta en estas fórmulas:

- Convierte una fecha de una cadena en la configuración regional del usuario y muestra el resultado como una fecha larga.

    ```powerapps-dot
    Text( DateValue( Startdate.Text ), DateTimeFormat.LongDate )
    ```

    Dispositivo establecido en **en** configuración regional muestra la etiqueta como **sábado, 11 de octubre de 2014**.
  
    > [!NOTE]
    > Puede utilizar varias opciones con la enumeración **DateTimeFormat** . Para mostrar una lista de opciones, escriba el parámetro seguido de un punto o un punto ( **.** ) en la barra de fórmulas o en la referencia de la función de comprobación de [ **texto** ](function-text.md).

- Convertir la fecha de una cadena en la configuración regional en francés y mostrar el resultado como una fecha larga. En este ejemplo, los meses y el día del mes se interpretan de forma diferente del inglés.

    ```powerapps-dot
    Text( DateValue( Startdate.Text, "fr" ), DateTimeFormat.LongDate )
    ```
  
    Dispositivo establecido en **en** la configuración regional muestra la etiqueta como **lunes, 10 de noviembre de 2014**.

Si escribió el **20 de octubre de 2014** en su lugar:

- Convertir una fecha de una cadena en la configuración regional del usuario y calcular la diferencia entre dos días, en días

    ```powerapps-dot
    DateDiff( DateValue( Startdate.Text ), Today() )
    ```
  
    Dispositivo establecido en **en** la configuración regional muestra la etiqueta **9**, que indica el número de días entre el 11 de octubre y el 20 de octubre. La función [DateDiff](function-dateadd-datediff.md) también puede mostrar la diferencia en meses, trimestres o años.

### <a name="datetimevalue"></a>DateTimeValue

Si escribió **10/11/2014 1:50:24.765 PM** en un control de entrada de texto denominado **Start**y, después, establezca la propiedad [Text](../controls/properties-core.md) de una etiqueta en la siguiente fórmula:

- Convierte una cadena de fecha y hora en la configuración regional actual.
 
    ```powerapps-dot
    Text( DateTimeValue( Start.Text ), DateTimeFormat.LongDateTime )
    ```    
    
    Dispositivo establecido en **en** configuración regional muestra la etiqueta como **sábado, 11 de octubre de 2014 1:50:24 PM**.
  
  > [!NOTE]
  > Puede utilizar varias opciones con la enumeración **DateTimeFormat** . Para mostrar una lista de opciones, escriba el parámetro seguido de un punto o un punto ( **.** ) en la barra de fórmulas o en la referencia de la función de comprobación de [ **texto** ](function-text.md).

- Convierte una cadena de fecha y hora en la configuración regional en francés. El mes y el día del mes se interpretan de forma diferente.

    ```powerapps-dot
    Text( DateTimeValue( Start.Text, "fr"), DateTimeFormat.LongDateTime )
    ```
  
    Dispositivo establecido en **en** la configuración regional muestra la etiqueta como **lunes, 10 de noviembre de 2014 1:50:24 PM**.

- Convierte una cadena de fecha y hora en la configuración regional del usuario y muestra el resultado con una fracción de segundo.

    ```powerapps-dot
    Text( DateTimeValue( Start.Text ), "dddd, mmmm dd, yyyy hh:mm:ss.fff AM/PM" )
    ```
  
    Dispositivo establecido en **en** configuración regional muestra la etiqueta como **sábado, 11 de octubre de 2014 01:50:24.765 PM**.
  
    Como alternativa, puede especificar **HH: mm: SS. f** o **HH: mm: SS. FF** para redondear la hora a la<sup>cuarta</sup> o<sup>100</sup> de segundo más cercana.

### <a name="timevalue"></a>TimeValue

Asigne el nombre **FinishedAt**a un control de entrada de texto y establezca la propiedad [texto](../controls/properties-core.md) de una etiqueta en esta fórmula:

```powerapps-dot
If( TimeValue( FinishedAt.Text ) < TimeValue( "5:00:00.000 PM" ), 
    "You made it!", 
    "Too late!"
)
```

- Si escribe **4:59:59.999 PM** en el control **FinishedAt** , la etiqueta muestra " *¡ lo hizo!* "
- Si escribe **5:00:00.000 PM** en el control **FinishedAt** , la etiqueta muestra "*demasiado tarde*"
