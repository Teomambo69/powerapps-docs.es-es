---
title: Función Shuffle | Microsoft Docs
description: Información de referencia de la función Shuffle de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 181ef038a90c9bfc7e3fe72af9514a34afce9776
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71983947"
---
# <a name="shuffle-function-in-powerapps"></a>Función Shuffle en PowerApps
Reordena aleatoriamente los [registros](../working-with-tables.md#records) de una [tabla](../working-with-tables.md).

## <a name="description"></a>Descripción
La función **Shuffle** reordena los registros de una tabla.

**Shuffle** devuelve una tabla que tiene las mismas [columnas](../working-with-tables.md#columns) y número de filas que el argumento.

## <a name="syntax"></a>Sintaxis
**Shuffle**( *Table* )

* *Table*: requerido.  La tabla que se va a ordenar de forma aleatoria.

## <a name="example"></a>Ejemplo
Si almacena detalles sobre las cartas de la baraja en una [colección](../working-with-data-sources.md#collections) denominada **Deck**, esta fórmula devuelve una copia de dicha colección que ha sido ordenada de forma aleatoria.

**Shuffle(Deck)**

