---
title: Funciones Collect, Clear y ClearCollect | Microsoft Docs
description: Información de referencia sobre las funciones Collect, Clear y ClearCollect de PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 02a69fd7844de8965607cd828c6b3e17437ce34f
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678405"
---
# <a name="collect-clear-and-clearcollect-functions-in-powerapps"></a>Funciones Collect, Clear y ClearCollect en PowerApps

Crea y borra [colecciones](../working-with-data-sources.md#collections) y agrega [registros](../working-with-tables.md#records) a cualquier [origen de datos](../working-with-data-sources.md).

## <a name="description"></a>Descripción

### <a name="collect"></a>Collect

La función **Collect** agrega registros a un origen de datos. Los elementos que se pueden agregar son:

- Un valor único: el valor se coloca en el campo **[Value](function-value.md)** de un nuevo registro.  Todas las demás propiedades se dejan [blank](function-isblank-isempty.md).
- Un registro: cada propiedad con nombre se coloca en la propiedad correspondiente de un nuevo registro.  Todas las demás propiedades se dejan en blanco.
- Una [tabla](../working-with-tables.md): cada registro de la tabla se agrega como un registro independiente del origen de datos, como se ha descrito anteriormente. La tabla no se agrega como una tabla anidada a un registro. Para lograrlo, primero ajuste la tabla en un registro.

Cuando se usa con una colección, se crearán [columnas](../working-with-tables.md#columns) adicionales según sea necesario. Las columnas de otros orígenes de datos están determinadas por el origen de datos y no se pueden agregar nuevas columnas.  

Si el origen de datos todavía no existe, se crea una colección.

Las colecciones a veces se usan para almacenar variables globales o realizar una copia temporal de un origen de datos. Las aplicaciones de energía se basan en fórmulas que se recalculan automáticamente a medida que el usuario interactúa con una aplicación. Las colecciones no tienen esta ventaja y su uso puede hacer que la aplicación sea más difícil de crear y comprender. Antes de usar una colección de esta manera, revise el [trabajo con variables](../working-with-variables.md).

También puede usar la función **[Patch](function-patch.md)** para crear registros en un origen de datos.

**Collect** devuelve el origen de datos modificado como una tabla.  **Collect** solo se puede usar en una [fórmula de comportamiento](../working-with-formulas-in-depth.md).

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
* *Item(s)* : requerido.  Uno o varios registros o tablas que se van a agregar al origen de datos.  

**Clear**( *Colección* )

* *Collection*: requerido. Colección que quiere borrar.

**ClearCollect**( *Colección*, *Elemento*, ... )

* *Collection*: requerido. Colección que quiere borrar, a la que después va a agregar datos.
* *Item(s)* : requerido.  Uno o varios registros o tablas que se van a agregar al origen de datos.  

## <a name="examples"></a>Ejemplos

### <a name="clearing-and-adding-records-to-a-data-source"></a>Borrar y agregar registros a un origen de datos

En estos ejemplos, borrará y agregará registros a una colección denominada **IceCream**. El origen de datos comienza con este contenido:

![Origen de datos de ejemplo](media/function-clear-collect-clearcollect/icecream.png)

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **ClearCollect( IceCream, {&nbsp;Flavor:&nbsp;"Strawberry",&nbsp;Quantity:&nbsp;300&nbsp;} )** |Borra todos los datos de la colección **IceCream** y, después, agrega un registro que incluye una cantidad de helado de fresa. |<style>IMG {Max-width: None}</style> ![tabla con un registro](media/function-clear-collect-clearcollect/icecream-clearcollect.png)<br><br>La colección **icecream** también se ha modificado. |
| **Collect( IceCream, {&nbsp;Flavor:&nbsp;"Pistachio",&nbsp;Quantity:&nbsp;40&nbsp;}, {&nbsp;Flavor:&nbsp;"Orange",&nbsp;Quantity:&nbsp;200&nbsp;}  )** |Agrega dos registros a la colección **icecream** que incluye una cantidad de pistacho y una nata de hielo naranja. |![tabla con dos registros](media/function-clear-collect-clearcollect/icecream-collect.png)<br><br>La colección **icecream** también se ha modificado. |
| **Clear( IceCream )** |Quita todos los registros de la colección **IceCream**. |![tabla vacía](media/function-clear-collect-clearcollect/icecream-clear.png)<br><br>La colección **icecream** también se ha modificado. |

Para obtener ejemplos paso a paso de cómo crear una colección, vea [crear y actualizar una colección](../create-update-collection.md).

### <a name="records-and-tables"></a>Registros y tablas

En estos ejemplos se examina cómo se administran los argumentos de registro y tabla para **recopilar** y **ClearCollect** .

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **ClearCollect (IceCream, {&nbsp;Flavor:&nbsp;"chocolate",&nbsp;Quantity:&nbsp;100&nbsp;}, {&nbsp;Flavor:&nbsp;"vainilla",&nbsp;Quantity:&nbsp;200&nbsp;})** | Borre todos los datos y, a continuación, agregue dos registros a la colección **icecream** , que incluye una cantidad de chocolate y una nata de hielo de vainilla.  Los registros que se van a agregar se proporcionan como argumentos individuales para la función.| ![los registros de chocolate y vainilla agregados a la colección](media/function-clear-collect-clearcollect/icecream.png) <br><br>La colección **icecream** también se ha modificado. |
| **ClearCollect (IceCream, tabla ({&nbsp;Flavor:&nbsp;"chocolate",&nbsp;Quantity:&nbsp;100&nbsp;}, {&nbsp;Flavor:&nbsp;"vainilla",&nbsp;Quantity:&nbsp;200&nbsp;}))** | Igual que el ejemplo anterior, salvo que los registros se combinan en una tabla y se pasan a través de un único argumento. El contenido de la tabla se extrae registro por registro antes de agregarse a la colección **icecream** . | ![los registros de chocolate y vainilla agregados a la colección](media/function-clear-collect-clearcollect/icecream.png)<br><br>La colección **icecream** también se ha modificado. |
| **ClearCollect (IceCream,<br>{&nbsp;Favorites: tabla ({&nbsp;Flavor:&nbsp;"chocolate",&nbsp;Quantity:&nbsp;100&nbsp;}, {&nbsp;Flavor:&nbsp;"vainilla",&nbsp;Quantity:&nbsp;200&nbsp;})})** | Igual que el ejemplo anterior, salvo que la tabla se ajusta en un registro.  Los registros de la tabla no se extraen y, en su lugar, se agrega toda la tabla como una subtabla del registro. | ![los registros de chocolate y vainilla agregados a la colección](media/function-clear-collect-clearcollect/icecream-myfavorites.png)<br><br>La colección **icecream** también se ha modificado. |

