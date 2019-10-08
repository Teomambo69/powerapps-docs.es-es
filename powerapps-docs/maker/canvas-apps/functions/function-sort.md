---
title: Funciones Sort y SortByColumns | Microsoft Docs
description: Información de referencia para las funciones Sort y SortByColumns en PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/26/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: aa51c97eff57b9659e5fd246af8016898eeeb9df
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992240"
ms.PowerAppsDecimalTransform: true
---
# <a name="sort-and-sortbycolumns-functions-in-powerapps"></a>Funciones Sort y SortByColumns en PowerApps
Ordena una [tabla](../working-with-tables.md).

## <a name="description"></a>Descripción
La función **Sort** ordena una tabla según una fórmula.  

La fórmula se evalúa para cada [registro](../working-with-tables.md#records) de la tabla y los resultados se usan para ordenar la tabla.  La fórmula debe dar como resultado un número, una cadena o un valor booleano; no puede generar una tabla ni un registro.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

Para ordenar primero por una columna y luego por otra, debe insertar una fórmula **Sort** dentro de otra. Por ejemplo, puede usar esta fórmula para ordenar una tabla **Contacts** primero por una columna **LastName** y después por una columna **FirstName** :  **Sort (sort (contactos, apellidos), FirstName)**

La función **SortByColumns** también se puede usar para ordenar una tabla según una o más columnas.

La lista de parámetros para **SortByColumns** proporciona los nombres de las columnas según las cuales ordenar y la dirección de ordenación por columna.  La ordenación se realiza según el orden de los parámetros (ordenados primero por la primera columna, luego la segunda, etc.).  Los nombres de columna se especifican como cadenas y requieren comillas dobles si se incluyen directamente en la lista de parámetros.  Por ejemplo, **SortByColumns( CustomerTable; "LastName" )** .

Puede combinar **SortByColumns** con un control **[Menú desplegable](../controls/control-drop-down.md)** o **[Cuadro de lista](../controls/control-list-box.md)** para permitir que los usuarios seleccionen la columna según la cual ordenar.

Además de ordenar de manera ascendente o descendente, **SortByColumns** puede ordenar según una tabla de valores de una sola columna.  Por ejemplo, puede ordenar el registro según el nombre de un día de la semana si suministra **[ "Lunes"; "Martes"; "Miércoles"; "Jueves"; "Viernes"; "Sábado"; "Domingo" ]** como el criterio de ordenación.  Todos los registros que incluyan **Lunes"** aparecerán primero, seguidos de los registros que incluyan **Martes**, etc.  Los registros encontrados que no aparezcan en la tabla de ordenación se colocan al final de la lista.

Las [tablas](../working-with-tables.md) son un valor en PowerApps, tal como una cadena o un número.  Se pueden pasar a funciones y las funciones pueden devolverlas.  **Sort** y **SortByColumn** no modifican una tabla; en lugar de eso, toman una tabla como argumento y devuelven una tabla nueva que se ordenó.  Consulte cómo [trabajar con tablas](../working-with-tables.md) para más detalles.

[!INCLUDE [delegation](../../../includes/delegation.md)]

## <a name="syntax"></a>Sintaxis
**Sort**( *Table*; *Formula* [; *SortOrder* ] )

* *Table*: requerido. La tabla que se va a ordenar.
* *Formula*: requerido. Esta fórmula se evalúa para cada registro de la tabla y los resultados se usan para ordenar la tabla.  Puede hacer referencia a columnas dentro de la tabla.
* *SortOrder*: opcional. Especifique **SortOrder.Descending** para ordenar la tabla en orden descendente. **SortOrder.Ascending** es el valor predeterminado.

**SortByColumns**( *Table*; *ColumnName1* [; *SortOrder1*; *ColumnName2*; *SortOrder2*; ... ] )

* *Table*: requerido. La tabla que se va a ordenar.
* *ColumnName(s)* : requerido. Los nombres de las columnas según las cuales ordenar, como cadenas.
* *SortOrder(s)* : opcional.  **SortOrder.Ascending** o **SortOrder.Descending**.  **SortOrder.Ascending** es el valor predeterminado.  Si se suministran varios *ColumnNames*, todas las columnas, menos la última, deben incluir un *SortOrder*.
  
    > [!NOTE]
  > En el caso de orígenes de datos de SharePoint y Excel que contengan nombres de columna con espacios, especifique cada uno de ellos como **"\_x0020\_"** . Por ejemplo, especifique **"Nombre de columna"** como **"Nombre_x0020_de_columna"** .

**SortByColumns**( *Table*; *ColumnName*; *SortOrderTable* )

* *Table*: requerido. La tabla que se va a ordenar.
* *ColumnName*: requerido. El nombre de la columna según la cual ordenar, como cadenas.
* *SortOrderTable*: requerido.  Tabla de valores de una sola columna según la cual ordenar.
  
    > [!NOTE]
  > En el caso de orígenes de datos de SharePoint y Excel que contengan nombres de columna con espacios, especifique cada uno de ellos como **"\_x0020\_"** . Por ejemplo, especifique **"Nombre de columna"** como **"Nombre_x0020_de_columna"** .

## <a name="examples"></a>Ejemplos
En los ejemplos siguientes, usaremos el [origen de datos](../working-with-data-sources.md) **IceCream**, que contiene los datos de esta tabla:

![](media/function-sort/icecream.png)

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Sort( IceCream; Flavor )**<br><br>**SortByColumns( IceCream; "Flavor" )** |Ordena **IceCream** según su columna **Flavor**. La columna **Sabor** contiene cadenas, por lo que la tabla se ordena alfabéticamente. De manera predeterminada, el criterio de ordenación es ascendente. |<style> img { max-width: none; } </style> ![](media/function-sort/icecream-flavor.png) |
| **Sort( IceCream; Quantity )**<br><br>**SortByColumns( IceCream; "Quantity" )** |Ordena **IceCream** según su columna **Quantity**.  La columna **Cantidad** contiene números, por lo que la tabla se ordena numéricamente.  De manera predeterminada, el criterio de ordenación es ascendente. |![](media/function-sort/icecream-quantity-asc.png) |
| **Sort( IceCream; Quantity; SortOrder.Descending )**<br><br>**SortByColumns( IceCream; "Quantity"; SortOrder.Descending )** |Ordena **IceCream** según su columna **Quantity**.  La columna **Cantidad** contiene números, por lo que se ordena numéricamente.  El criterio de ordenación se especificó como descendente. |![](media/function-sort/icecream-quantity-desc.png) |
| **Sort( IceCream; Quantity + OnOrder )** |Ordena **IceCream** por la suma de sus columnas **Quantity** y **OnOrder** para cada registro individualmente. La suma es un número, por lo que la tabla se ordena numéricamente.  De manera predeterminada, el criterio de ordenación es ascendente.  Como ordenamos según una fórmula y no según valores de columna sin formato, no hay ningún equivalente usando **SortByColumns**. |![](media/function-sort/icecream-total.png) |
| **Sort( Sort( IceCream; OnOrder ); Quantity )**<br><br>**SortByColumns( IceCream; "OnOrder"; Ascending; "Quantity"; Ascending )** |Ordena **IceCream** primero según su columna **OnOrder** y, luego, según su columna **Quantity**.  Observe que "Pistacho" apareció arriba de "Vainilla" en la primera ordenación según **OnOrder** y, luego, pasaron a su lugar adecuado según **Quantity**. |![](media/function-sort/icecream-onorder-quantity.png) |
| **SortByColumns( IceCream; "Flavor"; [&nbsp;"Pistachio";&nbsp;"Strawberry"&nbsp;] )** |Ordena **IceCream** según su columna **Flavor** en función de la tabla con una sola columna que contiene "Pistacho" y "Fresa".  Los registros que tienen un **Sabor** "Pistacho" aparecerán primero en el resultado, seguidos de los registros que contienen "Fresa".  En el caso de los valores de la columna **Sabor** que no tienen coincidencia, como "Vainilla", aparecerán después de los elementos que sí tuvieron coincidencia. |![](media/function-sort/icecream-onflavor-sorttable.png) |

### <a name="step-by-step"></a>Paso a paso
Para ejecutar estos ejemplos, cree el origen de datos **IceCream** como una [colección](../working-with-data-sources.md#collections):

1. Agregue un botón y establezca su propiedad **[OnSelect](../controls/properties-core.md)** en esta fórmula:<br>**ClearCollect (IceCream; {Flavor: "Chocolate"; cantidad: 100; en orden: 150}; {Flavor:  "Vainilla"; cantidad: 200; en orden: 20}; {Flavor: "Fresa"; cantidad: 300; en orden: 0}; {Flavor: "Menta chocolate"; cantidad: 60; en orden: 100}; {Flavor: "Pistacho"; cantidad: 200; en orden: 10})**
2. Obtenga una vista previa de la aplicación, seleccione el botón y, luego, presione Esc para volver al área de trabajo predeterminada.
3. Seleccione **Colecciones** en el menú **Archivo** para mostrar la colección que acaba de crear y, luego, presione Esc para volver al área de trabajo predeterminada.

#### <a name="sort"></a>Ordenar
1. Agregue otro botón y establezca su propiedad **[OnSelect](../controls/properties-core.md)** en esta fórmula:<br>
   **ClearCollect( SortByFlavor; Sort( IceCream; Flavor ) )**
   
     La fórmula anterior crear otra colección, denominada **SortByFlavor**, que contiene los mismos datos que **IceCream**. Sin embargo, la colección nueva contiene los datos ordenados alfabéticamente según la columna **Sabor** en orden ascendente.
2. Presione F5, seleccione el botón nuevo y, luego, presione Esc.
3. Seleccione **Colecciones** en el menú **Archivo** para mostrar ambas colecciones y, luego, presione Esc para volver al área de trabajo predeterminada.
4. Repita los últimos tres pasos, pero cambie el nombre de la colección que desea crear y reemplace la fórmula **Sort** por una fórmula distinta de la tabla de ejemplos que apareció anteriormente en esta sección que usa **Sort**.

#### <a name="sortbycolumns"></a>SortByColumns
1. Agregue otro botón y establezca su propiedad **[OnSelect](../controls/properties-core.md)** en esta fórmula:<br>
   **ClearCollect( SortByQuantity; SortByColumns( IceCream; "Quantity"; Ascending; "Flavor"; Descending ) )**
   
     La fórmula anterior crea una tercera colección, denominada **SortByQuantity**, que contiene los mismos datos que **IceCream**. Sin embargo, la nueva colección contiene los datos ordenados numéricamente por la columna **Quantity** en orden ascendente y luego por la columna **Flavor** en orden descendente.
2. Presione F5, seleccione el botón nuevo y, luego, presione Esc.
3. Seleccione **Colecciones** en el menú **Archivo** para mostrar las tres colecciones y, luego, presione Esc para volver al área de trabajo predeterminada.
4. Repita los últimos tres pasos, pero cambie el nombre de la colección que desea crear y reemplace la fórmula **SortByColumns** por una fórmula distinta de la tabla de ejemplos que apareció anteriormente en esta sección que usa **SortByColumns**.

