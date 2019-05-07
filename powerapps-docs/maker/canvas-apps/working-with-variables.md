---
title: Comprender las variables de aplicaciones de lienzo | Microsoft Docs
description: Información de referencia para trabajar con estado, variables de contexto y colecciones en aplicaciones de lienzo
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 02/28/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6f46dcdf300c91be9fbc2f39e6b2a5418a4b82de
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61559320"
ms.PowerAppsDecimalTransform: true
---
# <a name="understand-canvas-app-variables-in-powerapps"></a>Comprender las variables de aplicaciones de lienzo en PowerApps

Si ha usado otra herramienta de programación, como Visual Basic o JavaScript, probablemente se pregunte: **¿Dónde están las variables?** PowerApps es ligeramente diferente y requiere otro enfoque. En lugar de buscar una variable al compilar una aplicación de lienzo, pregúntese lo siguiente: **¿Qué hacer en Excel?**

En otras herramientas, lo más probable es que haya realizado explícitamente un cálculo y haya almacenado el resultado en una variable. Pero PowerApps y Excel recalculan automáticamente las fórmulas cuando los datos de entrada cambian, por lo que normalmente no tendrá que crear ni actualizar las variables. Si adopta este enfoque siempre que sea posible, podrá crear, comprender y mantener la aplicación más fácilmente.

En algunos casos deberá usar variables en PowerApps, que amplía el modelo de Excel mediante la adición de [fórmulas de comportamiento](working-with-formulas-in-depth.md). Estas fórmulas se ejecutan cuando, por ejemplo, un usuario selecciona un botón. Dentro de una fórmula de comportamiento, a menudo resulta útil establecer una variable para su uso en otras fórmulas.

En general debe evitar el uso de variables, pero a veces solo una variable puede habilitar la experiencia que busca. Implícitamente las variables se crean y se escribió cuando aparecen en las funciones que establecen sus valores. 

## <a name="translate-excel-into-powerapps"></a>Traducir Excel a PowerApps

### <a name="excel"></a>Excel

Revisemos el funcionamiento de Excel. Una celda puede contener un valor, como un número o una cadena, o una fórmula basada en los valores de otras celdas. Cuando el usuario introduce un valor diferente en una celda, Excel recalcula automáticamente las fórmulas que dependen del valor nuevo. No hace falta realizar ningún tipo de programación para habilitar este comportamiento.

En el ejemplo siguiente, la celda **A3** está establecida en la fórmula **A1 + A2**. Si **A1** o **A2** cambios, **A3** vuelve a calcular automáticamente para reflejar el cambio. Este comportamiento no requiere código fuera de la fórmula en Sí.

![Animación de volver a calcular la suma de dos números en Excel](media/working-with-variables/excel-recalc.gif)

Excel no tiene variables. El valor de una celda que contiene una fórmula cambia en función de su entrada, pero no es posible recordar el resultado de una fórmula y almacenarlo en una celda o en otro lugar. Si cambia el valor de una celda, toda la hoja de cálculo podría cambiar y los valores calculados previamente se perderían. Un usuario de Excel puede copiar y pegar las celdas, pero esto depende del control manual del usuario y no es posible hacerlo con las fórmulas.

### <a name="powerapps"></a>PowerApps

Las aplicaciones que se crean en PowerApps se comportan de una manera muy parecida a Excel. En lugar de actualizar las celdas, puede agregar controles donde quiera en una pantalla y asignarles un nombre para usarlos en fórmulas.

Por ejemplo, puede replicar el comportamiento de Excel en una aplicación mediante la adición de un **[etiqueta](controls/control-text-box.md)** control denominado **Label1**y dos **[deentradadetexto](controls/control-text-input.md)** controles, denominados **TextInput1** y **TextInput2**. Si, a continuación, Establece el **[texto](controls/properties-core.md)** propiedad de **Label1** a **TextInput1 + TextInput2**, siempre se mostrará la suma de los números que se encuentran en **TextInput1** y **TextInput2** automáticamente.

