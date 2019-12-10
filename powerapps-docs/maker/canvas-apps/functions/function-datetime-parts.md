---
title: Funciones Day, Month, Year, Hour, Minute, Second y Weekday | Microsoft Docs
description: Información de referencia, incluida la sintaxis y ejemplos, para las funciones Day, month, Year, hour, Minute, Second y Weekday en Power apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 571ec9d9b18be623a60bedfc3ac04e8ed8e46b33
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731138"
ms.PowerAppsDecimalTransform: true
---
# <a name="day-month-year-hour-minute-second-and-weekday-functions-in-power-apps"></a>Funciones día, mes, año, hora, minuto, segundo y día de la semana en Power apps
Devuelve los componentes individuales de un valor de fecha y hora.

## <a name="description"></a>Descripción
La función **Day** devuelve el componente de día de un valor de fecha y hora, comprendido entre 1 y 31.

La función **Month** devuelve el componente de mes de un valor de fecha y hora, comprendido entre 1 y 12.

La función **Year** devuelve el componente de año de un valor de fecha y hora, a partir de 1900.

La función **Hour** devuelve el componente de hora de un valor de fecha y hora, comprendido entre 0 (12:00 a. m.) y 23 (11:00 p. m).

La función **Minute** devuelve el componente de minuto de un valor de fecha y hora, comprendido entre 0 y 59.

La función **Second** devuelve el componente de segundo de un valor de fecha y hora, comprendido entre 0 y 59.

La función **Weekday** devuelve el día de la semana de un valor de fecha y hora.  De forma predeterminada, el resultado está comprendido entre 1 (domingo) y 7 (sábado).  Puede especificar un intervalo diferente con un código de la función Weekday de la semana de Microsoft Excel o un valor de enumeración de StartOfWeek:

| Código de Excel | Enumeración de StartOfWeek | Descripción |
| --- | --- | --- |
| **1**, **17** |**StartOfWeek.Sunday** |Números del 1 (domingo) al 7 (sábado).  Predeterminado. |
| **2**, **11** |**StartOfWeek.Monday** |Números del 1 (lunes) al 7 (domingo). |
| **3** |**StartOfWeek.MondayZero** |Números del 0 (lunes) al 6 (domingo). |
| **12** |**StartOfWeek.Tuesday** |Números del 1 (martes) al 7 (lunes). |
| **13** |**StartOfWeek.Wednesday** |Números del 1 (miércoles) al 7 (martes). |
| **14** |**StartOfWeek.Thursday** |Números del 1 (jueves) al 7 (miércoles). |
| **15** |**StartOfWeek.Friday** |Números del 1 (viernes) al 7 (jueves). |
| **16** |**StartOfWeek.Saturday** |Números del 1 (sábado) al 7 (viernes). |

Todas las funciones devuelven un número.

Consulte [cómo trabajar con fechas y horas](../show-text-dates-times.md) para más información.

## <a name="syntax"></a>Sintaxis
**Day**( *DateTime* )<br>**Month**( *DateTime* )<br>**Year**( *DateTime* )<br>**Hour**( *DateTime* )<br>**Minute**( *DateTime* )<br>**Second**( *DateTime* )

* *DateTime*: requerido.  Valor de fecha y hora con el que operar.  

**Weekday**( *DateTime* [; *WeekdayFirst* ] )<br>

* *DateTime*: requerido.  Valor de fecha y hora con el que operar. 
* *WeekdayFirst*: opcional.  Código de Excel que especifica qué día comienza la semana.  Si no se indica, se usará 1 (primero el domingo).

## <a name="examples"></a>Ejemplos
En el ejemplo siguiente, la hora actual es las **3:59:37 p. m.** del **jueves, 9 de abril de 2015**.

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Year(&nbsp;Now()&nbsp;)** |Devuelve el componente de año de la fecha y hora actuales. |2015 |
| **Month(&nbsp;Now()&nbsp;)** |Devuelve el componente de mes de la fecha y hora actuales. |4 |
| **Day(&nbsp;Now()&nbsp;)** |Devuelve el componente de día de la fecha y hora actuales. |9 |
| **Hour(&nbsp;Now()&nbsp;)** |Devuelve el componente de hora de la fecha y hora actuales. |15 |
| **Minute(&nbsp;Now()&nbsp;)** |Devuelve el componente de minuto de la fecha y hora actuales. |59 |
| **Second(&nbsp;Now()&nbsp;)** |Devuelve el componente de minuto de la fecha y hora actuales. |37 |
| **Weekday(&nbsp;Now()&nbsp;)** |Devuelve el componente de día de la semana de la fecha y hora actuales, considerando al domingo como inicio de la semana de forma predeterminada. |5 |
| **Weekday(&nbsp;Now();&nbsp;14&nbsp;)** |Devuelve el componente de día de la semana de la fecha y hora actuales, usando un código de Excel para especificar el jueves como inicio de la semana. |1 |
| **Weekday(&nbsp;Now();&nbsp;StartOfWeek.Wednesday&nbsp;)** |Devuelve el componente de día de la semana de la fecha y hora actuales, usando una enumeración **StartOfWeek** para especificar el miércoles como inicio de la semana. |2 |

