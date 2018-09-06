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
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8d96b9362047113bda332ab7e7e36c8d5cea0666
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42852597"
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

