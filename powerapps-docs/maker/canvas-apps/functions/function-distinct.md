---
title: Función Distinct | Microsoft Docs
description: Información de referencia sobre la función Distinct de PowerApps, incluidos ejemplos y sintaxis
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 101c28f2b4ac8135a9b4def9421f886f373105bf
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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

