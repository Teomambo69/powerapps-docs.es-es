---
title: "Funciones Primero, FirstN, Último y LastN | Microsoft Docs"
description: "Información de referencia sobre las funciones Primero, FirstN, Último y LastN de PowerApps, incluidos ejemplos y sintaxis"
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: dcbc897f14c34a84757a3d99d5433715b4c1d3c0
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="first-firstn-last-and-lastn-functions-in-powerapps"></a>Funciones Primero, FirstN, Último y LastN en PowerApps
Devuelve el primer o último conjunto de [registros](../working-with-tables.md#records) de una tabla.

## <a name="description"></a>Descripción
La función **Primero** devuelve el primer registro de una [tabla](../working-with-tables.md).

La función **FirstN** devuelve el primer conjunto de registros de una tabla; el segundo argumento especifica el número de registros que se van a devolver.

La función **Último** devuelve el último registro de una tabla.

La función **LastN** devuelve el último conjunto de registros de una tabla; el segundo argumento especifica el número de registros que se van a devolver.

**Primero** y **Último** devuelven un único registro.  **FirstN** y **LastN** devuelven una tabla, incluso si se especifica solo un único registro.

[!INCLUDE [delegation-no](../includes/delegation-no.md)]

## <a name="syntax"></a>Sintaxis
**Primero**( *Table* )<br>**Último**( *Table* )

* *Table*: requerido. La tabla sobre la cual se opera.

**FirstN**( *Table* [, *NumberOfRecords* ] )<br>**LastN**( *Table* [, *NumberOfRecords* ] )

* *Table*: requerido. La tabla sobre la cual se opera.
* *NumberOfRecords*: opcional.  Número de registros que se va a devolver. Si no especifica este argumento, la función devolverá un registro.

## <a name="examples"></a>Ejemplos
Esta fórmula devuelve el primer registro de una tabla denominada **Empleados**:<br>
**First(Employees)**

Esta fórmula devuelve los últimos 15 registros de una tabla denominada **Empleados**:<br>
**LastN(Employees, 15)**

