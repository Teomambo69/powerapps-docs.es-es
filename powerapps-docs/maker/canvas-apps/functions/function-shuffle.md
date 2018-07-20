---
title: Función Shuffle | Microsoft Docs
description: Información de referencia de la función Aleatorio de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 39307e9c7b3de7bfae151709827c409fcc7087ad
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39014245"
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

