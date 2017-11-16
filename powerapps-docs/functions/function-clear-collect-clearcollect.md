---
title: Funciones Recopilar, Borrar y ClearCollect | Microsoft Docs
description: "Información de referencia sobre las funciones Collect, Clear y ClearCollect de PowerApps, incluidos ejemplos y sintaxis"
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
ms.date: 11/01/2015
ms.author: gregli
ms.openlocfilehash: 532b30b2a8740dc3f4adf879029608c6f764c6e2
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="collect-clear-and-clearcollect-functions-in-powerapps"></a>Funciones Collect, Clear y ClearCollect en PowerApps
Crea y borra [colecciones](../working-with-data-sources.md#collections) y agrega [registros](../working-with-tables.md#records) a cualquier [origen de datos](../working-with-data-sources.md).

## <a name="description"></a>Descripción
### <a name="collect"></a>Collect
La función **Collect** agrega registros a un origen de datos. Los elementos que se pueden agregar son:

* Un valor único: el valor se coloca en el campo **[Value](function-value.md)** de un nuevo registro.  Todas las demás propiedades se dejan [en blanco](function-isblank-isempty.md).
* Un registro: cada propiedad con nombre se coloca en la propiedad correspondiente de un nuevo registro.  Todas las demás propiedades se dejan en blanco.
* Una [tabla](../working-with-tables.md): cada registro de la tabla se agrega como un registro independiente del origen de datos, como se ha descrito anteriormente. La tabla no se agrega como una tabla anidada a un registro. Para lograrlo, primero ajuste la tabla en un registro.

Cuando se usa con una colección, se crearán [columnas](../working-with-tables.md#columns) adicionales según sea necesario. Las columnas de otros orígenes de datos están determinadas por el origen de datos y no se pueden agregar nuevas columnas.  

Si el origen de datos todavía no existe, se crea una colección.

Las colecciones a veces se usan para almacenar variables globales o realizar una copia temporal de un origen de datos. PowerApps se basa en fórmulas que se recalculan automáticamente a medida que el usuario interactúa con una aplicación. Las colecciones no tienen esta ventaja y su uso puede hacer que la aplicación sea más difícil de crear y comprender. Antes de usar una colección de esta manera, revise el [trabajo con variables](../working-with-variables.md).

También puede usar la función **[Patch](function-patch.md)** para crear registros en un origen de datos.

**Collect** devuelve el origen de datos modificado como una tabla.  **Collect** solo se puede usar en una [fórmula de comportamiento](../working-with-formulas-in-depth.md#behavior-formulas).

### <a name="clear"></a>Clear
La función **Clear** elimina todos los registros de una colección.  Las columnas de la colección se conservarán.

Tenga en cuenta que **Clear** solo funciona en colecciones y no en otros orígenes de datos.  Puede usar **[RemoveIf](function-remove-removeif.md)( *DataSource*, true )** para este propósito.  Tenga cuidado, ya que esto quitará todos los registros del almacenamiento del origen de datos y puede afectar a otros usuarios.

Puede usar la función **[Remove](function-remove-removeif.md)** para quitar registros de forma selectiva.

**Clear** no tiene ningún valor devuelto.  Solo se puede usar en una fórmula de comportamiento.

### <a name="clearcollect"></a>ClearCollect
La función **ClearCollect** elimina todos los registros de una colección y, después, agrega un conjunto de registros diferente a la misma colección.  Con una sola función, **ClearCollect** ofrece la combinación de **Clear** y **Collect**.

**ClearCollect** devuelve la colección modificada como una tabla.  **ClearCollect** solo se puede usar en una fórmula de comportamiento.

## <a name="syntax"></a>Sintaxis
**Collect**( *DataSource*, *Elemento*, ... )

* *DataSource*: requerido. Origen de datos al que quiere agregar datos.  Si todavía no existe, se crea una colección.
* *Item(s)*: requerido.  Uno o varios registros o tablas que se van a agregar al origen de datos.  

**Clear**( *Colección* )

* *Collection*: requerido. Colección que quiere borrar.

**ClearCollect**( *Colección*, *Elemento*, ... )

* *Collection*: requerido. Colección que quiere borrar, a la que después va a agregar datos.
* *Item(s)*: requerido.  Uno o varios registros o tablas que se van a agregar al origen de datos.  

## <a name="examples"></a>Ejemplos
### <a name="clearing-and-adding-records-to-a-data-source"></a>Borrar y agregar registros a un origen de datos
En estos ejemplos, borrará y agregará registros a una colección denominada **IceCream**.  El origen de datos comienza con este contenido:

![](media/function-clear-collect-clearcollect/icecream.png)

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **ClearCollect( IceCream, {&nbsp;Flavor:&nbsp;"Strawberry",&nbsp;Quantity:&nbsp;300&nbsp;} )** |Borra todos los datos de la colección **IceCream** y, después, agrega un registro que incluye una cantidad de IceCream de fresa. |<style> img { max-width: none } </style> ![](media/function-clear-collect-clearcollect/icecream-clearcollect.png)<br><br>El origen de datos **IceCream** también se ha modificado. |
| **Collect( IceCream, {&nbsp;Flavor:&nbsp;"Pistachio",&nbsp;Quantity:&nbsp;40&nbsp;}, {&nbsp;Flavor:&nbsp;"Orange",&nbsp;Quantity:&nbsp;200&nbsp;}  )** |Agrega dos registros a la colección **IceCream**, que incluye una cantidad de IceCream de pistacho y naranja. |![](media/function-clear-collect-clearcollect/icecream-collect.png)<br><br>El origen de datos **IceCream** también se ha modificado. |
| **Clear( IceCream )** |Quita todos los registros de la colección **IceCream**. |![](media/function-clear-collect-clearcollect/icecream-clear.png)<br><br>El origen de datos **IceCream** también se ha modificado. |

### <a name="step-by-step"></a>Paso a paso
1. Agregue un botón y establezca su propiedad **[OnSelect](../controls/properties-core.md)** en esta función:<br>**Collect(Productos, &quot;Europa&quot;, &quot;Ganymede&quot;, &quot;Callisto&quot;)**
   
    Esta función crea una colección denominada **Products** que contiene una fila para cada uno de estos tres nombres de producto.
2. Presione F5, haga clic en el botón y presione la tecla Esc para volver al área de trabajo de diseño.
3. (Opcional) Para mostrar una vista previa de la colección que ha creado, haga clic en **Colecciones** en la pestaña **Contenido**.

