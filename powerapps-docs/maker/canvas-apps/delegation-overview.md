---
title: Descripción de delegación | Microsoft Docs
description: La delegación se usa para procesar eficazmente grandes conjuntos de datos.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 07/05/2018
ms.author: lanced
ms.openlocfilehash: 484d7b1149f158840238fc3d54713a1e6e33443b
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39023606"
---
# <a name="understand-delegation"></a>Descripción de delegación
PowerApps incluye un eficaz conjunto de funciones para filtrar, ordenar y dar forma a tablas de datos: las funciones **[Filter](functions/function-filter-lookup.md)**, **[Sort](functions/function-sort.md)** y **[AddColumns](functions/function-table-shaping.md)** son solo algunas de ellas. Con estas funciones puede proporcionar a los usuarios acceso a la información que necesitan. Para quienes conozcan bien las bases de datos, el uso de estas funciones es como escribir una consulta de base de datos.

La clave para compilar aplicaciones eficientes es minimizar la cantidad de datos que debe contener el dispositivo. Quizás necesite solo unos pocos registros de un mar de millones o que un único valor agregado pueda representar miles de registros. O quizás solo se pueda recuperar el primer conjunto de registros, y el resto se trae cuando el usuario indica que desea más. De esta forma se puede reducir drásticamente la potencia de procesamiento, la memoria y el ancho de banda de red que necesita la aplicación, lo que conlleva menores tiempos de respuesta para los usuarios, incluso en teléfonos conectados a través de una red móvil. 

La *delegación* es el lugar en el que la expresividad de las fórmulas de PowerApps cubre la necesidad de minimizar la cantidad de datos que se mueven a través de la red. En resumen, PowerApps delega el procesamiento de los datos al origen de los mismos, en lugar de moverlos a la aplicación para que los procese localmente.

Esto se complica, y el motivo por el que existe este artículo, porque no todo lo que se puede expresar en una fórmula de PowerApps puede delegarse a todos los orígenes de datos. El lenguaje de PowerApps imita el lenguaje de fórmulas de Excel, que se está diseñado con acceso completo e instantáneo a un libro completo en la memoria, con una amplia variedad de funciones numéricas y de manipulación de texto. Como consecuencia, el lenguaje de PowerApps es mucho complejo de lo que la mayoría de orígenes de datos pueden admitir, incluidos motores de base de datos eficaces como SQL Server.

**El trabajo con grandes conjuntos de datos requiere que se usen orígenes de datos y fórmulas que se puedan delegar.**  Es la única manera de que la aplicación funcione correctamente y de tener la certeza de que los usuarios pueden acceder a toda la información que necesitan. Preste atención a las advertencias de delegación que identifiquen lugares donde esta no es posible. Si trabaja con conjuntos de datos pequeños (menos de 500 registros), puede usar cualquier origen de datos y cualquier fórmula, ya que la aplicación puede procesar datos en local si la fórmula no se puede delegar. 

> [!NOTE]
> Anteriormente las advertencias de delegación se marcaban en PowerApps como sugerencias de "punto azul", pero desde entonces las sugerencias de delegación se han reclasificado como advertencias. Si los datos del origen de datos superan los 500 registros y no se puede delegar una función, quizás PowerApps no pueda recuperar todos los datos y la aplicación pueda tener resultados incorrectos. Las advertencias de delegación permiten administrar la aplicación para que tenga resultados correctos.

## <a name="delegable-data-sources"></a>Orígenes de datos delegables
En la [lista de delegación](delegation-list.md) se encuentran todos los orígenes de datos que admiten la delegación orígenes y en hasta qué punto lo hacen.

A continuación agregaremos compatibilidad con la delegación a los orígenes de datos existentes y agregaremos más orígenes de datos.

Los libros de Excel importados (que usan el origen de datos "Agregar datos estáticos a la aplicación"), las colecciones y las tablas almacenadas en variables de contexto no requieren delegación. Todos estos datos ya están en la memoria y se puede aplicar el lenguaje de PowerApps completo.

## <a name="delegable-functions"></a>Funciones que se pueden delegar
El siguiente paso es usar solo aquellas fórmulas que se puedan delegar. Aquí se incluyen los elementos de las fórmulas que se pueden delegar. Sin embargo, todos los orígenes de datos son diferentes, y no todos ellos admiten todos estos elementos. Compruebe si hay advertencias de delegación en la fórmula en cuestión.

Estas listas cambiarán con el tiempo, ya que en el futuro habrá más funciones y operadores que admitan la delegación.

### <a name="filter-functions"></a>Funciones de filtro
**[Filtrar](functions/function-filter-lookup.md)**, **[Buscar](functions/function-filter-lookup.md)** y **[Búsqueda](functions/function-filter-lookup.md)** se pueden delegar.  

Las funciones **Filter** y **LookUp** se pueden usar con columnas de la tabla para seleccionar los registros apropiados:

