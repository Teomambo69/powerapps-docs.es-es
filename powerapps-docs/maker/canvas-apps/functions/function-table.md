---
title: Función Tabla | Microsoft Docs
description: Información de referencia para la función Tabla en PowerApps, incluidos ejemplos y sintaxis
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
ms.openlocfilehash: 28d393d9be240b3e9ba57d108761c7a38f013b24
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="table-function-in-powerapps"></a>Función Tabla en PowerApps
Crea una [tabla](../working-with-tables.md) temporal.

## <a name="description"></a>Descripción
La función **Tabla** crea una tabla desde una lista de argumentos de [registros](../working-with-tables.md#records).

Las [columnas](../working-with-tables.md#columns) de la tabla será la unión de todas las propiedades de todos los registros de argumento. Un valor *en blanco* se agrega a cualquier columna para la que un registro no incluye un valor.

Una tabla es un valor en PowerApps, como una cadena o un número. Puede especificar una tabla como un argumento para una fórmula, y las funciones pueden devolver una tabla como resultado. **Tabla** no crea una tabla permanente. En su lugar, devuelve una tabla temporal hecha de sus argumentos.  Puede especificar esta tabla temporal como un argumento para otra función, visualizarla en una galería o insertarla en otra tabla.  Consulte cómo [trabajar con tablas](../working-with-tables.md) para más detalles.

También puede crear una tabla de una sola columna con la sintaxis **[valor1, valor2,...]** .

## <a name="syntax"></a>Sintaxis
**Tabla**( *Registro1* [, *Registro2*, ... ] )

* *Registro(s)*: requerido. Los registros para agregar a la tabla.

## <a name="examples"></a>Ejemplos
* Establezca la propiedad **[Elementos](../controls/properties-core.md)** de un cuadro de lista con esta fórmula:
  <br>**Tabla({Color:"red"}, {Color:"green"}, {Color:"blue"})**
  
    El cuadro de lista muestra cada color como una opción.
* Agregue una galería de texto y establezca su propiedad **[Elementos](../controls/properties-core.md)** con esta función:<br>
  **Table({Item:"Violin123", Location:"France", Owner:"Fabrikam"}, {Item:"Violin456", Location:"Chile"})**
  
    La galería muestra dos registros, ambos contienen el nombre y la ubicación de un elemento. Solo un registro contiene el nombre del propietario.

