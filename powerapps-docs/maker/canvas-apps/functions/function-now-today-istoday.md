---
title: Funciones Ahora, Hoy y EsHoy | Microsoft Docs
description: Información de referencia de las funciones Ahora, Hoy y EsHoy de PowerApps, con sintaxis y ejemplos
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 483922d2c96c23d1d2672aed7e284e30d38f298a
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="now-today-and-istoday-functions-in-powerapps"></a>Funciones Ahora, Hoy y EsHoy en PowerApps
Devuelve la fecha y hora actuales y comprueba si un valor de fecha y hora es el día de hoy.

## <a name="description"></a>Descripción
La función **Now** devuelve la fecha y hora actuales como un valor de fecha y hora.

La función **Today** devuelve la fecha actual como un valor de fecha y hora. La parte de la hora es la medianoche. **EsHoy** tiene el mismo valor a lo largo del día, desde hoy a medianoche hasta mañana a medianoche.

La función **EsHoy** comprueba si un valor de fecha y hora está comprendido entre hoy a medianoche y mañana a medianoche. Esta función devuelve un valor booleano **true** o **false**.

Todas estas funciones funcionan con la hora local del usuario actual.

Consulte [cómo trabajar con fechas y horas](../show-text-dates-times.md) para más información.

## <a name="syntax"></a>Sintaxis
**Now**()

**Today**()

**IsToday**( *FechaHora* )

* *FechaHora*: requerido.  El valor de fecha y hora para comprobar.

## <a name="examples"></a>Ejemplos
En los ejemplos de esta sección, la hora actual es **3:59 AM** el **12 de febrero de 2015** y el idioma es **en-us**.

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Text( Now(), "mm/dd/yyyy hh:mm:ss" )** |Recupera la fecha y hora actuales y las muestra como una cadena. |"02/12/2015 03:59:00" |
| **Text( Today(), "mm/dd/yyyy hh:mm:ss" )** |Recupera solo la fecha actual, dejando la parte de hora como medianoche, y la muestra como una cadena. |"02/12/2015 00:00:00" |
| **IsToday( Now() )** |Comprueba si la fecha y hora actuales se encuentran entre hoy a medianoche y mañana a medianoche. |**true** |
| **IsToday( Today() )** |Comprueba si la fecha actual se encuentra entre hoy a medianoche y mañana a medianoche. |**true** |
| **Text( DateAdd( Now(), 12 ), "mm/dd/yyyy hh:mm:ss" )** |Recupera la fecha y hora actuales, agrega 12 días al resultado y lo muestra como una cadena. |"02/24/2015 03:59:00" |
| **Text( DateAdd( Today(), 12 ), "mm/dd/yyyy hh:mm:ss" )** |Recupera la fecha actual, agrega 12 días al resultado y lo muestra como una cadena. |"02/24/2015 00:00:00" |
| **IsToday( DateAdd( Now(), 12 ) )** |Comprueba si la fecha y hora actuales, más 12 días, se encuentran entre hoy a medianoche y mañana a medianoche. |**false** |
| **IsToday( DateAdd( Today(), 12 ) )** |Comprueba si la fecha actual, más 12 días, se encuentra entre hoy a medianoche y mañana a medianoche. |**false** |

