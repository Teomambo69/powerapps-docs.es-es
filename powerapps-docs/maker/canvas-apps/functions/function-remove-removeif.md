---
title: Funciones Quitar y RemoveIf | Microsoft Docs
description: Información de referencia para las funciones Quitar y RemoveIf en PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/21/2015
ms.author: gregli
ms.openlocfilehash: c8c5ba80b8ade242c367b47bf9fc1663fc4ae997
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39014843"
---
# <a name="remove-and-removeif-functions-in-powerapps"></a>Funciones Quitar y RemoveIf en PowerApps
Quita [registros](../working-with-tables.md#records) de un [origen de datos](../working-with-data-sources.md).

## <a name="description"></a>Descripción
### <a name="remove-function"></a>Función Quitar
Use la función **Quitar** para quitar un registro o registros específicos de un origen de datos.  

Para las [colecciones](../working-with-data-sources.md#collections), tiene que coincidir con todo el registro. Puede usar el argumento **Todo** para quitar todas las copias de un registro; en caso contrario, se quita solo una copia del registro.

### <a name="removeif-function"></a>Función RemoveIf
Use la función **RemoveIf** para quitar un registro o registros en función de una condición o un conjunto de condiciones. Cada condición puede ser cualquier fórmula que da como resultado **true** o **false** y puede hacer referencia a [columnas](../working-with-tables.md#columns) del origen de datos por su nombre. Cada condición se evalúa individualmente para cada registro, y si todas las condiciones se evalúan como **true** se elimina el registro.

**Quitar** y **RemoveIf** devuelven el origen de datos modificado como una [tabla](../working-with-tables.md). Puede usar ambas funciones únicamente en [fórmulas de comportamiento](../working-with-formulas-in-depth.md).

También puede usar la función **[Clear](function-clear-collect-clearcollect.md)** para eliminar registros en un origen de datos.

### <a name="delegation"></a>Delegación
[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>Sintaxis
**Quitar**( *DataSource*, *Record1* [, *Record2*, ... ] [, **Todo** ] )

* *DataSource*: requerido. El origen de datos que contiene el registro o los registros que desea quitar.
* *Registro(s)*: requerido. El registro o los registros que se van a quitar.
* **Todo**: opcional. En una colección, el mismo registro puede aparecer más de una vez.  Puede agregar el argumento **Todo** para quitar todas las copias del registro.

**Quitar**( *DataSource*, *Tabla* [, **Todo** ] )

* *DataSource*: requerido. El origen de datos que contiene los registros que desea quitar.
* *Tabla*: requerido. Tabla de registros que se van a quitar.
* **Todo**: opcional. En una colección, el mismo registro puede aparecer más de una vez.  Puede agregar el argumento **Todo** para quitar todas las copias del registro.

**RemoveIf**( *DataSource*, *Condición* [,...])

* *DataSource*: requerido. El origen de datos que contiene el registro o los registros que desea quitar.
* *Condition(s)*: requerido. Una fórmula que se evalúa como **true** para el registro o los registros que se van a quitar.  Puede usar nombres de columna de *DataSource* en la fórmula.  Si especifica varias *Condiciones*, todas se deben evaluar como **true** para el registro o registros que va a quitar.

## <a name="examples"></a>Ejemplos
En estos ejemplos, va a quitar un registro o registros de un origen de datos que se denomina **IceCream** y que comienza con los datos en esta tabla:

![](media/function-remove-removeif/icecream.png)

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Quitar (&nbsp;IceCream,<br>Primero (&nbsp;Filtrar (&nbsp;IceCream,&nbsp;Flavor = "Chocolate"&nbsp;)&nbsp;))** |Quita el registro **Chocolate** del origen de datos. |<style> img { max-width: none } </style> ![](media/function-remove-removeif/icecream-no-chocolate.png)<br><br>El origen de datos **IceCream** se ha modificado. |
| **Quitar (&nbsp;IceCream,<br>Primero (&nbsp;Filtrar (&nbsp;IceCream,&nbsp;Flavor = "Chocolate"&nbsp;)&nbsp;) First (&nbsp;Filtrar (&nbsp;IceCream,&nbsp;Flavor = "Strawberry"&nbsp;)&nbsp;) )** |Quita los dos registros del origen de datos. |![](media/function-remove-removeif/icecream-only-vanilla.png)<br><br>El origen de datos **IceCream** se ha modificado. |
| **RemoveIf (&nbsp;IceCream, Cantidad&nbsp;>&nbsp;150)** |Quita los registros que tienen una **Cantidad** superior a **150**. |![](media/function-remove-removeif/icecream-only-chocolate.png)<br><br>El origen de datos **IceCream** se ha modificado. |
| **RemoveIf(&nbsp;IceCream, Cantidad&nbsp;>&nbsp;150, Left(&nbsp;Flavor,&nbsp;1&nbsp;) = "S" )** |Quita los registros que tienen una **Cantidad** superior a 150 y cuyo valor **Flavor** empieza con **S**. |![](media/function-remove-removeif/icecream-no-strawberry.png)<br><br><br>El origen de datos **IceCream** se ha modificado. |
| **RemoveIf (&nbsp;IceCream, true)** |Quita todos los registros del origen de datos. |![](media/function-remove-removeif/icecream-empty.png)<br><br>El origen de datos **IceCream** se ha modificado. |

### <a name="step-by-step"></a>Paso a paso
1. Importe o cree una colección denominada **Inventory** y muéstrela en una galería, como se describe en el artículo sobre la [visualización de datos en una galería](../show-images-text-gallery-sort-filter.md).
2. En la galería, establezca la propiedad **[AlSeleccionar](../controls/properties-core.md)** de la imagen en la expresión:<br>**Quitar (Inventario, EsteElemento)**
3. Presione F5 y, a continuación, seleccione una imagen en la galería.<br>El elemento se quita de la galería y la colección.

