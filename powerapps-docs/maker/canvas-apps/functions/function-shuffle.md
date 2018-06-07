---
title: Función Shuffle | Microsoft Docs
description: Información de referencia de la función Aleatorio de PowerApps, con sintaxis y ejemplos
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
ms.openlocfilehash: 6d981c410b22dd9db52cdf077a00e6eaae83be75
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "31827376"
---
# <a name="shuffle-function-in-powerapps"></a>Función Aleatorio en PowerApps
Reordena aleatoriamente los [registros](../working-with-tables.md#records) de una [tabla](../working-with-tables.md).

## <a name="description"></a>Descripción
La función **Aleatorio** reordena los registros de una tabla.

**Aleatorio** devuelve una tabla que tiene las mismas [columnas](../working-with-tables.md#columns) y número de filas que el argumento.

## <a name="syntax"></a>Sintaxis
**Aleatorio**( *Tabla* )

* *Table*: requerido.  La tabla que se va a ordenar de forma aleatoria.

## <a name="example"></a>Ejemplo
Si almacena detalles sobre las cartas de la baraja en una [colección](../working-with-data-sources.md#collections) denominada **Deck**, esta fórmula devuelve una copia de dicha colección que ha sido ordenada de forma aleatoria.

**Aleatorio(Deck)**

