---
title: Funciones Round, RoundDown y RoundUp | Microsoft Docs
description: Información de referencia para las funciones Round, RoundDown y RoundUp en PowerApps, incluida la sintaxis
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
ms.openlocfilehash: 8480d66949994ba59f5ab84aef7999ab36a20b51
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71983981"
ms.PowerAppsDecimalTransform: true
---
# <a name="round-rounddown-and-roundup-functions-in-powerapps"></a>Funciones Round, RoundDown y RoundUp en PowerApps
Redondea un número.

## <a name="description"></a>Descripción
Las funciones **Round**, **RoundDown** y **RoundUp** redondean un número al número especificado de posiciones decimales:

* **Round** redondea si el dígito siguiente es 5 o un número superior. En caso contrario, esta función redondea a menos.
* **RoundDown** siempre redondea hacia abajo al número anterior.
* **RoundUp** siempre redondea hacia arriba al número siguiente.

Si se pasa un número único, el valor devuelto es la versión redondeada de dicho número.  Si pasa una [tabla](../working-with-tables.md) de una sola columna que contiene números, el valor devuelto es una tabla de una sola columna de números redondeados. Si tiene una tabla con varias columnas, puede convertirla en una tabla de una sola columna, como se describe en cómo [trabajar con tablas](../working-with-tables.md).

## <a name="syntax"></a>Sintaxis
**Round**( *Number*; *DecimalPlaces* )<br>**RoundDown**( *Number*; *DecimalPlaces* )<br>**RoundUp**( *Number*; *DecimalPlaces* )

* *Number*: requerido. Número que se va a redondear.
* *DecimalPlaces*: requerido.  El número de posiciones a la derecha del separador decimal que se desea utilizar para redondear.  Use 0 para redondear a un número entero.  

