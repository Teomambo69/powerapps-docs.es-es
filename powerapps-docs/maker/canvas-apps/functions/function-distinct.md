---
title: Función Distinct | Microsoft Docs
description: Información de referencia sobre la función Distinct de PowerApps, incluidos ejemplos y sintaxis
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
ms.openlocfilehash: 17a2f2cfca16c5589f74ac434b36326037146b16
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42843207"
---
# <a name="distinct-function-in-powerapps"></a>Función Distinct de PowerApps
Resume los [registros](../working-with-tables.md#records) de una [tabla](../working-with-tables.md), quitando los duplicados.

## <a name="description"></a>Descripción
La función **Distinct** evalúa una fórmula en cada uno de los registros de una tabla. **Distinct** genera una tabla de una columna que contiene los resultados, sin los valores duplicados.  

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

## <a name="syntax"></a>Sintaxis
**Distinct**( *Table*, *Formula* )

* *Table*: requerido.  Tabla en la cual se realizará la evaluación.
* *Formula*: requerido.  La fórmula que se evalúa en cada registro.

## <a name="example"></a>Ejemplo
Si tuviera una tabla **Employees** con una columna **Department**, esta función mostraría el nombre de cada departamento único en esa columna, independientemente de cuántas veces apareció cada nombre en esa columna:

**Distinct(Employees, Department)**

