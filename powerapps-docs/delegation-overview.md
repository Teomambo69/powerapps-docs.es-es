---
title: "Descripción de delegación | Microsoft Docs"
description: "La delegación se usa para procesar eficazmente grandes conjuntos de datos."
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
ms.date: 08/15/2017
ms.author: gregli
ms.openlocfilehash: d4305884c14a4b85b2ed992a5df13a7d3bb2baa7
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="understand-delegation"></a>Descripción de delegación
PowerApps incluye un eficaz conjunto de funciones para filtrar, ordenar y dar forma a tablas de datos:  las funciones **[Filtrar](functions/function-filter-lookup.md)**, **[Ordenar](functions/function-sort.md)** y **[AddColumns](functions/function-table-shaping.md)** son solo algunas de ellas.  Con estas funciones puede proporcionar a los usuarios acceso a la información que necesitan.  Para quienes conozcan bien las bases de datos, el uso de estas funciones es como escribir una consulta de base de datos.  

La clave para compilar aplicaciones eficientes es minimizar la cantidad de datos que debe contener el dispositivo.  Quizás se necesiten solo unos pocos registros de un mar de millones o que un único valor agregado pueda representar miles de registros.  O quizás solo se pueda recuperar el primer conjunto de registros, y el resto se trae cuando el usuario indica que desea más.  De esta forma se puede reducir drásticamente la potencia de procesamiento, la memoria y el ancho de banda de red que necesita la aplicación, lo que conlleva menores tiempos de respuesta para los usuarios, incluso en teléfonos conectados a través de una red móvil.  

La *delegación* es el lugar en el que la expresividad de las fórmulas de PowerApps cubre la necesidad de minimizar la cantidad de datos que se mueven a través de la red.  En resumen, significa que PowerApps delegará el procesamiento de los datos al origen de los mismos, en lugar de moverlos a la aplicación para que los procese localmente.  

Esto se complica, y el motivo por el que existe este artículo, porque no todo lo que se puede expresar en una fórmula de PowerApps puede delegarse a todos los orígenes de datos.  El lenguaje de PowerApps imita el lenguaje de fórmulas de Excel, que se está diseñado con acceso completo e instantáneo a un libro completo en la memoria, con una amplia variedad de funciones numéricas y de manipulación de texto.  Como consecuencia, el lenguaje de PowerApps es mucho complejo de lo que la mayoría de orígenes de datos pueden admitir, incluidos motores de base de datos eficaces como SQL Server.

