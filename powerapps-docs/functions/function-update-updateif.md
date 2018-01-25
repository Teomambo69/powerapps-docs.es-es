---
title: Funciones Actualizar y UpdateIf | Microsoft Docs
description: "Información de referencia para las funciones Update y UpdateIf en PowerApps, incluidos ejemplos y sintaxis"
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
ms.date: 10/21/2015
ms.author: gregli
ms.openlocfilehash: 71732f7d2785dba42ba2a6e05b70ce16d3f017a5
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="update-and-updateif-functions-in-powerapps"></a>Funciones Update y UpdateIf en PowerApps
Actualiza los [registros](../working-with-tables.md#records) de un [origen de datos](../working-with-data-sources.md).

## <a name="description"></a>Descripción
### <a name="update-function"></a>Función Update
Use la función **Update** para reemplazar todo un registro en un origen de datos. En cambio, las funciones **UpdateIf** y  **[Patch](function-patch.md)**  modifican uno o varios valores de un registro, y dejan los demás valores como están.

En el caso de una [colección](../working-with-data-sources.md#collections), tiene que coincidir todo el registro. Las colecciones permiten registros duplicados, por lo que podrían coincidir varios registros. Puede usar el argumento **All** para actualizar todas las copias de un registro; en caso contrario, se actualiza solo una copia del registro.

Si el origen de datos genera automáticamente un valor de columna, el valor de esa [columna](../working-with-tables.md#columns) debe confirmarse.

### <a name="updateif-function"></a>Función UpdateIf
Use la función **UpdateIf** para modificar uno o varios valores de uno o más registros que coincidan con una o varias condiciones. Cada condición puede ser cualquier fórmula cuyo resultado sea **true** o **false**, y puede hacer referencia a columnas del origen de datos por su nombre. La función evalúa la condición para cada registro y modifica los registros cuyo resultado sea **true**.  

Para especificar una modificación, use un registro de cambio que contenga los nuevos valores de la propiedad. Si proporciona este registro de cambio en línea entre llaves, las fórmulas de propiedad pueden hacer referencia a las propiedades del registro que se van a modificar. Puede usar este comportamiento para modificar registros en función de una fórmula.

De forma similar a **UpdateIf**, también puede usar la función  **[Patch](function-patch.md)** para cambiar columnas específicas de un registro sin que afecte a otras columnas.

Tanto **Update** como **UpdateIf** devuelven el origen de datos modificado como una [tabla](../working-with-tables.md). Debe usar estas funciones en una [fórmula de comportamiento](../working-with-formulas-in-depth.md).

### <a name="delegation"></a>Delegación
[!INCLUDE [delegation-no](../includes/delegation-no.md)]

## <a name="syntax"></a>Sintaxis
**Update**( *DataSource*, *OldRecord*, *NewRecord* [, **All** ] )

* *DataSource*: requerido. Origen de datos que contiene el registro que desea reemplazar.
* *OldRecord*: requerido. Registro que se va a reemplazar.
* *NewRecord*: requerido. Registro de reemplazo. No es un registro de cambio. Se reemplaza todo el registro y propiedades que faltan contendrán *blank*.
* **Todo**: opcional. En una colección, el mismo registro puede aparecer más de una vez. Especifique el argumento **All** para quitar todas las copias del registro.

**UpdateIf**( *DataSource*, *Condition1*, *ChangeRecord1* [, *Condition2*, *ChangeRecord2*, ... ] )

* *DataSource*: requerido. Origen de datos que contiene el registro o los registros que desea modificar.
* *Condition(s)*: requerido. Fórmula que se evalúa como **true** para el registro o los registros que desea modificar.  Puede usar nombres de columna de *DataSource* en la fórmula.  
* *ChangeRecord(s)*: requerido.  Para cada condición, un registro de cambio con los nuevos valores de propiedad que se aplicarán a los registros de *DataSource* que cumplan la condición. Si proporciona el registro en línea entre llaves, los valores de propiedad del registro existente pueden utilizarse en las fórmulas de propiedad.

## <a name="examples"></a>Ejemplos
En estos ejemplos, va a reemplazar o modificar registros de un origen de datos llamado **IceCream**, que comienza con los datos de esta tabla:

![](media/function-update-updateif/icecream.png)

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Update(&nbsp;IceCream,<br>First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Chocolate"&nbsp;)&nbsp;), {&nbsp;ID:&nbsp;1,&nbsp;Flavor:&nbsp;"Mint&nbsp;Chocolate",&nbsp;Quantity:150&nbsp;} )** |Reemplaza un registro del origen de datos. |<style> img { max-width: none } </style> ![](media/function-update-updateif/icecream-mint.png)<br><br>El origen de datos **IceCream** se ha modificado. |
| **UpdateIf(&nbsp;IceCream, Quantity > 175, {&nbsp;Quantity:&nbsp;Quantity&nbsp;+&nbsp;10&nbsp;} )** |Modifica los registros con un valor de **Quantity** superior a **150**.  El campo **Quantity** se incrementa en 10, y no se modifica ningún otro campo. |![](media/function-update-updateif/icecream-mint-plus10.png)<br><br>El origen de datos **IceCream** se ha modificado. |
| **Update(&nbsp;IceCream,<br>First(&nbsp;Filter(&nbsp;IceCream, Flavor="Strawberry"&nbsp;)&nbsp;),<br>{&nbsp;ID:&nbsp;3, Flavor:&nbsp;"Strawberry Swirl"} )** |Reemplaza un registro del origen de datos. El registro de reemplazo no contiene la propiedad **Quantity**, por lo que el valor de esta propiedad será *blank* en el resultado. |![](media/function-update-updateif/icecream-mint-swirl.png)<br><br>El origen de datos **IceCream** se ha modificado. |
| **UpdateIf(&nbsp;IceCream, true, {&nbsp;Quantity:&nbsp;0&nbsp;} )** |Establece en 0 el valor de la propiedad **Quantity** de todos los registros del origen de datos. |![ ](media/function-update-updateif/icecream-mint-zero.png)<br> <br>El origen de datos **IceCream** se ha modificado. |

### <a name="step-by-step"></a>Paso a paso
1. Importe o cree una colección denominada **Inventory** y muéstrela en una galería, como se describe en el artículo sobre la [visualización de datos en una galería](../show-images-text-gallery-sort-filter.md).
2. Asigne el nombre **ProductGallery** a la galería.
3. Agregue un control deslizante llamado **UnitsSold** y establezca su propiedad **Max** en esta expresión:<br>**ProductGallery.Selected.UnitsInStock**
4. Agregue un botón y establezca su propiedad **[OnSelect](../controls/properties-core.md)** en esta fórmula:<br>**UpdateIf(Inventory, ProductName = ProductGallery.Selected.ProductName, {UnitsInStock:UnitsInStock-UnitsSold.Value})**
5. Presione F5, seleccione un producto de la galería, especifique un valor con el control deslizante y, a continuación, seleccione el botón.
   
    El número de unidades en existencias del producto se reduce en la cantidad especificada.

