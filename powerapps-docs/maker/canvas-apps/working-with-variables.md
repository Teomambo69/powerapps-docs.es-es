---
title: Comprender las variables de aplicaciones de lienzo | Microsoft Docs
description: Información de referencia para trabajar con estado, variables de contexto y colecciones en aplicaciones de lienzo
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/07/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d7fb0e386309f207809204d4f9f582aa3aedfe7e
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79212754"
ms.PowerAppsDecimalTransform: true
---
# <a name="understand-canvas-app-variables-in-power-apps"></a>Descripción de las variables de la aplicación Canvas en Power apps

Si ha usado otra herramienta de programación como Visual Basic o JavaScript, probablemente se pregunte: **¿dónde están las variables?** Power apps es un poco diferente y requiere un enfoque diferente. En lugar de buscar una variable al compilar una aplicación de lienzo, pregúntese lo siguiente: **¿qué haría en Excel?**

En otras herramientas, lo más probable es que haya realizado explícitamente un cálculo y haya almacenado el resultado en una variable. Sin embargo, Power apps y Excel recalculan automáticamente las fórmulas a medida que los datos de entrada cambian, por lo que normalmente no es necesario crear y actualizar variables. Si adopta este enfoque siempre que sea posible, podrá crear, comprender y mantener la aplicación más fácilmente.

En algunos casos, necesitará usar variables en Power Apps, que amplía el modelo de Excel agregando [fórmulas de comportamiento](working-with-formulas-in-depth.md). Estas fórmulas se ejecutan cuando, por ejemplo, un usuario selecciona un botón. Dentro de una fórmula de comportamiento, a menudo resulta útil establecer una variable para su uso en otras fórmulas.

En general debe evitar el uso de variables, pero a veces solo una variable puede habilitar la experiencia que busca. Las variables se crean y se escriben implícitamente cuando aparecen en funciones que establecen sus valores. 

## <a name="translate-excel-into-power-apps"></a>Traducción de Excel en Power apps

### <a name="excel"></a>Excel

Revisemos el funcionamiento de Excel. Una celda puede contener un valor, como un número o una cadena, o una fórmula basada en los valores de otras celdas. Cuando el usuario introduce un valor diferente en una celda, Excel recalcula automáticamente las fórmulas que dependen del valor nuevo. No hace falta realizar ningún tipo de programación para habilitar este comportamiento.

En el ejemplo siguiente, la celda **a3** se establece en la fórmula **a1 + a2**. Si **a1** o **a2** cambian, **a3** se vuelve a calcular automáticamente para reflejar el cambio. Este comportamiento no requiere codificación fuera de la propia fórmula.

![Animación de recalcular la suma de dos números en Excel](media/working-with-variables/excel-recalc.gif)

Excel no tiene variables. El valor de una celda que contiene una fórmula cambia en función de su entrada, pero no es posible recordar el resultado de una fórmula y almacenarlo en una celda o en otro lugar. Si cambia el valor de una celda, toda la hoja de cálculo podría cambiar y los valores calculados previamente se perderían. Un usuario de Excel puede copiar y pegar las celdas, pero esto depende del control manual del usuario y no es posible hacerlo con las fórmulas.

### <a name="power-apps"></a>Power Apps

Las aplicaciones que crea en Power apps se comportan de manera muy parecida a Excel. En lugar de actualizar las celdas, puede agregar controles donde quiera en una pantalla y asignarles un nombre para usarlos en fórmulas.

Por ejemplo, puede replicar el comportamiento de Excel en una aplicación agregando un control de **[etiqueta](controls/control-text-box.md)** , denominado **Label1**, y dos controles de **[entrada de texto](controls/control-text-input.md)** , denominados **TextInput1** y **TextInput2**. Si después establece la propiedad **[Text](controls/properties-core.md)** de **Label1** en **TextInput1 + TextInput2**, siempre mostrará la suma de los números que se encuentren en **TextInput1** y **TextInput2** automáticamente.

