---
title: Funciones EndsWith y StartsWith | Microsoft Docs
description: Información de referencia para las funciones EndsWith y StartsWith en PowerApps, incluidos ejemplos y sintaxis
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 07/24/2017
ms.author: gregli
ms.openlocfilehash: c01a69f311378e8e818036c866b96a78f223baf9
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="endswith-and-startswith-functions-in-powerapps"></a>Funciones EndsWith y StartsWith en PowerApps
Comprueba si una cadena de texto comienza o termina con otra cadena de texto.

## <a name="description"></a>Descripción
La función **EndsWith** comprueba si una cadena de texto termina con otra.

La función **StartsWith** comprueba si una cadena de texto comienza con otra.    

Para ambas funciones, las pruebas no distinguen mayúsculas de minúsculas.  El valor devuelto por ambas es un valor booleano **true** o **false**.  

Use **EndsWith** y **StartsWith** con la función **[Filter](function-filter-lookup.md)** para buscar los datos dentro de la aplicación. También puede usar el operador **[in](operators.md#in-and-exactin-operators)** o la función **[Search](function-filter-lookup.md)** para realizar una búsqueda en cualquier lugar dentro de las cadenas de texto, no solo al principio o al final.  La selección de las funciones dependerá de las necesidades de la aplicación y las funciones que se pueden [delegar](../delegation-overview.md) para el origen de datos específico.  Si una de estas funciones no se puede delegar, aparecerá un punto azul en el momento de la creación para avisarle de esta limitación.

## <a name="syntax"></a>Sintaxis
**EndsWith**( *Text*, *EndText* )

* *Texto*: requerido.  Texto que se va a probar.
* *EndText*: requerido.  Texto que desea buscar al final de *Text*.  Si *EndText* es una cadena vacía, **EndsWith** devuelve *true*.

**StartsWith**( *Text*, *StartText* )

* *Texto*: requerido.  Texto que se va a probar.
* *StartText*: requerido.  El texto que desea buscar al principio de *Text*.  Si *StartText* es una cadena vacía, **StartsWith** devuelve *true*.

## <a name="examples"></a>Ejemplos
| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **EndsWith( "Hola mundo", "mundo" )** |Comprueba si **"Hola mundo"** termina con **"mundo"**.  La prueba no distingue mayúsculas de minúsculas. |**true** |
| **EndsWith( "Hasta luego", "hasta" )** |Comprueba si **"Hasta luego"** termina con **"hasta"**.  El argumento *EndText* (**"hasta"**) aparece en el texto, pero no al final. |**false** |
| **EndsWith( "Di siempre hola", "hola" )** |Comprueba si **"Di siempre hola"** termina con **"hola"**. |**true** |
| **Endswith( "Adios", "" )** |Comprueba si **"Adios"** termina con una cadena vacía (**Len** devuelve 0).  Para facilitar su uso en expresiones **Filter**, **EndsWith** está definida para devolver **true** en este caso. |**true** |

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **StartsWith( "Hello World", "hello" )** |Prueba si **"Hello World"** comienza con **"hello"**.  La prueba no distingue mayúsculas de minúsculas. |**true** |
| **StartsWith( "Good bye", "hello" )** |Prueba si **"Good bye"** comienza con **"hello"**. |**false** |
| **StartsWith( "Always say hello", "hello" )** |Prueba si **"Always say hello"** comienza con **"hello"**.  Aunque **"hello"** aparece en el texto, no aparece al principio. |**false** |
| **StartsWith( "Adios", "" )** |Comprueba si **"Adios"** comienza con una cadena vacía (**Len** devuelve 0).  Para facilitar su uso en expresiones **Filter**, **StartsWith** está definida para devolver **true** en este caso. |**true** |

### <a name="search-user-experience"></a>Experiencia de búsqueda del usuario
En muchas aplicaciones, puede escribir uno o varios caracteres en un cuadro de búsqueda para filtrar una lista de registros en un conjunto de datos grande. A medida que escribe, la lista muestra solo los registros que coinciden con los criterios de búsqueda.

Los ejemplos que aparecen en el resto de este tema muestran los resultados de buscar en una lista **Clientes**, que contiene estos datos:

![](media/function-startswith/customers.png)

Para crear este origen de datos como una colección, cree un control **[Botón](../controls/control-button.md)** y establezca la propiedad **AlSeleccionar** en esta fórmula:

**ClearCollect( Clientes, Tabla( { Nombre: "Fred Garcia", Empresa: "Northwind Traders" }, { Nombre: "Cole Miller", Empresa: "Contoso" }, { Nombre: "Glenda Johnson", Empresa: "Contoso" }, { Nombre: "Mike Collins", Empresa: "Adventure Works" }, { Nombre: "Colleen Jones", Empresa: "Adventure Works" } ) )**

Como en este ejemplo, puede mostrar una lista de registros en un [**control Galería**](../controls/control-gallery.md) en la parte inferior de una pantalla. Cerca de la parte superior de la pantalla, puede agregar un control [**Entrada de texto**](../controls/control-text-input.md) denominado **SearchInput**, de modo que los usuarios puedan especificar los registros que más les interesen.

![](media/function-startswith/customers-ux-unfiltered.png)

A medida que el usuario escribe caracteres en **SearchInput**, automáticamente se filtran los resultados en la galería. En este caso, se configura la galería para que muestre los registros para los que el nombre del cliente (no el nombre de la empresa) comienza con la secuencia de caracteres de **SearchInput**. Si el usuario escribe **co** en el cuadro de búsqueda, la galería muestra estos resultados:

![](media/function-startswith/customers-ux-startswith-co.png)

Para filtrar según la columna **Nombre**, establezca la propiedad **Elementos** del control Galería en una de estas fórmulas:

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Filtrar( Clientes, StartsWith( Nombre, SearchInput.Text ) )** |Filtra el origen de datos **Clientes** para los registros en los que la cadena de búsqueda aparece al principio de la columna **Nombre**. La prueba no distingue mayúsculas de minúsculas. Si el usuario escribe **co** en el cuadro de búsqueda, la galería mostrará **Colleen Jones** y **Cole Miller**. La galería no mostrará **Mike Collins** porque la columna **Nombre** de ese registro no comienza por la cadena de búsqueda. |<style> img { max-width: none } </style> ![](media/function-startswith/customers-name-co-startswith.png) |
| **Filtrar( Clientes, SearchInput.Text in Name )** |Filtra el origen de datos **Clientes** para los registros en los que la cadena de búsqueda aparece en cualquier parte de la columna **Nombre**. La prueba no distingue mayúsculas de minúsculas. Si el usuario escribe **co** en el cuadro de búsqueda, la galería mostrará **Colleen Jones,** **Cole Miller** y **Mike Collins** ya que la cadena de búsqueda aparece en algún lugar de la columna **Nombre** de todos esos registros. |<style> img { max-width: none } </style> ![](media/function-startswith/customers-name-co-contains.png) |
| **Buscar( Clientes, SearchInput.Text, "Nombre" )** |De forma parecida al uso del operador **in**, la función **Buscar** busca una coincidencia en cualquier parte de la columna **Nombre** de cada registro. Tenga en cuenta que debe incluir el nombre de la columna entre comillas dobles. |<style> img { max-width: none } </style> ![](media/function-startswith/customers-name-co-contains.png) |

Puede expandir la búsqueda para incluir la columna **Empresa** además de la columna **Nombre**:

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Filtrar( Clientes, StartsWith( Nombre, SearchInput.Text ) &#124;&#124; StartsWith( Empresa, SearchInput.Text ) )** |Filtra el origen de datos **Clientes** de aquellos registros en los que la columna **Nombre** o la columna **Empresa** comienza por la cadena de búsqueda (por ejemplo, **co**).  El operador [**&#124;&#124;** ](operators.md) será *true* si la función **StartsWith** es también *true*. |<style> img { max-width: none } </style> ![](media/function-startswith/customers-all-co-startswith.png) |
| **Filtrar( Clientes, SearchInput.Text en Nombre &#124;&#124; SearchInput.Text en Empresa )** |Filtra el origen de datos **Clientes** de aquellos registros en los que la columna **Nombre** o la columna **Empresa** contienen la cadena de búsqueda en cualquier lugar (por ejemplo, **co**). |<style> img { max-width: none } </style> ![](media/function-startswith/customers-all-co-contains.png) |
| **Buscar( Clientes, SearchInput.Text, "Nombre", "Empresa" )** |De forma parecida al uso del operador **in**, la función **Buscar** busca en el origen de datos **Clientes** aquellos registros en los que la columna **Nombre** o la columna **Empresa** contienen la cadena de búsqueda en cualquier lugar (por ejemplo, **co**). La función **Buscar** es más fácil de leer y escribir que **Filtrar** si desea especificar varias columnas y varios operadores **in**. Tenga en cuenta que debe incluir los nombres de las columnas entre comillas dobles. |<style> img { max-width: none } </style> ![](media/function-startswith/customers-all-co-contains.png) |

