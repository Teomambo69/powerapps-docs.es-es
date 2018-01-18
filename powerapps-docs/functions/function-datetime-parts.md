---
title: "Funciones Día, Mes, Año, Hora, Minuto, Segundo y Día de la semana | Microsoft Docs"
description: "Información de referencia de las funciones Día, Mes, Año, Hora, Minuto, Segundo y Día de la semana de PowerApps, con sintaxis y ejemplos"
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
ms.date: 10/25/2016
ms.author: gregli
ms.openlocfilehash: 68514c498e4737fdc5a8b78ea6bdfbb16811ba65
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2018
---
# <a name="day-month-year-hour-minute-second-and-weekday-functions-in-powerapps"></a>Funciones Día, Mes, Año, Hora, Minuto, Segundo y Día de la semana en PowerApps
Devuelve los componentes individuales de un valor de fecha y hora.

## <a name="description"></a>Descripción
La función **Día** devuelve el componente de día de un valor de fecha y hora, comprendido entre 1 y 31.

La función **Mes** devuelve el componente de mes de un valor de fecha y hora, comprendido entre 1 y 12.

La función **Año** devuelve el componente de año de un valor de fecha y hora, a partir de 1900.

La función **Hora** devuelve el componente de hora de un valor de fecha y hora, comprendido entre 0 (12:00 a. m.) y 23 (11:00 p. m).

La función **Minuto** devuelve el componente de minuto de un valor de fecha y hora, comprendido entre 0 y 59.

La función **Segundo** devuelve el componente de segundo de un valor de fecha y hora, comprendido entre 0 y 59.

La función **Día de la semana** devuelve el día de la semana de un valor de fecha y hora.  De forma predeterminada, el resultado está comprendido entre 1 (domingo) y 7 (sábado).  Puede especificar un intervalo diferente con un código de la función Día de la semana de Microsoft Excel o un valor de enumeración de InicioDeLaSemana:

| Código de Excel | Enumeración de InicioDeLaSemana | Descripción |
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
**Día**( *FechaHora* )<br>**Mes**( *FechaHora* )<br>**Año**( *FechaHora* )<br>**Hora**( *FechaHora* )<br>**Minuto**( *FechaHora* )<br>**Segundo**( *FechaHora* )

* *FechaHora*: requerido.  Valor de fecha y hora con el que operar.  

**Día de la semana**( *FechaHora* [, *WeekdayFirst* ])<br>

* *FechaHora*: requerido.  Valor de fecha y hora con el que operar. 
* *WeekdayFirst*: opcional.  Código de Excel que especifica qué día comienza la semana.  Si no se indica, se usará 1 (primero el domingo).

## <a name="examples"></a>Ejemplos
En el ejemplo siguiente, la hora actual es las **3:59:37 p. m.** del **jueves, 9 de abril de 2015**.

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Año(&nbsp;Ahora()&nbsp;)** |Devuelve el componente de año de la fecha y hora actuales. |2015 |
| **Mes(&nbsp;Ahora()&nbsp;)** |Devuelve el componente de mes de la fecha y hora actuales. |4 |
| **Día(&nbsp;Ahora()&nbsp;)** |Devuelve el componente de día de la fecha y hora actuales. |9 |
| **Hora(&nbsp;Ahora()&nbsp;)** |Devuelve el componente de hora de la fecha y hora actuales. |15 |
| **Minuto(&nbsp;Ahora()&nbsp;)** |Devuelve el componente de minuto de la fecha y hora actuales. |59 |
| **Segundo(&nbsp;Ahora()&nbsp;)** |Devuelve el componente de minuto de la fecha y hora actuales. |37 |
| **Día de la semana(&nbsp;Ahora()&nbsp;)** |Devuelve el componente de día de la semana de la fecha y hora actuales, considerando al domingo como inicio de la semana de forma predeterminada. |5 |
| **Día de la semana(&nbsp;Ahora(),&nbsp;14&nbsp;)** |Devuelve el componente de día de la semana de la fecha y hora actuales, usando un código de Excel para especificar el jueves como inicio de la semana. |1 |
| **Día de la semana(&nbsp;Ahora(),&nbsp;StartOfWeek.Wednesday&nbsp;)** |Devuelve el componente de día de la semana de la fecha y hora actuales, usando una enumeración **InicioDeLaSemana** para especificar el miércoles como inicio de la semana. |2 |

