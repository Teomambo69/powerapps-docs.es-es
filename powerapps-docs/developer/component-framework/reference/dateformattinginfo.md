---
title: DateFormattingInfo | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4e7d43fb-b6b7-4f1d-89e3-0b8157c9d2d9
ms.openlocfilehash: fb6dc5c67cc0ea031ab4e264d282458163ee46a0
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72344839"
---
# <a name="dateformattinginfo"></a>DateFormattingInfo

[!INCLUDE [context-description](includes/dateformattinginfo-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="properties"></a>Propiedades

### <a name="abbreviateddaynames"></a>abbreviatedDayNames

{"Sun", "Mon", "Ma", "Wed", "Thu", "vie", "SAT"}

**Tipo**: `string`

### <a name="abbreviatedmonthgenitivenames"></a>abbreviatedMonthGenitiveNames

{"Jan", "Feb", "mar", "APR", "May", "Jun", "Jul", "Ago", "Sep", "Oct", "Nov", "Dec", ""}

**Tipo**: `string[]`

### <a name="abbreviatedmonthnames"></a>abbreviatedMonthNames

{"Jan", "Feb", "mar", "APR", "May", "Jun", "Jul", "Ago", "Sep", "Oct", "Nov", "Dec", ""}

**Tipo**: `string[]`

### <a name="amdesignator"></a>amDesignator

18:30

**Tipo**: `string`

### <a name="calendar"></a>Natural

**Tipo**: `object`

El objeto `calendar` contiene las siguientes propiedades:

|Nombre|Tipo|Descripción|
|--|--|--|
|`algorithmType`|`number`|1|
|`calendarType`|`number`|1|
|`maxSupportedDateTime`|`Date`|"/Date (253402300799999)/"|
|`minSupportedDateTime`|`Date`|"/Date (-62135568000000)/"|
|`twoDigitYearMax`|`number`|2029|

### <a name="calendarweekrule"></a>calendarWeekRule

**Tipo**: `number`

### <a name="dateseparator"></a>dateSeparator

"/"

**Tipo**: `string`

### <a name="daynames"></a>dayNames

{"Sunday", "Monday", "Tuesday", "miércoles", "jueves", "viernes", "sábado"}

**Tipo**: `string[]`

### <a name="firstdayofweek"></a>primerdíasemana

**Tipo**: `number`

La propiedad `firstDayOfWeek` se puede establecer en uno de los valores siguientes:

|Value|Al|
|--|--|
|0|Domingo|
|1|Lunes|
|2|Jueves|
|3|Lunes|
|4|Martes|
|5|Día|
|6|Sábado|

### <a name="fulldatetimepattern"></a>fullDateTimePattern

"dddd, MMMM d, YYYY h:mm: SS TT"

**Tipo**: `string`

### <a name="longdatepattern"></a>longDatePattern

dddd, MMMM d, yyyy "

**Tipo**: `string`

### <a name="longtimepattern"></a>longTimePattern

"HH: mm: SS TT"

**Tipo**: `string`

### <a name="monthdaypattern"></a>monthDayPattern

"MMMM dd"

**Tipo**: `string`

### <a name="monthgenitivenames"></a>monthGenitiveNames

{"Enero", "febrero", "marzo",...  "Diciembre", ""}

**Tipo**: `string[]`

### <a name="monthnames"></a>monthNames

{"Enero", "febrero", "marzo",...  "Diciembre", ""}

**Tipo**: `string[]`

### <a name="pmdesignator"></a>pmDesignator

PM

**Tipo**: `string`

### <a name="shortdatepattern"></a>shortDatePattern

"M/d/yyyy"

**Tipo**: `string`

### <a name="shorttimepattern"></a>shortTimePattern

"h:mm TT"

**Tipo**: `string`

### <a name="shortestdaynames"></a>shortestDayNames

{"Su", "Mo", "Ma", "We", "TH", "fr", "SA"}

**Tipo**: `string[]`

### <a name="sortabledatetimepattern"></a>sortableDateTimePattern

yyyy-'-Dd't ': ' mm ': ' SS '

**Tipo**: `string`

### <a name="timeseparator"></a>timeSeparator

":"

**Tipo**: `string`

### <a name="universalsortabledatetimepattern"></a>universalSortableDateTimePattern

"YYYY-'-DD HH ': ' mm ': ' ss'Z '"

**Tipo**: `string`

### <a name="yearmonthpattern"></a>yearMonthPattern

"MMMM yyyy"

**Tipo**: `string`


### <a name="related-topics"></a>Temas relacionados

[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)