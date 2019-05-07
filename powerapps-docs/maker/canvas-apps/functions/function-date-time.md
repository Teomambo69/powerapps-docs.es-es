---
title: Funciones Date y Time | Microsoft Docs
description: Información de referencia de las funciones Date y Time de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 869c0fcff6e519281e527c832305d74f2e7fd78f
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61551247"
ms.PowerAppsDecimalTransform: true
---
# <a name="date-and-time-functions-in-powerapps"></a>Funciones de Date y Time en PowerApps
Convierte los componentes de fecha y hora en un valor de fecha y hora.

## <a name="description"></a>Descripción
La función **Date** convierte los valores individuales de año, mes y día en un valor de fecha y hora.  La parte de la hora es la medianoche.

* Si el año está comprendido entre 0 y 1899 (ambos incluidos), la función agrega ese valor a 1900 para calcular el año.  **70** se convierte en **1970**.
* Si el valor de Mes es menor que 1 o mayor que 12, el resultado restará o sumará esos meses desde el principio del año especificado.
* Si el valor de Día es mayor que el número de días del mes especificado, la función sumará esos días al primer día del mes y devolverá una fecha correspondiente de un mes posterior.  Si el valor de Día es menor que 1, la función resta esa cantidad de días, más 1, desde el primer día del mes especificado.

La función **Time** convierte los valores individuales de hora, minuto y segundo en un valor de fecha y hora.  El resultado no tiene ninguna fecha asociada a él.

Consulte las funciones **[DateValue](function-datevalue-timevalue.md)**, **[TimeValue](function-datevalue-timevalue.md)** y **[DateTimeValue](function-datevalue-timevalue.md)** para obtener información acerca de cómo convertir una cadena en un valor.  

Consulte también [cómo trabajar con fechas y horas](../show-text-dates-times.md) para más información.

## <a name="syntax"></a>Sintaxis
**Date**( *Year*; *Month*; *Day* )

* *Year*: requerido.  Los números mayores a 1899 se interpretan como un absoluto (1980 se interpreta como 1980). Los números comprendidos entre 0 y 1899 se interpretan en relación con 1900. (Por ejemplo, 80 se interpreta como 1980).
* *Month*: requerido.  Un número comprendido entre 1 y 12.
* *Day*: requerido. Un número comprendido entre 1 y 31.

**Time**( *Hour*; *Minute*; *Second* )

* *Hour*: requerido.  Un número comprendido entre 0 (12:00 a. m.) y 23 (11:00 p. m).
* *Minute*: requerido. Un número comprendido entre 0 y 59.
* *Second*: requerido. Un número comprendido entre 0 y 59.

## <a name="examples"></a>Ejemplos
### <a name="date"></a>Fecha
Si un usuario escribe **1979** en un control de entrada de texto denominado **HireYear**, **3** en otro control denominado **HireMonth** y **17** en un tercer control denominado **HireDay**, esta función debería devolver **3/17/1979**:

**Date(Value(HireYear.Text); Value(HireMonth.Text); Value(HireDay.Text))**

### <a name="time"></a>Time
Si un usuario escribe **14** en un control de entrada de texto denominado **BirthHour**, **50** en otro control denominado **BirthMinute** y **24** en un tercer control denominado **BirthSecond**, esta función debería devolver **02:50:24 p**.

**Text(Time(Value(BirthHour.Text); Value(BirthMinute.Text); Value(BirthSecond.Text)); "hh:mm:ss a/p")**

