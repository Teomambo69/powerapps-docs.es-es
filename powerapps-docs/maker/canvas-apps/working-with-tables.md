---
title: Comprender las tablas de aplicaciones de lienzo | Microsoft Docs
description: Información de referencia sobre cómo trabajar con tablas, columnas y registros de aplicaciones de lienzo en PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8477ecce3ebd1953807cd348ca4080118c03991d
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74673162"
ms.PowerAppsDecimalTransform: true
---
# <a name="understand-canvas-app-tables-and-records-in-powerapps"></a>Comprender las tablas y los registros de aplicaciones de lienzo en PowerApps

En Power Apps, puede crear una aplicación de lienzo que tenga acceso a información en Microsoft Excel, SharePoint, SQL Server y otros orígenes que almacenen datos en registros y tablas. Para trabajar de forma más eficaz con este tipo de datos, revise los conceptos que subyacen a estas estructuras.

* Un registro contiene una o varias categorías de información sobre una persona, un lugar o una cosa. Por ejemplo, un registro puede contener el nombre, la dirección de correo electrónico y el número de teléfono de un solo cliente. Otras herramientas hacen referencia a un registro como una "fila" o un "elemento".
* Una tabla contiene uno o varios registros que incluyen las mismas categorías de información. Por ejemplo, una tabla puede contener los nombres, las direcciones de correo electrónico y los números de teléfono de 50 clientes.

