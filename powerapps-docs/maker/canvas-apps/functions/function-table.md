---
title: Función Table | Microsoft Docs
description: Información de referencia para la función Table en PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2388df10fbc735f619497dc9b93dd049c8a46afa
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74680107"
ms.PowerAppsDecimalTransform: true
---
# <a name="table-function-in-powerapps"></a>Función Table en PowerApps
Crea una [tabla](../working-with-tables.md) temporal.

## <a name="description"></a>Descripción
La función **Table** crea una tabla desde una lista de argumentos de [registros](../working-with-tables.md#records).

Las [columnas](../working-with-tables.md#columns) de la tabla será la unión de todas las propiedades de todos los registros de argumento. Un valor *blank* se agrega a cualquier columna para la que un registro no incluye un valor.

Una tabla es un valor de Power Apps, al igual que una cadena o un número. Puede especificar una tabla como un argumento para una fórmula, y las funciones pueden devolver una tabla como resultado. **Table** no crea una tabla permanente. En su lugar, devuelve una tabla temporal hecha de sus argumentos.  Puede especificar esta tabla temporal como un argumento para otra función, visualizarla en una galería o insertarla en otra tabla.  Consulte cómo [trabajar con tablas](../working-with-tables.md) para más detalles.

También puede crear una tabla de una sola columna con la sintaxis **[valor1; valor2;...]** .

## <a name="syntax"></a>Sintaxis
**Table**( *Record1* [; *Record2*; ... ] )

* *Registro(s)* : requerido. Los registros para agregar a la tabla.

## <a name="examples"></a>Ejemplos
* Establezca la propiedad **[Items](../controls/properties-core.md)** de un cuadro de lista con esta fórmula:
  <br>**Table({Color:"red"}; {Color:"green"}; {Color:"blue"})**
  
    El cuadro de lista muestra cada color como una opción.
* Agregue una galería de texto y establezca su propiedad **[Elementos](../controls/properties-core.md)** con esta función:<br>
  **Table({Item:"Violin123"; Location:"France"; Owner:"Fabrikam"}; {Item:"Violin456"; Location:"Chile"})**
  
    La galería muestra dos registros, ambos contienen el nombre y la ubicación de un elemento. Solo un registro contiene el nombre del propietario.

