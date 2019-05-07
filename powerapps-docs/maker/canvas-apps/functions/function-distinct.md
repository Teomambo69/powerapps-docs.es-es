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
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61551224"
ms.PowerAppsDecimalTransform: true
---
# <a name="distinct-function-in-powerapps"></a>Función Distinct de PowerApps
Resume los [registros](../working-with-tables.md#records) de una [tabla](../working-with-tables.md), quitando los duplicados.

## <a name="description"></a>Descripción
La función **Distinct** evalúa una fórmula en cada uno de los registros de una tabla. **Distinct** genera una tabla de una columna que contiene los resultados, sin los valores duplicados.  

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

## <a name="syntax"></a>Sintaxis
**Distinct**( *Table*; *Formula* )

* *Table*: requerido.  Tabla en la cual se realizará la evaluación.
* *Formula*: requerido.  La fórmula que se evalúa en cada registro.

## <a name="example"></a>Ejemplo
Si tuviera una tabla **Employees** con una columna **Department**, esta función mostraría el nombre de cada departamento único en esa columna, independientemente de cuántas veces apareció cada nombre en esa columna:

**Distinct(Employees; Department)**

