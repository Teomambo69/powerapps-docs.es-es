---
title: Funciones Filter, Search y LookUp | Microsoft Docs
description: Información de referencia para las funciones Filter y LookUp en PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 02/05/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c37aa315981c51a446254473686c44501e72a96f
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63321037"
ms.PowerAppsDecimalTransform: true
---
# <a name="filter-search-and-lookup-functions-in-powerapps"></a>Funciones Filter, Search y LookUp en PowerApps
Busca uno o varios [registros](../working-with-tables.md#records) en una [tabla](../working-with-tables.md).

## <a name="description"></a>Descripción
La función **Filter** busca registros en una tabla que satisface una fórmula.  Use la función **Filter** para buscar un conjunto de registros que coinciden con uno o varios criterios y descartar aquellos que no lo hacen.

La función **LookUp** busca el primer registro de una tabla que satisface una fórmula.  Use **LookUp** para encontrar un único registro que coincida con uno o varios criterios.

En ambos casos, la fórmula se evalúa para cada registro de la tabla.  Los registros que dan como resultado *true* se incluyen en el resultado.  Además de los [operadores](operators.md) de la fórmula normal, puede usar los operadores **[in](operators.md#in-and-exactin-operators)** y **[exactin](operators.md#in-and-exactin-operators)** para las coincidencias de subcadenas.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

La función **Search** busca registros en una tabla que contengan una cadena en una de sus columnas. La cadena puede estar en cualquier lugar dentro de la columna. Por ejemplo, si busca "rob" o "bert" encontrará una coincidencia en una columna que contiene "Roberto". La búsqueda no distingue mayúsculas de minúsculas. A diferencia de **Filter** y **LookUp**, la función **Search** usa solo una cadena de coincidencia en lugar de una fórmula.

**Filter** y **Search** devuelven una tabla que contiene las mismas columnas que la tabla original y los registros que coinciden con los criterios. **LookUp** devuelve solo el primer registro encontrado después de aplicar una fórmula para reducir el registro a un solo valor. Si no se encuentra ningún registro, las funciones **Filter** y **Search** devuelven una tabla [vacía](function-isblank-isempty.md), y **LookUp** devuelve *blank*.  

Las [tablas](../working-with-tables.md) son un valor en PowerApps, tal como una cadena o un número. Se pueden pasar a funciones y las funciones pueden devolverlas.  Las funciones **Filter**, **Search** y **LookUp** no modifican la tabla. En vez de eso, usan la tabla como argumento y devuelven una tabla, un registro o un solo valor de ella. Consulte cómo [trabajar con tablas](../working-with-tables.md) para más detalles.

[!INCLUDE [delegation](../../../includes/delegation.md)]

## <a name="syntax"></a>Sintaxis
**Filter**( *Table*; *Formula1* [; *Formula2*; ... ] )

* *Table*: requerido. La tabla en la que se va a buscar.
* *Formula(s)*: requerido. La fórmula por la que se evalúa cada registro de la tabla. La función devuelve todos los registros cuyo resultado es **true**. Puede hacer referencia a columnas dentro de la tabla. Si se proporciona más de una fórmula, los resultados de todas las fórmulas se combinan con la función **[And](function-logicals.md)**.

**Search**( *Table*; *SearchString*; *Column1* [; *Column2*; ... ] )

* *Table*: requerido. La tabla en la que se va a buscar.
* *SearchString*: requerido. La cadena que se va a buscar. Si es *blank* o es una cadena vacía, se devolverán todos los registros.
* *Column(s)*: requerido. Los nombres de las columnas dentro de *Table* que se van a buscar. Las columnas en las que se va a buscar deben contener texto. Los nombres de las columnas deben ser cadenas e ir entre comillas dobles. Sin embargo, los nombres de las columnas deben ser estáticos y no se pueden calcular con una fórmula. Si se encuentra *SearchString* dentro de los datos de cualquiera de estas columnas como una coincidencia parcial, se devolverá el registro completo.

> [!NOTE]
> En el caso de orígenes de datos de SharePoint y Excel que contengan nombres de columna con espacios, especifique cada uno de ellos como **"\_x0020\_"**. Por ejemplo, especifique **"Nombre de columna"** como **"Nombre_x0020_de_columna"**.

**LookUp**( *Table*; *Formula* [; *ReductionFormula* ] )

* *Table*: requerido. La tabla en la que se va a buscar. En la interfaz de usuario, la sintaxis se muestra como *origen* encima del cuadro de función.
* *Formula*: requerido.
  La fórmula por la que se evalúa cada registro de la tabla. La función devuelve el primer registro cuyo resultado es **true**. Puede hacer referencia a columnas dentro de la tabla. En la interfaz de usuario, la sintaxis se muestra como *condición* encima del cuadro de función.
* *ReductionFormula*: opcional. Esta fórmula se evalúa en el registro que se ha encontrado y luego el registro se reduce a un valor único. Puede hacer referencia a columnas dentro de la tabla. Si no se usa este parámetro, la función devuelve el registro completo de la tabla. En la interfaz de usuario, la sintaxis se muestra como *resultado* encima del cuadro de función.

## <a name="examples"></a>Ejemplos
Los ejemplos siguientes usan el [origen de datos](../working-with-data-sources.md) **IceCream**:

![](media/function-filter-lookup/icecream.png)

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Filter( IceCream; OnOrder > 0 )** |Devuelve aquellos registros en los que **OnOrder** es mayor que cero. |<style> img { max-width: none; } </style> ![](media/function-filter-lookup/icecream-onorder.png) |
| **Filter( IceCream; Quantity + OnOrder > 225 )** |Devuelve aquellos registros en los que la suma de las columnas **Cantidad** y **OnOrder** es mayor que 225. |![](media/function-filter-lookup/icecream-overstock.png) |
| **Filter( IceCream; "chocolate" in Lower( Flavor ) )** |Devuelve aquellos registros donde aparece la palabra "chocolate" en el nombre **Flavor**, sin tener en cuenta mayúsculas o minúsculas. |![](media/function-filter-lookup/icecream-chocolate.png) |
| **Filter( IceCream; Quantity < 10  && OnOrder < 20 )** |Devuelve aquellos registros donde la **cantidad** es menor que 10 y la cantidad **OnOrder** es menor que 20.  No hay registros que coincidan con estos criterios, por lo que se devolverá una tabla vacía. |![](media/function-filter-lookup/icecream-empty.png) |
| **Search( IceCream; "choc"; "Flavor" )** |Devuelve aquellos registros donde aparece la cadena "choc" en el nombre **Flavor**, sin tener en cuenta mayúsculas o minúsculas. |![](media/function-filter-lookup/icecream-chocolate.png) |
| **Search( IceCream; ""; "Flavor" )** |Dado que el término de búsqueda está vacío, se devolverán todos los registros. |![](media/function-filter-lookup/icecream.png) |
| **LookUp( IceCream; Flavor = "Chocolate"; Quantity )** |Busca un registro cuyo valor de **Flavor** sea igual a "Chocolate". En este caso, devuelve uno.  Para el primer registro que se encuentra, devuelve el valor de **Cantidad** de ese registro. |100 |
| **LookUp( IceCream; Quantity > 150; Quantity + OnOrder )** |Busca un registro cuyo valor de **Quantity** sea mayor que 100. En este caso, devuelve varios.  Para el primer registro que se encuentra, que es el **Flavor** "Vanilla", devuelve la suma de las columnas **Quantity** y **OnOrder**. |250 |
| **LookUp( IceCream; Flavor = "Pistachio"; OnOrder )** |Busca un registro cuyo valor de **Flavor** sea igual a "Pistachio". En este caso no devuelve ninguno.  Como no se encontró ninguno, **Búsqueda** devuelve *blank*. |*blank* |
| **LookUp( IceCream; Flavor = "Vanilla" )** |Busca un registro cuyo valor de **Flavor** sea igual a "Vanilla". En este caso, devuelve uno.  Como no se proporcionó ninguna fórmula de reducción, se devuelve todo el registro. |{Sabor: "Vanilla", cantidad: 200, OnOrder: 75 } |

### <a name="search-user-experience"></a>Experiencia de búsqueda del usuario
En muchas aplicaciones, puede escribir uno o varios caracteres en un cuadro de búsqueda para filtrar una lista de registros en un conjunto de datos grande. A medida que escribe, la lista muestra solo los registros que coinciden con los criterios de búsqueda.

Los ejemplos que aparecen en el resto de este tema muestran los resultados de buscar en una lista, denominada **Clientes**, que contiene estos datos:

![](media/function-filter-lookup/customers.png)

Para crear este origen de datos como una colección, cree un control **[Botón](../controls/control-button.md)** y establezca la propiedad **OnSelect** en esta fórmula:

**ClearCollect (clientes; tabla ({nombre: "Fred Garcia"; empresa: "Northwind Traders"}; {nombre: "Cole Miller"; empresa: "Contoso"}; {nombre: "Glenda Johnson"; empresa: "Contoso"}; {nombre: "Mike Collins"; empresa: "Adventure Works"}; {nombre: "Colleen Jones"; empresa: "Adventure Works" } ) )**

Como en este ejemplo, puede mostrar una lista de registros en un [**control Galería**](../controls/control-gallery.md) en la parte inferior de una pantalla. Cerca de la parte superior de la pantalla, puede agregar un control [**Entrada de texto**](../controls/control-text-input.md) denominado **SearchInput**, de modo que los usuarios puedan especificar los registros que más les interesen.

![](media/function-filter-lookup/customers-ux-unfiltered.png)

A medida que el usuario escribe caracteres en **SearchInput**, automáticamente se filtran los resultados en la galería. En este caso, se configura la galería para que muestre los registros para los que el nombre del cliente (no el nombre de la empresa) comienza con la secuencia de caracteres de **SearchInput**. Si el usuario escribe **co** en el cuadro de búsqueda, la galería muestra estos resultados:

![](media/function-filter-lookup/customers-ux-startswith-co.png)

Para filtrar según la columna **Nombre**, establezca la propiedad **Elementos** del control Galería en una de estas fórmulas:

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Filter( Customers; StartsWith( Name; SearchInput.Text ) )** |Filtra el origen de datos **Clientes** para los registros en los que la cadena de búsqueda aparece al principio de la columna **Nombre**. La prueba no distingue mayúsculas de minúsculas. Si el usuario escribe **co** en el cuadro de búsqueda, la galería mostrará **Colleen Jones** y **Cole Miller**. La galería no mostrará **Mike Collins** porque la columna **Nombre** de ese registro no comienza por la cadena de búsqueda. |<style> img { max-width: none } </style> ![](media/function-filter-lookup/customers-name-co-startswith.png) |
| **Filter( Customers; SearchInput.Text in Name )** |Filtra el origen de datos **Clientes** para los registros en los que la cadena de búsqueda aparece en cualquier parte de la columna **Nombre**. La prueba no distingue mayúsculas de minúsculas. Si el usuario escribe **co** en el cuadro de búsqueda, la galería mostrará **Colleen Jones,** **Cole Miller** y **Mike Collins** ya que la cadena de búsqueda aparece en algún lugar de la columna **Nombre** de todos esos registros. |<style> img { max-width: none } </style> ![](media/function-filter-lookup/customers-name-co-contains.png) |
| **Search( Customers; SearchInput.Text; "Name" )** |De forma parecida al uso del operador **in**, la función **Search** busca una coincidencia en cualquier parte de la columna **Nombre** de cada registro. Tenga en cuenta que debe incluir el nombre de la columna entre comillas dobles. |<style> img { max-width: none } </style> ![](media/function-filter-lookup/customers-name-co-contains.png) |

Puede expandir la búsqueda para incluir la columna **Empresa** además de la columna **Nombre**:

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Filter( Customers; StartsWith( Name; SearchInput.Text ) &#124;;&#124;; StartsWith( Company; SearchInput.Text ) )** |Filtra el origen de datos **Clientes** de aquellos registros en los que la columna **Nombre** o la columna **Empresa** comienza por la cadena de búsqueda (por ejemplo, **co**).  El operador [**&#124;&#124;** ](operators.md) será *true* si la función **StartsWith** es también *true*. |<style> img { max-width: none } </style> ![](media/function-filter-lookup/customers-all-co-startswith.png) |
| **Filter( Customers; SearchInput.Text in Name &#124;;&#124;; SearchInput.Text in Company )** |Filtra el origen de datos **Clientes** de aquellos registros en los que la columna **Nombre** o la columna **Empresa** contienen la cadena de búsqueda en cualquier lugar (por ejemplo, **co**). |<style> img { max-width: none } </style> ![](media/function-filter-lookup/customers-all-co-contains.png) |
| **Search( Customers; SearchInput.Text; "Name"; "Company" )** |De forma parecida al uso del operador **in**, la función **Search** busca en el origen de datos **Customers** aquellos registros en los que la columna **Name** o la columna **Company** contienen la cadena de búsqueda en cualquier lugar (por ejemplo, **co**). La función **Search** es más fácil de leer y escribir que **Filter** si desea especificar varias columnas y varios operadores **in**. Tenga en cuenta que debe incluir los nombres de las columnas entre comillas dobles. |<style> img { max-width: none } </style> ![](media/function-filter-lookup/customers-all-co-contains.png) |

