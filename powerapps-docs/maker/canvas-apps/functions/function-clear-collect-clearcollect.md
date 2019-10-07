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
ms.openlocfilehash: 351fede5be1e0f3db74bde065dd9663672afd08a
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992911"
---
# <a name="collect-clear-and-clearcollect-functions-in-powerapps"></a>Funciones Collect, Clear y ClearCollect en PowerApps

Crea y borra [colecciones](../working-with-data-sources.md#collections) y agrega [registros](../working-with-tables.md#records) a cualquier [origen de datos](../working-with-data-sources.md).

## <a name="description"></a>Descripción

### <a name="collect"></a>Collect

La función **Collect** agrega registros a un origen de datos. Los elementos que se pueden agregar son:

- Un valor único: El valor se coloca en el campo de **[valor](function-value.md)** de un nuevo registro.  Todas las demás propiedades se dejan [blank](function-isblank-isempty.md).
- Un registro: Cada propiedad con nombre se coloca en la propiedad correspondiente de un nuevo registro.  Todas las demás propiedades se dejan en blanco.
- Una [tabla](../working-with-tables.md): Cada registro de la tabla se agrega como un registro independiente del origen de datos, tal y como se ha descrito anteriormente. La tabla no se agrega como una tabla anidada a un registro. Para lograrlo, primero ajuste la tabla en un registro.

Cuando se usa con una colección, se crearán [columnas](../working-with-tables.md#columns) adicionales según sea necesario. Las columnas de otros orígenes de datos están determinadas por el origen de datos y no se pueden agregar nuevas columnas.  

Si el origen de datos todavía no existe, se crea una colección.

Las colecciones a veces se usan para almacenar variables globales o realizar una copia temporal de un origen de datos. PowerApps se basa en fórmulas que se recalculan automáticamente a medida que el usuario interactúa con una aplicación. Las colecciones no tienen esta ventaja y su uso puede hacer que la aplicación sea más difícil de crear y comprender. Antes de usar una colección de esta manera, revise el [trabajo con variables](../working-with-variables.md).

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
| **ClearCollect( IceCream, {&nbsp;Flavor:&nbsp;"Strawberry",&nbsp;Quantity:&nbsp;300&nbsp;} )** |Borra todos los datos de la colección **IceCream** y, después, agrega un registro que incluye una cantidad de helado de fresa. |<style>IMG {Max-width: None}</style> ![Table con un registro @ no__t-2<br><br>La colección **icecream** también se ha modificado. |
| **Collect( IceCream, {&nbsp;Flavor:&nbsp;"Pistachio",&nbsp;Quantity:&nbsp;40&nbsp;}, {&nbsp;Flavor:&nbsp;"Orange",&nbsp;Quantity:&nbsp;200&nbsp;}  )** |Agrega dos registros a la colección **icecream** que incluye una cantidad de pistacho y una nata de hielo naranja. |![Table con dos registros @ no__t-1<br><br>La colección **icecream** también se ha modificado. |
| **Clear( IceCream )** |Quita todos los registros de la colección **IceCream**. |![Empty Table @ no__t-1<br><br>La colección **icecream** también se ha modificado. |

Para obtener ejemplos paso a paso de cómo crear una colección, vea [crear y actualizar una colección](../create-update-collection.md).

### <a name="records-and-tables"></a>Registros y tablas

En estos ejemplos se examina cómo se administran los argumentos de registro y tabla para **recopilar** y **ClearCollect** .

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **ClearCollect (IceCream, {&nbsp;Flavor: &nbsp; "chocolate", &nbsp;Quantity: &nbsp;100 @ no__t-5}, {&nbsp;Flavor: &nbsp; "vainilla", &nbsp;Quantity: &nbsp;200 @ no__t-10})** | Borre todos los datos y, a continuación, agregue dos registros a la colección **icecream** , que incluye una cantidad de chocolate y una nata de hielo de vainilla.  Los registros que se van a agregar se proporcionan como argumentos individuales para la función.| ![Chocolate y los registros de vainilla agregados a la colección @ no__t-1 <br><br>La colección **icecream** también se ha modificado. |
| **ClearCollect (IceCream, tabla ({&nbsp;Flavor: &nbsp; "chocolate", &nbsp;Quantity: &nbsp;100 @ no__t-5}, {&nbsp;Flavor: &nbsp; "vainilla", &nbsp;Quantity: &nbsp;200 @ no__t-10}))** | Igual que el ejemplo anterior, salvo que los registros se combinan en una tabla y se pasan a través de un único argumento. El contenido de la tabla se extrae registro por registro antes de agregarse a la colección **icecream** . | ![Chocolate y los registros de vainilla agregados a la colección @ no__t-1<br><br>La colección **icecream** también se ha modificado. |
| **ClearCollect (IceCream, <br> {&nbsp;MyFavorites: Tabla ({&nbsp;Flavor: &nbsp; "chocolate", &nbsp;Quantity: &nbsp;100 @ no__t-4}, {&nbsp;Flavor: &nbsp; "vainilla", &nbsp;Quantity: &nbsp;200 @ no__t-9})}) 0 | Igual que el ejemplo anterior, salvo que la tabla se ajusta en un registro.  Los registros de la tabla no se extraen y, en su lugar, se agrega toda la tabla como una subtabla del registro. | ![Chocolate y los registros de vainilla agregados a la colección @ no__t-1<br><br>La colección **icecream** también se ha modificado. |