* **[And](functions/function-logicals.md)** (incluyendo **[&&](functions/operators.md)**), **[Or](functions/function-logicals.md)** (incluyendo **[||](functions/operators.md)**), **[Not](functions/function-logicals.md)** (incluyendo **[!](functions/operators.md)** )
* **[In (En)](functions/operators.md)**
* **[=](functions/operators.md)**, **[<>](functions/operators.md)**, **[>=](functions/operators.md)**, **[<=](functions/operators.md)**, **[>](functions/operators.md)**, **[<](functions/operators.md)**
* **[+](functions/operators.md)**, **[-](functions/operators.md)**
* **[TrimEnds (RecortarExtr)](functions/function-trim.md)**
* **[EsBlanco](functions/function-isblank-isempty.md)**
* **[StartsWith (EmpiezaPor)](functions/function-startswith.md)**
* Valores constantes que son iguales en todos los registros, como las propiedades del control y [las variables globales y de contexto](working-with-variables.md).

También se pueden usar partes de la fórmula que se evalúen en un valor constante para todos los registros. Por ejemplo, **Left( Language(), 2 )** no depende de ninguna columna del registro y, por tanto, devuelve el mismo valor para todos los registros. Efectivamente es una constante. El uso de variables de contexto, colecciones y señales puede no ser constante y, por tanto, evita la delegación de **Filter** y **LookUp**.  

La lista anterior no incluye estos elementos importantes:

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
**[Suma](functions/function-aggregates.md)**,  **[Promedio](functions/function-aggregates.md)**,  **[Min](functions/function-aggregates.md)** y **[Max](functions/function-aggregates.md)** pueden delegarse. En este momento, solo un número limitado de orígenes de datos admite esta delegación. Para obtener más detalles, vea la [lista de delegación](delegation-list.md).

Las funciones de recuento como **[CountRows](functions/function-table-counts.md)**, **[CountA](functions/function-table-counts.md)** y **[Count](functions/function-table-counts.md)** no se pueden delegar.

Otras funciones de agregado, como **[StdevP](functions/function-aggregates.md)** y **[VarP](functions/function-aggregates.md)**, no se pueden delegar.

## <a name="non-delegable-functions"></a>Funciones no delegables
Las demás funciones no admiten la delegación, incluidas estas importantes funciones:

* Forma de tabla: **[AddColumns](functions/function-table-shaping.md)**, **[DropColumns](functions/function-table-shaping.md)**, **[ShowColumns](functions/function-table-shaping.md)**, ...
* **[Primero](functions/function-first-last.md)**, **[FirstN](functions/function-first-last.md)**, **[Último](functions/function-first-last.md)**, **[LastN](functions/function-first-last.md)**
* **[Choices](functions/function-choices.md)**
* **[Concat](functions/function-concatenate.md)**
* **[Recopilar](functions/function-clear-collect-clearcollect.md)**, **[ClearCollect](functions/function-clear-collect-clearcollect.md)**
* **[CountIf](functions/function-table-counts.md)**, **[RemoveIf](functions/function-remove-removeif.md)**, **[UpdateIf](functions/function-update-updateif.md)**
* **[GroupBy](functions/function-groupby.md)**, **[Desagrupar](functions/function-groupby.md)**

Un patrón habitual consiste en usar **AddColumns** y **Buscar** para combinar información de una tabla con la de otra, lo que suele conocerse como una combinación en el lenguaje de base de datos.  Por ejemplo:

**AddColumns( Products, "Supplier Name", LookUp( Suppliers, Suppliers.ID = Product.SupplierID ).Name )**

Aunque **Products** y **Suppliers** pueden ser orígenes de datos delegables y **LookUp** es una función delegable, la función **AddColumns** no se puede delegar.  El resultado de la fórmula completa se limitará a la primera parte del origen de datos **Products**.  

Dado que la función **LookUp** y su origen de datos se pueden delegar, se puede encontrar una coincidencia con **Suppliers** en cualquier lugar del origen de datos, aunque sea grande. Un posible inconveniente es que **LookUp** realizará llamadas independientes al origen de datos en todos los primeros registros de **Products**, lo que provocará mucha charla en la red. Si **Suppliers** es suficientemente pequeño y no cambia con frecuencia, puede almacenar en la memoria caché de la aplicación el origen de datos con una llamada **Collect** cuando se inicia la aplicación (para lo que se usa [**OnVisible**](controls/control-screen.md) en la pantalla inicial) y usar **LookUp** en su lugar.  

## <a name="non-delegable-limits"></a>Límites no delegables
Las fórmulas que no se pueden delegar se procesan localmente. Esto permite usar todo el espectro del lenguaje de fórmulas de PowerApps. Pero esto tiene un precio: primero deben pasarse todos los datos al dispositivo, lo que podría implicar la recuperación de una gran cantidad de datos a través de la red. Esta operación puede tardar un tiempo, lo que daría la impresión de que la aplicación se ejecuta con lentitud, o incluso que está bloqueada.

Para evitarlo, PowerApps impone un límite en la cantidad de datos que se pueden procesar localmente: 500 registros de forma predeterminada.  Elegimos este número para que tuviera acceso completo a los conjuntos de datos pequeños y pudiera pueda refinar su uso de conjuntos de datos grandes viendo los resultados parciales.

