---
title: Funciones Redondear, RedondearMenos y RedondearMas | Microsoft Docs
description: Información de referencia para las funciones Redondear, RedondearMenos y RedondearMas en PowerApps, incluida la sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 182106097fb08d6ba2a3689048e9e33c5383ff57
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39016430"
---
# <a name="round-rounddown-and-roundup-functions-in-powerapps"></a>Funciones Redondear, RedondearMenos y RedondearMas en PowerApps
Redondea un número.

## <a name="description"></a>Descripción
Las funciones **Redondear**, **RedondearMenos** y **RedondearMas** redondean un número al número especificado de posiciones decimales:

* **Redondear** redondea si el dígito siguiente es 5 o un número superior. En caso contrario, esta función redondea a menos.
* **RedondearMenos** siempre redondea hacia abajo al número anterior.
* **RedondearMas** siempre redondea hacia arriba al número siguiente.

Si se pasa un número único, el valor devuelto es la versión redondeada de dicho número.  Si pasa una [tabla](../working-with-tables.md) de una sola columna que contiene números, el valor devuelto es una tabla de una sola columna de números redondeados. Si tiene una tabla con varias columnas, puede convertirla en una tabla de una sola columna, como se describe en cómo [trabajar con tablas](../working-with-tables.md).

## <a name="syntax"></a>Sintaxis
**Redondear**( *Número*, *DecimalPlaces* )<br>**RedondearMenos**( *Número*, *DecimalPlaces* )<br>**RedondearMas**( *Número*, *DecimalPlaces* )

* *Number*: requerido. Número que se va a redondear.
* *DecimalPlaces*: requerido.  El número de posiciones a la derecha del separador decimal que se desea utilizar para redondear.  Use 0 para redondear a un número entero.  

