---
title: Funciones Fecha y hora | Microsoft Docs
description: Información de referencia de las funciones de fecha y hora de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 440d7bc8a737fdc53a5c76ec80db7fcf0d515f7e
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39020110"
---
# <a name="date-and-time-functions-in-powerapps"></a>Funciones de fecha y hora en PowerApps
Convierte los componentes de fecha y hora en un valor de fecha y hora.

## <a name="description"></a>Descripción
La función **fecha** convierte los valores individuales de año, mes y día en un valor de fecha y hora.  La parte de la hora es la medianoche.

* Si el año está comprendido entre 0 y 1899 (ambos incluidos), la función agrega ese valor a 1900 para calcular el año.  **70** se convierte en **1970**.
* Si el valor de Mes es menor que 1 o mayor que 12, el resultado restará o sumará esos meses desde el principio del año especificado.
* Si el valor de Día es mayor que el número de días del mes especificado, la función sumará esos días al primer día del mes y devolverá una fecha correspondiente de un mes posterior.  Si el valor de Día es menor que 1, la función resta esa cantidad de días, más 1, desde el primer día del mes especificado.

La función **Hora** convierte los valores individuales de hora, minuto y segundo en un valor de fecha y hora.  El resultado no tiene ninguna fecha asociada a él.

Consulte las funciones **[FechaNumero](function-datevalue-timevalue.md)**, **[HoraNumero](function-datevalue-timevalue.md)** y **[FechaHoraNumero](function-datevalue-timevalue.md)** para obtener información acerca de cómo convertir una cadena en un valor.  

Consulte también [cómo trabajar con fechas y horas](../show-text-dates-times.md) para más información.

## <a name="syntax"></a>Sintaxis
**Fecha**( *Año*, *Mes*, *Día* )

* *Año*: requerido.  Los números mayores a 1899 se interpretan como un absoluto (1980 se interpreta como 1980). Los números comprendidos entre 0 y 1899 se interpretan en relación con 1900. (Por ejemplo, 80 se interpreta como 1980).
* *Mes*: requerido.  Un número comprendido entre 1 y 12.
* *Día*: requerido. Un número comprendido entre 1 y 31.

**Hora**( *Hora*, *Minuto*, *Segundo* )

* *Hora*: requerido.  Un número comprendido entre 0 (12:00 a. m.) y 23 (11:00 p. m).
* *Minuto*: requerido. Un número comprendido entre 0 y 59.
* *Segundo*: requerido. Un número comprendido entre 0 y 59.

## <a name="examples"></a>Ejemplos
### <a name="date"></a>Fecha
Si un usuario escribe **1979** en un control de entrada de texto denominado **HireYear**, **3** en otro control denominado **HireMonth** y **17** en un tercer control denominado **HireDay**, esta función debería devolver **3/17/1979**:

**Date(Value(HireYear.Text), Value(HireMonth.Text), Value(HireDay.Text))**

### <a name="time"></a>Hora
Si un usuario escribe **14** en un control de entrada de texto denominado **BirthHour**, **50** en otro control denominado **BirthMinute** y **24** en un tercer control denominado **BirthSecond**, esta función debería devolver **02:50:24 p**.

**Text(Time(Value(BirthHour.Text), Value(BirthMinute.Text), Value(BirthSecond.Text)), "hh:mm:ss a/p")**

