---
title: Descripción de la delegación en una aplicación de lienzo | Microsoft Docs
description: La delegación se usa para procesar eficazmente grandes conjuntos de datos en una aplicación de lienzo.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/05/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1d98f01920dbcbf960b1e2bb21159586318e0386
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79211581"
---
# <a name="understand-delegation-in-a-canvas-app"></a>Descripción de la delegación en una aplicación de lienzo
Power Apps incluye un eficaz conjunto de funciones para filtrar, ordenar y dar forma a tablas de datos en una aplicación de lienzo **[: funciones de filtrado,](functions/function-filter-lookup.md)** **[ordenación](functions/function-sort.md)** y **[AddColumns](functions/function-table-shaping.md)** por nombrar solo algunas. Con estas funciones puede proporcionar a los usuarios acceso a la información que necesitan. Para quienes conozcan bien las bases de datos, el uso de estas funciones es como escribir una consulta de base de datos.

La clave para compilar aplicaciones eficientes es minimizar la cantidad de datos que debe contener el dispositivo. Quizás necesite solo unos pocos registros de un mar de millones o que un único valor agregado pueda representar miles de registros. O quizás solo se pueda recuperar el primer conjunto de registros, y el resto se trae cuando el usuario indica que desea más. De esta forma se puede reducir drásticamente la potencia de procesamiento, la memoria y el ancho de banda de red que necesita la aplicación, lo que conlleva menores tiempos de respuesta para los usuarios, incluso en teléfonos conectados a través de una red móvil. 

La *delegación* es donde la expresividad de las fórmulas de Power apps satisface la necesidad de minimizar los datos que se mueven a través de la red. En Resumen, Power apps delegará el procesamiento de datos en el origen de datos, en lugar de mover los datos a la aplicación para su procesamiento local.

En los casos en los que esto resulta complicado y el motivo de este artículo, se debe a que no todo lo que se puede expresar en una fórmula de Power apps se puede delegar en todos los orígenes de datos. El lenguaje Power apps imita el lenguaje de fórmulas de Excel, diseñado con acceso completo e inmediato a un libro completo en memoria, con una amplia variedad de funciones de manipulación numérica y de texto. Como resultado, el lenguaje de Power apps es mucho más rico de lo que la mayoría de los orígenes de datos pueden admitir, incluidos motores de base de datos eficaces como SQL Server.

**El trabajo con grandes conjuntos de datos requiere que se usen orígenes de datos y fórmulas que se puedan delegar.** Es la única manera de que la aplicación funcione correctamente y de tener la certeza de que los usuarios pueden acceder a toda la información que necesitan. Preste atención a las advertencias de delegación que identifiquen lugares donde esta no es posible. Si trabaja con conjuntos de datos pequeños (menos de 500 registros), puede usar cualquier origen de datos y cualquier fórmula, ya que la aplicación puede procesar datos en local si la fórmula no se puede delegar. 

> [!NOTE]
> Las advertencias de delegación se marcaron previamente en Power apps como sugerencias de "punto azul", pero las sugerencias de delegación se han vuelto a clasificar como advertencias. Si los datos del origen de datos superan los 500 registros y una función no se puede delegar, es posible que las aplicaciones de energía no puedan recuperar todos los datos y que la aplicación tenga resultados incorrectos. Las advertencias de delegación permiten administrar la aplicación para que tenga resultados correctos.

