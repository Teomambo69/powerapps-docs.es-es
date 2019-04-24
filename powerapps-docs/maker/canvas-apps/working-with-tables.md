---
title: Comprender las tablas de aplicaciones de lienzo | Microsoft Docs
description: Información de referencia sobre cómo trabajar con tablas, columnas y registros de aplicaciones de lienzo en PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/26/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5883ae65beb698a8c7681d9eac6ba0f7439ca19e
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61557894"
---
# <a name="understand-canvas-app-tables-and-records-in-powerapps"></a>Comprender las tablas y los registros de aplicaciones de lienzo en PowerApps

En PowerApps, puede crear una aplicación de lienzo que tenga acceso a información en Microsoft Excel, SharePoint, SQL Server y otros orígenes diferentes que almacenan datos en registros y tablas. Para trabajar de forma más eficaz con este tipo de datos, revise los conceptos que subyacen a estas estructuras.

* Un registro contiene una o varias categorías de información sobre una persona, un lugar o una cosa. Por ejemplo, un registro puede contener el nombre, la dirección de correo electrónico y el número de teléfono de un solo cliente. Otras herramientas hacen referencia a un registro como una "fila" o un "elemento".
* Una tabla contiene uno o varios registros que incluyen las mismas categorías de información. Por ejemplo, una tabla puede contener los nombres, las direcciones de correo electrónico y los números de teléfono de 50 clientes.