**El trabajo con grandes conjuntos de datos requiere que se usen orígenes de datos y fórmulas que se puedan delegar.**  Es la única manera de que la aplicación funcione correctamente y de tener la certeza de que los usuarios pueden acceder a toda la información que necesitan. Siga las [sugerencias de los puntos azules](delegation-overview.md#blue-dot-suggestions) que marcan los lugares en los que no es posible la delegación.  Si trabaja con conjuntos de datos pequeños (menos de 500 registros), puede utilizar cualquier origen de datos y cualquier fórmula, ya que el procesamiento se puede realizar localmente si la fórmula no se puede delegar.  

## <a name="delegable-data-sources"></a>Orígenes de datos delegables
En la [lista de delegación](delegation-list.md) se encuentran todos los orígenes de datos que admiten la delegación orígenes y en hasta qué punto lo hacen.

A continuación agregaremos compatibilidad con la delegación a los orígenes de datos existentes y agregaremos más orígenes de datos.

Los libros de Excel importados (que usan el origen de datos "Agregar datos estáticos a la aplicación"), las colecciones y las tablas almacenadas en variables de contexto no requieren delegación. Todos estos datos ya están en la memoria y se puede aplicar el lenguaje de PowerApps completo.

## <a name="delegable-functions"></a>Funciones que se pueden delegar
El siguiente paso es usar solo aquellas fórmulas que se puedan delegar. Aquí se incluyen los elementos de las fórmulas que se pueden delegar.  Sin embargo, todos los orígenes de datos son diferentes, y no todos ellos admiten todos estos elementos. Consulte las sugerencias de los puntos azules de su fórmula concreta.

Estas listas cambiarán con el tiempo, ya que en el futuro habrá más funciones y operadores que admitan la delegación.

### <a name="filter-functions"></a>Funciones de filtro
**[Filtrar](functions/function-filter-lookup.md)**, **[Buscar](functions/function-filter-lookup.md)** y **[Búsqueda](functions/function-filter-lookup.md)** se pueden delegar.  

En las funciones **Filtrar** y **Buscar**, se puede usar lo siguiente en las columnas de la tabla para seleccionar los registros apropiados:

* **[And](functions/function-logicals.md)** (incluyendo **[&&](functions/operators.md)**), **[Or](functions/function-logicals.md)** (incluyendo **[||](functions/operators.md)**), **[Not](functions/function-logicals.md)** (incluyendo **[!](functions/operators.md)** )
* **[In (En)](functions/operators.md)**
* **[=](functions/operators.md)**, **[<>](functions/operators.md)**, **[>=](functions/operators.md)**, **[<=](functions/operators.md)**, **[>](functions/operators.md)**, **[<](functions/operators.md)**
* **[+](functions/operators.md)**, **[-](functions/operators.md)**
* **[TrimEnds (RecortarExtr)](functions/function-trim.md)**
* **[EsBlanco](functions/function-isblank-isempty.md)**
* **[StartsWith (EmpiezaPor)](functions/function-startswith.md)**
* Valores constantes que son iguales en todos los registros, como las propiedades del control y [las variables globales y de contexto](working-with-variables.md).

También se pueden utilizar las partes de la fórmula que se evalúan como un valor constante para todos los registros.  Por ejemplo, **Izquierda (Lenguaje(), 2)** no depende de ninguna columna del registro y, por tanto, devuelve el mismo valor para todos los registros.  Efectivamente es una constante.  El uso de variables de contexto, colecciones y señales puede no ser constante y, por tanto, impedirá la delegación de **Filtrar** y **Buscar**.  

Algunos elementos importantes que faltan en la lista anterior:

* **[If (Si)](functions/function-if.md)**
* **[*](functions/operators.md)**, **[/](functions/operators.md)**, **[Mod](functions/function-mod.md)**
* **[Concatenar](functions/function-concatenate.md)** (incluyendo **[&](functions/operators.md)**)
* **[ExactIn (ExactoEn)](functions/operators.md)**
* Funciones de manipulación de cadenas: **[Minusc](functions/function-lower-upper-proper.md)**, **[Mayusc](functions/function-lower-upper-proper.md)**, **[Izquierda](functions/function-left-mid-right.md)**, **[Extrae](functions/function-left-mid-right.md)**, **[Largo](functions/function-left-mid-right.md)**, ...
* Señales: **[Ubicación](functions/signals.md)**, **[Aceleración](functions/signals.md)**, **[Brújula](functions/signals.md)**, ...
* Volátiles: **[Ahora](functions/function-now-today-istoday.md)**, **[Hoy](functions/function-now-today-istoday.md)**, **[Casual](functions/function-rand.md)**, ...
* [Colecciones](working-with-variables.md)

### <a name="sorting-functions"></a>Funciones de ordenación
**[Ordenar](functions/function-sort.md)** y **[SortByColumns (OrdenarPorColumnas)](functions/function-sort.md)** se pueden delegar.  

En **Ordenar**, la fórmula solo puede ser el nombre de una columna individual y no puede incluir otros operadores o funciones.

### <a name="aggregate-functions"></a>Funciones de agregado
**[Suma](functions/function-aggregates.md)**,  **[Promedio](functions/function-aggregates.md)**,  **[Min](functions/function-aggregates.md)** y  **[Max](functions/function-aggregates.md)**  pueden delegarse.  En este momento, solo un número limitado de orígenes de datos admite esta delegación. Para más información, consulte la [lista de delegación](delegation-list.md).

Las funciones de recuento como  **[CountRows (ContarFilas)](functions/function-table-counts.md)**, **[ContarA](functions/function-table-counts.md)** y **[Contar](functions/function-table-counts.md)** no se pueden delegar.

Otras funciones de agregado, como **[StdevP](functions/function-aggregates.md)** y **[VarP](functions/function-aggregates.md)**, no se pueden delegar.

### <a name="other-functions"></a>Otras funciones
Las restantes funciones, entre las que se incluyen las siguientes, no admiten la delegación:

* Forma de tabla: **[AddColumns](functions/function-table-shaping.md)**, **[DropColumns](functions/function-table-shaping.md)**, **[ShowColumns](functions/function-table-shaping.md)**, ...
* **[Primero](functions/function-first-last.md)**, **[FirstN](functions/function-first-last.md)**, **[Último](functions/function-first-last.md)**, **[LastN](functions/function-first-last.md)**
* **[Concat](functions/function-concatenate.md)**
* **[Recopilar](functions/function-clear-collect-clearcollect.md)**, **[ClearCollect](functions/function-clear-collect-clearcollect.md)**
* **[CountIf](functions/function-table-counts.md)**, **[RemoveIf](functions/function-remove-removeif.md)**, **[UpdateIf](functions/function-update-updateif.md)**
* **[GroupBy](functions/function-groupby.md)**, **[Desagrupar](functions/function-groupby.md)**

Un patrón habitual consiste en usar **AddColumns** y **Buscar** para combinar información de una tabla con la de otra, lo que suele conocerse como una combinación en el lenguaje de base de datos.  Por ejemplo:

* **AddColumns( Products, "Supplier Name", LookUp( Suppliers, Suppliers.ID = Product.SupplierID ).Name )**

Aunque **Products** y **Suppliers** pueden ser orígenes de datos delegables y **Buscar** es una función delegable, la función **AddColumns** no se puede delegar.  El resultado de la fórmula completa se limitará a la primera parte del origen de datos **Products**.  

Dado que **Buscar** y su origen de datos se pueden delegar, se puede encontrar una coincidencia con **Suppliers** en cualquier lugar del origen de datos, aunque sea grande.  Un posible inconveniente es que **Buscar** realizará llamadas al origen de datos en todos los primeros registros de **Products**, lo que provocará mucha charla en la red.  Si **Suppliers** es suficientemente pequeño y no cambia con frecuencia, puede almacenar en la memoria caché el origen de datos en su aplicación con una llamada **Recopilar** cuando se inicia la aplicación (para lo que se usa [**AlEstarVisible**](controls/control-screen.md) en la pantalla inicial) y usar **Buscar** en su lugar.  

## <a name="non-delegable-limits"></a>Límites no delegables
Las fórmulas que no se puede delegar se procesarán localmente.  Esto permite usar todo el espectro del lenguaje de fórmulas de PowerApps.  Pero esto tiene un precio: primero deben pasarse todos los datos al dispositivo, lo que podría implicar la recuperación de una gran cantidad de datos a través de la red.  Esta operación puede tardar un tiempo, lo que daría la impresión de que la aplicación se ejecuta con lentitud, o incluso que está bloqueada.

Para evitarlo, PowerApps impone un límite en la cantidad de datos que se pueden procesar localmente: 500 registros.  Elegimos este número para que tuviera acceso completo a los conjuntos de datos pequeños y pudiera pueda refinar su uso de conjuntos de datos grandes viendo los resultados parciales.

Obviamente si se usa este recurso es preciso tener cuidado, ya que puede ser confuso para los usuarios.  Por ejemplo, considere una función **Filtrar** función con una fórmula de selección que no se puede delegar y con un origen de datos de más de un millón de registros.  Como el filtrado se realizará localmente, solo se examinarán los primeros 500 registros.  Si el registro deseado es el 501, o el 500 001, **Filtrar** no lo tendrá en cuenta o no lo devolverá.

Otro lugar en el que puede producirse confusión son las funciones de agregado.  Tomemos como ejemplo **Promedio** en una columna con el mismo origen de datos de un millón de registros.  Como **Promedio** aún no se puede delegar, solo se obtendrá el promedio de los primeros 500 registros.  Se debe tener cuidado, ya que algún usuario de la aplicación podría malinterpretar una respuesta parcial como una respuesta completa.

## <a name="blue-dot-suggestions"></a>Sugerencias de puntos azules
Para que sea más fácil saber lo que se va a delegar y lo que no, se proporciona sugerencias de puntos azules cuando una fórmula algo que no se puede delegar.

Los puntos azules solo se muestran en las fórmulas que operan en orígenes de datos delegables.  Si no ve un punto azul y cree que la fórmula no se delega correctamente, compruebe el tipo de origen de datos en la lista anterior de <a href="#delegable-data-sources">orígenes de datos que se pueden delegar</a>.

## <a name="examples"></a>Ejemplos
En este ejemplo, usaremos una tabla de SQL Server que contiene productos, en concreto frutas, nombres **[dbo]. [ Products]**.  En la pantalla nueva, PowerApps puede crear una aplicación básica de tres pantallas conectada a este origen de datos:

![](media/delegation-overview/products-afd.png)

Tenga en cuenta la fórmula de la propiedad **Elementos** de la galería.  Usa las funciones **SortByColumns** y **Buscar**, que se pueden delegar.

Vamos a escribir **"Manzana"** en el control de entrada de texto de búsqueda.  Si estamos muy atentos, veremos durante un instante unos puntos que se mueven en la parte superior de la pantalla mientras se procesa la nueva entrada de la nueva búsqueda.  Dichos puntos indican que hay comunicación con el servidor SQL Server:

![](media/delegation-overview/products-apple.png)

Dado que todo esto se puede delegar, aunque si la tabla **[dbo]. [ Products]** contiene millones de registros, se seguirán encontrando todos, para lo que nos desplazamos por la galería a medida que el usuario se desplaza por los resultados.

Observará que aparece una coincidencia para "Manzana" y "Piña".  La función **Buscar** encontrará un término de búsqueda en cualquier parte de una columna de texto.  Sin embargo, supongamos que solo deseamos buscar el término de búsqueda únicamente al principio del nombre de fruta.  Podemos usar otra función que se puede delegar, **Filtrar**, con un término de búsqueda más complicado (por motivos de simplicidad quitaremos la llamada a **SortByColumns**):

![](media/delegation-overview/products-apple-bluedot.png)

Ahora solo se muestra **"Manzanas"**, pero no **"Piña"**.  Sin embargo, se muestra un punto azul al lado de la galería y hay una línea ondulada de azul debajo de una parte de la fórmula.  Incluso aparece un punto azul en la miniatura de la pantalla.  Si se mantiene el puntero sobre el punto azul que hay al lado de la galería, se ve lo siguiente:

![](media/delegation-overview/products-apple-bluepopup.png)

Aunque usamos **Filtrar**, que es una función delegable, con SQL Server, que es un origen de datos que se puede delegar, la fórmula que se utilizó en **Filtrar** no se puede delegar.  **Extrae** y **Largo** no se pueden delegar en ningún origen de datos.

Pero ha funcionado, ¿no?  Bueno, más o menos.  Por eso aparece un punto azul, en lugar de un icono de peligro amarillo y una línea ondulada roja de error.  Si la tabla **[dbo]. [ Products]** contiene menos de 500 registros, ha funcionado perfectamente.   Todos los registros han pasado al dispositivo y **Filtrar** se ha aplicado localmente.  

Si la tabla contiene más de 500 registros, en la galería solo se mostrará la fruta que empiezan por **"Manzana"** *en los primeros 500 registros de la tabla*.  Si **"Manzana, Fuji"** aparece como nombre en los registros 501 o 500 001, no se encontrará.

