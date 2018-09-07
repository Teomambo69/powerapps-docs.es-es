---
title: Funciones Ordenar y SortByColumns | Microsoft Docs
description: Información de referencia para las funciones Sort y SortByColumns en PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/26/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d3a83f5ae96b8d9146163ed7d5ff4c4529f8d562
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42830780"
---
# <a name="sort-and-sortbycolumns-functions-in-powerapps"></a>Funciones Sort y SortByColumns en PowerApps
Ordena una [tabla](../working-with-tables.md).

## <a name="description"></a>Descripción
La función **Sort** ordena una tabla según una fórmula.  

La fórmula se evalúa para cada [registro](../working-with-tables.md#records) de la tabla y los resultados se usan para ordenar la tabla.  La fórmula debe dar como resultado un número, una cadena o un valor booleano; no puede generar una tabla ni un registro.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

Para ordenar primero por una columna y luego por otra, debe insertar una fórmula **Sort** dentro de otra. Por ejemplo, puede usar esta fórmula para ordenar una tabla **Contacts** primero por una columna **LastName** y, luego, por una columna **FirstName**: **Sort( Sort( Contacts, LastName ), FirstName )**

La función **SortByColumns** también se puede usar para ordenar una tabla según una o más columnas.

La lista de parámetros para **SortByColumns** proporciona los nombres de las columnas según las cuales ordenar y la dirección de ordenación por columna.  La ordenación se realiza según el orden de los parámetros (ordenados primero por la primera columna, luego la segunda, etc.).  Los nombres de columna se especifican como cadenas y requieren comillas dobles si se incluyen directamente en la lista de parámetros.  Por ejemplo, **SortByColumns( CustomerTable, "LastName" )**.

Puede combinar **SortByColumns** con un control **[Menú desplegable](../controls/control-drop-down.md)** o **[Cuadro de lista](../controls/control-list-box.md)** para permitir que los usuarios seleccionen la columna según la cual ordenar.

Además de ordenar de manera ascendente o descendente, **SortByColumns** puede ordenar según una tabla de valores de una sola columna.  Por ejemplo, puede ordenar el registro según el nombre de un día de la semana si suministra **[ "Lunes", "Martes", "Miércoles", "Jueves", "Viernes", "Sábado", "Domingo" ]** como el criterio de ordenación.  Todos los registros que incluyan **Lunes"** aparecerán primero, seguidos de los registros que incluyan **Martes**, etc.  Los registros encontrados que no aparezcan en la tabla de ordenación se colocan al final de la lista.

Las [tablas](../working-with-tables.md) son un valor en PowerApps, tal como una cadena o un número.  Se pueden pasar a funciones y las funciones pueden devolverlas.  **Sort** y **SortByColumn** no modifican una tabla; en lugar de eso, toman una tabla como argumento y devuelven una tabla nueva que se ordenó.  Consulte cómo [trabajar con tablas](../working-with-tables.md) para más detalles.

[!INCLUDE [delegation](../../../includes/delegation.md)]

## <a name="syntax"></a>Sintaxis
**Sort**( *Table*, *Formula* [, *SortOrder* ] )

* *Table*: requerido. La tabla que se va a ordenar.
* *Formula*: requerido. Esta fórmula se evalúa para cada registro de la tabla y los resultados se usan para ordenar la tabla.  Puede hacer referencia a columnas dentro de la tabla.
* *SortOrder*: opcional. Especifique **SortOrder.Descending** para ordenar la tabla en orden descendente. **SortOrder.Ascending** es el valor predeterminado.

**SortByColumns**( *Table*, *ColumnName1* [, *SortOrder1*, *ColumnName2*, *SortOrder2*, ... ] )

* *Table*: requerido. La tabla que se va a ordenar.
* *ColumnName(s)*: requerido. Los nombres de las columnas según las cuales ordenar, como cadenas.
* *SortOrder(s)*: opcional.  **SortOrder.Ascending** o **SortOrder.Descending**.  **SortOrder.Ascending** es el valor predeterminado.  Si se suministran varios *ColumnNames*, todas las columnas, menos la última, deben incluir un *SortOrder*.
  
    > [!NOTE]
  > En el caso de orígenes de datos de SharePoint y Excel que contengan nombres de columna con espacios, especifique cada uno de ellos como **"\_x0020\_"**. Por ejemplo, especifique **"Nombre de columna"** como **"Nombre_x0020_de_columna"**.

**SortByColumns**( *Table*, *ColumnName*, *SortOrderTable* )

* *Table*: requerido. La tabla que se va a ordenar.
* *ColumnName*: requerido. El nombre de la columna según la cual ordenar, como cadenas.
* *SortOrderTable*: requerido.  Tabla de valores de una sola columna según la cual ordenar.
  
    > [!NOTE]
  > En el caso de orígenes de datos de SharePoint y Excel que contengan nombres de columna con espacios, especifique cada uno de ellos como **"\_x0020\_"**. Por ejemplo, especifique **"Nombre de columna"** como **"Nombre_x0020_de_columna"**.

## <a name="examples"></a>Ejemplos
En los ejemplos siguientes, usaremos el [origen de datos](../working-with-data-sources.md) **Helado**, que contiene los datos de esta tabla:

![](media/function-sort/icecream.png)

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Sort( Helado, Sabor )**<br><br>**SortByColumns( Helado, "Sabor" )** |Ordena **Helado** según su columna **Sabor**. La columna **Sabor** contiene cadenas, por lo que la tabla se ordena alfabéticamente. De manera predeterminada, el criterio de ordenación es ascendente. |<style> img { max-width: none; } </style> ![](media/function-sort/icecream-flavor.png) |
| **Sort( Helado, Cantidad )**<br><br>**SortByColumns( Helado, "Cantidad" )** |Ordena **Helado** según su columna **Cantidad**.  La columna **Cantidad** contiene números, por lo que la tabla se ordena numéricamente.  De manera predeterminada, el criterio de ordenación es ascendente. |![](media/function-sort/icecream-quantity-asc.png) |
| **Sort( Helado, Cantidad, SortOrder.Descending )**<br><br>**SortByColumns( Helado, "Cantidad", SortOrder.Descending )** |Ordena **Helado** según su columna **Cantidad**.  La columna **Cantidad** contiene números, por lo que se ordena numéricamente.  El criterio de ordenación se especificó como descendente. |![](media/function-sort/icecream-quantity-desc.png) |
| **Sort( Helado, Cantidad + EnPedido )** |Ordena **Helado** por la suma de sus columnas **Cantidad** y **EnPedido** para cada registro individualmente. La suma es un número, por lo que la tabla se ordena numéricamente.  De manera predeterminada, el criterio de ordenación es ascendente.  Como ordenamos según una fórmula y no según valores de columna sin formato, no hay ningún equivalente usando **SortByColumns**. |![](media/function-sort/icecream-total.png) |
| **Sort( Sort( Helado, EnPedido ), Cantidad )**<br><br>**SortByColumns( Helado, "EnPedido", Ascendente, "Cantidad", Ascendente )** |Ordena **Helado** primero según su columna **EnPedido** y, luego, según su columna **Cantidad**.  Observe que "Pistacho" apareció arriba de "Vainilla" en la primera ordenación según **EnPedido** y, luego, pasaron a su lugar adecuado según **Cantidad**. |![](media/function-sort/icecream-onorder-quantity.png) |
| **SortByColumns( Helado, "Sabor", [&nbsp;"Pistacho",&nbsp;"Fresa"&nbsp;] )** |Ordena **Helado** según su columna **Sabor** en función de la tabla con una sola columna que contiene "Pistacho" y "Fresa".  Los registros que tienen un **Sabor** "Pistacho" aparecerán primero en el resultado, seguidos de los registros que contienen "Fresa".  En el caso de los valores de la columna **Sabor** que no tienen coincidencia, como "Vainilla", aparecerán después de los elementos que sí tuvieron coincidencia. |![](media/function-sort/icecream-onflavor-sorttable.png) |

### <a name="step-by-step"></a>Paso a paso
Para ejecutar estos ejemplos, cree el origen de datos **Helado** como una [colección](../working-with-data-sources.md#collections):

1. Agregue un botón y establezca su propiedad **[OnSelect](../controls/properties-core.md)** en esta fórmula:<br>**ClearCollect( Helado, { Sabor: "Chocolate", Cantidad: 100, EnPedido: 150 }, { Sabor:  "Vainilla", Cantidad: 200, EnPedido: 20 }, { Sabor: "Fresa", Cantidad: 300, EnPedido: 0 }, { Sabor: "Menta-chocolate", Cantidad: 60, EnPedido: 100 }, { Sabor: "Pistacho", Cantidad: 200, EnPedido: 10 } )**
2. Obtenga una vista previa de la aplicación, seleccione el botón y, luego, presione Esc para volver al área de trabajo predeterminada.
3. Seleccione **Colecciones** en el menú **Archivo** para mostrar la colección que acaba de crear y, luego, presione Esc para volver al área de trabajo predeterminada.

#### <a name="sort"></a>Ordenar
1. Agregue otro botón y establezca su propiedad **[OnSelect](../controls/properties-core.md)** en esta fórmula:<br>
   **ClearCollect( SortByFlavor, Sort( IceCream, Flavor ) )**
   
     La fórmula anterior crear otra colección, denominada **SortByFlavor**, que contiene los mismos datos que **Helado**. Sin embargo, la colección nueva contiene los datos ordenados alfabéticamente según la columna **Sabor** en orden ascendente.
2. Presione F5, seleccione el botón nuevo y, luego, presione Esc.
3. Seleccione **Colecciones** en el menú **Archivo** para mostrar ambas colecciones y, luego, presione Esc para volver al área de trabajo predeterminada.
4. Repita los últimos tres pasos, pero cambie el nombre de la colección que desea crear y reemplace la fórmula **Sort** por una fórmula distinta de la tabla de ejemplos que apareció anteriormente en esta sección que usa **Sort**.

#### <a name="sortbycolumns"></a>SortByColumns
1. Agregue otro botón y establezca su propiedad **[OnSelect](../controls/properties-core.md)** en esta fórmula:<br>
   **ClearCollect( SortByQuantity, SortByColumns( IceCream, "Quantity", Ascending, "Flavor", Descending ) )**
   
     La fórmula anterior crea una tercera colección, denominada **SortByQuantity**, que contiene los mismos datos que **Helado**. Sin embargo, la colección nueva contiene los datos ordenados numéricamente según la columna **Cantidad** en orden ascendente y, luego, según la columna **Sabor** en orden descendente.
2. Presione F5, seleccione el botón nuevo y, luego, presione Esc.
3. Seleccione **Colecciones** en el menú **Archivo** para mostrar las tres colecciones y, luego, presione Esc para volver al área de trabajo predeterminada.
4. Repita los últimos tres pasos, pero cambie el nombre de la colección que desea crear y reemplace la fórmula **SortByColumns** por una fórmula distinta de la tabla de ejemplos que apareció anteriormente en esta sección que usa **SortByColumns**.

