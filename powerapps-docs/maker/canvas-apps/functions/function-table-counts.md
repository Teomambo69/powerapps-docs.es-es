---
title: Funciones Count, CountA, CountIf y CountRows | Microsoft Docs
description: Información de referencia, incluida la sintaxis y un ejemplo, para las funciones Count, CountA, contar.Si y CountRows en Power apps
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
ms.openlocfilehash: a0c9d7d96b4ca6ce75993586de5a39fd33906f3b
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730056"
ms.PowerAppsDecimalTransform: true
---
# <a name="count-counta-countif-and-countrows-functions-in-power-apps"></a>Funciones Count, CountA, contar.Si y CountRows en Power apps
Cuenta todos los [registros](../working-with-tables.md#records) de una [tabla](../working-with-tables.md) o todos los registros que cumplen una condición.

## <a name="description"></a>Descripción
La función **Count** cuenta el número de registros que contienen un número en una tabla de una sola columna.

La función **CountA** cuenta el número de registros que no están *blank* en una tabla de una sola columna. Esta función incluye texto [vacío](function-isblank-isempty.md) ("") en el recuento.

La función **CountIf** cuenta el número de registros de una tabla que son **true** para una fórmula lógica.  La fórmula puede hacer referencia a [columnas](../working-with-tables.md#columns) de la tabla.

La función **CountRows** cuenta el número de registros de una tabla.

Cada una de estas funciones devuelve un número.

[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>Sintaxis
**Count**( *SingleColumnTable* )<br>
**CountA**( *SingleColumnTable* )

* *SingleColumnTable*: requerido.  Columna de registros que se van a contar.  

**CountIf**( *Table*; *LogicalFormula* )

* *Table*: requerido.  Tabla de registros que se van a contar.
* *LogicalFormula*: requerido.  Fórmula que se evalúa para cada registro de la tabla.  Se cuentan los registros que devuelven el valor **true** para esta fórmula.  La fórmula puede hacer referencia a columnas de la tabla.

**CountRows**( *Table* )

* *Table*: requerido.  Tabla de registros que se van a contar.

## <a name="example"></a>Ejemplo
1. Importe o cree una [colección](../working-with-data-sources.md#collections) denominada **Inventory**, como se describe en el primer subprocedimiento de [Show images and text in a gallery](../show-images-text-gallery-sort-filter.md) (Mostrar imágenes y texto en una galería).
2. Agregue una etiqueta y establezca su propiedad **[Text](../controls/properties-core.md)** en esta fórmula:
   
    **CountIf(Inventory; UnitsInStock < 30)**
   
    La etiqueta muestra el valor **2** porque dos productos (Ganymede y Callisto) tienen menos de 30 unidades en existencias.
3. Agregue otra etiqueta y establezca su propiedad **[Text](../controls/properties-core.md)** en esta fórmula:
   
    **CountA(Inventory.UnitsInStock)**
   
    La etiqueta muestra el valor **5**, el número de celdas no vacías en la columna **UnitsInStock**.
4. Agregue otra etiqueta y establezca su propiedad **[Text](../controls/properties-core.md)** en esta fórmula:
   
    **CountRows(Inventory)**
   
    La etiqueta muestra el valor **5** porque la colección contiene cinco filas.