En la aplicación, usará [fórmulas](working-with-formulas.md) para crear, actualizar y manipular registros y tablas. Probablemente podrá leer y escribir datos en un [origen de datos](working-with-data-sources.md) externo, que es una tabla extendida. Además, puede crear una o varias tablas internas, que se denominan [colecciones](working-with-data-sources.md#collections).

Puede crear una variedad de fórmulas que usan el nombre de una tabla como argumento, al igual que las fórmulas de Excel consideran una o varias referencias de celda como argumentos. Algunas fórmulas de Power apps devuelven una tabla que refleja los demás argumentos que especifique. Por ejemplo, podría crear una fórmula:

* para actualizar un registro en una tabla mediante la especificación de esa tabla como uno de varios argumentos para la función **[Revisión](functions/function-patch.md)** ,
* para agregar, quitar y cambiar el nombre de las columnas de una tabla mediante la especificación de esa tabla como un argumento para la función **[AgregarColumnas](functions/function-table-shaping.md)** , **[EliminarColumnas](functions/function-table-shaping.md)** o **[CambiarNombreColumnas](functions/function-table-shaping.md)** . Ninguna de esas funciones modifica la tabla original. En su lugar, la función devuelve otra tabla basada en el resto de los argumentos que se especifiquen.

## <a name="elements-of-a-table"></a>Elementos de una tabla
![](media/working-with-tables/elements-of-a-table.png)

### <a name="records"></a>Registros
Cada registro contiene al menos una categoría de información sobre una persona, un lugar o una cosa. El ejemplo anterior muestra un registro para cada producto (**Chocolate**, **Pan** y **Agua**) y una columna para cada categoría de información (**Precio**, **Cantidad disponible** y **Cantidad en pedido**).

En una fórmula, puede hacer referencia a un registro por sí mismo, fuera del contexto de una tabla, mediante el uso de llaves. Por ejemplo, este registro **{ Nombre: "Fresas"; Precio: 7;99 }** no está asociado a una tabla. Tenga en cuenta que los nombres de los campos, como **Nombre** y **Precio** en ese ejemplo, no están dentro de comillas dobles.

### <a name="fields"></a>Campos
Un campo es un elemento individual de información de un registro. Puede visualizar este tipo de campo como un valor de una columna para un registro concreto.

Igual que con un control, puede hacer referencia a un campo de un registro mediante **.** , que es el [operador](functions/operators.md) en el registro.  Por ejemplo, **Primero(Productos).Nombre** devuelve el campo **Nombre** para el primer registro de la tabla **Productos**.

Un campo puede contener otro registro o tabla, como muestra el ejemplo de la función **[AgruparPor](functions/function-groupby.md)** . Puede anidar tantos niveles de registros y tablas como desee.

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
> En el caso de los orígenes de datos de SharePoint y Excel que contienen nombres de columna con espacios, Power apps reemplazará los espacios por **"\_x0020\_"** . Por ejemplo, **"nombre de columna"** en SharePoint o Excel aparecerá como **"Column_x0020_Name"** en Power apps cuando se muestre en el diseño de datos o se use en una fórmula.

### <a name="table"></a>Table
Una tabla consta de uno o varios registros, cada uno con varios campos que tienen nombres coherentes entre los registros.

Cualquier tabla almacenada en un origen de datos o en un colección tiene un nombre, que se usa para hacer referencia a la tabla y para pasarlo a funciones que consideran las tablas como argumentos.  Las tablas también pueden resultar de una función o de una fórmula.

Como en el ejemplo siguiente, puede expresar una tabla en una fórmula mediante la utilización de la función **[Tabla](functions/function-table.md)** con un conjunto de registros, que se expresa entre llaves:

`Table( { Value: "Strawberry" }; { Value: "Vanilla" } )`

También puede definir una tabla de una sola columna entre corchetes.  Una manera equivalente de escribir lo anterior:

`[ "Strawberry"; "Vanilla" ]`

## <a name="table-formulas"></a>Fórmulas de tabla
En Excel y Power Apps, se usan fórmulas para manipular números y cadenas de texto de maneras similares:

* En Excel, escriba un valor, como **42**, en la celda **A1** y después escriba una fórmula, como **A1+2**, en otra celda para mostrar el valor de **44**.
* En Power Apps, establezca la propiedad **[default](controls/properties-core.md)** de **Slider1** en **42**y establezca la propiedad **[Text](controls/properties-core.md)** de una etiqueta en **Slider1. Value + 2** para mostrar el valor de **44**.

En ambos casos, el valor calculado cambia automáticamente si modifica los valores de los argumentos (por ejemplo, el número de la celda **A1** o el valor de **Slider1**).

Del mismo modo, puede usar fórmulas para acceder a datos de tablas y registros y manipularlos. Puede usar nombres de tablas como argumentos en algunas fórmulas, como **Min(Catálogo; Precio)** , para mostrar el valor mínimo en la columna **Precio** de la tabla **Catálogo**. Otras fórmulas proporcionan tablas completas como valores devueltos, como **CambiarNombreColumnas(Catálogo; "Precio"; "Coste")** , que devuelve todos los registros de la tabla **Catálogo**, pero cambia el nombre de la columna **Precio** a **Coste**.

Al igual que con los números, las fórmulas relacionadas con tablas y registros se recalculan automáticamente a medida que el registro o la tabla subyacentes cambian. Si el coste de un producto de la tabla **Catálogo** está muy por debajo del mínimo anterior, el valor devuelto de la fórmula **[Min](functions/function-aggregates.md)** cambiará automáticamente para establecer la coincidencia.

Se van a analizar algunos ejemplos sencillos.

1. Cree una aplicación en blanco para un teléfono y agregue un control **[Galería](controls/control-gallery.md)** vertical que contenga otros controles.

    De forma predeterminada, la pantalla muestra texto de marcador de posición de una tabla denominada **CustomGallerySample**. La propiedad **[Items](controls/properties-core.md)** del control **[Galería](controls/control-gallery.md)** de la pantalla se establece automáticamente en esa tabla.

    ![](media/working-with-tables/gallery-items.png)

    > [!NOTE]
    > Algunos controles se han reorganizado y ampliado con fines meramente ilustrativos.

2. En lugar de establecer la propiedad **[Elementos](controls/properties-core.md)** con el nombre de la tabla, defina una fórmula que incluya el nombre de la tabla como un argumento, como en este ejemplo:

    `Sort(CustomGallerySample; SampleHeading; Descending)`

    Esta fórmula incorpora la función **[Ordenar](functions/function-sort.md)** , que considera el nombre de una tabla como su primer argumento y el nombre de una columna de dicha tabla como su segundo argumento. La función también admite un tercer argumento opcional, que estipula que desea ordenar los datos en orden descendente.

    ![](media/working-with-tables/gallery-items-sort.png)

3. Defina la propiedad **[Elementos](controls/properties-core.md)** con una fórmula que considere la fórmula del paso anterior como un argumento y devuelve una tabla, como en este ejemplo:

    `FirstN(Sort(CustomGallerySample; SampleHeading; Descending); 2)`

    En esta fórmula, use la función **[FirstN](functions/function-first-last.md)** para mostrar un número concreto de registros de una tabla. Se usa la función **[Ordenar](functions/function-sort.md)** como el primer argumento de **[FirstN](functions/function-first-last.md)** y un número (en este caso, **2**) como el segundo argumento, que especifica la cantidad de registros que se van a mostrar.

    Toda la fórmula devuelve una tabla que contiene los dos primeros registros de la tabla **CustomGallerySample**, ordenados por la columna **SampleHeading** en orden descendente.

    ![](media/working-with-tables/gallery-items-sort-firstn.png)

## <a name="table-functions-and-control-properties"></a>Funciones de tabla y propiedades de control

Considere la función **Lower** . Si la **Página principal** contiene la cadena de **texto "Hello, World"** , la fórmula **Lower (Welcome)** devuelve **"Hello, World"** .  En cualquier caso, esta función no cambia el valor de esa variable. **Lower** es una función pura en la que solo procesa la entrada y genera resultados. Eso es todo; no tiene efectos secundarios. Todas las funciones de Excel y la mayoría de las funciones de Power apps son funciones puras, que permiten que el libro o la aplicación se vuelvan a calcular automáticamente.

Power Apps ofrece un conjunto de funciones que operan en tablas de la misma manera. Estas funciones toman las tablas como entrada y filtran, ordenan, transforman, reducen y resumen todas las tablas de datos. De hecho, las funciones **inferiores** y muchas otras que normalmente toman un único valor también pueden tomar una tabla de una sola columna como entrada.

* **[Ordenar](functions/function-sort.md)** , **[Filtrar](functions/function-filter-lookup.md)** : ordena y filtra registros.
* **[FirstN](functions/function-first-last.md)** , **[LastN](functions/function-first-last.md)** : devuelve los primeros o últimos registros N de la tabla.
* **[Abs](functions/function-numericals.md)** , **[Raíz](functions/function-numericals.md)** , **[Redondear](functions/function-round.md)** , **[Redondear.Mas](functions/function-round.md)** , **[Redondear.Menos](functions/function-round.md)** : operaciones aritméticas de cada registro de una tabla con sola columna, que resulta en una tabla de resultados con una sola columna.
* **[Izquierda](functions/function-left-mid-right.md)** , **[Medio](functions/function-left-mid-right.md)** , **[Derecha](functions/function-left-mid-right.md)** , **[Reemplazar](functions/function-replace-substitute.md)** , **[Sustituir](functions/function-replace-substitute.md)** , **[Espacios](functions/function-trim.md)** , **[Minusc](functions/function-lower-upper-proper.md)** , **[Mayusc](functions/function-lower-upper-proper.md)** , **[NomPropio](functions/function-lower-upper-proper.md)** : manipulaciones de cadena en cada registro de una tabla con una sola columna, que resultan en una tabla de cadenas de una sola columna.
* **[Largo](functions/function-len.md)** : para una columna de cadenas, devuelve una tabla de una sola columna que contiene la longitud de cada cadena.
* **[Concatenar](functions/function-concatenate.md)** : concatena varias columnas de cadenas, que resultan en una tabla de cadenas de una sola columna.
* **[AgregarColumnas](functions/function-table-shaping.md)** , **[EliminarColumnas](functions/function-table-shaping.md)** , **[CambiarNombreColumnas](functions/function-table-shaping.md)** , **[MostrarColumnas](functions/function-table-shaping.md)** : manipulación de columnas de la tabla, que resulta en una tabla nueva con columnas distintas.
* **[Distinto](functions/function-distinct.md)** : elimina registros duplicados.
* **[Aleatorio](functions/function-shuffle.md)** : ordena los registros de forma aleatoria.
* **[HashTags](functions/function-hashtags.md)** : busca hashtags en una cadena.
* **[Errores](functions/function-errors.md)** : proporciona información de errores cuando se trabaja con un origen de datos.

Muchas de estas funciones toman una tabla de una sola columna como entrada. Si toda una tabla solo tiene una columna, puede especificarla por su nombre. Si una tabla tiene varias columnas, puede especificar una de esas columnas mediante la sintaxis de *TABLE. Column* . Por ejemplo, **Products.Name** devuelve la tabla de una sola columna con solo los valores de **nombre** de la tabla **Products** .

Puede cambiar completamente la forma de una tabla con las funciones **[AddColumns](functions/function-table-shaping.md)** , **[cambiarnombrecolumnas](functions/function-table-shaping.md)** , **[mostrarcolumnas](functions/function-table-shaping.md)** o **[DropColumns](functions/function-table-shaping.md)** . De nuevo, estas funciones solo cambian su salida, no su origen.

Las propiedades de los controles también pueden ser tablas:

* **Elementos** : se aplica a galerías, cuadros de lista y cuadros combinados. Esta propiedad define la tabla que muestra la galería o la lista.
* **SelectedItems** : se aplica a los cuadros de lista y cuadros combinados. Esta propiedad define la tabla de elementos que el usuario ha seleccionado si **SelectMultiple** está habilitado.

## <a name="behavioral-formulas"></a>Fórmulas de comportamiento

Otras funciones están diseñadas específicamente para modificar datos y tienen efectos secundarios. Dado que estas funciones no son puras, debe crearlas con cuidado y no pueden participar en el recálculo automático de los valores de la aplicación. Estas funciones solo se pueden usar dentro de [fórmulas de comportamiento](working-with-formulas-in-depth.md).

* **[Collect](functions/function-clear-collect-clearcollect.md)** , **[Clear](functions/function-clear-collect-clearcollect.md)** , **[ClearCollect](functions/function-clear-collect-clearcollect.md)** crea colecciones, las borra y les agrega datos.
* **[Patch](functions/function-patch.md)** : modifica uno o varios campos de un registro.
* **[Actualizar](functions/function-update-updateif.md)** , **[ActualizarSi](functions/function-update-updateif.md)** : actualiza registros que reúnen uno o varios criterios especificados.
* **[Eliminar](functions/function-remove-removeif.md)** , **[EliminarSi](functions/function-remove-removeif.md)** : elimina registros que reúnen uno o varios criterios especificados.

## <a name="record-formulas"></a>Fórmulas de registro

También puede generar una fórmula que calcula los datos de un registro individual, considera un registro individual como un argumento y proporciona un registro individual como un valor devuelto. Al volver al ejemplo anterior de la galería, se usa la propiedad **Galería1.Seleccionada** para mostrar información de cualquier registro que el usuario selecciona en la galería.

1. Agregue un [**botón**](controls/control-button.md)y establezca su propiedad **[alseleccionar](controls/properties-core.md)** en esta fórmula:<br>
    **Recopilar( RegistroSeleccionado; Galería1.Seleccionada )**

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

* Si crea una fórmula a partir de las funciones **[ActualizarContexto](functions/function-updatecontext.md)** y **[Navegar](functions/function-navigate.md)** , use un registro para recopilar las [variables de contexto](working-with-variables.md#use-a-context-variable) que desea actualizar.
* Use la propiedad **[Actualizaciones](controls/control-form-detail.md)** en un control **[Editar formulario](controls/control-form-detail.md)** para recopilar los cambios que el usuario ha realizado en un formulario.
* Use la función **[Revisión](functions/function-patch.md)** para actualizar un origen de datos, pero también para combinar registros.

En estos casos, el registro nunca formaba parte de una tabla.

## <a name="record-functions-and-control-properties"></a>Funciones de registro y propiedades de control
Funciones que devuelven registros:

* **[FirstN](functions/function-first-last.md)** , **[LastN](functions/function-first-last.md)** : devuelve el o los primeros o últimos registros de la tabla.
* **[Búsqueda](functions/function-filter-lookup.md)** : devuelve el primer registro de una tabla que coincide con uno o varios criterios.
* **[Revisión](functions/function-patch.md)** : actualiza un origen de datos o combina registros.
* **[Predeterminado](functions/function-defaults.md)** : devuelve los valores predeterminados para un origen de datos.

Propiedades que devuelven registros:

* **Seleccionado**: se aplica a galerías y cuadros de lista. Devuelve el registro seleccionado actualmente.
* **Actualizaciones**: se aplica a las galerías.  Reúne todos los cambios que realiza un usuario en un formulario de entrada de datos.
* **[Actualizar](functions/function-update-updateif.md)** : se aplica a los controles de entrada, como controles deslizantes y controles de entrada de texto. Configura las propiedades individuales para que se recopilen en la galería.

## <a name="record-scope"></a>Ámbito del informe

Algunas funciones se aplican mediante la evaluación de una fórmula en todos los registros de una tabla de forma individual. El resultado de la fórmula se utiliza de varias maneras:

* **AgregarColumnas**: la fórmula proporciona el valor del campo agregado.
* **Media**, **Max**, **Min**, **Sum**, **DesvesTP**, **VarP**: la fórmula proporciona el valor que se va a agregar.
* **Filtrar**, **Búsqueda**: la fórmula determina si el registro debe incluirse en la salida.
* **Concatenar**: la fórmula determina las cadenas que se deben concatenar.
* **Distinto**: la fórmula devuelve un valor, que se usa para identificar registros duplicados.
* **Forall** : la fórmula puede devolver cualquier valor, potencialmente con efectos secundarios.
* **Ordenar**: la fórmula ofrece el valor en función del cual ordenar los registros.
* **With** -formula puede devolver cualquier valor, potencialmente con efectos secundarios.

Dentro de estas fórmulas, puede hacer referencia a los campos del registro que se va a procesar. Cada una de estas funciones crea un "ámbito de registro" en el que se evalúa la fórmula, donde los campos del registro están disponibles como identificadores de primer nivel. También puede hacer referencia a propiedades de control y a otros valores en toda la aplicación.

Por ejemplo, considere una tabla de **Productos**:

![](media/working-with-tables/requested.png)

Para crear esta tabla de ejemplo en la aplicación, inserte un botón, establezca su propiedad **alseleccionar** en esta fórmula y, a continuación, seleccione el botón (haga clic en él mientras mantiene presionada la tecla Alt en Power apps Studio):

```powerapps-comma
Set( Products;
    Table(
        { Product: "Widget";    'Quantity Requested': 6;  'Quantity Available': 3 };
        { Product: "Gadget";    'Quantity Requested': 10; 'Quantity Available': 20 };
        { Product: "Gizmo";     'Quantity Requested': 4;  'Quantity Available': 11 };
        { Product: "Apparatus"; 'Quantity Requested': 7;  'Quantity Available': 6 }
    )
)
```

Para determinar si alguno de estos productos tenía más solicitado que el que está disponible:

`Filter( Products; 'Quantity Requested' > 'Quantity Available' )`

El primer argumento para **Filtrar** es la tabla de registros en los que operar, y el segundo argumento es una fórmula.  **Filtrar** crea un ámbito de registro para evaluar esta fórmula en la que están disponibles los campos de cada registro; en este caso, **Producto**, **Cantidad en pedido** y **Cantidad disponible**.  El resultado de la comparación determina si cada registro debe incluirse en el resultado de la función:

![](media/working-with-tables/needed.png)

Según este ejemplo, podemos calcular qué cantidad de cada producto solicitar:

```powerapps-comma
AddColumns( 
    Filter( Products; 'Quantity Requested' > 'Quantity Available' ); 
    "Quantity To Order"; 'Quantity Requested' - 'Quantity Available'
)
```

A continuación, se va a agregar una columna calculada al resultado. **AgregarColumnas** tiene su propio ámbito de registro que se utiliza para calcular la diferencia entre lo que se ha solicitado y lo que está disponible.

![](media/working-with-tables/toorder.png)

Por último, podemos reducir la tabla de resultados a solo las columnas que queremos:

```powerapps-comma
ShowColumns(
    AddColumns(
        Filter( Products; 'Quantity Requested' > 'Quantity Available' );
        "Quantity To Order"; 'Quantity Requested' - 'Quantity Available'
    );
    "Product";
    "Quantity To Order"
)
```

![](media/working-with-tables/toorderonly.png)

Tenga en cuenta que en la fórmula anterior, se han usado comillas dobles (") en algunos casos y comillas simples (') en otros.  Las comillas simples son necesarias cuando se hace referencia al valor de un objeto, como un campo o una tabla, donde el nombre del objeto contiene un espacio.  Las comillas dobles se usan cuando no se hace referencia al valor de un objeto, sino que se habla de él, sobre todo en situaciones en que el objeto todavía no existe, como en el caso de **AgregarColumnas**.

## <a name="disambiguation"></a>Anulación de ambigüedades

Los nombres de campo agregados con el ámbito de registro invalidan los mismos nombres de los restantes lugares de la aplicación.  Cuando esto sucede, para acceder a los valores desde fuera del ámbito de registro hay que utilizar el operador [ **@** de anulación de ambigüedades](functions/operators.md):

* Para acceder a valores de ámbitos de registro anidados, use el operador **@** con el nombre de la tabla en la que opera mediante este modelo:<br>_Table_ **[@** _FieldName_ **]**
* Para acceder a valores globales, como orígenes de datos, colecciones y variables de contexto, use el modelo **[@** _ObjectName_ **]** (sin designación de tabla).

Si la tabla en la que se opera es una expresión, como **Filter(** _Table_ **,** ... **)** , no se puede usar el operador de desambiguación.  Solo el ámbito de registro más interno puede acceder a los campos de esta expresión de tabla, pero sin usar el operador de anulación de ambigüedades.

Por ejemplo, imagine que tiene una colección **X**:

![](media/working-with-tables/X.png)

Puede crear esta colección con **BorrarColección( X; \[1; 2\] )** .

Y otra colección **Y**:

![](media/working-with-tables/Y.png)

Puede crear esta colección con **BorrarColección( Y; ["A"; "B"] )** .

Además, defina una variable de contexto denominada **Valor** con esta fórmula: **ActualizarContexto( {Valor: "!"} )**

Se va a agrupar todo. En este contexto, la fórmula siguiente:

```powerapps-comma
Ungroup(
    ForAll( X;
        ForAll( Y;
            Y[@Value] & Text( X[@Value] ) & [@Value]
        )
    );
    "Value"
)
```

genera esta tabla:

![](media/working-with-tables/XY.png)

¿Qué sucede aquí?  La función **ParaTodo** más externa define un ámbito de registro para **X**, que permite acceder al campo **Valor** de cada registro a medida que se procesa.  Puede acceder a él con tan solo usar la palabra **Valor** o **X[@Value]** .

La función **forall** más interna define otro ámbito de registro para **Y**.  Como esta tabla también tiene un campo de **valor** definido, el uso de **Value** aquí hace referencia al campo del registro **de y y ya no es el**de **X**.  Aquí, para tener acceso al campo de **valor** de **X**, debemos usar la versión más larga con el operador de anulación de ambigüedades.

Puesto que **Y** es el ámbito de registro más interno, el acceso a los campos de esta tabla no precisa de la anulación de desambigüedades, lo que permite usar esta fórmula con el mismo resultado:

```powerapps-comma
Ungroup(
    ForAll( X;
        ForAll( Y;
            Value & Text( X[@Value] ) & [@Value]
        )
    );
    "Value"
)
```

Todos los ámbitos de registro **ParaTodo** invalidan el ámbito global. La variable de contexto de **valor** que definimos no está disponible por el nombre sin el operador de desambiguación. Para obtener acceso a este valor, use **[@Value]** .

**Ungroup** reduce el resultado porque las funciones de **forall** anidadas dan como resultado una tabla de resultados anidada.

## <a name="single-column-tables"></a>Tablas de una sola columna

Para operar en una sola columna de una tabla, use la función **mostrarcolumnas** como en este ejemplo:

```powerapps-comma
ShowColumns( Products; "Product" )
```

Esta fórmula genera esta tabla de una sola columna:

![](media/working-with-tables/single-column.png)

Para una alternativa más corta, especifique *TABLE. Column*, que extrae la tabla de una sola columna de la *columna* solo de la *tabla*. Por ejemplo, esta fórmula produce exactamente el mismo resultado que el uso de **mostrarcolumnas**.

```powerapps-comma
Products.Product
```

## <a name="inline-records"></a>Registros en línea

Exprese registros con el uso de llaves que contienen valores de campo con nombre.  Por ejemplo, puede expresar el primer registro en la tabla al inicio de este tema mediante la utilización de la fórmula:

`{ Name: "Chocolate"; Price: 3,95; 'Quantity on Hand': 12; 'Quantity on Order': 10 }`

También puede insertar fórmulas dentro de otras, como se muestra en este ejemplo:

`{ Name: First(Products).Name; Price: First(Products).Price * 1,095 }`

Puede anidar registros mediante llaves de anidación, como se muestra en este ejemplo:

`{ 'Quantity': { 'OnHand': ThisItem.QuantOnHand; 'OnOrder': ThisItem.QuantOnOrder } }`

Encierre cada nombre de columna que contiene un carácter especial, como un espacio o dos puntos, entre comillas simples.  Para usar una comilla simple dentro de un nombre de columna, duplíquela.

Tenga en cuenta que el valor de la columna **Precio** no incluye ningún símbolo de moneda, como un signo de dólar. Dicho formato se aplicará cuando se muestre el valor.  

## <a name="inline-tables"></a>Tablas insertadas
Puede crear una tabla mediante la utilización de la función **[Tabla](functions/function-table.md)** y un conjunto de registros. Puede expresar la tabla al inicio de este tema mediante la utilización de la fórmula:

```powerapps-comma
Table( 
    { Name: "Chocolate"; Price: 3,95; 'Quantity on Hand': 12; 'Quantity on Order': 10 };
    { Name: "Bread"; Price: 4,95; 'Quantity on Hand': 34; 'Quantity on Order': 0 };
    { Name: "Water"; Price: 4,95; 'Quantity on Hand': 10; 'Quantity on Order': 0 } 
)
```

También puede anidar tablas:

```powerapps-comma
Table( 
    { Name: "Chocolate"; 
      'Quantity History': Table( { Quarter: "Q1"; OnHand: 10; OnOrder: 10 };
                                 { Quarter: "Q2"; OnHand: 18; OnOrder: 0 } ) 
    }
)
```

## <a name="inline-value-tables"></a>Tablas de valores insertados
Puede crear tablas de una sola columna mediante la definición de valores entre corchetes. La tabla resultante tiene una sola columna, denominada **Valor**.

Por ejemplo, `[ 1; 2; 3; 4 ]` es equivalente a `Table( { Value: 1 }; { Value: 2 }; { Value: 3 }; { Value: 4 } )` y devuelve esta tabla:

![](media/working-with-tables/inline-table.png)