![Calcular la suma de dos números en Power apps](media/working-with-variables/recalc1.png)

Observe que el control **Label1** está seleccionado y muestra su fórmula de **[texto](controls/properties-core.md)** en la barra de fórmulas en la parte superior de la pantalla. Aquí se encuentra la fórmula **TextInput1 + TextInput2**. Esta fórmula crea una dependencia entre estos controles, del mismo modo que se crean las dependencias entre las celdas de un libro de Excel.  Vamos a cambiar el valor de **TextInput1**:

![Animación del cálculo de la suma de dos números en Power apps](media/working-with-variables/recalc2.gif)

La fórmula de **Label1** se ha recalculado automáticamente y muestra el nuevo valor.

En Power Apps, puede usar fórmulas para determinar no solo el valor principal de un control, sino también propiedades como el formato. En el ejemplo siguiente, una fórmula para la propiedad **[Color](controls/properties-color-border.md)** de la etiqueta mostrará automáticamente los valores negativos en rojo. El aspecto de la función **[If](functions/function-if.md)** debería resultarle familiar de Excel:

`If( Value(Label1.Text) < 0; Red; Black )`

![Animación de formato condicional](media/working-with-variables/recalc-color.gif)

Puede usar fórmulas para una amplia variedad de escenarios:

* Mediante el uso del GPS de su dispositivo, un control de mapa puede mostrar su ubicación actual con una fórmula que use **Location.Latitude** y **Location.Longitude**.  A medida que se desplaza, el mapa seguirá automáticamente su ubicación.
* Otros usuarios pueden actualizar los [orígenes de datos](working-with-data-sources.md).  Por ejemplo, otros miembros del equipo pueden actualizar los elementos de una lista de SharePoint.  Al actualizar un origen de datos, las fórmulas dependientes se recalculan automáticamente para que reflejen los datos actualizados. En este mismo ejemplo, puede establecer la propiedad **[Items](controls/properties-core.md)** de una galería en la fórmula **Filter( SharePointList )**, que mostrará automáticamente el conjunto recién filtrado de [registros](working-with-tables.md#records).

### <a name="benefits"></a>Ventajas

El uso de fórmulas para compilar aplicaciones tiene muchas ventajas:

* Si sabe Excel, conocerá Power apps. El lenguaje de fórmulas y modelos es el mismo.
* Si ha usado otras herramientas de programación, piense en la gran cantidad de código que sería necesario para llevar a cabo estos ejemplos.  En Visual Basic, tendría que escribir un controlador de eventos para el evento de cambio en cada control de entrada de texto.  El código para realizar el cálculo de cada uno de ellos es redundante y podría desincronizarse, o tendría que escribir una subrutina común.  En Power Apps, todo esto se logra con una sola fórmula de una línea.
* Para saber de dónde procede el texto de **Label1**, sabe exactamente dónde buscar: la fórmula en la propiedad **[Text](controls/properties-core.md)** .  No hay otra manera de influir en el texto de este control.  En una herramienta de programación tradicional, cualquier controlador de eventos o subrutina puede cambiar el valor de la etiqueta desde cualquier lugar del programa.  Esto puede hacer que sea difícil detectar cuándo y dónde se ha cambiado una variable.
* Si el usuario cambia un control deslizante pero después cambia de opinión, puede devolver el control deslizante a su valor original  y es como si nunca hubiera cambiado nada: la aplicación muestra los mismos valores de control que antes.  No hay repercusiones si se experimenta y se comprueba qué sucede al cambiar algo, igual que en Excel.  

En general, si puede conseguir un efecto mediante una fórmula, lo mejor es que la use. Permita que el motor de fórmulas de Power apps funcione para usted.  

## <a name="know-when-to-use-variables"></a>Saber cuándo usar variables

Vamos a cambiar el sumador simple para que actúe como una máquina de sumar antigua, con un total acumulado. Si selecciona el botón **Sumar**, sumará un número al total acumulado. Si selecciona el botón **Borrar**, restablecerá en cero el total acumulado.

| Display | Descripción |
|----|----|
| <style>IMG {Max-width: None}</style> ![aplicación con un control de entrada de texto, una etiqueta y dos botones](media/working-with-variables/button-changes-state-1.png) | Cuando se inicia la aplicación, el total en ejecución es 0.<br><br>El punto rojo representa el dedo del usuario en el cuadro de entrada de texto, donde el usuario escribe **77**. |
| ![El control entrada de texto contiene 77 y se está presionando el botón Agregar.](media/working-with-variables/button-changes-state-2.png) | El usuario selecciona el botón **Agregar** . |
| ![El total es 77 y se le agrega otro 77.](media/working-with-variables/button-changes-state-3.png) | 77 se agrega al total acumulado.<br><br>El usuario vuelve a seleccionar el botón **Agregar** . |
| ![El total es 154 antes de que se borre.](media/working-with-variables/button-changes-state-4.png) | 77 se agrega de nuevo al total acumulado, lo que da como resultado 154.<br><br>El usuario selecciona el botón **Borrar** . |
| ![Se borra el total.](media/working-with-variables/button-changes-state-5.png) | El total acumulado se restablece en 0. |

Esta máquina de sumar usa algo que no existe en Excel: un botón. En esta aplicación, no puede usar solamente fórmulas para calcular el total acumulado, ya que su valor depende de una serie de acciones que realiza el usuario. El total acumulado debe registrarse y actualizarse manualmente. La mayoría de las herramientas de programación almacena esta información en una *variable*.

En ocasiones necesitará una variable para que la aplicación se comporte de la manera deseada,  pero debe tener en cuenta una serie de advertencias:

* Debe actualizar manualmente el total acumulado. El recálculo automático no lo hará por usted.
* El total acumulado ya no se puede calcular en función de los valores de otros controles. Depende del número de veces que el usuario haya seleccionado el botón **Sumar** y del valor que se encontrase en cada ocasión en el control de entrada de texto. ¿El usuario ha escrito 77 y ha seleccionado **Sumar** dos veces, o bien ha escrito 24 y 130 para cada una de las sumas? No es posible determinarlo una vez que el total haya alcanzado 154.
* Los cambios en el total pueden proceder de diferentes acciones. En este ejemplo, tanto el botón **Sumar** como el botón **Borrar** pueden actualizar el total. Si la aplicación no se comporta de la manera esperada, ¿qué botón causa el problema?

## <a name="use-a-global-variable"></a>Usar una variable global

Para crear la máquina de sumar, necesitamos una variable que contenga el total acumulado. Las variables más sencillas con las que trabajar en Power apps son *las variables globales*.  

Cómo funcionan las variables globales:

* Establezca el valor de la variable global con la función **[Set](functions/function-set.md)**.  **Set( MyVar; 1 )** establece la variable global **MyVar** en un valor de **1**.
* Use la variable global mediante la referencia al nombre usado con la función **Set**.  En este caso, **MyVar** devolverá **1**.
* Las variables globales pueden contener cualquier valor, como cadenas, números, registros y [tablas](working-with-tables.md).

Vamos a recompilar la máquina de sumar mediante el uso de una variable de global:

1. Agregue un control de entrada de texto, denominado **TextInput1**, y dos botones, denominados **Button1** y **Button2**.

2. Establezca la propiedad **[Text](controls/properties-core.md)** de **Button1** en **"Sumar"** y la propiedad **Text** de **Button2** en **"Borrar"**.

3. Para actualizar el total acumulado cada vez que un usuario seleccione el botón **Sumar**, establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:

    **Set (RunningTotal, RunningTotal + TextInput1)**

    La mera existencia de esta fórmula establece **RunningTotal** como una variable global que contiene un número debido al operador **+** . Puede hacer referencia a **RunningTotal** en cualquier parte de la aplicación. Cada vez que el usuario abre esta aplicación, **RunningTotal** tiene un valor inicial de *Blank*.

    La primera vez que un usuario selecciona el botón **Agregar** y **[establece](functions/function-set.md)** ejecuciones, **RunningTotal** se establece en el valor **RunningTotal + TextInput1**.

    ![La propiedad alseleccionar del botón Agregar está establecida en Set function](media/working-with-variables/global-variable-1.png)

4. Para establecer el total acumulado en **0** cada vez que el usuario seleccione el botón **Borrar**, establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:

    **Set( RunningTotal; 0 )**

    ![La propiedad alseleccionar del botón Clear está establecida en Set function](media/working-with-variables/global-variable-2.png)

5. Agregue un control **[Etiqueta](controls/control-text-box.md)** y establezca su propiedad **[Texto](controls/properties-core.md)** en **RunningTotal** (TotalAcumulado).

    Esta fórmula se recalculará automáticamente y mostrará al usuario el valor de **RunningTotal** cuando cambie en función de los botones que el usuario seleccione.

    ![La propiedad Text de la etiqueta se establece en el nombre de la variable.](media/working-with-variables/global-variable-3.png)

6. Obtenga una vista previa de la aplicación y ya tiene la máquina de sumar, tal como se describió anteriormente. Escriba un número en el cuadro de texto y presione el botón de **suma** varias veces. Cuando esté listo, vuelva a la experiencia de creación mediante la tecla Esc.

    ![El control de entrada de texto contiene un valor y la etiqueta contiene el total acumulado](media/working-with-variables/global-variable-4.png)

7. Para mostrar el valor de la variable global, seleccione el menú **archivo** y seleccione **variables** en el panel izquierdo.

    ![Opción variables en el menú Archivo](media/working-with-variables/global-variable-file-1.png)

8. Para mostrar todos los lugares donde se define y se usa la variable, selecciónela.

    ![Lista de la ubicación donde se usa la variable](media/working-with-variables/global-variable-file-2.png)

## <a name="types-of-variables"></a>Tipos de variables

Power apps tiene tres tipos de variables:

| Tipo de variable | Ámbito | Descripción | Funciones que establecen |
| --- | --- | --- | --- |
| Variables globales |de Power BI |Las más sencillas de utilizar. Contiene un número, una cadena de texto, un valor booleano, un registro, una tabla, etc. a los que se puede hacer referencia desde cualquier parte de la aplicación. |[**Set**](functions/function-set.md) |
| Variables de contexto |Pantalla |Idóneas para pasar valores a una pantalla, de forma parecida a como se pasan los parámetros a un procedimiento en otros lenguajes. Solo se puede hacer referencia desde una pantalla. |[**UpdateContext**](functions/function-updatecontext.md)<br>[**Navegar**](functions/function-navigate.md) |
| Colecciones |de Power BI |Contiene una tabla a la que se puede hacer referencia desde cualquier lugar de la aplicación. Permite que el contenido de la tabla se pueda modificar en lugar de establecerla como un todo. Se pueden guardar en el dispositivo local para su uso posterior. |[**Collect**](functions/function-clear-collect-clearcollect.md)<br>[**ClearCollect**](functions/function-clear-collect-clearcollect.md) |

## <a name="create-and-remove-variables"></a>Crear y quitar variables

Todas las variables se crean implícitamente cuando aparecen en una función **set**, **UpdateContext**, **Navigate**, **Collect**o **ClearCollect** . Para declarar una variable y su tipo, solo tiene que incluirla en cualquiera de estas funciones en cualquier parte de la aplicación. Ninguna de estas funciones crea variables. solo rellenan las variables con valores. Nunca se declaran variables explícitamente como se haría en otra herramienta de programación, y todo lo que se escribe es implícito en el uso.

Por ejemplo, podría tener un control de botón con una fórmula **alseleccionar** igual a **set (X, 1)**. Esta fórmula establece **X** como variable con un tipo de número. Puede usar **X** en las fórmulas como un número y esa variable tiene un valor *en blanco* después de abrir la aplicación, pero antes de seleccionar el botón. Cuando se selecciona el botón, se asigna a **X** el valor **1**.

Si agregó otro botón y establece su propiedad **alseleccionar** en **set (X, "Hello")**, se producirá un error porque el tipo (cadena de texto) no coincide con el tipo del **conjunto** anterior (número). Todas las definiciones implícitas de la variable deben estar de acuerdo en el tipo. De nuevo, todo esto se produjo porque se mencionó **X** en fórmulas, no porque ninguna de esas fórmulas se ejecutó realmente.

Quite una variable quitando todas las funciones **set**, **UpdateContext**, **Navigate**, **Collect**o **ClearCollect** que establezcan implícitamente la variable. Sin estas funciones, la variable no existe. También debe quitar las referencias a la variable, ya que provocarán un error.

## <a name="variable-lifetime-and-initial-value"></a>Duración de la variable y valor inicial

Todas las variables se mantienen en la memoria mientras se ejecuta la aplicación. Una vez que se cierra la aplicación, se pierden los valores que contienen las variables.

Puede almacenar el contenido de una variable en un origen de datos mediante las funciones **patch** o **Collect** . También puede almacenar valores en colecciones en el dispositivo local mediante la función [**savedata**](functions/function-savedata-loaddata.md) .

Cuando el usuario abre la aplicación, todas las variables tienen el valor inicial *en blanco*.

## <a name="reading-variables"></a>Leer variables

Use el nombre de la variable para leer su valor. Por ejemplo, puede definir una variable con esta fórmula:

`Set( Radius; 12 )`

A continuación, puede usar simplemente **RADIUS** en cualquier lugar en el que pueda usar un número y se reemplazará por **12**:

`Pi() * Power( Radius; 2 )`

Si asigna a una variable de contexto el mismo nombre que una variable global o una colección, la variable de contexto tiene prioridad. Sin embargo, todavía puede hacer referencia a la variable global o colección si utiliza el [operador de desambiguación](functions/operators.md#disambiguation-operator) **[@Radius]**.

## <a name="use-a-context-variable"></a>Usar una variable de contexto

Veamos cómo se crearía la máquina de sumar mediante una variable de contexto en lugar de una variable global.

Cómo funcionan las variables de contexto:

* Puede establecer y establecer implícitamente variables de contexto mediante la función **[UpdateContext](functions/function-updatecontext.md)** o **[Navigate](functions/function-navigate.md)** . Cuando se inicia la aplicación, el valor inicial de todas las variables de contexto está *en blanco*.
* Las variables de contexto se actualizan con registros. En otras herramientas de programación, normalmente se usa "=" para la asignación, como en "x = 1". En el caso de las variables de contexto, se usa **{ x: 1 }**. Cuando use una variable de contexto, use su nombre directamente sin la sintaxis de registro.
* También puede establecer una variable de contexto al usar la función **[Navigate](functions/function-navigate.md)** para mostrar una pantalla. Si piensa en una pantalla como un tipo de procedimiento o subrutina, este enfoque se asemeja al paso de parámetros en otras herramientas de programación.
* Excepto en el caso de **[Navigate](functions/function-navigate.md)**, las variables de contexto están limitadas al contexto de una sola pantalla, que es donde obtienen su nombre. No puede usarlas ni establecerlas fuera de este contexto.
* Las variables de contexto pueden contener cualquier valor, como cadenas, números, registros, y [tablas](working-with-tables.md).

Vamos a volver a compilar la máquina de sumar mediante el uso de una variable de contexto:

1. Agregue un control de entrada de texto, denominado **TextInput1**, y dos botones, denominados **Button1** y **Button2**.

2. Establezca la propiedad **[Text](controls/properties-core.md)** de **Button1** en **"Sumar"** y la propiedad **Text** de **Button2** en **"Borrar"**.

3. Para actualizar el total acumulado cada vez que un usuario seleccione el botón **Sumar**, establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:

    **UpdateContext ({RunningTotal: RunningTotal + TextInput1})**

    La mera existencia de esta fórmula establece **RunningTotal** como una variable de contexto que contiene un número debido al operador **+** . Puede hacer referencia a **RunningTotal** en cualquier parte de esta pantalla. Cada vez que el usuario abre esta aplicación, **RunningTotal** tiene un valor inicial de *Blank*.

    La primera vez que el usuario selecciona el botón **Agregar** y se ejecuta **[UpdateContext](functions/function-updatecontext.md)** , **RunningTotal** se establece en el valor **RunningTotal + TextInput1**.

    ![Propiedad alseleccionar del botón Agregar](media/working-with-variables/context-variable-1.png)

4. Para establecer el total acumulado en **0** cada vez que el usuario seleccione el botón **Borrar**, establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:

    **UpdateContext( { RunningTotal: 0 } )**

    Una vez más, se usa **[UpdateContext](functions/function-updatecontext.md)** con la fórmula **UpdateContext( { RunningTotal: 0 } )**.

    ![Propiedad alseleccionar del botón borrar](media/working-with-variables/context-variable-2.png)

5. Agregue un control **[Etiqueta](controls/control-text-box.md)** y establezca su propiedad **[Texto](controls/properties-core.md)** en **RunningTotal** (TotalAcumulado).

    Esta fórmula se recalculará automáticamente y mostrará al usuario el valor de **RunningTotal** cuando cambie en función de los botones que el usuario seleccione.

    ![Propiedad de texto de Label](media/working-with-variables/context-variable-3.png)

6. Obtenga una vista previa de la aplicación y ya tiene la máquina de sumar, tal como se describió anteriormente. Escriba un número en el cuadro de texto y presione el botón de **suma** varias veces. Cuando esté listo, vuelva a la experiencia de creación mediante la tecla Esc.

    ![Control de entrada de texto muestra un valor, y etiqueta muestra total acumulado](media/working-with-variables/context-variable-4.png)

7. Puede establecer el valor de una variable de contexto mientras se desplaza a una pantalla. Esto resulta útil a la hora de pasar "contexto" o "parámetros" de una pantalla a otra. Para mostrar esta técnica, inserte una pantalla, inserte un botón y establezca su propiedad **alseleccionar** en esta fórmula:

    **Navegar( Screen1; None; { RunningTotal: -1000 } )**

    ![Propiedad alseleccionar de un botón](media/working-with-variables/context-variable-5.png)

    Mantenga presionada la tecla Alt mientras selecciona este botón para mostrar **Screen1** y establezca la variable de contexto **RunningTotal** en-1000.

    ![Screen1 está abierto](media/working-with-variables/context-variable-6.png)

8. Para mostrar el valor de la variable de contexto, seleccione el menú **archivo** y, a continuación, seleccione **variables** en el panel izquierdo.

    ![Opción variables en el menú Archivo](media/working-with-variables/context-variable-file-1.png)

9. Para mostrar dónde se define y se usa la variable de contexto, selecciónela.

    ![Lista de la ubicación en la que se usa una variable](media/working-with-variables/context-variable-file-2.png)

## <a name="use-a-collection"></a>Usar una colección

Por último, veamos cómo crear la máquina de sumar con una colección.  Puesto que una colección contiene una tabla que es fácil modificar, vamos a hacer que esta máquina de sumar tenga un "registro" de todos los valores a medida que se escriben.

Cómo funcionan las colecciones:

* Para crear y establecer colecciones, use la función **[ClearCollect](functions/function-clear-collect-clearcollect.md)**.  También puede usar la función **[Collect](functions/function-clear-collect-clearcollect.md)**, pero requerirá otra variable en vez de reemplazar la anterior.  
* Una colección es una clase de origen de datos y, por lo tanto, una tabla. Para obtener acceso a un valor único de una colección, use la función **[First](functions/function-first-last.md)** y extraiga un campo del registro resultante. Si ha usado un solo valor con **[ClearCollect](functions/function-clear-collect-clearcollect.md)**, este será el campo **Value**, como en este ejemplo:<br>
**Primero (** *VariableName* **). Valor** de

Vamos a recrear la máquina de sumar mediante una colección:

1. Agregue un control **[Text input](controls/control-text-input.md)**, denominado **TextInput1**, y dos botones, denominados **Button1** y **Button2**.

2. Establezca la propiedad **[Text](controls/properties-core.md)** de **Button1** en **"Sumar"** y la propiedad **Text** de **Button2** en **"Borrar"**.

3. Para actualizar el total acumulado cada vez que un usuario seleccione el botón **Sumar**, establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta fórmula:

    **Collect( PaperTape; TextInput1.Text )**

    La mera existencia de esta fórmula establece **PaperTape** como una colección que contiene una tabla de cadenas de texto de una sola columna. Puede hacer referencia a **PaperTape** en cualquier parte de esta aplicación. Cada vez que un usuario abre esta aplicación, **PaperTape** es una tabla vacía.

    Cuando se ejecuta esta fórmula, agrega el nuevo valor al final de la colección. Dado que estamos agregando un solo valor, **Collect** lo coloca automáticamente en una tabla de una sola columna y el nombre de la columna es **Value**, que usará más adelante.

    ![Propiedad alseleccionar del botón Agregar](media/working-with-variables/papertape-1.png)

4. Para borrar la cinta papel cuando el usuario selecciona el botón **Borrar** , establezca su propiedad **[alseleccionar](controls/properties-core.md)** en esta fórmula:

    **Clear( PaperTape )**

    ![Propiedad alseleccionar del botón borrar](media/working-with-variables/papertape-2.png)

5. Para mostrar el total acumulado, agregue una etiqueta y establezca su propiedad **[Texto](controls/properties-core.md)** en esta fórmula:

    **Sum( PaperTape; Value )**

    ![Propiedad texto de la etiqueta](media/working-with-variables/papertape-3.png)

6. Para ejecutar la máquina de sumar, presione F5 para abrir la vista previa, escriba números en el control de entrada de texto y seleccione botones.

    ![El control entrada de texto muestra un valor y la etiqueta muestra el total acumulado](media/working-with-variables/papertape-run-1.png)

7. Presione la tecla Esc para volver al área de trabajo predeterminada.

8. Para mostrar el registro, inserte un control **Tabla de datos** y establezca su propiedad **[Items](controls/properties-core.md)** en esta fórmula:

    **PaperTape**

    En el panel derecho, seleccione la columna **valor** para mostrarla.

    ![Tabla de datos que muestra los valores agregados a la colección](media/working-with-variables/papertape-4.png)

9. Para ver los valores de la colección, seleccione **Colecciones** en el menú **Archivo**.

    ![Vista previa de la colección PaperTape](media/working-with-variables/papertape-file.png)

10. Para almacenar y recuperar la colección, agregue dos controles de botón adicionales y establezca sus propiedades de **texto** para **cargar** y **Guardar**. Establezca la propiedad **alseleccionar** del botón **cargar** en esta fórmula:

     **Clear( PaperTape );; LoadData( PaperTape; "StoredPaperTape"; true )**

     Primero debe borrar la colección porque **LoadData** anexará los valores almacenados al final de la colección.

     ![Propiedad alseleccionar del botón cargar](media/working-with-variables/papertape-5.png)

11. Establezca la propiedad **alseleccionar** del botón **Guardar** en esta fórmula:

     **SaveData( PaperTape; "StoredPaperTape" )**

     ![Propiedad alseleccionar * del botón Guardar](media/working-with-variables/papertape-6.png)

12. Vuelva a obtener la vista previa pulsando la tecla F5, escriba números en el control de entrada de texto y seleccione botones. Seleccione el botón **Guardar**. Cierre y vuelva a cargar la aplicación y seleccione el botón **cargar** para volver a cargar la colección.

> [!NOTE]
> La función **savedata** y **LoadData** de Power apps Mobile, pero no Power apps Studio o el reproductor web para Power apps.