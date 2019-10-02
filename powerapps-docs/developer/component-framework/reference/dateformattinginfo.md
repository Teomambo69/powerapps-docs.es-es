---
title: DateFormattingInfo | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4e7d43fb-b6b7-4f1d-89e3-0b8157c9d2d9
---

# <a name="dateformattinginfo"></a>DateFormattingInfo

[!INCLUDE [context-description](includes/dateformattinginfo-description.md)]

## <a name="abbreviateddaynames"></a>abbreviatedDayNames

{ "Dom", "Lun", "Mar", "Mie", "Jue", "Vie", "Sab" }

**Tipo**: `string`

## <a name="abbreviatedmonthgenitivenames"></a>abbreviatedMonthGenitiveNames

{ "Ene", "Feb", "Mar", "Abr", "May", "Jun", "Jul", "Ago", "Sep", "Oct", "Nov", "Dic", "" }

**Tipo**: `string[]`

## <a name="abbreviatedmonthnames"></a>abbreviatedMonthNames

{ "Ene", "Feb", "Mar", "Abr", "May", "Jun", "Jul", "Ago", "Sep", "Oct", "Nov", "Dic", "" }

**Tipo**: `string[]`

## <a name="amdesignator"></a>amDesignator

"AM"

**Tipo**: `string`

## <a name="calendar"></a>calendario

**Tipo**: `object`

El objeto `calendar` contiene las siguientes propiedades:

|Nombre|Escriba|Descripción|
|--|--|--|
|`algorithmType`|`number`|1|
|`calendarType`|`number`|1|
|`maxSupportedDateTime`|`Date`|"/Date(253402300799999)/"|
|`minSupportedDateTime`|`Date`|"/Date(-62135568000000)/"|
|`twoDigitYearMax`|`number`|2029|

## <a name="calendarweekrule"></a>calendarWeekRule

0

**Tipo**: `number`

## <a name="dateseparator"></a>dateSeparator

"/"

**Tipo**: `string`

## <a name="daynames"></a>dayNames

{ "Domingo", "Lunes", "Martes", "Miércoles", "Jueves", "Viernes", "Sábado" }

**Tipo**: `string[]`

## <a name="firstdayofweek"></a>firstDayOfWeek

**Tipo**: `number`

La propiedad `firstDayOfWeek` puede establecerse con uno de los siguientes valores:

|Value|Significado|
|--|--|
|0|Domingo|
|1|Lunes|
|2|Martes|
|3|Miércoles|
|4|Jueves|
|5|Viernes|
|6|Sábado|

## <a name="fulldatetimepattern"></a>fullDateTimePattern

"dddd, MMMM d, aaaa h:mm:ss tt"

**Tipo**: `string`

## <a name="longdatepattern"></a>longDatePattern

dddd, MMMM d, aaaa"

**Tipo**: `string`

## <a name="longtimepattern"></a>longTimePattern

"hh:mm:ss tt"

**Tipo**: `string`

## <a name="monthdaypattern"></a>monthDayPattern

"MMMM dd"

**Tipo**: `string`

## <a name="monthgenitivenames"></a>monthGenitiveNames

{ “Enero”, “Febrero”, “Marzo”,…  “Diciembre”, "" }

**Tipo**: `string[]`

## <a name="monthnames"></a>monthNames

{ “Enero”, “Febrero”, “Marzo”,…  “Diciembre”, "" }

**Tipo**: `string[]`

## <a name="pmdesignator"></a>pmDesignator

"PM"

**Tipo**: `string`

## <a name="shortdatepattern"></a>shortDatePattern

"M/d/aaaa"

**Tipo**: `string`

## <a name="shorttimepattern"></a>shortTimePattern

"h:mm tt"

**Tipo**: `string`

## <a name="shortestdaynames"></a>shortestDayNames

{ "Do", "Lu", "Ma", "Mi", "Ju", "Vi", "Sa" }

**Tipo**: `string[]`

## <a name="sortabledatetimepattern"></a>sortableDateTimePattern

aaaa'-'MM'-'dd'T'HH':'mm':'ss"

**Tipo**: `string`

## <a name="timeseparator"></a>timeSeparator

":"

**Tipo**: `string`

## <a name="universalsortabledatetimepattern"></a>universalSortableDateTimePattern

"aaaa'-'MM'-'dd HH':'mm':'ss'Z'"

**Tipo**: `string`

## <a name="yearmonthpattern"></a>yearMonthPattern

"MMMM aaaa"

**Tipo**: `string`


### <a name="related-topics"></a>Temas relacionados

[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../overview.md)