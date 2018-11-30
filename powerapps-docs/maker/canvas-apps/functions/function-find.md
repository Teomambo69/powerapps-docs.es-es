---
title: Función Find | Microsoft Docs
description: Información de referencia para la función Encontrar en PowerApps, incluidos ejemplos y sintaxis
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
ms.openlocfilehash: 04f257b40e778d3611203f2bdc17aad5554a4ac6
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42865969"
---
# <a name="find-function-in-powerapps"></a>Función Find en PowerApps
Busca una cadena de texto, si existe, dentro de otra cadena.

## <a name="description"></a>Descripción
La función **Find** busca una cadena dentro de otra cadena y distingue mayúsculas de minúsculas. Para omitir mayúsculas y minúsculas, utilice primero la función **[Lower](function-lower-upper-proper.md)** en los argumentos.

La función **Find** devuelve la posición inicial de la cadena que se ha encontrado.  El primer carácter de la cadena ocupa la posición 1. La función **Find** devuelve *blank* si la cadena en la que está buscando no contiene la cadena que está buscando.

## <a name="syntax"></a>Sintaxis
**Find**( *FindString*, *WithinString* [, *StartingPosition* ] )

* *FindString*: requerido.  La cadena que se va a buscar.
* *WithinString*: requerido.  La cadena dentro de la que se va a buscar.
* *StartingPosition*: requerido.  La posición inicial para empezar a buscar.  El primer carácter ocupa la posición 1.