Obviamente, si se usa este recurso, es preciso tener cuidado, ya que puede confundir a los usuarios. Por ejemplo, imagine una función **Filter** con una fórmula de selección que no se puede delegar en lugar de un origen de datos que contiene un millón de registros. Dado que el filtrado se realiza localmente, solo se examinan los primeros 500 registros. Si el registro deseado es el 501, o el 500 001, **Filter** no lo tiene en cuenta o no lo devuelve.

Las funciones de agregado también pueden provocar confusión. Tome **Average** en lugar de una columna de ese mismo origen de datos de un millón de registros. **Average** aún no se puede delegar, así que solo se obtiene el promedio de los primeros 500 registros. Si no tiene cuidado, algún usuario de la aplicación podría malinterpretar una respuesta parcial como una respuesta completa.

## <a name="changing-the-limit"></a>Cambio del límite
500 es el número predeterminado de registros, pero se puede cambiar este número para toda una aplicación:

1. En la pestaña **Archivo**, seleccione **Configuración de aplicación**.
2. En **Características experimentales**, cambie el valor **Límite de filas de datos para las consultas no delegables** de 1 a 2000.

En algunos casos, sabrá que 2000 (o 1000 o 1500) satisfará las necesidades del escenario. Puede aumentar esta cifra con precaución para que se ajuste a su escenario. A medida que aumenta esta cifra, el rendimiento de la aplicación puede verse afectado, sobre todo en las tablas anchas que contienen muchas columnas. Aun así, la mejor respuesta es delegar lo máximo posible.

Para asegurarse de que la aplicación se pueda escalar a grandes conjuntos de datos, reduzca este valor a 1. Todo lo que no se puede delegar devuelve un único registro, que debería ser fácil de detectar al probar la aplicación. De esta manera se pueden evitar sorpresas al intentar llevar una aplicación de prueba de concepto a producción.

## <a name="delegation-warnings"></a>Advertencias de delegación
Para que sea más fácil saber qué se delega y qué no, PowerApps proporciona una advertencia (triángulo amarillo) cuando se crea una fórmula que contiene algo que no se puede delegar.

Las advertencias de delegación solo aparecen en las fórmulas que operan en orígenes de datos delegables. Si no ve una advertencia y cree que la fórmula no se delega correctamente, compruebe el tipo de origen de datos en la lista anterior de [orígenes de datos que se pueden delegar](delegation-overview.md#delegable-data-sources) de este tema.

## <a name="examples"></a>Ejemplos
En este ejemplo se genera automáticamente una aplicación de tres pantallas basada en una tabla de SQL Server denominada **[dbo].[Fruit]**. Para obtener información sobre cómo generar la aplicación, puede aplicar principios similares a los del [tema sobre Common Data Service for Apps](data-platform-create-app.md) a SQL Server.

![Aplicación de tres pantallas](./media/delegation-overview/products-afd.png)

La propiedad **Items** de la galería está establecida en una fórmula que contiene las funciones **SortByColumns** y **Search**, que se pueden delegar.

En el cuadro de búsqueda, escriba **"Apple"**.

Una fila de puntos aparece momentáneamente junto a la parte superior de la pantalla mientras la aplicación se comunica con SQL Server para procesar la solicitud de búsqueda. Aparecen todos los registros que cumplen los criterios de búsqueda, aunque el origen de datos contenga millones de registros.

![Control de entrada de texto de búsqueda](./media/delegation-overview/products-apple.png)

Los resultados de búsqueda incluyen **"Apples"**, **"Crab apples"** y **"Pineapple"**, porque la función **Search** busca por todas las partes de un columna de texto. Si solo quiere buscar los registros que contienen el término de búsqueda al principio del nombre de la fruta, puede usar otra función delegable, **Filter**, con un término de búsqueda más complicado. (Por motivos de simplicidad, quite la llamada a **SortByColumns**).

![Quitar la llamada a SortByColumns](./media/delegation-overview/products-apple-delegationwarning.png)

Los nuevos resultados incluyen **"Apples"**, pero no **"Crab apples"** ni **"Pineapple"**.  Pero aparece un triángulo amarillo junto a la galería (y en la miniatura de pantalla si la barra de navegación izquierda muestra miniaturas) y una línea ondulada azul debajo de una parte de la fórmula. Cada uno de estos elementos indica una advertencia. Si mantiene el puntero sobre el triángulo amarillo junto a la galería, aparece este mensaje:

![Puntero sobre la advertencia de delegación](./media/delegation-overview/products-apple-yellowwarning.png)

SQL Server es un origen de datos delegable y **Filter** es una función delegable, pero **Mid** y **Len** no se pueden delegar a cualquier origen de datos.

Pero ha funcionado, ¿no? Bueno, más o menos. Por eso es una advertencia y no un subrayado ondulado rojo.

- Si la tabla contiene menos de 500 registros, la fórmula ha funcionado perfectamente. Todos los registros se han pasado al dispositivo y **Filter** se ha aplicado localmente.
- Si la tabla contiene más de 500 registros, la fórmula no devuelve los registros desde el 501, aun cuando cumplan los criterios.
