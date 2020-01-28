---
title: Funciones DateAdd, DateDiff y TimeZoneOffset | Microsoft Docs
description: Información de referencia de las funciones DateAdd, DateDiff y TimeZoneOffset de Power Apps con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/23/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e5c321617f08b6747824757344e3cc61b1abf27b
ms.sourcegitcommit: 2fd8b682e2d4c1e6a45c851b56f37f842ef18224
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2020
ms.locfileid: "76708783"
ms.PowerAppsDecimalTransform: true
---
# <a name="dateadd-datediff-and-timezoneoffset-functions-in-power-apps"></a>Funciones DateAdd, DateDiff y TimeZoneOffset de Power Apps
Agrega valores de fecha y hora o encuentra la diferencia en estos valores y realiza la conversión entre la hora local y UTC.

## <a name="description"></a>Descripción
La función **DateAdd** agrega un número de unidades a un valor de fecha y hora. El resultado es un nuevo valor de fecha y hora. También puede restar un número de unidades de un valor de fecha y hora mediante la especificación de un valor negativo.

La función **DateDiff** devuelve la diferencia entre dos valores de fecha y hora. El resultado es un número de unidades.

En ambas funciones, las unidades pueden ser **Milisegundos**, **Segundos**, **Minutos**, **Horas**, **Días**, **Meses**, **Trimestres** o **Años**.  De forma predeterminada, ambas funciones usan **días** como unidades.

La función **TimeZoneOffset** devuelve el número de minutos entre la hora local del usuario y la Hora universal coordinada (UTC).   

Puede usar **DateAdd** con **TimeZoneOffset** para realizar la conversión entre la hora local del usuario y la Hora universal coordinada (UTC).  Al sumar **TimeZoneOffset** se convierte la hora local a UTC y al restarlo (agregar el signo negativo) se convierte de UTC a la hora local.

Para obtener más información, consulte también las secciones sobre los tipos de datos [Date, Time y DateTime](../functions/data-types.md#date-time-and-datetime), y sobre [cómo trabajar con Date y Time](../show-text-dates-times.md).

## <a name="syntax"></a>Sintaxis
**DateAdd**( *DateTime*; *Addition* [; *Units* ] )

* *DateTime*: requerido. Valor de fecha y hora con el que operar.
* *Suma*: requerido. Número, en *unidades*, para agregar a *DateTime*.
* *Unidades*: opcional. Tipo de *elemento Units* que se va a agregar: **Milliseconds**, **Seconds**, **Minutes**, **Hours**, **Days**, **Months**, **Quarters** o **Years**.  Si no se especifica, se usará **Días**.

**DateDiff**( *StartDateTime*; *EndDateTime* [; *Units* ] )

* *StartDateTime*: requerido. Valor de fecha y hora de inicio.
* *EndDateTime*: requerido. Valor de fecha y hora de finalización.
* *Unidades*: opcional. Tipo de *elemento Units* que se va a agregar: **Milliseconds**, **Seconds**, **Minutes**, **Hours**, **Days**, **Months**, **Quarters** o **Years**.  Si no se especifica, se usará **Días**.

**TimeZoneOffset**( [ *DateTime* ] )

* *DateTime*: opcional.  Valor de fecha y hora para el que se devuelve el desplazamiento.  De forma predeterminada, se utiliza la fecha y hora actuales.

## <a name="examples"></a>Ejemplos
En todos estos ejemplos, se supone que la fecha y hora actuales son **15 de julio de 2013, 1:02 p.m**.

### <a name="simple-dateadd"></a>DateAdd simple

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Text( DateAdd( Now(); 3 );<br>"dd-mm-yyyy hh:mm" )** |Agrega tres días (unidades predeterminadas) a la fecha y hora actuales. |"18-07-2013 13:02" |
| **Text( DateAdd( Now(); 4; Hours );<br>"dd-mm-yyyy hh:mm" )** |Agrega cuatro horas a la fecha y hora actuales. |"15-07-2013 17:02" |
| **Text( DateAdd( Today(); 1; Months );<br>"dd-mm-yyyy hh:mm" )** |Agrega un mes a la fecha actual, sin tiempo dado que **Today** no devuelve un componente de tiempo. |"15-08-2013 00:00" |
| **Text( DateAdd( Now(); &#8209;;30; Minutes );<br>"dd-mm-yyyy hh:mm" )** |Resta 30 minutos de la fecha y hora actuales. |"15-07-2013 12:32" |

### <a name="simple-datediff"></a>DateDiff simple

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **DateDiff( Now(); DateValue("1/1/2014") )** |Devuelve la diferencia entre las dos unidades en las unidades predeterminadas de **Días**. |170 |
| **DateDiff( Now(); DateValue("1/1/2014"); Months )** |Devuelve la diferencia entre los dos valores en **Meses**. |6 |
| **DateDiff( Now(); Today(); Minutes )** |Devuelve la diferencia entre la fecha y hora actuales y la fecha actual solamente (ninguna hora) en minutos.  Puesto que **Now** es posterior a **Today**, el resultado es negativo. |-782 |

### <a name="converting-to-utc"></a>Conversión a UTC
Para convertir a UTC (Hora universal coordinada), agregue **TimeZoneOffset** durante el tiempo especificado.  

Imagine, por ejemplo, que los valores de fecha y hora actuales son **15 de julio de 2013, 1:02 p.m.** en la Hora de verano del Pacífico (PDT, UTC-7).  Para determinar la hora actual en hora UTC, use:

* **DateAdd( Now(); TimeZoneOffset(); Minutes )**

**TimeZoneOffset** toma como valor predeterminado la hora actual, por lo que no es necesario pasarle un argumento.

Para ver el resultado, use la función **Text** con el formato *dd-mm-aaaa hh:mm*, que devolverá **15-07-2013 20:02**.

### <a name="converting-from-utc"></a>Conversión desde UTC
Para convertir desde UTC, reste **TimeZoneOffset** (agregando el signo negativo) para la hora especificada.

Imagine, por ejemplo, que los valores de fecha y hora UTC **15 de julio de 2013, 8:02 p.m.** se almacenan en una variable llamada **StartTime**. Para ajustar la hora de la zona horaria del usuario, use:

* **DateAdd( StartTime; &minus;TimeZoneOffset( StartTime ); Minutes )**

Tenga en cuenta el signo negativo delante de **TimeZoneOffset** para restar el desplazamiento en lugar de sumarlo.

Para ver el resultado, use la función **Text** con el formato *dd-mm-aaaa hh:mm*, que devuelve **15-07-2013 13:02** en la Hora de verano del Pacífico.