![Calcular la suma de dos números en PowerApps](media/working-with-variables/recalc1.png)

Tenga en cuenta que el **Label1** control está seleccionado y muestra su **[texto](controls/properties-core.md)** fórmulas en la barra de fórmulas en la parte superior de la pantalla. Aquí se encuentra la fórmula **TextInput1 + TextInput2**. Esta fórmula crea una dependencia entre estos controles, del mismo modo que se crean las dependencias entre las celdas de un libro de Excel.  Vamos a cambiar el valor de **TextInput1**:

![Animación de calcular la suma de dos números en PowerApps](media/working-with-variables/recalc2.gif)

La fórmula para **Label1** se ha calculado automáticamente, que muestra el nuevo valor.

En PowerApps, puede usar fórmulas para determinar no solo el valor principal de un control, sino propiedades como el formato. En el ejemplo siguiente, una fórmula para la propiedad **[Color](controls/properties-color-border.md)** de la etiqueta mostrará automáticamente los valores negativos en rojo. El aspecto de la función **[If](functions/function-if.md)** debería resultarle familiar de Excel:

`If( Value(Label1.Text) < 0; Red; Black )`

![Animación de formato condicional](media/working-with-variables/recalc-color.gif)

Puede usar fórmulas para una amplia variedad de escenarios:

* Mediante el uso del GPS de su dispositivo, un control de mapa puede mostrar su ubicación actual con una fórmula que use **Location.Latitude** y **Location.Longitude**.  A medida que se desplaza, el mapa seguirá automáticamente su ubicación.
* Otros usuarios pueden actualizar los [orígenes de datos](working-with-data-sources.md).  Por ejemplo, otros miembros del equipo pueden actualizar los elementos de una lista de SharePoint.  Al actualizar un origen de datos, las fórmulas dependientes se recalculan automáticamente para que reflejen los datos actualizados. En este mismo ejemplo, puede establecer la propiedad **[Items](controls/properties-core.md)** de una galería en la fórmula **Filter( SharePointList )**, que mostrará automáticamente el conjunto recién filtrado de [registros](working-with-tables.md#records).

### <a name="benefits"></a>Ventajas

El uso de fórmulas para compilar aplicaciones tiene muchas ventajas:

* Si está familiarizado con Excel, sabrá usar PowerApps. El lenguaje de fórmulas y modelos es el mismo.
* Si ha usado otras herramientas de programación, piense en la gran cantidad de código que sería necesario para llevar a cabo estos ejemplos.  En Visual Basic, tendría que escribir un controlador de eventos para el evento de cambio en cada control de entrada de texto.  El código para realizar el cálculo de cada uno de ellos es redundante y podría desincronizarse, o tendría que escribir una subrutina común.  En PowerApps, todo esto se consigue con una única fórmula de una línea.
* Sepa a dónde **Label1**del texto procede, sabrá exactamente dónde buscar: la fórmula en la **[texto](controls/properties-core.md)** propiedad.  No hay otra manera de influir en el texto de este control.  En una herramienta de programación tradicional, cualquier controlador de eventos o subrutina puede cambiar el valor de la etiqueta desde cualquier lugar del programa.  Esto puede hacer que sea difícil detectar cuándo y dónde se ha cambiado una variable.
* Si el usuario cambia un control deslizante pero después cambia de opinión, puede devolver el control deslizante a su valor original  y es como si nunca hubiera cambiado nada: la aplicación muestra los mismos valores de control que antes.  No hay repercusiones si se experimenta y se comprueba qué sucede al cambiar algo, igual que en Excel.  

En general, si puede conseguir un efecto mediante una fórmula, lo mejor es que la use. Deje que el motor de fórmulas de PowerApps trabaje por usted.  

## <a name="know-when-to-use-variables"></a>Saber cuándo usar variables

Vamos a cambiar el sumador simple para que actúe como una máquina de sumar antigua, con un total acumulado. Si selecciona el botón **Sumar**, sumará un número al total acumulado. Si selecciona el botón **Borrar**, restablecerá en cero el total acumulado.

| Para mostrar | Descripción |
|----|----|
| <style> IMG {max-width: Ninguno} </style> ![aplicación con un texto de entrada de control, una etiqueta y dos botones](media/working-with-variables/button-changes-state-1.png) | Cuando se inicia la aplicación, el total acumulado es 0.<br><br>El punto rojo representa los dedos del usuario en el cuadro de entrada de texto, donde el usuario escribe **77**. |
| ![El control de entrada de texto contiene 77 y se presiona el botón Agregar](media/working-with-variables/button-changes-state-2.png) | El usuario selecciona el **agregar** botón. |
| ![El total es 77, y se está agregando otro 77](media/working-with-variables/button-changes-state-3.png) | 77 se agrega para el total acumulado.<br><br>El usuario selecciona el **agregar** nuevamente en el botón. |
| ![El total es 154 antes de está desactivada.](media/working-with-variables/button-changes-state-4.png) | 77 nuevo se agrega a la suma total, lo que resulta en 154.<br><br>El usuario selecciona el **clara** botón. |
| ![El total está desactivado.](media/working-with-variables/button-changes-state-5.png) | El total acumulado se restablece en 0. |

Esta máquina de sumar usa algo que no existe en Excel: un botón. En esta aplicación, no puede usar solamente fórmulas para calcular el total acumulado, ya que su valor depende de una serie de acciones que realiza el usuario. El total acumulado debe registrarse y actualizarse manualmente. La mayoría de las herramientas de programación almacena esta información en una *variable*.

En ocasiones necesitará una variable para que la aplicación se comporte de la manera deseada,  pero debe tener en cuenta una serie de advertencias:

* Debe actualizar manualmente el total acumulado. El recálculo automático no lo hará por usted.
* El total acumulado ya no se puede calcular en función de los valores de otros controles. Depende del número de veces que el usuario haya seleccionado el botón **Sumar** y del valor que se encontrase en cada ocasión en el control de entrada de texto. ¿El usuario ha escrito 77 y ha seleccionado **Sumar** dos veces, o bien ha escrito 24 y 130 para cada una de las sumas? No es posible determinarlo una vez que el total haya alcanzado 154.
* Los cambios en el total pueden proceder de diferentes acciones. En este ejemplo, tanto el botón **Sumar** como el botón **Borrar** pueden actualizar el total. Si la aplicación no se comporta de la manera esperada, ¿qué botón causa el problema?

## <a name="use-a-global-variable"></a>Utilizar una variable global

Para crear la máquina de sumar, necesitamos una variable que contenga el total acumulado. Las variables más sencillas para trabajar con PowerApps son las *variables globales*.  

Cómo funcionan las variables globales:

* Establezca el valor de la variable global con la función **[Set](functions/function-set.md)**.  **Set( MyVar; 1 )** establece la variable global **MyVar** en un valor de **1**.
* Use la variable global mediante la referencia al nombre usado con la función **Set**.  En este caso, **MyVar** devolverá **1**.
* Las variables globales pueden contener cualquier valor, como cadenas, números, registros y [tablas](working-with-tables.md).

Vamos a recompilar la máquina de sumar mediante el uso de una variable de global:

1. Agregue un control de entrada de texto, denominado **TextInput1**, y dos botones, denominados **Button1** y **Button2**.

2. Establezca la propiedad **[Text](controls/properties-core.md)** de **Button1** en **"Sumar"** y la propiedad **Text** de **Button2** en **"Borrar"**.

3. Para actualizar el total acumulado cada vez que un usuario seleccione el botón **Sumar**, establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:

    **Set( RunningTotal; RunningTotal + TextInput1 )**

    Establece la existencia de esta fórmula simple **RunningTotal** como una variable global que contiene un número porque el **+** operador. Puede hacer referencia a **RunningTotal** en cualquier parte de la aplicación. Cada vez que el usuario abre esta aplicación, **RunningTotal** tiene un valor inicial de *en blanco*.

    La primera vez que un usuario selecciona el **agregar** botón y **[establecer](functions/function-set.md)** se ejecuta, **RunningTotal** se establece en el valor  **RunningTotal + TextInput1**.

    ![Se establece la propiedad OnSelect del botón Agregar para establecer la función](media/working-with-variables/global-variable-1.png)

4. Para establecer el total acumulado en **0** cada vez que el usuario seleccione el botón **Borrar**, establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:

    **Set( RunningTotal; 0 )**

    ![Se establece la propiedad OnSelect del botón Borrar para establecer la función](media/working-with-variables/global-variable-2.png)

5. Agregue un control **[Etiqueta](controls/control-text-box.md)** y establezca su propiedad **[Texto](controls/properties-core.md)** en **RunningTotal** (TotalAcumulado).

    Esta fórmula se recalculará automáticamente y mostrará al usuario el valor de **RunningTotal** cuando cambie en función de los botones que el usuario seleccione.

    ![Propiedad de texto de la etiqueta se establece en el nombre de la variable](media/working-with-variables/global-variable-3.png)

6. Obtenga una vista previa de la aplicación y ya tiene la máquina de sumar, tal como se describió anteriormente. Escriba un número en el cuadro de texto y presione el botón de **suma** varias veces. Cuando esté listo, vuelva a la experiencia de creación mediante la tecla Esc.

    ![Control de entrada de texto contiene un valor, y la etiqueta contiene el total acumulado](media/working-with-variables/global-variable-4.png)

7. Para mostrar el valor de la variable global, seleccione el **archivo** menú y seleccione **Variables** en el panel izquierdo.

    ![Opción de variables en el menú archivo](media/working-with-variables/global-variable-file-1.png)

8. Para mostrar todos los lugares donde se define y usa la variable, selecciónela.

    ![Lista de la ubicación donde se utiliza la variable](media/working-with-variables/global-variable-file-2.png)

## <a name="types-of-variables"></a>Tipos de variables

PowerApps tiene tres tipos de variables:

| Tipo de variable | Ámbito | Descripción | Funciones que establecen |
| --- | --- | --- | --- |
| Variables globales |App |Las más sencillas de utilizar. Contiene un número, una cadena de texto, un valor booleano, un registro, una tabla, etc. a los que se puede hacer referencia desde cualquier parte de la aplicación. |[**Set**](functions/function-set.md) |
| Variables de contexto |Pantalla |Idóneas para pasar valores a una pantalla, de forma parecida a como se pasan los parámetros a un procedimiento en otros lenguajes. Puede hacer referencia a solo hay una pantalla. |[**UpdateContext**](functions/function-updatecontext.md)<br>[**Navegar**](functions/function-navigate.md) |
| Colecciones |App |Contiene una tabla que puede hacer referencia desde cualquier lugar en la aplicación. Permite que el contenido de la tabla se pueda modificar en lugar de establecerla como un todo. Se pueden guardar en el dispositivo local para su uso posterior. |[**Collect**](functions/function-clear-collect-clearcollect.md)<br>[**ClearCollect**](functions/function-clear-collect-clearcollect.md) |

## <a name="create-and-remove-variables"></a>Crear y quitar variables

Todas las variables se crean implícitamente cuando aparecen en un **establecer**, **UpdateContext**, **Navigate**, **recopilar**, o  **ClearCollect** función. Para declarar una variable y su tipo, se necesita sólo incluir en cualquiera de estas funciones en cualquier lugar en la aplicación. Ninguna de estas funciones crear variables; solo rellenan las variables con valores. Nunca declara variables explícitamente como es posible que en otra herramienta de programación y escribir todos los es implícito de uso.

Por ejemplo, podría tener un control de botón con un **Alseleccionar** fórmula igual a **(X; 1) conjunto**. Esta fórmula establece **X** como una variable con un tipo de número. Puede usar **X** en fórmulas como un número y esa variable tiene un valor de *en blanco* después de abrir la aplicación, pero antes de seleccionar el botón. Cuando se selecciona el botón, asigne a **X** el valor de **1**.

Si ha agregado otro botón y establezca su **OnSelect** propiedad **(X; "Hola") del conjunto**, produciría un error porque el tipo (cadena de texto) no coincide con el tipo en el anterior **establecer**(número). Deben aceptar todas las definiciones de implícitas de la variable de tipo. Una vez más, todo esto ha ocurrido porque ha mencionado **X** en las fórmulas, no porque cualquiera de las fórmulas se había ejecutado realmente.

Quitar una variable mediante la eliminación de todos los **establecer**, **UpdateContext**, **Navigate**, **recopilar**, o **ClearCollect**  funciones que establecen implícitamente la variable. Sin estas funciones, la variable no existe. También debe quitar todas las referencias a la variable porque producirá un error.

## <a name="variable-lifetime-and-initial-value"></a>Duración de la variable y el valor inicial

Todas las variables se mantienen en memoria mientras se ejecuta la aplicación. Después de cerrar la aplicación, se pierden los valores que mantienen las variables.

Puede almacenar el contenido de una variable en un origen de datos mediante el uso de la **Patch** o **recopilar** funciones. También puede almacenar valores en las colecciones en el dispositivo local mediante el [ **SaveData** ](functions/function-savedata-loaddata.md) función.

Cuando el usuario abre la aplicación, todas las variables tienen un valor inicial de *en blanco*.

## <a name="reading-variables"></a>Variables de lectura

Utilice el nombre de variable para leer su valor. Por ejemplo, puede definir una variable con esta fórmula:

`Set( Radius; 12 )`

Puede usar simplemente **Radius** desde cualquier lugar que puede usar un número, y se reemplazará con **12**:

`Pi() * Power( Radius; 2 )`

Si asigna el mismo nombre que una variable global o una colección a una variable de contexto, la variable de contexto tiene prioridad. Sin embargo, todavía puede hacer referencia la variable global o la colección si usas el [operador de desambiguación](functions/operators.md#disambiguation-operator) **@[Radius]**.

## <a name="use-a-context-variable"></a>Usar una variable de contexto

Veamos cómo se crearía la máquina de sumar mediante una variable de contexto en lugar de una variable global.

Cómo funcionan las variables de contexto:

* Establecer implícitamente y establecer variables de contexto utilizando la **[UpdateContext](functions/function-updatecontext.md)** o **[Navigate](functions/function-navigate.md)** función. Cuando se inicia la aplicación, el valor inicial de todas las variables de contexto es *en blanco*.
* Actualice las variables de contexto con los registros. En otras herramientas de programación, normalmente se usa "=" para la asignación, como en "x = 1". Las variables de contexto, use **{x: 1}** en su lugar. Cuando se usa una variable de contexto, use su nombre directamente sin la sintaxis de registro.
* También puede establecer una variable de contexto cuando se usa el **[Navigate](functions/function-navigate.md)** función para mostrar una pantalla. Si piensa en una pantalla como una especie de procedimiento o subrutina, este enfoque es similar a pasar parámetros en otras herramientas de programación.
* Excepto en el caso de **[Navigate](functions/function-navigate.md)**, las variables de contexto están limitadas al contexto de una sola pantalla, que es donde obtienen su nombre. No puede usarlas ni establecerlas fuera de este contexto.
* Las variables de contexto pueden contener cualquier valor, como cadenas, números, registros, y [tablas](working-with-tables.md).

Vamos a volver a compilar la máquina de sumar mediante el uso de una variable de contexto:

1. Agregue un control de entrada de texto, denominado **TextInput1**, y dos botones, denominados **Button1** y **Button2**.

2. Establezca la propiedad **[Text](controls/properties-core.md)** de **Button1** en **"Sumar"** y la propiedad **Text** de **Button2** en **"Borrar"**.

3. Para actualizar el total acumulado cada vez que un usuario seleccione el botón **Sumar**, establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:

    **UpdateContext( { RunningTotal: RunningTotal + TextInput1 } )**

    Establece la existencia de esta fórmula simple **RunningTotal** como una variable de contexto que contiene un número porque el **+** operador. Puede hacer referencia a **RunningTotal** en cualquier parte de esta pantalla. Cada vez que el usuario abre esta aplicación, **RunningTotal** tiene un valor inicial de *en blanco*.

    La primera vez que el usuario selecciona el **agregar** botón y **[UpdateContext](functions/function-updatecontext.md)** se ejecuta, **RunningTotal** se establece en el valor **RunningTotal + TextInput1**.

    ![Propiedad OnSelect del botón Agregar](media/working-with-variables/context-variable-1.png)

4. Para establecer el total acumulado en **0** cada vez que el usuario seleccione el botón **Borrar**, establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:

    **UpdateContext( { RunningTotal: 0 } )**

    Nuevamente, **[UpdateContext](functions/function-updatecontext.md)** se usa con la fórmula **UpdateContext ({RunningTotal: 0 } )**.

    ![Propiedad OnSelect del botón Borrar](media/working-with-variables/context-variable-2.png)

5. Agregue un control **[Etiqueta](controls/control-text-box.md)** y establezca su propiedad **[Texto](controls/properties-core.md)** en **RunningTotal** (TotalAcumulado).

    Esta fórmula se recalculará automáticamente y mostrará al usuario el valor de **RunningTotal** cuando cambie en función de los botones que el usuario seleccione.

    ![Propiedad de texto de etiqueta](media/working-with-variables/context-variable-3.png)

6. Obtenga una vista previa de la aplicación y ya tiene la máquina de sumar, tal como se describió anteriormente. Escriba un número en el cuadro de texto y presione el botón de **suma** varias veces. Cuando esté listo, vuelva a la experiencia de creación mediante la tecla Esc.

    ![Control de entrada de texto muestra un valor y etiqueta muestra el total acumulativo](media/working-with-variables/context-variable-4.png)

7. Puede establecer el valor de una variable de contexto mientras se desplaza a una pantalla. Esto resulta útil a la hora de pasar "contexto" o "parámetros" de una pantalla a otra. Para demostrar esta técnica, insertar una pantalla, inserte un botón y establezca su **OnSelect** propiedad en esta fórmula:

    **Navegar( Screen1; None; { RunningTotal: -1000 } )**

    ![Propiedad OnSelect de un botón](media/working-with-variables/context-variable-5.png)

    Mantenga presionada la tecla Alt mientras selecciona este botón para ambos show **Screen1** y establezca la variable de contexto **RunningTotal** en -1000.

    ![Screen1 está abierto](media/working-with-variables/context-variable-6.png)

8. Para mostrar el valor de la variable de contexto, seleccione el **archivo** menú y, a continuación, seleccione **Variables** en el panel izquierdo.

    ![Opción de variables en el menú archivo](media/working-with-variables/context-variable-file-1.png)

9. Para mostrar dónde se define y usa la variable de contexto, selecciónela.

    ![Lista de donde se usa una variable](media/working-with-variables/context-variable-file-2.png)

## <a name="use-a-collection"></a>Usar una colección

Por último, veamos cómo crear la máquina de sumar con una colección.  Puesto que una colección contiene una tabla que es fácil modificar, vamos a hacer que esta máquina de sumar tenga un "registro" de todos los valores a medida que se escriben.

Cómo funcionan las colecciones:

* Para crear y establecer colecciones, use la función **[ClearCollect](functions/function-clear-collect-clearcollect.md)**.  También puede usar la función **[Collect](functions/function-clear-collect-clearcollect.md)**, pero requerirá otra variable en vez de reemplazar la anterior.  
* Una colección es una clase de origen de datos y, por lo tanto, una tabla. Para obtener acceso a un valor único de una colección, use la función **[First](functions/function-first-last.md)** y extraiga un campo del registro resultante. Si ha usado un solo valor con **[ClearCollect](functions/function-clear-collect-clearcollect.md)**, este será el campo **Value**, como en este ejemplo:<br>
**First(** *VariableName* **).Value**

Vamos a recrear la máquina de sumar mediante una colección:

1. Agregue un control **[Text input](controls/control-text-input.md)**, denominado **TextInput1**, y dos botones, denominados **Button1** y **Button2**.

2. Establezca la propiedad **[Text](controls/properties-core.md)** de **Button1** en **"Sumar"** y la propiedad **Text** de **Button2** en **"Borrar"**.

3. Para actualizar el total acumulado cada vez que un usuario seleccione el botón **Sumar**, establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:

    **Collect( PaperTape; TextInput1.Text )**

    Establece la existencia de esta fórmula simple **PaperTape** como una colección que contiene una tabla de una columna de cadenas de texto. Puede hacer referencia a **PaperTape** en cualquier parte de esta aplicación. Cada vez que un usuario abre esta aplicación, **PaperTape** es una tabla vacía.

    Cuando se ejecuta esta fórmula, agrega el nuevo valor al final de la colección. Dado que estamos agregando un valor único, **recopilar** coloca automáticamente en una sola columna de tabla, y es el nombre de la columna **valor**, que usará más adelante.

    ![Propiedad OnSelect del botón Agregar](media/working-with-variables/papertape-1.png)

4. Para borrar la cinta de papel cuando el usuario selecciona el **borrar** botón, establezca su **[Alseleccionar](controls/properties-core.md)** propiedad en esta fórmula:

    **Clear( PaperTape )**

    ![Propiedad OnSelect del botón Borrar](media/working-with-variables/papertape-2.png)

5. Para mostrar el total acumulado, agregue una etiqueta y establezca su propiedad **[Texto](controls/properties-core.md)** en esta fórmula:

    **Sum( PaperTape; Value )**

    ![Propiedad de texto de la etiqueta](media/working-with-variables/papertape-3.png)

6. Para ejecutar la máquina de sumar, presione F5 para abrir la vista previa, escriba números en el control de entrada de texto y seleccione botones.

    ![El control de entrada de texto muestra un valor y la presentación de la etiqueta el total acumulado](media/working-with-variables/papertape-run-1.png)

7. Presione la tecla Esc para volver al área de trabajo predeterminada.

8. Para mostrar el registro, inserte un control **Tabla de datos** y establezca su propiedad **[Items](controls/properties-core.md)** en esta fórmula:

    **PaperTape**

    En el panel derecho, seleccione el **valor** columna para mostrarla.

    ![Tabla de datos que se muestra los valores que se agregan a la colección](media/working-with-variables/papertape-4.png)

9. Para ver los valores de la colección, seleccione **Colecciones** en el menú **Archivo**.

    ![Vista previa de la colección PaperTape](media/working-with-variables/papertape-file.png)

10. Para almacenar y recuperar la colección, agregue dos controles de botón adicionales y establezca sus **texto** propiedades a **carga** y **guardar**. Establecer el **Alseleccionar** propiedad de la **carga** botón en esta fórmula:

     **Clear( PaperTape );; LoadData( PaperTape; "StoredPaperTape"; true )**

     Deberá borrar la colección en primer lugar porque **LoadData** anexará los valores almacenados al final de la colección.

     ![Propiedad OnSelect del botón Cargar](media/working-with-variables/papertape-5.png)

11. Establecer el **Alseleccionar** propiedad de la **guardar** botón en esta fórmula:

     **SaveData( PaperTape; "StoredPaperTape" )**

     ![Propiedad OnSelect * del botón Guardar](media/working-with-variables/papertape-6.png)

12. Vuelva a obtener la vista previa pulsando la tecla F5, escriba números en el control de entrada de texto y seleccione botones. Seleccione el botón **Guardar**. Cierre y vuelva a cargar la aplicación y seleccione el **carga** botón volver a cargar la colección.

> [!NOTE]
> **SaveData** y **LoadData** función en PowerApps Mobile, pero no en PowerApps Studio o el Reproductor web de PowerApps.