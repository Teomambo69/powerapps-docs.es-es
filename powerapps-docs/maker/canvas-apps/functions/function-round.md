---
title: Funciones Round, RoundDown y RoundUp | Microsoft Docs
description: Información de referencia, incluida la sintaxis, para las funciones de redondeo, redondear y redondear en Power apps
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
ms.openlocfilehash: 3b319f831291b1d0d21f3ed4699a144beb023611
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730290"
---
# <a name="round-rounddown-and-roundup-functions-in-power-apps"></a>Funciones de redondeo, redondear y recorte en Power apps
Redondea un número.

## <a name="description"></a>Descripción
Las funciones **Round**, **RoundDown** y **RoundUp** redondean un número al número especificado de posiciones decimales:

* **Round** redondea si el dígito siguiente es 5 o un número superior. En caso contrario, esta función redondea a menos.
* **RoundDown** siempre redondea hacia abajo al número anterior.
* **RoundUp** siempre redondea hacia arriba al número siguiente.

Si se pasa un número único, el valor devuelto es la versión redondeada de dicho número.  Si pasa una [tabla](../working-with-tables.md) de una sola columna que contiene números, el valor devuelto es una tabla de una sola columna de números redondeados. Si tiene una tabla con varias columnas, puede convertirla en una tabla de una sola columna, como se describe en cómo [trabajar con tablas](../working-with-tables.md).

## <a name="syntax"></a>Sintaxis
**Round**( *Number*, *DecimalPlaces* )<br>**RoundDown**( *Number*, *DecimalPlaces* )<br>**RoundUp**( *Number*, *DecimalPlaces* )

* *Number*: requerido. Número que se va a redondear.
* *DecimalPlaces*: requerido.  El número de posiciones a la derecha del separador decimal que se desea utilizar para redondear.  Use 0 para redondear a un número entero.  

