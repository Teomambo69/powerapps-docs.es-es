---
title: Función Shuffle | Microsoft Docs
description: Información de referencia, incluida la sintaxis y un ejemplo, para la función de orden aleatorio en Power apps
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
ms.openlocfilehash: c67e8095a7c0ed3246bce0401bbe787becd7cea0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730154"
---
# <a name="shuffle-function-in-power-apps"></a>Función de orden aleatorio en Power apps
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

