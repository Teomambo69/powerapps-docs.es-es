---
title: Función Encontrar | Microsoft Docs
description: Información de referencia para la función Encontrar en PowerApps, incluidos ejemplos y sintaxis
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 8e95f03c934e0989269ff9ec21b432f609cb13ad
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "31826094"
---
# <a name="find-function-in-powerapps"></a>Función Encontrar en PowerApps
Busca una cadena de texto, si existe, dentro de otra cadena.

## <a name="description"></a>Descripción
La función **Encontrar** busca una cadena dentro de otra cadena y distingue mayúsculas de minúsculas. Para omitir mayúsculas y minúsculas, utilice primero la función **[Minusc](function-lower-upper-proper.md)** en los argumentos.

La función **Encontrar** devuelve la posición inicial de la cadena que se ha encontrado.  El primer carácter de la cadena ocupa la posición 1. La función **Encontrar** devuelve *en blanco* si la cadena en la que está buscando no contiene la cadena que está buscando.

## <a name="syntax"></a>Sintaxis
**Encontrar**( *FindString*, *WithinString* [, *StartingPosition* ] )

* *FindString*: requerido.  La cadena que se va a buscar.
* *WithinString*: requerido.  La cadena dentro de la que se va a buscar.
* *StartingPosition*: requerido.  La posición inicial para empezar a buscar.  El primer carácter ocupa la posición 1.