En la aplicación, usará [fórmulas](working-with-formulas.md) para crear, actualizar y manipular registros y tablas. Probablemente podrá leer y escribir datos en un [origen de datos](working-with-data-sources.md) externo, que es una tabla extendida. Además, puede crear una o varias tablas internas, que se denominan [colecciones](working-with-data-sources.md#collections).

Puede crear una variedad de fórmulas que usan el nombre de una tabla como argumento, al igual que las fórmulas de Excel consideran una o varias referencias de celda como argumentos. Algunas fórmulas de PowerApps devuelven una tabla que refleja el resto de los argumentos que se especifiquen. Por ejemplo, podría crear una fórmula:

* para actualizar un registro en una tabla mediante la especificación de esa tabla como uno de varios argumentos para la función **[Revisión](functions/function-patch.md)**,
* para agregar, quitar y cambiar el nombre de las columnas de una tabla mediante la especificación de esa tabla como un argumento para la función **[AgregarColumnas](functions/function-table-shaping.md)**, **[EliminarColumnas](functions/function-table-shaping.md)** o **[CambiarNombreColumnas](functions/function-table-shaping.md)**. Ninguna de esas funciones modifica la tabla original. En su lugar, la función devuelve otra tabla basada en el resto de los argumentos que se especifiquen.

## <a name="elements-of-a-table"></a>Elementos de una tabla
![](media/working-with-tables/elements-of-a-table.png)

### <a name="records"></a>Registros
Cada registro contiene al menos una categoría de información sobre una persona, un lugar o una cosa. El ejemplo anterior muestra un registro para cada producto (**Chocolate**, **Pan** y **Agua**) y una columna para cada categoría de información (**Precio**, **Cantidad disponible** y **Cantidad en pedido**).

En una fórmula, puede hacer referencia a un registro por sí mismo, fuera del contexto de una tabla, mediante el uso de llaves. Por ejemplo, este registro **{nombre: "Fresas", precio: 7,99}** no está asociado a una tabla. Tenga en cuenta que los nombres de los campos, como **Nombre** y **Precio** en ese ejemplo, no están dentro de comillas dobles.

### <a name="fields"></a>Campos
Un campo es un elemento individual de información de un registro. Puede visualizar este tipo de campo como un valor de una columna para un registro concreto.

Igual que con un control, puede hacer referencia a un campo de un registro mediante **.**, que es el [operador](functions/operators.md) en el registro.  Por ejemplo, **Primero(Productos).Nombre** devuelve el campo **Nombre** para el primer registro de la tabla **Productos**.

Un campo puede contener otro registro o tabla, como muestra el ejemplo de la función **[AgruparPor](functions/function-groupby.md)**. Puede anidar tantos niveles de registros y tablas como desee.

### <a name="columns"></a>Columnas
Una columna hace referencia al mismo campo de uno o varios registros de una tabla. En el ejemplo anterior, cada producto tiene un campo de precio, y el precio está en la misma columna para todos los productos.  La tabla anterior tiene cuatro columnas, que se muestran horizontalmente en la parte superior:

* **Nombre**
* **Precio**
* **Cantidad disponible**
* **Cantidad en pedido**

El nombre de la columna refleja los campos de dicha columna.

Todos los valores de una columna son del mismo tipo de datos. En el ejemplo anterior, la columna "Cantidad disponible" siempre contiene un número y no puede contener una cadena, como "12 unidades", para un registro.  El valor de cualquier campo también puede aparecer *en blanco*.  

Es posible que en otras herramientas haya hecho referencia a las columnas con el término "campos".

> [!NOTE]
> En los orígenes de datos de SharePoint y Excel que contengan nombres de columna con espacios, PowerApps los sustituirá por **"\_x0020\_"**. Por ejemplo, **"Nombre de columna"** en SharePoint o Excel aparecerá como **"Nombre_x0020_de_columna"** en PowerApps cuando se muestre en el diseño de datos o se use en una fórmula.

### <a name="table"></a>Tabla
Una tabla consta de uno o varios registros, cada uno con varios campos que tienen nombres coherentes entre los registros.

Cualquier tabla almacenada en un origen de datos o en un colección tiene un nombre, que se usa para hacer referencia a la tabla y para pasarlo a funciones que consideran las tablas como argumentos.  Las tablas también pueden resultar de una función o de una fórmula.

Como en el ejemplo siguiente, puede expresar una tabla en una fórmula mediante la utilización de la función **[Tabla](functions/function-table.md)** con un conjunto de registros, que se expresa entre llaves:

`Table( { Value: "Strawberry" }, { Value: "Vanilla" } )`

También puede definir una tabla de una sola columna entre corchetes.  Una manera equivalente de escribir lo anterior:

`[ "Strawberry", "Vanilla" ]`

## <a name="table-formulas"></a>Fórmulas de tabla
En Excel y PowerApps, las fórmulas se usan para manipular números y cadenas de texto de formas similares:

* En Excel, escriba un valor, como **42**, en la celda **A1** y después escriba una fórmula, como **A1+2**, en otra celda para mostrar el valor de **44**.
* En PowerApps, establezca la propiedad **[Valor predeterminado](controls/properties-core.md)** de **Slider1** en **42**, y defina la propiedad **[Texto](controls/properties-core.md)** de una etiqueta en **Slider1.Value + 2** para mostrar el valor de **44**.

En ambos casos, el valor calculado cambia automáticamente si modifica los valores de los argumentos (por ejemplo, el número de la celda **A1** o el valor de **Slider1**).

Del mismo modo, puede usar fórmulas para acceder a datos de tablas y registros y manipularlos. Puede usar nombres de tablas como argumentos en algunas fórmulas, como **Min(Catálogo, Precio)**, para mostrar el valor mínimo en la columna **Precio** de la tabla **Catálogo**. Otras fórmulas proporcionan tablas completas como valores devueltos, como **CambiarNombreColumnas(Catálogo, "Precio", "Coste")**, que devuelve todos los registros de la tabla **Catálogo**, pero cambia el nombre de la columna **Precio** a **Coste**.

Al igual que con los números, las fórmulas relacionadas con tablas y registros se recalculan automáticamente a medida que el registro o la tabla subyacentes cambian. Si el coste de un producto de la tabla **Catálogo** está muy por debajo del mínimo anterior, el valor devuelto de la fórmula **[Min](functions/function-aggregates.md)** cambiará automáticamente para establecer la coincidencia.

Se van a analizar algunos ejemplos sencillos.

1. Cree una aplicación en blanco para un teléfono y agregue un control **[Galería](controls/control-gallery.md)** vertical que contenga otros controles.

    De forma predeterminada, la pantalla muestra texto de marcador de posición de una tabla denominada **CustomGallerySample**. La propiedad **[Items](controls/properties-core.md)** del control **[Galería](controls/control-gallery.md)** de la pantalla se establece automáticamente en esa tabla.

    ![](media/working-with-tables/gallery-items.png)

    > [!NOTE]
    > Algunos controles se han reorganizado y ampliado con fines meramente ilustrativos.

2. En lugar de establecer la propiedad **[Elementos](controls/properties-core.md)** con el nombre de la tabla, defina una fórmula que incluya el nombre de la tabla como un argumento, como en este ejemplo:

    `Sort(CustomGallerySample, SampleHeading, Descending)`

    Esta fórmula incorpora la función **[Ordenar](functions/function-sort.md)**, que considera el nombre de una tabla como su primer argumento y el nombre de una columna de dicha tabla como su segundo argumento. La función también admite un tercer argumento opcional, que estipula que desea ordenar los datos en orden descendente.

    ![](media/working-with-tables/gallery-items-sort.png)

3. Defina la propiedad **[Elementos](controls/properties-core.md)** con una fórmula que considere la fórmula del paso anterior como un argumento y devuelve una tabla, como en este ejemplo:

    `FirstN(Sort(CustomGallerySample, SampleHeading, Descending), 2)`

    En esta fórmula, use la función **[FirstN](functions/function-first-last.md)** para mostrar un número concreto de registros de una tabla. Se usa la función **[Ordenar](functions/function-sort.md)** como el primer argumento de **[FirstN](functions/function-first-last.md)** y un número (en este caso, **2**) como el segundo argumento, que especifica la cantidad de registros que se van a mostrar.
   
    Toda la fórmula devuelve una tabla que contiene los dos primeros registros de la tabla **CustomGallerySample**, ordenados por la columna **SampleHeading** en orden descendente.
   
    ![](media/working-with-tables/gallery-items-sort-firstn.png)

### <a name="table-functions-and-control-properties"></a>Funciones de tabla y propiedades de control
Muchas funciones de PowerApps consideran el nombre de una tabla como un argumento, crean una segunda tabla que contiene los mismos datos, manipulan la tabla nueva en función de los otros argumentos y después devuelven el resultado. Estas funciones no modifican la tabla original, ni siquiera si se trata de un origen de datos.

* **[Ordenar](functions/function-sort.md)**, **[Filtrar](functions/function-filter-lookup.md)**: ordena y filtra registros.
* **[FirstN](functions/function-first-last.md)**, **[LastN](functions/function-first-last.md)**: devuelve los primeros o últimos registros N de la tabla.
* **[Abs](functions/function-numericals.md)**, **[Raíz](functions/function-numericals.md)**, **[Redondear](functions/function-round.md)**, **[Redondear.Mas](functions/function-round.md)**, **[Redondear.Menos](functions/function-round.md)**: operaciones aritméticas de cada registro de una tabla con sola columna, que resulta en una tabla de resultados con una sola columna.
* **[Izquierda](functions/function-left-mid-right.md)**, **[Medio](functions/function-left-mid-right.md)**, **[Derecha](functions/function-left-mid-right.md)**, **[Reemplazar](functions/function-replace-substitute.md)**, **[Sustituir](functions/function-replace-substitute.md)**, **[Espacios](functions/function-trim.md)**, **[Minusc](functions/function-lower-upper-proper.md)**, **[Mayusc](functions/function-lower-upper-proper.md)**, **[NomPropio](functions/function-lower-upper-proper.md)**: manipulaciones de cadena en cada registro de una tabla con una sola columna, que resultan en una tabla de cadenas de una sola columna.
* **[Largo](functions/function-len.md)**: para una columna de cadenas, devuelve una tabla de una sola columna que contiene la longitud de cada cadena.
* **[Concatenar](functions/function-concatenate.md)**: concatena varias columnas de cadenas, que resultan en una tabla de cadenas de una sola columna.
* **[AgregarColumnas](functions/function-table-shaping.md)**, **[EliminarColumnas](functions/function-table-shaping.md)**, **[CambiarNombreColumnas](functions/function-table-shaping.md)**, **[MostrarColumnas](functions/function-table-shaping.md)**: manipulación de columnas de la tabla, que resulta en una tabla nueva con columnas distintas.
* **[Distinto](functions/function-distinct.md)**: elimina registros duplicados.
* **[Aleatorio](functions/function-shuffle.md)**: ordena los registros de forma aleatoria.
* **[HashTags](functions/function-hashtags.md)**: busca hashtags en una cadena.
* **[Errores](functions/function-errors.md)**: proporciona información de errores cuando se trabaja con un origen de datos.

Puede ejecutar una función en una tabla que contiene varias columnas, incluso si la función requiere una sola columna como un argumento. Para extraer una única columna de una tabla de varias columnas, use la función **[MostrarColumnas](functions/function-table-shaping.md)** como un argumento para la función que va a utilizar, como en este ejemplo:<br>**Minusc( MostrarColumnas( Productos, "Nombre" ) )**

Esta fórmula crea una tabla de una sola columna que contiene todos los datos de la columna **Nombre** de la tabla **Productos**, pero convierte las letras mayúsculas a minúsculas. Si especifica una tabla como un argumento para la función **[AgregarColumnas](functions/function-table-shaping.md)**, **[CambiarNombreColumnas](functions/function-table-shaping.md)** o **[EliminarColumnas](functions/function-table-shaping.md)**, puede volver a dar forma completamente a la tabla deseada.

Si especifica un origen de datos como un argumento para una de estas funciones, modificará los registros de ese origen de datos y, por lo general, devolverá el nuevo valor del origen de datos como una tabla.

* **[Recopilar](functions/function-clear-collect-clearcollect.md)**, **[Borrar](functions/function-clear-collect-clearcollect.md)**, **[BorrarColección](functions/function-clear-collect-clearcollect.md)**: crea, borra y agrega en una colección.
* **[Actualizar](functions/function-update-updateif.md)**, **[ActualizarSi](functions/function-update-updateif.md)**: actualiza registros que reúnen uno o varios criterios especificados.
* **[Eliminar](functions/function-remove-removeif.md)**, **[EliminarSi](functions/function-remove-removeif.md)**: elimina registros que reúnen uno o varios criterios especificados.

Estas propiedades se establecen en valores que son tablas:

* **Elementos**: se aplica a galerías y cuadros de lista. Tabla que se va a mostrar en la galería.
* **ElementosSeleccionados**: se aplica a cuadros de lista. Tabla de elementos que el usuario ha seleccionado.

## <a name="record-formulas"></a>Fórmulas de registro
También puede generar una fórmula que calcula los datos de un registro individual, considera un registro individual como un argumento y proporciona un registro individual como un valor devuelto. Al volver al ejemplo anterior de la galería, se usa la propiedad **Galería1.Seleccionada** para mostrar información de cualquier registro que el usuario selecciona en la galería.

1. Agregue un botón y establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:<br>
    **Recopilar( RegistroSeleccionado, Galería1.Seleccionada )**

2. Mientras mantiene presionada la tecla Alt, seleccione el botón.

3. En el menú **Archivo**, seleccione **Colecciones**.

    ![](media/working-with-tables/selected-collection.png)

Esta fórmula devuelve un registro que incluye no solo los datos del registro que está seleccionado actualmente en la galería, sino también cada control de dicha galería. Por ejemplo, el registro contiene una columna **SampleText** que coincide con la columna **SampleText** de la tabla original y una columna **Subtitle1** que representa la etiqueta que muestra los datos de esa columna. Seleccione el icono de tabla de la columna **Subtitle1** para profundizar en esos datos.

> [!NOTE]
> La columna **Subtitle1** podría llamarse **Subtitle2** o similar si se han agregado elementos distintos a los que se especifican en este tema.

Ahora que tiene el registro seleccionado, puede extraer campos individuales de él con el operador **.** .

1. Agregue un control **[Etiqueta](controls/control-text-box.md)** y luego muévalo a la galería y el botón.

1. Establezca la propiedad **[Text](controls/properties-core.md)** de la etiqueta en esta expresión:<br>
    **"Selected: " & Gallery1.Selected.SampleHeading**
   
    ![](media/working-with-tables/gallery-selected.png)

Ha usado la propiedad **Selected**, que es un registro, y ha extraído la propiedad **SampleHeading** de ella.

También puede usar un registro como un contenedor de uso general para los valores con nombre relacionados.

* Si crea una fórmula a partir de las funciones **[ActualizarContexto](functions/function-updatecontext.md)** y **[Navegar](functions/function-navigate.md)**, use un registro para recopilar las [variables de contexto](working-with-variables.md#use-a-context-variable) que desea actualizar.
* Use la propiedad **[Actualizaciones](controls/control-form-detail.md)** en un control **[Editar formulario](controls/control-form-detail.md)** para recopilar los cambios que el usuario ha realizado en un formulario.
* Use la función **[Revisión](functions/function-patch.md)** para actualizar un origen de datos, pero también para combinar registros.

En estos casos, el registro nunca formaba parte de una tabla.

### <a name="record-functions-and-control-properties"></a>Funciones de registro y propiedades de control
Funciones que devuelven registros:

* **[FirstN](functions/function-first-last.md)**, **[LastN](functions/function-first-last.md)**: devuelve el o los primeros o últimos registros de la tabla.
* **[Búsqueda](functions/function-filter-lookup.md)**: devuelve el primer registro de una tabla que coincide con uno o varios criterios.
* **[Revisión](functions/function-patch.md)**: actualiza un origen de datos o combina registros.
* **[Predeterminado](functions/function-defaults.md)**: devuelve los valores predeterminados para un origen de datos.

Propiedades que devuelven registros:

* **Seleccionado**: se aplica a galerías y cuadros de lista. Devuelve el registro seleccionado actualmente.
* **Actualizaciones**: se aplica a las galerías.  Reúne todos los cambios que realiza un usuario en un formulario de entrada de datos.
* **[Actualizar](functions/function-update-updateif.md)**: se aplica a los controles de entrada, como controles deslizantes y controles de entrada de texto. Configura las propiedades individuales para que se recopilen en la galería.

## <a name="record-scope"></a>Ámbito del informe
Algunas funciones se aplican mediante la evaluación de una fórmula en todos los registros de una tabla de forma individual.  El resultado de la fórmula se utiliza de varias maneras:  

* **Filtrar**, **Búsqueda**: la fórmula determina si el registro debe incluirse en la salida.
* **Ordenar**: la fórmula ofrece el valor en función del cual ordenar los registros.
* **Concatenar**: la fórmula determina las cadenas que se deben concatenar.
* **ParaTodo**: la fórmula puede devolver cualquier valor, posiblemente con un efecto secundario.
* **Distinto**: la fórmula devuelve un valor, que se usa para identificar registros duplicados.  
* **AgregarColumnas**: la fórmula proporciona el valor del campo agregado.
* **Media**, **Max**, **Min**, **Sum**, **DesvesTP**, **VarP**: la fórmula proporciona el valor que se va a agregar.

Dentro de estas fórmulas, puede hacer referencia a los campos del registro que se va a procesar.  Cada una de estas funciones crea un "ámbito de registro" en el que se evalúa la fórmula, donde los campos del registro están disponibles como identificadores de primer nivel.  También puede hacer referencia a propiedades de control y a otros valores en toda la aplicación.

Por ejemplo, considere una tabla de **Productos**:

![](media/working-with-tables/requested.png)

Para determinar si se había solicitado más cantidad de alguno de estos productos de la que se encuentra disponible:

`Filter( Products, 'Quantity Requested' > 'Quantity Available' )`

El primer argumento para **Filtrar** es la tabla de registros en los que operar, y el segundo argumento es una fórmula.  **Filtrar** crea un ámbito de registro para evaluar esta fórmula en la que están disponibles los campos de cada registro; en este caso, **Producto**, **Cantidad en pedido** y **Cantidad disponible**.  El resultado de la comparación determina si cada registro debe incluirse en el resultado de la función:

![](media/working-with-tables/needed.png)

Según este ejemplo, podemos calcular qué cantidad de cada producto solicitar:

```powerapps-dot
AddColumns( 
    Filter( Products, 'Quantity Requested' > 'Quantity Available' ), 
    "Quantity To Order", 'Quantity Requested' - 'Quantity Available'
)
```

A continuación, se va a agregar una columna calculada al resultado.  **AgregarColumnas** tiene su propio ámbito de registro que se utiliza para calcular la diferencia entre lo que se ha solicitado y lo que está disponible.

![](media/working-with-tables/toorder.png)

Por último, se puede reducir la tabla de resultados a solo las columnas deseadas:

```powerapps-dot
ShowColumns( 
    AddColumns( 
        Filter( Products, 'Quantity Requested' > 'Quantity Available' ), 
        "Quantity To Order", 'Quantity Requested' - 'Quantity Available'
    ), 
    "Product", 
    "Quantity To Order"
)
```

![](media/working-with-tables/toorderonly.png)

Tenga en cuenta que en la fórmula anterior, se han usado comillas dobles (") en algunos casos y comillas simples (') en otros.  Las comillas simples son necesarias cuando se hace referencia al valor de un objeto, como un campo o una tabla, donde el nombre del objeto contiene un espacio.  Las comillas dobles se usan cuando no se hace referencia al valor de un objeto, sino que se habla de él, sobre todo en situaciones en que el objeto todavía no existe, como en el caso de **AgregarColumnas**.  

### <a name="disambiguation"></a>Anulación de ambigüedades
Los nombres de campo agregados con el ámbito de registro anulan los mismos nombres de los restantes lugares de la aplicación.  Cuando esto sucede, para acceder a los valores desde fuera del ámbito de registro hay que utilizar el operador [**@** de anulación de ambigüedades](functions/operators.md):

* Para acceder a valores de ámbitos de registro anidados, use el operador **@** con el nombre de la tabla en la que opera mediante este modelo:<br>_Table_**[@**_FieldName_**]**
* Para acceder a valores globales, como orígenes de datos, colecciones y variables de contexto, use el modelo **[@**_ObjectName_**]** (sin designación de tabla).

Si la tabla en la que se opera es una expresión, como **Filter(** _Table_**,** ... **)**, no se puede usar el operador de desambiguación.  Solo el ámbito de registro más interno puede acceder a los campos de esta expresión de tabla, pero sin usar el operador de anulación de ambigüedades.

Por ejemplo, imagine que tiene una colección **X**:

![](media/working-with-tables/X.png)

Puede crear esta colección con **BorrarColección( X, \[1, 2\] )**.

Y otra colección **Y**:

![](media/working-with-tables/Y.png)

Puede crear esta colección con **BorrarColección( Y, ["A", "B"] )**.

Además, defina una variable de contexto denominada **valor** con esta fórmula: **UpdateContext( {Value: "!"} )**

Se va a agrupar todo.  En este contexto, la fórmula siguiente:

```powerapps-dot
Ungroup( 
    ForAll( X, 
        ForAll( Y, 
            Y[@Value] & Text( X[@Value] ) & [@Value] 
        ) 
    ), 
    "Value" 
)
```

genera esta tabla:

![](media/working-with-tables/XY.png)

¿Qué sucede aquí?  La función **ParaTodo** más externa define un ámbito de registro para **X**, que permite acceder al campo **Valor** de cada registro a medida que se procesa.  Puede acceder a él con tan solo usar la palabra **Valor** o **X[@Value]**.

La función **ParaTodo** más interna define otro ámbito de registro para **Y**.  Puesto que esta tabla también tiene un campo **Valor** definido, el uso de **Valor** aquí hace referencia al campo del registro de **Y** y ya no hace referencia al de **X**.  Aquí, para acceder al campo **Valor** de **X**, es necesario usar la versión más larga con el operador de anulación de ambigüedades.

Puesto que **Y** es el ámbito de registro más interno, el acceso a los campos de esta tabla no precisa de la anulación de desambigüedades, lo que permite usar esta fórmula con el mismo resultado:

```powerapps-dot
Ungroup( 
    ForAll( X, 
        ForAll( Y, 
            Value & Text( X[@Value] ) & [@Value] 
        ) 
    ), 
    "Value" 
)
```

Todos los ámbitos de registro **ParaTodo** invalidan el ámbito global.  La variable de contexto **Valor** definida no está disponible por su nombre sin el operador de anulación de ambigüedades.   Para acceder a este valor, es necesario usar **[@Value]**.

**Desagrupar** acopla el resultado, ya que las funciones **ParaTodo** anidadas darán como resultado una tabla de resultados anidados.

## <a name="inline-syntax"></a>Sintaxis en línea
### <a name="records"></a>Registros
Exprese registros con el uso de llaves que contienen valores de campo con nombre.  Por ejemplo, puede expresar el primer registro en la tabla al inicio de este tema mediante la utilización de la fórmula:

`{ Name: "Chocolate", Price: 3.95, 'Quantity on Hand': 12, 'Quantity on Order': 10 }`

También puede insertar fórmulas dentro de otras, como se muestra en este ejemplo:

`{ Name: First(Products).Name, Price: First(Products).Price * 1.095 }`

Puede anidar registros mediante llaves de anidación, como se muestra en este ejemplo:

`{ 'Quantity': { 'OnHand': ThisItem.QuantOnHand, 'OnOrder': ThisItem.QuantOnOrder } }`

Encierre cada nombre de columna que contiene un carácter especial, como un espacio o dos puntos, entre comillas simples.  Para usar una comilla simple dentro de un nombre de columna, duplíquela.

Tenga en cuenta que el valor de la columna **Precio** no incluye ningún símbolo de moneda, como un signo de dólar. Dicho formato se aplicará cuando se muestre el valor.  

### <a name="tables"></a>Tablas
Puede crear una tabla mediante la utilización de la función **[Tabla](functions/function-table.md)** y un conjunto de registros. Puede expresar la tabla al inicio de este tema mediante la utilización de la fórmula:

```powerapps-dot
Table( 
    { Name: "Chocolate", Price: 3.95, 'Quantity on Hand': 12, 'Quantity on Order': 10 },
    { Name: "Bread", Price: 4.95, 'Quantity on Hand': 34, 'Quantity on Order': 0 },
    { Name: "Water", Price: 4.95, 'Quantity on Hand': 10, 'Quantity on Order': 0 } 
)
```

También puede anidar tablas:

```powerapps-dot
Table( 
    { Name: "Chocolate", 
      'Quantity History': Table( { Quarter: "Q1", OnHand: 10, OnOrder: 10 },
                                 { Quarter: "Q2", OnHand: 18, OnOrder: 0 } ) 
    }
)
```

### <a name="value-tables"></a>Tablas de valores
Puede crear tablas de una sola columna mediante la definición de valores entre corchetes. La tabla resultante tiene una sola columna, denominada **Valor**.

Por ejemplo, `[ 1, 2, 3, 4 ]` es equivalente a `Table( { Value: 1 }, { Value: 2 }, { Value: 3 }, { Value: 4 } )` y devuelve esta tabla:

![](media/working-with-tables/inline-table.png)

