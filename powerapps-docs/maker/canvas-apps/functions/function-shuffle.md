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
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3fd93ce6cf9703e9e9fbf69c5826213d9aa78e02
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42863577"
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

