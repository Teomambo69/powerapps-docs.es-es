---
title: "Función ForAll | Microsoft Docs"
description: "Información de referencia para la función ForAll en PowerApps, incluidos ejemplos y sintaxis"
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
ms.date: 04/26/2016
ms.author: gregli
ms.openlocfilehash: c0ca5547f433aea1bee8d5d0d430c3e11a7f4caa
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="forall-function-in-powerapps"></a>Función ForAll en PowerApps
Calcula valores y realiza acciones para todos los [registros](../working-with-tables.md#records) de una [tabla](../working-with-tables.md).

## <a name="description"></a>Descripción
La función **ForAll** evalúa una fórmula para todos los registros de una tabla.  La fórmula puede calcular un valor o realizar acciones, como modificar datos o trabajar con una conexión.

[!INCLUDE [record-scope](../includes/record-scope.md)]

### <a name="return-value"></a>Valor devuelto
Se devuelve el resultado de cada evaluación de fórmula en una tabla, en el mismo orden que la tabla de entrada.

Si el resultado de la fórmula es un valor único, la tabla resultante será una tabla con una sola columna.  Si el resultado de la fórmula es un registro, la tabla resultante contendrá registros con las mismas columnas que el registro del resultado.  

Si el resultado de la fórmula es un valor *en blanco*, no habrá ningún registro en la tabla de resultados para ese registro de entrada.  En este caso, habrá menos registros en la tabla de resultados que en la tabla de origen.

### <a name="taking-action"></a>Realización de acciones
La fórmula puede incluir funciones que realicen acciones, como modificar los registros de un origen de datos con las funciones **[Revisión](function-patch.md)** y **[Recopilar](function-clear-collect-clearcollect.md)**.  La fórmula también puede llamar a métodos en las conexiones.  Se pueden realizar varias acciones por registro mediante el operador [**;** ](operators.md). No se puede modificar la tabla objeto de la función **ForAll**.

Al escribir la fórmula, tenga en cuenta que los registros se pueden procesar en cualquier orden y, siempre que sea posible, en paralelo.  Se puede procesar el primer registro de la tabla después del último registro.  Tenga cuidado para evitar la ordenación de las dependencias.  Por esta razón, no puede usar las funciones **[UpdateContext](function-updatecontext.md)**, **[Clear](function-clear-collect-clearcollect.md)** y  **[ClearCollect](function-clear-collect-clearcollect.md)**  dentro de una función **ForAll** ya que se podrían usar fácilmente para mantener variables que son susceptibles de sufrir este efecto.  Puede usar **[Recopilar](function-clear-collect-clearcollect.md)**, pero el orden en que se agregan los registros no está definido.

Varias funciones que modifican los orígenes de datos, incluidas las funciones **Recopilar**, **Quitar** y **Actualizar**, devuelven el origen de datos que han cambiado como su valor devuelto.  Estos valores devueltos pueden ser grandes y consumir recursos significativos si se devuelven para cada registro de la tabla **ForAll**.  También es posible que estos valores devueltos no sean los esperados, ya que **ForAll** puede funcionar en paralelo y puede separar los efectos secundarios de estas funciones a partir de la obtención de su resultado.  Afortunadamente, si el valor devuelto desde **ForAll** no se utiliza realmente, y este suele ser el caso de las funciones de modificación de datos, el valor devuelto no se creará con lo que no habrá ningún problema de recursos u ordenación.  Sin embargo, si va a utilizar el resultado de una función **ForAll** y el de alguna de las funciones que devuelve un origen de datos, medite concienzudamente sobre cómo estructurar el resultado y pruébelas primero en conjuntos de datos pequeños.  

### <a name="alternatives"></a>Alternativas
Muchas funciones de PowerApps pueden procesar más de un valor a la vez mediante el uso de una tabla de una sola columna.  Por ejemplo, la función **Len** puede procesar una tabla de valores de texto, devolviendo una tabla de longitudes, de la misma manera que podría hacerlo la función **ForAll**.  Esto hace que no sea necesario usar la función **ForAll** en muchos casos, puede resultar más eficaz y es más fácil de leer.

Otra consideración a tener en cuenta es que **ForAll** no es delegable mientras que otras funciones sí que lo pueden ser como, por ejemplo, **Filtrar**.  

### <a name="delegation"></a>Delegación
[!INCLUDE [delegation-no-one](../includes/delegation-no-one.md)]

## <a name="syntax"></a>Sintaxis
**ForAll**( *Table*, *Formula* )

* *Table*: requerido. Tabla sobre la que se va a actuar.
* *Formula*: requerido.  La fórmula que se evalúa para todos los registros de la *tabla*.

## <a name="examples"></a>Ejemplos
### <a name="calculations"></a>Cálculos
Los ejemplos siguientes usan el [origen de datos](../working-with-data-sources.md) **Cuadrados**:

![](media/function-forall/squares.png)

Para crear este origen de datos como una colección, establezca la propiedad **AlSeleccionar** de un control **Botón** en esta fórmula, abra el modo de vista previa y, a continuación, haga clic o pulse en el botón:

* **ClearCollect( Squares, [ "1", "4", "9" ] )**

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **ForAll(&nbsp;Cuadrados, Raiz(&nbsp;Value&nbsp;)&nbsp;)**<br><br>**Raiz(&nbsp;Squares&nbsp;)** |Para todos los registros de la tabla de entrada calcula la raíz cuadrada de la columna **Valor**.  La función **Raiz** también puede utilizarse con una tabla de una sola columna, lo que permite realizar este ejemplo sin usar la función **ForAll**. |<style> img { max-width: none } </style> ![](media/function-forall/sqrt.png) |
| **ForAll(&nbsp;Cuadrados, Power(&nbsp;Value,&nbsp;3&nbsp;)&nbsp;)** |Para todos los registros de la tabla de entrada eleva la columna **Valor** a la tercera potencia.  La función **Power** no admite tablas de una sola columna. Por tanto, se debe usar **ForAll** en este caso. |<style> img { max-width: none } </style> ![](media/function-forall/power3.png) |

### <a name="using-a-connection"></a>Uso de una conexión
Los ejemplos siguientes usan el [origen de datos](../working-with-data-sources.md) **Expresiones**:

![](media/function-forall/translate.png)

Para crear este origen de datos como una colección, establezca la propiedad **AlSeleccionar** de un control **Botón** en esta fórmula, abra el modo de vista previa y, a continuación, haga clic o pulse en el botón:

* **ClearCollect( Expresiones, [ "Hello", "Good morning", "Thank you", "Goodbye" ] )**

Este ejemplo usa también una conexión con [Microsoft Translator](../connections/connection-microsoft-translator.md).  Para agregar esta conexión a la aplicación, consulte el tema acerca de cómo [administrar conexiones](../add-manage-connections.md).

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **ForAll( Expresiones, MicrosoftTranslator.Translate( Value, "es" ) )** |Para todos los registros de la tabla Expresiones, traduce el contenido de la columna **Valor** en español (abreviado "es"). |<style> img { max-width: none } </style> ![](media/function-forall/translate-es.png) |
| **ForAll( Expresiones, MicrosoftTranslator.Translate( Value, "fr" ) )** |Para todos los registros de la tabla Expresiones, traduce el contenido de la columna **Valor** en francés (abreviado "fr"). |<style> img { max-width: none } </style> ![](media/function-forall/translate-fr.png) |

### <a name="copying-a-table"></a>Copia de una tabla
A veces, es necesario filtrar, dar forma, ordenar y manipular los datos.  PowerApps proporciona una serie de funciones para hacerlo como, por ejemplo, **Filtrar**, **AddColumns** y **Ordenar**.  PowerApps trata cada tabla como un valor, lo que permite que fluya a través de las fórmulas y se consuma fácilmente.      

Puede que, en alguna ocasión, desee realizar una copia de este resultado para su uso posterior.  O puede que desee mover información de un origen de datos a otro.  PowerApps proporciona la función **Recopilar** para copiar datos.

Pero antes de hacer esa copia, debe considerar cuidadosamente si realmente se necesita.  Hay muchas situaciones que se pueden solucionar mediante el filtrado y la forma del origen de datos subyacente a petición con una fórmula. Algunas de las desventajas a la hora de realizar una copia son:

* Dos copias de la misma información significa que una de ellas puede no sincronizarse.  
* Realizar una copia puede consumir una gran cantidad de memoria del equipo, ancho de banda de red y tiempo.  
* En la mayoría de los orígenes de datos, la copia no se puede delegar, lo cual limita la cantidad de datos que se pueden mover.      

Los ejemplos siguientes usan el [origen de datos](../working-with-data-sources.md) **Productos**:

![](media/function-forall/prod.png)

Para crear este origen de datos como una colección, establezca la propiedad **AlSeleccionar** de un control **Botón** en esta fórmula, abra el modo de vista previa y, a continuación, haga clic o pulse en el botón:

* **ClearCollect( Productos, Tabla( { Product: "Widget", 'Quantity Requested': 6, 'Quantity Available': 3 }, { Product: "Gadget", 'Quantity Requested': 10, 'Quantity Available': 20 }, { Product: "Gizmo", 'Quantity Requested': 4, 'Quantity Available': 11 }, { Product: "Apparatus", 'Quantity Requested': 7, 'Quantity Available': 6 } ) )**

Nuestro objetivo es trabajar con una tabla derivada que incluya solo los artículos de los que se ha solicitado una cantidad mayor a la disponible y para los cuales hay que realizar un pedido:

![](media/function-forall/prod-order.png)  

Se puede realizar esta tarea de dos maneras diferentes, que generan el mismo resultado, y cada una con sus ventajas y desventajas.

#### <a name="table-shaping-on-demand"></a>Forma de tabla a petición
No haga esa copia  Podemos utilizar la fórmula siguiente en cualquier lugar que sea necesario:

* **MostrarColumnas( AgregarColumnas( Filtrar( Productos, 'Cantidad en pedido' > 'Cantidad disponible' ), "Cantidad para solicitar", 'Cantidad en pedido' - 'Cantidad disponible' ), "Producto", "Cantidad para solicitar" )**

Se crea un [ámbito de registro](../working-with-tables.md#record-scope) mediante las funciones **Filtrar** y **AddColumns** que permite realizar las operaciones de comparación y resta, respectivamente, con los campos **'Cantidad en pedido'** y **'Cantidad disponible'** de cada registro.

En este ejemplo, la función **Filtrar** se puede delegar.  Esto es importante, ya que puede encontrar todos los productos que cumplen los criterios, incluso si se trata solo de unos pocos registros en una tabla de millones de ellos.  En este momento, las funciones **MostrarColumnas** y **AddColumns** no se pueden delegar, por lo que se limitará el número real de productos que es necesario solicitar.  Si sabe que el tamaño de este resultado siempre será relativamente pequeño, este enfoque es adecuado.

Y dado que no realizamos una copia, no hay ninguna copia adicional de la información para administrar o que esté obsoleta.  

#### <a name="forall-on-demand"></a>Función ForAll a petición
Otro enfoque consiste en utilizar la función **ForAll** para reemplazar las funciones de forma de tabla:

* **ForAll( Productos, If( 'Cantidad en pedido' > 'Cantidad disponible', { Producto: Producto, 'Cantidad para solicitar': 'Cantidad en pedido' - 'Cantidad disponible' } ) )**

Esta fórmula puede ser más sencilla de leer y escribir para algunas personas.

No se puede delegar ninguna parte de **ForAll**.  Solo se evaluará la primera parte de la tabla **Productos**, lo cual podría ser un problema si esta tabla es muy grande.  Dado que la función **Filtrar** se pudo delegar en el ejemplo anterior, esta podría funcionar mejor con grandes conjuntos de datos.

#### <a name="collect-the-result"></a>Recopilación de resultados
En algunos casos, puede que sea necesario realizar una copia de los datos.  Puede que necesite mover información de un origen de datos a otro.  En este ejemplo, se realizan los pedidos a través de una tabla denominada **NewOrder**del sistema del proveedor.  Para interacciones de usuario de alta velocidad, puede que desee almacenar en caché una copia local de una tabla para que no haya ninguna latencia del servidor.

Se utilizará la misma forma de tabla que en los dos ejemplos anteriores, pero se capturará el resultado en una colección:

* **ClearCollect( NewOrder, MostrarColumnas( AddColumns( Filtrar( Productos, 'Cantidad en pedido' > 'Cantidad disponible' ), "Cantidad para solicitar", 'Cantidad en pedido' - 'Cantidad disponible' ), "Producto", "Cantidad para solicitar" ) )**
* **ClearCollect( NewOrder, ForAll( Productos, If( 'Cantidad en pedido' > 'Cantidad disponible', { Producto: Producto, 'Cantidad para solicitar': 'Cantidad en pedido' - 'Cantidad disponible' } ) ) )**

Las funciones **ClearCollect** y **Recopilar** no se pueden delegar.  Como consecuencia, la cantidad de datos que se pueden mover de esta manera es limitada.

#### <a name="collect-within-forall"></a>Recopilación dentro de ForAll
Por último, se puede realizar la función **Recopilar** directamente dentro de **ForAll**:

* **Borrar( ProductsToOrder ); ForAll( Productos, If( 'Cantidad en pedido' > 'Cantidad disponible', Recopilar( NewOrder, { Producto: Producto, 'Cantidad para solicitar': 'Cantidad en pedido' - 'Cantidad disponible' } ) ) )**

Una vez más, la función **ForAll** no se puede delegar en este momento.  Si la tabla **Productos** es grande, la función **ForAll** buscará solo en el primer conjunto de registros y puede que se pasen por alto algunos productos que es necesario solicitar.  Pero en el caso de tablas que sabemos que seguirán siendo pequeñas, este enfoque es adecuado.

Tenga en cuenta que no vamos a capturar el resultado de la función **ForAll**.  Las llamadas de la función **Recopilar** realizadas desde dentro de ella devolverán el origen de datos **NewOrder** para todos los registros, lo que podría agregarse a muchos datos si los fuéramos a capturar.  
