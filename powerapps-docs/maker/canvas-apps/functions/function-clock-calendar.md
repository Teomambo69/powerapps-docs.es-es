---
title: Funciones Calendar y Clock | Microsoft Docs
description: Información de referencia para las funciones Calendar y Clock en PowerApps, incluidos ejemplos y sintaxis
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
ms.openlocfilehash: 6625df3f822462c86de1f720b7a310f5e516a6ca
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42849880"
---
# <a name="calendar-and-clock-functions-in-powerapps"></a>Funciones Calendar y Clock en PowerApps
Recupera información de calendario y reloj de la configuración regional actual.

## <a name="description"></a>Descripción
Las funciones **Calendar** y **Clock** son un conjunto de funciones que recuperan información sobre la configuración regional actual.

Puede usar estas funciones para mostrar las fechas y las horas en el idioma del usuario actual.  Las tablas de una sola columna devueltas por las funciones **Calendar** y **Clock** pueden usarse directamente con la propiedad **[Items](../controls/properties-core.md)** de los controles de lista desplegable y cuadro de lista.

| Función | Descripción |
| --- | --- |
| **Calendar.MonthsLong()** |Tabla de una sola columna que contiene los nombres completos de cada mes, empezando por "January". |
| **Calendar.MonthsShort()** |Tabla de una sola columna que contiene los nombres abreviados de cada mes, empezando por "Jan" para "January". |
| **Calendar.WeekdaysLong()** |Tabla de una sola columna que contiene los nombres completos de cada día de la semana empezando por "Sunday". |
| **Calendar.WeekdaysShort()** |Tabla de una sola columna que contiene los nombres abreviados de cada día de la semana empezando por "Sun" para Sunday. |
| **Clock.AmPm()** |Tabla de una sola columna que contiene las designaciones largas de "AM" y "PM" en mayúsculas.  Si en el idioma se usa un reloj de 24 horas, la tabla estará vacía. |
| **Clock.AmPmShort()** |Tabla de una sola columna que contiene las designaciones cortas de "A" y "P" en mayúsculas.  Si en el idioma se usa un reloj de 24 horas, la tabla estará vacía. |
| **Clock.IsClock24()** |Booleano que indica si se usa un reloj de 24 horas en esta configuración regional. |

Use la función **[Text](function-text.md)** para dar formato a valores de fecha y hora con esta misma información.  La función **[Language](function-language.md)** devuelve el código de idioma y región actual.

## <a name="syntax"></a>Sintaxis
**Calendar.MonthsLong**()

**Calendar.MonthsShort**()

**Calendar.WeekdaysLong**()

**Calendar.WeekdaysShort**()

**Clock.AmPm**()

**Clock.AmPmShort**()

**Clock.IsClock24**()

## <a name="examples"></a>Ejemplos
1. Inserte un control desplegable.
2. Establezca la fórmula de la propiedad **[Items](../controls/properties-core.md)** en:
   
   * **Calendar.MonthsLong()**
3. Los usuarios de la aplicación ahora pueden seleccionar un mes en su propio idioma.  Se puede reemplazar **MonthsLong** por cualquiera de las tablas de una sola columna devueltas por **Calendar** para crear selectores de día de la semana y hora.

En los Estados Unidos, donde **[Language](function-language.md)** devuelve "en-US", las funciones **Calendar** devuelven lo siguiente:

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Calendar.MonthsLong()** |El valor devuelto contiene los nombres completos de cada mes, empezando por "January". |[ "January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December" ] |
| **Calendar.MonthsShort()** |El valor devuelto contiene los nombres abreviados de cada mes, empezando por "January". |[ "Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec" ] |
| **Calendar.WeekdaysLong()** |El valor devuelto contiene los nombres completos de cada mes, empezando por "Sunday". |[ "Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday" ] |
| **Calendar.WeekdaysShort()** |El valor devuelto contiene los nombres abreviados de cada mes, empezando por "Sun" para "Sunday". |[ "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" ] |
| **Clock.AmPm()** |En este idioma se usa un reloj de 12 horas.  El valor devuelto contiene las versiones en mayúsculas de las designaciones completas de AM y PM. |[ "AM", "PM" ] |
| **Clock.AmPmShort()** |En este idioma se usa un reloj de 12 horas.  El valor devuelto contiene las versiones en mayúsculas de las designaciones cortas de AM y PM. |[ "A", "P" ] |
| **Clock.IsClock24()** |En este idioma se usa un reloj de 12 horas. |**false** |