## <a name="delegable-data-sources"></a>Orígenes de datos delegables
Solo se admite la delegación para determinados orígenes de datos tabulares. Si un origen de datos admite la delegación, en la [documentación del conector](https://docs.microsoft.com/connectors/) se describe dicha compatibilidad. Por ejemplo, estos orígenes de datos tabulares son los más populares y admiten la delegación:

- [Common Data Service](https://docs.microsoft.com/connectors/commondataservice/) 
- [SharePoint](https://docs.microsoft.com/connectors/sharepointonline/) 
- [SQL Server](https://docs.microsoft.com/connectors/sql/) 

Los libros de Excel importados (mediante **Agregar datos estáticos a su** origen de datos de la aplicación), las colecciones y las tablas almacenadas en variables de contexto no requieren delegación. Todos estos datos ya están en memoria y se puede aplicar el idioma completo de Power apps.

## <a name="delegable-functions"></a>Funciones que se pueden delegar
El siguiente paso es usar solo aquellas fórmulas que se puedan delegar. Aquí se incluyen los elementos de las fórmulas que se pueden delegar. Sin embargo, todos los orígenes de datos son diferentes, y no todos ellos admiten todos estos elementos. Compruebe si hay advertencias de delegación en la fórmula en cuestión.

Estas listas cambiarán con el tiempo, ya que en el futuro habrá más funciones y operadores que admitan la delegación.

### <a name="filter-functions"></a>Funciones de filtro
**[Filtrar](functions/function-filter-lookup.md)**, **[Buscar](functions/function-filter-lookup.md)** y **[Búsqueda](functions/function-filter-lookup.md)** se pueden delegar.  

Las funciones **Filter** y **LookUp** se pueden usar con columnas de la tabla para seleccionar los registros apropiados:

* **[And](functions/function-logicals.md)** (incluyendo **[&&](functions/operators.md)**), **[Or](functions/function-logicals.md)** (incluyendo **[||](functions/operators.md)**), **[Not](functions/function-logicals.md)** (incluyendo **[!](functions/operators.md)**)
* **[In (En)](functions/operators.md)**
* **[=](functions/operators.md)**, **[<>](functions/operators.md)**, **[>=](functions/operators.md)**, **[<=](functions/operators.md)**, **[>](functions/operators.md)**, **[<](functions/operators.md)**
* **[+](functions/operators.md)**, **[-](functions/operators.md)**
* **[TrimEnds (RecortarExtr)](functions/function-trim.md)**
* **[EsBlanco](functions/function-isblank-isempty.md)**
* **[StartsWith](functions/function-startswith.md)**, ** [EndsWith](functions/function-startswith.md)**
* Valores constantes que son iguales en todos los registros, como las propiedades del control y [las variables globales y de contexto](working-with-variables.md).

También se pueden usar partes de la fórmula que se evalúen en un valor constante para todos los registros. Por ejemplo, **left (Language (), 2)**, **Date (2019, 3, 31)** y **hoy ()** no dependen de ninguna columna del registro y, por tanto, devuelven el mismo valor para todos los registros. Estos valores se pueden enviar al origen de datos como una constante y no bloquearán la delegación. 

La lista anterior no incluye estos elementos importantes:

* **[If (Si)](functions/function-if.md)**
* **[*](functions/operators.md)**, **[/](functions/operators.md)**, **[Mod](functions/function-mod.md)**
* **[Concatenar](functions/function-concatenate.md)** (incluyendo **[&](functions/operators.md)**)
* **[ExactIn (ExactoEn)](functions/operators.md)**
* Funciones de manipulación de cadenas: **[Minusc](functions/function-lower-upper-proper.md)**, **[Mayusc](functions/function-lower-upper-proper.md)**, **[Izquierda](functions/function-left-mid-right.md)**, **[Extrae](functions/function-left-mid-right.md)**, **[Largo](functions/function-left-mid-right.md)**, ...
* Señales: **[Ubicación](functions/signals.md)**, **[Aceleración](functions/signals.md)**, **[Brújula](functions/signals.md)**, ...
* Volatiles: **[Rand](functions/function-rand.md)**,...
* [Colecciones](working-with-variables.md)

### <a name="sorting-functions"></a>Funciones de ordenación
**[Ordenar](functions/function-sort.md)** y **[SortByColumns (OrdenarPorColumnas)](functions/function-sort.md)** se pueden delegar.

En **Ordenar**, la fórmula solo puede ser el nombre de una columna individual y no puede incluir otros operadores o funciones.

### <a name="aggregate-functions"></a>Funciones de agregado
**[Suma](functions/function-aggregates.md)**, **[Promedio](functions/function-aggregates.md)**, **[Min](functions/function-aggregates.md)** y **[Max](functions/function-aggregates.md)** pueden delegarse. En este momento, solo un número limitado de orígenes de datos admite esta delegación. Para obtener más detalles, vea la [lista de delegación](delegation-list.md).

Las funciones de recuento como **[CountRows](functions/function-table-counts.md)**, **[CountA](functions/function-table-counts.md)** y **[Count](functions/function-table-counts.md)** no se pueden delegar.

Otras funciones de agregado, como **[StdevP](functions/function-aggregates.md)** y **[VarP](functions/function-aggregates.md)**, no se pueden delegar.

### <a name="table-shaping-functions"></a>Funciones de modelado de tabla

**[AddColumns](functions/function-table-shaping.md)**, **[DropColumns](functions/function-table-shaping.md)**, **[cambiarnombrecolumnas](functions/function-table-shaping.md)** y **[mostrarcolumnas](functions/function-table-shaping.md)** admiten parcialmente la delegación.  Las fórmulas de sus argumentos se pueden delegar.  Sin embargo, el resultado de estas funciones está sujeto al límite de registros que no son de delegación.

Como en este ejemplo, los responsables suelen usar **AddColumns** y **Buscar** para combinar información de una tabla en otra, lo que se conoce comúnmente como una combinación en el lenguaje de la base de datos:

```powerapps-dot
AddColumns( Products, 
    "Supplier Name", 
    LookUp( Suppliers, Suppliers.ID = Product.SupplierID ).Name 
)
```

Aunque los **productos** y **proveedores** pueden ser orígenes de datos delegables y **lookup** es una función delegables, la salida de la función **AddColumns** no es delegables. El resultado de la fórmula completa se limita a la primera parte del origen de datos **Products** . Dado que la función **LookUp** y su origen de datos se pueden delegar, se puede encontrar una coincidencia con **Suppliers** en cualquier lugar del origen de datos, aunque sea grande. 

Si utiliza **AddColumns** de esta manera, la **búsqueda** debe realizar llamadas independientes en el origen de datos para cada uno de esos primeros registros de **productos**, lo que provoca una gran cantidad de chatter de red. Si los **proveedores** son lo suficientemente pequeños y no cambian a menudo, puede llamar a la función **Collect** en [**OnStart**](functions/signals.md) para almacenar en caché el origen de datos en la aplicación cuando se inicia. Como alternativa, puede reestructurar la aplicación para que extraiga los registros relacionados solo cuando el usuario los solicite.  
 
## <a name="non-delegable-functions"></a>Funciones no delegables
Las demás funciones no admiten la delegación, incluidas estas importantes funciones:

* **[Primero](functions/function-first-last.md)**, **[FirstN](functions/function-first-last.md)**, **[Último](functions/function-first-last.md)**, **[LastN](functions/function-first-last.md)**
* **[Choices](functions/function-choices.md)**
* **[Concat](functions/function-concatenate.md)**
* **[Recopilar](functions/function-clear-collect-clearcollect.md)**, **[ClearCollect](functions/function-clear-collect-clearcollect.md)**
* **[CountIf](functions/function-table-counts.md)**, **[RemoveIf](functions/function-remove-removeif.md)**, **[UpdateIf](functions/function-update-updateif.md)**
* **[GroupBy](functions/function-groupby.md)**, **[Desagrupar](functions/function-groupby.md)**

## <a name="non-delegable-limits"></a>Límites no delegables
Las fórmulas que no se pueden delegar se procesan localmente. Esto permite usar toda la amplitud del lenguaje de fórmulas de Power apps. Pero esto tiene un precio: primero deben pasarse todos los datos al dispositivo, lo que podría implicar la recuperación de una gran cantidad de datos a través de la red. Esta operación puede tardar un tiempo, lo que daría la impresión de que la aplicación se ejecuta con lentitud, o incluso que está bloqueada.

Para evitar esto, Power apps impone un límite en la cantidad de datos que se pueden procesar localmente: 500 registros de forma predeterminada.  Elegimos este número para que tuviera acceso completo a los conjuntos de datos pequeños y pudiera pueda refinar su uso de conjuntos de datos grandes viendo los resultados parciales.

Obviamente, si se usa este recurso, es preciso tener cuidado, ya que puede confundir a los usuarios. Por ejemplo, imagine una función **Filter** con una fórmula de selección que no se puede delegar en lugar de un origen de datos que contiene un millón de registros. Dado que el filtrado se realiza localmente, solo se examinan los primeros 500 registros. Si el registro deseado es el 501, o el 500 001, **Filter** no lo tiene en cuenta o no lo devuelve.

Las funciones de agregado también pueden provocar confusión. Tome **Average** en lugar de una columna de ese mismo origen de datos de un millón de registros. **Average** aún no se puede delegar, así que solo se obtiene el promedio de los primeros 500 registros. Si no tiene cuidado, algún usuario de la aplicación podría malinterpretar una respuesta parcial como una respuesta completa.

## <a name="changing-the-limit"></a>Cambio del límite
500 es el número predeterminado de registros, pero se puede cambiar este número para toda una aplicación:

1. En la pestaña **Archivo**, seleccione **Configuración de aplicación**.
2. En **Configuración avanzada**, cambie el valor de **límite de filas de datos para consultas que no sean delegables** de 1 a 2000.

En algunos casos, sabrá que 2000 (o 1000 o 1500) satisfará las necesidades del escenario. Puede aumentar esta cifra con precaución para que se ajuste a su escenario. A medida que aumenta esta cifra, el rendimiento de la aplicación puede verse afectado, sobre todo en las tablas anchas que contienen muchas columnas. Aun así, la mejor respuesta es delegar lo máximo posible.

Para asegurarse de que la aplicación se pueda escalar a grandes conjuntos de datos, reduzca este valor a 1. Todo lo que no se puede delegar devuelve un único registro, que debería ser fácil de detectar al probar la aplicación. De esta manera se pueden evitar sorpresas al intentar llevar una aplicación de prueba de concepto a producción.

## <a name="delegation-warnings"></a>Advertencias de delegación
Para que sea más fácil saber qué es y qué no se está delegando, Power apps proporciona una advertencia (triángulo amarillo) cuando se crea una fórmula que contiene algo que no se puede delegar.

Las advertencias de delegación solo aparecen en las fórmulas que operan en orígenes de datos delegables. Si no ve una advertencia y cree que la fórmula no se delega correctamente, compruebe el tipo de origen de datos en la lista anterior de [orígenes de datos que se pueden delegar](delegation-overview.md#delegable-data-sources) de este tema.

## <a name="examples"></a>Ejemplos:
En este ejemplo se genera automáticamente una aplicación de tres pantallas basada en una tabla de SQL Server denominada **[dbo].[Fruit]**. Para obtener información sobre cómo generar la aplicación, puede aplicar principios similares en el [tema sobre Common Data Service](data-platform-create-app.md) a SQL Server.

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
